# Public Repository Policy

## Purpose

This repository publishes reusable governance, scripts, templates, masked examples, and verification methods for WCF DIGITAL.

## Allowed content

- Governance and operating standards
- Reusable source code and tests
- Prompts with sensitive data removed
- Templates and schemas
- Masked or synthetic examples
- Evidence hashes, metadata, and controlled links
- Findings that contain no personal or confidential data

## Prohibited content

- Production or legacy PDF evidence
- Raw or normalized transaction data from live systems
- Personal data, employer-identifying data, or office transaction details
- Credentials, tokens, secrets, keys, connection strings, or cookies
- Proprietary reference documents without publication authority
- Any dataset that can be reverse-mapped to a real person or transaction

## Publication control

Every pull request must confirm:

1. No secrets are present.
2. No source evidence is embedded.
3. Examples are synthetic or masked.
4. Drive links remain access-controlled.
5. Jira and production status are not closed or declared without Boss approval.

Boss is the sole final approver for merge, closure, and production confirmation.
