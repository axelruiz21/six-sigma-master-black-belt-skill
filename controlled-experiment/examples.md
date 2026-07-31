# Controlled Experiment — examples

## Canary: timeout budget on checkout→payments

**Hypothesis:** Reducing sync wait from 5s→1.5s with fail-fast raises purchase
success by cutting thread exhaustion.

**Success:** purchase success ↑; p99 checkout latency ↓.  
**Guardrail:** payment_error_rate must not ↑ beyond +0.2pp; refund rate flat.

**Rules:** abort if guardrail red for 15m; ship if success ↑ and guardrails green
for 48h at 50% traffic; else iterate.

**Control:** keep deadline + bulkhead as fitness-enforced defaults.
