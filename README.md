# Talk, Check, Decide: Summary

30 September 2026 · Stefan Mohr

## About this repository

This repository holds the skills and templates of the workflow described in the paper "Talk, Check, Decide: A Skill-Based Workflow for Writing and Verifying Geological Excursion Reports with an AI Assistant" by Stefan Mohr, version v5 of 28 September 2026, under the MIT licence. This page summarises the paper; every number up to the section Limits is taken from it unchanged. The section The skills describes the current state of the repository. The project records of the two reports and the scripts of the figures are not published.

## The problem and the questions

Large language models write fluent text but invent references and blur the line between what was seen and what was read. Geological excursion reports are sensitive to both failures, because every statement must be bound to a place and a source. The workflow was applied to two reports: a post-trip report on 20 localities in Germany and a pre-trip field guide on 21 localities in southern Norway and Denmark.

The paper asks three questions:

- **RQ1:** Where does an AI assistant help in writing field guides and excursion reports, and where does it fall short?
- **RQ2:** Which errors does AI assistance introduce, and which checks catch them before publication?
- **RQ3:** Does building skills in loops, from analysed practice and revised after each review round, support the building of skills and improve the reports?

## The workflow

An AI assistant (Claude) works under 20 written procedures, called skills, and two templates; the author works almost entirely by voice, decides and confirms. The assistant proposes, the author decides, and only confirmed wording enters the text.

Every task passes the same eight steps:

1. Locate the task.
2. Enter it in the work plan.
3. Research solutions.
4. Propose a solution or wording.
5. The author confirms, changes or rejects it.
6. Apply the change and log it.
7. Verify it against the metrics of the skills.
8. Present the result for acceptance.

Four working principles carry the cycle:

- **Wording proposals.** The assistant sets out the complete wording, numbered, with its place, the old wording, the sources and the consequences. Only the confirmed wording is inserted, unchanged, then logged and verified. The paper itself took 47 such proposals by 28 September 2026.
- **Separate review axes.** Six checks are kept apart because one can find errors the others miss: fact support, internal consistency, reference accuracy, locality evidence, genre and usefulness.
- **Counting instead of assuring.** Every finding carries a count or a location, and success is reported as measured values. References, coordinates and names are never taken from memory.
- **Records outside the chat.** Logs, work plans, decision logs and a chat record keep every input, decision and measured value in files that can be read, checked and exported.

## Results

The central result is that in three documented cases an error was caught by one review axis only: a misplaced age by internal consistency, a conclusion of the writer inside a citation by fact support, and a DOI pointing to a neighbouring paper by reference accuracy.

| Check | Report | Result |
|---|---|---|
| Consistency runs | Norway | 7 runs with 18, 4, 6, 4, 0, 2 and 71 findings; the last after the target format changed from a planning report to a dossier |
| Consistency runs | Germany | 29, then 8 findings over the whole report; 3, 5 and 4 in three later runs |
| Fact support | Germany, chapter 1 | 36 statements with a source: 18 verified, 14 partly verified, 3 not checkable, 1 misattributed |
| Reference accuracy | Germany | 13 errors in 211 entries, about 6 % |
| Locality evidence | Norway | 55 citations of Mindat checked; 26 proposals, 21 confirmed by a second pass, 22 changes made |
| Genre | Germany, version v13 | 9 of 11 obligations of an excursion report met |
| Usefulness | Norway | 45 measures from a three-perspective critique, 9 struck by the author |

Every rule of the two templates names the incident it came from, 43 in all. The errors that arose were misattributions, misplaced attributions, wrong DOIs or authors, regional statements transferred to single sites, stale numbers and cross-references, and editing accidents; each has an axis or a rule that catches it.

## Limits

The evidence comes from two reports by one author and one assistant, and the counts are taken from the author's own records. That building skills in loops also improved the reports is indicated but not shown: with two cases and no comparison group, better skills cannot be separated from reports that simply matured.

- About one reference in eight in the Germany list could be verified only in part.
- Two skills, for genre selection and genre analysis, were each tested once or not at all.
- The effort was large: 243 log entries for a pre-trip field guide.

