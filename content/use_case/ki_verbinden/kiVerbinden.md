---
title: "Use Case – UC-01 KI mit CredEx verbinden"
linkTitle: "UC-01 KI mit CredEx verbinden"
type: use-case
description: "Partner-IT oder Berater/in verbindet einen KI-Client einmalig mit dem MCP-Server von CredEx."
weight: 3
tags: [ki-verbindung, berater, partner]
sources:
  - id: use-case-diagram
    resource: /use_case/useCaseDiagram.md
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Use Case – UC-01 KI mit CredEx verbinden

## Überblick

Partner-IT oder Berater/in verbindet einen KI-Client einmalig mit dem MCP-Server von CredEx. Entspricht **Prozessschritten 0.1 – 0.2**.[^business-process] Siehe auch [Use-Case-Diagramm](../useCaseDiagram.md) und [Soll-Prozess](../../business_process/businessProcess.md). Priorität Must (Pilot), technologisches Risiko mittel: Anmeldung über OAuth ist in den KI-Clients unterschiedlich gelöst. Im PoC vereinfacht ohne Anmeldung.

---

## Vorbedingungen

- Der Berater ist bei CredEx als Benutzer seines Partners erfasst
- Für den Berater besteht keine gültige KiVerbindung (`gültigBis` abgelaufen oder keine)

## Nachbedingungen

**Erfolg:**
- Eine KiVerbindung mit `kiClient`, `berechtigungen` und `gültigBis` ist angelegt
- Die Partner-KI sieht die Werkzeuge des MCP-Servers

**Fehler – Anmeldung abgelehnt:**
- Keine KiVerbindung angelegt, Meldung an die einrichtende Person

---

## Beschreibung

Die Partner-IT trägt die Adresse des MCP-Servers im KI-Client des Partners ein. Bei Brokern ohne eigene IT macht das der Berater selbst nach Anleitung. Beim ersten Aufruf meldet sich der Berater über den Identity Provider an (OAuth, pro Person); CredEx legt die KiVerbindung an und gibt nur die Werkzeuge und Anträge frei, die zur Person gehören. Ziel ist eine Einrichtung ohne Softwareinstallation in höchstens 30 Minuten pro KI-Client.

---

## Qualitätsanforderungen

- [NFA-04 Interoperabilität](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-10 Vertraulichkeit](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-15 Installierbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)

---

## Aktivitätsdiagramm

![Aktivitätsdiagramm – UC-01 KI mit CredEx verbinden](kiVerbinden.puml)

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
