# Aufgabe Heute

## **Teil 3: Dateien suchen und finden**

### Aufgabe 9: Die verlorenen Projektdateien 📁

Alex hat erfahren, dass sein Vorgänger wichtige Projektdateien irgendwo im System versteckt hat.

**Ihre Aufgaben:**

1. Erstellen Sie zunächst ein Testszenario:
   - Erstellen Sie Verzeichnisse: `~/projekte/app1`, `~/projekte/app2`, `~/backup`
     > > mkdir -p ~/projekte/app{1..2} ~/backup
   - Erstellen Sie Dateien: `projekt_alpha.txt`, `projekt_beta.doc`, `backup_projekt.txt`
     > > touch projekt_alpha.txt projekt_beta.txt backup_projekt.txt
2. Nutzen Sie `locate` um alle Dateien zu finden, die "projekt" enthalten
   > > locate "projekt"
3. Nutzen Sie `find` um alle `.txt` Dateien in Ihrem Home-Verzeichnis zu finden
   > > find ~ -type f -name "\*.txt"
4. Nutzen Sie `find` um alle Dateien zu finden, die in den letzten 10 Minuten geändert wurden
   > > find . -mmin -10

**Befehle zu verwenden:** `mkdir`, `touch`, `locate`, `find`

---

### Aufgabe 10: Das Backup-Dilemma 💾

Alex muss herausfinden, welche Backup-Dateien älter als eine Woche sind und gelöscht werden können.

**Ihre Aufgaben:**

1. Erstellen Sie mehrere Testdateien mit verschiedenen Datums-Stempeln:

   - `backup_alt.tar` (versuchen Sie, das Datum zu ändern)
   - `backup_neu.tar`
   - `backup_config.conf`

     > > touch backup_alt.tar backup_neu.tar backup_config.conf
     > > echo date > backup_alt.tar
     > > echo date > backup_new.tar
     > > echo date > backup_config.conf
     > > touch -d "2 days ago" backup_alt.tar
     > > touch -t "202411241200.44" backup_config.conf

2. Nutzen Sie `find` um:
   - Alle `.tar` Dateien zu finden
     > > find . -type f -name "\*.tar"
   - Alle Dateien zu finden, die größer als 0 Bytes sind
     > > find ~ -size 0c
   - Alle Dateien zu finden, die das Wort "backup" im Namen haben
     > > find ~ -name "backup\*"
3. Kombinieren Sie `find` mit `ls -l` um Details der gefundenen Dateien anzuzeigen

   > > find ~ -name "backup\*" -exec ls -l {} \;
   > > find ~ -name "backup\*" -type f -size +0c -exec ls -l {} \;

**Befehle zu verwenden:** `touch`, `find`, `ls`
