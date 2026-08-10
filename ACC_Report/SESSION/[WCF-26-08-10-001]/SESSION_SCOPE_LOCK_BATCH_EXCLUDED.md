# [WCF-26-08-10-001] Session Scope Lock — BATCH Excluded

## Effective Decision
Boss authorized continuous execution across the session STATE structure, except BATCH work. BATCH will be handled by Boss in a separate session.

## Master STATE Structure
- 00_MASTER_CONTROL
- 01_SOURCE_OF_TRUTH
- 02_TOR_REQUIREMENT
- 03_BUSINESS_PROCESS
- 04_BATCH_AUTOMATION — EXCLUDED FROM THIS SESSION EXECUTION
- 05_E2E_EVENT
- 06_CHART_OF_ACCOUNTS
- 07_ACCOUNTING_REPORT
- 08_WCFLEGACY_REFERENCE
- 09_AUTHORITY_ACCESS_CONTROL
- 10_CHECKLIST_TESTING
- 11_AUDIT_VETO
- 12_HANDOFF_TO_TEAMS

## Execution Rule
1. Continue STATE-by-STATE to avoid scope confusion.
2. Do not execute, modify, validate, or conclude BATCH logic in STATE04 within this session.
3. Preserve BATCH references only as cross-reference evidence where another STATE depends on them.
4. Any BATCH-specific gap must be marked `DEFERRED TO SEPARATE BATCH SESSION`.
5. WCFLEGACY remains the expected-result/reference baseline; WCFUAT is not a Source of Truth.
6. Boss remains Final Gate.
7. No Evidence = No Progress.

## Immediate Sequence
Continue current STATE01_SOURCE_OF_TRUTH to exit criteria, then proceed to STATE02_TOR_REQUIREMENT, STATE03_BUSINESS_PROCESS, skip execution of STATE04_BATCH_AUTOMATION, then continue STATE05 through STATE12 in sequence.

## Gate Note
STATE04 is not failed or cancelled. It is intentionally carved out and will be governed by a separate Boss-controlled BATCH session.
