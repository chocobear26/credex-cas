---
title: "Berater/in"
type: actor
description: "Eine Person beim Partner, die Hypothekaranträge erfasst, die Zuordnungen prüft und einreicht."
weight: 1
tags: [berater, partner, ki-verbindung, antrag, zuordnung, kreditnehmer]
sources:
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Berater/in

**Art:** Primär

## Beschreibung

Eine Person beim Partner, die Hypothekaranträge erfasst und einreicht – entspricht der Fachklasse [Berater](../../domain_model/entities/berater.md). Es gibt zwei Ausprägungen: die Kundenberaterin eines grossen Partners mit Microsoft 365 und Copilot (Persona Sandra Keller, primär) und den selbständigen Hypothekarbroker ohne eigene IT (Persona Reto Frei, sekundär). Der Berater gibt seiner KI den Auftrag, prüft die Zuordnungen, beschafft fehlende Unterlagen selbst beim Kreditnehmer und reicht als einziger ein. «Der Berater soll beraten und nicht Daten abfüllen» (O. Braun, PostFinance). Entspricht 🟦 Berater/in im Soll-Prozess.

## Systemzugriff

Übersicht im CredEx-Tool für die Anträge in seinem Zugriffsbereich: Status je Pflichtdokument ansehen, Zuordnungen bestätigen, umordnen oder verwerfen, Antrag einreichen. Bei Brokern ohne IT: KiVerbindung selbst einrichten. Kein direkter Zugriff auf den MCP-Server – das tut seine KI.
