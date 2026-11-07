---
title: "Architektur – Ablauf über MCP"
linkTitle: "Ablauf über MCP"
type: architecture-view
description: "Ein vollständiger Durchlauf als Sequenzdiagramm: Ablage durch die Partner-KI, Prüfen in der Übersicht oder per Auftrag, Einreichen."
weight: 2
tags: [berater, antrag, pflichtdokument, dokument, zuordnung, protokolleintrag, team]
sources:
  - id: system-context
    resource: /system_context/systemContext.md
  - id: mcp-schnittstelle
    resource: /interface/mcpSchnittstelle.md
  - id: zuordnung-bestaetigen
    resource: /use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Architektur – Ablauf über MCP

## Überblick

Das Sequenzdiagramm zeigt, wie MCP im Fall CredEx funktioniert: Der Berater spricht mit seiner eigenen KI; die KI ruft die Werkzeuge des MCP-Servers auf; der MCP-Server arbeitet mit der bestehenden Plattform und schreibt das Protokoll. Einreichen geht nur in der Übersicht. Es ergänzt die [Komponenten](komponenten.md) und die Spezifikation der [MCP-Schnittstelle](../interface/mcpSchnittstelle.md); die Statuswerte stammen aus dem [Zustandsdiagramm Dokument](../state_chart/dokumentStateChart.md).

---

## Diagramm

![Sequenzdiagramm – ein Antrag von der Ablage bis zur Einreichung](mcpAblauf.puml)

---

## Elemente

- **Schritte 2 bis 6** entsprechen UC-02 und UC-03, **7 bis 13** UC-04, **14 bis 16** UC-05, **17 bis 23** UC-06 (zwei Wege), **24 bis 29** UC-07.
- **MCP** ist das Protokoll zwischen Partner-KI (Client) und CredEx (Server): Die KI erfährt beim Verbinden, welche Werkzeuge es gibt und welche Parameter sie brauchen, und ruft sie bei Bedarf auf. CredEx baut die Schnittstelle einmal; jede MCP-fähige KI dockt an.
