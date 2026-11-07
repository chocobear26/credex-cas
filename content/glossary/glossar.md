---
title: "Glossar – CredEx Phase 1"
linkTitle: "Glossar"
type: glossary
description: "Alle Fachbegriffe von CredEx Phase 1 von A bis Z, mit Bedeutung und Link."
weight: 1
tags: [antrag, berater, dokument, dokumenttyp, kreditnehmer, ki-verbindung, partner, pflichtdokument, protokolleintrag, pruefer, team, zuordnung]
sources:
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:45:00Z
---

# Glossar – CredEx Phase 1

## Überblick

Alle Begriffe, die in dieser Dokumentation eine feste Bedeutung haben. Fachklassen verlinken ihre Entitätsseite.

---

## A

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Antrag** | Hypothekarantrag eines Partners auf der CredEx-Plattform, in sechs Schritten erfasst; Phase 1 betrifft Schritt 5 «Hochladen». | [Antrag](../domain_model/entities/antrag.md) |

---

## B

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Berater/in** | Person beim Partner, die Anträge erfasst und einreicht: Kundenberaterin einer Bank oder Hypothekarbroker. | [Berater](../domain_model/entities/berater.md), [Akteur](../use_case/actors/berater.md) |
| **BPMN** | Business Process Model and Notation 2.0, Notation des Soll-Prozesses. | [Soll-Prozess](../business_process/businessProcess.md) |
| **Business Case** | Wirtschaftlichkeitsrechnung aus Modul 1 (NPV CHF 34'186). | [Ausgangslage](../problem/ausgangslage.md) |

---

## C

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Change Request** | Aufgeschriebene Änderung an der Dokumentation, Grundlage jeder Version. | [Quellen](../sources/_index.md) |
| **CredEx** | Credit Exchange, B2B-Marktplatz für Hypotheken. | [Ausgangslage](../problem/ausgangslage.md) |

---

## D

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **DMS** | Dokumentenablagesystem des Partners, z.B. SharePoint; Quelle der Kundendokumente. | [Systemkontext](../system_context/systemContext.md) |
| **Dokument** | Im Antrag abgelegte Datei, ganz oder als Seitenbereich eines Sammel-PDF. | [Dokument](../domain_model/entities/dokument.md) |
| **Dokumenttyp** | Art einer Unterlage, z.B. Lohnausweis, mit erlaubten Formaten. | [Dokumenttyp](../domain_model/entities/dokumenttyp.md) |

---

## G

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Glarner KB (GLKB)** | Glarner Kantonalbank; prüft die Dossiers und schliesst die Hypotheken rechtlich ab. | [Akteur](../use_case/actors/glarnerKb.md) |

---

## K

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **KANO** | Modell zur Einordnung von Anforderungen in Basis-, Leistungs- und Begeisterungsmerkmale. | [Story Map](../epics/epics.md) |
| **KiVerbindung** | Eingerichtete Verbindung zwischen dem KI-Client eines Beraters und dem MCP-Server. | [KiVerbindung](../domain_model/entities/kiVerbindung.md) |
| **Konfidenz** | Wert zwischen 0 und 1, wie sicher die KI eine Zuordnung ist. | [Zuordnung](../domain_model/entities/zuordnung.md) |
| **Kreditnehmer** | Person, für die ein Antrag gestellt wird. | [Kreditnehmer](../domain_model/entities/kreditnehmer.md) |

---

## M

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **MCP** | Model Context Protocol: offener Standard, über den KI-Assistenten Werkzeuge externer Systeme aufrufen; seit November 2024, unterstützt u.a. von ChatGPT, Copilot und Claude. | [MCP-Schnittstelle](../interface/mcpSchnittstelle.md) |
| **MCP-Server** | Der Teil von CredEx, der der Partner-KI Werkzeuge anbietet; neu in Phase 1. | [Komponenten](../architecture/komponenten.md) |
| **MCP-Werkzeug** | Eine Funktion des MCP-Servers, z.B. `credex_dokument_ablegen`; acht in Phase 1. | [MCP-Schnittstelle](../interface/mcpSchnittstelle.md) |
| **MoSCoW** | Priorisierung in Must, Should, Could, Won't. | [Story Map](../epics/epics.md) |

---

## N

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Nutzwertanalyse** | Bewertung von Optionen mit gewichteten Kriterien. | [Nutzwertanalyse](../evaluation/nutzwertanalyse.md) |

---

## O

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **OAuth** | Standard für die Anmeldung; jede Beraterin meldet sich einzeln an. | [UC-01](../use_case/ki_verbinden/kiVerbinden.md) |
| **OKF** | Open Knowledge Format, das Format dieser Dokumentation. | [Startseite](../_index.md) |

---

## P

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Partner** | Distributionspartner von CredEx: Bank, Versicherung oder Broker. | [Partner](../domain_model/entities/partner.md) |
| **Partner-KI** | KI-Assistent des Partners, z.B. Copilot; ruft die MCP-Werkzeuge auf. | [Akteur](../use_case/actors/partnerKi.md) |
| **Persona** | Fiktive, aus Interviews abgeleitete Nutzerin; hier Sandra Keller und Reto Frei. | [Personas](../personas/benutzerrollen.md) |
| **Pflichtdokument** | Unterlage, die CredEx für einen Antrag verlangt; heute ein Upload-Feld. | [Pflichtdokument](../domain_model/entities/pflichtdokument.md) |
| **Pflichtliste** | Alle Pflichtdokumente eines Antrags mit Status. | [UC-03](../use_case/pflichtliste_abfragen/pflichtlisteAbfragen.md) |
| **PoC** | Proof of Concept: lauffähiger MCP-Server mit Testdossier und Übersicht. | [PoC](../prototype/pocMcpServer.md) |
| **Protokolleintrag** | Eintrag im Protokoll eines Antrags: wer wann was getan hat. | [Protokolleintrag](../domain_model/entities/protokolleintrag.md) |
| **Prüfer/in** | Person bei der Glarner KB, die eingereichte Anträge prüft. | [Prüfer](../domain_model/entities/pruefer.md) |

---

## S

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Sammel-PDF** | PDF mit mehreren Unterlagen; die KI teilt es nach Seiten auf. | [US-4.2](../epics/user_stories/us_4_2.md) |
| **Schwelle** | Konfidenz, ab der eine Zuordnung als sicher gilt; Startwert 0.80. | [Zustandsdiagramm Dokument](../state_chart/dokumentStateChart.md) |
| **Swiss AI Platform** | KI-Plattform der Swisscom; vorgesehen für die integrierte CredEx-KI in Phase 2. | [E01](../decisions/e01VarianteZuerstMcp.md) |

---

## T

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Team** | Gruppe von Beratern eines Partners mit gemeinsamem Zugriff auf Anträge. | [Team](../domain_model/entities/team.md) |

---

## U

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Übersicht** | Erweiterung von Schritt 5 im CredEx-Tool: Status je Pflichtdokument, Prüfen, Einreichen. | [UC-06](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) |

---

## W

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Weiteres Dokument** | Ziel einer Zuordnung ohne Pflichtdokument. | [Zuordnung](../domain_model/entities/zuordnung.md) |

---

## Z

| Begriff | Bedeutung | Siehe |
|---|---|---|
| **Zuordnung** | Verknüpfung eines Dokuments mit einem Pflichtdokument, von der KI vorgeschlagen oder vom Berater bestätigt. | [Zuordnung](../domain_model/entities/zuordnung.md) |
