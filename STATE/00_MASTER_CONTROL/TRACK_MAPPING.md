# WCF Parallel Track → STATE Mapping

Approved by Boss on 2026-08-12.

## Track Mapping

| Track | Primary STATE | Secondary STATEs | Purpose |
|---|---|---|---|
| A01 — Whole-WCF INACTIVE Census | STATE04 | STATE03, STATE05, STATE07, STATE08, STATE10, STATE11 | Classify ACTIVE / INACTIVE / DORMANT / BROKEN / REPLACED / UNKNOWN across Whole-WCF |
| B01 — Accounting Deep Proof | STATE06 | STATE01, STATE03, STATE05, STATE07, STATE10, STATE11 | Accounting lifecycle, GL_ID, posting, cancellation, manual-entry/auto-posting |
| C01 — Whole-WCF E2E Deep Proof | STATE05 | STATE03, STATE04, STATE06, STATE07, STATE10, STATE11 | End-to-end business flow and handoff proof |
| D01 — Source / Runtime Deep Trace | STATE04 | STATE01, STATE03, STATE05, STATE06, STATE07, STATE10, STATE11 | Source writer, runtime, launcher, scheduler references, procedure/report technical trace |
| E01 — Original Control → V3 Gap | STATE11 | STATE03, STATE04, STATE05, STATE06, STATE07, STATE09, STATE10 | Original control, V2 regression, V3 LEGACY recommendation/governance |
| F01 — Missing Evidence Recovery | STATE01 | STATE04, STATE05, STATE06, STATE07, STATE08, STATE09, STATE10, STATE11 | Recover missing DB/Dump/Operations/Scheduler/HA-DR/Performance evidence |

## STATE Coverage View

- STATE01 SOURCE_OF_TRUTH ← B01, D01, F01
- STATE02 TOR_REQUIREMENT ← Parent/BA baseline; Tracks consume requirements but do not own TOR changes
- STATE03 BUSINESS_PROCESS ← A01, B01, C01, D01, E01
- STATE04 BATCH_AUTOMATION ← A01, D01, E01, F01
- STATE05 E2E_EVENT ← A01, B01, C01, D01, E01, F01
- STATE06 CHART_OF_ACCOUNTS ← B01, C01, D01, E01, F01
- STATE07 ACCOUNTING_REPORT ← A01, B01, C01, D01, E01, F01
- STATE08 WCFLEGACY_REFERENCE ← A01, F01 plus Parent comparison evidence
- STATE09 AUTHORITY_ACCESS_CONTROL ← E01, F01
- STATE10 CHECKLIST_TESTING ← A01, B01, C01, D01, E01, F01
- STATE11 AUDIT_VETO ← A01, B01, C01, D01, E01, F01
- STATE12 HANDOFF_TO_TEAMS ← NONE until integrated reconciliation + Boss Final Gate

## Control Rules

1. Parallel tracks remain isolated/non-destructive while Parent execution is active.
2. Track findings are evidence inputs, not automatic Master Verdict changes.
3. Cross-track contradiction must use OLD FINDING → NEW EVIDENCE → CORRECTION → IMPACT.
4. No Evidence = Not Proven.
5. STATE12 remains HOLD until integrated reconciliation, verification, Audit/VETO and Boss Final Gate.
