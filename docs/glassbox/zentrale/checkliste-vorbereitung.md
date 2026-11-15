# Checkliste – Vorbereitung 2026 Epic AI MegaJam
**Team: Produktlicht · Engine: Unreal Engine · Stand: 09.11.2026**

> Ziel: gewinnen. Wir setzen maximal KI ein (Code-Agenten + Unreal MCP + KI-Assets).
> Die ~2 Tage Vorbereitung JETZT entscheiden mit – vor allem die großen Downloads und das MCP-Setup.

---

## 0. Termine (deutsche Zeit / CET)
- **11.11., 20:00 Uhr** – Kickoff-Livestream + Theme-Reveal (Twitch/YouTube/X „UnrealEngine"). Erst dann kennen wir das Thema.
- **12.11., 06:00 Uhr – 15.11.** – Bauen erlaubt (vorher NICHT).
- **16.11., 02:59 Uhr** – Abgabeschluss. Zu spät = disqualifiziert → wir geben mit Puffer ab.
- Gewinner: bis 29.01.2027.

---

## 1. Accounts & Anmeldung
- [x] itch.io-Account (René) – erledigt
- [x] „Join jam" geklickt (René) – erledigt
- [ ] **Freund:** itch.io-Account anlegen **und** auf der Jam-Seite „Join jam" klicken → https://itch.io/jam/2026-epic-ai-megajam
- [ ] **Beide:** Epic-Games-Account (Pflicht, **Alter 18+**). Notiert euch genau, **welche E-Mail** pro Person mit dem Epic-Account verknüpft ist – die wird bei der Abgabe gebraucht.
- [ ] Offizielle Regeln lesen (gibt es **auf Deutsch**, Link auf der Jam-Seite) – v. a. Asset-/Lizenzregeln und Länder-Eignung.

### ❓ „Wie wird ein Team erstellt – jetzt oder bei Start?"
**Es gibt KEINEN eigenen Team-Schritt vorab.** Das Team wird **erst bei der Abgabe** angelegt: im Submit-Formular tragen wir ein → **Teamname: Produktlicht** + beide Namen + beide Epic-E-Mails. Einer lädt am Schluss das fertige Build auf **sein** itch-Konto und submittet für beide. Jetzt zu tun: Beide treten dem Jam bei und haben einen Epic-Account.

---

## 2. Software installieren (⏳ zig GB – HEUTE starten!)
- [ ] **Epic Games Launcher** (reagiert „Engine installieren" nicht? → Einstellungen → „Spielebibliothek ausblenden" an/aus togglen)
- [ ] **Unreal Engine 5.8.4** (beide Rechner gleiche Version, NICHT 5.8.0). **Sparsam installieren** (Speicher!): im Installations-Dialog unter „Optionen" **„Editor-Symbole zum Debuggen" ABWÄHLEN** (+40–70 GB) und **keine zusätzlichen Plattformen** anhaken (+5–15 GB je); keinen Starter Content.
- [ ] **Visual Studio 2026** – NUR die 2 Workloads „Desktop development with C++" + „Game development with C++" (keine Extras). Auch auf dem Laptop nötig (C++).
- [ ] Speicher knapp (Laptop ~138 GB frei → es bleiben ~20–50 GB). Der Rechner des Freundes baut + packt die Abgabe.

---

## 3. KI-/Agenten-Setup – das Herzstück „max KI" (René)
- [ ] Claude Code (unser Harness) einsatzbereit
- [ ] Im UE-Editor **Unreal MCP** aktivieren – Plugins: „Unreal MCP" + „All Toolsets" + „Toolset Registry" + „EditorToolSet"; „Auto Start Server" an; `.mcp.json` generieren; Claude Code aus dem Projektordner starten.
  *(Epic verlinkt Setup-Video + Doku direkt auf der Jam-Seite unter „Tools".)*
- [ ] **Test VOR dem Jam:** Agent spawnt einen Würfel, setzt ein Licht, startet „Play". Läuft das → Pipeline steht.
- [ ] **Einmal ein Windows-Build packen** (leeres C++-Projekt) – beweist den Abgabe-Weg.
- [ ] **Diversion-Repo** fürs Spiel (NICHT git im Jam) + die drei Claude-Dateien ins Repo: **ONBOARDING.md** (Kontext+Setup), **COLLABORATION.md** (Zusammenarbeit + Diversion-Workflow), **DOCUMENTATION.md** (Dev-Log/Deklarationen). Liest jede Claude-Instanz.
- [ ] Fallback bereit: „EngineWire" (Drittanbieter-MCP), falls Blueprints/UMG über MCP nötig werden.
- 🔒 Sicherheit: MCP-Server haben keine Authentifizierung → nur lokal laufen lassen, nach Gebrauch stoppen.

---

## 4. KI-Asset-Tools (Freund: Art / Grafik / Sound)
Kostenpflichtige nur, wenn wir die Assets wirklich im Entry nutzen (Lizenz wegen Preisgeld):
- [ ] **2D/Grafik:** Adobe Firefly (geringstes Lizenzrisiko) / Midjourney (Paid) / Flux
- [ ] **3D-Modelle:** Meshy (Gratis = CC-BY mit Namensnennung; Pro ~19 €/Monat = eigene Rechte) – Export FBX/GLB/OBJ
- [ ] **Musik:** Suno **Pro ($10/Monat)** für kommerzielle Rechte (Gratis-Plan reicht NICHT)
- [ ] **SFX/Stimme:** ElevenLabs Starter (~$6/Monat)
- [ ] Eure DAWs für Mix / eigene Musik
- [ ] 👉 Epic will **Asset-Credits** bereitstellen („details coming soon") – vor dem Kickoff nochmal die Jam-Seite prüfen, evtl. sparen wir Geld.
- [ ] **Lizenz-Liste führen:** jedes genutzte Asset + seine Lizenz notieren (muss bei der Abgabe gelistet werden).

---

## 5. Regel-Pflichten (nicht vergessen)
- [ ] **Nicht vor dem 12.11. am Spiel bauen.** Tool-/Agenten-/MCP-Setup vorher ist erlaubt.
- [ ] **Deklarations-Liste führen:** alles, was VOR dem Jam entsteht (Prompts, Skripte, Assets, Setup), muss bei der Abgabe deklariert werden.
- [ ] Nur **eine** Engine (wir: Unreal Engine).
- [ ] Nur **gepacktes** Build abgeben (keine „unpackaged" Projekte).
- [ ] Eigenes Gameplay bauen, das über Epics Starter-Templates hinausgeht.

---

## 6. Abgabe – was am Ende rein muss (15./16.11.)
- [ ] Windows-Build (Development), spielbar auf Win 10/11; `.zip` namens **`Produktlicht_<Spielname>`**, < 1 GB (größer → butler / Blendo Itch Uploader)
- [ ] **Gameplay-Video 30–60 Sek.** (Gameplay in den ersten 5 Sekunden zeigen!)
- [ ] Teamname **Produktlicht** + beide Namen + beide Epic-E-Mails + Spielname
- [ ] Optional, aber lohnt sich: **Dev-Log** (Pflicht für die Kategorie „Glass Box")

---

## 7. Unsere Preis-Strategie (realistisch aufs Gewinnen)
Neben „Best Overall" gibt es **Modifier-Kategorien** – da sind wir als 2er-Team mit Max-KI stark:
- 🎯 **Best Team** ($5.000) – bestes Spiel eines 2+-Teams → genau wir
- 🎯 **Glass Box** ($2.500) – bestes Dev-Log, das zeigt, WIE wir gebaut haben → perfekt für unseren KI-/MCP-Ansatz → **ab Tag 1 Dev-Log/Notizen führen**
- 🎯 **Render Royalty** ($2.500) – beste Optik → deine Art-Stärke
- + **Best Overall UE** ($7.500) als Stretch
- Bewertet wird 1–5 in: Ambition/Innovation, Thema, Spaß, Gameplay, Visuals, Leveldesign/Progression, Audio.

## 8. Hardware & Rollen (von der CTO geprüft, 10.11.)
- **René / Laptop** (i7-1185G7, 16 GB RAM, Intel Iris Xe, ~138 GB frei): Logik, **C++-Programmierung**, Balancing, **Musik**, Tests. Wenig/keine Grafik. Schwache GPU → Editor auf **Scalability Low**, Lumen/Nanite/Virtual Shadow Maps **aus**, „Use Less CPU when in Background" an; Projekt **einmal vor dem Kickoff** öffnen (erste Shader-Kompilierung dauert 30–60+ Min).
- **Freund / Bau-Rechner:** 3D, Grafik, Licht, Level **und das Packen der Abgabe** (dort läuft die GPU-Last + das MCP-Editor-Steuern). → **Bitte Eckdaten seines Rechners geben: CPU, RAM, GPU, freier Speicher.**
- **Windows-Updates** für die Jam-Woche **pausieren** (ausstehende vorher installieren) – ein erzwungener Neustart in der Abgabenacht wäre fatal.
- **Zusammenarbeit:** `.uasset`-Dateien lassen sich nicht mergen → pro Blueprint/Map festlegen, wem es „gehört"; World Partition / One File Per Actor nutzen; **Diversion mit Dateisperren** (gemeinsame Binärdatei VOR dem Bearbeiten sperren).

---
*Fragen oder etwas unklar? → an René / den PM.*
