---
name: forschungszulage-antrag
description: "Erstellt Forschungszulage-Anträge (§ 6 FZulG) aus Meeting-Transkripten für die BSFZ. Verwende diesen Skill wenn der Nutzer einen Forschungszulagenantrag, FZulG-Antrag, BSFZ-Antrag, oder einen Antrag für ein F&E-Vorhaben erstellen möchte, oder wenn er ein Meeting-Transkript hat und daraus einen Förderantrag generieren will. Auch triggern bei: 'Antrag schreiben', 'Forschungszulage', 'Bescheinigung Forschungszulage', 'FuE-Vorhaben', 'Kick-Off Transkript', 'Forschungszulage Antrag', 'research tax credit application'."
---

# Forschungszulage-Antragsgenerator

Verwandelt Meeting-Transkripte in einreichungsfertige Forschungszulage-Anträge (§ 6 FZulG). Output: Drei Dateien im `output/`-Ordner — Antragstext, Arbeitsplan, Berater-Analyse.

## Wie der Gutachter denkt

Der Gutachter ist ein **Pattern-Matcher mit 30-60 Minuten**. Er sucht vier Signale:

1. **WISSENSLÜCKE** (erster Absatz): Offenes Problem → grün. Produkt → skeptisch.
2. **METHODEN-NAMEN**: Wissenschaftliche Namen (LSTM, FEM, Bayes, DoE) → Forschung. Kommerzielle Namen (PostgreSQL, ANSYS) → rote Flagge.
3. **PARAPHRASE-FÄHIGKEIT**: Kann er den Antrag in einem Absatz zusammenfassen? Ja → gut. Nein → Nachforderung.
4. **SCHEITERN-KÖNNEN**: Ein Szenario, in dem das Vorhaben komplett scheitert.

## Die 5 entscheidenden Regeln

1. **Wissenslücke als Eröffnung**, nicht Unternehmen/Produkt.
2. **Wissenschaftliche Methoden mit Namen** benennen.
3. **SdT: Konkrete bestehende Ansätze** mit Namen + Limitierungen. Zeitlich: "Zum Vorhabenbeginn [Jahr]..."
4. **Risiken: System-Ebene** mit AP-Bezug + Problemlösungsstrategie + Restrisiko. Als Forschungsfrage.
5. **Zeichenlimits exakt** (95-100%, per Code verifiziert).

## Reference-Dateien

- `references/pruefkriterien.md` — Prüfkriterien, Negativlisten
- `references/stilregeln.md` — Verdichtung, Vokabular, Formulierungsmuster
- `references/antragsstruktur.md` — Sektionen, Limits, AP-Struktur
- `references/nachforderungen.md` — Anti-Patterns aus echten Nachforderungen
- `references/beispiele.md` — Echte bewilligte Antragstexte als Qualitätsanker

---

## Phase 1: Transkript-Interpretation

### Ziel
Strukturiertes Briefing + gezielte Rückfragen + Forschungsnarrativ.

### Vorgehen

Das Transkript ist in **Produktsprache**. Deine Aufgabe ist **Interpretation**, nicht Extraktion. Bei "wir haben X gebaut" frage dich: Welche Wissenslücke wurde geschlossen? Was war unklar? Wo hätte es scheitern können?

**Behalte technische Fachbegriffe.** Ersetze Business-Vokabular: "Churn" → "Nutzungsabbruch", "Attribution" → "Kanalwirkungsanalyse", "Conversion" → "Übergangswahrscheinlichkeit", "KPI" → "Kenngröße", "ROI" → nie, "Customer Journey" → "Nutzungsverlauf", "Retention" → "Verbleibswahrscheinlichkeit".

### Briefing-Struktur

