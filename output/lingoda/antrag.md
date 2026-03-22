# ML-basiertes adaptives Lern-Ökosystem zur datengetriebenen Abbruchprognose & Interventionssteuerung im Online-Spracherwerb

## Was ist das Ziel Ihres Vorhabens? Welche Herausforderung oder Problemstellung soll mit dem Vorhaben gelöst bzw. welche Wissenslücke soll mit dem Vorhaben geschlossen werden?

Im Online-Spracherwerb fehlen gesicherte Erkenntnisse darüber, wie heterogene Lernverhaltensdaten (Unterrichtsteilnahme, Übungsfrequenz, Pausenverhalten, Abonnementstatus) so modelliert werden können, dass individualisierte Interventionen zur Reduktion v. Beteiligungsdrift bei ernsthaften Sprachlernenden zuverlässig ableitbar sind. Bestehende Ansätze (Duolingo, Babbel, Busuu) nutzen gamifizierte Mikrolern-Impulse für Gelegenheitslernende; kohortenbasierte Verbleibsmodelle können individuelle Risikomuster nicht prognostizieren. Stationäre Sprachschulen (Goethe-Institut, Berlitz) bieten keine datengetriebene Verhaltensanalyse.
Ziel war es zu untersuchen, ob ein adaptives Lern-Ökosystem aus (1) ML-basierter Abbruchprognose (Gradient Boosting, Random Forest) auf rekonstruierten Subskriptionsketten, (2) verhaltensbasiertem Nudging-Framework zur individualisierten Interventionssteuerung & (3) probabilistischer Kanalwirkungsanalyse (Markov-Ketten, Shapley-Wert-Dekomposition) die Verbleibswahrscheinlichkeit signifikant verbessern kann. Datengrundlage: ca. 40.000 Klassen/Monat, vier Sprachen, globaler Nutzerstamm. Die Subskriptionsdaten mussten in analysefähige Verlaufsketten transformiert werden (Pausen, Reaktivierungen, Testzeiträume), da keine entsprechende Datenstruktur existierte. Angestrebt wurden Erkenntnisse, ob & unter welchen Bedingungen ML-Prognosemodelle auf rekonstruierten Verhaltensdaten handlungsrelevante Interventionssignale erzeugen können.

(1.472 / 1.500 Zeichen)

## Inwieweit hebt sich das angestrebte Produkt, Verfahren oder die Dienstleistung vom Stand der Technik ab?

Zum Vorhabenbeginn 2021 existierten keine Verfahren zur ML-basierten Abbruchprognose für ernsthafte Online-Sprachlernende m. flexiblen Subskriptionsmodellen. Lösungen (Duolingo, Babbel, Busuu) adressierten Gelegenheitslernende; kohortenbasierte Modelle boten keine individuelle Prognose.
Neu:
- ML-Abbruchprognose auf rekonstruierten Subskriptionsketten
- Verhaltensbasiertes Nudging-Framework
- Probabilist. Kanalwirkungsanalyse (Markov, Shapley-Wert)
- ELT-basierte Echtzeitdatenverfügbarkeit

(494 / 500 Zeichen)

## Welche Arbeiten werden durchgeführt, um der zuvor benannten Herausforderung oder Problemstellung zu begegnen bzw. um die Wissenslücke zu schließen?

Zunächst wurde die ETL-Datenplattform zu einer ELT-Architektur transformiert, heterogene Rohdaten in einem Data Lake konsolidiert & über deklarative Transformationsschichten harmonisiert, um Echtzeitverfügbarkeit für nachgelagerte Analysen zu gewährleisten. Darauf wurden Subskriptionsketten rekonstruiert, die Pausen, Reaktivierungen & Testzeiträume abbilden – eine Struktur, die in d. Produktionsdatenbank nicht existierte. Nun wurde ein ML-basiertes Abbruchprognosemodell entwickelt: Klassifikationsverfahren (Random Forest, Gradient Boosting, Logistic Regression) wurden auf histor. Verhaltensdaten trainiert & mittels Kreuzvalidierung evaluiert. Parallel wurde eine probabilist. Kanalwirkungsanalyse (Markov-Ketten & Shapley-Wert-Dekomposition) implementiert, um regelbasierte Zuordnungsmodelle durch datengetriebene Verfahren zu ersetzen. Final wurde ein Nudging-Framework konzipiert, das Prognoseergebnisse in individualisierte Interventionssignale überführt & deren Wirksamkeit evaluiert.

