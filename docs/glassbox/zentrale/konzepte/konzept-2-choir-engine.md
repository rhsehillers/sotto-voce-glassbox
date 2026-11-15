# ⛪ The Choir Engine — A Silent Movement

> *„Beweg dich auf der Musik. Stirb in der Stille."*
> **Pitch in einem Satz:** Du schleichst durch eine riesige singende Orgel-Kathedrale an blinden Automaten vorbei, die nur hören können – die Musik deckt dich, die Stille verrät dich.

*Konzept-Entwurf für Team Produktlicht · 2026 Epic AI MegaJam · Stand 11.11.2026 (Vor-Jam-Planung, wird in DECLARATIONS.md deklariert)*

---

## 1. Setting & Ära
Das Innere einer **unterirdischen Kathedralen-Maschine**: eine weltgroße Orgel aus Messingpfeifen, grünspanigem Stein und blinden **Automaten-Sängern**, tief unter einer Oberfläche, die verstummt ist. Eine fern-zukünftige, mythisch-industrielle „Konservatorium"-Ära.

**Warum frisch:** Man spielt nie *im Inneren* einer Maschine, die zugleich Kathedrale und lebender Chor ist. Eine einzige ehrfurchtgebietende Diorama-Halle – **das Setting selbst ist der Hook**: „ein Ort, den du noch in keinem Spiel gesehen hast."

> **Ton:** bewusst **ehrfürchtig-bedrohlich, NICHT Horror** – keine Schockmomente, kein Grusel. Erhabene Größe + Anspannung (passt zur Absage an Horror).

## 2. Core-Loop (die EINE Mechanik)
Du führst einen einsamen Eindringling über den Kathedralenboden zum **glühenden Herz** der Maschine. Blinde Automaten-**Lauscher** orientieren sich allein am Klang.

- **Swells / Crescendi** (laute Passagen) → ihr Gehör ist übertönt, du bewegst dich frei zwischen den Pfeifen.
- **Pausen / Pianissimo** → die Halle wird totenstill, ein einziger Schritt wird gehört. Du **erstarrst** in Deckung und wartest auf den nächsten Swell.
- Ein **Verdachts-Meter** stapelt als Warnung dissonante Musikschichten übereinander.

Lies die Musik, time deine Sprints, fädel dich zum Herz. **Ein fehlgetimter Schritt in einer Pause = entdeckt = verloren.** Echtzeit-Stealth-Timing, kein rundenbasiertes Rätsel.

## 3. Story / Lore
Als die Oberfläche verstummte, baute das Konservatorium die **Choir Engine** und verfügte: Sie darf nie aufhören zu singen – ihr Lied hält die schlafende Welt zusammen.

Doch das Lied, das sie spielt, ist eine **zensierte, endlos nachbearbeitete Fassung**. Die wahre, ungekürzte Komposition liegt im Herzen verschlossen.

Du bist der **Understudy** (die Zweitbesetzung), der die Halle durchquert – vorbei an den tauben, doch lauschenden Wärtern –, um das Podium zu erreichen und endlich die echte Partitur erklingen zu lassen. **Gewinnen bringt die Maschine nicht zum Schweigen – es lässt sie die Wahrheit sagen.**

## 4. Warum in 4 Tagen machbar
- **Feste Diorama-Kamera:** kein Kamerasystem, Animationsschwächen verschwinden in der Distanz, der Künstler investiert alles in **eine** dramatisch beleuchtete „Money-Shot"-Halle. (Liest sich nebenbei wie ein Filmset – leiser Theme-Bezug.)
- **Winziger Scope:** ein Ort, ein Loop, ein Layout, klarer Win (Herz erreichen + interagieren) / Lose (gehört werden).
- **Kleine Code-Fläche:** Klick-Bewegung auf NavMesh, **ein** Gegnertyp, ein Musik-Timeline-Leser, Trigger-Volumes. Unreal MCP baut das Szenengerüst, damit wir nicht mit dem Editor kämpfen.
- **KI generiert den Großteil:** Pfeifen, Automaten, Props (3D-Gen), Messing/Stein/Grünspan (Material-Gen), Lauf-/Dreh-/Idle-Clips (Animations-Gen). Wir Menschen konzentrieren uns auf unsere zwei Superkräfte: **Original-Musik** und **Helden-Set + Licht**.

## 5. Arbeitsaufteilung (3 Spuren, kaum Überlappung)

