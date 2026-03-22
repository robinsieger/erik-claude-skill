# KI-basiertes agentengestütztes Kontextmapping fragmentierter Kommunikationseinheiten zur automatischen Zuordnung in mehrdimensionale Projektstrukturen

## Was ist das Ziel Ihres Vorhabens? Welche Herausforderung oder Problemstellung soll mit dem Vorhaben gelöst bzw. welche Wissenslücke soll mit dem Vorhaben geschlossen werden?

In der professionellen Projektkommunikation müssen Nachrichten, Dokumente & Aufgaben simultan drei Dimensionen zugeordnet werden: Akteure, sachl. Projektstruktur (Projekte, Teilschritte, Meilensteine) & Zeitachse. Bestehende Werkzeuge decken jeweils nur eine Dimension ab: Chat-Systeme (Slack, MS Teams) bilden Personenkanäle, PM-Tools (Asana, Trello, ClickUp) verwalten Aufgabenstrukturen, E-Mail bietet theoret. Mehrdimensionalität ohne prozessurale Einbindung. Keines ordnet unstrukturierte Kommunikationseinheiten autom. in eine mehrdimensionale Projektmatrix ein.
Ziel war es zu untersuchen, ob ein agentenbasiertes KI-System aus kurzen, kontextarmen Kommunikationsfragmenten (1–3 Sätze) zuverlässig die korrekte Zuordnung zu einer dreidimensionalen Projektstruktur ableiten kann. Dazu wurde ein mehrstufiges Retrieval-Verfahren entwickelt: Ein Primäragent analysiert eingehende Nachrichten mittels Intent-Erkennung & Entitätsextraktion, generiert strukturierte Abfragen an heterogene Datenquellen (Volltextindex, relationale Projektdatenbank) & führt iterative Eingrenzungsschritte durch, bis die Treffermenge auf wenige hochwahrscheinl. Zuordnungskandidaten konvergiert. Ein nachgelagertes probabilist. Re-Ranking bewertet Kandidaten anhand v. Kontexthistorie & semant. Ähnlichkeit.
Ergebnis ist ein validiertes Verfahren zur autom. Kontextzuordnung mit einer Ziel-Trefferquote v. >90 % auf den ersten zwei Vorschlagsrängen.

(1.431 / 1.500 Zeichen)

## Inwieweit hebt sich das angestrebte Produkt, Verfahren oder die Dienstleistung vom Stand der Technik ab?

Zum Vorhabenbeginn 2022 existierte kein Verfahren, das natürlichsprachl. Kommunikationsfragmente autom. in mehrdimensionale Projektstrukturen einordnet. Tools wie Slack, Teams, Asana & ClickUp trennen Kommunikation & Projektstruktur. Konventionelle Ansätze (Hashtags, Baumnavigation, Volltextsuche) scheiterten.
Neu:
• Agentenbasiertes mehrstufiges Retrieval für Kontextmapping
• Iterative Eingrenzung bei begrenztem LLM-Kontextfenster
• Probabilist. Re-Ranking auf heterogenen Projektdaten

(490 / 500 Zeichen)

## Welche Arbeiten werden durchgeführt, um der zuvor benannten Herausforderung oder Problemstellung zu begegnen bzw. um die Wissenslücke zu schließen?

Zunächst wurden bestehende Zuordnungsverfahren (Hashtag-Selektion, hierarch. Navigation, Volltextsuche) evaluiert & deren Limitierungen hinsichtl. Nutzerakzeptanz dokumentiert (experimentelle Evaluation). Darauf wurde eine Projektstruktur-Taxonomie modelliert, die Akteure, Sachstruktur & Zeitachse als Graphschema abbildet (Ontologie-Modellierung). Heterogene Datenquellen (Volltextindex & relationale Projektdatenbank) wurden über eine einheitl. API integriert. Nun wurde ein agentenbasiertes Retrieval-System entwickelt, bei dem ein Primäragent Nachrichten mittels Intent-Erkennung & Entitätsextraktion analysiert, strukturierte Abfragen generiert & iterativ die Treffermenge eingrenzt (mehrstufiges Retrieval). Darauf aufbauend wurde ein probabilist. Re-Ranking implementiert, das Kandidaten anhand v. Kontexthistorie & semant. Ähnlichkeit bewertet. Final wurden versch. LLM-Backends (Mistral, Llama, Claude, GPT) hinsichtl. Extraktionsqualität & Zuordnungsgüte verglichen (Benchmarking).

