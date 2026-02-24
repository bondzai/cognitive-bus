# Context Schema

Context is the core infrastructure of Cognitive Bus. It flows through two layers: **state** (mutable, persistent) and **snapshots** (immutable, portable).

## state.yaml

The single source of truth. Lives at the project root or `~/.cbus/state.yaml` for global state.

### Schema

```yaml
# ── Identity ──────────────────────────────────
project: string            # Project name
phase: enum                # discovery | design | build | ship | maintain

# ── Current Focus ─────────────────────────────
current_goal: string       # One-line active objective
active_mode: enum          # THINK | BUILD | LEARN | OPERATE

# ── Decisions ─────────────────────────────────
decisions:
  - id: string             # Unique identifier (e.g., d-001)
    question: string       # What needs to be decided
    status: enum           # open | decided | revisit
    mode: enum             # Which mode owns this decision
    verdict: string|null   # The decision made (null if open)
    reasoning: string|null # Why this was decided
    date: date|null        # When decided

# ── Blockers ──────────────────────────────────
blockers:
  - string                 # Free-text blocker descriptions

# ── Reflections ───────────────────────────────
reflections:
  - date: date
    score: integer         # 1-10
    insight: string        # Key takeaway
    mode_distribution:     # Optional: time per mode
      THINK: float
      BUILD: float
      LEARN: float
      OPERATE: float

# ── Energy ────────────────────────────────────
energy: enum               # high | medium | low

# ── Custom Modes ──────────────────────────────
custom_modes: []           # See 02-modes-and-roles.md
```

### Rules

- `state.yaml` is read at the start of every session
- `state.yaml` is updated at the end of every reflection
- Fields are additive — new fields never break existing ones
- All fields except `project` are optional

## Snapshots

A snapshot is a **read-only, timestamped export** of state.yaml formatted for AI consumption. It is the context payload injected into any AI session.

### Format

```markdown
## Context Snapshot ({date})
- Project: {project}
- Phase: {phase}
- Mode: {active_mode}
- Goal: {current_goal}
- Open decisions: {count} ({list ids})
- Blockers: {count}
- Last reflection: {date} — score {score}/10
- Energy: {energy}
- Key insight: {latest reflection insight}
```

### Snapshot Rules

- Generated on demand (not stored permanently)
- Always derived from current `state.yaml` — never hand-edited
- Portable across AI backends (plain markdown)
- Snapshots may be archived for historical reference under `.cbus/snapshots/`

## Directory Structure

```
project-root/
├── state.yaml              # Project-level state
├── .cbus/
│   ├── snapshots/          # Archived snapshots (optional)
│   ├── prompts/            # Mode-specific system prompts
│   │   ├── think.md
│   │   ├── build.md
│   │   ├── learn.md
│   │   └── operate.md
│   └── reflections/        # Daily reflection logs
│       └── 2026-02-24.yaml
└── docs/
    └── cognitive-bus/      # This documentation
```
