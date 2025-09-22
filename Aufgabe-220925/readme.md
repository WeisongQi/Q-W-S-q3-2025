# Aufgabe Heute

## 1. **Entkopplung und Vorteile von Queues gegenüber direkter Kopplung**

**Entkopplung** (Decoupling) ermöglicht es, Systemkomponenten unabhängig voneinander zu entwickeln und zu skalieren. Eine **Queue** (z. B. Amazon SQS) bietet folgende Vorteile gegenüber direkter Kopplung:

- **Fehlerisolierung**: Wenn ein Konsumierer ausfällt, bleiben Nachrichten in der Queue erhalten und werden später verarbeitet .
- **Lastverteilung**: Mehrere Konsumierer können parallele Nachrichten verarbeiten, ohne dass der Producer blockiert wird .
- **Asynchrone Verarbeitung**: Producer müssen nicht auf eine Antwort warten, was die Reaktionszeit verbessert .
- **Skalierbarkeit**: Die Queue kann je nach Last automatisch skaliert werden .

---

## 2. **SQS vs. SNS: Wann nutze ich welches?**

| **SQS (Simple Queue Service)**                                                          | **SNS (Simple Notification Service)**                                                                      |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Einsatz**: Asynchrone Verarbeitung (z. B. Bestellungen in einer Warteschlange) .      | **Einsatz**: Echtzeit-Benachrichtigungen (z. B. SMS, E-Mails) an mehrere Abonnenten .                      |
| **Nachrichten**: Speichert Nachrichten bis zu 14 Tage, bis sie verarbeitet werden .     | **Nachrichten**: Keine Persistenz; werden sofort gesendet und verloren, wenn kein Abonnent verfügbar ist . |
| **Consumer**: Ein Consumer pro Queue (FIFO) oder mehrere (Standard) .                   | **Consumer**: Unbegrenzte Abonnenten (z. B. Lambda, HTTP-Endpunkte) .                                      |
| **Beispiel**: Bestellverarbeitung, wo jede Bestellung einzeln verarbeitet werden muss . | **Beispiel**: Benachrichtigung an 10.000 Nutzer über einen neuen Artikel .                                 |

---

## 3. **Wann Kinesis?**

Nutze **Amazon Kinesis**, wenn:

- **Echtzeit-Datenströme** verarbeitet werden (z. B. IoT-Sensordaten, Log-Analysen) .
- **Parallele Verarbeitung** erforderlich ist (z. B. gleichzeitige Analyse durch mehrere Consumer) .
- **Datenreplay** oder **Batch-Verarbeitung** benötigt wird (z. B. historische Datenanalyse) .
- **Beispiel**: Überwachung von Echtzeit-Transaktionen, um Betrug zu erkennen .

---

## 4. **CloudWatch: Metriken, Alarms, Logs**

- **Metrik**: Messwerte, die Ressourcen-Performance anzeigen (z. B. CPU-Auslastung, Netzwerkverkehr) .
- **Alarm**: Trigger bei Metrik-Überschreitung (z. B. CPU > 80% für 5 Minuten) und senden Benachrichtigungen .
- **Logs**: Detaillierte Aktivitätsprotokolle (z. B. Anwendungsfehler), gespeichert in CloudWatch Logs .

---

## 5. **EventBridge & CloudTrail: Zeitplan/Pattern und Änderungsnachweise**

- **EventBridge**:
  - **Zeitplan**: Regelmäßige Ausführung (z. B. tägliche Backups) über Cron-Expressions .
  - **Pattern**: Filterung von Ereignissen (z. B. "Alle EC2-Instanzen-Starts") .
- **CloudTrail**:
  - Protokolliert **API-Aufrufe** (z. B. wer eine Ressource gelöscht hat) .
  - **Änderungen finden**: Im CloudTrail-Konsolen filtere nach Ereignissen wie `DeleteResource` und prüfe das `userIdentity`-Feld .

---

## Zusammenfassung

- **Queues** (SQS) für zuverlässige, asynchrone Kommunikation.
- **SNS** für Breitband-Benachrichtigungen.
- **Kinesis** für Echtzeit-Datenströme.
- **CloudWatch** zur Überwachung und Alarmierung.
- **EventBridge/CloudTrail** für Event-Routing und Sicherheitsaudits.
