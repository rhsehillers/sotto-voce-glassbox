# Brief - balancing run for "Sotto Voce: The Cut" (team Produktlicht, Epic AI MegaJam 2026)

Written by the megajam PM, 14.11.2026 23:50. Submission: Sunday 15.11. 22:00 (candidate 20:00). Your report is read by
Rene (producer, balancing owner) on Sunday morning. Write the report in German; code and data stay English.

## The goal in Rene's words
> "harness starten für balancing ... das harness hat oft erkennt neues gebracht ; wichtig für harness welche route wird
> gelaufen, gibt es noch irgendwo wege die das spiel brechen? wie ist die schwierigkeit als abschätzung? verstehen die
> agenten das ziel mit den gegebenen infos? ... einerseits rein an zahlen andererseits einen plan wie wir das game
> sinnvoll testen lassen"

So: (1) which route a player walks, (2) ways that break the game, (3) how hard it is, (4) whether a first-time player
understands the goal from what the game shows, (5) numbers, (6) a plan for how Rene tests it by hand.

## The game in one paragraph
Paris opera, 1891, one evening of 10 minutes on the opera clock. Lucienne, a composer, sneaks in through the stage door
to steal back her own score from the Maestro Valcourt in box 7. Social stealth: costumes let her blend in where their
people belong; guards fill an "eye" meter when they see something wrong; a full eye = caught = the evening starts over
at 0:00 (no checkpoints, a deliberate demo rule). Three levers in the wings ("cues") move the whole house and open
windows. Two endings: out through the stage door with the score (A), or the score on the conductor's desk in the
finale (B). The jury plays it once, maybe 10-15 minutes.

## What you get (`in/`)
- `map.json` - every collision box (`blockers`), zones with the costumes they allow, stations (racks + screens),
  cue levers with their target points, hide spots, NPC spawn points, exits, the score. Units cm. The box corridor
  (y ~ 900-1200) and box 7 (x 1200-1600, y 1200-1600) are in it too.
- `data/` - the live CSVs: `balancing.csv` (Rene's 41 levers, each with Min/Max), `npcs.csv` (per guard: sight range,
  cone, what he sees through, which cue he reacts to, InvestigateTime), `schedule.csv` (routes per phase, waits),
  `phases.csv` (the clock), `notebook.csv` (what the player reads on Tab).
- `model/*.md` - the real C++ in Markdown: suspicion maths (`SVSuspicionModel.*` - pure functions, port them 1:1), the guard
  (`SVGuard.cpp`: patrol, cue reaction, investigate, hunt), the eye component, the changing screen, the cue lever.

You have NO Unreal. Build your own small 2D simulation from this material (Python, standard library is enough) and
calibrate it against the measurements below before you trust it.

## Rules (short - the code is the truth)
- **Her speeds:** walk 300, sneak 160 (crouch), run 550 cm/s (fixed). Running in sight fills fast; footsteps are heard
  behind a guard: sneak 80, walk 200, run 1000 cm (through walls x HearWallFactor 0.4).
- **Costumes / zones:** own clothes belong nowhere. Wings + behind the flats: smock (Worker) or chorus robe. Stage:
  chorus robe only. Box corridor and box 7: nobody's costume - there only not being seen helps (darkness, lures, timing).
  Wrong zone in sight -> FillWrongZone 0.5/s. Brac sees through BOTH costumes within SeerRange 400 (FillSeer 0.2/s).
- **Sight:** per guard range + cone (`npcs.csv`), line of sight; dark corridor (Steam down) -> range DarkSightRange 500;
  shadows shorten sight further (her light value: ShadowSightFactor 0.5 at < LitLux 20 lux - approximate with the
  lamp positions you can infer, or treat as a +-band). Fill x distance factor x attention (busy 0.5 / idle 1.5) x
  escalation (1.5 after the score is taken). Decay 0.15/s when nothing is seen. Notice 0.25, suspicious 0.6 (he comes to
  look), 1.0 = caught. Inside CloseRange 160 any costume fills 0.15/s (personal space).
- **Changing:** 3 s behind a screen (+ ~2 s walking round it). Unseen while behind it, but guards within
  ChangeNoiseRadius 600 (walls x 0.4) hear it and come to look; one within ChangeCatchDistance 200 while she is still
  behind it = caught; being SEEN stepping in = caught almost at once.
- **Cues (levers, `map.json` cues):** Fly -> usher + Pompier go to (700, -870); Steam down -> the box corridor goes dark
  for DarkSeconds 30 and Gaspard goes to the main valve (760, -1290) in the wings; Trap -> Valcourt + Brac go to the trap
  (600, 0) in the middle of the stage. Each looks for InvestigateTime (npcs.csv) and walks back. A lever works again after
  CueCooldown 20 s.
