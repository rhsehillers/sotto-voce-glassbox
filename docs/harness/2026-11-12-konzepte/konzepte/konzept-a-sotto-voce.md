# Konzept A: SOTTO VOCE: The Cut

Runde 2, überarbeitet nach dem Review (`review-runde-1.md`). Was sich geändert hat, steht kurz am Ende des Dokuments.
Der Kern bleibt der Sotto-Voce-Kern, den das Team gut fand: Pariser Oper um 1890, Premiere, Ghostwriterin, Partitur
aus der Loge. Die Kernmechanik ist Social Stealth wie bei Hitman. Die Musik ist Uhr und Belohnung. Sie entscheidet
nie, ob man sich bewegen darf.

Engram-Knoten stehen in eckigen Klammern. "(eigenes Wissen)" heißt: kein passender Engram-Treffer, die Lücke ist per
`missing` gemeldet. **Sprache:** Diese Teamunterlage ist deutsch. Alles, was die Jury sieht (Titel, Texte im Spiel,
Untertitel, UI, Trailer), ist englisch und hier *kursiv in Englisch* angegeben.

---

## 1. Titel + Logline

**SOTTO VOCE: The Cut**

Warum dieser Titel: "Sotto voce" ist eine Spielanweisung in der Musik ("mit gedämpfter Stimme"). Sie zeigt Oper und
Schleichen zugleich. "The Cut" trägt im Englischen drei Bedeutungen. Es ist der Strich, mit dem Valcourt ihr Finale
aus der Partitur gekürzt hat. Es ist der *Final Cut*, also das Thema. Und es ist "her cut", ihr Anteil, der ihr
vorenthalten wird. Damit wird das deutsche Wortspiel "Der Strich" übersetzbar. Der Titel hat 1-3 Wörter, ein
Regie-Wort und einen Hinweis auf den Ort (Leitfaden Jury 4.1).

**Logline / Pitch (englisch, 24 Wörter):**
> *Disguised as stagehand or chorus ghost, sneak through a Paris opera on opening night and steal back the score the
> Maestro stole from you.*

Deutsch: Verkleidet als Bühnenarbeiterin oder als verschleierte Chorsängerin schleichst du in der Premierennacht durch
eine Pariser Oper und stiehlst die Partitur zurück, die der Maestro dir gestohlen hat. Das Bild steht nach einem Satz
fest. Leicht Vorstellbares wird besser bewertet [IMAGERY_ACCESSIBILITY_ACCOUNT].

---

## 2. Bezug zum Thema "Director's Cut"

Das Thema arbeitet auf drei Ebenen, und keine davon braucht ein Filmset:

1. **In der Story geht es darum, wer den letzten Schnitt am Werk hat.** Valcourt hat seinen Namen über die Oper der
   Ghostwriterin geschrieben. Außerdem hat er ihr Finale *gekürzt*: Ihre Coda, in der Eurydike sich selbst umdreht und
   allein ins Licht geht, ist gestrichen. Seine Fassung ist gefällig und tragisch, denn bei ihm sinkt Eurydike zurück
   in die Schatten. Am Ende entscheidet die Spielerin, wer den *Final Cut* bekommt.
2. **In der Mechanik bist du die heimliche Regisseurin des Abends.** Jede Ablenkung ist eine Szene, die du
   inszenierst: Licht, Maschine, Projektion, Auftritt. Die NPCs folgen deinen Cues wie Darsteller. Dein Gegenspieler
   hinter der Bühne ist Inspizient Brac, der eigentliche Regisseur des Hauses, und du kaperst seine Cues. Das passt
   auch zur Epic-Lesart "Wer Agenten nutzt, führt Regie": Man lenkt Figuren, die eigene Pläne haben.
3. **Am Ende steht das Regiebuch.** Der Endbildschirm zeigt deinen "Schnitt" des Abends als handschriftliches
   Regiebuch (*Prompt Book*), mit Szenen, Route und Ende. Das ist NICE.

Damit die Jury "Regie" sieht, bevor sie "Diebstahl" sieht, heißt jede Gelegenheit im Spiel *Scene* und jede Maschine
*Cue* (*"Cue 3: Gas down"*).

---

## 3. Setting und Zeit

**Wann und wo:** Paris, Montag, 16. November 1891, 20 Uhr. Uraufführung von *L'Ombre d'Eurydice*, Oper in drei Akten,
im **Grand Opéra de l'Étoile**. Das Haus ist erfunden, Vorbild ist das Palais Garnier. Gezeigt wird nur, was das
Publikum nie sieht, plus eine einzige Samtloge. Das Datum zwinkert zum Jam, denn die Abgabe ist am 16.11. Das ist eine
Zeile für den Dev-Log.

