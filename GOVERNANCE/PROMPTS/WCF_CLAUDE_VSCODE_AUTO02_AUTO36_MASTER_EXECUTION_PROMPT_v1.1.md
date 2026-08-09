# WCF DIGITAL — Claude AI VS Code AUTO02–AUTO36 Master Execution Prompt v1.1

Status: CONTROLLED VS CODE VARIANT
Approved operating scope: AUTO02–AUTO36 BATCH Version 2 learning.

This variant preserves the approved END-TO-END, NO CARRY-FORWARD, CONTINUE, REGISTER, REPORT, COMMENT and BATCH-to-REPORT modes, but adds VS Code runtime controls.

Mandatory VS Code pre-flight:
- record workspace root;
- verify repository and current Git branch;
- expected repository TH-PATTARAKRIT/WCF_DIGITAL and controlled branch SMEsPlus when available;
- verify Java read access, workspace write access, terminal/Git/network availability and local Google Drive sync path;
- never assume a Google Drive URL is a writable filesystem path.

If Drive local sync is unavailable, create deliverables under ./WCF_BA_ACCOUNTING_NEW_REVISION/ using the approved folder hierarchy, record the official Drive target, mark STORAGE_PENDING_UPLOAD, and continue.

If workspace is not the WCF_DIGITAL repository, do not alter unrelated repositories. Produce local deliverables and mark GITHUB_UPDATE_PENDING.

Before Git changes, inspect git status. Never delete, reset, clean, force-checkout, force-push or discard uncommitted user work automatically. Do not include unrelated user changes in commits.

Every artifact must record local_file_path, intended_google_drive_folder/url, github_target_path where applicable, timestamp, AUTO number and evidence status.

CONTINUE recovery: inspect local files, register and Git status; identify the last completed step and continue from the next unfinished step. Do not regenerate completed artifacts without evidence/recovery reason.

At each AUTO completion create AUTOxx_HANDOFF_MANIFEST.md with local outputs, Drive destinations, GitHub status, completed/blocked/skipped items, report mappings, scenarios, Repair Prompt, Boss decisions and next-AUTO readiness.

Boss remains final authority for final accounting verdict, final acceptance, scope/architecture change, critical risk acceptance, Production Ready and designated final publication/merge decisions.

Full operational prompt: WCF_CLAUDE_VSCODE_AUTO02_AUTO36_MASTER_EXECUTION_PROMPT_v1.1.md
Official Drive root: https://drive.google.com/drive/folders/1y5XrMuOwqRcbQiTNvGXLoJL61Cqtl9ri
