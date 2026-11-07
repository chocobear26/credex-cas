---
paths:
  - content/requirements/**
---

# Konventionen Anforderungskataloge

## Dateien
- `geschaeftsanforderungen.md` – GA1 … GA6
- `funktionaleAnforderungen.md` – FA-01 … FA-nn
- `nichtfunktionaleAnforderungen.md` – NFA-01 … NFA-nn, gegliedert nach ISO/IEC 25010

## Aufbau
```
# {Katalogname} – {Systemname}
## Überblick          → Ein Absatz: Zweck, Quelle (Anforderungs-Excel der Gruppe, Stand), Links auf verwandte Kataloge
## Anforderungen      → Tabelle (siehe unten)
## Offene Punkte      → Zielwerte oder Fragen, die noch zu validieren sind
```

## Tabellen
- Geschäftsanforderungen: `ID | Geschäftsanforderung | Messgrösse / Ziel | Quelle`
- Funktional: `ID | Funktion | Anforderung | Abnahmekriterium | Bezug | Wichtigkeit`
- Nicht-funktional: `ID | Merkmal (ISO 25010) | Anforderung | Abnahmekriterium | Wichtigkeit`
- Wichtigkeit Hoch = Must, Mittel = Should, Tief = Could

## Inhalt
- Anforderungen nach Satzschablone: «Das System muss / darf nicht …»
- Jede Anforderung hat ein **prüfbares Abnahmekriterium** («Abnahme erfolgt, wenn …»)
- **Bezug** verlinkt die User Stories und Use Cases, aus denen die FA abgeleitet ist
- Die IDs sind dieselben wie im Anforderungs-Excel der Gruppe; Excel und Katalog werden synchron gehalten
- Zielwerte, die noch nicht validiert sind, tragen den Vermerk *(Vorschlag)*
