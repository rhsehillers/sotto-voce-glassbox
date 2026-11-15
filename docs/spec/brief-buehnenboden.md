# Auftrag: Bühnenboden (Dielen) für *Sotto Voce: The Cut*

Für eine Instanz außerhalb des Projekts (René leitet weiter). Ziel: **ein fertiges, kachelbares Material für den Boden von
Bühne und Seitenbühne**, das wir in Unreal direkt auf die vorhandene Graubox legen. Fläche dort: rund 16 × 23 m.
Gang und Loge bekommen später einen eigenen Boden (siehe unten).

## Das Spiel in drei Sätzen

Paris 1891, Premierenabend in der Oper. Eine Schleich-Geschichte hinter der Bühne: Seitenbühne, Bühne, Logengang.
Third-Person-Kamera etwa 3 m hinter und 1,7 m über der Figur; man sieht den Boden also schräg von oben, nie aus der Nähe.

## Look, an den der Boden passen muss

- **"Tinten-Noir":** Toon-Post-Process mit Tuschelinien und harten Schatten, darunter normale PBR-Materialien.
- **Licht:** warmes, bernsteinfarbenes Gaslicht, viel Dunkel, wenige Lichtinseln.
- **Was schon steht:** Nussbaum (Trennwand), bordeauxroter Samt, Messing, Wolle, Jute. Der Boden muss sich davon
  abheben - also **nicht** Nussbaum und nicht rötlich.
- **Detailgrad:** lieber klar lesbare Dielen mit ruhiger, mittelgrober Maserung als feine Foto-Poren. Feines
  Hochfrequenz-Rauschen wird unter dem Tusche-Filter zu Flimmern. Variation entsteht über die Dielen (Ton, Maserung),
  nicht über Mikrodetail. Der Stil des Weinfasses (einzelne Dauben mit eigener Maserung) passt, wenn die Maserung so
  ruhig bleibt.

## Holz und Stil

**Gealterte, dunkel geölte Kiefer (Pitch Pine / Kiefer, Nadelholz).** So waren Bühnenböden im 19. Jahrhundert: Weichholz,
weil man Dielen tauscht und Versenkungen hineinschneidet. Jahrzehnte von Öl, Staub und Schuhen haben es nachgedunkelt.
*Gegencheck 13.11. (René, Google/Gemini):* Opernbühnen des 19. Jahrhunderts in Paris nutzten Nadelholz (Fichte, Tanne,
Kiefer - französisch "sapin") für die stark beanspruchten, austauschbaren Bühnenbretter; Eichenparkett gehört in Foyers,
Säle und Logen. Kiefer oder Tanne ist für Bühne und Seitenbühne also stimmig; nachgedunkelt und geölt sind beide kaum zu
unterscheiden. Eiche bekommen Logengang und Loge 7 (siehe "Später").

- **Farbe:** warmes Honigbraun bis Umbra. Richtwerte (sRGB): Mitte etwa 95/62/38, dunkle Dielen bis 55/36/22, hellere
  (später ersetzte) Dielen bis 140/98/60. Kanten und Fugen dunkler.
- **Maserung:** Längsmaserung. Gemischt: manche Dielen mit Fladern (gewölbte "Kathedralen"-Maserung, Flachschnitt),
  manche mit geraden, dichten Jahresringen (Riftschnitt). Jahresring-Dichte je Diele verschieden.
- **Gebrauchsspuren gleichmäßig über die Kachel:** etwas Schmutz in den Fugen, leicht gerundete Kanten, ein paar Kratzer
  in Laufrichtung. **Keine** großen Laufwege oder Flecken in der Kachel - die würden sich alle 2,4 m wiederholen. Die
  kommen als eigene Decals (siehe Extras).
- **Oberfläche:** geölt, matt. Roughness 0,55-0,8, abgelaufene Dielen etwas glatter. Metallic 0.

## Maße und Aufbau der Kachel

| | Wert |
|---|---|
| Kachel (echte Größe) | **240 × 240 cm**, nahtlos in beide Richtungen |
| Dielenbreite | **15 cm** - also **16 Dielen nebeneinander** pro Kachel |
| Dielenlängen in der Kachel | gemischt 60-240 cm, pro Reihe 1-3 Dielen |
| Fugen | Längsfuge 1-2 mm dunkel; Stoßfugen (Dielenende an Dielenende) sichtbar |
| Nägel | Balken liegen quer unter dem Boden alle 60 cm: **4 Nagelreihen** pro Kachel, je Diele ein Nagelpaar, über alle Reihen in einer Linie; zusätzlich ein Nagelpaar an jedem Dielenende |
| Laufrichtung | Dielen laufen **entlang der Bildhorizontalen** (U-Achse) |

**Damit es nicht nach Matsch aussieht - die Regeln:**

