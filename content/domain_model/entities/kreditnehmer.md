---
title: "Kreditnehmer"
type: entity
description: "Eine Person, für die ein Antrag gestellt wird; ein Antrag kann mehrere Kreditnehmer betreffen."
weight: 6
tags: [kreditnehmer]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Kreditnehmer

Eine Person, für die ein Antrag gestellt wird; ein Antrag kann mehrere Kreditnehmer betreffen. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** existiert in der CredEx-Plattform (Abgleich mit dem CredEx-Datenmodell offen)

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| name | String | Name der Person |
| kundennummer | String | Kundennummer beim Partner |
