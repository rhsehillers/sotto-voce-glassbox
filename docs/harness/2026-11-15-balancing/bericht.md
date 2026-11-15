# Balancing-Nacht „Sotto Voce: The Cut“ – Bericht für Rene (15.11.2026)

Lesezeit ~10 min. Details und Rohdaten liegen in `analysis/` (Pfade jeweils angegeben). Alle Zeiten sind Sim-Sekunden
(Film nach dem Partitur-Diebstahl pausiert, nicht mitgezählt). Alles hier sind **Vorschläge** – du entscheidest.

## Kurzfassung

- **Route:** Die geplante Route geht für einen perfekten Spieler auf (Partitur 38,0 s, raus 45,3 s, 100 %). Am schnellsten
  ist eine Route nur im Kittel: 24,6 / 31,9 s. Der Talar ist optional, die Kulissen sind kein Tor.
- **Spielbrecher:** Der wichtigste Punkt ist ungeklärt: Was gilt für eigene Kleidung **außerhalb jeder Zone** (Start,
  Chor-Station, Graben)? Liest der Code das streng, wird man am Start nach ~1 s erwischt und das Spiel ist unspielbar.
  Abhilfe #1 (Pompier-Route) ist getestet. Das klärt **Handtest T1** in ~3 Minuten.
- **Schwierigkeit:** Ein Neuling wird ~3× erwischt (Band 2–5) und braucht ~7,5 min (5–11) bis zum ersten Sieg. Ein
  geübter Spieler braucht ~2,4 min und schafft es zu 74 % im ersten Versuch. **Jury: grenzwertig.** Die Hürde ist Wissen,
  nicht Reflexe.
- **Verständnis:** Ohne HUD-Texte versteht ein Erstleser nicht, was er mit der Partitur tun soll und wie Kostüme und
  Hebel wirken. Notizbuch-Zeile 017 schickt ihn an den falschen Ort. Textvorschläge stehen in Abschnitt 4.
- **Harness:** Zahlen, CSV, C++ und Karte reichten für Route, Exploits und Zahlen. Es fehlen Regeln, die in nicht
  mitgeliefertem Code stehen (Zone, Schacht, Partitur, Restart), Licht, HUD-Texte und echte Spielerdaten (Liste in Abschnitt 5).

## 0. Vorschläge, nach Rang (5 Änderungen)

| # | Datei | Änderung | Wofür | Beleg |
|---|---|---|---|---|
| 1 | schedule | `Pompier_Act1` Points → `1300 -450;1300 -1150;500 -1150;1300 -1150` | B2: Pompier steht beim Start 2,5 m vor ihr und schaut sie an | strict: 0 → 100 %; allow: 6 s Startwarten fallen weg (45,3 → 39,1 s). **Pflicht, wenn T1 scheitert**, sonst optional |
| 2 | balancing | `FillSeer` 0.20 → **0.12** | Flucht nach dem Diebstahl steht auf Messers Schneide | 2 s Zögern an 3 Punkten des Fluchtwegs: heute 63/49/76 % ok → **100/100/100 %**, egal wie Brac nach dem Hebel steht (T5). 0.15 reicht nicht: Sitzt Brac am Pult, bleibt (200,−900) bei 0 % |
| 3 | schedule | `Valcourt_Interval` Points `740 1410`, Wait 6, FacingYaw 90 | B5: Pause-Belohnung gibt evtl. nie die Partitur frei | **nur wenn T2 scheitert**; Pausen-Route 0 → 100 %, geplante Route unverändert |
| 4 | balancing | `DarkSeconds` 30 → 45 | mehr Luft im Logengang (Top-Fangzone) | Neuling −0,23 Fänge (andere Seeds: −0,13) – **im Rauschen, Nutzen unbewiesen, schadet nicht**. Keine Route ändert sich |
| 5 | balancing | `FillWrongZone` 0.5 → 0.25 | weniger Frust für Neulinge (Geschmacksfrage) | Neuling 3,4 → 2,5 Fänge, aber nur 7,8 → 7,4 min. **Nebenwirkung:** Route ohne Kostüm 48 → 77 % (n=100) |

