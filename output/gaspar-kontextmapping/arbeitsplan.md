# Arbeitsplan – KI-basiertes agentengestütztes Kontextmapping fragmentierter Kommunikationseinheiten zur automatischen Zuordnung in mehrdimensionale Projektstrukturen

## AP1 – Evaluation konventioneller Zuordnungsverfahren (Experimentelle Evaluation) Jan 2022 – Jun 2022

### AP1.1 – Evaluieren bestehender Mapping-Ansätze: Jan 2022 – Mär 2022
Systematische Erprobung konventioneller Zuordnungsmechanismen (Hashtag-basierte Selektion, hierarchische Baumnavigation, Volltextsuche) im Kontext mehrdimensionaler Projektkommunikation. Für jeden Ansatz wurden Testszenarien mit realen Kommunikationsdaten durchgeführt & Zuordnungspräzision sowie Nutzungsaufwand erfasst.
**Ergebnis:** Dokumentierte Evaluierungsmatrix mit Präzisions- & Akzeptanzkennwerten für 7-8 konventionelle Zuordnungsverfahren.

### AP1.2 – Dokumentieren von Limitierungen: Mär 2022 – Mai 2022
Analyse der identifizierten Schwachstellen: Hashtag-Zuordnung erfordert manuellen Aufwand pro Nachricht, hierarch. Navigation unterbricht den Kommunikationsfluss, Volltextsuche liefert bei generischen Begriffen zu viele Ergebnisse. Die Limitierungen wurden hinsichtl. Skalierbarkeit & Nutzerakzeptanz strukturiert erfasst.
**Ergebnis:** Anforderungskatalog mit quantifizierten Schwellenwerten für ein KI-gestütztes Zuordnungssystem (u.a. max. Interaktionszeit <2 Sek., Trefferquote >90%).

### AP1.3 – Ableiten von Anforderungen an KI-gestütztes Verfahren: Mai 2022 – Jun 2022
Aus den Limitierungen der konventionellen Verfahren wurden funktionale & nicht-funktionale Anforderungen an ein agentenbasiertes System abgeleitet, insb. die Fähigkeit zur Kontextrekonstruktion aus fragmentierten Eingaben ohne explizite Nutzerzuordnung.
**Ergebnis:** Spezifikationsdokument mit definierten Anforderungen & Abnahmekriterien.

## AP2 – Projektstruktur-Modellierung & Datenintegration (Ontologie-Modellierung) Jul 2022 – Dez 2022

### AP2.1 – Modellieren der Projektstruktur-Taxonomie: Jul 2022 – Sep 2022
Entwurf einer formalen Taxonomie, die die drei Dimensionen der Projektkommunikation (Akteure, sachliche Struktur, Zeitachse) als Graphschema abbildet. Die Modellierung berücksichtigt hierarchische Projektstrukturen (Projekt → Teilprojekt → Aufgabe → Meilenstein) sowie organisatorische Zuordnungen.
**Ergebnis:** Formales Graphschema mit definierten Entitätstypen, Relationen & Konsistenzregeln.

### AP2.2 – Integrieren heterogener Datenquellen: Sep 2022 – Nov 2022
Entwurf & Implementierung einer einheitlichen API-Schicht, die sowohl den Volltextindex (für semantische Suche) als auch die relationale Projektdatenbank (für strukturierte Abfragen) über eine gemeinsame Schnittstelle zugänglich macht. Die API ermöglicht kombinierte Abfragen über beide Datenquellen.
**Ergebnis:** Einheitliche API mit dokumentierten Endpunkten für kombinierte Struktur- & Volltextabfragen.

### AP2.3 – Validieren der Schemaabdeckung: Nov 2022 – Dez 2022
Prüfung der Taxonomie an realen Projektdatenbeständen: Können alle relevanten Kommunikationsszenarien (Einzel-/Gruppennachrichten, Dateizuordnungen, Aufgabenreferenzen) durch das Graphschema abgebildet werden? Identifikation von Lücken & iterative Anpassung.
**Ergebnis:** Validierungsbericht mit Abdeckungsgrad & dokumentierten Schemaanpassungen.

## AP3 – Entwicklung des agentenbasierten Retrieval-Systems (NLP & mehrstufiges Retrieval) Jan 2023 – Dez 2023

### AP3.1 – Entwickeln des Primäragenten: Jan 2023 – Mai 2023
Entwurf & Implementierung eines KI-Agenten, der eingehende Kommunikationsfragmente analysiert. Der Agent extrahiert mittels Intent-Erkennung die Kommunikationsabsicht (Frage, Anweisung, Statusmeldung) & identifiziert mittels Entitätsextraktion projektrelevante Begriffe (Projektnamen, Aufgabenbezeichnungen, Personenreferenzen, Zeitangaben).
**Ergebnis:** Funktionsfähiger Primäragent mit dokumentierter Extraktionspräzision auf Testdatensatz.

