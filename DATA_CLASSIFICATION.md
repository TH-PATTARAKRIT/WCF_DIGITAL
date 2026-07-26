# Data Classification

## PUBLIC

Content suitable for this public repository:

- Governance documents
- Generic scripts and templates
- Synthetic examples
- Masked configuration samples
- Public issue and pull-request metadata

## CONTROLLED

Content stored outside GitHub, normally in controlled Google Drive locations:

- Official verification reports
- Reconciliation workbooks
- Evidence manifests with restricted links
- Visual verification screenshots
- Business-rule reference documents

## RESTRICTED

Content that must not be committed:

- WCF, WCFUAT, or WCFLEGACY source PDFs containing real data
- Raw extracted data from real reports
- Personal information and employer-identifying information
- Authentication material and infrastructure secrets
- Database exports, queries containing secrets, or production connection details

## Handling rule

When classification is uncertain, treat the material as RESTRICTED and do not commit it. Use a hash, masked example, or controlled Drive reference instead.
