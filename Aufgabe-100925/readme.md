# Aufgabe Heute

## 1. Unterschied zwischen IAM-User und IAM-Rolle

Ein **IAM-User** ist eine dauerhafte Identität in AWS, die über Benutzername und Passwort oder Zugriffsschlüssel authentifiziert wird. Er eignet sich für langfristigen Zugriff auf Ressourcen, z. B. für Entwickler oder Anwendungen, die kontinuierlich mit AWS interagieren . Eine **IAM-Rolle** hingegen bietet temporäre Anmeldeinformationen (via AWS STS) und wird genutzt, um kurzfristigen Zugriff oder Zugriff über verschiedene Konten/Services (z. B. EC2-Instanzen, externe Benutzer) zu ermöglichen. Rollen sind nicht an eine bestimmte Person gebunden und reduzieren Risiken durch dauerhafte Credentials .

---

## 2. Warum ist das Least Privilege Prinzip wichtig?

Das **Prinzip der geringsten Berechtigung** stellt sicher, dass Benutzer und Anwendungen nur die minimal notwendigen Rechte erhalten, um ihre Aufgaben auszuführen. Dies minimiert das Risiko unbefugter Zugriffe und begrenzt Schäden bei kompromittierten Zugängen .

---

## 3. Passwort-Policy: Definition und Nutzung

Eine **Passwort-Policy** definiert Regeln für die Erstellung und Verwaltung von Passwörtern (z. B. Mindestlänge, Komplexität, Ablaufzeit). Sie schützt Konten vor unbefugtem Zugriff durch schwache Passwörter und fördert Sicherheitsbewusstsein in Organisationen .

---

## 4. Zugriff über Management Console, CLI und SDK

- **Management Console**: Webbasierte Oberfläche für manuelle Verwaltung von AWS-Ressourcen (z. B. EC2-Instanzen starten) .
- **CLI**: Befehlszeilentool für Skript-Automatisierung (z. B. Dateien per `aws s3 cp` in S3 hochladen) .
- **SDK**: Programmierschnittstellen (z. B. Python/Boto3) zur Integration von AWS-Diensten in Anwendungen .

---

## 5. Zwei Best Practices für IAM

1. **Multi-Faktor-Authentifizierung (MFA)**: Erzwingen Sie MFA für alle IAM-Benutzer, um zusätzliche Sicherheitsebenen gegen Passwortkompromittierung zu gewährleisten .
2. **Regelmäßige Zugriffsüberprüfung**: Entfernen Sie nicht mehr benötigte Berechtigungen und überprüfen Sie policies periodisch, um überflüssige Zugriffe zu vermeiden .
