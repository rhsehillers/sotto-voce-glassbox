---
contractor: musikstudio
use: commercial
---
# Order - musik-sotto-voce

Written by the PM of megajam (2026-11-12). Format: `organisation/SCHNITTSTELLEN.md` section 9. A handover happens only
with the user's release, in both directions (user, 09.11.2026): `php auftrag.php release` hands the order over,
`php auftrag.php deliver` hands the result back - each with the user's words.

This order formalizes the brief in mailbox #188 (which replaced #187). The user's line (12.11.2026): "dem musik pm
nicht vorschreiben bpm etc, dazu hat der mehr ahnung. eher setting erklären und wofür musik also grob ... die ganze
musik wird auch musik pm übernehmen, hier wird nur übergeben."

## Goal
ALL music AND all sound for "SOTTO VOCE: The Cut", a short polished demo (5-15 min) for the Epic AI MegaJam 2026
(UE 5.8, third-person stealth like Hitman). Paris, opening night 16.11.1891, behind the stage of an opera with a
steam-driven stage machinery (light steampunk: brass, valves, steam, wood, hemp, velvet; no ghosts, no horror). A
composer, Lucienne, sneaks in disguise through the running premiere to take back the score the Maestro stole from her.
Mood: tension behind the curtain while the opera plays on, festive, in front; elegant, not creepy; release at the
end. "Audio" is one of the seven jury criteria. Story, characters AND the game flow: material `spec.md` (sections 3,
3a, 4, 5); section 6 there says only that music AND sound are yours.

## Scope
What the game needs, roughly - form, number of pieces, lengths AND variants are the contractor's call:
- Title / menu
- Short intro (about 10 s: her name on the score is struck out)
- Play before the theft: the opera runs (muffled behind walls, fuller on the stage) under the sneaking; an opera clock
  with 4 phases (act 1, interval, act 2 with chorus, finale) and a theatre bell between them
- Being spotted / alarm
- After the theft: escape, more tense
- Short moments: distraction landed, spotted, score taken, act change, failed ("Curtain")
- Ending A (quiet exit into the night) AND ending B ("Final Cut": the orchestra plays her struck coda)
- Sounds: steam machinery (valves, winches, a stage trap), a falling sandbag, steps on wood, costumes, hiding in
  costume racks, a small wind-up gadget that makes noise, portfolio AND paper, doors, the fire watch's whistle, the
  audience behind walls; ambience for the stage AND the box
- Later: a 45 s trailer track

## Specs
Decided by the contractor (user, 12.11.: no technical prescriptions). The only frame: Unreal Engine 5.8. Please
deliver with the files a table "event -> file" (loop yes/no) as proposed in #180, so the game loads the delivery as
data AND a rework is a file swap.

## Material
- ~/projects/game/megajam/docs/spec/mvp-sotto-voce.md -> spec.md

## Done when
René has heard every piece AND sound in the game AND accepted it. Timing (the contractor's own advice in #180):
sketches on Fri 13.11., all final on Sat 14.11.; Sunday only integration AND the trailer. Submission is Sun 15.11.
22:00. Early audible material by Fri noon helps (merges at 13:00 AND 19:00).

## Rights
Commercial use (the jam pays prize money). AI tools are allowed in the jam. Before the delivery the contractor names
every tool, model OR source per file AND its licence, so megajam can list everything in ASSETS.md. No paid tools
without René's Go.

## Way back
The PM of megajam copies the delivery into the game repo (Diversion), Claude in René's session integrates it in UE 5.8
from the event -> file table (placeholder beeps until then), AND René judges it in the game: `accept` OR `rework`
with his words.
