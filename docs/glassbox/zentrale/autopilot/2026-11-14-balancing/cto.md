# CTO-Urteil - megajam/2026-11-14-balancing

Geprüft 2026-11-15 00:05 (CTO-Session). Antrag vom megajam-PM (#224), zweiter Antrag von megajam. Freier Lauf in einem
NEUEN leeren Käfig `megajam-balancing`. Wortlaut des Nutzers, im Transkript der PM-Session geprüft:
- das Ziel (14.11. 23:32);
- „habe jetzt auch chrome beendet … 5-stunden fenster ist eher das problem, wochenvolumen ist noch genug vorhanden ;
  update ist pausiert ; sende den antrag" (15.11. 00:00).

`check` -> **gelb** (`pruefung.json` 00:0x), `preview` gelesen.

## Käfig vorbereitet (CTO, 00:0x)
- `newcage.php megajam-balancing --work ~/projects/game/megajam-balancing --owner megajam --free`.
  - Pitch = das `## Goal` (Renes Worte, wörtlich).
  - Phase setup, Image `zentrale-cage:1` (Python-Standardbibliothek, wie beantragt).
  - Kickoff `free`: `kickoff.md` zitiert nur den Satz als „User said".
- `cage_audit --live`: alles grün. Kein Netz außer Modell AND Engram-Suche; Engram `/missing`, `/propose`, `/register`
  abgewiesen; kein Token; nicht root.

## Urteil
- **Ziel (frei, 630 Z., gelb):** Renes Wortlaut, ein Ausschnitt seiner Nachricht. Davor stehen nur Spieldesign-Sätze an
  den PM. Tragbar.
- **Material (`rahmen.md`):** Es gibt viel Plan für einen freien Lauf: 2D-Simulation, Dateien, Spalten, Testplan.
  - Tragbar, weil das Ergebnis Sonntag 08:00 brauchbar sein muss AND Renes zwei Wünsche abbildet („rein an zahlen" +
    „plan wie wir das game sinnvoll testen").
  - **Lesart:** Renes Frage „verstehen die agenten das ziel mit den gegebenen infos? … muss da etwas erweitert werden"
    fragt, ob das MATERIAL reicht. Der Brief macht daraus Punkt (4): „versteht ein Neuling das Ziel aus HUD, Notizbuch".
  - Der Loop bekommt Renes Satz wörtlich im Kickoff, er kann also beides beantworten. Der PM sollte am Morgen Renes
    eigene Frage beantworten. Sie steht als versiegelte Erwartung (6) im Antrag.
- **Hypothesen:** H1/H0, die Entscheidungsregel AND die 6 Erwartungen des PM stehen vor dem Lauf fest AND sind
  versiegelt. Die Vorschau zeigt sie nicht.
- **Leck (vom CTO geprüft):**
  - Lieferung: 13 Dateien, 0,1 MB, nur md/json/csv. `rahmen.md` habe ich ganz gelesen, die übrigen nach den Erwartungen
    durchsucht.
  - Erwartungen (1), (3), (4), (5) AND (6) stehen nicht im Material.
  - Zu (2): `rahmen.md` nennt die Spielregel „it can be picked up again". Die Regel braucht der Loop zum Simulieren; den
    Schluss „endlose Köder" zieht er selbst. Das ist ein kleiner Schubs, kein Leck, und die Erwartung entscheidet nichts.
  - Die 6 Messwerte von H1 stehen im Material. Das ist gewollt, sie dienen zum Kalibrieren.
  - Personen nur mit Vornamen (Rene), keine E-Mail-Adresse.
  - Text-Scan (`textscan.py`): 1 Treffer, ein BOM mitten in `SVSuspicionComponent.cpp.md`. Es ist der Anfang der
    kopierten C++-Datei hinter ```cpp, also harmlos. Keine an Agenten gerichteten Sätze, Befehle, URLs oder Geheimnisse.
- **Was der Lauf zuerst sieht:** einen leeren Arbeitsordner (README, Branch `main`) AND `inbox/2026-11-14-balancing/`.
  Kein Loop-State, kein altes `status.json`.
- **Ressourcen:** 3 CPUs, 2 GB (grün; VM 4 CPUs, 3,8 GB).
- **Budget (gemessen 00:0x mit dem Lauf-Token):**
  - **5-h-Fenster: 8 %, Rücksetzen 01:00.** Bis 01:00 ist reichlich Luft: Selbst bei 69 pp/h kommt der Stopp nicht vor dem
    Rücksetzen.
  - Das nächste Fenster beginnt mit dem Lauf um ~01:00 AND setzt ~06:00 zurück, also vor dem Start des Teams. Darin darf
    der Lauf bis `five_hour` arbeiten.
  - Bei der Mehr-Agenten-Höchstrate (69 pp/h) stoppt er bei 80 % gegen 02:10, bei 90 % gegen 02:20. Bei normaler Rate
    (Median 11 pp/h) läuft er bis zur Zeitgrenze.
  - **Woche: 20 %**, Rücksetzen Do 13:00. Der Antrag erlaubt +10 pp, also Stopp bei 30 %.
  - **Die Woche ist im ungünstigsten Fall die engere Grenze:** konzepte (opus, 9 Agenten) zog 7,7 pp/h, das hieße Stopp
    nach ~80 min. +15 pp (Rahmen-Maximum) lässt nach dem Lauf noch 65 % für den Sonntag, genug für Renes Sessions.
  - **Warteschlange (Frage des PM):** nicht nötig, eher schädlich. Vor 01:00 greift der Stopp nicht. Ein zweiter Lauf
    nach dem nächsten Rücksetzen (~06:00) würde das Morgenfenster des Teams verbrauchen.
- **System (00:05):**
  - Netzteil (100 %); kein Unreal, kein Spiel, kein Chrome; Host-RAM 5,2 GB frei.
  - C: 97 GB frei; Docker läuft.
  - Update-Pause bis So 23:59, kein Neustart offen.
- **Abo-Messung:** Der `check` meldet „probe failed": Die Anmeldung der Kommandozeile `claude` auf dem Host ist
  abgelaufen („OAuth session expired").
  - Der Lauf nutzt einen eigenen Token (`ZENTRALE_LOOP_TOKEN`), mit ihm hat die Probe 00:0x geklappt. Für den Lauf ist
    das also kein Hindernis.
  - Nach dem Jam: `claude` im Terminal starten AND `/login` (die Anmeldung macht der Nutzer). Sonst misst `check` die
    Auslastung nicht.
- **Nach dem Lauf:** CTO-Nacharbeit (summary, Git-Zahlen, Last). Der PM liest read-only AND schreibt Rene eine Seite.
  Ein Export ins Spiel-Repo nur auf Bitte des PM mit Renes Worten (`export.php`). Code nie, nur seine Ergebnisse.

## Freigabe-Anfrage an den Nutzer
**Frage:** Balancing-Lauf jetzt freigeben? Freier Lauf, opus, 6 Runden, 240 min (bis ~04:10).

**Empfehlung:** Ja, jetzt starten. Dabei die Grenzen auf `--week-pp 15 --five-hour 90` setzen (Rahmen-Maximum):
- Die Woche ist bei vielen Opus-Agenten die engere Grenze. Nach dem Lauf bleiben mindestens 65 % für den Sonntag.
- Das Fenster ab ~01:00 setzt gegen 06:00 zurück, bevor ihr anfangt.

Kein Leck, Hypothesen vorab fest, Käfig geprüft, Laptop bereit.

**Alternativen:**
- So wie beantragt (+10 pp, 80 %). Bei vielen Agenten endet der Lauf dann eher nach 1-1,5 h.
- Sonnet statt Opus: etwa halb so viel Verbrauch je Stunde, für Simulation AND Zahlen reicht es.

**Wenn keine Antwort:** kein Start. Der Käfig bleibt leer stehen.

## Freigegeben AND gestartet (2026-11-15 00:10)
Nutzer-Wortlaut: „Ja, mit 15/90".
- **Vorher geprüft:** kein `UnrealEditor`/`UnrealBuildTool`/Spiel, Netzteil dran.
- **Freigabe:** `release --said "Ja, mit 15/90" --week-pp 15 --five-hour 90` (check gelb).
- **Start:** `start` 00:10:08, Lauf `20261115-001016`.
- **Startprüfung:**
  - `status` LAUFEND, Runde 1/6. Container `zcage-megajam-balancing` up 00:10:29, `docker inspect` 2 GB/3 CPUs.
  - run.json: mode free, Grenzen 6/240/15/90/opus/120/1/3/2, Woche 20 % (Stopp 35 %), 5-h 8 %, `loop_state: none`
    (neuer Käfig), C: 97,2 GB.
  - Lieferung `inbox/2026-11-14-balancing/` vollständig: 13 Dateien + MANIFEST + .gitattributes. Hardlinks (Linkzahl 2),
    Commit `444a7b7`, `user_said` „Ja, mit 15/90".
- Zeitgrenze ~04:10. Aus dem laufenden Käfig liest der CTO nichts.

## Nacharbeit AND Export (2026-11-15 09:4x)
- **Lauf:** 00:10 -> 02:26, goal reached, 1 Runde, 67 Züge, 10 Agenten inkl. QM, 495 Aufrufe, 39,17 USD-Äquivalent.
- **Budget:** Woche 20 -> 24 %; 5-h 8 % -> Rücksetzen 01:00 -> 20 %. Die Grenzen 15/90 banden nicht.
- **Last:** RAM 0,36 GB von 2 GB, CPU 299 %, 175,2 CPU-min; Größe +2,4 MB.
- **Git:** Arbeitsordner 17 Commits bis `2f83c47`, Projektordner 1 Commit; nichts ungesichert, nichts verschwunden.
  Lieferung unverändert (13/13 Prüfsummen).
- **Export (PROZESSE 9.7, PM #230):** Renes Worte im PM-Transkript geprüft (15.11. 09:41): „eintragen und auch den
  harness report mit verweis dass ein harness lief mit ins git". 10 Dateien aus `2f83c47` ->
  `megajam/docs/harness/2026-11-15-balancing`, Scan ohne Treffer, `EXPORT.json` ohne Host-Pfade.
- **Hinweis:** `bericht.md` nennt Belege, die nicht mit exportiert sind (`analysis/deliverable-check/*`,
  `analysis/difficulty/out/profiles.txt` u. a.). Sie bleiben im Käfig, Stand `2f83c47`.
- Käfig bleibt offen bis zum Abschlussbericht des PM.
