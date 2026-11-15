# Balancing harness run - night of 14./15.11.2026

An autonomous agent run tested the game's balancing overnight, while the team slept. This folder holds its report as
exported from the sandbox (`EXPORT.json`: commit, checksums, the producer's words). The request, the brief the agents
got and the CTO's notes are in [`../../glassbox/zentrale/autopilot/2026-11-14-balancing/`](../../glassbox/zentrale/autopilot/2026-11-14-balancing/).

## Why
Rene (producer, owns the balancing), 14.11. ~23:20: *"wichtig für harness welche route wird gelaufen, gibt es noch
irgendwo wege die das spiel brechen? wie ist die schwierigkeit als abschätzung? verstehen die agenten das ziel mit den
gegebenen infos?"* - which route is played, are there ways that break the game, how hard is it, do the agents understand
the goal from the material they get.

## How it ran
- **Where:** an isolated Docker sandbox ("cage" `megajam-balancing`): no game repo, no Unreal, no internet. Only the
  material: the rules with every number, 6 timings measured in the game, the intended route, the level as JSON (every
  collision box), the 5 data CSVs and the perception C++ as Markdown.
- **Who:** a Claude Opus loop, started by the CTO role after Rene's release ("Ja, mit 15/90"), 00:10-02:26.
  1 round, 10 agents incl. an independent QM, 495 tool calls.
- **Sealed beforehand:** the PM's hypothesis and expectations stayed in the request, out of the sandbox.
- **What the agents built:**
  - a 2D simulation of the game in plain Python, calibrated against the 6 in-game measurements: all 6 within 25 %,
    most within 1 s (`sim/README.md`);
  - 18 scripted routes and exploit probes (`analysis/exploits/findings.md`) and a map scan (`analysis/map-scan/findings.md`);
  - a Monte Carlo player model, 400 sessions per profile, for difficulty (`analysis/difficulty/out/summary.txt`);
  - a blind comprehension test of the notebook texts (`blind/comprehension.md`);
  - an internal review with recheck (`analysis/sim-review/review.txt`).
- **Deliverables:** [`bericht.md`](bericht.md) (German report), [`testplan.md`](testplan.md) (20 min hand test),
  [`vorschlag-balancing.csv`](vorschlag-balancing.csv) and [`vorschlag-schedule.csv`](vorschlag-schedule.csv)
  (5 ranked proposals, all inside Min/Max, data only).

## Agents and models - who did what
Source: the harness recording, not the agents' own account. The harness logs the CLI's output stream
(`round-1.jsonl`) and the totals per model (`run.json`); the CTO read them after the run (15.11.).

**The lead agent picked every sub-agent and its model itself.** Roles and models were not given in advance; the goal
was only Rene's sentence. The lead agent ran on Opus (claude-opus-5-5): 113 responses, 67 turns.

| # | Start | Task (the agent's own description) | Role | Model | Responses |
|---|---|---|---|---|---|
| 1 | 00:11 | P1 build and calibrate the simulator | general-purpose | Opus | 108 |
| 2 | 00:11 | P2 check the map statically for exploits | general-purpose | Opus | 31 |
| 3 | 00:11 | P3 blind test: does a newcomer understand the goal? | general-purpose | Sonnet | 4 |
| 4 | 00:36 | P4 search exploits and routes | general-purpose | Opus | 190 |
| 5 | 00:36 | P5 difficulty (Monte Carlo) | general-purpose | Opus | 160 |
| 6 | 00:36 | P6 check the simulator independently | general-purpose | Opus | 57 |
| 7 | 01:43 | P7 write report, proposals, test plan | general-purpose | Opus | 108 |
| 8 | 02:03 | P7 check the deliverables independently | general-purpose | Opus | 65 |
| 9 | 02:03 | QM check of the run | qm | Opus | 71 |
| 10 | 02:24 | re-check the rework | general-purpose | Sonnet | 7 |

- **Agents:** 10 in total, 8 on Opus and 2 on Sonnet. 1-3 ran in parallel from 00:11, 4-6 in parallel from 00:36. None
  started further agents.
- **Why Sonnet:** only for the unbiased blind reader (3) and a short re-check (10).
- **Usage:**
  - Opus: 686,911 output tokens; 49.3 M read from the cache, 3.0 M written to it; 38.90 USD equivalent.
  - Sonnet: 8,547 output tokens; 0.21 M cache read, 0.07 M cache write; 0.27 USD equivalent.
  - In total 39.17 USD equivalent, at the CLI's list-price calculation. What is actually paid is the subscription:
    weekly use went 20 -> 24 %.
  - 495 tool calls: 66 by the lead agent, 429 by the sub-agents.
- **Machine:** sandbox with 3 CPUs and 2 GB. Peak RAM 0.36 GB, peak CPU 299 %, 175 CPU minutes. The simulator is plain
  Python, standard library only.
- **Limits of these numbers:**
  - Responses are only a rough measure of work; the recording does not count tokens per agent.
  - The end time per agent is not recorded; the start times are exact.

## What the humans and the PM did with it (15.11. morning)
- **Five open "breaker" questions checked against the game code.** The sandbox had no character, game mode or level
  code, so it could only name these as hand tests. The PM (Claude Code in Rene's session) checked them in the code
  before Rene played. Four are not breakers, one was:
  - Own clothes outside every zone are allowed (`IsCostumeAllowedHere`).
  - The shaft is one-way in the code (the stage end can be closed). **Correction 15.11. 11:06:** the PM checked
    the code, not the level - the flags were not set there, so the shaft did work both ways (Rene found it in his
    play test). Set and read back in the level; the agents' hand test T3 was right to ask.
  - The change noise only sounds during the 3 s change.
  - Off-stage guards never block the score (`FindWatcher`).

  The hand test shrank from 20 to ~10 min. The PM's page for Rene:
  [`ergebnis-rene.md`](../../glassbox/zentrale/autopilot/2026-11-14-balancing/ergebnis-rene.md).
- **Taken over by Rene ("eintragen", 15.11. ~09:15)**, aimed at the play feel ("der frust zum ende sollte nicht
  aufkommen"):
  - `FillSeer` 0.20 -> 0.12: after the theft a short hesitation past Brac no longer ends the run. Sim: 2 s pause on the
    escape 50 % caught -> 0 %.
  - `DarkSeconds` 30 -> 45: more time in the dark box corridor, where ~35 % of first-time catches happen.
  - Notebook row 017: the chorus robe hangs at the pit wall, not behind the garden flat. The agents' blind reader found it.
  - A catch tip for the escape: "Take the shaft in box 7 and keep moving". It comes from the report's finding that
    leaving without the shaft is the costliest first-time mistake.
- **Not taken:**
  - #1 (Pompier reversed): only needed if the start were broken, and it is not.
  - #3 (Valcourt visible in the interval): not needed per the code.
  - #5 (`FillWrongZone` 0.25): it would make costumes optional for good players.
- **Hypothesis:** met on both parts. The calibration hit all 6 measured values, and Rene took over proposals. His play
  test of the result follows the same morning (`DEVLOG.md`).

## Not in this folder
- The simulation code and the raw evidence the report cites (`analysis/deliverable-check/*`, `difficulty/out/profiles.txt`,
  `mistakes.txt`, `sensitivity.txt`, `catch_hotspots.csv`, `sim-review/escape.txt`). They stay in the sandbox at commit
  `2f83c47`.
- Code is never exported from a sandbox, only its results.
