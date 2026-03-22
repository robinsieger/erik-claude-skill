---
name: forschungszulage-antrag
description: "Erstellt Forschungszulage-Anträge (§ 6 FZulG) aus Meeting-Transkripten für die BSFZ. Verwende diesen Skill wenn der Nutzer einen Forschungszulagenantrag, FZulG-Antrag, BSFZ-Antrag, oder einen Antrag für ein F&E-Vorhaben erstellen möchte, oder wenn er ein Meeting-Transkript hat und daraus einen Förderantrag generieren will. Auch triggern bei: 'Antrag schreiben', 'Forschungszulage', 'Bescheinigung Forschungszulage', 'FuE-Vorhaben', 'Kick-Off Transkript', 'Forschungszulage Antrag', 'research tax credit application'."
---

# Forschungszulage-Antragsgenerator

Dieser Skill verwandelt Meeting-Transkripte in einreichungsfertige Forschungszulage-Anträge nach § 6 FZulG. Output: .docx-Dokument mit Antragstext + Arbeitsplan-Anlage.

## Wie der Gutachter denkt

Der Gutachter ist kein Forscher, der dein Projekt versteht. Er ist ein **Pattern-Matcher mit 30-60 Minuten pro Antrag**. Er sucht nach vier Signalen:

1. **WISSENSLÜCKE** (erster Absatz Ziel-Sektion): Steht dort ein offenes Problem → grünes Licht. Steht dort ein Produkt → sofort skeptisch.
2. **METHODEN-NAMEN**: Er scannt nach wissenschaftlichen Methodennamen (LSTM, FEM, Monte-Carlo, Bayes, DoE...). Je mehr er findet, desto eher ordnet er es als Forschung ein. Kommerzielle Tool-Namen (PostgreSQL, ANSYS, AWS) sind rote Flaggen.
3. **PARAPHRASE-FÄHIGKEIT**: Er versucht, den Antrag in einem Absatz zusammenzufassen. Geht das leicht → gut. Muss er zweimal lesen → Nachforderung.
4. **SCHEITERN-KÖNNEN**: Bei den Risiken sucht er ein Szenario, in dem das Vorhaben komplett scheitert. Nicht "wird schwierig", sondern "funktioniert möglicherweise nicht".

Alle Regeln in diesem Skill dienen dazu, diese vier Signale zu maximieren.

## Die 5 entscheidenden Regeln

Wenn du nur 5 Dinge richtig machst, dann diese. Sie entscheiden über Bewilligung oder Ablehnung. Alles andere ist Optimierung.

1. **Wissenslücke als Eröffnung**, nicht Unternehmen/Produkt. Erster Satz = offenes Problem.
2. **Wissenschaftliche Methoden mit Namen** benennen. Nicht "wir nutzen KI", sondern konkrete Verfahren.
3. **Stand der Technik: Konkrete existierende Ansätze** mit Namen + deren spezifische Limitierungen. Zeitlich verankert: "Zum Vorhabenbeginn [Jahr]..."
4. **Risiken: System-Ebene** mit AP-Bezug + Problemlösungsstrategie + Restrisiko. Formuliert als offene Forschungsfrage, nicht als KPI.
5. **Zeichenlimits exakt einhalten** (95-100% Auslastung, per Code verifiziert).

## Reference-Dateien

Lies diese, wenn du sie für eine Phase brauchst:
- `references/pruefkriterien.md` — Die drei Prüfkriterien der BSFZ, Negativlisten
- `references/stilregeln.md` — Verdichtungstechniken, Formulierungsmuster, Vokabular-Regeln
- `references/antragsstruktur.md` — Sektionen, Zeichenlimits, Arbeitsplan-Struktur
- `references/nachforderungen.md` — Anti-Pattern-Katalog aus echten BSFZ-Nachforderungen
- `references/beispiele.md` — Echte bewilligte Antragstexte als Qualitätsanker

---

## Phase 1: Transkript-Interpretation

### Ziel
Aus dem Rohmaterial ein strukturiertes Briefing destillieren — die einzige Grundlage für Phase 2.

### Vorgehen

Das Transkript wird in **Produktsprache** sein. Deine Aufgabe ist nicht bloße Extraktion, sondern **Interpretation**. Wenn der Kunde sagt "wir haben X gebaut", frage dich:
- Welche **Wissenslücke** hat er dabei geschlossen?
- Was war **unklar**, bevor er angefangen hat?
- Wo hätte es **scheitern** können?

Diese Fragen stehen nicht explizit im Transkript — du musst sie aus dem Kontext ableiten.

