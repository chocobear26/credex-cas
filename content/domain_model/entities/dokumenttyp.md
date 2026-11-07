---
title: "Dokumenttyp"
type: entity
description: "Die Art einer Unterlage, z.B. Lohnausweis oder Grundbuchauszug, mit den erlaubten Dateiformaten."
weight: 11
tags: [dokumenttyp]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T11:15:00Z
---

# Dokumenttyp

Die Art einer Unterlage, z.B. Lohnausweis oder Grundbuchauszug, mit den erlaubten Dateiformaten. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** existiert in der CredEx-Plattform (Abgleich mit dem CredEx-Datenmodell offen)

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| bezeichnung | String | Name des Dokumenttyps |
| erlaubteFormate | String | Zulässige Dateiformate, z.B. PDF, JPG |
