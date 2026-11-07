---
title: "Use Case – UC-07 Antrag einreichen"
linkTitle: "UC-07 Antrag einreichen"
type: use-case
description: "Der Berater reicht den vollständigen Antrag ein; CredEx übermittelt das Dossier an die Glarner KB."
weight: 9
tags: [antrag, dokument, pflichtdokument, protokolleintrag, berater, kreditnehmer]
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

# Use Case – UC-07 Antrag einreichen

## Überblick

Der Berater reicht den vollständigen Antrag ein; CredEx übermittelt das Dossier an die Glarner KB. Entspricht **Prozessschritten 4.1 – 4.5**.[^business-process] Siehe auch [Use-Case-Diagramm](../useCaseDiagram.md) und [Soll-Prozess](../../business_process/businessProcess.md). Priorität Must, Wichtigkeit hoch, technologisches Risiko gering. Nur in der Übersicht möglich – die Partner-KI hat kein Werkzeug zum Einreichen. Im Detail spezifiziert.

---

## Vorbedingungen

- Der Antrag hat `status = IN_ERFASSUNG`
- Kein Dokument des Antrags hat `status = UNSICHER`

## Nachbedingungen

**Erfolg:**
- Antrag mit `status = EINGEREICHT` und `eingereichtAm`
- Alle zugeordneten Dokumente mit `status = EINGEREICHT`
- Dossier über die bestehende Schnittstelle an die Glarner KB übermittelt, Protokolleintrag geschrieben
- Keine Ablage über den MCP-Server mehr möglich

**Fehler – unvollständig:**
- Einreichen gesperrt mit Hinweis auf die fehlenden Pflichtdokumente

**Fehler – Übermittlung gescheitert:**
- Antrag bleibt `IN_ERFASSUNG`, Meldung an den Berater

---

## Beschreibung

Der Berater klickt in der Übersicht auf «Einreichen». CredEx prüft die Vollständigkeit (UC-05, «include»). Ist noch eine Zuordnung unsicher, bleibt das Einreichen gesperrt (1x). Fehlen Pflichtdokumente, ist das Einreichen ebenfalls gesperrt: Der Berater beschafft die Unterlagen selbst beim Kreditnehmer und legt sie nach – über seine KI (UC-04) oder selbst im Upload-Feld (2a). Ist alles vorhanden, übermittelt CredEx das Dossier über die bestehende Schnittstelle an die Glarner KB, setzt Antrag und Dokumente auf eingereicht und protokolliert die Einreichung. Scheitert die Übermittlung, bleibt der Antrag offen und der Berater erhält eine Meldung (3x); wie sich die bestehende Schnittstelle dabei verhält, ist offen.

---

## Qualitätsanforderungen

- [NFA-05 Koexistenz](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-08 Verfügbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-11 Integrität](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-12 Nachweisbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)

---

## Aktivitätsdiagramm

![Aktivitätsdiagramm – UC-07 Antrag einreichen](antragEinreichen.puml)

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
