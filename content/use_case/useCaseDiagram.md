---
title: "Use-Case-Diagramm – CredEx Phase 1"
linkTitle: "Use-Case-Übersicht"
type: use-case-diagram
description: "Das Use-Case-Diagramm zeigt, wie die Akteure aus dem Soll-Prozess mit CredEx Phase 1 interagieren."
weight: 1
tags: [berater, ki-verbindung, antrag, pflichtdokument, dokument, zuordnung, partner]
sources:
  - id: business-process
    resource: /business_process/businessProcess.md
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

# Use-Case-Diagramm – CredEx Phase 1

> [!NOTE] v1.1 – Geändert 2026-11-07
> Diagramm neu angeordnet: Übersicht links, MCP-Werkzeuge rechts, gemeinsamer Diagrammstil.

## Überblick

Das Use-Case-Diagramm zeigt, wie die Akteure aus dem [Soll-Prozess](../business_process/businessProcess.md) mit CredEx Phase 1 interagieren. Die Systemgrenze umfasst MCP-Server, Übersicht und Auswertung. Die Nummern stammen aus dem Detailkonzept der Gruppe; UC-08 ist nicht vergeben. UC-02 bis UC-05 ruft die Partner-KI im Auftrag des Beraters als Werkzeuge auf. Bestätigen bleibt ein Entscheid des Menschen (UC-06), auch wenn er ihn über seine KI ausführen lässt; einreichen kann nur der Mensch in der Übersicht (UC-07). Im Detail spezifiziert waren in der Gruppe UC-04, UC-06 und UC-07.

---

## Diagramm

![Use-Case-Diagramm – CredEx Phase 1](useCaseDiagram.puml)

---

## Akteure

| Akteur | Art | Beschreibung |
|---|---|---|
| **Berater/in** | Primär | Kundenberaterin eines Partners oder Hypothekarbroker; beauftragt die KI, prüft, reicht ein (🟦 im Soll-Prozess). |
| **Partner-IT** | Primär | Richtet die KiVerbindung beim Partner ein (⬜ im Soll-Prozess). |
| **Partnermanagement** | Primär | Wertet die Nutzung pro Partner aus (⬜ im Soll-Prozess). |
| **Partner-KI** | System | KI-Assistent des Partners, ruft die Werkzeuge des MCP-Servers auf (🟪 im Soll-Prozess). |
| **Glarner KB** | System | Empfängt das eingereichte Dossier über die bestehende Schnittstelle (🟩 im Soll-Prozess). |

---

## Use Cases

### UC-01 KI mit CredEx verbinden
Die Partner-IT oder der Berater (bei Brokern ohne IT) verbindet einen KI-Client einmalig mit CredEx.
Entspricht **Prozessschritten 0.1 – 0.2**.[^business-process]

### UC-02 Offene Anträge abrufen
Die Partner-KI findet den offenen Antrag, ohne dass der Berater eine Antragsnummer nennt.
Entspricht **Prozessschritten 1.2 – 1.3**.[^business-process]

### UC-03 Pflichtliste abfragen
Die Partner-KI erfährt, welche Pflichtdokumente der Antrag verlangt und welche schon vorhanden sind.
Entspricht **Prozessschritten 1.4 – 1.5**.[^business-process]

### UC-04 Dokument ablegen
Die Partner-KI legt jede Datei mit einer Zuordnung und Konfidenz im Antrag ab.
Entspricht **Prozessschritten 2.1 – 2.5**.[^business-process]

### UC-05 Vollständigkeit prüfen
CredEx meldet, welche Pflichtdokumente fehlen oder unsicher sind.
Entspricht **Prozessschritten 2.6 und 4.1**.[^business-process]

### UC-06 Zuordnung bestätigen oder ändern
Der Berater bestätigt, ändert oder verwirft Zuordnungen, in der Übersicht oder per ausdrücklichem Auftrag an seine KI.
Entspricht **Prozessschritten 3.1 – 3.4**.[^business-process]

### UC-07 Antrag einreichen
Der Berater reicht den vollständigen Antrag ein; CredEx übermittelt das Dossier an die Glarner KB.
Entspricht **Prozessschritten 4.1 – 4.5**.[^business-process]

### UC-09 Nutzung auswerten
Das Partnermanagement wertet Nutzung und Zeitersparnis pro Partner aus.
Entspricht **Prozessschritt 6.1**.[^business-process]

---

## Beziehungen

| Beziehung | Art | Beschreibung |
|---|---|---|
| UC-04 Dokument ablegen → UC-03 Pflichtliste abfragen | `<<include>>` | Ohne Pflichtliste kann die Partner-KI nicht zuordnen. |
| UC-07 Antrag einreichen → UC-05 Vollständigkeit prüfen | `<<include>>` | Vor jedem Einreichen wird die Vollständigkeit geprüft. |

[^business-process]: [Soll-Prozess](../business_process/businessProcess.md)
