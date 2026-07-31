---
name: control-plan
description: >-
  Builds hold-the-gains control plans for software systems: architectural
  fitness functions, alerts, owners, review gates, reaction plans, and rollback.
  Use when locking in improvements after a refactor, launch control plans,
  preventing regression, defining fitness functions, or operationalizing the
  Control phase of DMAIC.
---

# Control Plan

Turn Improve recommendations into lasting Control. Do **not** re-derive the
architecture verdict (use `six-sigma-master-black-belt`) or deep FMEA (use
`design-fmea` first if failure modes are unknown).

## Workflow

```
Control progress:
- [ ] CTQs and Xs to protect
- [ ] Controls matrix (detect / prevent)
- [ ] Owners and reaction plans
- [ ] Fitness functions / gates
- [ ] Rollback / escape hatch
```

1. List CTQs and the Xs the change was meant to move.
2. For each risk of regression, define **prevention** and **detection**.
3. Assign **owner**, review cadence, and **reaction plan** (what to do if red).
4. Prefer automated fitness functions (import lint, contract tests, SLO burn).
5. Define rollback / feature-flag escape if Control fails.

## Escalate when

- Failure modes not ranked → `design-fmea`
- Metrics untrustworthy → `measurement-system`
- Need experiment to set thresholds → `controlled-experiment`
- Regression is structural debt → `six-sigma-master-black-belt`

## Output template

```markdown
# Control Plan — [System / Change]

## Purpose
[What gain we are holding; link to CTQs]

## Controls matrix
| What (CTQ/X or invariant) | How measured | Frequency | Who | Reaction if red | Severity |
|---------------------------|--------------|-----------|-----|-----------------|----------|

## Fitness functions & gates
- [ ] …
CI / review gates: …

## Rollback / escape
[How to undo; timebox]

## Review cadence
[When to revisit thresholds]

## Open gaps
[What is still manual or unmeasured]
```
