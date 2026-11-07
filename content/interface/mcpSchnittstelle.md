---
title: "Schnittstelle – CredEx MCP-Server"
linkTitle: "MCP-Schnittstelle"
type: interface-spec
description: "Die acht Werkzeuge, die der MCP-Server von CredEx der Partner-KI anbietet, mit Eingaben, Rückgaben und Fehlerfällen."
weight: 1
tags: [team, antrag, pflichtdokument, dokument, zuordnung, dokumenttyp, berater, ki-verbindung, kreditnehmer]
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
  - id: zuordnung-bestaetigen
    resource: /use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Schnittstelle – CredEx MCP-Server

> [!NOTE] v1.2 – Geändert 2026-11-07
> Vier Werkzeuge zum Prüfen im Auftrag des Beraters aufgenommen (Teamentscheid 07.11.2026); total acht Werkzeuge.

## Überblick

MCP (Model Context Protocol) ist ein offener Standard, über den KI-Assistenten Werkzeuge externer Systeme aufrufen – ein Stecker, an den jede KI andocken kann. **Client** ist die Partner-KI (z.B. Copilot, ChatGPT, Claude), **Server** ist CredEx, die **Werkzeuge** legen fest, was die KI darf. Die Anmeldung erfolgt pro Berater über OAuth ([UC-01](../use_case/ki_verbinden/kiVerbinden.md)); jedes Werkzeug arbeitet nur auf den Anträgen des Teams des angemeldeten Beraters. Der Ablauf eines Aufrufs steht im [Sequenzdiagramm](../architecture/mcpAblauf.md). Siehe [Systemkontext](../system_context/systemContext.md) und [funktionale Anforderungen](../requirements/funktionaleAnforderungen.md). Namen und Parameter sind im PoC lauffähig umgesetzt (`credex_mcp_poc.py`) und ein Vorschlag für das Zielsystem.

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


### Prüfen im Auftrag des Beraters

Diese vier Werkzeuge dürfen nur auf ausdrücklichen Auftrag des Beraters aufgerufen werden (Teamentscheid 07.11.2026). Jeder Aufruf schreibt einen Protokolleintrag mit `akteur = BERATER_VIA_KI` und dem Auftrag im Wortlaut. Die KI darf dafür nie den Browser steuern.

### `credex_abgelegte_dokumente`

Realisiert [UC-06 Zuordnung bestätigen oder ändern](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) · FA-11

| Parameter | Typ | Pflicht | Beschreibung |
|---|---|---|---|
| `antrag_id` | String | ja | antragsnummer des Antrags |

**Rückgabe:** `Liste<Dokument>` mit `dokument_id`, `dateiname`, Zuordnung (Pflichtdokument), `status` und `konfidenz`; dient dazu, die `dokument_id` für die folgenden Werkzeuge zu finden.

**Fehlerfälle:** Antrag unbekannt oder keine Berechtigung.

### `credex_zuordnung_bestaetigen`

Realisiert [UC-06 Zuordnung bestätigen oder ändern](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) · FA-06, FA-11

| Parameter | Typ | Pflicht | Beschreibung |
|---|---|---|---|
| `antrag_id` | String | ja | antragsnummer des Antrags |
| `dokument_id` | String | ja | aus `credex_abgelegte_dokumente`, z.B. `DOK-007` |
| `auftrag_beraterin` | String | ja | Der Auftrag des Beraters, möglichst wörtlich; mindestens 5 Zeichen; wird protokolliert |

**Rückgabe:** Dokument mit `status = BESTAETIGT`, Zuordnung mit `quelle = MENSCH`; Hinweis, dass einreichen nur in der Übersicht geht.

**Fehlerfälle:** kein oder zu kurzer Auftrag; Dokument unbekannt; Antrag eingereicht; keine Berechtigung.

### `credex_zuordnung_aendern`

Realisiert [UC-06 Zuordnung bestätigen oder ändern](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) · FA-06, FA-11

| Parameter | Typ | Pflicht | Beschreibung |
|---|---|---|---|
| `antrag_id` | String | ja | antragsnummer des Antrags |
| `dokument_id` | String | ja | aus `credex_abgelegte_dokumente` |
| `neues_pflichtdok_id` | String | ja | Ziel aus `credex_pflichtliste` oder `weiteres` |
| `auftrag_beraterin` | String | ja | Der Auftrag des Beraters, möglichst wörtlich; mindestens 5 Zeichen; wird protokolliert |

**Rückgabe:** Dokument umgeordnet mit `status = BESTAETIGT`, Zuordnung mit `quelle = MENSCH`.

**Fehlerfälle:** kein oder zu kurzer Auftrag; unbekanntes Pflichtdokument; Antrag eingereicht; keine Berechtigung.

### `credex_dokument_verwerfen`

Realisiert [UC-06 Zuordnung bestätigen oder ändern](../use_case/zuordnung_bestaetigen/zuordnungBestaetigen.md) · FA-06, FA-11

| Parameter | Typ | Pflicht | Beschreibung |
|---|---|---|---|
| `antrag_id` | String | ja | antragsnummer des Antrags |
| `dokument_id` | String | ja | aus `credex_abgelegte_dokumente` |
| `auftrag_beraterin` | String | ja | Der Auftrag des Beraters, möglichst wörtlich; mindestens 5 Zeichen; wird protokolliert |

**Rückgabe:** Dokument mit `status = VERWORFEN`; das Pflichtdokument gilt wieder als `FEHLT`.

**Fehlerfälle:** kein oder zu kurzer Auftrag; Dokument unbekannt; Antrag eingereicht; keine Berechtigung.

---

## Bewusst nicht angeboten

- **Kein Werkzeug zum Einreichen** (FA-08): Die KI legt ab und darf im Auftrag prüfen, aber nur der Berater reicht ein, und nur in der Übersicht (GA3, Teamentscheid 23.10.2026).
- **Kein Anfordern fehlender Unterlagen beim Kreditnehmer**: Der Berater fragt selbst nach (Teamentscheid 30.10.2026).

---

## Offene Punkte

- **Simulation der Partnerseite.** Die PoC-Werkzeuge `dms_dateien_auflisten` und `dms_datei_lesen` simulieren das Partner-DMS und gehören nicht zur Schnittstelle von CredEx.
- **Übertragung grosser Dateien:** direkt in der MCP-Nachricht oder über eine separate Upload-Adresse – mit CredEx klären, ebenso zulässige Formate und maximale Grösse (Vorschlag 32 MB, NFA-02, NFA-03).
- **Anbindung an ChatGPT und Microsoft 365 Copilot** braucht eine öffentlich erreichbare Adresse mit Anmeldung; im PoC offen.
