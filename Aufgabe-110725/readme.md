# Aufgabe Heute Nachmittagsaufgabe

Da wir Kapitel 4 heute bewusst ausgelassen haben, besteht eure Aufgabe heute darin:
Lest Kapitel 4.1 und 4.2 vollständig durch.
Diese Kapitel behandeln die Themen:

Was ist ein Betriebssystem?
Verschiedene Linux-Distributionen
Grundlegendes Verständnis von Hardware (Mainboard, RAM, Speicher, Partitionen etc.)
Kapitel 4.3 und 4.4 behandeln andere Schwerpunkte und werden nächste Woche gemeinsam im Unterricht behandelt.

Wenn ihr mit dem Kapitel fertig seid, könnt ihr entweder mit der optionalen Aufgabe weitermachen oder die Zeit nutzen, um euch weiter im Linux Essentials PDF einzulesen.

Abgabe:

Schreibt eure Fragen auf oder schreibt als Kommentar, wenn alles klar ist.\***\*\_\*\***

## Antwort

Ich lerne gerade die Kapitel 4.1 und 4.2 des Linux Essentials PDF. Das Hauptthema betrifft das Dateisystem von Linux – wie es Festplatten verwaltet. Im Vergleich zum Dateisystem von Windows scheint Linux universeller zu sein. Allerdings stellt sich bei der häufigen Nutzung der Shell die Frage, wie man die Verwaltung für Benutzer intuitiver gestalten kann.

## Optionale Zusatzaufgabe

```bash

#!/bin/bash

# Überprüfen, ob ein Ordnerargument übergeben wurde
if [ $# -ne 1 ]; then
    echo "Benutzung: $0 <Pfad_zum_Ordner>"
    exit 1
fi

TARGET_DIR="$1"

# Überprüfen, ob der Ordner existiert
if [ ! -d "$TARGET_DIR" ]; then
    echo "Fehler: Ordner $TARGET_DIR existiert nicht."
    exit 1
fi

# Datei-Typen und Zielordner definieren
declare -A FOLDER_MAP=(
    ["jpg"]="Bilder"
    ["png"]="Bilder"
    ["gif"]="Bilder"
    ["pdf"]="Dokumente"
    ["zip"]="Archive"
    ["tar.gz"]="Archive"
    ["rar"]="Archive"
    ["mp4"]="Videos"
    ["mkv"]="Videos"
    ["mp3"]="Musik"
    ["wav"]="Musik"
)

# Dateien im Zielordner durchgehen
find "$TARGET_DIR" -maxdepth 1 -type f | while read file; do
    filename=$(basename "$file")
    extension="${filename##*.}"
    targetSubFolder="Sonstiges"

    # Sonderbehandlung für Endungen mit Punkt
    if [[ "$filename" == *".tar.gz" ]]; then
        extension="tar.gz"
    fi

    # Zielordner anhand Dateityp festlegen
    if [[ ${FOLDER_MAP[$extension]+_} ]]; then
        targetSubFolder="${FOLDER_MAP[$extension]}"
    fi

    # Zielordner erstellen, falls nicht vorhanden
    mkdir -p "$TARGET_DIR/$targetSubFolder"

    # Datei verschieben
    mv "$file" "$TARGET_DIR/$targetSubFolder/"
    echo "→ $filename wurde verschoben nach $targetSubFolder/"
done
```
