# DECLARATIONS - pre-jam work (Team Produktlicht)

**Rule:** anything created BEFORE the build window (**Nov 12, 06:00 CET**) - prompts, scripts, tool/agent/MCP
setup, or assets - must be declared at submission. Add a line the moment you create such a thing.
**No game content** (levels, gameplay code, art, audio) is created before the build window.

Format: `- <date> | <what> | <who/tool> | <where it lives>`

- 2026-11-09..11 | Project planning + onboarding docs (ONBOARDING / COLLABORATION / DOCUMENTATION, roadmap, memory) | Rene + Claude (Zentrale PM) | project docs
- 2026-11-10..11 | Tool/engine setup: UE 5.8.4 install, Visual Studio 2026 (C++ workloads) | Rene | laptop
- 2026-11-10 | Unreal MCP setup + pre-jam pipeline spike on the build machine: empty UE 5.8 C++ project "VKTJam" (Epic "Blank" template), MCP plugins (ModelContextProtocol, ToolsetRegistry, AllToolsets, EditorToolset) + auto-start config, `.mcp.json`; spike via MCP (spawned cube + point light, Play started/stopped, test actors removed, nothing saved); Shipping Windows package built and launched (fix: AssetManager rule for GameFeatureData in DefaultGame.ini) | Mehmet (Friend) + Claude | build machine, project root
- 2026-11-10..11 | Build machine tools: VS 2026 C++ workloads, Git LFS, Blender, OBS, ShareX; Python remote execution + StateTree plugins enabled in VKTJam (config only); Fab + Quixel Bridge plugins (editor only) | Mehmet + Claude | build machine
- 2026-11-10..11 | Helper scripts + Claude skills on the build machine (MCP test client, editor remote control, character import/retarget pipeline Tripo -> UE5 skeleton, Mixamo fetch, map building, packaging); tested only in a separate practice project (F:\Claude\UE_Uebung) - **nothing from it goes into the jam game** | Mehmet + Claude | build machine (outside repo)
- 2026-11-11 | Diversion setup on build machine (client install, login, clone); VKTJam copied into the repo root; compiler set to Visual Studio 2026 (`Config/DefaultEngine.ini`) | Mehmet + Claude | project root
- 2026-11-11 | Diversion repo setup (repo, `.dvignore`, doc commits dv.commit.2-6) + engine registration fix on Rene's laptop (registry value renamed to "5.8", backup kept) | Rene + Claude (Zentrale PM) | repo root / laptop
- 2026-11-11 (evening, after the theme reveal) | Concept ideation round 1: 3 text concept drafts (Sotto Voce / The Choir Engine / The Last Gong) by Claude subagents in the Zentrale PM session + a PM recommendation; text only, no game content. The game is built from round-2 concept A (made Nov 12 08:39, inside the build window), which reuses the Sotto Voce setting and story from round 1 | Rene + Claude (Zentrale PM) | Zentrale project folder `konzepte/` (outside the repo)
<!-- add more as created, before Nov 12 06:00 CET -->
