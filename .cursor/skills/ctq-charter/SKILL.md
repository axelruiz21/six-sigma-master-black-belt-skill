---
name: ctq-charter
description: >-
  Frames vague improvement asks into a Black Belt–ready project charter with
  problem statement, SIPOC sketch, CTQ candidates (Y=f(X)), scope, stakeholders,
  success criteria, and tollgates. Use when writing a project charter, defining
  CTQs, kickoff or intake, clarifying the real problem, or scoping a Six Sigma
  / improvement project before architecture work.
---

# CTQ Charter

Produce a one-page charter. Do **not** run a full architecture audit (hand off
to `six-sigma-master-black-belt`) or greenfield design (hand off to
`dfss-system-design`).

Shared terms: suite `shared/vocabulary.md` when present.

## Workflow

```
Charter progress:
- [ ] Problem statement (VOC)
- [ ] SIPOC sketch
- [ ] CTQ candidates + operational definitions
- [ ] Scope in/out + stakeholders
- [ ] Success criteria + tollgates
- [ ] Assumption log
```

1. Restate the ask as a **business/user problem** (no technology in the sentence).
2. Minimal **SIPOC**: Suppliers → Inputs → Process → Outputs → Customers.
3. Propose 2–5 **CTQs** with operational definitions and direction (↑/↓/target).
4. List primary **Xs** believed to drive each Y (hypotheses, not proven).
5. **In scope / out of scope**; name sponsor, process owner, team.
6. **Success criteria** and Define/Measure/Analyze/Improve/Control tollgates.
7. **Assumptions**: validated / unverified / likely false.

## Escalate when

- User wants structural redesign verdict → `six-sigma-master-black-belt`
- Greenfield from CTQs → `dfss-system-design`
- Metrics need validation → `measurement-system`

## Output template

```markdown
# Project Charter — [Name]

## Problem statement
[One sentence; no tech]

## Business case (brief)
[Why now; COPQ or opportunity]

## SIPOC (sketch)
| S | I | P | O | C |
|---|---|---|---|---|

## CTQs (Y)
| CTQ | Operational definition | Direction | Baseline | Target |
|-----|------------------------|-----------|----------|--------|

## Suspected Xs
| CTQ | Suspected drivers (X) | Notes |
|-----|----------------------|-------|

## Scope
**In:** …
**Out:** …

## Stakeholders
| Role | Person/team | Interest |
|------|-------------|----------|

## Success criteria & tollgates
| Gate | Exit criteria |
|------|---------------|

## Assumption log
| Assumption | Status | Risk if wrong |
|------------|--------|---------------|

## Recommended next skill
[mbb audit | dfss | measurement-system | …]
```