1. **Jede Diele ist ein eigenes Stück Holz.** Die Maserung läuft nie über eine Fuge hinweg, weder über die Längsfuge
   noch über eine Stoßfuge. An jedem Dielenende beginnt neues Holz.
2. **Mindestens 12 verschiedene Quell-Dielen**, besser 16. Jede kommt höchstens 2-3 Mal in der Kachel vor, **nie direkt
   nebeneinander** und nie in derselben Lage: mal um 180° gedreht, mal entlang der Länge verschoben.
3. **Stoßfugen versetzt:** Benachbarte Reihen haben ihre Stoßfugen mindestens 30 cm auseinander. Kein Treppen- oder
   Leitermuster, kein regelmäßiger Verband - es soll wie zufällig verlegt aussehen.
4. **Nahtlos am Rand:** Eine Diele, die rechts aus der Kachel läuft, läuft links in derselben Reihe weiter, mit derselben
   Maserung. Die Kachel wird gedanklich als Ring gebaut, nicht als Ausschnitt.
5. **Ton je Diele:** jede Diele ±8 % Helligkeit und leicht anderer Farbton. Dazu 2 deutlich dunklere Dielen, 1-2 mit
   Ast, 1 mit Riss, 1 geflickte (andere Holzfarbe, "später ersetzt").
6. **Fugen im Farbbild führen, Relief bleibt sanft:** In der Normal Map die Kanten nur leicht gefast. Harte Kanten in
   der Normal Map erzeugen unter dem Tusche-Filter zu viele Linien.

**Empfohlener Weg (weil ganze Kacheln aus der Bild-KI an den Rändern verschmieren):** Die Dielen **einzeln** erzeugen -
jede als langer, flacher Streifen von oben, gleichmäßig beleuchtet, ohne Perspektive, ohne Schatten, z. B. 4096 × 256 px
für 240 × 15 cm. Danach die Kachel aus den Streifen **zusammensetzen** (Skript, Blender oder Substance) nach den Regeln
oben. Das Zusammensetzen kann auch Renés Seite per Skript übernehmen, wenn ihr nur die Streifen liefert.

## Was wir brauchen (Format)

Alles als PNG, quadratisch, Zweierpotenz, nahtlos:

| Datei | Inhalt | Format |
|---|---|---|
| `T_Buehnenboden_BC.png` | Base Color (Albedo, ohne Licht und Schatten) | sRGB, 8 Bit, 4096 × 4096 |
| `T_Buehnenboden_N.png` | Normal Map, Tangent Space, **DirectX-Konvention (Y-)** wie Unreal sie erwartet | 16 Bit (8 Bit geht), 4096² |
| `T_Buehnenboden_ORM.png` | gepackt: **R = Ambient Occlusion, G = Roughness, B = Metallic** (0) | linear, 8 Bit, 4096² |
| `T_Buehnenboden_H.png` | Höhe (optional), Fugen dunkel | linear, 16 Bit, 4096² |
| `T_Buehnenboden_ID.png` | **eine Graustufe je Diele** (zufällig, flach) - damit Unreal jede Diele zusätzlich einfärben kann | linear, 8 Bit, 4096² |

Dazu:
- **Vorschau:** ein Render der Kachel auf einer Fläche von 10 × 10 m, einmal von oben, einmal schräg (45°), unter warmem
  Licht - um zu sehen, ob sich etwas sichtbar wiederholt.
- **Kurzer Begleittext:** echte Kachelgröße (240 cm), Laufrichtung, verwendete Werkzeuge und **Lizenz** (kommerzielle
  Nutzung muss erlaubt sein - kommt in unsere `ASSETS.md`).
- **Optional:** die einzelnen Dielen-Streifen, damit wir später größere Kacheln oder andere Verlegungen bauen können.

Ablage beim Übergeben: `artwork/materialien/buehnenboden/` im Spiel-Repo. Import nach Unreal und das Material übernimmt
Renés Seite: weltbezogene Projektion (keine UVs nötig), je Diele ein kleiner Farbversatz über die ID-Map, dazu eine
großflächige Schmutz-Variation, damit die 2,4-m-Kachel auf 16 × 23 m nicht auffällt.

## Extras (gern, aber nach dem Boden)

- Decals, die sich nicht wiederholen: abgelaufene Laufwege (heller), Kreidemarken der Bühne (Kreuze, Zahlen), Klebeband,
  Kratzer.
- Der Umriss der Versenkung (Bühnenmitte, ca. 120 × 120 cm) als eigenes Decal oder Mesh.

## Später: Gang und Loge

Logengang und Loge 7: dunkles Eichenparkett im Fischgrätmuster mit bordeauxrotem Läufer. Eigener Auftrag, wenn der
Bühnenboden sitzt.
