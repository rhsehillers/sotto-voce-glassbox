# 🪘 The Last Gong — Ein Schattenspiel in einem Akt

> *Ein Raum, eine Nacht, eine Tat – getaktet von lebendiger Musik.*
> **Pitch in einem Satz:** Am javanischen Hof des 17. Jahrhunderts deckt das Gamelan deine Schritte – doch dein Schatten auf der Puppenleinwand kann dich verraten, und vor dem letzten Gong musst du zurück sein.

*Konzept-Entwurf für Team Produktlicht · 2026 Epic AI MegaJam · Stand 11.11.2026 (Vor-Jam-Planung, wird in DECLARATIONS.md deklariert)*

---

## 1. Setting & Ära
Der königliche Hof (**Keraton**) im **Java des 17. Jahrhunderts** – das Mataram-Sultanat – während einer mitternächtlichen **Wayang-kulit**-Schattenpuppen-Vorstellung mit vollem Live-**Gamelan**.

**Warum frisch:** Games besuchen den javanischen Hof praktisch **nie**. Optisch unverwechselbar – geschnitztes Teak, Batik-Seide, Blattgold, Öllampen-Glühen, eine leuchtende Leinwand mit Puppen-Schatten, ein spiegelnder Boden. Klanglich wie nichts sonst auf dem Jam – Gongs, Metallophone, das Klagen der *Rebab*. **„Ein Ort und ein Klang, den du buchstäblich noch nie gespielt hast."**

## 2. Core-Loop (die EINE Mechanik)
Eine feste Kamera blickt in ein einzelnes, kerzenbeleuchtetes **Pavillon** hinab. Du bewegst eine Figur durch den Raum zu einem Ziel.

- **Das Live-Gamelan ist deine Deckung.** Schwillt das Ensemble zu einer lauten, dichten Passage an, ist der Hof gebannt und deine Schritte sind übertönt – du bewegst dich frei.
- Dünnt die Musik zu einem zarten Solo oder zur Stille vor dem großen Gong aus, wird jede Bewegung gehört – du **erstarrst**.
- **Zweite Ebene:** Die Lampe hinter der Schattenleinwand (*Blencong*) wirft **deine** Silhouette auf die Leinwand (*Kelir*), wenn du durchs Licht gehst – und verrät dich dem Publikum. Also bleibst du auch in den Schatteninseln zwischen den Lampen.
- Der **große Gong** (*Gong Ageng*) markiert jeden Zyklus und das Ende des Stücks: Erledige die Tat und schlüpf an deinen Platz zurück **vor dem Schlussgong** – sonst gehen die Lichter an und du bist entlarvt.

**Lies die Musik. Beweg dich im Lauten. Versteck dich im Dunkel. Schlag den Gong.**

## 3. Story / Lore
Ein **Usurpator** hat den Thron an sich gerissen und für heute Nacht ein privates Schattenspiel des alten Epos befohlen – eine Demonstration seiner Legitimität.

Doch der führende Puppenspieler, der **Dalang**, ist der letzte Loyalist. Die heutige Vorstellung verbirgt eine zweite Geschichte: Während das Gamelan jeden Laut übertönt und der ganze Hof in den Schatten auf der Leinwand versinkt, durchquert eine Figur im Dunkel darunter das Pavillon, um alles richtigzustellen. Oben spielen die Puppen das alte Ende – darunter wird ein anderes geschrieben.

> *„Jedes Schattenspiel hat zwei Geschichten – die auf der Leinwand und die, die sie verbirgt."*

Der Höhepunkt wird **nur als Schatten auf der Leinwand** gezeigt – zwei Silhouetten verschmelzen, ein Sinken, mehr nicht. **Geschmackvoll, blutlos, thematisch perfekt** (und regelkonform).

## 4. Warum in 4 Tagen machbar
- **Ein Raum, feste Kamera** = keine offene Welt, kein NavMesh-Wildwuchs, kein Kamera-Code, komplett gestaltete Sichtlinien. Der Diorama-Rahmen ist das ganze Spiel.
- **„Komplexe KI" wird durch Musik ersetzt:** Die Wachen sind nicht schlau – Entdeckung ist ein globales Gate (*ist die Musik gerade laut?*) plus ein einfacher Check, ob du im Lampenlicht stehst. Günstig, lesbar, tunebar.
- **Der stilisierte Lampenlicht-/Silhouetten-Look verzeiht viel** – Stimmung kaschiert raue Assets, ideal für Erstlinge, und zielt direkt auf den Optik-Preis.
- **KI-Tools heben die Asset-Last:** 3D-Props (Gamelan-Instrumente, Lampen, Leinwand, Puppen, Kissen, Säulen, Opfergaben), Materialien (geschnitztes Holz, Batik, Gold, Stein), ein paar Figuren + kurzes Animationsset (Idle / Gehen / Sitzen / die eine Tat). Unreal MCP baut und dekoriert die eine Szene.

## 5. Arbeitsaufteilung (3 Spuren, kaum Überlappung)
> **Hinweis:** René trägt Code- **und** Komponisten-Hut. Die beiden Spuren sind aber **zeitlich sauber trennbar**: erst die Musik als DAW-Block komponieren, dann die Systeme bauen, die sie lesen. Dass dasselbe Hirn Musik und Mechanik schreibt, ist sogar ein Integrationsvorteil.

