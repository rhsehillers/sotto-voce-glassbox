---
project: megajam
cage: megajam-balancing   # a NEW blank cage (the game repo is Unreal - no use in a cage)
kind: blank
mode: free
rounds: 6
minutes: 240
week_pp: 10
five_hour: 80
model: opus
max_turns: 120
size_gb: 1
cpus: 3                   # the loop builds and runs a small simulator - CPU-bound
mem_gb: 2
---
# Autopilot request - balancing (overnight run, 14./15.11.)

Written by the PM (2026-11-14 23:50). Format: `organisation/SCHNITTSTELLEN.md` section 7. The PM never starts a run:
`php autopilot.php check` -> CTO -> the user releases (A17). Second request of megajam (first: 2026-11-12-konzepte).
Submission Sunday 15.11. 22:00 (candidate 20:00); the result is needed by Sunday ~08:00.

## Goal
Rene, 14.11. ~23:20, verbatim: "werde noch ein paar mal testen und dann später noch harness starten für balancing ;
ob wir es dann nutzen oder morgen noch einmal ran müssen entscheiden wir dann, aber die nacht würde ich gern nutzen,
das harness hat oft erkennt neues gebracht ; wichtig für harness welche route wird gelaufen, gibt es noch irgendwo
wege die das spiel brechen? wie ist die schwierigkeit als abschätzung? verstehen die agenten das ziel mit den
gegebenen infos? also rein zahlen oder csv muss da etwas erweitert werden, sprich einerseits rein an zahlen
andererseits einen plan wie wir das game sinnvoll testen lassen"

## Hypotheses
H1: The run builds a simulation that matches at least 4 of the 6 measured values in `in/rahmen.md` within +-25 %
(usher back ~t 47, Gaspard back at the door ~t 58, Valcourt back ~t 63, Brac back ~t 26, box corridor empty ~35 s,
Pompier round ~28 s) AND delivers a route with times, a checked list of route-breakers (at least one concrete one OR a
checked "none"), a difficulty estimate for a first-time AND a trained player, a hand test plan of <= 20 min AND value
proposals inside Min/Max - AND Rene takes over at least one proposal (value, route OR test step) after his Sunday
morning play test.
H0: The simulation misses more than 2 of the 6 values by more than 25 %, OR a proposal lies outside Min/Max OR needs
code, OR Rene takes over nothing.
Decision rule: the PM checks the report's own calibration table against the 6 values in `rahmen.md`; Rene's take-over
counts by his words on Sunday; the loop's self-assessment does not count.

**Reported, decides nothing (PM expectations, sealed):** (1) without the trap lever nobody watches the north-west of
the stage - the chorus robe can be skipped; (2) the gadget can be picked up again - endless lures; (3) the first change
by the stage door is a first-time player's hardest step; (4) the HUD never says the stage needs the chorus robe;
(5) the way out after the theft has never been measured; (6) whether the loop asks for engine data it cannot get.

## Done when
The cage work folder holds `sim/` (with a README AND a calibration table against the 6 values), `bericht.md`
(German: route + times, route-breakers + data fixes, difficulty, does a newcomer understand the goal),
`vorschlag-balancing.csv` (+ optional `vorschlag-schedule.csv`) AND `testplan.md` - OR the run hit its limits; the
status the loop sets says which. The PM reads it read-only and gives Rene one German page on Sunday morning.

## Why autopilot
Rene asked for it in these words and wants the night used ("das harness hat oft erkennt neues gebracht"). The task is
bounded and numeric: rules, map, routes and Rene's 41 levers are all in data, the suspicion maths is pure functions,
so a 2D simulation can test routes, windows and breakers without Unreal while the team sleeps. Taste stays out: every
change is a proposal that Rene plays and decides on Sunday.

## Into the cage
- A NEW blank cage `megajam-balancing`, image `zentrale-cage:1`, Python 3 standard library only (no numpy needed), no
  database, no internet, no Unreal, no images.
- Delivered read-only: the brief with rules, measurements and the route the design intends (`rahmen.md`), the level as
  JSON (positions + collision boxes, dumped from the level 14.11.), the live CSVs and the relevant C++ as Markdown.
- NOT in: the game repo, art, audio, these sealed hypotheses, secrets, e-mail addresses OR other personal data.

## Deliver
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/rahmen.md -> team/rahmen.md
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/map.json -> level/map.json
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/data/balancing.csv -> data/balancing.csv
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/data/npcs.csv -> data/npcs.csv
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/data/schedule.csv -> data/schedule.csv
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/data/phases.csv -> data/phases.csv
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/data/notebook.csv -> data/notebook.csv
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/model/SVSuspicionModel.h.md -> model/SVSuspicionModel.h.md
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/model/SVSuspicionModel.cpp.md -> model/SVSuspicionModel.cpp.md
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/model/SVSuspicionComponent.cpp.md -> model/SVSuspicionComponent.cpp.md
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/model/SVGuard.cpp.md -> model/SVGuard.cpp.md
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/model/SVChangingScreen.cpp.md -> model/SVChangingScreen.cpp.md
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-14-balancing/in/model/SVCueValve.cpp.md -> model/SVCueValve.cpp.md

## Halt points
None - a free run, bounded by its limits. Rene decides every change after the run.

## Way back
The results stay in the cage work folder. The PM reads them read-only on Sunday morning and gives Rene one German page
(route, breakers, difficulty, the ranked proposals, the test plan). Values Rene takes over go into `Data/balancing.csv`
/ `Data/schedule.csv` of the game repo by the PM, with Rene's words, then tests + package. Nothing reaches the game by
itself; an export of files from the cage does the CTO on the PM's request (`PROZESSE.md` 9.7).

## Risks
- **Laptop memory:** the Docker VM does not fit next to Unreal on Rene's 16 GB laptop. -> No editor AND no packaged game
  during the run; Rene plays first, then releases; the CTO checks free RAM before the start.
- **5-hour window on Sunday morning:** Rene and Mehmet work early. -> 240 min cap AND stop at 80 % of the window; a
  start around 00:30 ends by ~04:30, the window resets before the team starts. The CTO times the start.
- **No engine in the cage:** a 2D model can be wrong (light, navigation, line of sight). -> calibration against the
  6 measured values is part of "done"; every proposal is a hypothesis Rene plays before it counts.
- **Anchoring:** the brief names the route the design intends. -> it is a design fact the loop needs to judge "breaks";
  the PM's suspicions about breakers stay sealed here and are not in the cage.
- **Deadline:** the result must be usable Sunday morning; changes after 20:00 are frozen for the candidate. -> ranked,
  at most ~8 proposals; data only.
