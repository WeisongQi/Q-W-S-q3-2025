# Aufgabe Heute

## 1. **ECS auf EC2 vs. Fargate**

**Unterschiede:**

- **Infrastruktur-Management:** ECS auf EC2 erfordert die manuelle Verwaltung von EC2-Instanzen (z. B. Bereitstellung, Skalierung, Patching), während Fargate vollständig serverlos ist und AWS die Infrastruktur automatisch bereitstellt und skaliert .
- **Kostenmodell:** ECS auf EC2 kostet für die EC2-Instanzen (auch in Leerlaufzeiten), während Fargate nur für tatsächlich genutzte Ressourcen (vCPU/Memory pro Sekunde) abgerechnet wird .
- **Flexibilität:** ECS auf EC2 ermöglicht die Anpassung von Hardware (z. B. GPU-Instanzen) und spezielle Netzwerkkonfigurationen. Fargate bietet weniger Kontrolle, ist aber einfacher zu bedienen .
- **Skalierung:** Fargate skaliert automatisch basierend auf der Containerlast, während ECS auf EC2 manuelle oder automatisierte Skalierung der EC2-Instanzen erfordert .

**Wann verwenden?**

- **ECS auf EC2:** Bei stabilen, langfristigen Workloads (z. B. 24/7-Dienste), die spezifische Hardware oder bestehende EC2-Optimierungen benötigen .
- **Fargate:** Bei unvorhersehbaren Spikes (z. B. Event-driven-Anwendungen), Serverless-Ansätzen oder schnellen Bereitstellungen ohne Infrastruktur-Overhead .

---

## 2. **Lambda + API Gateway als schlanke Backend-Architektur**

**Vorteile:**

- **Serverless:** Keine Server-Verwaltung, automatische Skalierung und Bezahlung nur für tatsächliche Anfragen .
- **Einfache Integration:** API Gateway verwaltet Routing, Authentifizierung (z. B. IAM, Cognito) und Lastverteilung, während Lambda die Geschäftslogik ausführt .
- **Kosteneffizienz:** Geringe Betriebskosten durch serverlose Architektur und Pay-per-Use-Modell .

**Typischer Use-Case:**

- **RESTful API für Microservices:** Beispiel: Ein E-Commerce-Backend, das über `/products` GET/POST-Anfragen verarbeitet, um Produktdaten aus einer Datenbank (z. B. DynamoDB) abzurufen oder zu aktualisieren .

---

## 3. **DynamoDB vs. RDS im Serverless-Kontext**

- **DynamoDB:**

  - **Passend für:** Dynamische, hochskalierbare Workloads (z. B. IoT-Daten, User-Session-Management) mit flexiblen Schemas und geringer Latenz. Ideal, wenn komplexe Abfragen nicht benötigt werden .

- **RDS:**

  - **Passend für:** Relationale Daten mit komplexen Transaktionen (z. B. ERP-Systeme, Finanzanwendungen) oder analytische Workloads, die ACID-Eigenschaften erfordern .

**Entscheidungshilfe:**

- **Serverless-Optimierung:** DynamoDB eignet sich besser für Event-driven-Architekturen, da es serverlos skaliert. RDS erfordert mehr management, ist aber für relationale Daten unverzichtbar .

---

## 4. **Batch vs. Lambda: Wofür ist Batch besser geeignet?**

**Batch** ist besser geeignet für **langlaufende, ressourcenintensive Batch-Jobs** (z. B. Massendatenverarbeitung, Image-Optimierung), die mehr als 15 Minuten dauern oder parallele Verarbeitung benötigen. Lambda hingegen eignet sich für kurze, ereignisgesteuerte Tasks (z. B. HTTP-Trigger) .
