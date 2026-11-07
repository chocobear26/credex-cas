---
paths:
  - content/system_context/**
---

# Konventionen Systemkontext

## Dateien
- `systemContext.md` – Überblick, eingebettetes Diagramm, Tabelle der Informationsflüsse, Abgrenzung
- `systemContext.d2` – das Diagramm in [D2](https://d2lang.com), beim Build über Kroki gerendert

## Aufbau `systemContext.md`
```
# Systemkontext – {Systemname}
## Überblick          → Ein Absatz: was im Scope liegt, was Kontext ist; Links auf Soll-Prozess und Fachklassenmodell
## Diagramm           → Legende + ![Systemkontext – {Systemname}](systemContext.d2)
## Informationsflüsse → Tabelle: Von | Nach | Information
## Abgrenzung         → Liste, was ausdrücklich nicht im Scope liegt
```

## D2-Regeln
- Layout-Engine **ELK** (`vars: d2-config: layout-engine: elk`), Hauptrichtung `right`, in den
  Gruppen `down`.
- **Drei Gruppen** wie im Original der Gruppe: «Distributionspartner (Kontext)», «Scope Phase 1
  (neu)», «CredEx und Dritte (Kontext)».
- Klassen `scope` (rot umrandet) für Neues, `kontext` (gestrichelt) für Bestehendes, `gruppe` für die
  drei Rahmen, `fluss` für Kanten. Farben nur über diese Klassen.
- Kanten sind **gerichtet** und mit der fliessenden Information beschriftet. Fliesst zwischen zwei
  Systemen in beide Richtungen etwas, ein Doppelpfeil `<->` mit «hin / zurück».
- Die Tabelle *Informationsflüsse* führt jede Richtung einzeln – sie ist die vollständige Liste; das
  Diagramm darf Beschriftungen weglassen, wenn sie sich sonst überlagern.
- Datenobjekte heissen wie im Fachklassenmodell (`Dokument`, `Zuordnung`, `Pflichtdokument`).
