# MVP-Spezifikation: SOTTO VOCE: The Cut

**Status: ABGENOMMEN am 12.11.2026 von René und dem Kollegen. Ab jetzt verbindlich.** Die Punkte in Abschnitt 11
bleiben offen, bis das Team sie entscheidet. Änderungen am Umfang nur mit dem Ja beider Producer. Geschrieben vom PM.
Grundlage ist Konzept A aus der Konzeptrunde 2 (Harness-Lauf 12.11.), verändert nach der Entscheidung des Teams.
Diese Datei ist Teamunterlage (deutsch). Alles, was Spieler und Jury sehen, ist **englisch**.

Producer-Modell: Claude schreibt das gesamte C++ (Session von René). Beim Kollegen produziert Claude Assets, Licht und
Level per MCP und KI-Tools. René und der Kollege geben Richtung, spielen, entscheiden und nehmen ab.
Zusammenarbeit nach `COLLABORATION.md` 1.2 (Schichten, C++-Klasse + Blueprint-Kind, Platzhalter, `BOARD.md`).

---

## 1. Was das Team geändert hat (12.11.)

- **Keine Geister.** Die Projektionslaterne, der Schattenchor und der Bühnengeist sind gestrichen.
- **Steampunk statt Fantasy.** Der Twist ist jetzt eine dampfbetriebene Bühnenmaschinerie: Messing, Ventile, Manometer,
  Zahnräder, Dampfstöße.
- **Bühne und Figuren stilisiert**, mit leichtem Fantasy-Einschlag, nicht realistisch.
- **Kleiner geschnitten als Konzept A:** 2 Zonen (Bühne und Loge), der Keller nur, wenn Zeit bleibt (Team, 12.11.).
  Musik und Ton übernimmt komplett der Musikstudio-PM (statt 12 Minuten Musik von René).

Alle Stellen mit **[Vorschlag]** sind Vorschläge des PM. Story und Look entscheidet der Kollege, Mechanik und Zahlen
René.

## 1b. Änderungen nach dem ersten gemeinsamen Spieltest (13.11., René und Kollege)

Diese Punkte gelten vor älteren Stellen in Abschnitt 4.

- **Umziehen hinter einer Trennwand.** Es gibt keine große Umzieh-Animation. Neben jedem Kostümständer steht eine
  einfache Trennwand (Paravent), die man in den Raum stellen kann. Lucienne verschwindet dahinter, solange sie sich
  umzieht, und kommt im neuen Kostüm wieder hervor. **Statt gesehen zu werden, macht sie dabei Geräusche:** Wachen in
  einem kleinen Radius hören sie und kommen nachsehen. Dauer und Radius sind Balancing-Werte.
- **Gadget ohne Abklingzeit, dafür begrenzt.** Lucienne startet mit **2** Aufzieh-Apparaten (Balancing-Wert). Ein
  geworfener Apparat bleibt liegen und kann **wieder aufgehoben** werden (E).
- **Werfen im Bogen.** Der Apparat fliegt im Bogen aus ihrer Hand, auch über kleine Hindernisse, und landet nie direkt
  neben ihr.
- **Wachen bewegen sich lebendiger:** unterschiedliche Wartezeiten, Umsehen im Stehen, kleine Abweichungen im Weg,
  weichere Drehungen. Dazu kommen die Tätigkeits-Animationen der Art-Seite.
- **[Nice to have, gebaut 13.11.] Blick aus dem Versteck:** Im Kostümständer oder hinter dem Vorhang wechselt die Kamera auf ihre
  Augenhöhe, man schaut durch einen schmalen Schlitz, die Kamera dreht sich mit der Maus in Grenzen. Später passend zum
  Versteck-Asset.
- **Figuren:** Die Art-Seite liefert jede Figur fertig (Mesh, Anim-BP, alle Animationen verdrahtet) als Blueprint-Kind.
  Renés Seite tauscht sie nur aus und prüft sie im Spiel (BOARD).
