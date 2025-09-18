# Aufgabe Heute

## 1. **Warum senkt die Nähe einer Region oder Edge-Location die Latenz?**

Die Nähe einer Region oder Edge-Location reduziert die Latenz, da die physische Entfernung zwischen Nutzer und Server minimiert wird. Daten müssen weniger weit über das Netzwerk übertragen werden, was die Übertragungszeit verkürzt. Edge-Locations befinden sich in der Nähe der Nutzer und nutzen lokale Netzwerkinfrastrukturen, um Content-Caching und direkte Verarbeitung von Anfragen zu ermöglichen. Dies reduziert die Anzahl der Hops (Netzwerk-Sprünge) und vermeidet Engpässe im öffentlichen Internet .

---

## 2. **Was unterscheidet CloudFront von S3 Transfer Acceleration?**

- **CloudFront**:

  - **Funktion**: CDN (Content Delivery Network), das statische/dynamische Inhalte (z. B. Bilder, Videos, APIs) an Edge-Locations cacht und global verteilt.
  - **Ziel**: Latenzreduktion für Endnutzer durch nahegelegene Cache-Server.
  - **Beispiel**: Bereitstellung einer Website mit globaler Reichweite .

- **S3 Transfer Acceleration**:
  - **Funktion**: Optimiert das Hoch- und Herunterladen von Daten in S3-Buckets über AWS-Edge-Locations.
  - **Ziel**: Beschleunigung großer Dateitransfers (z. B. Backup-Dateien) durch routingoptimierte Pfade.
  - **Beispiel**: Upload eines 10 GB-Videos von Asien in einen US-basierten S3-Bucket .

---

## 3. **Weighted Routing vs. Latency Routing in Route 53**

- **Weighted Routing**:

  - **Einsatz**: Verteilt Traffic gemäß festgelegten Gewichten auf mehrere Endpunkte (z. B. A/B-Tests, schrittweise Deployment-Übergänge).
  - **Beispiel**: 80 % Traffic an eine neue Version einer Anwendung, 20 % an die alte Version .

- **Latency Routing**:
  - **Einsatz**: Leitet Traffic an den Endpunkt mit der geringsten Latenz basierend auf der Nutzergeografie.
  - **Beispiel**: Globale Anwendung, die in Echtzeit reagieren muss (z. B. Online-Gaming) .

---

## 4. **Vorteil des AWS Global Accelerator**

AWS Global Accelerator optimiert die Netzwerkleistung durch:

- **Anycast-IPs**: Statische Eintrittspunkte, die Traffic an die nächste AWS-Region weiterleiten.
- **AWS-Backbone-Netzwerk**: Vermeidet öffentliche Internet-Wege, reduziert Latenz und Jitter.
- **Automatische Failover**: Erkennung gesunder Endpunkte und Traffic-Umleitung bei Ausfällen.
- **Vorteil gegenüber Standard-Routing**: Stabilere Leistung, besonders für transkontinentale Anwendungen .

---

## 5. **Beispiel für AWS Outposts**

Ein Unternehmen nutzt **AWS Outposts**, um eine lokale Recheninstanz in einer Niederlassung in Europa zu betreiben. Dies ermöglicht:

- **Hybrides Cloud-Modell**: Daten verarbeiten, die aus Datenschutzgründen lokal bleiben müssen (z. B. Gesundheitsdaten).
- **Nahtlose Integration**: Direkte Verbindung zum AWS-Cloud-Backend für Backups oder Machine-Learning-Modelle .

---

## 6. **Relevanz von Wavelength für 5G-Anwendungen**

**Wavelength** ist eine AWS-Dienstebene, die Edge-Computing-Ressourcen direkt an 5G-Mobilfunkbasestationen integriert. Dies ermöglicht:

- **Ultrahohe Geschwindigkeiten und niedrige Latenz**: Kritisch für Anwendungen wie autonomes Fahren (Echtzeit-Sensorik) oder AR/VR (nahtlose Interaktion).
- **Datenverarbeitung am Rand**: Vermeidung von Round-Trip-Delays im Kernnetzwerk .

---

## 7. **Nutzen von Local Zones**

**Local Zones** sind AWS-Erweiterungen in Ballungsräumen (z. B. Berlin, München). Vorteile:

- **Reduzierte Latenz**: Für Echtzeit-Anwendungen wie Finanztransaktionen oder Online-Spiele.
- **Lokale Compliance**: Daten speichern und verarbeiten, ohne über Regionen hinweg zu wandern.
- **Kosteneffizienz**: Keine langen Datenwege, z. B. für IoT-Geräte in Smart Cities .

---
