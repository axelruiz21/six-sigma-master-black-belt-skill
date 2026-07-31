---
name: measurement-system
description: >-
  Validates software metrics and instrumentation for decision-making (MSA-style):
  operational definitions, bias, lag, coverage, gaming risk, and instrumentation
  backlogs. Use when asking if metrics are trustworthy, designing SLOs or
  dashboards, closing Measure-phase gaps, or before running experiments.
---

# Measurement System (Software MSA)

Ensure metrics can support decisions. Do **not** redesign architecture (MBB) or
design the experiment protocol (`controlled-experiment`) until metrics are fit.

## Workflow

```
MSA progress:
- [ ] CTQs → candidate metrics
- [ ] Operational definitions
- [ ] MSA scorecard (bias, lag, coverage, gaming)
- [ ] Instrumentation backlog
```

1. Map each CTQ to 1–3 candidate metrics.
2. Write operational definitions (numerator, denominator, window, filters).
3. Score each metric:

| Dimension | Question |
|-----------|----------|
| Bias | Does it systematically misstate truth? |
| Lag | Too late for the decision? |
| Coverage | Does it see the failure modes that matter? |
| Stability | Sensitive to noise / deploy artifacts? |
| Gaming | Easy to improve without moving Y? |
| Cost | Expensive to collect vs value? |

4. Mark **fit / fit-with-caveats / unfit**. Replace unfit metrics.
5. Produce an instrumentation backlog for unknowns.

## Escalate when

- Need experiment design → `controlled-experiment`
- Structural causes dominate → `six-sigma-master-black-belt`
- Charter/CTQs missing → `ctq-charter`

## Output template

```markdown
# Measurement System Review — [Area]

## CTQ → metric map
| CTQ | Metric | Op definition | Fit | Caveats |
|-----|--------|---------------|-----|---------|

## MSA scorecard
| Metric | Bias | Lag | Coverage | Gaming | Verdict |
|--------|------|-----|----------|--------|---------|

## Instrumentation backlog
| Gap | Signal to add | Owner | Priority |
|-----|---------------|-------|----------|

## Decision readiness
[What decisions these metrics can / cannot support yet]
```
