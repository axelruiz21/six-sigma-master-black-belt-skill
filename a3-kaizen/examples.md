# A3 Kaizen — examples

## Flaky checkout e2e

**Current:** 12% flake rate on `checkout.spec`; mean wait +20 min/PR.

**Goal:** Flake <2% in 2 weeks.

**Cause:** Shared staging DB; tests not isolated.

**Countermeasure:** Ephemeral DB per run; delete cross-test fixtures.

**Escalation:** None (local). If isolation requires new service boundaries → MBB.
