# Stilregeln für Forschungszulage-Anträge

Dieses Dokument kodifiziert die Stilmuster, die in positiv beschiedenen Anträgen funktionieren. Die Regeln sind domänenunabhängig — sie gelten für jede Branche.

---

## Grundhaltung: Wissenschaftlich, nicht kommerziell

Der Antrag wird von einem wissenschaftlichen Gutachter gelesen. Jede Formulierung muss durch die Brille "Ist das F&E?" bestehen.

**Verboten im gesamten Antrag:**
- Kommerzieller Nutzen, Umsatzpotenzial, Marktchancen
- "Wettbewerbsvorteil", "Marktführerschaft", "Kundenzufriedenheit"
- Wirtschaftliche Risiken oder finanzielle Argumente
- Marketing-Sprache ("revolutionär", "einzigartig", "Gamechanger")
- Business-Intelligence-Jargon: "Churn", "Attribution", "Conversion", "KPI", "ROI", "Customer Journey", "Retention" — diese Begriffe signalisieren Geschäftsoptimierung statt Forschung. Ersetze durch wissenschaftliche Äquivalente: "Nutzungsabbruch/Beteiligungsdrift", "Kanalwirkungsanalyse", "Übergangswahrscheinlichkeit", "Kenngröße", "Nutzungsverlauf/Interaktionssequenz", "Verbleibswahrscheinlichkeit"

**Stattdessen:**
- Wissenslücken, methodische Neuheit, technische Herausforderungen
- "Es ist zu untersuchen, ob...", "Unklar ist, ob..."
- Passivkonstruktionen und Nominalstil
- Sachlich-wissenschaftlicher Ton durchgehend

**Vokabular-Regeln (differenziert nach Kontext):**

Im **eigenen Forschungsansatz** (Ziel-Sektion Absatz 3+4, Arbeiten, Risiko):
- Keine kommerziellen Produktnamen, Cloud-Provider, Hosting-Details
- Stattdessen wissenschaftliche Methoden benennen:
  - PostgreSQL → "relationale Datenbankabfragen"
  - ANSYS → "FEM-basierte Struktursimulation"
  - Shimadzu HPLC → "flüssigchromatographische Analytik"
  - SolidWorks → "3D-CAD-gestützte Konstruktion"
  - Self-Hosting → "kontrollierte Evaluierungsumgebung"

Im **Stand der Technik** (Ziel-Sektion Absatz 2, Neuartigkeit):
- Kommerzielle Produktnamen ERLAUBT und ERWÜNSCHT
- Sie zeigen dem Gutachter, dass der Antragsteller den Markt kennt
- z.B. "Bestehende TOS (NavisN4, RBS, SAP) verarbeiten nur Echtzeit- & histor. Daten"
- z.B. "Tools wie Jira, Asana, Monday bieten keine autom. Kontextstrukturierung"

**Wissenschaftliche Methoden-Vokabular (Positivliste nach Fachgebiet):**

*Branchenübergreifend:* experimentelle Evaluierung, statistische Validierung, Benchmarking, Design of Experiments (DoE), Monte-Carlo-Simulation, Konfidenzintervalle, Varianzanalyse (ANOVA), Regressionsanalyse, Prototypentestung, Versuchsplanung

*Software/KI:* Ontologie-Modellierung, NER, Dependency Parsing, Bayes'sche Modellierung, probabilistisches Re-Ranking, RAG, Transferlernen, Few-Shot-Learning, Finetuning, Feature Engineering, Wissensgraph

*Ingenieurwissenschaften:* Finite-Elemente-Methode (FEM), Computational Fluid Dynamics (CFD), Mehrkörpersimulation (MKS), Topologieoptimierung, Betriebsfestigkeitsanalyse, zerstörungsfreie Prüfung (ZfP), Schwingungsanalyse, thermographische Analyse

*Chemie/Material/Biotech:* nasschemische Synthese, Katalysatorcharakterisierung, Rasterelektronenmikroskopie (REM), Röntgendiffraktometrie (XRD), HPLC-Analytik, Hochdurchsatz-Screening (HTS), In-vitro-Validierung, thermogravimetrische Analyse (TGA), Impedanzspektroskopie