- **Gadget:** 2 at the start, thrown up to 600 cm, rattles once after 1 s; the nearest free guard within 1500 comes and
  stares 4 s (sees and hears nothing meanwhile); it can be picked up again.
- **Hide spots:** break every line of sight while inside.
- **Clock:** Act 1 0:00-2:30, Interval 2:30-4:30 (Valcourt in the foyer, routes change), Act 2 4:30-7:30, Finale
  7:30-10:00; 10:00 = final curtain = caught unless she has the score (then the clock stops, she still has to get out).
- **Score:** takeable when no undistracted guard within 450 cm has line of sight to it. Then a 10 s film (paused), the
  house goes on alert (escalation 1.5, "Hunt" routes), the music changes.
- **Endings:** A = reach the stage door exit (0, -1150) with the score. B = put the score on the conductor's desk
  (1330, -90) in the finale before 8:10.
- **Shaft:** box 7 -> stage, escape only (usable after the theft).

## Measured in the game (14.11., editor build) - calibrate against these
- All three levers pulled 2 s apart from t = 1.5 s, no player: usher leaves the corridor ~t 4, back ~t 47; Gaspard leaves
  the box door t 4, at the main valve ~t 18, back at the door ~t 58; Valcourt leaves box 7 t 6, at stage centre t 14,
  back t 63; Brac at stage centre t 8-20, back at the desk t 26. Box corridor empty ~t 12-47; box 7 free ~55 s.
- Pompier, acts 1/2/finale: L from (500, -1150) east to x ~1218, then south to (1290, -532) by the music stands and back;
  one round ~28 s incl. waits (2.5 s per point +-15 %).
- PM estimate before the station move: from the levers to the score ~25 s for a player who knows the way.

## The route the design intends (find better or worse ones)
1. Stage door -> smock rack + screen 1 by the door; change while the Pompier walks away east (he must be > 6 m away).
2. As a stagehand pull the levers (order matters - find the best one).
3. East to the chorus station at the end of the L (rack (1550, -1010), screen (1490, -860)), change into the robe -
   timed against the Pompier (he turns at x ~1218 / y -532) and Gaspard at the main valve (760, -1290).
4. Through a flats opening onto the stage, across it to the proscenium door (120, 826) - Valcourt and Brac stand at the
   trap (600, 0) after the trap lever: the robe lets her pass, Brac sees through it within 4 m.
5. Box corridor (dark after Steam down, usher away after Fly) -> box 7 door (1400, 1164) -> score (1520, 1520).
6. Escape (alert): shaft box 7 -> stage, then out through the wings to the stage door; or ending B in the finale.
The interval is meant as the "reward for watching" (Valcourt away, one lever is enough).

## What Rene can use most (in your work folder)
1. `sim/` - your simulation + a README how to run it, and how well it matches the measurements above.
2. `bericht.md` (German, for Rene, short):
   - die Route(n) mit Zeiten, Schritt für Schritt, und welche Fenster sie braucht;
   - Wege, die das Spiel brechen (mit Koordinaten) und je eine Abhilfe - zuerst über Daten (CSV), Code nur als Notiz;
   - Schwierigkeit: wie oft wird ein Neuling erwischt, bis er es schafft, und wie lange braucht er; dasselbe für
     einen geübten Spieler; ist das für eine Jury mit 10-15 Minuten richtig?
   - versteht ein Neuling das Ziel aus HUD-Zielen, Notizbuch (`notebook.csv`) und Tipps? Was fehlt?
3. `vorschlag-balancing.csv` - only rows you change, columns `Name,Old,New,Why`; New inside Min/Max. Route or wait
   changes for `schedule.csv` as a separate `vorschlag-schedule.csv`. At most ~8 changes, ranked.
4. `testplan.md` (German) - a hand test for Rene, at most 20 minutes, in the packaged game: what to play, what to watch,
   what counts as pass/fail. The development package accepts test switches, e.g. `-svnotitle` (straight into act 1),
   `-svcue=Fly,SteamDown,Trap` (levers at 1.5/3.5/5.5 s), `-svwindowlog` (guard positions every second in the log),
   `-svpos=x,y,yaw` (put her somewhere), `-svclock=N` (clock to N s), `-svscore` (score taken at 3 s).

## Walls
Do not change Min/Max, art, code or the map; no balancing value outside its range; Rene decides every change.