**Behalte technische Fachbegriffe** aus dem Transkript. Ersetze aber Business-Vokabular: "Churn" → "Nutzungsabbruch", "Attribution" → "Kanalwirkungsanalyse", "Conversion" → "Übergangswahrscheinlichkeit", "KPI" → "Kenngröße", "ROI" → nie nennen, "Customer Journey" → "Nutzungsverlauf", "Retention" → "Verbleibswahrscheinlichkeit".

### Briefing-Struktur

```
BRIEFING: [Projektname/Arbeitstitel]

1. PROJEKTKERN
   - Was wird entwickelt/erforscht?
   - Welches fundamentale Problem wird gelöst?
   - Für welche Domäne?

2. TECHNISCHE SUBSTANZ
   - Wissenschaftliche Methoden und Verfahren
   - Grundlagen: Daten, Materialien, Werkstoffe, Reagenzien — je nach Fachgebiet
   - Quantifizierte Ziele: Metriken, Schwellenwerte, Toleranzen
   - Konkrete Modelle/Verfahren mit wissenschaftlichen Namen
   - GETRENNT: Infrastruktur/Tools/Geräte/Lieferanten — nur Kontext

3. STAND DER TECHNIK & ABGRENZUNG
   - Was existiert bereits? (Konkrete Produkte, Ansätze MIT NAMEN)
   - Warum reichen bestehende Ansätze nicht?
   - Was genau ist neu am eigenen Ansatz?
   - Literatur / DOIs (falls im Transkript erwähnt)

4. ARBEITSSCHRITTE
   - Chronologische/logische Abfolge
   - Eingesetzte Methoden pro Schritt
   - Zeitachse (falls genannt)

5. RISIKEN & UNWÄGBARKEITEN
   Extraktionsheuristik: Suche nach Stellen, wo der Kunde sagt "Das war
   schwierig", "Da haben wir lange gebraucht", "Das hat nicht funktioniert",
   "Da mussten wir umdenken". Wende das Gedankenspiel an: "Wenn Geld und
   Personal keine Rolle spielten — was hätte TROTZDEM schiefgehen können?"
   Die Antwort ist ein FuE-Risiko.

6. ROHMATERIAL
   - Gute Originalzitate, Zahlen, Fachbegriffe
```

### Bescheinigungsfähigkeits-Check

Bevor du weitermachst, prüfe gegen `references/pruefkriterien.md`:
- Ist das Vorhaben **offensichtlich nicht bescheinigungsfähig**? (Reine Konfiguration, Post-Prototyp-Marktanpassung, Routine-Engineering ohne Wissenslücke)
- Falls ja: Sage das dem Nutzer direkt und schlage vor, wie das Vorhaben ggf. umgeframed werden könnte.

### Kritische Prüfung

Prüfe das Briefing gegen die drei BSFZ-Kriterien:
1. **Neuartigkeit:** Genug Material für SdT-Abgrenzung?
2. **Risiko:** Echte technische Unwägbarkeiten, die zum Scheitern führen könnten?
3. **Planmäßigkeit:** Genug Arbeitsschritte für nachvollziehbaren Plan?

Bei kritischen Lücken **proaktiv** kommunizieren: "Für einen bewilligungsfähigen Antrag brauchen wir noch: [X]."

### Output Phase 1

Präsentiere das Briefing. Stelle gezielte Fragen zu Lücken, plus:
- Gibt es externe Auftragnehmer?
- Gibt es wissenschaftliche Publikationen / DOIs?
- Gibt es quantifizierte Zielparameter (Genauigkeit, Schwellenwerte)?

Gehe erst zu Phase 2, wenn der Nutzer bestätigt hat.

---

## Phase 2: Antragserstellung

### Ziel
Aus dem Briefing einen Antrag formen, der die vier Gutachter-Signale maximiert.

### Vorgehen

Lies `references/stilregeln.md`, `references/antragsstruktur.md` und `references/beispiele.md`. Die Beispiele in `beispiele.md` zeigen das Qualitätsniveau, das du erreichen musst.

Schreibe die Sektionen in dieser Reihenfolge:

#### Schritt 1: Ziel-Sektion (1.500 Zeichen, ~200-220 Wörter)

Die Sektion, die 60% der Bewertung bestimmt. Lies das Beispiel in `references/beispiele.md` als Qualitätsanker.

