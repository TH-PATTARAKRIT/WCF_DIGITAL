# WCF DIGITAL AUTO STATE EXECUTION CONTROL v1.0

Session: `[WCF-26-08-10-001] BA Accounting New Revision — Master Control & Document Baseline`

Status: ACTIVE
Effective: 2026-08-11

## Operating Model
- Autonomous execution within each STATE.
- Boss is Final Gate only.
- No routine approval pause between STEP/STATE activities.
- Auto-close a STATE when Exit Criteria are met and evidence is complete.
- Auto-open the next STATE after closure.
- `04_BATCH_AUTOMATION` is excluded from this session and must be marked `DEFERRED TO SEPARATE BATCH SESSION`.

## Master State Flow
00_MASTER_CONTROL
01_SOURCE_OF_TRUTH
02_TOR_REQUIREMENT
03_BUSINESS_PROCESS
04_BATCH_AUTOMATION — SKIP / DEFERRED
05_E2E_EVENT
06_CHART_OF_ACCOUNTS
07_ACCOUNTING_REPORT
08_WCFLEGACY_REFERENCE
09_AUTHORITY_ACCESS_CONTROL
10_CHECKLIST_TESTING
11_AUDIT_VETO
12_HANDOFF_TO_TEAMS
FINAL GATE — BOSS

## Auto Execution Cycle Per State
1. Verify inputs and Source of Truth.
2. Execute analysis/work within approved scope.
3. Create deliverables using `WCF_DIGITAL_Project_Document_Standard_v1.0`.
4. Attach accessible evidence in Google Drive.
5. Create/update GitHub STATE record and traceability.
6. Record Gap, Risk, Blocker, Programmer Recommendation where applicable.
7. Validate Exit Criteria.
8. Auto-close STATE if criteria are satisfied.
9. Auto-start next STATE.

## Mandatory Stop / Escalation Conditions
- Critical Accounting Conflict.
- Source of Truth Conflict that cannot be reconciled from evidence.
- Scope Change.
- Destructive action or irreversible data change.
- Missing evidence that blocks the next STATE.
- Final Acceptance / Final Publication / Final Gate.

## Difficult Item Rule
If an item is technically complex but safe work can continue, continue analysis and mark `NEEDS BOSS REVIEW`. Stop the STATE only when the unresolved item blocks correctness, scope, accounting integrity, or final acceptance.

## Control Rules
- No Evidence = No Progress.
- WCFLEGACY = Expected Result / Reference baseline.
- WCFUAT is not Source of Truth.
- BATCH ORIGINAL is reference for the separate BATCH session only.
- BATCH V2.0 is not Source of Truth.
- Project document formatting, font, layout, naming, versioning, revision history and QA follow one standard across all STATEs.

## Current Execution
Continue `STATE01_SOURCE_OF_TRUTH` to Exit Criteria and then auto-open `STATE02_TOR_REQUIREMENT`.
