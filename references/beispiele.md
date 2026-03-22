# Echte bewilligte Antragstexte als Qualitätsanker

Diese Beispiele stammen aus positiv beschiedenen Anträgen. Sie zeigen das Qualitätsniveau, das du erreichen musst. Studiere Struktur, Dichte, Ton und Abstraktionsniveau — nicht den Inhalt kopieren.

---

## Beispiel 1: Containerterminal-Prognose (Bescheid 686-122-858, bewilligt ohne Nachforderung)

### Ziel (1.485 / 1.500 Zeichen)

Terminal Operating Systeme (TOS) von Containerterminals basieren im Wesentlichen auf Ist-Daten mit beschränkter/keiner Prognosefähigkeit zukünftiger Zustände. Datensilos, unvollständige Eingangsdaten (Schiffsanläufe, Verkehr, Wetter) und fehlende Integration zwischen Berth-, Yard- & Hinterlandplanung führen zu reaktiver statt vorausschauender Steuerung. Plausibilitätsanalysen in der Planung sind aufgrund sich ständig ändernden Voraussetzungen (techn. Ausfälle, Wetter, veränderte Ladelisten, beschädigte Container) nicht möglich.
Ziel ist die Entwicklung eines datengetriebenen, KI-gestützten Prognoseframeworks, das zukünftige Terminalzustände mehrere Tage präzise vorhersagt, Unsicherheiten quantifiziert und operative Entscheidungen datenbasiert unterstützt.
Heterogene TOS-, Verkehrs- & Sensordaten werden in einer domänenspezifischen Ontologie strukturiert und semantisch harmonisiert und fehlende Werte mittels generativer Modellierung (realistische Dummys) synthetisch ergänzt. Darauf aufbauend berechnet ein hybrides ML-Modell aus LSTM-Zeitreihen- und probabilistischen Graphenmodellen Zustandsprognosen mit Konfidenzintervallen. Eine stochastische Multi-Objective-Anpassung koppelt diese Prognosen mit heuristischen Verfahren (Genetische Algorithmen, Tabu Search), um zentrale Terminal-KPI (Household Moves, Leerfahrten, Operationszeiten) zu minimieren und die Planung m.H.d. generierten Entities in Szenarien alternativer Strategien zu simulieren (Monte-Carlo-Iteration).

**Was dieses Beispiel zeigt:**
- Eröffnung in Domänensprache (TOS, Berth, Yard, Hinterland) → dann Abstrahierung auf Methoden
- Kein Unternehmensname, kein Produkt — nur das Problem und der Ansatz
- Extreme Methodendichte: Ontologie, LSTM, Graphenmodelle, Genetische Algorithmen, Tabu Search, Monte-Carlo
- Domänenspezifische Fachbegriffe (Household Moves, Leerfahrten) zeigen Expertise
- Klammertechnik für Verdichtung: "(Schiffsanläufe, Verkehr, Wetter)", "(Genetische Algorithmen, Tabu Search)"
- "&" statt "und" durchgehend
- 99% Zeichenauslastung

### Neuartigkeit (493 / 500 Zeichen)

Aktuelle TOS (NavisN4, RBS, SAP) verarbeiten nur Echtzeit- & histor. Daten ohne probabilistisches Vorhersagen. Dieser Forschungsbedarf wird auch in der Literatur aufgezeigt: DOI:10.1057/s41278-023-00254-0.
Neu: Kombination bislang nicht integrierter Forschung:
Ontologiegestützte Datenfusion
Generative Modellierung
Hybride ML-Architektur aus LSTM- und probabilistischen Graphenmodellen
Stochastische Multi-Objective-Anpassung
Monte-Carlo-Simulation
Erklärbarkeit der Modellergebnisse

**Was dieses Beispiel zeigt:**
- Kommerzielle Produktnamen (NavisN4, RBS, SAP) IM STAND DER TECHNIK — das ist erlaubt und erwünscht
- DOI-Referenz für Glaubwürdigkeit
- "Neu:" gefolgt von 6 Bullet-Points — extrem kompakt
- 98.6% Zeichenauslastung

### Risiko (962 / 1.000 Zeichen)

