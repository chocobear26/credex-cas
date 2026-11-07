---
title: "Schnittstelle – CredEx MCP-Server"
linkTitle: "MCP-Schnittstelle"
type: interface-spec
description: "Die Werkzeuge, die der MCP-Server von CredEx der Partner-KI anbietet, mit Eingaben, Rückgaben und Fehlerfällen."
weight: 1
tags: [antrag, pflichtdokument, dokument, zuordnung, dokumenttyp, berater, ki-verbindung, kreditnehmer]
sources:
  - id: offene-antraege-abrufen
    resource: /use_case/offene_antraege_abrufen/offeneAntraegeAbrufen.md
  - id: pflichtliste-abfragen
    resource: /use_case/pflichtliste_abfragen/pflichtlisteAbfragen.md
  - id: dokument-ablegen
    resource: /use_case/dokument_ablegen/dokumentAblegen.md
  - id: vollstaendigkeit-pruefen
    resource: /use_case/vollstaendigkeit_pruefen/vollstaendigkeitPruefen.md
  - id: funktionale-anforderungen
    resource: /requirements/funktionaleAnforderungen.md
  - id: system-context
    resource: /system_context/systemContext.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T08:45:00Z
---

# Schnittstelle – CredEx MCP-Server

## Überblick

MCP (Model Context Protocol) ist ein offener Standard, über den KI-Assistenten Werkzeuge externer Systeme aufrufen – ein Stecker, an den jede KI andocken kann. **Client** ist die Partner-KI (z.B. Copilot, ChatGPT, Claude), **Server** ist CredEx, die **Werkzeuge** legen fest, was die KI darf. Die Anmeldung erfolgt pro Berater über OAuth ([UC-01](../use_case/ki_verbinden/kiVerbinden.md)); jedes Werkzeug arbeitet nur auf Anträgen, auf die der angemeldete Berater zugreifen darf. Siehe [Systemkontext](../system_context/systemContext.md) und [funktionale Anforderungen](../requirements/funktionaleAnforderungen.md). Namen und Parameter sind im PoC lauffähig umgesetzt (`credex_mcp_poc.py`) und ein Vorschlag für das Zielsystem.

---

## Werkzeuge

### `credex_offene_antraege`

Realisiert [UC-02 Offene Anträge abrufen](../use_case/offene_antraege_abrufen/offeneAntraegeAbrufen.md) · FA-01

| Parameter | Typ | Pflicht | Beschreibung |
|---|---|---|---|
| – | – | – | Keine Eingaben; die Identität stammt aus der KiVerbindung |

**Rückgabe:** `Liste<Antrag>` mit `antrag_id` (antragsnummer), Kreditnehmer, Objekt, Antragsschritt und Anzahl Pflichtdokumente mit Status `FEHLT`.

**Fehlerfälle:** nicht angemeldet.

### `credex_pflichtliste`

Realisiert [UC-03 Pflichtliste abfragen](../use_case/pflichtliste_abfragen/pflichtlisteAbfragen.md) · FA-02

| Parameter | Typ | Pflicht | Beschreibung |
|---|---|---|---|
| `antrag_id` | String | ja | antragsnummer des Antrags |

**Rückgabe:** `Liste<Pflichtdokument>` mit `pflichtdok_id`, Dokumenttyp (`bezeichnung`), `bezug` und `status`; dazu das Ziel «weiteres Dokument».

**Fehlerfälle:** Antrag unbekannt oder keine Berechtigung.

### `credex_dokument_ablegen`

Realisiert [UC-04 Dokument ablegen](../use_case/dokument_ablegen/dokumentAblegen.md) · FA-03, FA-04

| Parameter | Typ | Pflicht | Beschreibung |
|---|---|---|---|
| `antrag_id` | String | ja | antragsnummer des Antrags |
| `datei` | Datei | ja | Die abzulegende Datei |
| `pflichtdok_id` | String | ja | Ziel der Zuordnung oder `weiteres` |
| `konfidenz` | Decimal | ja | Sicherheit der Partner-KI zwischen 0 und 1 |
| `seiten` | String | nein | Seitenbereich bei Sammel-PDF, z.B. `1-3` |
| `begruendung` | String | nein | Kurze Begründung der Partner-KI für die Zuordnung, sichtbar in der Übersicht |

**Rückgabe:** `dokument_id`, Dokument-`status` (`VON_KI_ZUGEORDNET`, `UNSICHER`) und die geltende Schwelle.

**Fehlerfälle:** keine Berechtigung; Antrag eingereicht; unbekanntes Pflichtdokument; ungültiger Seitenbereich; Format oder Grösse unzulässig. In jedem Fall keine Teilablage (NFA-09).

### `credex_vollstaendigkeit_pruefen`

Realisiert [UC-05 Vollständigkeit prüfen](../use_case/vollstaendigkeit_pruefen/vollstaendigkeitPruefen.md) · FA-02, FA-05

| Parameter | Typ | Pflicht | Beschreibung |
|---|---|---|---|
| `antrag_id` | String | ja | antragsnummer des Antrags |

**Rückgabe:** Zusammenfassung, Liste der Pflichtdokumente mit `status = FEHLT`, Liste mit `status = UNSICHER`, Link zur Übersicht.

**Fehlerfälle:** Antrag unbekannt.

---

## Bewusst nicht angeboten

- **Kein Werkzeug zum Einreichen** (FA-08): Die KI legt ab, nur der Berater reicht in der Übersicht ein (GA3, Teamentscheid 23.10.2026).
- **Kein Anfordern fehlender Unterlagen beim Kreditnehmer**: Der Berater fragt selbst nach (Teamentscheid 30.10.2026).

---

## Offene Punkte

- **Zusätzliche Werkzeuge im PoC.** Der PoC bietet vier weitere Werkzeuge an: `credex_abgelegte_dokumente`, `credex_zuordnung_bestaetigen`, `credex_zuordnung_aendern`, `credex_dokument_verwerfen`. Damit kann der Berater Entscheide aus UC-06 per Auftrag an die KI ausführen (Pflichtfeld `auftrag_beraterin`, protokolliert als «Beraterin (via KI)»). Das reibt sich mit GA3 und der Regel, dass eine unsichere Zuordnung erst nach dem Ansehen bestätigt wird. Teamentscheid offen, ob diese Werkzeuge ins Zielsystem gehören.
- **Simulation der Partnerseite.** Die PoC-Werkzeuge `dms_dateien_auflisten` und `dms_datei_lesen` simulieren das Partner-DMS und gehören nicht zur Schnittstelle von CredEx.
- **Übertragung grosser Dateien:** direkt in der MCP-Nachricht oder über eine separate Upload-Adresse – mit CredEx klären, ebenso zulässige Formate und maximale Grösse (Vorschlag 32 MB, NFA-02, NFA-03).
- **Anbindung an ChatGPT und Microsoft 365 Copilot** braucht eine öffentlich erreichbare Adresse mit Anmeldung; im PoC offen.