Nebenwirkungen:
- **#1:** Geübte schaffen es im Modell im 1. Versuch nur noch zu 68 % statt 75 %. Neulinge brauchen 8,0 statt 7,8 min,
  P(≤10 min) sinkt von 0,69 auf 0,66 (n=200, im Rauschen). Die Pausen-Route dauert 9 s länger (178,2 → 187,2 s). Bracs
  höchstes Auge auf der geplanten Route steigt von 0,12 auf 0,61 (Review).
- **#2:** Brac sieht vor dem Diebstahl 40 % langsamer durch den Talar. Die Wirkung auf Neulinge (3,36 → 3,25 Fänge) liegt
  im Rauschen.
- **#3:** Valcourt steht in der Pause sichtbar in Loge 4. Das **widerspricht dem Notizbuch** („Valcourt to the foyer“).
  Der Punkt liegt 100 cm neben dem Versteck `M6_Hide_Box4` (680,1330), nicht darauf. Das Versteck in Loge 4 ist in der
  Pause dann nutzlos.

Alles zusammen (1+2+4+5), Neuling zentral, n=200, gleiche Seeds:

| | Fänge (Mittel) | Minuten (Median) | P(≤10 min) | P(≤15 min) | Geübt, 1. Versuch |
|---|---|---|---|---|---|
| heute | 3,36 | 7,8 | 0,69 | 0,88 | 75 % |
| mit 1+2+4+5 | **2,27** | **7,2** | **0,76** | **0,92** | 72 % |

Das Review hat das mit anderen Seeds bestätigt (Paket mit FillSeer 0.15): heute 3,84 Fänge, mit dem Paket 2,50. Die
geplante Route bleibt 100 % in beiden Zonen-Lesarten (39,1 s). Ohne Kostüm gewinnt ein perfekter Spieler dann aber zu 99 %
(n=100). Ohne #5 sind es 66 %, heute 48 %. Belege: `analysis/deliverable-check/difficulty_out.txt`, `escape_out.txt`,
`routes_out.txt` und `b5_out.txt` (Skript `proposal_runs.py`).

Bewusst **nicht** vorgeschlagen (getestet, aber kein Nutzen vor der Abgabe):
- `Valcourt_*` FacingYaw −120: stoppt S4, macht Box 7 aber für Neulinge härter; Schwierigkeit dafür ungetestet.
- `HearSneak` 150: NEW-2, macht das Spiel schwerer.
- `CueCooldown` 40: stoppt nur die Fly-Kette.
- `Decay` 0.08: keine Wirkung auf S7.
- Gadget-Werte: keine Wirkung.
- `Brac` FacingYaw 0: keine Wirkung.

`SuspiciousLevel` ist **kein Hebel**: Der Code nutzt den Wert nicht. Die Wache wird schon bei `NoticeLevel` 0.25 misstrauisch.

## 1. Routen

| Route | Hebel | Kostüm | Partitur | raus | Erfolg (perfekter Spieler) |
|---|---|---|---|---|---|
| geplant (r00) | Trap, Steam, Fly | Kittel → Talar | 38,0 | 45,3 (A) | 100 % |
| schnellste (r10): nur Kittel, Streifen + Gang laufen | Trap, Steam, Fly | Kittel | 24,6 | 31,9 | 100 % (Brac-Auge bis 0,85) |
| nur Kittel (r01) | Trap, Steam, Fly | Kittel | 29,8 | 37,1 | 100 % |
| durch den Graben statt Kulissenöffnung (r12) | Trap, Steam, Fly | Kittel → Talar | 35,5 | 42,8 | 100 % |
| ohne Kostümwechsel (r02) | Steam, Fly, Trap | eigene | 32,1 | 39,5 | 48 % (Brac auf der Flucht) |
| Pause, ein Hebel (r05) | Steam | Kittel | 170,9 | 178,2 | 100 % (wenn B5 nicht greift) |
| Ende B, wartet im Graben bis 7:30 (r08) | Trap, Steam, Fly | Kittel → Talar | 38,0 | 451,9 (B) | 100 % |
| überall rennen (r09) | Trap, Steam, Fly | Kittel → Talar | – | – | 0 % (Pompier) |

