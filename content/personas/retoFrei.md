---
title: "Persona – Reto Frei"
linkTitle: "Reto Frei"
type: persona
description: "Reto Frei, R2 selbständiger Hypothekarbroker: sekundär Persona."
weight: 2
tags: [berater, antrag, dokument, pflichtdokument, zuordnung, ki-verbindung, kreditnehmer]
sources:
  - id: benutzerrollen
    resource: /personas/benutzerrollen.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:45:00Z
---

# Persona – Reto Frei

**Rolle:** R2 selbständiger Hypothekarbroker · **sekundär**

> «Ich habe keine IT-Abteilung. Wenn ich es nicht in zehn Minuten selbst einrichten kann, nutze ich es nicht.»
> Persona-Zitat, abgeleitet aus Interview T. Cruz, CTO CredEx: «zwei Welten», Broker ohne eigene IT

---

## Steckbrief

| Merkmal | Ausprägung |
|---|---|
| Betrieb | kleines Brokerbüro ohne eigene IT *(Annahme)* |
| CredEx | wichtiger Kanal für seine Abschlüsse |
| Werkzeuge | KI-Assistent wie ChatGPT oder Claude, Unterlagen im Ordner oder per Mail *(Annahme)* |
| Haltung zu KI | pragmatisch, muss sofort Zeit sparen *(Annahme)* |

## Ziele

- Schnell und vollständig einreichen, damit der Abschluss nicht verzögert wird
- Keine Einrichtung, keine zusätzliche Lizenz
- Mit der KI arbeiten, die er schon nutzt

## Frust heute

- Gleicher Upload-Aufwand wie Sandra, aber niemand nimmt ihm etwas ab
- Unterlagen in allen Formaten: Fotos, Scans, Mail-Anhänge
- Bisherige Lösungen hätten eigene Lizenzen und Integration verlangt

## Szenario mit der Lösung

1. Verbindet ChatGPT einmal mit CredEx: anmelden, Berechtigung bestätigen, fertig.
2. Gibt der KI die Handyfotos von Familie Weber: «Lade das in CredEx hoch.»
3. Prüft die unsicheren Zuordnungen in der Übersicht und reicht ein.

## Was sie von der Lösung braucht

- KiVerbindung ohne IT einrichten ([US-1.1](../epics/user_stories/us_1_1.md), NFA-15)
- Fotos und Scans werden erkannt und richtig zugeordnet ([US-4.1](../epics/user_stories/us_4_1.md))
- Funktioniert mit jeder KI: offener MCP-Standard ([E03](../decisions/e03OffenerMcpStattCopilot.md))

---

## Quellen und Annahmen

Interview T. Cruz, CTO CredEx (15.09.2026, Zeitmarken 1:20, 39:23, 43:44). Angaben mit *(Annahme)* sind in [V3](../validation/validierung.md) mit einem Broker zu prüfen.
