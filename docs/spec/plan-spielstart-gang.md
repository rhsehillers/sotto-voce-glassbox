# Plan: Spielstart im Gang mit Vorspann (D20, beschlossen 14.11.)

Stand 14.11. 11:56, René + Mehmet (Besprechung am Vormittag), ausgearbeitet vom PM. René: *"Er baut die start story und
dann gehts in den gang mit den besprochen stilmitteln ... dann plane es einmal, den start des spiels im gang"*.

## Der Ablauf

1. **Titelkarte** - *Begin the evening*.
2. **Cold Opener (Mehmet):** leitet die Geschichte ein - warum, was ist passiert. Er endet mit Lucienne im Bühneneingang,
   die Kamera hinter ihr.
3. **Prolog im Gang:** Sie läuft selbst. Kein HUD, keine Opernuhr, niemand nimmt sie wahr. Hinter der Wand hört man
   gedämpft das Orchester (Akt 1). Unten rechts erscheinen nacheinander die Namen - dezent, wie im Vorspann eines
   90er-Films oder in *Death Stranding*: zuerst die KI-Instanzen als Mitentwickler, am Ende Mehmet und René.
4. **Die Bühnentür:** Sie geht auf, Lucienne tritt in die Seitenbühne. Die Aktglocke schlägt, die Uhr startet bei 0:00, die
   Musik setzt voll ein, das HUD blendet ein, das Ziel-Banner erscheint. Ab hier läuft das Spiel wie bisher.
5. Die letzten Namen laufen leise weiter, bis die Liste durch ist.

## Die Regeln

- **Balancing bleibt unberührt:** Der Prolog zählt nicht zur Spielzeit. Die Uhr startet erst an der Bühnentür.
- **Vorspann auf Zeit, nicht an festen Punkten.** Lucienne läuft fest 3 m/s; für 7 Namen à 3,5 s bräuchte es sonst
  ~75 m Gang. Darum: Der Vorspann startet mit ihrem ersten Schritt, jede Karte steht ~3,5 s (0,6 s ein, 2,3 s stehen,
  0,6 s aus), eine nach der anderen. Zurückgehen blendet nichts neu ein. Der Gang dauert ~6 s, der Rest des Vorspanns
  (~20 s) läuft in den ersten Sekunden von Akt 1 weiter, in denen an der Bühnentür wenig passiert.
- **Einmal pro Spielstart:** Der Vorspann kommt nur am ersten Abend nach dem Programmstart. Ein neuer Abend über die
  Titelkarte geht durch Cold Opener (mit Enter überspringbar) und Gang, aber ohne Namen.
- **Nach Erwischt oder R:** Neustart wie heute an der Bühnentür innen - kein Cold Opener, kein Gang (D11 unverändert,
  kein zusätzlicher Zeitverlust je Versuch).
- **Die Tür hinter ihr:** Nach dem Prolog bleibt die Bühnentür zu; zurück in den Gang geht es nicht. Mit der Partitur ist
  sie der Ausgang für Ende A wie bisher - sie kam durch diese Tür und geht durch sie.
- **Im Gang:** Laufen, Schleichen, Rennen und Esc (Pause) gehen; Interagieren und Gadget erst ab der Tür. Ihre Schritte
  sind zu hören. Steht sie 4 s still, erscheint unten links leise "WASD - walk".

## Der Gang (Vorschlag, Ort mit Mehmet abstimmen)

Westlich der Bühnentür (Rückwand x = 0, Türöffnung um y = -1150) steht nichts - geprüft, kein Actor bei x < -40.
Vorschlag: ein **L-förmiger Bühneneingang, ~16 m**:

| Teil | von | bis | Länge |
|---|---|---|---|
| Schenkel 1 (vom Straßeneingang) | (-900, -400) | (-900, -1150) | 7,5 m |
| Schenkel 2 (zur Bühnentür) | (-900, -1150) | (0, -1150) | 9 m |

Breite 2,5 m, Höhe 3,5 m (Platz für die Schulterkamera). Graubox von uns (Labels `M7_*`, nichts Bestehendes wird
umbenannt), Ausstattung von Mehmet (Putz, Gaslampen, Anschlagbrett, Pförtnerloge - seine Wahl). Das Licht dort ist
reine Stimmung, es wirkt nicht aufs Spiel.

## Schnittstellen mit Mehmet

| Was | Wie |
|---|---|
| Cold Opener -> Prolog | wie bisher: `OnColdOpen` startet seine Sequenz, am Ende ruft er `SkipIntro()` - das führt jetzt in den Prolog statt direkt ins Spiel |
| Startpunkt im Gang | ein Actor mit Tag `SV_PrologueStart` (Position + Blickrichtung); seine Sequenz endet mit der Kamera hinter Lucienne dort |
| Bühnentür | sein Türblatt bekommt den Tag `SV_PrologueDoor` (Pivot an der Angel): wir drehen es auf, wenn sie kommt, und schließen es hinter ihr. Wer lieber selbst animiert: Ereignis `OnPrologueDoor` im Blueprint |
| Namen | `Data/credits.csv` (Rolle, Name) - Wortlaut und Reihenfolge legen René und Mehmet fest; das Aussehen (Schrift, Platz, Farbe) stimmt Mehmet im HUD |
| Musik | kein neues Stück: im Gang die gedämpfte Akt-1-Spur ("hinter der Wand"), an der Tür die volle. Sein Cold Opener darf `Music.Intro` behalten, sie blendet am Gangbeginn über |

## Vorspann - Entwurf (René und Mehmet entscheiden)

1. *Produktlicht presents*
2. Code & project management - Claude (René's session)
3. Art, story & film - Claude (Mehmet's session), with Codex, Tripo, Hyper3D Rodin and Blender agents
4. Music & sound - the Music PM (Claude), synthesized in Python
5. Stage floor - the image instance, generated in code
6. Story & art - Mehmet
7. Code & production - René

## Aufwand und Reihenfolge (Code-Seite, ~2,5 h)

1. Flow-Zustand *Prolog*: Uhr steht, Wahrnehmung aus, Schritte an, Pause erlaubt; der Neustartpunkt bleibt an der
   Bühnentür innen (45 min)
2. Gang-Graubox (`Tools/Editor/place_m7.py`), Startpunkt, Tür-Auslöser (30 min)
3. Vorspann: `Data/credits.csv`, Einblendung unten rechts, einmal pro Programmstart (45 min) - dafür braucht unsere
   Seite `UI/SVHUD.*` noch einmal kurz (Ansage auf dem BOARD)
4. Musik gedämpft im Gang, Aktglocke an der Tür (20 min)
5. Tests, Paket (20 min)

Prüfschalter: `-svnotitle` startet wie bisher direkt an der Bühnentür im Spiel (alle bisherigen Prüfungen bleiben
gültig); neu `-svprologue` startet im Gang.

**Rückfall, falls die Zeit vor dem Freeze (19:00) knapp wird:** Vorspann ohne Gang - die Namen laufen in den ersten
~25 s von Akt 1 an der Bühnentür; die Uhr läuft dann ab dem Start.

## Offen

1. Ort des Gangs (Vorschlag oben) - Mehmet
2. Tür: Tag zum Aufdrehen oder eigene Animation - Mehmet
3. Wortlaut und Reihenfolge der Namen - René + Mehmet
4. Endet der Cold Opener im Gang am `SV_PrologueStart`? - Mehmet
