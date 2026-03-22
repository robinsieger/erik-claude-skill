# Berater-Analyse: ML-basiertes adaptives Lern-Ökosystem zur datengetriebenen Abbruchprognose & Interventionssteuerung im Online-Spracherwerb

## Sofort-Handlungsbedarf (Top 3)

1. **Vorhabenzeitraum exakt klären:** Das Transkript nennt 2021 als Start, aber das Ende ist unklar. Samy erwaehnt "nach Juli 2022" habe man die Data Scientists verloren und die ML-Projekte pausiert. Der Berater muss den exakten Vorhabenzeitraum mit dem Kunden abstimmen (vermutlich Jan 2021 – Jul 2022) und im Antrag eintragen.

2. **ML-Modelldetails vom Kunden bestätigen lassen:** Im Transkript sagt Samy, er muesse die konkreten ML-Bibliotheken und den AWS-Service nachschauen. Der Berater muss sicherstellen, dass die im Antrag genannten Verfahren (Random Forest, Gradient Boosting, Logistic Regression) mit den tatsaechlich verwendeten uebereinstimmen. Auch die Markov-Ketten- und Shapley-Wert-Implementierung muss bestätigt werden.

3. **DOI/Literaturreferenz ergaenzen in Neuartigkeits-Sektion:** Aktuell fehlt eine wissenschaftliche Referenz. Eine DOI zum Thema Lernabbruchprognose im Online-Sprachunterricht wuerde die Neuartigkeitsargumentation erheblich staerken. Der Berater sollte den Kunden nach relevanten Publikationen fragen oder selbst recherchieren.

## Forschungsnarrativ

1. **WISSENSFRAGE:** Ist es moeglich, dass ML-basierte Klassifikationsverfahren auf rekonstruierten Subskriptionsketten mit starkem Klassenungleichgewicht zuverlaessig handlungsrelevante Interventionssignale zur Reduktion von Beteiligungsdrift bei ernsthaften Online-Sprachlernenden erzeugen koennen?

2. **WARUM OFFEN:** Zum Vorhabenbeginn 2021 existierten keine integrierten Verfahren fuer diesen spezifischen Anwendungsfall. Bestehende Loesungen (Duolingo, Babbel, Busuu) adressierten Gelegenheitslernende mit gamifizierten Ansaetzen. Kohortenbasierte Verbleibsmodelle boten keine individuelle Prognose. Die benoetigen Datenstrukturen (Subskriptionsketten mit Pausen, Reaktivierungen, Testzeitraeumen) existierten nicht.

3. **UNSICHERHEIT:** Es ist unsicher, ob die rekonstruierten Subskriptionsketten die tatsaechlichen Lernverlaeufe valide abbilden und ob ML-Modelle bei starkem Klassenungleichgewicht (nur 15% Abbrueche) und hochgradig nichtlinearen Verhaltensmustern (flexible Pausen/Reaktivierungen) ueberhaupt praezise genug prognostizieren koennen, um handlungsrelevante Interventionen abzuleiten. Zusaetzlich erzeugt die Kopplung datengetriebener und regelbasierter Attribution ein ungeloestes Spannungsfeld zwischen Modellkomplexitaet und Erklaerbarkeit.

## Simulierte Nachforderung

**Frage 1:** "Die Abgrenzung zum Stand der Technik in Ihrer Branche bzw. zu bestehenden Produkten, Verfahren oder Dienstleistungen Ihres Unternehmens ist unzureichend beschrieben. Bitte konkretisieren Sie, warum bestehende kohortenbasierte Verbleibsmodelle nicht ausreichen und worin genau die Limitation besteht."
- Status: ✅ Abgedeckt
- Der Antrag benennt konkret Duolingo, Babbel, Busuu, Goethe-Institut, Berlitz und deren Limitierungen (gamifizierte Mikrolern-Impulse vs. ernsthafte Lernende; keine individuelle Prognose bei kohortenbasierten Modellen).

**Frage 2:** "Welcher Verarbeitungs-/Prozessschritt wird konkret durch die ML-Modelle uebernommen und mit welchem Ansatz/Modell soll der Schritt umgesetzt werden? Wie sehen die Input-Daten und der erwuenschte Output aus?"
- Status: ✅ Abgedeckt
- Input: Rekonstruierte Subskriptionsketten (Teilnahme, Pausen, Rabattnutzung, Testverhalten). Modelle: Random Forest, Gradient Boosting, Logistic Regression. Output: Abbruchwahrscheinlichkeit auf 7-Tage-Horizont. Kanalwirkung: Markov-Ketten + Shapley-Wert.

**Frage 3:** "Bitte beschreiben Sie aussagekraeftig technische und/oder wissenschaftliche Risiken, die ueber methodeninhärente Risiken bzw. unvermeidbare Standardrisiken hinausgehen."
- Status: ⚠️ Teilweise abgedeckt
- Handlungsempfehlung: Das erste Risiko (Klassenungleichgewicht) koennte als methodeninhaerent gewertet werden. Der Berater sollte den Aspekt der **nichtlinearen Verhaltensmuster durch flexible Subskriptionsmodelle** staerker betonen und ggf. einen konkreten quantifizierten Schwellenwert ergaenzen (z.B. "Prognosequalitaet unter F1-Score von 0,6 wuerde Interventionssignale unbrauchbar machen"). Das zweite Risiko (Ground-Truth-Problem bei Attribution) ist stark und projektspezifisch.

**Frage 4:** "Bitte legen Sie das Vorhabenziel, dessen Anforderungen und Charakteristiken konkret und aussagekraeftig dar. Unterlegen Sie dies bitte mit Angaben zu angestrebten Parametern."
- Status: ✅ Abgedeckt
- Der Antrag nennt: 40.000 Klassen/Monat, 4 Sprachen, 15% Abbruchrate, 7-Tage-Prognosehorizont, Markov-Ketten + Shapley-Wert.