**Geplante Route Schritt für Schritt** (`sim/README.md`):

| t (s) | Schritt | Fenster, das sie braucht |
|---|---|---|
| 0–6,2 | an der Bühnentür warten | Pompier > 6,5 m von Paravent 1 (er läuft nach Osten) |
| 6,2–11 | Kittel an Paravent 1 (290,−1280) | niemand < 6 m (Umziehgeräusch), niemand < 2 m |
| 11,9 / 13,5 / 14,4 | Hebel Trap (420,−860), Steam (700,−1370), Fly (1000,−1370) | Reihenfolge West → Ost |
| 17–21,5 | Talar an Paravent 2 (1490,−860) | Pompier unterwegs zum Fly-Ziel; der häufigste Neulingsfehler ist hier ein unpassendes Timing |
| 21,5–32 | Kulissenöffnung x 900–1100, an den Kulissen nach Westen, Streifen x 75 nach Süden, Proszeniumstür (120,826) | Brac/Valcourt an der Falltür (600,0), > 4 m Abstand zu Brac |
| 32–38 | dunkler, leerer Logengang → Tür Box 7 (1400,1164) → Partitur (1520,1520) | Gang leer ab ~10 s nach den Hebeln für ~30 s, dunkel 13,5–43,5 s; Box 7 ~55 s frei, sobald Valcourt geht |
| 38,4–45,3 | Schacht → Bühne (80,650), Streifen nach Norden an Brac vorbei, Bühnentür (0,−1150) | **nicht stehen bleiben**. Valcourt ist ~20 s nach dem Diebstahl zurück |

Vor dem Diebstahl ist die Route robust: 1–8 s Pause an 9 Punkten, langsameres Gehen und längere Interaktionen ändern
nichts (100 %). **Nach dem Diebstahl steht sie auf Messers Schneide.** Nach dem Alarm sehen alle innerhalb von 4 m durch Kostüme.

| 2 s Zögern bei | (75,−745) | (200,−760) | (200,−900) | (200,−1150) |
|---|---|---|---|---|
| erwischt, Brac bleibt nach dem Hebel 80 cm vor dem Pult stehen (Sim-Standard) | 37–40 % (Brac) | 45 % (Brac) | 50 % (Brac) | 24–27 % (Pompier) |
| erwischt, Brac sitzt am Pult und schaut nach Westen (Settle 90) | 0 % | – | **100 %** (Brac) | 27 % (Pompier) |
| erwischt, mit #2 (FillSeer 0.12), beide Fälle | 0 % | – | 0 % | 0 % |

Welcher Fall im Spiel gilt, klärt Handtest T5. Belege: `analysis/sim-review/escape.txt`,
`analysis/deliverable-check/escape_out.txt`. Die Pause in Akt 2 ist die „Belohnung fürs Zuschauen“ und
funktioniert mit einem Hebel oder sogar ohne Hebel (Gadget lockt Gaspard). Das gilt aber nur, wenn B5 nicht greift.

## 2. Wege, die das Spiel brechen

Status: **Sim** = im Sim bestätigt; **Handtest** = nur statisch oder Code fehlt, Test in `testplan.md`.
Abhilfe zuerst über Daten. Code und Karte stehen nur als Notiz da.

