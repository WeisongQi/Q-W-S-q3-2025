# Aufgabe Heute

## 1. **Unterschied zwischen EBS und Instance Store**

- **EBS (Elastic Block Store)**

  - **Persistenz**: Daten bleiben auch nach Beendigung der EC2-Instanz erhalten .
  - **Leistung**: Konfigurierbare IOPS und Durchsatz (z. B. gp3, io2) .
  - **Verwaltung**: Kann an/durch Instanzen angehängt/detachet werden, unterstützt Snapshots und Änderungen der Größe .
  - **Kosten**: Separate Abrechnung basierend auf Kapazität und Leistung .

- **Instance Store**:
  - **Vergänglichkeit**: Daten gehen bei Instanz-Stop/Beendigung verloren .
  - **Leistung**: Hohe IOPS durch physische Anbindung an den Host .
  - **Größe**: Fixiert, abhängig von der Instanztyp .
  - **Kosten**: Inklusive in der EC2-Instanzgebühr .

**Einsatz**:

- **EBS**: Persistente Daten (Datenbanken, Anwendungen).
- **Instance Store**: Temporäre Daten (Caching, Big-Data-Processing) .

---

## 2. **Wann setzt man ein AMI ein? Vorteile**

- **Einsatz**:

  - Schnelle Bereitstellung neuer Instanzen mit vorkonfigurierten Umgebungen (z. B. Betriebssystem, Software).
  - Konsistenz über mehrere Instanzen hinweg (z. B. Entwicklung/Produktion-Umgebungen).
  - Wiederherstellung nach Ausfällen.

- **Vorteile**:
  - **Schnelle Startzeiten**: Instanzen starten in Sekunden .
  - **Kustomisierung**: Benutzerdefinierte Konfigurationen (z. B. Sicherheitsupdates, Anwendungen) .
  - **Kosteneffizienz**: Keine manuelle Einrichtung pro Instanz erforderlich .

---

## 3. **Einsatzszenarien für EFS**

- **Big-Data-Analyse**: Shared Storage für Hadoop/Spark-Cluster .
- **Web-Apps**: statische Inhalte (Bilder, Videos) für mehrere Server .
- **Containerisierung**: Persistent Volumes für Kubernetes-Pods .
- **Medienverarbeitung**: Simultane Bearbeitung großer Dateien (z. B. Rendering) .

---

## 4. **FSx for Windows vs. FSx for Lustre**

- **FSx for Windows**:

  - **Dateisystem**: NATiv Windows-NTFS.
  - **Protokoll**: SMB.
  - **Einsatz**: Windows-basierte Apps (z. B. Active Directory, Home-Directorys) .

- **FSx for Lustre**:
  - **Dateisystem**: Paralleles Lustre-Dateisystem.
  - **Protokoll**: POSIX/Lustre-API.
  - **Einsatz**: HPC, Machine Learning, große Datenmengen .

---

## 5. **Folgen des Löschens aller Instanzen in einer Auto Scaling Group**

- **Instanzen**: Alle laufenden Instanzen werden beendet .
- **Lastverteilung**: Load Balancer entfernt die Instanzen aus der Zielgruppe .
- **Kapazität**: Die Gruppe setzt die gewünschte Kapazität auf 0, und neue Instanzen werden nicht mehr bereitgestellt .
- **Datenverlust**: Daten auf Instance Stores gehen verloren; EBS-Volumes bleiben erhalten, sofern sie nicht gelöscht wurden .

---

## 6. **Vorteil dynamischer vs. geplanter Skalierung**

- **Dynamische Skalierung**:

  - **Anpassung an Last**: Skalierung basierend auf Echtzeit-Nutzung (z. B. Spitzenzeiten) .
  - **Kosteneinsparung**: Reduziert Kapazität in Leerlaufphasen .
  - **Flexibilität**: Ideal für unvorhersehbare Workloads (z. B. E-Commerce-Traffic) .

- **Geplante Skalierung**:
  - **Vorhersehbare Last**: Skalierung nach festen Zeitplänen (z. B. tägliche Spitzen) .
  - **Einfachere Konfiguration**: Keine Echtzeit-Monitoring nötig .
  - **Nachteil**: Kann zu Über- oder Unterkapazität führen, wenn die Last nicht exakt vorhergesagt wird .

**Zusammenfassung**: Dynamische Skalierung ist besser für variable Workloads, geplante für vorhersehbare Muster .