- **Loge 7 nachschärfen:** Die Loge braucht eine offene Brüstung zum Saal, damit Valcourt seine Premiere sieht, und
  einen Stuhl für ihn (siehe BOARD).

## 1c. Schwierigkeit (Team, 13.11.)

- **Beim ersten Durchlauf ohne Erfahrung schafft man es nicht.** Es gibt eine Lernkurve: Mit jedem Versuch kommt man
  ein Stück weiter.
- **Ohne Gadgets schaffen es nur absolute Profis.** Otto Normalspieler braucht sie.
- Das Spiel ist im Moment insgesamt schwer. Die genaue Abstimmung folgt später im Team.
- **Balancing macht René** (D11). Er entscheidet alle Werte; der PM baut Datenvertrag, Simulator, Antrag und Einbau.
- **Lernen ist der Kern** (René): Der erste Lauf darf nicht unfair sein; im Moment des Verlierens muss man sehen
  "ah, da geht's besser lang". Wiederspielwert ist ein großer Hebel; Metaprogression gibt es nicht - **Wissen ist die
  Progression**. Darum bleiben die Fahrpläne der Wachen ein festes, lernbares Rückgrat; Lebendigkeit nur als kleine,
  begrenzte Streuung [Vorschlag PM: Wartezeiten +/-15 %, Umsehen, keine zufälligen Routenwechsel].
- **Keine Checkpoints** (D11): Die Welt ist klein, es ist eine Demo. Erwischt oder R = der Abend beginnt von vorn
  (Testszenen bleiben für die Entwicklung). Damit wird die Länge des Abends auch ein Hebel für Frust
  (Messgröße: verlorene Zeit pro Fehlschlag).
- **Zeit ist ein Hebel** (D11): Die Musik läuft in Schleifen auf einem Taktraster von 2,5 s; Phasen lassen sich in
  2,5-s-Schritten verlängern oder kürzen, ohne die Musik zu ändern.
- **Gadget:** kurz aufziehen, dann werfen. Hebel: Anzahl (2), Aufziehdauer, Wurfweite (9 m ist für die Räume eher zu
  weit, [Vorschlag PM: ca. 6 m]), Hörradius des Ratterns (heute 15 m).
- **Umziehen:** Hebel ist der Abstand, ab dem eine Wache sie hört; wer sie hört, kommt nachsehen [Annahme PM: steht sie
  dann noch hinter der Wand, ist sie erwischt].
- **Vorhang-Karte kurz** (D12): Name und ein kurzer Grund, "Gaspard caught you - you ran." - keine Orts-Details. **Keine Regiebuch-Notizen über Versuche hinweg** (Welt zu klein).
- **Simuliert werden Neuling und Normal** (mit und ohne Gadgets). Profis nur theoretisch: der Lauf prüft lediglich, dass
  es einen Weg ohne Gadgets gibt.
- **Hebel, alle als Daten und nicht fest im Code** (Ziel: `Data/balancing.csv`, Eingabe für einen Balancing-Lauf im
  Harness): Gadgets zu Beginn (2), Umziehdauer (3 s), Hörradius beim Umziehen (neu), Hörradien der Schritte
  (schleichen / gehen / rennen 0,8 / 4 / 10 m), Füllraten des Auges (falsche Zone, Nähe, Rennen, Durchschauer),
  Sichtweite hell / dunkel (12 / 5 m), Länge der Fenster (Gang dunkel 30 s, Valcourt weg ca. 30 s), Checkpoints.

## 2. In einem Satz (Logline, englisch)

> *Disguised as a stagehand or a chorus singer, sneak through a steam-driven Paris opera on opening night and steal
> back the score the Maestro stole from you.*

Der Bezug zum Thema „Director's Cut": Die Heldin inszeniert den Abend heimlich, denn jede Ablenkung ist ein Bühnen-Cue,
den sie auslöst. Am Ende entscheidet sie, wer den *Final Cut* an ihrem Werk hat.

## 3. Story (kurz, Details beim Kollegen)

