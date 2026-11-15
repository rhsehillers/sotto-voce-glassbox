# 🎭 Sotto Voce — Ein Dieb in den Kulissen

> *„Sotto voce" (ital.) = im Flüsterton, im Verborgenen. Der Doppelsinn IST das Spiel.*
> **Pitch in einem Satz:** Du stiehlst deine eigene, geklaute Partitur aus der Loge des Maestros zurück – während der Premiere, und nur das Orchester verdeckt deine Schritte.

*Konzept-Entwurf für Team Produktlicht · 2026 Epic AI MegaJam · Stand 11.11.2026 (Vor-Jam-Planung, wird in DECLARATIONS.md deklariert)*

---

## 1. Setting & Ära
Hinter der Bühne eines prunkvollen **Belle-Époque-Opernhauses** – gaslichtbeleuchtetes Paris, um 1890 – während einer **Live-Premiere**: Schnürboden, Seilzüge, Sandsäcke, bemalte Kulissen, Souffleurkasten, Umkleide-Nischen, das Pult des Régisseurs.

**Warum frisch:** Games zeigen immer das Publikum oder die Bühne. Niemand spielt in der schwitzenden, knarrenden Maschinerie **drei Meter hinter dem Vorhang**. Der Ort bringt Rhythmus, Gefahr und edle Zeit-Textur gleich mit: Samt, Messing, Gold, Staub im warmen Licht.

## 2. Core-Loop (die EINE Mechanik)
**Das Orchester ist deine Deckung.**
- **Musik laut** (Tutti, Crescendo, Applaus) → deine Schritte sind übertönt, du bewegst dich frei – gehen, schleichen, sprinten.
- **Musik leise** (Solo-Arie, Generalpause, die Stille vor dem Einsatz) → jede Bewegung wird gehört. Du **erstarrst**, duckst dich in den Schatten oder hinter ein Requisit und wartest aufs nächste Anschwellen.
- Eine klare **Dynamik-Leiste** (und das mit der Lautstärke pulsierende Rampenlicht) zeigt dir jederzeit, ob du sicher bist.

**Aufgabe:** von der Bühnentür zur verschlossenen Privatloge des Maestros, die Partitur nehmen, wieder raus – **bevor der Schlussvorhang fällt** (= die Musik endet).
Im Kern „Rotlicht–Grünlicht", dirigiert von einem Live-Orchester: Spannung aus **Timing + Atmosphäre + Musik**, mit nur trivialer Gegner-KI.

## 3. Story / Lore
Du bist der **Ghostwriter** dieser Oper. Das Meisterwerk, das heute Abend umjubelt uraufgeführt wird, stammt von dir – doch es erklingt unter dem Namen des gefeierten Maestros. Deine Urheberschaft: gestohlen und begraben.

Der einzige Beweis, die **original signierte Partitur**, liegt in seiner Loge hinter der Bühne. Du hast genau **eine Vorstellung** – einen perfekten Moment –, um sie zurückzuholen und deinen Namen zu reklamieren.

**Die bittere Ironie:** Die gestohlene Musik, die aus dem Orchestergraben schwillt, ist genau das, was deine Schritte verbirgt. *Dein eigenes Meisterwerk schützt den Dieb, der es geschrieben hat.*