## The skills

The repository holds 22 skills and 2 templates, 24 packages in all, in three families. Each family has its own folder with a README that describes every skill, its input and output, and how the skills work together; the same overview is included as a PDF. Each skill is provided as a `.skill` package for installation in Claude. Skill names are the identifiers of the skill files, most of them German. All packages are at version 2.0.0, except science-arbeitsplan-erstellen, which is at version 2.1.0.

The paper describes the family at an earlier state, with 20 skills and version numbers on three of them.

| Family | Folder | Packages | Scope |
|---|---|---|---|
| GEO | [geo-skills](geo-skills/README.md) | 10 | geological reports and localities |
| SCIENCE | [science-skills](science-skills/README.md) | 12 | work on any scientific document |
| TEMPLATE | [template-skills](template-skills/README.md) | 2 | file structure of document and skill projects |

### GEO skills

Ten skills for geological, mineralogical and palaeontological fieldwork, from researching localities to a finished, checked excursion report. Details in [geo-skills/README.md](geo-skills/README.md).

| Skill | Task |
|---|---|
| geo-exkursionsbericht-erstellen | Write an excursion or field report in one of 15 genres |
| geo-exkursionsbericht-typenanalyse | Check a finished report against all genres that could fit |
| geo-excursion-report | English excursion report with route map, geological overlay and stratigraphic chart |
| geo-fundstellen-evidenzregeln | Shared rules for locality work |
| geo-fundstellen-evidenz-pruefung | Check a locality document against these rules |
| geo-fundstellen-bibliographie | Bibliography by locality, with DOI check |
| geo-fundstueckregister | Register of collected specimens, with labels |
| geo-fundort-datenbank-recherche | Link localities in Mindat, Mineralienatlas and PBDB via web search |
| geo-mindat-datenbank-recherche-mit-api | The same, with Mindat via its API |
| geo-frage-belegbasiert-klaeren | Answer a geological question with source, evidence level and scope |

### SCIENCE skills

Twelve skills for scientific writing and document work, independent of the subject area: planning, research, capturing observations, review, decisions, changes, graphical abstracts and handover. Details in [science-skills/README.md](science-skills/README.md).

| Skill | Task |
|---|---|
| science-arbeitsplan-erstellen | Write a verifiable work plan before execution |
| science-entscheidungspunkt-klaeren | Turn a single decision point into an applicable rule |
| science-deep-research-prompt-generator | Write a deep research brief for a literature search |
| science-recherchebericht-mit-quellen | Run a web search and report with numbered references |
| science-beobachtung-erfassen-befragung | Capture own observations with separate evidence grades |
| science-faktenbeleg-pruefung | Check statements against their sources |
| science-quellenapparat-pruefung | Check the reference list, DOIs and citations |
| science-interne-konsistenz-pruefung | Check a document against itself |
| science-dokumentkritik-drei-sichten | Assess a finished document from three perspectives of use |
| science-aenderungsfortpflanzung | Carry a correction through every place it occurs |
| science-graphical-abstract | Design, draw and check a graphical abstract |
| science-uebergabeprotokoll-erstellen | Write the handover protocol for a new chat |

### TEMPLATE skills

Two templates that set up and maintain the working files around a project. Details in [template-skills/README.md](template-skills/README.md).

| Skill | Task |
|---|---|
| template-dokumentprojekt | File set and rules for projects whose result is a document |
| template-skill-projekt | File set and rules for developing a Claude skill |

### Getting started

A lighter start, as the paper suggests, keeps three parts and drops most of the project files:

- a register of repeated statements, consulted before every change (`science-aenderungsfortpflanzung`);
- one consistency run per chapter (`science-interne-konsistenz-pruefung`);
- one fact check per chapter (`science-faktenbeleg-pruefung`).

A full project starts from `template-dokumentprojekt`, which lays down the file set, naming, versions, logs, the chat record, wording proposals and the check after every write.

## Licence

MIT, see [LICENSE](LICENSE).
