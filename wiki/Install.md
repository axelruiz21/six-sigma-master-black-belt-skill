# Install

Clone:

```bash
git clone https://github.com/axelruiz21/six-sigma-master-black-belt-skill.git
cd six-sigma-master-black-belt-skill
```

## Install all (personal — every project)

```bash
mkdir -p ~/.cursor/skills
for d in six-sigma-master-black-belt ctq-charter measurement-system incident-rca \
  eng-value-stream dfss-system-design design-fmea controlled-experiment \
  control-plan a3-kaizen; do
  cp -R "$d" ~/.cursor/skills/
done
```

## Install all (this project only)

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
mkdir -p ~/.cursor/skills   # or .cursor/skills
cp -R six-sigma-master-black-belt ~/.cursor/skills/
```

Restart or refresh Cursor agents after installing so skills are discovered.

Invoke explicitly when needed, e.g. *“Use ctq-charter, then six-sigma-master-black-belt.”*
