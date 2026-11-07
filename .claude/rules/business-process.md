---
paths:
  - content/business_process/**
---

# Konventionen Soll-Prozess

## Dateien
- `businessProcess.md` – Überblick, eingebettete Diagramme und «Änderungen gegenüber heute»
- `sollProzessTeil1.bpmn`, `sollProzessTeil2.bpmn` – BPMN 2.0 mit Diagram Interchange (DI), je ein Pool

## Aufbau `businessProcess.md`
```
# Soll-Prozess – {Prozessname}
## Überblick          → Ein Absatz + Links auf Fachklassenmodell und Systemkontext
## Prozessdiagramm    → Ein H3 pro Teil mit ![Soll-Prozess Teil N – …](sollProzessTeilN.bpmn)
## Änderungen gegenüber heute → kurze Liste, was wegfällt und was neu ist
```

## BPMN-Regeln
- **BPMN 2.0, bearbeitbar in bpmn.io** (Camunda Modeler geht auch). Der Build rendert die Datei über
  Kroki mit bpmn-js; nie ein exportiertes Bild einchecken.
- **Ein Pool pro Teil, eine Lane pro Akteur.** Lane-Namen exakt wie die Akteure: «Partner-IT»,
  «Berater/in», «Partner-KI», «CredEx-System», «Glarner KB», «Partnermanagement».
- **Zwei Teile**, damit das Diagramm auf einer Seite lesbar bleibt: Teil 1 Ablage (0.x – 2.x),
  Teil 2 Prüfen und Einreichen (3.x – 6.x). Verbunden mit einem Link-Zwischenereignis
  («weiter mit Teil 2» / «von Teil 1»).
- **Schrittnummer vorne im Namen:** `{phase}.{schritt} Tätigkeit` (z.B. «2.4 Dokument speichern, …»).
  Alternativpfade `4.1a`. Die Nummern sind Join-Schlüssel für Use Cases und Story Map.
- **Gateways:** exklusive Gateways mit Frage als Name («2.3 Berechtigung, Format, Grösse gültig?»),
  ausgehende Flüsse mit «Ja» / «Nein». Schleifen laufen über ein Merge-Gateway ohne Namen.
- **Ereignisse:** Start mit Auslöser («Antrag in Schritt 5»), Timer-Start für Periodisches
  («Monatsende»), Ende mit Ergebnis («Dossier geprüft»).
- **Layout:** Fluss von links nach rechts; Aufgaben 130 × 80, Gateways 50 × 50; rechtwinklige
  Kanten; keine Kante durch ein anderes Element. Gateway-Beschriftung oberhalb.
- Klassennamen des Fachklassenmodells in den Beschriftungen verwenden.
