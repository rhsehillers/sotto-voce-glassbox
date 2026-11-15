# Map scan findings (P2, static: map.json + CSV + C++; no sim)

Saved by the PM from the agent's report (the harness blocked the agent from writing .md). Evidence: `geometry.txt`,
`coverage.txt`, scripts in this folder. Assumptions: player radius 35, guard 42 (SVGuard.cpp:29); "lintel" boxes are
walk-under beams; only blockers >= 150 cm hide a standing player; coverage = upper bound (no lamps, cues, darkness).

## BREAKS
- **B1 Zones do not cover the wings.** `M1_Zone_Wings` spans only x 400..1200, y -1400..-800; 76 of 284 m2 walkable has
  no zone: start (250,-1150), smock rack (150,-1330), screen 1, stage door exit, chorus rack (1550,-1010), screen 2 + exit
  point (1430,-735), pit strip x 1210..1580 (Pompier south leg, desk (1330,-90)), proscenium passage. "No zone" = allowed
  -> own clothes free pass (incl. ending B); = not allowed -> smock wrong at its own rack, robe wrong 130 cm from the
  Pompier path. Sure (gap); consequence needs code. Fix: map note - Wings to x 0..1600, plus a pit zone.
- **B2 Possible restart loop at the stage door.** Pompier Act1 first point (500,-1150), 250 cm before the start, spawns
  facing west (yaw 180); teleport keeps rotation + 2.5 s wait (SVGuard.cpp:195-206), ResetForRestart keeps rotation.
  Own clothes fill 0.5x0.86x1.5 = 0.65/s -> caught in ~1.5 s. Needs in-game check (`-svnotitle`, restart near start).
  Data fix: `Pompier_Act1` points `1300 -450;1300 -1150;500 -1150;1300 -1150` (start 1262 cm away > 1200 range).
- **B3 Shaft before the theft skips the corridor** if it works then: stage end (20,650) never seen. Wings -> stage strip
  -> shaft -> box 7, only Trap/gadget needed. Shaft code not in material. Check `-svpos=60,650,0`, E before theft. Code fix.
- **B4 Stepping out of the screen may be "heard" by every guard.** Behind screen BuildInput Distance=0
  (SVSuspicionComponent.cpp:126-129); hearing excludes hide spots, not the screen (195-196); errands dropped while
  Suspicious (SVGuard.cpp:293). Needs SVCharacter + `-svwindowlog`. Code fix.
- **B5 The Interval may never yield the score.** Valcourt has no Interval points -> hidden in place, 99 cm from the score
  (SVGuard.cpp:182-190); if the score rule does not skip hidden guards, the interval reward fails. Check `-svclock=160`.

## STRONG
- **S1 Flats are not a gate:** gap x 1210..1579 at y -800 into the pit, 200 cm pit rail gap (x 1200, y -100..100) onto
  the stage; with all three flats openings blocked, stage/corridor/box 7 stay reachable. Sure. Map note.
- **S2 Stage nearly unwatched in the acts, robe optional:** Brac faces west (180), sees 0.8 m2 of wall; only the Pompier
  glances from (1300,-450) at 7-12 m. Levers have no costume check (SVCueValve.cpp:24-27). Likely. Data: `Brac_*`
  FacingYaw 180 -> 0, or a two-point route.
- **S3 Valcourt blind in his chair** (yaw -30, 0.8 m2 toward balustrade); box 7 inside never seen; after theft box 7 is a
  safe room. Sure. Data: `Valcourt_*` FacingYaw -30 -> -120.
- **S4 Gadget makes the score takeable next to the guard:** distracted guards ignored by the score rule; gadget at
  ~(1300,1400) lures Valcourt 158 cm, stares 4 s (SVGuard.cpp:550-556); same on Gaspard in the interval; pickup = unlimited.
  Data: `GadgetDistractSeconds` 4 -> 2, `GadgetHearingRadius` 1500 -> 800.
