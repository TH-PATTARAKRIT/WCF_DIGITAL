# ACC Report Controlled Workspace

This directory contains controlled report-verification records for WCF DIGITAL.

Primary Google Drive: https://drive.google.com/drive/folders/1fwc4S0zlkWRVq5qYiPqU6HWPLGz2lwaq

## Drive-to-GitHub structure

Each Google Drive ACC folder is represented by one GitHub workspace under `ACC_Report/ACCxxxx/`. Evidence folders are represented by pointer `README.md` files containing the controlled Drive URL. Raw evidence is not copied to this public repository.

## Standard execution structure

```text
ACC_Report/ACCxxxx/
├── README.md
├── control/
├── prompts/
├── results/
├── reviews/
├── references/
├── outputs/
├── scripts/
├── tests/
├── WCF/
├── WCFLEGACY/
├── WCFUAT/
└── REPORT_STATUS/
```

Additional Drive folders such as `VDO` or `RAW_DATA` are represented only when present.

## Naming standard

- Prompt: `ACCxxxxyyy_v1.0.0.md`
- Claude Code result: `VSACCxxxxyyy_v1.0.0.md`
- Independent review: `PRACCxxxxyyy_v1.0.0.md`

## Evidence rule

Do not upload raw WCF, WCFUAT or WCFLEGACY evidence to this public repository. Use controlled Google Drive folders and reference them through links, hashes and evidence manifests.
