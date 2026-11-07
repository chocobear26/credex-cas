---
title: "CredEx-System"
type: actor
description: "Die CredEx-Plattform mit den neuen Teilen von Phase 1: MCP-Server, Übersicht im CredEx-Tool und Protokoll."
weight: 3
tags: [antrag, dokument, zuordnung, pflichtdokument, protokolleintrag, ki-verbindung]
sources:
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-5
    resource: /sources/cr_1_5.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:19:37Z
---

# CredEx-System

**Art:** System

## Beschreibung

Die CredEx-Plattform mit den neuen Teilen von Phase 1: MCP-Server, Übersicht im CredEx-Tool und Protokoll. Prüft Berechtigungen, speichert Dokumente, setzt Status, schreibt Protokolleinträge und übermittelt das Dossier an die Glarner KB. Entspricht 🟨 CredEx-System im Soll-Prozess.[^business-process]

## Systemzugriff

Lese- und Schreibzugriff auf Antrag, Dokument, Zuordnung, Pflichtdokument und Protokolleintrag. Übermittlung an die Glarner KB über die bestehende, unveränderte Schnittstelle. Kein Zugriff auf das Partner-DMS.

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
