# Security and Permissions

Cognitive Bus enforces security through **separation of concerns**: reasoning, execution, and permissions are distinct layers that never collapse into one.

## Three-Layer Model

```
┌─────────────────────────┐
│  Layer 1: REASONING     │  ← What should we do?
│  (THINK, LEARN modes)   │     No execution allowed
├─────────────────────────┤
│  Layer 2: EXECUTION     │  ← Do the thing
│  (BUILD, OPERATE modes) │     Scoped permissions only
├─────────────────────────┤
│  Layer 3: PERMISSIONS   │  ← What are we allowed to do?
│  (Gate rules, approvals)│     Human-controlled
└─────────────────────────┘
```

### Layer 1: Reasoning (No Side Effects)

Modes: `THINK`, `LEARN`

- Cannot execute commands, write files, or modify state
- Can only produce analysis, recommendations, and explanations
- Output is advisory — human decides what to act on
- Safe to run without any permission grants

### Layer 2: Execution (Scoped)

Modes: `BUILD`, `OPERATE`

- Can execute commands and modify files
- Scoped by permission declarations (see below)
- Must pass through gating before execution
- All actions are logged for audit

### Layer 3: Permissions (Human-Controlled)

- Permissions are declared per-mode in `state.yaml` or `.cbus/permissions.yaml`
- Human approves or denies at the gate step
- No implicit permission escalation between modes

## Permission Schema

```yaml
# .cbus/permissions.yaml
build:
  allow:
    - write_files: ["src/**", "tests/**"]
    - run_commands: ["npm test", "npm run build"]
  deny:
    - write_files: [".env", "*.secret", "credentials.*"]
    - run_commands: ["rm -rf", "git push --force"]

operate:
  allow:
    - run_commands: ["docker ps", "docker logs *", "kubectl get *"]
    - write_files: ["config/**"]
  deny:
    - run_commands: ["docker rm", "kubectl delete"]
    - write_files: ["src/**"]

think:
  allow: []    # No execution permissions
  deny: ["*"]  # Explicit deny-all

learn:
  allow: []
  deny: ["*"]
```

## Security Principles

1. **Least privilege** — Each mode gets only the permissions it needs
2. **Deny by default** — Unlisted actions are denied
3. **No lateral movement** — BUILD permissions don't carry into OPERATE
4. **Audit trail** — Every execution-layer action is logged
5. **Human veto** — Any action can be blocked at the gate step

## Sensitive Data

- `state.yaml` may contain project context — treat it as internal documentation (not secret, but not public)
- `.cbus/permissions.yaml` defines security boundaries — protect it from unauthorized modification
- Snapshots are derived from state — same sensitivity level
- Reflection logs may contain strategic insights — store appropriately
