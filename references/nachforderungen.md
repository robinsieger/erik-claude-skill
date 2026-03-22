# Nachforderungs-Vermeidung: Anti-Pattern-Katalog

Dieses Dokument destilliert aus realen Nachforderungen der BSFZ die Muster, die zu Rückfragen führen, und wie man sie vermeidet. Die BSFZ fordert grundsätzlich nur einmal nach — bei erneut unzureichender Antwort wird abgelehnt.

---

## Allgemeine Nachforderungs-Trigger

Die BSFZ fordert nach, wenn Angaben zu einem Kriterium "erkennbar fehlerhaft oder unvollständig" sind. Ist mindestens ein Kriterium unabhängig von einer Nachforderung unzweifelhaft nicht erfüllt, wird sofort abgelehnt (keine Nachforderung zu anderen Kriterien).

---

## Neuartigkeit: Häufigste Fehler

### Fehler 1: Unzureichende Abgrenzung zum Stand der Technik

**Trigger-Formulierung der BSFZ:**
> "Die Abgrenzung zum Stand der Technik in Ihrer Branche bzw. zu bestehenden Produkten, Verfahren oder Dienstleistungen Ihres Unternehmens ist unzureichend beschrieben."

**Was fehlt:** Konkrete Benennung, was es am Markt/in der Forschung bereits gibt UND warum genau es nicht ausreicht.

**Vermeidung:** In der Neuartigkeits-Sektion explizit bestehende Ansätze/Tools benennen (mit Namen, nicht "bestehende Lösungen"), deren spezifische Limitierungen aufzeigen, und erklären, was der eigene Ansatz anders/besser macht.

### Fehler 2: Keine konkreten Modelle/Methoden benannt

**Trigger-Formulierung der BSFZ:**
> "Welcher Verarbeitungs-/Prozessschritt wird konkret durch die KI übernommen und mit welchem Ansatz/Modell soll der Schritt umgesetzt werden? Wie sehen die Input-Daten und der erwünschte Output aus?"

**Was fehlt:** Konkrete Algorithmen, Frameworks, Datenflüsse.

**Vermeidung:** Für jeden Forschungsschritt explizit benennen: (a) welche Methode/welches Verfahren, (b) welche Eingangsgrößen/Daten/Materialien, (c) welches erwünschte Ergebnis. Beispiele:
- *KI:* Nicht "KI-basierte Analyse", sondern "LSTM-basierte Zeitreihenprognose auf Basis historischer Sensordaten zur Vorhersage von Zustandsgrößen mit Konfidenzintervallen"
- *Maschinenbau:* Nicht "innovatives Fertigungsverfahren", sondern "Laserstrahlschweißen unter Schutzgas mit adaptiver Parameterregelung auf Basis thermographischer Inline-Messung zur Nahtgeometrie-Kontrolle"
- *Chemie:* Nicht "neuartige Synthese", sondern "Sol-Gel-Synthese mit kontrollierter Hydrolysegeschwindigkeit zur Erzeugung mesoporöser Titanoxid-Dünnschichten mit definierter Porengrößenverteilung (5-20 nm)"

### Fehler 3: Lösungsweg "im Stand der Technik realisierbar"

**Trigger-Formulierung der BSFZ:**
> "Vergleichbare Lösungen existieren und der gezeichnete Lösungsweg konnte auch zum Vorhabenbeginn mit Instrumenten im Stand der Technik bzw. notwendiger fachlicher Sorgfalt realisiert werden."

**Was fehlt:** Der Antrag hat nicht klar gemacht, warum bestehende Instrumente NICHT ausreichen.

**Vermeidung:** Beim Beschreiben des eigenen Ansatzes explizit benennen, welche Aspekte über bestehende Werkzeuge/Methoden hinausgehen. "Im Gegensatz zu [bestehender Ansatz], der [Limitation], erfordert unser Vorhaben [neue Kombination/Methode], weil [Grund]."

### Fehler 4: Fehlende Konkretisierung des Lösungsansatzes

