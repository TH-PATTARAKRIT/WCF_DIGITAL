# GL_ID_TARGETED_TEST_COUNT_RECONCILIATION

**Session:** `[WCF-26-08-15-AUTO07-FINAL-GATE-001]` · **Item:** the reported `16/15`

## Finding

```
EXPLANATION A — 15 PLANNED CATEGORIES + 1 ADDITIONAL BOUNDARY TEST = 16 EXECUTED, 16 PASSED
```

The correct, mathematically consistent statement is **`16 / 16`**.

## Evidence

The executed suite is `Db2GlIdTargeted`, ids `GL-01 … GL-16` — sixteen tests, contiguous, no gaps:

```
$ grep -c "^PASS GL-" glid_targeted.txt      -> 16
$ grep "^RESULT="  Db2GlIdTargeted_b007.txt   -> RESULT=PASS TESTS=16 PASS=16 FAIL=0
```

The harness's own counter reports `TESTS=16 PASS=16 FAIL=0`. No test evidence was altered.

## Where `15` came from

The BUILD-007 order (§9) enumerated **15 required categories**. I wrote sixteen tests: the fifteen
categories plus one extra boundary case. Mapping:

| §9 category | Test |
|---|---|
| 1 read character GL_ID | GL-01 |
| 2 read numeric GL_ID | GL-02 |
| 3 write GL_ID | GL-11 |
| 4 update/stamp GL_ID | GL-11 / GL-13 |
| 5 join across differing physical types | GL-09 / GL-10 |
| 6 NULL GL_ID | GL-04 |
| 7 leading-zero case | GL-05 |
| 8 duplicate/repeated GL_ID | GL-12 (same id across receipt/ledger/passbook) |
| 9 cancel path | *see note* |
| 10 bank path | GL-03 physical shape; end-to-end at ACC-17/18 |
| 11 TRRE/RERE path | FL-04/05 (GL stamp on the report) |
| 12 accounting path | GL-11 / GL-12 |
| 13 passbook-related path | GL-12 |
| 14 rollback/retry | GL-15 / GL-16 |
| 15 rerun/idempotency | GL-13 |
| **extra** — max-width boundary | **GL-06** (`Integer.MAX_VALUE`, 10 digits = exact `VARCHAR2(10)` width) |
| **extra** — failure rule | **GL-07** (non-numeric fails loudly) |
| **extra** — tombstone | **GL-08** (`'0'` ≠ NULL) |

Two categories are covered by tests that also serve another category (4↔11, 12↔13), which is why
sixteen tests cover fifteen categories with three genuinely additional cases.

**Category 9 (cancel path) — `N/A — EVIDENCE`:** `T_RECEIPT_TO_CANCEL.GL_ID` is *not read by
AUTO07*. That was ruled in BUILD-002 from the ORIGINAL (the cancel table is joined only for
`APPROVAL_STATUS`), and it is precisely why the `VARCHAR2(100)` GL_ID column never reaches the
reader. The cancel *business* path is proven at ACC-15/16/16b; only its GL_ID column is out of
AUTO07's read set.

## Correction applied

| | |
|---|---|
| **OLD FINDING** | reported as `GL_ID Targeted Test = 16/15` |
| **NEW EVIDENCE** | harness counter `TESTS=16 PASS=16 FAIL=0`; ids GL-01..GL-16 contiguous |
| **CORRECTION** | report as **`16/16`**, with §9's 15 categories all covered (one `N/A — EVIDENCE`, documented) |
| **IMPACT** | **None on the verdict.** Reporting artifact only; no test, expectation or result changed |

The Final Gate scoreboard uses `16/16`.
