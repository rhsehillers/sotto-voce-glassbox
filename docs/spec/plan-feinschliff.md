# Plan: Feinschliff nach Renés Spieltest (14.11. nachmittags)

Stand 14.11. ~16:00, PM. Renés Spieltest-Feedback, geprüft gegen Code, Daten und Level. **Nichts davon ist schon
umgesetzt.** Ordnung: erst was das Spiel kaputt oder unklar macht, dann Balancing (Renés Werte), dann Neues.

## Was die Prüfung ergeben hat

| Befund (René) | Ursache |
|---|---|
| Am Buch nach Valcourt: nicht aufhebbar, keine Anzeige; E schickt in den Schacht | Das Buch zählt jede Wache im Umkreis von 4,5 m als "Aufpasser" - **auch durch die Wand** (Gaspard im Gang, ein gelockter NPC). Dann ist das Buch stumm, und E nimmt das nächste Benutzbare: die Schachtluke 2,3 m daneben |
| Im Logengang sofort erwischt, man sieht nichts | Der Logenschließer dreht bei X 200 um - **genau vor der neuen Proszeniumstür** (X 60-180) und 1 m neben dem Gang-Vorhang. Wer reinkommt, steht neben ihm; dazu ist der Eingang dunkel |
| Vorhang im Gang: kommt ein NPC zu nah, keine Chance | Versteckt nimmt niemand sie wahr; aber der Logenschließer wartet 3 s direkt vor dem Vorhang - rauskommen geht nur in seinen Rücken |
| Durch große Bilder, Kulissen, den leeren Stuhl laufen | Seit 11:20 hat **die ganze Kunst-Ebene keine Kollision** (198 Teile; 81 davon groß genug zum Anstoßen: Kulissen Garten/Palast, Kostümständer, Fässer, Leinwandrollen, Pult, Tafel, Grabenbrüstung, Valcourts Sessel ...). Wände halten, weil die Graubox-Wände dahinter Kollision haben |
| Durchrennen klappt immer, an der ersten Wache vorbeigehen auch | Füllung beim Rennen 0,25/s, falsche Zone 0,34/s: ~3 s Sichtkontakt bis zum Alarm - Vorbeirennen dauert ~2 s |
| Figuren "sehen nach hinten" | Sie hören Schritte: Gehen 4 m, Rennen 10 m hinter dem Rücken -> sie drehen sich um |
| Durch den Schacht erwischt Valcourt sie immer | Die Luke kommt in Loge 7 heraus, ~2 m vor Valcourts Sessel, in seinem Blick |
| Text beim Umziehen passt nicht | Eine Zeile mit 16 px in einer 340 px breiten Box |
| Kleidung fliegt nicht richtig über die Wand | Die Wurfbahn ist fest, Mehmets neue Paravents sind anders hoch |
| Valcourts Beine im Sessel | Sitzpunkt (Daten) und Sessel (Kunst) passen nicht zusammen |
| Umziehen nicht nötig und nicht klar, unklar was zu tun ist, viel Warten | Das Ziel ist eine einzige Zeile ("Get into Box 7"); die Opernuhr-Fenster sieht man nur im Programmheft; Akt 1 dauert 2:30, das erste echte Fenster kommt erst in der Pause |

**Hitman zum Vergleich:** Eine Verkleidung täuscht dort alle - außer den "Enforcern" (weißer Punkt über dem Kopf):
Leute derselben Rolle, die sie aus der Nähe durchschauen. Umziehen ist nur verdächtig, wenn jemand zusieht. Wer
"kompromittiert" ist, schüttelt die Suche durch eine neue Verkleidung ab. Bei uns sind die Durchschauer (Brac bei
Bühnenarbeitern, Gaspard im Gang) die Enforcer - **nur sieht man nicht, wer einen durchschaut.**

## A. Fehler (Code-Seite, sicher)

1. **Buch:** "Aufpasser" nur, wer das Buch wirklich sieht (Sichtlinie, gleicher Raum); ist es blockiert, zeigt der
   Prompt den Grund ("Gaspard is watching the score"); E springt dann nicht in den Schacht.
