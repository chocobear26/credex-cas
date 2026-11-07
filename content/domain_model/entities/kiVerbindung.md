---
title: "KiVerbindung"
type: entity
description: "Die eingerichtete Verbindung zwischen der KI eines Beraters und dem MCP-Server von CredEx."
weight: 3
tags: [ki-verbindung]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# KiVerbindung

Die eingerichtete Verbindung zwischen der KI eines Beraters und dem MCP-Server von CredEx. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** neu in Phase 1

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| kiClient | String | Verwendeter KI-Client, z.B. Copilot, ChatGPT, Claude |
| berechtigungen | String | Freigegebene Werkzeuge und Datenbereich |
| gültigBis | DateTime | Ablauf der Anmeldung (Token) |
