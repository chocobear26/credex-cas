---
title: "Zuordnung"
type: entity
description: "Die Verknüpfung eines Dokuments mit einem Pflichtdokument oder als «weiteres Dokument», von der KI vorgeschlagen oder vom Berater bestätigt."
weight: 9
tags: [zuordnung]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
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
| quelle | Enum | KI, MENSCH (auch wenn der Berater per Auftrag an die KI bestätigt; der Protokolleintrag zeigt den Weg) |
| zeitpunkt | DateTime | Zeitpunkt der letzten Änderung |
