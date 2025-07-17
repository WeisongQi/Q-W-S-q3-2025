# Aufgabe Heute Nachmittagsaufgabe

## 1. Kapitel 5 fertig lesen

Lies Kapitel 5 inklusive Kapitel 5.4 durch und probier auch einiges im Terminal aus um das Verständnis zu festigen
Überlege dir dabei Fragen oder notiere Unklarheiten.

> Abgabe: Alles ist verständlich.

## 2. Beantworte folgende Fragen

Was ist der Vorteil von useradd im Vergleich zu adduser?

> `adduser` ist in den meisten Linux-Distributionen ein ​benutzerfreundliches Wrapper-Skript​ für den unterliegenden Befehl useradd. Der Hauptunterschied liegt in der Benutzerführung:
>
> > `adduser` fragt interaktiv nach Einstellungen (z. B. Home-Verzeichnis, Shell, Passwortrichtlinien) und automatisiert Standardkonfigurationen (z. B. Erstellung eines Home-Verzeichnisses).
> >
> > `useradd` ist ein ​low-level Befehl​ ohne Interaktion – er erfordert explizite Angabe aller Parameter (z. B. -m für Home-Verzeichnis, -s für Shell). Er bietet mehr Flexibilität (z. B. für Skripting oder spezielle Konfigurationen), ist aber weniger benutzerfreundlich.

Was macht die Option -G bei useradd?

> Die Option `-G (oder --groups)` in useradd dient dazu, ​Zusatzgruppen (Supplementary Groups)​​ für den neuen Benutzer anzugeben.
>
> > Jeder Benutzer hat eine ​Hauptgruppe​ (primary group, angegeben mit `-g` oder automatisch erstellt) und beliebig viele ​Zusatzgruppen​ (Zugriffsrechte für zusätzliche Gruppen).
> >
> > `-G` fügt den Benutzer zu diesen vorgegebenen Gruppen hinzu (die Gruppen müssen bereits existieren!).

Was bewirkt chmod 777 datei.txt?

> `chmod 777` setzt die ​Dateiberechtigungen​ von datei.txt so, dass:
>
> > Der ​Besitzer​ (User) Lese-, Schreib- und Ausführungsrechte erhält (7 = 4+2+1).
> >
> > Die ​Gruppe​ (Group), zu der der Besitzer gehört, ebenfalls Lese-, Schreib- und Ausführungsrechte erhält.
> >
> > ​Alle anderen Benutzer​ (Others) ebenfalls Lese-, Schreib- und Ausführungsrechte erhalten.

Wozu dient der Befehl chown benutzer:gruppe datei?

> `chown` (change owner) dient dazu, den ​Besitzer​ und/oder die ​Gruppe​ einer Datei oder eines Verzeichnisses zu ändern.
>
> > Syntax: `chown [Optionen] Benutzer[:Gruppe] Datei`
> >
> > Benutzer: Neuer Besitzer der Datei.
> >
> > `:Gruppe` (optional): Neue Gruppe der Datei (falls weggelassen, bleibt die Gruppe unverändert, es sei denn, nur : ohne Gruppe wird angegeben, z. B. `chown :neue_gruppe datei`).

Was ist der Zweck des Sticky Bits in /tmp?

> Der `​Sticky Bit`​ (auch "Sticky-Schalter" genannt) ist ein spezielles Berechtigungsbit, das für ​Verzeichnisse​ gilt. In /tmp hat er folgende Funktion:
>
> > Ein Verzeichnis mit `Sticky Bit` (gesetzt via chmod +t /tmp oder chmod 1777 /tmp) erlaubt es Benutzern, Dateien darin zu erstellen, zu lesen oder zu schreiben – `​aber sie können nur ihre eigenen Dateien löschen oder umbenennen.`
> >
> > Dies schützt vor versehentlichem Löschen von Dateien anderer Benutzer, selbst wenn sie Schreibrechte auf das Verzeichnis haben.
