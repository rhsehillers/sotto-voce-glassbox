# CTO-Urteil - megajam/2026-11-12-konzepte

Geprüft 2026-11-12 08:37 (CTO-Session). Antrag vom megajam-PM (#171), erster Antrag von megajam. Freier Lauf
(Konzeptrunde 2) in einem NEUEN leeren Käfig. Nutzerwort dahinter: „antrag stellen für ein harness beim cto, hier
sollen ruhig mehrere Agenten unabhängig arbeiten. Sprich harness nutzen mit engram" AND „Ja, senden" (PM-Session
12.11. 08:20/08:32, im Transkript geprüft). `check` -> **gelb** (`pruefung.json` 08:36), `preview` gelesen (Hash
1f7292dd…).

## Käfig vorbereitet (CTO, 08:35)
- `newcage.php megajam-konzepte --work ~/projects/game/megajam-konzepte --owner megajam --free`, Pitch =
  das `## Goal` des Antrags. Phase setup, Image `zentrale-cage:1`, kickoff `free` (nur der Satz AND die Wände),
  WebSearch/WebFetch gesperrt.
- `cage_audit.php --live`: alles grün. Kein Netz außer Modell AND Engram-Suche über den Proxy; Engram
  `/missing`, `/propose` AND `/register` abgewiesen, Lücken bleiben also lokal.

## Urteil
- **Ziel (frei, 640 Z., gelb):** dein Wortlaut aus der PM-Session, sprachlich geglättet. Der PM hat vorne einen
  Satz ergänzt, der die Aufgabe nennt („Konzepte … entwerfen lassen, mit Story und Vorschlägen zur Stilrichtung“).
  Er stützt sich auf dein „festlegen welche Stilrichtung, bzw vorschläge“. Weggelassen sind nur die Anweisungen an
  den PM („kurz planen…, antrag stellen…“). Keine Methode, keine Familienliste. Tragbar. Der Kickoff zitiert diesen
  Text als „User said“.
- **Hypothesen:** H1/H0, die Entscheidungsregel AND die 8 Kernloop-Familien stehen vor dem Lauf fest AND bleiben
  versiegelt. Die Vorschau zeigt nur das Ziel. Der PM sortiert nach dem Lauf, das Team wählt.
- **Leck (vom CTO geprüft):**
  - Lieferung: 2 Markdown-Dateien (4,2 KB), vollständig gelesen.
  - Keine Familienliste, keine Hypothesen, keine PM-Erwartung, keine E-Mail-Adresse. Personen nur mit Vornamen bzw.
    als „Kollege“.
  - Die Runde-1-Konzepte stehen nur als Dreizeiler drin, ihre Mechanik ausdrücklich als abgelehnt. Die vollen
    Dokumente AND `EMPFEHLUNG.md` bleiben draußen. Das ist so gewollt.
  - „Hitman“ ist ein Wunsch des Teams, kein Leck.
  - Käfig-Ordner (neu) nach Plan-Wörtern durchsucht (Familien, Runde-1-Namen, H1/H0, Empfehlung): 0 Treffer.
- **Kleiner Rahmen in `rahmen.md`:** Der Satz „Das Thema ist eine Metapher, keine Bauanleitung“ war in der PM-Notiz
  die Klarstellung „keinen alten Build wiederverwenden“. In der Lieferung liest er sich eher als „nicht wörtlich
  nehmen“. Epics Rahmung „die ambitionierte Idee, die nie Zeit bekam“ AND „Aim for ambition“ fehlt. Das ist kein Leck
  und berührt H1 nicht (die Erwartung zum wörtlichen Thema entscheidet nichts). Für den Theme-Bezug der Konzepte
  ist es aber ein kleiner Schubs. Hinweis an den PM; kein Grund, den Start aufzuhalten.
- **Was der Lauf zuerst sieht:** einen leeren Arbeitsordner (README, Branch `main`), `inbox/2026-11-12-konzepte/`
  mit den 2 Dateien, den freien Kickoff. Kein Loop-State, kein altes `status.json`.
- **Budget:** 4 Runden, 120 min, opus, max_turns 50, 1 GB.
  - Woche: 57 % + 6 pp = Stopp bei 63 % (Rücksetzen heute 13:00, Probe 09.11.).
  - 5-h-Fenster: 5 %, Stopp bei 60 %. `check` rechnet mit der Opus-Höchstrate 12 pp/h (alles Läufe mit einem
    Hauptagenten) -> erst nach der Zeitgrenze. **Mehrere unabhängige Agenten auf Opus ziehen aber schneller.**
    feedback-graphics (9 Agenten) lag bei 39 pp/h. Bei 40-55 pp/h kommt der Stopp nach etwa 60-80 min, nicht nach
    120. Der Lauf wird also eher kurz AND schwer.
  - Der Stopp bei 60 % ist gewollt: Er lässt dir 40 % für deine eigenen Sessions bis zum Rücksetzen. Deine
    Sessions UND meine CTO-Session ziehen am selben Fenster, der Stopp kann also früher kommen.
  - Konzepttext auf Platte bleibt auch bei einem Abbruch erhalten.
- **System (08:37):**
  - Docker läuft (VM 3,8 GB, 0 Käfige), C: 82 GB frei, Host-RAM 3,2 GB frei.
  - `UnrealEditor.exe` läuft nicht. **Der Editor muss während des ganzen Laufs zu bleiben.** Der PM erwähnt deinen
    kurzen Packaging-Test: ihn vorher machen AND den Editor schließen, ODER danach.
- **Windows-Updates (gelb):** dieselben 3 optionalen (2× Dell-Firmware, Audio-Treiber). Deine Pause von heute Nacht
  gilt. Ein Lauf von ~09:00 bis höchstens 11:00 liegt in der Nutzungszeit. **Nicht einspielen:** Firmware heißt
  Neustart, mitten im Jam unnötig. Den Rat „install before the start“ der Prüfzeile halte ich hier für falsch
  (Vorschlag #149 an den Architekten ist offen).
- **Nach dem Lauf:** CTO-Nacharbeit (summary, Git-Zahlen, Last). Die Konzepte bleiben im Arbeitsordner. Der PM liest
  sie, sortiert nach den versiegelten Familien AND schreibt euch eine deutsche Seite. In das megajam-Projekt kommen
  sie nur als PM-Paket mit deinem Ja.

## Freigabe-Anfrage an den Nutzer
**Frage:** Konzeptrunde 2 freigeben? Freier Lauf im neuen Käfig `megajam-konzepte`. Opus, mehrere Agenten, 4 Runden,
120 min, Woche bis 63 %, Stopp bei 60 % des 5-h-Fensters. Start sofort, sobald der Unreal Editor zu ist.

**Empfehlung:** Ja, jetzt. Kein Leck, Hypothesen vorab fest, Käfig geprüft. Rechne mit 1-1,5 h statt 2 h, weil das
5-h-Fenster bei mehreren Opus-Agenten früher greift. Für das MANIFEST reicht ein kurzer, neutraler Satz wie
„Lauf freigeben“.

**Alternativen:**
- Erst den Packaging-Test in Unreal, Editor zu, dann freigeben (kostet nur die Zeit des Tests).
- Erst lässt der PM den Theme-Satz in `rahmen.md` richtigstellen (~10 min, neue Prüfung).

**Wenn keine Antwort:** kein Start. Der Käfig bleibt leer stehen.

## Freigegeben AND gestartet (2026-11-12 08:39)
Nutzer-Wortlaut: „Lauf freigeben". Vorher geprüft: `UnrealEditor.exe` läuft nicht, C: 81,5 GiB frei, kein Lauf aktiv.
`release --said "Lauf freigeben"` (check gelb), `start` 08:39, Lauf `20261112-083921`. Startcheck: run.json mode
free, Grenzen 4/120/6/60/opus/50/1, Woche 57 % (Stopp 63 %), 5-h 5 %, C: 81,3 GB, `loop_state: none` (neuer Käfig);
Container `zcage-megajam-konzepte` up, Runde 1/4; Lieferung `inbox/2026-11-12-konzepte/` vollständig (2 Dateien +
MANIFEST + .gitattributes), Hardlinks (Linkzahl 2), Commit `bb5e512`, `user_said` „Lauf freigeben". PM informiert
(#174). Aus dem laufenden Käfig liest der CTO nichts.

## Nacharbeit (2026-11-12 09:3x, nach dem Lauf)
Ende 09:26 week budget (63 %), 5-h 59 %, nach 1 Runde (47 min), 1 min nach dem letzten Commit. loop-state: done,
goal_reached true, gate passed. 11 Commits `e865c19`..`42e4a10`, 11 Dateien +5033, Baum sauber, Bestand 0 verschwunden.
In `konzepte/`: 4 Konzepte (A-D), 2 Leitfäden, Übersicht mit eigener Empfehlung des Loops (C, Ersatz A; zählt nach
der Regel nicht), Review AND Prüfung. 9 Agenten, 594 Aufrufe. Last 0,31 GB / 26 % CPU - reine Modellarbeit. 5-h-Rate
~69 pp/h statt der geschätzten 12 (Vorschlag #176 an den Architekten). PM informiert (#177).
