# SCIENCE Skills: Overview

## Introduction

The SCIENCE skills are a set of twelve Claude skills for scientific writing and document work, independent of the subject area. They cover planning a piece of work, research, capturing one's own observations, reviewing finished documents against their sources and against themselves, making decisions that affect a document, carrying changes through it, designing a graphical abstract, and handing a project over to a new chat.

All twelve skills are at version 2.0.0, except science-arbeitsplan-erstellen, which is at version 2.1.0. Each skill is available as a `.skill` package for installation in Claude and as a `.zip` archive with identical content.

The skills share two principles. First, review is split into separate checks with a clear subject each: statements against sources, the bibliography against itself and the citations, and the document against its own conventions. Second, the language of an output follows its purpose: reports on a document are written in the language of that document, while plans and critique, which are instructions for the user, are written in the user's language.

## The skills at a glance

The table groups the skills by working phase.

| Phase | Skill | Task | Input | Output | Supporting files |
|---|---|---|---|---|---|
| Planning | science-arbeitsplan-erstellen | Write a verifiable work plan before execution: blocks in a justified order, steps with task, result and stop criterion, decision points, acceptance criteria, progress table | a project or task | work plan | none |
| Planning | science-entscheidungspunkt-klaeren | Turn a single decision point into an applicable rule, after counting the consequences of each option in the document | a decision point from a plan or review report | rule with exceptions and check expression | none |
| Research | science-deep-research-prompt-generator | Write a structured deep research brief for a literature search, without running the search | topic, research question, notes or exposé | ready-to-copy Markdown prompt | none |
| Research | science-recherchebericht-mit-quellen | Run a multi-stage web search and report the result | topic or question, or an existing research report | German Markdown report with numbered references and grouped source list | none |
| Capture | science-beobachtung-erfassen-befragung | Draw out a person's own observations through single questions tied to places in the document | target document and the person's answers | entries with separate evidence grades: observation, estimate, interpretation, third-party statement | none |
| Review | science-faktenbeleg-pruefung | Check in four phases whether statements are covered by their sources, find peer-reviewed replacements, work them in | text section with its sources | fact table, revised text, reference list, change report | none |
| Review | science-quellenapparat-pruefung | Check the bibliography entry by entry, resolve DOIs, test URLs, check citations in both directions | document with reference list | work plan, batch-wise results, change log | none |
| Review | science-interne-konsistenz-pruefung | Check a document against itself: conventions against their use, self-descriptions against chapters, repeated figures, rendering | document | Markdown review report | none |
| Review | science-dokumentkritik-drei-sichten | Assess a finished document from three perspectives of use | finished document | frozen critique and running work list, 15 measures per perspective | none |
| Maintenance | science-aenderungsfortpflanzung | Keep a register of statements that occur in several places and carry every correction through all of them | document and intended change | register and run report naming every place changed | none |
| Presentation | science-graphical-abstract | Design, draw and check a graphical abstract in the target journal's format | scientific article | two concepts, SVG, check sheet, rating grid | 5 references, 3 scripts, 2 templates |
| Session | science-uebergabeprotokoll-erstellen | Close log and chat record, align the working documents and write a handover protocol for a new chat | ongoing project | handover protocol as project file and paste text | 1 template |

## How the skills fit together

**Three kinds of review.** science-faktenbeleg-pruefung checks statements against sources, science-quellenapparat-pruefung checks the reference list and its citations, and science-interne-konsistenz-pruefung checks the document against itself. science-interne-konsistenz-pruefung only checks that citations and entries match each other; whether an entry describes the work correctly is checked by science-quellenapparat-pruefung alone. science-dokumentkritik-drei-sichten adds a further axis: the checks above establish correctness, while it judges usefulness, and it is meant to run after them.

**From plan to decision to change.** science-arbeitsplan-erstellen marks steps that need a judgement as decision points. science-entscheidungspunkt-klaeren resolves each of them into a rule that a later step can apply without further judgement. Factual questions with a single right answer are left to science-faktenbeleg-pruefung or geo-frage-belegbasiert-klaeren. Once a change is decided, science-aenderungsfortpflanzung carries it to every place and every dependent artefact.

**Research.** science-deep-research-prompt-generator only writes the research brief, for use in a deep research tool. science-recherchebericht-mit-quellen runs a search itself and delivers the report.

## A typical sequence

1. Plan the work with science-arbeitsplan-erstellen.
2. Prepare or run the research with science-deep-research-prompt-generator or science-recherchebericht-mit-quellen.
3. Add own observations with science-beobachtung-erfassen-befragung.
4. Review the draft with science-faktenbeleg-pruefung, science-quellenapparat-pruefung and science-interne-konsistenz-pruefung.
5. Resolve open decision points with science-entscheidungspunkt-klaeren and carry the changes through with science-aenderungsfortpflanzung.
6. Assess the result with science-dokumentkritik-drei-sichten.
7. For a journal article, design the graphical abstract with science-graphical-abstract.
8. At a change of chat, write the handover protocol with science-uebergabeprotokoll-erstellen.

## Related skills

**TEMPLATE skills.** template-dokumentprojekt and template-skill-projekt use science-interne-konsistenz-pruefung for their consistency reports and science-arbeitsplan-erstellen for their workplans; document projects also use science-quellenapparat-pruefung and science-aenderungsfortpflanzung. science-uebergabeprotokoll-erstellen closes the projects they set up when work moves to a new chat.

**GEO skills.** The SCIENCE skills provide the subject-independent part of the GEO workflow. geo-exkursionsbericht-erstellen plans with science-arbeitsplan-erstellen and has the finished text reviewed by science-faktenbeleg-pruefung, science-interne-konsistenz-pruefung and science-quellenapparat-pruefung. geo-exkursionsbericht-typenanalyse adds the genre as a fourth review axis alongside science-faktenbeleg-pruefung, science-interne-konsistenz-pruefung and science-dokumentkritik-drei-sichten, and should run before those checks. In the other direction, science-entscheidungspunkt-klaeren passes geological factual questions to geo-frage-belegbasiert-klaeren, and science-quellenapparat-pruefung passes questions of location binding to geo-fundstellen-evidenz-pruefung.