**Trigger-Formulierung der BSFZ:**
> "Bitte legen Sie das Vorhabenziel, dessen Anforderungen und Charakteristiken konkret und aussagekräftig dar. Unterlegen Sie dies bitte mit Angaben zu angestrebten Parametern sowie Lösungsansätzen/Modellen/Methoden, anzuwendenden Technologien und softwareseitigen Modulen."

**Vermeidung:** In der Ziel-Sektion technologische Bausteine mit Namen benennen, Parameter quantifizieren, Module/Komponenten aufzählen.

---

## Risiko: Häufigste Fehler

### Fehler 1: Risiken ohne Bezug zum Lösungsweg

**Trigger-Formulierung der BSFZ:**
> "Bitte gehen Sie genauer auf die Risiken und Herausforderungen ein und erläutern Sie, inwiefern diese nicht mit etablierten Lösungsansätzen zu lösen sind."

**Was fehlt:** Die Risiken schweben frei im Raum, ohne Bezug zu den konkreten Arbeitsschritten.

**Vermeidung:** Jedes Risiko an einen konkreten Arbeitsschritt/Methode binden: "Bei der Kopplung von [Prognosemodell] und [Entscheidungsmodell] (vgl. AP3.3) ist unklar, ob..."

### Fehler 2: Zirkelschluss-Risiken

**Trigger-Formulierung der BSFZ:**
> "[X, Y, Z] stellen Vorhabenprämissen dar, die zum Vorhabenbeginn als lösbar anzunehmen sind, sodass hier ein Zirkelschluss vorliegt."

**Was das bedeutet:** Wenn das Risiko eigentlich eine Grundannahme des Vorhabens ist ("es könnte sein, dass unsere Grundidee nicht funktioniert"), ist das kein anerkanntes Risiko — es ist eine Prämisse.

**Vermeidung:** Risiken nicht auf der Ebene "Funktioniert der Grundansatz?" formulieren, sondern auf der Ebene "WIE funktioniert er unter realen Bedingungen?" — z.B. Datenqualität, Modellkopplung, Skalierung, unerwartete Interaktionseffekte zwischen Komponenten.

### Fehler 3: Methodeninhärente Standardrisiken

**Trigger-Formulierung der BSFZ:**
> "Beschreiben Sie bitte aussagekräftig technische und/oder wissenschaftliche Risiken, die über methodeninhärente Risiken bzw. unvermeidbare Standardrisiken hinausgehen."

**Was das bedeutet:** Standardrisiken jeder Disziplin werden nicht anerkannt. Beispiele für methodeninhärente Risiken, die die BSFZ NICHT akzeptiert:
- *KI/Software:* "Overfitting", "Klassenungleichgewicht", "fehlende Ground-Truth", "unvollständige Daten"
- *Maschinenbau:* "Materialtoleranzen", "Fertigungsstreuung" (als generische Aussage)
- *Chemie:* "Nebenreaktionen könnten auftreten", "Ausbeute könnte niedrig sein"
- *Allgemein:* "Es könnten mehr Tests nötig sein als geplant"

**Vermeidung:** Risiken müssen projektspezifisch sein. Beispiele:
- *KI:* Nicht "Daten könnten fehlerhaft sein", sondern "Die heterogenen Datenformate könnten bei der ontologiegestützten Harmonisierung zu semantischen Konflikten führen (Ontologie-Matching-Accuracy <0,85)"
- *Maschinenbau:* Nicht "Der Prototyp könnte nicht funktionieren", sondern "Die FEM-simulierten Festigkeitswerte basieren auf idealisierten Materialparametern; unter realen Fertigungsbedingungen könnten streuungsbedingte Werkstoffinhomogenitäten zu Spannungskonzentrationen führen, die die Dauerfestigkeit um >30% reduzieren"
- *Chemie:* Nicht "Die Reaktion könnte nicht funktionieren", sondern "Die im Labormaßstab erzielte Umsetzungsrate lässt sich nicht ohne Weiteres auf den Pilotmaßstab übertragen; veränderte Mischungsverhältnisse und Temperaturgradienten könnten die Reaktionskinetik destabilisieren"

---

## Planmäßigkeit: Häufigste Fehler

### Fehler 1: Arbeitspakete zu vage

