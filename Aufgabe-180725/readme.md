# Aufgabe Heute Nachmittagsaufgabe

## Aufgabe 1

Szenario:

Stell dir vor, in deinem Unternehmen beginnt heute ein Praktikant mit dem Benutzernamen praktikant1. Du bist dafür verantwortlich, ihn korrekt ins System aufzunehmen und ihm einen Arbeitsbereich bereitzustellen, in dem er mitarbeiten kann – jedoch ohne Zugriff auf sensible Daten.

Erstelle einen neuen Benutzer mit dem Namen praktikant1 und richte für ihn ein persönliches Home-Verzeichnis ein.
(Mögliche Befehle: adduser,useradd, passwd)

> sudo adduser praktikant1

Erstelle eine neue Gruppe, z. B. dokumente, und füge den neuen Benutzer dieser Gruppe hinzu.
(Mögliche Befehle: groupadd, usermod)

> sudo groupadd dokumente
>
> sudo usermod -aG dokumente praktikant1

Lege einen Ordner an, z. B. /daten/praktikum, der der neuen Gruppe gehört.
Der Ordner soll so eingerichtet sein, dass alle Dateien, die dort entstehen, automatisch dieselbe Gruppenzugehörigkeit bekommen.
(Mögliche Befehle: mkdir, chown, chmod mit SGID)

> sudo mkdir -p /daten/praktikum
>
> sudo chown :dokumente /daten/praktikum
>
> sudo chmod g+s /daten/praktikum
>
> sudo chmod 770 /daten/praktikum

Lege eine Datei im neuen Ordner an, die nur vom Administrator gelesen werden darf.
(Mögliche Befehle: touch, chmod)

> sudo touch /daten/praktikum/geheim.txt
>
> sudo chmod 600 /daten/praktikum/geheim.txt

Teste den Zugriff:
Wechsle zur Sicht des Praktikanten und prüfe, ob dieser Zugriff auf den Ordner hat – und ob er auf die geschützte Datei zugreifen kann.
(Mögliche Befehle: su, ls, cat)

> su - praktikant1
>
> ls -ld /daten/praktikum
>
> cat /daten/praktikum/geheim.txt

Erstelle als Praktikant eine eigene Datei in dem Ordner und beobachte, welche Rechte sie erhält.
(Mögliche Befehle: touch, ls -l)

> touch /daten/praktikum/meine_datei.txt
>
> ls -l /daten/praktikum/meine_datei.txt

Abgabe: Kurz beschreiben, was funktioniert hat und was nicht und ob es Unklarheiten gab.

## Aufgabe 2

Bitte nutze die verbleibende Zeit, um dich gezielt auf die Prüfung vorzubereiten. Lies dazu die Kapitel, bei denen du selbst noch Unsicherheiten hast. Versuche idealerweise auch die geführten Übungen in diesen Kapiteln selbstständig durchzugehen.

Abgabe: Gemäß der Gewichtung der einzelnen Kapitel sind Kapitel 2 und 3 am wichtigsten, gefolgt von Kapitel 4, 5 und 1. Ich plane, mich in der Reihenfolge 5-2-4-3-1 auf die Prüfung vorzubereiten und zu lernen.
