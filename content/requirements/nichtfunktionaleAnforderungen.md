---
title: "Nicht-funktionale Anforderungen – CredEx Phase 1"
linkTitle: "Nicht-funktionale Anforderungen"
type: requirement-catalog
description: "Die nicht-funktionalen Anforderungen NFA-01 bis NFA-15 nach ISO/IEC 25010 mit Abnahmekriterium, dazu die Restriktionen R-01 bis R-08."
weight: 3
tags: [dokument, zuordnung, protokolleintrag, antrag, berater, ki-verbindung]
sources:
  - id: geschaeftsanforderungen
    resource: /requirements/geschaeftsanforderungen.md
  - id: system-context
    resource: /system_context/systemContext.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
  - id: cr-1-6
    resource: /sources/cr_1_6.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T11:00:54Z
---

# Nicht-funktionale Anforderungen – CredEx Phase 1

> [!NOTE] v1.3 – Neu 2026-11-07
> Abschnitt Restriktionen R-01 bis R-08.

> [!NOTE] v1.2 – Geändert 2026-11-07
> NFA-04 gilt für alle acht Werkzeuge.

## Überblick

Die nicht-funktionalen Anforderungen legen fest, wie gut das System sein muss, gegliedert nach ISO/IEC 25010. Quelle ist das Anforderungs-Excel der Gruppe (Stand 31.10.2026); die IDs sind dieselben. Abgeleitet sind sie aus den [Geschäftsanforderungen](geschaeftsanforderungen.md) und dem [Systemkontext](../system_context/systemContext.md). Zielwerte sind Vorschläge und werden mit den Stakeholdern und im PoC validiert. Wichtigkeit Hoch = Must, Mittel = Should.

---

## Anforderungen

| ID | Merkmal (ISO 25010) | Anforderung | Abnahmekriterium (Abnahme erfolgt, wenn …) | Wichtigkeit |
|---|---|---|---|---|
| NFA-01 | Funktionale Eignung: Korrektheit | Höchstens 2 % der Dokumente mit Status „zugeordnet“ dürfen falsch zugeordnet sein. | Wenn beim Abgleich der Testläufe mit der Musterlösung des Testdossiers höchstens 2 % der als „zugeordnet“ markierten Dokumente falsch sind. | Hoch |
| NFA-02 | Leistungseffizienz: Zeitverhalten | Das System muss 95 % der Ablagen bis 32 MB innert 3 s nach Ende der Übertragung bestätigen. | Wenn im Lasttest (100 Ablagen) mind. 95 % der Bestätigungen laut Serverlog höchstens 3 s dauern. | Mittel |
| NFA-03 | Leistungseffizienz: Kapazität | Das System muss pro Antrag bis 40 Dateien à max. 32 MB annehmen, auch bei 20 parallel bearbeiteten Anträgen. | Wenn der Lasttest mit 20 parallelen Anträgen à 40 Dateien ohne Fehler durchläuft. | Mittel |
| NFA-04 | Kompatibilität: Interoperabilität | Die MCP-Werkzeuge müssen der offenen MCP-Spezifikation entsprechen und mit mind. 2 KI-Clients funktionieren. | Wenn alle acht Werkzeuge in Testfällen mit Claude und Copilot das erwartete Ergebnis liefern. | Hoch |
| NFA-05 | Kompatibilität: Koexistenz | Die bestehende Schnittstelle zur Glarner KB darf nicht verändert werden. | Wenn der Regressionstest der Dossierübergabe an die Glarner KB ohne Abweichung durchläuft und keine Änderung an der Schnittstelle nötig war. | Hoch |
| NFA-06 | Benutzbarkeit: Erlernbarkeit | Beratende müssen die Übersicht ohne Schulung bedienen können. | Wenn im Usability-Test (16. bis 18.11.2026) mind. 4 von 5 Beratenden den Testantrag ohne Hilfe einreichen. | Hoch |
| NFA-07 | Benutzbarkeit: Zugänglichkeit | Jeder Status muss mit Symbol und Text angezeigt werden, der Textkontrast muss mind. 4.5:1 betragen. | Wenn alle Status in der Graustufenansicht unterscheidbar sind und das Kontrast-Tool für alle Texte mind. 4.5:1 misst. | Mittel |
| NFA-08 | Verlässlichkeit: Verfügbarkeit | Der MCP-Server muss Mo bis Fr von 7 bis 19 Uhr zu mind. 99.5 % pro Monat verfügbar sein. | Wenn das Monitoring im Monatsreport mind. 99.5 % Verfügbarkeit im Zeitfenster ausweist. | Mittel |
| NFA-09 | Verlässlichkeit: Fehlertoleranz | Bricht eine Übertragung ab, darf keine Teilablage entstehen und die Partner-KI muss eine Fehlermeldung erhalten. | Wenn im Abbruchtest (Verbindung während des Uploads trennen) 0 Teilablagen entstehen, die KI eine Fehlermeldung erhält und eine erneute Ablage kein Duplikat erzeugt. | Mittel |
| NFA-10 | Sicherheit: Vertraulichkeit | Das System darf der angemeldeten Person nur die Anträge und Dokumente ihres Teams zugänglich machen. | Wenn Testlogins aus einem fremden Team keinen Antrag sehen oder abrufen können und der Penetrationstest 0 teamfremde Zugriffe findet. | Hoch |
| NFA-11 | Sicherheit: Integrität | Die an die Glarner KB übergebene Datei muss bitgleich mit der abgelegten Datei sein. | Wenn die Prüfsummen (SHA-256) bei Ablage und Übergabe für alle Testdateien identisch sind. | Mittel |
| NFA-12 | Sicherheit: Nachweisbarkeit | Das Protokoll muss lückenlos sein: 100 % der Aktionen mit Zeit, Akteur und Quelle (KI oder Mensch). | Wenn nach einem Testlauf jede durchgeführte Aktion im Protokoll steht. Aufbewahrungsdauer: offen, mit Compliance Glarner KB klären. | Hoch |
| NFA-13 | Sicherheit: Datenhaltung | Dokumente und Protokolle dürfen ausschliesslich in Rechenzentren in der Schweiz gespeichert und verarbeitet werden. | Wenn Hosting-Vertrag und Infrastruktur-Konfiguration ausschliesslich Standorte in der Schweiz ausweisen. | Hoch |
| NFA-14 | Sicherheit: Vertraulichkeit | Dokumente müssen bei der Übertragung (TLS 1.2 oder höher) und bei der Speicherung (AES-256) verschlüsselt sein. | Wenn der TLS-Scan nur TLS 1.2 oder höher zulässt und das Konfigurationsreview AES-256 für die Speicherung bestätigt. | Hoch |
| NFA-15 | Portierbarkeit: Installierbarkeit | Partner müssen ihre KI ohne Softwareinstallation in max. 30 Min. pro KI-Client mit CredEx verbinden können. | Wenn eine Partner-IT die Verbindung nach Anleitung in höchstens 30 Min. einrichtet (Zeit gestoppt). | Hoch |

