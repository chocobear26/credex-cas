---
title: "Use Case – UC-02 Offene Anträge abrufen"
linkTitle: "UC-02 Offene Anträge abrufen"
type: use-case
description: "Die Partner-KI ruft die offenen Anträge ab, auf die der angemeldete Berater zugreifen darf."
weight: 4
tags: [antrag, berater, kreditnehmer, pflichtdokument, protokolleintrag, ki-verbindung]
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

# Use Case – UC-02 Offene Anträge abrufen

## Überblick

Die Partner-KI ruft die offenen Anträge ab, auf die der angemeldete Berater zugreifen darf. Entspricht **Prozessschritten 1.2 – 1.3**.[^business-process] Siehe auch [Use-Case-Diagramm](../useCaseDiagram.md) und [Soll-Prozess](../../business_process/businessProcess.md). Priorität Must, technologisches Risiko gering. Werkzeug `credex_offene_antraege`.

---

## Vorbedingungen

- Eine gültige KiVerbindung besteht (UC-01)
- Der Berater hat der Partner-KI einen Auftrag gegeben

## Nachbedingungen

**Erfolg:**
- Die Partner-KI kennt die offenen Anträge (`status = IN_ERFASSUNG`) mit Kreditnehmer, Objekt und Anzahl Pflichtdokumente mit Status `FEHLT`

**Fehler – nicht angemeldet:**
- Keine Daten geliefert, Meldung an die Partner-KI

---

## Beschreibung

Die Partner-KI fragt ohne Antragsnummer nach den offenen Anträgen. CredEx prüft Identität und Berechtigung aus der KiVerbindung und liefert nur Anträge, auf die der Berater zugreifen darf. Gibt es genau einen offenen Antrag, arbeitet die Partner-KI damit weiter; gibt es mehrere, fragt sie den Berater. Ein Zugriff auf fremde Anträge wird abgelehnt und als Protokolleintrag festgehalten.

---

## Qualitätsanforderungen

- [NFA-10 Vertraulichkeit](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-12 Nachweisbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)

---

## Aktivitätsdiagramm

![Aktivitätsdiagramm – UC-02 Offene Anträge abrufen](offeneAntraegeAbrufen.puml)

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
