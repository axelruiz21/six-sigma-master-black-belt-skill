---
name: eng-value-stream
description: >-
  Maps engineering and delivery value streams from idea to production, finds
  Lean waste (wait, batch, handoff, rework), and proposes flow experiments. Use
  when lead time is high, PRs are slow, deployment frequency suffers, process
  waste is suspected, or team topology friction blocks flow.
---

# Engineering Value Stream

Lean map of **idea → production**. If the bottleneck is structural coupling in
the codebase/platform, escalate to `six-sigma-master-black-belt`. Process-only
fixes close with `control-plan` or `a3-kaizen`.

## Workflow

```
VSM progress:
- [ ] Select value stream & CTQs (flow)
- [ ] Current-state steps + wait/touch time
- [ ] Waste table
- [ ] Future-state sketch
- [ ] Flow experiments
```

1. Pick one value stream (e.g. “vertical feature to prod”).
2. Flow CTQs: lead time, deploy frequency, change fail rate, rework %.
3. Map steps with queue/wait vs active time; note handoffs and batch sizes.
4. Classify waste (waiting, transport, over-processing, inventory, defects…).
5. Future state: fewer handoffs, smaller batches, faster feedback.
6. Propose 1–3 flow experiments; validate metrics via `measurement-system` if weak.

## Escalate when

- Code/module coupling is the constraint → MBB
- Local team pain only → `a3-kaizen`
- Hold process gains → `control-plan`

## Output template

```markdown
# Value Stream — [Name]

## Flow CTQs
| CTQ | Definition | Baseline | Target |
|-----|------------|----------|--------|

## Current state
| Step | Actor | Touch time | Wait time | Exit criteria |
|------|-------|------------|-----------|---------------|

## Waste table
| Waste type | Where | Effect on CTQ | Severity |
|------------|-------|---------------|----------|

## Future state (sketch)
## Flow experiments
| Experiment | Hypothesis | Measure | Owner |
|------------|------------|---------|-------|

## Escalation
[None | MBB | control-plan | a3-kaizen]
```
