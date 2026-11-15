# Art, story, film - every AI and program we used (Mehmet + his Claude, 10.-15.11.2026)

Mehmet is the art director and does not code. Everything on the art side was directed by him in German, in chat,
and executed by one Claude Code session (plus its subagents) that drove the other AIs and programs: in the browser
(Claude in Chrome for Tripo, Rodin, Mixamo, Fab), through MCP (Unreal, Blender, Higgsfield) and with scripts
(`tools/`, `artwork/**.py`). Numbers are read from the accounts and logs, not estimated, unless marked "about".
Detail lists: [`../abgabe/TOOLS_USED.md`](../abgabe/TOOLS_USED.md), [`../abgabe/VERBRAUCH_CREDITS_TOKENS.md`](../abgabe/VERBRAUCH_CREDITS_TOKENS.md).

## The AIs
| AI | What for | How much |
|---|---|---|
| **Claude Code** (Anthropic; Opus 5.5, Fable 5.2, Sonnet 5.5, Haiku 5.5) | the "art studio": art direction in chat, level art + lighting in Unreal (Python + MCP), character pipeline, Blender scripts, Codex/Tripo/Rodin/Higgsfield briefs, film cutting + sound, HUD look in C++ (notebook, film hand-over), hero shots, docs | **2.92 billion tokens** in 6,000 replies, 107 transcripts incl. subagents (output 5.10 M) |
| **OpenAI Codex** (ImageGen) | 2D concept art and style bible, character sheets for Tripo, prop templates for Rodin, UI art (frames, bars, eyes, icons, notebook spread), title/logo/icon, film keyframes, itch cover | **408 images** in 81 sessions, 316 M tokens |
| **Tripo Studio** | the 10 characters (P2.0 multiview, Smart UV, texture, PBR, UE5 mannequin rig) | **1,900 credits** |
| **Hyper3D Rodin Gen-2.5** | 35 hero props (valve wall, score portfolio, wind-up gadget, doors, lever, winch, lamps, ...) | **about 51 credits** |
| **Higgsfield Seedance 2.5** | 5 story films (cold open, two endings, portfolio, curtain) from Codex keyframes, one clip per shot; plus the corridor shot that ends the cold open on the game's first frame and 3 title clips for the trailer / animated itch cover | **889 credits net** (refunds for failed jobs counted) |

## The programs
| Program | What for |
|---|---|
| Unreal Engine 5.8 + Unreal MCP + Unreal Python | level dressing, lighting, materials, character import, test runs, packaging |
| Blender + Blender MCP | about 25 procedural meshes (stage set, stage house, corridor, flats, hand props), character fixes (weights, heads, proportions) |
| Adobe After Effects | cold open post (grain, transitions, title text) |
| FFmpeg + Python (NumPy, SciPy, Pillow) | cutting all films, rebuilding their sound from the team's SFX, image checks, hero-shot sheets |
| Quixel Megascans (Fab), Mixamo, Epic Game Animation Sample, Quaternius | 29 props + surfaces, 23 + 61 + 25 animation clips (free licences, see ASSETS.md) |
| Diversion | version control, about 300 commits shared with Rene's side |

## How we pushed it (short)
- **One AI drives the others:** Claude wrote every Codex/Tripo/Rodin/Higgsfield brief, clicked through the web tools
  itself (no download dialogs), imported, checked and placed the results.
- **Pictures are checked by the AI too:** every character went through an in-engine showroom with screenshots; every
  film was cut frame-exact on the music; the itch screenshots were taken by scripted game runs with a fixed cinematic
  camera (no paint-over).
- **The human decides, in plain words:** Mehmet's acceptances and rejections are quoted in DEVLOG.md (e.g. the first
  cold open was rejected as "null verstaendlich" and rebuilt shot by shot).
