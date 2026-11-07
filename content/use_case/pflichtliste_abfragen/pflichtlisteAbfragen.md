---
title: "Use Case – UC-03 Pflichtliste abfragen"
linkTitle: "UC-03 Pflichtliste abfragen"
type: use-case
description: "Die Partner-KI fragt für einen Antrag die Pflichtdokumente mit Bezug und Status ab."
weight: 5
tags: [antrag, pflichtdokument, dokumenttyp, kreditnehmer]
sources:
  - id: use-case-diagram
    resource: /use_case/useCaseDiagram.md
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Use Case – UC-03 Pflichtliste abfragen

## Überblick

Die Partner-KI fragt für einen Antrag die Pflichtdokumente mit Bezug und Status ab. Entspricht **Prozessschritten 1.4 – 1.5**.[^business-process] Siehe auch [Use-Case-Diagramm](../useCaseDiagram.md) und [Soll-Prozess](../../business_process/businessProcess.md). Priorität Must, technologisches Risiko gering. Werkzeug `credex_pflichtliste`. Wird von UC-04 immer mit ausgeführt («include»).

---

## Vorbedingungen

- Der Antrag ist bekannt (UC-02) und hat `status = IN_ERFASSUNG`

## Nachbedingungen

**Erfolg:**
- Die Partner-KI kennt jedes Pflichtdokument des Antrags mit ID, Dokumenttyp, Bezug (Kreditnehmer oder Objekt) und Status, dazu das Ziel «weiteres Dokument»

**Fehler – Antrag unbekannt oder keine Berechtigung:**
- Keine Daten geliefert, Fehlermeldung an die Partner-KI

---

## Beschreibung

Damit die Partner-KI jede Datei dem richtigen Pflichtdokument zuordnen kann, braucht sie die Pflichtliste des Antrags: welche Unterlagen für welchen Kreditnehmer oder für das Objekt verlangt sind und welche schon vorhanden sind. CredEx liefert die Liste mit den Bezeichnungen der Dokumenttypen und dem zusätzlichen Ziel «weiteres Dokument» für Dateien, die zu keinem Pflichtdokument passen.

---

## Qualitätsanforderungen

- [NFA-10 Vertraulichkeit](../../requirements/nichtfunktionaleAnforderungen.md)

---

## Aktivitätsdiagramm

![Aktivitätsdiagramm – UC-03 Pflichtliste abfragen](pflichtlisteAbfragen.puml)

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
