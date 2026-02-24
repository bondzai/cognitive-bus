# Cognitive Bus

A personal AI orchestration framework that routes your thinking through specialized modes — each with distinct roles, constraints, and behaviors.

## What It Does

Instead of treating AI as a single generalist, Cognitive Bus splits interactions into four **modes**, each with a dedicated **role**:

| Mode | Role | What It Does |
|------|------|-------------|
| `THINK` | critic | Analyze, challenge assumptions, make decisions |
| `BUILD` | builder | Implement, write code, ship artifacts |
| `LEARN` | tutor | Explain concepts, fill knowledge gaps |
| `OPERATE` | operator | Monitor, triage, maintain systems |

Key mechanics:
- **Human-first gating** — AI must critique/analyze before acting
- **Persistent context** — `state.yaml` carries your goals, decisions, and blockers across sessions
- **Reflection loops** — Built-in scorecard system to improve how you think
- **Security by separation** — Reasoning and execution are distinct permission layers

## Quick Start (Stage 1: Files)

No installation required. The framework works with flat files today.

```bash
# 1. Clone
git clone https://github.com/bondzai/cognitive-bus.git
cd cognitive-bus

# 2. Create your state file
cp docs/examples/state.yaml ./state.yaml  # or create from schema

# 3. Create mode prompts
mkdir -p .cbus/prompts
# Write think.md, build.md, learn.md, operate.md

# 4. Generate a snapshot and paste into your AI tool
# (See docs/cognitive-bus/03-context-schema.md)
```

## Documentation

| Doc | Description |
|-----|-------------|
| [00-overview](docs/cognitive-bus/00-overview.md) | Architecture and design goals |
| [01-principles](docs/cognitive-bus/01-principles.md) | Core principles governing all decisions |
| [02-modes-and-roles](docs/cognitive-bus/02-modes-and-roles.md) | Detailed mode definitions and behaviors |
| [03-context-schema](docs/cognitive-bus/03-context-schema.md) | state.yaml schema and snapshot format |
| [04-human-first-gating](docs/cognitive-bus/04-human-first-gating.md) | Gate rules and enforcement |
| [05-routing-policy](docs/cognitive-bus/05-routing-policy.md) | How modes route to prompts and permissions |
| [06-reflection-and-scorecard](docs/cognitive-bus/06-reflection-and-scorecard.md) | Feedback loops and scoring |
| [07-daily-workflow](docs/cognitive-bus/07-daily-workflow.md) | Plan → Think → Build → Reflect cycle |
| [08-claude-cli-integration](docs/cognitive-bus/08-claude-cli-integration.md) | Integration with Claude Code CLI |
| [09-security-and-permissions](docs/cognitive-bus/09-security-and-permissions.md) | Permission model and security layers |
| [10-roadmap-openclaw](docs/cognitive-bus/10-roadmap-openclaw.md) | Files → CLI → Service → OpenClaw runtime |
| [11-intelligent-friction](docs/cognitive-bus/11-intelligent-friction.md) | AI as gym spotter, not wheelchair (theMITmonk) |

## Roadmap

1. **Files** (current) — Flat files, zero dependencies
2. **CLI** — `cbus` command-line tool
3. **Service** — Local HTTP service with dashboard
4. **OpenClaw** — Portable runtime for cognitive workflows

## License

MIT
