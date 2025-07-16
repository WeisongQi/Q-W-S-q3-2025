# Aufgabe Heute Nachmittagsaufgabe

## 1.Wiederholung & Verständnisfragen

Lies dir bitte die Inhalte aus den heutigen Kapiteln nochmal in Ruhe durch:
Kapitel 4.4 – Der Rechner im Netzwerk
Kapitel 5.1 – Sicherheitsgrundlagen & Benutzerverwaltung

> Abgabe: Die grundlegenden Konzepte wurden in früheren Kursen bereits behandelt, aber wie man sie unter Linux anwendet, muss noch geübt werden. Außerdem würde ich gerne erfahren, wie diese Kenntnisse in den Prüfungsfragen abgefragt werden. Ich hoffe, dass wir das in den kommenden Kursen noch genauer kennenlernen.

## 2. Praktische Übung: Benutzer erstellen & Sudo-Rechte testen

### Schritte

Benutzer anlegen
Zum neuen Benutzer wechseln
Versuche einen Befehl mit sudo auszuführen, z.B sudo apt update -> Sollte zu einer Fehlermeldung führen, warum ?

> Der neue Benutzer gehört standardmäßig nicht zur Gruppe `sudo`. Ohne Mitgliedschaft in dieser Gruppe hat er keine Berechtigung, `sudo` zu verwenden.

Wechsle zurück zum ursprünglichen Benutzer mit exit
Füge den neuen Benutzer zur sudo-Gruppe hinzu
Melde dich erneut als den neuen user an und überprüfe ob sudo apt update jetzt funktioniert. Warum funktioniert er diesmal ?

> Durch die Mitgliedschaft in der Gruppe `sudo` erhält der Benutzer die nötigen Berechtigungen, um mit sudo administrative Befehle auszuführen. Die Gruppe sudo ist in der Datei `/etc/sudoers` konfiguriert, die definiert, welche Benutzer oder Gruppen `sudo` nutzen dürfen.

![Schritte](/images/Screenshot%202025-07-16%20193348.png)

### Weitere Frage zu beantworten

Was ist der Unterschied zwischen root, Standardbenutzer und Systemaccount?

> ​root: Der "Superuser" mit der Benutzerkennung (UID) 0. Hat uneingeschränkte Zugriffsrechte auf das gesamte System. Wird selten direkt genutzt, um Sicherheitsrisiken zu minimieren.
>
> ​Standardbenutzer: Allgemeine Benutzer mit UID ≥ 1000 (bei Ubuntu/Debian). Haben eingeschränkte Rechte (z. B. nur Zugriff auf ihre eigenen Dateien) und werden von Endnutzern verwendet.
>
> ​Systemaccount: Spezielle Benutzer für die Ausführung von Diensten/Prozessen (z. B. apache, mysql). Haben UID zwischen 1–999 (bei Ubuntu) und keine interaktive Login-Möglichkeit. Ihre Rechte sind auf die Funktion des Dienstes beschränkt.

Was bedeutet es, wenn ein Befehl mit sudo ausgeführt wird?

> sudo (engl. "superuser do") ermöglicht es einem Benutzer, einen Befehl mit den Rechten eines anderen Benutzers (normalerweise root) auszuführen. Standardmäßig wird root verwendet.
>
> > Der Benutzer muss sein eigenes Passwort eingeben (nicht das von root), um seine Identität zu bestätigen.
> >
> > Die Berechtigung ist temporär: Standardmäßig gilt sie für 15 Minuten (konfigurierbar via /etc/sudoers).
> >
> > Sicherheitsvorteil: Vermeidet dauerhaftes Benutzen von root und reduziert das Risiko von versehentlichen Schäden.

Wo stehen die Informationen zu einem Benutzer im System?

> Benutzerinformationen werden in Textdateien im Verzeichnis /etc gespeichert:
>
> > ​`/etc/passwd`: Enthält grundlegende Benutzerdaten (Benutzername, UID, GID, Home-Verzeichnis, Shell). Beispielzeile: testuser:x:1001:1001:Test Benutzer:/home/testuser:/bin/bash (Felder: Benutzername : Passwort-Hash (x = verschlüsselt in /etc/shadow) : UID : GID : Kommentar : Home-Verzeichnis : Shell)
> >
> > ​`/etc/shadow`: Speichert verschlüsselte Passwörter, Passwort-Ablaufzeiten und Sicherheitseinstellungen. Nur root kann lesen.
> >
> > ​`/etc/group`: Enthält Gruppendaten (Gruppenname, GID, Mitglieder).
> >
> > ​`/etc/gshadow`: Speichert verschlüsselte Gruppeninformationen (ähnlich /etc/shadow).

Warum braucht ein neuer Benutzer erst zusätzliche Rechte, um sudo verwenden zu dürfen?

> Aus Sicherheitsgründen folgt Linux dem Prinzip der "geringsten Rechte" (Least Privilege Principle): Benutzer erhalten nur die Rechte, die sie zur Durchführung ihrer Aufgaben benötigen.
>
> > Standardmäßig haben neue Benutzer keine sudo-Berechtigungen, um versehentliche oder böswillige Änderungen am System zu verhindern.
> >
> > sudo-Rechte müssen explizit vergeben werden (z. B. durch Hinzufügen zur sudo-Gruppe), um sicherzustellen, dass nur vertrauenswürdige Benutzer administrative Aufgaben ausführen können.
