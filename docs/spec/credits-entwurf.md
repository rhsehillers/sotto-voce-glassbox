# Vorspann und Credits - Entwurf zur Entscheidung (René + Mehmet)

Stand 14.11. 13:14, PM. René: *"erst einmal klar machen wer was gemacht hat und wie dann die texte sind"*. Grundlage:
DEVLOG, ASSETS.md, das Entscheidungs-Log (D1-D20) und die Glass-Box-Mappe. **Nichts davon ist schon im Spiel** - der
Vorspann im Gang zeigt noch den ersten Entwurf aus `Data/credits.csv`.

## 1. Wie Credits bei Spielen üblich sind

- **Vorspann kurz, Abspann vollständig.** Der Vorspann (wie im 90er-Film) nennt das Team, den Titel und die wichtigsten
  Köpfe - meist 6-10 Karten. Alles Vollständige (jede Rolle, Fremd-Assets, Lizenzen, Dank) steht im Abspann oder auf
  einer Credits-Seite im Menü.
- **Rollen heißen nach dem, was jemand tut**, nicht nach Stellentiteln:

| Rolle | Was sie tut |
|---|---|
| Game Director / Creative Director | Vision des Spiels, letzte Entscheidung über Spiel und Mechaniken |
| Producer | Plan, Zeit, Umfang, Koordination aller Beteiligten |
| Game Designer | Regeln, Mechaniken, Balancing |
| Writer / Narrative Designer | Geschichte, Figuren, Texte |
| Art Director | Stil und Look, Abnahme aller Grafik |
| Artist (3D, 2D, Level, Lighting, Technical) | baut die Grafik, stattet Level aus, setzt Licht |
| Cinematics | Zwischensequenzen, Kamera |
| Programmer / Engineer | Code, Systeme, Werkzeuge |
| Composer / Sound Designer | Musik, Geräusche |
| QA / Playtesting | testet, meldet Fehler, prüft Balance |

- **Kleine Teams bündeln Rollen** ("Design & Direction", "Art & Story").
- **Fremd-Assets und Werkzeuge** stehen am Ende unter *Third-party assets* / *Made with* / *Special thanks*; die Engine
  bekommt ihren Hinweis.
- **Unsere Regel (Glass Box):** Jede Zeile sagt, was jemand wirklich getan hat - auch, was die KI getan hat.

## 2. Wer hat was gemacht

| Wer | Was (belegt in DEVLOG / ASSETS / Entscheidungen) |
|---|---|
| **René** | Projektleitung und Planung vorab und im Detail (Jam-Wahl, Engine D1, Zeitplan, Abnahmen); Konzeptwahl mit Mehmet (D5) und Spec-Abnahme (D6); Spielmechaniken entschieden und verfeinert (Umziehen hinter der Trennwand D7, Gadget-Wurf D8, Schwierigkeit D9, Neustart D11, Fail-Karte D12, Logengang D13/D16, Schatten D18, Spielstart im Gang D20); Balancing ganz bei ihm (D11); Spieltests; hat alle KI-Instanzen geführt (Zentrale). **Keine Zeile Code selbst geschrieben.** |
| **Mehmet** | Art Direction (Stilbibel "Gaslicht-Noir"); Figuren, Props, Level-Ausstattung, Licht, HUD-Grafik, Schriften, Titelbild - vieles mit eigener Hand nachgearbeitet; Story mit René ausgewählt und verfeinert (keine Geister, Steampunk); der Cold Opener; Animationen ausgewählt und eingebaut |
| **Claude in Renés Zentrale** (PM-Instanz) | den ganzen Code (C++), Graubox-Level und Layout, Werkzeuge, Pakete, Dokumentation |
| **Claude-Agenten der Zentrale** (Konzept-Lauf 12.11., 9 Agenten, 47 min) | die 4 Konzeptentwürfe, aus denen René und Mehmet *Sotto Voce* gewählt haben |
| **Claude in Mehmets Studio** | Art-Pipeline: Import, Retargeting, Blender-Skripte für Bühnenteile, Paravents und Saal, Ausstattung per Unreal Python, Lichtdurchgang, Prüfskripte |
| **Der Music PM** (Claude, Projekt musikstudio) | alle Musik, Stinger und Geräusche, von Null in Python synthetisiert; Trailer-Musik |
| **Die Bild-Instanz** (Renés Labor) | den Bühnenboden, jede Diele von Null in Code erzeugt |
| **Werkzeuge, die Mehmet eingesetzt hat** | Codex / OpenAI ImageGen (Konzeptbilder, UI, Titel), Tripo Studio (Figuren), Hyper3D Rodin (Props), Blender |
| **Fremd-Assets** | Epic Games (Unreal Engine 5.8, UE5-Mannequin, Game Animation Sample), Quaternius (Universal Animation Library, CC0), Adobe Mixamo (Animationen), Quixel Megascans via Fab (Flächen + Props), Toon Studio Lite von RafaSC (Fab), Google Fonts (Abril Fatface, Libre Baskerville, OFL) |

## 3. Rollen-Vorschlag

- **René - "Directed & produced by"** (Game Director & Producer). Director, weil er die Vision und jede Spiel-Entscheidung
  verantwortet; Producer, weil er geplant und koordiniert hat. "Game Design" steckt darin (Mechaniken, Balancing). Kein
  "Programmer" - den Code hat die KI geschrieben, unter seiner Führung.
- **Mehmet - "Art Director"**, im vollen Abspann zusätzlich *Art, Level Art & Lighting* und *Cinematics* - er hat nicht nur
  abgenommen, sondern selbst gebaut.
- **Story - "René & Mehmet, from concept drafts by Claude"**: die Idee kam aus dem KI-Konzept-Lauf, gewählt und
  verfeinert haben die beiden.
