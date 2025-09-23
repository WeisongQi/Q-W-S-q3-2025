# Aufgabe Heute

## 1. **Was ist eine VPC?**

Eine Virtual Private Cloud (VPC) ist ein logisch isoliertes Netzwerk in einer Public Cloud, das es Unternehmen ermöglicht, Ressourcen wie Server und Datenbanken in einem privaten, kontrollierten Umfeld bereitzustellen. Sie bietet Sicherheit durch Netzwerksegmentierung und ermöglicht die Integration mit lokalen Netzwerken über VPN oder Direct Connect .

---

## 2. **Public vs. Private Subnet**

- **Public Subnet**: Hat eine Route zum Internet Gateway (IGW) und kann öffentliche IPs erhalten (z. B. Webserver).
- **Private Subnet**: Keine direkte Internetverbindung; benötigt NAT-Gateways für ausgehenden Traffic.
- **Fehlende Route im Private Subnet**: Keine Route zum IGW, stattdessen Route zu NAT-Gateway (z. B. `0.0.0.0/0 → NAT`) .

---

## 3. **Internet Gateway vs. NAT Gateway**

- **Internet Gateway (IGW)**: Ermöglicht bidirektionalem Traffic (Ein-/Ausgang) für öffentliche Subnetze (z. B. Web-Apps).
- **NAT Gateway**: Ermöglicht nur ausgehenden Traffic für private Subnetze (z. B. Datenbank-Updates).
- **Beispiel**: Ein Webserver in einer Public Subnet verwendet ein IGW, während eine interne App in einer Private Subnet ein NAT nutzt .

---

## 4. **Route Tables**

- **Internetzugriff**: Route `0.0.0.0/0` zum IGW (Public Subnet) oder NAT (Private Subnet).
- **Subnet-Kommunikation**: Route zwischen Subnetzen über VPC-Routing (z. B. `10.0.1.0/24 → 10.0.2.0/24`).
- **Beispiel**: Private Subnet-Route-Table leitet Traffic über NAT-Gateway an das Internet .

---

## 5. **Security Group vs. NACL**

- **Security Group (SG)**: _Stateful_, instance-bezogen. Erlaubt z. B. SSH (Port 22) oder HTTP (Port 80).
- **NACL**: _Stateless_, subnetzbezogen. Steuert Ein-/Ausgangsregeln (z. B. Blockieren von ICMP).
- **Typisches Beispiel**:
  - SG: `ALLOW TCP 80 FROM 0.0.0.0/0` (Webzugriff).
  - NACL: `DENY ICMP FROM 192.168.1.0/24` (Ping-Blockierung) .

---

## 6. **IPv4/IPv6 in AWS**

- **IPv4**: Beim Stop/Start ändern sich private IPs. Elastic IPs bleiben erhalten (für feste öffentliche IPv4-Adressen).
- **IPv6**: Adressen bleiben nach Stop/Start erhalten.
- **Elastic IPs**: Wichtig für Server mit dauerhaften öffentlichen IPs (z. B. Load Balancer) .

---

## 7. **VPC Endpoints**

- **Gateway Endpoint**: Für AWS-Dienste wie S3/DynamoDB (keine Internetverbindung nötig).
- **Interface Endpoint**: Für Drittdienste (z. B. EC2 über PrivateLink).
- **Beispiel**: S3-Access über Gateway Endpoint, Lambda über Interface Endpoint .

---

## 8. **VPC Peering-Regeln**

- **Überlappende CIDRs**: Verhindern Routing-Konflikte (z. B. VPC A: `10.0.0.0/16`, VPC B: `10.0.0.0/24`).
- **Nicht transitiv**: Traffic muss direkt zwischen Peered VPCs fließen, keine Zwischen-Hops .

---

## 9. **VPC Flow Logs**

- **Ziel**: CloudWatch Logs oder S3-Buckets.
- **Nutzung**: Analysieren von Traffic-Patterns, Erkennen von Angriffen (z. B. ungewöhnlicher Datenverkehr) .

---

## 10. **Site-to-Site VPN vs. Direct Connect**

- **VPN**: Über Internet, kostengünstig, aber höhere Latenz (z. B. Filiale mit VPN-Tunnel).
- **Direct Connect**: Physische Leitung, niedrige Latenz, hohe Bandbreite (z. B. Rechenzentrum-Verbindung) .

---

## 11. **Client VPN**

- **Einsatz**: Remote-Zugriff von externen Geräten (z. B. Mitarbeiter von zu Hause).
- **Vorteil gegenüber S2S-VPN**: Keine dedizierte Hardware nötig, einfachere Konfiguration .

---

## 12. **Transit Gateway**

- **Vorteil**: Zentralisiertes Management mehrerer VPCs/VPN-Verbindungen.
- **Anwendung**: Komplexe Topologien (z. B. Hybrid Cloud mit mehreren Regionen) .

---

## 13. **Troubleshooting: Private Subnet-Instanz ohne Internet**

1. **NAT-Gateway**: Überprüfen, ob eine Route (`0.0.0.0/0 → NAT`) in der Subnet-Route-Table existiert.
2. **Sicherheitsgruppen**: Sicherstellen, dass ausgehender Traffic (z. B. HTTP/HTTPS) erlaubt ist.
3. **NAT-Instanz-Status**: Überprüfen, ob das NAT-Gateway aktiv und korrekt konfiguriert ist .
