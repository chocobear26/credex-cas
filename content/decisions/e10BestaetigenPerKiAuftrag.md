---
title: "E10 – Der Berater darf per Auftrag an seine KI bestätigen, ändern oder verwerfen"
linkTitle: "E10 Der Berater darf per Auftrag an seine KI bestätigen, ändern oder verwerfen"
type: decision
description: "Der Berater darf per Auftrag an seine KI bestätigen, ändern oder verwerfen (entschieden, 2026-11-07)."
weight: 11
sources:
  - id: entscheide
    resource: /decisions/entscheide.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:45:00Z
---

# E10 – Der Berater darf per Auftrag an seine KI bestätigen, ändern oder verwerfen

**Status:** entschieden · **Datum:** 2026-11-07 · **Quelle:** Teamentscheid; Rückfrage Medienbruch aus LNW 1

## Kontext

Der PoC bot dafür vier Werkzeuge an; im Konzept stand nur die Übersicht. Die Rückfrage aus Modul 1 betraf den Wechsel zwischen KI-Fenster und CredEx-Tool.

## Optionen

- Nur in der Übersicht
- Auch per ausdrücklichem Auftrag an die KI, protokolliert

## Entscheid

Auch per Auftrag an die KI, nur mit ausdrücklichem Auftrag im Pflichtfeld und protokolliert als BERATER_VIA_KI.

## Begründung

- Beseitigt den Medienbruch für die Kontrolle
- Der Entscheid bleibt beim Menschen, der Auftrag steht im Protokoll
- Einreichen bleibt in der Übersicht (E04)

## Folgen

Vier zusätzliche [MCP-Werkzeuge](../interface/mcpSchnittstelle.md), FA-11, [US-6.3](../epics/user_stories/us_6_3.md), [UC-06](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md), Akteur BERATER_VIA_KI im [Protokolleintrag](../domain_model/entities/protokolleintrag.md). Festgehalten in [CR-1.2](../sources/cr_1_2.md).
