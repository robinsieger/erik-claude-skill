# Berater-Analyse: KI-gestuetzte Modellierung von Lernverhalten & Beteiligungsdrift (Lingoda)

## Sofort-Handlungsbedarf (Top 5)

1. **Arbeiten-Sektion Variante A nur 94,3 % ausgelastet** -- 57 Zeichen ungenutzt. In der drittgewichtigsten Sektion fehlt Substanz. Konkret: Evaluationsschritt der Nudging-Wirkung (Hypothesentests, Kontrollgruppe) ergaenzen, der im Arbeitsplan (AP5.3) vorhanden ist, aber im Fliesstext fehlt.

2. **Risiko A: Kein AP-Bezug bei Risiko 2 (Kanalwirkungsmodell)** -- Die BSFZ fordert bei Nachforderungen explizit den Bezug zum Arbeitsschritt. "Unklar ist ferner, ob d. probabilist. Kanalwirkungsmodell..." muss mit "(vgl. AP4)" verankert werden.

3. **Risiko A: Kein quantifizierter Scheitern-Schwellenwert** -- Die Nachforderungs-Referenz verlangt mindestens einen quantifizierten Schwellenwert. Ergaenzen: z.B. "AUC-ROC < 0,65" oder "Praezision < 60 %" als Scheiternskriterium.

4. **Ziel-Sektion Variante B nur 94,7 %** -- 79 Zeichen verschenkt in der wichtigsten Sektion (60 % der Bewertung). Die Eroeffnung in Domaenensprache koennte konkreter werden (Gruppengroessen, Sprachniveaus, Unterrichtsfrequenz).

5. **Auftragnehmer-Frage ungeklaert** -- Weder Variante A noch B adressieren externe Auftragnehmer. Falls Lingoda externe Dienstleister fuer Dateninfrastruktur oder App-Entwicklung eingesetzt hat, muss deren FuE-Beitrag benannt werden, sonst droht Nachforderung.

---

## Forschungsnarrativ

1. **WISSENSFRAGE:** Ist es moeglich, dass verhaltensbasierte ML-Modellierung auf individuellen Subskriptionsketten unter den Bedingungen heterogener Lernbiografien und nicht-linearer Zustandsuebergaenge zuverlaessig Beteiligungsdrift prognostizieren und durch Nudging-Interventionen reduzieren kann?

2. **WARUM OFFEN:** Zum Vorhabenbeginn 2021 existierten keine integrierten Verfahren, die Abbruchprognose, Kanalwirkungsanalyse und Nudging fuer lehrergestuetzten Live-Gruppenunterricht verbinden. Bestehende Retentionsmodelle bildeten nur Kohorten-Durchschnitte ab.

3. **UNSICHERHEIT:** Nicht-lineare Zustandsuebergaenge (Pausen, Reaktivierungen, Formatwechsel) entziehen sich einer standardisierten Feature-Repraesentation. Die Horizonterweiterung (7 Tage auf 3 Monate) unterliegt staerkeren exogenen Stoerfaktoren, deren Einfluss auf die Prognosequalitaet unklar ist.

---

## Varianten-Vergleich