```
BRIEFING: [Projektname]

1. PROJEKTKERN
   - Was wird erforscht? Welches Problem? Welche Domäne?

2. TECHNISCHE SUBSTANZ
   - Wissenschaftliche Methoden/Verfahren
   - Grundlagen (Daten, Materialien, Werkstoffe — je nach Fachgebiet)
   - Quantifizierte Ziele
   - GETRENNT: Infrastruktur/Tools — nur Kontext

3. STAND DER TECHNIK
   - Bestehende Produkte/Ansätze MIT NAMEN + Limitierungen
   - Was ist neu? Literatur/DOIs?

4. ARBEITSSCHRITTE
   - Chronologische Abfolge, Methoden pro Schritt, Zeitachse

5. RISIKEN
   Extraktionsheuristik: Suche "Das war schwierig", "Da mussten wir umdenken".
   Gedankenspiel: "Wenn Geld/Personal keine Rolle spielten — was hätte
   TROTZDEM schiefgehen können?"

6. ROHMATERIAL
   - Originalzitate, Zahlen, Fachbegriffe
```

### Bescheinigungsfähigkeits-Check

Prüfe gegen `references/pruefkriterien.md`. Offensichtlich nicht bescheinigungsfähig? → Direkt sagen + ggf. Reframing vorschlagen.

### Gezielte Rückfragen (spezifisch, nicht generisch)

Analysiere die Lücken im Briefing und formuliere **projektspezifische** Rückfragen. Nicht "Gibt es DOIs?" sondern Fragen, die sich aus dem konkreten Projekt ableiten:

Beispiele für gute, spezifische Rückfragen:
- "Sie sagten, 7-8 Verfahren sind gescheitert — welche drei waren die vielversprechendsten und woran genau scheiterten sie?"
- "Welche konkreten NLP-Schritte durchläuft eine Nachricht? (Tokenisierung, NER, Dependency Parsing, Koreferenzauflösung?)"
- "Gibt es ein formales Modell (Ontologie, Schema), gegen das die KI-Ergebnisse validiert werden?"
- "Welche Genauigkeits-/Qualitätsschwellen haben Sie definiert, ab denen das System unbrauchbar wäre?"

Frage immer nach:
- Externen Auftragnehmern
- DOIs / wissenschaftlichen Publikationen
- Dem genauen Vorhabenzeitraum

### Forschungsnarrativ

**Der wichtigste Schritt.** Bevor du schreibst, formuliere in 3-4 Sätzen das Forschungsnarrativ — die Essenz, warum dieses Vorhaben Forschung ist:

```
FORSCHUNGSNARRATIV:

1. WISSENSFRAGE: [Was ist die offene Frage, die dieses Vorhaben beantwortet?]
   → Nicht "Können wir X bauen?" sondern "Ist es möglich, dass [Methode]
   unter [Bedingung] zuverlässig [Ergebnis] liefert?"

2. WARUM OFFEN: [Warum konnte man diese Frage zum Startzeitpunkt nicht
   mit bekannten Mitteln beantworten?]

3. UNSICHERHEIT: [Was genau macht den Lösungsweg unsicher — nicht schwierig,
   sondern unsicher?]
```

Präsentiere Briefing + Rückfragen + Forschungsnarrativ dem Nutzer. Das Narrativ ist der Kompass für Phase 2 — wenn es nicht überzeugt, wird der Antrag nicht überzeugen.

Gehe erst zu Phase 2, wenn der Nutzer Briefing UND Narrativ bestätigt hat.

---

## Phase 2: Antragserstellung

### Ziel
Einen Antrag formen, der die vier Gutachter-Signale maximiert.

### Vorgehen

Lies `references/stilregeln.md`, `references/antragsstruktur.md` und `references/beispiele.md`.

Das Forschungsnarrativ aus Phase 1 ist der Kompass: Jede Sektion muss dazu beitragen, die Wissensfrage, die Offenheit und die Unsicherheit zu belegen.

### Reframing-Prinzip

