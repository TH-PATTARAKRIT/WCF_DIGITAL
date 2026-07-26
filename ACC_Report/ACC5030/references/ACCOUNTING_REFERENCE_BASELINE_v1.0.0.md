# ACC5030 Accounting Verification Reference Baseline

Document ID: ACC5030-REF-001
Version: 1.0.0
Status: CONTROLLED BASELINE

## Controlled locations

Primary Google Drive: https://drive.google.com/drive/folders/1fwc4S0zlkWRVq5qYiPqU6HWPLGz2lwaq
ACC5030 Google Drive: https://drive.google.com/drive/folders/1KRI_Vrnf7L5RNj2odU0XW-tzsrd0Djvu

## Environment baseline

- WCF — Production System / Actual Result — https://wcf.sso.go.th
- WCFUAT — Development, Remediation and Retest Environment — https://wcfuat.sso.go.th
- WCFLEGACY — Legacy System / Source of Truth / Expected Result — https://wcflegacy.sso.go.th/wcf

## Reference precedence

### 1. Primary accounting source of truth

`การบันทึกบัญชีกองทุนเงินทดแทน...`

Use this document to determine the correct:
- accounting treatment
- transaction code
- account code and account name
- debit and credit legs
- journal type or transfer voucher
- own-office, receive-on-behalf and responsible-office treatment
- automatic or manual posting
- supporting accounting evidence

### 2. Transaction-code master

`รหัสรายการทางบัญชี.xlsx`

Use this workbook to validate transaction-code identity, description, document type and process category. It must not override the debit/credit treatment in the primary accounting source of truth.

### 3. Process supplement

`0311 กระบวนการทำงานของการเงินรับ WCF.xlsx`

Use this workbook to validate process sequence, actor, channel, automatic/manual behavior and test coverage. It supplements the accounting rule and must not override it.

## Conflict rule

When reference sources conflict:

```yaml
reference_status: CONFLICT
accounting_rule_source: การบันทึกบัญชีกองทุนเงินทดแทน
conflicting_source: IDENTIFY_SOURCE
decision_status: ACCOUNTING_OWNER_CONFIRMATION_REQUIRED
```

Do not resolve a conflict by assumption.

## Required verification output

Each tested item should show:

| Process | Transaction Code | Expected DR | Expected CR | WCF | WCFLEGACY | Reference | Status |
|---|---|---|---|---|---|---|---|

Summary statuses:
- Accounting Rule: PASS / FAIL
- Transaction Code: PASS / FAIL
- Process Flow: PASS / FAIL
- System Result: PASS / FAIL
- Reference Conflict: YES / NO

## Public repository restriction

The actual PDF and Excel reference files remain in controlled Google Drive. Do not commit those source files to this public repository. GitHub stores only this reference definition, controlled links, hashes or sanitized extracts approved for publication.
