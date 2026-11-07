---
title: "Nutzwertanalyse – CredEx Phase 1"
linkTitle: "Nutzwertanalyse"
type: option-evaluation
description: "Fünf Lösungsoptionen mit sechs gewichteten Kriterien, Rangfolge und Sensitivität."
weight: 1
tags: [partner, berater]
sources:
  - id: geschaeftsanforderungen
    resource: /requirements/geschaeftsanforderungen.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:45:00Z
---

# Nutzwertanalyse – CredEx Phase 1

Bewertung der Lösungsoptionen für den Dokumentenupload (Lernziel Modul 2: Bewertung alternativer Lösungsoptionen und Auswahl). Quelle: `Gruppe_6_CredEx_Nutzwertanalyse.xlsx`; Gewichte und Punkte sind ein Vorschlag, den die Gruppe am 13.11.2026 bestätigt ([E11](../decisions/e11OptionDragAndDrop.md)).

---

## Optionen

| Option | Beschreibung |
|---|---|
| **A** | Offener MCP-Server, jede Partner-KI dockt an (Phase 1, gewählt) |
| **B** | Eingebettete Copilot-Lösung im CredEx-Tool |
| **C** | Bestehende Schnittstelle zu Kernsystemen der Partner (z.B. Hypo Pro) |
| **D** | Mehrfach-Upload per Drag & Drop ohne KI |
| **E** | Integrierte CredEx-KI über die Swiss AI Platform (Phase 2) |

---

## Kriterien und Bewertung

Skala 1 (schlecht) bis 5 (sehr gut); Gewichte summieren sich zu 1.00.

| Kriterium | Gewicht | A | B | C | D | E | Begründung |
|---|---|---|---|---|---|---|---|
| Zeitersparnis Berater (GA1) | 0.25 | 4 | 4 | 3 | 2 | 5 | Hauptpain Einzel-Upload und Trennen von Sammel-PDFs (Interviews); D löst nur das Einzelklicken |
| Abdeckung der Partner (Lösungsentscheid Modul 1) | 0.20 | 3 | 2 | 1 | 5 | 5 | A: nur Partner mit MCP-fähiger KI; B: nur Microsoft; C: nur Partner mit eigenem Kernsystem |
| Aufwand und Kosten für CredEx (Business Case) | 0.20 | 4 | 2 | 2 | 4 | 1 | E: ca. 60 PT plus Tokenkosten (Interview CTO); B und C: Integration pro Partner |
| Zeit bis zum Nutzen (Business Case) | 0.15 | 4 | 2 | 2 | 5 | 1 | Modul 1: Phase 1 in ca. 6 Monaten, erster Partner nach ca. 3 Monaten |
| Datenschutz und Kontrolle (GA4) | 0.10 | 4 | 4 | 4 | 5 | 3 | A und B: Daten in der KI-Umgebung des Partners; E: Verarbeitung bei CredEx |
| Bedienung ohne Medienbruch (Feedback LNW 1) | 0.10 | 3 | 5 | 4 | 4 | 5 | Rückfrage Modul 1: Wechsel zwischen KI-Fenster und CredEx-Tool |
| **Nutzwert** | 1.00 | **3.70** | 3.00 | 2.45 | **3.95** | 3.40 | |
| **Rang** | | 2 | 4 | 5 | 1 | 3 | |

---

## Sensitivität

| Variante | A | B | C | D | E |
|---|---|---|---|---|---|
| Basis (Vorschlag) | 3.70 (2.) | 3.00 (4.) | 2.45 (5.) | 3.95 (1.) | 3.40 (3.) |
| Zeitersparnis stärker (0.35), Abdeckung und Aufwand je 0.15 | 3.75 (1.) | 3.20 (4.) | 2.60 (5.) | 3.70 (2.) | 3.60 (3.) |
| Medienbruch nach E10 entschärft: A erhält 4 statt 3 | 3.80 (2.) | 3.00 (4.) | 2.45 (5.) | 3.95 (1.) | 3.40 (3.) |
| Gleichgewichtet (je 1/6) | 3.67 (2.) | 3.17 (4.) | 2.67 (5.) | 4.17 (1.) | 3.33 (3.) |

---

## Ergebnis

- **D liegt mit den Basisgewichten knapp vorne**, weil es alle Partner erreicht und schnell gebaut ist; es spart aber am wenigsten Zeit.
- **A liegt vorne, sobald die Zeitersparnis (GA1) stärker zählt** – also genau dann, wenn man die Leitfrage aus Modul 1 ernst nimmt.
- **A und D schliessen sich nicht aus:** Die Übersicht mit Pflichtlisten-Prüfung ist für beide dieselbe. Die Gruppe entscheidet, ob D als Ergänzung in den Pilot kommt ([E11](../decisions/e11OptionDragAndDrop.md)).
- B und C scheiden aus: B schliesst Partner ohne Microsoft aus ([E03](../decisions/e03OffenerMcpStattCopilot.md)), C verlangt eine Integration pro Partner. E bleibt Phase 2 ([E01](../decisions/e01VarianteZuerstMcp.md)).