**Frage 5:** "Welche eigene Problemloesungsstrategie wird im Vorhaben verfolgt?"
- Status: ✅ Abgedeckt
- Risiko 1: Feature Engineering, Resampling, Schwellenwertoptimierung + Restrisiko. Risiko 2: Spannungsfeld wird benannt, Aufloesung als offen markiert.

**Frage 6:** "Bitte fuehren Sie aus, inwieweit die Auftragnehmer Taetigkeiten durchfuehren, die zur Zielerreichung des Vorhabens beitragen."
- Status: ⚠️ Teilweise abgedeckt
- Handlungsempfehlung: Im Transkript wird die Firma "Incremental" als externer Vendor fuer die Inkrementalitaetsanalyse erwaehnt. Der Berater muss klaeren, ob diese Zusammenarbeit im Vorhabenzeitraum lag und ob sie als Auftragsforschung deklariert werden muss. Falls ja: konkreten FuE-Beitrag des Auftragnehmers beschreiben. Falls nein (reiner SaaS-Einkauf): kann im Antrag weggelassen werden, muss aber bewusst entschieden werden.

## Qualitaetsbewertung pro Sektion

### Ziel-Sektion
- **Staerke:** Eroeffnung in Domaenensprache (Online-Spracherwerb, Beteiligungsdrift), starke Methodendichte (Gradient Boosting, Random Forest, Markov-Ketten, Shapley-Wert), konkrete Zahlen (40.000 Klassen/Monat, 4 Sprachen), ergebnisoffen formuliert.
- **BSFZ-Risiko:** Der Gutachter koennte fragen, ob die ELT-Migration nicht Routine-IT ist. Im Antrag ist sie als Voraussetzung fuer die ML-Forschung gerahmt, was korrekt ist, aber der Berater sollte sicherstellen, dass AP1 nicht zu viel Gewicht im Gesamtprojekt einnimmt.
- **Berater pruefen:** Sind die 40.000 Klassen/Monat fuer den Vorhabenbeginn 2021 korrekt? Zeitbezug validieren.

### Neuartigkeits-Sektion
- **Staerke:** Klare Benennung bestehender Loesungen mit Namen, kompakte Bullet-Struktur fuer Neuerungen.
- **BSFZ-Risiko:** Fehlende DOI-Referenz. Eine wissenschaftliche Publikation wuerde die Argumentation deutlich staerken.
- **Berater pruefen:** DOI recherchieren/vom Kunden erfragen; SdT-Zeitstempel "2021" ist korrekt gesetzt.

### Arbeiten-Sektion
- **Staerke:** Klarer temporaler Rhythmus (Zunaechst, Darauf, Nun, Parallel, Final), jeder Satz mit Methode, hohe Auslastung (99.6%).
- **BSFZ-Risiko:** Gering. Die Arbeitspakete sind konkret und methodisch benannt.
- **Berater pruefen:** Stimmt die chronologische Reihenfolge mit dem tatsaechlichen Projektverlauf ueberein?

### Risiko-Sektion
- **Staerke:** Zwei klar getrennte Risikoboecke, Problemloesungsstrategie vorhanden, Spannungsfeld (datengetrieben vs. regelbasiert) als Forschungssignal.
- **BSFZ-Risiko:** Klassenungleichgewicht koennte als methodeninhaerent gewertet werden. Der projektspezifische Aspekt (nichtlineare Subskriptionsverlaeufe) muss deutlicher herausgearbeitet werden.
- **Berater pruefen:** Quantifizierten Schwellenwert fuer Scheitern ergaenzen (z.B. F1-Score < 0.6).

## Offene Annahmen

- [ ] Vorhabenzeitraum Jan 2021 – Jul 2022 -- betrifft Sektion: Alle
- [ ] ML-Verfahren (Random Forest, Gradient Boosting, Log. Regression) sind korrekt -- betrifft Sektion: Ziel, Arbeiten, Risiko
- [ ] Markov-Ketten & Shapley-Wert wurden tatsaechlich implementiert (Samy erwaehnte nur "two models" ohne Details) -- betrifft Sektion: Ziel, Neuartigkeit, Risiko
- [ ] 40.000 Klassen/Monat zum Vorhabenbeginn 2021 ist korrekt -- betrifft Sektion: Ziel
- [ ] Ausgangs-Abbruchrate war 13% pro Monat (Zielwert 5%) -- betrifft Sektion: Ziel (nicht im Antrag erwaehnt wg. Produktversprechen-Gefahr)
- [ ] Keine weiteren externen Auftragnehmer ausser ggf. Incremental -- betrifft Sektion: ggf. Auftragsforschung
- [ ] Die Data Scientists haben das Unternehmen nach Juli 2022 verlassen -- betrifft Sektion: Vorhabenzeitraum
- [ ] Inkrementalitaetsprojekt (Vendor: Incremental) ist Teil des Vorhabens oder nicht -- betrifft Sektion: Auftragsforschung, Arbeitsplan
- [ ] Nudging-Framework und Mobile App wurden tatsaechlich prototypisch umgesetzt -- betrifft Sektion: AP5

## Zeichenauslastung

| Sektion      | Zeichen | Limit | Auslastung |
|--------------|---------|-------|------------|
| Titel        | 122     | 150   | 81.3%      |
| Ziel         | 1.472   | 1.500 | 98.1%      |
| Neuartigkeit | 494     | 500   | 98.8%      |
| Arbeiten     | 996     | 1.000 | 99.6%      |
| Risiko       | 982     | 1.000 | 98.2%      |
