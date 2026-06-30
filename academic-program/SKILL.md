---
name: academic-program
description: Use when the user mentions developing, starting, managing, organizing, planning, coding, experimenting, summarizing, or writing a research or academic project, especially phrases like “开发科研项目”, “科研项目管理”, “论文项目”, “规划实验”, “写代码跑实验”, “总结实验结果”, “撰写科研论文”, or asks to standardize project files, code, references, experiments, and paper goals.
---

# Academic Program Skill

## Overview

Use this skill to manage an academic research project from idea formation to project organization, experiment planning, code execution, result synthesis, and paper writing.

Core principle: every research project must first establish three root Markdown entry documents, then keep all code, data, references, experiments, results, and manuscript materials traceable to those documents.

Secondary principle: define the research claim boundary before running code. A project must distinguish what the current data and method can prove, what is only a plausible interpretation, and what requires future evidence.

## First Action

When this skill triggers, start by locating the project root and checking whether these three root documents exist:

1. `项目文件说明.md`
2. `项目开发规则.md`
3. `项目开发说明.md`

If any are missing, create or update them before doing substantial project work. If all exist, read them in that order before changing files, writing code, planning experiments, or drafting paper text.

For reusable document outlines, read `references/project-doc-templates.md`.

## Three Required Documents

Create or maintain these documents for every academic project:

| Document | Purpose |
| --- | --- |
| `项目文件说明.md` | Explain directory structure, where files belong, and the default entry points for future conversations. |
| `项目开发规则.md` | Define rules for file naming, code style, experiment records, output paths, reference storage, verification, and collaboration. |
| `项目开发说明.md` | Define the research topic, current hypothesis, paper target, development goals, experiment route, and near-term priorities. |

Keep the documents concise enough to read at the start of each future session, but specific enough that another agent can continue the project without guessing.

## Research Workflow

Follow this sequence unless the user explicitly asks for a narrower task:

1. **Idea and scope**: clarify the research question, paper target, core claim, available data, expected contribution, constraints, and what the project must not claim yet.
2. **Project structure**: create the three root documents and decide where papers, code, data, references, docs, and outputs live.
3. **Evidence plan**: map each intended paper claim to required data, scripts, metrics, figures, tables, negative controls, and validation checks.
4. **Experiment plan**: write testable hypotheses, input data, labels or reference signals, train/validation/test splits, baselines, metrics, ablations, expected figures, and success criteria.
5. **Code development**: implement code inside the project’s code directory, use relative paths, avoid duplicating shared data, and route outputs to the correct `outputs/` directory.
6. **Experiment execution**: run scripts or notebooks with recorded parameters, seeds, input paths, output paths, environment notes, and failure conditions.
7. **Result summary**: convert raw outputs into Markdown summaries that include purpose, settings, main findings, failure cases, limitations, and next steps.
8. **Paper writing**: maintain manuscript, figures, tables, references, and experiment evidence so every claim can be traced back to code and results.
9. **Review and revise**: compare paper claims with actual evidence, identify missing experiments, update plans, and iterate.

Do not skip from an idea directly to code if the project lacks the three root documents.

## Claim Boundary Rules

Before planning or writing a paper section, classify each claim:

| Claim type | Meaning | Required handling |
| --- | --- | --- |
| Confirmed result | Directly supported by recorded experiments or verified analysis | Link to experiment record, code entry point, output path, and figure/table. |
| Plausible interpretation | Reasonable explanation but not uniquely proven | State as interpretation and list what would verify or falsify it. |
| Future work | Not demonstrated by current evidence | Keep out of results and conclusion claims; place in discussion or plan. |

If a proposed method depends on labels, metadata, ground truth, reference geometry, human annotations, or simulation assumptions, record the source and independence of that evidence. Do not describe a result as blind, general, causal, or end-to-end unless the experiment design actually supports that wording.

## Directory Policy

Prefer a simple structure adapted to the project:

```text
project-root/
  项目文件说明.md
  项目开发规则.md
  项目开发说明.md
  docs/
  paper/
  references/
  code/
  data/
  outputs/
```

For multi-line research projects, use numbered research-line folders:

```text
project-root/
  01_short_paper_or_baseline/
  02_main_method_or_journal_paper/
  03_shared_data/
```

Use names that match the project language and discipline. Keep shared large datasets in one shared data directory and reference them from code; do not copy large raw data into each method folder.

## Code Rules

- Use project-root-relative paths or clearly documented config paths.
- Put reusable code under the chosen `code/` directory.
- Put generated figures, metrics, logs, and intermediate experiment artifacts under `outputs/`.
- Record every script entry point and key parameters in an experiment note.
- Add validation gates for fragile inputs: dimensions, file formats, missing values, label validity, train/test leakage, duplicated samples, and coordinate or metadata consistency.
- If validation fails, stop and write a failure record instead of producing polished but invalid outputs.
- Before claiming completion, run the relevant verification command and report what passed or what failed.
- Avoid unrelated refactors while doing research experiments; preserve comparability.

## Experiment Record Rules

Each experiment record must include:

- Purpose or hypothesis
- Input data and version
- Label, reference, annotation, or ground-truth source, if any
- Data split rule and leakage prevention rule, if the experiment trains or evaluates a model
- Code entry point and command
- Parameters, random seed, and environment notes
- Output directory
- Metrics and figures produced
- Main conclusion
- Failure cases or limitations
- Next action

Store experiment records under `docs/` or the relevant research-line `docs/`. Do not rely on terminal history as the only record.

For model-based projects, prefer split rules that match the scientific question. For example, split by scene, subject, patient, instrument, site, or time when random sample-level splitting would leak context from training into testing.

## Reference and Paper Rules

- Store PDFs, BibTeX, RIS, reading notes, and citation exports under `references/`.
- Store manuscript files, figures, tables, and paper-specific assets under `paper/`.
- Keep conference papers, journal papers, and thesis materials separate when they serve different claims.
- Track which experiment supports each figure, table, and major claim.
- Distinguish confirmed results, plausible interpretation, and future work.
- Keep paper figures reproducible from scripts whenever possible. Save both the final figure and the data or configuration used to generate it.
- For manuscript figures, use consistent sizing, legible fonts, and caption-driven titles. Avoid putting large explanatory titles inside the figure unless the target format requires it.

## Common Mistakes

| Mistake | Correction |
| --- | --- |
| Starting code before project documents exist | Create the three root Markdown documents first. |
| Saving outputs in random root folders | Route outputs to the correct `outputs/` directory and record the path. |
| Mixing short-paper and journal-paper goals | Split goals in `项目开发说明.md` and separate paper folders if needed. |
| Copying large shared datasets into method folders | Keep one shared data source and reference it. |
| Writing paper claims from memory | Link claims to experiment records, scripts, figures, or tables. |
| Calling a candidate-selection experiment an end-to-end method | State exactly what the input is, what is selected or estimated, and what remains unproven. |
| Treating dependent metadata or labels as independent ground truth | Record evidence provenance and limit the claim boundary. |
| Hiding failed validation | Write a failure record and make the next action explicit. |
| Randomly splitting correlated samples | Split by the unit needed for the scientific claim, such as scene, subject, or time. |

## Completion Check

Before ending a research-project task, report:

- Which of the three root documents were read, created, or updated.
- Which files, code, experiments, outputs, or paper sections changed.
- Which claim boundary or evidence map was updated, if paper claims or conclusions changed.
- What verification was run.
- What the next research step should be.
