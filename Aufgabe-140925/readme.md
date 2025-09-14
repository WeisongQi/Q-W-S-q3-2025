# Aufgabe Heute

## **Antworten auf die gestellten Fragen:**

---

### **1. IAM: Unterschied zwischen IAM-Policy (identitätsbasiert) und Bucket-Policy (ressourcenbasiert)**

- **IAM-Policy (identitätsbasiert):**

  - **Definition:** Regeln, die an IAM-Entitäten (Benutzer, Gruppen, Rollen) gebunden sind und deren Zugriffsrechte auf AWS-Dienste definieren .
  - **Einsatz:**
    - Zentralisierte Verwaltung von Berechtigungen für Benutzer/Rollen innerhalb eines Accounts.
    - Beispiele: Zugriff auf EC2-Instanzen, Lambda-Funktionen oder CloudWatch-Logs.
  - **Beispiel:**

    ```json
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Effect": "Allow",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::my-bucket/*"
        }
      ]
    }
    ```

- **Bucket-Policy (ressourcenbasiert):**

  - **Definition:** Regeln, die direkt an S3-Buckets gebunden sind und kontrollieren, wer auf den Bucket und seine Objekte zugreifen darf .
  - **Einsatz:**
    - Cross-Account-Zugriff (z. B. erlauben, dass ein externer AWS-Account auf Ihren Bucket zugreift).
    - Öffentliche Zugriffsbeschränkungen (z. B. Blockieren öffentlicher Schreibzugriffe).
  - **Beispiel:**

    ```json
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Effect": "Deny",
          "Principal": "*",
          "Action": "s3:DeleteObject",
          "Resource": "arn:aws:s3:::my-bucket/*"
        }
      ]
    }
    ```

- **Least Privilege (Prinzip der geringsten Rechte):**
  - **Konkretisierung:**
    - Benutzer/Rollen erhalten nur die minimal erforderlichen Berechtigungen für ihre Aufgaben.
    - Beispiel: Ein Benutzer, der nur Logs lesen soll, erhält keinen Schreibzugriff auf den Bucket.
  - **Umsetzung:**
    - Nutzung von `Deny`-Anweisungen in Policies, um unnötige Aktionen auszuschließen .
    - Regelmäßige Überprüfung von Policies zur Berechtigungsbereinigung.

---

### **2. EC2/EBS/Instance Store**

- **Wann Instance Store statt EBS wählen?**

  - **Instance Store (ephemeral Storage):**
    - **Vorteile:** Hohe IOPS, keine zusätzlichen Kosten (inbegriffen im EC2-Preis).
    - **Einsatz:** Temporäre Daten wie Caches, Session-Daten oder Batch-Jobs, bei denen Datenverlust akzeptabel ist .
    - **Nachteil:** Daten gehen beim Stoppen/Beenden der Instanz verloren.

- **EBS-Volume in eine andere AZ verschieben:**

  1. **Snapshot erstellen:**

     ```bash
     aws ec2 create-snapshot --volume-id vol-123456 --description "Backup for AZ migration"
     ```

  2. **Snapshot in der Ziel-AZ verwenden:**

     ```bash
     aws ec2 create-volume --snapshot-id snap-123456 --availability-zone eu-central-1a
     ```

  3. **Volume an Instanz anhängen:**

     ```bash
     aws ec2 attach-volume --volume-id vol-654321 --instance-id i-123456 --device /dev/xvdb
     ```

- **Neues Volume anhängen:**

  1. **Volume erstellen oder Snapshot verwenden.**
  2. **Volume an Instanz binden:**

     ```bash
     aws ec2 attach-volume --volume-id vol-123456 --instance-id i-123456 --device /dev/xvdb
     ```

  3. **Dateisystem auf dem Volume erstellen und einhängen (z. B. mit `mkfs` und `/etc/fstab`).**

---

### **3. Load Balancer (ALB)**

- **Vorteile gegenüber direktem Instanzenzugriff:**

  - **Lastverteilung:** Automatische Verteilung von Anfragen auf mehrere Instanzen.
  - **Health Checks:** Automatische Erkennung und Ausschluss fehlerhafter Instanzen .
  - **SSL-Terminierung:** Verschlüsselung der Kommunikation am Load Balancer.
  - **Pfadbasiertes Routing:** Anfragen an verschiedene Instanzen basierend auf Pfaden (z. B. `/api/*` vs. `/static/*`).

