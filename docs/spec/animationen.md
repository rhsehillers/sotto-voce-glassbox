# Figuren und Animationen - was das Spiel braucht

**Stand:** 12.11.2026, mit René abgestimmt ("ja passt soweit"). Der Kollege prüft und ergänzt mit seiner Instanz
(Ergänzungen bitte unten unter *Ergänzungen Art-Seite* mit Datum, damit beide Seiten sehen, was neu ist).
**Zweck:** Der Kollege kann jede Figur sofort komplett modellieren, weil hier steht, welche Bewegungen sie können muss,
welche Requisiten sie in der Hand hält und was der Code zum Abspielen liefert.

## 1. Was schon im Projekt ist

Nur die Animationen aus der Unreal-Vorlage (`Content/Characters/Mannequins/Anims/Unarmed`, Skelett `SK_Mannequin`):
- `MM_Idle` (Stehen), `MF_Unarmed_Walk_*` (Gehen, 8 Richtungen), `MF_Unarmed_Jog_*` (Laufen, 8 Richtungen),
  `MM_Jump`/`MM_Fall_Loop`/`MM_Land` (Springen - im Spiel nicht belegt), Blendspace `BS_Idle_Walk_Run`,
  Anim-Blueprint `ABP_Unarmed`.
- Das reicht für **Gehen und Laufen aller Figuren**. Alles andere unten fehlt.
- Pistole, Gewehr, Angriffe, Treffer- und Todesanimationen liegen auch dort - **nicht verwenden** (kein Kampf im Spiel).

## 2. Regeln, damit die Figuren gleich komplett gebaut werden können

**Skelett und Maße**
- Jede Figur wird auf das **UE5-Mannequin-Skelett `SK_Mannequin`** geriggt (Lucienne und Frauen wie Quinn, Männer wie
  Manny). Dann laufen alle Animationen auf allen Figuren, ohne eigene Animationsarbeit.
- Proportionen nah am Mannequin halten (Größe etwa 170-185 cm). Starke Abweichungen kosten Nacharbeit beim Retargeting.
- Kapsel im Spiel: Radius 42 cm, halbe Höhe 96 cm (ca. 192 cm hoch); Mesh-Versatz Z -96, Drehung -90 (Standard).
- **Hocken:** Die Kapsel wird auf 110 cm Höhe kleiner (halbe Höhe 55). **Der Kopf muss beim Hocken unter ca. 95 cm
  bleiben**, denn die Deckungen sind ca. 1 m hoch und die Sichtprüfung testet den Kopf eines Hockenden bei ca. 80 cm.

**Kleidung muss diese Bewegungen aushalten** (ohne dass Stoff durch Beine oder Arme stößt):
- tiefes Hocken mit gebeugten Knien (Lucienne)
- Sitzen mit 90 Grad in Hüfte und Knie (Valcourt; ggf. ein Bühnenarbeiter auf einer Kiste)
- Arme über den Kopf, für den Kostümwechsel (Lucienne)
- Unterhandwurf (Lucienne)
- Lucienne (eigene Kleidung) trägt **keinen Rock**, sondern Reithose + hohe Stiefel (Stand Art-Seite 12.11.,
  siehe *Ergänzungen Art-Seite*) - Hocken ist damit unkritisch; lange Mäntel (Valcourt) nur so
  lang, dass sie im Sitzen nicht durch den Stuhl gehen.

**Requisiten sind eigene Meshes an Sockets, nicht in den Körper eingebaut.** Dann kann der Code oder der Blueprint sie
zeigen, verstecken und von einer Hand in die andere geben.

| Figur | Requisit | Socket (am Skelett anlegen) |
|---|---|---|
| Lucienne | Aufzieh-Gadget (Metronom) am Gürtel / beim Werfen in der Hand | `belt_gadget` an `pelvis` rechts, `hand_r` |
| Lucienne | Partitur-Mappe nach dem Raub | `chest_score` an `spine_05` (an die Brust gedrückt) bzw. `hand_l` |
| Valcourt | Taktstock aus Ebenholz | `hand_r` |
| Valcourt | Mappe auf dem Schoß (Akt 1 + 2) | `lap_score` an `pelvis` |
| Brac | Sprachrohr um den Hals | `neck_01` |
| Brac | Taschenuhr an Kette | `hand_l` (beim Nachsehen), sonst `spine_03` |
| Gaspard | hoher Leuchter (Gas- oder Dampflampe) | `hand_r` |
| Pompier | Messinghelm mit Nackenschutz | `head` (kann auch Teil des Meshes sein) |