**🧠 Code / Systeme – René**
- Klick-Bewegung + Erstarren/Ducken auf NavMesh
- **Musik-Uhr:** datengetriebene Timeline mit globalem Flag „kann gehört werden" aus LAUT/LEISE-Markern
- **Lauscher:** Patrouillenpfad + schmaler Sichtkegel + Hör-Check (gesteuert durch die Musik-Uhr) → Alarm
- Verdachts-Meter → löst Events aus, die Audio-Schichten wechseln/stapeln
- Win/Lose-Trigger + Neustart; Unreal-MCP-Szenengerüst

**🎨 Art / Environment – Kollege (+ KI)**
- Die Helden-Halle: Pfeifen, Automaten, das glühende Herz/Podium, volumetrische Lichtstrahlen, filmisches Post-Processing
- Modulare Pfeifen- und Deckungsteile, Lauscher-Modell mit einfachem Rig, Spielermodell
- Dramatisches Licht mit einer Hauptquelle + die feste Kamera-Kadrage

**🎼 Musik / SFX – René als Komponist (der STAR)**
- **„Das Lied der Maschine":** ~2–3 Min Original, aufgebaut aus wechselnden **SWELLS** (bewegen) und **PAUSEN** (erstarren) – **das IST das Level**
- Adaptive Verdachts-Stems (vertikaler Remix), Entdeckungs-Stinger, das **Director's-Cut-Finale** bei Sieg / das zusammenbrechende Lied bei Niederlage
- Diegetische SFX: Schritte, der Atem der Pfeifen, das Gewicht der Stille, Automaten-Klicken, das Summen des Herzens

> **Nur zwei Übergabe-Verträge:** Musik → Code liefert eine LAUT/LEISE-Marker-Datei; Art → Code liefert Meshes + Sockets. Sonst blockieren sich die Spuren nicht.

## 6. Wo die Musik glänzt
- **Die Partitur ist die Uhr** – du „spielst" die Musik, indem du dich in ihr bewegst.
- **Stille als Waffe:** Die Pausen sind die intensivsten Momente – totale Ruhe, ein Schritt = Ende. Der Komponist gestaltet die Stille so sorgfältig wie die Noten.
- **Adaptive Beklemmung:** Verdachtsstufen stapeln dissonante Schichten, je näher du der Entdeckung kommst.
- **Der Payoff:** Am Herz löst sich endlich der wahre „Director's Cut" des Lieds auf – emotionaler und klanglicher Höhepunkt; bei Niederlage erstickt es in Verzerrung.
- **Alles ist diegetisch** – die Maschine *ist* die Musik, Audio steht immer im Vordergrund.

## 7. Preis-Fit
| Kategorie | Warum |
|---|---|
| **Audio** (Schlagzeile) | musikgetriebene Mechanik + originale adaptive Partitur + Stille als Gameplay |
| **Render Royalty** | feste Kamera = totale Kontrolle über ein atemberaubendes, screenshot-perfektes Set; höchstes Optik-Ceiling der drei |
| **Best Team** | Lehrbuch-Drei-Spuren-Split, jede Superkraft (Musik, 3D) sichtbar |
| **Glass Box** | lesbares System: „die Musik steuert buchstäblich, was die Gegner hören" + transparente MCP-/KI-Pipeline |

## 8. Director's-Cut-Bezug
Das Herz hält den **Director's Cut** der Welt – die ungeschnittene, wahre Partitur. Gewinnen lässt sie endlich spielen.

## 9. Größtes Risiko + Cut-Plan
**Risiko:** Gegner-KI (Patrouille, Sichtkegel, Alarmzustände, Gegner-Animation) frisst auf einem ersten Unreal-Projekt das Code- und Art-Budget. Dazu: eine **komplett erfundene Welt** braucht mehr Design-Arbeit from scratch (keine reale Referenz zum Anlehnen).

**Cut:**
1. Patrouillierende Lauscher durch **stationäre „Sentinel-Ohren"** ersetzen – glühende Schall-Sensoren mit festem Erfassungsradius, einfach **AN in Pausen / AUS bei Swells**. Kein NavMesh, keine Gegner-Animation, keine Sichtkegel. Der Kern-Loop überlebt zu 100 %.
2. Musik auf **einen** loopenden Swell/Pause-Zyklus kürzen.
3. Level auf eine gerade Korridor-Durchquerung mit drei Deckungs-Beats reduzieren.

---
**Einschätzung PM:** höchstes Optik- und Originalitäts-Ceiling, experimentellste Musik – aber mehr Welt-Design from scratch und Gegner-Risiko. → siehe `EMPFEHLUNG.md`.
