---
paths:
  - content/architecture/**
---

# Konventionen Architektursichten

## Dateien
- `komponenten.md` + `komponenten.puml` – UML-Komponentendiagramm
- `mcpAblauf.md` + `mcpAblauf.puml` – UML-Sequenzdiagramm eines vollständigen Durchlaufs

## Aufbau
```
# Architektur – {Sicht}
## Überblick        → Ein Absatz, Links auf Systemkontext und MCP-Schnittstelle
## Diagramm         → ![…]({sicht}.puml)
## Elemente         → nur was das Diagramm nicht selbst sagt (Verantwortung, Technologie)
```

## PlantUML
- Komponenten: Neues mit Stereotyp `<<neu>>`, Bestehendes ohne; Schnittstellen als `()`
- Sequenz: Teilnehmer in der Reihenfolge Berater/in, Partner-KI, MCP-Server, Plattform, Protokoll,
  Glarner KB; Werkzeugaufrufe mit ihrem exakten Namen; `alt` und `loop` für Verzweigungen
- Kein eigenes Styling (gemeinsames Stilblatt)