**Luciennes drei Looks** (eigene Kleidung, Arbeitskittel, Chorkostüm mit Schleier) laufen auf **demselben Skelett**.
Der Wechsel kommt über das Ereignis `OnCostumeChanged` (Tag `Costume.Own` / `Costume.Worker` / `Costume.Chorus`)
im Blueprint-Kind von `ASVCharacter`: Mesh oder Material tauschen. Statisten (Bühnenarbeiter, Chor) bekommen **eigene
Meshes** (Männer, anderes Gesicht), damit man sie nicht mit der verkleideten Lucienne verwechselt (Art-Seite 12.11.).

**Sitzen braucht Möbel:** Valcourts Stuhl in Loge 7 steht an seinem Punkt (1450, 1450), Blickrichtung zur Bühne
(Yaw -120). Brac arbeitet am Pult `M2_BracDesk` bei (170, -650), er steht bei (250, -650) und schaut zum Pult (Yaw 180).

## 3. Animationsliste

**Prio:** MUST = für die Abgabe nötig, NICE = wenn Zeit bleibt. **Art:** Schleife (Loop) oder einmal (Montage).
Schleifen ohne Root Motion (an Ort und Stelle). Montagen im Slot `DefaultSlot`.

### Lucienne (Spielfigur)

| Animation | Wann im Spiel | Art, Länge | Prio | Auslöser im Code |
|---|---|---|---|---|
| Hocken, stehend | Strg gedrückt | Schleife | MUST | `bIsCrouched` (Character) |
| Hocken, gehend - vor, zurück, links, rechts | Strg + Bewegung (160 cm/s) | Schleife, Blendspace | MUST | `bIsCrouched` + Geschwindigkeit |
| ~~Kostümwechsel: Arm rein, Kostüm drüber, anderer Arm~~ **entfällt (Team 13.11.):** sie verschwindet hinter einer Trennwand, solange sie sich umzieht | E am Kostümständer | - | entfällt | `OnAction(ChangeCostume)` bleibt (z. B. für einen kurzen Schritt hinter die Wand, NICE) |
| Ventilrad drehen | Cue *Steam down* am Ventil | einmal, ca. 1,2 s | MUST | `OnAction(TurnValve)` |
| Hebel ziehen | Cues *Trap* und *Fly* | einmal, ca. 1,0 s | MUST | `OnAction(PullLever)` |
| Mappe vom Tisch nehmen, an die Brust drücken | Partitur in Loge 7 nehmen | einmal, ca. 1,2 s | MUST | `OnAction(TakeScore)` |
| Gadget aufziehen und werfen (Unterhand) | F | einmal, ca. 1,0 s | MUST | `OnAction(ThrowGadget)` |
| Partitur aufs Dirigentenpult legen | Ende B | gehört in die Sequenz *Final Cut* des Kollegen | MUST (Sequenz) | `OnAction(PlaceScore)`, `ASVGameMode::OnEnding` |
| Erstarren, Hände leicht heben | erwischt, kurz vor der Vorhang-Karte | einmal, ca. 0,8 s | NICE | `OnAction(Caught)` |
| In ein Versteck treten / heraustreten | E am Versteck (Kostümständer, Vorhang) | einmal, ca. 0,6 s | NICE | `OnAction(Hide)` / `OnAction(LeaveHide)` |
| In die Luke ducken | Wartungsschacht | einmal, ca. 0,5 s | NICE | `OnAction(EnterShaft)` |

- **Durch den Schacht kriechen** braucht keine Animation: Der Weg durch den Schacht ist abgeblendet (ca. 1 s schwarz).
- **An die Wand lehnen** braucht Lucienne nicht: Sie hockt hinter Deckung, ein Wandlehnen-System gibt es nicht.
- **Rennen** (Shift, 550 cm/s) und **Gehen** kommen aus der Vorlage. **Schleichen** = Hocken-gehend.