| ID | Was | Wo | Status | Abhilfe (Daten) | Notiz Code/Map |
|---|---|---|---|---|---|
| B1 | Zonen decken die Flügel nicht ab: Start, Chor-Station und Graben haben keine Zone | Start (250,−1150), Kittel-Ständer (150,−1330), Chor-Ständer (1550,−1010), Graben x 1210–1580, Pult (1330,−90) | Sim (beide Lesarten) + **Handtest T1** | „allow“: Kostüme optional, Graben (1500,−300) ist ein sicherer Raum (413 s), Ende B in eigener Kleidung 100 %. „strict“: unspielbar → #1 | Map: `M1_Zone_Wings` auf x 0–1600, Graben-Zone |
| B2 | Pompier steht beim Start 250 cm vor ihr und schaut nach Westen | (500,−1150) | Sim (strict: 100 % erwischt bei ~1 s) | **#1** | – |
| B3 | Schacht schon vor dem Diebstahl nach oben nutzbar? | Bühnenende (20,650) → Box 7 (1300,1580) | **Handtest T3** | – | Code: Schacht nur in eine Richtung. Falls offen: Partitur nach 23,8 s nur mit Trap |
| B4 | Aus dem Paravent treten wird evtl. von allen Wachen „gehört“ | Paravents (290,−1280), (1490,−860) | **Handtest T4** | – | Code (IsBehindScreen-Flag). Sim schlimmster Fall: alle Laufwege abgebrochen, Route bleibt 100 % |
| B5 | Pause: versteckter Valcourt 99 cm neben der Partitur blockiert sie evtl. | (1450,1450) | **Handtest T2** | **#3** | Code: Partitur-Regel soll Off-Stage-NPCs ignorieren |
| Flucht | 2 s Zögern an Brac vorbei bedeutet 37–50 % erwischt (sitzt Brac am Pult: bei (200,−900) 100 %) | (75,−745)…(200,−900), (200,−1150) | Sim | **#2** | – |
| S4 | Gadget lockt Valcourt direkt neben der Partitur weg | Wurf ~(1300,1400) | Sim 100 % (langsamer: 44,7 s) | keine – legitime Alternative | – |
| S5 | Hebel erneut ziehen verlängert das Wegschicken | Trap-Fenster 56 → 107 s bei 3× ziehen | Sim, geringe Wirkung | keine | – |
| S7 | Verstecken im Blick der Wache setzt das Auge zurück | Verstecke (900,−1350), (1150,−740), (250,1160), (680,1330) | Sim (100 % überlebt bei Auge 0,95) | Decay hilft nicht | Code: „hat sie verschwinden sehen“ |
| NEW-1 | Blinde Scheibe vor jeder Wache: stehend < 121 cm, geduckt < 182 cm | z. B. 1,25 m vor Valcourt geduckt: 30/30 ungesehen | Sim (hängt an der Augenhöhe) + Handtest „Blinde Scheibe“ (Zusatz im Testplan) | – | Code: Kegel in 2D prüfen |
| NEW-2 | Schleichen wird nie gehört (HearSneak 80 < Höhenabstand 105) | überall | Sim | HearSneak 150 getestet, nicht vorgeschlagen | – |
| Lauf | Hört eine Wache Schritte, bricht sie ihren Hebel-Auftrag ab (Platzanweiser an den Kulissen) | an den Kulissen y −745 | Sim (codegetreu) | – | Code: nur bei Sicht abbrechen |
| Settle | Brac/Valcourt kommen nach einem Hebel nie richtig an (82 vs. 60 cm) und schauen danach falsch | Bracs Pult (250,−650) | Sim + **Handtest T5** | #2 deckt beide Fälle | Code: Settle-Radius ≥ 90. **Achtung:** Dann sitzt Brac richtig und die Flucht wird härter ((200,−900) 0 % ok ohne #2) – nur zusammen mit #2 |
| Text | Notizbuch 017: Talar „hinter der Garten-Kulisse“ (190,−350), der Ständer steht aber bei (1550,−1010) | – | sicher (statisch) | Text, siehe Abschnitt 4 | – |