| Sektion | Variante A | Variante B | Empfehlung |
|---------|-----------|-----------|------------|
| **Titel** | Konkret, nennt alle Kernkomponenten (ML, Beteiligungsdrift, Lernpfade). 145 Z. (96,7 %) | Abstrakter ("multimodal", "praediktiv"). Wissenschaftlicher klingend. 148 Z. (98,7 %) | **Titel B nehmen** -- wissenschaftlicher, bessere Zeichenauslastung |
| **Ziel** | Solide Eroeffnung in Domaenensprache. SdT mit konkreten Namen. Drei Saeulen klar benannt. 1491 Z. (99,4 %) | Staerkere theoretische Rahmung (Motivationsdynamik, kognitive Belastung, soziale Kohaesion). Ontologie als Zusatzdimension. 1421 Z. (94,7 %) | **Ziel A als Basis**, Eroeffnung aus B uebernehmen (Motivationsdynamik, kognitive Belastung). Ontologie nur wenn vom Kunden bestaetigbar |
| **Neuartigkeit** | Vier klare Bullet-Points. Praegnant. 497 Z. (99,4 %) | Ontologie und Closed-Loop als Differenzierungsmerkmal, aber beides BERATER-ANNAHME. 495 Z. (99,0 %) | **Neuartigkeit A** -- sicherer, da vollstaendig belegbar |
| **Arbeiten** | Chronologisch sauber. Nudging-Evaluation fehlt. 943 Z. (94,3 %) | Ontologie-Entwurf als erster Schritt staerkt Forschungscharakter. Closed-Loop am Ende. 972 Z. (97,2 %) | **Arbeiten B hat bessere Struktur**, aber A ergaenzen auf >95 % und als Basis nutzen (keine BERATER-ANNAHMEN) |
| **Risiko** | Zwei solide Risiken. Horizonterweiterung und Konfundierung. 974 Z. (97,4 %) | Paradigmenkonflikt (Ontologie vs. ML) und paradoxe Rueckkopplung -- staerkere Forschungssignale. 949 Z. (94,9 %) | **Risiko B ist ueberzeugender** (Paradigmenkonflikt = starkes BSFZ-Signal). Aber nur verwendbar wenn Ontologie bestaetigt. Sonst A mit AP-Bezuegen und Schwellenwert nachrüsten |
| **Schlagwoerter** | Methodisch korrekt, aber generischer | Verhaltensontologie, Closed-Loop-Nudging -- differenzierter | **Mix**: Schlagwoerter aus B, wo belegbar; Rest aus A |

---

## Simulierte Nachforderung

### Variante A

**Frage 1:** "Bitte gehen Sie genauer auf die Risiken und Herausforderungen ein und erlaeutern Sie, inwiefern diese nicht mit etablierten Loesungsansaetzen zu loesen sind."
- Status: [TEILWEISE]
- Handlungsempfehlung: *Risiko 1 hat Problemloesungsstrategie (iterative Feature-Konstruktion + Benchmarking), aber Risiko 2 (Kanalwirkungsmodell) hat KEINE explizite Gegenstrategie. Ergaenzen: "Dem wurde mit Kreuzvalidierung ueber disjunkte Zeitfenster & saisonaler Dekomposition begegnet." + Restrisiko benennen.*

**Frage 2:** "Beschreiben Sie bitte aussagekraeftig technische und/oder wissenschaftliche Risiken, die ueber methodeninahaerente Risiken bzw. unvermeidbare Standardrisiken hinausgehen."
- Status: [TEILWEISE]
- Handlungsempfehlung: *Risiko 1 ("nicht-lineare Zustandsuebergaenge entziehen sich Feature-Repraesentation") ist projektspezifisch -- gut. Aber die Horizonterweiterung als Risiko koennte als methodeninaharent gelesen werden ("laengere Prognosen sind immer schwieriger"). Staerker ans Projektspezifische binden: exogene Stoerfaktoren BENENNEN (Semesterzyklen, Feiertage, Pandemie-Effekte).*

**Frage 3:** "Welcher Verarbeitungs-/Prozessschritt wird konkret durch die KI uebernommen und mit welchem Ansatz/Modell soll der Schritt umgesetzt werden?"
- Status: [ABGEDECKT]
- Die Ziel-Sektion benennt alle drei Saeulen mit konkreten Methoden (Random Forest, Gradient Boosting, logist. Regression, Markov-Ketten, Shapley-Wert).

**Frage 4:** "Die Abgrenzung zum Stand der Technik in Ihrer Branche bzw. zu bestehenden Produkten, Verfahren oder Dienstleistungen Ihres Unternehmens ist unzureichend beschrieben."
- Status: [ABGEDECKT]
- Duolingo, Babbel, Busuu namentlich benannt. Limitierung (Selbstlernformate, keine Prognosefaehigkeit fuer Gruppenformate) klar dargestellt.

**Frage 5:** "Bitte fuehren Sie aus, inwieweit die Auftragnehmer Taetigkeiten durchfuehren, die zur Zielerreichung des Vorhabens beitragen."
- Status: [OFFEN]
- Handlungsempfehlung: *Klaeren, ob externe Auftragnehmer beteiligt waren. Falls ja: deren FuE-Beitrag im Antrag benennen. Falls nein: explizit "Keine externen Auftragnehmer" dokumentieren.*

### Variante B