*Sozialwissenschaften:* quasi-experimentelles Design, Längsschnittstudie, Mixed-Methods-Design, qualitative Inhaltsanalyse, Strukturgleichungsmodellierung (SEM), Mehrebenenanalyse

---

## Verdichtungstechniken

Bei 500-1.500 Zeichen pro Sektion zählt jedes Wort.

### Systematische Abkürzungen
Verwende konsequent: "insb.", "div.", "i.d.R.", "bzgl.", "hinsichtl.", "Zus.hänge", "ggü.", "nat.", "Entw.", "notw.", "spez.", "d.", "v.", "m.H.d.", "o.g.", "u.a.", "z.B.", "autom."

### Klammertechnik
Fachbegriffe und Spezifizierungen in Klammern statt ausgeschriebene Erklärungen:
- "ML-Verfahren (Random Forest, LightGBM, Gradient Boosting)"
- "Simulationsverfahren (FEM, CFD, MKS)"
- "analytische Methoden (REM, XRD, HPLC)"
- "heterogene Datenquellen (Sensoren, Messdaten, Prozessparameter)"

### Komposita statt Umschreibungen
- "Optimierungsproblematik" statt "das Problem der Optimierung"
- "Zustandsprognosen" statt "Vorhersagen über zukünftige Zustände"
- "Modellkopplung" statt "Verbindung zwischen den Modellen"
- "Datenfusionspipeline" statt "Pipeline zur Zusammenführung von Daten"

### Weitere Techniken
- "&" statt "und" in dichten Passagen
- Nummerierte Aufzählungen statt Fließtext (insb. in Arbeiten-Sektion)
- Semikolons statt Punkte bei zusammengehörigen Aussagen
- Partizipialkonstruktionen: "Darauf aufbauend berechnet..." statt "Danach wird berechnet..."

---

## Quantifizierung als Glaubwürdigkeitssignal

Abstrakte Behauptungen überzeugen Gutachter nicht. Jede Behauptung sollte durch eine Zahl gestützt werden:

- **Datensatzgrößen:** "500 cases", "über 1 Mio. Trainingspläne", "4-5k Datenpunkte je Messdatensatz"
- **Präzisionsziele:** "Präzision von 95%", "Abweichungen von +/-50%"
- **Schwellenwerte:** "Ontologie-Matching-Accuracy <0,85 führt zu signifikantem Performanceverlust"
- **Strukturierte Zahlen:** "100 Felder pro Geografie", "17 Kategorien", "fünf Layer"
- **Zeithorizonte:** "Prognosen über mehrere Tage", "Rechenzeit <5 min"

Wenn das Transkript konkrete Zahlen enthält, immer verwenden. Wenn nicht, den Nutzer gezielt danach fragen — Zahlen sind zu wichtig um sie wegzulassen.

---

## Literaturreferenzen (DOI-Strategie)

In erfolgreichen Anträgen tauchen DOI-Referenzen auf, um den Forschungsbedarf zu untermauern:
- "Dieser Forschungsbedarf wird auch in der Literatur aufgezeigt: DOI:10.1057/s41278-023-00254-0"
- "2022 wird in der Literatur (DOI:10.56889/nrkr7690) Forschungsbedarf dargestellt, ob..."

DOIs werden in der Neuartigkeits-Sektion platziert. Sie belegen, dass das Problem wissenschaftlich anerkannt ist und der Stand der Technik tatsächlich nicht ausreicht. Dies stärkt die Argumentation gegenüber dem Gutachter erheblich.

Wenn im Transkript Literaturhinweise oder Paper genannt werden, unbedingt verwenden. Wenn nicht, den Nutzer fragen, ob es relevante Publikationen gibt.

---

## Sektionsspezifische Formulierungsmuster

### Titel
Muster: **[Methode/Technologie]-basierte/gestützte [Lösung/Framework] zur [Zielprozess] in/für [Anwendungsdomäne]**

