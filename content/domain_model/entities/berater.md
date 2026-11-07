---
title: "Berater"
type: entity
description: "Eine Person beim Partner, die Anträge erfasst und einreicht – Kundenberaterin einer Bank oder selbständiger Hypothekarbroker."
weight: 3
tags: [berater]
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

# Berater

Eine Person beim Partner, die Anträge erfasst und einreicht – Kundenberaterin einer Bank oder selbständiger Hypothekarbroker. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** existiert in der CredEx-Plattform (Abgleich mit dem CredEx-Datenmodell offen)

Jeder Berater gehört zu genau einem [Team](team.md); er sieht über seine KI die Anträge seines Teams (Teamentscheid 07.11.2026, [CR-1.2](../../sources/cr_1_2.md)).

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| name | String | Name der Person |
| eMail | String | E-Mail-Adresse, zugleich Anmeldename |
