---
title: "Soll-Prozess – Dokumentenupload über die eigene KI des Partners"
linkTitle: "Soll-Prozess"
type: business-process
description: "Der Soll-Prozess von Phase 1: von der KiVerbindung über die Ablage durch die Partner-KI und die Prüfung durch den Berater bis zur Einreichung bei der Glarner KB."
weight: 1
tags: [berater, ki-verbindung, antrag, pflichtdokument, dokument, zuordnung, protokolleintrag, kreditnehmer, partner]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-1
    resource: /sources/cr_1_1.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Soll-Prozess – Dokumentenupload über die eigene KI des Partners

## Überblick

Der Soll-Prozess beschreibt Schritt 5 «Hochladen» eines Antrags in Phase 1: Der Berater beauftragt seine eigene KI, die Partner-KI ruft über den MCP-Server von CredEx den Antrag und die Pflichtdokumente ab, legt jedes Dokument mit einer Zuordnung und Konfidenz ab, der Berater prüft unsichere Zuordnungen in der Übersicht und reicht selbst ein. Die Glarner KB prüft das Dossier wie heute. Die Begriffe stammen aus dem [Fachklassenmodell](../domain_model/domainModel.md); die Systeme und Informationsflüsse zeigt der [Systemkontext](../system_context/systemContext.md). Grundlage ist das BPMN-Modell der Gruppe (`CredEx_Sollprozess_Phase1.bpmn`, Stand 23.10.2026), nachgeführt auf die Entscheide in [CR-1.0](../sources/cr_1_0.md).

---

## Prozessdiagramm

> [!NOTE] v1.1 – Geändert 2026-11-07
> Der Soll-Prozess ist neu ein BPMN-2.0-Modell in zwei Teilen statt eines Mermaid-Flussdiagramms. Schritte und Nummern sind unverändert.

> [!NOTE] v1.2 – Geändert 2026-11-07
> Schritt 3.3: Der Berater kann auch per ausdrücklichem Auftrag an seine KI bestätigen, umordnen oder verwerfen.

Das Modell ist BPMN 2.0 mit Pool und Lanes; jede Lane ist ein Akteur. Teil 1 endet mit dem Link-Ereignis «weiter mit Teil 2», Teil 2 beginnt mit «von Teil 1». Die Quelldateien lassen sich in [bpmn.io](https://demo.bpmn.io) öffnen und bearbeiten.

### Teil 1 – Ablage durch die Partner-KI (Schritte 0.1 – 2.6)

![Soll-Prozess Teil 1 – Ablage durch die Partner-KI](sollProzessTeil1.bpmn)

### Teil 2 – Prüfen und Einreichen (Schritte 3.1 – 6.1)

![Soll-Prozess Teil 2 – Prüfen und Einreichen](sollProzessTeil2.bpmn)

---

## Änderungen gegenüber heute

- **Fällt weg:** Sammel-PDFs von Hand trennen und jedes der Pflichtdokumente einzeln in sein Upload-Feld laden.
- **Neu:** Die Partner-KI legt ab (2.1 – 2.5), der Berater prüft nur noch die unsicheren Zuordnungen (3.2 – 3.4), in der Übersicht oder per Auftrag an seine KI, ohne das KI-Fenster zu verlassen.
- **Neu:** Fehlende Pflichtdokumente sind vor dem Einreichen sichtbar (2.6, 4.1) statt erst bei der Prüfung durch die Glarner KB.
- **Bleibt:** Nur der Berater reicht ein (4.2); die Partner-KI kann nicht einreichen. Fehlende Unterlagen beschafft der Berater selbst (4.1a), CredEx fordert nichts beim Kreditnehmer an.
- **Bleibt:** Übermittlung an die Glarner KB über die bestehende Schnittstelle (4.3) und Prüfung wie heute (5.1).
