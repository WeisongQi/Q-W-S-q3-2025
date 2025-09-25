# Aufgabe Heute

## 1. **Wann ist ein Multi-Account-Ansatz (Organizations/OUs) besser als „alles in einem Konto“?**

Ein Multi-Account-Ansatz ist sinnvoll, wenn:

- **Trennung von Verantwortlichkeiten** erforderlich ist (z. B. separate Teams für Entwicklung, Produktion oder Compliance) .
- **Datenhoheit und Datenschutz** im Vordergrund stehen, z. B. bei internationalen Teams oder regulatorischen Anforderungen (GDPR, HIPAA) .
- **Kostenoptimierung** durch getrennte Abrechnung und Ressourcenkontrolle gewünscht ist .
- **Skalierbarkeit** und **Flexibilität** bei unterschiedlichen Projektanforderungen (z. B. unterschiedliche Lizenzmodelle oder Regionen) .

## 2. **Welche Rolle spielen SCPs und wo setzt du sie sinnvoll ein?**

**SCP (Service Control Policies)** sind zentrale Sicherheitsinstrumente in AWS:

- **Rollen**:
  - **Berechtigungsbeschränkung**: Verhindern Sie unerlaubte Aktionen (z. B. Blockieren von S3-Buckets in bestimmten Regionen) .
  - **Compliance-Einhaltung**: Erzwingen Sie Sicherheitsstandards (z. B. Verschlüsselung oder Zugriffsbeschränkungen) .
- **Einsatzszenarien**:
  - **Zentrale Richtlinienverwaltung**: Anwenden Sie Richtlinien global über alle Konten hinweg (z. B. Verbot von Root-Zugriff) .
  - **Projektspezifische Einschränkungen**: Begrenzen Sie Entwicklerzugriffe auf Produktionssysteme .

## 3. **Wofür nutzt du Pricing Calculator im Alltag?**

Der **AWS Pricing Calculator** hilft bei:

- **Kostenschätzung**: Berechnen Sie monatliche Ausgaben für EC2-Instanzen, S3-Speicher oder Lambda-Aufrufe .
- **Szenarien-Optimierung**: Vergleichen Sie verschiedene Konfigurationen (z. B. Reserved Instances vs. On-Demand) .
- **Budgetplanung**: Exportieren Sie detaillierte CSV-Berichte für interne Abstimmungen .
- **Regionale Preisanalysen**: Identifizieren Sie günstigste Regionen für Speicher oder Rechenleistung .
