---
title: "E08 – CredEx baut den MCP-Server selbst"
linkTitle: "E08 CredEx baut den MCP-Server selbst"
type: decision
description: "CredEx baut den MCP-Server selbst (entschieden, 2026-10-31)."
weight: 9
sources:
  - id: entscheide
    resource: /decisions/entscheide.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:45:00Z
---

# E08 – CredEx baut den MCP-Server selbst

**Status:** entschieden · **Datum:** 2026-10-31 · **Quelle:** Teamentscheid

## Kontext

Offen war, ob ein externer Lieferant den MCP-Server baut.

## Optionen

- Externer Entwicklungslieferant
- Interne Entwicklung bei CredEx

## Entscheid

Interne Entwicklung.

## Begründung

- Kleine Komponente, nahe an der Plattform
- Keine eigenen Wartbarkeits- und Lieferantenanforderungen nötig

## Folgen

Wartbarkeit im [NFA-Katalog](../requirements/nichtfunktionaleAnforderungen.md) bewusst ohne eigene Anforderung. Festgehalten in [CR-1.0](../sources/cr_1_0.md).
