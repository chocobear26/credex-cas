---
title: "Geschäftsanforderungen – CredEx Phase 1"
linkTitle: "Geschäftsanforderungen"
type: requirement-catalog
description: "Die sechs Geschäftsanforderungen GA1 bis GA6 an Phase 1, je mit Messgrösse und Quelle."
weight: 1
tags: [berater, antrag, pflichtdokument, zuordnung, partner, kreditnehmer]
sources:
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:30:00Z
---

# Geschäftsanforderungen – CredEx Phase 1

> [!NOTE] v1.2 – Geändert 2026-11-07
> GA1 auf den Zielwert aus Modul 1 korrigiert (31.5 statt «ca. 31» Min.); GA3 präzisiert (Bestätigen auch per Auftrag an die KI).

## Überblick

Die Geschäftsanforderungen sagen, was Phase 1 für CredEx und die Partner erreichen muss. Sie stammen aus dem Detailkonzept der Gruppe (Kapitel 2) und gehen auf Problemstatement, Business Case und Interviews aus Modul 1 zurück. Daraus abgeleitet sind die [funktionalen](funktionaleAnforderungen.md) und [nicht-funktionalen Anforderungen](nichtfunktionaleAnforderungen.md).

---

## Anforderungen

| ID | Geschäftsanforderung | Messgrösse / Ziel | Quelle |
|---|---|---|---|
| GA1 | Aufwand beim Partner senken | Dauer bis Einreichung −30 % (Ø 45 auf 31.5 Min.), 6 Monate nach Go-live; davon entfallen heute Ø 15 Min. auf den Upload | Problemstatement, Analytics, Leitfrage Modul 1 |
| GA2 | Qualität der Dossiers halten | Vollständigkeit mind. heutiges Niveau; eingereicht wird nur, wenn alle Pflichtdokumente vorhanden sind | Interview PostFinance (O. Braun, 17.09.2026) |
| GA3 | Verantwortung bleibt beim Berater | Die KI schlägt vor; unsichere Zuordnungen bestätigt der Mensch, in der Übersicht oder per ausdrücklichem Auftrag an seine KI; nur der Mensch reicht ein, und nur in der Übersicht | Interviews CredEx (T. Cruz, 15.09.2026) und PostFinance |
| GA4 | Datenschutz und Nachvollziehbarkeit | Daten nur in der Schweiz; 100 % der Zuordnungen protokolliert | Interview CTO CredEx |
| GA5 | Kein Eingriff ins Kernsystem | Bestehende Systeme und Schnittstellen von CredEx und Partnern bleiben unverändert | Modul 1, Interview PostFinance |
| GA6 | Nutzen messbar machen | Nutzung und Zeitersparnis pro Partner ausgewiesen; Basis für Gebühr und Go/No-Go Phase 2 | Business Case Modul 1 |

---

## Offene Punkte

- **GA1 – zwei Zeitbasen.** GA1 misst die Dauer bis Einreichung des ganzen Antrags (Ø 45 Min.). Persona, Hypothese H1 und [US-4.1](../epics/user_stories/us_4_1.md) messen den Upload-Schritt (heute ca. 15 Min., Ziel unter 2 Min.). Beide Zahlen sind verträglich, müssen aber auf den Folien klar getrennt werden.
- **GA4 – Information der Kreditnehmer.** Im Detailkonzept verlangt GA4 auch, dass die Kreditnehmer über die KI-Nutzung informiert werden (DSG). Die Story dazu (US-09) ist gestrichen; die rechtliche Klärung, wer informiert, ist offen. Diese Fassung lässt den Teil weg, bis die Gruppe entscheidet.
