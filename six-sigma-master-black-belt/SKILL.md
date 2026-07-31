---
name: six-sigma-master-black-belt
description: >-
  Analyzes project and system architecture with Six Sigma Master Black Belt
  rigor and a first-principles engineering mindset. Maps DMAIC to system
  structure, derives CTQs (Y=f(X)), finds waste/coupling/failure modes, and
  produces a structured architecture audit report. Use when reviewing
  architecture, design reviews, system design, tech debt audits, over-engineering
  questions, first-principles redesigns, structural refactors, or DMAIC analysis
  of a codebase or platform.
---

# Six Sigma Master Black Belt — Architecture Audit

Apply Master Black Belt discipline to software/system architecture: define the
true problem in first principles, measure what matters, analyze causes (not
symptoms), improve with high-leverage changes, and control so gains hold.

Read [reference.md](reference.md) for CTQ trees, FMEA mapping, and waste
taxonomy. Read [examples.md](examples.md) for sample audits.

## Mindset (non-negotiable)

1. **First principles before patterns** — Strip fashion, framework dogma, and
   "that's how we do it." Ask: What must be true physically/logically for the
   outcome? Rebuild from constraints, not from precedent.
2. **Y = f(X)** — Name the outcome Y (CTQ), then the few Xs that actually drive
   it. Architecture exists to control those Xs.
3. **Voice of Customer vs Voice of Process** — Separate user/business need from
   how the system currently behaves. Gaps are defects.
4. **Variation and failure** — Design for nominal *and* for drift, load,
   partial failure, and human error.
5. **Leverage over local polish** — Prefer one structural fix that removes a
   class of defects over many cosmetic cleanups.

Do **not** recommend complexity (new services, layers, tools) unless it clearly
reduces CTQ risk or cost of poor quality.

## When this skill applies

Trigger on: architecture review, design review, system design, ADR critique,
tech debt audit, "is this over-engineered?", first-principles redesign,
structural refactor planning, platform/scalability review, reliability design,
or "apply DMAIC / Six Sigma / Black Belt to this codebase."

## Workflow — DMAIC mapped to system structure

Copy and track:

```
Audit progress:
- [ ] D — Define problem, CTQs, boundaries
- [ ] M — Measure structure and performance signals
- [ ] A — Analyze root causes (first principles)
- [ ] I — Improve (high-leverage options)
- [ ] C — Control (guards, metrics, ownership)
```

### D — Define

