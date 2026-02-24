# Routing Policy

The router is the component that selects the correct AI role based on the active mode. It connects mode declarations to system prompts, permissions, and gating rules.

## Routing Table

```
Mode Selection → Prompt Loading → Gate Enforcement → Execution
```

| Step | Input | Output |
|------|-------|--------|
| 1. Mode select | Human declares mode | `active_mode` set in state |
| 2. Prompt load | `active_mode` value | System prompt from `.cbus/prompts/{mode}.md` |
| 3. Context inject | `state.yaml` | Snapshot prepended to conversation |
| 4. Gate enforce | Mode's gate rules | Gate output required before action |
| 5. Execute | Approved gate output | AI performs the task within role constraints |
| 6. State update | Execution result | `state.yaml` updated with outcomes |

## Route Resolution

The router resolves in this order:

1. **Explicit mode** — Human specifies mode directly (e.g., `cbus think ...`)
2. **State mode** — Falls back to `active_mode` in `state.yaml`
3. **Default mode** — If no mode is set, defaults to `THINK` (safest)

Default to THINK ensures the system never executes without analysis first.

## Prompt Resolution

Prompts are loaded from `.cbus/prompts/` in this order:

1. **Project-level** — `./cbus/prompts/{mode}.md` (project-specific)
2. **User-level** — `~/.cbus/prompts/{mode}.md` (global defaults)
3. **Built-in** — Hardcoded fallback prompts (minimal, functional)

Project-level prompts override user-level, which override built-in.

## Context Injection

Before routing to the AI, the router:

1. Reads `state.yaml`
2. Generates a snapshot (see [03-context-schema](03-context-schema.md))
3. Prepends the snapshot to the system prompt
4. Sends the combined prompt + user input to the AI

This ensures every interaction has full context without manual copy-paste.

## Multi-Mode Sessions

Within a single session, mode can be switched:

```
cbus think "Should I use Redis or in-memory cache?"
  → (decision made, state updated)
cbus build "Implement the in-memory cache"
  → (reads the decision from state, builds accordingly)
```

Each switch re-runs the routing pipeline: new prompt, new gate, new context snapshot.
