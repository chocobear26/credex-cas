---
title: "Zustandsdiagramm – Antrag"
linkTitle: "Antrag"
type: state-chart
description: "Wie sich das Attribut status der Fachklasse Antrag in Phase 1 ändert."
weight: 2
tags: [antrag, berater, dokument, pruefer]
sources:
  - id: antrag
    resource: /domain_model/entities/antrag.md
  - id: use-case-diagram
    resource: /use_case/useCaseDiagram.md
  - id: antrag-einreichen
    resource: /use_case/antrag_einreichen/antragEinreichen.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-1
    resource: /sources/cr_1_1.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T09:55:00Z
---

# Zustandsdiagramm – Antrag

> [!NOTE] v1.1 – Geändert 2026-11-07
> Diagramm waagrecht, gemeinsamer Diagrammstil.

## Überblick

Dieses Zustandsdiagramm zeigt, wie sich das Attribut `status` der Fachklasse [Antrag](../domain_model/entities/antrag.md) in Phase 1 ändert. Phase 1 betrifft nur Schritt 5 «Hochladen» und das Einreichen; Erfassung, Prüfung und Freigabe sind bestehende Abläufe von CredEx und der Glarner KB. Siehe auch das [Use-Case-Diagramm](../use_case/useCaseDiagram.md).

---

## Diagramm

![Zustandsdiagramm – Antrag](antragStateChart.puml)

---

## Zustände

| Zustand | Beschreibung |
|---|---|
| **IN_ERFASSUNG** | Der Berater erfasst den Antrag; in Schritt 5 legen Partner-KI und Berater Dokumente ab. Nur in diesem Zustand nimmt der MCP-Server Dokumente an. |
| **EINGEREICHT** | Der Berater hat den vollständigen Antrag eingereicht; das Dossier ist an die Glarner KB übermittelt. Keine Ablage über den MCP-Server mehr möglich. |

---

## Rückverfolgung der Übergänge

| Übergang | Auslösende Aktivität | Use Case | Schritt im Aktivitätsdiagramm |
|---|---|---|---|
| IN_ERFASSUNG → EINGEREICHT | «CredEx-System setzt Antrag (status = EINGEREICHT)» | [UC-07 Antrag einreichen](../use_case/antrag_einreichen/antragEinreichen.md) | Nach erfolgreicher Übermittlung an die Glarner KB |

---

## Nicht abgedeckte Zustände

- **[*] → IN_ERFASSUNG** – Der Antrag entsteht in den Antragsschritten 1 bis 4, die nicht zu Phase 1 gehören.
- **IN_PRUEFUNG** und **FREIGEGEBEN** – Prüfung und Freigabe durch die Glarner KB laufen wie heute und sind nicht Teil von Phase 1. Ein Use Case der Glarner KB wäre nötig, um diese Übergänge zu modellieren.
