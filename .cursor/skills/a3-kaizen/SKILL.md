---
name: a3-kaizen
description: >-
  Runs small-scope A3 / kaizen problem-solving for a single local pain point:
  background, current state, goal, analysis, countermeasures, and follow-up.
  Use when fixing one team or code-area issue, running a kaizen, writing an A3,
  or when a full architecture audit would be oversized.
---

# A3 Kaizen

One-page problem-solving for **local** issues. If analysis shows systemic
coupling, multiple bounded contexts, or unjustified distribution, **stop** and
hand off to `six-sigma-master-black-belt`.

## Workflow

```
A3 progress:
- [ ] Background & problem
- [ ] Current state (facts)
- [ ] Goal / target
- [ ] Analysis (root cause)
- [ ] Countermeasures
- [ ] Follow-up / Control
```

1. Bound to one pain point and one owner.
2. Capture current state with evidence (not opinions).
3. Set a measurable goal tied to a CTQ or local Y.
4. Analyze with 5-Why or simple fishbone; stop at actionable cause.
5. Propose few countermeasures; prefer delete/simplify.
6. Define follow-up checks; hand lasting controls to `control-plan` if needed.

## Escalate when

- Structural / cross-system → `six-sigma-master-black-belt`
- Incident-shaped with severity → `incident-rca`
- Need formal control matrix → `control-plan`

## Output template

```markdown
# A3 — [Title]

## 1. Background
## 2. Current state
[Facts; metrics if any]
## 3. Goal
[Operational target]
## 4. Analysis
[Root cause; 5-Why chain]
## 5. Countermeasures
| Action | Owner | When | Expected effect |
|--------|-------|------|-----------------|
## 6. Follow-up
[How we’ll know it worked; next review date]

## Escalation
[None | hand off to …]
```
