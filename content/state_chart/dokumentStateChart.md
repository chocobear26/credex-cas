---
title: "Zustandsdiagramm – Dokument"
linkTitle: "Dokument"
type: state-chart
description: "Wie sich das Attribut status der Fachklasse Dokument durch die Aktivitäten der Use Cases ändert."
weight: 1
tags: [dokument, zuordnung, pflichtdokument, antrag, berater]
sources:
  - id: dokument
    resource: /domain_model/entities/dokument.md
  - id: use-case-diagram
    resource: /use_case/useCaseDiagram.md
  - id: dokument-ablegen
    resource: /use_case/dokument_ablegen/dokumentAblegen.md
  - id: zuordnung-bestaetigen
    resource: /use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md
  - id: antrag-einreichen
    resource: /use_case/antrag_einreichen/antragEinreichen.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-1
    resource: /sources/cr_1_1.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T09:55:00Z
---

# Zustandsdiagramm – Dokument

> [!NOTE] v1.1 – Geändert 2026-11-07
> Diagramm waagrecht, Status farblich markiert wie im Original der Gruppe.

## Überblick

Dieses Zustandsdiagramm zeigt, wie sich das Attribut `status` der Fachklasse [Dokument](../domain_model/entities/dokument.md) durch die Aktivitäten der [Use Cases](../use_case/useCaseDiagram.md) ändert. Kernaussage: Die KI schlägt vor, der Mensch entscheidet, was unsicher ist – solange ein Dokument `UNSICHER` ist, bleibt das Einreichen gesperrt. Grundlage ist das Zustandsdiagramm der Gruppe vom 30.10.2026. Die Schwelle für die Konfidenz startet bei 0.80 und wird im PoC kalibriert.

---

## Diagramm

![Zustandsdiagramm – Dokument](dokumentStateChart.puml)

---

## Zustände

| Zustand | Beschreibung |
|---|---|
| **ABGELEGT** | Die Datei ist im Antrag gespeichert, die Zuordnung der Partner-KI mit Konfidenz liegt vor. Durchgangszustand. |
| **VON_KI_ZUGEORDNET** | Die Konfidenz liegt auf oder über der Schwelle. Ziel ist ein Pflichtdokument oder «weiteres Dokument». Der Berater kann umordnen. |
| **UNSICHER** | Die Konfidenz liegt unter der Schwelle. Sperrt das Einreichen, bis der Berater bestätigt, umordnet oder verwirft. |
| **BESTAETIGT** | Der Berater hat die Zuordnung bestätigt oder geändert; die Zuordnung hat `quelle = MENSCH`. |
| **VERWORFEN** | Der Berater hat das Dokument verworfen; das Pflichtdokument gilt wieder als `FEHLT`. Endzustand. |
| **EINGEREICHT** | Der Antrag wurde eingereicht; das Dokument ist Teil des Dossiers an die Glarner KB. Endzustand. |

---

## Rückverfolgung der Übergänge

Jeder Übergang entspricht einer Aktivität (`:aktion;`) in einem Aktivitätsdiagramm.

| Übergang | Auslösende Aktivität | Use Case | Schritt im Aktivitätsdiagramm |
|---|---|---|---|
| [*] → ABGELEGT | «CredEx-System legt Dokument an (status = ABGELEGT)» | [UC-04 Dokument ablegen](../use_case/dokument_ablegen/dokumentAblegen.md) | Nach gültiger Prüfung von Berechtigung, Format und Grösse |
| ABGELEGT → VON_KI_ZUGEORDNET | «CredEx-System setzt Dokument (status = VON_KI_ZUGEORDNET)» | [UC-04 Dokument ablegen](../use_case/dokument_ablegen/dokumentAblegen.md) | Konfidenz ≥ Schwelle |
| ABGELEGT → UNSICHER | «CredEx-System setzt Dokument (status = UNSICHER)» | [UC-04 Dokument ablegen](../use_case/dokument_ablegen/dokumentAblegen.md) | Konfidenz < Schwelle |
| UNSICHER → BESTAETIGT | «CredEx-System setzt Dokument (status = BESTAETIGT)» | [UC-06 Zuordnung bestätigen oder ändern](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) | Zuordnung bestätigt oder anderes Pflichtdokument gewählt (3a) |
| VON_KI_ZUGEORDNET → BESTAETIGT | «CredEx-System setzt Dokument (status = BESTAETIGT)» | [UC-06 Zuordnung bestätigen oder ändern](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) | Anderes Pflichtdokument gewählt (3a) |
| UNSICHER → VERWORFEN | «CredEx-System setzt Dokument (status = VERWORFEN)» | [UC-06 Zuordnung bestätigen oder ändern](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) | Dokument verworfen (3b) |
| VON_KI_ZUGEORDNET → EINGEREICHT | «CredEx-System setzt Dokument (status = EINGEREICHT)» | [UC-07 Antrag einreichen](../use_case/antrag_einreichen/antragEinreichen.md) | Nach erfolgreicher Übermittlung |
| BESTAETIGT → EINGEREICHT | «CredEx-System setzt Dokument (status = EINGEREICHT)» | [UC-07 Antrag einreichen](../use_case/antrag_einreichen/antragEinreichen.md) | Nach erfolgreicher Übermittlung |

---

## Nicht abgedeckte Zustände

Alle Zustände sind durch Aktivitäten gedeckt. Zwei Fälle sind im Modell noch nicht geregelt:

- **Verwerfen einer sicheren Zuordnung.** FA-06 erlaubt das Verwerfen jeder Zuordnung, auch einer sicheren; das Zustandsdiagramm der Gruppe kennt `VON_KI_ZUGEORDNET → VERWORFEN` nicht. Offen, ob der Übergang dazukommt.
- **Selbst hochgeladene Dokumente.** Lädt der Berater ein nachgeliefertes Dokument selbst im Upload-Feld hoch (bestehende Funktion, UC-07 Szenario 2a), ist der Anfangszustand nicht festgelegt. **Annahme:** `BESTAETIGT` mit `quelle = MENSCH`.
