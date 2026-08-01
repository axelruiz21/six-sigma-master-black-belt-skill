# Handoffs

Use the smallest skill that fits. Escalate to `six-sigma-master-black-belt` only when structure is the constraint.

## When to use which

| Need | Skill |
|------|-------|
| Vague problem / define CTQs | `ctq-charter` |
| Metrics untrusted / what to measure | `measurement-system` |
| Architecture / design review | `six-sigma-master-black-belt` |
| Incident / recurring defect | `incident-rca` |
| Slow PRs / lead time / process waste | `eng-value-stream` |
| Greenfield from CTQs | `dfss-system-design` |
| Launch readiness / what can go wrong | `design-fmea` |
| Did the fix work? | `controlled-experiment` |
| Prevent regression | `control-plan` |
| One local pain point | `a3-kaizen` |

## Typical paths

1. **Audit:** `ctq-charter` → `six-sigma-master-black-belt` → `design-fmea` → `control-plan`
2. **Incident:** `incident-rca` → MBB (if structural) or `a3-kaizen` → `control-plan`
3. **Greenfield:** `ctq-charter` → `dfss-system-design` → `design-fmea` → `control-plan`
4. **Validate Improve:** `measurement-system` → `controlled-experiment` → `control-plan`
5. **Flow:** `eng-value-stream` → MBB (if structure) or `control-plan`

Full map: [`SUITE.md`](https://github.com/axelruiz21/six-sigma-master-black-belt-skill/blob/main/SUITE.md).
