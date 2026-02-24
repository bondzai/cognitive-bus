# Principles

These principles govern all design decisions in Cognitive Bus. When in doubt, refer here.

## 1. Capability Over Convenience

Choose power over ease. A system that makes you stronger is worth more than one that makes things easier.

- Prefer explicit mode selection over auto-detection
- Prefer structured state over free-form chat history
- Prefer deliberate reflection over passive logging
- Accept friction when it produces better thinking

## 2. Human-First Reasoning

The human decides. The AI advises, critiques, and executes — but never overrides human judgment.

- AI must present trade-offs, not just recommendations
- Gating rules enforce critique before action
- Mode transitions are human-initiated (the system may suggest, never force)
- No autonomous execution without explicit human approval

## 3. Context as Infrastructure

Context is not a convenience feature — it is the core infrastructure that makes AI interactions compound over time.

- `state.yaml` is the single source of truth
- Snapshots are immutable, timestamped context packages
- Every session reads from and writes back to state
- Context is structured (YAML), not unstructured (chat logs)

## 4. Separation of Concerns

Reasoning, execution, and permissions are architecturally distinct layers.

- THINK mode never executes; BUILD mode never decides
- Permissions are declared per-mode, not globally
- Reflection is a separate phase, not embedded in execution
- Security boundaries are enforced, not suggested

## 5. Composability

Every component should work standalone and compose with others.

- Modes are independent — use one or all four
- State schema is extensible without breaking existing fields
- Routing rules are declarative and overridable
- The framework adapts to your workflow, not the reverse
