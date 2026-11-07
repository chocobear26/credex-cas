---
title: "Fachklassenmodell – CredEx Phase 1"
linkTitle: "Fachklassenmodell"
type: domain-model
description: "Das Fachklassenmodell von CredEx Phase 1 auf einen Blick: Klassendiagramm und ein Link auf jede Fachklasse."
weight: 1
tags: [partner, berater, ki-verbindung, pruefer, antrag, kreditnehmer, dokument, zuordnung, pflichtdokument, dokumenttyp, protokolleintrag]
sources:
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Fachklassenmodell – CredEx Phase 1

## Überblick

Das Fachklassenmodell beschreibt die fachlichen Objekte von CredEx Phase 1 – Dokumentenupload über die eigene KI des Partners. Acht Klassen gibt es heute schon in der CredEx-Plattform; neu sind `KiVerbindung`, `Zuordnung` und `Protokolleintrag` (Stereotyp `<<neu>>`). Fachliche Sicht ohne Methoden und technische Schlüssel. Grundlage ist das Fachklassenmodell der Gruppe vom 30.10.2026; der Abgleich mit dem bestehenden Datenmodell von CredEx ist offen.

---

## Klassendiagramm

![Fachklassenmodell – CredEx Phase 1](domainModel.puml)

---

## Klassen

- [Partner](entities/partner.md)
- [Berater](entities/berater.md)
- [KiVerbindung](entities/kiVerbindung.md)
- [Prüfer](entities/pruefer.md)
- [Antrag](entities/antrag.md)
- [Kreditnehmer](entities/kreditnehmer.md)
- [Dokument](entities/dokument.md)
- [Zuordnung](entities/zuordnung.md)
- [Pflichtdokument](entities/pflichtdokument.md)
- [Dokumenttyp](entities/dokumenttyp.md)
- [Protokolleintrag](entities/protokolleintrag.md)

---

## Beziehungen

```
Partner "1" -- "1..*" Berater : beschäftigt
Berater "1" -- "0..*" KiVerbindung : nutzt
Berater "1" -- "0..*" Antrag : erfasst
Prüfer "0..1" -- "0..*" Antrag : prüft, gibt frei
Antrag "0..*" -- "1..*" Kreditnehmer : betrifft
Antrag "1" *-- "0..*" Dokument : enthält
Antrag "1" *-- "1..*" Pflichtdokument : verlangt
Antrag "1" *-- "0..*" Protokolleintrag : dokumentiert
Pflichtdokument "0..*" -- "0..1" Kreditnehmer : bezieht sich auf
Pflichtdokument "0..*" -- "1" Dokumenttyp : ist vom Typ
Dokument "1" *-- "1" Zuordnung : erhält
Zuordnung "0..*" -- "0..1" Pflichtdokument : verweist auf
```

| Beziehung | Beschreibung |
|---|---|
| Partner beschäftigt Berater | Jeder Berater gehört zu genau einem Partner. |
| Berater nutzt KiVerbindung | Ein Berater kann seine KI mit CredEx verbinden, auch mehrere KI-Clients. |
| Berater erfasst Antrag | Der Berater erfasst den Antrag und reicht ihn ein. |
| Prüfer prüft Antrag | Ein Prüfer der Glarner KB prüft eingereichte Anträge und gibt sie frei. |
| Antrag betrifft Kreditnehmer | Ein Antrag betrifft eine oder mehrere Personen. |
| Antrag enthält Dokument | Die abgelegten Dateien existieren nur im Antrag (Komposition). |
| Antrag verlangt Pflichtdokument | Die Pflichtliste ergibt sich aus dem Antrag (Personen, Objekt, Produkt). |
| Antrag dokumentiert Protokolleintrag | Jede Aktion am Antrag wird protokolliert. |
| Pflichtdokument bezieht sich auf Kreditnehmer | Personenbezogene Pflichtdokumente (z.B. Lohnausweis) gehören zu einer Person; objektbezogene (z.B. Grundbuchauszug) zu keiner. |
| Pflichtdokument ist vom Typ Dokumenttyp | Der Dokumenttyp legt Bezeichnung und erlaubte Formate fest. |
| Dokument erhält Zuordnung | Jedes Dokument hat genau eine aktuelle Zuordnung. |
| Zuordnung verweist auf Pflichtdokument | Ohne Pflichtdokument ist das Ziel «weiteres Dokument». |
