# AUTO07 V3.1 — FINAL GATE DECISION PACK

**Session:** `[WCF-26-08-15-AUTO07-FINAL-GATE-001]` · **Prepared (UTC):** 2026-08-15T12:10:00Z
**Baseline:** BUILD-001 → BUILD-007 · **Evidence:** 198 files, frozen with SHA-256

---

## Executive summary

AUTO07 V3.1 has been proven end-to-end against a **real DB2 v11.5.9.0 instance** (UTF-8), driving the
**shipped** `Auto07Runner` through the **shipped** `Db2Adapter` — the same wiring the simulation
uses, pointed at a real engine. **117 of 117 DB2 assertions pass**, alongside Golden 33/33 and
simulation 67/67. All nine ORIGINAL dependencies are implemented and proven. **P0 = 0, P1 = 0.**

Fourteen defects were found and closed across the seven build sessions. **Eight of them were
invisible to the simulation** and surfaced only on real DB2 — including three that a conventional
`Dr = Cr` reconciliation would have passed while the accounting was wrong.

The single remaining item is **D19 (P2, non-gating)**: three test-estate tables carry *derived*
physical type declarations because the authoritative catalogue is unreachable. It cannot produce a
wrong number — only a loud deploy-time error — and it closes with the same read-only extract already
specified for D04.

**Recommended decision: APPROVE the AUTO07 V3.1 technical baseline** and authorise the next stage
(pilot planning), with D19 carried as tracked technical debt.

---

## Final scoreboard

| Gate | Result | Evidence |
|---|---|---|
| Real DB2 | **PASS** — v11.5.9.0, UTF-8 (cp 1208), schema 38 stmts / 0 errors, fixtures 26/26 | `15_/`, `16_/`, `17_/` |
| Build | **PASS** — javac 0 errors | `17_/00_CONTROL/` |
| Dependencies | **9 / 9** | `16_/03_DEPENDENCIES/` |
| D04 GL_ID | **CLOSED** | `17_/02_CONTRACT/` |
| Golden | **33 / 33** | `17_/04_FINAL_REGRESSION/` |
| Accounting | **34 / 34 REAL DB2** | `18_/04_ACCOUNTING/` |
| Full Loop | **24 / 24 REAL DB2** | `18_/05_FULL_LOOP/` |
| GL_ID targeted | **16 / 16** *(corrected from the reported 16/15 — see reconciliation)* | `18_/01_RECONCILIATION/` |
| Idempotency ×3 | **PASS** (passbook active) | `18_/06_RECOVERY/` |
| Rollback | **PASS** (3 injection points, passbook active) | `18_/06_RECOVERY/` |
| P0 / P1 / P2 | **0 / 0 / 1 non-gating** | `18_/02_DEFECT/` |

**Aggregate on real DB2: 117/117** — full loop 24, passbook-failure 6, accounting 34, GL_ID 16,
loop proof 9, bank union 6, BUILD-004 15, BUILD-005 7.

## Scope proven

Source receipt → selection → invoice mapping → channel/bank (TR **and** TT) → office attribution
(all five ORIGINAL branches) → cancel decision → fee/fine → exceed money → accounting mapping →
RERE/TRRE → TRRE report → GL stamp → passbook → status write-back → re-run → failure recovery.

## Original behaviour equivalence

15 areas reviewed (`18_/03_EQUIVALENCE/`): **12 MATCH**, **3 INTENTIONAL TECHNICAL CHANGE — BUSINESS
EQUIVALENT** (excluded rows returned with a reason code rather than filtered in SQL; item ids
resolved from master data instead of literals; the transaction boundary made explicit), **1
DIFFERENCE — NON-GATING** (V3 does not use `WITH UR`; it reads committed rows, which is strictly
safer and is a recorded decision, SC-15). **0 BLOCKERS.**

No Golden or Accounting expectation was ever weakened. The one Golden change in the whole programme
— GRO-15 — corrected a *fixture's input status code* against three independent authorities, leaving
the expectation untouched.