### Figuren mit Wahrnehmung: Pompier, Gaspard, Brac

Damit man sieht, was sie denken (Spec Abschnitt 4: "Absicht zeigen").

| Animation | Wann | Art | Prio | Auslöser im Code |
|---|---|---|---|---|
| Umsehen, suchen | Nachsehen bei Cue, Gadget oder Geräusch (10-15 s) | Schleife | MUST | `GetGuardState() == Investigate` |
| Misstrauisch hinstarren, leicht vorgebeugt | Verdacht ab 60 % | Schleife | MUST | `GetGuardState() == Suspicious` |
| Zeigen und rufen | Alarm: Lucienne ist erwischt | einmal, ca. 1,0 s | MUST | `Suspicion.OnStateChanged` -> `Alarm` |
| Kurzes Stutzen, Kopf drehen | bemerkt etwas, ab 25 % | einmal, ca. 0,5 s (additiv) | NICE | `Suspicion.OnNoticed` |

### Tätigkeiten an den Wegpunkten (alle NPCs)

Was eine Figur tut, während sie an ihrem Punkt steht, steht in `Data/schedule.csv` in der Spalte **`Activity`**. Der
Anim-Blueprint fragt `GetActivity()` und `IsAtActivity()` (true, solange sie dort steht und nicht reagiert) und spielt
die passende Schleife. Beim Gehen läuft die normale Fortbewegung.

| Activity | Wer, wann | Animation | Prio |
|---|---|---|---|
| `Sit` | Valcourt in Loge 7 (Akt 1, Akt 2, Finale), Mappe auf dem Schoß | Sitz-Idle, gelegentlich Taktstock heben | MUST |
| `Work` | Brac am Inspizientenpult (Akt 1, Akt 2, Finale); Kontrollgang in der Pause | Hebel bedienen, Taschenuhr ansehen, ins Sprachrohr sprechen | MUST |
| `Guard` | Pompier (immer), Gaspard (Logengang, Loge) | Wache stehen: Hände hinter dem Rücken (Gaspard, Leuchter in der Hand), Hand am Helm (Pompier) | NICE |
| `Lean` | Bühnenarbeiter in der Pause | an die Wand lehnen, stehend | NICE |
| `Carry` | Bühnenarbeiter in Akt 1, Akt 2, Finale | Seil ziehen oder Kiste tragen | NICE |
| `Sing` | Chor in Akt 2 (zieht über die Bühne) | singen, im Stehen und im Gehen (Oberkörper) | NICE |
| `Search` | Gaspard und Pompier nach dem Raub | suchend gehen, sich umsehen | NICE (sonst `Umsehen`) |
| `Stand` | alle anderen | `MM_Idle` aus der Vorlage | vorhanden |

- Optional: ein Bühnenarbeiter **sitzt auf einer Kiste** (dann neue Activity `SitCrate`, sag Renés Seite Bescheid).
- Valcourt **stürmt** beim Cue *Trap* aus der Loge: das ist schnelles Gehen/Laufen aus der Vorlage.

## 4. Was der Code liefert (Anschlüsse)

| Wo | Name | Was |
|---|---|---|
| `ASVCharacter` (Lucienne) | `OnAction(ESVAction)` | Ereignis pro Aktion: TurnValve, PullLever, ChangeCostume, Hide, LeaveHide, TakeScore, PlaceScore, EnterShaft, ThrowGadget, Caught, Use |
| `ASVCharacter` | `OnCostumeChanged(Tag)` | Kostüm ist gewechselt: Look tauschen |
| `ASVCharacter` | `bIsCrouched`, `IsChangingCostume()`, `HasScore()`, `IsInHideSpot()` | Zustände fürs Anim-BP |
| `ASVCharacter` | `bSquashWhenCrouching` | Platzhalter-Stauchen beim Hocken; **im Blueprint-Kind ausschalten**, sobald die Hock-Animationen da sind |
| `ASVGuard` (alle NPCs) | `GetActivity()`, `IsAtActivity()`, `GetGuardState()` | Tätigkeit und Wahrnehmungszustand fürs Anim-BP |
| `ASVGuard` -> `Suspicion` | `OnStateChanged(Alt, Neu)`, `OnNoticed` | für Montagen (Zeigen/Rufen, Stutzen) |
| `ASVGameMode` | `OnColdOpen`, `OnEveningStarts`, `OnEnding(Id)` | Sequenzen (Cold Open, Ende A/B) |
| `ASVTransitionPoint` | `OnTransit` | Schacht: Geräusch / Effekt |

