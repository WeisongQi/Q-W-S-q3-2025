# Aufgabe Heute für den Nachmittag

## Aufgabe 1: Skript erstellen und demonstrieren

Schreibe ein einfaches Shell-Skript, das:

ein Verzeichnis als Argument bekommt
prüft, ob dieses Verzeichnis existiert
alle enthaltenen Dateien in ein Archiv packt (mit tar)
das Archiv mit gzip komprimiert
Das Archiv kann z. B. so heißen:
backup-2025-07-09.tar.gz

Das Skript soll von überall aus aufrufbar sein.

Tipp: Nutze dafür die PATH-Variable.

Test:

Erstelle ein Testverzeichnis mit ein paar Dateien, führe dein Skript aus, entpacke das Archiv, und prüfe, ob alle Dateien korrekt enthalten sind.

Abgabe:

![skript](/images/Screenshot%202025-07-10%20191642.png)

## Aufgabe 2: Kapitel 3.3 lesen und Fragen notieren

Lies dir bitte Kapitel 3.3 im Linux Essentials Skript vollständig durch.

Konzentriere dich auf die Teile zu:
Variablen
Argumenten
Bedingungen
Exit-Codes
Schleifen
Wenn Fragen entstehen, notiere sie bitte.

Abgabe:

### 1. Regeln für Linux-Befehlsparameter – **Verzeichnispfade**

Linux-Befehle verwenden konsistente Regeln für die Angabe von Verzeichnissen, basierend auf **Pfadangaben**. Diese umfassen absolute und relative Pfade sowie spezielle Symbole zur Vereinfachung der Eingabe.

#### 1.1 Grundlagen von Pfaden

- **Absoluter Pfad**: Ein Pfad, der vom Wurzelverzeichnis (`/`) aus beginnt und unabhängig vom aktuellen Arbeitsverzeichnis ist.
  Beispiele: `/home/user/dokumente`, `/tmp/logs`, `/mnt/usb`.
- **Relativer Pfad**: Ein Pfad, der relativ zum aktuellen Arbeitsverzeichnis (angezeigt durch `pwd`) steht.
  Beispiele: Wenn das aktuelle Verzeichnis `/home/user` ist, steht `docs` für `/home/user/docs`, und `../tmp` steht für `/home/tmp`.

#### 1.2 Spezielle Symbole zur Pfadvereinfachung

Linux bietet spezielle Symbole, um lange Pfade zu verkürzen:

| Symbol      | Bedeutung                                                                            | Beispiel                                                                                                                |
| ----------- | ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| `.`         | Aktuelles Verzeichnis                                                                | `ls ./unterverzeichnis` (Listet den Inhalt von `unterverzeichnis` im aktuellen Verzeichnis)                             |
| `..`        | Elterverzeichnis (das übergeordnete Verzeichnis)                                     | `cd ../elternverzeichnis` (Wechselt in das Elterverzeichnis des aktuellen Verzeichnisses)                               |
| `~`         | Home-Verzeichnis des aktuellen Benutzers (entspricht der Umgebungsvariablen `$HOME`) | `cp ~/backup/datei .` (Kopiert `datei` aus dem Home-Verzeichnis in das aktuelle Verzeichnis)                            |
| `~benutzer` | Home-Verzeichnis eines bestimmten Benutzers (erfordert Berechtigungen)               | `ls ~bob/dokumente` (Listet den Inhalt von `dokumente` im Home-Verzeichnis von `bob`)                                   |
| `-`         | Letztes besuchtes Verzeichnis (vor dem letzten `cd`-Befehl)                          | `cd -` (Wechselt schnell zurück zum vorherigen Verzeichnis)                                                             |
| `/`         | Wurzelverzeichnis                                                                    | `rm -rf /` (Achtung: Löscht alle Inhalte des Wurzelverzeichnisses – extrem gefährlich!)                                 |
| `*`         | Wildcard für beliebige Zeichen (einschließlich leer)                                 | `ls /home/*/dokument` (Listet alle `dokument`-Verzeichnisse/Dateien unter `/home` mit beliebigem Unterverzeichnisnamen) |
| `?`         | Wildcard für ein einzelnes beliebiges Zeichen                                        | `ls datei?.txt` (Passt `datei1.txt`, `dateiA.txt` usw.)                                                                 |

#### 1.3 Standardverhalten von Befehlen

Die meisten Linux-Befehle operieren **standardmäßig im aktuellen Arbeitsverzeichnis**, ohne dass ein Pfad explizit angegeben werden muss. Beispiele:

- `ls`: Listet den Inhalt des aktuellen Verzeichnisses auf (äquivalent zu `ls .`).
- `touch test.txt`: Erstellt `test.txt` im aktuellen Verzeichnis.
- `rm *.log`: Löscht alle `.log`-Dateien im aktuellen Verzeichnis.

#### 1.4 Eingabe mehrstufiger Unterverzeichnisse

Für Verzeichnisse, die **mehrstufige Unterverzeichnisse** des aktuellen Verzeichnisses sind, verwenden Sie `/` zur Trennung der Unterverzeichnisnamen:

- Beispiel: Das aktuelle Verzeichnis ist `/home/user`. Um auf `/home/user/projekt/src` zuzugreifen:
  - Absoluter Pfad: `cd /home/user/projekt/src` oder relativer Pfad: `cd projekt/src`.
  - Falls das Verzeichnis nicht existiert, verwenden Sie `mkdir -p projekt/src`, um es rekursiv zu erstellen (das `-p`-Flag füllt fehlende Elternverzeichnisse automatisch).

---

### 2. Regeln für Linux-Befehlsparameter – **Dateiparameter**

