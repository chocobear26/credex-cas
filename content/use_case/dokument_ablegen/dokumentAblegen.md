---
title: "Use Case – UC-04 Dokument ablegen"
linkTitle: "UC-04 Dokument ablegen"
type: use-case
description: "Die Partner-KI legt eine Datei aus dem Dossier im Antrag ab und schlägt das passende Pflichtdokument mit Konfidenz vor."
weight: 6
tags: [dokument, zuordnung, pflichtdokument, antrag, protokolleintrag, berater]
sources:
  - id: use-case-diagram
    resource: /use_case/useCaseDiagram.md
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Use Case – UC-04 Dokument ablegen

## Überblick

Die Partner-KI legt eine Datei aus dem Dossier im Antrag ab und schlägt das passende Pflichtdokument mit Konfidenz vor. Entspricht **Prozessschritten 2.1 – 2.5**.[^business-process] Siehe auch [Use-Case-Diagramm](../useCaseDiagram.md) und [Soll-Prozess](../../business_process/businessProcess.md). Priorität Must, Wichtigkeit hoch, technologisches Risiko mittel: das Verhalten der KI-Clients unterscheidet sich (Konfidenz, Seitenaufteilung). Werkzeug `credex_dokument_ablegen`. Im Detail spezifiziert.

---

## Vorbedingungen

- Eine gültige KiVerbindung besteht (UC-01)
- Der Antrag hat `status = IN_ERFASSUNG`
- Die Pflichtliste wurde abgefragt (UC-03, «include»)

## Nachbedingungen

**Erfolg:**
- Das Dokument ist im Antrag gespeichert, mit Zuordnung (`quelle = KI`, `konfidenz`)
- Dokument mit `status = VON_KI_ZUGEORDNET` bei Konfidenz ≥ Schwelle, sonst `status = UNSICHER`
- Ein Protokolleintrag mit `akteur = KI` ist geschrieben
- Die Übersicht zeigt das Dokument

**Fehler – Ablage abgelehnt:**
- Kein Dokument gespeichert, keine Teilablage
- Die Partner-KI erhält eine verständliche Fehlermeldung

---

## Beschreibung

Für jede Datei im Dossier bestimmt die Partner-KI das passende Pflichtdokument und ihre Konfidenz und ruft das Werkzeug zum Ablegen auf. Bei einem Sammel-PDF übergibt sie je Teil einen Seitenbereich; CredEx legt nur diese Seiten als eigenes Dokument ab (Alternativszenario 1a). Passt eine Datei zu keinem Pflichtdokument, wählt die KI das Ziel «weiteres Dokument» (1b). CredEx prüft Berechtigung, Format und Grösse; fehlt die Berechtigung, ist der Antrag schon eingereicht, ist die Datei nicht lesbar oder zu gross, wird die Ablage abgelehnt (2x). Sonst speichert CredEx das Dokument, setzt den Status nach der Schwelle (Startwert 0.80, im PoC zu kalibrieren) und schreibt einen Protokolleintrag. Ob ein Duplikat über eine Prüfsumme erkannt wird, ist offen (2y). Nach der letzten Datei prüft die Partner-KI die Vollständigkeit (UC-05).

---

## Qualitätsanforderungen

- [NFA-01 Korrektheit](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-02 Zeitverhalten](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-03 Kapazität](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-09 Fehlertoleranz](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-12 Nachweisbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-13 Datenhaltung in der Schweiz](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-14 Verschlüsselung](../../requirements/nichtfunktionaleAnforderungen.md)

---

## Aktivitätsdiagramm

![Aktivitätsdiagramm – UC-04 Dokument ablegen](dokumentAblegen.puml)

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
