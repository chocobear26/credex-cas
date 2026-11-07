---
title: "Partner"
type: entity
description: "Ein Distributionspartner von CredEx – Bank, Versicherung oder Broker –, der Hypothekaranträge über die Plattform einreicht."
weight: 1
tags: [partner]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Partner

Ein Distributionspartner von CredEx – Bank, Versicherung oder Broker –, der Hypothekaranträge über die Plattform einreicht. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** existiert in der CredEx-Plattform (Abgleich mit dem CredEx-Datenmodell offen)

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| name | String | Name des Partners |
| typ | Enum | BANK, VERSICHERUNG, BROKER |