Dateiparameter (insbesondere mit Sonderzeichen) müssen durch Anführungszeichen oder Klammern geschützt werden, um eine korrekte Verarbeitung durch die Shell zu gewährleisten.

#### 2.1 Anführungszeichen: Unterschied zwischen einfachen und doppelten Anführungszeichen

Anführungszeichen dienen dazu, Sonderzeichen in Dateinamen (z. B. Leerzeichen, `$`, `*`, `?`) vor der Interpretation durch die Shell zu schützen. Die Unterschiede zwischen einfachen (`' '`) und doppelten (`" "`) Anführungszeichen sind:

| Anführungsart                  | Verhalten                                                                                                                                                             | Beispiel                                                                                                                             |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **Einfache Anführungszeichen** | Wörtliche Textdarstellung – keine Sonderzeichen werden interpretiert (einschließlich Variablen, Befehlsersetzung oder Escape-Sequenzen `\`).                          | `cat 'datei mit $var.txt'` (Liest direkt die Datei `datei mit $var.txt`).                                                            |
| **Doppelte Anführungszeichen** | Leerzeichen und andere Sonderzeichen werden wörtlich behandelt, aber Variablen (`$var`), Befehlsersetzung (`$(befehl)`), Escape-Sequenzen (`\`) werden interpretiert. | `echo "Heute ist $(date)"` (Gibt das aktuelle Datum aus); `cp "datei mit leerzeichen.txt" ziel` (Kopiert die Datei mit Leerzeichen). |

#### 2.2 Klammern: Typen und Anwendungen

Klammern werden zur Gruppierung, Subshell-Ausführung oder speziellen Erweiterungen verwendet. Häufige Typen:

| Klammernart                   | Verhalten                                                                                                                                         | Beispiel                                                                                                                                                                                                                    |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Runde Klammern `()`**       | 1. Führt Befehle in einer Subshell aus (ohne Auswirkungen auf die aktuelle Shell-Umgebung). 2. Gruppiert Befehle (zusammen mit `;` oder `&&`).    | `(cd /tmp && ls)` (Wechselt in `/tmp` innerhalb einer Subshell und listet den Inhalt auf – das aktuelle Verzeichnis bleibt unverändert); `{ befehl1; befehl2; }` (Ähnlich wie `()`, erfordert jedoch Leerzeichen nach `{`). |
| **Eckige Klammern `[]`**      | Testbefehl (äquivalent zu `test`) – prüft Dateieigenschaften oder Bedingungen ( gibt Exit-Status `0` (wahr) oder `1` (falsch) zurück).            | `[ -f "datei.txt" ]` (Prüft, ob `datei.txt` eine normale Datei ist); `[ "$a" -gt 10 ]` (Vergleicht numerisch, ob `$a` größer als 10 ist).                                                                                   |
| **Geschweifte Klammern `{}`** | 1. Generiert eine Sequenz von Zeichen (erfordert Leerzeichen zwischen den Elementen). 2. Codeblock (muss mit einem Zeilenumbruch oder `;` enden). | `cp datei_{1,2}.txt ziel` (Kopiert `datei_1.txt` und `datei_2.txt` nach `ziel`); `{ echo "a"; echo "b"; } > ausgabe.txt` (Schreibt zwei Zeilen in `ausgabe.txt`).                                                           |
| **Spitze Klammern `<>`**      | Eingabe-/Ausgabeumleitung: `<` liest eine Datei ein, `>` überschreibt eine Datei, `>>` hängt an einer Datei an.                                   | `sort < unsortiert.txt > sortiert.txt` (Sortiert den Inhalt von `unsortiert.txt` und schreibt ihn in `sortiert.txt`).                                                                                                       |

#### 2.3 Spezielle Szenarien

- **Dateinamen mit Leerzeichen oder Sonderzeichen**: Muss mit Anführungszeichen (am besten doppelten) umschlossen werden.
  Beispiel: `mv "meine dokument.txt" "backup/meine doc 2024.txt"` (Verschiebt die Datei mit Leerzeichen).
- **Dateinamen, die mit `-` beginnen**: Können fälschlicherweise als Befehlsoptionen interpretiert werden. Nutzen Sie `--`, um die Optionen zu beenden, oder geben Sie den absoluten Pfad an.
  Beispiel: `rm -- -datei.txt` (Löscht die Datei `datei.txt`, die mit `-` beginnt); `rm /pfad/zur/-datei.txt`.
- **Wildcards, die nicht expandiert werden sollen**: Schützen Sie den Pfad mit einfachen Anführungszeichen, um zu verhindern, dass `*` oder `?` von der Shell expandiert werden.
  Beispiel: `ls '*.log'` (Listet nur Dateien mit dem Namen `*.log` auf – nicht alle `.log`-Dateien).

---

### Zusammenfassung

1. **Verzeichnispfade**:

   - Nutzen Sie absolute Pfade (`/`-Start) oder relative Pfade (abhängig vom aktuellen Verzeichnis).
   - Spezielle Symbole wie `.`, `..`, `~` vereinfachen die Eingabe.
   - Mehrstufige Unterverzeichnisse verwenden `/` zur Trennung; `mkdir -p` erstellt fehlende Elternverzeichnisse.

2. **Dateiparameter**:
   - **Einfache Anführungszeichen `' '`**: Wörtliche Textdarstellung (keine Interpretation von Sonderzeichen).
   - **Doppelte Anführungszeichen `" "`**: Schützt Leerzeichen, interpretiert Variablen/Befehlsersetzung/Escapes.
   - **Klammern**: `()` (Subshell), `[]` (Test), `{}` (Sequenz/Codeblock), `<>` (Umleitung).
   - Besondere Dateinamen (Leerzeichen, `-`-Start) benötigen Anführungszeichen oder `--`.
