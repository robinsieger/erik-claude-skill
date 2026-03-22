# Berater-Analyse: KI-basiertes agentengestütztes Kontextmapping

## Forschungsnarrativ

1. **WISSENSFRAGE:** Ist es möglich, dass ein agentenbasiertes KI-System aus kurzen, kontextarmen Kommunikationsfragmenten (1–3 Sätze) zuverlässig die korrekte Zuordnung zu einer mehrdimensionalen Projektstruktur (Akteur x Thema x Zeitachse) ableitet, ohne dass die gesamte Projektdatenbank als Kontext mitgeliefert wird?

2. **WARUM OFFEN:** Zum Vorhabenbeginn 2022 existierte kein Verfahren, das unstrukturierte Kommunikationseinheiten automatisch in mehrdimensionale Projektstrukturen einordnet. 7-8 konventionelle Ansätze (Hashtag-Zuordnung, Baumnavigation, Volltextsuche) scheiterten an der Diskrepanz zwischen natürlichsprachlicher Eingabe und strukturierter Projekttaxonomie.

3. **UNSICHERHEIT:** Es ist unklar, ob mehrstufiges agentenbasiertes Retrieval bei begrenztem Kontextfenster und heterogenen Projektdatenbeständen konvergiert — ob die iterative Eingrenzung aus Tausenden möglicher Zuordnungspunkte zuverlässig auf die korrekten 1-2 Treffer führt.

## Gutachter-Paraphrase (Phase 3, Durchgang 1)

> "Ziel des Vorhabens ist die Entwicklung eines agentenbasierten KI-Systems zur automatischen Zuordnung unstrukturierter Kommunikationsfragmente in mehrdimensionale Projektstrukturen. Bisher werden Projektkommunikation und Projektstruktur in getrennten Tools verwaltet (Slack, Teams für Kommunikation; Asana, Trello für Projektmanagement). Konventionelle Zuordnungsverfahren (Hashtags, manuelle Navigation) scheiterten an der Nutzerakzeptanz. Im Gegensatz dazu soll ein mehrstufiges Retrieval-Verfahren entwickelt werden, bei dem ein KI-Agent natürlichsprachliche Nachrichten analysiert und iterativ die korrekte Projektzuordnung ableitet. Dadurch wird der Stand der Technik übertroffen, da erstmals ein automatisches Mapping zwischen unstrukturierter Kommunikation und mehrdimensionaler Projektstruktur realisiert wird. → Neuartigkeit erfüllt.
>
> Risiko: Es ist unklar, ob das iterative Retrieval bei begrenztem LLM-Kontextfenster konvergiert, insbesondere bei semantischen Überlappungen zwischen Projekten. Ein weiteres Risiko liegt in der Kopplung probabilistischer LLM-Ausgaben mit deterministischen Konsistenzregeln des Projektgraphschemas. → Unwägbarkeit erfüllt.
>
> Strukturierter Arbeitsplan von AP1 (Evaluation konventioneller Verfahren) über AP2 (Ontologie-Modellierung) und AP3 (Retrieval-System) bis AP5 (Validierung) erkennbar. → Planmäßigkeit erfüllt."

Die Paraphrase geht flüssig durch — der Antrag ist klar genug formuliert.

## Qualitätsbewertung pro Sektion

### Ziel-Sektion
- **Stärke:** Eröffnung in Domänensprache (3 Dimensionen der Projektkommunikation), kein Unternehmensname, klare Methodenbenennung (Intent-Erkennung, Entitätsextraktion, probabilistisches Re-Ranking), quantifiziertes Ziel (>90% Trefferquote)
- **BSFZ-Risiko:** Der Gutachter könnte fragen, welche konkreten NLP-Schritte der Primäragent durchläuft — die Beschreibung ist kompakt, aber die Methoden sind benannt.
- **Berater prüfen:** Kunde sollte bestätigen, ob "Intent-Erkennung & Entitätsextraktion" technisch korrekt die tatsächlichen NLP-Schritte beschreibt.

### Neuartigkeit
- **Stärke:** Zeitstempel ("Zum Vorhabenbeginn 2022"), konkrete Produktnamen im SdT (Slack, Teams, Asana, ClickUp), klare "Neu:"-Bullets
- **BSFZ-Risiko:** Keine DOI-Referenz vorhanden. Der Gutachter könnte argumentieren, dass Information Retrieval ein etabliertes Feld ist.
- **Berater prüfen:** Falls verfügbar, eine DOI zu "task-oriented dialogue systems" oder "context-aware information retrieval in collaborative environments" ergänzen.

### Arbeiten-Sektion
- **Stärke:** Klarer Temporalmarker-Rhythmus, jeder Schritt mit Methode in Klammern, keine kommerziellen Produktnamen im eigenen Ansatz, 99.2% Auslastung
- **BSFZ-Risiko:** Gering — die Struktur ist klar und paraphrasierbar.
- **Berater prüfen:** Arbeitsplan-Anlage enthält deutlich mehr Detail; Fließtext ist konsistent damit.

### Risiko-Sektion
- **Stärke:** Zwei klar getrennte Risikoblöcke (1: Konvergenz/Fehlvorschlagsrate, 2: Paradigmen-Kopplung), quantifizierter Schwellenwert (30% Fehlvorschlagsrate, 90%-Schwelle), Problemlösungsstrategie + Restrisiko vorhanden, Spannungsfeld probabilistisch vs. deterministisch explizit benannt
- **BSFZ-Risiko:** Gering — beide Risiken sind projektspezifisch und keine methodeninhärenten Standardrisiken.
- **Berater prüfen:** Kunde sollte die 30%-Schwelle und die 90%-Zielquote bestätigen.