**Trigger-Formulierung der BSFZ:**
> "Bitte beschreiben Sie die durchgeführten Entwicklungstätigkeiten im Arbeitspaket [X] konkreter."

**Vermeidung:** Jedes Arbeitspaket muss konkrete Tätigkeiten mit Methoden beschreiben. Beispiele:
- *KI:* Nicht "Entwicklung eines Modells", sondern "Trainieren eines LSTM-basierten Zeitreihenmodells auf historischen Sensordaten zur Vorhersage terminaler Kennwerte"
- *Maschinenbau:* Nicht "Konstruktion eines Prototyps", sondern "Iterative Auslegung einer fluidisch-thermischen Kühlstruktur mittels CFD-Simulation und experimenteller Validierung im Prüfstand (Wärmebildkamera, Drucksensoren)"
- *Biotech:* Nicht "Durchführung von Tests", sondern "Evaluierung der enzymatischen Detektionsmethode an 200 klinischen Proben mittels ELISA mit definierter Sensitivitätsschwelle (LOD <5 ng/ml)"

### Fehler 2: Fehlender detaillierter Arbeitsplan

**Vermeidung:** Immer einen detaillierten Arbeitsplan als Anlage mitliefern (Gantt-Chart oder tabellarisch). Die BSFZ bewertet diese Anlage explizit und referenziert sie im Bescheid.

---

## Auftragnehmer: Häufigste Fehler

**Trigger-Formulierung der BSFZ:**
> "Bitte führen Sie aus, inwieweit die Auftragnehmer Tätigkeiten durchführen, die zur Zielerreichung des Vorhabens beitragen. Welchen konkreten Beitrag leisten die einzelnen Auftragnehmer, um die Wissenslücke in der Umsetzung des Vorhabens zu schließen?"

**Vermeidung:** Für jeden Auftragnehmer: (a) konkrete FuE-Tätigkeit benennen, (b) Bezug zum Vorhabenziel herstellen, (c) erklären, warum diese Tätigkeit zur Schließung der Wissenslücke beiträgt. "Routine-Implementierung" oder "Programmierung nach Spezifikation" sind keine FuE-Tätigkeiten.

---

## Muster erfolgreicher Nachforderungs-Antworten

Aus den analysierten Nachforderungs-Antworten, die zu positiven Bescheiden geführt haben:

### Muster: Input-Output-Methode-Triade
Auf die Frage "Was konkret tut die KI?" funktioniert diese Struktur:
1. **Input-Daten** konkret benennen (Datentypen, Quellen, Format)
2. **Verarbeitungsmethode** konkret benennen (Algorithmus, Modelltyp, Framework)
3. **Output** konkret benennen — und klar machen, dass der Output kein fertiges Produkt ist, sondern ein "analytisch-prognostisches Modellresultat" (Erkenntnis, nicht Produkt)

### Muster: Abgrenzung durch Aufzählung
"Ansätze personalisierter [X] gliedern sich wie folgt: 1. [Kategorie A], 2. [Kategorie B], 3. [Kategorie C]. Keiner der Ansätze ist in der Lage, [spezifische Anforderung] zu erfüllen."

### Muster: Risiko mit Problemlösungsstrategie (PFLICHT)
Die BSFZ fragt bei Nachforderungen immer: "Welche eigene Problemlösungsstrategie wird im Vorhaben verfolgt?" Risiken ohne Gegenstrategie provozieren Nachforderungen.

Aufbau:
1. "Es ist unklar, ob [konkretes Problem bei konkretem Arbeitsschritt]."
2. "Dem wollen wir mit [Strategie A], [Strategie B] und [Strategie C] entgegenwirken."
3. "Dennoch könnte das Vorhaben scheitern, wenn [konkrete Bedingung eintritt]."

Alle drei Teile müssen vorhanden sein. Der dritte Teil ist entscheidend: Er zeigt, dass trotz Strategie echtes Scheitern möglich ist.