Kein Bruch, sondern Alternativen: S1 (Kulissen sind kein Tor: Graben-Lücke x 1210–1579 / Geländerlücke x 1200) und S2
(Talar optional, Streifen x 75 hinter der Palast-Kulisse). Quellen: `analysis/exploits/findings.md`,
`analysis/map-scan/findings.md`.

## 3. Schwierigkeit

Spielermodell auf dem Sim (14 Fehlerklassen, Lernen zwischen Versuchen). **Die Menschen-Annahmen sind nicht validiert.**
Deshalb Bänder (optimistisch – zentral – pessimistisch).

| | Fänge bis zum 1. Sieg (Median) | Minuten bis zum 1. Sieg (Median) | P(Sieg ≤ 10 min) | P(≤ 15 min) |
|---|---|---|---|---|
| Neuling | **3** (2–5) | **7,4** (5,4–10,6) | 0,68 (0,44–0,85) | 0,88 (0,72–0,95) |
| geübt | 0 (1. Versuch 74 %, 60–88 %) | 2,4 (1,5–2,9) | 0,99 | 1,00 |
| Neuling zentral, n=200, gleiche Seeds: heute → mit #1+2+4+5 | 3 → 2 (Mittel 3,36 → 2,27) | 7,8 → 7,2 | 0,69 → 0,76 | 0,88 → 0,92 |

- **Wo Neulinge erwischt werden:** Logengang vor der Tür von Box 7 (x 900–1500, y 1050) ~35 %, Paravent 2 (Pompier hört
  das Umziehen) 7 %, Pompier-L in eigener Kleidung 6 %, Kittel auf der Bühne 8 %.
- **Was am meisten kostet** (ohne diesen Fehler): falsche Flucht ohne Schacht −0,7 Fänge / −1,3 min; Steam- oder
  Fly-Hebel vergessen je −1,3 min; Box 7 nicht finden −0,9 min. Reaktionszeit spielt keine Rolle.
- **Stärkster Zahlenhebel unter den geprüften:** `FillWrongZone`. Bei Min 0.15 gibt es −1,4 Fänge, bei 0.25 −0,84, bei
  0.35 fast nichts. Er senkt Fänge, aber kaum die Zeit. Der Min/Max-Test lief nur für 8 von 23 geplanten Werten
  (`sensitivity.txt`), ist also unvollständig. FillSeer 0.12 ist aus einem eigenen Lauf, in der Wirkung auf Neulinge im Rauschen.

**Jury-Urteil:** Grenzwertig. Ein Neuling wird ~3× erwischt und braucht ~7,5 min. Etwa jeder Dritte (Band jeder Siebte
bis jeder Zweite) hat nach 10 min noch nicht gewonnen, etwa jeder Achte nach 15 min nicht. Mit 10–15 min ist das knapp
machbar. Die Hürde ist Wissen (welcher Hebel lockt wen, Talar für die Bühne, Schacht zur Flucht, wo Box 7 ist). Deshalb
helfen die Texte aus Abschnitt 4 vermutlich mehr als jede Zahl. Das Vertrauen ist niedrig bis mittel: Fehlen die
HUD-Texte, kann ein echter Neuling auch schlechter liegen als das pessimistische Band.
Quellen: `analysis/difficulty/out/summary.txt`, `profiles.txt`, `mistakes.txt`, `sensitivity.txt`, `catch_hotspots.csv`.

## 4. Versteht ein Neuling das Ziel?

