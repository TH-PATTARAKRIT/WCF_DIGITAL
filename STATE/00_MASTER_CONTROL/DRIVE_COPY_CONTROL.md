# Google Drive → GitHub Copy Control

Boss approval: 2026-08-12

Source folder:
`https://drive.google.com/drive/folders/1y5XrMuOwqRcbQiTNvGXLoJL61Cqtl9ri`

## Source structure verified
The source Drive currently contains the STATE folders:
00_MASTER_CONTROL through 12_HANDOFF_TO_TEAMS.

## Public repository safety rule
`TH-PATTARAKRIT/WCF_DIGITAL` is a PUBLIC repository. Therefore direct bulk publication of all Drive files is NOT automatically safe.

Before any file bytes are copied into GitHub, each file must be classified:
- SAFE_PUBLIC
- SANITIZE_REQUIRED
- PRIVATE_DO_NOT_PUBLISH
- UNKNOWN_REVIEW_REQUIRED

Sensitive/raw operational data, personal data, credentials, private accounting extracts, DB dumps, runtime logs containing sensitive values, and any file whose publication status is not proven must not be pushed to the public repository.

## Approved execution sequence
1. Inventory Drive recursively by STATE.
2. Map each file to GitHub STATE path.
3. Classify publication safety.
4. Copy SAFE_PUBLIC files.
5. Sanitize then copy SANITIZE_REQUIRED files after verification.
6. Keep PRIVATE/UNKNOWN files in Drive and create GitHub evidence pointers/manifests only.
7. Record file ID, Drive path, GitHub path, SHA/hash where available, status, and reason.

## Current status
- Root Drive STATE structure: VERIFIED.
- STATE00 contents: inspected; includes many XLSX/CSV/DOCX/MD evidence files and nested folders.
- Bulk binary copy to public GitHub: HOLD pending publication classification.
- Track→STATE mapping: CREATED in `TRACK_MAPPING.md`.

No Evidence = Not Proven.
