# Control Plan — examples

## After modularizing checkout

| What | How measured | Who | Reaction |
|------|--------------|-----|----------|
| No sync calls from checkout→pricing | CI import/arch unit | platform | Fail PR |
| Purchase success ≥99% | SLO burn alert | checkout on-call | Page; feature-flag old path |
| Single writer for Order | Contract test + CODEOWNERS | payments lead | Block merge on second writer |
