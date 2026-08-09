# WCF DIGITAL BA Accounting Batch Execution Standard

Document ID: WCF-GOV-BATCH-001
Version: 1.0.0
Status: CONTROLLED BASELINE
Approved by: Boss
Effective date: 2026-08-10

## 1. Purpose

This standard governs BA Accounting Batch learning and analysis for WCF DIGITAL, including BATCH Version 2 learning, future Original-vs-V2 comparison, End-to-End scenario construction, report traceability, evidence control, comments/findings, repair prompts and Boss final review.

## 2. Controlled storage locations

### Google Drive — official evidence and deliverables
Primary BA Accounting New Revision folder:
https://drive.google.com/drive/folders/1y5XrMuOwqRcbQiTNvGXLoJL61Cqtl9ri

All Claude AI (Web) prompts must explicitly state the destination path/folder for every output file. Do not create a deliverable without recording where it must be stored.

Required storage structure under the primary folder:
- 00_MASTER_CONTROL — master prompts, standards, registers and control records
- 01_SOURCE_OF_TRUTH — authoritative accounting references and supporting references
- 02_TOR_REQUIREMENT — TOR clauses and compliance mapping
- 03_BUSINESS_PROCESS — contribution, receipt, compensation, payment and accounting processes
- 04_BATCH_AUTOMATION — AUTO01-AUTO36 and future Original/V2 comparison evidence
- 05_E2E_EVENT — E2E event and scenario mapping
- 06_CHART_OF_ACCOUNTS — chart-of-accounts interpretation and mapping
- 07_ACCOUNTING_REPORT — accounting report catalogue and traceability
- 08_WCFLEGACY_REFERENCE — selected WCFLEGACY report evidence
- 09_AUTHORITY_ACCESS_CONTROL — menu authority and segregation-of-duties evidence
- 10_CHECKLIST_TESTING — TOR, BA, accounting, batch, report and E2E checklists
- 11_AUDIT_VETO — independent challenge, findings and clearance
- 12_HANDOFF_TO_TEAMS — controlled handoff packages for BA/SA/Dev/QA/UAT

For each AUTOxx under 04_BATCH_AUTOMATION, use:
- 01_SOURCE_JAVA_V2
- 02_CLAUDE_ANALYSIS_V2
- 03_MULTI_SOURCE_CROSSCHECK
- 04_SCENARIO_TEST
- 05_DIAGRAM
- 06_AUDIT_VETO
- 07_ORIGINAL_FUTURE
- 08_ORIGINAL_VS_V2_COMPARE

## 3. GitHub governance location

Repository: TH-PATTARAKRIT/WCF_DIGITAL
Branch: SMEsPlus
Governance path: GOVERNANCE/

GitHub stores prompts, Markdown summaries, registers, sanitized findings, lineage and reusable templates. Google Drive stores controlled source evidence and official binary deliverables.

The repository is public. Never commit production PDFs, raw production evidence, personal data, credentials, tokens, cookies, connection strings or identifiable live records. Store those in controlled Google Drive and record only links, hashes, manifests and sanitized summaries in GitHub.

## 4. Mandatory Claude AI (Web) operating modes

Every controlled Batch prompt must support these modes:

1. END-TO-END MODE — continue from source code and process evidence through event sequence, accounting impact, GL, E2E, report mapping, findings, diagrams and summary as far as evidence permits.
2. NO CARRY-FORWARD MODE — do not treat conclusions from another Batch/session as facts. Re-verify each Batch from its own evidence. Prior work may be used only as reference.
3. CONTINUE MODE — read the current register before execution and continue only unfinished work. Do not repeat completed work without reason.
4. REGISTER MODE — record Batch, Event, Source, Condition, Transaction, Debit/Credit, GL, Report, E2E, Evidence, Finding, Status and Next Action.
5. REPORT MODE — produce technical and executive summaries showing Completed, Verified, Partial, Conflict, Blocked, Skipped, Pending, Recommendation and Next Action.
6. COMMENT MODE — preserve doubts, conflicts and unresolved items as comments/findings. Do not silently normalize conflicting evidence.
7. BATCH-TO-REPORT TRACEABILITY MODE — identify every evidence-supported report relationship for the Batch.

## 5. Blocker and continuous-execution rule

If a step cannot be completed because evidence, access, file, dependency or authority is missing:
- record BLOCKED or SKIPPED;
- record exact reason, missing evidence, affected step and proposed repair action;
- continue immediately to the next independent step that can be completed;
- do not count the blocked step as progress;
- at the end of the run, generate a Repair Prompt covering only unresolved or failed work.

## 6. Autonomous selection rule

When multiple operational options exist and waiting for Boss is not required for a final decision, Claude AI (Web) must select the most evidence-supported, least-assumptive path automatically and record:
- AUTO-DECISION;
- options considered;
- option selected;
- evidence/reason;
- reversibility;
- impact.

