# Jam-Ablauf 12.-16.11.: grober Plan

*Entwurf vom PM, 12.11.2026, Stand 11:45, nach den Antworten von CTO (#182) und Musikstudio-PM (#180, #181).
Baut auf `2026-11-09-megajam-plan.md` auf. Alle Zeiten MEZ.*

## Ziel

Eine richtig gute, kurze Demo, die sich wie ein kleines fertiges Spiel anfühlt (5-15 Minuten): Intro, eine
Kernhandlung, Steigerung, Ende mit Gewinnen oder Verlieren. Poliert schlägt groß.
**Abgabe Sonntag 15.11. um 22:00.** Bis zur Frist um 02:59 bleibt das als Puffer.

## Leitsätze

0. **Ihr seid Producer, die KI baut.** Claude schreibt das gesamte C++. Beim Kollegen läuft die Art-Produktion
   automatisiert in großem Stil (MCP, KI-Asset-Tools). René und der Kollege geben die Richtung vor, spielen,
   entscheiden und nehmen ab. Wir zeigen, was KI im Maximum kann. Das ist zugleich die Glass-Box-Geschichte und trifft
   Epics Satz zum Thema: „If you're utilizing AI agents ... you're directing those too!"
1. **Drei Spuren laufen parallel, keiner wartet.** Die Regeln stehen in `COLLABORATION.md` 1.2.
2. **Der Harness läuft nachts, tagsüber wartet niemand auf ihn.** Der Antrag entsteht tagsüber, die Freigabe kommt
   abends, das Ergebnis liegt morgens im Repo. Jeder Lauf liefert etwas ohne Unreal, das sich prüfen lässt (Zahlen,
   Tabellen, Testfälle). Geschmack, Gefühl und Musik bleiben bei euch und den Sessions vor Ort.
3. **Pro Lauf eine neue Fähigkeit.** Das Ziel steht in euren Worten, das Material ist knapp, das Hauptmodell ist
   Sonnet. Opus nur dort, wo eine Urteilsfrage den Jam steuert. Die Agenten wählen ihre Modelle selbst. Jeden Lauf
   besprechen wir vorher.
4. **Auf Renés Laptop laufen nie Unreal oder ein Unreal-Build gleichzeitig mit einem Lauf.**
5. **Ergebnisse sind am Morgen im Repo**, unter `docs/harness/<lauf>/`.

## Budget (gemessen vom CTO)

- Das Wochenbudget setzt sich heute um 13:00 zurück, das nächste Mal erst am Do 19.11. **Der ganze Jam hat also
  einmal 100 Prozentpunkte.**
- Weil Claude das gesamte C++ schreibt, brauchen Renés Sessions etwa 10-15 Prozentpunkte am Tag, bis Sonntagnacht
  also 35-50.
- Für den Harness bleiben 35-45 Prozentpunkte, dazu 10 als Reserve für Sonntag. Das sind **etwa 8-11 je
  Nachtlauf**.
- Im 5-h-Fenster ist ein Lauf mit mehreren Opus-Agenten nach etwa 80 Minuten am Limit. Mit Sonnet als Hauptmodell
  reicht ein Fenster für 2-3 Stunden.

## Wer was macht

| Spur | Vor Ort (Producer + Claude) | Harness (nachts, ohne Unreal) | Extern |
|---|---|---|---|
| **Code / Logik** | Claude in Renés Session: gesamtes C++, Graubox, Einbau. René spielt, entscheidet und nimmt ab | Referenzmodell in Python, Balancing-Tabellen (CSV), Testfälle mit Sollwerten | - |
| **Story / Art / Video** | Claude beim Kollegen: Assets, Licht, Level per MCP, automatisiert. Der Kollege ist Producer und Art Director: Story, Stil, Auswahl, Intro, Zwischensequenzen, Trailer, Packen des Builds | - (Geschmack) | KI-Asset-Tools; RunPod nur bei Bedarf |
| **Musik / Sound** | René übergibt und nimmt ab; Claude baut ein | - (Geschmack) | **Musikstudio-PM: die gesamte Musik und der ganze Ton** (Auftrag #188); Technik entscheidet er |
| **Glass Box / Abgabe** | beide, je 15 Minuten am Abend. **Zum Schluss (So) fordert René alle beteiligten PMs auf, einen Bericht zu schreiben, was sie gemacht haben, wie Abteilungen eines Studios** (megajam-PM, Musikstudio-PM, CTO, die Bau-Sessions). Daraus entsteht der Glass-Box-Dev-Log | Dev-Log-Entwurf aus Repo und Log | - |

## Tagesplan

| Tag | Ziel des Tages | Harness (nachts) |
|---|---|---|
| **Do 12.** | Heute das Konzept festlegen. Danach schreibt der PM mit euch noch heute die MVP-Spezifikation (kein Lauf, damit niemand wartet). Bis dahin arbeiten beide an der konzeptunabhängigen Startliste. Um 19:00 das erste Zusammenführen. Der Musikauftrag geht an den Musikstudio-PM | **Nacht 1:** Referenzmodell in Python, Balancing-Tabellen und Testfälle mit Sollwerten. Gegen sie prüft Claude das C++ |
| **Fr 13.** | Die Kernhandlung ist in der Graubox spielbar, Hauptfigur und Bausatz sind drin. Musik als Skizzen. Abends der erste Build, und er startet | **Nacht 2:** Balancing nach euren Spieltest-Notizen, dazu ein gezielter Test auf die Fehler aus Nacht 1 |
| **Sa 14.** | Alle MUST-Punkte sind drin. Jede Szene klingt, notfalls mit Platzhalter. Die Musik ist fertig, Intro und Zwischensequenzen ebenfalls. Abends Feature-Freeze, danach der Build-Test auf Renés Laptop | **Nacht 3:** Testplan und Fehlerliste aus dem Build, Dev-Log-Entwurf. Den genauen Inhalt besprechen wir am Samstag |
| **So 15.** | Politur, Fehler, Trailer auf den fertigen Track, keine neue Musik. 20:00 Kandidat, 22:00 Abgabe | keiner |

## Musik

**Stand 12.11. nachmittags (René):** Die gesamte Musik und den Ton übernimmt der Musikstudio-PM, René übergibt nur.
Der PM schreibt ihm keine Technik vor (Tempo, Formate, Lautheit), sondern erklärt Setting, Story, Stimmung und wofür
Musik gebraucht wird (Auftrag #188, ersetzt #187). Was unten steht, ist sein eigener Rat aus #180 und nur Hintergrund.

- **3-4 Stücke plus 15-25 SFX:** ein Titel-Loop, 1-2 Spiel-Loops (ruhig und angespannt), 1-2 Stinger. **Ein starkes
  Thema**, das in Titel, Spiel und Trailer wiederkehrt.
- **Keine Stems, die nach Spannung gemischt werden.** Das macht für Erstlinge zu viel Arbeit in der Engine. Besser
  zwei Loops im selben Tempo und derselben Tonart, Wechsel per Crossfade (1-2 s am Taktende), Stinger darüber.
- **Freitag Skizzen, Samstag fertig, Sonntag keine neue Musik.**
- **Technik:**
  - WAV 48 kHz, 24 bit.
  - Loops aus ganzen Takten, der Hall wird auf den Anfang gefaltet.
  - Tempo 96, 100 oder 120 BPM.
  - Namen: `music_<szene>_<bpm>bpm.wav`, `sting_<ereignis>.wav`, `sfx_<ereignis>.wav`, dazu `sounds.json`.
  - Loops auf -14 LUFS, Spitzen höchstens -1 dBFS, Stinger 2 dB leiser.
  - Im Spiel liegt die Musik 6-10 dB unter den SFX. Der Trailer bekommt einen eigenen Mix (-14 LUFS, -1 dBTP).
- **Achtung:** Konzept A plant etwa 12 Minuten Musik und 4 Spannungs-Stems. Das ist zu viel und wird im MVP gekürzt.
  Die Lautheitswerte aus den Leitfäden des Laufs (Spiel-Mix -18 LUFS) klärt der Musikauftrag.

## Renés Laptop

- Unreal tagsüber in Blöcken, Läufe nachts. Während eines Laufs sind **kein Editor und kein Unreal-Build** offen,
  auch nicht über die Kommandozeile.
- **Checkliste vor jedem Nachtlauf (René):**
  - Netzteil dran. Im Akkubetrieb schläft der Laptop nach 3 Minuten ein, und das beendet den Lauf.
  - Deckel offen.
  - **Windows-Updates neu pausieren**, die Pause von gestern ist nicht mehr aktiv.
  - Unreal und alle Builds sind zu.
  - Docker läuft.
- Mehr Speicher für die VM bringt erst etwas, wenn der Architekt CPU und Speicher je Antrag einstellbar macht. Für
  Textläufe bringt es nichts.

## So laufen die Nachtläufe

- **Der CTO koordiniert die Nächte** (René, 12.11.): Stellen der megajam-PM und der Musikstudio-PM beide einen Antrag,
  legt der CTO fest, welcher Lauf wann läuft. Bis zur Warteschlange (#184) geht nur ein Lauf pro Nacht.
- Die Läufe selbst besprechen wir später.

- **Ein neuer Bau-Käfig für alle Nachtläufe**, mit dem Image `zentrale-cage-studio:1` (Python mit numpy und scipy für
  den Simulator). Der CTO legt ihn mit dem ersten Antrag an. Die Ergebnisse einer Nacht liegen der nächsten schon vor.
- **Kein C++ im Käfig.** Stattdessen ein Python-Referenzmodell als Orakel und CSV-Tabellen als Vertrag. Code aus dem
  Käfig läuft nie auf dem Host. Ins Repo kommen Tabellen, Ergebnisse und Berichte.
- **Grenzen je Nachtlauf (Rat des CTO):** 180-240 Minuten, 4-6 Runden, 8-10 Prozentpunkte der Woche, 90 % des
  5-h-Fensters, 1-2 GB.
- **Ablauf:** tagsüber besprechen und den Antrag prüfen lassen. Abends kommen der CTO und deine Freigabe, am besten
  gleich mit Ja zur Übernahme der md/csv/json-Dateien nach `docs/harness/<lauf>/`. Der Lauf startet nachts. Morgens
  exportiert der CTO, und ich checke in Diversion ein.
- **In jedem Antrag:** eine neue Fähigkeit, Hypothesen vorher, Begriffe im Antrag definiert, „entfernen heißt
  verschieben", und nur das Material, das dieser Lauf braucht.

## RunPod

Es gilt der Rahmen aus #157: Jeder Einsatz braucht dein Go. Es gibt einen Pod mit höchstens 2 h, und am Ende wird er
gelöscht. Erst die Credits der Asset-Tools nutzen. Wenn RunPod, dann abends, solange jemand wach ist, denn der Pod
stoppt nicht von selbst.

## Was ich aus den Fehlern mitnehme

- **Harness heißt** CTO-Antrag plus deine Freigabe. Subagenten nenne ich Subagenten.
- **Jeder Lauf wird vorher mit dir besprochen.**
- **Den Brief trenne ich in drei Teile:** Zäune, Wünsche in euren Worten, versiegelte Hypothesen. Das Thema ist nur
  ein loser Bezug. Das Rückgabeformat bleibt neutral.
- **Freie Läufe verengen ein breites Ziel** auf das, was sie selbst erzeugen und prüfen können. Deshalb braucht jeder
  Lauf einen klaren Satz und eine Prüfung von außen danach.
- **Budget rechne ich von Hand.** Die Schätzung im Check unterschätzt Läufe mit mehreren Agenten um das 5-6-Fache.

## Offene Punkte

**Von euch:**
1. Das Konzept, heute.
2. Die Specs vom Rechner des Kollegen (CPU, RAM, GPU, freier Platz).
3. Welche Asset-Tools und Credits aktiv sind.

**Vom PM:**
1. Die Jam-Regeln zu KI-Audio und zur Sprache prüfen.
2. Die MVP-Spezifikation mit euch schreiben.
3. Der Musikauftrag nach dem Konzept.
4. Den Antrag für Nacht 1 tagsüber vorbereiten.
