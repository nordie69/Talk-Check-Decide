# Talk, Check, Decide: Summary

28 September 2026 · Stefan Mohr

## About this repository

This repository holds the skills and templates of the workflow described in the paper "Talk, Check, Decide: A Skill-Based Workflow for Writing and Verifying Geological Excursion Reports with an AI Assistant" by Stefan Mohr, version v5 of 28 September 2026, under the MIT licence. This page summarises the paper; every number is taken from it unchanged. The project records of the two reports and the scripts of the figures are not published.

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

The family has 20 skills in two groups, `geo-` skills for geological reports and localities and `science-` skills that work on any document, plus two templates. Skill names are the identifiers of the skill files, most of them German; the paper's Appendix A gives the task of each in English. Three carry a version number: `science-arbeitsplan-erstellen` (5.0.0), `template-skill-projekt` (1.5.0) and `template-dokumentprojekt` (1.6.0).

A lighter start, as the paper suggests, keeps three parts and drops most of the project files:

- a register of repeated statements, consulted before every change (`science-aenderungsfortpflanzung`);
- one consistency run per chapter (`science-interne-konsistenz-pruefung`);
- one fact check per chapter (`science-faktenbeleg-pruefung`).

A full project starts from `template-dokumentprojekt`, which lays down the file set, naming, versions, logs, the chat record, wording proposals and the check after every write.

## Licence

MIT, see [LICENSE](LICENSE).
