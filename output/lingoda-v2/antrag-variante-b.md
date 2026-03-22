# Multimodale verhaltensbezogene Modellierung zur prädiktiven Steuerung individueller Lernpfade & Drift-Erkennung im digitalen Gruppensprachunterricht

> **Variante B — Kreatives Reframing (zur Diskussion)**
> Diese Variante geht über das im Transkript Belegbare hinaus. Alle Stellen mit kreativer Freiheit sind mit [BERATER-ANNAHME] markiert.

## Was ist das Ziel Ihres Vorhabens? Welche Herausforderung oder Problemstellung soll mit dem Vorhaben gelöst bzw. welche Wissenslücke soll mit dem Vorhaben geschlossen werden?

Langfristiger Online-Sprachunterricht mit Live-Lehrkräften konfrontiert Lernende mit einem Zusammenspiel aus Motivationsdynamik, kognitiver Belastung & sozialer Kohäsion im Gruppenformat. Bis zu 60 % brechen innerhalb d. ersten Monate ab — ein Phänomen, das als Beteiligungsdrift beschrieben wird & sich einer einfachen kausalen Zuordnung entzieht. Bestehende adaptive Lernsysteme (Duolingo, Babbel, Busuu) adressieren ausschließlich Selbstlernformate; kohortenbasierte Retentionsmodelle (Standard 2021) bilden Durchschnittsverläufe ab, ohne individuelle Verhaltensmuster zu erfassen.
Ziel war es zu untersuchen, ob ein multimodales Modellierungsframework — bestehend aus (1) einem verhaltensontologischen Zustandsmodell [BERATER-ANNAHME: Ontologie-Modellierung individueller Lernzustände], das Subskriptionsketten als gerichteten Graphen formalisiert, (2) einem ML-Ensemble (Random Forest, Gradient Boosting, logist. Regression) zur prädiktiven Drift-Erkennung, (3) einem probabilist. Kanalwirkungsmodell (Markov-Ketten, Shapley-Wert-Dekomposition) & (4) einer regelbasierten Nudging-Engine m. Rückkopplungsschleife [BERATER-ANNAHME: Closed-Loop-Feedback] — Beteiligungsdrift individuell prognostizieren & durch gezielte Interventionen abschwächen kann.
Angestrebt wurden Erkenntnisse darüber, ob verhaltensontologische Zustandsmodellierung die prädiktive Güte ggü. rein statistischen Ansätzen signifikant steigern kann.

(1421 / 1.500 Zeichen)

## Inwieweit hebt sich das angestrebte Produkt, Verfahren oder die Dienstleistung vom Stand der Technik ab?

Zum Vorhabenbeginn 2021 existierten weder verhaltensontolog. Zustandsmodelle für Lernverläufe im Live-Gruppenformat noch Regelkreise aus Prognose, Intervention & Wirkungsmessung. Plattformen (Duolingo, Babbel, Busuu) adressieren Selbstlern.
Neu:
- Verhaltensontolog. Zustandsmodell als gerichteter Graph [BERATER-ANNAHME]
- ML-Ensemble zur Drift-Erkennung auf Subskriptionsketten
- Probabilist. Kanalwirkungsmodell m. Shapley-Dekomposition
- Closed-Loop-Nudging m. Rückkopplung [BERATER-ANNAHME]

(495 / 500 Zeichen)

## Welche Arbeiten werden durchgeführt, um der zuvor benannten Herausforderung oder Problemstellung zu begegnen bzw. um die Wissenslücke zu schließen?

Zunächst wurde ein verhaltensontologisches Zustandsmodell [BERATER-ANNAHME] entworfen, das individuelle Lernverläufe als gerichteten Graphen formalisiert (Zustände: aktiv, pausiert, reaktiviert, abgebrochen; Kanten: gewichtete Übergangswahrscheinlichkeiten). Parallel wurde d. ETL-Plattform zu einem ELT-Paradigma transformiert & heterogene Quellsysteme (Lernplattform, Buchungssystem, CRM) semantisch harmonisiert. Darauf wurden Subskriptionsketten als Feature-Vektoren extrahiert & ein ML-Ensemble (Random Forest, Gradient Boosting, logist. Regression) zur Beteiligungsdrift-Prognose trainiert & mittels Kreuzvalidierung evaluiert. Parallel wurde ein probabilist. Kanalwirkungsmodell (Markov-Ketten, Shapley-Wert-Dekomposition) entwickelt & gegen d. regelbasierte Referenz benchmarked. Final wurde eine Closed-Loop-Nudging-Engine [BERATER-ANNAHME] implementiert, die Prognose-Outputs in individualisierte Interventionen überführt & deren Wirkung ins Modell zurückspeist.

