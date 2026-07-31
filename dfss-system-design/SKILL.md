---
name: dfss-system-design
description: >-
  Design for Six Sigma for greenfield or major redesigns: CTQ-to-function
  mapping (QFD-lite), concept selection, and robust interface design from first
  principles. Use when designing a new system, writing a greenfield ADR,
  rebuilding vs evolving, or designing from CTQs—not for as-is architecture audits.
---

# DFSS System Design

Forward design from CTQs. Complement to `six-sigma-master-black-belt` (as-is
audit). Start from `ctq-charter` if CTQs are unclear. After concept selection,
run `design-fmea` and optionally MBB review of the chosen shape.

## Workflow

```
DFSS progress:
- [ ] CTQs and constraints
- [ ] CTQ → function matrix (QFD-lite)
- [ ] 2–3 concepts
- [ ] Concept score vs CTQs
- [ ] Selected design + rationale
- [ ] Next: FMEA / Control
```

1. Lock CTQs, constraints (team, compliance, scale, latency), non-goals.
2. Map CTQs to required system functions / interfaces.
3. Generate **2–3** concepts (including a deliberately simple co-located option).
4. Score concepts against CTQs and distribution-tax criteria (scale, failure
   domain, deploy ownership, compliance — need ≥1 to split).
5. Select; name invariants and sources of record.
6. Hand off to `design-fmea` then `control-plan`.

## Escalate when

- Auditing an existing system → `six-sigma-master-black-belt`
- CTQs undefined → `ctq-charter`
- Deep failure modes → `design-fmea`

## Output template

```markdown
# DFSS Design — [System]

## CTQs & constraints
## CTQ → function matrix
| CTQ | Functions / interfaces that must exist |
|-----|----------------------------------------|

## Concepts
### Concept A — [name]
### Concept B — [name]
### Concept C — [name] (often: simplest)

## Scorecard
| CTQ / criterion | A | B | C |
|-----------------|---|---|---|

## Selected design
[Structure, boundaries, SoR, why]

## Explicitly rejected complexity
[What we will not build]

## Next steps
[design-fmea | control-plan | MBB review]
```
