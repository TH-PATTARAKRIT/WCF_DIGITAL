# WCF DIGITAL — Claude AI Web AUTO02–AUTO36 Master Execution Prompt v1.0

Controlled prompt approved by Boss on 2026-08-10.

Official execution copy / deliverable location:
Google Drive Root: https://drive.google.com/drive/folders/1y5XrMuOwqRcbQiTNvGXLoJL61Cqtl9ri
Batch Root: 04_BATCH_AUTOMATION

This controlled prompt activates all of the following modes simultaneously:
1. END-TO-END MODE
2. NO CARRY-FORWARD MODE
3. CONTINUE MODE
4. REGISTER MODE
5. REPORT MODE
6. COMMENT MODE
7. BATCH-TO-REPORT TRACEABILITY MODE

Mandatory execution chain:
SOURCE JAVA -> ENTRY POINT -> SOURCE DATA -> FILTER -> JOIN -> GROUP/CALCULATE -> BUSINESS EVENT -> TRANSACTION CODE -> DEBIT/CREDIT -> ITEM LEDGER/GL -> GL_ID/REFERENCE UPDATE -> COMMIT/ROLLBACK -> DEPENDENCY -> E2E SCENARIO -> ACCOUNTING REPORT -> FINDINGS -> DIAGRAM -> SUMMARY -> REGISTER -> REPAIR PROMPT -> BOSS REVIEW PACKAGE.

Blocker rule: mark BLOCKED/SKIPPED, record reason/evidence/action, continue the next independent step, and create a Repair Prompt at the end. Blocked work is not progress.

Auto-decision rule: Claude AI Web must choose reversible evidence-supported operational options automatically when they do not change scope, approve final accounting, accept critical risk, or make a final gate decision. Record AUTO-DECISION, options, reason, evidence, reversibility and impact. Boss remains final authority for final accounting verdict, acceptance, scope change, architecture change, critical risk acceptance, Production Ready, and designated final publication/merge decisions.

No Carry-Forward rule: business/accounting/report conclusions from another AUTO are references only and must be independently re-verified for the current AUTO.

Batch-to-Report rule: create bidirectional mapping AUTOxx -> affected reports and ACCxxxx -> contributing BATCHes. Relationship classes: DIRECT, DERIVED, RECONCILIATION, CANDIDATE, NO EVIDENCE. Never invent ACC codes. If a report is not present in the controlled Final Accounting Report Register, use the exact comment: ลูกค้าไม่ได้ใช้งานในส่วนของรายงานทางบัญชี

Required per-AUTO Drive structure under 04_BATCH_AUTOMATION/AUTOxx/:
01_SOURCE_JAVA_V2
02_CLAUDE_ANALYSIS_V2
03_MULTI_SOURCE_CROSSCHECK
04_SCENARIO_TEST
05_DIAGRAM
06_AUDIT_VETO
07_ORIGINAL_FUTURE
08_ORIGINAL_VS_V2_COMPARE

Required outputs include reverse-engineering analysis, I/O Full Loop, Markdown summary, multi-source recommendation, Batch-Report traceability, Scenario Test Matrix, diagrams, Audit/Veto findings, and Repair Prompt when required.

Before ANY Next Prompt, Claude must output an UNDERSTANDING CHECK in Thai covering current AUTO, current state, proven facts, unverified items, skipped items, Repair Prompt, report mappings, E2E chain, Boss decisions, work that can continue automatically, and proposed next AUTO. Then state exactly: ทวนความเข้าใจเสร็จแล้ว — พร้อมสร้าง Next Prompt

AUTO02–AUTO36 loop:
EXECUTE -> REGISTER -> REPORT -> COMMENT -> MAP REPORTS -> BUILD SCENARIOS -> SKIP BLOCKERS -> REPAIR PROMPT -> FINAL SUMMARY -> UNDERSTANDING CHECK -> NEXT PROMPT.

At AUTO36 create master register, Batch-Report cross-reference, E2E Scenario Catalogue, Finding Register, Repair Backlog and Boss Executive Summary. Final state: READY FOR BOSS REVIEW.

Full execution prompt file is controlled in Google Drive and must be used as the operational prompt. This GitHub copy records the approved governance/operating requirements and version lineage without controlled evidence or production data.