## 5. Wohin damit

- Figuren: `Content/Art/Characters/<Figur>/`, Animationen: `Content/Art/Animations/<Figur>/` (gemeinsame unter
  `Content/Art/Animations/Shared/`).
- Je Figur ein Blueprint-Kind: Lucienne von `ASVCharacter`, jede NPC-Figur von `ASVGuard` (Pompier, Gaspard, Brac,
  Valcourt, Chorsänger, Bühnenarbeiter). **Den Pfad jedes Blueprint-Kinds Renés Seite sagen** (BOARD): dann setzt
  `ASVGameMode` Lucienne als Spielfigur und `Tools/Editor/place_m2.py` stellt die NPC-Kinder statt der C++-Klasse auf
  (Logik und `NpcId` bleiben gleich).
- Quellen für Animationen: Mixamo (per IK Retargeter auf `SK_Mannequin`), Epics kostenloses *Game Animation Sample*
  (enthält z. B. Hock-Fortbewegung), Fab. **Jede Quelle mit Lizenz in `ASSETS.md`.**

## Ergänzungen Art-Seite

*(Kollege: hier mit Datum ergänzen.)*

**12.11.2026 abends (Art-Seite, Mehmet):**
- **Luciennes finaler Look (eigene Kleidung):** kurze taillierte flaschengrüne Jacke (endet an der Taille) mit Messingknoepfen + Notenschlüssel-Brosche, dunkle Lederweste über elfenbeinfarbener Stehkragen-Bluse, enge dunkelbraune Reithose in hohen geschnürten Lederstiefeln, breiter Gürtel mit Taschen und Aufzieh-Metronom, fingerlose Lederhandschuhe mit Tintenflecken; KEIN Rock, KEIN Mantel, KEIN Stift im Haar. Referenz: `artwork/figuren/lucienne_eigen/look_v3.png`, `charakterblatt_v2.png`, `tripo_*_v2/_v3.png`. Der Socket für den Bleistift entfällt.
- **Kittel-Look:** `artwork/figuren/lucienne_kittel/` (Leinenkittel, Lederschürze, Schirmmütze, Reithose, Stiefel). **Chor-Look (final 12.11. spätabends, Mehmet):** `artwork/figuren/lucienne_chor/look_v4.png` - weiblich taillierte violette Chor-Jacke (bis zur Hüfte, Messingknöpfe), helle Rüschenbluse mit Schleife, dunkle Hose, Schnürstiefel; **kein Rock, kein Schleier**. Look freigegeben; Charakterblatt + Tripo-Ansichten (`_v4`) sind bei Codex in Arbeit.
- **Statist Chorsänger:** kein langes Gewand, sondern kurzer violetter Chor-Gehrock (bis Mitte Oberschenkel), Hose, Schuhe.
- **Statisten bekommen eigene Figuren:** `artwork/figuren/statist_buehnenarbeiter/` und `statist_chorsaenger/` (Männer). In der Liste der Blueprint-Kinder bleiben sie wie geplant (Chorsänger, Bühnenarbeiter).
- **12.11. spätabends - Hock-Animationen sind im Projekt** (`Content/Art/Animations/Shared/Crouch/`, auf `SK_Mannequin`):
  `A_Crouch_Idle_Loop` (+ `_Break_v01/v02`, `_Turn_090_L/R`), `A_Crouch_Loop_F/B/LL/RR/FL/FR/BL/BR` (Root Motion vorwärts),
  `A_Transition_Stand_to_Crouch`, `A_Transition_Crouch_to_Stand`. Quelle Epic *Game Animation Sample*, für Renés Regel
  **tiefer gemacht** (Oberkörper leicht geduckt, 35 Grad; Hüfte beim Schleichen bis 16 cm tiefer; Füße exakt am Boden):
  **Kopf-Knochen max. 0,93 m** (Mehmet wollte es natürlicher als 0,83 m). Hinter 1-m-Deckungen schaut höchstens
  ein Haar-Ansatz heraus -> Deckungen bitte **ca. 1,05-1,10 m** hoch (Kit E ist 0,9-1,1 m); die Sichtprüfung bei 80 cm passt. Dazu `Sit/` (Bank: hinsetzen, sitzen, aufstehen) und
  `Idle/` (Stehen + Umsehen-Varianten für die Wachen).


