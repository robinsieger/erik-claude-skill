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
NICHT: Methodeninhärente Standardrisiken. Stattdessen: Systemrisiken, Paradigmenkonflikte, Übertragbarkeit.

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

## Phase 4: Output — Kundenordner mit drei Dateien

Erstelle einen Kundenordner `output/[kundenname]/` im Arbeitsverzeichnis. Der Kundenname wird aus dem Transkript abgeleitet (Firmenname oder Projektname, als slug: Kleinbuchstaben, Bindestriche statt Leerzeichen, keine Sonderzeichen). Beispiele: `output/lingoda/`, `output/medocheck/`, `output/containerterminal-htg/`.

Lege dort drei Dateien ab:

### Datei 1: `output/[kundenname]/antrag.md` — Der Antragstext

Enthält alle Sektionen versandfertig, in der Formular-Reihenfolge:

```markdown
# [TITEL]

## Was ist das Ziel Ihres Vorhabens? [...]
[Ziel-Text]
(X / 1.500 Zeichen)

## Inwieweit hebt sich das angestrebte Produkt [...] vom Stand der Technik ab?
[Neuartigkeit-Text]
(X / 500 Zeichen)

## Welche Arbeiten werden durchgeführt [...]?
[Arbeiten-Fließtext]
(X / 1.000 Zeichen)

## Welche wissenschaftlichen [...] Unsicherheiten bestehen [...]?
[Risiko-Text]
(X / 1.000 Zeichen)

## Schlagwörter
[10 Schlagwörter]
```

Zusätzlich am Ende: Arbeitspakete (Kurzfassung).

Dieser Text kann direkt in das BSFZ-Formular kopiert werden.

### Datei 2: `output/[kundenname]/arbeitsplan.md` — Der detaillierte Arbeitsplan

Separate Datei, wird als Anlage eingereicht:

```markdown
# Arbeitsplan – [Projekttitel]

## AP1 – [Thema] ([Methode]) [Zeitraum]

### AP1.1 – [Titel]: [Zeitraum]
[Beschreibung]
**Ergebnis:** [Konkretes Artefakt]

### AP1.2 – [Titel]: [Zeitraum]
...
```

### Datei 3: `output/[kundenname]/analyse.md` — Berater-Feedback

Diese Datei verändert NICHT den Antragstext. Sie ist das strukturierte Feedback für den Berater.

```markdown
# Berater-Analyse: [Projekttitel]

## ⚡ Sofort-Handlungsbedarf (Top 3)

Die wichtigsten Punkte, die der Berater VOR Einreichung prüfen/ändern sollte:

1. [Wichtigster Punkt — z.B. "DOI ergänzen in Neuartigkeits-Sektion"]
2. [Zweitwichtigster — z.B. "Kunde muss NLP-Pipeline-Schritte bestätigen"]
3. [Drittwichtigster — z.B. "Vorhabenzeitraum klären: 2021 oder 2022?"]

## Forschungsnarrativ
[Die 3 Sätze aus Phase 1 — Wissensfrage, Warum offen, Unsicherheit]

## Simulierte Nachforderung

Was würde ein kritischer BSFZ-Gutachter fragen? Für jede Frage:
- Die exakte Formulierung (im Stil echter BSFZ-Nachforderungen)
- Ob der Antrag sie beantwortet
- Was der Berater tun sollte

Frage 1: "[Exakte Formulierung]"
→ Status: ✅ Abgedeckt / ⚠️ Teilweise / ❌ Offen
→ Handlungsempfehlung: [Konkret — nicht "kein Handlungsbedarf" wenn es
   der häufigste Nachforderungsgrund ist]

WICHTIG: Bei "⚠️ Teilweise" immer eine konkrete Handlungsempfehlung
geben. "Teilweise abgedeckt" ohne Aktion ist für den Berater nutzlos.

## Qualitätsbewertung pro Sektion

### Ziel-Sektion
- **Stärke:** [Was ist gut]
- **BSFZ-Risiko:** [Wo könnte der Gutachter nachfragen]
- **Berater prüfen:** [Was der Berater nochmal anschauen sollte]

[...für jede Sektion...]

## Offene Annahmen
[Alle Annahmen, die vom Kunden bestätigt werden müssen]

- [ ] [Annahme 1] — betrifft Sektion: [X]
- [ ] [Annahme 2] — betrifft Sektion: [X]

## Zeichenauslastung
| Sektion | Zeichen | Limit | Auslastung |
|---------|---------|-------|------------|
| Titel   | X       | 150   | X%         |
| Ziel    | X       | 1.500 | X%         |
| ...     | ...     | ...   | ...        |
```

### Datei 4: `output/[kundenname]/komplett.docx` — Word-Gesamtdokument

Ein professionell formatiertes Word-Dokument, das alle Informationen visuell sauber aufbereitet. Falls eine Docx-Skill-Anleitung unter `/mnt/skills/public/docx/SKILL.md` existiert, befolge deren technische Anweisungen. Sonst nutze Python-docx.

**Aufbau des .docx:**

**Teil 1: Antragstext (Seite 1-2)**
- Titel: Arial 14pt Bold, zentriert
- Sektionsüberschriften: Arial 12pt Bold, die exakten BSFZ-Fragetexte
- Fließtext: Arial 11pt
- Zeichenzählung unter jeder Sektion: Arial 9pt, grau, kursiv, z.B. "(1.485 / 1.500 Zeichen)"
- Schlagwörter als nummerierte Liste
- Seitenformat: A4, Ränder 2,5 cm

**Teil 2: Arbeitsplan-Anlage (ab Seite 3)**
- Überschrift: "Arbeitsplan – [Projekttitel]"
- Pro AP: Überschrift Arial 11pt Bold, Unter-APs als Unterüberschriften
- Ergebnis-Zeilen: fett markiert
- Zeitachse in der AP-Überschrift

**Teil 3: Arbeitspakete Kurzfassung (1 Seite)**
- Kompakte nummerierte Liste mit Methoden in Klammern

**Teil 4: Berater-Analyse (ab nächste Seite)**
- Seitenumbruch vor diesem Teil
- Überschrift: "Interne Analyse — nicht zur Einreichung"
- Hintergrundfarbe oder Rahmen, der visuell klar macht: Das ist nicht Teil des Antrags
- Sofort-Handlungsbedarf: Top 3 als nummerierte rote/orange Markierung
- Forschungsnarrativ
- Simulierte Nachforderung mit Status-Icons (✅ / ⚠️ / ❌)
- Qualitätsbewertung pro Sektion
- Offene Annahmen als Checkliste
- Zeichenauslastungs-Tabelle

---

## Gesamtablauf

```
1. Nutzer gibt Meeting-Transkript
2. Phase 1: Briefing + spezifische Rückfragen + Forschungsnarrativ → Nutzer bestätigt
3. Phase 2: Antrag schreiben → Zeichenkontrolle per Code
4. Phase 3: Gutachter-Paraphrase + Simulierte Nachforderung + Zeichenverifikation
5. Phase 4: Vier Dateien in output/[kundenname]/ ablegen
```

Zwischen jeder Phase aktiv Feedback einholen. Wenn der Nutzer nach Phase 1 bestätigt, können Phase 2-4 zusammen ausgeführt werden.