**Aufbau — zwei Register:**
1. **Eröffnung IN DER SPRACHE DER DOMÄNE** (2-3 Sätze, ~400 Zeichen): Konkrete, domänenspezifische Probleme benennen. Der Gutachter muss sofort verstehen, WO das Problem existiert. Fachbegriffe der Branche nutzen.
2. **Stand der Forschung als Kontrast** (2-3 Sätze, ~350 Zeichen): Warum lösen aktuelle Ansätze das Problem nicht? Bestehende Ansätze mit Namen benennen, deren Limitierungen aufzeigen.
3. **Forschungsansatz AUF METHODENEBENE** (3-4 Sätze, ~500 Zeichen): Was soll untersucht werden? Wissenschaftliche Methoden benennen, NICHT kommerzielle Tools. Formulierung: "Ziel ist es zu untersuchen, ob..." oder "Unser Ziel in [Jahr] war, zu untersuchen, ob..."
4. **Angestrebtes Ergebnis** (1-2 Sätze, ~250 Zeichen): Was existiert am Ende als validiertes Verfahren/Erkenntnis? Mindestens 1-2 messbare Zielparameter nennen.

**Vokabular-Regeln (entscheidend):**
- Im EIGENEN Ansatz: Keine kommerziellen Produktnamen. Nur wissenschaftliche Methoden.
- Im STAND DER TECHNIK: Kommerzielle Produktnamen ERLAUBT und ERWÜNSCHT — sie zeigen dem Gutachter, dass der Antragsteller den Markt kennt (z.B. "Bestehende TOS wie NavisN4, RBS, SAP können nur...").

#### Schritt 2: Detaillierter Arbeitsplan (Anlage)

4-6 Hauptarbeitspakete mit je 2-3 Unter-APs. Jedes Unter-AP:
- Aktives Verb am Anfang
- Konkrete Tätigkeitsbeschreibung (2-3 Sätze)
- Methode in Klammern
- Ergebnisdefinition (konkretes, messbares Artefakt)
- Zeitraum (Monatsangaben)

**Anti-SdT-Begründungen nur dort**, wo der Kunde im Transkript erklärt hat, WARUM Standard-Tools nicht reichten. Nicht bei jedem AP generisch einfügen — das wirkt künstlich.

Logischer Aufbau je nach Fachgebiet:
- **Software/KI:** Datenaufbereitung → Modellentwicklung → Integration → Evaluation
- **Ingenieurwesen:** Analyse/Entwurf → Simulation → Prototyp → Prüfung
- **Chemie/Material:** Synthese → Charakterisierung → Optimierung → Scale-up
- **Biotech/Medizin:** Methodenentwicklung → Screening → Optimierung → Validierung
- **Sozialwissenschaften:** Instrumentenentwicklung → Erhebung → Auswertung → Validierung

#### Schritt 3: Arbeiten-Fließtext (1.000 Zeichen, ~130-150 Wörter)

Verdichte den Arbeitsplan. Strenger Rhythmus: Jeder Satz beginnt mit einem Temporalmarker ("Zunächst...", "Darauf aufbauend...", "Nun...", "Final..."). Jeder Schritt enthält die Methode in Klammern. "&" statt "und" durchgehend.

#### Schritt 4: Arbeitspakete gekürzt

```
[Nr] [Thema]
[Nr.1] [Aktives Verb] [Beschreibung] ([Methode])
```

#### Schritt 5: Neuartigkeit (500 Zeichen, ~65-75 Wörter)

1. "Zum Vorhabenbeginn [Jahr]..." — SdT zeitlich verankern
2. Bestehende Ansätze/Produkte mit Namen benennen (hier SIND kommerzielle Namen richtig)
3. Ggf. DOI-Referenz
4. "Neu:" gefolgt von Bulletpoints der Neuerungen

#### Schritt 6: Risiko (1.000 Zeichen, ~130-150 Wörter)

Lies das Beispiel in `references/beispiele.md` als Qualitätsanker.

2 Risikoblöcke, jeder enthält:
1. "Unklar ist, ob [MODELLNAME] [INPUTVARIABLEN] [VERSAGENSKRITERIUM]" — nach dem "ob" müssen drei Dinge stehen: das konkrete Modell/Verfahren, die konkreten Eingangsvariablen, und das konkrete Scheiterns-Szenario.
2. Problemlösungsstrategie: "Dem soll mit [A], [B] & [C] entgegengewirkt werden."
3. Restrisiko: "Dennoch könnte d. Vorhaben scheitern, wenn [konkrete Bedingung]."

**NICHT akzeptiert:** Methodeninhärente Standardrisiken (Overfitting, Klassenungleichgewicht, fehlende Ground-Truth, unvollständige Daten, Materialtoleranzen als Pauschalaussage). Stattdessen: Systemrisiken, Wechselwirkungen, Paradigmenkonflikte, Übertragbarkeitsprobleme.

#### Schritt 7: Schlagwörter (10 Stück)

Mix aus Forschungsfeld, Methoden, Domäne, Technologien.

#### Schritt 8: Titel (~150 Zeichen)

