---
title: "Dokument"
type: entity
description: "Eine Datei, die im Antrag abgelegt wurde – ganz oder als Seitenbereich eines Sammel-PDF."
weight: 8
tags: [dokument]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T11:15:00Z
---

# Dokument

Eine Datei, die im Antrag abgelegt wurde – ganz oder als Seitenbereich eines Sammel-PDF. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** existiert in der CredEx-Plattform (Abgleich mit dem CredEx-Datenmodell offen)

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| dateiname | String | Name der abgelegten Datei |
| quelldatei | String | Ursprüngliche Datei, wenn das Dokument aus einem Sammel-PDF stammt |
| seiten | String | Seitenbereich in der Quelldatei, z.B. 1-3 |
| hochgeladenAm | DateTime | Zeitpunkt der Ablage |
| status | Enum | ABGELEGT, VON_KI_ZUGEORDNET, UNSICHER, BESTAETIGT, VERWORFEN, EINGEREICHT |
