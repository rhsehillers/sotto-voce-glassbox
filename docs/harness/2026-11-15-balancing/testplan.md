# Handtest „Sotto Voce: The Cut“ – höchstens 20 Minuten (Rene, 15.11.)

Gespielt wird im **gepackten Development-Build** mit Test-Schaltern. `-svpos=x,y,yaw` arbeitet mit Karten-Koordinaten in cm
(+x Ost, +y Süd), yaw in Grad (0 = Ost, 90 = Süd, 180 = West, −90 = Nord). Mit `-svwindowlog` steht jede Sekunde die
Position jeder Wache im Log. Reihenfolge = Wichtigkeit: T1 entscheidet über Vorschlag #1, T2 über #3.
Hinter jedem Test steht, welcher Vorschlag aus `bericht.md` / `vorschlag-*.csv` davon abhängt.

**Zeitbudget:** 16,5 min Spielzeit plus ~3 min für 7 Starts des Builds (~25 s pro Start, bitte selbst messen) = ~20 min.
Wird es knapp, T3 und T4 auf nach der Abgabe schieben. Sie betreffen nur Code-Notizen, keinen Daten-Vorschlag.

| # | min | Start mit | Was spielen | Worauf achten | BESTANDEN | DURCHGEFALLEN → dann |
|---|---|---|---|---|---|---|
| T1 Start/Zonenregel (B1/B2) | 3 (2 Starts) | `-svnotitle -svwindowlog` | a) In eigener Kleidung 10 s am Start (250,−1150) stehen bleiben, nicht bewegen. b) Einmal absichtlich erwischen lassen (zum Pompier laufen), nach dem Neustart wieder 10 s stehen. c) Neustart mit `-svnotitle -svpos=1430,-735,90`: in eigener Kleidung warten, bis der Pompier auf seinem Süd-Schenkel (x ~1290) zu ihr schaut. | Pompier-Auge, Zeitpunkt des Fangs | a) und b): Auge bleibt leer, kein Fang. c): Auge füllt sich nicht (Regel „außerhalb der Zone erlaubt“) | a/b gefangen nach ~1–2 s: **Vorschlag #1 ist Pflicht** (strenge Lesart, Spiel sonst unspielbar). c) füllt sich: Chor-Station und Graben sind in eigener Kleidung gefährlich, der Bericht unterschätzt dann die Schwierigkeit |
| T2 Pause/Partitur (B5) | 3 | `-svnotitle -svclock=160 -svcue=SteamDown -svpos=1420,1480,0 -svwindowlog` | In Box 7 stehen bleiben, bis Gaspard zum Ventil gelaufen ist (Log, ~10 s), dann an der Partitur (1520,1520) „nehmen“ drücken. **Wird sie in den ersten 2 s erwischt** (Gaspard ist in der Pause in Box 7 und sieht sie vor dem Hebel; im Sim 2 von 20 Mal): einmal neu starten, das zählt nicht als Ergebnis | Geht die Partitur, obwohl Valcourt unsichtbar im Foyer ist? | Film startet, Partitur genommen | Partitur blockiert, obwohl niemand zu sehen ist: **Vorschlag #3 einspielen**. Hinweis: Im Sim ignorieren Off-Stage-NPCs Hebel, im C++ nicht. Ergebnis darum genau notieren. Ersatzweg, wenn auch der 2. Start sofort scheitert: ohne `-svclock` bis 2:30 im Versteck (900,−1350) warten. Das kostet **+3 min**, dafür T3 und T4 streichen |
| T3 Schacht aufwärts (B3) | 1,5 | `-svnotitle -svpos=80,650,180` | Am Schacht-Ende auf der Bühne (20,650) interagieren, **vor** dem Diebstahl | Kommt sie in Box 7 (1300,1580) an? | Nichts passiert / Hinweis „erst nach dem Diebstahl“ | Sie landet in Box 7: Abkürzung (Partitur nach 23,8 s nur mit dem Trap-Hebel). Code-Fix: Schacht nur abwärts – oder bewusst so lassen |
| T4 Paravent „gehört“ (B4) | 2 | `-svnotitle -svpos=1430,-760,0 -svcue=Fly,SteamDown,Trap -svwindowlog` | Bis t ≈ 16 s warten (alle Wachen sind unterwegs), dann am Paravent 2 (1490,−860) den Talar anziehen und heraustreten | Im Log in den 2 s nach dem Heraustreten: brechen Gaspard (Ventil 760,−1290), Valcourt/Brac (Falltür 600,0) oder der Platzanweiser ihren Weg ab und drehen um? | Alle bleiben auf ihrem Weg, bis ihre Zeit abläuft (Valcourt ~30 s an der Falltür) | Alle drehen gleichzeitig um: B4 bestätigt. Code: IsBehindScreen löschen, bevor sie sich bewegt. Die Route bleibt im Sim trotzdem gewinnbar |
| T5 Bracs Blick nach dem Hebel | 2 | `-svnotitle -svcue=Trap -svwindowlog -svpos=450,-1100,180` | Im Kittel stehen bleiben (falls T1 streng: erst umziehen) und Brac beobachten, bis er zurück ist (~26 s) | Sitzt/arbeitet Brac an seinem Pult (250,−650) und schaut nach Westen (180°)? Oder bleibt er ~80 cm davor stehen und schaut nach Nordwesten? | Kein Bestanden/Durchgefallen, sondern: **welcher Fall?** | **Fall A – Brac bleibt ~80 cm vor dem Pult stehen** (= Sim-Standard): Die Zahlen im Bericht gelten. 2 s Zögern bei (200,−900) heißt heute ~50 % erwischt. **Fall B – Brac sitzt am Pult und schaut nach Westen:** Die Flucht ist härter. 2 s Zögern bei (200,−900) heißt heute 100 % erwischt, bei (75,−745) dafür 0 %. In beiden Fällen hilft **#2 (FillSeer 0.12)**: 0 % erwischt. Code-Notiz Settle-Radius ≥ 90 erzeugt Fall B, also nur zusammen mit #2 |
| T6 Ganze Route + Flucht | 5 | `-svnotitle` (ohne weitere Schalter; **mit den Vorschlägen, die du übernommen hast**) | Geplante Route laut `bericht.md`, Abschnitt 1: Kittel → Trap/Steam/Fly → Talar an der Chor-Station (1550,−1010) → Kulissenöffnung → Streifen x 75 → Proszeniumstür → Box 7 → Schacht → Bühnentür. Auf der Flucht bei (200,−900) **absichtlich 2 s stehen bleiben** | Gefangen wo, von wem? Talar-Ständer am richtigen Ort zu finden (Notizbuch 017)? HUD-Ziel klar? Dreht der Platzanweiser an den Kulissen um, weil er Schritte hört? | Sieg in ≤ 2 Versuchen. Erwartung für die 2-s-Pause laut Sim: **ohne #2** ~50 % überlebt (Fall A aus T5) bzw. 0 % (Fall B); **mit #2 (0.12)** 100 % in beiden Fällen | Fang an einer Stelle, die der Bericht sicher nennt: Ort und Wache notieren (Sim-Annahme falsch). Mit #2 trotzdem bei (200,−900) gefangen: Sim weicht vom Spiel ab. FillSeer 0.10 (Min) ist der letzte Schritt (im Sim ebenfalls 100 %, `analysis/deliverable-review/rerun_escape.txt`) |
| Starts + Reserve | 3,5 | – | 7 Starts à ~25 s; Rest: T1a nach dem Einspielen der Vorschläge wiederholen | – | – | – |

