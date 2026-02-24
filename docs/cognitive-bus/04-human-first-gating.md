# Human-First Gating

Gating is the mechanism that prevents AI from jumping to solutions. Every mode has a **gate** — a required step the AI must complete before it can act.

## Why Gating Exists

Without gating, AI defaults to the most "helpful" response: an immediate answer. This is dangerous because:

- It skips problem analysis
- It anchors you on the first solution proposed
- It removes the human from the decision loop
- It creates a false sense of progress

Gating forces a **pause between stimulus and response** — the same discipline that separates good engineers from fast ones.

## Gate Rules by Mode

| Mode | Gate Requirement | Must Include |
|------|-----------------|--------------|
| THINK | Critique before recommending | Risks, assumptions, alternatives |
| BUILD | Scope before implementing | What changes, what could break |
| LEARN | Model before details | Mental model, then specifics |
| OPERATE | Assess before acting | Current state, risks of action |

## Gate Flow

```
  Input (question/task)
       │
       ▼
  ┌─────────────┐
  │  GATE CHECK  │  ← AI must produce gate output first
  │  (per mode)  │
  └──────┬──────┘
         │
         ▼
  ┌─────────────┐
  │  HUMAN      │  ← You review the gate output
  │  REVIEW     │
  └──────┬──────┘
         │
    ┌────┴────┐
    ▼         ▼
  APPROVE   REVISE  ← You decide: proceed or redirect
    │         │
    ▼         └──► back to GATE CHECK
  EXECUTE
```

## Implementation

Gates are enforced via system prompts. Each mode's prompt file (`.cbus/prompts/{mode}.md`) must begin with the gate instruction:

**Example — `think.md`:**
```
Before answering, you MUST:
1. List 3 risks or failure modes for the proposed approach
2. State your assumptions explicitly
3. Present at least 2 alternative approaches with trade-offs

Only after completing steps 1-3 may you provide a recommendation.
```

## Gate Override

In rare cases, you may want to skip gating (e.g., trivial tasks in BUILD mode). This is allowed but must be:

- Explicitly requested by the human
- Logged in the reflection for the session
- Never the default behavior