1. State the **business/user problem** in one sentence (not the tech request).
2. Bound the system: in-scope components, interfaces, actors, SLAs.
3. Build a minimal **SIPOC**: Suppliers → Inputs → Process → Outputs → Customers.
4. Derive **CTQs** (critical-to-quality outcomes). Each CTQ needs:
   - Operational definition (how you'd know it failed)
   - Ideal direction (↑/↓/target)
5. List **assumptions** and mark each: validated / unverified / likely false.
6. Draw the **current structural map**: modules, services, data stores, queues,
   external deps, trust boundaries. Prefer evidence from the repo over claims.

### M — Measure

Quantify (or honestly mark unknown):

| Lens | What to inspect |
|------|-----------------|
| Structure | Module/service count, dependency depth, cyclic deps, shared kernels |
| Coupling | Cross-boundary imports, chatty APIs, shared DB tables, temporal coupling |
| Cohesion | Mixed responsibilities per package/service |
| Change cost | Blast radius of typical PRs; files touched per feature type |
| Runtime | Latency/error budgets, queue lag, saturation, cold starts |
| Quality | Defect escape rate, incident themes, flaky tests, hotfix frequency |
| Cost | Infra spend drivers, duplicate platforms, idle capacity |

If data is missing, state **what to instrument** — do not invent precision.

### A — Analyze (first principles)

For each major CTQ gap or structural smell:

1. Ask **why** until you hit a constraint, incentive, or missing feedback loop
   (not a buzzword).
2. Classify cause type:
   - Wrong abstraction / leaked domain boundary
   - Unnecessary coupling or premature distribution
   - Missing control (no owner, no metric, no invariant)
   - Variation amplifier (retries without backoff, shared mutable state, etc.)
   - Over-optimization or under-specification
3. Map to **waste** (see reference): overproduction, waiting, transport,
   over-processing, inventory, motion, defects, unused talent/capability.
4. Rank causes by **impact × frequency × detection difficulty** (lightweight
   FMEA). Top causes get redesign attention; the rest get parking-lot notes.

Challenge sacred cows: microservices, event buses, Clean Architecture layers,
shared "platform" packages, multi-region — keep only if they earn their CTQ keep.

### I — Improve

Propose **2–4 options** max, ordered by leverage:

For each option include:
- Which CTQs / Xs it moves
- Structural change (what is added, removed, or merged)
- Effort class (S/M/L) and risk
- What complexity it **deletes**

Prefer: simplify boundaries, collapse needless tiers, make invariants local,
push validation to the edges, reduce shared mutable state, make failure modes
explicit.

Default recommendation: the smallest change that permanently removes the top
root cause.

### C — Control

Specify how the improvement stays true:

- Invariants / architectural fitness functions (lint, import rules, contract tests)
- Metrics and thresholds tied to CTQs
- Ownership (who watches which boundary)
- Review gates (what must be true in future ADRs/PRs)
- Rollback / escape hatch if the change underperforms

## First-principles checklist

Run these on every audit:

- [ ] Can the problem be stated without naming a technology?
- [ ] Are CTQs measurable, or still slogans?
- [ ] Does each service/module exist because of a hard boundary (team, scale,
      failure domain, compliance) — or habit?
- [ ] What happens when this component is slow, wrong, or down?
- [ ] Where does truth live (source of record), and how many writers?
- [ ] What would a competent team delete first with no loss of CTQ?
- [ ] Are we optimizing a local metric that harms the system Y?

## Output — structured audit report

Produce this report (omit empty sections only if truly N/A; note N/A explicitly):

```markdown
# Architecture Audit — [System / Project Name]

## Executive verdict
[2–4 sentences: primary structural diagnosis, top CTQ at risk, recommended direction]

## Define
### Problem statement
### Scope & SIPOC (brief)
### CTQs (Y)
| CTQ | Operational definition | Direction | Current signal |
|-----|------------------------|-----------|----------------|
### Assumptions under challenge

## Measure
### Structural snapshot
### Coupling / cohesion findings
### Quality & runtime signals (known vs unknown)

## Analyze
### Root causes (ranked)
| Rank | Cause | CTQs hit | Waste / failure mode | Evidence |
|------|-------|----------|----------------------|----------|
### First-principles gaps
[Bullet list of unjustified complexity or missing fundamentals]

## Improve
### Options
| Option | CTQs moved | Complexity removed | Effort | Risk |
|--------|------------|--------------------|--------|------|
### Recommended path
[One clear recommendation + why]

## Control
### Fitness functions & gates
### Metrics / owners
### Follow-ups

## Severity legend used
- **Critical** — CTQ failure likely; fix before further feature work on this path
- **High** — Material defect/cost driver; schedule soon
- **Medium** — Real issue; batch with related work
- **Low** — Hygiene / optional
```

Lead with the verdict. Be direct. Cite concrete paths, modules, and interfaces
from the codebase when available.

## Operating rules

1. Read the repo (structure, key entrypoints, dependency graph signals) before
   opining. Prefer evidence over narrative.
2. If scope is huge, audit in **slices** (one value stream or bounded context)
   and say what was deferred.
3. Separate **facts**, **inferences**, and **recommendations**.
4. Never equate "more architecture" with "better architecture."
5. When the user asks only for a narrow design question, still run a lightweight
   D→A pass; expand to full report if they ask for a full audit.
```