- **Lucienne Varenne**, Komponistin. Ihre Oper wird heute unter dem Namen des Maestros uraufgeführt.
- **Théodore Valcourt**, der Maestro. Er hat ihr Werk signiert und ihr Finale gestrichen. Nach dem letzten Vorhang gibt
  er die signierte Originalpartitur dem Verleger, und dann ist der einzige Beweis fort.
- **Nebenfiguren mit Wahrnehmung:** Brac (Inspizient, Herr über die Dampfmaschinerie), Gaspard (Kammerdiener, bewacht
  die Loge), ein Pompier (Feuerwache mit Messinghelm).
- **Ohne Wahrnehmung, auf Schienen:** Valcourt, Bühnenarbeiter, Chor.
- **Paris, 16.11.1891**, Grand Opéra de l'Étoile (erfunden, Vorbild Palais Garnier).
- **[Vorschlag] Steampunk-Twist:** Das Haus ist stolz auf seine neue *Machinerie à vapeur*: Versenkung,
  Schnürboden-Winden und Effekte laufen mit Dampf. Darum gibt es überall Ventile, Rohre und Druckanzeigen. Das sind
  genau die Hebel, mit denen Lucienne ihre Cues stellt.

## 3a. Figuren

**Basis aus Konzept A, an Steampunk und „keine Geister" angepasst.** Ausgearbeitet sind bisher nur Lucienne und
Valcourt. Bei den anderen gibt Konzept A nur Rolle und einen Look-Haken vor. Charakterzüge und Look arbeitet der
Kollege aus, er ist Producer für Story und Figuren. Die Lücken sind markiert.

**Für alle Figuren:**
- Stilisiert, nicht realistisch.
- Jede Figur hat **einen** starken Look-Haken, damit die Silhouette sofort lesbar ist.
- Gesichter liegen eher im Schatten, unter Mützen, Helmen oder Schleiern, oder man sieht die Figur von hinten. Dort
  scheitern KI-Modelle am ehesten.
- Steampunk nur als Akzent: Messing, Ventile, Uhrwerk.
- Alle Figuren laufen auf dem UE5-Mannequin-Skelett.

| Figur | Rolle im Spiel | Wesen (Charakterzüge) | Look-Haken |
|---|---|---|---|
| **Lucienne Varenne** (29), Komponistin | Spielfigur | Sieben Jahre Kopistin bei Valcourt, seit drei Jahren schreibt sie die Musik, die er signiert. Still, präzise, beharrlich. Sie will keine Rache, sondern den letzten Schnitt an ihrem eigenen Werk | **Look (Stand 12.11. abends):** kurze flaschengrüne Jacke, Lederweste, Bluse, Reithose, hohe Stiefel, fingerlose Handschuhe mit Tintenflecken, kein Rock (`artwork/figuren/lucienne_eigen/`). **[Vorschlag]** Der Aufzieh-Apparat hängt am Gürtel (statt der Laterne). 3 Looks: eigene Kleidung, Arbeitskittel, Chorkostüm mit Schleier |
| **Théodore Valcourt** (61), „le Lion de l'Opéra" | Gegenspieler, auf Schienen, hat die Mappe | Eitel und gefeiert. Er hat sich leer geschrieben, weiß es und ist gerade deshalb gefährlich. Ihre Coda hat er gestrichen, weil ein trauriges Ende „dem Publikum gefällt" | Weiße Löwenmähne, rote Schärpe, Taktstock aus Ebenholz, den er sogar in der Loge in der Hand hält |
| **Henri Brac** (50), Inspizient | Wahrnehmung; durchschaut Bühnenarbeiter und Chor aus der Nähe | Kennt jeden seiner Leute. Der eigentliche Regisseur des Hauses und damit Luciennes Rivale um die Cues. *Sonst offen (Kollege)* | Sprachrohr um den Hals, Taschenuhr an langer Kette. **[Vorschlag]** Herr über die Dampfmaschinerie, Manometer am Pult |
| **Gaspard** (45), Kammerdiener | Wahrnehmung; bewacht Loge und Mappe, durchschaut im Logengang | *Offen (Kollege)* | Weiße Handschuhe, hoher Leuchter (**[Vorschlag]** als Gas- oder Dampflampe) |
| **Pompier** (Feuerwache der Oper) | Wahrnehmung; Sicherheit, wird bei Alarm gerufen | *Offen (Kollege)* | Messinghelm mit Nackenschutz, das Gesicht im Schatten. Steampunk passt hier von selbst |
| Bühnenarbeiter, Chor | Statisten auf Schienen | - | eigene Figuren (Männer), siehe `artwork/figuren/statist_*` (12.11.) |
| ~~Diva, Dirigent Delorme~~ | gestrichen (D19, 14.11.) | - | - |