**🧠 Code / Systeme – René**
- Spielerbewegung im begrenzten Raum
- Das Musik→Deckung-Gate; Wach-Aufmerksamkeit + Sichtlinie-zum-Licht
- Der *Gongan*-Zyklus-Timer + Win/Lose; Interaktion mit dem Ziel
- Die dezente „Bist du verdeckt?"-Anzeige
- Adaptive Musik-Stems ans Gameplay anbinden

**🎨 Art / Environment – Kollege (besitzt diese Spur komplett)**
- Das eine **Pendopo**-Diorama
- Beleuchtung: Lampen, der *Blencong*, Schatteninseln
- Alle Props + die leuchtende *Kelir* mit Puppen
- Figuren: Spieler, 2–3 Wachen, Usurpator, Dalang
- Batik-/Holz-/Gold-Materialien; die Schatten-Verschmelz-VFX des Höhepunkts; finale Kadrage für den „Render"

**🎼 Musik / SFX – René als Komponist (der STAR)**
- Ein originales **Gending** (Gamelan-Stück) mit bewusstem Dynamik-Bogen und kolotomischer Gong-Zyklus-Struktur, das **der Level-Takt ist**
- Adaptive Stems: leiser Einstieg → aufbauendes Ensemble → schneller Höhepunkt → Schlussgong
- Die Zuordnung laut/leise → sicher/exponiert
- Diegetische SFX: Gongschläge, Schritte auf Teak, knarrender Boden, das Raunen des Hofs, Lampenflackern, Stoff
- „Stück endet / Lichter an"-Verlier-Sting + Sieg-Kadenz

## 6. Wo die Musik glänzt
Die Musik ist hier nicht Hintergrund – sie ist **Uhr, Deckungssystem und Leveldesign** zugleich.
- **Der Einstieg** (sparsame *Rebab* + weicher Gong): Du bist exponiert, wartest, lernst den Raum zu lesen.
- **Der Aufbau** (Metallophone schichten sich ein, das Tempo zieht an): Deine Bewegungsfenster öffnen und weiten sich – **die Komposition choreografiert die Route des Spielers.**
- **Der Höhepunkt** (volles Ensemble, schnell und laut): das eine Fenster, breit genug, um das Ziel unbemerkt zu erreichen.
- **Der Schlussgong:** deine harte Deadline – das Stück löst sich auf, die Lampen gehen hoch, und wer nicht an seinem Platz ist, wird gesehen.

> **Gamelan ist der distinktivste Klang auf dem ganzen Jam – das hat garantiert kein anderes Team.** Die meisten bauen Audio zuletzt ein; hier wird das ganze Slice zuerst komponiert und um die Musik herum gebaut.

## 7. Preis-Fit
| Kategorie | Warum |
|---|---|
| **Audio** | Beinahe-Sieg: eine originale Gamelan-Partitur, die die Kern-Mechanik IST |
| **Render Royalty** | ein Helden-Diorama auf maximale Stimmung beleuchtet – Kerzenlicht, Gold, Batik, die leuchtende Schattenleinwand, spiegelnder Boden |
| **Glass Box** | neuartige, sofort lesbare Mechanik („die Musik sagt dir, wann du sicher bist" + der Schatten-Tell) |
| **Best Team** | zwei Erstlinge liefern eine saubere, polierte, klar aufgeteilte Slice |

## 8. Director's-Cut-Bezug
Der *Dalang* schneidet das alte Epos heute Nacht heimlich **neu** – das wahre Ende des Schattenspiels ist der Director's Cut.

## 9. Größtes Risiko + Cut-Plan
**Risiken:**
- Das **adaptive Musiksystem** *plus* das **zweite Deckungssystem** (Schatten-Silhouette) ist, wo die Stunden verschwinden.
- **Gamelan authentisch zu komponieren ist Spezialgebiet** (Stimmungen, Kolotomik) – größte Hürde für die Musik-Spur.
- **Kulturelle Sorgfalt:** Eine reale Kultur (javanischer Hof, Wayang) muss respektvoll dargestellt werden – kurze Recherche, keine Klischees.

**Cut, in dieser Reihenfolge:**
1. Das **Schatten-Silhouetten-System** zuerst streichen – Audio-Deckung allein (laut bewegen, leise erstarren) trägt die ganze Spannung.
2. Interaktive Stems durch **einen** loopenden Track mit gescripteten Laut/Leise-Abschnitten auf fester Timeline ersetzen.
3. Den Verschmelz-Höhepunkt als **vorgebackene Animation** statt dynamischer Enthüllung.

→ **Boden-Version, die trotzdem komplett und spannend ausliefert:** Diorama + eine Wache + ein Ziel + Gong-Deadline + loopende Partitur mit markierten Fenstern.

---
**Einschätzung PM:** größtes Audio-Upside (unverwechselbar), höchste kulturelle Novelty – aber höchstes Risiko (Gamelan-Komposition, zweites System, kulturelle Sorgfalt). → siehe `EMPFEHLUNG.md`.
