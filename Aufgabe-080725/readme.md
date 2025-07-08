# Aufgabe Heute

## **Teil 4: Komplexe Szenarien**

### Aufgabe 11: Das große Aufräumen 🧹

Alex muss das chaotische Home-Verzeichnis seines Vorgängers aufräumen.

**Ihre Aufgaben:**

     1. Erstellen Sie folgende Verzeichnisstruktur:

    ```

    ~/alex_workspace/
    ├── projekte/
    │ ├── mobile_apps/
    │ │ ├── ios_app.swift
    │ │ └── android_app.java
    │ ├── web_apps/
    │ │ ├── frontend.html
    │ │ └── backend.php
    ├── dokumentation/
    │ ├── benutzer_handbuch.pdf
    │ └── tech_specs.md
    └── scripts/
    ├── backup_script.sh
    └── deploy_script.py

    ```


    > > mkdir alex_workspace/
    > > cd alex_workspace
    > > mkdir -p projekte/mobile_apps/ projekte/web_apps/ dokumentation/ scripts/
    > > touch backup_script.sh deploy_script.py
    > > touch ./dokumentation/benutzer_handbuch.pdf ./dokumentation/tech_specs.md
    > > touch ./web_apps/frontend.html ./web_apps/backend.php
    > > touch ./mobile_apps/ios_app.swift ./mobile_apps/android_app.java

    2.  Nutzen Sie verschiedene Befehle um:
    - Alle `.sh` Dateien zu finden
      > > sudo find / -name "\*.sh"
    - Alle Dateien zu finden, die "app" im Namen haben
      > > sudo find / -name "app"
    - Die Verzeichnisstruktur anzuzeigen
      > > tree or ls -R

**Befehle zu verwenden:** `mkdir -p`, `touch`, `find`, `tree` (falls verfügbar) oder `ls -R`

---

### Aufgabe 12: Umgebungsvariablen für das Team 👥

Alex muss Umgebungsvariablen für das Entwicklungsteam konfigurieren.

**Ihre Aufgaben:**

1. Erstellen Sie folgende Umgebungsvariablen:
   - `PROJEKT_NAME="TechnoWunderland-App"`
   - `ENTWICKLER="Alex"`
   - `VERSION="1.0.0"`
   - `DEBUG_MODUS="true"`
     > > export PROJEKT_NAME="TechnoWunderland-App"
     > >
     > > export ENTWICKLER="Alex"
     > >
     > > export VERSION="1.0.0"
     > >
     > > export DEBUG_MODUS="true"
2. Erstellen Sie eine Variable `PROJEKT_PFAD`, die den Pfad zu Ihrem alex_workspace enthält
   > > export PROJEKT_PFAD="$HOME/alex_workspace"
3. Kombinieren Sie Variablen: Erstellen Sie `VOLLSTÄNDIGER_TITEL` aus `$PROJEKT_NAME v$VERSION`
   > > export VOLLSTÄNDIGER_TITEL="$PROJEKT_NAME v$VERSION"
4. Zeigen Sie alle Umgebungsvariablen an, die mit "PROJEKT" beginnen
   > > env | grep ^PROJEKT
5. Nutzen Sie eine Variable in einem Befehl: `echo "Arbeite an $PROJEKT_NAME"`
   > > echo "Arbeite an $PROJEKT_NAME"

**Befehle zu verwenden:** `export`, `echo`, `env`

---

### Aufgabe 13: Debugging mit Hilfe-Tools 🐛

Alex muss ein Problem lösen und benötigt Informationen über verschiedene Befehle.

**Ihre Aufgaben:**

1. Ein Kollege hat gesagt: "Nutze den Befehl `rsync` für Backups". Finden Sie heraus:
   - Was macht `rsync`? (Manpage)
     > > man rsync
   - Welche wichtigsten Optionen gibt es?
     > > -a: archive mode
     > >
     > > -v: increase verbosity
     > >
     > > --progress: show progress during transferq
     > >
     > > --delete: delete extraneous files from dest dirs
   - Gibt es Beispiele in der Dokumentation?
     > > rsync -av --progress /home/alex/data/ /mnt/backup/data/
2. Finden Sie heraus, was der Befehl `grep` macht und wie man ihn verwendet
   > > man grep
   > >
   > > grep is print lines that match patterns
   > >
   > > grep "Alex" benutzer_handbuch.pdf
3. Suchen Sie nach allen Manpages, die das Wort "backup" enthalten
   > > man -k backup
4. Nutzen Sie `apropos` um Befehle zu finden, die mit "copy" zu tun haben
   > > apropos copy

**Befehle zu verwenden:** `man`, `apropos`, `grep` (in Manpages)

---

### Aufgabe 14: Das Escape-Zeichen-Rätsel 🎭

Alex muss lernen, wie er Sonderzeichen richtig verwendet.

**Ihre Aufgaben:**

1. Erstellen Sie eine Datei mit dem Namen `$pecial_File!.txt`
   > > touch \$pecial_File\!.txt
2. Erstellen Sie eine Variable `NACHRICHT` mit dem Inhalt: `Er sagte: "Hallo" und grinste.`
   > > export NACHRICHT='Er sagte: "Hallo" und grinste.'
