# Aufgabe Heute

## 1. **AWS-Schutz im Shared Responsibility Model**

AWS übernimmt im Shared Responsibility Model die Sicherheit der Infrastruktur (z. B. physische Rechenzentren, Hypervisor, Netzwerk- und Speicherebene), während Kunden für die Sicherheit ihrer Anwendungen, Daten und Konfigurationen verantwortlich sind. Konkret:

- **AWS**:
  - Schützt physische Einrichtungen, Hypervisor, virtuelle Maschinen und Netzwerkebene .
  - Stellt Sicherheitsdienste wie AWS Shield (DDoS-Schutz) und AWS WAF bereit .
- **Kunde**:
  - Verantwortlich für Betriebssysteme, Anwendungen, Datenverschlüsselung (z. B. KMS) und Zugriffssteuerung (IAM) .
  - Konfiguriert Sicherheitsgruppen, Netzwerk-ACLs und WAF-Regeln .

---

## 2. **Shield Standard vs. WAF-Regeln**

- **Shield Standard**:
  - **Wann**: Schützt gegen Infrastruktur-Angriffe (Layer 3/4) wie SYN-Floods oder UDP-Flooding .
  - **Einsatz**: Automatische Abschwächung von DDoS-Angriffen, ideal für allgemeine Verfügbarkeitssicherung.
- **WAF-Regeln**:
  - **Wann**: Benötigt für Angriffe auf Anwendungsebene (Layer 7), z. B.:
    - **Rate-Limit**: Verhindert DDoS durch Anfragenbegrenzung (z. B. 1.000 Anfragen/Minute) .
    - **SQLi/XSS**: Blockiert injektionsbasierte Angriffe über HTTP-Header oder Parameter .
  - **Beispiel**: WAF-Regeln wie `BlockSQLInjection` oder `RateLimit` für WebACLs .

---

## 3. **KMS vs. ACM vs. Secrets Manager**

| Service             | Zweck                                     | Problemstellung                                                   |
| ------------------- | ----------------------------------------- | ----------------------------------------------------------------- |
| **AWS KMS**         | Verschlüsselungsschlüssel-Management      | Zentrale Verwaltung von Krypto-Schlüsseln (z. B. für S3, RDS) .   |
| **AWS ACM**         | TLS/SSL-Zertifikate-Verwaltung            | Automatische Bereitstellung von Zertifikaten für Webanwendungen . |
| **Secrets Manager** | Geheimnismanagement (z. B. DB-Passwörter) | Automatische Rotation und sichere Speicherung sensibler Daten .   |

---

## 4. **Priorisierung von Sicherheits-Findings**

- **GuardDuty**:
  - **Priorität 1**: Erkennung von verdächtigen Aktivitäten (z. B. unbefugte IP-Zugriffe, Kryptojacking) .
  - **Beispiel**: Sofortige Überprüfung von Instanzen mit `Port Scanning`-Alarmen.
- **Inspector**:
  - **Priorität 2**: Schwachstellen in VMs/Container-Images (z. B. veraltete Pakete) .
  - **Beispiel**: Behebung von CVEs in Amazon Linux-AMI-Builds.

---

## 5. **AWS Config & Security Hub für Compliance**

- **AWS Config**:
  - Protokolliert Ressourcenkonfigurationen (z. B. "Sicherheitsgruppen mit offenen Ports") und vergleicht sie mit Compliance-Richtlinien (z. B. GDPR) .
- **Security Hub**:
  - Aggregiert Sicherheitsdaten aus GuardDuty, Inspector und anderen Quellen.
  - Generiert Berichte für Standards wie ISO 27001 oder HIPAA .
- **Beispiel**: Automatische Erstellung von Compliance-Dashboards für Audits.
