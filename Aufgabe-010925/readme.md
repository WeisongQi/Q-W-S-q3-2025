# Aufgabe Heute

## **Szenario 1: Ein Startup für Online-Spiele**

- **Hauptproblem:** Das Startup hat ein unvorhersehbares und möglicherweise stark schwankendes Traffic-Volumen zum Start, aber ein sehr begrenztes Budget, das es nicht erlaubt, vorsorglich in teure Infrastruktur zu investieren.
- **Wichtigster Vorteil 1 & Begründung:** **Elastizität/Skalierbarkeit**. Cloud-Services können automatisch und schnell Ressourcen (Server, Speicher) nach oben oder unten skalieren, je nach tatsächlicher Nachfrage. Das Startup kann die Server-Kapazität dynamisch an die Anzahl der Spieler anpassen und zahlt nur für das, was es wirklich nutzt.
- **Wichtigster Vorteil 2 & Begründung:** **Pay-per-use (Kostenersparnis).** Anstatt teure Server im Voraus zu kaufen, die möglicherweise ungenutzt bleiben, ermöglicht das Pay-per-use-Modell die Abrechnung nach tatsächlicher Nutzung. Dies reduziert die Anfangsinvestitionen erheblich und schont das knappe Budget des Startups.

## **Szenario 2: Ein E-Commerce-Händler für Weihnachtsdekoration**

- **Hauptproblem:** Das Unternehmen betreibt eine eigene, teure IT-Infrastruktur, die nur drei Monate im Jahr voll ausgelastet ist, während sie die restlichen neun Monate ungenutzt Kosten verursacht (Strom, Wartung, Miete).
- **Wichtigster Vorteil 1 & Begründung:** **Pay-per-use (Kostenersparnis).** Durch die Nutzung von Cloud-Diensten kann das Unternehmen von einem Modell der Betriebskosten (OPEX) statt der Investitionskosten (CAPEX) profitieren. Es zahlt nur während der Spitzensaison für die benötigten Ressourcen und kann diese außerhalb der Saison fast vollständig herunterfahren, was zu erheblichen Einsparungen führt.
- **Wichtigster Vorteil 2 & Begründung:** **Elastizität/Skalierbarkeit.** Die Cloud ermöglicht es, die Serverkapazität in der kurzen, aber intensiven Weihnachtszeit massiv zu erhöhen, um den 50-fachen Traffic zu bewältigen, ohne dass die Website langsamer wird oder ausfällt. Nach der Saison kann die Kapazität sofort wieder auf das Minimum reduziert werden.

## **Szenario 3: Eine globale Nachrichten-App**

- **Hauptproblem:** Die App hat lange Ladezeiten für Nutzer in weit entfernten Regionen (Asien, Nordamerika), da alle Daten von einem zentralen Serverstandort in Deutschland geladen werden müssen. Der Aufbau eigener Rechenzentren ist zu teuer und dauert zu lange.
- **Wichtigster Vorteil 1 & Begründung:** **Globale Reichweite/Verfügbarkeit.** Cloud-Anbieter verfügen über Rechenzentren und Content Delivery Networks (CDNs) auf der ganzen Welt. Die Nachrichten-App kann ihre Inhalte und Services schnell und einfach in der Nähe der Nutzer in Tokio und New York bereitstellen, was die Ladezeiten dramatisch verkürzt und das Nutzererlebnis verbessert.
- **Wichtigster Vorteil 2 & Begründung:** **Agilität/Geschwindigkeit.** Die Expansion in neue Märkte kann dank der Cloud in wenigen Wochen oder Monaten umgesetzt werden, anstatt Jahre für den Bau eigener Rechenzentren warten zu müssen. Dies ermöglicht es dem Unternehmen, schnell auf globale Wachstumschancen zu reagieren und Wettbewerbsvorteile zu erzielen.

---

**Tabelle zur Zusammenfassung:**

| Szenario           | Hauptproblem des Unternehmens                                                    | Vorteil 1 & Begründung                                                                                                                    | Vorteil 2 & Begründung                                                                                                 |
| ------------------ | -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| 1. Gaming-Startup  | Unvorhersehbare Nachfragespitzen bei begrenztem Budget.                          | **Elastizität/Skalierbarkeit:** Ressourcen passen sich der Nachfrage an und verhindern Leistungseinbrüche.                                | **Pay-per-use (Kostenersparnis):** Es werden keine teuren, überdimensionierten Server im Voraus gekauft.               |
| 2. E-Commerce      | Ineffiziente, kostenintensive Infrastruktur, die 9 Monate im Jahr ungenutzt ist. | **Pay-per-use (Kostenersparnis):** Kosten fallen nur für die tatsächlich genutzte Kapazität während der Hauptsaison an.                   | **Elastizität/Skalierbarkeit:** Ermöglicht die schnelle Bewältigung des 50-fachen Traffic-Anstiegs zur Weihnachtszeit. |
| 3. Nachrichten-App | Lange Ladezeiten und hoher Aufwand für die globale Expansion.                    | **Globale Reichweite/Verfügbarkeit:** Daten können in der Nähe von Nutzern in aller Welt bereitgestellt werden, was die Latenz reduziert. | **Agilität/Geschwindigkeit:** Schnelle Markterweiterung ohne den jahrelangen und teuren Bau eigener Rechenzentren.     |

## **Bonusfrage:**

- **Netflix:** Eine der bekanntesten AWS-Fallstudien ist die von Netflix. Das Unternehmen hebt oft die **Elastizität** und **Skalierbarkeit** hervor. Netflix muss täglich riesige Mengen an Video-Traffic für Millionen von Nutzern weltweit streamen. Die Nachfrage schwankt jedoch stark (z.B. abends, wenn die meisten Nutzer streamen). Durch die Cloud kann Netflix die Kapazität dynamisch anpassen. Sie müssen nicht für die Spitzenlast der gesamten Welt 24/7 Server betreiben, sondern können die Infrastruktur je nach geografischer und zeitlicher Nachfrage skalieren. Ein weiterer oft genannter Punkt ist die **Agilität**, die es Netflix ermöglicht, schnell neue Services und Funktionen zu entwickeln und weltweit bereitzustellen, ohne sich um die darunterliegende physische Infrastruktur kümmern zu müssen.