Bevor du eine Sektion schreibst, frage dich: "Beschreibe ich gerade, WAS gebaut wurde — oder WELCHE ERKENNTNIS gewonnen wurde?" Der Gutachter will Erkenntnisse, nicht Produkte. Systematisch umdenken:

- "Churn-Prediction" → "Untersuchung, ob verhaltensbezogene Modellierung Beteiligungsdrift prognostizieren kann"
- "Wir haben ein Mapping-Tool gebaut" → "Es wurde untersucht, ob semantische Kontextrekonstruktion aus fragmentierter Kommunikation realisierbar ist"
- "Die Pipeline verarbeitet Daten" → "Es wurde erforscht, ob multimodale Datenfusion heterogener Signalquellen eine kohärente Zustandsbewertung ermöglicht"

Der Trick: Ersetze das konkrete Produkt/Feature durch die dahinterliegende wissenschaftliche Fragestellung. Das Projekt bleibt dasselbe — nur die Perspektive wechselt von Engineering zu Forschung.

Schreibe in dieser Reihenfolge:

#### Schritt 1: Ziel-Sektion (1.500 Zeichen, ~200-220 Wörter)

60% der Bewertung. Lies das Beispiel in `references/beispiele.md`.

**Aufbau — zwei Register:**
1. **Eröffnung IN DOMÄNENSPRACHE** (~400 Z.): Konkrete, domänenspezifische Probleme. Der Gutachter muss sofort verstehen, WO das Problem existiert.
2. **SdT als Kontrast** (~350 Z.): Aktuelle Ansätze mit Namen + Limitierungen.
3. **Forschungsansatz AUF METHODENEBENE** (~500 Z.): "Ziel war es zu untersuchen, ob..." Wissenschaftliche Methoden, NICHT kommerzielle Tools.
4. **Ergebnis — ergebnisoffen** (~250 Z.): Formuliere als offene Erkenntnisfrage, nicht als Lieferergebnis. NICHT: "Ergebnis ist ein validiertes Verfahren mit >90% Trefferquote." SONDERN: "Angestrebt wurden Erkenntnisse darüber, ob & unter welchen Bedingungen [Methode] die angestrebte [Kenngröße] erreichen kann." Nenne 1-2 messbare Parameter, aber als Untersuchungsgegenstand, nicht als Versprechen.

**Vokabular:** Im eigenen Ansatz keine kommerziellen Namen. Im SdT kommerzielle Namen ERLAUBT und ERWÜNSCHT.

#### Schritt 2: Detaillierter Arbeitsplan (separate Datei)

4-6 Hauptarbeitspakete mit je 2-3 Unter-APs. Jedes Unter-AP:
- Aktives Verb, Tätigkeitsbeschreibung (2-3 Sätze), Methode in Klammern
- Ergebnisdefinition (konkretes Artefakt)
- Zeitraum (Monatsangaben)

Anti-SdT-Begründungen nur wo aus dem Transkript begründbar.

Aufbau je nach Fachgebiet:
- **Software/KI:** Datenaufbereitung → Modellentwicklung → Integration → Evaluation
- **Ingenieurwesen:** Analyse/Entwurf → Simulation → Prototyp → Prüfung
- **Chemie/Material:** Synthese → Charakterisierung → Optimierung → Scale-up
- **Biotech:** Methodenentwicklung → Screening → Optimierung → Validierung
- **Sozialwissenschaften:** Instrumentenentwicklung → Erhebung → Auswertung → Validierung

#### Schritt 3: Arbeiten-Fließtext (1.000 Zeichen, ~130-150 Wörter)

Verdichte den Arbeitsplan. Temporalmarker: "Zunächst... Darauf... Nun... Final..." Methode in Klammern. "&" durchgehend.

#### Schritt 4: Arbeitspakete gekürzt

```
[Nr] [Thema]
[Nr.1] [Aktives Verb] [Beschreibung] ([Methode])
```

#### Schritt 5: Neuartigkeit (500 Zeichen, ~65-75 Wörter)

