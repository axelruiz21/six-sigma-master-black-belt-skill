# Measurement System — reference

## Good operational definition pattern

`metric = count(events matching filter) / count(eligible opportunities)`  
in window `W`, excluding `E`, attributed by `A`.

Example: *Purchase success = orders with status=paid within 15m of checkout_start,
excluding synthetic traffic, per checkout_id.*

## Common software metric failures

| Failure | Example |
|---------|---------|
| Proxy drift | “Deploy count” as quality |
| Availability theater | 99.99% excluding the error budget burn path |
| Open denominators | Error rate without traffic filter |
| Vanity | Lines of code, story points as outcomes |
| Lagging only | Monthly NPS for weekly control |

## Before/after measurement

Prefer same operational definition pre/post. If definition changes midstream,
treat as a new metric — do not compare naively.
