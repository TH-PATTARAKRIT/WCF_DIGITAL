# D19_NON_GATING_DISPOSITION

**Defect:** `BUILD006-D19` · **Severity:** `P2` · **Status:** `OPEN — NON-GATING`
**Session:** `[WCF-26-08-15-AUTO07-FINAL-GATE-001]`

## The exact issue

Three tables were added to the **test estate DDL** during BUILD-005/006 because AUTO07 requires
them and the P5 export does not cover them:

| Table | Why it exists | How its physical types were chosen |
|---|---|---|
| `T_COMPANY_PASSBOOK` | the employer passbook (D15) | column **list and order** are 1:1 from the ORIGINAL (`CompanyPassbookModel:36-50`); **types** inferred from the ORIGINAL's bind calls (`setString` → VARCHAR, `setBigDecimal` → DECIMAL(15,2), date → DATE) |
| `T_RECEIVE_BY_CASH` | exceed-money amount source (D13) | `EXCEED_AMOUNT` typed DECIMAL(15,2) by analogy with every other amount in P5 |
| `T_CON_INVOICE` | `EXCEED_MONEY` bound on the bank pass (D13) | same |

The **names** follow the estate's proven naming generation (`CON_TR_*` → `T_CON_*`, as with
`T_CON_BALANCE_REMAIN_MONEY`), not a catalogue read.

So: the *column identities and semantics* are ORIGINAL-proven; the *physical type declarations* are
derived, because the authoritative catalogue is unreachable (same root cause as D04's tier-1 gap).

## Why it is P2 and not P1

A physical-type guess can only change behaviour if the adapter's **reading or writing** of that
column depends on the declared type. Both risks are eliminated:

1. **GL_ID — the one field where a type guess demonstrably changed behaviour — is now
   type-agnostic.** D04's canonical `readGlId()` accepts `Long`, `BigDecimal` or `String` and
   narrows per the ORIGINAL's own semantics. `T_COMPANY_PASSBOOK.ACCOUNT_LEDGER_ID` is read through
   that same reader. This is not an assertion: D04 proved the failure (`ClassCastException` on
   VARCHAR and on DECIMAL) and then proved the fix, 16/16 on real DB2.
2. **Every amount is `DECIMAL(15,2)`, which is P5's own scale for every monetary column** it
   declares (`PAYMENT_AMOUNT`, `PAID_FINE_FEE`, `TOTAL_AMOUNT`, `EXCEED_AMOUNT`, …). ACC-33 proves
   `999.99` survives end-to-end on ledger *and* passbook with no rounding.
3. Text columns are `VARCHAR`/`VARGRAPHIC` and are carried, never parsed or compared arithmetically.

## Residual risk — stated plainly

| Risk | Likelihood | Impact if it occurs | Detection |
|---|---|---|---|
| A real column is **narrower** than declared (e.g. `ITEM_NAME` shorter than 200) | low | insert truncation or SQLCODE -302 on deploy | first deploy against the real catalogue — fails loudly, does not corrupt |
| A real amount column has a different **scale** | very low | rounding difference | the deploy-time schema preflight compares declared vs catalogue |
| The real **table name** differs from the derived `T_*` form | moderate | DDL deploy fails with SQLCODE -204 | immediate and loud at deploy |

Every failure mode is a **loud deploy-time error**, not a silent accounting difference. That is the
substance of the non-gating verdict: D19 cannot produce a wrong number; it can only stop a
deployment until the names/types are reconciled.

## Why it must not be closed now

Closing it would assert the physical types are proven. They are not — they are derived. Recording
that honestly is worth more than a clean-looking register.

## Recommended future action

1. **Belongs in the technical-debt backlog** — yes, raise as a Jira item against AUTO07 V3.1.
2. **Closes automatically with D04's external request:** the same read-only `SYSCAT.COLUMNS` extract
   already specified (`13_.../02_GL_ID/`) resolves D19 if it is widened from `COLNAME='GL_ID'` to the
   three tables above. One extract, both items.
3. Until then the schema preflight (`SchemaCheck` / `SchemaPreflight`) is the standing control: it
   compares the required object/column set against the live catalogue at startup and refuses to run
   on a mismatch.

## Disposition

```
D19 = P2, OPEN, NON-GATING for the AUTO07 V3.1 Final Gate
```

Not closed, not downgraded, not hidden. Carried into the frozen baseline as the single known
residual item, with its closure path specified.