- **Die KI-Instanzen als Mitentwickler** mit ihrer echten Aufgabe (Tabelle oben). Claude ist von Anthropic - das gehört
  einmal dazu.

## 4. Vorspann im Gang (Entwurf, 8 Karten, ~28 s)

Erst die KI-Mitentwickler, am Ende Mehmet und René. Englisch wie das ganze Spiel.

| # | Rolle (klein) | Name (groß) |
|---|---|---|
| 1 | | Produktlicht presents |
| 2 | Programming & level layout | Claude, in René's Zentrale |
| 3 | Art production | Claude, in Mehmet's studio |
| 4 | Music & sound | The Music PM (Claude), composed in Python |
| 5 | Stage floor | The image instance, generated in code |
| 6 | Story | René & Mehmet, from concept drafts by Claude |
| 7 | Art Director | Mehmet |
| 8 | Directed & produced by | René |

Varianten: Karte 2-5 kürzer als eine Karte *"Developed with Claude (Anthropic) - code, art production, music"*; oder
Karte 1 als *"A Produktlicht game"*.

## 5. Abspann / Credits-Seite (nicht im Gang)

```
SOTTO VOCE: THE CUT                          a Produktlicht game - 2026 Epic AI MegaJam

Directed & produced by ........ René
Game design & balancing ....... René
Art direction ................. Mehmet
Art, level art & lighting ..... Mehmet
Cinematics .................... Mehmet
Story ......................... René & Mehmet, from concept drafts by Claude

AI co-developers (Claude by Anthropic)
  Programming & level layout .. Claude, in René's Zentrale
  Concept drafts .............. a team of 9 Claude agents in the Zentrale
  Art production .............. Claude, in Mehmet's studio
  Music & sound ............... the Music PM (Claude), synthesized in Python
  Stage floor ................. the image instance, generated in code

Made with
  Unreal Engine 5.8 - Epic Games
  Concept art, UI and title art - OpenAI Codex (ImageGen)
  3D characters - Tripo Studio      3D props - Hyper3D Rodin      Procedural meshes - Blender

Third-party assets
  UE5 Mannequin, Game Animation Sample - Epic Games
  Universal Animation Library - Quaternius (CC0)
  Animations - Adobe Mixamo
  Surfaces and props - Quixel Megascans (Fab)
  Toon Studio Lite - RafaSC (Fab)
  Fonts - Abril Fatface, Libre Baskerville (SIL Open Font License)

Special thanks
  Epic Games and the AI MegaJam team
  Diversion (version control for the jam)
```

## 6. Notizen René 14.11. (Zuordnung passt - Feinschliff am Ende)

René: *"ja das reicht, wird mit sicherheit auch noch ergänzt aber so denk ich passt die zuordnung"*.

- **Schreibweise der KI-Mitentwickler: Abteilung (Modell), Mensch** - die Instanz mit ihrer Rolle und dem Menschen, mit
  dem sie gearbeitet hat. Beispiele:
  - *PM Megajam (Claude Opus 5.5), René* - Code, Level-Layout, Projekt-PM
  - *Art Studio (Claude), Mehmet* - Art-Produktion
  - *Audit (Fable)* - das Audit vor dem Balancing (D15, steht noch aus)
  - *Balancing (Claude Harness), René* - der Balancing-Lauf (steht noch aus; René entscheidet die Werte)
  - analog Music PM, Bild-Instanz, Konzept-Agenten
- **Modellnamen statt nur "Claude"** - wo bekannt (diese Session: Claude Opus 5.5). Zu klären: welches Modell lief in
  Mehmets Studio, beim Music PM, im Konzept-Lauf, im Audit.
- **Werkzeuge nicht im Gang, sondern in den Credits auf der Titelkarte** (Menüpunkt *Credits*): der Vorspann im Gang
  bleibt kurz (Menschen + KI-Mitentwickler), die volle Liste mit allen Werkzeugen, Fremd-Assets und Lizenzen steht dort.
- **Neu in der Werkzeugliste:** Higgsfield - Mehmet baut den Cold Opener vermutlich damit (bestätigen).
- Audit und Balancing kommen erst in die Credits, wenn sie gelaufen sind.
- **14.11. 14:20, René:** *"credits menü kann erstellt werden, soweit schon text rein, genauer text kommt später ; abspann
  würde nach der videosequenz von mehmet kommen am ende ; auf todo, wie genau bespreche ich später mit mehmet"*.
  Gebaut: Knopf *Credits* auf der Titelkarte, Text in `Data/credits_full.csv` (Entwurf). Mehmets Videos laufen über
  Higgsfield (Seedance 2.5, siehe seine Commits 243-248) - steht in der Liste.
- **TODO Abspann nach dem Ende:** derselbe Abspann läuft nach Mehmets Videosequenz am Ende - wie genau, klären René und
  Mehmet; der Code kann denselben Lauf aus `DT_CreditsFull` zeigen.

## 7. Offen

1. **Rollen und Wortlaut** - René + Mehmet (vor allem: "Directed & produced by" für René, "Art Director" für Mehmet).
2. **Mehmets Liste prüfen** - fehlt ein Werkzeug oder eine Quelle? Wer hat das Trailer-Video gemacht?
3. **Wo erscheint der volle Abspann?** Vorschlag: ein Knopf *Credits* auf der Titelkarte (~30 min Code), dazu derselbe
   Text auf der itch-Seite.
4. **Engine-Hinweis:** Epics Unreal-EULA verlangt meines Wissens einen Hinweis auf die Engine in den Credits - vor der
   Abgabe gegen den EULA-Text prüfen (PM).
5. **Namen:** Vornamen reichen, oder mit Nachnamen?
