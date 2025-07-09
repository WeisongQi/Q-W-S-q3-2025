# Aufgabe Heute Nachmittagsaufgabe

## Aufgabe 1

Stell dir vor, du arbeitest im Support-Team und bekommst regelmäßig Logdateien von Kunden geschickt. Du willst die Daten sauber vorbereiten und sichern.

Deine Aufgabe:

Erstelle ein Verzeichnis support_logs

    Lege in diesem Verzeichnis drei Textdateien an:
    log1.txt, log2.txt, log3.txt
    Jede Datei soll ein paar Zeilen enthalten – ein Mix aus:
    „OK“
    „Fehler: Verbindung verloren“
    „Fehler: Zeitüberschreitung“
    „Hinweis: Prozess beendet“
    Finde alle Zeilen mit „Fehler“ und speichere sie in eine neue Datei nur_fehler.txt.
    Packe die Datei nur_fehler.txt in ein tar.gz-Archiv namens fehlerpaket.tar.gz.

Teste anschließend:

    Entpacken des Archivs
    Anzeigen des Inhalts mit cat, less oder more

Bonus:

    Zähle mit wc die Zeilenanzahl in nur_fehler.txt
    Verwende cut, um z. B. nur das Wort nach dem Doppelpunkt (:) anzuzeigen

### Abgabe 1

> > mkdir support_logs
> >
> > cd support_logs
> >
> > touch log{1..3}.txt
> >
> > echo "OK" > log1.txt
> >
> > echo "Fehler: Verbindung verloren" > log2.txt
> >
> > echo "Fehler: Zeitüberschreitung" > log3.txt
> >
> > echo "Hinweis: Prozess beendet" >> log3.txt
> >
> > grep "Fehler" log\*.txt > nur_fehler.txt
> >
> > tar -czf fehlerpaket.tar.gz nur_fehler.txt
>
> Test
>
> > tar -xzf fehlerpaket.tar.gz
> >
> > cat nur_fehler.txt
> >
> > less nur_fehler.txt
> >
> > more nur_fehler.txt
>
> Bonus
>
> > wc -l nur_fehler.txt
> >
> > cut -d':' -f3 nur_fehler.txt

## Aufgabe 2

Wiederholung & Durcharbeitung von Kapitel 3.1 und 3.2

Bitte lest euch heute Kapitel 3.1 („Dateien archivieren“) und Kapitel 3.2 („Daten in Dateien suchen und extrahieren“) aus dem Linux Essentials Lernmaterial noch einmal gründlich durch.

Achtung: Der Abschnitt zu Regulären Ausdrücken wurde im Unterricht noch nicht richtig behandelt

Wichtiger Hinweis:

    Bitte nicht nur lesen, sondern die Inhalte im Terminal ausprobieren.

Das bedeutet:

    Nutzt die Beispiele im Linux Essentials Skript direkt im Terminal.
    Überlegt euch auch eigene Varianten
    Ziel: Die Befehle selbst ausführen, verstehen, und beobachten, was passiert.

### Abgabe 2

> Mit **tar** und **gzip** kann ich gezielt Dateien archivieren und komprimieren.
>
> **grep** ist sehr nützlich, um gezielt Zeilen mit „Fehler“ aus mehreren Dateien zu extrahieren.
>
> Das Packen (**tar -czf**) und anschließende Entpacken (**tar -xzf**) der Datei „nur_fehler.txt“ hat einwandfrei funktioniert.
>
> Mit **wc -l** konnte ich zählen, wie viele Fehlerzeilen vorhanden sind.
>
> Mit **cut -d':' -f3** habe ich erfolgreich nur die eigentliche Fehlerbeschreibung extrahiert.
