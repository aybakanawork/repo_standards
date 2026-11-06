# Testing Style Guide

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
```