Insgesamt **7 Meshes:** Lucienne (mit 3 Looks), Valcourt, Brac, Gaspard, Pompier, Bühnenarbeiter, Chor.

## 4. Kernhandlung

**Kamera:** Third Person über die Schulter, aus dem UE-C++-Third-Person-Template.
**Steuerung:** WASD + Maus, Strg schleichen, E interagieren, F Gadget, R zum letzten Checkpoint, Esc Pause.

**Minute für Minute:** beobachten (wer steht wo, wer ist beschäftigt), eine Gelegenheit finden (Kostüm, Cue, Gadget),
die Szene stellen, im Fenster gehen. Danach ist die Lage neu.

**4 Verben:**
1. **Verkleiden:** ein Kostüm vom Ständer nehmen (Bühnenarbeiterin, Chor). Jedes Kostüm erlaubt bestimmte Zonen.
   Niemand wird niedergeschlagen.
2. **Inszenieren:** einen Bühnen-Cue an einem Ventil oder Hebel auslösen. Der zuständige NPC geht hin, schaut
   10-15 Sekunden und kehrt dann in seinen Fahrplan zurück.
3. **Verstecken:** in Kostümständern oder Vorhangfalten. Die Sichtlinie ist dann unterbrochen.
4. **[Vorschlag] Gadget statt Laterne:** ein kleiner Aufzieh-Apparat (Look: Kollege), den Lucienne wirft oder
   abstellt. Er macht Lärm am Zielort und lockt **einen** NPC an. Abklingzeit 45 s. Er ersetzt das alte Dia *Lure*.

**3 Cues (MUST):**

| Cue | Ort | Wirkung |
|---|---|---|
| *Steam down* (Hauptventil) | Seitenbühne, Ventilwand | Das Licht im Logengang flackert aus (30 s). Gaspard geht nachsehen und verlässt den Gang |
| *Trap* (Dampf-Versenkung) | Bühne | Die Versenkung fährt zischend hoch. Brac verlässt sein Pult. (Mit Keller ist sie auch der Weg vom Keller zur Bühne) |
| *Fly* (Dampfwinde) | Seitenbühne | Ein Sandsack fällt in die Gasse. Der Pompier geht hin und gibt den Gang frei |

**Verdacht (vereinfachtes Hitman-Prinzip):**
- Sichtkegel 60°, 12 m, im Dunkeln 5 m. Über dem Kopf ein Auge, das sich von weiß nach rot füllt.
- Wer in einer Zone steht, die das Kostüm nicht erlaubt, füllt das Auge schnell. In erlaubten Zonen füllt es sich nur
  bei „Durchschauern" aus der Nähe (Brac bei Bühnenarbeitern, Gaspard im Logengang).
- Beschäftigte NPCs schauen halb so genau hin (Faktor 0,5), untätige anderthalbmal so genau (1,5).
- Rennen in Sichtweite erhöht den Verdacht. Ist das Auge voll: Alarm, Pompier kommt. Wer gefasst wird, geht zurück zum
  Checkpoint.
- **Fallback, falls die Wahrnehmung nicht rechtzeitig steht:** Lichtkegel auf dem Boden sind die Entdeckungszonen
  (*"Stay out of the light - or wear the right costume."*).

