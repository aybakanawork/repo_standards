# Investigation Documentation Standards

**Purpose**: Guidelines for writing investigation documents in `docs/06_investigations/`  
**Scope**: Generic, project-agnostic standards  
**Format**: Applicable to any project investigating technical questions, root causes, or architectural decisions

---

## 5 Core Standards

### 1. Scope: One Topic Per Investigation
- Focus on ONE major investigation/question/problem per document
- Limit scope to 5-7 key sections/tasks
- Don't mix multiple unrelated areas (e.g., don't combine "Image Strategy" + "Architecture" + "Database Design")
- **Exception**: OK to combine sequential phases of the same investigation (Phase 1 → Phase 2 → Phase 3)

---

### 2. Task/Section Status with Checkboxes
- **Every task/phase/section must have a status indicator**
- Use checkboxes for tracking completion:
  - `[ ]` — Not started
  - `[x]` — Completed
  - `⏳` — In progress
  - `❌` — Blocked or rejected
  - `🔄` — Needs revisit
- **Implementation Status Table** (optional): Create a table showing all related tasks with checkboxes
- **Placement**: Include status near section title or in a summary table at the top
- **Example**:
  ```markdown
  ### 2.1 Phase 1: Setup Database
  - **Status**: `[x]` Completed
  - Related task: TASK03
  - Details...
  
  | Phase | Task | Status |
  |-------|------|--------|
  | Phase 1 | TASK03 | [x] Completed |
  | Phase 2 | TASK04 | [ ] Not started |
  | Phase 3 | TASK05 | ⏳ In progress |
  ```

---

### 3. Task Reference & Traceability
- Include task ID(s) at the top of the document: `**Task Reference**: TASK01, TASK02, TASK05`
- Link each section/phase to its task ID
- **Why**: Connects investigation findings directly to implementation work
- Related ADRs or other investigations can be referenced but are optional

---

### 4. Metadata Header
- **File naming**: `YYYY-MM-DD_investigation_title.md` (date prefix for sorting)
- **At document start, include**:
  - **Status**: Overall investigation status (💡 Proposed, ✅ Approved, 🔄 In Progress, ❌ Blocked)
  - **Task Reference**: Related task IDs (e.g., `TASK01, TASK02, TASK05`)
  - Authors (optional)
- **No Document ID needed** (filename date provides identification)
- **Example**:
  ```markdown
  # Image Deduplication Investigation
  
  **Status**: ✅ Approved & Implemented
  **Task Reference**: `TASK03`, `TASK05`, `TASK09`
  **Authors**: Core R&D Team (optional)
  ```

---

### 5. Executive Summary (Mandatory)
- Always start investigation with 1-3 paragraph summary
- Include:
  - The question/problem being investigated
  - Key finding or recommendation
  - Impact on project
- **Example**:
  ```markdown
  ## Executive Summary
  Investigation determined that SHA256-based image deduplication 
  is more efficient than perceptual hashing for catalog images. 
  Recommendation: Implement SHA256 in Phase 1 with perceptual 
  hashing as Phase 2 enhancement.
  ```

---

## Implementation Status Tracking

Track investigation progress as implementation happens:

1. **Add status checkboxes** to each phase/task section
2. **Link to task IDs** in the roadmap (TASK01, TASK02, etc.)
3. **Update checkbox** when task is completed: `[ ]` → `[x]`
4. **Use Implementation Status Table** at the top to show overall progress at a glance
5. **Example**:
   ```markdown
   ## Implementation Status
   
   | Phase | Description | Task | Status |
   |-------|-------------|------|--------|
   | 1 | Database schema | TASK03 | [x] |
   | 2 | Extract service | TASK05 | ⏳ |
   | 3 | UI integration | TASK09 | [ ] |
   ```

---

## Checklist for Creating a New Investigation

Before starting a new investigation:

- [ ] Topic is singular and focused (not multiple areas mixed)
- [ ] Expected sections/phases: 5-7 max
- [ ] File named: `YYYY-MM-DD_investigation_title.md`
- [ ] Include status + task reference in header
- [ ] Write executive summary first (1-3 paragraphs)
- [ ] Plan implementation status table if multiple phases
- [ ] Link each section to a task ID
- [ ] Add status checkboxes to each section

---

## Quick Reference

| Standard | What | Why |
|----------|------|-----|
| 1 | One topic per doc | Keeps investigations focused |
| 2 | Checkboxes for status | Track completion as tasks progress |
| 3 | Task reference IDs | Connect findings to implementation |
| 4 | Metadata header | Clear status and traceability |
| 5 | Executive summary | Quick understanding of investigation |

---

## Generic & Project-Agnostic

These standards work across any project by:
- Using generic terminology (investigation, task, section, finding)
- Not requiring specific tools or platforms
- Focusing on **structure** not **content**
- Being copyable to `standards/` folder in any new project