(972 / 1.000 Zeichen)

## Welche wissenschaftlichen, technischen und/oder methodischen Unsicherheiten bestehen bei der Bearbeitung der Herausforderung oder Problemstellung?

Unklar ist, ob d. verhaltensontologische Zustandsmodellierung [BERATER-ANNAHME] individuelle Lernverläufe differenziert abbilden kann: Nicht-lineare Zustandsübergänge (Pausen, Reaktivierungen, Formatwechsel) könnten sich einer formalen Graphrepräsentation entziehen. Es besteht d. Risiko eines Paradigmenkonflikts — während d. Ontologie konsistente Zustandsklassifikationen erzwingt, erzeugt d. ML-Ensemble graduelle Wahrscheinlichkeitsverteilungen. Die Kopplung beider Paradigmen könnte zu systematischen Fehlklassifikationen führen, die erst im Zusammenspiel auftreten.
Ein zweites Risiko ist paradoxe Rückkopplung [BERATER-ANNAHME]: Erfolgreiche Nudging-Interventionen verändern d. Verhaltensmuster, sodass d. Prognosemodell auf veralteten Verteilungen trainiert wurde. Es ist offen, ob d. Closed-Loop-System konvergiert oder ob Interventionseffekte d. Datengrundlage so verschieben, dass d. Modell seine Prognosequalität systematisch untergräbt.

(949 / 1.000 Zeichen)

## Schlagwörter

1. Verhaltensontologie
2. Beteiligungsdrift-Prognose
3. ML-Ensemble
4. Markov-Ketten
5. Shapley-Wert-Dekomposition
6. Closed-Loop-Nudging
7. Subskriptionsketten
8. Sprachlernplattform
9. ELT-Datenplattform
10. Prädiktive Lernpfadsteuerung

## Arbeitspakete (Kurzfassung)

1 Verhaltensontologische Zustandsmodellierung [BERATER-ANNAHME]
1.1 Entwerfen d. Ontologie-Schemas für Lernzustände (Graphmodellierung)
1.2 Formalisieren v. Subskriptionsketten als gerichtete Graphen (Zustandsübergänge)
1.3 Validieren d. Ontologie gegen reale Nutzungsdaten (semantische Konsistenzprüfung)

2 Datentransformation & Plattformaufbau
2.1 Transformieren d. ETL-Pipeline zu ELT-Architektur (deklarative Modellierung)
2.2 Implementieren d. Data Lake m. semantischer Quellenharmonisierung
2.3 Aufbauen d. Transformationsschicht (SQL/Jinja-Templates, Datenqualitätsprüfung)

3 ML-basierte Beteiligungsdrift-Prognose
3.1 Extrahieren ontologiegestützter Feature-Vektoren aus Subskriptionsketten
3.2 Trainieren d. ML-Ensembles (Random Forest, Gradient Boosting, logist. Regression)
3.3 Evaluieren & Erweitern d. Prognosehorizonts (7 Tage → 4 Wochen → 3 Monate)

4 Probabilist. Kanalwirkungsmodell
4.1 Implementieren d. Markov-Ketten-Modells für Kanalübergänge
4.2 Entwickeln d. Shapley-Wert-Dekomposition zur Wirkungsquantifizierung
4.3 Benchmarken gegen d. regelbasierte Referenzmodell (Vergleichsanalyse)

5 Closed-Loop-Nudging-Engine [BERATER-ANNAHME]
5.1 Entwerfen d. Interventionslogik m. Rückkopplungsschleife
5.2 Implementieren d. mobilen Auslieferungsschicht für Interventionen
5.3 Evaluieren d. Nudging-Wirkung & Konvergenzverhalten (statist. Hypothesentests)
