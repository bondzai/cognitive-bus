# Overview

Cognitive Bus is a personal AI orchestration framework that routes your thinking through specialized AI modes — each with distinct roles, constraints, and behaviors.

## Problem

Most AI interactions are modeless: you get the same generalist response whether you're debugging, brainstorming, learning, or operating production systems. This leads to:

- AI jumping to solutions before understanding the problem
- No separation between reasoning and execution
- Lost context between sessions
- No feedback loop on how effectively you're using AI

## Solution

Cognitive Bus introduces **mode-aware AI routing** with four core modes:

| Mode | Role | Purpose |
|------|------|---------|
| `THINK` | critic | Analyze, challenge, decide |
| `BUILD` | builder | Execute, implement, ship |
| `LEARN` | tutor | Explain, teach, fill knowledge gaps |
| `OPERATE` | operator | Monitor, triage, maintain |

Each mode loads a different system prompt, enforces different gating rules, and writes to a shared state file (`state.yaml`) that persists context across sessions.

## Architecture

```
    ┌─────────────────────────────────────────────┐
    │             HUMAN (decisions + judgment)      │
    └──────────┬──────────────────────┬────────────┘
               │                      │
          state.yaml             mode switch
               │                      │
    ┌──────────▼──────────────────────▼────────────┐
    │              COGNITIVE BUS                    │
    │                                               │
    │  ┌───────┐ ┌───────┐ ┌───────┐ ┌──────────┐  │
    │  │ THINK │ │ BUILD │ │ LEARN │ │ OPERATE  │  │
    │  │critic │ │builder│ │ tutor │ │ operator │  │
    │  └──┬────┘ └──┬────┘ └──┬────┘ └────┬─────┘  │
    │     └─────────┴────┬────┴────────────┘        │
    │                    │                          │
    │            gate → execute → reflect            │
    │                              │                │
    │                        scorecard → state       │
    └───────────────────────────────────────────────┘
```

## Design Goals

1. **Human controls the mode, AI adapts** — never the reverse
2. **Context survives sessions** — state.yaml is the source of truth
3. **Critique is mandatory** — gating prevents blind execution
4. **Reflection is built-in** — you improve how you think, not just what you build
5. **Portable** — works with any AI backend (Claude, GPT, local models)
