---
paths:
  - content/use_case/**
---

# Konventionen Use Cases

## Dateien
- `useCaseDiagram.puml` – PlantUML-Use-Case-Diagramm
- `useCaseDiagram.md` – Akteure, Use Cases und Beziehungen

## Aufbau `useCaseDiagram.md`
```
# Use-Case-Diagramm – {Systemname}
## Überblick          → Ein Absatz + Link auf den Soll-Prozess
## Diagramm           → ![Use-Case-Diagramm – {Systemname}](useCaseDiagram.puml)
## Akteure            → Tabelle: Akteur | Art (Primär / Unterstützend / System) | Beschreibung
## Use Cases          → Ein H3 pro Use Case mit kurzer Beschreibung und Rückverweis auf Prozessschritte
## Beziehungen        → Tabelle: Beziehung | Art (include / Generalisierung) | Beschreibung
```

## Akteurseiten
`actorDescriptions.md` listet jeden Akteur als Link; jeder Akteur hat eine eigene Seite in `actors/`.

- `actors/{akteurname}.md` – camelCase (`partnerKi.md` für «Partner-KI»), `type: actor`
- Aufbau:
  ```
  # {Akteurname}
  **Art:** Primär / Unterstützend / System
  ## Beschreibung    → Wer oder was der Akteur ist, und seine Rolle im Soll-Prozess
  ## Systemzugriff   → Worauf der Akteur zugreifen kann und worauf nicht
  ```

## Akteure
- Jeder Akteur stammt aus dem Soll-Prozess – keine erfundenen Akteure
- Primär (löst die Interaktion aus), Unterstützend (liefert einen Dienst), System (externes System)
- Gleiche Namen wie in der Prozesslegende («Berater/in», «Partner-KI», «Glarner KB»)
- Die Beschreibung verweist auf die Rolle im Prozess (z.B. «Entspricht 🟦 Berater/in im Soll-Prozess»)

## Use Cases
- IDs aus dem Detailkonzept (`UC-01` … `UC-09`) bleiben erhalten; Titel `UC-{nn} {Name}`
- Benennung **Verb am Ende, Objekt vorne**, 2–4 Wörter, wie in der Gruppe üblich («Dokument ablegen»)
- Jeder Use Case bekommt ein H3 (`### UC-04 Dokument ablegen`) mit
  - einem Satz zum Ziel
  - einem **Rückverweis** auf die Prozessschritte mit Fussnote (z.B. «Entspricht **Prozessschritten
    3.1 – 3.4**.[^business-process]»)
- Use Cases mit Leerzeilen trennen (keine `---`-Linien)

## Beziehungen
- **`<<include>>`** – für Abläufe, die immer mit ausgeführt werden (Pfeil vom Basis- zum
  inkludierten Use Case)
- **Generalisierung** – zwischen Akteuren (Kundenberater/in und Hypothekarbroker/in sind Berater/in)
- Jede Beziehung in der `.puml`-Datei hat eine Zeile in der Markdown-Tabelle

## PlantUML Use-Case-Diagramm
- `@startuml` / `@enduml`, `left to right direction`, `skinparam actorStyle awesome`
- Systemgrenze: `rectangle "CredEx-Plattform · Phase 1" { … }`
- Primäre Akteure **links**, System-Akteure **rechts**
- `usecase "UC-04\nDokument ablegen" as UC04`
- Akteure mit `--` verbunden, Beziehungen mit `..>`
- Diagramm **flach** – keine verschachtelten Rechtecke in der Systemgrenze

## Detaillierte Use-Case-Beschreibungen

Jeder Use Case bekommt einen **Unterordner** in `use_case/` (snake_case, z.B. `use_case/dokument_ablegen/`).

### Dateien pro Use Case
- `{useCaseName}.md` – Beschreibung (camelCase)
- `{useCaseName}.puml` – PlantUML-Aktivitätsdiagramm (camelCase)

### Aufbau
```
# Use Case – UC-{nn} {Name}
## Überblick          → Ein Absatz + Links auf Use-Case-Diagramm und Soll-Prozess; Priorität und Kritikalität
## Vorbedingungen     → Aufzählung
## Nachbedingungen    → nach Ausgang gruppiert (Erfolg / Fehler)
## Beschreibung       → Ein Absatz Erzählung mit Klassennamen, inkl. Alternativ- und Ausnahmeszenarien in Worten
## Qualitätsanforderungen → Links auf die NFA, die für diesen Use Case gelten
## Aktivitätsdiagramm → ![Aktivitätsdiagramm – UC-{nn} {Name}]({useCaseName}.puml)
```

### Inhalt
- Vor- und Nachbedingungen nennen Fachklassen mit Attributen und Status (z.B. «Antrag mit `status = IN_ERFASSUNG`»)
- Die Beschreibung fasst die Absicht zusammen und wiederholt das Diagramm nicht Schritt für Schritt
- Rückverweis auf die Prozessschritte mit `[^business-process]`
- `---` trennt die Hauptabschnitte

### PlantUML-Aktivitätsdiagramm
- `@startuml` / `@enduml`, `!theme plain`
- Titel: `title Aktivitätsdiagramm – UC-{nn} {Name}`
- Swimlanes `|Berater/in|`, `|Partner-KI|`, `|CredEx-System|` wo mehrere Akteure handeln
- `:aktion;` für Tätigkeiten, `if (...) then (...)` / `else (...)` für Entscheidungen
- `repeat` / `repeat while (...)` für Schleifen
- `stop` für jeden Endpfad
- Klassennamen in den Aktionen (z.B. «CredEx-System speichert Dokument im Antrag»)
- Beschriftungen kurz, max. 2 Zeilen mit `\n`
