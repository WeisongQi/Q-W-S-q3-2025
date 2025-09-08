# Aufgabe Heute

## Kurze Antworten auf die Aufgabenstellung

### **1. Vertikale vs. horizontale Skalierung**

- **Vertikale Skalierung**: Eine einzelne Instanz wird durch leistungsstärkere Hardware (z. B. mehr CPU/RAM) aufgerüstet. Ideal für Workloads, die starke Einzelressourcen benötigen, hat aber physische Grenzen .
- **Horizontale Skalierung**: Hinzufügen mehrerer Instanzen, um Last zu verteilen. Flexibler und fehlertoleranter, da einzelne Ausfälle nicht kritisch sind .

---

### **2. Warum Load Balancer SPOF verhindern**

Ein Load Balancer verteilt den Traffic auf **mehrere Backend-Instanzen**. Falls eine Instanz ausfällt, leitet er den Traffic automatisch um, sodass der gesamte Service nicht zusammenbricht. Durch Redundanz (z. B. Active-Passive-Cluster) wird SPOF eliminiert .

---

### **3. On-Demand vs. Reserved Instances**

- **On-Demand**: Keine langfristige Bindung, bezahlbar pro Stunde. Flexibel, aber teurer bei dauerhafter Nutzung .
- **Reserved Instances**: Langfristige Buchung (1–3 Jahre) mit bis zu 72 % Rabatt. Günstiger für stabile Workloads, aber unflexibel bei Änderungen .

---

## Vorteile/Nachteile der Kaufoptionen (EC2 & Load Balancer)

### **EC2-Kaufoptionen**

| Option                 | Vorteil                                  | Nachteil                                  |
| ---------------------- | ---------------------------------------- | ----------------------------------------- |
| **On-Demand**          | Kein Commitment, sofortige Verfügbarkeit | Hohe Kosten bei langfristiger Nutzung     |
| **Reserved Instances** | Geringere Kosten, Kapazitätsgarantie     | Hohe Anfangsinvestition, unflexibel       |
| **Spot Instances**     | Extrem günstig für kurzfristige Jobs     | Instanz kann jederzeit abgebrochen werden |

---

### **Load Balancer-Kaufoptionen**

| Option              | Vorteil                                           | Nachteil                               |
| ------------------- | ------------------------------------------------- | -------------------------------------- |
| **Application ALB** | Optimiert für HTTP/HTTPS, einfache Konfiguration  | Nicht für extreme Performance geeignet |
| **Network NLB**     | Ultra-hohe Durchsatzleistung (Millionen Anfragen) | Komplexere Einrichtung                 |
| **Gateway GWLB**    | Integriert Sicherheitslösungen (Firewalls)        | Spezialisiert, weniger flexibel        |

---

### Zusätzliche Hinweise

- **Horizontale Skalierung** erfordert oft Load Balancer und verteilte Datenbanken (z. B. Sharding), um Konsistenz zu gewährleisten .
- **Spot Instances** eignen sich gut für Batch-Jobs, aber nicht für kritische Echtzeitanwendungen .
