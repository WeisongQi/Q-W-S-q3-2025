# Aufgabe Heute

## Die Geschichte von Alex, dem neuen Linux-Administrator

Alex hat gerade seinen ersten Job als Junior-Systemadministrator bei der Firma "TechnoWunderland GmbH" bekommen. Das Unternehmen entwickelt innovative Apps für Smartphones und benötigt einen gut organisierten Linux-Server. Alex muss verschiedene Aufgaben bewältigen, um das System zu verwalten und dabei die Grundlagen der Befehlszeile meistern.

---

## **Teil 1: Grundlagen der Shell und Befehlszeile**

### Aufgabe 1: Alex' erster Arbeitstag 🏢

Alex loggt sich zum ersten Mal in das System ein und möchte sich orientieren.

**Ihre Aufgaben:**

1. Zeigen Sie den aktuellen Benutzernamen an
   > > whoami
2. Zeigen Sie den Hostnamen des Systems an
   > > Hostmame
3. Zeigen Sie das aktuelle Arbeitsverzeichnis an
   > > pwd
4. Überprüfen Sie, welche Shell Sie verwenden
   > > echo $SHELL

**Befehle zu verwenden:** `echo`, `hostname`, `pwd`, `echo $SHELL`

---

### Aufgabe 2: Die mysteriöse Nachricht 📝

Alex findet eine Datei mit einer verschlüsselten Nachricht von seinem Vorgänger. Er muss verschiedene Befehle ausprobieren.

**Ihre Aufgaben:**

1. Erstellen Sie eine Datei namens `geheimnis.txt` mit folgendem Inhalt: "Willkommen bei TechnoWunderland! Der Tresor-Code ist: echo 'Hallo Welt'"
   > > echo "Willkommen bei TechnoWunderland! Der Tresor-Code ist: echo 'Hallo Welt'" > geheimnis.txt
2. Zeigen Sie den Inhalt der Datei an
   > > cat geheimnis.txt
3. Führen Sie den im Text versteckten Befehl aus
   > > echo 'Hallo Welt'
4. Überprüfen Sie den Typ des Befehls `echo`
   > > type echo

**Befehle zu verwenden:** `touch`, `echo`, `cat`, `type`

---

### Aufgabe 3: Quoting-Chaos 🤯

Alex muss lernen, wie er mit Leerzeichen und Sonderzeichen in Dateinamen umgeht.

**Ihre Aufgaben:**

1. Erstellen Sie eine Datei namens `Mein Projekt.txt` (mit Leerzeichen!)
   > > touch "Mein Projekt.txt"
2. Erstellen Sie eine Datei mit dem Namen `$Budget_2024.txt`
   > > touch '$Budget_2024.txt'
3. Erstellen Sie eine Datei mit dem Namen `'Anführungszeichen'.txt`
   > > touch "'Anführungszeichen'.txt"
4. Listen Sie alle Dateien auf und beobachten Sie die Ausgabe
   > > ls -a -l

**Befehle zu verwenden:** `touch`, `ls`, verschiedene Quoting-Techniken

---

### Aufgabe 4: Variable Verwirrung 🔄

Alex muss verstehen, wie Variablen funktionieren, um Skripte für die Firma zu schreiben.

**Ihre Aufgaben:**

1. Erstellen Sie eine lokale Variable `FIRMA` mit dem Wert "TechnoWunderland"
   > > FIRMA="TechnoWunderland"
2. Erstellen Sie eine lokale Variable `ABTEILUNG` mit dem Wert "IT-Support"
   > > ABTEILUNG="IT-Support"
3. Geben Sie beide Variablen aus
   > > echo $FIRMA
   > > echo $ABTEILUNG
4. Exportieren Sie `FIRMA` als Umgebungsvariable
   > > export FIRMA="TechnoWundland"
5. Starten Sie eine neue Shell mit `bash` und prüfen Sie, welche Variable noch verfügbar ist
   > > bash
   > > echo $FIRMA # sichtbar
   > > echo $ABTEILUNG # fehlt
