# Shared suite vocabulary

Use these terms consistently across all skills in this suite.

## Core model

| Term | Meaning |
|------|---------|
| **Y** | Outcome that matters (CTQ) — customer or business valued |
| **X** | Controllable driver of Y |
| **Y = f(X)** | Architecture and process exist to move the Xs that move Y |
| **CTQ** | Critical-to-quality characteristic with an operational definition |
| **VOC** | Voice of Customer — need / desire / pain |
| **VOP** | Voice of Process — how the system currently behaves |
| **Operational definition** | Exact rule for measuring pass/fail (no slogans) |
| **COPQ** | Cost of poor quality — rework, incidents, delay, waste |

## Severity (all reports)

- **Critical** — CTQ failure likely; block further feature work on this path
- **High** — Material defect/cost driver; schedule soon
- **Medium** — Real issue; batch with related work
- **Low** — Hygiene / optional

## Evidence hygiene

Separate explicitly:

1. **Facts** — observed in repo, data, or logs
2. **Inferences** — reasoned from facts
3. **Recommendations** — proposed actions

Do not invent precision. Mark unknowns and what to instrument.

## Design bias

Prefer deleting unjustified complexity. New services, layers, or tools must clearly reduce CTQ risk or COPQ.

## Skill ownership (avoid overlap)

| Skill | Owns |
|-------|------|
| `ctq-charter` | Problem framing, charter, CTQ candidates |
| `measurement-system` | Metric validity, instrumentation |
| `six-sigma-master-black-belt` | Architecture-level DMAIC audit |
| `incident-rca` | Incident / recurring defect causal analysis |
| `eng-value-stream` | Idea→prod delivery flow and process waste |
| `dfss-system-design` | Greenfield / major forward design from CTQs |
| `design-fmea` | Deep failure-mode workbook |
| `controlled-experiment` | Hypothesis tests and rollout decision rules |
| `control-plan` | Hold-the-gains matrix (fitness, owners, reaction) |
| `a3-kaizen` | Small-scope one-page problem solving |
