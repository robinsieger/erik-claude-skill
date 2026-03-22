# Arbeitsplan – ML-basiertes adaptives Lern-Ökosystem zur datengetriebenen Abbruchprognose & Interventionssteuerung im Online-Spracherwerb

## AP1 – Datenplattform-Transformation & Echtzeitdatenverfügbarkeit (Datenarchitektur) (Jan 2021 – Jun 2021)

### AP1.1 – Transformieren der ETL-Architektur zu ELT mit Data Lake: Jan 2021 – Mär 2021
Die bestehende ETL-basierte Datenplattform wurde grundlegend umstrukturiert. Rohdaten aus heterogenen Quellsystemen (Produktionsdatenbank, Buchungssystem, Zahlungsplattform) wurden in einen zentralen Data Lake überführt, der sofortige Verfügbarkeit in Rohformat gewährleistet. Die bisherige Architektur erforderte Wochen bis Monate für die Datenbereitstellung; die ELT-Architektur ermöglicht Zugriff in Stunden.
**Ergebnis:** Funktionsfähiger Data Lake mit automatisierten Extraktionspipelines für alle relevanten Datenquellen.

### AP1.2 – Implementieren deklarativer Transformationsschichten: Mär 2021 – Mai 2021
Auf dem Data Lake wurden SQL-basierte Transformationsschichten implementiert, die Rohdaten in analytisch nutzbare Modelle überführen. Durch den deklarativen Ansatz konnten neben den Dateningenieuren auch Datenanalysten (12-15 Personen statt zuvor 3-4) an der Transformationslogik mitwirken, was die Entwicklungsgeschwindigkeit signifikant erhöhte.
**Ergebnis:** Deklarative Transformationspipeline mit versionierter Modelllogik und automatisierten Tests.

### AP1.3 – Validieren der Datenqualität und Verfügbarkeit: Mai 2021 – Jun 2021
Die transformierten Daten wurden systematisch gegen das Produktionssystem validiert. Statistische Vergleichsanalysen (Zeilenanzahl, Verteilungen, Nullwert-Anteile) stellten sicher, dass die ELT-Pipeline keine systematischen Verzerrungen einführt.
**Ergebnis:** Validierungsbericht mit quantifizierten Abweichungsmetriken; dokumentierte Datenqualitätssicherung.

## AP2 – Subskriptionsketten-Rekonstruktion & Feature Engineering (Datenmodellierung) (Apr 2021 – Sep 2021)

### AP2.1 – Rekonstruieren von Subskriptionsverläufen aus heterogenen Quelldaten: Apr 2021 – Jun 2021
Die Lernverläufe der Nutzenden mussten aus fragmentierten Quelldaten (Testphasen, aktive Abonnements, Pausen, Reaktivierungen, Kündigungen) in zusammenhängende Subskriptionsketten transformiert werden. Diese Datenstruktur existierte in keinem bestehenden System. Domänenspezifische Regeln für die Verkettung von Statusübergängen wurden entwickelt und iterativ validiert.
**Ergebnis:** Rekonstruierte Subskriptionsketten für den gesamten historischen Nutzerstamm mit dokumentierter Verkettungslogik.

### AP2.2 – Entwickeln domänenspezifischer Features: Jun 2021 – Aug 2021
Aus den Subskriptionsketten wurden Merkmale extrahiert, die das Abbruchrisiko prognostizieren: Teilnahmefrequenz, Pausenmuster, Rabattnutzung, Testverhalten, Buchungszeitpunkte. Zusätzlich wurden aggregierte Verhaltensmetriken (z.B. Trend der Teilnahmefrequenz über rollierende Fenster) als Features konzipiert.
**Ergebnis:** Feature-Katalog mit dokumentierten Definitionen, Berechnungslogik und explorativer Analyse der prädiktiven Relevanz.

### AP2.3 – Validieren der Verlaufsketten gegen manuelle Stichproben: Aug 2021 – Sep 2021
Eine stratifizierte Stichprobe von 200 Nutzerprofilen wurde manuell gegen die automatisch rekonstruierten Verlaufsketten geprüft. Diskrepanzen wurden analysiert und die Rekonstruktionslogik iterativ angepasst.
**Ergebnis:** Validierungsprotokoll mit Fehlerklassifikation und quantifizierter Rekonstruktionsgenauigkeit (>95% Übereinstimmung).

## AP3 – ML-basierte Abbruchprognose (Maschinelles Lernen) (Jul 2021 – Mär 2022)

### AP3.1 – Trainieren und Benchmarken von Klassifikationsverfahren: Jul 2021 – Nov 2021
Mehrere Klassifikationsverfahren (Random Forest, Gradient Boosting, Logistic Regression) wurden auf den rekonstruierten Subskriptionsketten trainiert. Das starke Klassenungleichgewicht (nur ca. 15% Abbrüche) erforderte spezifische Resampling-Strategien (SMOTE, Undersampling) und angepasste Verlustfunktionen. Prognosehorizont: zunächst 7 Tage, geplante Erweiterung auf 4 Wochen und 3 Monate.
**Ergebnis:** Benchmarkbericht mit Vergleich der Modelle hinsichtlich Precision, Recall und F1-Score auf stratifiziertem Test-Set.

