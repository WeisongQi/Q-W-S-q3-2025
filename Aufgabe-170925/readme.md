# Aufgabe Heute

## **AWS CDK: Vorteile gegenüber reinem YAML und Beispiel für wiederverwendbare Konstrukte**

**Vorteile von CDK:**

1. **Programmierbarkeit:** CDK ermöglicht die Infrastruktur als Code (IaC) in allgemeinen Programmiersprachen (z. B. TypeScript, Python) zu definieren, was Flexibilität und Wiederverwendbarkeit erhöht. YAML ist statischer und weniger anpassbar .
2. **Typensicherheit:** Durch die Verwendung von Klassen und Interfaces werden Fehler in der Infrastrukturdefinition frühzeitig erkannt.
3. **Modularität:** Komplexe Infrastrukturen lassen sich in wiederverwendbare Konstrukte zerlegen, die über NPM-Pakete oder private Repositories geteilt werden können .
4. **Integration mit AWS-Diensten:** CDK bietet hochwertige Bindungen zu AWS-Diensten (z. B. S3, EC2), die in YAML-Schemas nicht vollständig abgebildet werden können.

**Beispiel für ein wiederverwendbares Konstrukt:**
Ein **S3-Bucket-Konstrukt** mit Lebenszyklusregeln zur automatischen Löschung alter Objekte:

```typescript
import * as cdk from "aws-cdk-lib";
import { Construct } from "constructs";
import * as s3 from "aws-cdk-lib/aws-s3";

export class ReusableS3Bucket extends Construct {
  public readonly bucket: s3.Bucket;
  constructor(
    scope: Construct,
    id: string,
    props: { lifecycleRuleDays: number }
  ) {
    super(scope, id);
    this.bucket = new s3.Bucket(this, "Bucket", {
      lifecycleRules: [
        { expiration: cdk.Duration.days(props.lifecycleRuleDays) },
      ],
      removalPolicy: cdk.RemovalPolicy.DESTROY,
    });
  }
}
```

Dieser Konstrukt kann in mehreren Projekten importiert und mit unterschiedlichen Parametern instantiiert werden .

---

## **AWS Elastic Beanstalk: Automatisierte Infrastruktur vs. manuelle Aufgaben**

**Automatisch verwaltete Teile:**

- **Bereitstellungsumgebung:** Erstellung von EC2-Instanzen, Load-Balancern, Auto Scaling-Gruppen und VPC-Konfigurationen .
- **Deployment-Pipeline:** Automatische Bereitstellung von Anwendungscode über CI/CD-Integration (z. B. AWS CodePipeline) .
- **Skalierung:** Dynamische Anpassung der Instanzenanzahl basierend auf Traffic-Metriken (z. B. CPU-Auslastung) .

**Manuell zu überwachende Aspekte:**

- **Anwendungscode:** Entwicklung und Tests der Anwendung selbst (z. B. Fehlerbehebung in der Geschäftslogik).
- **Datenbankkonfiguration:** Verbindungsparameter und Schema-Migrationen für RDS-Instanzen .
- **Sicherheitsrichtlinien:** Manuelle Definition von IAM-Rollen und Sicherheitsgruppen für interne Kommunikation (z. B. zwischen EC2 und RDS) .

---

## **AWS Code-Services: Rollenverteilung bei Build, Orchestrierung und Deployment**

1. **Build:**

   - **AWS CodeBuild:** Kompiliert Code, führt Tests aus und generiert Artefakte (z. B. JAR-Dateien).
   - _Beispiel:_ Ein `buildspec.yml` definiert Phasen wie `install` (Abhängigkeiten) und `build` (Kompilierung) .

2. **Orchestrierung:**

   - **AWS CodePipeline:** Steuert den CI/CD-Workflow (z. B. Trigger bei Code-Commits, Sequential/Parallel-Ausführung von Stufen).

3. **Deployment:**
   - **AWS CodeDeploy:** Deployed Artefakte auf EC2, Lambda oder On-Premise-Servern. Nutzt `appspec.yml`, um Bereitstellungsschritte (z. B. Skripte) zu definieren .

**CodeArtifact:**
Dient als zentraler Speicher für private Pakete (z. B. npm, Maven). Wird während des Builds genutzt, um Abhängigkeiten herunterzuladen, und während des Deployments, um Artefakte bereitzustellen .

---

## **AWS Systems Manager: Parameter Store vs. Session Manager**

1. **Parameter Store:**

   - **Einsatzfall:** Speicherung sensibler Konfigurationsdaten (z. B. Datenbank-Passwörter, API-Schlüssel).
   - _Beispiel:_ Ein Parameter `db_password` wird in Parameter Store gespeichert und von EC2-Instanzen über IAM-Rollen abgerufen .

2. **Session Manager:**
   - **Einsatzfall:** Remote-Debugging und -Verwaltung von Instanzen ohne SSH-Zugriff.
   - _Beispiel:_ Ein Entwickler startet über die AWS-Konsole eine Sitzung, um Logs in einer EC2-Instanz zu analysieren oder Fehler zu debuggen .

**Zusammenfassung:**

- **Parameter Store:** Für statische Konfigurationsdaten.
- **Session Manager:** Für interaktive Sitzungen zur Problembehebung.
