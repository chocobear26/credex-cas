# Produktdokumentation CredEx Phase 1 (OKF)

Die Anforderungsdokumentation von **CredEx Phase 1 – Dokumentenupload über die eigene KI des Partners**,
geführt als Bundle im [Open Knowledge Format](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
(OKF). Gruppe 6 (Marco, Jessica, Cem), Leistungsnachweis Modul 2, CAS Business Analysis and Methods, ZHAW.

Jedes Artefakt – Fachklassenmodell, Soll-Prozess, Systemkontext, Use Cases, Zustandsdiagramme, User
Stories, Anforderungskataloge, MCP-Schnittstelle – sagt, welchen Typ es hat, woraus es abgeleitet ist,
wer es geschrieben hat und ob ein Mensch aus der Gruppe es freigegeben hat. Jede Änderung ist ein Change
Request, jede Version ein Eintrag im Change Log.

**Jarvis**, ein KI-Agent in Claude Code oder GitHub Copilot, hilft bei der Anforderungsanalyse: Er
ermittelt, was eine Änderung betrifft, fragt nach, führt die Artefakte in der richtigen Reihenfolge nach
und entwirft die User Stories. Die Gruppe entscheidet und gibt frei.

Grundlage ist das Lehrbeispiel [okf-productdocumentation](https://github.com/marcelRonner/okf-productdocumentation)
von Marcel Ronner (ATM-System). Alle ATM-Inhalte sind entfernt; Mechanik, Skripte und Prüfregister sind
übernommen. Marcel Ronner hat die Nutzung für diese Gruppenarbeit am 07.11.2026 ausdrücklich freigegeben.

## Wo anfangen

| Du willst … | Lies |
|---|---|
| den Fall und die Artefakte sehen | [`content/_index.md`](content/_index.md) |
| wissen, was noch offen oder angenommen ist | [`content/sources/cr_1_0.md`](content/sources/cr_1_0.md) |
| wissen, was der Agent darf und muss | [`AGENTS.md`](AGENTS.md), [`.claude/rules/`](.claude/rules/), [`.claude/skills/`](.claude/skills/) |
| die veröffentlichte Seite sehen | <https://chocobear26.github.io/credex-cas/site/> |
| das Repository bauen oder ändern | diese Datei |

## Was drin ist

```
content/                  die Dokumentation – das OKF-Bundle und das Hugo-Content-Verzeichnis
  _index.md               Startseite: Fall, Artefaktliste, Ableitungskette
  domain_model/           domainModel.md + .puml, und entities/ – eine Seite pro Fachklasse
  business_process/       businessProcess.md und der Soll-Prozess als BPMN in zwei Teilen (.bpmn)
  system_context/         systemContext.md und das Kontextdiagramm in D2 (.d2)
  use_case/               useCaseDiagram, actorDescriptions, actors/, ein Ordner pro Use Case (.md + .puml)
  state_chart/            Dokument und Antrag (.md + .puml)
  epics/                  Story Map und user_stories/ – eine Datei pro Story
  requirements/           Geschäftsanforderungen, funktionale und nicht-funktionale Anforderungen
  interface/              MCP-Schnittstelle
  change_log/             changeLog.md – jede Version, jedes berührte Artefakt
  sources/                Change Requests und OKF-Assessments
  log.md                  ERZEUGT – das OKF-Log aus Change Log und Assessments
AGENTS.md                 der Vertrag für Jarvis: Identität, Muss-Regeln, Frontmatter, Checkliste
CLAUDE.md                 eine Zeile, importiert AGENTS.md für Claude Code
.claude/rules/            die Konventionen je Artefakttyp, nur für ihren Ordner geladen
.claude/skills/           change-request und okf-check (mit dem Register der 41 Prüfungen)
.github/                  ERZEUGT – die Regeln im Copilot-Dialekt; Deploy-Workflow
schema.yml                die Artefakttypen und welche Metadaten jeder tragen muss
index.html                Landing Page; die eingebetteten Anweisungen werden ERZEUGT
hugo.yaml, layouts/, assets/   Site-Build mit Docsy und Kroki
scripts/                  Lint, Generator, verify, Tests
Makefile                  alle Befehle unten
```

Gegenüber dem ATM-Beispiel neu sind die Artefakttypen `system-context`, `requirement-catalog` und
`interface-spec` (je mit Regeln in `.claude/rules/` und Eintrag in `schema.yml`). Die Dokumentation ist
auf Deutsch.

Die folgenden Abschnitte stammen aus dem Original und gelten unverändert.

## Setting it up

| Tool | Version | Why |
|---|---|---|
| [Hugo](https://gohugo.io/installation/) **extended** | 0.166.0 (CI), at least 0.160.1 | builds the site |
| [Go](https://go.dev/dl/) | as in `go.mod` (1.27) | Hugo fetches the Docsy theme as a Hugo module |
| [Node.js](https://nodejs.org/) | current LTS | Dart Sass and PostCSS compile Docsy's stylesheets |
| Python | 3.13 | the checks, the generator and the tests (PyYAML) |
| network access to [kroki.io](https://kroki.io) | — | PlantUML diagrams render at build time |

```sh
git clone https://github.com/chocobear26/credex-cas.git && cd credex-cas
npm install                       # Dart Sass, PostCSS, Bootstrap, Font Awesome
pip install -r requirements.txt   # PyYAML — a virtualenv is fine
make build                        # the same checks and build CI runs
make serve                        # http://localhost:1313/credex-cas/site/
```

## Commands

| Command | What it does |
|---|---|
| `make serve` | Live-reload site at <http://localhost:1313/credex-cas/site/>. Offline, a diagram shows as a link to its `.puml` source |
| `make generate` | Regenerate everything that restates something written elsewhere: `.github/instructions/`, `.github/prompts/`, the type table in `AGENTS.md`, the instructions embedded in `index.html`, and `content/log.md` |
| `make lint` | `make generate`, then check the documentation (codes below). `STRICT=1` makes warnings fail |
| `make test` | The OKF consumer acceptance tests — against the Python reader and a real Hugo build — and the script tests |
| `make build` | What CI runs: fail on a stale generated file, a lint error or a failing test, then `hugo --minify --panicOnWarning` into `site/` — which fails on a broken link or a diagram that did not render |
| `make stage` | `make build`, then assemble `deploy/` exactly as the server receives it |
| `make verify PAGES="content/a.md content/b.md" [WHO=owner]` | Record **your** approval of artifacts as an OKF `verified` event. Run by a person, never by the agent |
| `make clean` | Remove `site/` and `deploy/` |

## How a change is made

1. Ask Jarvis, the requirements-analysis agent, for the change — in Copilot or Claude Code, typed as
   `/change-request` or not.
2. Jarvis follows [`.claude/skills/change-request/SKILL.md`](.claude/skills/change-request/SKILL.md):
   analyse, clarify, impact summary, then write the change request to
   `content/sources/cr_{major}_{minor}.md`.
3. Jarvis updates the artifacts from the domain model outward, drafts user stories for any
   functional change, adds a version to the change log, stamps `generated` and `sources` on every
   artifact it touched, and runs `make generate` and `make build`.
4. You review and approve, and record the approval with `make verify PAGES="…"`.
5. Merge to `main`; CI builds and deploys.

## The documentation model

**Artifact types.** Every Markdown file in `content/` has one `type`, declared in
[`schema.yml`](schema.yml) with where it lives, which rules file governs it, and which metadata it
must carry. The table in `AGENTS.md` is generated from it. Adding a type means declaring it there,
writing `.claude/rules/<type>.md` with a `paths:` glob, adding a row to the routing table in
`AGENTS.md`, and running `make generate`.

**Frontmatter.** Every file carries `title`, `type` and `description`; artifacts also carry
`linkTitle` (the sidebar label), `weight` (the sidebar position), `tags` (the domain entities it
names, plus release and KANO class on a user story), `sources` (what it derives from, as
bundle-absolute paths with kebab-case ids) and `generated` (`jarvis/1.0`, and when). `verified` is
added only by `make verify`. The full contract is in [`AGENTS.md`](AGENTS.md).

**Derivation.** The artifacts form a chain — domain model → business process → use cases → state
charts and story map → user stories → change log — recorded in each artifact's `sources:` and
explained, with its join keys and review rules, on the [documentation home](content/_index.md).
Traceability references in the text ("Corresponds to **Business Process steps 4a.1 – 4a.7**") cite
their source with a footnote keyed to the source id.

**Versions.** `content/change_log/changeLog.md` is the only place a version is written:
`## v{X.Y} – {Title} ({YYYY-MM-DD})`, a summary sentence, and a row per artifact touched.
`make generate` restates it as `content/log.md` in OKF §9 form. Inline change markers use blockquote
alerts (`> [!NOTE] v1.4 – Added …`) and block attributes (`{.v-new}`), styled in
`assets/scss/_styles_project.scss`.

## The instructions

Jarvis runs on the same files in Claude Code and GitHub Copilot:

- **`AGENTS.md`** is read on every request — Copilot reads it natively, Claude Code through the
  one-line `CLAUDE.md`.
- **`.claude/rules/<type>.md`** holds the conventions for one artifact type, with a `paths:` glob so
  it loads only when that folder is touched. A rule attaches only after a file in its folder has been
  read, so `AGENTS.md` carries a routing table telling the agent which rules to open before a first
  write. Copilot reads project rules only from `.github/instructions/`, so `make generate` restates
  each one there, as `applyTo:`.
- **`.claude/skills/`** holds the operations: `change-request`, the protocol for changing the
  documentation, and `okf-check`, which assesses the bundle against the check register in
  `okf-v0-2-checks.md` and files the result in `content/sources/`. Both tools discover skills there; the generated `.github/prompts/*.prompt.md`
  files exist only so `/change-request` and `/okf-check` can be typed in Copilot.
- **`index.html`** shows the same instruction files to students, regenerated into the page on every
  `make generate`.

Edit the source files, never the generated ones — `make build` fails if they have drifted.

## Open Knowledge Format

`content/` is an OKF v0.2 bundle, so any agent that reads OKF can consume the documentation straight
from the repository. `/okf-check` assesses it against the 41 numbered checks of the register and
files each run as `content/sources/okf_assessment_<yyyy>_<mm>_<dd>.md`: the verdict and the counts
first, then the three mandatory checks, then one table per check family, every row showing the
check's name next to its ID. Runs are never rewritten, so two can be compared check by check; each
appears in `content/log.md` under its day, and a change request fixing a finding cites the run. The
conformance and quality rules are enforced by `make lint`:

| Code | Fails on |
|---|---|
| E1 | missing or unparseable frontmatter (OKF criterion 1) |
| E2 | empty `type`, or one not declared in `schema.yml` (OKF criterion 2) |
| E3 | any `index.md` (reserved, and a Hugo leaf bundle), or a `log.md` breaking OKF §9 (criterion 3) |
| E4 | missing `title` or `description`, or a multi-line description |
| E5 | a relative link or image pointing at nothing |
| E6 | malformed `sources`: no `resource` or `id`, duplicate ids, a missing resource, a footnote naming no source |
| E7 | malformed `generated` or `verified`: wrong actor form, datetime without a UTC offset |
| E8 | `tags` that are not lowercase-kebab strings |
| W1 | a page whose first `# Heading` differs from its `title` |
| W2 | a `.puml` diagram nothing embeds or links |
| W3 | an artifact missing metadata its type requires in `schema.yml` |

`scripts/test_okf_consumer.py` proves the consumer side: the Python reader in `scripts/okflib.py` and
a real Hugo build both accept an unknown type, an unknown key, a broken link, a concept with only a
type, and a bundle without `index.md`.

## How the site is built

Hugo renders `content/` with [Docsy](https://www.docsy.dev/) 0.17, pulled in as a Hugo module, into
`site/`. `baseURL` is `<eigene Adresse>/site/`, because Hugo writes root-relative URLs.
There is no navigation list: the sidebar is the folder tree, ordered by `weight`, labelled by
`linkTitle`, with each folder's title and description in its `_index.md`.

The overrides in `layouts/`, each documented in place:

| File | Why |
|---|---|
| `_markup/render-link.html` | Resolves relative `.md` links, links to folders, and links to other files such as `.puml` sources, to their published URLs; warns on anything that resolves to nothing |
| `_markup/render-image.html` | Renders `![…](diagram.puml)` through Kroki at build time and publishes the SVG |
| `_partials/sidebar-args.html` | Roots the sidebar at the home page, so every artifact folder is reachable from every page |
| `_td-content.html`, `list.html` | Stop the page's own `# Heading` rendering twice under Docsy's title |

`hugo.yaml` also remounts Docsy's `layouts/docs` at the layout root: every page has an OKF `type`,
which Hugo would otherwise use to look for layouts and fall through to a page without the sidebar.
Re-check the mounts against Docsy's own `hugo.yaml` after `hugo mod get -u`.

## Diagrams

Jedes Diagramm liegt als Quelltext neben seiner Seite und wird über ein Bild eingebunden:

| Diagramm | Format | Werkzeug |
|---|---|---|
| Klassen, Use Cases, Aktivitäten, Zustände | `.puml` | [PlantUML](https://plantuml.com), mit dem gemeinsamen Stilblatt `assets/diagrams/style.puml` |
| Soll-Prozess | `.bpmn` | BPMN 2.0, gezeichnet von [bpmn-js](https://bpmn.io); in bpmn.io oder Camunda Modeler bearbeitbar |
| Systemkontext | `.d2` | [D2](https://d2lang.com) mit ELK-Layout |
| Übersicht auf der Startseite | Mermaid im Markdown | Docsy im Browser |

```markdown
![Aktivitätsdiagramm – UC-04 Dokument ablegen](dokumentAblegen.puml)
```

Im Site-Build öffnet ein Klick auf ein Diagramm das SVG in voller Grösse.

There is no PlantUML installation and no generated SVG in the repository. During the build,
`render-image.html` posts each `.puml`, `.bpmn` and `.d2` file to Kroki (PlantUML with the shared style inserted after `@startuml`) and publishes the SVG it returns — a diagram
cannot drift from its source, and a syntax error fails the build. Hugo caches each response
by its source. To keep diagram source off the public service, run Kroki yourself
(`docker run -p 8000:8000 yuzutech/kroki`) and set `HUGO_PARAMS_KROKI_URL=http://localhost:8000`.
On GitHub, a page shows a broken image where its diagram would be; the site renders it.

## Deploy

[`.github/workflows/deploy-docs.yml`](.github/workflows/deploy-docs.yml) runs on every push to
`main`, and on demand from the Actions tab:

1. set up Go, Node LTS (with `npm ci`), Python 3.13 (with `requirements.txt`) and Hugo extended 0.166.0;
2. `make stage` — generated files current, lint, tests, Hugo build, then `deploy/`;
3. upload `deploy/` to **GitHub Pages** (`actions/upload-pages-artifact`, `actions/deploy-pages`).

Pages must be set to *Settings → Pages → Source: GitHub Actions*. `deploy/` holds exactly what is
served — `index.html` at <https://chocobear26.github.io/credex-cas/>, the documentation under `site/`
at <https://chocobear26.github.io/credex-cas/site/>.

## Troubleshooting

| Symptom | Cause and fix |
|---|---|
| `npm dependencies are out of sync` | `package.json` changed without Hugo's pack step: run `hugo mod npm pack`, then `npm install` |
| Sass errors, or no stylesheet | Dart Sass is missing from `PATH`: run `npm install`, and build through `make` — it puts `node_modules/.bin` first |
| `render-image: … could not be rendered by https://kroki.io/…` | No network, or a PlantUML syntax error in that file. `make serve` falls back to a link; `make build` fails on purpose |
| `generate: STALE — run make generate` | A generated file was edited by hand, or its source changed: run `make generate` and commit the result |
| `render-link: … does not resolve` | A relative link inside `content/` points at nothing — fix the path; `make lint` reports it with a line number |
| A page has no sidebar | Its `type` is not reaching Docsy's docs layout: check the `layouts/docs` mount in `hugo.yaml` — `make test` catches this |
