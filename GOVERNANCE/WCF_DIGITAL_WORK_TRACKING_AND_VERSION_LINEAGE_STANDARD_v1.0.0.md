# WCF DIGITAL Work Tracking and Version Lineage Standard

Document ID: WCF-GOV-TRACKING-001
Version: 1.0.0
Status: CONTROLLED BASELINE
Approved by: Boss

## 1. System environments

- WCF — Production System / Actual Result — https://wcf.sso.go.th
- WCFUAT — Development, Remediation and Retest Environment — https://wcfuat.sso.go.th
- WCFLEGACY — Legacy System / Source of Truth / Expected Result — https://wcflegacy.sso.go.th/wcf

Primary Google Drive: https://drive.google.com/drive/folders/1fwc4S0zlkWRVq5qYiPqU6HWPLGz2lwaq

## 2. Controlled cycle identifiers

- ACCxxxxyyy — ChatGPT controlled execution prompt
- VSACCxxxxyyy — Claude Code / VS Code execution result
- PRACCxxxxyyy — independent review result

Where xxxx is the four-digit report code and yyy is the three-digit execution cycle.
One cycle contains exactly one Prompt, one Result and one Review. Files must not be overwritten. Corrections require the next sequence.

## 3. Version lineage

Every controlled document must identify document_id, document_version, previous_version_id, previous_commit_sha, derived_from, supersedes, change_reason, change_summary, current_version and commit_sha.
The current version must never be inferred only from the file date. Each report maintains `control/CURRENT.yml` and `control/version-lineage.yml` when execution begins.

## 4. Source-of-truth roles

- Jira: execution status, owner, blocker and next action
- GitHub: prompts, results, reviews, lineage, scripts and version history
- Google Drive: controlled source evidence and official deliverables
- Google Sheets: executive status register
- Make: orchestration only; not a source of truth

When records conflict: Evidence -> GitHub controlled record -> Jira -> Google Sheets.

## 5. Accounting reference precedence

1. `การบันทึกบัญชีกองทุนเงินทดแทน...` — authoritative accounting rule and DR/CR source of truth
2. `รหัสรายการทางบัญชี.xlsx` — transaction-code master
3. `0311 กระบวนการทำงานของการเงินรับ WCF.xlsx` — process supplement and coverage reference
4. WCFLEGACY — expected system result
5. WCF — actual production result
6. WCFUAT — remediation and retest result

The process supplement must not override the accounting treatment in the authoritative accounting guide. Any conflict must be recorded as `ACCOUNTING_OWNER_CONFIRMATION_REQUIRED`.

## 6. Mandatory state control

Allowed states: NOT_STARTED, EVIDENCE_REQUIRED, PROMPT_DRAFT, WAITING_FOR_BOSS_AUTHORIZATION, AUTHORIZED_FOR_EXECUTION, CLAUDE_RUNNING, WAITING_FOR_CLAUDE_RESULT, WAITING_FOR_REVIEW, CORRECTION_REQUIRED, WAITING_FOR_RETEST, READY_FOR_BOSS_REVIEW, BOSS_DECISION_REQUIRED and CLOSED.

Every status record includes Current State, Current Owner, Next Action, Due Date, Blocker, Required Evidence and Last Updated.

## 7. Automation safeguards

- Make uses an idempotency key: Report Code + Sequence + Source Commit SHA
- One report may have only one active cycle
- Default maximum cycle: 5
- Stop for evidence gaps, scope change, restricted-data risk, business decision, merge, Jira closure or Production Ready declaration
- Boss remains the sole final approver

## 8. Public repository control

This repository is public. Do not commit production PDFs, raw evidence, personal data, credentials, tokens, cookies, connection strings or identifiable live records. Store source evidence and official binary deliverables in controlled Google Drive and record only links, hashes, manifests, sanitized summaries and reusable templates in GitHub.
