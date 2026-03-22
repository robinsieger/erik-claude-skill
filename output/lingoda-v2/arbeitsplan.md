# Arbeitsplan – KI-gestützte Modellierung von Lernverhalten & Beteiligungsdrift zur datenbasierten Optimierung individueller Lernpfade im Online-Sprachunterricht

## AP1 – Datentransformation & Plattformaufbau (Datenarchitektur) Jan 2021 – Jun 2021

### AP1.1 – Transformieren der ETL-Pipeline zu ELT-Architektur: Jan 2021 – Mär 2021
Die bestehende ETL-basierte Datenverarbeitungspipeline wird zu einem ELT-Paradigma umstrukturiert. Datenquellen (Lernplattform, Buchungssystem, CRM, Zahlungssysteme) werden über SaaS-basierte Konnektoren (Stitch, Fivetran) angebunden, um die Extraktionszeit von Wochen auf Stunden zu reduzieren. Die Rohdaten werden direkt in einen Data Lake geladen, bevor Transformationen angewendet werden.
**Ergebnis:** Funktionsfähige ELT-Pipeline mit automatisierter Extraktion aus allen relevanten Quellsystemen.

### AP1.2 – Implementieren des Data Lake mit Rohdatenbereitstellung: Mär 2021 – Mai 2021
Aufbau eines zentralen Data Lake, der Rohdaten aus allen Quellsystemen in ihrem Originalformat speichert und für interne Stakeholder sofort zugänglich macht. Implementierung von Zugriffsschichten, die explorative Analysen auf Rohdaten ermöglichen, ohne auf die Transformation warten zu müssen.
**Ergebnis:** Data Lake mit direktem Rohdatenzugriff für 12–15 Analysten; Zugriffslatenz <1 Stunde nach Ingestion.

### AP1.3 – Aufbauen der Transformationsschicht: Apr 2021 – Jun 2021
Implementierung der Transformationsschicht mittels deklarativer Modellierung (DBT, SQL/Jinja-Templates). Durch den Wechsel von Python/Airflow-basierter Transformation zu SQL-basierter deklarativer Modellierung wird die Zahl der befähigten Datenmodellierer von 3–4 Dateningenieuren auf 12–15 Personen erweitert. Statistische Plausibilitätsprüfungen sichern die Datenqualität.
**Ergebnis:** Vollständige Transformationsschicht mit automatisierten Qualitätschecks; eine zentrale Wahrheitsquelle (Data Warehouse).

## AP2 – Feature Engineering & Subskriptionskettenmodellierung (Verhaltensmodellierung) Mai 2021 – Sep 2021

### AP2.1 – Konstruieren individueller Subskriptionsketten: Mai 2021 – Jul 2021
Aus den heterogenen Nutzungsdaten werden individuelle Subskriptionsketten rekonstruiert, die den gesamten Lernverlauf eines Nutzers abbilden: Testphase, erste Subskription, Pausen, Reaktivierungen, Formatwechsel und Abbruch. Diese Zustandsketten existierten nicht in der Produktionsdatenbank und mussten als neues Datenmodell konstruiert werden.
**Ergebnis:** Dokumentiertes Datenmodell für Subskriptionsketten mit vollständiger Abbildung aller Zustandsübergänge.

### AP2.2 – Extrahieren verhaltensbasierter Features: Jul 2021 – Aug 2021
Systematische Extraktion von Verhaltensmerkmalen aus den Subskriptionsketten: Anwesenheitsquoten, Buchungsmuster (Zeitfenster, Häufigkeit, Vorlaufzeit), Kursfortschritt, Nutzung von Zusatzmaterialien, Pausendauer und -häufigkeit. Feature-Selektion mittels Korrelationsanalyse und Varianzanalyse (ANOVA).
**Ergebnis:** Feature-Matrix mit >20 verhaltensbasierten Merkmalen pro Nutzer; dokumentierte Feature-Importance-Analyse.

### AP2.3 – Evaluieren der Feature-Qualität: Aug 2021 – Sep 2021
Statistische Evaluation der Feature-Qualität: Prüfung auf Multikollinearität, Analyse der Trennschärfe einzelner Features mittels ROC-Analyse, Bewertung der zeitlichen Stabilität der Features über verschiedene Kohorten.
**Ergebnis:** Bereinigter Feature-Satz mit dokumentierter Qualitätsbewertung; Empfehlung für die Modellentwicklung.

## AP3 – ML-basierte Beteiligungsdrift-Prognose (Maschinelles Lernen) Aug 2021 – Feb 2022

### AP3.1 – Trainieren von Prognosemodellen: Aug 2021 – Nov 2021
Training mehrerer ML-Algorithmen (Random Forest, Gradient Boosting, logistische Regression) auf den konstruierten Feature-Vektoren zur Prognose der 7-Tage-Abbruchwahrscheinlichkeit. Berücksichtigung des Klassenungleichgewichts (85 % Nicht-Abbrecher vs. 15 % Abbrecher) durch Oversampling (SMOTE) und Gewichtungsanpassung.
**Ergebnis:** Trainierte Modelle mit dokumentierten Hyperparametern; initiale Prognose für 7-Tage-Horizont.

