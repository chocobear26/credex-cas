---
title: "Protokolleintrag"
type: entity
description: "Ein Eintrag im Protokoll eines Antrags: wer wann was getan hat, KI oder Berater."
weight: 12
tags: [protokolleintrag]
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

# Protokolleintrag

Ein Eintrag im Protokoll eines Antrags: wer wann was getan hat, KI oder Berater. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** neu in Phase 1

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| zeitpunkt | DateTime | Zeitpunkt der Aktion |
| akteur | Enum | KI, BERATER, BERATER_VIA_KI (der Berater hat die Aktion per ausdrücklichem Auftrag an seine KI ausgelöst) |
| aktion | String | Ablage, Bestätigung, Umordnung, Verwerfen, Einreichung, abgelehnter Zugriff; bei BERATER_VIA_KI mit dem Auftrag des Beraters im Wortlaut |
