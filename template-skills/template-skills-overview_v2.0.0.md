# TEMPLATE Skills: Overview

## Introduction

The TEMPLATE skills are two Claude skills that set up and maintain the working files around a project according to a fixed scheme. template-dokumentprojekt covers projects whose result is a document or a set of related documents, such as reports, expert opinions, concepts, excursion reports and review reports. template-skill-projekt covers the development of a Claude skill, from creating or adopting it to packaging it.

Both skills are at version 2.0.0. Each is available as a `.skill` package for installation in Claude and as a `.zip` archive with identical content.

The two skills share two principles. First, the result is kept apart from the working documents that accompany it: organisation, log, consistency report, workplan and chat record each have their own file and their own role. Second, every write operation is followed by a check of the result, so that success is measured, not asserted.

## The skills at a glance

| Skill | Task | Input | Output | Supporting files |
|---|---|---|---|---|
| template-dokumentprojekt | Set up or extend a document project: result document, data table, organisation, decision log, consistency report, workplan and chat record; shared project version, precedence rules between files, identifiers, wording drafts, maintenance rules | a new project, or a report with companion files that are missing or out of date | project file set built from the templates | 1 template file (organisation, log, workplan, consistency report) |
| template-skill-projekt | Set up or extend a skill project: package, organisation, log, consistency report, workplan and chat record; naming, versioning and identifier rules | a skill to be created, adopted, renamed or developed further | project file set and `.skill` package | 1 template file (organisation, log, workplan, consistency report) |

## How the skills fit together

**Common base.** template-dokumentprojekt is the base of the two. template-skill-projekt takes over its template for the chat record and its rules for wording drafts, and adds what only skills need: naming by family prefix, `metadata.version` as the authoritative version, and the rule that a skill is handed over only as a complete package.

**Delegation to the SCIENCE skills.** Neither template writes its checks or plans itself. Consistency reports come from science-interne-konsistenz-pruefung and workplans from science-arbeitsplan-erstellen. Document projects also use science-quellenapparat-pruefung for source checks and science-aenderungsfortpflanzung for changes that affect several places. Skill projects take validation and packaging from skill-creator.

**Handover.** When a project moves to a new chat, science-uebergabeprotokoll-erstellen closes the log and the chat record kept under these templates and records the current state and the next identifiers.

**Identifiers.** The labels D1 to D6 are reserved for the dimensions of the consistency check. Decisions therefore carry the identifier D-nn in document projects but are referred to in running text as "decision nn", and in skill projects they are called EP.

## A typical sequence

1. Set up the file set with template-dokumentprojekt or template-skill-projekt.
2. Run a consistency check over the whole file set with science-interne-konsistenz-pruefung.
3. Create the workplan with science-arbeitsplan-erstellen, covering all known open points.
4. Work through the plan, recording decisions in the log and new findings in the workplan.
5. For a skill project, set the version, validate and build the package.
6. At a change of chat, write the handover protocol with science-uebergabeprotokoll-erstellen.

## Related skills

**SCIENCE skills.** The TEMPLATE skills define the files of a project but do no checking or planning of their own. As described above, they rely on the SCIENCE skills for consistency reports, workplans, source checks and the propagation of changes, and on science-uebergabeprotokoll-erstellen for the handover to a new chat.

**GEO skills.** Excursion and field reports written with geo-exkursionsbericht-erstellen or geo-excursion-report are typical document projects for template-dokumentprojekt, which provides the working files around them. geo-excursion-report relies on it for the inputs and project script of redrawn synthesis maps. template-skill-projekt governs the development of the GEO skills and lists geo- as a family prefix.
