---
title: "Change Log – CredEx Phase 1"
linkTitle: "Change Log"
type: change-log
description: "Versionsgeschichte der Produktdokumentation CredEx Phase 1 mit jedem erstellten oder geänderten Artefakt."
weight: 1
sources:
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-1
    resource: /sources/cr_1_1.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T09:55:00Z
---

# Change Log – CredEx Phase 1

## So liest man dieses Log

Jeder Versionsabschnitt nennt **jedes Artefakt, das erstellt oder geändert wurde**, mit Link und kurzer Beschreibung. Hinweise in den Artefakten und Diagrammmarker einer Version werden nach **zwei weiteren Versionen** entfernt.

**Versionsmarker:**

| Marker | Bedeutung |
|---|---|
| 🟢 `neu` | Artefakt oder Element in dieser Version hinzugefügt |
| 🟡 `geändert` | Bestehendes Artefakt oder Element geändert |
| 🔴 `veraltet` | Artefakt oder Element zur Entfernung vorgesehen |
| ⚫ `entfernt` | Artefakt oder Element gelöscht |

---

## v1.1 – Lesbarere Diagramme (2026-11-07)

Alle Diagramme einheitlich und übersichtlich: gemeinsamer PlantUML-Stil, Soll-Prozess als BPMN in zwei Teilen, Systemkontext in D2; inhaltlich unverändert. Siehe [CR-1.1](../sources/cr_1_1.md).

| Artefakt | Status | Beschreibung |
|---|---|---|
| [Soll-Prozess – Dokumentenupload über die eigene KI des Partners](../business_process/businessProcess.md) | 🟡 geändert | Diagramm als BPMN in zwei Teilen |
| [sollProzessTeil1.bpmn](../business_process/sollProzessTeil1.bpmn) | 🟢 neu | BPMN Teil 1 – Ablage durch die Partner-KI |
| [sollProzessTeil2.bpmn](../business_process/sollProzessTeil2.bpmn) | 🟢 neu | BPMN Teil 2 – Prüfen und Einreichen |
| [Systemkontext – CredEx Phase 1](../system_context/systemContext.md) | 🟡 geändert | Diagramm in D2 |
| [systemContext.d2](../system_context/systemContext.d2) | 🟢 neu | D2-Quelle |
| [Fachklassenmodell – CredEx Phase 1](../domain_model/domainModel.md) | 🟡 geändert | Hinweis v1.1 |
| [domainModel.puml](../domain_model/domainModel.puml) | 🟡 geändert | Gemeinsamer Stil, rechtwinklige Linien |
| [Use-Case-Diagramm – CredEx Phase 1](../use_case/useCaseDiagram.md) | 🟡 geändert | Hinweis v1.1 |
| [useCaseDiagram.puml](../use_case/useCaseDiagram.puml) | 🟡 geändert | Neue Anordnung |
| [Use Case – UC-06 Zuordnung bestätigen oder ändern](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) | 🟡 geändert | Hinweis v1.1 |
| [antragEinreichen.puml](../use_case/antrag_einreichen/antragEinreichen.puml) | 🟡 geändert | Gemeinsamer Stil, Swimlane-Farben |
| [dokumentAblegen.puml](../use_case/dokument_ablegen/dokumentAblegen.puml) | 🟡 geändert | Gemeinsamer Stil, Swimlane-Farben |
| [kiVerbinden.puml](../use_case/ki_verbinden/kiVerbinden.puml) | 🟡 geändert | Gemeinsamer Stil, Swimlane-Farben |
| [nutzungAuswerten.puml](../use_case/nutzung_auswerten/nutzungAuswerten.puml) | 🟡 geändert | Gemeinsamer Stil, Swimlane-Farben |
| [offeneAntraegeAbrufen.puml](../use_case/offene_antraege_abrufen/offeneAntraegeAbrufen.puml) | 🟡 geändert | Gemeinsamer Stil, Swimlane-Farben |
| [pflichtlisteAbfragen.puml](../use_case/pflichtliste_abfragen/pflichtlisteAbfragen.puml) | 🟡 geändert | Gemeinsamer Stil, Swimlane-Farben |
| [vollstaendigkeitPruefen.puml](../use_case/vollstaendigkeit_pruefen/vollstaendigkeitPruefen.puml) | 🟡 geändert | Gemeinsamer Stil, Swimlane-Farben |
| [zuordnungBestaetigen.puml](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.puml) | 🟡 geändert | Gemeinsamer Stil, Swimlane-Farben; Entscheid als switch vereinfacht |
| [Zustandsdiagramm – Dokument](../state_chart/dokumentStateChart.md) | 🟡 geändert | Hinweis v1.1 |
| [dokumentStateChart.puml](../state_chart/dokumentStateChart.puml) | 🟡 geändert | Waagrecht, Statusfarben |
| [Zustandsdiagramm – Antrag](../state_chart/antragStateChart.md) | 🟡 geändert | Hinweis v1.1 |
| [antragStateChart.puml](../state_chart/antragStateChart.puml) | 🟡 geändert | Waagrecht, gemeinsamer Stil |
| [Startseite](../_index.md) | 🟡 geändert | Mermaid-Übersicht gestaltet |
| [Change Log – CredEx Phase 1](changeLog.md) | 🟡 geändert | Dieser Eintrag |
| [Log](../log.md) | 🟡 geändert | Mit v1.1 neu erzeugt |
| [CR-1.1](../sources/cr_1_1.md) | 🟢 neu | Der Change Request zu dieser Version |

