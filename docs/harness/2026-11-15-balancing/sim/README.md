# svsim - 2D simulation of "Sotto Voce: The Cut"

A small, standard-library-only Python simulation of the evening (guards, suspicion, costumes, cues, gadgets,
score, endings), calibrated against the in-game measurements of 14.11. It is meant for agents who
script player routes and run Monte Carlo over `WaitJitter` / look-around to find routes, exploits and difficulty.

Python 3.8+ only, no installs. All game values are read at runtime from the CSVs and `map.json`.

## Run

```
python3 sim/calibrate.py                       # measured vs. simulated (levers 1.5/3.5/5.5 s, Pompier round)
python3 sim/routes/intended.py -v              # the design's route once, step timeline + event log
python3 sim/routes/intended.py --runs 200      # Monte Carlo over seeds
python3 sim/run.py path/to/my_route.py --runs 100
```

Options for every script:

| option | meaning |
|---|---|
| `--data DIR` | directory with `balancing.csv`, `npcs.csv`, `schedule.csv`, `phases.csv` (default: `inbox/2026-11-14-balancing/data`) |
| `--map FILE` | `map.json` (default: `inbox/2026-11-14-balancing/level/map.json`) |
| `--set Name=Value` | override one `balancing.csv` value (repeatable); values outside Min/Max print a WARNING |
| `--tune name=value` | override a sim-internal unknown (`svsim/guard.py` `Tuning`), e.g. `--tune settle_radius=90` |
| `--seed N`, `--runs N` | Monte Carlo: run N seeds starting at N |
| `--light lit/shadow` | her light value everywhere: `lit` = 1.0 (default, worst case for her), `shadow` = ShadowSightFactor |
| `--outside-zone allow/strict` | costume rule outside every zone (see Assumptions) |
| `--dt 0.05` | sim step (perception always runs at 10 Hz, like the component) |
| `-v`, `--json` | event log of the first run; JSON summary |

The navigation graph is cached in `sim/.cache/` (rebuilt automatically when the map changes).

## Write a route

A route file defines `build()` returning a `Route`. Steps run in order; each step's start/end time is logged.
`routes/example.py` uses every step type (it gets caught by the usher - a demo, not a good route):

```python
from svsim import Route
from svsim.runner import main

def build():
    r = Route('example')
    r.wait_until(lambda s: s.npc('Pompier').x > 1000, timeout=30, desc='Pompier walks east')
    r.change('smock')                                   # screen by costume alias (smock/chorus) or label part
    r.move((420, -1150), (420, -950), gait='walk')      # straight waypoints; walk / sneak / run
    r.pull('Trap')                                      # Fly / SteamDown / Trap, within 150 cm of the lever
    r.goto((950, -1250))                                # planned shortest path around blockers
    r.throw((900, -1100))                               # gadget: wind-up, flight, rattle, lure
    r.hide('WingsRack', until=lambda s: s.npc('Pompier').is_distracted(), timeout=20)
    r.goto((900, -1180))
    r.wait_until(lambda s: not s.npc('Pompier').is_distracted(), timeout=20)
    r.pickup()
    r.goto((1420, 1480), gait='sneak')
    r.take_score(wait=True, timeout=60); r.shaft(); r.goto((40, -1150), gait='run'); r.exit()  # or r.desk()
    return r

if __name__ == '__main__':
    main(build, 'example route')      # gives the CLI options above
```

(The route files add `sim/` to `sys.path` first, see the top of `routes/example.py`.)

- **Blockers:** `move()` checks every straight segment against the blockers inflated by her radius (34 cm).
  A segment that crosses one ends the run with outcome `route_error` and names the blocker and its
  extents - nothing clips silently. `goto()` plans around blockers instead (A* over a visibility graph of the
  inflated blocker corners = any-angle shortest path; it serves as the "grid A*" helper and is exact).
  `sim.level.nav(34).path(start, goal)` gives the waypoints directly.
- **Conditions** see the whole state: `s.t`, `s.clock`, `s.phase`, `s.npc(name)` (`.x .y .yaw .State
  .Suspicion .bOffStage`), `s.away(name)`, `s.guards_in_zone('M1_Zone_Corridor')`, `s.cue_ready('Fly')`,
  `s.score_takeable()`, `s.is_dark_at(x, y)`, `s.player` (`.x .y .costume .has_score .gadgets`).
- **Other steps:** `wait(sec)`, `crouch()`/`stand()`, `mark(text)`, `pull(cue, wait_ready=True)`.
- **Failed actions** (out of reach, lever on cooldown, score blocked without `wait=True`, wait timeout)
  end the run as `route_error` with the reason.
