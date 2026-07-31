# Design FMEA — examples

## Outbox publisher

| Failure mode | Effect | S | O | D | RPN | Action |
|--------------|--------|---|---|---|-----|--------|
| Poison message blocks partition | Checkout events stall | 9 | 4 | 6 | 216 | DLQ + alert on lag |
| Dual publish without idempotency key | Double charge risk | 10 | 3 | 5 | 150 | Idempotency key required in contract test |
| Clock skew skips due | Missed billing | 8 | 2 | 7 | 112 | Store absolute due_at; synthetic check |
