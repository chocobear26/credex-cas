---
title: "Architektur – Komponenten"
linkTitle: "Komponenten"
type: architecture-view
description: "Die Komponenten von Phase 1 und ihre Abhängigkeiten: was neu ist und was CredEx und Dritte schon haben."
weight: 1
tags: [antrag, pflichtdokument, dokument, protokolleintrag, ki-verbindung, partner]
sources:
  - id: system-context
    resource: /system_context/systemContext.md
  - id: mcp-schnittstelle
    resource: /interface/mcpSchnittstelle.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Architektur – Komponenten

## Überblick

Die Komponentensicht verfeinert den [Systemkontext](../system_context/systemContext.md): Welche Bausteine baut CredEx neu, und worauf stützen sie sich? Rot umrandet ist neu in Phase 1. Die Schnittstelle zur Partner-KI ist in der [MCP-Schnittstelle](../interface/mcpSchnittstelle.md) spezifiziert, der Ablauf über alle Komponenten im [Sequenzdiagramm](mcpAblauf.md).

---

## Diagramm

![Komponentendiagramm – CredEx Phase 1](komponenten.puml)

---

## Elemente

| Komponente | Verantwortung | Neu? |
|---|---|---|
| MCP-Server | bietet der Partner-KI acht Werkzeuge an; prüft Token und Teamzugriff; setzt Status nach der Schwelle; schreibt Protokolleinträge | neu, intern gebaut ([E08](../decisions/e08McpServerIntern.md)) |
| Übersicht | Schritt 5 im CredEx-Tool: Status je Pflichtdokument, Prüfen, Einreichen | neu, Erweiterung des Tools |
| Protokoll | jede Aktion mit Zeit, Akteur und Quelle (FA-09, NFA-12) | neu |
| Auswertung | Kennzahlen pro Partner aus dem Protokoll (UC-09) | neu, ab R2 |
| CredEx-Plattform | Antrag, Pflichtliste, Dokumentenablage; Übermittlung an die Glarner KB | bestehend |
| Identity Provider | Anmeldung pro Berater (OAuth 2.1) | bestehend oder einzuführen – Klärung in V1 |
| Partner-KI, Partner-DMS | Verantwortung des Partners | Kontext |