## 4. Warum in 4 Tagen machbar
- **Eine Szene, ein Loop, ein Win/Lose.** Feste **Diorama-Kamera** – ein beleuchteter Querschnitt des Backstage-Bereichs wie ein Theatermodell. Kein weitläufiges Level, kein Kamera- oder Traversal-Code. **Ein** Set wunderschön ausgestalten statt zehn mittelmäßiger.
- **Mechanik winzig + datengetrieben:** die Laut/Leise-Fenster sind eine **handgesetzte Timeline** synchron zum fertigen Musiktrack – **keine Echtzeit-Audioanalyse**. Gegner brauchen nur Idle / Patrouille / Alarm und reagieren nur auf Bewegung in leisen Passagen. Win/Lose ist eine kleine State-Machine; **die Länge der Musik IST der Level-Timer.**
- **KI-Tools übernehmen die Asset-Last:** 3D-Props (Seile, Sandsäcke, Kulissen, Kostümständer, Truhen, Kandelaber, das vergoldete Pult), PBR-Materialien (Samt, Messing, staubiges Holz), ein paar Animationen (schleichen / sprinten / ducken / „erschrockene" Bühnenkraft). Unreal MCP baut die Szene zusammen.
- **Clevere Reihenfolge:** **Musik ZUERST (Tag 1).** Weil die Partitur die Stealth-Timeline definiert, ist die Musik die Level-Spezifikation – nicht Deko am letzten Tag.

## 5. Arbeitsaufteilung (3 Spuren, kaum Überlappung)

**🧠 Code / Logik – René**
- Musiksynchrone „Lärm-Fenster"-Timeline (laut = sicher / leise = Gefahr) als Data-Asset
- Spielerbewegung (schleichen / gehen / sprinten / ducken), Lärm abhängig von Tempo × aktueller Dynamik
- Einfache Entdeckung (Hörweite + kurze Sichtkegel), die nur bei Bewegung in der Stille auslöst
- Win/Lose-State-Machine, Retry/Checkpoint, Dynamik-Leiste (UI), Interaktions-Prompt
- Unreal MCP für Aufbau und Iteration der Szene

**🎨 Art / Environment – Kollege**
- Das Helden-Diorama: Schnürboden, Seil- und Sandsack-Linien, bemalte Kulissen, Requisitentische, Umkleide-Nische, die vergoldete Maestro-Loge, die Rückseite des großen Vorhangs
- Gaslicht-Stimmung: warme Lichtinseln, tiefe Schatten als Verstecke, stilisiert-realistisches Post-Processing
- Figuren: Protagonist + 2–3 Bühnenkraft-Typen; das Partitur-Requisit
- VFX: Staub im Licht, Kerzenflackern, wehender Vorhang

**🎼 Musik / Sound – René als Komponist (der STAR)**
- Ein originales Orchesterstück (~3–5 Min, Ouvertüre/Arie), dessen Dynamik-Verlauf **bewusst der Stealth-Rhythmus ist** – du entwirfst das Level, indem du es komponierst
- Adaptive Stinger: Entdeckung, „Partitur erbeutet"-Motiv, Finale-Klimax
- Diegetische Schichtung (gedämpft von hinter der Bühne vs. klar) + SFX: knarrende Bretter, Seilknarzen, ferner Applaus, das „Psst!" des Régisseurs, der Vorhang
- Mix so abgestimmt, dass man **durch Zuhören überlebt**

> **Übergabe-Verträge zwischen den Spuren:** Musik → Code liefert die Laut/Leise-Marker; Art → Code liefert Meshes + Versteck-Positionen. Sonst blockiert sich niemand.

## 6. Wo die Musik glänzt
- **Die ganze Mechanik IST die Partitur** – die Dynamik des Komponisten ist der Spieltakt. Das Soundtrack ist das Level, nicht Dekoration.
- Ein langes **Crescendo**, zu dem du einen gewagten Sprint timest.
- Ein plötzliches **Pianissimo**, das dich mitten im Raum strandet – exponiert.
- Das **Ritardando** vor dem Finale, das dich ein letztes Mal quälend erstarren lässt.
- Das **Schluss-Fortissimo + Applaus** als Fluchtfenster.
- **Thematischer Payoff:** Es ist die *eigene gestohlene* Musik, die dich verbirgt – Partitur und Story sind dasselbe Objekt.

## 7. Preis-Fit
| Kategorie | Warum |
|---|---|
| **Audio** | stärkster denkbarer Fit – die Original-Partitur IST das Spiel |
| **Render Royalty** | ein liebevoll beleuchtetes Gaslicht-Diorama boxt weit über die Gewichtsklasse eines ersten Jams |
| **Best Team** | sauberes Duo-Schaufenster: einer liefert Code + Musik, der andere den gesamten Look |
| **Glass Box** | transparente Mechanik (man sieht immer, warum man erwischt wurde) + KI-Pipeline-Story |

## 8. Director's-Cut-Bezug
Die Premiere ist der „Director's Cut" des Maestros – von **deinem** gestohlenen Werk. Heute Nacht holst du dir den Credit zurück.

## 9. Größtes Risiko + Cut-Plan
**Risiko:** die Musik-zu-Gameplay-Synchronität **fair** hinbekommen (Fenster so tunen, dass sich niemand betrogen fühlt) – während wir gleichzeitig Unreal lernen. Die Falle wäre Echtzeit-Audioanalyse.

**Cut, in dieser Reihenfolge:**
1. Nie Live-Audio analysieren → Laut/Leise als handgetunte Timeline zum fixen Track.
2. Die Dynamik-Leiste garantiert Fairness, auch wenn die musikalische Feinheit nicht perfekt sitzt.
3. Wenn's immer noch zu viel ist: **eine** patrouillierende Bühnenkraft + **ein** fester Zuhörer (Régisseur am Souffleurkasten), Stück auf ~2 Min kürzen, Route fast gerade mit 2–3 Versteck-Beats.

→ Die Vertical Slice liest sich trotzdem komplett: eine spannende Durchquerung, getaktet von einem Musikstück, gewonnen oder verloren vor dem Vorhang.

---
**Einschätzung PM:** niedrigstes Risiko der drei, stärkste Story, Musikstil (orchestral) liegt René. → siehe `EMPFEHLUNG.md`.
