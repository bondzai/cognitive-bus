# Intelligent Friction

> Reference: ["Give Me 18 Minutes and I'll Make you Dangerously Smart (with AI)"](https://www.youtube.com/watch?v=A8_nNYLTXEQ) — theMITmonk

This document integrates the core concepts from theMITmonk's framework into Cognitive Bus. The central insight: **the top 1% use AI backwards** — not to remove thinking, but to sharpen it.

## The Core Question

> "Is AI your wheelchair, or is it your gym spotter?"

Most people use AI to remove friction (do the work for me). Cognitive Bus uses AI to add **productive friction** (challenge me, then help me execute). This is the philosophical foundation that connects theMITmonk's framework to our mode system.

---

## Concept 1: Intelligent Laziness — The Two-Curve Model

Not all tasks deserve equal effort. There are two types:

```
  Value                              Value
    ▲  ┌────────── cap                 ▲        ╱
    │ ╱                                │      ╱
    │╱                                 │    ╱
    └──────────► Effort                └──────────► Effort
    Capped Payoff                     Uncapped Payoff
    (emails, formatting,              (strategy, design,
     reports, grunt work)              decisions, learning)
```

**Capped payoff tasks** — returns flatten after "good enough." Extra effort is wasted.
**Uncapped payoff tasks** — returns compound. Small improvements unlock massive value.

### How This Maps to Cognitive Bus

| Task Type | Cognitive Bus Strategy |
|-----------|----------------------|
| Capped payoff | Delegate to AI in `BUILD` or `OPERATE` mode — execute fast, don't overthink |
| Uncapped payoff | Route through `THINK` first — invest in analysis, challenge assumptions |

**The principle (from Nobel laureate Herbert Simon):** *Satisfice* on capped tasks. *Obsess* on uncapped tasks.

**Completion bias warning:** Your brain gives equal dopamine for completing a formatting task and closing a strategic decision. Cognitive Bus fights this by forcing mode selection — you must declare *what type of work this is* before starting.

---

## Concept 2: DRAG Framework — What to Delegate

Four categories of work that AI should handle immediately:

| Letter | Category | Description | Cognitive Bus Mode |
|--------|----------|-------------|-------------------|
| **D** | Drafting | Overcome blank-page paralysis — AI writes the first messy draft | `BUILD` |
| **R** | Research | Summarization, extraction, competitive intelligence | `LEARN` |
| **A** | Analysis | Pattern-finding in unstructured data | `THINK` |
| **G** | Grunt Work | Formatting, translation, repetitive tasks | `BUILD` or `OPERATE` |

### The AIM Protocol for Delegation

When delegating via DRAG, structure your prompt with:

- **A**ct — Assign AI a role (maps directly to Cognitive Bus roles: critic, builder, tutor, operator)
- **I**nput — Provide the data/context (maps to `state.yaml` snapshots)
- **M**ission — State the objective (maps to `current_goal` in state)

**Key insight:** *"Be the architect. Let AI carry the bricks."* — This is the BUILD mode philosophy.

---

## Concept 3: The Intelligent Hill — Prompting as a Skill

AI is a **probability engine**, not a calculator. The quality of output depends on the sophistication of input. There are five levels:

```
  Sophistication
       ▲
       │  5. AI Agents ─────── autonomous execution
       │  4. Chain of Thought ─ step-by-step reasoning
       │  3. Few-shot ───────── multiple examples + context
       │  2. One-shot ──────── one example provided
       │  1. Zero-shot ─────── basic question, hope for luck
       └──────────────────────────────────────────────►
```

### How This Maps to Cognitive Bus

| Prompting Level | Cognitive Bus Equivalent |
|----------------|------------------------|
| Zero-shot | No mode, no context — the anti-pattern |
| One-shot | Mode selected, but no state loaded |
| Few-shot | Mode + snapshot + relevant decisions |
| Chain of Thought | `THINK` mode with gating (forced reasoning) |
| AI Agents | Full pipeline: route → gate → execute → reflect |

**The key practice:** Don't evaluate AI's answers — evaluate its **reasoning**. This is exactly what `THINK` mode gating enforces: the AI must show its work before you approve execution.

---

## Concept 4: The Intelligent Gym — Productive Friction

This is the most important concept for Cognitive Bus.

There are two types of AI tasks:

| Type | Goal | AI Role | Friction |
|------|------|---------|----------|
| **Information tasks** | Get answers fast | Remove barriers | Low friction (good) |
| **Transformation tasks** | Build capability | Add resistance | High friction (good) |

### The Gym Metaphor

```
  WHEELCHAIR (passive)              GYM SPOTTER (active)
  ─────────────────────             ──────────────────────
  "Write my speech"                 "Critique my speech"
  "Solve this problem"             "Quiz me on this problem"
  "Give me the answer"             "Guide me to the answer"
  "Do the work"                    "Challenge my work"
```

### How This Maps to Cognitive Bus Modes

| Mode | Friction Type | Why |
|------|--------------|-----|
| `THINK` (critic) | **High friction** — challenges your ideas, forces alternatives | Transformation |
| `BUILD` (builder) | **Low friction** — executes efficiently on decided plans | Information |
| `LEARN` (tutor) | **High friction** — guides, doesn't give answers, quizzes you | Transformation |
| `OPERATE` (operator) | **Low friction** — monitors, triages, runs playbooks | Information |

**This is why Cognitive Bus has THINK and LEARN modes that deliberately resist giving you the easy answer.** They are the gym. BUILD and OPERATE are the tools you use *after* you've done the work of thinking and learning.

### Progressive Difficulty

The Intelligent Gym uses progressive resistance:

1. AI explains a concept (baseline)
2. AI quizzes you on it (recall)
3. AI presents edge cases (application)
4. AI challenges your reasoning (mastery)

This maps to LEARN mode's system prompt: *"Never just give the answer — guide toward it."*

---

## Concept 5: The Intelligent Fool — Beginner's Mindset

> "True confidence comes from admitting what you don't know."

The neuroscience principle: **your brain rewires at the edge of ability** — not in comfort zones.

### Two Cultures

| Culture | Behavior | Outcome |
|---------|----------|---------|
| **Know-it-all** | Hide gaps, avoid basic questions, protect ego | Stagnation |
| **Learn-it-all** | Admit gaps, ask fundamental questions, embrace discomfort | Compound growth |

### How This Maps to Cognitive Bus

The `LEARN` mode exists specifically to be the "intelligent fool" space:

- No judgment — it's a mode, not a confession
- Explicit permission to ask basic questions
- AI as tutor, not evaluator
- Knowledge gaps become `blockers` in state.yaml — visible, trackable, actionable

**The energy field in `state.yaml` also connects here:** When energy is low, you're more likely to fake understanding. The system should route you toward LEARN (fill gaps) rather than BUILD (accumulate debt).

---

## Integration: The Combined Framework

```
┌──────────────────────────────────────────────────────────┐
│                    INTELLIGENT LAZINESS                    │
│         Classify: Is this capped or uncapped payoff?      │
└─────────────┬───────────────────────────┬────────────────┘
              │                           │
       Capped payoff               Uncapped payoff
              │                           │
              ▼                           ▼
┌─────────────────────┐    ┌──────────────────────────────┐
│   DRAG → Delegate   │    │   INTELLIGENT GYM            │
│   D: Draft (BUILD)  │    │   Route through THINK first  │
│   R: Research (LEARN)│    │   Challenge before execute   │
│   A: Analyze (THINK)│    │   Add friction, not remove   │
│   G: Grunt (OPERATE)│    │                              │
└─────────────────────┘    │   INTELLIGENT HILL           │
                           │   Use Chain of Thought       │
                           │   Evaluate reasoning > answer│
                           │                              │
                           │   INTELLIGENT FOOL           │
                           │   Admit gaps → LEARN mode    │
                           │   Quiz yourself → grow       │
                           └──────────────────────────────┘
                                        │
                                        ▼
                              ┌──────────────────┐
                              │     REFLECT      │
                              │  Did I use AI as │
                              │  wheelchair or   │
                              │  gym spotter?    │
                              └──────────────────┘
```

## New Reflection Question

Add to the daily reflection scorecard:

```yaml
friction_check:
  wheelchair_uses: integer    # Times AI did the thinking for you
  spotter_uses: integer       # Times AI challenged your thinking
  ratio: float               # spotter / (wheelchair + spotter)
```

**Target ratio:** > 0.5 for uncapped payoff tasks. Wheelchair usage is fine for capped payoff (DRAG) tasks.

---

## Key Quotes for System Prompts

These can be embedded in `.cbus/prompts/` to reinforce the framework:

- **THINK prompt:** *"Evaluate the reasoning, not just the answer."*
- **BUILD prompt:** *"Be the architect. Let AI carry the bricks."*
- **LEARN prompt:** *"The brain rewires at the edge of ability, not in the comfort zone."*
- **OPERATE prompt:** *"Satisfice on capped payoff. Reserve obsession for what compounds."*
- **Reflection prompt:** *"Am I using AI to skip the workout, or to lift heavier weights?"*
