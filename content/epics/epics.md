---
title: "Epics & Story Map – CredEx Phase 1"
linkTitle: "Epics / Story Map"
type: story-map
description: "Die Epics von CredEx Phase 1, jedes realisiert genau einen Use Case, mit den User Stories in Release-Zeilen."
weight: 1
tags: [ki-verbindung, team, berater, antrag, pflichtdokument, dokumenttyp, dokument, zuordnung, protokolleintrag, partner, kreditnehmer, pruefer]
sources:
  - id: use-case-diagram
    resource: /use_case/useCaseDiagram.md
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: ki-verbinden
    resource: /use_case/ki_verbinden/kiVerbinden.md
  - id: offene-antraege-abrufen
    resource: /use_case/offene_antraege_abrufen/offeneAntraegeAbrufen.md
  - id: pflichtliste-abfragen
    resource: /use_case/pflichtliste_abfragen/pflichtlisteAbfragen.md
  - id: dokument-ablegen
    resource: /use_case/dokument_ablegen/dokumentAblegen.md
  - id: vollstaendigkeit-pruefen
    resource: /use_case/vollstaendigkeit_pruefen/vollstaendigkeitPruefen.md
  - id: zuordnung-bestaetigen
    resource: /use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md
  - id: antrag-einreichen
    resource: /use_case/antrag_einreichen/antragEinreichen.md
  - id: nutzung-auswerten
    resource: /use_case/nutzung_auswerten/nutzungAuswerten.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:30:00Z
---

# Epics & Story Map – CredEx Phase 1

> [!NOTE] v1.2 – Geändert 2026-11-07
> US-6.3 neu (Bestätigen per Auftrag an die KI); US-2.2 auf Anträge des Teams geändert.

## Überblick

Diese Seite listet die Epics von CredEx Phase 1. Jedes Epic realisiert genau einen [Use Case](../use_case/useCaseDiagram.md); die Epic-Nummer ist die Nummer des Use Case (UC-08 ist nicht vergeben). Die Begriffe stammen aus dem [Fachklassenmodell](../domain_model/domainModel.md). Die Stories sind in Release-Zeilen gruppiert: **R0 – PoC** (November 2026, Nutzennachweis mit Beratenden), **R1 – Pilot (MVP)** mit einem Pilotpartner, **R2 – Rollout Phase 1** bis ca. Monat 6. Die Story-IDs des Detailkonzepts (US-01 … US-10; US-6.3 ist neu) stehen in jeder Story unter *Conversation*; die Detailkonzept-Story US-01 ist auf UC-02, UC-03 und UC-04 aufgeteilt.

**MoSCoW** (Pilot): Must = für den Pilot nötig · Should = wünschenswert · **KANO:** MUSS / BRAUCHE = Basismerkmal · MÖCHTE = Leistungsmerkmal · HÄTTE GERN = Begeisterungsmerkmal

---

## Story Map

| | Epic 1: KI mit CredEx verbinden | Epic 2: Offene Anträge abrufen | Epic 3: Pflichtliste abfragen | Epic 4: Dokument ablegen | Epic 5: Vollständigkeit prüfen | Epic 6: Zuordnung bestätigen oder ändern | Epic 7: Antrag einreichen | Epic 9: Nutzung auswerten |
|---|---|---|---|---|---|---|---|---|
| **Use Case** | [UC-01](../use_case/ki_verbinden/kiVerbinden.md) | [UC-02](../use_case/offene_antraege_abrufen/offeneAntraegeAbrufen.md) | [UC-03](../use_case/pflichtliste_abfragen/pflichtlisteAbfragen.md) | [UC-04](../use_case/dokument_ablegen/dokumentAblegen.md) | [UC-05](../use_case/vollstaendigkeit_pruefen/vollstaendigkeitPruefen.md) | [UC-06](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) | [UC-07](../use_case/antrag_einreichen/antragEinreichen.md) | [UC-09](../use_case/nutzung_auswerten/nutzungAuswerten.md) |
| **Ziel** | KiVerbindung anlegen, damit die Partner-KI die Werkzeuge nutzen kann | Offene Anträge des Teams liefern | Pflichtdokumente des Antrags mit Status liefern | Dokument mit Zuordnung im Antrag ablegen und Status setzen | Fehlende und unsichere Pflichtdokumente melden | Zuordnung bestätigen, ändern oder verwerfen | Vollständigen Antrag einreichen und Dossier übermitteln | Kennzahlen pro Partner aus den Protokolleinträgen auswerten |
| **Fachklassen** | KiVerbindung, Berater | Antrag, Berater | Pflichtdokument, Dokumenttyp | Dokument, Zuordnung, Protokolleintrag | Pflichtdokument, Dokument | Zuordnung, Dokument, Protokolleintrag | Antrag, Dokument, Protokolleintrag | Partner, Protokolleintrag |
| **Akteur** | Partner-IT, Berater/in | Partner-KI | Partner-KI | Partner-KI, Berater/in | Partner-KI | Berater/in | Berater/in, Glarner KB | Partnermanagement |
| **Prozessschritte** | 0.1 – 0.2 | 1.2 – 1.3 | 1.4 – 1.5 | 2.1 – 2.5 | 2.6, 4.1 | 3.1 – 3.4 | 4.1 – 4.5 | 6.1 |
| | | | | | | | | |
| **R0 – PoC** |  | [US-2.1](user_stories/us_2_1.md) Offenen Antrag ohne Antragsnummer finden | [US-3.1](user_stories/us_3_1.md) Pflichtliste für die Zuordnung kennen | [US-4.1](user_stories/us_4_1.md) Unterlagen per Auftrag an die eigene KI ablegen | [US-5.1](user_stories/us_5_1.md) Erfahren, was fehlt oder unsicher ist | [US-6.1](user_stories/us_6_1.md) Status je Pflichtdokument auf einen Blick | [US-7.1](user_stories/us_7_1.md) Nur vollständig und nur selbst einreichen |  |
| |  |  |  | [US-4.2](user_stories/us_4_2.md) Sammel-PDF aufteilen lassen |  | [US-6.2](user_stories/us_6_2.md) Unsichere Zuordnung bestätigen, ändern oder verwerfen |  |  |
| |  |  |  |  |  | [US-6.3](user_stories/us_6_3.md) Zuordnung per Auftrag an die eigene KI bestätigen |  |  |
| **R1 – Pilot (MVP)** | [US-1.1](user_stories/us_1_1.md) KI einmalig mit CredEx verbinden | [US-2.2](user_stories/us_2_2.md) Nur Anträge des eigenen Teams sehen |  |  |  |  |  |  |
| **R2 – Rollout Phase 1** |  |  |  |  |  |  |  | [US-9.1](user_stories/us_9_1.md) Nutzung und Zeitersparnis pro Partner sehen |

---

## Nicht in Phase 1

| Detailkonzept | Story | Grund |
|---|---|---|
| US-06 | Fehlende Unterlagen markieren und über die KI nachliefern | Teamentscheid 30.10.2026: Der Berater fragt selbst beim Kreditnehmer nach. |
| US-09 | Kreditnehmer über KI-Verarbeitung informieren | Teamentscheid 30.10.2026: gestrichen. |
| US-11 | Prüfer der Glarner KB sieht, welche Zuordnung von der KI stammt | Teamentscheid 30.10.2026: Verantwortung liegt beim Berater. |
| US-12 | Mehrere Dateien per Drag & Drop ohne KI hochladen (Option D) | Won't in Phase 1; Teamentscheid zur Nutzwertanalyse offen. |

Die Entscheide sind in [CR-1.0](../sources/cr_1_0.md) festgehalten.
