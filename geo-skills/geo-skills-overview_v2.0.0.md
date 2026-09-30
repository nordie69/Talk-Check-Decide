# GEO Skills: Overview

## Introduction

The GEO skills are a set of ten Claude skills for geological, mineralogical and palaeontological fieldwork. Together they cover the path from a list of localities to a finished, checked excursion report and a documented collection: researching localities in the relevant databases, answering factual questions with sources, writing reports in a defined genre, compiling bibliographies, registering collected specimens, and reviewing finished documents.

All ten skills are at version 2.0.0. Each skill is available as a `.skill` package for installation in Claude and as a `.zip` archive with identical content.

The skills share two principles. First, every statement about a locality is bound to evidence for that locality, not to information about the surrounding region. Second, anything that cannot be confirmed is marked OFFEN (open) or UNKLAR (unclear) instead of being filled in by assumption.

## The skills at a glance

The table groups the skills by working phase.

| Phase | Skill | Task | Input | Output | Supporting files |
|---|---|---|---|---|---|
| Rules | geo-fundstellen-evidenzregeln | Shared rules for locality work: identity, region vs. point, evidence binding, literature categories A to D, markers OFFEN/UNKLAR | read in advance by other skills | none of its own, supplies rules | none |
| Research | geo-fundort-datenbank-recherche | Find and link localities in Mindat, Mineralienatlas and PBDB via web search | list of localities, with or without coordinates | .md with ID links, coordinates, type, PBDB collections | none |
| Research | geo-mindat-datenbank-recherche-mit-api | As above, but Mindat via API, plus mineral and rock lists and literature | list of localities, API token | Markdown table | 1 script |
| Research | geo-frage-belegbasiert-klaeren | Answer a geological question: source, evidence level, scope, confidence, check against the ICS time scale | question or statement | short answer, or review document with a register of claims | none |
| Writing | geo-exkursionsbericht-erstellen | Write a report in one of 15 genres; asks for the type first | localities, field notes, photos | report following the type profile, skeleton with OFFEN markers | 3 reference files |
| Writing | geo-excursion-report | English excursion report with route map, geological overlay and stratigraphic chart | list of localities | Markdown and PNG figures | 4 references, 5 scripts, 3 templates |
| Writing | geo-fundstellen-bibliographie | Sort existing sources by locality, Harvard style, verify DOIs | locality or excursion document | bibliography as .md | none |
| Collection | geo-fundstueckregister | Record a collecting trip as a register, identification per specimen | field notes, photo tables, box lists | Markdown table, CSV, labels | none |
| Review | geo-fundstellen-evidenz-pruefung | Check a finished locality document against the evidence rules | finished document | review report with severity levels and release recommendation | none |
| Review | geo-exkursionsbericht-typenanalyse | Check a finished report against all genres that could fit | finished report | type analysis, core plan, one delta plan per type | 2 reference files |

## How the skills fit together

**Shared rules.** geo-fundstellen-evidenzregeln is the common rule base. It is read before the database research, before geo-fundstellen-bibliographie and before geo-excursion-report. geo-fundstellen-evidenz-pruefung applies the same rules to finished documents, so the rules used for writing and those used for checking are identical.

**Writing and review.** geo-exkursionsbericht-erstellen writes a report and geo-exkursionsbericht-typenanalyse reviews it. Both work from the same typology of 15 genres, ranging from the peer-reviewed field guide to the legally binding exploration report. The analysis does not choose the genre; it shows what each candidate requires and leaves the choice to the author.

**Overlap.** geo-fundort-datenbank-recherche and geo-mindat-datenbank-recherche-mit-api do almost the same job and differ only in access: web search or the Mindat API. At roughly 5,000 to 6,000 words, their SKILL.md files are also the longest of the ten.

## A typical sequence

1. Link the localities in the databases with one of the two research skills.
2. Clarify open factual questions, such as the age of a unit, with geo-frage-belegbasiert-klaeren.
3. Write the report with geo-exkursionsbericht-erstellen, or with geo-excursion-report for an English report with maps and a stratigraphic chart.
4. Compile the bibliography by locality with geo-fundstellen-bibliographie.
5. Record the collected specimens with geo-fundstueckregister.
6. Check the finished report with geo-fundstellen-evidenz-pruefung and, if the target publication is not yet settled, with geo-exkursionsbericht-typenanalyse.

## Related skills

The GEO skills build on the two other families: the SCIENCE skills supply subject-independent planning and review, and the TEMPLATE skills supply the file structure of a project.

**SCIENCE skills.** geo-exkursionsbericht-erstellen leaves planning to science-arbeitsplan-erstellen and the review of the finished text to science-faktenbeleg-pruefung, science-interne-konsistenz-pruefung and science-quellenapparat-pruefung. geo-exkursionsbericht-typenanalyse is a fourth review axis alongside correctness (science-faktenbeleg-pruefung), self-consistency (science-interne-konsistenz-pruefung) and usefulness for readers (science-dokumentkritik-drei-sichten): it asks about the genre. It takes the form of its work plans from science-arbeitsplan-erstellen, hands single decision points to science-entscheidungspunkt-klaeren, and should run before the fact and consistency checks, because it decides which parts the report needs at all. In the other direction, science-entscheidungspunkt-klaeren passes geological factual questions to geo-frage-belegbasiert-klaeren, and science-quellenapparat-pruefung passes questions of location binding to geo-fundstellen-evidenz-pruefung.

**TEMPLATE skills.** An excursion report with its companion files is a document project in the sense of template-dokumentprojekt, which names excursion reports among its typical cases. geo-excursion-report refers to template-dokumentprojekt for redrawn synthesis maps, whose inputs and project script are set up there. The development of the GEO skills themselves follows template-skill-projekt, which lists geo- as one of the family prefixes.
