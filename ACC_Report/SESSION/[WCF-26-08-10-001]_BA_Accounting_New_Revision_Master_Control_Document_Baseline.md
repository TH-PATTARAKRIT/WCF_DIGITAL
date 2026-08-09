# [WCF-26-08-10-001] BA Accounting New Revision — Master Control & Document Baseline

## Status
- SESSION: OPEN
- EXECUTION: APPROVED
- CONTROL MODE: Master Control / Document Baseline
- DATE: 2026-08-10

## Purpose
Establish the new BA Accounting revision baseline for WCF DIGITAL and maintain auditable traceability between Google Drive evidence and GitHub session records.

## Repository / Evidence Baseline
- GitHub Repository: TH-PATTARAKRIT/WCF_DIGITAL
- Branch: SMEsPlus
- Primary GitHub Area: `ACC_Report/`
- Google Drive Master Folder: `97 WCF PROJECT`
- Google Drive folder structure is treated as the business-document baseline; GitHub structure should mirror report/module naming where practical.

## Google Drive Structure Observed
Examples of current accounting/report folders include:
- ACC5001
- ACC5002
- ACC5003
- ACC5004
- ACC5005
- ACC5013
- ACC5020
- ACC5021
- ACC5022
- ACC5023
- ACC5030 / ACC5030#01
- ACC5031
- ACC5034
- ACC5038
- ACC5042
- ACC5043
- ACC5051
- ACC5052
- ACC5053
- ACC5054
- ACC5057
- 00 REVIEW_FOR_APPROVE

GitHub already contains `ACC_Report/` with report-aligned folders. New session/evidence records must remain consistent with this structure.

## Source-of-Truth Rules
1. Accounting conclusions must trace back to source documents and/or verified system evidence.
2. No conclusion may rely only on an account code or report name.
3. No Evidence = No Confirmed Requirement.
4. WCFLEGACY is the operational reference baseline; WCFUAT is used for controlled comparison/validation as applicable.
5. Every STEP/STATE closure must preserve a Markdown session record in GitHub with evidence references.

## Accounting Baseline Source
Primary reference document:
- `การบันทึกบัญชีกองทุนเงินทดแทน (รวม)-จังหวัด`

Coverage includes:
- Chart of Accounts
- Accounting transaction codes
- Receipt journal
- Payment journal
- Transfer vouchers
- Debit/Credit logic
- Supporting reports
- Accounting workflow and posting logic

## Scope of This Session
1. Document baseline / Source of Truth
2. Accounting process and workflow
3. Chart of Accounts / accounting codes / Debit-Credit logic
4. Business Transaction → Accounting Entry → Report mapping
5. ACC / TRRE / RERE report relationship
6. WCFLEGACY vs WCFUAT validation where instructed
7. BA Requirement → Programmer/System Logic
8. Gap / Special Condition / Exception control
9. Evidence and traceability
10. Programmer recommendations

## Font / Document Standard
Font quality is a mandatory acceptance criterion for this revision.
- Thai text must render correctly.
- No missing glyphs, broken Thai shaping, or unreadable substituted fonts.
- Tables, Excel, PDF, and generated diagrams must be reviewed for Thai font rendering before delivery.
- Font handling must be treated as a functional document-quality requirement, not cosmetic cleanup.

## Control Status
**EXECUTION APPROVED / BASELINE BUILD IN PROGRESS**

## Next Actions
1. Build the Accounting Document Baseline index.
2. Map Google Drive report folders to corresponding `ACC_Report/` GitHub folders.
3. Create/maintain Session + STEP + STATE Markdown records.
4. Begin BA Accounting revision analysis from verified source documents.
5. Record blockers, evidence location, required owner/action, proposed fix, what can continue, and what cannot be counted as progress.
