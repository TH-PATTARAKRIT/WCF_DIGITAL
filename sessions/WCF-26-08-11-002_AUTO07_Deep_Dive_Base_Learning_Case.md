# [WCF-26-08-11-002] AUTO07 Deep Dive — Base Learning Case / Original vs V2

## Session Objective
Use AUTO07 as the Golden Base Learning Case for WCF DIGITAL batch modernization.

Core rule approved by Boss:
1. Original BATCH = **Business Behavior 100% / Source of Truth**
2. V2 = **New Implementation Technology / Architecture / Technical Pattern only**
3. NEW Source Code = **Original Business Behavior 100% + V2 Technology**

Business Behavior must not be changed by V2.

## Official Google Drive Working Structure
AUTO07 / 08_ORIGINAL_VS_V2_COMPARE/

- 01_AUTO07_OVERVIEW
- 02_AUTO07_ORIGINAL_GOLDEN_FLOW
- 03_AUTO07_V2_ACTUAL_FLOW
- 04_AUTO07_ORIGINAL_VS_V2_DIFFERENCE
- 05_AUTO07_WORKING_SPEC
- 06_AUTO07_TEST_PACK
- 07_AUTO07_PROGRAMMER_FIX
- 08_EVIDENCE
- 09_AUTO07_NEW_SOURCE_CODE

## Required Analysis Flow
Overview → Original Golden Flow → V2 Actual Flow → Original vs V2 Difference → Working Specification → Test Pack → Programmer Fix → Evidence → Final Gate

## Final Gate Result
Status reported by execution agent:
`AUTO07_BASE_LEARNING_CASE_READY_FOR_FINAL_GATE`

Recommendation:
`APPROVE WITH CONDITIONS`

The Final Gate analysis reported:
- Original trace: 17 steps
- V2 trace: 15 steps
- Original source: 6 files / 2,266 decompiled lines
- 59 accounting legs enumerated per side
- 30-row difference matrix
- 63 test cases across groups A-W
- 45 evidence records
- 5 diagrams rendered

## Proven Technical Defects / Differences
The execution agent reported 13 tracked findings:
- 7 TECHNICAL_DEFECT: DEF-01..DEF-07
- 4 V2_GAP: DEF-08, DEF-09, DEF-11, DEF-12
- 1 UNVERIFIED: DEF-10
- 1 VERIFIED shared weakness: DEF-13

### DEF-01 — Receiving-type-6 treatment mapping
Original Business Behavior selects account profiles from a treatment-code mapping table. V2 collapses the receiving-type-6 credit mapping to `11600000`.
Impact: accounting credit routing differs from Original.

### DEF-02 — Channels 29 and 30 missing
Original supports channels 11-30. V2 mapping/exclusion/SQL logic stops at 28.
Impact: Channel 29/30 routing and accounting behavior are not preserved.

### DEF-03 — PAY_TYPE / cheque override removed
Original separates cash/cheque behavior using PAY_TYPE and grouping logic. V2 removed PAY_TYPE from SQL/grouping and the related override.
Impact: mixed-tender receipts can merge and produce different debit behavior.

### DEF-04 — TREATMENT_CODE source changed
Original and BANKEDIT use base-table treatment data. V2 SSO logic sources treatment code from `VW_REVOKE_MONEY` via LEFT JOIN.
Impact: classification may differ or become NULL when join is unmatched.

### DEF-05 — Credit leg suppressed
Original emits debit/credit pair and allows unresolved profile to surface as unbalanced status N. V2 skips credit when profile code is empty.
Impact: silent incomplete posting and GL_ID may prevent later rerun recovery.

### DEF-06 — Transaction boundary removed
Original raw JDBC execution used explicit connection/commit/rollback behavior. V2 Spring migration did not replace it with a complete declarative transaction boundary.
Impact: partial commit / rerun safety risk.

### DEF-07 — Filter state leaks between runs
Original created fresh model state per call. V2 injected singleton retains mutable filters.
Impact: scoped rerun can affect later full run without explicit failure.

## Programmer Reference Requirement
Boss requires every Difference / Defect presented to Programmer to include at minimum:

`BATCH NO. | FUNCTION / METHOD | LINE | ORIGINAL BEHAVIOR | V2 BEHAVIOR | DIFFERENCE | IMPACT | STATUS`

Where exact source line references are not yet proven, status must remain `PENDING SOURCE LINE ENRICHMENT`; line numbers must not be guessed.

Before coding, enrich every actionable defect with:
- Original File
- Original Function/Method
- Original Line Start-End
- V2 File
- V2 Function/Method
- V2 Line Start-End

## Meeting Deliverables
Prepared for presentation:
1. AUTO07 difference Excel pack
2. AUTO07 Overview diagram
3. Final Gate / Programmer Fix summary
4. Meeting decision points

Local generated artifact in ChatGPT runtime:
`AUTO07_MEETING_DIFFERENCE_PACK_2026-08-11.xlsx`

## Approved Control Rule for New Implementation
Do not treat V2 as Business Reference.

Correct rule:

`Original Business Behavior 100%`
+
`V2 Technology / Architecture / Implementation Pattern`
=
`NEW AUTO07 Implementation`

The NEW implementation must pass regression tests against Original behavior before release.

## Recommended Next Phase
After Final Gate approval:
1. Lock `05_AUTO07_WORKING_SPEC` as Business Behavior Contract
2. Lock `06_AUTO07_TEST_PACK` as Acceptance Contract
3. Complete Source Reference Enrichment (Batch / Function / Line)
4. Design NEW AUTO07 implementation under `09_AUTO07_NEW_SOURCE_CODE`
5. Implement using V2 technology while preserving Original behavior 100%
6. Unit Test + Integration Test + Regression Test
7. Final Acceptance Gate

## Session Control
No source code modification was authorized during this Base Learning Case session.
Coding begins only after Final Gate approval and source-reference enrichment.

## Traceability
Repository: `TH-PATTARAKRIT/WCF_DIGITAL`
Session: `[WCF-26-08-11-002]`
Project: WCF DIGITAL
Batch: AUTO07

Status at update: `FINAL GATE READY / APPROVE WITH CONDITIONS`