**Frage 1:** "Bitte gehen Sie genauer auf die Risiken und Herausforderungen ein und erlaeutern Sie, inwiefern diese nicht mit etablierten Loesungsansaetzen zu loesen sind."
- Status: [ABGEDECKT]
- Paradigmenkonflikt (Ontologie vs. ML) ist ein starkes Forschungssignal. Paradoxe Rueckkopplung zeigt echtes Scheitern-Koennen. Beide Risiken haben implizite Gegenstrategien.

**Frage 2:** "Beschreiben Sie bitte aussagekraeftig technische und/oder wissenschaftliche Risiken, die ueber methodeninahaerente Risiken hinausgehen."
- Status: [ABGEDECKT]
- Paradigmenkonflikt und paradoxe Rueckkopplung sind beide projektspezifisch und nicht standardmaessig.

**Frage 3:** "Welcher Verarbeitungs-/Prozessschritt wird konkret durch die KI uebernommen?"
- Status: [ABGEDECKT]
- Vier Saeulen mit konkreten Methoden benannt.

**Frage 4:** "Die Abgrenzung zum Stand der Technik ist unzureichend."
- Status: [ABGEDECKT]
- Zusaetzlich zu A: "kohortenbasierte Retentionsmodelle (Standard 2021)" als zeitlich verankerte Referenz.

**Frage 5:** "Bitte fuehren Sie aus, inwieweit die Auftragnehmer Taetigkeiten durchfuehren..."
- Status: [OFFEN]
- Identisch mit Variante A -- ungeklaert.

**Frage 6 (nur B):** "[X, Y, Z] stellen Vorhabenspraemissen dar, die zum Vorhabenbeginn als loesbar anzunehmen sind, sodass hier ein Zirkelschluss vorliegt."
- Status: [TEILWEISE]
- Handlungsempfehlung: *Die Ontologie-Modellierung ist eine BERATER-ANNAHME. Falls der Kunde sie nicht bestaetigt, waere die gesamte Risiko-Sektion (Paradigmenkonflikt Ontologie vs. ML) hinfaellig. Vor Einreichung klaeren.*

---

## Sektions-Tiefenanalyse

### Ziel-Sektion
- **Gutachter-Paraphrase:** "Ziel ist die Untersuchung, ob ML-basierte Prognosemodelle auf individuellen Subskriptionsketten Beteiligungsdrift in Online-Sprachkursen vorhersagen koennen. Bisherige Ansaetze (Duolingo, Babbel) adressieren nur Selbstlernformate. Der Ansatz kombiniert Drift-Prognose, Kanalwirkungsmodell und Nudging." -- Paraphrase gelingt gut.
- **Staerke:** Klare Wissensluecke als Eroeffnung. Drei Saeulen sauber benannt. Ergebnisoffen formuliert ("Erkenntnisse darueber, ob & unter welchen Bedingungen").
- **BSFZ-Risiko:** Die ELT-Transformation (letzter Satz des Ziels) koennte als Infrastruktur/Routine gelesen werden, nicht als Forschung. Sie steht aktuell gleichgewichtig neben den drei Forschungssaeulen.
- **Berater-Aktion:** ELT-Transformation als "Voraussetzung" rahmen, nicht als gleichwertiges Forschungsziel. Ggf. in die Arbeiten-Sektion verlagern.

### Neuartigkeit-Sektion
- **Gutachter-Paraphrase:** "Zum Vorhabenbeginn 2021 gab es keine integrierten Verfahren fuer Abbruchprognose + Kanalwirkung + Nudging in Live-Gruppenunterricht. Neu sind vier Komponenten." -- Funktioniert.
- **Staerke:** Zeitliche Verankerung ("Zum Vorhabenbeginn 2021"), konkrete Wettbewerber, klare Bullet-Points.
- **BSFZ-Risiko:** "ELT-Datenplattform m. semantischer Quellenharmonisierung" als vierter Neuartigkeitspunkt koennte als Infrastruktur gewertet werden.
- **Berater-Aktion:** ELT-Bullet streichen oder umformulieren zu "Semantische Harmonisierung heterogener Verhaltensdatenquellen als Voraussetzung fuer cross-system Feature Engineering".

