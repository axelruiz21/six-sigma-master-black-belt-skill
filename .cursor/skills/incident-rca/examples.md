# Incident RCA — examples

## Recurring timeout cascade

**Symptom:** SEV2 every peak Friday when payments slow.

**Chain:** Payments p99↑ → checkout sync wait → thread pool exhaust → 502s →
retry storm amplifies payments.

**Root cause:** No bulkhead/deadline; retries without jitter on non-idempotent path.

**Preventive:** Timeouts + bulkhead; idempotent retry budget. **Escalate:** MBB
on checkout coupling if more services share the same sync pattern.