Beispielmuster nach Fachgebiet (nicht Inhalt kopieren):
- *KI:* "KI-basierte semantische Kontextrekonstruktion fragmentierter [Datenart] zur automatischen Ableitung mehrdimensionaler [Struktur]"
- *Maschinenbau:* "FEM-gestützte Entwicklung einer adaptiven [Komponente] zur [Prozess]-Optimierung unter dynamischen [Randbedingungen]"
- *Chemie:* "Katalytische [Methode] zur selektiven [Reaktion] neuartiger [Material]-Schichten mit definierter [Eigenschaft]"
- *Biotech:* "Entwicklung eines [Verfahren]-basierten Nachweissystems zur [Erkennung/Quantifizierung] von [Biomarker] in [Medium]"
- *Sozialwiss.:* "Mixed-Methods-Evaluation [methodischer Ansatz] zur [Fragestellung] in [Kontext]"

Der Titel benennt immer: die technologische Methode, das Ziel und die Domäne.

### Ziel-Sektion (die wichtigste)
Aufbau:
1. **Eröffnung mit dem Kernproblem** (2-3 Sätze): Welche fundamentale Wissenslücke oder technische Herausforderung existiert? Nie mit dem Unternehmen anfangen, immer mit dem Problem.
2. **Stand der Forschung als Kontrast** (2-3 Sätze): Warum lösen aktuelle Ansätze das Problem nicht?
3. **Der eigene Forschungsansatz** (3-4 Sätze): Was genau soll entwickelt/erforscht werden? Methodische Kernbausteine benennen.
4. **Angestrebtes Ergebnis** (1-2 Sätze): Was existiert am Ende, das vorher nicht existierte?

### Neuartigkeits-Sektion
Bewährtes Muster:
1. Einen Satz, der den Forschungsbedarf benennt (optional mit DOI)
2. "Neu:" gefolgt von Bulletpoints mit den konkreten Neuerungen
3. Jeder Bullet benennt eine spezifische methodische/technische Innovation

### Arbeiten-Sektion (Fließtext)
- Chronologisch-logischer Aufbau, angepasst an das Fachgebiet (siehe AP-Aufbau in SKILL.md)
- Jeder Schritt enthält die verwendete Methode in Klammern
- Partizipialkonstruktionen für Übergänge: "Darauf werden...", "Nun wird...", "Final wird..."
- Aktive Verben mit F&E-Charakter: Analysieren, Erforschen, Entwickeln, Synthetisieren, Simulieren, Charakterisieren, Evaluieren, Validieren, Testen, Optimieren, Prüfen

### Arbeitspakete (gekürzte Variante für Formular)
Format pro AP:
```
[Nummer] [Übergeordnetes Thema]
[Nummer.1] [Aktives Verb + Beschreibung] ([Methode])
[Nummer.2] [Aktives Verb + Beschreibung] ([Methode])
[Nummer.3] [Aktives Verb + Beschreibung] ([Methode])
```

Die Methode in Klammern am Ende jedes Unter-APs signalisiert wissenschaftliches Vorgehen.

### Risiko-Sektion
Jede Unsicherheit muss:
1. **Spezifisch sein** — bezogen auf einen konkreten Lösungsschritt
2. **Das WARUM benennen** — technische Begründung, warum es scheitern könnte
3. **Den Bezug zum Lösungsansatz herstellen** — nicht generisch, sondern "bei unserem Ansatz"

Bewährte Einleitungsformeln (variieren):
- "Unklar ist, ob..."
- "Es ist offen, ob..."
- "Unsicher ist, ob..."
- "Es besteht das Risiko, dass..."
- "Es kann nicht vorab beurteilt werden, ob..."
- "Risikobehaftet ist, dass..."

Idealstruktur: 2 klar getrennte Risikoblöcke. Erstes Risiko: fundamental (Machbarkeit unter realen Bedingungen). Zweites Risiko: integrativ (Zusammenspiel der Komponenten oder Paradigmenkonflikte).

**Jedes Risiko enthält eine Problemlösungsstrategie:**
Das Muster aus erfolgreichen Nachforderungs-Antworten: "Es ist unklar, ob [konkretes Problem bei konkretem Arbeitsschritt]. Dem wollen wir mit [Strategie A], [Strategie B] und [Strategie C] entgegenwirken. Dennoch könnte das Vorhaben scheitern, wenn [konkrete Bedingung]."