### Muster: Paradigmen-Spannungsfeld als Risiko
Der Gutachter erkennt echte Forschung, wenn zwei gegensätzliche Anforderungen oder Ansätze kombiniert werden und deren Zusammenspiel unsicher ist:
- *KI:* "Während LLMs Kontexthypothesen probabilistisch erzeugen, prüft die Ontologie deterministische Konsistenzregeln. Es ist unklar, ob sich diese beiden Paradigmen stabil koppeln lassen."
- *Maschinenbau:* "Die FEM-Simulation geht von idealisierten Materialparametern aus, reale Werkstoffe zeigen jedoch streuungsbedingte Abweichungen. Es ist unklar, ob die simulierten Festigkeitswerte unter realen Fertigungsbedingungen reproduzierbar sind."
- *Chemie/Biotech:* "Die enzymatische Umsetzungsrate im Labormaßstab lässt sich nicht ohne Weiteres auf den Pilotmaßstab übertragen. Unklar ist, ob die Reaktionskinetik bei veränderten Mischungsverhältnissen und Temperaturgradienten stabil bleibt."

Solche Spannungsfelder sind starke Forschungssignale und sollten, wo vorhanden, immer als Risiko benannt werden.

---

## Qualitäts-Checkliste: Nachforderungs-Resilienz

Prüfe jeden Antrag gegen diese Fragen, bevor er als fertig gilt:

**Neuartigkeit:**
- [ ] Sind bestehende Ansätze/Tools mit Namen benannt?
- [ ] Sind deren spezifische Limitierungen beschrieben?
- [ ] Ist klar, was der eigene Ansatz anders/besser macht?
- [ ] Sind konkrete Modelle/Algorithmen/Methoden benannt?
- [ ] Ist der Antrag klar von Routinearbeit abgegrenzt?

**Risiko:**
- [ ] Hat jedes Risiko einen Bezug zu einem konkreten Arbeitsschritt?
- [ ] Sind die Risiken projektspezifisch (nicht methodeninhärent)?
- [ ] Liegt kein Zirkelschluss vor (Risiko ≠ Prämisse)?
- [ ] Ist erklärt, WARUM das Risiko technisch besteht?
- [ ] Könnte das Risiko den Lösungsansatz zum Scheitern bringen?
- [ ] Enthält jedes Risiko eine Problemlösungsstrategie UND erklärt, warum es trotzdem scheitern könnte?
- [ ] Sind die Risiken als Forschungsfragen formuliert (nicht als KPI-Ziele)?

**Planmäßigkeit:**
- [ ] Beschreiben die Arbeitspakete konkrete Tätigkeiten mit Methoden?
- [ ] Liegt ein detaillierter Arbeitsplan als Anlage vor?
- [ ] Ist eine logische Abfolge erkennbar?

**Framing:**
- [ ] Liest sich der Antrag wie ein Forschungsvorhaben (nicht wie eine Produktbeschreibung)?
- [ ] Eigener Ansatz: frei von kommerziellen Tool-/Produktnamen?
- [ ] Stand der Technik: konkrete Produkte/Tools MIT Namen benannt? (hier erwünscht!)
- [ ] Wissenschaftliche Methodennamen im eigenen Ansatz verwendet?
- [ ] Ziel als offene Forschungsfrage formuliert?
- [ ] Kein Business-Jargon (Churn, Attribution, Conversion, KPI, ROI)?
- [ ] SdT mit Jahreszahl ("Zum Vorhabenbeginn [Jahr]...") verankert?

**Risiko-Qualität (die häufigste Nachforderungsursache):**
- [ ] Steht nach "ob" immer: MODELLNAME + INPUTVARIABLEN + VERSAGENSKRITERIUM?
- [ ] Enthält mindestens ein Risiko einen quantifizierten Scheitern-Schwellenwert?
- [ ] Enthält jedes Risiko eine Problemlösungsstrategie + Restrisiko?
- [ ] Kein einziges methodeninhärentes Standardrisiko (Overfitting, fehlende Daten, Materialtoleranzen)?

**Allgemein:**
- [ ] Ist der gesamte Antrag frei von kommerzieller/wirtschaftlicher Sprache?
- [ ] Kann ein Gutachter jede Sektion in einem Satz paraphrasieren?
- [ ] Sind alle Zeichenlimits per Code verifiziert (95-100%)?
