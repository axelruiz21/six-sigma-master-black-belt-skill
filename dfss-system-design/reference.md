# DFSS — reference

## Distribution tax (must earn a split)

Before a new process/service/region, confirm at least one:

- Independent scale or resource profile
- Independent failure domain required by CTQ
- Independent deploy/ownership cadence
- Compliance / data residency boundary

## QFD-lite tips

- Rows = CTQs; columns = functions/modules
- Strong / medium / weak relationship is enough — avoid fake precision
- Empty CTQ rows = design hole; empty columns = candidate deletion

## Concept selection bias

Always include a **modular monolith / few-process** concept unless a hard
constraint forbids it. Complexity must pay rent in CTQs.