## Nur wenn Zeit bleibt (nicht in den 20 min)

- **Notizbuch** (falls du die Texte aus `bericht.md`, Abschnitt 4 übernommen hast): Tab öffnen und prüfen, ob die
  Zeilen 004, 013 und 017 passen.
- **Blinde Scheibe (NEW-1), 1,5 min:** Start mit `-svnotitle -svpos=1558,1388,150`, sofort ducken (1,25 m vor dem
  sitzenden Valcourt). **Den kurzen Ausschlag des Auges direkt nach dem Start ignorieren** – sie erscheint stehend und
  wird kurz gesehen. Gezählt wird nur, ob das Auge nach dem Ducken wieder fällt und dann 10 s leer bleibt. Bleibt es leer,
  ist die blinde Scheibe bestätigt (Code-Notiz nach der Jam: Kegel in 2D prüfen). Füllt es sich weiter: kein Problem.
- **Erstspieler-Test:** Einen Menschen, der das Spiel nicht kennt, 10 Minuten ohne Hilfe spielen lassen. Notieren:
  - Fänge
  - Minuten bis zum ersten Sieg
  - wo er hängen bleibt
  - ob er weiß, was mit der Partitur zu tun ist

  Das ist die einzige echte Prüfung der Schwierigkeitsschätzung (Modell: Neuling ~3 Fänge, ~7,5 min).

## Ergebnis (zum Ausfüllen)

| Test | bestanden / durchgefallen | Notiz |
|---|---|---|
| T1 a / b / c | | |
| T2 | | |
| T3 | | |
| T4 | | |
| T5 | | |
| T6 (Route) | | |