Boss decision is mandatory for final accounting conclusions, acceptance, scope change, critical risk disposition, architecture change, production declaration, publication/merge designated as final, or any item explicitly reserved for Boss approval.

## 7. BATCH Version 2 learning rule

AUTO01-AUTO36 currently represent BATCH Version 2 learning evidence. The objective is to learn what Version 2 actually does; findings are preserved and are not rewritten merely to align with documentation.

When Original Batch source is received later:
- analyze Original independently first;
- then compare Original vs V2;
- classify differences as UNCHANGED, INTENTIONAL CHANGE, BUSINESS LOGIC CHANGE, ACCOUNTING CHANGE, CONTROL CHANGE, POSSIBLE REGRESSION or NEED VERIFICATION.

Original is treated as a functional benchmark when Boss confirms the Original version operates correctly, but accounting conclusions still require authoritative accounting references.

## 8. Mandatory Batch analysis chain

For each AUTOxx, trace:
Trigger -> Source Table/View/Model -> Selection Condition -> Join -> Group/Calculate -> Business Event -> Transaction Code -> Debit/Credit Account Codes -> Item Ledger/GL -> GL_ID/Reference Update -> Commit/Rollback -> Downstream Dependency -> E2E Scenario -> Accounting Report.

Separate:
- FACT FROM CODE
- SOURCE-DERIVED ACCOUNTING RULE
- BA INTERPRETATION
- INFERENCE
- OPEN QUESTION

Java code is Legacy Implementation Evidence, not accounting Source of Truth.

## 9. BATCH-to-Report Traceability requirement

Every Batch analysis must identify all evidence-supported report relationships and create a bidirectional mapping:

AUTOxx -> Reports affected
ACCxxxx -> Batches contributing data

Use relationship classes:
- DIRECT — source/code/process explicitly identifies the report
- DERIVED — report is derived from Journal/GL affected by the Batch
- RECONCILIATION — report is used to verify/reconcile the Batch result
- CANDIDATE — plausible relationship but evidence is incomplete
- NO EVIDENCE — no supported report relationship found

Minimum register fields:
Batch | Business Event | Transaction Code | Journal Type | Debit/Credit | GL Impact | Report Code | Final Report Name | Relationship Type | Evidence | Verification Status | Scenario Link | Finding/Open Question

Do not invent ACC report codes from event names.

## 10. Report register authority

For customer-used accounting reports, use the controlled Final Accounting Report Register as the customer-usage authority. If a source report is not present in the final customer report register, mark the comment exactly:

ลูกค้าไม่ได้ใช้งานในส่วนของรายงานทางบัญชี

Implementation status and customer usage are separate controls.

## 11. Multi-source cross-check

Batch conclusions should be cross-checked, where relevant, against:
1. authoritative WCF accounting guide;
2. accounting transaction-code master;
3. current business-process documentation;
4. WBS/Batch register;
5. Chart of Accounts;
6. E2E Activity evidence;
7. WCFLEGACY evidence;
8. Final Accounting Report Register;
9. Authority/Menu Access evidence;
10. TOR 6.15.6 and 6.15.9(1).

If sources conflict, record the conflict. Do not choose silently.

## 12. Required output package for each Batch

Recommended controlled files:
- AUTOxx_Reverse_Engineering_Analysis.docx
- AUTOxx_Section15_IO_Flow_FullLoop_REV02.docx
- AUTOxx_Section15_REV02.md
- AUTOxx_MultiSource_Recommendation.docx
- AUTOxx_Batch_Report_Traceability.xlsx or controlled register entry
- AUTOxx_Scenario_Test_Matrix.xlsx or controlled register entry
- fig1_ioflow.png
- fig2_crosscheck.png
- AUTOxx_REPAIR_PROMPT.md when blockers/skips exist

Document fonts, heading hierarchy, table formatting, page layout, headers/footers, spacing, colors and visual standards must follow the approved BA Accounting Master document format.

## 13. Mandatory final run summary

Before generating the Next Prompt, Claude AI (Web) must summarize:
- completed work;
- verified work;
- partial/conflicting work;
- blocked/skipped work;
- auto-decisions made;
- report mappings found;
- unresolved evidence;
- repair work required;
- Boss decisions required;
- current storage paths/links;
- readiness for the next Batch/state.

The Next Prompt must be based on this actual final state, not a generic template.

## 14. Final control principle

EXECUTE -> REGISTER -> CONTINUE -> SKIP BLOCKER -> REPORT -> COMMENT -> MAP BATCH TO REPORT -> AUTO-DECIDE WHEN SAFE -> SUMMARIZE GAPS -> GENERATE REPAIR PROMPT -> BOSS FINAL REVIEW.

No Evidence = No Verified Conclusion.
