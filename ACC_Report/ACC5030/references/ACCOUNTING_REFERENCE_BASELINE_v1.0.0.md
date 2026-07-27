# ACC5030 Accounting Verification Reference Baseline

Document ID: ACC5030-REF-001
Version: 1.0.0
Status: CONTROLLED BASELINE

Primary Google Drive: https://drive.google.com/drive/folders/1fwc4S0zlkWRVq5qYiPqU6HWPLGz2lwaq
ACC5030 Google Drive: https://drive.google.com/drive/folders/1KRI_Vrnf7L5RNj2odU0XW-tzsrd0Djvu

## Environment baseline
- WCF — Production System / Actual Result — https://wcf.sso.go.th
- WCFUAT — Development, Remediation and Retest Environment — https://wcfuat.sso.go.th
- WCFLEGACY — Legacy System / Source of Truth / Expected Result — https://wcflegacy.sso.go.th/wcf

## Reference precedence
1. `การบันทึกบัญชีกองทุนเงินทดแทน...` — accounting treatment, account codes and debit/credit legs
2. `รหัสรายการทางบัญชี.xlsx` — transaction-code master
3. `0311 กระบวนการทำงานของการเงินรับ WCF.xlsx` — process sequence and coverage supplement

The process supplement must not override the primary accounting source. Conflicts require `ACCOUNTING_OWNER_CONFIRMATION_REQUIRED`.

## Required verification output
| Process | Transaction Code | Expected DR | Expected CR | WCF | WCFLEGACY | Reference | Status |
|---|---|---|---|---|---|---|---|

The actual PDF and Excel reference files remain in controlled Google Drive.