- **Outcomes:** `A`, `B`, `caught` (with guard, reason and position), `curtain` (10:00 without the score),
  `route_error`, `unfinished` (route ended before an ending), `timeout`.
- **Python API:** `run_route(route, seed=..)` returns a `Result` (`.outcome .t .steps .events
  .max_suspicion .info`); `monte_carlo(build, runs=.., gd=GameData(dir, map, overrides))` returns
  `(results, stats)`. Pass `record_trace=True` to `Sim` for per-tick positions.

## What is modelled

- **Suspicion maths:** `FSVSuspicionModel` ported 1:1 (`svsim/model.py`): FillRate (wrong zone, seer, run, close
  range, changing, sneaking; distance factor `Lerp(1, FarFactor, d/range)`; busy/idle; escalation), Step/decay,
  HearingRadius/HearsSteps. Non-CSV defaults are kept from the header (FarFactor 0.35, ResumeLevel 0.12,
  FillChanging 1.0).
- **Eye component** (`USVSuspicionComponent`, 10 Hz): BuildInput (hidden in hide spot / behind screen,
  distracted, 3D distance from the eye, dark corridor, light scale, cone `dot >= cos(half angle)`, line of sight
  with the two standing traces (+65/+20 cm) or the crouched trace (+25 cm)), costume/zone check, seer (Brac's
  `SeesThrough`, or everyone after the theft), running, changing, sneaking. Footsteps behind him (not in sight,
  not distracted, hearing trace body to body; through a wall x HearWallFactor) push the eye to
  Notice + 0.05. States Schedule / Suspicious (stops, turns to her at GuardTurnToPlayer) / Return (below
  ResumeLevel) / Alarm (1.0 = caught).
- **Guard** (`ASVGuard::Tick`, `svsim/guard.py`): schedules per phase from `schedule.csv` (teleport at the
  start, non-teleport at phase changes, `<Npc>_Hunt` rows after the theft), patrol/hurry speeds, waits with
  `WaitJitter`, look-around (LookAroundDegrees at GuardLookAroundTurn, random re-targets 1.4-3 s),
  single-point NPCs (settle + FacingYaw), cue reactions (`OnCue`: go to target at HurrySpeed,
  InvestigateTime, look around x1.6, walk back at PatrolSpeed), noise investigation, gadget lure
  (distracted GadgetDistractSeconds, WaitLeft max(InvestigateTime, distract + 2)), the changing-screen catch
  (perceiving NPC within ChangeCatchDistance while she changes = caught), off-stage rows (no points).
- **Player:** walk/sneak/run speeds from the CSV, costume and zones (the smallest zone wins where zones
  overlap), hide spots (no sight, no hearing), changing screens as in `SVChangingScreen.cpp` (corner -> door
  -> hidden walk in the screen's local frame at WalkSpeed, ChangeSeconds from the door point, visible
  while stepping in, hidden afterwards, noise at the door point to guards within ChangeNoiseRadius
  (x HearWallFactor through walls)), cue levers (cooldown, Steam down darkens the box corridor for
  DarkSeconds), gadgets (count, wind-up, range, rattle delay, nearest free guard within
  GadgetHearingRadius), score rule (no undistracted perceiving guard within 450 cm with line of sight),
  10 s film (paused), alert (AlertEscalation, Hunt rows), shaft box 7 -> stage (after the theft),
  ending A (stage door with the score), ending B (desk in the finale before 8:10), 10:00 curtain (caught
  without the score, clock stops with it).
- **Geometry:** every `map.json` blocker as an axis-aligned box with its `top_z`; line of sight is a 2.5D trace
  (the trace height at the box is compared with `top_z`, so low cover hides a crouched player but not a
  standing one). The changing screens add their panel (10 x 160 x 180, blocks sight and walking) and the two
  pawn-only side blockers (walking only, off while she changes).

## Approximations (each simplification)

1. Guards move along the exact shortest path around blockers inflated by 42 cm (navmesh stand-in); speed
   ramps with MaxAcceleration 1200, but there is no braking curve, no corner slow-down and no avoidance
   between NPCs or between NPCs and the player (pawns do not block each other).
2. Path following stops when within 82 cm of the goal (acceptance 40 + capsule 42, see calibration).
3. Turning: body yaw follows the movement direction at `walk_turn_rate` 360 deg/s (WalkTurnRate is not in the
   material); facing a set direction at 90 deg/s (FacingTurnRate not in the material).
4. Heights: guard eye 160 cm, guard body 96 cm, her actor 90 cm standing / 55 cm crouched; floor flat (z = 0)
   everywhere, box 7 is not raised.
