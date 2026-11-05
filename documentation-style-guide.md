# Documentation Style Guide

* **Code over Prose:** Show exact terminal commands or code blocks instead of explaining them in text.
* **No Intros/Outros:** Omit introductory filler ("In this document we will discuss...") and conclusions. Jump straight to headers.
* **Checklists for Status:** Use `[ ]` and `[x]` checkable lists for tracking tasks and requirements.
* **Flat Structure:** Prefer internal subheadings inside a single file over creating multiple small sub-files.

---

## Allowed Root Files

To avoid clutter, the project root directory MUST ONLY contain:
- `README.md`
- `AGENT.md`
- `TEST_SUMMARY.md` (latest test run only)
- Standard config / dotfiles (`.gitignore`, etc.)

**ALL other documentation MUST live strictly inside `docs/01_...` to `docs/08_...`.**

---

## Docs Folder Organization

### Folder Structure

All project documentation lives in `docs/` organized into numbered folders (01–08):

| Folder | Purpose |
|--------|---------|
| **01_overview/** | System overview, high-level architecture, key design decisions |
| **02_architecture/** | Design documents, UML diagrams, UI/UX standards, architectural patterns |
| **03_roadmap/** | Project planning, task tracking (`todo.md`, `completed.md`, `planned.md`) |
| **04_investigations/** | Research, troubleshooting, bug root-cause analysis |
| **05_decisions/** | Architecture Decision Records (ADRs) |
| **06_operations/** | Runbooks, deployment, processes, agent prompts, `test_reports/` |
| **07_data/** | Data models, schemas, category references |
| **08_archive/** | Deprecated or obsolete documentation |

### File Naming Conventions

* **Timeless docs** (no date prefix):
  * `filename.md` (e.g., `docs/07_data/database.md`, `docs/02_architecture/system_design.md`)
* **Dated docs** (in `04_investigations/`):
  * `YYYY-MM-DD_short_title.md` (ISO format).
  * **Rule:** Every new investigation MUST create a NEW file. Never append unrelated investigation logs to an existing file.
* **Architecture Decision Records** (in `05_decisions/`):
  * `ADR_XX_short_title.md` (e.g., `ADR_01_add_images_table.md`)
* **Agent Prompts** (in `06_operations/`):
  * `AGENT_PROMPT_TASKXX_short_title.md` (e.g., `AGENT_PROMPT_TASK01_images_table.md`)

---

## Roadmap & Task ID Standards (`03_roadmap/`)

The `03_roadmap/` folder contains three core files:
- **`completed.md`**: Finished tasks merged into branch/prod. Append-only log with date prefixes.
- **`todo.md`**: Current active sprint/tier tasks.
- **`planned.md`**: Backlog, future ideas, unprioritized features.

### Task ID Generation Algorithm
1. Inspect both `03_roadmap/todo.md` and `03_roadmap/completed.md`.
2. Extract the highest existing integer from the `TASK(\d+)` pattern.
3. Assign the next sequential ID as `TASK` + $(N + 1)$ (e.g., `TASK01` to `TASK09`, then `TASK10`, `TASK57`...).
4. Task IDs MUST be strictly sequential and never change once assigned.

---

## Investigation Documentation

For standards on how to structure and maintain investigation documents, see `investigation-standards.md`.

---

## Test Documentation Standard (`TEST_SUMMARY.md`)

When executing tests, the agent MUST NOT dump raw CLI logs into chat. Instead, write structured test reports:

1. Overwrite the latest report at `./TEST_SUMMARY.md` (root).
2. Archive a permanent copy at `docs/06_operations/test_reports/YYYY-MM-DD_HHMM_test_summary.md`.

### Required Report Template:

```markdown
# Test Summary Report
**Date/Time:** YYYY-MM-DD HH:MM | **Status:** [PASSED / FAILED]

### 1. Metric Overview
| Metric | Value |
|--------|-------|
| Total Tests | 0 |
| Passed | 0 |
| Failed | 0 |
| Code Coverage | 0% |

### 2. Changes & Executed Tests
* List of tests added/modified/executed in this run.

### 3. Failures & Root Cause
* **Test Name:** `path/to/test.py::test_name`
  * **Failure Reason:** Exact assertion error or exception.
  * **Action Taken / Fix Required:** Root cause analysis and resolution.

### 4. Edge Cases & Risks
* [ ] Uncovered condition / edge case identified

Archive Policy (08_archive/)

Move superseded ADRs, outdated runbooks, or obsolete docs to 08_archive/.

  - Prefix archived files: archived_YYYY-MM-DD_original_filename.md.
  - Never delete historical documentation; archive it instead.