Beispiel-Strategien je Fachgebiet:
- *KI:* "domänenspezifische Anpassung der NLP-Modelle", "RAG mit Quellenverankerung", "Multi-Agenten-Prüfung"
- *Ingenieurwesen:* "iterative Parametervariation mittels DoE", "Validierung durch Prüfstandsversuche unter Realbedingungen"
- *Chemie:* "systematische Katalysator-Optimierung über Hochdurchsatz-Screening", "Parallelansätze mit alternativen Syntheserouten"

**Risiken als Forschungsfragen, nicht als KPIs formulieren:**
- FALSCH: "Ob wir >90% Trefferquote / Festigkeit / Ausbeute erreichen" (das ist ein Produktziel)
- RICHTIG: "Ob das Verfahren unter realen Bedingungen [spezifisches technisches Problem] bewältigen kann"
- FALSCH: "Ob das System schnell genug / stabil genug ist" (das ist ein Performance-Ziel)
- RICHTIG: "Ob die Kopplung von [Ansatz A] und [Ansatz B] bei [konkreter Randbedingung] konvergiert"

**Spannungsfeld als Forschungssignal:**
Ein besonders starkes Signal für die BSFZ: Wenn der Ansatz zwei gegensätzliche Anforderungen oder Paradigmen kombiniert, deren Zusammenspiel unklar ist.

Beispiele nach Fachgebiet:
- *KI/Software:* probabilistisch vs. deterministisch, datengetrieben vs. regelbasiert, generativ vs. faktengebunden
- *Maschinenbau:* Leichtbau vs. Steifigkeit, thermische Ausdehnung vs. Maßtoleranzen, Automatisierung vs. Prozessflexibilität
- *Chemie:* Reaktionsselektivität vs. Umsatzrate, Katalysatoraktivität vs. Langzeitstabilität
- *Biotech:* Sensitivität vs. Spezifität, In-vitro-Ergebnis vs. In-vivo-Übertragbarkeit
- *Sozialwiss.:* interne vs. externe Validität, Standardisierung vs. Kontextsensitivität

Dieses Spannungsfeld explizit als Risiko benennen — es zeigt dem Gutachter, dass echte Forschungsarbeit nötig ist.

### Schlagwörter
Mix aus: übergeordnetem Forschungsfeld, spezifischen Methoden, Anwendungsdomäne, Schlüsseltechnologien. Keine generischen Begriffe wie "Innovation" oder "Digitalisierung" allein. Orientierung an den tatsächlichen Fachbegriffen des Vorhabens.

---

## Der Gutachter-Paraphrase-Test

Das übergeordnete Qualitätskriterium: Kann ein Gutachter den Antrag in eigenen Worten zusammenfassen und dabei klar erkennen, warum alle drei Kriterien erfüllt sind?

Der Gutachter schreibt im Bescheid immer eine Paraphrase des Antrags. Wenn die Formulierungen im Antrag so klar und spezifisch sind, dass die Paraphrase quasi automatisch entsteht, ist der Antrag gut. Wenn der Gutachter rätseln muss, was genau gemeint ist, kommt eine Nachforderung.

Prüfe jeden Absatz: "Kann ein fachfremder Gutachter nach dem Lesen dieses Absatzes in einem Satz wiedergeben, was hier gesagt wird und warum es FuE ist?"

---

## Schutzformulierungen

Formulierungen, die den Forschungscharakter signalisieren:

**SdT-Zeitstempel (Pflicht in Neuartigkeits-Sektion):**
"Zum Vorhabenbeginn [Jahr]..." — die BSFZ prüft Neuartigkeit zum Startzeitpunkt. Der Zeitbezug ist nicht optional.

**Ergebnisoffenheit (empfohlen in Ziel-Sektion, wenn Forschungscharakter sonst nicht klar genug):**
"Unser Ziel in [Jahr] war, zu untersuchen, ob..." oder "Die Arbeiten dien(t)en der Prüfung der technischen Realisierbarkeit." Nicht in jedem Antrag nötig — die Forschungshaltung muss aus dem gesamten Text emergieren, nicht aus einem Disclaimer-Satz.

**Anti-Routine-Signale (nur dort, wo aus dem Transkript begründbar):**
Dort, wo der Kunde erklärt hat, warum Standard-Tools nicht reichten, das im AP aufgreifen: "Standard-[X] konnten [Y] nicht leisten." Nicht bei jedem AP generisch einfügen — das wirkt künstlich.
