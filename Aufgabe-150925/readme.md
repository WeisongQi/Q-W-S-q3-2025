# Aufgabe Heute

## 1. **OLTP vs. OLAP: Wann passt RDS/Aurora (Transaktionen) und wann Redshift (Analysen)?**

- **RDS/Aurora (OLTP):**

  - **Einsatz:** OLTP-Systeme (Online Transaction Processing) für **Echtzeittransaktionen** wie Bestellungen, Benutzerkonten oder Bestandsmanagement.
  - **Vorteile:** Hohe Schreib-/Lesegeschwindigkeit für Einzeloperationen, ACID-Konformität, Skalierung für parallele Transaktionen .
  - **Beispiel:** Ein E-Commerce-System, das Bestellungen in Echtzeit verarbeitet.

- **Redshift (OLAP):**

  - **Einsatz:** OLAP-Systeme (Online Analytical Processing) für **komplexe Analysen** großer Datenmengen (z. B. Verkaufsberichte, Kundenverhalten).
  - **Vorteile:** Spaltenbasierte Speicherung, Massively Parallel Processing (MPP), Optimierung für Aggregationen und Joins .
  - **Beispiel:** Analyse von Verkaufsdaten über mehrere Jahre hinweg, um Trends zu identifizieren.

  **Entscheidungshilfe:**

  - **RDS/Aurora:** Bei häufigen Schreiboperationen und geringer Latenzanforderung.
  - **Redshift:** Bei komplexen Abfragen, historischen Datenanalyse und hohem Datenvolumen.

---

## 2. **Multi-AZ vs. Read Replica: Worin liegt der Unterschied – und in welcher Situation wählst du welche Option?**

- **Multi-AZ Deployment:**

  - **Zweck:** Hohe Verfügbarkeit und Notfallwiederherstellung (DR).
  - **Funktionsweise:** Automatische Failover zu einer Standby-Instanz in einer anderen Availability Zone (AZ) bei Ausfall.
  - **Einsatz:** Kritische Produktionssysteme, die minimale Downtime erfordern (z. B. Banken, E-Commerce) .

- **Read Replica:**

  - **Zweck:** Skalierung von Leseoperationen.
  - **Funktionsweise:** Asynchrone Replikation des Primär-Clusters, um Leseabfragen zu verteilen.
  - **Einsatz:** Leseintensive Workloads (z. B. Berichte, Dashboards) .

  **Entscheidungshilfe:**

  - **Multi-AZ:** Bei Notfallresilienz und minimaler Ausfallzeit.
  - **Read Replica:** Bei Leselast-Verteilung, ohne HA-Anforderungen.

---

## 3. **Athena vs. Redshift: Wann reicht SQL auf S3 (Athena) und wann brauchst du ein Data Warehouse (Redshift)?**

- **Athena:**

  - **Einsatz:** Ad-hoc-Abfragen zu **unstrukturierten/semi-structured Daten** (z. B. CSV, JSON) in S3.
  - **Vorteile:** Kein Infrastrukturmanagement, kostengünstig für sporadische Analysen .
  - **Beispiel:** Schnelle Überprüfung von Webserver-Logs.

- **Redshift:**

  - **Einsatz:** **Strukturierte Daten** in großen Volumina mit komplexen Abfragen (Joins, Aggregationen).
  - **Vorteile:** Optimierte Abfrageperformance, Columnar Storage, Integration mit BI-Tools .
  - **Beispiel:** Monatliche Vertriebsberichte mit Multi-Table-Joins.

  **Entscheidungshilfe:**

  - **Athena:** Bei einfacheren Analysen ohne Infrastrukturaufwand.
  - **Redshift:** Bei komplexen Workloads und langfristiger Datenarchivierung.

---

## 4. **Shared Responsibility (DB): Nenne je zwei Aufgaben von AWS und dir**

- **AWS:**

  1. **Infrastruktur-Sicherheit:** Physische Sicherheit der Rechenzentren, Netzwerk-Schutz (z. B. Firewalls).
  2. **Automatische Updates:** Betriebssystem- und Datenbank-Updates (z. B. RDS-Patches) .

- **Du (Kunde):**

  1. **Datenverwaltung:** Verschlüsselung, Zugriffsrechte (IAM-Policies), Backups.
  2. **Anwendungslogik:** Datenmodellierung, ETL-Pipelines, Abfrageoptimierung .

---

## 5. **Glue: Welche Probleme löst AWS Glue im Analytics-Umfeld?**

- **Datenintegration:** Automatische Schema-Erkennung und Katalogisierung von Daten aus S3, RDS, etc.
- **ETL/ELT-Prozesse:** Serverlose Transformationen (z. B. Datenbereinigung, Formatkonvertierung) .
- **Datenqualität:** Erkennung von Duplikaten, fehlenden Werten durch benutzerdefinierte Skripte.
- **Metadaten-Management:** Zentrale Speicherung von Tabellen- und Partitionierungsinformationen.

---

## 6. **ElastiCache vs. DAX: Worin unterscheiden sich ElastiCache und DAX – wann nimmst du welches?**

- **ElastiCache (Redis/Memcached):**

  - **Allgemeiner Caching-Dienst** für beliebige Daten (z. B. Session-Daten, API-Caching).
  - **Flexibel:** Unterstützt mehrere Datenstrukturen und Skalierung.

- **DAX (DynamoDB Accelerator):**

  - **Spezialisiert auf DynamoDB:** Reduziert Latenz für häufige Lesezugriffe (z. B. User-Profile).
  - **Nahtlose Integration:** Keine Codeänderungen nötig, direkte Verwendung der DynamoDB-API .

  **Entscheidungshilfe:**

  - **ElastiCache:** Bei gemischten Caching-Anforderungen.
  - **DAX:** Optimierung von DynamoDB-Read-Heavy-Workloads.

---

## Zusammenfassung

Die Wahl der AWS-Dienste hängt stark von der **Workload-Eigenschaft** (OLTP/OLAP, Echtzeit vs. Batch) und **Anforderungen an Verfügbarkeit/Skalierung** ab. Für komplexe Analysen ist Redshift überlegen, während Athena für einfache, ad-hoc-Abfragen genügt. Bei Multi-AZ vs. Read Replica entscheidet die Priorität zwischen HA und Leseperformance.
