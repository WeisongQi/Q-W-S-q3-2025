# Aufgabe Heute

## 1. **Warum ist ein S3-Bucket nicht automatisch öffentlich und welche zwei Schritte braucht es für öffentliche Leserechte?**

AWS S3-Buckets sind standardmäßig privat, um unbeabsichtigte Datenlecks zu verhindern. Um öffentliche Leserechte zu gewähren, sind folgende Schritte notwendig:

- **Schritt 1:** Deaktivieren Sie die _Block Public Access_-Einstellungen im Bucket. Dies überprüft, ob die Bucket-Politik oder Object ACLs keine öffentlichen Zugriffe blockieren .
- **Schritt 2:** Konfigurieren Sie entweder eine **Bucket-Politik**, die `s3:GetObject`-Berechtigungen für alle Benutzer (`Principal": "*"`) erteilt, oder setzen Sie die Object-ACL auf `public-read` bei der Upload-Phase .

Beispiel für eine Bucket-Politik:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

---

## 2. **Objekt vs. Key in S3 und warum „Ordner“ eigentlich Präfixe sind**

- **Objekt:** Ein Objekt ist die physische Speicherung von Daten (z. B. eine Datei) im S3-Bucket. Es enthält die Daten selbst und Metadaten wie Größe, Erstellungsdatum und ACLs .
- **Key:** Der Key ist der eindeutige Bezeichner eines Objekts innerhalb eines Buckets. Er ähnelt einem Dateipfad (z. B. `images/photo.jpg`) und dient zur Adressierung des Objekts .
- **Präfixe als "Ordner":** Präfixe (z. B. `backup/`) werden verwendet, um Objekte hierarchisch zu gruppieren. Sie funktionieren wie virtuelle Ordner, sind aber keine echten Verzeichnisse. S3 listet nur Objekte, deren Key mit dem Präfix beginnt .

---

## 3. **Versionierung: Was passiert beim Überschreiben/Löschen eines Objekts und wie kommst du an eine alte Version?**

- **Überschreiben:** Beim Überschreiben eines Objekts wird eine neue Version erstellt, während die alte Version erhalten bleibt. Die neue Version erhält eine neue Versions-ID .
- **Löschen:** Ein Löschen führt zur Erstellung einer _Löschmarkierung_ (Version-ID `null`), die als aktuelle Version markiert wird. Die vorherigen Versionen bleiben erhalten .
- **Alte Version abrufen:** Um eine historische Version zu erhalten, geben Sie die spezifische `VersionId` in einer GET-Anfrage an (z. B. `aws s3api get-object --version-id <ID>`). Eine dauerhafte Löschung erfordert die Angabe der `VersionId` in einer DELETE-Anfrage .

---

## 4. **CRR vs. SRR: Anwendungsfälle**

- **CRR (Cross-Region Replication):**
  - **Szenario:** Disaster Recovery, globale Verfügbarkeit.
  - **Beispiel:** Replikation von Daten in die EU, wenn die US-Region ausfällt .
- **SRR (Same-Region Replication):**
  - **Szenario:** Redundanz innerhalb einer Region, lokale Backups.
  - **Beispiel:** Replikation von Datenbank-Snapshots in einer anderen Zone derselben Region .

---

## 5. **Vorteile/Nachteile von Storage-Klassen (Beispiel: Standard-IA vs. Glacier Instant)**

| **Klasse**          | **Vorteil**                           | **Nachteil**                             |
| ------------------- | ------------------------------------- | ---------------------------------------- |
| **Standard-IA**     | Geringere Kosten für seltenen Zugriff | Höhere Lösch-/Abrufgebühren              |
| **Glacier Instant** | Extrem niedrige Speicherkosten        | Lange Wiederherstellungszeiten (Stunden) |

---

## 6. **Lifecycle-Rule für Logs/Archive zur Kostenoptimierung**

- **Kriterien:**
  - **Übergangsregeln:** Archivieren Sie nach 30 Tagen in `Standard-IA` und nach 90 Tagen in `Glacier`.
  - **Löschregeln:** Löschen Sie nach 365 Tagen (z. B. für temporäre Logs).
  - **Filter:** Wenden Sie Regeln nur auf Präfixe wie `logs/` oder `archive/` an .
- **Beispiel-Regel:**

  ```json
  {
    "Status": "Enabled",
    "Filter": { "Prefix": "logs/" },
    "Transitions": [
      {
        "Days": 30,
        "StorageClass": "STANDARD_IA"
      },
      {
        "Days": 90,
        "StorageClass": "GLACIER"
      }
    ],
    "Expiration": { "Days": 365 }
  }
  ```

Diese Konfiguration reduziert Kosten durch automatische Verschiebung in günstigere Klassen und zeitgesteuerte Löschung.