### AP3.2 – Evaluieren mittels Kreuzvalidierung & Benchmarking: Nov 2021 – Jan 2022
Systematische Evaluation der Modelle mittels k-facher Kreuzvalidierung (k=10). Benchmarking gegen das bestehende kohortenbasierte Retentionsmodell. Metriken: Precision, Recall, F1-Score, AUC-ROC. Identifikation des leistungsfähigsten Modells für den Produktiveinsatz.
**Ergebnis:** Benchmark-Bericht mit Modellvergleich; Empfehlung für das Produktivmodell.

### AP3.3 – Erweitern des Prognosehorizonts: Jan 2022 – Feb 2022
Erweiterung des Prognosemodells von 7-Tage- auf 4-Wochen- und 3-Monats-Horizonte. Untersuchung, ob die Feature-Relevanz über längere Horizonte stabil bleibt oder ob zusätzliche temporale Features (Saisonalität, Kurszyklen) erforderlich sind.
**Ergebnis:** Evaluationsbericht zur Prognosequalität über verschiedene Zeithorizonte; Dokumentation der Modellstabilität.

## AP4 – Probabilistisches Kanalwirkungsmodell (Stochastische Modellierung) Okt 2021 – Apr 2022

### AP4.1 – Implementieren des Markov-Ketten-Modells: Okt 2021 – Jan 2022
Entwicklung eines Markov-Ketten-basierten Attributionsmodells, das die Übergangswahrscheinlichkeiten zwischen Marketingkanälen auf dem Weg zur Konversion datengetrieben schätzt. Im Gegensatz zum bestehenden regelbasierten Last-Touch-Modell werden alle Kanalkontakte berücksichtigt.
**Ergebnis:** Funktionsfähiges Markov-Ketten-Attributionsmodell mit Übergangsmatrizen für alle relevanten Kanalkombinationen.

### AP4.2 – Entwickeln der Shapley-Wert-Dekomposition: Jan 2022 – Mär 2022
Implementierung einer Shapley-Wert-basierten Dekomposition, die den marginalen Beitrag jedes Kanals zur Gesamtkonversion fair quantifiziert. Vergleich der Shapley-Allokation mit den Markov-Ketten-Ergebnissen und dem regelbasierten Referenzmodell.
**Ergebnis:** Shapley-basiertes Kanalwirkungsmodell mit dokumentierter Allokationslogik.

### AP4.3 – Benchmarken gegen das regelbasierte Referenzmodell: Mär 2022 – Apr 2022
Systematischer Vergleich der drei Attributionsansätze (regelbasiert, Markov-Ketten, Shapley-Wert) auf historischen Konversionsdaten. Analyse der Abweichungen zwischen den Modellen und Identifikation von Kanälen mit größten Diskrepanzen.
**Ergebnis:** Benchmark-Bericht mit Modellvergleich; Empfehlung für das Produktivmodell.

## AP5 – Nudging-Architektur & Mobile Integration (Interventionsdesign) Mär 2022 – Jul 2022

### AP5.1 – Entwerfen der verhaltensbasierten Nudging-Logik: Mär 2022 – Apr 2022
Entwicklung eines regelbasierten Interventionssystems, das auf Basis der Drift-Prognosen individuelle Nudging-Maßnahmen ableitet: Buchungserinnerungen, personalisierte Übungsempfehlungen, Motivationsimpulse. Definition von Interventionsschwellen und Eskalationsstufen.
**Ergebnis:** Dokumentiertes Nudging-Regelwerk mit Interventionsmatrix (Risikostufe x Maßnahme).

### AP5.2 – Entwickeln der mobilen Applikation: Apr 2022 – Jun 2022
Konzeption und Entwicklung einer mobilen Applikation zur Auslieferung der Nudging-Interventionen und Bereitstellung von Übungsmaterialien, die auf den aktuellen Kursfortschritt und die individuellen Lernziele abgestimmt sind. Berücksichtigung der globalen Nutzerschaft (Mehrsprachigkeit, Zeitzonen).
**Ergebnis:** Funktionsfähiger Prototyp der mobilen Applikation mit Nudging-Integration.

### AP5.3 – Evaluieren der Nudging-Wirkung: Jun 2022 – Jul 2022
Statistische Evaluation der Nudging-Wirkung auf Engagement-Kenngrößen (Buchungsfrequenz, Anwesenheitsquote, Kursabschlussrate) mittels Hypothesentests (t-Tests, Chi-Quadrat-Tests). Vergleich der Interventionsgruppe mit einer Kontrollgruppe.
**Ergebnis:** Evaluationsbericht mit statistischer Wirkungsanalyse; Empfehlungen für die Weiterentwicklung des Nudging-Systems.