6. Verlassen Sie die neue Shell mit `exit`
   > > exit

**Befehle zu verwenden:** `export`, `echo`, `bash`, `exit`

---

### Aufgabe 5: PATH-Probleme 🛤️

Alex stellt fest, dass ein wichtiges Programm nicht gefunden wird und muss die PATH-Variable untersuchen.

**Ihre Aufgaben:**

1. Zeigen Sie die aktuelle PATH-Variable an
   > > echo $PATH
2. Erstellen Sie ein Verzeichnis `~/meine_tools`
   > > mkdir -p +/meine_tools
3. Fügen Sie dieses Verzeichnis zur PATH-Variable hinzu
   > > export PATH=$PATH:+/meine_tools
4. Erstellen Sie in `~/meine_tools` eine ausführbare Datei namens `hallo` (erstellen Sie nur die Datei, Ausführungsrechte kommen später)
   > > touch ~/meine_tools/hallo
   > > echo -e '#!/bin/bash\necho "Hallo Welt!"' > ~/meine_tools/hallo
   > > chmod +x ~/meine_tools/hallo
5. Überprüfen Sie mit `which`, ob das System die Datei finden würde

> > which hallo

**Befehle zu verwenden:** `echo`, `mkdir`, `touch`, `which`

## **Teil 2: Hilfe suchen und Dokumentation**

### Aufgabe 6: Handbuch-Hunting 📚

Alex muss lernen, wie er selbstständig Hilfe finden kann, wenn er nicht weiter weiß.

**Ihre Aufgaben:**

1. Öffnen Sie die Manpage von `ls` und finden Sie heraus:
   > > man ls
   - Wie Sie versteckte Dateien anzeigen
     > > ls -a
   - Wie Sie Dateien nach Änderungszeit sortieren
     > > ls -t
   - Wie Sie eine detaillierte Auflistung erhalten
     > > ls -l
2. Verwenden Sie `ls --help` und vergleichen Sie die Informationen
   > > ls --help
3. Finden Sie heraus, zu welcher Kategorie die Manpage von `ls` gehört
   > > man 1 ls
4. Öffnen Sie die Manpage von `passwd` (Kategorie 5) - die Konfigurationsdatei
   > > man 5 passwd

**Befehle zu verwenden:** `man`, `ls` mit verschiedenen Optionen

---

### Aufgabe 7: Info-Expedition 🔍

Alex entdeckt, dass manche Programme auch Info-Seiten haben.

**Ihre Aufgaben:**

1. Öffnen Sie die Info-Seite von `ls`
   > > info ls
2. Navigieren Sie durch das Menü und finden Sie Informationen über:
   > > ↑/↓, j/k
   - "What information is listed"
     > > /what
   - "Sorting the output"
     > > /sorting
3. Suchen Sie nach dem Wort "time" in der Info-Seite
   > > u
4. Kehren Sie zum Hauptmenü zurück und verlassen Sie Info
   > > q

**Befehle zu verwenden:** `info`, Navigation mit Pfeiltasten, `/`, `q`

---

### Aufgabe 8: Dokumentations-Detektiv 🕵️

Alex soll ein Problem mit einem unbekannten Programm lösen und muss alle verfügbaren Hilfequellen nutzen.

**Ihre Aufgaben:**

1. Schauen Sie sich das Verzeichnis `/usr/share/doc/` an
   > > ls /usr/share/doc/
2. Finden Sie die Dokumentation für `bash`
   > > ls /usr/share/doc/bash-\*
3. Schauen Sie sich die README-Datei (falls vorhanden) an
   > > cat /usr/share/doc/bash\*/README
4. Nutzen Sie `locate` um alle README-Dateien im System zu finden (erste 5 Treffer)
   > > locate README | head -n 5
5. Aktualisieren Sie die locate-Datenbank (falls Sie root-Rechte haben)
   > > sudo updatedb

**Befehle zu verwenden:** `ls`, `cat`, `less`, `locate`, `sudo updatedb`
