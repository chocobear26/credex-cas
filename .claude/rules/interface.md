---
paths:
  - content/interface/**
---

# Konventionen Schnittstellen

## Dateien
- `{schnittstelle}.md` – eine Seite pro Schnittstelle (z.B. `mcpSchnittstelle.md`)

## Aufbau
```
# Schnittstelle – {Name}
## Überblick          → Zweck, Protokoll, wer Client und wer Server ist; Links auf Systemkontext und Use Cases
## Werkzeuge          → Ein H3 pro Werkzeug mit Tabelle: Parameter | Typ | Pflicht | Beschreibung,
                        danach Rückgabe und Fehlerfälle als Aufzählung, dazu der Use Case und die FA
## Bewusst nicht angeboten → was die Schnittstelle absichtlich nicht kann, mit Begründung
## Offene Punkte      → noch zu klärende technische Fragen
```

## Inhalt
- Werkzeugnamen in `snake_case` mit Präfix des Systems (`credex_dokument_ablegen`), exakt wie im PoC
- Parameter- und Rückgabenamen entsprechen den Attributen im Fachklassenmodell
- Typen: `String`, `Integer`, `Decimal`, `Boolean`, `Datei`, `Liste<…>`
- Jedes Werkzeug verweist auf genau einen Use Case