**Opernuhr (Startwerte, Nacht 1 rechnet sie nach):** Ein Durchlauf dauert höchstens 10 Minuten Opernzeit.

| Phase | Uhr | Lage | Fenster und Checkpoint |
|---|---|---|---|
| Akt 1 | 0:00-2:30 | Valcourt in Loge 7, Mappe auf dem Schoß. Brac untätig am Pult | **CP0.** Kostüm holen, *Fly* lernen |
| Entracte | 2:30-4:30 | Valcourt im Foyer. Gaspard **in** der Loge, Mappe auf dem Tisch. Alle beschäftigt | **CP1. Fenster 1:** *Steam down* oder Gadget lockt Gaspard raus |
| Akt 2 | 4:30-7:30 | Valcourt zurück. Der Chor zieht über die Bühne | **CP2. Fenster 2:** im Chorkostüm mit dem Chor zur Proszeniumstür, *Trap* lässt Valcourt wütend zur Bühne stürmen, die Loge ist 30 s leer |
| Nach dem Raub | sofort | Gaspard sucht, der Pompier ist strenger (1,5) | **CP3** beim Nehmen der Mappe |
| Finale | 7:30-10:00 | Umbau bis 8:10, das Dirigentenpult am Bühnenrand ist frei | **CP4.** Ende A: durch die Bühnentür hinaus. Ende B: Partitur bis 8:10 aufs Pult |
| Letzter Vorhang | 10:00 | Valcourt geht zum Verleger | ohne Partitur gescheitert |

Jede Figur folgt einem **Fahrplan aus der Uhr**: pro Phase eine Schleife aus Wegpunkten und die Markierung
„beschäftigt: ja/nein". Beim Phasenwechsel springen alle während der Akt-Glocke und einer kurzen Abblende auf ihre
neuen Wegpunkte. Zurücksetzen auf einen Checkpoint heißt: Uhr zurückstellen, alle Figuren stehen auf ihrem Punkt.
Neustart in unter 2 Sekunden.

**Abwechslung** kommt aus den Phasen: Jede Phase ändert Licht, Aufgaben und offene Wege, und nach dem Raub kippt das
Spiel in eine Flucht auf derselben Karte.

**Enden:**
- **Ende A, *Quiet Exit*:** durch die Bühnentür hinaus in die Pariser Nacht, die Partitur an der Brust (mit Keller:
  der Kahn über die Zisterne). Lucienne hat den Beweis, aber die Welt weiß nichts.
- **Ende B, *Final Cut*:** die Partitur auf das Dirigentenpult legen. Das Orchester spielt ihre gestrichene Coda.
  Die mechanische Anzeigetafel des Hauses klappt um auf *"Music by Lucienne Varenne"* (D19, 14.11.: entschieden; die
  Kunstseite baut sie mit Actor-Tags `SV_EndingB_Show` / `SV_EndingB_Hide` / `SV_EndingB_Camera`, die Karte wartet 4 s).
- **Scheitern:** gefasst oder der letzte Vorhang fällt, dann 1 s *"Curtain."* und zurück zum Checkpoint.

## 5. Level: 2 Zonen, der Keller ist optional

Ein zusammenhängendes Level. Übergänge laufen über Interaktion mit Abblende und Geräusch, ohne Klettern.
**Reihenfolge des Baus (Team, 12.11.): erst Loge und Bühne, der Keller nur, wenn Zeit bleibt.**

