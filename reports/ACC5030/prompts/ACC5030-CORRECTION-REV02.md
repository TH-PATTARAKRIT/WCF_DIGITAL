# ACC5030 Correction Prompt REV02

## Objective

Reperform ACC5030 verification using office-specific WCF versus WCFLEGACY pairs, resolve inconsistencies in the first Claude output, and produce a reproducible, internally consistent correction package.

## Mandatory controls

- WCFLEGACY is Source of Truth / Expected Result.
- WCF is Production System / Actual Result.
- WCFUAT is used only for remediation and retest.
- Do not compare across offices.
- Do not declare PASS, Production Ready, or close Jira.
- Do not publish source PDFs or real extracted data to this public repository.
- Use controlled Google Drive for source evidence and official binary deliverables.

## Required execution

1. Confirm file hashes, page counts, offices, report identity, and date ranges.
2. Visually inspect the disputed pages identified in the controlled review, including Bangkok pages 18 and 44 and Nonthaburi pages 8, 37, and 60.
3. Distinguish true report defects from PDF extraction or column-mapping errors.
4. Use the controlled accounting manual, accounting-code workbook, and receipt-process workbook for business-rule validation.
5. Reconcile every record and field for both office pairs.
6. Reconcile record, daily, account, office, and report totals.
7. Validate debit equals credit where the report structure supports it.
8. Produce one findings register used consistently by every output.
9. Generate a detailed reconciliation workbook, official report, executive summary, evidence manifest, execution log, and masked reproducibility package.
10. Upload official deliverables to controlled Drive.
11. Update Jira WCFDIG-22 without closing it.
12. Update the existing ACC5030 row in the executive Google Sheet without creating a duplicate.

## Acceptance conditions

The correction package is ready for independent review only when:

- All disputed findings have visual evidence.
- Business-rule references are traceable.
- Workbook, report, summary, Jira, and Google Sheet use identical counts and verdicts.
- No required deliverable is missing.
- No restricted data has been committed to GitHub.
- Boss final decision remains pending.