Ein Blindleser hat nur `notebook.csv` und die AwayTexts bekommen, keine HUD-Ziele und keine Tipps (die fehlten im
Material). Ergebnis (`blind/comprehension.md`):
- Er weiß nicht, **was er mit der Partitur tun soll**: stehlen, tauschen oder die Coda schreiben?
- Er weiß nicht, **wie man verliert**.
- Er weiß nicht, **wie Kostüme und Hebel funktionieren** und **wo Dinge sind** (Box 7, Hebel, Ständer).
- Bühnenjargon bleibt unerklärt (Fly winch, Trap, garden flat).
- Zeile 017 schickt ihn an den falschen Ort.
- Zwei AwayTexts sind leer.

Textvorschläge (englischer Spieltext, wichtigste zuerst):

| Wo | Text |
|---|---|
| HUD-Ziel Start | `Take the score from box 7. Get out through the stage door.` |
| HUD-Ziel Finale | `Or lay the score on the conductor's desk (7:30-8:10).` |
| HUD-Tipp Start | `Wrong clothes in sight fill their eye. Full eye: caught, the evening restarts.` |
| HUD-Tipp Wings | `Levers in the wings lure guards away. Watch who leaves.` |
| HUD-Tipp nach dem Diebstahl | `Alarm - they see through costumes now. Take the shaft in box 7 down to the stage.` |
| Notizbuch 017 Chorus | `East end of the wings, by the auditorium wall. The stage.` |
| Notizbuch 013 Brac | `Trap lever too. Sees through any costume - keep 4 m.` |
| Notizbuch 004 Act 1 | `Valcourt in box 7 (end of the box corridor), the score beside him. Gaspard at the door.` |

Bitte prüfen, ob das HUD diese Dinge schon sagt. Das Material hatte keine HUD-Texte, also kann ich es nicht beurteilen.

## 5. Verstehen die Agenten das Ziel mit den gegebenen Infos? Reichen Zahlen/CSV?

**Ja für die Mechanik:**
- Aus `rahmen.md`, den CSVs, `map.json` und dem C++-Markdown haben die Agenten einen kalibrierten Sim gebaut:
  14 von 17 Messungen liegen innerhalb von 1,2 s, die Rechenregeln sind 1:1 übernommen (54 Prüfungen).
- Daraus kamen die Routen, die Exploits und getestete Daten-Abhilfen.
- Der Harness hat dabei zwei Fehler im Brief gefunden: „suspicious 0.6, er kommt nachsehen“ widerspricht dem Code, und
  Notizbuch 017 nennt den falschen Ort.

**Nein für:**
- Regeln, die in nicht mitgeliefertem Code stehen.
- Licht.
- Echte Menschen.
- Das Verständnis (HUD).

Zahlen/CSV allein reichen nicht. Die wichtigste offene Frage (B1/B2) ist eine Code-Regel.

| Lücke im Material | Folge | gefunden von |
|---|---|---|
| `SVCharacter`: Kostüm/Zone außerhalb jeder Zone, Vorrang bei überlappenden Zonen, wann IsBehindScreen gelöscht wird, Kapsel/Ducken, Augenhöhe | B1/B2 nur als zwei Lesarten; B4 und NEW-1 offen | Sim, Map-Scan, Review |
| Code für Partitur-Regel, Schacht, Gadget, Verstecke, Pult, Ausgang | B3, B5 und S4 nicht entscheidbar | Map-Scan, Exploits |
| GameMode/Clock: Restart, Checkpoints (`bCheckpoint=True` vs. „keine Checkpoints“), Teleport beim Phasenwechsel, wer beim Diebstahl ApplyPhase bekommt, Start der Hunt-Routen | Annahmen 10, 11 und 14 | Sim |
| Lampen: Positionen und Helligkeit | `ShadowSightFactor`/`LitLux` nur als Band (hell = schlimmster Fall) | Sim |
| Blocker-Unterkanten/Stürze, Türzustände, Navmesh, Interaktionsreichweiten, Triggergrößen | Annahmen 4 und 8; Trap-Hebel durch die Wand bedienbar (150 cm ignoriert Wände) | Sim, Exploits |
| HUD-Texte (Ziele, Tipps, Steuerung, Prompts), leere AwayTexts | Verständnistest nur halb | Blindleser |
| Engine-Bewegung: Drehraten, Bremsen, Settle | ±1–3 s; Bracs Blickrichtung auf der Flucht hängt daran | Review |
| Nur ein Messszenario (alle Hebel) und keine Spielerdaten | Fluchtweg und Menschenmodell unkalibriert | Review, Schwierigkeit |
| 16 Balancing-Werte werden von keinem mitgelieferten Code gelesen | Wirkung nur aus `rahmen.md` | Map-Scan |

