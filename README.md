# Six Sigma MBB Skill Suite

Cursor Agent Skills for **software-systems excellence**: Master Black Belt architecture audits plus adjacent skills that own charter, measurement, RCA, value stream, DFSS, FMEA, experiments, control plans, and kaizen.

Anchor skill: **architecture-level DMAIC** with first-principles checks. Suite map and handoffs: [SUITE.md](SUITE.md). Shared terms: [shared/vocabulary.md](shared/vocabulary.md).

## Skills

| Folder | Role |
|--------|------|
| `six-sigma-master-black-belt` | Architecture DMAIC audit |
| `ctq-charter` | Problem framing and project charter |
| `measurement-system` | Metric validity / instrumentation (MSA) |
| `incident-rca` | Incident and recurring-defect root cause |
| `eng-value-stream` | Engineering delivery value-stream map |
| `dfss-system-design` | Design for Six Sigma (greenfield / redesign) |
| `design-fmea` | Design/process FMEA workbook |
| `controlled-experiment` | Hypothesis tests and rollout rules |
| `control-plan` | Hold-the-gains control plan |
| `a3-kaizen` | Small-scope A3 / kaizen |

## Install all (personal)

```bash
git clone https://github.com/axelruiz21/six-sigma-master-black-belt-skill.git
cd six-sigma-master-black-belt-skill
mkdir -p ~/.cursor/skills
for d in six-sigma-master-black-belt ctq-charter measurement-system incident-rca \
  eng-value-stream dfss-system-design design-fmea controlled-experiment \
  control-plan a3-kaizen; do
  cp -R "$d" ~/.cursor/skills/
done
```

## Install all (project)

From this repo root (or after clone):

```bash
mkdir -p .cursor/skills
for d in six-sigma-master-black-belt ctq-charter measurement-system incident-rca \
  eng-value-stream dfss-system-design design-fmea controlled-experiment \
  control-plan a3-kaizen; do
  cp -R "$d" .cursor/skills/
done
```

## Install one

```bash
mkdir -p ~/.cursor/skills   # or .cursor/skills for project-only
cp -R six-sigma-master-black-belt ~/.cursor/skills/
```

Restart or refresh Cursor agents after installing.

## When skills auto-invoke

Each skill’s description uses **distinct** trigger language (see [SUITE.md](SUITE.md)). Invoke explicitly when needed, e.g. *“Use ctq-charter, then six-sigma-master-black-belt.”*

## License

Use and adapt freely for your teams and repos.
