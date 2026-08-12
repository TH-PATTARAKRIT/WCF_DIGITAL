# WCF STATE Evidence Index

Drive source root: `1y5XrMuOwqRcbQiTNvGXLoJL61Cqtl9ri`
GitHub target root: `STATE/`

| STATE | Drive folder | GitHub folder | Primary Track Mapping | Control Status |
|---|---|---|---|---|
| STATE00 | 00_MASTER_CONTROL | STATE/00_MASTER_CONTROL | Integration / Governance | ACTIVE |
| STATE01 | 01_SOURCE_OF_TRUTH | STATE/01_SOURCE_OF_TRUTH | B01/C01/D01/E01 support | CLOSED WITH GAPS |
| STATE02 | 02_TOR_REQUIREMENT | STATE/02_TOR_REQUIREMENT | E01 support | CLOSED WITH GAPS |
| STATE03 | 03_BUSINESS_PROCESS | STATE/03_BUSINESS_PROCESS | C01 primary | CLOSED WITH GAPS / BATCH DEPENDENCY OPEN |
| STATE04 | 04_BATCH_AUTOMATION | STATE/04_BATCH_AUTOMATION | A01/B01/C01/D01/E01 | IN PROGRESS |
| STATE05 | 05_E2E_EVENT | STATE/05_E2E_EVENT | C01 primary | WORKING BASELINE / BATCH DEPENDENCY OPEN |
| STATE06 | 06_CHART_OF_ACCOUNTS | STATE/06_CHART_OF_ACCOUNTS | B01/E01 | CLOSED WITH CRITICAL GAP |
| STATE07 | 07_ACCOUNTING_REPORT | STATE/07_ACCOUNTING_REPORT | B01/C01/D01 | WORKING BASELINE / BATCH DEPENDENCY OPEN |
| STATE08 | 08_WCFLEGACY_REFERENCE | STATE/08_WCFLEGACY_REFERENCE | B01/C01/D01/E01 | CLOSED WITH CRITICAL GAP |
| STATE09 | 09_AUTHORITY_ACCESS_CONTROL | STATE/09_AUTHORITY_ACCESS_CONTROL | E01 | CLOSED WITH CRITICAL GAP |
| STATE10 | 10_CHECKLIST_TESTING | STATE/10_CHECKLIST_TESTING | Integration / later verification | WORKING BASELINE / BATCH DEPENDENCY OPEN |
| STATE11 | 11_AUDIT_VETO | STATE/11_AUDIT_VETO | A01–E01 Audit/VETO reconciliation | NOT READY FOR FINAL GATE |
| STATE12 | 12_HANDOFF_TO_TEAMS | STATE/12_HANDOFF_TO_TEAMS | Integrated result only | HOLD / NOT STARTED |

## Parallel Tracks

- A01 — Whole-WCF INACTIVE Census
- B01 — Accounting Deep Proof & Posting Control
- C01 — Whole-WCF E2E Business Flow Deep Proof
- D01 — Source / Runtime Deep Trace
- E01 — Original Control → V3 LEGACY Gap & Improvement Governance
- F01 — Missing Evidence Recovery (planned)

## Publication Control

GitHub repository is public. Drive evidence must be classified before raw publication:

- PUBLIC / SAFE_PUBLIC → eligible for GitHub copy
- SANITIZE_REQUIRED → publish sanitized derivative only
- CONTROLLED / PRIVATE → Drive remains source; GitHub stores link/hash/index only
- RESTRICTED → never publish to public GitHub
- UNKNOWN → review required

## Current PUBLIC-safe baseline

Existing Drive publication manifest for AUTO02–AUTO36 classified 669 files as:

- PUBLIC: 43
- CONTROLLED: 546
- RESTRICTED: 80

The 43 PUBLIC items are approved for controlled copying under Boss authorization dated 2026-08-12. Remaining Drive content requires recursive STATE inventory and classification.

Status: `TRACK MAPPING ACTIVE / DRIVE→GITHUB CONTROLLED COPY ACTIVE`