(996 / 1.000 Zeichen)

## Welche wissenschaftlichen, technischen und/oder methodischen Unsicherheiten bestehen bei der Bearbeitung der Herausforderung oder Problemstellung?

Unklar ist, ob ML-Klassifikationsverfahren (Random Forest, Gradient Boosting) auf rekonstruierten Subskriptionsketten m. starkem Klassenungleichgewicht (15% Abbrüche) präzise Interventionssignale erzeugen, wenn Verhaltensmuster durch flexible Subskriptionsmodelle (Pausen, Reaktivierungen) nichtlinear verlaufen. Dem wurde m. domänenspez. Feature Engineering, Resampling & Schwellenwertoptimierung entgegengewirkt. Dennoch könnte d. Vorhaben scheitern, wenn d. Subskriptionsketten d. Lernverläufe nicht valide abbilden & d. Prognosequalität unter Realbedingungen keine handlungsrelevante Differenzierung ermöglicht.
Offen ist, ob d. probabilist. Kanalwirkungsanalyse (Markov-Ketten, Shapley-Wert) ohne verifizierbare Referenzzuordnung (fehlende Ground Truth) konvergente & interpretierbare Ergebnisse liefern kann. D. Kopplung datengetriebener m. regelbasierter Attribution erzeugt ein Spannungsfeld zw. Modellkomplexität & Erklärbarkeit, dessen Auflösung vorab nicht gesichert ist.

(982 / 1.000 Zeichen)

## Schlagwörter

1. Maschinelles Lernen
2. Abbruchprognose
3. Online-Spracherwerb
4. Verhaltensmodellierung
5. Nudging-Framework
6. Kanalwirkungsanalyse
7. Markov-Ketten
8. Subskriptionsketten-Rekonstruktion
9. ELT-Datenarchitektur
10. Probabilistische Attribution

## Arbeitspakete (Kurzfassung)

1 Datenplattform-Transformation & Echtzeitdatenverfügbarkeit
1.1 Transformieren d. ETL-Architektur zu ELT m. Data Lake (Datenarchitektur-Migration)
1.2 Implementieren deklarativer Transformationsschichten (SQL-basierte Modellierung)
1.3 Validieren d. Datenqualität & Verfügbarkeit ggü. Produktionssystem (statist. Vergleichsanalyse)

2 Subskriptionsketten-Rekonstruktion & Feature Engineering
2.1 Rekonstruieren v. Subskriptionsverläufen aus heterogenen Quelldaten (Datenmodellierung)
2.2 Entwickeln domänenspez. Features (Pausen, Reaktivierungen, Testzeiträume) (Feature Engineering)
2.3 Validieren d. Verlaufsketten gegen manuelle Stichproben (statist. Validierung)

3 ML-basierte Abbruchprognose
3.1 Trainieren & Benchmarken v. Klassifikationsverfahren (Random Forest, Gradient Boosting, Log. Regression) (Modellselektion)
3.2 Evaluieren m. Kreuzvalidierung & Schwellenwertoptimierung bei Klassenungleichgewicht (statist. Evaluation)
3.3 Testen d. Prognosemodells unter Realbedingungen (experimentelle Validierung)

4 Probabilistische Kanalwirkungsanalyse
4.1 Implementieren einer Markov-Ketten-basierten Kanalattribution (probabilist. Modellierung)
4.2 Entwickeln einer Shapley-Wert-Dekomposition zur Kanalgewichtung (spieltheoret. Analyse)
4.3 Evaluieren ggü. regelbasiertem Referenzmodell (Vergleichsanalyse)

5 Nudging-Framework & Interventionssteuerung
5.1 Konzipieren d. verhaltensbasierten Interventionslogik auf Basis d. Prognosemodelle (Systemarchitektur)
5.2 Entwickeln mobiler Auslieferungskomponenten für Übungsinhalte (Prototypentwicklung)
5.3 Evaluieren d. Interventionswirksamkeit auf Verbleibswahrscheinlichkeit (experimentelle Evaluation)
