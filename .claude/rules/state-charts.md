---
paths:
  - content/state_chart/**
---

# Konventionen Zustandsdiagramme

## Wann
- Nur für Fachklassen mit einem **Enum-Attribut `status`**
- Nur Übergänge, die durch **Aktivitäten** in Use-Case-Beschreibungen gedeckt sind
- Zustände ohne auslösende Aktivität stehen im Abschnitt «Nicht abgedeckte Zustände»

## Dateien
- Ein `.puml` pro Entität (z.B. `dokumentStateChart.puml`)
- Eine `.md`-Seite pro Zustandsdiagramm (z.B. `dokumentStateChart.md`)
- Dateinamen `{entität}StateChart` in camelCase

## Aufbau
```
# Zustandsdiagramm – {Entität}
## Überblick          → Ein Absatz + Links auf Entität und Use-Case-Diagramm
## Diagramm           → ![Zustandsdiagramm – {Entität}]({entität}StateChart.puml)
## Zustände           → Tabelle: Zustand | Beschreibung
## Rückverfolgung der Übergänge → Tabelle: Übergang | Auslösende Aktivität | Use Case | Schritt im Aktivitätsdiagramm
## Nicht abgedeckte Zustände → Zustände des Fachklassenmodells ohne auslösende Aktivität
```

## Inhalt
- Jede Zeile der Rückverfolgung zitiert ein `:aktion;`-Label aus einem Aktivitätsdiagramm wörtlich
- Aktivitäten, die einen Statuswechsel auslösen, folgen exakt dem Muster:
  - Erzeugen: `"CredEx-System legt {Entität} an (status = {ZUSTAND})"`
  - Ändern: `"CredEx-System setzt {Entität} (status = {ZUSTAND})"`
- Zeigt eine Aktivität den Wechsel nicht ausdrücklich, zuerst das Aktivitätsdiagramm nachführen
- Jeder genannte Use Case ist in der Tabelle verlinkt

## PlantUML
- `@startuml` / `@enduml`, `left to right direction`, `skinparam stateFontStyle bold`; kein eigenes Styling ausser der Statusfarbe
- Statusfarbe nach Bedeutung: `#F0FDF4;line:16A34A` (von der KI sicher), `#FFFBEB;line:D97706` (unsicher / wartet auf Mensch), `#EFF6FF;line:2563EB` (vom Menschen bestätigt bzw. in Bearbeitung), `#F8FAFC;line:94A3B8` (verworfen), `#F1F5F9;line:334155` (abgeschlossen)
- Titel: `title Zustandsdiagramm – {Entität}`
- `[*] -->` für den Startübergang
- Zustandsbeschreibung: `state ZUSTAND : kurze Beschreibung`
- Übergangsbeschriftungen entsprechen der auslösenden Aktivität, max. 2 Zeilen mit `\n`
