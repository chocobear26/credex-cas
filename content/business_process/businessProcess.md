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
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Soll-Prozess – Dokumentenupload über die eigene KI des Partners

## Überblick

Der Soll-Prozess beschreibt Schritt 5 «Hochladen» eines Antrags in Phase 1: Der Berater beauftragt seine eigene KI, die Partner-KI ruft über den MCP-Server von CredEx den Antrag und die Pflichtdokumente ab, legt jedes Dokument mit einer Zuordnung und Konfidenz ab, der Berater prüft unsichere Zuordnungen in der Übersicht und reicht selbst ein. Die Glarner KB prüft das Dossier wie heute. Die Begriffe stammen aus dem [Fachklassenmodell](../domain_model/domainModel.md); die Systeme und Informationsflüsse zeigt der [Systemkontext](../system_context/systemContext.md). Grundlage ist das BPMN-Modell der Gruppe (`CredEx_Sollprozess_Phase1.bpmn`, Stand 23.10.2026), nachgeführt auf die Entscheide in [CR-1.0](../sources/cr_1_0.md).

---

## Prozessdiagramm

**Legende:** 🟦 Berater/in &nbsp; 🟪 Partner-KI &nbsp; 🟨 CredEx-System &nbsp; 🟩 Glarner KB &nbsp; ⬜ Partner-IT / Partnermanagement &nbsp; 🟥 Entscheidung

```mermaid
flowchart TD
    classDef berater fill:#DBEAFE,stroke:#2563EB,color:#1E3A5F
    classDef partnerKi fill:#EDE9FE,stroke:#7C3AED,color:#3B0764
    classDef credex fill:#FEF9C3,stroke:#CA8A04,color:#713F12
    classDef glkb fill:#DCFCE7,stroke:#16A34A,color:#14532D
    classDef support fill:#F3F4F6,stroke:#6B7280,color:#1F2937
    classDef decision fill:#FEE2E2,stroke:#DC2626,color:#7F1D1D

    start(("Start:\nAntrag in Schritt 5")) --> hatVerbindung{"0.1 KiVerbindung\nvorhanden?"}:::decision
    hatVerbindung -->|Nein| verbinden["0.2 KiVerbindung einrichten\n(einmalig)"]:::support
    verbinden --> hatVerbindung
    hatVerbindung -->|Ja| auftrag["1.1 Auftrag an\neigene KI geben"]:::berater

    auftrag --> antraegeAbrufen["1.2 Offene Anträge\nabrufen"]:::partnerKi
    antraegeAbrufen --> antraegeLiefern["1.3 Berechtigung prüfen,\noffene Anträge liefern"]:::credex
    antraegeLiefern --> pflichtlisteAbrufen["1.4 Pflichtliste\ndes Antrags abfragen"]:::partnerKi
    pflichtlisteAbrufen --> pflichtlisteLiefern["1.5 Pflichtdokumente\nmit Status liefern"]:::credex

    pflichtlisteLiefern --> dateiLesen["2.1 Datei aus Partner-DMS lesen,\nPflichtdokument und Konfidenz bestimmen"]:::partnerKi
    dateiLesen --> ablegen["2.2 Dokument mit Zuordnung\nablegen (ggf. Seitenbereich)"]:::partnerKi
    ablegen --> gueltig{"2.3 Berechtigung, Format\nund Grösse gültig?"}:::decision
    gueltig -->|Nein| ablehnen["2.3a Ablage ablehnen,\nFehlermeldung an KI"]:::credex
    gueltig -->|Ja| speichern["2.4 Dokument speichern, Status\nsetzen, Protokolleintrag"]:::credex
    ablehnen --> weitere{"2.5 Weitere Datei\nim Dossier?"}:::decision
    speichern --> weitere
    weitere -->|Ja| dateiLesen
    weitere -->|Nein| vollstaendigkeit["2.6 Vollständigkeit prüfen,\nfehlende und unsichere melden"]:::credex

    vollstaendigkeit --> uebersicht["3.1 Übersicht im\nCredEx-Tool öffnen"]:::berater
    uebersicht --> unsicher{"3.2 Zuordnung\nunsicher?"}:::decision
    unsicher -->|Ja| pruefen["3.3 Dokument ansehen, bestätigen,\numordnen oder verwerfen"]:::berater
    pruefen --> statusSetzen["3.4 Zuordnung und Status\nsetzen, Protokolleintrag"]:::credex
    statusSetzen --> unsicher
    unsicher -->|Nein| vollstaendig{"4.1 Alle Pflichtdokumente\nvorhanden?"}:::decision
    vollstaendig -->|Nein| beschaffen["4.1a Fehlende Unterlagen selbst\nbeim Kreditnehmer beschaffen"]:::berater
    beschaffen --> nachliefern["4.1b Nachgelieferte Datei ablegen\n(KI oder Upload-Feld)"]:::berater
    nachliefern --> vollstaendig
    vollstaendig -->|Ja| einreichen["4.2 Antrag\neinreichen"]:::berater
    einreichen --> uebermitteln["4.3 Dossier über bestehende\nSchnittstelle übermitteln"]:::credex
    uebermitteln --> erfolgreich{"4.4 Übermittlung\nerfolgreich?"}:::decision
    erfolgreich -->|Nein| meldung["4.4a Antrag bleibt in Erfassung,\nMeldung an Berater/in"]:::credex
    meldung --> einreichen
    erfolgreich -->|Ja| eingereicht["4.5 Antrag eingereicht setzen,\nProtokolleintrag"]:::credex
    eingereicht --> pruefungGlkb["5.1 Dossier prüfen\n(wie heute)"]:::glkb
    pruefungGlkb --> ende(("Ende"))

    monat(("Start:\nMonatsende")) --> auswerten["6.1 Nutzung und Zeitersparnis\npro Partner auswerten"]:::support
    auswerten --> ende2(("Ende"))
```

---

## Änderungen gegenüber heute

- **Fällt weg:** Sammel-PDFs von Hand trennen und jedes der Pflichtdokumente einzeln in sein Upload-Feld laden.
- **Neu:** Die Partner-KI legt ab (2.1 – 2.5), der Berater prüft nur noch die unsicheren Zuordnungen (3.2 – 3.4).
- **Neu:** Fehlende Pflichtdokumente sind vor dem Einreichen sichtbar (2.6, 4.1) statt erst bei der Prüfung durch die Glarner KB.
- **Bleibt:** Nur der Berater reicht ein (4.2); die Partner-KI kann nicht einreichen. Fehlende Unterlagen beschafft der Berater selbst (4.1a), CredEx fordert nichts beim Kreditnehmer an.
- **Bleibt:** Übermittlung an die Glarner KB über die bestehende Schnittstelle (4.3) und Prüfung wie heute (5.1).