### AP3.2 – Evaluieren mittels Kreuzvalidierung und Schwellenwertoptimierung: Nov 2021 – Jan 2022
Die Modelle wurden mittels k-facher Kreuzvalidierung evaluiert. Die Entscheidungsschwellenwerte wurden systematisch optimiert, um die Balance zwischen Fehlalarmen (unnötige Interventionen) und verpassten Abbrüchen zu justieren. Konfidenzintervalle für die Prognosegüte wurden berechnet.
**Ergebnis:** Optimierte Schwellenwertmatrix mit dokumentiertem Trade-off zwischen Precision und Recall.

### AP3.3 – Testen des Prognosemodells unter Realbedingungen: Jan 2022 – Mär 2022
Das Modell wurde auf aktuelle Nutzerdaten angewendet und die Prognosen gegen tatsächliches Verhalten evaluiert. Hierbei zeigte sich, ob die auf historischen Daten trainierte Modellierung auch unter veränderten Rahmenbedingungen (neue Kursformate, saisonale Effekte) valide Ergebnisse liefert.
**Ergebnis:** Evaluierungsbericht mit Prognosequalität unter Realbedingungen; dokumentierte Abweichungen und Modellgrenzen.

## AP4 – Probabilistische Kanalwirkungsanalyse (Probabilistische Modellierung) (Okt 2021 – Mai 2022)

### AP4.1 – Implementieren einer Markov-Ketten-basierten Kanalattribution: Okt 2021 – Jan 2022
Ein Markov-Ketten-Modell wurde entwickelt, das die Übergangswahrscheinlichkeiten zwischen den Kontaktpunkten der Nutzenden im Akquisitionsprozess abbildet. Im Gegensatz zum bestehenden regelbasierten Last-Touch-Modell lernt das Markov-Modell die Kanalwirkungen aus historischen Konversionspfaden.
**Ergebnis:** Implementiertes Markov-Ketten-Attributionsmodell mit dokumentierten Übergangsmatrizen.

### AP4.2 – Entwickeln einer Shapley-Wert-Dekomposition zur Kanalgewichtung: Jan 2022 – Mär 2022
Ergänzend wurde eine spieltheoretische Dekomposition (Shapley-Wert) implementiert, die den marginalen Beitrag jedes Kanals zur Konversion quantifiziert. Die Kombination mit dem Markov-Modell erlaubt die Kreuzvalidierung der Attributionsergebnisse.
**Ergebnis:** Shapley-basiertes Attributionsmodell mit Kanal-Ranking und Konfidenzintervallen.

### AP4.3 – Evaluieren gegenüber regelbasiertem Referenzmodell: Mär 2022 – Mai 2022
Die probabilistischen Modelle wurden systematisch gegen das bestehende regelbasierte Attributionsmodell evaluiert. Divergenzen wurden analysiert und auf ihre Plausibilität geprüft. Besonderes Augenmerk lag auf der Interpretierbarkeit der Ergebnisse für Entscheidungsträger.
**Ergebnis:** Vergleichsanalyse mit quantifizierten Abweichungen zum Referenzmodell; Interpretationsleitfaden für Entscheidungsträger.

## AP5 – Nudging-Framework & Interventionssteuerung (Systemintegration) (Mär 2022 – Jul 2022)

### AP5.1 – Konzipieren der verhaltensbasierten Interventionslogik: Mär 2022 – Apr 2022
Basierend auf den Abbruchprognosen (AP3) wurde eine Interventionslogik konzipiert, die risikoadaptierte Handlungsempfehlungen ableitet: Buchungserinnerungen, Übungsempfehlungen, Klassenvorschläge. Die Interventionsintensität wurde an die prognostizierte Abbruchwahrscheinlichkeit gekoppelt.
**Ergebnis:** Dokumentierte Interventionslogik mit Entscheidungsregeln und Schwellenwerten.

### AP5.2 – Entwickeln mobiler Auslieferungskomponenten: Apr 2022 – Jun 2022
Für die Auslieferung der Übungsinhalte und Interventionssignale wurde eine mobile Applikationsarchitektur konzipiert, die den globalen Nutzerstamm (verschiedene Zeitzonen, Endgeräte, Netzwerkbedingungen) adressiert. Curriculumsalignierte Übungsinhalte wurden für die mobile Nutzung aufbereitet.
**Ergebnis:** Prototyp der mobilen Interventionskomponente mit curriculumsalignierten Inhalten.

### AP5.3 – Evaluieren der Interventionswirksamkeit: Jun 2022 – Jul 2022
Die Wirksamkeit der Interventionen auf die Verbleibswahrscheinlichkeit wurde mittels kontrollierter Vergleiche evaluiert. Kenngroessen: Teilnahmefrequenz, Buchungsverhalten, Verbleibsdauer nach Intervention.
**Ergebnis:** Evaluierungsbericht mit quantifizierter Interventionswirksamkeit und identifizierten Optimierungspotenzialen.
