---
title: "Use Case – UC-09 Nutzung auswerten"
linkTitle: "UC-09 Nutzung auswerten"
type: use-case
description: "Das CredEx Partnermanagement wertet Nutzung und Zeitersparnis pro Partner aus."
weight: 10
tags: [partner, antrag, protokolleintrag, zuordnung]
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

# Use Case – UC-09 Nutzung auswerten

## Überblick

Das CredEx Partnermanagement wertet Nutzung und Zeitersparnis pro Partner aus. Entspricht **Prozessschritten 6.1**.[^business-process] Siehe auch [Use-Case-Diagramm](../useCaseDiagram.md) und [Soll-Prozess](../../business_process/businessProcess.md). Priorität Should (Rollout), technologisches Risiko gering. Grundlage für die Gebühr der Partner und das Go/No-Go zu Phase 2.

---

## Vorbedingungen

- Es gibt eingereichte Anträge mit Protokolleinträgen

## Nachbedingungen

**Erfolg:**
- Kennzahlen pro Partner und Monat: Anzahl Anträge über den MCP-Server, Dauer bis Einreichung, Anteil Zuordnungen mit `quelle = MENSCH`

---

## Beschreibung

Am Monatsende wertet das Partnermanagement aus, wie viele Anträge jeder Partner über seine KI abgelegt hat, wie lange es von der ersten Ablage bis zur Einreichung gedauert hat und wie oft der Berater Zuordnungen bestätigen oder ändern musste. Die Zahlen stammen aus den Protokolleinträgen.

---

## Qualitätsanforderungen

- [NFA-12 Nachweisbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)

---

## Aktivitätsdiagramm

![Aktivitätsdiagramm – UC-09 Nutzung auswerten](nutzungAuswerten.puml)

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