Muster: [Methode]-basierte/gestützte [Lösung/Framework] zur [Zielprozess] in/für [Domäne]

### Zeichenkontrolle

Nach dem Schreiben jeder Sektion: **Zeichen per Code zählen.**
```python
print(f"{len(text)} / {limit} Zeichen ({len(text)/limit*100:.0f}%)")
```
- Wenn >100%: Kürze mit Verdichtungstechniken aus `references/stilregeln.md`
- Wenn <95%: Arbeite weitere Details aus dem Briefing ein
- Ziel: **95-100%** pro Sektion. Jedes ungenutzte Zeichen ist verschwendetes Argumentationspotenzial.

### Output Phase 2

Präsentiere alle Sektionen mit Code-verifizierter Zeichenzählung. Der Nutzer kann gezielt Feedback geben.

---

## Phase 3: Qualitätsprüfung

### Durchgang 1: Gutachter-Simulation

Schreibe eine Paraphrase des Antrags — exakt so, wie sie im Bescheid stehen würde:

> "Ziel des Vorhabens ist [Paraphrase Ziel]. Bisher werden [SdT]. Im Gegensatz dazu soll [Neuer Ansatz]. Dadurch wird der Stand der Technik übertroffen. Anhand der Arbeitspakete lässt sich erkennen, dass es sich nicht um routinemäßige Arbeiten handelt. → Kriterium Neuartigkeit erfüllt.
> Ein Risiko bezieht sich auf [Risiko 1]. Ein weiteres auf [Risiko 2]. → Kriterium Unwägbarkeit erfüllt.
> Ein inhaltlich strukturierter Arbeitsplan ist erkennbar. → Kriterium Planmäßigkeit erfüllt."

Wenn du beim Schreiben dieser Paraphrase stockst oder raten musst → die betreffende Stelle im Antrag nachschärfen.

### Durchgang 2: Nachforderungs-Resilienz

Prüfe gegen die Checkliste in `references/nachforderungen.md`. Jeder nicht-erfüllte Punkt wird korrigiert.

### Durchgang 3: Zeichenlimits verifizieren

Alle Sektionen nochmals per Code zählen. Limits dürfen NICHT überschritten sein.

### Korrektur

Korrigiere alle Mängel direkt. Präsentiere dem Nutzer den geprüften Entwurf mit Zeichenzählung.

---

## Phase 4: Dokument-Output

Erstelle das .docx. Falls eine Docx-Skill-Anleitung unter `/mnt/skills/public/docx/SKILL.md` existiert, befolge deren Anweisungen. Sonst nutze Python-docx oder docx-js.

### Dokument-Aufbau

**Seite 1+: Antragstext**
- Titel: Arial 14pt Bold
- Sektionsüberschriften: Arial 12pt Bold — die exakten Fragetexte als Überschriften:
  - "Was ist das Ziel Ihres Vorhabens? Welche Herausforderung oder Problemstellung soll mit dem Vorhaben gelöst bzw. welche Wissenslücke soll mit dem Vorhaben geschlossen werden?"
  - "Inwieweit hebt sich das angestrebte Produkt, Verfahren oder die Dienstleistung vom Stand der Technik ab?"
  - "Welche Arbeiten werden durchgeführt, um der zuvor benannten Herausforderung oder Problemstellung zu begegnen bzw. um die Wissenslücke zu schließen?"
  - "Welche wissenschaftlichen, technischen und/oder methodischen Unsicherheiten bestehen bei der Bearbeitung der Herausforderung oder Problemstellung?"
  - "Schlagwörter"
- Fließtext: Arial 11pt
- Zeichenzählung unter jeder Sektion: graue Schrift, z.B. "(1.485 / 1.500 Zeichen)"
- Seitenformat: A4, Ränder 1 Zoll

**Folgeseite(n): Arbeitsplan-Anlage**
- "Arbeitsplan – [Projekttitel]"
- Detaillierter Arbeitsplan mit allen APs, Unter-APs, Zeitachse

**Folgeseite: Arbeitspakete (Kurzfassung)**

---

## Gesamtablauf

```
1. Nutzer gibt Meeting-Transkript
2. Phase 1: Briefing interpretieren → Bescheinigungsfähigkeits-Check → Nutzer bestätigt
3. Phase 2: Antrag schreiben → Zeichenkontrolle per Code → Nutzer sieht Vorschau
4. Phase 3: Gutachter-Simulation + Nachforderungs-Check + Zeichenverifikation → Nutzer gibt frei
5. Phase 4: .docx erstellen
```

Zwischen jeder Phase aktiv Feedback einholen. Wenn der Nutzer nach Phase 1 bestätigt, können Phase 2 und 3 zusammen ausgeführt werden.
