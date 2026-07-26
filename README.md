# WCF DIGITAL

Public repository for controlled report-verification standards, reusable scripts, templates, sanitized records and version history for the WCF DIGITAL project.

## Repository role

- **GitHub:** governance, prompts, results, reviews, templates, scripts, controlled configuration and version lineage
- **Google Drive:** controlled source evidence and official deliverables
- **Jira:** tasks, defects, retest, owner, blocker and approval status
- **Google Sheets:** executive status register
- **Make:** orchestration only; not a source of truth

Primary Google Drive:
https://drive.google.com/drive/folders/1fwc4S0zlkWRVq5qYiPqU6HWPLGz2lwaq

## System environments

- **WCF:** Production System / Actual Result — https://wcf.sso.go.th
- **WCFUAT:** Development, Remediation and Retest Environment — https://wcfuat.sso.go.th
- **WCFLEGACY:** Legacy System / Source of Truth / Expected Result — https://wcflegacy.sso.go.th/wcf

## Controlled execution cycle

- `ACCxxxxyyy` — ChatGPT controlled execution prompt
- `VSACCxxxxyyy` — Claude Code / VS Code execution result
- `PRACCxxxxyyy` — independent review result

`xxxx` is the four-digit report code and `yyy` is the three-digit cycle.

## Accounting reference baseline

1. `การบันทึกบัญชีกองทุนเงินทดแทน...` — authoritative accounting treatment and DR/CR source of truth
2. `รหัสรายการทางบัญชี.xlsx` — transaction-code master
3. `0311 กระบวนการทำงานของการเงินรับ WCF.xlsx` — process and coverage supplement

The process supplement must not override the authoritative accounting treatment. Conflicts require Accounting Owner confirmation.

## Data-publication rule

This is a public repository. Do not commit production PDFs, raw evidence, personal data, credentials, tokens, cookies, connection strings, or any dataset that can identify a person, employer, office transaction or live system record.

## Governance

- No Evidence = No Progress
- WCFLEGACY = Source of Truth / Expected Result
- WCF = Production System / Actual Result
- WCFUAT = Development, Remediation and Retest Environment
- Boss is the sole final approver
- Do not merge, close Jira or declare Production Ready without Boss approval

Initial controlled pilot: `ACC5030`.