1. "Zum Vorhabenbeginn [Jahr]..." 2. Bestehende Ansätze mit Namen. 3. Ggf. DOI. 4. "Neu:" + Bullets.

#### Schritt 6: Risiko (1.000 Zeichen, ~130-150 Wörter)

2 Blöcke. Jeder: "Unklar ist, ob [MODELL] [INPUTS] [VERSAGEN]." + Lösungsstrategie + Restrisiko.

**Selbsttest vor dem Schreiben jedes Risikos:** Würde dieses Risiko in JEDEM ML/Ingenieur/Chemie-Projekt existieren? Wenn ja → es ist methodeninhärent und wird von der BSFZ abgelehnt. Verwerfen und ein projektspezifisches Risiko formulieren.

Beispiele für ABGELEHNTE Risiken (methodeninhärent):
- "Klassenungleichgewicht", "Overfitting", "fehlende Ground-Truth", "unvollständige Daten"
- "Materialtoleranz", "Fertigungsstreuung", "Scale-up könnte scheitern"

Beispiele für AKZEPTIERTE Risiken (projektspezifisch):
- Paradoxe Rückkopplung (Intervention verschlechtert Ergebnis)
- Technische Artefakte nicht von echten Signalen trennbar
- Nichtlineare Wechselwirkungen zwischen Komponenten, die erst im Zusammenspiel auftreten
- Übertragbarkeit von Simulation/Labor auf Realbedingungen bei KONKRETEM Grund warum

#### Schritt 7: Schlagwörter (10 Stück)

#### Schritt 8: Titel (~150 Zeichen)

### Zeichenkontrolle

Per Code nach jeder Sektion:
```python
print(f"{len(text)} / {limit} Zeichen ({len(text)/limit*100:.0f}%)")
```
Ziel: **95-100%**. Die Ziel-Sektion muss am vollsten sein (**98-100%**) — sie bestimmt 60% der Bewertung, jedes ungenutzte Zeichen dort ist der größte Verlust. Wenn >100%: verdichten. Wenn <95%: Details einarbeiten.

---

## Phase 3: Qualitätsprüfung & Analyse

### Durchgang 1: Gutachter-Paraphrase

Schreibe die Bescheid-Paraphrase:
> "Ziel des Vorhabens ist [X]. Bisher [SdT]. Im Gegensatz dazu [Ansatz]. Dadurch wird SdT übertroffen. → Neuartigkeit erfüllt.
> Risiko: [R1]. Weiteres: [R2]. → Unwägbarkeit erfüllt.
> Strukturierter Arbeitsplan erkennbar. → Planmäßigkeit erfüllt."

Stockst du? → Stelle im Antrag nachschärfen.

### Durchgang 2: Simulierte Nachforderung

Versetze dich in einen kritischen BSFZ-Gutachter und schreibe die **konkreten Nachforderungsfragen**, die er stellen würde. Nutze die echten Trigger-Formulierungen aus `references/nachforderungen.md`.

Für jede simulierte Frage:
- Prüfe, ob der Antrag sie bereits beantwortet
- Wenn ja → notiere als "abgedeckt" in der Analyse
- Wenn nein → **überarbeite den Antrag**, sodass die Frage beantwortet wird

Wenn du keine überzeugenden Nachforderungsfragen formulieren kannst → der Antrag ist robust.

### Durchgang 3: Zeichenverifikation per Code

Alle Sektionen nochmals zählen. Kein Limit darf überschritten sein.

---

## Phase 4: Output — Kundenordner

Erstelle einen Kundenordner `output/[kundenname]/` im Arbeitsverzeichnis. Der Kundenname wird aus dem Transkript abgeleitet (Firmenname oder Projektname, als slug: Kleinbuchstaben, Bindestriche statt Leerzeichen, keine Sonderzeichen).

Lege dort diese Dateien ab:

### Datei 1: `antrag.md` — Hauptvariante (versandfertig)

