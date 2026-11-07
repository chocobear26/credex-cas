---
title: "Berater"
type: entity
description: "Eine Person beim Partner, die Anträge erfasst und einreicht – Kundenberaterin einer Bank oder selbständiger Hypothekarbroker."
weight: 2
tags: [berater]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Berater

Eine Person beim Partner, die Anträge erfasst und einreicht – Kundenberaterin einer Bank oder selbständiger Hypothekarbroker. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** existiert in der CredEx-Plattform (Abgleich mit dem CredEx-Datenmodell offen)

Das Fachklassenmodell kennt keine Klasse `Team`. Die Anforderungen FA-01 und NFA-10 sprechen vom Team des Beraters; das ist ein offener Punkt (siehe [CR-1.0](../../sources/cr_1_0.md)).

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| name | String | Name der Person |
| eMail | String | E-Mail-Adresse, zugleich Anmeldename |
