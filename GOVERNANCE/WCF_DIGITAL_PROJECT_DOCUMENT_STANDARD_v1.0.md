# WCF DIGITAL Project Document Standard v1.0

**Status:** MANDATORY PROJECT-WIDE CONTROL  
**Effective:** 2026-08-10  
**Authority:** 00_MASTER_CONTROL / Boss Final Gate

## Mandatory Rule
All WCF DIGITAL project documents across STATE 00-12 must use one consistent document standard covering font, layout, naming, versioning, status terminology, evidence references, and traceability.

## Font Control
- One approved project font family must be used consistently across the project.
- No agent/team may independently choose a different font per document.
- The exact official font family name must be verified from the approved project template before it is formally named; it must not be guessed.
- Until verified, preserve the font of the approved project template and do not introduce a new font family.
- Thai rendering must pass QA: no missing glyphs, broken shaping, misplaced vowel/tone marks, unreadable substitutions, or export layout corruption.

## Standard Document Identity
Every controlled document must include, where applicable:
- Session ID
- STATE / STEP
- Document ID / Title
- Version
- Date
- Status
- Owner / Reviewer
- Scope / Objective
- Source / Evidence
- Findings / Requirements
- Gap / Blocker / Risk
- Recommendation / Next Action
- Gate Impact
- Revision History

## File Naming
Preferred pattern:
`[SESSION]_[STATE]_[DocumentType]_[Subject]_vX.Y_YYYYMMDD`

Avoid uncontrolled names such as `Final`, `Latest`, or `New` without version/date in controlled deliverables.

## Versioning
- Draft: v0.x
- Controlled baseline: v1.0+
- Material changes require revision-history updates.
- Do not overwrite historical evidence without an audit trail.

## Evidence / Status
- No Evidence = No Progress.
- Do not use COMPLETE/PASS/READY without accessible evidence.
- Standard statuses include FOUND, VERIFIED, PARTIAL, GAP, BLOCKED, DEFERRED, READY FOR REVIEW.

## Spreadsheet / Table Standard
- Keep headers consistent and readable.
- Use stable formats for dates, amounts, account codes, IDs, and status fields.
- Row count alone is not Data Validation or Calculation Validation.
- Preserve Thai text and account/report codes as controlled values.

## Repository Roles
- Google Drive = Official Documents / Source / Working Evidence / Deliverables.
- GitHub = Session Log / STATE-STEP Record / Traceability / Technical Audit Trail.
- Cross-reference both sides.

## BATCH Scope
STATE04_BATCH_AUTOMATION is excluded from session `[WCF-26-08-10-001]` execution and will be handled in a separate Boss-controlled session. This session may record Batch dependencies only.

## Acceptance
Before Final Gate, controlled documents must pass:
1. Content Evidence Check
2. Version Check
3. Font / Thai Rendering Check
4. Layout Check
5. Traceability Check
6. Status / Gate Check

Any change to font/template/naming/version convention after this baseline requires a Change Record and consistent project-wide rollout.

Google Drive control document: `WCF_DIGITAL_Project_Document_Standard_v1.0` under `00_MASTER_CONTROL`.
