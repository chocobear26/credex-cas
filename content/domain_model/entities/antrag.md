---
title: "Antrag"
type: entity
description: "Ein Hypothekarantrag eines Partners auf der CredEx-Plattform; in Phase 1 geht es um Schritt 5 «Hochladen»."
weight: 6
tags: [antrag]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T11:15:00Z
---

# Antrag

Ein Hypothekarantrag eines Partners auf der CredEx-Plattform; in Phase 1 geht es um Schritt 5 «Hochladen». Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** existiert in der CredEx-Plattform (Abgleich mit dem CredEx-Datenmodell offen)

Das Attribut `ausnahmeBegründung` aus dem Modell vom 30.10.2026 entfällt: Eingereicht wird nur ein vollständiger Antrag (siehe [CR-1.0](../../sources/cr_1_0.md)).

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| antragsnummer | String | Nummer des Antrags, z.B. D226894 |
| status | Enum | IN_ERFASSUNG, EINGEREICHT, IN_PRUEFUNG, FREIGEGEBEN |
| erfasstAm | DateTime | Beginn der Erfassung |
| eingereichtAm | DateTime | Zeitpunkt der Einreichung |
