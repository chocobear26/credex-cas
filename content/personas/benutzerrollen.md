---
title: "Benutzerrollenmodell – CredEx Phase 1"
linkTitle: "Benutzerrollen"
type: user-role-model
description: "Neun Rollen rund um den Dokumentenupload, mit Attributen; zwei davon im Fokus."
weight: 1
tags: [berater, partner, pruefer, kreditnehmer, ki-verbindung]
sources:
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: cr-1-3
    resource: /sources/cr_1_3.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Benutzerrollenmodell – CredEx Phase 1

## Vorgehen

15 Rollenkandidaten gesammelt, nach Organisation und Nähe zum System gruppiert, zu 9 Rollen konsolidiert und mit Attributen verfeinert (Übung Benutzerrollenmodell, 30.10.2026). Konsolidiert: Kundenberater von Bank, Versicherung und Grosskunde zu R1 (gleiche Aufgaben, gleiche Werkzeuge); Sachbearbeitung Erfassung zu R4; Kreditentscheid GLKB zu R6; CredEx Support zu R7. Datenschutz und Compliance des Partners sind Stakeholder, nutzen das System aber nicht.

---

## Rollen

| Rolle | Name | Nutzung | Fachwissen | KI / IT | Ziel | Use Cases |
|---|---|---|---|---|---|---|
| R1 | Kundenberater/in mit KI ★ | täglich, mehrere Anträge pro Woche | hoch | hoch, Copilot (M365) | Schnell und vollständig einreichen, Kontrolle über KI-Vorschläge behalten | UC-02 bis UC-07 (über die KI) |
| R2 | Hypothekarbroker/in ★ | mehrmals pro Woche | hoch | mittel, ChatGPT oder Claude, kein IT-Support | Ohne Einrichtungsaufwand starten; Fotos und Scans verarbeiten | UC-01 selbst, UC-04, UC-06, UC-07 |
| R3 | Kundenberater/in ohne KI | wie R1 | hoch | keine KI | Arbeitet wie heute; Upload ohne KI ist nicht in Phase 1 (US-12) | keine in Phase 1 |
| R4 | Assistenz / Backoffice | täglich | mittel | Office, DMS | Unterlagen sammeln und vorbereiten *(Annahme)* | UC-04 (über die KI) |
| R5 | Partner-IT (Admin) | einmalig bei Einrichtung | gering | hoch, OAuth, Berechtigungen | Sichere Anbindung, nur nötige Rechte | UC-01 |
| R6 | Prüfer/in Glarner KB | täglich | hoch | GLKB-Systeme | Vollständiges, korrekt zugeordnetes Dossier, weniger Rückfragen | erhält das Dossier (bestehende Schnittstelle) |
| R7 | CredEx Partnermanagement | monatlich | mittel | Auswertungen | Nutzung und Einsparung belegen, Partner gewinnen | UC-09 |
| R8 | Kreditnehmer/in | einmal pro Antrag | gering | sehr unterschiedlich | Kredit rasch erhalten, Daten geschützt | indirekt, liefert Unterlagen |
| R9 | Partner-KI | pro Auftrag der Beraterin | n/a | MCP-Client | Werkzeuge korrekt aufrufen, Konfidenz zurückgeben | UC-02 bis UC-06 (MCP) |

★ Fokusrolle mit Persona

---

## Fokusrollen

- **R1 → [Sandra Keller](sandraKeller.md)**, primäre Persona: der grösste Teil der Anträge, Copilot vorhanden.
- **R2 → [Reto Frei](retoFrei.md)**, sekundäre Persona: bewusst von R1 getrennt, weil er keine IT hat und eine andere KI nutzt. Darum muss die KiVerbindung ohne IT einrichtbar sein (NFA-15).
- **R3** bleibt sichtbar, damit Option D (Upload ohne KI) bewusst entschieden wird ([E11](../decisions/e11OptionDragAndDrop.md)).
- **R9** ist eine eigene Rolle: Die Partner-KI ruft die Werkzeuge auf, der Mensch entscheidet.
