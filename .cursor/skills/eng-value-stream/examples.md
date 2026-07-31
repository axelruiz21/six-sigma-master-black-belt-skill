# Eng Value Stream — examples

## Feature lead time

**Steps:** idea → backlog → design review → code → PR wait → QA env → prod.

**Findings:** 70% wait in PR review queue; QA env shared (inventory + waiting);
design review after code (rework).

**Future:** review-with-code in same PR; ephemeral preview envs; WIP limit on
review.

**Escalate to MBB** if “many repos per feature” is the dominant motion waste.