**13.11.2026 15:23 (Art-Seite, Abgleich Spec <-> Projekt, Pruef-Agent + Spieltest):**
Es fehlen keine Dateien; alle Figuren/ABPs/Skelette sind gueltig. Offen ist, was **nicht passt oder nur Platzhalter ist**:

| # | Figur | Was | Ist jetzt | Fehlt / Problem | Prio | Wer |
|---|---|---|---|---|---|---|
| 1 | alle NPCs | Gehen 110-150 cm/s | Vorlage-Walk ist fuer 300 cm/s | **langsamer Geh-Clip + eigener NPC-Blendspace** (Fuesse rutschen sonst) | MUST | Art |
| 2 | alle NPCs | Drehen auf der Stelle (LookAround 80 Grad/s, Spieler ansehen 300 Grad/s) | Koerper dreht ohne Fussbewegung | Turn-in-Place 90/180 L/R im NPC-ABP; Code: langsamer drehen | MUST | Art + Rene |
| 3 | Pompier, Gaspard, Brac | Umsehen/Suchen (Investigate, Search) | A_Relaxed_Stand_Idle_Break_v02 (entspannt) | **Umsehen/Suchen-Loop** | MUST | Art |
| 4 | Pompier, Gaspard, Brac | Misstrauisch starren (Suspicious) | A_Idle_No_Loop (Kopfschuetteln) | **vorgebeugt hinstarren** | MUST | Art |
| 5 | Pompier, Gaspard, Brac | Zeigen + rufen (Alarm) | A_Idle_Rail_Call (Rufen am Gelaender) | **Zeigen + Rufen** (einmal, ~1 s) | MUST | Art |
| 6 | Lucienne | Ventilrad drehen | A_Interact (allgemein) | **Ventilrad drehen** (~1,2 s) | MUST | Art |
| 7 | Lucienne | Hebel ziehen | A_Push_Loop (schieben) | **Hebel ziehen** (~1,0 s) | MUST | Art |
| 8 | Lucienne | Gadget werfen | A_OverhandThrow (Ueberhand) | Spec: **Unterhand**-Wurf mit Aufziehen; Abstimmen mit Renes neuer Wurf-Logik | MUST | Art + Rene |
| 9 | Lucienne | Mappe nehmen, an die Brust | A_PickUp_Table | an die Brust druecken fehlt (Teil 2 der Bewegung) | MUST | Art |
| 10 | Brac | Arbeiten am Pult | A_Interact | Hebel bedienen / Taschenuhr / Sprachrohr | MUST | Art |
| 11 | Buehnenarbeiter | Carry | A_Push_Loop (Schritte auf der Stelle) | **Seil ziehen** (Stand-Loop ohne Beinbewegung) | NICE | Art |
| 12 | Lucienne | Hocken an/aus | Uebergang 2,5 s | Uebergang kuerzen (~0,4 s), Strg reagiert sonst spaet | NICE | Art |
| 13 | Lucienne | Rennen 550 cm/s | Jog-Clip 600 cm/s | Rate Scale ~0,92 | NICE | Art |
| 14 | Lucienne | Erwischt (Caught) | A_Hit_Chest (Treffer) | Erstarren, Haende heben | NICE | Art |
| 15 | NPCs | Stutzen (OnNoticed), Guard-Varianten (Haende hinterm Ruecken, Hand am Helm), Singen | Platzhalter/fehlt | eigene Clips | NICE | Art |
| 16 | alle | Requisiten an Sockets (Taktstock, Mappe auf dem Schoss, Sprachrohr, Taschenuhr, Leuchter, Gadget) | fehlen | Meshes + Sockets | MUST (Valcourt/Gaspard), sonst NICE | Art |
- Erledigt 13.11.: Valcourts Sessel (Megascans-Ohrensessel, `L_Main_Art`, Yaw -120, ohne Kollision) - er erreicht jetzt seinen Punkt und sitzt (vorher MoveTo failed -> Sitz-Loop in der Luft).
- Fuer Rene (Code): Drehtempo LookAround/LookAtPlayer (SVGuard.cpp ~251-258, 319-333, 476), bei fehlgeschlagenem MoveTo keinen Taetigkeits-Loop spielen, `SVGuard_0` bei (-800, 1400) steht neben dem Navmesh.

