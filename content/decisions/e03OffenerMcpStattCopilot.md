---
title: "E03 – Offener MCP-Server statt eingebetteter Copilot-Lösung"
linkTitle: "E03 Offener MCP-Server statt eingebetteter Copilot-Lösung"
type: decision
description: "Offener MCP-Server statt eingebetteter Copilot-Lösung (entschieden, 2026-10-23)."
weight: 4
sources:
  - id: entscheide
    resource: /decisions/entscheide.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# E03 – Offener MCP-Server statt eingebetteter Copilot-Lösung

**Status:** entschieden · **Datum:** 2026-10-23 · **Quelle:** Teamentscheid

## Kontext

Eine im CredEx-Tool eingebettete Copilot-Lösung wurde als Alternative diskutiert.

## Optionen

- Offener MCP-Server, jede MCP-fähige KI kann andocken (Option A)
- Eingebettete Copilot-Lösung im CredEx-Tool (Option B)

## Entscheid

Offener MCP-Server.

## Begründung

- Partner nutzen verschiedene KIs (Copilot, ChatGPT, Claude)
- Kleinere Broker ohne Microsoft wären sonst ausgeschlossen
- Im PoC keine Energie in Details eines Anbieters

## Folgen

[MCP-Schnittstelle](../interface/mcpSchnittstelle.md); NFA-04 Interoperabilität; [Nutzwertanalyse](../evaluation/nutzwertanalyse.md) (A gegen B). Festgehalten in [CR-1.0](../sources/cr_1_0.md).