| # | Zone | Spielfunktion | Look (für den Kollegen) |
|---|---|---|---|
| 1 | **Bühne + Seitenbühne** mit Bühnentür und Orchestergraben-Rand | Start (Bühnentür) und Ausgang (Ende A). Zentrum: Cues *Steam down* (Ventilwand), *Fly* und *Trap*, Kittel- und Chorkostüm, Verstecke, Bracs Pult. In Akt 2 der Chorgang. Am Bühnenrand das Dirigentenpult (Ende B) | gemalte Kulissen (flache KI-Bilder), Dampfwinden, eine Ventilwand mit Messingrohren, Ventilrädern und Manometern, Inspizientenpult mit Sprachrohr, Kostümständer, Blick auf den dunklen Saal mit Lichtpunkten |
| 2 | **Logengang + Loge 7** | Ziel. Gaspard bewacht sie. Ein Wartungsschacht hinter der Bühne führt per Interaktion in die Rückwand der Loge; vorne verbindet die Proszeniumstür | roter Samt, Gold, Wandlampen, Ledermappe |
| - | *optional:* **Keller / Maschinenraum** mit Zisterne | Wenn er kommt: Start im Keller, *Steam down* zieht in den Kessel um, die Versenkung führt nach oben, Ende A wird der Kahn | Holzbalken, Kessel, Rohre, Dampf, schwarzes Wasser mit Kahn |

Der Saal ist eine gemalte Rückwand mit Punktlichtern, kein 3D-Publikum. Der **Schnürboden** als eigene Zone ist NICE.

## 6. Musik und Ton