Alle Sektionen in BSFZ-Formular-Reihenfolge + Arbeitspakete (Kurzfassung). Kann direkt ins Formular kopiert werden. Zeichenzählung unter jeder Sektion.

### Datei 2: `antrag-variante-b.md` — Berater-Variante

Zweite Variante mit kreativem Reframing:
- **Mutigeres Forschungsnarrativ** auf höherer Abstraktionsebene
- **Wissenschaftlichere Konzepte** (Ontologie, Wissensgraph etc.), die zum Projekt passen aber im Transkript nicht explizit genannt wurden
- **Stärkere Risiken:** Systemrisiken, Paradigmenkonflikte, paradoxe Rückkopplungseffekte
- Alle Freiheiten als `[BERATER-ANNAHME: ...]` markiert

Der Berater pickt die besten Formulierungen und übernimmt sie nach Kundenabstimmung in die Hauptvariante.

### Datei 3: `arbeitsplan.md` — Detaillierter Arbeitsplan (Anlage)

4-6 APs mit je 2-3 Unter-APs, Zeitachse, Ergebnisse. Wird als Anlage eingereicht.

### Datei 4: `analyse.md` — Berater-Analyse

Unabhängige Prüfung BEIDER Varianten. Verändert nicht den Antragstext. Struktur:

```markdown
# Berater-Analyse: [Projekttitel]

## ⚡ Sofort-Handlungsbedarf (Top 5)
Die wichtigsten Punkte VOR Einreichung. Nummeriert nach Priorität.

## Forschungsnarrativ
Die 3 Sätze aus Phase 1 (Wissensfrage, Warum offen, Unsicherheit).

## Varianten-Vergleich

| Sektion | Variante A | Variante B | Empfehlung |
|---------|-----------|-----------|------------|
| Titel   | [Titel A] | [Titel B] | [Welchen nehmen / kombinieren] |
| Ziel    | [Stärke/Schwäche] | [Stärke/Schwäche] | [Konkret: was übernehmen] |
| ...     | ...       | ...       | ...        |

## Simulierte Nachforderung

Für BEIDE Varianten getrennt geprüft. Der Berater sieht sofort:
Variante A hätte Nachforderung X bekommen, Variante B nicht.

### Variante A
Frage 1: "[BSFZ-Formulierung]"
→ Status: ✅ / ⚠️ / ❌
→ Handlungsempfehlung: [Konkret]

### Variante B
Frage 1: "[BSFZ-Formulierung]"
→ Status: ✅ / ⚠️ / ❌
→ Handlungsempfehlung: [Konkret]

Bei ⚠️ IMMER eine konkrete Handlungsempfehlung.

## Sektions-Tiefenanalyse

### Ziel-Sektion
- **Gutachter-Paraphrase:** [Kann er es in eigenen Worten zusammenfassen?]
- **Stärke:** [Was ist gut]
- **BSFZ-Risiko:** [Wo könnte nachgefragt werden]
- **Berater-Aktion:** [Was tun]

[...für jede Sektion...]

## Offene Annahmen
- [ ] [Annahme] — betrifft: [Sektion], Variante: [A/B/beide]

## Zeichenauslastung
| Sektion | Var. A | Var. B | Limit |
|---------|--------|--------|-------|
| Titel   | X (Y%) | X (Y%) | 150   |
| Ziel    | X (Y%) | X (Y%) | 1.500 |
| ...     | ...    | ...    | ...   |
```

### Datei 5: `[kundenname].docx` — Word-Gesamtdokument

Benannt nach dem Kunden (z.B. `lingoda.docx`, `medocheck.docx`). Enthält ALLES — professionell formatiert. Nutze Python-docx (oder falls `/mnt/skills/public/docx/SKILL.md` existiert, deren Anweisungen).

**Aufbau:**

