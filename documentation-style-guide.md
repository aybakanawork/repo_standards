# Documentation Style Guide

* Code over Prose: Show exact terminal commands or code blocks instead of explaining them in text.
* No Intros/Outros: Omit introductory filler ("In this document we will discuss...") and conclusions. Jump straight to headers.
* Checklists for Status: Use [ ] and [x] checkable lists for tracking tasks and requirements.
* Flat Structure: Prefer internal subheadings inside a single file over creating multiple small sub-files.

---

## Docs Folder Organization

### Folder Structure

All documentation lives in `docs/` organized into numbered folders (01–08) by category:

| Folder | Purpose |
|--------|---------|
| **01_overview/** | System overview, high-level architecture, key design decisions |
| **02_architecture/** | Design documents, UML diagrams, UI/UX standards, architectural patterns |
| **03_decisions/** | Architecture Decision Records (ADRs), important choices and rationale |
| **04_data/** | Data models, database schemas, category references, data documentation |
| **05_operations/** | Operational docs: deployment runbooks, agent prompts, processes, checklists |
| **06_investigations/** | Research and analysis: root causes, troubleshooting, findings, investigations |
| **07_roadmap/** | Project planning and tracking (see roadmap standard below) |
| **08_archive/** | Deprecated or obsolete docs (move here instead of deleting) |

### File Naming Conventions

**Timeless docs** (no date prefix):
- `filename.md`
- Examples: `database.md`, `ADR_01_images_table.md`, `architecture.md`

**Dated docs** (use in 06_investigations/):
- `YYYY-MM-DD_title.md` (ISO format for easy sorting)
- Examples: `2026-10-23_bbox_extraction_fix.md`, `2026-10-24_catalog_image_issue.md`

**Agent prompts** (use in 05_operations/):
- `AGENT_PROMPT_taskname.md`
- Examples: `AGENT_PROMPT_task1_images_table.md`, `AGENT_PROMPT_task2_categories_table.md`

**Architecture Decision Records** (use in 03_decisions/):
- `ADR_XX_short_title.md`
- Examples: `ADR_01_add_images_table.md`, `ADR_02_two_app_architecture.md`

### Roadmap Folder Structure (07_roadmap/)

The `07_roadmap/` folder contains three main files:

| File | Purpose |
|------|---------|
| **completed.md** | Tasks finished and merged into production. Date-stamped entries with what was done and why. |
| **todo.md** | Current sprint work: in-progress and immediately next tasks. Use task IDs (TASK01, TASK02, etc.). Organized by tier. |
| **planned.md** | Future roadmap: backlog, use cases, features not yet started, long-term ideas. |

**Requirements for each file**:
- **completed.md**: Append-only log with date prefix. Each entry: what was done + rationale + affected files.
- **todo.md**: Tier-based organization (TIER 1, TIER 2, TIER 3). Clear task IDs, effort estimates, dependencies, status.
- **planned.md**: Backlog items, ideas, future phases. Can be reorganized. Include effort estimates and use cases.

### Archive Policy

**What goes to `08_archive/`**:
- Obsolete ADRs (superseded by newer decisions)
- Deprecated runbooks (old processes)
- Outdated investigation reports
- Removed feature documentation

**How to archive**:
- Move file to `08_archive/`
- Optionally prefix: `archived_YYYY-MM-DD_original_name.md`
- Keep for historical reference (don't delete)

### When to Create New Folders

Create a new folder if:
- Docs share a clear category/purpose
- More than 5 related files accumulate
- Different naming patterns needed

Otherwise keep docs in root or existing folders.

---

## Investigation Documentation

For standards on how to structure and maintain investigation documents, see `investigation-standards.md`.