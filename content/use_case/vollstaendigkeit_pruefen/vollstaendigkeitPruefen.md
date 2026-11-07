---
title: "Use Case – UC-05 Vollständigkeit prüfen"
linkTitle: "UC-05 Vollständigkeit prüfen"
type: use-case
description: "CredEx meldet, welche Pflichtdokumente eines Antrags fehlen oder unsicher sind."
weight: 7
tags: [antrag, pflichtdokument, dokument, berater]
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

# Use Case – UC-05 Vollständigkeit prüfen

## Überblick

CredEx meldet, welche Pflichtdokumente eines Antrags fehlen oder unsicher sind. Entspricht **Prozessschritten 2.6 und 4.1**.[^business-process] Siehe auch [Use-Case-Diagramm](../useCaseDiagram.md) und [Soll-Prozess](../../business_process/businessProcess.md). Priorität Must, technologisches Risiko gering. Werkzeug `credex_vollstaendigkeit_pruefen`; wird von UC-07 immer mit ausgeführt («include»).

---

## Vorbedingungen

- Der Antrag hat `status = IN_ERFASSUNG`

## Nachbedingungen

**Erfolg:**
- Zusammenfassung mit der Liste der Pflichtdokumente mit `status = FEHLT` und `status = UNSICHER` und einem Link zur Übersicht

**Fehler – Antrag unbekannt:**
- Fehlermeldung

---

## Beschreibung

Nach der Ablage fragt die Partner-KI, ob das Dossier vollständig ist, und meldet dem Berater, was fehlt oder unsicher ist, mit Link zur Übersicht. Dieselbe Prüfung läuft beim Einreichen (UC-07). Grundlage ist der abgeleitete Status jedes Pflichtdokuments.

---

## Qualitätsanforderungen

- [NFA-01 Korrektheit](../../requirements/nichtfunktionaleAnforderungen.md)

---

## Aktivitätsdiagramm

![Aktivitätsdiagramm – UC-05 Vollständigkeit prüfen](vollstaendigkeitPruefen.puml)

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
