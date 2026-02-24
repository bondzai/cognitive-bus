# Daily Workflow

The daily workflow is a four-phase cycle that structures how you move through a workday with Cognitive Bus.

## The Cycle

```
  PLAN → THINK → BUILD → REFLECT
    ▲                        │
    └────────────────────────┘
```

### Phase 1: Plan (5-10 min)

**Mode:** None (pre-mode setup)

- Review `state.yaml` — what's the current goal, open decisions, blockers?
- Review yesterday's reflection — what did you learn?
- Set today's intention: one clear goal
- Update `state.yaml` with today's focus

```
cbus snapshot  # Review current context
# Edit state.yaml → set current_goal, energy level
```

### Phase 2: Think (15-30 min)

**Mode:** `THINK`

- Process open decisions
- Analyze blockers
- Challenge your plan — what could go wrong?
- Close decisions and clear blockers before building

```
cbus think "I need to decide between X and Y for today's build"
```

### Phase 3: Build (bulk of the day)

**Mode:** `BUILD`

- Execute on decided plans
- Reference closed decisions from state
- Switch to THINK if you hit an unexpected fork
- Switch to LEARN if you encounter unfamiliar territory
- Switch to OPERATE if production needs attention

```
cbus build "Implement the caching layer we decided on"
```

**Transition triggers during BUILD:**

| Signal | Action |
|--------|--------|
| Stuck > 20 min | Switch to THINK |
| Unfamiliar concept | Switch to LEARN |
| 3+ open decisions accumulated | Switch to THINK |
| Production alert | Switch to OPERATE |
| 2+ hours without a break | Pause and mini-reflect |

### Phase 4: Reflect (5-10 min)

**Mode:** None (post-mode wrap-up)

- Run reflection on the day
- Score effectiveness
- Capture key insight
- Update `state.yaml` with outcomes

```
cbus reflect
```

## Workflow Variations

**Short session (< 2 hours):** Skip formal Plan phase. Read snapshot, pick one task, build, reflect.

**Research day:** Heavy LEARN + THINK, minimal BUILD. Reflection focuses on what you now understand that you didn't before.

**Incident day:** OPERATE-dominant. Reflection focuses on what broke, why, and how to prevent recurrence.

**Planning day:** THINK-dominant. Focus on closing open decisions and clearing blockers. Minimal BUILD.

## Anti-Patterns

- **No THINK before BUILD** — You're guessing, not engineering
- **No REFLECT after BUILD** — You're repeating, not improving
- **All THINK, no BUILD** — Analysis paralysis. Set a time-box.
- **Ignoring energy levels** — Do THINK when sharp, BUILD when in flow, LEARN when curious, OPERATE when alert