### Schlagwörter
- **Stärke:** Mix aus Forschungsfeld, Methoden und Domäne
- **BSFZ-Risiko:** Keines
- **Berater prüfen:** OK

## Simulierte Nachforderung (Phase 3, Durchgang 2)

**Frage 1:** "Bitte legen Sie dar, welcher konkrete Verarbeitungsschritt durch die KI übernommen wird und mit welchem Ansatz/Modell dieser umgesetzt wird. Wie sehen die Input-Daten und der erwünschte Output aus?"
→ Status: Teilweise abgedeckt. Der Antrag benennt Intent-Erkennung & Entitätsextraktion als NLP-Schritte und beschreibt Input (Kommunikationsfragmente) und Output (Zuordnungsvorschläge). Die konkreten LLM-Modellnamen sind im Arbeitsplan (AP4.1) als Benchmarking-Gegenstand benannt, nicht aber im Zieltext.
→ Handlungsempfehlung: Kann bei Nachforderung mit Verweis auf AP4.1 im Arbeitsplan beantwortet werden. Kein Handlungsbedarf vorab.

**Frage 2:** "Vergleichbare Lösungen existieren und der gezeichnete Lösungsweg konnte auch zum Vorhabenbeginn mit Instrumenten im Stand der Technik realisiert werden."
→ Status: Abgedeckt. Der Antrag stellt klar dar, dass 7-8 konventionelle Verfahren gescheitert sind und dass zum Vorhabenbeginn 2022 kein vergleichbares System existierte. ClickUp wird als einziger Ansatz in die Richtung benannt, aber ohne tiefes KI-Mapping.
→ Handlungsempfehlung: Kein Handlungsbedarf.

**Frage 3:** "Bitte gehen Sie genauer auf die Risiken ein und erläutern Sie, inwiefern diese nicht mit etablierten Lösungsansätzen zu lösen sind."
→ Status: Abgedeckt. Beide Risiken benennen konkret, warum etablierte Ansätze nicht greifen (begrenztes Kontextfenster verhindert "brute force"-Ansatz; Paradigmenkonflikt probabilistisch vs. deterministisch). Problemlösungsstrategien + Restrisiko vorhanden.
→ Handlungsempfehlung: Kein Handlungsbedarf.

**Frage 4:** "Welche eigene Problemlösungsstrategie wird im Vorhaben verfolgt?"
→ Status: Abgedeckt. Risiko 1: mehrstufige Abfragezerlegung, Kontexthistorie-Anreicherung, parallele LLM-Evaluation. Risiko 2: implizit durch die Kopplung beider Paradigmen.
→ Handlungsempfehlung: Für Risiko 2 könnte bei Nachforderung eine explizitere Gegenstrategie formuliert werden (z.B. "fallback auf deterministische Zuordnung bei niedrigem LLM-Konfidenzwert").

## Offene Annahmen

- [ ] **Vorhabenzeitraum:** Im Antrag als Jan 2022 – Dez 2025 angenommen. Kunde muss bestätigen, ob 2021 einbezogen werden soll oder ob Jan 2022 korrekt ist. — betrifft Sektionen: Neuartigkeit, Arbeitsplan
- [ ] **7-8 gescheiterte Verfahren:** Im Transkript erwähnt, aber nicht im Detail beschrieben. Welche drei waren die vielversprechendsten? — betrifft Sektionen: Arbeitsplan AP1
- [ ] **NLP-Schritte:** "Intent-Erkennung & Entitätsextraktion" als Hauptmethoden angenommen. Kunde/technisches Team sollte bestätigen, ob das die tatsächlichen Verarbeitungsschritte sind. — betrifft Sektionen: Ziel, Arbeiten
- [ ] **Projektstruktur als Graphschema:** Angenommen, dass eine formale Taxonomie modelliert wurde. Kunde sollte bestätigen, ob ein solches Schema existiert. — betrifft Sektionen: Arbeitsplan AP2
- [ ] **30% Fehlvorschlagsrate als Schwellenwert:** Aus Transkript ("20-30% Fehlvorschläge → unbrauchbar"). Exakter Wert vom Kunden bestätigen lassen. — betrifft Sektionen: Risiko
- [ ] **90% Trefferquote auf Rang 1-2:** Aus Transkript ("auf den ersten 2 Plätzen 90% Treffer"). Exakter Wert bestätigen lassen. — betrifft Sektionen: Ziel, Risiko
- [ ] **Keine externen Auftragnehmer:** Aus Transkript. Bestätigen lassen. — betrifft Sektionen: Alle
- [ ] **Keine DOIs vorhanden:** Nicht im Transkript erwähnt. Beim Kunden nachfragen, ob relevante Publikationen bekannt sind. — betrifft Sektionen: Neuartigkeit

## Zeichenauslastung

| Sektion | Zeichen | Limit | Auslastung |
|---------|---------|-------|------------|
| Titel   | 150     | 150   | 100,0%     |
| Ziel    | 1.431   | 1.500 | 95,4%      |
| Neuartigkeit | 490 | 500  | 98,0%      |
| Arbeiten | 992    | 1.000 | 99,2%      |
| Risiko  | 1.000   | 1.000 | 100,0%     |
| **Gesamt** | **4.063** | **4.150** | **97,9%** |