3. Geben Sie folgende Texte exakt aus:
   - `Der Preis beträgt $100`
     > > echo 'Der Preis beträgt $100'
   - `Verwende "Anführungszeichen" richtig`
     > > echo 'Verwende "Anführungszeichen" richtig'
   - `Das Verzeichnis ist: /home/$USER`
     > > echo "Das Verzeichnis ist: /home/$USER"
4. Erstellen Sie eine Datei deren Name ein Leerzeichen UND ein Dollarzeichen enthält
   > > touch "Budget \$2025 Report.txt"

**Befehle zu verwenden:** `touch`, `echo`, verschiedene Quoting-Techniken

---

### Aufgabe 15: Das finale Projekt 🎯

Alex muss alles zusammenfügen und ein komplettes Arbeitsverzeichnis für ein neues Projekt erstellen.

**Ihre Aufgaben:**

1. Erstellen Sie Umgebungsvariablen für ein neues Projekt:

   - `NEUES_PROJEKT="MegaApp"`
   - `TEAM_LEAD="Alex"`
   - `DEADLINE="2024-12-31"`
     > > export NEUES_PROJEKT="MegaApp"
     > >
     > > export TEAM_LEAD="Alex"
     > >
     > > export DEADLINE="2024-12-31"

2. Erstellen Sie eine Verzeichnisstruktur unter `~/projekte/$NEUES_PROJEKT/`:

   - src/ (für Quellcode)
   - docs/ (für Dokumentation)
   - tests/ (für Tests)
   - config/ (für Konfigurationsdateien)
     > > mkdir -p ~/projekte/$NEUES_PROJEKT/{src,docs,tests,config}

3. Erstellen Sie in jedem Verzeichnis eine README.md Datei mit einer Beschreibung

   > > echo "# Quellcode für $NEUES_PROJEKT" > ~/projekte/$NEUES_PROJEKT/src/README.md
   > >
   > > echo "# Dokumentation für $NEUES_PROJEKT" > ~/projekte/$NEUES_PROJEKT/docs/README.md
   > >
   > > echo "# Testfälle für $NEUES_PROJEKT" > ~/projekte/$NEUES_PROJEKT/tests/README.md
   > >
   > > echo "# Konfigurationsdateien für $NEUES_PROJEKT" > ~/projekte/$NEUES_PROJEKT/config/README.md

4. Nutzen Sie `find` um:

   - Alle README.md Dateien zu finden
     > > find ~/projekte/$NEUES_PROJEKT -name README.md
   - Alle leeren Verzeichnisse zu finden
     > > find ~/projekte/$NEUES_PROJEKT -type d -empty
   - Eine Übersicht aller erstellten Dateien zu bekommen
     > > find ~/projekte/$NEUES_PROJEKT

5. Dokumentieren Sie Ihr Projekt:

   - Nutzen Sie `man` um herauszufinden, wie Sie mit `wc` Zeilen zählen können
     > > man wc
   - Zählen Sie die Anzahl der README-Dateien in Ihrem Projekt
     > > find ~/projekte/$NEUES_PROJEKT -name README.md | wc -l
   - Erstellen Sie eine Variable `PROJEKT_STATUS` mit einer Zusammenfassung
     > > export PROJEKT_STATUS="Projekt $NEUES_PROJEKT unter Leitung von $TEAM_LEAD. Deadline: $DEADLINE. Struktur und Dokumentation initialisiert."
     > >
     > > echo "$PROJEKT_STATUS"

**Befehle zu verwenden:** Alle bisher gelernten Befehle kombiniert

---

## **Zusatzaufgaben für Fortgeschrittene** 🚀

### Aufgabe 16: Command History Detective

Alex muss herausfinden, welche Befehle er heute verwendet hat.

**Ihre Aufgaben:**

1. Nutzen Sie `history` um Ihre letzten Befehle anzuzeigen
   > > history
2. Suchen Sie in der History nach allen `find` Befehlen
   > > history | grep find
3. Wiederholen Sie einen Befehl aus der History mit `!nummer`
   > > !999
4. Löschen Sie die History und bestätigen Sie es
   > > history -c
   > >
   > > history

**Befehle zu verwenden:** `history`, `!`, `history -c`

### Aufgabe 17: Variable Expansion Challenge

Alex muss verstehen, wie Variable Expansion funktioniert.

**Ihre Aufgaben:**

1. Erstellen Sie `BASENAME="projekt"` und `NUMMER="42"`

   > > export BASENAME="projekt"
   > >
   > > export NUMMER="42"

2. Nutzen Sie diese Variablen um eine Datei namens `projekt_42.txt` zu erstellen
   > > touch "${BASENAME}_${NUMMER}.txt"
3. Erweitern Sie PATH um `.:$HOME/bin:/opt/tools`
   > > export PATH=".:$HOME/bin:/opt/tools:$PATH"
4. Erstellen Sie eine Variable `HEUTE` mit dem aktuellen Datum (nutzen Sie `date`)
   > > export HEUTE=$(date "+%Y-%m-%d")
   > >
   > > echo $HEUTE

**Befehle zu verwenden:** `export`, `echo`, `date`, `touch`
