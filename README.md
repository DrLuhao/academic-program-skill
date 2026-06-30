# Academic Program Skill

`academic-program` is a Codex skill for managing academic research projects from early ideas to structured experiments, reproducible code, result summaries, and manuscript writing.

It is designed for research work that can easily become scattered across papers, scripts, data folders, figures, temporary outputs, and chat history. The skill enforces a lightweight but durable project workflow: every research project starts with three root Markdown documents, then keeps experiments, outputs, references, figures, and paper claims traceable back to those documents.

## Purpose

Academic projects often fail to progress cleanly because the research question, file layout, experiment records, and paper claims drift apart. This skill helps Codex keep those parts connected.

Use it when you want to:

- Start a new academic or scientific research project.
- Standardize an existing research project folder.
- Plan experiments before writing code.
- Run code-driven experiments while preserving reproducibility.
- Summarize experimental results into durable Markdown records.
- Prepare figures, tables, references, and manuscript sections.
- Keep paper claims linked to actual evidence instead of memory.
- Separate confirmed findings, plausible interpretations, and future work.

## What It Does

The skill guides Codex to create or maintain three project-entry documents:

| File | Role |
| --- | --- |
| `项目文件说明.md` | Explains the project directory structure and where materials belong. |
| `项目开发规则.md` | Defines rules for naming, code style, experiment records, outputs, references, verification, and collaboration. |
| `项目开发说明.md` | Describes the research topic, current hypothesis, paper target, experiment route, and near-term priorities. |

After those documents exist, Codex should read them at the start of future research tasks before changing code, running experiments, or drafting paper text.

## Core Workflow

The skill organizes research work into a repeatable sequence:

1. Define the research question, expected contribution, constraints, and claim boundary.
2. Create or repair the three root Markdown entry documents.
3. Map intended paper claims to required evidence, scripts, figures, tables, and validation checks.
4. Plan experiments with data sources, labels, baselines, metrics, ablations, splits, and success criteria.
5. Implement code under a clear project directory, using relative paths and reproducible outputs.
6. Run experiments with recorded commands, parameters, seeds, environment notes, and failure conditions.
7. Summarize results into Markdown records with findings, limitations, failure cases, and next steps.
8. Write or revise manuscript sections while tracing each claim back to recorded evidence.
9. Review the gap between paper claims and experimental support before declaring progress complete.

## Key Features

- Three-document project entry system.
- Directory and naming conventions for research projects.
- Experiment-record template for reproducible scientific work.
- Claim-boundary rules for avoiding overclaiming.
- Evidence mapping from paper claims to experiments, code, figures, and tables.
- Data validation gates for fragile research inputs.
- Model-evaluation guidance, including split and leakage prevention.
- Reference and manuscript organization rules.
- Completion checklist for reporting what changed and what was verified.

## Installation

Copy the `academic-program` folder into your Codex skills directory:

```powershell
Copy-Item -Recurse .\academic-program "$env:USERPROFILE\.codex\skills\academic-program"
```

Restart Codex if the skill list does not refresh immediately.

## Example Prompts

```text
Use $academic-program to initialize this research project and create the three root Markdown documents.
```

```text
Use $academic-program to plan experiments for this paper idea before writing code.
```

```text
Use $academic-program to summarize these experiment results and update the claim-evidence map.
```

## Repository Structure

```text
academic-program-skill/
  README.md
  academic-program/
    SKILL.md
    agents/
      openai.yaml
    references/
      project-doc-templates.md
```

## Notes

This skill is intentionally domain-neutral. It does not encode any project-specific dataset, method, paper topic, or private research detail. It provides a reusable workflow for academic project development across disciplines.