### AP3.2 – Implementieren des mehrstufigen Retrieval: Mai 2023 – Sep 2023
Entwicklung des iterativen Eingrenzungsprozesses: Der Agent generiert aus den extrahierten Entitäten strukturierte Datenbankabfragen, wertet die Ergebnismenge aus & verfeinert die Abfragen schrittweise, bis die Kandidatenmenge auf max. 5-10 Zuordnungsvorschläge konvergiert. Dabei wird der beschränkte LLM-Kontext durch gezielte API-Abfragen kompensiert.
**Ergebnis:** Mehrstufiger Retrieval-Algorithmus mit definierten Konvergenzbedingungen & Abbruchkriterien.

### AP3.3 – Entwickeln des probabilistischen Re-Rankings: Sep 2023 – Dez 2023
Implementierung eines Ranking-Moduls, das die vom Retrieval gelieferten Kandidaten anhand v. Kontexthistorie (vorherige Kommunikation des Nutzers), semantischer Ähnlichkeit (Nachrichteninhalt vs. Projektbeschreibung) & zeitlicher Relevanz gewichtet. Die Gewichtung der Faktoren wurde experimentell optimiert.
**Ergebnis:** Re-Ranking-Modul mit dokumentierten Gewichtungsparametern & Ranking-Metriken.

## AP4 – LLM-Backend-Evaluation & Optimierung (Benchmarking & Prompt Engineering) Jan 2024 – Aug 2024

### AP4.1 – Vergleichen verschiedener LLM-Backends: Jan 2024 – Apr 2024
Systematischer Vergleich von vier LLM-Backends (Mistral lokal, Llama lokal, Claude API, GPT API) hinsichtl. Extraktionsqualität, Kontextverständnis & Zuordnungsgüte. Für jedes Backend wurden identische Testszenarien durchgeführt & Präzision, Recall & F1-Score erfasst.
**Ergebnis:** Vergleichsmatrix mit quantifizierten Leistungskennwerten pro Backend & Empfehlung für produktiven Einsatz.

### AP4.2 – Optimieren der Agenten-Instruktionen: Apr 2024 – Jun 2024
Iterative Verbesserung der Agenten-Anweisungen (System-Prompts & Handlungsregeln) für domänenspezifische Zuordnung. Dabei wurde systematisch untersucht, welche Instruktionsformate (strukturierte Regeln vs. Few-Shot-Beispiele vs. Rollenanweisungen) die höchste Zuordnungspräzision liefern.
**Ergebnis:** Optimiertes Instruktionsset mit dokumentierter Präzisionssteigerung ggü. Baseline.

### AP4.3 – Evaluieren bei variierender Kontextfenstergröße: Jun 2024 – Aug 2024
Untersuchung des Einflusses der Kontextfenstergröße auf die Zuordnungsgüte. Dabei wurde getestet, wie sich unterschiedl. Mengen an Kontexthistorie (letzte 5, 10, 20, 50 Nachrichten) auf die Trefferquote des Mapping auswirken & ab welchem Punkt die Zuordnungsgüte bei steigender Kontextmenge nicht weiter verbessert wird.
**Ergebnis:** Dokumentierte Kontext-Leistungskurve mit optimalem Kontextfenster-Parameter.

## AP5 – Integration & Validierung (Systemintegration & statist. Validierung) Sep 2024 – Dez 2025

### AP5.1 – Integrieren in die Kommunikationsplattform: Sep 2024 – Feb 2025
Integration des Mapping-Systems in die bestehende Kommunikationsplattform: Echtzeit-Zuordnungsvorschläge werden bei jeder Nachrichteneingabe angezeigt. Nutzer können Vorschläge bestätigen, korrigieren oder verwerfen. Korrektur-Feedback fließt in die Verbesserung des Re-Rankings zurück.
**Ergebnis:** Integriertes System mit Echtzeit-Zuordnungsvorschlägen & Feedback-Schleife.

### AP5.2 – Validieren der Trefferquote: Feb 2025 – Jul 2025
Statistische Validierung der Zuordnungsgüte an realen Kommunikationsdaten über einen definierten Testzeitraum. Erfassung von Trefferquote auf Rang 1, Rang 1-2 & Rang 1-5 sowie der Fehlvorschlagsrate. Vergleich mit definierten Abnahmekriterien (>90% Treffer auf Rang 1-2, <30% Fehlvorschläge).
**Ergebnis:** Validierungsbericht mit statistisch belastbaren Kennzahlen zur Zuordnungsgüte.

### AP5.3 – Evaluieren der Skalierbarkeit: Jul 2025 – Dez 2025
Untersuchung der Systemleistung bei wachsenden Projektdatenbeständen: Wie verändert sich die Zuordnungsgüte & -geschwindigkeit bei 10, 50, 100 & 500 aktiven Projekten? Ab welcher Datenbankgröße degradiert die Konvergenz des mehrstufigen Retrievals?
**Ergebnis:** Skalierungsbericht mit dokumentierten Leistungsgrenzen & Optimierungsempfehlungen.