2. **Umzieh-Text** zweizeilig, Box größer.
3. **Kleidungswurf** über die echte Oberkante des Paravents.
4. **Kollision:** unsichtbare Blocker auf unserer Gameplay-Ebene für die großen Kunstteile (Mehmets Ebene bleibt
   unangetastet, er ist heute offline); flache Wandteile brauchen keine, die Wand dahinter hält. Valcourts Sessel
   blockt nur, wenn er nicht drin sitzt.
5. **Valcourts Sitzpunkt** nach vorn, bis die Beine frei sind (Prüfbild).

## B. Klarheit (Code-Seite, Entscheidung René)

6. **Ziel in Schritten statt einer Zeile:** "Find a disguise - the stagehand smock hangs behind you" -> "Cross the
   wings to the stage" -> "Wait for the interval (2:30): Valcourt leaves box 7" -> "Get the score" -> "Out: the stage
   door or the conductor's desk". Jeder Schritt mit dem nächsten Fenster der Opernuhr.
7. **Luciennes Notizbuch (Tab):** ihre eigenen Notizen - wer wann wo ist (je Akt), die drei Cues und was sie bewirken,
   welche Kleidung wo passt, wer durchschaut. Pausiert das Spiel. Löst "was passiert wann" und "was muss ich tun".
8. **Durchschauer sichtbar:** ein kleines Zeichen über Brac/Gaspard, wenn ihre Kleidung von ihnen durchschaut wird
   (wie Hitmans weißer Punkt).
9. **Warten abkürzen:** in einem Versteck eine Taste halten -> die Opernuhr läuft 6x schneller ("sie wartet im
   Kostümständer"); und/oder Akt 1 kürzer. Balancing-Zeit ist Renés Hebel.

## C. Balancing (Renés Werte - PM-Vorschläge)

10. **Rennen in Sicht** `FillRun` 0,25 -> 0,6; **falsche Zone** `FillWrongZone` 0,34 -> 0,5 (Vorbeirennen scheitert,
    vorbeischleichen im Schatten geht).
11. **Hören** `HearWalk` 400 -> 200 cm (wie Hitman: Gehen ist leise, Rennen hört man - `HearRun` bleibt 10 m).
12. **Logenschließer:** Wende bei X 450 statt 200 - die Proszeniumstür und der Vorhang werden ein sicherer Einstieg.
13. **Schacht:** Variante a) nur noch Fluchtweg nach dem Raub (Loge 7 -> Bühne, Einbahn) - der Weg hinein bleibt der
    Gang; Variante b) beide Richtungen, aber am Ende der Luke erst ein Blick durchs Gitter (wie im Versteck), dann
    "E: climb out". PM-Empfehlung: a) - das macht den Gang zum Kern und die Flucht schlauer.
14. **Licht am Logengang-Eingang** heller (Mehmet; bis dahin eine Graubox-Lampe von uns).

## D. Videos (Mehmets GO 15:45)

15. **Musik:** Auftrag an den Music PM ist angelegt (`megajam/2026-11-14-musik-videos`, alle 5 Filme, Effektspur
    reinigen), wartet auf Renés Freigabe.
16. **Einbau:** Cold Open nach Begin, Enden bei `OnEnding`, Portfolio nach dem Raub, Vorhang beim Erwischtwerden -
    überspringbar; Film stumm, Ton aus der WAV des Music PM (bis dahin der Filmton leise).

## Reihenfolge und Zeit

| Wann | Was | Zeit |
|---|---|---|
| Sa bis 19:00 | A1-A5, C10-C12 (Werte nach Renés Ja), B6 Ziel-Schritte, Paket | ~3 h |
| Sa Abend / So früh | B7 Notizbuch, B9 Warten, C13 Schacht, B8 Zeichen, D16 Filme | ~4,5 h |
| So | Musik der Filme einbauen, Fable-Audit (D15), Fixes, Kandidat 20:00 | |

Der Freeze um 19:00 hält damit nicht für alles - B7/B9/C13/D16 sind Sonntag-Arbeit. **Entscheidung René.**
NPC-Bewegungen: Renés nächstes Feedback.
