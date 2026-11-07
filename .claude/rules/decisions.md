---
paths:
  - content/decisions/**
---

# Konventionen Teamentscheide

## Dateien
- `entscheide.md` – Übersicht aller Entscheide (`type: decision-log`)
- `e{nn}{TitelInCamelCase}.md` – ein Entscheid pro Datei (`type: decision`), fortlaufend nummeriert

## Aufbau Entscheid
```
# E{nn} – {Entscheid als Aussage}
**Status:** entschieden · offen · ersetzt durch E{mm}   **Datum:** YYYY-MM-DD   **Quelle:** Teamentscheid / Feedback / Interview
## Kontext       → Warum die Frage aufkam
## Optionen      → Aufzählung der betrachteten Optionen
## Entscheid     → Ein Satz
## Begründung    → Aufzählung
## Folgen        → Welche Artefakte sich dadurch ändern, mit Links; der Change Request, der sie umgesetzt hat
```

## Inhalt
- Ein Entscheid wird nie umgeschrieben. Ändert die Gruppe ihre Meinung, folgt ein neuer Entscheid,
  und der alte bekommt den Status «ersetzt durch E{mm}»
- Offene Entscheide nennen, wer bis wann entscheidet