5. Her movement is instant (no acceleration); she moves exactly along the waypoints; while aiming a gadget she
   stands still (GadgetAimMoveSpeed is not used).
6. Other NPCs do not block line of sight.
7. Gadget flight time = sqrt(2 d / 980) (45 degree throw); a throw is refused if a wall >= 200 cm high is
   between her and the target or the target lies inside a blocker; the throw arc (GadgetThrowArc) and
   GadgetShowDelay are not modelled.
8. Interactions are instant (lever, score besides the paused film, hide, shaft, desk, pick-up).
9. Sim step 0.05 s for movement; perception at 10 Hz like the component.
10. Chorus1 and Stagehand1 (bPerceives false) are simulated but cannot see or hear.

## Assumptions (material gaps - please confirm or extend the material)

| # | Gap | Choice in the sim |
|---|---|---|
| 1 | Costume rule **outside every zone** (stage-door strip x 0..400, chorus station / pit x 1200..1600) | No rule there: any costume is allowed (`--outside-zone allow`). With "own clothes are wrong everywhere" (`strict`) the Pompier, teleported to (500,-1150) facing west, catches her at t ~1 s in 100 % of runs - so the game cannot work that way. |
| 2 | Overlapping zones (Backstage lies inside Stage) | The smallest zone wins (Backstage allows smock + robe behind the flats, as the spec says). |
| 3 | **Lamp positions / her light value** (ShadowSightFactor, LitLux) | No lamps in the material. Treated as a band: `--light lit` (1.0 everywhere, default) and `--light shadow` (0.5 everywhere). A callable `light=(x, y) -> scale` can be passed to `Sim`. |
| 4 | Lintels (`*_lintel_*`, `M5_Box7_Lintel`) | Door openings: passable and see-through. Ceilings (`M7_Ceiling_*`) and floors (top_z 0) ignored; prologue street (x < 0) ignored. |
| 5 | Which zone goes dark on Steam down | `M1_Zone_Corridor` only (code: `SVTags::Zone_Corridor`); box 7 stays lit. |
| 6 | Changing noise: source and investigate spot | Distance from the guard to her at the door point; the guard investigates the screen's location. |
| 7 | Gadget hearing | Straight distance to the gadget (no wall factor); "free" = `CanHearNoise()` (not Suspicious/Alarm, on stage) - so a guard on a cue can be re-targeted. |
| 8 | Ranges of interaction | Levers, score, hide spots, shaft, desk, pick-up 150 cm; screen 250 cm from the screen actor; exit 100 cm around (0,-1150). |
| 9 | Shaft exit point (20, 650) lies inside a wall | She comes out 60 cm along its yaw, at (80, 650). Transit is instant. |
| 10 | Who gets `ApplyPhase` at the theft | Every NPC (Hunt row if any, else its phase row); an NPC on a cue is sent back (`Investigate -> Return`). |
| 11 | Phase changes | Non-teleport (they walk); only the start of the evening teleports to the first point. |
| 12 | Off-stage NPCs (usher, Valcourt in the interval) and cues | They ignore cues. |
| 13 | Cue lever before its first use | Ready at t = 0 (`-svcue` pulls at 1.5 s). |
| 14 | The clock after the theft | Keeps running; it stops at 10:00 only if she has the score (rahmen: "then the clock stops"). Ending B needs clock 7:30..8:10 (490 s, a rahmen value, not in a CSV). |
| 15 | Her capsule | Radius 34 cm (UE default character), used for route collision checks. |
| 16 | HUD | Not modelled (the material has no HUD texts besides `notebook.csv` / AwayText). |

## Calibration (`python3 sim/calibrate.py --runs 30`)

Scenario A = `-svcue=Fly,SteamDown,Trap` (levers at 1.5 / 3.5 / 5.5 s), no player. The measurement was read
from `-svwindowlog` (one position per second), so +-1 s is noise.