**Teil 1: Antragstext** (Seite 1-2)
- Titel: Arial 14pt Bold, zentriert
- Sektionsüberschriften: Arial 12pt Bold, exakte BSFZ-Fragetexte
- Fließtext: Arial 11pt
- Zeichenzählung: Arial 9pt, grau, kursiv
- Schlagwörter als nummerierte Liste
- A4, Ränder 2,5 cm

**Teil 2: Arbeitsplan-Anlage** (Seitenumbruch)
- "Arbeitsplan – [Projekttitel]"
- APs: Arial 11pt Bold, Unter-APs als Unterüberschriften
- Ergebnis-Zeilen: fett
- Zeitachse in AP-Überschrift

**Teil 3: Arbeitspakete Kurzfassung** (1 Seite)

**Teil 4: Variante B — Kreatives Reframing** (Seitenumbruch)
- Überschrift: "Variante B — Kreatives Reframing (zur Diskussion mit dem Kunden)"
- Alle Sektionen der Berater-Variante
- `[BERATER-ANNAHME]`-Markierungen in dunkelgrau kursiv (nicht rot — das wirkt wie ein Fehler)

**Teil 5: Berater-Analyse** (Seitenumbruch)
- Überschrift: "Interne Analyse — nicht zur Einreichung"
- Dünne graue Linie (1pt) oben als visueller Trenner zum Antragstext

Visuelles Styling — zurückhaltend und professionell (Consulting-Dokument, kein Ampelbericht):

*Grundprinzip:* Schwarzer Text, sparsamer Einsatz von einer Akzentfarbe (Dunkelblau RGB 0,51,102) für Struktur. Farbe nur dort, wo sie dem Berater hilft, schneller zu scannen. Kein Rot, kein Grün im Fließtext.

- **Gesamter Analyse-Teil:** Arial 10pt (eine Stufe kleiner als Antragstext — signalisiert: internes Dokument)
- **Überschriften:** Arial 11pt Bold, Dunkelblau (RGB 0,51,102) — einzige Akzentfarbe
- **Sofort-Handlungsbedarf:** Nummeriert, fett, schwarzer Text. Kein Rot. Die Priorität wird durch die Position (ganz oben) kommuniziert, nicht durch Farbe.
- **Varianten-Vergleich:** Saubere Tabelle mit dunkelblauer Kopfzeile (weißer Text). Empfehlungs-Spalte fett. Tabellenzeilen abwechselnd weiß/hellgrau (Zebra-Streifen) für Lesbarkeit.
- **Simulierte Nachforderung:** Status als schlichte Tags in eckigen Klammern: [ABGEDECKT], [TEILWEISE], [OFFEN]. Status-Tag fett. Handlungsempfehlung in normalem Text, eingerückt.
- **Sektions-Tiefenanalyse:** Pro Sektion ein Block. Labels ("Stärke:", "BSFZ-Risiko:", "Berater-Aktion:") in fett. Normaler schwarzer Text dahinter. Keine farbigen Labels.
- **Offene Annahmen:** Nummerierte Liste mit ☐ Checkbox-Zeichen
- **Zeichenauslastung:** Tabelle mit dunkelblauer Kopfzeile. Werte in normalem Schwarz — der Berater sieht die Prozentzahl und braucht keine Ampel.

---

## Gesamtablauf

```
1. Nutzer gibt Meeting-Transkript
2. Phase 1: Briefing + spezifische Rückfragen + Forschungsnarrativ → Nutzer bestätigt
3. Phase 2: Zwei Antragsvarianten + Arbeitsplan schreiben → Zeichenkontrolle per Code
4. Phase 3: Gutachter-Paraphrase + Simulierte Nachforderung (beide Varianten) + Zeichenverifikation
5. Phase 4: Fünf Dateien in output/[kundenname]/ ablegen
```

Zwischen jeder Phase aktiv Feedback einholen. Wenn der Nutzer nach Phase 1 bestätigt, können Phase 2-4 zusammen ausgeführt werden.
