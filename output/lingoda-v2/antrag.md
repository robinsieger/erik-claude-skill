# KI-gestützte Modellierung von Lernverhalten & Beteiligungsdrift zur datenbasierten Optimierung individueller Lernpfade im Online-Sprachunterricht

## Was ist das Ziel Ihres Vorhabens? Welche Herausforderung oder Problemstellung soll mit dem Vorhaben gelöst bzw. welche Wissenslücke soll mit dem Vorhaben geschlossen werden?

Online-Sprachlernangebote mit Live-Unterricht verzeichnen hohe Abbruchraten: Bis zu 60 % d. Lernenden beenden Kurse (9–12 Monate) vorzeitig. Die Ursachen liegen in heterogenen Lernbiografien, variablen Motivationsverläufen & fehlender individueller Anpassung d. Lernpfade an d. tatsächliche Nutzungsverhalten. Bestehende Ansätze (Duolingo, Babbel, Busuu) fokussieren gamifizierte Selbstlernmodule & liefern keine Prognosefähigkeit für Verbleibswahrscheinlichkeiten in lehrergestützten Gruppenformaten; kohortenbasierte Retentionsmodelle bilden nur Durchschnittswerte ab, ohne individuelle Verhaltensmuster zu erfassen.
Ziel war es zu untersuchen, ob ein datengetriebener Ansatz aus (1) einem ML-basierten Prognosemodell für Beteiligungsdrift (Random Forest, Gradient Boosting, logist. Regression), (2) einem probabilistischen Kanalwirkungsmodell (Markov-Ketten, Shapley-Wert-Dekomposition) & (3) einer verhaltensbasierten Nudging-Architektur individuelle Lernverläufe so modellieren kann, dass Abbruchrisiken frühzeitig identifiziert & durch gezielte Interventionen reduziert werden. Voraussetzung war die Transformation d. ETL-basierten Datenplattform zu einem ELT-Paradigma mit semantischer Harmonisierung heterogener Quellsysteme (Lernplattform, Buchungssystem, CRM).
Angestrebt wurden Erkenntnisse darüber, ob & unter welchen Bedingungen verhaltensbasierte Modellierung die 7-Tage-Abbruchprognose auf eine Präzision >80 % steigern & auf 4-Wochen- sowie 3-Monats-Horizonte erweitern kann.

(1491 / 1.500 Zeichen)

## Inwieweit hebt sich das angestrebte Produkt, Verfahren oder die Dienstleistung vom Stand der Technik ab?

Zum Vorhabenbeginn 2021 existierten keine integrierten Verfahren, die Abbruchprognose, Kanalwirkungsanalyse & Nudging für lehrergestützten Live-Gruppenunterricht verbinden. Plattformen wie Duolingo, Babbel & Busuu fokussieren Selbstlernformate.
Neu:
- ML-basierte Drift-Prognose auf individuellen Subskriptionsketten
- Probabilist. Kanalwirkungsmodell (Markov-Ketten, Shapley-Wert)
- Verhaltensbasierte Nudging-Architektur m. Rückkopplung
- ELT-Datenplattform m. semantischer Quellenharmonisierung

(497 / 500 Zeichen)

## Welche Arbeiten werden durchgeführt, um der zuvor benannten Herausforderung oder Problemstellung zu begegnen bzw. um die Wissenslücke zu schließen?

Zunächst wurde d. ETL-Datenplattform zu einem ELT-Paradigma transformiert: Heterogene Quellsysteme (Lernplattform, Buchungssystem, CRM) wurden extrahiert & als Rohdaten im Data Lake bereitgestellt; d. Transformationsschicht wurde m.H.v. deklarativer Modellierung (SQL/Jinja-Templates) neu implementiert. Darauf wurden individuelle Subskriptionsketten konstruiert, die Pausen, Reaktivierungen & Testphasen abbilden (Feature Engineering). Nun wurde ein ML-Prognosemodell für Beteiligungsdrift entwickelt: Algorithmen (Random Forest, Gradient Boosting, logist. Regression) wurden auf historischen Verhaltensdaten (Anwesenheit, Buchungsverhalten, Kursfortschritt) trainiert & mittels Kreuzvalidierung evaluiert. Parallel wurde ein probabilist. Kanalwirkungsmodell (Markov-Ketten, Shapley-Wert) gegen d. regelbasierte Referenz benchmarked. Final wurde eine verhaltensbasierte Nudging-Architektur entworfen & in einer mobilen Applikation integriert.

