# Roadmap - 2026 Epic AI MegaJam participation (v0.1, 2026-11-09)

**Status:** DRAFT - waiting on the user for team skills, available time AND the engine decision.
**Owner:** PM (megajam). **Team name (submission):** Produktlicht.
**Team:** 2 humans, full-time during the jam (vacation + home office), going all in.
- User: programming, code AND logic, project organization; has a DAW for audio. Background: web/js dev; NO games built before.
- Friend: art/graphics AND design (years of experience, on par with the user's programming depth); more experience with Suno (AI music).
- Both: strong in their field, but NO game-dev experience, NO Unreal/UEFN experience, no prior game jam.
**Goal:** WIN - and the entry doubles as a reference for the team's joint project "Produktlicht".
**Max AI:** the team agrees the direction together, then hands tasks to AI; the Claude Code harness is to be used to the maximum to ship in the short window.
**Project theme:** maximum AI use.

## Goal
Enter the 2026 Epic AI MegaJam as a 2-person team AND submit a finished, playable game before the deadline, using AI as heavily as the jam allows. The jam itself is AI-themed with $50k+ in prizes, SO a heavy-AI entry fits its spirit AND can be a differentiator.

## The hard constraint: timing (today is 2026-11-09; all times CET) - CONFIRMED on the itch page
- Nov 11, 20:00 CET: kickoff livestream + theme reveal. Building is NOT allowed before Nov 12.
- Nov 12, 06:00 CET -> Nov 15: build window (~4 days).
- Nov 16, 02:59 CET (= Nov 15, 17:59 PST): submission deadline. Late = disqualified.
- Winners announced by Jan 29, 2027.
- => Prep window is NOW: Nov 9-11 (~2 days). Pre-jam tool/agent/MCP setup is explicitly allowed. This is where a "max AI" team wins or loses.

(Facts + sources: see `memory.md`.)

## Prize strategy (how we actually aim to win)
Multiple shots, not just "Best Overall":
- **Best Team** ($5k) - best game by a 2+ team -> we qualify by default.
- **Glass Box** ($2.5k) - best dev log of HOW you built it -> perfect for our max-AI/MCP angle. KEEP A DEV LOG FROM DAY 1.
- **Render Royalty** ($2.5k) - best visuals -> the friend's art strength.
- plus **Best Overall UE** ($7.5k first) as the stretch.
Judges score 1-5 on: ambition/innovation, theme, fun, gameplay, visuals, level design/progression, audio.

## Phases AND hold points
### Phase 0 - Prep (Nov 9-11) [the critical phase]
- [USER, G1] Register on itch.io for the jam; create/confirm itch.io + Epic accounts.
- [USER, G1] Read the Official Rules + the itch page; confirm deadline/timezone, eligibility (country/age), asset/IP rules, build platform.
- [DECISION D1] Engine: Unreal Engine vs UEFN (see "Open decisions").
- [TEAM] Install the chosen engine; verify a blank project packages/builds end-to-end (UE: Windows build zip; UEFN: publish a private version).
- [TEAM + PM] Stand up the AI toolchain (see "Max-AI toolchain"); set up Unreal MCP so an AI agent can drive the editor. DECLARE everything built pre-jam.
- [TEAM] Dry run: make a trivial change via the AI toolchain AND produce a valid submission build, SO the pipeline is proven before the clock starts.
- **HOLD POINT:** user releases the engine + toolchain before Nov 11.

### Phase 1 - Concept (Nov 11, after the theme reveal)
- Watch the kickoff; capture the theme.
- [PM + TEAM] Ideate 3-5 concepts (AI-assisted); pick ONE that fits the theme, the 4-day scope AND plays to "max AI". Lock a tiny MVP + stretch goals.
- Define the vertical slice: one core loop, one level, a win/lose state.
- **HOLD POINT:** user picks the concept + MVP scope.

### Phase 2 - Build (Nov 12-15)
- Day 1: core loop playable (greybox). Day 2: content + an art/audio pass (AI-generated). Day 3: polish, difficulty, bugs. Day 4 (half): freeze, package, record the 30-60s video, submit early.
- Every day ends on a packaged build that runs. Never leave packaging to the last hour.
- **HOLD POINT (daily check-in):** scope still fits the time left; cut features early.

### Phase 3 - Submit (Nov 15)
- [USER, G1] Upload the build to itch + submit to the jam; attach the gameplay video; fill in team/members/emails.
- Submit with a buffer (hours, not minutes).

## Open decisions (need the user)
- **D1 Engine:** PM RECOMMENDATION = **Unreal Engine** (not UEFN). Reasons: (1) max-AI-via-harness - UE gameplay can live in C++ (text files Claude writes/compiles/iterates) + Unreal MCP lets an agent drive the editor; UEFN needs Verse (niche language, far less AI training data) AND MCP support there is unclear; (2) originality ceiling + reference value for "Produktlicht" is higher than Fortnite-bound UEFN; (3) plays to the user's programming strength. RISK: no game-dev experience + steep UE curve + only 4 days. DE-RISK: a Phase-0 spike (install UE, get Unreal MCP + Claude working, package a trivial Windows build); if the pipeline is shaky by Nov 11, pivot to UEFN. When UEFN would win instead: if "fastest path to something playable in a possibly less-crowded category" beats originality + max-AI-code. STATUS: **DECIDED 2026-11-09 = Unreal Engine** (user). Pivot to UEFN only if the UE pipeline is unworkable by Nov 11.
- **D2 Scope:** ambition vs the 4-day window and the team's real available hours.
- **D3 "Max AI" reach:** which parts are AI-driven (code/Blueprint/Verse, 2D art, 3D, audio/music, design, QA) vs human.

## User steps (G1 - the user does these, not the PM)
- itch.io + Epic account; jam registration; reading/accepting the rules; anything that costs money; the final submission.

## Max-AI toolchain (confirmed 2026-11-09; UE path - sources in memory.md)
Prioritized Phase-0 setup order (times are rough estimates):
1. Start the big downloads FIRST (tens of GB): **UE 5.8.1+** via the Epic Launcher + **Visual Studio 2026** with the "Desktop development with C++" and "Game development with C++" workloads. (1-3h wait)
2. Create a **C++** template project, build it, and package a trivial **Windows build** once, end to end. (1-2h)
3. Enable **Unreal MCP** (+ All Toolsets + Toolset Registry + EditorToolSet), generate `.mcp.json`, launch **Claude Code** from the project root, run a spawn + Play test. **Claude Code is an officially supported MCP client.** (1h)
4. If Blueprint/UMG via MCP stalls, trial **EngineWire** (third-party MCP). Default gameplay logic = **C++**, written by the harness and fixed via the compile loop. (1h)
5. Assets - only if used in the prize entry (money = user's G1 step): **Suno Pro** ($10/mo, commercial music), **Meshy** (Pro ~19 EUR/mo, or Free = CC-BY), **Firefly**/similar for 2D, **ElevenLabs** Starter for SFX/voice. (0.5h)
6. Write a **CLAUDE.md** in the game repo with the UE version + conventions; every agent session reads it.
Security: the MCP servers have NO auth - keep them on loopback, stop them when idle, and review any third-party plugin before installing.

(If D1 lands on UEFN instead: UEFN has its own official MCP for Verse; steps 1-2 become "install Fortnite + UEFN"; submission is a private version code, so no Windows packaging.)

## What the PM does next (after the user answers)
- Recommend the engine from the team's skills.
- Build the AI-toolchain plan + the pre-jam setup brief.
- Turn Phase 2 into a concrete work split between the two people + the AI agents.
