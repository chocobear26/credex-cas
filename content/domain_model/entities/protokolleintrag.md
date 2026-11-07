---
title: "Protokolleintrag"
type: entity
description: "Ein Eintrag im Protokoll eines Antrags: wer wann was getan hat, KI oder Berater."
weight: 11
tags: [protokolleintrag]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Protokolleintrag

Ein Eintrag im Protokoll eines Antrags: wer wann was getan hat, KI oder Berater. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** neu in Phase 1

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| zeitpunkt | DateTime | Zeitpunkt der Aktion |
| akteur | Enum | KI, BERATER |
| aktion | String | Ablage, Bestätigung, Umordnung, Verwerfen, Einreichung, abgelehnter Zugriff |