**Fantasy-Twist: die Fantasmagorie-Laterne (*Lanterne d'Ombres*)**
Bühnenlicht ist 1891 Gas- und Kalklicht. In dieser Welt brennt der Kalk der großen Projektionslaterne mit "Ätherkalk".
Ihr Licht wirft Gestalten, die frei in Luft und Rauch stehen und für einige Sekunden wie echte Menschen wirken: cyan
leuchtend, leicht flackernd. Das Haus nutzt die große Laterne im 2. Akt für den Schattenchor. Lucienne trägt eine
selbstgebaute Taschenausgabe am Gürtel. Die Bühnenarbeiter flüstern seit Wochen von einem *Fantôme*.

**Warum dieser Twist:**
- **Er wächst aus der Geschichte.** Robertsons Fantasmagorie-Shows (um 1798) und "Pepper's Ghost" (1862) waren echte
  Bühnentricks (eigenes Wissen). Wir übersteigern nur einen Schritt: Die Laterne braucht keine Leinwand mehr
  [PEAK_SHIFT_CARICATURE_HYPOTHESIS]. Der Knoten ist eine Hypothese, hier also nur Faustregel.
- **Er versteckt KI-Fehler.** Halbtransparente, flackernde Gestalten dürfen unsauber sein. Technisch ist das ein
  unbeleuchtetes, additives Material auf einem vorhandenen Figuren-Mesh, dazu Rauschen.
- **Er ist das Thema.** Wer projiziert, setzt anderen Bilder in den Kopf. Das ist Regie.
- **Er übersteht die Trennung von Bild und Ton.** Für das Bild braucht es ein Material, für den Ton einen
  Glasharmonika-Schimmer. Die Glasharmonika wurde in echten Fantasmagorie-Shows gespielt (eigenes Wissen).

**Die 4 Zonen des Levels** (ein zusammenhängendes Level; Übergänge zwischen den Ebenen per Interaktion, nicht per
Klettern):

| # | Zone | Look (für den Kollegen) | Spielfunktion |
|---|------|-------------------------|---------------|
| 1 | **Unterbühne / Maschinenkeller** mit Zisterne und Souffleurgang | Wald aus Holzbalken, Seiltrommeln, Gasrohre mit Ventilrädern, Pfützen, ein Ständer mit Arbeitskitteln der Bühnenarbeiter. Am Rand schwarzes Wasser mit Kahn (die Garnier-Oper hat wirklich einen Wassertank). Ein enger Gang endet am Dirigentenpult im Orchestergraben | Start und Ausgang (Kahn = Ende A). **Cue: Gashaupthahn.** Der Aufzug der **Versenkung** führt zur Bühne. Der Graben-Winkel wird für Ende B gebraucht |
| 2 | **Seitenbühne + Bühne** mit Schnellumzug-Ecke | Gemalte Kulissen (Flats) in Reihen, die Nagelbank mit den Seilzügen an der Wand, Inspizientenpult mit Glocke und Sprachrohr, Kostümständer und Schleier in der Umzugsecke. Hartes Bühnenlicht fällt in die Gasse. Von der Bühne aus ein dunkler Saal voller Lichtpunkte | Zentrum. **Cue: Seilzug** an der Nagelbank (der Sandsack fällt vom Schnürboden in die Gasse). Hier liegt das Chorkostüm (Verstecke in den Kostümständern). Brac steht am Pult. Im 2. Akt zieht der Schattenchor über die Bühne |
| 3 | **Schnürboden** | Holzstege 15 m über der Bühne, Seile, Sandsäcke, die Lichtbrücke mit der großen Ätherkalk-Laterne, Staub im Gegenlicht | Vertikale Route. Hier liegt die große Laterne für den Bühnengeist in Fenster 2. Die Wartungsleiter am Proszenium führt per Interaktion in die Rückwand von Loge 7 |
| 4 | **Logengang + Loge 7** (Proszeniumsloge, direkt neben der Bühne) | Roter Samt, Goldstuck, Wandlampen. Enge Loge mit Brüstung zum Saal, Ledermappe auf dem Beistelltisch | Ziel, öffentlicher Bereich. Gaspard bewacht ihn |

Der Saal ist **kein 3D-Publikum**, sondern eine gemalte Rückwand mit Punktlichtern (Operngläser).

**Übergänge statt Klettern:** Leiter, Versenkung und Souffleurgang sind Interaktionen (*E: Climb*, *E: Ride the
trap*). Die Kamera blendet 0,6 s ab, ein Geräusch läuft (Knarzen, Seilsirren), dann wird die Figur am Ziel abgesetzt.
Dafür braucht es kein Kletter-System, und der Ton verkauft den Weg.

---

## 4. Story

**Prämisse:** Sieben Jahre war Lucienne Varenne Valcourts Kopistin. Seit drei Jahren schreibt sie die Musik, die er
signiert. Nach dem letzten Vorhang unterzeichnet Valcourt im Foyer den Verlagsvertrag und übergibt dem Verleger die
signierte Originalpartitur. In der steht noch ihr Name, durchgestrichen. Danach ist der einzige Beweis fort.

**Protagonistin: Lucienne Varenne (29), Komponistin.** Tintenschwarze Fingerkuppen, dunkelgrüner Kopistenmantel,
Bleistift hinter dem Ohr, Messinglaterne am Gürtel. Meist von hinten zu sehen. Sie will keine Rache. Sie will den
letzten Schnitt an ihrem eigenen Werk.

**Antagonist: Théodore Valcourt (61), "le Lion de l'Opéra".** Weiße Löwenmähne, rote Schärpe, ein Taktstock aus
Ebenholz, den er sogar in der Loge hält. Er hat sich leer geschrieben, weiß es und ist deshalb gefährlich. Ihre Coda
hat er gestrichen, weil ein trauriges Ende "dem Publikum gefällt".

**Nebenfiguren** (jede mit einem visuellen Haken):
- **Gaspard, Kammerdiener (45):** weiße Handschuhe, hoher Kerzenleuchter. Er bewacht Loge und Mappe.
- **Henri Brac, Inspizient (50):** Sprachrohr um den Hals, Taschenuhr an langer Kette. Er kennt jeden seiner Leute.
  Er ist der rivalisierende Regisseur.
- **Ein Pompier (Feuerwache der Oper):** Messinghelm mit Nackenschutz, das Gesicht im Schatten. Er ist das
  Sicherheitspersonal, und Feuerwachen in der Oper sind historisch belegt.
- **Statisten ohne eigene KI:** die Diva als Eurydike (Material-Variante des Chor-Meshes mit Silberschleier),
  Dirigent Delorme (nur von hinten zu sehen, Material-Variante des Brac-Meshes im Frack), ein Bühnenarbeiter (dasselbe
  Mesh wie Luciennes Verkleidung) und der Chor (dasselbe Mesh wie die Chor-Verkleidung).

**Insgesamt 7 Meshes:** Lucienne, Valcourt, Gaspard, Brac, Pompier, Bühnenarbeiter, Chor.

**Drei Akte im Level:**
- **Akt 1, Eindringen** (Ouvertüre und 1. Akt der Oper, 0:00-3:00): Lucienne nimmt sich ein Kostüm, lernt die erste
  Szene (Gashahn) und sieht Valcourt mit der Mappe auf dem Schoß.
- **Akt 2, Der Griff** (Entracte und 2. Akt, 3:00-9:00): In zwei Fenstern kommt sie an die Mappe heran. Danach folgt
  die längere Cutscene (*The Portfolio*), und von da an sucht Gaspard.
- **Akt 3, The Cut** (Finale, 9:00-12:00): Flucht mit der Partitur (Ende A) oder die Partitur auf das Dirigentenpult
  legen (Ende B).

**Intro: 10 s Cold Open, mit jeder Taste überspringbar, spielbar ab Sekunde 10:**
1. 0-4 s: Nahaufnahme einer tintigen Hand, die *"L. Varenne"* unter die letzte Seite schreibt. Ihr Motiv auf dem
   Klavier.
2. 4-7 s: Eine Hand mit Siegelring streicht den Namen durch. Blechbläser-Stoß (Valcourts Motiv).
3. 7-10 s: Texttafel *"Paris, 1891. Opening night. Take it back."*, gleichzeitig ein Kameraschwenk zu Lucienne im
   Keller. Die Ouvertüre setzt gedämpft von oben ein, und die Steuerung ist da.
4. Oben steht die Zielzeile: *"Get into Box 7. The Maestro has your score."*

Mehr Story kommt nicht vorab. Den Rest erfährt man, wenn man ihn braucht [PROGRESSIVE_DISCLOSURE]: über
Gesprächsfetzen und über die längere Cutscene nach dem ersten Erfolg.

**Längere Cutscene nach dem ersten Erfolg: *The Portfolio* (35 s, überspringbar, Sequencer):**
Lucienne öffnet in Loge 7 die Mappe. Der durchgestrichene Name ist zu sehen. Ihr Motiv spielt auf der Celesta. Die
Laterne flackert und projiziert eine Erinnerung in Cyan: Valcourt zieht den dicken Strich durch die letzten 32 Takte.
Untertitel: *"Sad endings sell, mademoiselle."* Sie blättert und sieht, dass ihre Coda fehlt. Dann erscheint die
neue optionale Zielzeile: *"Optional: put the original on the conductor's desk before the finale."* Damit führt die
Cutscene genau dann zur Entscheidung, wenn die Spielerin sie treffen kann.

**Enden:**
- **Ende A, *Quiet Exit* (25 s):** Der Kahn gleitet über die Zisterne, die Partitur an der Brust. Von oben gedämpfter
  Applaus für Valcourt. Tafel: *"The score bears her name. The world doesn't know. Yet."*
- **Ende B, *Final Cut* (40 s):** Delorme dirigiert aus der Originalpartitur über den Strich hinweg. In den
  Orchesterstimmen stehen die gekürzten Takte noch mit dem damals üblichen "vi-de"-Zeichen, also spielt das Orchester
  ihre Coda. Lucienne projiziert von der Lichtbrücke ihren Namen in Licht auf den Gazevorhang. Valcourt steht in der
  Loge auf und kann nichts mehr tun. Stille, dann Applaus. Tafel: *"Music by Lucienne Varenne."*

**Das Dilemma:** Ende A sichert den Beweis, aber Lucienne bleibt unsichtbar. Ende B macht das Werk öffentlich, und die
Partitur bleibt vor 2000 Zeugen liegen. Sie verliert das Dokument und gewinnt die Autorschaft. Besitz gegen Final
Cut: Das ist das Thema.

**Scheitern:** Ein Pompier fasst Lucienne, oder der letzte Vorhang fällt, bevor sie die Partitur hat. Dann kommt 1 s
Bild *"Curtain."*, und sie steht nach weniger als 2 s wieder am letzten Checkpoint (Abschnitt 5).

---

## 5. Kernmechanik und Spielablauf

**Kamera:** Third Person über die Schulter, gebaut aus dem UE-C++-Third-Person-Template.
**Steuerung** (nur Konventionen): WASD + Maus, Strg schleichen, E interagieren, Q Laterne, R zum letzten Checkpoint,
Esc Pause.

**4 Verben im Spiel** (3 davon im Trailer: Verkleiden, Inszenieren, Projizieren). Wenige Verben halten das
Arbeitsgedächtnis frei für die Planung [WORKING_MEMORY_CHUNK_CAPACITY] [COGNITIVE_LOAD_THEORY]:
1. **Verkleiden:** Ein Kostüm vom Ständer nehmen. Niemand wird niedergeschlagen. Das ist geschmackvoll und spart
   Takedown-Animationen. Jedes Kostüm erlaubt bestimmte Zonen.
2. **Inszenieren:** Einen Bühnen-Cue auslösen (Hebel oder Rad). Am Zielort entsteht ein Ereignis, der zuständige NPC
   geht hin, schaut 10-15 s und kehrt dann in seinen Plan zurück.
3. **Projizieren:** Die Laterne stellt einen Schemen dorthin, wohin man zielt. Abklingzeit 45 s. MUST ist das Dia
   *"Lure"*: Ein Schemen Valcourts winkt, und der NPC geht hin.
4. **Verstecken:** in Kostümständern oder Vorhangfalten. Die Sichtlinie ist dann unterbrochen.

E nimmt und legt außerdem Partitur und Dia. Das ist die gewöhnliche Interaktion und kein eigenes Verb.

**3 Bühnen-Cues** (MUST):

| Cue | Ort | Wirkung |
|-----|-----|---------|
| *Gas down* (Gashaupthahn) | Keller | Das Gaslicht im Logengang geht für 30 s aus. Gaspard geht eine Kerze holen und verlässt den Gang |
| *Trap* (Versenkung) | Keller und Bühne | Die Falltür fährt mit lautem Ereignis hoch. Brac kommt nachsehen und verlässt das Pult. Außerdem ist die Versenkung der Übergang Keller → Bühne |
| *Fly* (Seilzug) | Seitenbühne, Nagelbank an der Wand | Ein Sandsack fällt vom Schnürboden in die Gasse. Der Pompier geht hin und gibt den Gang zur Umzugsecke frei. Brac reagiert nicht, er reagiert nur auf *Trap* |

Alle Effekte kommen **sofort**. Sie auf den nächsten Schlag einrasten zu lassen ist NICE (Abschnitt 8). Spieleraktionen
werden nie verzögert.

**Feste Zeitpläne sind der Plan, nicht der Notfall.** Jede Figur hat einen Fahrplan aus der Opernuhr, so wie die
Zeitpläne bei Hitman. Pro Phase gibt es eine Schleife aus Wegpunkten und die Markierung "beschäftigt: ja/nein". Beim
Phasenwechsel springen die Figuren während der Akt-Glocke und einer kurzen Abblendung auf die Wegpunkte der neuen
Phase. Gebaut wird das als kleiner Zustandsautomat mit erlaubten Übergängen [EXPLICIT_STATE_MACHINE]:
`Fahrplan → Nachsehen (Cue) → Fahrplan`, `Fahrplan → Verdacht → Alarm → Fahrplan`. Weil der Ort jeder Figur eine
Funktion der Uhrzeit ist, ist das **Zurücksetzen auf einen Checkpoint trivial**: Uhr zurückstellen, und jede Figur
geht auf ihren Fahrplan-Punkt.

**Musik springt mit der Uhr (MUST).** Die Opernuhr *ist* die Abspielposition der Musik, beide laufen nie getrennt.
Dafür beginnt an jedem Checkpoint ein eigenes Musiksegment: CP0 = Cue 2 ab 0:00, CP1 = Cue 3 (Entracte) ab Anfang,
CP2 = Cue 4 (2. Akt) ab Anfang, CP4 = Cue 5 (Finale) ab Anfang. Beim Zurücksetzen passiert dreierlei: Abblende mit
`Event.Opera.Act.Bell` (Glocke und Raumton decken den Schnitt), die Uhr wird auf den Checkpoint-Zeitpunkt gesetzt, und
das Segment startet von vorn (`Play(0)` auf der Musik-AudioComponent). Nur CP3 (Partitur genommen) liegt mitten in
einem Segment. Dort startet die Musik mit `Play(StartTime)` an der gespeicherten Position. Fällt das aus, wird CP3 auf
den Anfang des laufenden Segments gelegt (also auf CP1 oder CP2), und die Mappe bleibt im Inventar. Die Spannungs-Stems
und die CSV-Hüllkurve lesen dieselbe Uhr und springen automatisch mit.

**Nur 3 Figuren mit Wahrnehmung und Verdacht:** Brac, Gaspard und ein Pompier. Alle anderen (Valcourt, Bühnenarbeiter,
Chor, Diva, Dirigent) laufen auf Schienen, ohne Wahrnehmung.

**Verdacht (Hitman-Prinzip, vereinfacht):**
- Sichtkegel 60°, 12 m, im Dunkeln 5 m. Über dem Kopf ein Auge, das sich von weiß nach rot füllt.
- Wer in einer Zone steht, die das Kostüm nicht erlaubt, füllt das Auge schnell (etwa 2 s aus der Nähe).
- In erlaubten Zonen füllt es sich nur bei **Durchschauern** und nur aus der Nähe (unter 4 m): Brac bei
  Bühnenarbeitern und beim Chor, Gaspard im Logengang.
- **Beschäftigte Figuren schauen weniger genau hin**, Faktor 0,5; untätige Figuren Faktor 1,5. Wer keine Zeit oder
  Kraft zum Prüfen hat, urteilt nach Äußerlichkeiten wie dem Kostüm [ELABORATION_LIKELIHOOD_MODEL]. Die Strategie
  lautet deshalb: erst Beschäftigung stiften, dann gehen.
- Rennen in Sichtweite erhöht den Verdacht. Ist das Auge voll, ruft die Figur den Pompier. Es folgen 30 s Alarm. Wer
  außer Sicht bleibt, setzt den Alarm zurück. Wird man gefasst, geht es zurück zum Checkpoint.

**Die Opernuhr, verdichtet auf 12 Minuten.** Die Musik läuft und gibt Zeit und Momente vor. Die Spielerin liest die
Zeit aber am Programmzettel oben rechts und an Bracs Glocke ab, nicht an der Musik.

| Phase | Uhr | Valcourt | Gaspard | Bühne | Fenster und Checkpoint |
|-------|-----|----------|---------|-------|------------------------|
| Ouvertüre + 1. Akt | 0:00-3:00 | Loge 7, Mappe auf dem Schoß | an der Logentür | Brac am Pult (untätig, genau) | **CP0 Start.** Kostüm holen (ab ca. 0:30), *Fly*-Cue lernen, Laterne finden |
| Entracte | 3:00-5:00 | im Foyer (nur zu hören) | *in* der Loge, Mappe auf dem Tisch | Umbau, alle beschäftigt (×0,5) | **CP1 bei 3:00. Fenster 1:** *Gas down* oder *Lure* lockt Gaspard raus, Weg über Schnürboden-Leiter in die Loge |
| 2. Akt (Schattenchor) | 5:00-9:00 | zurück in der Loge, Mappe hinter ihm | an der Logentür | Chor zieht über die Bühne, Ausgang an der Proszeniumstür | **CP2 bei 5:00. Fenster 2:** im Chorkostüm *Join the procession* (20 s auf Schienen über die offene Bühne), dann mit der großen Laterne einen falschen Geist auf die Bühne werfen. Valcourt springt auf und stürmt zur Bühnentür, die Loge ist 30 s leer |
| Nach dem Raub | sofort | - | sucht, Pompier ×1,5 | - | **CP3 beim Nehmen der Mappe** (nach der Cutscene) |
| 3. Akt (Finale) | 9:00-12:00 | in der Loge | sucht | Umbau bis 9:40, Dirigentenpult frei | **CP4 bei 9:00.** Ende B: Partitur bis 9:40 aufs Pult. Ende A: zum Kahn |
| Letzter Vorhang | 12:00 | geht mit der Mappe zum Verleger | - | - | ohne Partitur gescheitert |

Das **erste Fenster öffnet nach 3 Minuten.** Der Neustart dauert höchstens etwa 2 Minuten, weil es Checkpoints pro
Fenster gibt und R jederzeit zum letzten Checkpoint führt.

**Spannung, die nicht aus der Musik kommt:**
- **Informationsvorsprung:** Die Spielerin kennt die Uhr und Valcourts Plan. Sie weiß, dass die Bombe tickt. Das ist
  Hitchcocks Suspense (eigenes Wissen).
- **Eskalation nach dem Raub:** Gaspard sucht, der Pompier ist strenger. Die zweite Hälfte ist eine Flucht auf
  derselben Karte, aber in neuer Lage.
- **Die letzten 30 s jeder Phase:** Brac läutet, auf dem Programmzettel pulsiert die Zeit, und auf der Spannungsebene
  setzt eine Pauke ein.

**Minute für Minute:** Beobachten (wer steht wo, wer ist beschäftigt), dann eine Gelegenheit finden (Cue, Dia,
Kostüm), dann die Szene stellen, dann im Fenster gehen. Danach ist die Lage neu. Ein Durchlauf dauert höchstens 12
Minuten Opernzeit, mit Wiederholungen 15-20 Minuten Spielzeit. Ein geübter Lauf dauert 6-8 Minuten.

**Abwechslung:** Jede Phase ändert Licht, Aufgaben und offene Wege. Akt 1 ist warm in Bernstein. Der Entracte ist
hell und hektisch. Der 2. Akt (Unterwelt) wird über Dunkelheit und Nebel abgesetzt, nicht über eine neue Farbe: Das Gaslicht ist auf ein Drittel gedimmt, Bernstein nur noch als schmale Gegenlichtkanten, dazu dichter Bodennebel, und im Bühnennebel kann man sich
verstecken. Akt 3 ist rot und gold. Die eigene Rolle wechselt mit: erst Eindringling, dann Diebin, dann Gejagte oder
Regisseurin.

**Erste 60 s** (Leitfaden Jury 6):
- 0-10 s: Cold Open.
- 10-30 s: Keller, sichere Zone. Die Taste erscheint am Kittelständer (*E: Disguise*), dann über die Treppe in die Seitenbühne.
- 30-60 s: Erstes Wow in der Seitenbühne. Der Pompier steht im Gang zur Umzugsecke, an der Nagelbank erscheint der Hinweis *"Cue: Fly"*. Der Sandsack kracht,
  der Pompier geht hin, und der Weg ist frei.

---

## 6. Stilrichtung Bild

Paletten-Regel (Stil-Leitfaden 2.2, "Welcher Stil zu welchem Konzept"): **2-3 Hauptfarben + genau 1 Akzent, Neutrale
frei.** Der Akzent bedeutet immer "spielwichtig" und kommt nirgends sonst vor.

### Option A: "Gaslicht-Noir" (Empfehlung)
Basis ist das Noir-Plakat aus dem Stil-Leitfaden 1.1, der für die Oper empfohlen ist. Dazu kommt **ein** Stilgriff:
Das Licht ist warm (Gaslicht) statt neutralgrau. Pitch in einem Satz: *"Sin City in the Paris Opera, lit by gas."*
- **Referenzen:** Hitman: Blood Money (Plakate und Menüs), Edgar Degas *Le Foyer de la danse à l'Opéra* und
  *L'Orchestre de l'Opéra* (um 1870, Hinterbühne aus der Gasse, angeschnittene Figuren im Gaslicht), *Dishonored*
  (2012, überzeichnete Proportionen und gemalte Oberflächen).
- **Palette:** **Hauptfarben** Ochsenblut `#5A1A1A` (Samt, Holz im Schatten) und Gaslicht-Bernstein `#E8A24A` (alles
  Licht, Nebel im Gegenlicht). **Neutrale** Tintenschwarz `#0B0B0D` und Rauchbraun `#2B2220`; Messing wird nur
  entsättigt als Neutral geführt. **Akzent: Geister-Cyan `#7FE3F0`**, nur für Projektionen, Partitur und interaktive
  Cues. Als einzige kalte Farbe springt es sofort ins Auge [TOP_DOWN_BOTTOM_UP_ATTENTION] und führt den Blick
  [VISUAL_HIERARCHY].
- **Licht:** Pro Raum ein hartes Führungslicht (Spot, harte Schatten), Gegenlicht für Silhouetten, viel Schwarz.
  Exponential Height Fog als Grundlage. Volumetrischer Staub und Lumen sind über die Skalierungsstufe abschaltbar.
  Bei niedriger Stufe bleibt die Szene trotzdem lesbar, damit der Build auf Renés Laptop läuft.
- **Materialien:** abgegriffenes Holz, Samt, Hanfseil, bemalte Leinwand. **Die Kulissen sind flache, KI-generierte
  Gemälde auf Ebenen.** Das ist historisch korrekt, denn die Kulissen von 1891 *waren* gemalt, und es ist das
  billigste Asset.
- **Warum es KI-Fehler versteckt:** Schwarz und Nebel schlucken Texturdetail, gelesen wird die Form. Gesichter, bei
  denen KI-Modelle am ehesten scheitern und ins Unheimliche kippen (Uncanny Valley, eigenes Wissen), liegen unter
  Schleiern, Helmen und Mützen oder werden von hinten gezeigt. Ein einheitlicher Look mit klaren Silhouetten wird
  flüssig verarbeitet und dadurch als schön empfunden [PROCESSING_FLUENCY_AESTHETIC_PLEASURE].

### Option B: "Papiertheater"
- **Referenzen:** Pollock's Toy Theatres (19. Jahrhundert), Lotte Reiniger *Die Abenteuer des Prinzen Achmed* (1926),
  *Valiant Hearts: The Great War* (2014).
- **Palette:** Hauptfarben Theaterrot `#8E1B1B` und Rampenlicht-Gelb `#E8C070`. Neutrale Sepia-Papier `#D9C7A3` und
  Tintenschwarz `#0B0B0D`. Akzent Geister-Cyan `#7FE3F0`.
- **Licht:** flaches Rampenlicht von unten, Schatten als harte Formen.
- **Materialien:** Karton mit Schnittkanten, Low-Poly-Figuren mit Konturlinie.
- **Warum es KI-Fehler versteckt:** Alles ist absichtlich gebastelt, Fehler lesen sich als Handarbeit.
- **Schwäche:** weit weg vom Hitman-Wunsch. Sichtkegel lassen sich schlechter lesen, und für Render Royalty ist es
  schwächer.

**Empfehlung: Option A.** Aus B wird nur übernommen, dass die Kulissen gemalte Flächen bleiben. Die Überzeichnung
(Löwenmähne, Seilwald, übergroße Laterne) ist gewollt [PEAK_SHIFT_CARICATURE_HYPOTHESIS], aber nur in einem
Stilgriff, damit die Neuheit mittel bleibt [BERLYNE_AROUSAL_POTENTIAL_MODEL].

---

## 7. Ton und Musik

**Rolle der Musik:** Sie ist Welt (die Oper läuft wirklich), Uhr (die Akte), Gefühl (Spannungsebenen) und Belohnung
(Stinger, Coda). Sie ist **nie die Regel**. Gegen den Runde-1-Einwand "zu musiklastig" ist sie außerdem gekürzt (etwa
12 statt 23 Minuten). Im Spiel tragen Maschinen, Kostüme und Figuren das Geschehen, die Musik liegt darunter.
Überwiegend arbeitet sie als **Kontrapunkt**: Die Oper spielt feierlich weiter, während hinter der Bühne geschlichen
wird (Stil-Leitfaden 3.15).

**Leitmotive** (Leitmotivtechnik, eigenes Wissen):
1. **"The Quill" (Lucienne):** eine aufsteigende Figur aus 4 Tönen, zuerst auf Klavier oder Celesta. Sie erklingt im
   Cold Open, in *The Portfolio* und in Ende A. In ganzer Form mit Orchester kommt sie nur in der Coda (Ende B). Die
   Wiederholung macht das Motiv bis zum Finale vertraut und beliebt [MERE_EXPOSURE_EFFECT]
   [FAMILIARITY_PREDICTS_MUSIC_LIKING].
2. **"The Lion" (Valcourt):** punktiertes, pompöses Blech. **Es ist ihr Motiv, gestohlen und verkleidet:** dieselben
   Intervalle in Dur, mit Fanfaren-Schmuck. Die Musik erzählt den Diebstahl ohne Worte. Es erklingt aus dem Off,
   bevor Valcourt auftritt. Weil Motiv und Figur immer zusammen auftreten, kann das Motiv später allein auf ihn
   verweisen [ASYMMETRIC_HEBBIAN_CROSS_MODAL_ASSOCIATION]. Der Knoten ist ein Netzmodell, hier als Faustregel genutzt.
3. **"The Shades" (Projektionen):** Glasharmonika oder gläserne Fläche, kurz bei jeder Projektion.

**Adaptive Ebenen nach Spielzustand:**
- **Ebene 0, die Oper (diegetisch, eigenes Wissen):** läuft immer, mit Tiefpass je Zone. Im Keller etwa 400 Hz, in der
  Seitenbühne etwa 2 kHz, auf der Bühne und in der Loge voll. Wer nach oben steigt, hört die Oper "aufgehen".
- **Ebene 1, Schleichen:** tiefer Streicherpuls, sehr leise.
- **Ebene 2, Verdacht:** Col-legno-Ticken, laut nach dem höchsten Verdacht in der Nähe.
- **Ebene 3, Alarm:** Tremolo in hohen Streichern und Glocke.
- **Ebene 4, die letzten 30 s einer Phase:** Pauke im Herzschlag.
- **Stinger sparsam:** Nach einer ruhigen Phase wirkt ein Akzent stärker. Die Coda in Ende B ist die *unerwartete*
  Wendung in einem Kontext, den man inzwischen kennt [MUSICAL_PLEASURE_UNCERTAINTY_SURPRISE_INTERACTION]. Belegt ist
  das für Pop-Akkorde, hier gilt es als Faustregel.

**Signatur im Sounddesign:** Holz und Hanf. Knarzende Seiltrommeln, sirrende Seile, der Aufprall des Sandsacks, das
Klonk der Falltür, das Zischen der Gasventile, Bracs Glocke, das Klicken der Laterne mit Glasschimmer, gedämpftes
Publikum durch Wände, Stiefel auf Bohlen. Stealth-Geräusche sind echte Geräusche, kein Mickey-Mousing.

**Was René in seiner DAW komponiert** (alle Stücke in festem Tempo, siehe Abschnitt 8; Summe etwa 12 Minuten neue
Musik):

| # | Cue | Länge (neu) | Spielt | Stimmung / Inhalt |
|---|-----|-------------|--------|-------------------|
| 1 | Cold Open "The Quill" | 0:10 | 0:10 | Klavier, bei 0:04 Löwen-Stoß. Übergang in Cue 2 |
| 2 | Ouvertüre + 1. Akt | 3:00 (2 Blöcke à 1:30) | 3:00 | französische Spätromantik (Richtung Massenet/Gounod), festlich, Löwen-Motiv. Vokalisen-Chor statt Sänger, wird ja gedämpft gehört |
| 3 | Entracte "Foyer Waltz" | 1:00 Loop | 2:00 | leichter Salonwalzer, gedämpft, mit Gemurmel. **An den Musik-Experten** |
| 4 | 2. Akt "Chorus of Shades" | 2:00 (2 Blöcke à 1:00, im Wechsel) | 4:00 | Misterioso, Chorfläche, tiefes Ostinato, Glasharmonika |
| 5 | 3. Akt "Finale - Valcourt's version" | 3:00 | 3:00 | tragisch, groß. Endet mit harter Fortissimo-Kadenz *genau am Strich* |
| 6 | "Eurydice's Coda" (Ende B) | 1:00 | 1:00 | ihr Motiv im vollen Orchester, Dur, licht, Generalpause vor dem letzten Akkord |
| 7 | Ende A "Quiet Exit" | 0:40 | 0:40 | ihr Motiv solo auf dem Klavier, ferner Applaus. **An den Musik-Experten** |
| 8 | *The Portfolio* (Cutscene) | 0:35 | 0:35 | Celesta-Motiv, dann eine Löwen-Variante in Moll, endet offen |
| 9 | Spannungsebenen 1-4 | 0:32 Loop × 4 Stems | dauernd | Puls, Ticken, Tremolo, Pauke, alle im Tempo der Akte |
| 10 | Stinger | 5 × 2-3 s | Ereignis | *Scene landed*, *Spotted*, *Score taken*, *Act bell*, *Curtain* |
| 11 | Trailer-Track | 0:45, davon etwa 0:15 neu | - | Schnitt aus Cue 4 und Cue 6 mit neuer Überleitung, 96 BPM |

**Lautheit** (Stil-Leitfaden 4): **Spiel-Mix -18 LUFS integriert (±2)**, gemessen über 5 Minuten typisches Spielen,
True Peak höchstens -1 dBTP. **Trailer und Abgabevideo -14 LUFS**, True Peak höchstens -1 dBTP. Sound Classes:
`Music`, `SFX`, `Dialog`, `UI`, `Ambience`. Bei Stingern und Untertiteln weicht die Musik um 6 dB (Ducking). Der
Abstand zwischen Stille und Coda-Einsatz bleibt so erhalten, und dieser Kontrast ist der Audio-Trumpf von Ende B.

---

## 8. Bild-Ton-Hochzeit

**Ein Vertrag für beide: `sync-vertrag.csv`** im Repo-Wurzelordner, im Format des Stil-Leitfadens 3.1. Es gibt 8
Spalten `id,typ,ausloeser,zeit,raster,ton,bild,status`. Trenner ist das Komma, Inhalt nur ASCII, keine Kommas in den
Feldern. Musik-Cues heißen `Music.<Name>`, Lichtkurven `Pulse.<Name>`, alles andere ist ein Gameplay Tag
`Event.<Bereich>.<Ding>.<Aktion>`. René importiert die Datei als DataTable und hängt Sounds an die IDs. Der Kollege
löst dieselben IDs per AnimNotify und Sequencer-Event-Track aus. Fehlt ein Sound, piept ein Platzhalter. Cue Sheet,
Hit Points, Stinger und Trailer-Marker sind Zeilen derselben Datei. Tagesnotizen stehen in `sync-log.md`.
`zeit` ist `<LevelSequence>@<Frame>` bei 30 fps. Ein `raster` von `sofort` heißt: kommt sofort (die Quartz-Rasterung
auf `beat` ist NICE, siehe Trick 7).

Startdatei für dieses Konzept (40 Zeilen):

```
id,typ,ausloeser,zeit,raster,ton,bild,status
Music.ColdOpen,cue,sequencer,LS_Intro@0,96/4,MS_ColdOpen,Hand schreibt Namen,platzhalter
Music.Akt1,cue,code,-,96/4,MS_Akt1,Ouvertuere hinter Waenden,platzhalter
Music.Entracte,cue,code,-,96/3,MS_Entracte,Umbau hell und hektisch,offen
Music.Akt2,cue,code,-,96/4,MS_Akt2,Schattenchor im Nebel,platzhalter
Music.Finale,cue,code,-,96/4,MS_Finale,Finale rot und gold,offen
Music.Coda,cue,sequencer,LS_EndeB@0,96/4,MS_Coda,Name in Licht,offen
Music.QuietExit,cue,sequencer,LS_EndeA@0,96/4,MS_QuietExit,Kahn auf der Zisterne,offen
Music.Portfolio,cue,sequencer,LS_Portfolio@0,96/4,MS_Portfolio,Mappe geoeffnet,platzhalter
Music.Tension,cue,code,-,96/4,MS_Tension_4Stems,Verdachtsauge fuellt sich,offen
Music.Trailer,cue,sequencer,LS_Trailer@0,96/4,SW_Trailer,Trailer-Schnitt,offen
Event.Cut.Intro.Sign,hit,sequencer,LS_Intro@15,-,SW_Intro_Feder,Feder setzt an,offen
Event.Cut.Intro.Strike,hit,sequencer,LS_Intro@120,-,SW_Intro_Loewe,Name gestrichen,offen
Event.Cut.Intro.Title,transition,sequencer,LS_Intro@210,-,SW_Whoosh_Titel,Titeltafel und Schwenk,offen
Event.Cut.Portfolio.Strike,hit,sequencer,LS_Portfolio@540,-,SW_Portfolio_Strich,Strich durch die Coda,offen
Event.Opera.Act.Bell,transition,code,-,sofort,MS_Act_Bell,Abblende Phasenwechsel,offen
Event.Opera.Phase.Warning,stinger,code,-,sofort,MS_Pauke_Warnung,Programmzettel pulsiert,offen
Event.Player.Disguise.On,foley,anim,-,sofort,MS_Disguise_Stoff,Kostuem wechselt,offen
Event.Player.Hide.Enter,foley,code,-,sofort,MS_Hide_Stoff,Kostuemstaender wackelt,offen
Event.Foley.Step,foley,anim,-,sofort,MS_Step_Holz,Fuss auf Bohlen,offen
Event.Transition.Ladder,transition,code,-,sofort,MS_Ladder_Knarz,Abblende Leiter,offen
Event.Transition.Trap,transition,code,-,sofort,MS_Trap_Winde,Abblende Versenkung,offen
Event.Cue.Gas.Down,hit,code,-,sofort,MS_Gas_Ventil,Gaslicht erlischt,offen
Event.Cue.Fly.Drop,hit,anim,-,sofort,MS_Sandsack,Sandsack schlaegt auf,offen
Event.Cue.Trap.Rise,hit,code,-,sofort,MS_Falltuer,Falltuer faehrt hoch,offen
Event.Lantern.Project.Lure,stinger,code,-,sofort,MS_Glas_Lure,Schemen winkt,offen
Event.Lantern.Project.Stage,stinger,code,-,sofort,MS_Glas_Geist,Geist auf der Buehne,offen
Event.Guard.Alert,stinger,code,-,sofort,MS_Stinger_Spotted,Auge wird rot,offen
Event.Score.Taken,stinger,code,-,sofort,MS_Stinger_Score,Mappe leuchtet cyan,offen
Event.Fail.Curtain,stinger,code,-,sofort,MS_Stinger_Curtain,Vorhang faellt,offen
Event.Silence.Start,silence,code,-,sofort,-,Figur haelt inne,offen
Event.Ending.B.Coda,hit,sequencer,LS_EndeB@60,-,MS_Coda,Vorhang mit Namen,offen
Event.Duck.Subtitle,duck,code,-,sofort,-,Untertitel sichtbar,offen
Event.Atmo.Keller,atmo,code,-,sofort,MS_Atmo_Keller,Keller und Zisterne,offen
Event.Atmo.Seitenbuehne,atmo,code,-,sofort,MS_Atmo_Seitenbuehne,Gasse und Pult,offen
Event.Atmo.Schnuerboden,atmo,code,-,sofort,MS_Atmo_Schnuerboden,Seile im Gegenlicht,offen
Event.Atmo.Loge,atmo,code,-,sofort,MS_Atmo_Loge,Samt und Saal,offen
Pulse.Buehnenlicht,pulse,curve,-,-,CV_Oper_Huellkurve,Gassenlicht und Gasflammen,offen
Event.Trailer.Break,silence,sequencer,LS_Trailer@750,-,-,Mappe in Stille,offen
Event.Trailer.Peak,hit,sequencer,LS_Trailer@810,-,SW_Trailer,Name in Licht,offen
Event.Trailer.Title,hit,sequencer,LS_Trailer@1050,-,SW_Trailer,Titelkarte,offen
```

**Die Tricks, nach Wirkung geordnet:**

1. **Licht folgt der Oper über die CSV-Hüllkurve (MUST, billig, robust).** René exportiert aus der DAW für jedes
   Opern-Stück die Lautstärke-Hüllkurve als CSV (Zeit, Wert). Sie wird als Curve Float importiert. Ein Tick liest die
   Kurve synchron zur Abspielposition und schreibt den Wert in `MPC_Global.AudioPulse` (0..1, Release 150-300 ms). Das
   Bühnenlicht in den Gassen, das Flackern der Gasflammen und das Glühen der Laterne lesen diesen Wert. Ohne
   Echtzeit-Analyse läuft das auch auf Renés Laptop (Stil-Leitfaden 3.11). Lauter heißt heller (eigenes Wissen).
2. **Durch Wände hören.** Die Oper ist fast überall gedämpft. Sänger stehen weit weg, im Gegenlicht oder verschleiert.
   Es gibt also **keinen Lippensync** und keine echte Gesangsstimme, und der Ton darf ungenau sein.
3. **Der Ton verkauft die Bewegung.** Falltür, Sandsack und Leiter sind eine Sekunde Translation oder eine Abblende.
   Erst Knarzen, Seilsirren und Aufprall machen daraus Maschinen (Foley in Schichten, Leitfaden 3.8). Synchrone
   Bild- und Tonereignisse verschmelzen zu einem Eindruck (Synchrese nach Chion, eigenes Wissen).
4. **Hit Points, Stille, dann Schlag.** In Cutscenes und Enden liegt vor jedem Hit Point `Event.Silence.Start`. Den
   Ton eher 1-2 Frames später als früher setzen. Ein Hit, den man vorhersehen kann, wirkt stärker [PREDICTIVE_CODING].
5. **Wer liefert zuerst (Regel für alle, Stil-Leitfaden 3.3):** *Beim Bau kommt die Musikskizze zuerst.* René
   nimmt an Tag 1 für Cold Open, *The Portfolio* und die Enden eine grobe eigene Skizze oder einen Klick im festen
   Tempo auf, der Kollege schneidet darauf. Danach schreibt René das Original mit denselben Akzenten. *Beim Trailer
   kommt der fertige Track zuerst:* René liefert ihn mit Markern (die `Event.Trailer.*`-Zeilen), der Kollege
   schneidet darauf. Fremde Temp-Musik wird nicht verwendet.
6. **J-Cut und Raumton.** Der Ton der nächsten Szene beginnt einen halben Takt vor dem Bild (J-Cut, eigenes Wissen).
   Jede Zone hat immer Raumton (Murmeln, Holz, Gas), es gibt nie digitale Stille. Abblenden bei Übergängen bekommen
   immer ein Geräusch.
7. **NICE: Quartz-Rasterung.** Maschinen-Effekte rasten auf den nächsten Schlag ein (Quartz-Clock, `PlayQuantized`),
   damit Ablenkungen wie Teil der Inszenierung wirken. Das gilt nur für den *sichtbaren Effekt* der großen Bühnen-Cues
   und nie für Bewegung oder Verdacht. Ebenfalls NICE ist die Echtzeit-Hüllkurve auf dem Submix statt der CSV (in 5.8
   unsicher).

**Feste Absprachen** (an Tag 1 in `sync-log.md`, Ereignisse in `sync-vertrag.csv`): Opernakte in **96 BPM, 4/4**,
Walzer 96 BPM, 3/4. Sequencer mit 30 fps,
jede Sequence beginnt bei Frame 0, Vorschau mit eingebranntem Timecode. Audio als WAV 48 kHz. Für die Lautheit gelten
die Werte aus Abschnitt 7.

---

## 9. Jury-Karte

| Kriterium | Warum es punktet | Ehrliches Risiko |
|-----------|------------------|------------------|
| Ambition & Innovation | Social Stealth in einer laufenden Premiere, Projektionen als Werkzeug, Hinterbühne als Spielwelt | Die Hitman-Struktur ist bekannt. Neu sind vor allem Ort und Laterne |
| Thema | Drei Ebenen: The Cut in der Story, die Spielerin als heimliche Regisseurin (*Scenes*, *Cues*), Ende B *ist* der Final Cut. Der Titel trägt die Doppelbedeutung auf Englisch | Die Jury sieht zuerst die Diebin. Gegenmittel: die Wörter *Cue* und *Scene* im UI, und im Trailer der Satz *"You direct the night."* |
| Spaßfaktor | Szenen stellen und zusehen, wie Figuren darauf hereinfallen. Der Chorgang über die offene Bühne ist ein Lacher | Spaß hängt an den NPC-Reaktionen. Wirken sie dumm, kippt es. Darum nur 3 Figuren, die dafür gut gemacht |
| Gameplay | 4 klare Verben, 3 Cues, sichtbarer Verdacht, 2 Fenster mit je mehreren Lösungen, Neustart in unter 2 s | Wenig Zeit zum Balancieren. Feste Fahrpläne machen das berechenbar |
| Visuals | Gaslicht-Noir, Proszenium vor dunklem Saal, cyan Geister. Sehr screenshotstark | Figuren aus KI. Abgefedert durch Schleier, Helme und Ansicht von hinten |
| Leveldesign & Progression | 4 gestapelte Zonen, 3 Weltzustände durch die Phasen, Eskalation nach dem Raub, 2 Enden | Wenige Zonen. Die Abwechslung kommt aus den Phasen, nicht aus der Fläche |
| Audio | Die stärkste Seite: eine echte Oper, ein gestohlenes Motiv als Dramaturgie, Zonen-Filter, Finale in zwei Fassungen, Licht aus der Hüllkurve | Etwa 12 Minuten Musik neben der ganzen Logik, alles bei René. Zwei Stücke gehen an den Musik-Experten |

**Sonderpreise:**
- **Best Team:** Die Arbeitsteilung ist sichtbar (Bild: Welt und Figuren, Ton: Oper und Systeme). Event-Liste und
  CSV-Hüllkurve zeigen, wie zwei getrennt arbeiten und doch ein Werk liefern. *Risiko:* Hakt die Synchronisation,
  sieht man genau das.
- **Render Royalty:** 3-5 Hero-Shots mit fester Kamera, nur diese poliert. Proszenium mit Blick in den Saal,
  Schnürboden im Gegenlicht, Loge 7 mit cyan Mappe. *Risiko:* Die Hero-Shots entstehen auf dem Rechner des Kollegen;
  im Build muss es auch ohne Lumen gut aussehen.
- **Glass Box:** Die Geschichte "Wie zwei Erstlinge eine Oper in 3,5 Tagen komponiert und mit KI-Agenten inszeniert
  haben". Dazu die Event-Liste, die Hüllkurve als Vorher/Nachher und als Aufhänger 16.11.1891 gegen 16.11.2026.
  *Risiko:* Zeit. Pro Tag 15 Minuten abends, nicht alles am Ende.

**Erster Eindruck:** Wenn die Jury sich gezielt ein Urteil bildet, prägt der Anfang das Spätere
[INITIAL_CONSTRUAL_PERSISTENCE]. Darum zeigen Trailer und Spiel in den ersten Sekunden die Kernmechanik und nicht
Schwarz mit Text.

---

## 10. Umfang

**MUST:**
- 1 Level mit 4 Zonen (Keller mit Zisterne und Graben-Winkel, Seitenbühne/Bühne mit Umzugsecke, Schnürboden,
  Logengang mit Loge 7)
- Third Person: gehen, schleichen, verstecken, E interagieren, Übergänge per Interaktion und Abblende (kein Klettern)
- 2 Verkleidungen (Bühnenarbeiterin, Chor) plus Startkleidung, Zonen-Erlaubnis je Kostüm
- **Feste Fahrpläne** für alle Figuren aus der Opernuhr (4 Phasen), Teleport beim Phasenwechsel
- 3 Figuren mit Sicht und Verdacht (Brac, Gaspard, Pompier), der Rest auf Schienen
- 3 Cues (Gas, Versenkung, Seilzug), Laterne mit Dia *Lure*, großer Bühnengeist in Fenster 2
- 2 Fenster: Entracte über die Schnürboden-Leiter, 2. Akt über den Chorgang (Interaktion *Join the procession*, 20 s
  auf Schienen)
- Checkpoints pro Fenster (CP0-CP4), R zum letzten Checkpoint, Neustart unter 2 s, **Musiksegment startet mit dem Checkpoint neu** (Abschnitt 5)
- Ende A, Ende B, Scheitern
- Cold Open (10 s), *The Portfolio* (35 s), 2 Enden (25 s und 40 s), alle überspringbar
- Musik: Cues 1-11, Zonen-Filter, CSV-Hüllkurve auf `MPC_Global.AudioPulse`
- Englische Texte: Titel, Zielzeilen, Untertitel, Tastenhinweise
- Gepackter Windows-Build, getestet auf Renés Laptop; Trailer

**NICE** (in dieser Reihenfolge, wenn Samstagabend Luft bleibt):
1. Gesprächsfetzen als Hinweise (3-4, als Text)
2. Quartz-Rasterung der Bühnen-Cues auf den Schlag
3. Regiebuch-Endbildschirm (Szenen, Route, Ende, Zeit)
4. Dia *Scare* (Figuren fliehen 20 s)
5. Applaus aus dem Saal, wenn ein Effekt vor dem Publikum passiert
6. Echtzeit-Hüllkurve statt CSV
7. Eine dritte Verkleidung (Logenschließerin) mit sozialer Route durch die Tür

**CUT:** Sprachausgabe und Lippensync, Niederschlagen, Kampf, Klettern, 3D-Publikum, eine eigene Garderoben-Zone,
mehrere Level, Seilphysik, freies Speichern, feste Kamera, echte Gesangsstimmen, Behavior Trees und EQS, mehr als 3
Figuren mit Wahrnehmung.

**Grober Plan** (Do 12.11. bis Abgabe Mo 16.11. 02:59; fertig spätestens So 24:00, danach 3 h Puffer):

| Tag | René (Code, Logik, Musik, Ton) | Kollege (Story, 3D, Cutscenes, Trailer) |
|-----|--------------------------------|------------------------------------------|
| Do 12.11. | C++-Projekt aus dem Template, Repo mit LFS. Opernuhr im GameState, Fahrplan-Datenstruktur, Kostüm- und Zonensystem, `AInteractable`. `sync-vertrag.csv` (Startdatei aus Abschnitt 8) und `sync-log.md` mit Tempo und Lautheit. Skizze für Cue 1 und Cue 8 | Graybox der 4 Zonen. **Abends gemeinsame Abnahme der Graybox.** Stilbibel (eine Seite), Palette, Master-Material, Referenz-Szene |
| Fr 13.11. | NPC-Zustandsautomat, Sicht, Verdacht, Alarm. 3 Cues, Laterne, Übergänge. Checkpoints inklusive Musik-Neustart pro Segment (Uhr = Abspielposition). Komponiert Cue 2 und 4 und die Spannungsebenen. Auftrag an den Musik-Experten (Cue 3, Cue 7) | 7 Figuren per KI-Generierung, Animationen. Kulissen-Flats. Keller und Seitenbühne einrichten |
| Sa 14.11. | Enden, Chorgang, UI (Auge, Programmzettel, Zielzeile). CSV-Hüllkurve, Zonen-Filter, Ducking. Komponiert Cue 5 und 6, Stinger und den Trailer-Track. **18 Uhr: erster gepackter Build, Test auf Renés Laptop (niedrige Stufe)** | Schnürboden, Logengang und Loge 7. Licht je Phase. Projektionsmaterial. Cold Open und *The Portfolio* im Sequencer auf Renés Skizzen |
| So 15.11. | Bugfixes, Balancing, 3 Testläufe mit jemandem, der das Spiel nicht kennt (erste 60 s). Feature-Freeze 16 Uhr. Finaler Build bis 22 Uhr. Dev-Log | End-Cutscenes. Hero-Shots. Trailer auf Renés Track schneiden, -14 LUFS prüfen. Key Art. Upload bis 24 Uhr |

**Renés Laptop ohne GPU:** René arbeitet in einer Graubox-Map mit Würfeln, die dieselben Tags auslösen, Editor auf
Low. Licht und Hero-Shots laufen auf dem Rechner des Kollegen. Der gepackte Build wird ab Samstag auch auf dem Laptop
getestet.

**Riskantestes technisches Teil: Wahrnehmung und Verdacht der 3 Figuren** samt der Rückkehr in den Fahrplan nach
einer Ablenkung.
- **Plan:** C++-Komponente mit 5 Zuständen, Sicht als Winkel- und Distanztest plus Line Trace, Bewegung per NavMesh
  `MoveTo` zwischen festen Wegpunkten.
- **Fallback:** **Lichtkegel auf dem Boden sind die Entdeckungszonen.** Die Regel lautet *"Stay out of the light - or
  wear the right costume."* Das ist ein Trigger-Volume pro Licht, im Theater sogar thematisch stimmig.
- **Zweites Risiko ist der Chorgang.** Fallback: Er fällt weg. Fenster 2 läuft dann über den Bühnengeist und die
  Schnürboden-Leiter.

---

## 11. Trailer 30-60 s

45 s, 96 BPM. René liefert den Track mit Markern zuerst, der Kollege schneidet die Clips darauf. **Die Kernmechanik
ist in den ersten 3 s zu sehen.** Gezeigte Verben: Verkleiden, Inszenieren, Projizieren. Höchstens 4 Texteinblendungen
in Englisch. Alles, was zu sehen ist, ist auch im Build [PERSUASION_KNOWLEDGE]. Video -14 LUFS, True Peak höchstens
-1 dBTP.

| Sek. | Bild | Ton |
|------|------|-----|
| 0-3 | **Hook = Mechanik**, genau die Szene aus den ersten 60 s im Build: Seitenbühne im Gegenlicht. Lucienne im Arbeitskittel löst an der Nagelbank ein Seil, der Sandsack kracht vom Schnürboden in die Gasse, der Pompier dreht sich weg und geht hin, sie gleitet hinter ihm zur Umzugsecke. Kein Schwarz, kein Logo | Seilsirren, Aufprall, darunter die Oper gedämpft |
| 3-10 | Sie hebt die Laterne, ein cyan Schemen Valcourts winkt, Gaspard folgt ihm aus dem Logengang. Text: *"You direct the night."* | Glasschimmer, Motiv "The Quill" beginnt leise |
| 10-25 | 4 Clips à 3-4 s, Schnitte auf jeden 4. Schlag: Kostüm vom Ständer → Gaslicht geht aus → Chorgang verschleiert über die offene Bühne vor dem Lichtermeer → Verdachts-Auge wird rot, sie taucht in den Kostümständer. Text: *"Every stagehand is a cue."* | Musik baut auf (Cue 4), Puls schneller, Ticken |
| 25-27 | Loge 7: Hand öffnet die Mappe, cyan Partitur, der Name gestrichen | **Stille**, nur Raumton |
| 27-35 | Peak: Ende B. Ihr Name in Licht auf dem Gazevorhang, Valcourt steht in der Loge auf | Coda setzt voll ein |
| 35-40 | Titelkarte *"SOTTO VOCE: The Cut"* über dem fallenden Vorhang. Text: *"Who gets the final cut?"* | Motiv in voller Form, löst auf |
| 40-45 | *"Epic AI MegaJam 2026 - Team Produktlicht"*, klein *"In-game footage"* | Ausklang, sauberer letzter Ton |

Der Peak liegt kurz vor dem Ende, und der Schluss ist stark. Das Ende eines Erlebnisses bleibt überproportional im
Gedächtnis (Peak-End-Regel, eigenes Wissen).

---

## 12. Risiken und offene Fragen

1. **Umfang des Hitman-Sandkastens.** Er ist gekürzt (4 Zonen, 3 wahrnehmende Figuren, Fahrpläne statt KI-Planung,
   keine Leitern), aber noch immer das größte Konzept der Runde. *Gegenmittel:* Graybox-Abnahme am Donnerstagabend,
   Fallback mit Lichtkegeln, Chorgang ist streichbar, Feature-Freeze am Sonntag um 16 Uhr. *Offene Frage:* Bleibt der
   Chorgang MUST oder wird er die erste Streichung?
2. **Nähe zu "Das Phantom der Oper".** *Gegenmittel:* Der "Geist" ist hier eine Projektion, die die Heldin selbst
   inszeniert. Es gibt keine Maske, keine Liebesgeschichte, keinen Kronleuchter. Es geht um eine Komponistin und um
   Autorschaft. Loge 7, nicht Loge 5. *Offene Frage:* Den Gerüchtenamen *Fantôme* behalten (Augenzwinkern) oder
   streichen (Abstand)?
3. **Musikmenge und Sync-Disziplin bei René.** Etwa 12 Minuten Musik plus Sound plus die ganze Logik. *Gegenmittel:*
   Tempo und Tags am Donnerstag festlegen, Cue 3 und 7 an den Musik-Experten, Akte aus Blöcken, Licht über die CSV.
   *Offene Frage:* Schafft René beide Finale-Fassungen? Notfall: Cue 5 wird auf 1:30 gekürzt und geloopt, die Coda
   folgt direkt auf die Kadenz.

Weitere offene Punkte: Name und Look der Heldin (Vorschlag Lucienne Varenne) und
Endbildschirm mit Wertung (Hitman-Stil, z. B. *"Invisible Director"*).

---

## Änderungen nach Review

- **Titel:** *SOTTO VOCE: The Cut* statt "Der Strich". "Cut" trägt die Kürzung, den Final Cut und "her cut". Alle
  Jury-Texte sind englisch, die Teamunterlage bleibt deutsch.
- **Umfang (Fix a):** 5 → 4 Zonen (Garderobe in die Seitenbühne). Feste Fahrpläne mit Teleport beim Phasenwechsel
  sind jetzt der Plan. Nur 3 Figuren nehmen wahr, und es gibt 7 statt 9 Meshes. Leitern, Versenkung und Souffleurgang
  sind Interaktionen mit Abblende, Klettern ist gestrichen.
- **Tempo (Fix b, PM 1):** Die Opernuhr dauert 12 statt 20 Minuten, das erste Fenster öffnet bei 3:00. Checkpoints
  gibt es pro Fenster (CP0-CP4), R führt zurück, der Neustart dauert unter 2 s. Das Cold Open ist 10 s lang statt
  55 s. Die längere Cutscene *The Portfolio* kommt nach dem ersten Erfolg und führt das Ende B ein.
- **Musik und Sync (Fix c, PM 3/4):** etwa 12 statt 23 Minuten, 2 Cues gehen an den Musik-Experten. Licht folgt der
  CSV-Hüllkurve (`MPC_Global.AudioPulse`). Echtzeit-Hüllkurve und Quartz-Rasterung sind NICE, Spieleraktionen kommen
  sofort. Der einzige Vertrag ist `sync-vertrag.csv` mit den 8 Spalten aus dem Leitfaden 3.1 (40 Startzeilen inkl.
  Trailer-Marker). Regel: Beim Bau kommt die Musikskizze zuerst, beim Trailer der fertige Track. Lautheit: Spiel
  -18 LUFS ±2, Video -14 LUFS, True Peak jeweils -1 dBTP.
- **Pitch, Stil und Trailer (PM 2/6/7):** Die Logline hat 24 statt 40 Wörter. Stil "Gaslicht-Noir" auf Basis von Leitfaden 1.1. Palette laut "Welcher Stil zu welchem
  Konzept": Hauptfarben Ochsenblut und Bernstein, Neutrale Schwarz und Rauchbraun, Messing nur entsättigt, Akzent
  Cyan. Staub und Lumen sind abschaltbar, der Test auf Renés Laptop ist eingeplant. Der Trailer ist
  45 s lang, zeigt die Mechanik in 0-3 s, 3 Verben, den Titel bei 35 s.

**Feinschliff nach Review Runde 2:**
- **Palette:** Das "kalte Blau" im 2. Akt ist gestrichen. Die Unterwelt wird über Dunkelheit, Nebel und schmale
  Bernstein-Gegenlichtkanten abgesetzt. Cyan bleibt die einzige kalte Farbe, auch im wichtigsten Akt.
- **Trailer-Hook = Build:** Der *Fly*-Cue sitzt jetzt an der Nagelbank in der Seitenbühne, der Sandsack fällt vom
  Schnürboden, der Pompier reagiert (Brac nur auf *Trap*). Zonentabelle, Cue-Tabelle, die ersten 60 s und der
  Trailer-Hook zeigen dieselbe Szene.
- **Musik springt mit dem Checkpoint (MUST):** Je Fenster beginnt ein eigenes Musiksegment. Beim Zurücksetzen gibt es
  eine Abblende mit Glocke, die Uhr wird gesetzt, das Segment startet neu. CP3 nutzt `Play(StartTime)` und hat einen
  Fallback. Das ist im Freitagsplan eingetragen.
