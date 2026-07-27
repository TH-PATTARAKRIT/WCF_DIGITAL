# ACC5030 Finding Register

| Finding ID | Cycle | Severity | Category | Description | Evidence | Owner | Status |
|---|---:|---|---|---|---|---|---|
| F-ACC5030-AUTO-001 | 001 | LOW | VERSION_LINEAGE | Prompt versions `v1.0.0` and `v1.0.1` were failed technical attempts and must not be treated as completed business cycles. | `PRACC5030001_v1.0.0.md` | ChatGPT | CONTROLLED |
| F-ACC5030-AUTO-002 | 001 | MEDIUM | GOVERNANCE | ACC5030 control pointers were not initialized before execution. | `PRACC5030001_v1.0.0.md` | ChatGPT | RESOLVED_BY_CONTROL_FILES |
| F-ACC5030-AUTO-003 | 001 | LOW | RESULT_STATE | VSACC exit text said publication was pending although the file was subsequently published by automation. | `VSACC5030001_v1.0.2.md` | ChatGPT | ACCEPTED_WITH_CURRENT_POINTER |
| F-ACC5042-STRUCT-001 | N/A | MEDIUM | DRIVE_STRUCTURE | ACC5042 has two WCFUAT folders in Google Drive. Baseline selection remains unresolved and is outside ACC5030 scope. | `DRIVE_CLONE_MANIFEST_v1.0.0.yml` | Boss / Project Owner | REVIEW_REQUIRED |
