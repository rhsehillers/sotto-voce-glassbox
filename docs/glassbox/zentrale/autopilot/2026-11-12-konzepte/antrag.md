---
project: megajam
cage: megajam-konzepte
kind: blank
mode: free
rounds: 4
minutes: 120
week_pp: 6
five_hour: 60
model: opus
max_turns: 50
size_gb: 1
---
# Autopilot request - konzepte (concept round 2, free)

Written by the PM (2026-11-12, 08:40). Format: `organisation/SCHNITTSTELLEN.md` section 7. The PM never starts a run:
`php autopilot.php check` -> CTO -> the user releases (A17). First request of megajam; megajam has no cage yet.
The jam build window is open (since 2026-11-12 06:00 CET, deadline 2026-11-16 02:59 CET), so time matters.

## Goal
Konzepte für unser Spiel im Epic AI MegaJam 2026 entwerfen lassen, mit Story und Vorschlägen zur Stilrichtung. Hier
sollen ruhig mehrere Agenten unabhängig arbeiten. Engram nutzen: Psychologie und Marketing sowie Audio-Psychologie etc.
Die Atmosphäre wird nicht nur durch Musik, sondern auch durch Bild und Video erzeugt. Die Hochzeit zwischen Bild und
Ton, wo wir mehr unabhängig arbeiten, ist auch noch eine Herausforderung, daher eher „tricksen“ wie die Profis, damit
das Ergebnis gut wird. Zu realistisch ist gefährlich, da es dann auffällt, wenn Fehler sind - bisschen Fantasy oder
Future rein. Wir haben Konkurrenz und müssen liefern.

## Hypotheses
H1: One free run with several independent agents delivers at least 3 complete concepts (core loop, concrete era AND place, story hook, style direction) whose core loops fall into at least 3 different families of the sealed list below, with music as the core mechanic in at most one of them, AND René plus the colleague choose one of them (alone OR mixed with Sotto Voce) as the concept they build.
H0: Fewer than 3 complete concepts, OR fewer than 3 families, OR music as the core mechanic in 2 or more concepts, OR the team builds round-1 Sotto Voce unchanged OR a concept from outside the run.
Decision rule: the PM sorts every concept by its core loop (the main repeated player action) into exactly one family of the sealed list BEFORE showing the team; a concept counts only with all four parts present; the team's choice after reading decides the second half; the loop's own ranking AND self-assessment do not count.

Sealed families (fixed 2026-11-12, before the run): (1) movement/physics, (2) sneaking/perception (see AND be
seen), (3) disguise/social deception (blending in, playing a role), (4) choices/consequences (dialogue, branching),
(5) building/arranging/staging, (6) timing/rhythm/music, (7) combat/evasion, (8) exploring/collecting.

**Reported, decides nothing (PM expectations, sealed):** at least one concept takes the film/director frame
literally for the theme; the looks lean stylized OR fantasy/future as asked; whether the agents really worked
independently (separate drafts that differ); Engram use (searches, strong hits, gaps noted).

## Done when
For the PM, the CTO AND the user (free mode: not a checklist in the cage). The run ends at its limits (120 min,
4 rounds, +6 pp week, 60 % of the 5-hour window, 1 GB) OR when the loop judges the task done. Then the work folder
holds concept documents in German - each with a core loop AND where the variety comes from, a concrete era AND place,
story AND characters, a style direction for look AND sound including how image AND sound are made to fit while they
are produced separately, the split between René AND the colleague, the biggest risk AND a cut plan - plus the loop's
own overview of them AND the Engram nodes it used. The PM then sorts them by the sealed families, writes the team a
short German overview, the team picks, AND the PM locks the MVP.

## Why autopilot
The user asked for it in these words: a harness via the CTO where several agents work independently, with Engram.
Concept work is text only, bounded AND needs no Unreal. Round 1 (11.11., in-session subagents) showed that a frame
written by the PM narrows the result: all three concepts got the same mechanic from the brief. A free loop with only
the user's words AND the team's material is the counter-test. Taste is the team's AND is judged after the run.

## Into the cage
- A NEW blank cage `megajam-konzepte` with the FREE kickoff (the sentence AND the walls only); image default
  `zentrale-cage:1`; suggested work folder `~/projects/game/megajam-konzepte`. No database, no libraries.
- Engram read-only. Agents with the shell (rules of 07.11.2026). No internet, no Unreal, no image generation: the
  output is Markdown.
- Delivered (read-only): the jam facts AND the team's fences (`team/rahmen.md`), the team's wishes AND their verbatim
  feedback on round 1 with a three-line summary per round-1 concept (`team/wuensche-und-feedback.md`).
- NOT in: the full round-1 concept documents AND the PM's recommendation `konzepte/EMPFEHLUNG.md` (they anchor on the
  rejected mechanic), these sealed hypotheses, the game repo, secrets, e-mail addresses OR other personal data.

## Deliver
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-12-konzepte/in/rahmen.md -> team/rahmen.md
- C:/laragon/www/zentrale/projects/megajam/autopilot/2026-11-12-konzepte/in/wuensche-und-feedback.md -> team/wuensche-und-feedback.md

## Halt points
None - a free run, bounded by its limits. The team's choice comes after the run.

## Way back
The concept documents stay in the cage work folder. The PM reads them (read-only) AND brings the team a short German
overview. Into the Zentrale project (`konzepte/runde-2/`) they come as a PM package with the user's yes; the export
from the cage does the CTO on the PM's request (`PROZESSE.md` 9.7). Nothing goes into the game repo by itself: the
chosen concept becomes an MVP spec that the PM writes with the team.

## Risks
- **Time:** day 1 of about 3.5 build days; the concept decision moves to midday. -> 120 min cap, 4 rounds; the team
  works on concept-independent things meanwhile (packaging test, AI asset pipeline test, dev log).
- **5-hour window:** shared with René's own build sessions on day 1. -> the run stops at 60 % (not 80); opus only
  because this one decision steers the whole jam; the CTO times the start.
- **Laptop memory:** the Docker VM does not fit next to the Unreal editor on René's 16 GB laptop. -> Unreal stays
  closed on the laptop during the run; the colleague's machine is not affected.
- **Anchoring:** Sotto Voce got the best feedback AND is summarized in the material. -> only the team's own words AND
  a short summary go in; the round-1 mechanic is marked as rejected; the full documents stay out.
- **Engram gaps (PM search 2026-11-12):** game-design psychology (flow, suspense, pacing), image-sound fit in film AND
  games, AND the uncanny valley have no nodes - 3 gaps noted locally in the outbox. Present: marketing (positioning,
  AIDA, value proposition, visual hierarchy) AND music/consumer psychology (familiarity, mere exposure, Berlyne's
  arousal curve, appraisal). -> the loop uses its own knowledge where Engram is empty AND says so.
- **Text only:** no images in the cage. -> style directions as words AND references; the colleague makes mood boards
  with his own AI image tools afterwards.
- **Too much to read:** many long documents cost the team time on day 1. -> the PM condenses them into one German
  page for the team.
