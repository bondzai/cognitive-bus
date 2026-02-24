# Reflection and Scorecard

Reflection closes the feedback loop. Without it, you repeat the same mistakes and never improve how you use AI — only what you use it for.

## Reflection Process

At the end of each work session (or day), run a structured reflection:

### Inputs

- Session logs (what modes were used, what was produced)
- `state.yaml` (current goals, open decisions, blockers)
- Previous reflections (trend data)

### Output — Reflection Entry

```yaml
date: 2026-02-24
score: 7                       # 1-10 self-assessed effectiveness
insight: "string"              # One key takeaway
mode_distribution:
  THINK: 0.2
  BUILD: 0.6
  LEARN: 0.1
  OPERATE: 0.1
decisions_closed: 2
decisions_opened: 1
blockers_resolved: 1
gate_overrides: 0              # Times gating was skipped
energy_trend: "high → medium"
```

## Scorecard

The scorecard is a periodic summary (weekly or on-demand) that aggregates reflections:

```
══ Weekly Scorecard ═══════════════════════════════
  Sessions:        5
  Avg Score:       7.2 / 10
  Mode Balance:    THINK ██░░  BUILD ████  LEARN █░░░  OPERATE ░░░░
  Decisions:       +4 opened, +3 closed, 2 still open
  Blockers:        1 persistent (> 3 days)
  Gate Overrides:  1 (acceptable)
  Energy Pattern:  peaks Mon/Tue, dips Thu/Fri

  Top Insight:     "Switching to THINK after 2hrs of BUILD
                    consistently produces better code."

  Recommendation:  "Schedule THINK breaks mid-afternoon.
                    Address the persistent blocker — it's
                    been open 4 days."
══════════════════════════════════════════════════
```

## Reflection Rules

1. **Frequency** — At minimum, reflect daily. Optionally per-session.
2. **Honesty** — Scores are for you, not for metrics. Be accurate.
3. **Actionability** — Every insight should inform tomorrow's behavior.
4. **Brevity** — One insight per reflection. If you have more, pick the most important.
5. **Persistence** — Reflections are stored in `.cbus/reflections/{date}.yaml` and summarized in `state.yaml`.

## What Good Reflection Looks Like

**Weak:** "Today was productive."
**Strong:** "Spent 3hrs in BUILD without a THINK break. The auth middleware had a design flaw I caught late. Insert a THINK checkpoint after 2hrs next time."

Reflection is not journaling. It is **calibration**.
