# Development Standard

This document establishes **Incremental Vertical Slicing** as the mandatory development and planning methodology for this project.

## Incremental Vertical Slicing

All development work must be planned and executed using an incremental vertical slicing approach. The agent MUST follow this standard when creating an implementation plan.

### Rules for Implementation Phases

1.  **Independent and Small:** Implementation must be divided into small, independently deliverable phases.
2.  **Visible Progress:** Each phase should deliver visible, usable, and testable UI/UX progress.
3.  **Vertical Slices:** Implement vertically across UI, business logic, backend/integrations, and testing within each phase. Avoid large backend-only or infrastructure-only phases.
4.  **End-to-End Scenarios:** Every phase must deliver at least one working end-to-end user scenario.
5.  **Requirement Mapping:** Each phase must explicitly list the requirement IDs it implements or addresses.
6.  **Validation Activities:** Include the corresponding validation activities for each phase: automated tests (unit, integration, E2E where appropriate) and manual testing instructions.
7.  **Acceptance & Verification:** Include acceptance criteria and expected verification evidence for each phase.
8.  **Context Maintenance:** Identify remaining requirements and known limitations at the end of each phase.
9.  **Approval Gates:** Obtain my approval before proceeding to the next phase.
10. **Evidence-Based Completion:** Never mark requirements as completed without implementation and verification evidence.

### Plan Structure Template

When creating a development plan, structure each phase as follows:

```markdown
### Phase [X]: [Phase Name]

*   **Requirement IDs Addressed:** `REQ-XXX`, `REQ-YYY`
*   **End-to-End Scenario Delivered:** [Describe the working scenario]
*   **Vertical Slice Implementation:**
    *   UI/UX: [Description]
    *   Business Logic: [Description]
    *   Backend/Integration: [Description]
*   **Validation Activities:**
    *   Automated Tests: [List test types]
    *   Manual Testing Instructions: [Steps]
*   **Acceptance Criteria & Evidence:** [List criteria and what constitutes evidence]
*   **Remaining Requirements / Limitations:** [List]
```
