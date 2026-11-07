---
title: "Zuordnung"
type: entity
description: "Die Verknüpfung eines Dokuments mit einem Pflichtdokument oder als «weiteres Dokument», von der KI vorgeschlagen oder vom Berater bestätigt."
weight: 8
tags: [zuordnung]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Zuordnung

Die Verknüpfung eines Dokuments mit einem Pflichtdokument oder als «weiteres Dokument», von der KI vorgeschlagen oder vom Berater bestätigt. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** neu in Phase 1

Ziel `WEITERES_DOKUMENT` heisst: kein Pflichtdokument verknüpft (ersetzt die frühere Klasse Zusatzdokument). Die Schwelle für «unsicher» startet bei 0.80 und wird im PoC kalibriert.

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| ziel | Enum | PFLICHTDOKUMENT, WEITERES_DOKUMENT |
| konfidenz | Decimal | Sicherheit der KI zwischen 0 und 1; unter der Schwelle gilt die Zuordnung als unsicher |
| quelle | Enum | KI, MENSCH |
| zeitpunkt | DateTime | Zeitpunkt der letzten Änderung |
