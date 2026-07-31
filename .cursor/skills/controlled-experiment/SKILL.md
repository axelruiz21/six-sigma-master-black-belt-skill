---
name: controlled-experiment
description: >-
  Designs controlled experiments for product or system changes: hypotheses,
  A/B canary holdback or before/after protocols, success and guardrail metrics,
  and ship/stop decision rules. Use for experiment design, feature-flag
  rollouts, validating Improve changes, or asking whether a fix worked.
---

# Controlled Experiment

Statistical thinking for Improve validation — without fake precision. Require
fit metrics from `measurement-system` (or run that skill first). Results feed
`control-plan` thresholds.

## Workflow

```
Experiment progress:
- [ ] Hypothesis tied to CTQ / X
- [ ] Design (A/B, canary, holdback, before/after)
- [ ] Success + guardrail metrics
- [ ] Sample / duration / stop rules
- [ ] Ship / iterate / revert decision rules
```

1. State hypothesis: changing X moves Y by about Δ (direction matters more than
   false precision).
2. Choose design:
   - **A/B** — user/request split
   - **Canary** — progressive exposure
   - **Holdback** — keep baseline cohort
   - **Before/after** — only if no concurrent confounders (call risks out)
3. Success metrics (move Y) and **guardrails** (must not worsen).
4. Precommit: min runtime, peeking policy, abort conditions.
5. Decision table: ship / iterate / revert.

Do not claim significance you cannot support; prefer practical decision rules
tied to CTQs and error budgets.

## Escalate when

- Metrics unfit → `measurement-system`
- Lock winning config → `control-plan`
- Change is structural and untested in design → MBB / `design-fmea` first

## Output template

```markdown
# Experiment — [Name]

## Hypothesis
[If we change X, Y moves … because …]

## Design
| Type | Unit of split | Exposure plan | Duration |
|------|---------------|---------------|----------|

## Metrics
| Role | Metric | Op definition | Threshold |
|------|--------|---------------|-----------|
| Success | | | |
| Guardrail | | | |

## Stop / ship rules
| Condition | Action |
|-----------|--------|

## Risks & confounds
## Post-decision Control
[What enters control-plan if we ship]
```