Durch die Heterogenität in Ursprung und Format der Daten ist unklar, ob ein probabilistisches Graphenmodell die Interdependenzen zwischen Wetter, Kapazität und Verkehr mit allen Terminalprozessen ausreichend repräsentieren kann. Fehlerhafte Ontologieverknüpfungen oder nicht plausible synthetische Daten könnten zu verzerrten Eingangsverteilungen führen und die nachgelagerten Prognosemodelle unbrauchbar machen (Ontologie-Matching-Accuracy <0,85 führt zu signifikantem Performanceverlust).
Ein zweites Risiko ist die Modellkopplung von Prognose und resultierender Planung. Die komplexen Interdependenzen aus Liegeplatzplanung, Yard-Management und Transportprozessen werden als Kombination von Zeitreihen- und probabilistischen Graphenmodellen mit stochastischer Multi-Objective-Anpassung abgebildet und könnten zu nicht konvergenten oder instabilen Lösungen führen. Es ist offen, ob die angestrebte Rechenzeit <5 min und eine Prognosegüte >95 % erreichbar sind.

**Was dieses Beispiel zeigt:**
- Nach "ob" stehen immer drei Dinge: Modellname + Inputvariablen + Versagenskriterium
- Quantifizierte Scheitern-Schwellenwerte: "Accuracy <0,85", "Rechenzeit <5 min", "Prognosegüte >95%"
- 2 klar getrennte Risikoblöcke: (1) Daten/Ontologie, (2) Modellkopplung
- Domänenspezifische Begriffe (Liegeplatzplanung, Yard-Management)
- Keine methodeninhärenten Standardrisiken — alles projektspezifisch
- 96.2% Zeichenauslastung

### Arbeiten-Fließtext (994 / 1.000 Zeichen)

Zunächst werden heterogene TOS-, Verkehrs- & Wetterdaten erhoben, semantisch harmonisiert und in einer Ontologie strukturiert, die Entitäten (Schiffe, Container & Yard) abbildet. Datenlücken werden durch generative Modellierung ergänzt, wobei synthetische Dummy-Container basierend auf historischen Verteilungen erzeugt und mittels Ähnlichkeitsmetriken validiert werden. Nun werden LSTM-Zeitreihenmodelle trainiert, um terminale Zustände über mehrere Tage vorherzusagen, und mit probabilistischen Graphenmodellen kombiniert, die kausale Zusammenhänge zwischen Terminalkomponenten abbilden. Darauf werden die Prognoseergebnisse in ein stochastisches Entscheidungsmodell überführt, das mithilfe genetischer Algorithmen und Tabu Search konkurrierende Zielgrößen gewichtet und Handlungsszenarien berechnet. Final wird eine Monte-Carlo-Szenarien-Engine entwickelt, die alternative Strategien simuliert, während ein Accuracy-Tracker auf Basis von Reinforcement Learning die Modelle kontinuierlich anpasst.

**Was dieses Beispiel zeigt:**
- Strenger Temporalmarker-Rhythmus: "Zunächst... Nun... Darauf... Final..."
- Jeder Satz enthält eine Methode
- Keine kommerziellen Produktnamen im eigenen Ansatz
- 99.4% Zeichenauslastung

---

## Wie der Gutachter diese Anträge bewertet hat

Aus dem Bescheid 686 (Gutachter-Paraphrase):

> "Das Ziel des Vorhabens ist ein Prognose- und Entscheidungsframework zur Steuerung von Containerterminalprozessen. Bisher werden für diesen Anwendungszweck häufig Terminal Operating Systeme (TOS) genutzt, welche meist zur operativen Entscheidungsfindung auf vergangene und gegenwärtige Daten zurückgreifen. Im Gegensatz dazu soll im Rahmen dieses Vorhabens ein KI-gestütztes Prognosemodell entwickelt werden, welches zukünftige Terminalzustände vorhersagt und diese systematisch in operative Entscheidungsprozesse integriert. [...] Durch die Berücksichtigung von Prognosen in der Steuerung von Containerterminalprozessen und die dadurch verbesserte Effizienz des Containerterminals wird der Stand der Technik übertroffen."

Beachte: Der Gutachter paraphrasiert den Antrag in eigenen Worten. Die Struktur ist immer: "Ziel ist [X]. Bisher [Y]. Im Gegensatz dazu [Z]. Dadurch wird SdT übertroffen." Wenn dein Antrag so klar geschrieben ist, dass diese Paraphrase automatisch entsteht, ist er gut.

> "Anhand der Arbeitspakete lässt sich erkennen, dass es sich nicht um routinemäßige Arbeiten handelt. → Kriterium der Neuartigkeit erfüllt."

> "Es sind wissenschaftlich-technische Herausforderungen erkennbar, die die Zielerreichung des Vorhabens gefährden könnten. [...] → Kriterium der Unwägbarkeit erfüllt."

> "Ein inhaltlich strukturierter Arbeitsplan ist erkennbar. → Kriterium der Planmäßigkeit erfüllt."
