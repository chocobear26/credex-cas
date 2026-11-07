---
title: "Team"
type: entity
description: "Eine Gruppe von Beratern eines Partners, die gemeinsam auf ihre Anträge zugreifen."
weight: 3
tags: [team, partner, berater, antrag]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:30:00Z
---

# Team

Eine Gruppe von Beratern eines Partners, die gemeinsam auf ihre Anträge zugreifen. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** neu in Phase 1 (Teamentscheid 07.11.2026); ob die CredEx-Plattform Teams schon kennt, ist mit dem CTO abzugleichen.

Ein Berater sieht über seine KI die offenen Anträge aller Berater seines Teams (FA-01, NFA-10). So kann eine Stellvertretung oder ein Backoffice Unterlagen ablegen, ohne fremde Partner zu sehen.

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| name | String | Name des Teams, z.B. Filiale oder Abteilung |