**Bewusst ohne eigene Anforderung:** Wartbarkeit (der MCP-Server wird intern nach den Entwicklungsstandards von CredEx gebaut, Teamentscheid 31.10.2026), Ressourcennutzung, Attraktivität, Reife und Wiederherstellbarkeit (über das bestehende Backup der CredEx-Plattform). Einziger Lieferant ist das Hosting im bestehenden Swisscom-Rechenzentrum.

---

## Restriktionen

Restriktionen sind nicht verhandelbar und schränken den Lösungsraum ein (Einteilung nach Glinz, Kick-off Modul 2). Sie stehen deshalb getrennt von den Qualitätsanforderungen.

| ID | Restriktion | Art | Herkunft | Wirkung |
|---|---|---|---|---|
| R-01 | Personendaten der Kreditnehmer werden nach dem Schweizer Datenschutzgesetz (DSG) bearbeitet. | regulatorisch | DSG; Interview CTO CredEx | NFA-10, NFA-13, NFA-14 |
| R-02 | Dokumente und Protokolle werden nur in der Schweiz gespeichert und verarbeitet. | regulatorisch, vertraglich | Modul 1; bestehender Vertrag mit dem Swisscom-Rechenzentrum | NFA-13 |
| R-03 | Die Verarbeitung durch die Partner-KI und die Information der Kreditnehmer darüber liegen in der Verantwortung des Partners. | organisatorisch, rechtlich | Teamentscheid [E06](../decisions/e06Us09Gestrichen.md); rechtliche Klärung offen | keine Systemfunktion |
| R-04 | Die bestehende Schnittstelle zur Glarner KB bleibt unverändert. | technisch | GA5; Interview PostFinance | NFA-05, NFA-11 |
| R-05 | Kernsysteme der Partner werden nicht angebunden. | technisch, wirtschaftlich | Scope Phase 1 ([E02](../decisions/e02ScopeNurPhase1.md)) | Option C ausgeschieden |
| R-06 | Der MCP-Server folgt dem offenen MCP-Standard; keine anbieterspezifische Erweiterung. | technisch | [E03](../decisions/e03OffenerMcpStattCopilot.md) | NFA-04 |
| R-07 | CredEx baut den MCP-Server intern nach den eigenen Entwicklungsstandards. | organisatorisch | [E08](../decisions/e08McpServerIntern.md) | keine Wartbarkeits-NFA |
| R-08 | Budget Phase 1: Investition Jahr 0 CHF 71'840; Phase 2 erst nach Go/No-Go. | wirtschaftlich | Business Case Modul 1 | [Umsetzungsplan](../delivery/umsetzungsplan.md) |

---

## Offene Punkte

- Zielwerte für NFA-01 (Korrektheit) und NFA-02 (Zeitverhalten) nach dem PoC-Test festlegen.
- NFA-12: Aufbewahrungsdauer der Protokolleinträge mit der Compliance der Glarner KB klären.
- Das Detailkonzept (Kapitel 6.3) führt noch eine ältere Liste mit 9 NFA und anderen IDs; massgebend ist diese Liste.
