---
paths:
  - content/domain_model/**
---

# Konventionen Fachklassenmodell

## Dateien
- `domainModel.md` – das Fachklassenmodell auf einen Blick
- `domainModel.puml` – PlantUML-Klassendiagramm (spiegelt die Entitätsseiten exakt)
- `entities/{klassenname}.md` – eine Seite pro Klasse, camelCase ohne Umlaute (`kiVerbindung.md`, `pruefer.md`)

## Aufbau `domainModel.md`
```
# Fachklassenmodell – {Systemname}
## Überblick          → Ein Absatz zum Umfang; was neu ist in Phase 1 und was es in der CredEx-Plattform schon gibt
## Klassendiagramm    → ![Fachklassenmodell – {Systemname}](domainModel.puml)
## Klassen            → Aufzählung mit Link auf jede Entität, in der Reihenfolge des Diagramms
## Beziehungen        → Kompakte Notation + beschreibende Tabelle
```

## Aufbau `entities/{klassenname}.md`
```
# {Klassenname}
{Ein Satz, was die Klasse darstellt.} Teil des [Fachklassenmodells](../domainModel.md).
**Herkunft:** neu in Phase 1 · existiert in der CredEx-Plattform
## Attribute          → Tabelle: Attribut | Typ | Beschreibung
```
- Frontmatter: `type: entity`; `title: {Klassenname}` ohne `linkTitle`; der eine Satz als
  `description`; `weight` in Diagrammreihenfolge; `tags` beginnend mit dem eigenen Tag
- Andere Artefakte verlinken die Entitätsseite, nie einen Anker in `domainModel.md`

## Klassenkonventionen
- Fachliche Sicht: keine Methoden, keine technischen Schlüssel
- Typen: `String`, `Integer`, `Decimal`, `Boolean`, `Date`, `DateTime`, `Enum`
- Enum-Werte inline in GROSSBUCHSTABEN mit Unterstrich (`Enum {IN_ERFASSUNG, EINGEREICHT}`)

## Beziehungen
- Kompakte Notation mit Multiplizitäten: `Antrag "1" -- "0..*" Dokument : enthält`
- Danach eine Tabelle: `Beziehung | Beschreibung`

## PlantUML
- `@startuml` / `@enduml`, `skinparam classAttributeIconSize 0`, `skinparam linetype ortho`; kein eigenes Styling (siehe «Diagrammstil» in `AGENTS.md`)
- Alle Attribute mit Typ in den `class`-Blöcken
- Klassen, die neu in Phase 1 sind, tragen das Stereotyp `<<neu>>`
- Beziehungen: `Antrag "1" -- "0..*" Dokument : enthält >`
