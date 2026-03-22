# Berater-Analyse: KI-gestützte Modellierung von Lernverhalten & Beteiligungsdrift zur datenbasierten Optimierung individueller Lernpfade im Online-Sprachunterricht

## Sofort-Handlungsbedarf (Top 3)

1. **Vorhabenzeitraum exakt klären:** Das Transkript nennt "2021" als Start, aber der exakte Monat und das Enddatum sind unklar. Der Berater muss den genauen Zeitraum mit dem Kunden abstimmen (z.B. Jan 2021 – Jul 2022). Dies betrifft alle Sektionen.

2. **Konkrete ML-Bibliotheken/Frameworks bestätigen:** Samy erwähnte "Python" und "ML libraries", konnte sich aber nicht an den genauen AWS-Service erinnern. Der Berater sollte klären: Scikit-learn? XGBoost? SageMaker? Dies stärkt die Arbeiten-Sektion und den Arbeitsplan erheblich.

3. **DOI für Neuartigkeits-Sektion recherchieren:** Aktuell fehlt ein DOI-Verweis. Eine Literaturstelle zu Retentionsproblematik im Online-Sprachlernen oder zu ML-basierter Abbruchprognose im EdTech-Bereich würde die Neuartigkeitsargumentation deutlich stärken.

## Forschungsnarrativ

1. **WISSENSFRAGE:** Ist es möglich, dass ML-basierte verhaltensmodellierung auf Basis individueller Subskriptionsketten Beteiligungsdrift in lehrergestütztem Live-Gruppensprachunterricht zuverlässig prognostizieren und durch automatisierte Interventionen abschwächen kann?

2. **WARUM OFFEN:** Zum Vorhabenbeginn 2021 existierten keine integrierten Verfahren für diesen spezifischen Kontext. Bestehende Plattformen (Duolingo, Babbel, Busuu) adressieren Selbstlernformate; kohortenbasierte Retentionsmodelle liefern keine individuellen Prognosen. Die Kombination aus Drift-Prognose, Kanalwirkungsanalyse und Nudging in einem geschlossenen Regelkreis war für lehrergestützten Gruppenunterricht unerforscht.

3. **UNSICHERHEIT:** Unsicher ist, ob die nicht-linearen Zustandsübergänge in den Subskriptionsketten (Pausen, Reaktivierungen, Formatwechsel) sich in standardisierten Features abbilden lassen UND ob ein probabilistisches Kanalwirkungsmodell ohne unabhängige Grundwahrheit valide Kanaleffekte isolieren kann.

## Simulierte Nachforderung

**Frage 1:** "Bitte legen Sie das Vorhabenziel, dessen Anforderungen und Charakteristiken konkret und aussagekräftig dar. Unterlegen Sie dies bitte mit Angaben zu angestrebten Parametern sowie Lösungsansätzen/Modellen/Methoden."
- Status: Abgedeckt
- Der Antrag nennt konkrete Modelle (Random Forest, Gradient Boosting, logist. Regression, Markov-Ketten, Shapley-Wert), Parameter (Präzision >80 %, Zeithorizonte 7 Tage/4 Wochen/3 Monate) und den methodischen Aufbau.

**Frage 2:** "Die Abgrenzung zum Stand der Technik in Ihrer Branche bzw. zu bestehenden Produkten ist unzureichend beschrieben."
- Status: Abgedeckt
- Bestehende Plattformen (Duolingo, Babbel, Busuu) und kohortenbasierte Retentionsmodelle werden explizit genannt und deren Limitierungen beschrieben.

**Frage 3:** "Beschreiben Sie bitte aussagekräftig technische und/oder wissenschaftliche Risiken, die über methodeninhärente Risiken hinausgehen."
- Status: Teilweise
- Handlungsempfehlung: Risiko 1 (Feature-Repräsentation bei Zustandsübergängen) ist stark und projektspezifisch. Risiko 2 (fehlende Grundwahrheit bei Kanalwirkung) könnte als methodeninhärent gewertet werden. Der Berater sollte prüfen, ob hier ein projektspezifischerer Aspekt betont werden kann — z.B. der Konflikt zwischen der Markov-Annahme (Gedächtnislosigkeit) und den tatsächlich langfristigen Kanalwirkungsketten im EdTech-Bereich.

