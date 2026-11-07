---
title: "Use Case – UC-06 Zuordnung bestätigen oder ändern"
linkTitle: "UC-06 Zuordnung bestätigen oder ändern"
type: use-case
description: "Der Berater prüft eine Zuordnung in der Übersicht und bestätigt, ändert oder verwirft sie."
weight: 8
tags: [zuordnung, dokument, pflichtdokument, protokolleintrag, berater, antrag]
sources:
  - id: use-case-diagram
    resource: /use_case/useCaseDiagram.md
  - id: business-process
    resource: /business_process/businessProcess.md
  - id: domain-model
    resource: /domain_model/domainModel.md
  - id: cr-1-0
    resource: /sources/cr_1_0.md
  - id: cr-1-1
    resource: /sources/cr_1_1.md
  - id: cr-1-2
    resource: /sources/cr_1_2.md
generated:
  by: jarvis/1.0
  at: 2026-11-07T10:13:58Z
---

# Use Case – UC-06 Zuordnung bestätigen oder ändern

> [!NOTE] v1.2 – Geändert 2026-11-07
> Neuer Weg: Der Berater kann per ausdrücklichem Auftrag an seine KI bestätigen, umordnen oder verwerfen (Alternativszenario 3c).

> [!NOTE] v1.1 – Geändert 2026-11-07
> Aktivitätsdiagramm vereinfacht: ein Entscheid des Beraters, danach ein Block im CredEx-System. Inhalt und Aktivitätslabels unverändert.

## Überblick

Der Berater prüft eine Zuordnung in der Übersicht und bestätigt, ändert oder verwirft sie. Entspricht **Prozessschritten 3.1 – 3.4**.[^business-process] Siehe auch [Use-Case-Diagramm](../useCaseDiagram.md) und [Soll-Prozess](../../business_process/businessProcess.md). Priorität Must (in der Übersicht) und Should (per Auftrag an die KI), Wichtigkeit hoch, technologisches Risiko gering. Akteure: Berater/in, Partner-KI im Auftrag. Im Detail spezifiziert.

---

## Vorbedingungen

- Mindestens ein Dokument wurde abgelegt (UC-04)
- Der Antrag hat `status = IN_ERFASSUNG`

## Nachbedingungen

**Erfolg:**
- Kein Dokument des Pflichtdokuments hat mehr `status = UNSICHER`
- Bestätigte oder umgeordnete Zuordnung mit `quelle = MENSCH`, Dokument mit `status = BESTAETIGT`
- Verworfenes Dokument mit `status = VERWORFEN`; das Pflichtdokument gilt wieder als `FEHLT`
- Je Aktion ein Protokolleintrag mit `akteur = BERATER`, bei einem Auftrag an die KI mit `akteur = BERATER_VIA_KI` und dem Auftrag im Wortlaut

---

## Beschreibung

Der Berater öffnet die Übersicht des Antrags. Unsichere Zuordnungen sind hervorgehoben, mit Dateiname und Konfidenz. Er sieht sich das Dokument an und bestätigt die Zuordnung; wählt er ein anderes Pflichtdokument, ordnet CredEx um und bestätigt zugleich (3a); verwirft er das Dokument, gilt das Pflichtdokument wieder als fehlend (3b). Auch eine sichere Zuordnung der KI kann er umordnen. In der Übersicht lässt sich eine unsichere Zuordnung erst nach dem Ansehen bestätigen. Alternativ gibt der Berater seiner KI einen ausdrücklichen Auftrag, z.B. «Bestätige Dokument 17 als Betreibungsauskunft Petra» (3c); die Partner-KI ruft dann `credex_zuordnung_bestaetigen`, `credex_zuordnung_aendern` oder `credex_dokument_verwerfen` mit dem Auftrag im Pflichtfeld `auftrag_beraterin` auf. Ohne Auftrag lehnt CredEx ab. So bleibt der Entscheid beim Menschen, ohne dass er das KI-Fenster verlassen muss. Das ist die Antwort auf den Medienbruch aus dem Feedback zu Modul 1 (Teamentscheid 07.11.2026).

---

## Qualitätsanforderungen

- [NFA-06 Erlernbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)
- [NFA-07 Zugänglichkeit](../../requirements/nichtfunktionaleAnforderungen.md)
- [FA-11 Prüfen per Auftrag an die KI](../../requirements/funktionaleAnforderungen.md)
- [NFA-12 Nachweisbarkeit](../../requirements/nichtfunktionaleAnforderungen.md)

---

## Aktivitätsdiagramm

![Aktivitätsdiagramm – UC-06 Zuordnung bestätigen oder ändern](zuordnungBestaetigen.puml)

[^business-process]: [Soll-Prozess](../../business_process/businessProcess.md)
