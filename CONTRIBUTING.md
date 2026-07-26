# Contributing

## Workflow

1. Create a branch from the controlled base branch.
2. Make one logically grouped change per commit.
3. Reference the related Jira issue in the pull request.
4. Do not commit production evidence or restricted data.
5. Run tests and validation before requesting review.
6. Request independent review.
7. Wait for Boss final approval before merge when the change establishes a project baseline, closes a gate, or affects production conclusions.

## Branch naming

Examples:

- `claude/acc5030-controlled-reconciliation-rev02`
- `fix/acc5030-parser-column-shift`
- `docs/report-verification-standard`

## Pull-request minimum evidence

- Scope and objective
- Files changed
- Validation performed
- Data-classification confirmation
- Jira reference
- Known gaps and residual risks
- Explicit statement that Jira was not closed and Production Ready was not declared

## Prohibited actions

- Direct push to a protected baseline branch
- Uploading real WCF/WCFUAT/WCFLEGACY evidence
- Publishing credentials or personal data
- Declaring PASS from incomplete evidence
- Closing Jira without Boss authorization
