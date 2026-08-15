# AUTO07_V31_EVIDENCE_FREEZE_MANIFEST

**Session:** `WCF-26-08-15-AUTO07-FINAL-GATE-001` · **Frozen (UTC):** 2026-08-15T12:10:00Z

**198 files · 1085.1 KiB · SHA-256 recorded for every file.**

Machine-readable: `AUTO07_V31_EVIDENCE_FREEZE_MANIFEST.json` · per-file table: `...CSV`

## Freeze rule

No frozen file may be overwritten. Any correction must be **additive** — a new session folder,
referencing the superseded file's sha256. This makes the baseline auditable rather than mutable.

## Coverage by build session

| Source session | Files | Bytes |
|---|--:|--:|
| `00_CONTROL` | 3 | 9,878 |
| `01_DB2_SCHEMA` | 7 | 109,466 |
| `08_DEFECT` | 1 | 6,025 |
| `09_EVIDENCE` | 5 | 43,236 |
| `10_FINAL_GATE` | 2 | 7,109 |
| `11_BUILD001` | 41 | 325,613 |
| `12_BUILD002_P1_FIX_FULL_LOOP` | 23 | 80,673 |
| `13_BUILD003_GRO15_GLID_DEPENDENCY_RECOVERY` | 16 | 57,607 |
| `14_BUILD004_DEPENDENCY_ACCOUNTING_FULL_LOOP` | 17 | 58,264 |
| `15_BUILD005_D13_ACCOUNTING_FULL_LOOP` | 16 | 80,589 |
| `16_BUILD006_D15_PASSBOOK_FINAL_ACCOUNTING` | 30 | 166,941 |
| `17_BUILD007_D04_GL_ID_FINAL_REGRESSION` | 28 | 104,498 |
| `18_FINAL_GATE_001` | 9 | 61,270 |

## Category counts

| Category | Files |
|---|--:|
| control/harness | 24 |
| defect | 2 |
| evidence | 57 |
| gate | 14 |
| results | 101 |

## Integrity verification

```bash
# re-verify any file against the manifest
shasum -a 256 <path>   # compare with .sha256 in the JSON/CSV
```