| event | measured | sim | dev | likely cause of the deviation |
|---|---|---|---|---|
| usher leaves the corridor | ~4 | 3.1 | -0.9 | log resolution (1 s) |
| usher back (arrives at his post 1100,1050) | ~47 | 47.4 | +0.4 | - |
| usher back (re-enters the corridor at the proscenium door) | ~47 ? | 40.1 | -6.9 | definition: the measurement's "back" / "corridor empty until 47" matches arrival at his post, not the corridor entry |
| Gaspard leaves the box door | 4 | 3.5 | -0.5 | log resolution |
| Gaspard at the main valve | ~18 | 17.8 | -0.2 | - |
| Gaspard back (arrives at his post 1250,1050) | ~58 | 54.8 | -3.2 | "at the door" is ambiguous: his post is 1168 (stops 82 short), the door x 1340..1460 |
| Gaspard back in front of box 7 door (next leg) | ~58 | 59.1 | +1.1 | same ambiguity; the measurement lies between both readings |
| Valcourt leaves box 7 | 6 | 6.5 | +0.5 | the measurement is likely "starts to move" (5.5 s, log shows 6) |
| Valcourt at stage centre | 14 | 13.8 | -0.2 | - |
| Valcourt back at his chair | 63 | 63.5 | +0.5 | - |
| Brac at stage centre | 8 | 8.2 | +0.2 | - |
| Brac leaves stage centre | 20 | 20.1 | +0.1 | - |
| Brac back at the desk | 26 | 25.0 | -1.0 | log resolution / missing braking |
| box corridor empty from | ~12 | 10.8 | -1.2 | Gaspard's path along the corridor slightly short (no door-frame avoidance) |
| box corridor empty until (first NPC re-enters) | ~47 | 40.1 | -6.9 | see usher: measured value matches "until the usher is at his post" (47.4) |
| box 7 free (seconds) | ~55 | 55.6 | +0.6 | - |
| Pompier round act 1 / act 2 (wait 2.5 s) | ~28 | 27.0 / 27.3 | -1.0 / -0.7 | no braking and no corner slow-down in the sim |
| Pompier round finale (wait 2.0 s) | (~28) | 24.7 | -3.3 | the finale waits only 2.0 s (4 x 0.5 s less) - the measurement's "2.5 s per point" is acts 1/2 |
| Pompier east turn point | x ~1218 | x 1221 | +3 | - |
| Pompier south turn point | (1290,-532) | (1291,-531) | 1 cm | - |

Tuned (sim-internal only, no CSV value touched): the path-following acceptance 82 cm (= MoveTo 40 + capsule
42; the measured turn points 1218 and (1290,-532) are both exactly 82 cm before the schedule points 1300 and
(1300,-450)). The nav radius 42 fits better than 34 (34: usher back 43.4 instead of 47). Acceleration 600 vs
1200 and turn rates do not change the table by more than 0.4 s. A cue reaction delay of 0.5 s makes
Gaspard/usher "leave" times match exactly but shifts arrivals late; it stays 0 (the code reacts in the same frame).

## The intended route (`python3 sim/routes/intended.py --runs 200`)

Succeeds in 200/200 seeds (also with `--light shadow`, `--tune settle_radius=90`, `--tune nav_radius=34`):
ending A at t = 45.3 s.

| t (s) | step |
|---|---|
| 0.0-6.2 | wait at the stage door until the Pompier is > 6.5 m from screen 1 |
| 6.2-11.0 | smock at screen 1 (change starts 7.1, out 10.9) |
| 11.9 / 13.5 / 14.4 | pull Trap / SteamDown / Fly |
| 17.1-21.5 | chorus robe at screen 2 (nobody within 6.5 m; the Pompier is on his way to the Fly target) |
| 21.5-32.2 | north round the flats end, through the opening x 900..1100, west along the flats, south behind the flats (x 75) to the proscenium door |
| 32.2-38.0 | dark, empty box corridor -> box 7 -> score taken at 38.0 (26 s after the first lever; the PM estimated ~25) |
| 38.4-45.3 | shaft to the stage, north behind the flats, wings, stage door |

Observations while running it (for the balancing report):
- The usher, hurrying to the Fly target, hears her footsteps (HearWalk 200) as she walks along the flats
  and the eye jumps to 0.30 -> `Suspicious`, which **cancels his cue investigation** (he walks back to the
  corridor after 2 s). Hearing a player always aborts a cue reaction in the code.
- Single-point NPCs (Brac, Valcourt) that come back from a cue stop 82 cm short, but the settle test needs
  < 60 cm: they never sit down / face their FacingYaw again; they stand and look around their arrival
  direction (code: `bAtSinglePoint`). Brac then looks north-west instead of at his desk.
- Darkness does not matter on the intended route: the corridor is empty anyway when she passes
  (DarkSeconds 10 gives the same result).

## Files

- `svsim/data.py` - loads CSVs + map; `svsim/model.py` - suspicion maths (1:1); `svsim/geom.py` - blockers,
  2.5D line of sight, visibility-graph A*; `svsim/guard.py` - guard + eye component; `svsim/world.py` - the
  evening (clock, player, screens, cues, gadgets, score, endings); `svsim/route.py` - route steps, run,
  Monte Carlo; `svsim/runner.py`, `svsim/cli.py` - command line.
- `calibrate.py`, `run.py`, `routes/intended.py`.
