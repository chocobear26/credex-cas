---
title: "Use Case – UC-06 Zuordnung bestätigen oder ändern"
linkTitle: "UC-06 Zuordnung bestätigen oder ändern"
type: use-case
description: "Der Berater prüft eine Zuordnung in der Übersicht und bestätigt, ändert oder verwirft sie."
weight: 8
tags: [zuordnung, dokument, pflichtdokument, protokolleintrag, berater, antrag]
sources:
  - id: use-case-diagram
    resource: /use_case/useCaseDiagram.md
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-1
    resource: /sources/cr_1_1.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T09:55:00Z
---

# Use Case – UC-06 Zuordnung bestätigen oder ändern

> [!NOTE] v1.1 – Geändert 2026-11-07
> Aktivitätsdiagramm vereinfacht: ein Entscheid des Beraters, danach ein Block im CredEx-System. Inhalt und Aktivitätslabels unverändert.

## Überblick

Der Berater prüft eine Zuordnung in der Übersicht und bestätigt, ändert oder verwirft sie. Entspricht **Prozessschritten 3.1 – 3.4**.[^business-process] Siehe auch [Use-Case-Diagramm](../useCaseDiagram.md) und [Soll-Prozess](../../business_process/businessProcess.md). Priorität Must, Wichtigkeit hoch, technologisches Risiko gering. Im Detail spezifiziert.

---

## Vorbedingungen

- Mindestens ein Dokument wurde abgelegt (UC-04)
- Der Antrag hat `status = IN_ERFASSUNG`

## Nachbedingungen

**Erfolg:**
- Kein Dokument des Pflichtdokuments hat mehr `status = UNSICHER`
- Bestätigte oder umgeordnete Zuordnung mit `quelle = MENSCH`, Dokument mit `status = BESTAETIGT`
- Verworfenes Dokument mit `status = VERWORFEN`; das Pflichtdokument gilt wieder als `FEHLT`
- Je Aktion ein Protokolleintrag mit `akteur = BERATER`

---

## Beschreibung

Der Berater öffnet die Übersicht des Antrags. Unsichere Zuordnungen sind hervorgehoben, mit Dateiname und Konfidenz. Er sieht sich das Dokument an und bestätigt die Zuordnung; wählt er ein anderes Pflichtdokument, ordnet CredEx um und bestätigt zugleich (3a); verwirft er das Dokument, gilt das Pflichtdokument wieder als fehlend (3b). Auch eine sichere Zuordnung der KI kann er umordnen. Im PoC lässt sich eine unsichere Zuordnung erst nach dem Ansehen bestätigen; ob der Berater das auch per Auftrag an die KI tun darf, ist offen (siehe [CR-1.0](../../sources/cr_1_0.md)).

---

## Qualitätsanforderungen

- [NFA-06 Erlernbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-07 Zugänglichkeit](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-12 Nachweisbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)

---

## Aktivitätsdiagramm

![Aktivitätsdiagramm – UC-06 Zuordnung bestätigen oder ändern](zuordnungBestaetigen.puml)

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
