# Reference — MBB Architecture Toolkit

Supporting detail for [SKILL.md](SKILL.md). Read when deepening CTQs, waste,
or failure analysis.

## CTQ tree (lightweight)

```
Business outcome
└── CTQ Y (customer-critical)
    ├── X1 (driver) — e.g. p99 latency of checkout API
    ├── X2 (driver) — e.g. inventory consistency window
    └── X3 (driver) — e.g. change failure rate on payments path
```

Rules:
- Y must be customer- or business-valued, not "use Kubernetes."
- Each X must be controllable by design or process.
- If you cannot measure X, the design is flying blind — call that out in Measure.

### Example CTQs for software systems

| Domain | Example CTQ | Proxy Xs |
|--------|-------------|----------|
| Reliability | Successful requests under dependency failure | Blast radius, timeout budgets, isolation |
| Speed to market | Lead time for a vertical feature | Module coupling, shared release train |
| Correctness | Consistent reads after write | Single writer, idempotency, schema ownership |
| Cost | $ per useful transaction | Duplicate pipelines, over-provisioning |
| Security | Unauthorized data exfil prevented | Trust boundaries, secret sprawl |

## SIPOC for systems

| Element | Software reading |
|---------|------------------|
| Suppliers | Upstream teams, vendors, event producers, humans entering data |
| Inputs | Requests, events, configs, schemas, credentials |
| Process | Services, jobs, workflows, deploy pipelines |
| Outputs | APIs, UI states, reports, side effects on external systems |
| Customers | End users, downstream services, operators, auditors |

## Waste taxonomy (Lean) → architecture

| Waste | Architecture smell |
|-------|--------------------|
| Overproduction | Speculative services, unused feature flags forever, extra environments |
| Waiting | Sync chains, deploy queues, approval theater without risk |
| Transport | Needless hops (A→B→C for one write), chatty RPCs |
| Over-processing | Layers that only translate types; dual ORMs; golden-path frameworks unused |
| Inventory | Ticket backlogs of half-migrations; unused feature branches; zombie modules |
| Motion | Context switching across many repos for one change |
| Defects | Ambiguous ownership, no contract tests, silent data drift |
| Unused genius | Platform that teams work around; docs/tools nobody trusts |

## Coupling types (quick diagnose)

1. **Content** — reaching into another module's internals
2. **Common** — shared global mutable state / god config
3. **External** — shared data formats/protocols (OK if versioned)
4. **Control** — A tells B *how* to do work (prefer telling *what*)
5. **Temporal** — must run in lockstep / same process window
6. **Stamp** — fat shared DTOs forcing unrelated change coupling

Prefer dependency direction toward stable, high-cohesion cores. Invert when
volatile policy sits under stable domain.

## Distribution tax

Before recommending a new process/service/region, confirm at least one:

- Independent scale or resource profile
- Independent failure domain required by CTQ
- Independent deploy/ownership cadence required by org
- Compliance / data residency boundary

If none apply, co-locate and simplify.

## Lightweight FMEA columns

| Item | Failure mode | Effect on CTQ | Severity (1–10) | Cause | Occurrence (1–10) | Current controls | Detection (1–10) | RPN | Action |
|------|--------------|---------------|-----------------|-------|-------------------|------------------|------------------|-----|--------|

RPN = S × O × D. Focus Improve/Control on top RPNs.

## Fitness function examples

- Forbidden import rules (e.g. `domain` must not import `adapters`)
- Contract tests on public APIs / events
- Max dependency depth or cycle check in CI
- Latency SLO burn-rate alerts on the critical path
- Schema compatibility checks on produce/consume

## Define vs Improve language

| Avoid | Prefer |
|-------|--------|
| "Adopt microservices" | "Split only the inventory write path; blast radius is the CTQ" |
| "Add an event bus" | "Decouple billing from checkout with an outbox on OrderCommitted" |
| "Needs better architecture" | "Payments has two writers to `ledger`; pick one source of record" |
| "Best practice says…" | "Constraint X forces Y; evidence: …" |
```