- **S5 Re-pulling a lever resets the guard's timer** (OnCue restarts InvestigateTime mid-errand, SVGuard.cpp:286-302,
  545-549); cooldown 20 < Valcourt 30 s; darkness chainable; WingsRack hide spot between two levers. Likely.
  Data: `CueCooldown` -> 35, `DarkSeconds` -> 25.
- **S6 `SuspiciousLevel` is read but never used:** guards go Suspicious at NoticeLevel 0.25
  (SVSuspicionComponent.cpp:207), only stop and stare; a glimpse cancels a lure; ~1.2 s out of sight sends him back.
  Sure. NoticeLevel is the real lever.
- **S7 Hide spots / screens reset any stare instantly**, no "saw her hide" rule. Likely. Data: `Decay` 0.15 -> 0.08.
- **S8 Notebook points to the wrong robe place:** row 017 "Behind the garden flat" (190,-350); rack at (1550,-1010). Sure.
  Fix text: "East end of the wings, by the auditorium wall."
- **S9 Escape shaft lands by the usher's hunt post:** 112 cm from `Usher_Hunt` (120,700). Likely. Data: point -> `300 700`.

## MINOR
- M1 Change catch is 2D distance only, no LOS/walls (SVGuard.cpp:462-471); screen 1 start (415,-1310) 182 cm from the
  Pompier's west point; chorus screen 220-245 cm from his path. Keep ChangeCatchDistance <= 200.
- M2 Stage (Chorus) and Backstage (Worker, Chorus) overlap x 0..300, y -800..140 incl. Brac's desk; precedence unknown.
- M3 Phase change during an errand: guard still walks to the cue spot; hidden guards keep errand state (Valcourt lured at
  2:29 reappears on stage at 4:30).
- M4 Hunt routes may start only at the next phase change; Brac and Valcourt have no Hunt rows.
- M5 Low cover (pit rail, crates) counts as wall for hearing.
- M6 Shaft ends overlap walls: (20,650) inside `Putz_Rueck4`; (1300,1580) 10 cm from the box 7 wall.
- M7 Fly lever on the winch block; closest stand ~94 cm.
- M8 Hide spots overlap walls (WingsRack 19 cm from pipe, CorridorCurtain 13 cm from wall).
- M9 Schedule points closer than 42 cm to blockers: `Chorus1_Act2` (150,-600) -> (150,-540); `Gaspard_Hunt` (660,600) -> (660,640).
- M10 Seen stepping behind the screen gives a 0.3-0.6 stare, not a catch.
- M11 `DarkSightRange` Max 800 > Valcourt's 700 range; keep <= 700.
- M12 phases.csv bCheckpoint=True on all phases vs. "no checkpoints".
- M13 Brac's desk wedge blocks the backstage strip while he is at the desk.
- M14 A lever pulled in a guard's sight is ignored by him while Suspicious.
- M15 16 balancing values read by no code shown (Gadget*, ChangeSeconds, ChangeNoiseRadius, speeds, AlertEscalation,
  ShadowSightFactor, LitLux).

## Coverage
Acts: 66.6 of 282 m2 never seen (smock rack, flats opening 3, SW stage, backstage strip, proscenium door, box 7 inside).
Interval: corridor never seen. Hunt: 12.9 m2 never seen.

## Needs sim or in-game check
B1 consequence, B2, B3, B4, B5, S2, S3, S4, S5, S7, S9, M3, M6, M7, M8, M10.

## Material gaps
Code: SVCharacter (costume/zone rule, IsBehindScreen, sight scale), gadget, score rule, shaft, GameMode restart/
checkpoints, ClockSubsystem (phase apply, teleport, Hunt switch), darkness, hide spots, change noise, AlertEscalation
wiring. Map/engine: blocker bottom heights (lintels), door states, lamp positions/brightness, navmesh, capsule/crouch
size, interaction ranges, trigger sizes, guard eye height.