**Frage 4:** "Bitte führen Sie aus, inwieweit die Auftragnehmer Tätigkeiten durchführen, die zur Zielerreichung des Vorhabens beitragen."
- Status: Teilweise
- Handlungsempfehlung: Im Transkript wird der Vendor "Incremental" für das Incrementality-Projekt erwähnt. Falls dieser im Antrag aufgenommen wird, muss dessen FuE-Beitrag zur Wissenslücke dargestellt werden. Aktuell ist Auftragsforschung nicht thematisiert — der Berater muss klären, ob externe Auftragnehmer beteiligt waren.

**Frage 5:** "Welche eigene Problemlösungsstrategie wird im Vorhaben verfolgt?"
- Status: Abgedeckt
- Beide Risiken enthalten Problemlösungsstrategien (iterative Feature-Konstruktion, algorithmisches Benchmarking).

## Qualitätsbewertung pro Sektion

### Ziel-Sektion
- **Stärke:** Klare Eröffnung in Domänensprache, hohe Methodendichte, ergebnisoffene Formulierung
- **BSFZ-Risiko:** "Präzision >80 %" könnte als Produktziel statt als Forschungsfrage gelesen werden
- **Berater prüfen:** Ggf. umformulieren zu "ob eine Präzision von >80 % unter den gegebenen Bedingungen erreichbar ist"

### Neuartigkeit-Sektion
- **Stärke:** Zeitstempel ("Zum Vorhabenbeginn 2021"), konkrete SdT-Benennung, klare Bullet-Struktur
- **BSFZ-Risiko:** Fehlender DOI
- **Berater prüfen:** DOI recherchieren und ergänzen

### Arbeiten-Sektion
- **Stärke:** Klarer Temporalmarker-Rhythmus, Methoden durchgehend benannt
- **BSFZ-Risiko:** Gering
- **Berater prüfen:** Ggf. konkreteren Bezug zu den APs herstellen

### Risiko-Sektion
- **Stärke:** Zwei klar getrennte Risikoblöcke, Problemlösungsstrategien vorhanden
- **BSFZ-Risiko:** Risiko 2 könnte als methodeninhärent eingestuft werden
- **Berater prüfen:** Projektspezifischere Formulierung für Risiko 2 erwägen

## Offene Annahmen

- [ ] Exakter Vorhabenzeitraum (Start- und Endmonat) — betrifft: alle Sektionen
- [ ] Konkrete ML-Bibliotheken/Frameworks (Scikit-learn? XGBoost? SageMaker?) — betrifft: Arbeiten, Arbeitsplan
- [ ] Abbruchrate 13 % als Ausgangswert bestätigen — betrifft: Ziel-Sektion
- [ ] Klassenverteilung 85/15 bestätigen — betrifft: Arbeitsplan AP3.1
- [ ] War das Incrementality-Projekt (Vendor: Incremental) Teil des Vorhabens? — betrifft: Auftragsforschung
- [ ] Existieren DOIs/Publikationen zum Forschungsbedarf? — betrifft: Neuartigkeit
- [ ] Anzahl der beteiligten Mitarbeiter bestätigen (2 Data Scientists + Team) — betrifft: Zeitplanung
- [ ] Wurde die mobile App tatsächlich als Prototyp umgesetzt oder nur konzipiert? — betrifft: AP5
- [ ] Status des Churn-Modells: Wurde es in Produktion genommen bevor das Team abgebaut wurde? — betrifft: Risiko-Argumentation

## Zeichenauslastung

| Sektion | Zeichen | Limit | Auslastung |
|---------|---------|-------|------------|
| Titel A | 145 | 150 | 97% |
| Ziel A | 1491 | 1.500 | 99% |
| Neuartigkeit A | 497 | 500 | 99% |
| Arbeiten A | 943 | 1.000 | 94% |
| Risiko A | 974 | 1.000 | 97% |
| Titel B | 148 | 150 | 99% |
| Ziel B | 1421 | 1.500 | 95% |
| Neuartigkeit B | 495 | 500 | 99% |
| Arbeiten B | 972 | 1.000 | 97% |
| Risiko B | 949 | 1.000 | 95% |