## Real DB2 proof

Provisioned locally (colima x86_64 + DB2 community container), UTF-8, schema `ESSSWCF_T3`, JCC
4.33.31. Every harness re-run on the final BUILD-007 build. The DDL has been executed by a real DB2
parser, which is what caught `SQLCODE -206` (missing audit columns, BUILD-003), `SQLCODE -206`
(invented passbook columns, D15) and the GL_ID cast failures (D04).

## Golden proof

33/33, in-memory adapter, logic level. Retained as a regression control. **Its limits are recorded
honestly:** it did not and could not catch D15/D16/D17/D18 — the passbook port is suppressed there
by design, and the mapping layer is bypassed.

## Accounting proof

34/34 on real DB2, per-value: item code, Dr account, Dr amount, Cr account, Cr amount, office
attribution, exceed/fine component, GL_ID, TRRE/RERE linkage and passbook effect where applicable.
**No case passes on `SUM(Dr) = SUM(Cr)`** — ACC-09 is the standing proof of why: the exceed stream
balanced perfectly while sitting on the wrong account (D18).

## Full loop proof

24/24, all 20 required paths represented (`18_/05_FULL_LOOP/`), with before/run/after DB2 snapshots.

## Passbook proof

D15 closed. `ACC_TR_COMPANY_PASSBOOK`, 24-column ORIGINAL contract, one physical row per receipt
(confirmed against **19 real report workbooks, 3,620 rows**), three stream pairs, `'0000'` guard,
written inside the unit of work. PB-01..05, PBF-01..06.

## GL_ID proof

Contract settled from ORIGINAL runtime semantics (generated as `int`, `setInt` on every write,
`Integer.parseInt` on character reads) corroborated by P5 (`VARCHAR2(10)` = exactly
`Integer.MAX_VALUE`'s width) and by DB2's own measured implicit cast. **Numeric identifier,
table-specific physical representation, leading zeros insignificant, three-valued NULL/0/positive.**
Settling it exposed the last P1: `(Long) rs.getObject` threw on *both* authoritative physical
shapes. 16/16.

## Idempotency / rollback

PASS and PASS, on real DB2 with the passbook active — including a failure injected *inside* the
passbook insert, which rolled the ledger back with it (one atomic unit).

## Defect closure

| Sev | Found | Closed | Open |
|---|--:|--:|--:|
| P0 | 0 | 0 | **0** |
| P1 | 9 | 9 | **0** |
| P2 | 5 | 4 | **1** (D19, non-gating) |

Closed: D01, D02, D04, D07, D08, D09/GRO-15, D10, D12, D13, D15, D16, D17, D18.

## Remaining non-gating risk

**D19 only.** Derived physical types on three test-estate tables. Every failure mode is a loud
deploy-time error (`SQLCODE -204/-302`), never a silent accounting difference; GL_ID — the one field
where a type guess demonstrably mattered — is now type-agnostic. Closes with a read-only
`SYSCAT.COLUMNS` extract. Recommended as tracked technical debt. Full disposition: `18_/07_D19/`.

## Evidence index

`18_/01_RECONCILIATION/AUTO07_FINAL_GATE_EVIDENCE_INDEX.xlsx` — 189 artefacts indexed across 13
build-session folders; freeze manifest covers 198 files with SHA-256.

## Recommended Boss decision

```
APPROVE — AUTO07 V3.1 technical baseline is proven and frozen.
```

Conditions recommended:

1. **D19** raised as tracked technical debt, closed by the read-only catalogue extract.
2. **D04's external request** (read-only `SYSCAT.COLUMNS` + 50-row `GL_ID` sample) executed at pilot
   provisioning to confirm the canonical contract against the live catalogue. The contract is proven
   and the code is type-agnostic, so this is confirmation, not a dependency.
3. This baseline is a **technical proof, not a pilot or production approval**. Pilot planning is the
   next gate and remains Boss's decision.

**Not self-approved.** This pack recommends; the Boss decides.
