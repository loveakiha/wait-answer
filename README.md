# wait-answer

A [Hermes Agent](https://hermes-agent.nousresearch.com/docs) skill that gates every new product or
feature idea **before a single line of code is written**.

## Why this exists

AI has made it cheap to start a project. That shifts the real cost from *coding* to *choosing*.
The failure mode it creates is not "the code doesn't work" — it is **starting something on a whim,
building a lot, and never using any of it**. `wait-answer` is a pre-development review gate: when
you propose a new project or feature, the assistant challenges the idea first, instead of opening
with "okay, let's use Python + SQLite + FastAPI…".

## The core principles

Three questions, in this order. They multiply — **all three must hold**.

1. **Innovation** — *Why is it worth my doing?* Is there a genuinely different and valuable way to
   solve a real problem? (This is the entry gate and the hardest. If it fails, nothing else can
   save the project.)
2. **Minimalism** — *Can I solve just one core problem?* If you can't state the first version in
   one sentence with one core action, the scope is already wrong.
3. **Utility** — *Once it's solved, will you really come back to it again and again?* A tool even
   you can't be bothered to use is a hobby, not a product.

In one line:

> **Innovation decides whether to do it. Minimalism decides whether you can ship it. Utility
> decides whether what you built means anything.**

And the takeaway when in doubt:

> **AI makes starting cheap. That makes choosing more important.**
> **Do not build what you can merely imagine. Build what you repeatedly experience — unless the
> point is explicitly to run an experiment.**

## How it works

When the skill is loaded, the assistant acts as a **challenger**, not an implementer:

- Asks **one or two high-value questions at a time** (never a 20-question dump).
- Runs **innovation reconnaissance** — researches how the problem is actually solved in the world
  today, with real sources — before judging whether the idea is novel.
- Works through the three gates in order: Innovation → Minimalism → Utility.
- Ends with a **mandatory pause**: a short decision summary (problem, frequency, current solution,
  reason to build, MVP, cost, value, risk, type) — and only then does it start coding.

It also defines **stop conditions** (when to say "don't build this yet, here's what's missing") and
a clean **exception path for genuine experiments** (a bounded idea with a hypothesis, time budget,
and a stopping condition — not a fake product).

## Install

Copy `SKILL.md` into your Hermes skills directory and the skill is available:

```
~/.hermes/skills/wait-answer/SKILL.md
```

(or the skills directory of a specific Hermes profile, under `profiles/<name>/skills/`).

The skill is cross-platform (linux, macos, windows) and has no required commands or environment
variables.

## License

MIT
