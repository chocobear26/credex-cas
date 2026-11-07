---
title: "Pflichtdokument"
type: entity
description: "Eine Unterlage, die CredEx für einen Antrag verlangt – heute ein Upload-Feld in Schritt 5."
weight: 10
tags: [pflichtdokument]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Pflichtdokument

Eine Unterlage, die CredEx für einen Antrag verlangt – heute ein Upload-Feld in Schritt 5. Teil des [Fachklassenmodells](../domainModel.md).

**Herkunft:** existiert in der CredEx-Plattform (Abgleich mit dem CredEx-Datenmodell offen)

**Ableitung des Status:** `FEHLT`, solange keine Zuordnung auf das Pflichtdokument verweist; `UNSICHER`, solange ein zugeordnetes Dokument den Status `UNSICHER` hat; sonst `VORHANDEN`. Der Status wird deshalb nicht in einem eigenen Zustandsdiagramm geführt, sondern folgt dem [Zustandsdiagramm Dokument](../../state_chart/dokumentStateChart.md).

## Attribute

| Attribut | Typ | Beschreibung |
|---|---|---|
| bezug | Enum | PERSON, OBJEKT |
| status | Enum | FEHLT, UNSICHER, VORHANDEN – abgeleitet aus den zugeordneten Dokumenten |
