---
title: "Validierung – Gespräche mit CTO und Beratenden"
linkTitle: "Validierungsgespräche"
type: validation
description: "Validierung der Anforderungen mit dem CTO von CredEx, Beratenden eines Grosspartners und einem Broker; Plan, Fragen und Ergebnisse."
weight: 1
tags: [berater, antrag, pflichtdokument, zuordnung, team, kreditnehmer]
sources:
  - id: benutzerrollen
    resource: /personas/benutzerrollen.md
  - id: epics
    resource: /epics/epics.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Validierung – Gespräche mit CTO und Beratenden

## Ziel

Die Anforderungen mit den Betroffenen prüfen, bevor der PoC getestet wird – die Antwort auf das Feedback aus Modul 1 («Anforderungen besser verstehen und validieren»). Geprüft werden vor allem die Annahmen in den [Personas](../personas/benutzerrollen.md), die Stories des Pilots und das grösste offene Risiko aus dem [Hypothesenbaum](../problem/ausgangslage.md): Nutzen Grosspartner ihre KI über MCP?

## Vorgehen

| Gespräch | Mit | Fokus | Methode | Termin |
|---|---|---|---|---|
| V1 | CTO CredEx (T. Cruz) | Scope, MCP-Werkzeuge, Datenmodell, Datei-Übertragung, Pilotpartner, Testpersonen | strukturiertes Interview, Fachklassenmodell und Systemkontext zeigen | *ausstehend* |
| V2 | 1 bis 2 Beratende eines Grosspartners | Personas, Stories, Übersicht, genutzte KI | Klickprototyp zeigen, Stories nach Wichtigkeit sortieren lassen | *ausstehend* |
| V3 | Broker ohne eigene IT (optional) | Persona Reto, Einrichtung ohne IT | kurzes Interview | *ausstehend* |

## Fragen

**V1 – CTO**

1. Passt der Scope (MCP-Server, Übersicht, Protokoll) zur Planung von Phase 1?
2. Welche Partner nutzen heute welche KI? Wer käme als Pilotpartner in Frage?
3. Passt das [Fachklassenmodell](../domain_model/domainModel.md) zum Datenmodell? Kennt die Plattform Teams?
4. Wie sollen grosse Dateien übertragen werden; welche Formate und Grössen sind zulässig?
5. Gibt es eine bestehende Anmeldung (OAuth) für Partner?
6. Wer informiert die Kreditnehmer über die KI-Nutzung?
7. Können Sie 3 bis 5 Beratende für einen Test im November vermitteln?

**V2 – Beratende**

1. Wie läuft ein Upload bei CredEx heute? Wo verlieren Sie Zeit?
2. Welche KI nutzen Sie, und darf sie auf Kundendokumente zugreifen?
3. (Klickprototyp) Was ist unklar? Was fehlt in der Übersicht?
4. Wann würden Sie einer Zuordnung der KI vertrauen, wann prüfen?
5. Würden Sie lieber in der Übersicht oder per Auftrag an die KI bestätigen?
6. Welche Story ist am wichtigsten? (Karten sortieren)

## Ergebnisse

| Frage | Ergebnis | Folge für die Anforderungen |
|---|---|---|
| V1 | *ausstehend* | |
| V2 | *ausstehend* | |
| V3 | *ausstehend* | |

## Änderungen an den Artefakten

Noch keine. Jede Folge aus den Gesprächen wird ein eigener Change Request in den [Quellen](../sources/_index.md).
