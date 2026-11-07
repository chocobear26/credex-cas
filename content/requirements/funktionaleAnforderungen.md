---
title: "Funktionale Anforderungen – CredEx Phase 1"
linkTitle: "Funktionale Anforderungen"
type: requirement-catalog
description: "Die funktionalen Anforderungen FA-01 bis FA-10 mit Abnahmekriterium und Bezug auf User Stories und Use Cases."
weight: 2
tags: [antrag, pflichtdokument, dokument, zuordnung, protokolleintrag, berater, partner]
sources:
  - id: ki-verbinden
    resource: /use_case/ki_verbinden/kiVerbinden.md
  - id: offene-antraege-abrufen
    resource: /use_case/offene_antraege_abrufen/offeneAntraegeAbrufen.md
  - id: pflichtliste-abfragen
    resource: /use_case/pflichtliste_abfragen/pflichtlisteAbfragen.md
  - id: dokument-ablegen
    resource: /use_case/dokument_ablegen/dokumentAblegen.md
  - id: vollstaendigkeit-pruefen
    resource: /use_case/vollstaendigkeit_pruefen/vollstaendigkeitPruefen.md
  - id: zuordnung-bestaetigen
    resource: /use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md
  - id: antrag-einreichen
    resource: /use_case/antrag_einreichen/antragEinreichen.md
  - id: nutzung-auswerten
    resource: /use_case/nutzung_auswerten/nutzungAuswerten.md
  - id: epics
    resource: /epics/epics.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Funktionale Anforderungen – CredEx Phase 1

## Überblick

Die funktionalen Anforderungen beschreiben, was das System können muss. Quelle ist das Anforderungs-Excel der Gruppe (`Gruppe_6_CAS_BAM_Modul_2_CredEx_Funktionale_nichtfunktionale_Anforderungen.xlsx`, Stand 31.10.2026); die IDs sind dieselben. Abgeleitet sind sie aus den [User Stories](../epics/epics.md) und [Use Cases](../use_case/useCaseDiagram.md); die Qualitätsanforderungen stehen in den [nicht-funktionalen Anforderungen](nichtfunktionaleAnforderungen.md), die Werkzeuge in der [MCP-Schnittstelle](../interface/mcpSchnittstelle.md). Wichtigkeit Hoch = Must, Mittel = Should.

---

## Anforderungen

| ID | Funktion | Anforderung | Abnahmekriterium (Abnahme erfolgt, wenn …) | Bezug | Wichtigkeit |
|---|---|---|---|---|---|
| FA-01 | Anträge abrufen | Das System muss der angemeldeten Person die offenen Anträge ihres Teams mit Status und Anzahl offener Pflichtdokumente liefern. | Wenn im Test alle offenen Anträge des Teams mit korrektem Status und korrekter Anzahl offener Pflichtdokumente geliefert werden (Abgleich mit Testdaten). | [US-2.1](../epics/user_stories/us_2_1.md), [US-2.2](../epics/user_stories/us_2_2.md), [UC-02](../use_case/offene_antraege_abrufen/offeneAntraegeAbrufen.md) | Hoch |
| FA-02 | Pflichtliste | Das System muss pro Antrag die Pflichtliste mit ID, Bezug (Person oder Objekt) und Status liefern. | Wenn die Pflichtliste des Testantrags alle Pflichtdokumente mit ID, Bezug und Status enthält. | [US-3.1](../epics/user_stories/us_3_1.md), [UC-03](../use_case/pflichtliste_abfragen/pflichtlisteAbfragen.md) | Hoch |
| FA-03 | Dokument ablegen | Das System muss eine Datei mit Pflichtdokument und Konfidenz entgegennehmen, speichern und den Status nach der Konfidenzschwelle setzen. | Wenn eine Datei mit Konfidenz über der Schwelle den Status „zugeordnet“ und unter der Schwelle den Status „unsicher“ erhält. | [US-4.1](../epics/user_stories/us_4_1.md), [UC-04](../use_case/dokument_ablegen/dokumentAblegen.md) | Hoch |
| FA-04 | Dokument ablegen | Das System muss bei PDFs einen Seitenbereich übernehmen und nur diese Seiten ablegen (Sammel-PDF aufteilen). | Wenn bei Ablage mit Seitenbereich (z.B. S. 1 bis 3) nur diese Seiten gespeichert werden und als eigenes Dokument in der Übersicht erscheinen. | [US-4.2](../epics/user_stories/us_4_2.md), [UC-04](../use_case/dokument_ablegen/dokumentAblegen.md) | Mittel |
| FA-05 | Übersicht | Das System muss in der Übersicht pro Pflichtdokument Status, Datei, Quelle (KI oder Mensch) und Konfidenz anzeigen und sich selbst aktualisieren. | Wenn eine neue Ablage ohne Neuladen der Seite in der Übersicht erscheint, mit Status, Datei, Quelle und Konfidenz. | [US-6.1](../epics/user_stories/us_6_1.md), [US-5.1](../epics/user_stories/us_5_1.md) | Hoch |
| FA-06 | Prüfen | Das System muss der Beraterin ermöglichen, Zuordnungen zu bestätigen, einem anderen Pflichtdokument zuzuweisen oder zu verwerfen. | Wenn die Beraterin im Test eine Zuordnung bestätigen, umordnen und verwerfen kann und der Status jeweils korrekt wechselt. | [US-6.2](../epics/user_stories/us_6_2.md), [UC-06](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) | Hoch |
| FA-07 | Einreichen | Das System muss das Einreichen sperren, solange Zuordnungen unsicher sind oder Pflichtdokumente fehlen. | Wenn Einreichen mit mind. einer unsicheren Zuordnung oder einem fehlenden Pflichtdokument nicht möglich ist und ein Hinweis erscheint. | [US-7.1](../epics/user_stories/us_7_1.md), [UC-07](../use_case/antrag_einreichen/antragEinreichen.md) | Hoch |
| FA-08 | Einreichen | Das System darf über MCP kein Einreichen anbieten. | Wenn die MCP-Werkzeugliste kein Werkzeug zum Einreichen enthält und ein Einreichversuch über die KI scheitert. | [US-7.1](../epics/user_stories/us_7_1.md), GA3 | Hoch |
| FA-09 | Protokoll | Das System muss jede Ablage, Bestätigung, Umordnung und Einreichung mit Zeit, Akteur und Quelle protokollieren. | Wenn nach einem Testlauf jede durchgeführte Aktion mit Zeit, Akteur und Quelle im Protokoll steht. | [US-4.1](../epics/user_stories/us_4_1.md), [US-6.2](../epics/user_stories/us_6_2.md), GA4 | Hoch |
| FA-10 | Auswertung | Das System muss Kennzahlen pro Partner bereitstellen: Anträge über MCP, Dauer bis Einreichung, Anteil Bestätigungen. | Wenn die Auswertung pro Partner und Monat diese Kennzahlen korrekt ausweist (Abgleich mit den Messdaten des PoC). | [US-9.1](../epics/user_stories/us_9_1.md), [UC-09](../use_case/nutzung_auswerten/nutzungAuswerten.md) | Mittel |

---

## Offene Punkte

- **FA-07** ist gegenüber dem Excel vom 31.10.2026 geändert: kein Einreichen mit Begründung mehr (siehe [CR-1.0](../sources/cr_1_0.md)). Das Excel ist nachzuführen.
- **FA-01** spricht von den Anträgen des Teams; das Fachklassenmodell kennt keine Klasse Team.
