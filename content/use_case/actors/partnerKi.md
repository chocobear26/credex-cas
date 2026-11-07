---
title: "Partner-KI"
type: actor
description: "Der KI-Assistent des Partners, z.B."
weight: 2
tags: [berater, antrag, pflichtdokument, dokument, zuordnung]
sources:
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:30:00Z
---

# Partner-KI

**Art:** System

## Beschreibung

Der KI-Assistent des Partners, z.B. Microsoft Copilot, ChatGPT oder Claude. Läuft in der Umgebung und unter der Verantwortung des Partners, liest die Dateien aus dem Partner-DMS und ruft im Auftrag des Beraters die Werkzeuge des MCP-Servers auf. Die Partner-KI ist keine Fachklasse; ihre Verbindung zu CredEx ist die [KiVerbindung](../../domain_model/entities/kiVerbindung.md). Entspricht 🟪 Partner-KI im Soll-Prozess.

## Systemzugriff

Die acht Werkzeuge des MCP-Servers (siehe [MCP-Schnittstelle](../../interface/mcpSchnittstelle.md)) für die Anträge des Teams des angemeldeten Beraters. Vier davon (Bestätigen, Umordnen, Verwerfen, abgelegte Dokumente) nur mit ausdrücklichem Auftrag des Beraters. Kein Werkzeug zum Einreichen, kein Zugriff auf die Übersicht.
