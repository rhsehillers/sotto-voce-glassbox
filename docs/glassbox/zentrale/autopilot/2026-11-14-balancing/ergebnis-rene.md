# Balancing-Nacht: Ergebnis für René (15.11., 09:00)

Lauf 00:10 bis 02:26, 1 Runde, Ziel erreicht. Woche 20 % → 24 %.
Der volle Bericht liegt im Käfig: `~/projects\game\megajam-balancing\bericht.md`. Dort stehen auch
`testplan.md` und die beiden Vorschlags-CSVs.
Der PM hat jeden Spielbrecher-Verdacht im Spielcode nachgeprüft (Spalte „Code sagt“).

## Taugt der Sim?
Ja. Die 6 Messwerte vom 14.11. treffen alle innerhalb von 25 %:

| Messwert | gemessen | Sim |
|---|---|---|
| Platzanweiser zurück | 47 s | 47,4 s |
| Gaspard zurück | 58 s | 54,8 / 59,1 s |
| Valcourt zurück | 63 s | 63,5 s |
| Brac zurück | 26 s | 25,0 s |
| Gang leer | 35 s | 29,3 s (−16 %) |
| Pompier-Runde | 28 s | 27,0 s |

## Route
Die geplante Route geht für einen fehlerfreien Spieler immer auf: Partitur nach 38 s, draußen nach 45 s.
1. Kittel anziehen.
2. Hebel ziehen: Falltür, Ventil, Schnürboden.
3. Talar an der Grabenwand anziehen.
4. Durch die Kulissenöffnung, dann den Streifen bei x 75 entlang.
5. Proszeniumstür, Logengang, Box 7.
6. Schacht, Bühnentür.

**Der Talar ist für Könner optional.** Es geht auch nur im Kittel, in 25 s bis zur Partitur, aber riskant: Bracs Auge
steigt bis 85 %. Für Neulinge bleibt der Talar der sichere Weg.

## Spielbrecher

| Verdacht | Code sagt | Ergebnis |
|---|---|---|
| B1/B2: Start in eigener Kleidung sofort erwischt | Außerhalb jeder Zone ist jedes Kostüm erlaubt. Die Flügel-Zone beginnt erst bei x 400. | kein Bruch |
| B3: Schacht vor dem Diebstahl nach oben | Der Code kann das Bühnenende sperren. **Korrektur 11:06:** Im Level war die Sperre nicht gesetzt (Renés Spieltest). Jetzt gesetzt und nachgelesen. | **war ein Bruch, behoben** |
| B4: Heraustreten aus dem Paravent wird gehört | Geräusch nur während der 3 s Umziehen, nur bis 6 m, durch Wände weniger | kein Bruch |
| B5: In der Pause blockiert der unsichtbare Valcourt die Partitur | Wachen außerhalb der Bühne zählen nicht als Aufpasser. | kein Bruch |
| **Flucht nach dem Diebstahl** | Nach dem Alarm sehen alle bis 4 m durch Kostüme. | **echt:** 2 s Zögern an Brac vorbei bedeutet ~50 % erwischt |
| Blinde Stelle direkt vor jeder Wache | Der Sichtkegel wird vom Auge schräg nach unten gemessen. | **echt, aber selten:** geduckt 1,25 m vor einer Wache bleibt man ungesehen. Code-Notiz für nach der Jam. |

## Schwierigkeit
Die Schätzung kommt aus einem Spielermodell und ist nicht gemessen.

| Spieler | Erwischt bis zum ersten Sieg | Zeit bis zum ersten Sieg |
|---|---|---|
| Neuling | ~3× (2–5) | ~7,5 min (5–11) |
| Geübt | 74 % schaffen es im 1. Versuch | ~2,4 min |

- Neulinge werden vor allem im Logengang vor der Tür von Box 7 erwischt, das sind ~35 % der Fänge.
- Die Hürde ist **Wissen, nicht Reflexe**: welcher Hebel wen weglockt, wo Box 7 ist, dass der Schacht zur Flucht führt.

**Urteil des Laufs:** grenzwertig. Unsere neuen Tipps nach dem Verlieren kannte er noch nicht, sie zielen genau auf
diese Hürde.

## Die 5 Vorschläge, mit PM-Rat
Alle Werte liegen innerhalb von Min/Max, es ist kein Code nötig.

| # | Änderung | Rat |
|---|---|---|
| 2 | `FillSeer` 0.20 → **0.12** | **Testen.** Das ist der stärkste Vorschlag: Die Flucht verzeiht 2 s Zögern, ohne Nebenwirkung auf die Route. Dafür sieht Brac vor dem Diebstahl langsamer durch den Talar. |
| 4 | `DarkSeconds` 30 → 45 | Kann man nehmen. Es schadet nicht, der Nutzen liegt aber im Rauschen. 45 ist das Maximum. |
| 1 | Pompier läuft in Akt 1 andersherum | **Nicht nehmen.** Es ist nur nötig, wenn der Start kaputt wäre, und laut Code ist er das nicht. Es würde den Anfang ändern, den du gut fandest. |
| 3 | Valcourt in der Pause sichtbar in Loge 4 | **Nicht nehmen.** Laut Code blockiert er die Partitur nicht. Außerdem widerspricht es dem Notizbuch. |
| 5 | `FillWrongZone` 0.5 → 0.25 | **Eher nicht.** Neulinge würden ~1× weniger erwischt, aber Kostüme würden für gute Spieler überflüssig: Ohne Kostüm kommen 77 % statt 48 % durch. Das läuft gegen das zweite Umziehen. |

**Fehler von mir:** Notizbuch-Zeile 017 sagt beim Talar noch „Behind the garden flat“. Seit gestern Abend steht der
Ständer aber an der Grabenwand. Mein Vorschlag: „East end of the wings, by the pit wall. The stage.“

## Handtest (~10 min statt 20)
T1 bis T4 sind durch den Code beantwortet. Es bleibt:
- **T5 (2 min):** Start mit `-svnotitle -svcue=Trap -svpos=450,-1100,180`. Schau, wo Brac nach dem Hebel stehen
  bleibt: ~80 cm vor dem Pult, oder sitzt er am Pult mit Blick nach Westen? Im zweiten Fall ist die Flucht noch härter
  und #2 wichtiger.
- **T6 (5 min):** Die ganze Route, ohne Schalter. Auf der Flucht bei Bracs Pult absichtlich 2 s stehen bleiben.
  Notiere: Erwischt oder nicht? Von wem?
- **Wenn jemand da ist:** einen Erstspieler 10 min ohne Hilfe spielen lassen. Nur das prüft die Schwierigkeit wirklich.

## Deine Frage „verstehen die Agenten das Ziel mit den gegebenen Infos?“
**Ja, für Zahlen und Mechanik.** Aus CSV, Karte und Code-Auszügen hat der Lauf einen Sim gebaut, der die Messungen trifft.

**Nein, für alles, was nicht mitgeliefert war:**
- Zonenregel, Schacht, Partitur-Regel, Restart: Deshalb stand B1 bis B5 offen. Ich konnte sie jetzt aus dem Code
  schließen.
- Licht
- HUD-Texte
- echte Spieler

Für das nächste Mal fehlt also mehr Code (Character, GameMode) und das HUD, nicht mehr CSV.

## Ablauf
1. Du spielst T5 und T6 im Paket von 23:44.
2. Du sagst mir, welche Vorschläge du nimmst (#2, #4, Zeile 017).
3. Ich trage sie mit deinen Worten in die CSVs ein, dann Tests, dann ein neues Paket (~30 min).

Danach gilt der Freeze ab 20:00.
