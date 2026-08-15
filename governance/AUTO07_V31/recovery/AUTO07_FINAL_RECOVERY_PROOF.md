# AUTO07_FINAL_RECOVERY_PROOF — Idempotency ×3 and Rollback

**Session:** `[WCF-26-08-15-AUTO07-FINAL-GATE-001]` · **Verdict:** `IDEMPOTENCY = PASS · ROLLBACK = PASS`
**Backing:** REAL DB2 v11.5.9.0 via IBM JCC 4.33.31 — **passbook port ACTIVE**, no simulation used.

## Simulation evidence is explicitly excluded

Per §9 of the Final Gate order, no simulation result is used as final proof here. The HSQLDB suite
(67/67) and the in-memory Golden suite (33/33) remain in the evidence set as *regression* controls
only. Every assertion below is a value read back from DB2 after a real `Auto07Runner` invocation
through `Db2Adapter`.

This distinction is not academic: **D15, D16, D17 and D18 were all invisible to the simulation.** In
particular the simulation *suppresses the passbook port by design* (DEF-08), which is why a passbook
contract defect survived until the first live run.

## Idempotency ×3 — `Db2FullLoop`, runs 1/2/3

| Snapshot | docs | detail | working | TRRE | TRRE stamped | ledger↔receipt | **passbook** |
|---|---|---|---|---|---|---|---|
| BEFORE | 3 | 2 | 0 | 0 | 0 | 2 | 0 |
| **RUN 1** | 7 | 10 | 8 | 1 | 1 | 5 | **3** |
| **RUN 2** | 7 | 10 | 8 | 1 | 1 | 5 | **3** |
| **RUN 3** | 7 | 10 | 8 | 1 | 1 | 5 | **3** |

Runs 2 and 3 produced **zero new rows in every object**, outcome `SUCCESS_WITH_WORK` each time.

| Check | Result |
|---|---|
| ID-01 no new documents on run 2 or 3 | PASS |
| ID-02 no duplicate accounting rows | PASS |
| ID-03 no duplicate TRRE report rows | PASS |
| ID-04 no duplicate receipt–ledger links | PASS |
| **ID-05 no duplicate PASSBOOK rows** | **PASS** |
| GL-13 an already-stamped GL_ID is not re-stamped | PASS |
| ACC-30 accounting-level second run: 1 doc, 1 passbook row | PASS |

Mechanism: every UPDATE carries an expected-state predicate, and a 0-row result is **classified**
(`Applied.NOT_APPLICABLE`), never ignored.

## Rollback / failure injection

Two independent injections, both on real DB2 with the passbook active.

**A. Failure during accounting write** (`Db2FullLoop`, injected at the working-ledger insert)

| Check | Result |
|---|---|
| RB-01 failure surfaces (`PARTIAL_FAILURE`), lock released, audited — not silent | PASS |
| RB-02 NO partial ledger state | PASS |
| **RB-02b NO partial passbook row** | **PASS** |
| RB-03 failed receipt still unstamped — eligible for recovery | PASS |
| RB-04 re-run after failure posts the receipt | PASS |
| RB-05 recovered receipt GL-stamped **exactly once** | PASS |
| **RB-06 recovered receipt has exactly ONE passbook row** | **PASS** |

**B. Failure *inside* the passbook insert** (`Db2PassbookFail`) — the case that only exists because
the passbook is now real:

| Check | Result |
|---|---|
| PBF-01 failure inside the passbook insert surfaces | PASS |
| PBF-02 **ledger rows rolled back WITH the passbook failure** — one atomic unit (8→8) | PASS |
| PBF-03 zero partial passbook rows (4→4) | PASS |
| PBF-04 receipt unstamped, recoverable | PASS |
| PBF-05 recovery writes exactly ONE passbook row | PASS |
| PBF-06 recovered row carries the right **GL_ID, amount 333.00, employer, office** — value-level | PASS |

**C. GL path** (`Db2GlIdTargeted`)

| GL-15 rollback leaves NO partial GL stamp | PASS |
| GL-16 recovery stamps exactly once | PASS |

## Why atomicity holds

The passbook is buffered per receipt and **flushed inside `UnitOfWork.commit()`**, before
`Connection.commit()`; `rollback()` clears the pending buffer. So the passbook rows, the ledger
rows, the GL stamp and the TRRE report either all commit or all disappear. PBF-02 is the direct
proof: an injected passbook failure rolled the *ledger* back with it.

## Verdict

```
IDEMPOTENCY ×3 = PASS (REAL DB2, passbook active)
ROLLBACK       = PASS (REAL DB2, passbook active, 3 independent injection points)
```
