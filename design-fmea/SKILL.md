---
name: design-fmea
description: >-
  Produces a ranked design or process FMEA for software boundaries and features:
  failure modes, effects on CTQs, severity/occurrence/detection, RPN, and
  mitigations. Use for reliability reviews, launch readiness, pre-mortems,
  “what can go wrong?”, or deepening failure analysis after an architecture audit.
---

# Design FMEA

Deep failure-mode workbook for a **bounded** feature, interface, or service.
Not a full architecture audit (`six-sigma-master-black-belt`) and not a
postmortem of a past incident (`incident-rca`).

## Workflow

```
FMEA progress:
- [ ] Scope boundary + CTQs
- [ ] Functions / steps
- [ ] Failure modes + effects
- [ ] S / O / D scores + RPN
- [ ] Actions (prevent / detect)
```

1. Name the scope and CTQs at risk.
2. List functions or process steps.
3. For each: failure mode → effect on CTQ → cause → current controls.
4. Score Severity, Occurrence, Detection (1–10). RPN = S×O×D.
5. Rank by RPN; propose actions that cut S, O, or improve D.
6. Hand top detections/reactions to `control-plan`.

### Scoring guidance (software)

| Score band | Severity | Occurrence | Detection |
|------------|----------|------------|-----------|
| 9–10 | Data loss, safety, major $ | Likely under normal load | Blind / no signal |
| 6–8 | SLO breach, customer-visible | Occasional | Weak alerts / delayed |
| 3–5 | Degraded UX | Rare | Partial tests/metrics |
| 1–2 | Minor | Unlikely | Strong automated detect |

## Escalate when

- Scope is whole-platform structure → MBB first
- Past incident causal chain → `incident-rca`
- Lock mitigations in ops → `control-plan`

## Output template

```markdown
# FMEA — [Scope]

## CTQs in scope
## Ranked failure modes
| Item | Failure mode | Effect | S | Cause | O | Controls | D | RPN | Action |
|------|--------------|--------|---|-------|---|----------|---|-----|--------|

## Top actions
| RPN | Action | Prevent/Detect | Owner | → Control plan? |
|-----|--------|----------------|-------|-----------------|

## Residual risk
[What remains accepted]
```
