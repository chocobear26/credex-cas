---
title: "Umsetzungsplan – CredEx Phase 1"
linkTitle: "Umsetzungsplan"
type: delivery-plan
description: "Agiles Vorgehen in drei Releases bis zum Go/No-Go für Phase 2, mit Risiken und Entscheidungspunkten."
weight: 1
tags: [partner, berater, antrag]
sources:
  - id: epics
    resource: /epics/epics.md
  - id: ausgangslage
    resource: /problem/ausgangslage.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Umsetzungsplan – CredEx Phase 1

## Vorgehen

Agil mit kurzen Iterationen (Scrum, 2-Wochen-Sprints). Begründung nach der Stacey-Matrix: Die Technik ist für CredEx neu (MCP, Verhalten verschiedener KI-Clients), und die Anforderungen der Partner sind noch nicht stabil (Validierung ausstehend). Beides liegt im komplexen Bereich und spricht für schrittweises Vorgehen mit frühem Feedback. Der Releaseplan aus Modul 1 bleibt der Rahmen für Meilensteine und Budget.

---

## Releaseplan

| Release | Inhalt | Stories | Zeitraum | Meilenstein |
|---|---|---|---|---|
| R0 PoC | MCP-Server mit Testdossier, Übersicht, Test mit Beratenden | US-2.1, US-3.1, US-4.1, US-4.2, US-5.1, US-6.1, US-6.2, US-6.3, US-7.1 | Nov. 2026 (CAS) | Nutzen belegt (H1 bis H3) |
| R1 Pilot (MVP) | Anmeldung, Teamzugriff, Ablage in der Plattform, Protokoll; 1 Pilotpartner | US-1.1, US-2.2 | Monat 1 bis 4 nach Freigabe | erster Partner produktiv (nach ca. 3 Monaten) |
| R2 Rollout Phase 1 | weitere Grosspartner, Kennzahlen pro Partner, Anleitungen für weitere KI-Clients | US-9.1 | bis Monat 6 | Go-live Phase 1 |
| Go/No-Go Phase 2 | Entscheid integrierte CredEx-KI auf Basis der gemessenen Zahlen | – | Monat 12 | Business Case mit echten Zahlen |

Zeiträume aus dem Interview mit T. Cruz (PoC 1 bis 2 Monate, erster Partner nach ca. 3 Monaten, total ca. 6 Monate). Details der Stories in der [Story Map](../epics/epics.md).

---

## Risiken

| Risiko | Wirkung | Massnahme |
|---|---|---|
| Partner nutzen die MCP-Schnittstelle nicht | hoch | Pilot vor Rollout; Option D als Ergänzung prüfen ([E11](../decisions/e11OptionDragAndDrop.md)) |
| KI ordnet falsch zu und meldet trotzdem hohe Konfidenz | hoch | Schwelle im PoC kalibrieren; Stichproben im Pilot; Protokoll |
| IT-Richtlinien der Partner erlauben keine externe Verbindung der KI | hoch | in V1 und V2 klären; Anleitung für die Partner-IT |
| KI-Clients verhalten sich unterschiedlich | mittel | Test mit mind. 2 Clients (NFA-04) |
| Rechtliche Fragen zur Information der Kreditnehmer | mittel | frühe Klärung mit dem Rechtsdienst von CredEx (R-03) |
| Medienbruch wird als störend empfunden | mittel | im PoC messen (H3); Bestätigen per Auftrag an die KI ([E10](../decisions/e10BestaetigenPerKiAuftrag.md)) |

---

## Entscheidungspunkte

- **Nach R0:** Ist der Nutzen belegt (H1 bis H3)? Sonst Konzept überarbeiten, bevor ein Pilotpartner gesucht wird.
- **Nach R1:** Nutzt der Pilotpartner die Schnittstelle? Erreicht er die Zielwerte?
- **Monat 12, Go/No-Go Phase 2:** Business Case mit gemessener Zeitersparnis, tatsächlicher Partneradoption und GLKB-Beteiligung; dazu die kombinierte Szenarioanalyse aus dem Feedback zu Modul 1.