(992 / 1.000 Zeichen)

## Welche wissenschaftlichen, technischen und/oder methodischen Unsicherheiten bestehen bei der Bearbeitung der Herausforderung oder Problemstellung?

Unklar ist, ob das agentenbasierte Retrieval aus kontextarmen Fragmenten (1–3 Sätze) bei begrenztem LLM-Kontextfenster zuverlässig auf die korrekte Projektzuordnung konvergiert. Bei Tausenden möglicher Zuordnungspunkte können semant. Überlappungen & unvollständige Nutzereingaben dazu führen, dass die iterative Eingrenzung in lokale Optima gerät & die Fehlvorschlagsrate über 30 % steigt — ab diesem Schwellenwert wird das System unbrauchbar. Dem wird mit mehrstufiger Abfragezerlegung, Kontexthistorie-Anreicherung & paralleler LLM-Evaluation entgegengewirkt. Dennoch könnte es scheitern, wenn die Konvergenz bei wachsender Projektdatenbank nicht skaliert.
Risikobehaftet ist die Kopplung v. datengetriebenem Retrieval & deterministischer Projektstruktur: Das LLM erzeugt Zuordnungshypothesen probabilistisch, das Graphschema prüft deterministische Konsistenzregeln. Es ist offen, ob diese Paradigmen stabil koppelbar sind, ohne dass Konflikte die Zuordnungsqualität unter die 90%-Schwelle drücken.

(1.000 / 1.000 Zeichen)

## Schlagwörter

1. Agentenbasiertes Retrieval
2. Kontextmapping
3. Projektkommunikation
4. Natural Language Processing
5. Intent-Erkennung
6. Mehrstufiges Information Retrieval
7. Probabilistisches Re-Ranking
8. Large Language Models
9. Ontologie-Modellierung
10. Mensch-Maschine-Interaktion

## Arbeitspakete (Kurzfassung)

1 Evaluation konventioneller Zuordnungsverfahren
1.1 Evaluieren bestehender Mapping-Ansätze (Hashtag, Navigation, Volltextsuche) (experimentelle Evaluation)
1.2 Dokumentieren von Limitierungen hinsichtl. Nutzerakzeptanz & Zuordnungspräzision (vergleichende Analyse)
1.3 Ableiten von Anforderungen an ein KI-gestütztes Zuordnungsverfahren (Anforderungsmodellierung)

2 Projektstruktur-Modellierung & Datenintegration
2.1 Modellieren einer Taxonomie für Akteure, Sachstruktur & Zeitachse (Ontologie-Modellierung)
2.2 Integrieren heterogener Datenquellen über einheitl. API (Datenfusion)
2.3 Validieren der Schemaabdeckung an realen Projektdatenbeständen (Schemavalidierung)

3 Entwicklung des agentenbasierten Retrieval-Systems
3.1 Entwickeln eines Primäragenten für Intent-Erkennung & Entitätsextraktion (NLP-Pipeline)
3.2 Implementieren mehrstufiger Datenbankabfragen mit iterativer Eingrenzung (mehrstufiges Retrieval)
3.3 Entwickeln eines probabilist. Re-Rankings anhand Kontexthistorie & semant. Ähnlichkeit (probabilist. Modellierung)

4 LLM-Backend-Evaluation & Optimierung
4.1 Vergleichen versch. LLM-Backends hinsichtl. Extraktionsqualität (Benchmarking)
4.2 Optimieren der Agenten-Instruktionen für domänenspezif. Zuordnung (Prompt Engineering)
4.3 Evaluieren der Zuordnungsgüte bei variierender Kontextfenstergröße (Parametervariation)

5 Integration & Validierung
5.1 Integrieren des Mapping-Systems in die Kommunikationsplattform (Systemintegration)
5.2 Validieren der Trefferquote an realen Kommunikationsdaten (statistische Validierung)
5.3 Evaluieren der Skalierbarkeit bei wachsenden Projektdatenbeständen (Lasttests)
