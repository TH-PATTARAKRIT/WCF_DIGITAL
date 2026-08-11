# WCF DIGITAL — ChatGPT Session Update

Date: 2026-08-12
Scope: ACC5020 / ACC5021 / ACC5022
Comparison baseline: WCFUAT vs WCFLEGACY only

## Session Summary

### AC5020 — ACC5020 Trial Balance Validation
- Report: ACC5020 งบทดลอง
- Validation scope: WCFUAT vs WCFLEGACY only
- DATA rule: compare every business/accounting record and every amount; row count alone is not sufficient.
- Row order difference does not fail validation when all records match; comment must state: "ข้อมูลจัดเรียงไม่เหมือนกัน".
- Calculation rule: verify every calculated amount/item, not row count only.
- Current validated result: PASS.
- ACC5020 acts as the accounting balance base for ACC5021 and ACC5022.

### AC5022 — ACC5022 Operating Result Statement Validation
- Report: ACC5022 งบแสดงผลการดำเนินงาน
- Validation scope: WCFUAT vs WCFLEGACY only.
- Same DATA / Calculation / Row Order rules as ACC5020.
- Cross-report relationship: revenue accounts (4xxxxxxx) and expense accounts (5xxxxxxx) from the accounting balance feed ACC5022.
- ACC5022 calculates รายได้สูง (ต่ำ) กว่าค่าใช้จ่าย and this result links into the equity/accumulated-fund area used by ACC5021.

### AC5021 — ACC5021 Statement of Financial Position Validation
- Report: ACC5021 งบแสดงฐานะการเงิน
- Validation scope: WCFUAT vs WCFLEGACY only.
- Same DATA / Calculation / Row Order rules as ACC5020/ACC5022.
- Recheck performed after Boss identified a comparison concern.
- Corrected cross-system result: PASS.
- Example confirmed by Boss screenshot: รวมสินทรัพย์หมุนเวียน = 10,019,161,284.79 in both WCFUAT and WCFLEGACY.
- The previously reported 100,000,000.00 discrepancy was caused by comparing different views within the report, not a WCFUAT-vs-WCFLEGACY difference.
- Corrected interpretation:
  - Primary/Main view: WCFUAT = WCFLEGACY.
  - Summary/Grouped view: WCFUAT = WCFLEGACY.
  - Therefore Cross-System Difference = 0.00 for that issue.
- Advisory remains: BA/Accounting should confirm the business rule for why Primary/Main vs Summary/Grouped views may differ internally.

## Relationship of ACC5020, ACC5021, ACC5022

Accounting flow confirmed from the WCF accounting reference:

Source accounting transactions -> journals / transfer vouchers -> General Ledger -> month-end financial statements.

The reference financial statement set consists of:
- งบทดลอง
- งบแสดงผลการดำเนินงาน
- งบแสดงฐานะการเงิน

### Functional relationship
1. ACC5020 = Trial Balance / accounting balance source.
2. ACC5022 = Operating Result Statement derived mainly from revenue and expense accounts.
3. ACC5021 = Statement of Financial Position derived from assets, liabilities, and equity.
4. ACC5022 result (รายได้สูง/ต่ำกว่าค่าใช้จ่าย) affects the equity/accumulated-fund section used by ACC5021.

### Required reconciliation controls
- ACC5020 -> ACC5022: all revenue/expense accounts and amounts must trace.
- ACC5020 -> ACC5021: all asset/liability/equity accounts and amounts must trace.
- ACC5022 -> ACC5021: operating surplus/deficit must reconcile.
- ACC5021: Total Assets must reconcile with Total Liabilities + Equity according to the applicable report view/business rule.
- All three reports must use the same organization scope, period/date, and monthly/cumulative basis when cross-checking.

## Control Rules for Future Validation
- Compare WCFUAT vs WCFLEGACY only.
- DATA means record-by-record and amount-by-amount validation.
- Calculation means value-by-value calculation validation.
- Do not use row count as the sole pass criterion.
- Row-order differences alone do not fail; record comment: "ข้อมูลจัดเรียงไม่เหมือนกัน".
- Reports must include programmer recommendations where defects or reconciliation risks are found.

## Source of Truth Used in Session
- การบันทึกบัญชีกองทุนเงินทดแทน (รวม)-จังหวัด
- ACC5020 / ACC5021 / ACC5022 WCFUAT and WCFLEGACY report comparisons reviewed in this ChatGPT session.

## Current Control Status
- ACC5020: PASS
- ACC5021: PASS after recheck/correction
- ACC5022: retain prior validation evidence and cross-report linkage review; use current evidence-based comparison rules for any final approval.

This file is a session record for audit/review continuity under WCF DIGITAL project governance.