**13.11.2026 16:12 (Art-Seite) - Stand der Liste oben:**
- erledigt + auf allen 9 Figuren geprueft (Pruefbogen im Showroom): 1 NPC-Gehen (BS_NPC_Gehen/ABP_NPC, GASP Relaxed Walk),
  2 Drehen auf der Stelle (Schritt-Clips, `USVNPCActivityAnims` TurnLeft/TurnRight), 3 Umsehen/Suchen (Mixamo; Gaspard mit
  Leuchter-Haltung), 4 Misstrauisch (in die Ferne starren), 5 Alarm (vortreten + rufen), 6 Ventil (Hand-ueber-Hand),
  7 Hebel ziehen, 8 Unterhand-Wurf, 10 Brac am Pult (Signalknopf; Uhr-Variante liegt bereit), 11 Seil ziehen,
  13 Rennen (RateScale 0,917), 14 Erwischt (erschrecken), 15 Stutzen (`Suspicion.OnNoticed`), Singen.
- 12 Hock-Uebergang: die 2,5-s-Clips werden in ABP_Lucienne nicht benutzt (Wechsel per Blend 0,25 s) -> Strg reagiert sofort.
- offen: 9 Mappe an die Brust (Mixamo-Clips passten nicht -> eigene Pose), 16 Requisiten an Sockets.
- Mixamo-Finger werden nicht uebertragen (fremde Fingerhaltung = Krallen); Schuerze/Kittelsaum/Frackschoesse haengen nicht
  mehr an den Armen (`tools/figur_unten_ohne_arme.py`).

**13.11.2026 16:50 (Art-Seite, dv.commit.168) - 3. Runde, im Hauptlevel getestet:**
- Finger: in allen Live-Retargetern abgekoppelt (keine Krallen mehr); Haende mit Requisit greifen fest (Gaspard, Valcourt
  rechte Hand; `tools/ue_griff_haltung.py`), Gaspards Hand steht senkrecht um die Laternenstange.
- Requisiten (`USVPropAttacher`, `Content/Art/Props/Handrequisiten`): Valcourt Taktstock + Mappe auf dem Schoss (nur im
  Sitzen), Gaspard Laterne (haengt immer gerade), Brac Sprachrohr + Taschenuhr (nur beim Uhr-Clip), Lucienne Mappe an der
  Brust mit verschraenkten Armen, solange sie die Partitur hat (9 erledigt).
- `USVNPCActivityAnims`: ActivityExtras (Valcourt gestikuliert mit dem Taktstock, Brac Uhr / Sprachrohr, Pompier Hand an den
  Helm), AlarmStart (erst zeigen, dann rufen), Dreh-Clip endet mit der Drehung.
- Lucienne: ins Versteck ducken / heraustreten / in die Luke ducken (GASP-Hockuebergaenge, 0,5-0,6 s).
- NICHT umgesetzt (Clips ungeeignet, ehrlich offen): Chor singt im Gehen (Clip hat keine Schritte), Suchen im Gehen
  (GASP-Patrouillen-Clip laeuft nicht auf der Stelle). Beides laeuft im Stehen.
- Gadget in Luciennes Hand: bewusst nicht (OnAction(ThrowGadget) kommt erst beim Abwurf; `SM_Metronom` liegt als Look fuer
  `ASVGadget` bereit).