### Arbeiten-Sektion
- **Gutachter-Paraphrase:** "ETL zu ELT transformiert, Features konstruiert, ML-Modelle trainiert, Kanalwirkungsmodell benchmarked, Nudging in App integriert." -- Chronologie klar.
- **Staerke:** Temporalmarker ("Zunaechst... Darauf... Nun... Parallel... Final"). Methoden in Klammern.
- **BSFZ-Risiko:** Nudging-Evaluation (Hypothesentests, Kontrollgruppe) fehlt im Fliesstext, obwohl AP5.3 sie beschreibt.
- **Berater-Aktion:** Satz ergaenzen: "Die Nudging-Wirkung wurde mittels statist. Hypothesentests (t-Tests) gegen eine Kontrollgruppe evaluiert." Bringt Sektion auf >95 %.

### Risiko-Sektion
- **Gutachter-Paraphrase:** "Zwei Risiken: (1) Feature-Repraesentation nicht-linearer Zustandsuebergaenge, (2) Konfundierung im Kanalwirkungsmodell." -- Klar paraphrasierbar.
- **Staerke:** Risiko 1 ist projektspezifisch (Subskriptionsketten mit Pausen/Reaktivierungen). Hat Problemloesungsstrategie + Restrisiko.
- **BSFZ-Risiko:** Risiko 2 hat keine Gegenstrategie und kein Restrisiko. Der dreiteilige Aufbau (Problem-Strategie-Restrisiko) ist nicht vollstaendig. Kein quantifizierter Schwellenwert in beiden Risiken.
- **Berater-Aktion:** Risiko 2 mit Gegenstrategie ergaenzen. Mindestens einen quantifizierten Schwellenwert einfuegen (z.B. "AUC-ROC < 0,65").

### Schlagwoerter
- **Staerke:** Alle zehn Begriffe sind fachlich korrekt und forschungsrelevant.
- **BSFZ-Risiko:** "ELT-Datenplattform" klingt nach Infrastruktur.
- **Berater-Aktion:** Ersetzen durch "Semantische Datenharmonisierung" oder "Verhaltensontologie" (wenn B-Elemente uebernommen werden).

---

## Offene Annahmen

- [ ] Wurden externe Auftragnehmer eingesetzt? -- betrifft: alle Sektionen, Variante: beide
- [ ] Hat Lingoda tatsaechlich eine Ontologie/Graphmodellierung implementiert? -- betrifft: Ziel, Risiko, Variante: B
- [ ] Gibt es DOIs oder wissenschaftliche Publikationen als Referenz? -- betrifft: Neuartigkeit, Variante: beide
- [ ] Ist der exakte Vorhabenzeitraum Jan 2021 - Jul 2022 korrekt? -- betrifft: Arbeitsplan, Variante: beide
- [ ] War die 60 %-Abbruchrate eine gemessene interne Kenngroesse oder eine Branchenschaetzung? -- betrifft: Ziel, Variante: beide
- [ ] Wurde die Nudging-Wirkung tatsaechlich mittels Kontrollgruppe evaluiert (AP5.3) oder nur geplant? -- betrifft: Arbeiten, Variante: A
- [ ] Closed-Loop-Feedback: Wurde die Rueckspeisung der Nudging-Ergebnisse ins Modell tatsaechlich implementiert? -- betrifft: Risiko, Variante: B

---

## Zeichenauslastung

| Sektion | Var. A | Var. B | Limit | Bewertung A | Bewertung B |
|---------|--------|--------|-------|-------------|-------------|
| Titel | 145 (96,7 %) | 148 (98,7 %) | 150 | OK (95-100 %) | OK (95-100 %) |
| Ziel | 1491 (99,4 %) | 1421 (94,7 %) | 1.500 | OK (95-100 %) | UNTERAUSGELASTET (<95 %) |
| Neuartigkeit | 497 (99,4 %) | 495 (99,0 %) | 500 | OK (95-100 %) | OK (95-100 %) |
| Arbeiten | 943 (94,3 %) | 972 (97,2 %) | 1.000 | UNTERAUSGELASTET (<95 %) | OK (95-100 %) |
| Risiko | 974 (97,4 %) | 949 (94,9 %) | 1.000 | OK (95-100 %) | UNTERAUSGELASTET (<95 %) |

**Legende:** OK = 95-100 %, UNTERAUSGELASTET = <95 %, UEBERSCHRITTEN = >100 %

**Zusammenfassung:** Variante A hat eine Schwaeche in der Arbeiten-Sektion (94,3 %). Variante B hat Schwaechen in Ziel (94,7 %) und Risiko (94,9 %). Keine Sektion ueberschreitet das Limit.
