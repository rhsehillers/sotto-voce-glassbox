# Glass Box - how this game was planned, decided and built with AI

Team Produktlicht (2 humans, no game-dev experience) built *Sotto Voce: The Cut* for the 2026 Epic AI MegaJam with
several Claude instances, each in its own role ("departments"). This folder holds the **planning and decision
record**. The build itself is told in [`DEVLOG.md`](../../DEVLOG.md) (append-only, three authors), pre-jam work is
declared in [`DECLARATIONS.md`](../../DECLARATIONS.md), every third-party / AI asset with its licence is in
[`ASSETS.md`](../../ASSETS.md), the commit history is part of the evidence.

## The departments

| Department | Who | Where its work lives |
|---|---|---|
| Producers | Rene (code side), Mehmet (art + story side) | decisions, play tests, acceptances - quoted verbatim in the files |
| Project PM + code | Claude Code in Rene's session ("Zentrale PM" of the project, writes all C++) | `zentrale/` (this folder), `Source/`, `Tools/Editor/`, `Data/` |
| Art, story, film | Claude Code in Mehmet's session (+ Codex / GPT image, Tripo, Higgsfield, Rodin) | `artwork/`, `film/`, `Content/Art/`; AI table: [`art-side.md`](art-side.md); every tool and program: [`../abgabe/TOOLS_USED.md`](../abgabe/TOOLS_USED.md), credits and tokens used: [`../abgabe/VERBRAUCH_CREDITS_TOKENS.md`](../abgabe/VERBRAUCH_CREDITS_TOKENS.md) |
| Music + sound | Music PM (Claude, "musikstudio" project), via a formal order | `docs/audio/`, `zentrale/auftraege/` |
| Stage floor (kept by Rene 13.11.; final design call: Mehmet) | Rene's image instance "engram image" (lab stage, outside the Zentrale), an external order handed over by Rene; built the floor from zero in Python - every board a computed cut through a computed pine log, no image AI, no photos (the image KB's idea: graphics rebuilt from zero, as Engram does for knowledge) - and logged its steps; kept here if Rene and Mehmet like it in the game | brief `docs/spec/brief-buehnenboden.md`, files + its step log `artwork/materialien/buehnenboden/` |
| Harness / CTO | autonomous agent runs in a sandbox ("cage"), coordinated by the CTO role | `zentrale/autopilot/`, `../harness/` |

## What is in `zentrale/` (snapshot of the PM's project folder, 2026-11-12 evening)

| File | What it is |
|---|---|
| `decisions.md` | Decision log: open and decided questions, with the producers' words (D5 concept, D6 spec accepted, ...) |
| `memory.md` | The PM's running memory: facts and lessons, written as the project went (raw, unpolished) |
| `roadmap/` | The pre-jam plan (09.11.) and the jam schedule with budget, night runs and the laptop checklist (12.11.) |
| `konzepte/` | Concept round 1 (three drafts + recommendation, pre-jam - see DECLARATIONS) and the round-2 overview |
| `autopilot/2026-11-12-konzepte/` | The harness request for concept round 2: the request, the brief given to the agents (`in/`), the CTO's notes, the automatic pre-flight check. Results: `../harness/2026-11-12-konzepte/` |
| `autopilot/2026-11-14-balancing/` | The overnight balancing harness (15.11. 00:10-02:26): request with the sealed hypothesis, the brief (`in/rahmen.md`; the CSVs, level JSON and C++ excerpts it also got are copies of `Data/`, the level and `Source/`), the CTO's notes, the pre-flight check, and the PM's morning page for Rene (`ergebnis-rene.md`). Results and what was taken over: `../harness/2026-11-15-balancing/README.md` |
| `auftraege/2026-11-12-musik-sotto-voce/` | The music order to the Music PM (context, not technique - see memory "music is fully handed over") |
| `laws.md`, `competences.md` | The rules the PM works under and what it may decide alone |
| `checkliste-vorbereitung.md`, `insights.md` | Preparation checklist; insight candidates for the knowledge base |

**Left out on purpose:** e-mail addresses (replaced by `<e-mail removed>`), the account onboarding for the second
machine, the run release record, tool/config files and the hook logs of every brief and report (kept in the
Zentrale, can be exported at the end). The audio deliveries are not duplicated - they are in `docs/audio/`.

**This is a snapshot.** It is refreshed at the end of the jam together with the department reports. The balancing
request (`autopilot/2026-11-14-balancing/`) was added on 15.11. morning, right after its run.
