# Six Sigma Master Black Belt Skill

A Cursor Agent Skill that audits **project and system architecture** with Master Black Belt rigor and a **first-principles engineering** mindset. It maps **DMAIC** onto structure (boundaries, coupling, failure domains, CTQs) and emits a **structured audit report**.

## What it does

- Defines the real problem, SIPOC, and CTQs (`Y = f(X)`) before debating tools
- Measures structural and runtime signals (or names what to instrument)
- Analyzes root causes with Lean waste, coupling types, and lightweight FMEA
- Recommends high-leverage improvements that **delete** unjustified complexity
- Specifies Control: fitness functions, metrics, and ownership

## Install

### Option A — Project skill (this repo / any repo)

Copy the skill folder into the project:

```bash
mkdir -p .cursor/skills
cp -R six-sigma-master-black-belt .cursor/skills/
```

### Option B — Personal skill (all projects)

```bash
mkdir -p ~/.cursor/skills
cp -R six-sigma-master-black-belt ~/.cursor/skills/
```

### Option C — Clone

```bash
git clone https://github.com/axelruiz21/six-sigma-master-black-belt-skill.git
cp -R six-sigma-master-black-belt-skill/six-sigma-master-black-belt ~/.cursor/skills/
```

Restart or refresh Cursor agents after installing so the skill is discovered.

## When it auto-invokes

The skill description is written to trigger on language like:

- architecture review / design review / system design
- tech debt audit / over-engineering
- first-principles redesign / structural refactor
- DMAIC / Six Sigma / Black Belt applied to a codebase

You can also invoke it explicitly: *“Use the six-sigma-master-black-belt skill to audit this system.”*

## Skill contents

```
six-sigma-master-black-belt/
├── SKILL.md       # Workflow, checklist, audit report template
├── reference.md   # CTQs, waste, coupling, FMEA, fitness functions
└── examples.md    # Sample audits
```

## Output

Audits follow a DMAIC-shaped report: **Executive verdict → Define → Measure → Analyze → Improve → Control**, with severity on structural risks.

## License

Use and adapt freely for your teams and repos.
```