(943 / 1.000 Zeichen)

## Welche wissenschaftlichen, technischen und/oder methodischen Unsicherheiten bestehen bei der Bearbeitung der Herausforderung oder Problemstellung?

Unklar ist, ob d. ML-basierte Prognosemodell auf Basis individueller Subskriptionsketten Beteiligungsdrift zuverlässig prognostizieren kann, da d. Lernverläufe durch nicht-lineare Zustandsübergänge (Pausen, Reaktivierungen, Formatwechsel) gekennzeichnet sind, deren Sequenzmuster sich einer standardisierten Feature-Repräsentation entziehen. Dem wurde m. iterativer Feature-Konstruktion & algorithmischem Benchmarking (Random Forest, Gradient Boosting, logist. Regression) begegnet. Dennoch besteht d. Risiko, dass d. Modell bei Horizonterweiterung (7 Tage → 4 Wochen → 3 Monate) instabile Prognosen liefert, da langfristige Verhaltensmuster stärkeren exogenen Störfaktoren unterliegen.
Unklar ist ferner, ob d. probabilist. Kanalwirkungsmodell (Markov-Ketten) Kanaleffekte valide isolieren kann, da eine unabhängige Grundwahrheit für d. Kanalwirkung fehlt. Konfundierungseffekte (saisonale Schwankungen, Kampagnenüberlagerungen) könnten systematische Verzerrungen erzeugen.

(974 / 1.000 Zeichen)

## Schlagwörter

1. Machine Learning
2. Beteiligungsdrift-Prognose
3. Kanalwirkungsanalyse
4. Markov-Ketten
5. Nudging-Architektur
6. Sprachlernplattform
7. ELT-Datenplattform
8. Feature Engineering
9. Subskriptionsketten-Modellierung
10. Verhaltensbasierte Modellierung

## Arbeitspakete (Kurzfassung)

1 Datentransformation & Plattformaufbau
1.1 Transformieren d. ETL-Pipeline zu ELT-Architektur (deklarative Modellierung, SQL/Jinja)
1.2 Implementieren d. Data Lake m. Rohdatenbereitstellung (semantische Harmonisierung)
1.3 Validieren d. Datenqualität & Aufbau d. Transformationsschicht (statist. Plausibilitätsprüfung)

2 Feature Engineering & Subskriptionskettenmodellierung
2.1 Konstruieren individueller Subskriptionsketten aus Nutzungsdaten (Zustandsmodellierung)
2.2 Extrahieren verhaltensbasierter Features (Anwesenheit, Buchungsmuster, Kursfortschritt)
2.3 Evaluieren d. Feature-Qualität mittels Korrelationsanalyse & Varianzanalyse

3 ML-basierte Beteiligungsdrift-Prognose
3.1 Trainieren v. Prognosemodellen (Random Forest, Gradient Boosting, logist. Regression)
3.2 Evaluieren d. Modelle mittels Kreuzvalidierung & Benchmarking
3.3 Erweitern d. Prognosehorizonts (7 Tage → 4 Wochen → 3 Monate)

4 Probabilist. Kanalwirkungsmodell
4.1 Implementieren d. Markov-Ketten-Modells für Kanalübergänge
4.2 Entwickeln d. Shapley-Wert-Dekomposition zur Kanalwirkungsquantifizierung
4.3 Benchmarken gegen d. regelbasierte Referenzmodell (Vergleichsanalyse)

5 Nudging-Architektur & Mobile Integration
5.1 Entwerfen d. verhaltensbasierten Nudging-Logik (regelbasierte Interventionsableitung)
5.2 Entwickeln d. mobilen Applikation zur Interventionsauslieferung
5.3 Evaluieren d. Nudging-Wirkung auf Engagement-Kenngrößen (statist. Hypothesentests)