- **Musik und Ton liegen komplett beim Musikstudio-PM** (Übergabe von PM zu PM, Auftrag #188 vom 12.11.). René
  komponiert nicht selbst; er übergibt und nimmt ab. Form, Anzahl der Stücke, Tempo, Formate und Lautheit entscheidet
  der Musikstudio-PM.
- Er hat den Kontext bekommen: Setting, Story, Stimmung und wofür Musik und Ton gebraucht werden (Titel, Intro, Spiel
  vor und nach dem Raub, Alarm, kurze Momente, Enden A und B, Geräusche der Dampfmaschinerie, Atmo, Trailer).
- **Zeitplan (sein Rat):** Freitag Skizzen, Samstag fertig, Sonntag nur Einbau und Trailer. Bis Samstag klingt jede
  Szene, notfalls mit Platzhalter.
- **Einbau:** Claude in Renés Session baut ein, was geliefert wird, nach der Tabelle „Ereignis -> Datei" des
  Musikstudio-PM. Bis dahin piepen Platzhalter über `sync-vertrag.csv` (COLLABORATION 1.2). Ob die Oper je nach Zone
  gedämpft klingt, entscheidet sich mit seiner Lieferung.
- **Fertig** heißt: René hat es im Spiel gehört und abgenommen.

## 7. Technik (Claude in Renés Session)

C++-Basisklassen, die Blueprint-Kinder setzt der Kollege:
- `AOperaClock` (Uhr, Phasen, Glocke, Checkpoints), `UScheduleComponent` (Fahrplan aus CSV),
  `USuspicionComponent` (Sicht, Verdacht, 5 Zustände: Fahrplan, Nachsehen, Verdacht, Alarm, zurück)
- `AInteractable` → `ACueValve`, `ACostumeRack`, `AHideSpot`, `ATransitionPoint`, `AScorePortfolio`; `AGadget`
- Spielerfigur aus dem Template mit Kostüm-Zustand; HUD mit C++-Basis (Auge, Programmzettel mit Uhr, Zielzeile,
  Tastenhinweise)

Daten in CSV (`Data/`), Vertrag für das Referenzmodell aus Nacht 1: `phases.csv`, `npc_schedule.csv`,
`perception.csv`, `cues.csv`, `disguises.csv`.

**Alle Figuren auf dem UE5-Mannequin-Skelett**, damit die Template-Animationen ohne eigene Animationsarbeit passen.
Wahrnehmung nur für 3 Figuren. Keine Behavior Trees, keine EQS, kein Klettern, keine Physik-Seile.

Auf Renés Laptop läuft die Graubox auf Low. Licht, Hero-Shots und das Packen laufen auf dem Rechner des Kollegen.

## 8. Art und Video (Claude beim Kollegen)

- **Figuren (KI-generiert, Mannequin-Skelett):** Lucienne in 3 Looks (eigene Kleidung, Arbeitskittel, Chor), Valcourt,
  Gaspard, Brac, Pompier, Bühnenarbeiter, Chorsänger. Statisten über Material-Varianten.
- **Bausatz pro Zone** im Raster aus `COLLABORATION.md` 1.2, gemalte Kulissen als flache Bilder.
- **Stil:** Grundlage ist „Gaslicht-Noir" aus Konzept A (viel Schwarz, Bernstein-Licht, Ochsenblut), dazu Messing und
  Dampf. Eine Akzentfarbe nur für Spielwichtiges; welche, entscheidet der Kollege. Stilisiert, Gesichter eher im
  Schatten, unter Mützen und Helmen oder von hinten.
- **Sequenzen** (alle überspringbar):
  - Cold Open 10 s, spielbar ab Sekunde 10.
  - *The Portfolio* 20-30 s nach dem Raub; Lucienne sieht ihren gestrichenen Namen.
  - Ende A 20 s, Ende B 30 s.
- **Trailer** 45 s, die Mechanik schon in den ersten 3 Sekunden, geschnitten auf Renés fertigen Track.
- **3-5 Hero-Shots** für Render Royalty.

## 9. Umfang

**MUST:**
- 2 Zonen: Bühne mit Seitenbühne, Loge mit Logengang
- 4 Verben
- 3 Cues
- 2 Kostüme
- 3 wahrnehmende NPCs
- Opernuhr mit 4 Phasen und Checkpoints
- 2 Fenster
- Ende A, Ende B, Scheitern
- Cold Open und die beiden Enden als kurze Sequenzen
- Musik und Ton vom Musikstudio-PM, im Spiel eingebaut
- englische Texte
- gepackter Build, der auch auf Renés Laptop läuft
- Trailer

**NICE** (in dieser Reihenfolge, wenn Luft bleibt; über den Keller entscheidet das Team spätestens Freitag 19:00):
1. Keller als dritte Zone (Start, Kessel, Zisterne, Kahn-Ende)
2. *The Portfolio* in voller Länge
3. Schnürboden als Zone
4. Gesprächsfetzen als Hinweise
5. Licht folgt der Musik (CSV-Hüllkurve)
6. Endbildschirm „Regiebuch" mit Wertung
7. Applaus bei Effekten vor dem Publikum

**CUT:**
- Geister und Projektionen, Spannungs-Stems
- Sprachausgabe, Lippensync, Kampf, Niederschlagen, Klettern
- 3D-Publikum, mehrere Level, freies Speichern

## 10. Abnahmen (Producer)

| Wann | Was René und der Kollege prüfen |
|---|---|
| **Do 19:00** | Graubox von Bühne und Loge begehbar. Verkleiden, 1 Cue und 1 NPC mit Sichtkegel laufen. Ein Stilbild vom Kollegen. Die Maße sind bestätigt |
| **Fr 19:00** | Der ganze Ablauf ist in der Graubox spielbar (4 Phasen, 2 Fenster, Raub, Enden als Platzhalter). Erste Figuren und erster Bausatz sind drin. Erster gepackter Build, und er startet. Musik-Skizzen klingen im Spiel |
| **Sa 19:00** | Alle MUST-Punkte sind drin, die Musik ist fertig, die Sequenzen auch. Feature-Freeze. Build-Test auf Renés Laptop |
| **So 20:00 / 22:00** | Kandidat, danach Abgabe mit Build, Video und Seite |

## 11. Offen (Team)

1. ~~Steampunk-Gadget und Anzeigetafel~~ - entschieden: Gadget ist drin, Anzeigetafel ja (D19, 14.11.).
2. Name und Look der Heldin bleiben Lucienne Varenne? (Kollege)
3. Den Gerüchtenamen *Fantôme* streichen? Ohne Geister hat er keinen Bezug mehr.
4. Jury-Sprache Englisch (PM prüft die Jam-Regeln, dazu die Regeln zu KI-Audio).
