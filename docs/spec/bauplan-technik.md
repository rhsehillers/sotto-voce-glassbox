# Bauplan Technik: SOTTO VOCE: The Cut

*Vom PM, 12.11.2026, für René (Producer) und seine Bau-Session (Claude, schreibt das gesamte C++). Grundlage: die
abgenommene Spec `docs/spec/mvp-sotto-voce.md` und eine Recherche vom 12.11. Was „belegt" ist, stammt aus Quellen
(Game Developer: „The AI of Hitman (2016)", Epic-Forum zu StateTree in 5.7, Forum-Threads zu AIPerception), der Rest ist
Fachwissen. Engram hat zu Spiel-KI und Stealth nichts; die Lücken sind gemeldet. Die Seite mit den Release Notes von
UE 5.8 war nicht lesbar, Details der 5.8-API prüft die Bau-Session am Compiler.*

## 1. Grundsätze

1. **Erst die Kernschleife, dann alles andere.** Zuerst wird „sehen und gesehen werden" mit einer Wache gebaut und
   gespielt. Erst wenn das trägt, kommen Uhr, Fahrpläne und Inhalte dazu.
2. **Nach jedem Schritt ist das Spiel spielbar.** Es gibt keine halben Systeme über Nacht. Jeder Meilenstein endet mit
   einem Build, der läuft, und einem kleinen Commit.
3. **Logik in schlichtem C++, Zahlen in Tabellen.** Die Spiellogik steckt in einfachen Klassen ohne Engine-Abhängigkeit,
   damit sie testbar ist. Alle Stellschrauben stehen in CSV-Tabellen.
4. **Graubox zuerst.** Grafik kommt später als Blueprint-Kind auf dieselben Klassen (COLLABORATION 1.2).
5. **Fair vor schwer.** Wer entdeckt wird, muss verstehen, warum. Das ist wichtiger als jede weitere Funktion.

## 2. Architektur

| System | Umsetzung | Warum |
|---|---|---|
| NPC-Verhalten | **C++-Zustandsautomat** (enum, 5 Zustände: Fahrplan, Nachsehen, Verdacht, Alarm, Rückkehr) in `USuspicionComponent`, je Zustand `Enter`/`Tick`/`Exit` | Für Claude am leichtesten zu schreiben, zu lesen und zu testen; ca. 150 Zeilen. StateTree (im Projekt aktiv) ist an Editor-Grafen gebunden, die per MCP schlecht zu bearbeiten sind. Behavior Trees und EQS braucht es nicht |
| Sicht | **eigener Test:** Sichtkegel (Winkel), Distanz, ein Line Trace von Auge zu Brust, 10-mal pro Sekunde | Der Verdachtsbalken braucht eine stufenlose Füllrate (Distanz, Licht, Kostüm, beschäftigt, Rennen). AIPerception liefert nur „gesehen / nicht gesehen" und hat bekannte Fallstricke (belegt: Forum-Threads) |
| Bewegung | **NavMesh `MoveTo`** zwischen festen Wegpunkten | Standard, kein eigener Code |
| „Beschäftigt" | Feld `bBusy` im Fahrplan-CSV | Smart Objects wären zu schwer |
| Zonen, Kostüme, Ereignisse | **Gameplay Tags** (`Costume.Worker`, `Zone.Box`, `Cue.SteamDown`, `Event.*`) | Billig und typisiert. Die Zonenprüfung ist ein `HasAny` |
| Stellschrauben | **DataTables aus CSV** (`Data/*.csv` als Quelle, importiert als DataTable) | Dieselbe CSV liest später das Python-Referenzmodell |
| Opernuhr, Checkpoints | `AOperaClock` mit reinem `FClockState` | Neustart heißt: Uhr setzen, alle NPCs auf ihren Fahrplanpunkt |
| Eingabe | **Enhanced Input**, die Assets legt die Bau-Session per MCP an | Vorgabe des Templates |
| Sequenzen | `ALevelSequenceActor` + `OnFinished`, überspringbar mit `GoToEndAndStop()` | Einfach; die Sequenzen selbst baut der Kollege |
| Karten | `L_Main` + 4 Schichten nach Besitzer (COLLABORATION 1.2), **kein World Partition** | Weniger Einrichtung, klare Besitzer |
| HUD | UMG mit C++-Basisklasse (Auge über dem Kopf, Programmzettel mit Uhr, Zielzeile, Tastenhinweise) | Das Aussehen setzt später der Kollege |
| Tests | Automation-Specs für die Logikklassen, headless (`-nullrhi`), dazu ein Python-Orakel | Läuft auch auf dem Laptop ohne GPU |

**Module in `VKTJam.Build.cs` ergänzen:** `AIModule`, `NavigationSystem`, `GameplayTags`, `UMG`, `Slate`, `SlateCore`,
`LevelSequence`, `MovieScene`. Bisher stehen nur `Core`, `CoreUObject`, `Engine`, `InputCore` und `EnhancedInput` drin.

**Testbare Kernklassen** (ohne `UWorld`):
- `FSuspicionModel::Step(dt, inputs)`: Verdacht pro Takt
- `FSchedule::PointAt(clock)`: wo eine Figur zu welcher Zeit steht
- `FClockState`: Phase und Checkpoints

## 3. Bauschritte

| Meilenstein | Wann | Was | Fertig, wenn |
|---|---|---|---|
| **M0 Fundament** | Do bis ca. 15:30 | Module ergänzen. Third-Person-Inhalte (Mannequin, Input) per Feature Pack hinzufügen; das ist geteilter Content, also vorher in `BOARD.md` mit dem Kollegen abstimmen. Spielfigur, PlayerController, GameMode in C++. `L_Main` mit 4 Schichten, `L_Test_Logic`. Graubox von Bühne/Seitenbühne und Logengang/Loge 7 nach den Maßen. NavMesh | Man läuft in Third Person durch Bühne und Loge |
| **M1 Sehen und gesehen werden** | Do bis 19:00 | Eine Wache (`AGuard`) mit Patrouille und `USuspicionComponent`, Auge im HUD. `ACostumeRack` und Kostüm-Zonen. Ein Cue (`ACueValve`, *Steam down*): Die Wache geht 10-15 s nachsehen und kehrt zurück | **Abnahme 1.** Frage an euch: „Verstehst du, warum du entdeckt wurdest?" |
| **M2 Uhr, Fahrpläne, Neustart** | Fr bis ca. 13:00 | `AOperaClock`, `phases.csv`, `npc_schedule.csv`. Phasenwechsel: Abblende, Glocke, Teleport. Checkpoints CP0-CP4, R in unter 2 s. Brac, Gaspard, Pompier mit Wahrnehmung; Valcourt, Chor und Bühnenarbeiter auf Schienen. Cues *Trap* und *Fly* | Ein Durchlauf der Uhr mit allen Phasen; Neustart funktioniert |
| **M3 Die ganze Runde** | Fr bis 19:00 | Mappe nehmen (CP3, danach sind die Wachen strenger). Ende A, Ende B, Scheitern mit Erklärung *„Caught by X - Y"*. Verstecke, Gadget, Programmzettel, Zielzeile. Platzhalter-Sequenzen. Erster gepackter Build (Rechner des Kollegen) | **Abnahme 2.** Spielbar von Anfang bis Ende |
| **M4 Inhalt und Klang** | Sa bis 19:00 | Grafik als Blueprint-Kinder einsetzen. Musik und Ton nach der Tabelle des Musik-PM. Sequenzen des Kollegen. Balancing nach Spieltests und Orakel. Tests grün. Build-Test auf Renés Laptop | **Abnahme 3,** Feature-Freeze |
| **M5 Abgabe** | So | Nur noch Fehler, Leistung und das Packen. 20:00 Kandidat, 22:00 Abgabe | Abgabe ist hochgeladen |

**Wenn es eng wird, wird in dieser Reihenfolge gestrichen:**
1. Gadget
2. Cue *Fly*
3. Ende B als Sequenz (wird zur Texttafel)
4. Wahrnehmung (Rückfall: Lichtkegel sind Entdeckungszonen)

## 4. Damit Schleichen fair ist und Spaß macht

Die Hitman-Lehren sind belegt (Game Developer, „The AI of Hitman"), die Umsetzung ist Fachwissen:
- **Feste, vorhersehbare Abläufe.** Spieler planen um die Fahrpläne herum. Lücken in der Bewachung sind gewollt.
- **Absicht zeigen.** Hat sich das Auge zu 25 % gefüllt, dreht die Wache den Kopf. Bei 60 % kommen ein Geräusch und
  ein Blick. Erst danach folgt Alarm.
- **Entdeckung ist umkehrbar.** Das Auge füllt sich langsam genug, dass man noch ausweichen kann.
- **Fenster sichtbar machen.** Etwa 30 Sekunden mit sichtbarem Countdown auf dem Programmzettel.
- **Vorwarnung:** Ein Hinweis zeigt eine Zone, die das Kostüm nicht erlaubt, bevor man sie betritt.
- **Fairer Fehlschlag:** Der Vorhang-Bildschirm sagt, wer einen gesehen hat und warum.
- Die Spieltests nach M1 und M3 stellen nur eine Frage: „Verstehst du, warum du entdeckt wurdest?" Das wird zuerst
  repariert.

## 5. Tests

- **Logikklassen** bekommen Automation-Specs, die headless laufen:
  `UnrealEditor-Cmd ... -ExecCmds="Automation RunTests VKTJam; Quit" -nullrhi`. Das braucht keine GPU, aber nicht
  während eines Harness-Laufs.
- **Ein Python-Orakel** liest dieselben CSV und liefert Sollwerte, zum Beispiel wer zu welcher Phase wo steht und
  welcher Verdachtswert nach N Takten bei festen Szenarien erreicht ist. Die C++-Specs vergleichen dagegen. Feste
  Taktrate und festes `dt`, damit beide genau übereinstimmen. Das Orakel ist ein Kandidat für den ersten Nachtlauf;
  die Läufe besprechen wir noch.
- **Ein Funktionstest je Fenster** (NICE): ein festgelegter Weg, Prüfung „nicht entdeckt".
- **Datenversion:** Beim Start loggt das Spiel eine Versionsmarke und die Zeilenzahl jeder Tabelle. So fällt auf, wenn
  der Build alte Daten hat.

## 6. Fallstricke

1. **AIPerception für den Verdachtsbalken.** Kostet Fehlersuche und liefert zu wenig (belegt). Darum der eigene
   Sicht-Test.
2. **CSV geändert, aber nicht neu importiert.** Der gepackte Build läuft dann mit alten Daten. Darum Versionsmarke und
   Reimport nach jeder Änderung.
3. **Teleport beim Phasenwechsel im Blickfeld des Spielers.** Nur während der Abblende teleportieren.
4. **Von Hand oder per MCP angelegte Editor-Assets** (Input, Tags, DataTables, Blueprint-Kinder) ohne Notiz. Dann
   laufen die Rechner auseinander. Jedes neue Editor-Asset kommt mit Pfad in `BOARD.md` oder in den Commit-Text.
5. **Unverständliche Entdeckung.** Siehe Abschnitt 4.

## 7. Regeln für die Bau-Session

- Nach jedem lauffähigen Schritt klein committen (dv), mit Commit-Text nach der Konvention in `CLAUDE.md`.
- Nie eine Änderung der `EngineAssociation` committen.
- Bauen und testen über die Kommandozeile mit geschlossenem Editor, den Editor nur für Graubox und Spieltest. Läuft
  nachts ein Harness-Lauf, bleiben Editor und Builds aus.
- Was vom Kollegen gebraucht wird, kommt in `BOARD.md`. Seine Schichten und Ordner werden nicht angefasst.
- Vor jedem Meilenstein René kurz sagen, was kommt; fragen, wenn etwas den Umfang ändert.
- Am Ende jedes Meilensteins ein DEVLOG-Eintrag.
