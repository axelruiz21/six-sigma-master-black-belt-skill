---
name: incident-rca
description: >-
  Performs operational root-cause analysis for incidents and recurring defects
  using causal chains, 5-Why, and fishbone—corrective vs preventive actions.
  Use for postmortems, SEV reviews, defect escape analysis, or “why does this
  keep happening?”—not for full architecture redesign.
---

# Incident RCA

Deep Analyze for **incidents and recurring defects**. If the root cause is
structural (wrong boundaries, systemic coupling), escalate to
`six-sigma-master-black-belt`. Local fixes → `a3-kaizen` or `control-plan`.

## Workflow

```
RCA progress:
- [ ] Timeline & impact (facts)
- [ ] CTQs / customer impact
- [ ] Causal chain (5-Why)
- [ ] Contributing factors
- [ ] Corrective vs preventive
- [ ] Escalation decision
```

1. Build a factual timeline (detect → mitigate → recover).
2. Quantify impact against CTQs where possible.
3. Causal chain until a controllable cause (people/process/tech/design).
4. Separate **corrective** (this instance) from **preventive** (class of defect).
5. Decide: local Control, kaizen, or structural MBB audit.

Blameless on individuals; ruthless on missing controls and incentives.

## Escalate when

- Systemic architecture → `six-sigma-master-black-belt`
- Need ranked design failure modes → `design-fmea`
- Hold gains → `control-plan`
- Small process tweak → `a3-kaizen`

## Output template

```markdown
# RCA — [Incident / Defect theme]

## Summary
[One paragraph]

## Impact
| CTQ / user effect | Magnitude | Window |
|-------------------|-----------|--------|

## Timeline
| Time | Event | Evidence |
|------|-------|----------|

## Causal chain
1. …
5. **Root cause:** …

## Contributing factors
- …

## Actions
| Type (C/P) | Action | Owner | Due | Severity |
|------------|--------|-------|-----|----------|

## Escalation
[None | a3-kaizen | control-plan | six-sigma-master-black-belt | design-fmea]
```
