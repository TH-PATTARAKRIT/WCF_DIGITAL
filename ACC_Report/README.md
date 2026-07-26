# ACC Report Controlled Workspace

This directory contains controlled report-verification records for WCF DIGITAL.

Primary Google Drive: https://drive.google.com/drive/folders/1fwc4S0zlkWRVq5qYiPqU6HWPLGz2lwaq

## Standard report structure

```text
ACC_Report/ACCxxxx/
├── README.md
├── control/
│   ├── CURRENT.yml
│   ├── cycle-register.md
│   ├── version-lineage.yml
│   ├── finding-register.md
│   └── decision-log.md
├── prompts/
├── results/
├── reviews/
├── references/
├── outputs/
├── scripts/
└── tests/
```

## Naming standard

- Prompt: `ACCxxxxyyy_v1.0.0.md`
- Claude Code result: `VSACCxxxxyyy_v1.0.0.md`
- Independent review: `PRACCxxxxyyy_v1.0.0.md`

`xxxx` is the four-digit report code and `yyy` is the three-digit cycle.

## Evidence rule

Do not upload raw WCF, WCFUAT or WCFLEGACY evidence to this public repository. Use controlled Google Drive folders and reference them through links, hashes and evidence manifests.
