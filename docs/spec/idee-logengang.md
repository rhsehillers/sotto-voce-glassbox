# Idee zur Besprechung: der verlängerte Logengang (D13, beschlossen 13.11.)

Stand 13.11. abends, René + PM. **Beschlossen ist, dass der Logengang wächst. Wie genau, besprechen René und der Kollege am
Samstag früh in der Graubox.** Keller und Neustart-Regel bleiben davon getrennt offen.

## Warum

- **Die Gewinner 2025 waren kleine, dichte Welten.** Unreal-Platz 2, *Phantom's Manor*, spielt in einem einzigen Haus
  (Durchspiel-Video 5:41), gelobt für Politur, Kunst und Ton; Platz 3, *Renaissance*, ~28 min. Die Jam 2025 lief 8 Tage,
  unsere läuft 4. Unsere **Fläche reicht** (Bühnenhalle 16 × 23 m, Logengang 16 × 3 m, Loge 4 × 4 m).
- **Zu kurz ist der Höhepunkt.** Der Weg zur Partitur ist heute ein gerades 16-m-Rohr: Proszeniumstür in der Mitte, sieben
  Meter bis zur Loge 7, Gaspard an der Tür. Es gibt keinen Anschleichweg - und "Level design & progression" ist ein eigenes
  Jury-Kriterium.
- **Raum aus Systemen statt aus neuer Grafik** (wie beim Umziehen hinter der Trennwand): Ein Gang ist modular (Wand, Tür,
  Lampe wiederholt) und billig zu verlängern; der Rest kommt aus dem, was schon läuft - Verstecke mit Blick nach draußen,
  Fahrpläne, Steam down, der Schacht.

## Was dazukommt

1. **Längerer Weg zur Loge 7.** Die Proszeniumstür wandert ans Westende des Gangs; der Weg zur Loge 7 wird doppelt so lang.
2. **Attrappen-Türen** der Logen 3 bis 6 an der Nordwand, dazwischen Nischen, Säulen, schwere Vorhänge als Deckung.
3. **Eine leere Loge als Versteck** (eine der Attrappen-Türen steht offen): Lucienne schlüpft hinein und sieht durch den
   Türspalt den Gang - der neue Blick aus dem Versteck.
4. **Der Logenschließer** als zweite Gang-Wache: läuft den langen Teil ab, eigener Fahrplan je Akt, eigene Sätze. Gaspard
   bleibt an der Loge 7. Optik: Figurvariante einer vorhandenen Figur (andere Farbe, Schlüsselbund), kein neues Modell.
5. **Was dadurch Gewicht bekommt:** *Steam down* verdunkelt einen echten Weg statt eines kurzen Rohrs; der Wartungsschacht
   (Bühne -> Rückwand Loge 7) wird zur echten zweiten Route.

## Zwei Varianten fürs Layout (Entscheidung in der Graubox)

| | A: lang | B: lang + Knick |
|---|---|---|
| Form | Gang bleibt X 0-1600 / Y 900-1200, Tür von der Bühne ans Westende | Gang wird nach Westen verlängert (bis X -900), Eingang von der Bühne an der Westecke, dann ein 90-Grad-Knick in den bisherigen Gang |
| Weg zur Loge 7 | ~14 m (heute ~7 m) | ~23 m |
| Neu | 4 Attrappen-Türen, 1 leere Loge, Nischen | dazu eine Ecke - der klassische Moment zum Vorbeispähen |
| Art-Aufwand | ~16 m Gang ausstatten (wie heute geplant) | ~25 m Gang ausstatten + eine Ecke |
| Code-Aufwand | ~2 h | ~3 h |

PM-Empfehlung: **B, wenn die Art-Seite den längeren Gang am Samstag schafft, sonst A.** Beide lassen Loge 7, Brüstung,
Valcourts Sessel und den Schacht, wie sie sind.

## Wer macht was

- **René-Seite (Code):** Graubox des Gangs (Platzierungsskript, wiederholbar), Zonen anpassen, Attrappen-Türen und die leere
  Loge als Versteck mit Blick, Logenschließer (`Data/npcs.csv`, `schedule.csv`, `barks.csv`), Tests und Screenshots.
- **Art-Seite:** Gang-Module (Wand mit rotem Samt, Logentür, Wandlampe, Säule/Nische, Vorhang) und Ausstattung aus den
  Megascans (Sofa, Kandelaber, Bilderrahmen, Marmor-Geländer), Logenschließer als Figurvariante.
- **Zeit:** Samstag früh entscheiden, Graubox bis mittags, Ausstattung nachmittags, Feature-Freeze 19:00 bleibt.

## Fragen an den Kollegen (Samstag früh)

1. Variante A oder B - was schaffst du an Gang-Ausstattung bis zum Freeze?
2. Welche Figur trägt den Logenschließer (Farbvariante von Gaspard oder vom Bühnenarbeiter)?
3. Keller ja/nein - und wenn ja, statt oder zusätzlich zum Gang?