---

## v1.0 – Erstfassung Phase 1 (2026-11-07)

Erstfassung der Produktdokumentation CredEx Phase 1 aus dem Arbeitsstand der Gruppe 6, mit den Teamentscheiden bis 07.11.2026 und markierten Annahmen. Siehe [CR-1.0](../sources/cr_1_0.md).

| Artefakt | Status | Beschreibung |
|---|---|---|
| [Fachklassenmodell – CredEx Phase 1](../domain_model/domainModel.md) | 🟢 neu | Erstfassung |
| [domainModel.puml](../domain_model/domainModel.puml) | 🟢 neu | PlantUML-Quelle |
| [Antrag](../domain_model/entities/antrag.md) | 🟢 neu | Erstfassung |
| [Berater](../domain_model/entities/berater.md) | 🟢 neu | Erstfassung |
| [Dokument](../domain_model/entities/dokument.md) | 🟢 neu | Erstfassung |
| [Dokumenttyp](../domain_model/entities/dokumenttyp.md) | 🟢 neu | Erstfassung |
| [KiVerbindung](../domain_model/entities/kiVerbindung.md) | 🟢 neu | Erstfassung |
| [Kreditnehmer](../domain_model/entities/kreditnehmer.md) | 🟢 neu | Erstfassung |
| [Partner](../domain_model/entities/partner.md) | 🟢 neu | Erstfassung |
| [Pflichtdokument](../domain_model/entities/pflichtdokument.md) | 🟢 neu | Erstfassung |
| [Protokolleintrag](../domain_model/entities/protokolleintrag.md) | 🟢 neu | Erstfassung |
| [Prüfer](../domain_model/entities/pruefer.md) | 🟢 neu | Erstfassung |
| [Zuordnung](../domain_model/entities/zuordnung.md) | 🟢 neu | Erstfassung |
| [Soll-Prozess – Dokumentenupload über die eigene KI des Partners](../business_process/businessProcess.md) | 🟢 neu | Erstfassung |
| [Systemkontext – CredEx Phase 1](../system_context/systemContext.md) | 🟢 neu | Erstfassung |
| [Use-Case-Diagramm – CredEx Phase 1](../use_case/useCaseDiagram.md) | 🟢 neu | Erstfassung |
| [useCaseDiagram.puml](../use_case/useCaseDiagram.puml) | 🟢 neu | PlantUML-Quelle |
| [Akteurbeschreibungen – CredEx Phase 1](../use_case/actorDescriptions.md) | 🟢 neu | Erstfassung |
| [Berater/in](../use_case/actors/berater.md) | 🟢 neu | Erstfassung |
| [CredEx-System](../use_case/actors/credexSystem.md) | 🟢 neu | Erstfassung |
| [Glarner KB](../use_case/actors/glarnerKb.md) | 🟢 neu | Erstfassung |
| [Partner-IT](../use_case/actors/partnerIt.md) | 🟢 neu | Erstfassung |
| [Partner-KI](../use_case/actors/partnerKi.md) | 🟢 neu | Erstfassung |
| [Partnermanagement](../use_case/actors/partnermanagement.md) | 🟢 neu | Erstfassung |
| [Use Case – UC-07 Antrag einreichen](../use_case/antrag_einreichen/antragEinreichen.md) | 🟢 neu | Erstfassung |
| [antragEinreichen.puml](../use_case/antrag_einreichen/antragEinreichen.puml) | 🟢 neu | PlantUML-Quelle |
| [Use Case – UC-04 Dokument ablegen](../use_case/dokument_ablegen/dokumentAblegen.md) | 🟢 neu | Erstfassung |
| [dokumentAblegen.puml](../use_case/dokument_ablegen/dokumentAblegen.puml) | 🟢 neu | PlantUML-Quelle |
| [Use Case – UC-01 KI mit CredEx verbinden](../use_case/ki_verbinden/kiVerbinden.md) | 🟢 neu | Erstfassung |
| [kiVerbinden.puml](../use_case/ki_verbinden/kiVerbinden.puml) | 🟢 neu | PlantUML-Quelle |
| [Use Case – UC-09 Nutzung auswerten](../use_case/nutzung_auswerten/nutzungAuswerten.md) | 🟢 neu | Erstfassung |
| [nutzungAuswerten.puml](../use_case/nutzung_auswerten/nutzungAuswerten.puml) | 🟢 neu | PlantUML-Quelle |
| [Use Case – UC-02 Offene Anträge abrufen](../use_case/offene_antraege_abrufen/offeneAntraegeAbrufen.md) | 🟢 neu | Erstfassung |
| [offeneAntraegeAbrufen.puml](../use_case/offene_antraege_abrufen/offeneAntraegeAbrufen.puml) | 🟢 neu | PlantUML-Quelle |
| [Use Case – UC-03 Pflichtliste abfragen](../use_case/pflichtliste_abfragen/pflichtlisteAbfragen.md) | 🟢 neu | Erstfassung |
| [pflichtlisteAbfragen.puml](../use_case/pflichtliste_abfragen/pflichtlisteAbfragen.puml) | 🟢 neu | PlantUML-Quelle |
| [Use Case – UC-05 Vollständigkeit prüfen](../use_case/vollstaendigkeit_pruefen/vollstaendigkeitPruefen.md) | 🟢 neu | Erstfassung |
| [vollstaendigkeitPruefen.puml](../use_case/vollstaendigkeit_pruefen/vollstaendigkeitPruefen.puml) | 🟢 neu | PlantUML-Quelle |
| [Use Case – UC-06 Zuordnung bestätigen oder ändern](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) | 🟢 neu | Erstfassung |
| [zuordnungBestaetigen.puml](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.puml) | 🟢 neu | PlantUML-Quelle |
| [Zustandsdiagramm – Antrag](../state_chart/antragStateChart.md) | 🟢 neu | Erstfassung |
| [antragStateChart.puml](../state_chart/antragStateChart.puml) | 🟢 neu | PlantUML-Quelle |
| [Zustandsdiagramm – Dokument](../state_chart/dokumentStateChart.md) | 🟢 neu | Erstfassung |
| [dokumentStateChart.puml](../state_chart/dokumentStateChart.puml) | 🟢 neu | PlantUML-Quelle |
| [Epics & Story Map – CredEx Phase 1](../epics/epics.md) | 🟢 neu | Erstfassung |
| [US-1.1 – KI einmalig mit CredEx verbinden](../epics/user_stories/us_1_1.md) | 🟢 neu | Erstfassung |
| [US-2.1 – Offenen Antrag ohne Antragsnummer finden](../epics/user_stories/us_2_1.md) | 🟢 neu | Erstfassung |
| [US-2.2 – Nur Anträge im eigenen Zugriffsbereich sehen](../epics/user_stories/us_2_2.md) | 🟢 neu | Erstfassung |
| [US-3.1 – Pflichtliste für die Zuordnung kennen](../epics/user_stories/us_3_1.md) | 🟢 neu | Erstfassung |
| [US-4.1 – Unterlagen per Auftrag an die eigene KI ablegen](../epics/user_stories/us_4_1.md) | 🟢 neu | Erstfassung |
| [US-4.2 – Sammel-PDF aufteilen lassen](../epics/user_stories/us_4_2.md) | 🟢 neu | Erstfassung |
| [US-5.1 – Erfahren, was fehlt oder unsicher ist](../epics/user_stories/us_5_1.md) | 🟢 neu | Erstfassung |
| [US-6.1 – Status je Pflichtdokument auf einen Blick](../epics/user_stories/us_6_1.md) | 🟢 neu | Erstfassung |
| [US-6.2 – Unsichere Zuordnung bestätigen, ändern oder verwerfen](../epics/user_stories/us_6_2.md) | 🟢 neu | Erstfassung |
| [US-7.1 – Nur vollständig und nur selbst einreichen](../epics/user_stories/us_7_1.md) | 🟢 neu | Erstfassung |
| [US-9.1 – Nutzung und Zeitersparnis pro Partner sehen](../epics/user_stories/us_9_1.md) | 🟢 neu | Erstfassung |
| [Geschäftsanforderungen – CredEx Phase 1](../requirements/geschaeftsanforderungen.md) | 🟢 neu | Erstfassung |
| [Funktionale Anforderungen – CredEx Phase 1](../requirements/funktionaleAnforderungen.md) | 🟢 neu | Erstfassung |
| [Nicht-funktionale Anforderungen – CredEx Phase 1](../requirements/nichtfunktionaleAnforderungen.md) | 🟢 neu | Erstfassung |
| [Schnittstelle – CredEx MCP-Server](../interface/mcpSchnittstelle.md) | 🟢 neu | Erstfassung |
| [Startseite](../_index.md) | 🟢 neu | Fall, Artefaktliste, Ableitungskette |
| [CR-1.0 – Erstfassung der Produktdokumentation Phase 1](../sources/cr_1_0.md) | 🟢 neu | Erstfassung |
| [Change Log – CredEx Phase 1](changeLog.md) | 🟢 neu | Dieser Eintrag |
| [Log](../log.md) | 🟢 neu | Erzeugt aus diesem Change Log |