**Für das nächste Harness-Paket, nach Rang:**
1. HUD-Texte, Steuerung und Prompts plus `map.png` mit Legende. Dann wird der Verständnistest echt.
2. `SVCharacter`, GameMode und Clock-Code (Zonenregel, Restart, Phasenwechsel). Damit fallen B1/B2 und die Annahmen
   10/11/14 weg.
3. Code für Partitur, Schacht, Gadget, Verstecke und Pult (B3, B5, S4).
4. Ein `-svwindowlog` einer von Hand gespielten geplanten Route plus `-svcue=Trap` allein (Fluchtweg und Bracs
   Blickrichtung kalibrieren).
5. Lampen (Position, Candela).
6. Blocker-Unterkanten, Türzustände, Interaktions- und Triggergrößen, Augenhöhe, Kapselmaße.
7. 2–3 echte Erstspieler-Protokolle (Fänge, Minuten, wo) zum Validieren des Menschenmodells.
8. Engine-Parameter (Drehraten, Bremsen) und ein Brief, der mit dem Code übereinstimmt (SuspiciousLevel).

## 6. Wie belastbar?

| Kalibrierung (`sim/README.md`, `analysis/sim-review/review.txt`) | gemessen | Sim |
|---|---|---|
| Hebel-Zeiten (Valcourt 6/14/63, Brac 8/20/26, Gaspard am Ventil 18, Box 7 frei 55 s) | wie links | ±1 s (14 von 17 Zeilen ≤ 1,2 s) |
| Pompier-Runde und Wendepunkte | ~28 s, x 1218 / (1290,−532) | 27,0–27,3 s, 3 cm / 1 cm |
| 3 Abweichungen (Gang leer bis, Gaspard zurück, Finale-Runde) | 47 / 58 / ~28 | 40,1 / 54,8 / 24,7. Erklärt mit der Definition von „zurück“; plausibel, nicht bewiesen |

**Hauptannahmen:**
- **Außerhalb jeder Zone ist jedes Kostüm erlaubt.** Mit der strengen Lesart ist das Spiel unspielbar (→ T1).
- **Überall hell**, also der schlimmste Fall für sie. Im Schatten bleibt die Route 100 %.
- Interaktionen bis 150 cm, sofort ausgelöst.
- Phasenwechsel ohne Teleport.
- **NPCs außerhalb der Bühne ignorieren Hebel** (`sim/svsim/guard.py:282`). Im C++ (`OnCue`) gibt es diese Prüfung nicht:
  Platzanweiser und Valcourt bekommen in der Pause den Hebel-Auftrag trotzdem. Das betrifft B5, Vorschlag #3 und T2.
- Brac bleibt nach einem Hebel 80 cm vor dem Pult stehen (Code-Settle-Test 60 cm). Sitzt er doch richtig (T5), wird die
  Flucht ohne #2 härter.

**Was der Sim nicht sagen kann:**
- Alles, was im fehlenden Code steht (B3, B4, B5, Restart, Zonenregel).
- Echtes Licht, Kamera, Animation und Gefühl.
- Ob Menschen die Fenster sehen. Die Schwierigkeit ist ein Modell, keine Messung.
- „200/200“ heißt: Ein bildgenauer Spieler schafft es immer. Das ist keine Erfolgsquote für Menschen.
