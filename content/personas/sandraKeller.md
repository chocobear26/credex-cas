---
title: "Persona – Sandra Keller"
linkTitle: "Sandra Keller"
type: persona
description: "Sandra Keller, R1 Kundenberaterin Hypotheken mit KI: primär Persona."
weight: 1
tags: [berater, antrag, dokument, pflichtdokument, zuordnung, ki-verbindung, kreditnehmer]
sources:
  - id: benutzerrollen
    resource: /personas/benutzerrollen.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Persona – Sandra Keller

**Rolle:** R1 Kundenberaterin Hypotheken mit KI · **primär**

> «Der Berater soll beraten und nicht Daten abfüllen.»
> Kernaussage O. Braun, Projektleiter Hypotheken PostFinance (Interview 17.09.2026)

---

## Steckbrief

| Merkmal | Ausprägung |
|---|---|
| Arbeitgeber | grosser Distributionspartner (Bank) |
| CredEx | ein Kanal unter mehreren |
| Werkzeuge | Microsoft 365 mit Copilot, Kundendossiers im DMS (SharePoint) |
| Haltung zu KI | offen, aber nur mit gleicher Qualität wie ein Mensch |
| Team | arbeitet mit einer Stellvertretung im selben [Team](../domain_model/entities/team.md) |

## Ziele

- Mehr Zeit für Beratung, weniger Administration
- Antrag schnell und vollständig einreichen
- Kontrolle behalten: Sie verantwortet, was eingereicht wird

## Frust heute

- 10 bis 20 Dokumente, jedes einzeln an der richtigen Stelle hochladen
- Sammel-PDFs der Kunden vorher von Hand trennen
- 15 bis 20 Minuten pro Antrag, rein administrativ
- Bei Wechsel oder Refinanzierung alles nochmals hochladen

## Szenario mit der Lösung

1. Sagt Copilot: «Lade die Unterlagen Müller in meinen offenen CredEx-Antrag hoch.»
2. Die KI holt die Dateien aus dem DMS, teilt Sammel-PDFs auf und ordnet sie den Pflichtdokumenten zu.
3. Die Übersicht zeigt: 14 vorhanden, 2 unsicher, 2 fehlen. Sie bestätigt eine Zuordnung in der Übersicht und die andere per Auftrag an Copilot.
4. Sie holt die fehlenden Unterlagen beim Kunden, legt sie nach und reicht ein.

## Was sie von der Lösung braucht

- Eine Übersicht, die auf einen Blick zeigt, was fehlt oder unsicher ist ([US-6.1](../epics/user_stories/us_6_1.md))
- Jede KI-Zuordnung bestätigen oder ändern können ([US-6.2](../epics/user_stories/us_6_2.md), [US-6.3](../epics/user_stories/us_6_3.md))
- Einreichen nur, wenn alles vollständig ist ([US-7.1](../epics/user_stories/us_7_1.md))
- Funktioniert in ihrem Copilot, ohne neues Tool ([US-4.1](../epics/user_stories/us_4_1.md))

---

## Quellen und Annahmen

Interview O. Braun, PostFinance (17.09.2026, Zeitmarken 0:40, 4:20, 12:26, 13:22, 18:45); Interview T. Cruz, CTO CredEx (15.09.2026). Das Szenario ist illustrativ. Zu validieren in [V2](../validation/validierung.md): Anzahl Dokumente, Zeitaufwand, Zugriff von Copilot auf Kundendokumente.
