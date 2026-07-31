# Examples — Architecture audits

## Example 1 — Over-distributed checkout

**User ask:** "Review our checkout architecture before Black Friday."

**Condensed report excerpt:**

### Executive verdict
Checkout spans six synchronously coupled services for one user action. The CTQ
at risk is successful purchase under partial dependency failure. Collapse
pricing + cart validation into the checkout app process; keep payments and
inventory as explicit failure domains with timeouts and compensations.

### CTQs
| CTQ | Definition | Direction | Signal |
|-----|------------|-----------|--------|
| Purchase success rate | Paid order created / checkout starts | ↑ | 96.2% (SLO 99%) |
| p99 checkout latency | Start → order confirmed | ↓ | 4.8s (budget 2s) |

### Root causes (ranked)
1. Temporal + control coupling across services with no bulkhead — every hop
   multiplies failure probability.
2. No single source of record for "cart truth" during checkout — duplicate
   reads disagree under load.

### Recommended path
Modular monolith for cart/price/validate; keep `payments` and `inventory`
remote. Add deadline propagation and idempotent `CreateOrder`. Effort M;
removes three network failure modes.

---

## Example 2 — "Clean architecture" slowing features

**User ask:** "Is this over-engineered? Features take forever."

### Executive verdict
Four translation layers per use case with no independent test or deploy value.
CTQ is lead time for vertical features. Delete the unused `DomainService` +
`DtoMapper` tiers; keep ports only at the persistence and HTTP edges.

### First-principles gaps
- Layers named for purity, not for a failure/team/scale boundary
- Most "entities" are anemic mappers — no invariants enforced in one place

### Control
CI import lint: `handlers → app → domain`; forbid `domain → infrastructure`
except via interfaces defined in-domain. Metric: median files touched per
feature PR (baseline 18 → target ≤8).

---

## Example 3 — Narrow design question (lightweight pass)

**User ask:** "Should we add Redis in front of the user service?"

### Lightweight D→A
- **Y:** p95 `GET /me` latency; secondary: staleness tolerance for profile.
- **Current X:** DB primary is saturated on read-identical keys.
- **Assumption check:** "Must be real-time accurate" — unverified; product
  accepts 30s stale for avatar/name.

### Verdict
Cache only if staleness ≤30s is acceptable; otherwise fix the query/index or
add a read replica. Redis adds a failure domain and invalidation defects —
justified only if replica lag or cost blocks the CTQ.

Do not expand to a full five-section novel unless the user asks for a full audit.
```