- **Health Checks:**

  - **Funktionsweise:** ALB sendet regelmäßig HTTP(S)-Anfragen an Instanzen. Bei Nichtantwort (z. B. HTTP 5xx) wird die Instanz als "unhealthy" markiert.
  - **Aktion bei unhealthy Instanz:** ALB leitet Traffic automatisch auf gesunde Instanzen um.

- **Pfadbasiertes Routing:**

  - **Einsatz:** Unterschiedliche Backends für unterschiedliche Anfragepfade (z. B. `/api` an eine EC2-Instanz, `/static` an ein S3-Bucket).
  - **Beispiel-Konfiguration:**

    ```json
    {
      "Conditions": [{ "PathPattern": "/api/*" }],
      "Targets": [{ "Id": "i-123456", "Port": 80 }]
    }
    ```

---

### **4. Auto Scaling Group (ASG)**

- **Parameter:**

  - **Desired Capacity:** Aktuelle Anzahl der Instanzen.
  - **Min/Max Capacity:** Minimale/Maximale Instanzenanzahl.

- **Target Tracking vs. Scheduled Scaling:**

  - **Target Tracking:**
    - **Funktionsweise:** Automatische Skalierung basierend auf Metriken (z. B. CPU-Auslastung von 40 %).
    - **Beispiel:** Erhöhung der Instanzen bei CPU-Auslastung > 70 %.
  - **Scheduled Scaling:**
    - **Funktionsweise:** Skalierung nach festgelegten Zeitplänen (z. B. doppelte Instanzen an Feiertagen).

- **Ersetzen unhealthy Instanzen:**
  - **Prozess:**
    1. ASG erkennt unhealthy Instanz über Health Checks.
    2. Instanz wird beendet und durch eine neue Instanz ersetzt (basierend auf Launch Template).

---

### **5. S3: "Ordner" als Präfixe**

- **Begründung:**

  - S3 ist ein Schlüssel-Wert-Store. "Ordner" sind lediglich Präfixe in Schlüsseln (z. B. `documents/2023/`).
  - Dies ermöglicht logische Gruppierung ohne physische Unterverzeichnisse .

- **Storage-Klassen:**

  - **Logs:** **S3 Standard** – Häufige Zugriffe, hohe Verfügbarkeit.
  - **Statische Assets:** **S3 Intelligent-Tiering** – Automatische Optimierung von Kosten und Performance.
  - **Archivdaten:** **S3 Glacier** – Niedrige Kosten für seltenen Zugriff.

- **Öffentliche Lesbarkeit:**

  1. **Bucket-Policy:**

     ```json
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Effect": "Allow",
           "Principal": "*",
           "Action": "s3:GetObject",
           "Resource": "arn:aws:s3:::my-bucket/*"
         }
       ]
     }
     ```

  2. **ACL (veraltet):**
     - `s3:PutObjectAcl` mit `public-read` verwenden (nicht empfohlen).

---

### **6. Snowball**

- **Größenordnung:**
  - **Empfohlen ab:** 10 TB an Daten, da Netztransfers teuer und langsam sind.
- **Risiken von Netztransfers:**
  - **Kosten:** Hohe Bandbreitenkosten (insbesondere für große Dateien).
  - **Zeit:** Lange Übertragungsdauer (z. B. 10 TB über 100 Mbit/s benötigen ~28 Stunden).
  - **Sicherheit:** Risiko von Datenlecks während des Transfers.

---

### **Zusammenfassung**

Die Auswahl der AWS-Dienste hängt stark von den Anforderungen an **Datenpersistenz**, **Skalierung**, **Sicherheit** und **Kosten** ab. IAM-Policies und Bucket-Policies ergänzen sich dabei, um granulare Zugriffsrechte zu gewährleisten, während Tools wie ALB und ASG die Betriebsstabilität sicherstellen. Für S3 ist die Wahl der richtigen Storage-Klasse entscheidend, um Kosten und Performance zu optimieren.
