---
title: "Validierung – PoC-Test heute gegen neu"
linkTitle: "PoC-Test"
type: validation
description: "Test des PoC mit 3 bis 5 Beratenden: Hypothesen H1 bis H3, Testdesign, Messgrössen und Ergebnisse."
weight: 2
tags: [berater, dokument, zuordnung, pflichtdokument, antrag]
sources:
  - id: poc-mcp-server
    resource: /prototype/pocMcpServer.md
  - id: nichtfunktionale-anforderungen
    resource: /requirements/nichtfunktionaleAnforderungen.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
  - id: cr-1-6
    resource: /sources/cr_1_6.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T11:00:54Z
---

# Validierung – PoC-Test heute gegen neu

## Ziel

Belegen, dass der Upload über die eigene KI die Arbeit erleichtert (Feedback Modul 1), und die offenen Zielwerte festlegen: Konfidenz-Schwelle, NFA-01 Korrektheit, NFA-02 Zeitverhalten.

## Vorgehen

| Element | Festlegung |
|---|---|
| Teilnehmende | 3 bis 5 Kundenberatende eines Partners, vermittelt über V1 |
| Design | Jede Person macht beide Varianten mit demselben Testdossier (17 Dateien): heute (Einzel-Upload im [Klickprototyp](../prototype/klickprototyp.md)) und neu ([PoC](../prototype/pocMcpServer.md)); Reihenfolge abwechselnd gegen Lerneffekte |
| Ablauf pro Person, ca. 30 Min. | Einführung 3 Min. · Variante 1 · Variante 2 · Kurzfragebogen und 2 offene Fragen · Testlauf zurücksetzen |
| Nachreichung | Eingereicht wird nur vollständig ([E09](../decisions/e09EinreichenNurVollstaendig.md)). Sobald die Testperson die Lücken sieht, legt die Testleitung die zwei fehlenden Pflichtdokumente aus `testdossier_nachreichung/` ins Dossier («der Kunde hat sie geschickt»); die Testperson lässt sie von der KI ablegen und reicht dann ein. Die Wartezeit dazwischen zählt nicht zur Dauer. |
| Messung | automatisch: Dauer bis Einreichung, Klicks, Bestätigungen und Umordnungen (`messungen.csv`); manuell: korrekte Zuordnungen gegen Musterlösung; Fragebogen 1 bis 5 |
| Termin | Testwoche 16. bis 18.11.2026 |

## Hypothesen

| Nr. | Hypothese | Ziel | Bezug |
|---|---|---|---|
| H1 | Die Dauer bis Einreichung sinkt deutlich | unter 2 Min. statt ca. 15 Min. für den Upload-Schritt | GA1, [US-4.1](../epics/user_stories/us_4_1.md) |
| H2 | Die KI ordnet richtig zu | mind. 90 % korrekt; höchstens 2 % falsch mit Status «zugeordnet» | NFA-01, Hypothesenbaum |
| H3 | Der Wechsel zwischen KI-Fenster und CredEx-Tool stört nicht | Bewertung mind. 4 von 5 | Feedback Modul 1, [US-6.3](../epics/user_stories/us_6_3.md) |

## Ergebnisse

| Messgrösse | Heute | Neu (PoC) | Bemerkung |
|---|---|---|---|
| Dauer bis Einreichung (mm:ss) | *ausstehend* | *ausstehend* | |
| Klicks | *ausstehend* | *ausstehend* | |
| Korrekte Zuordnungen (von 17) | entfällt | *ausstehend* | |
| Bestätigungen / Umordnungen | entfällt | *ausstehend* | |
| Zufriedenheit (1 bis 5) | *ausstehend* | *ausstehend* | |
| Wechsel KI-Fenster störend? (1 bis 5) | entfällt | *ausstehend* | |

Technischer Vorlauf am 07.11.2026 (ohne Testpersonen, Werkzeugaufrufe direkt): 17 Dateien abgelegt, Sammel-PDF korrekt aufgeteilt, 2 Zuordnungen unter der Schwelle erkannt, 2 fehlende Pflichtdokumente gemeldet, Einreichen gesperrt. Nach dem Nachführen des PoC am selben Tag wiederholt: eine Zuordnung per Auftrag an die KI bestätigt und als `BERATER_VIA_KI` mit Auftrag protokolliert; Einreichen mit Lücken vom Server abgelehnt, nach der Nachreichung möglich.

## Änderungen an den Artefakten

Nach dem Test: Schwelle, NFA-01 und NFA-02 festlegen; Business Case mit der gemessenen Zeit nachführen ([Umsetzungsplan](../delivery/umsetzungsplan.md)).
