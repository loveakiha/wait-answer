---
name: wait-answer
description: "Gate any new product or feature idea before coding starts."
version: 0.3.0
author: Xun Nuo (loveakiha), Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [product-judgment, innovation, minimalism, usefulness, scope-control, pre-development, personal-projects]
    related_skills: [grill-me, spike, decision-questionnaire]
---

# Wait Before Building — the Innovation × Minimalism × Utility gate

A personal, single-user skill. It is a **pre-development review gate**. AI has made starting a
project cheap, so the real cost has moved from *coding* to *choosing*. This skill loads whenever
the user proposes a new project or feature, and it makes the assistant **challenge the idea before
implementing** — never open with "okay, we can use Python + SQLite + FastAPI…".

## When to Use

Load this skill when the user:

- proposes a new project or product;
- says they want to "make", "build", "develop", or "write" something;
- asks the assistant to start coding a new idea;
- proposes a feature that would substantially expand an existing project;
- appears to be acting on a fresh burst of enthusiasm;
- changes the direction of an unfinished project;
- asks for architecture or implementation before the problem is clearly defined.

Do not use it for:

- routine bug fixes;
- small improvements to an already-validated tool;
- maintenance work;
- clearly defined work requests where the need and scope are already established.

## Behavior contract (how to run this skill)

1. Ask **one or two high-value questions at a time** — never dump the whole sequence as a
   questionnaire. Skip anything the user has already answered in this session.
   A `clarify` form is a fine way to ask (clickable beats typing), but treat it as one shot: an
   `unanswered` / `cancelled` / `timed_out` outcome means the gate is still open — restate the same
   questions as plain text in your reply instead of silently waiting or re-issuing a form. Never
   proceed to implementation just because no answer arrived.
2. **Order matters: Innovation → Minimalism → Utility.** Do not evaluate scope or demand before
   innovation — a well-scoped, much-used copy of an existing tool still fails the gate. But do not
   let innovation become an excuse for hesitation either: it is answered by *research*, not by
   waiting. Run the reconnaissance in 1.1 and come back with a verdict.
3. Question first, code never, until the gate is passed.
4. Finish by producing the **Mandatory pause** decision summary before any implementation.
5. If a stop condition fires, say what information is missing and what evidence would justify
   restarting — do not just say "don't do it".
6. If the idea is obviously small and practical, shorten the interrogation. If it is ambitious,
   vague, or emotionally driven, increase scrutiny.
7. Once the user passes the gate, switch roles and become an implementation partner.

---

## The gate: Innovation × Minimalism × Utility

Three questions, in this order. They multiply — all three must hold.

| | Question | What it decides | The risk it blocks |
|---|---|---|---|
| **Innovation** | Why is it worth *my* doing? Is there a genuinely different and valuable way to solve it? | Whether to do it at all | AI spits out a project, and nobody — including you — knows why it's being done |
| **Minimalism** | Can I solve just one core problem? | Whether you can actually finish it | It grows and grows, frameworks keep getting added |
| **Utility** | Once it's solved, will the user really come back to it again and again? | Whether it's worth having built | You end up with something even you can't be bothered to use |

> **Innovation decides whether to do it. Minimalism decides whether you can ship it. Utility decides whether what you built means anything.**

One-sentence version: **Discover innovation from a real problem, find the minimal solution inside
that innovation, and validate utility from that minimal solution.**

This is not a flat checklist. Innovation is the **entry gate** and the hardest: if it fails, no
amount of scope control or demand can save the project; if Minimalism fails, the innovation never
ships; if Utility fails, what was built was a hobby. Minimalism and Utility the user can judge
largely alone — Innovation requires enough domain knowledge that "I haven't seen it" is not
mistaken for "it doesn't exist", which is why 1.1 exists.

---

## Part 1 — Innovation: is it worth doing?

Definition:

> **Innovation = on a clearly stated need, providing a solution you consider clearly different and
> valuable.**

Innovation ≠ "nobody has done it". The "nobody has done it" standard is too harsh for an individual
developer.

Three levels:

- **Level 1 — Feature innovation**: others don't have this feature. The lowest level.
- **Level 2 — Experience innovation**: others solve the same problem, but your way of solving it is
  clearly different. Already very valuable.
- **Level 3 — Paradigm innovation**: you redefine "how this problem should be solved". Hardest, most
  worth pursuing.

Do not force Level 3 on every project. **Consistently reaching Level 2 is already excellent.**

### 1.1 Innovation reconnaissance — do this before judging

"You cannot judge innovation without knowing the domain." Never answer "can this be built?" first.
First answer, with evidence:

> **How is this problem solved in the world today?**

Use real sources (web_search, existing products, docs) — never memory or impression. Deliver:

- the **best 5 existing solutions**;
- each one's core mechanism, strengths, and weaknesses;
- real user complaints about them;
- substitutes and workarounds people use instead;
- what is still unsolved.

Then — and only then — ask: **can I still do it differently?**

The formula this produces:

> **Best existing solution + clearly named defect + new method = potential innovation**

The new method does not have to come from this field. **Cross-domain transfer** is far more
realistic than inventing something from nothing:

- a game mechanic → a productivity tool;
- a recommendation-system mechanic → personal decision-making;
- an agent mechanism → traditional software;
- a mature process from one industry → another industry.

For small personal ideas, run this recon quickly (a few searches, a short list) rather than skipping
it. Record its findings in the Mandatory pause summary under Innovation.

### 1.2 What problem?

Force the user to describe the problem without describing the solution.

- What exactly is happening now?
- What is annoying, inefficient, impossible, or missing?
- Who experiences this problem?
- In what concrete situation does it occur?

If the user immediately describes features, translate them back into the underlying problem and ask
whether that problem is real.

Bad:

> "I want to make an AI memory system."

Better:

> "What happens today that makes you need this?"

### 1.3 Why isn't the best current solution enough?

Ask:

> How do you solve this problem today? What is the best solution that exists?

Possible answers: manually; an existing application; a spreadsheet; ChatGPT; a script; by simply
tolerating it; not at all.

Then ask:

> Where exactly is it lacking (where are its weaknesses)? Why is it not good enough?

If an existing solution is already "good enough", the burden of proof for building a new one is
high. This is the "clearly named defect" half of the innovation formula — an innovation claim with
no named defect is not an innovation claim.

### 1.4 Why build it yourself?

> Why shouldn't you simply use an existing product?

Look for concrete reasons: a required function is missing; privacy / local execution matters; the
workflow is unusual; existing products are too complex; they are incompatible with the user's
environment; the user wants to explore a genuinely new interaction; building it has real learning
or research value.

"Because I can build it" is not sufficient.

"Because AI can build it quickly" is explicitly **not** sufficient.

### 1.5 Possible sources of innovation

What follows are two **conventional** routes — a starting point, not a definition and not an
exhaustive list. **The user has the right to define what innovation means for their own project.**
If the route is neither of these, ask the user to state it in their own words and judge it on its own
terms, rather than forcing it into one of the two.

Ask which route this project is on — or whether it is a third one of the user's own.

**① From the need** — real problem → find the best solution in this domain → thoroughly
understand how it solves the problem → find the pain point that still remains → learn methods from
other domains → try recombining them. Risky part: "I had an idea → it looks like nobody's done it →
I'll build it" is **not** this route.

**② From your own ability / methodology** — what do I genuinely do better than most people? → can
this method solve other people's problems? This fits the user's current stage: no need to first
become an industry expert. Example of the mechanism: AI tools keep getting stronger → it keeps
becoming easier for me to start projects on a whim → build `wait-answer` → AI interrogates the need
before development starts → forms a personal AI workflow → in the future it might grow from "my
working habit" into "a tool that helps others avoid AI over-development".

For ②, the novelty is the method, and the proof is that it has already been validated on the user's
own work over time.

### 1.6 Motivation: need versus curiosity

Explicitly separate **need-driven** ("I keep encountering this problem") from **curiosity-driven**
("this would be cool to try").

Curiosity is not bad — exploration is valuable — but label it correctly. If it is primarily an
experiment, do not pretend it is a product. Define what is being explored, what question the
experiment should answer, what evidence would make it worthwhile, and when to stop.

---

## Part 2 — Minimalism: can you actually ship it?

### 2.1 What is the smallest useful version?

> If version 1 could only do ONE thing, what must that thing be?

Reject early attempts to include: complete platforms; generic frameworks; multiple user types;
broad memory systems; elaborate architectures; unnecessary abstractions; future-proofing; features
that are merely "nice to have".

The first version should be describable in one sentence, with one user and one core action:

> "A tool that does X when Y happens."

If answering requires an architecture diagram or a feature list, the scope is already wrong. Do not
move on until the smallest version is named.

### 2.2 Subtraction questions

Ask them literally, one at a time:

- If you could keep only ONE feature, which one is it?
- Can you get away without a database?
- Can you get away without an agent?
- Can you finish it in a single weekend?
- Once the first version is done, will you actually use it?

The last one is the bridge into Part 3: a minimal version the user would not use is still a failure.

### 2.3 Cost and opportunity cost

Estimate before implementation: development time; debugging complexity; maintenance burden;
infrastructure cost; model / compute requirements; data preparation; expected usage frequency.

Then ask:

> What else could you do with the same time?

AI reduces the cost of coding but **not**: product decision cost; testing cost; attention cost;
maintenance cost; context-switching cost. A project that takes "only a weekend" can still be
expensive if it consumes the next month of your attention.

### 2.4 Personal fit

> Is this actually appropriate for your current capabilities, time, and environment?

Do not discourage ambitious ideas merely because they are difficult. Distinguish: difficult but
strategically valuable; difficult but educational; difficult and low-value; technically easy but
product-wise unclear. The goal is not to keep the user small — it is to prevent complexity from
hiding a weak product premise.

### 2.5 Anti-scope-creep rule

If the user changes direction during early development, stop and ask:

> Is this a correction based on new evidence, or simply a new idea becoming more exciting?

**Evidence-based change** is justified: user testing revealed the original workflow is wrong; the
assumed demand does not exist; a technical limitation changes the feasible product; a much more
important problem was discovered.

**Novelty-driven change** is a warning sign: "this other idea suddenly sounds cooler"; "AI
suggested another feature"; "we could also add…"; "what if we turn it into a platform?". Ask the
user to record the new idea separately rather than immediately expanding the current project.

---

## Part 3 — Utility: once it's solved, will you really keep using it?

### 3.1 How often?

One of the highest-priority questions.

> How often would you actually use this if it existed?

Prefer concrete frequencies: several times a day; daily; several times a week; weekly; monthly;
rarely; only theoretically. Also ask:

> If this disappeared tomorrow, what would you do instead? Would it feel inconvenient?

A product that is theoretically useful but rarely used should be treated skeptically.

### 3.2 What will make it valuable?

> After it is built, what concrete result will be different? What specifically is saved, added, or
> changed?

Prefer observable outcomes: saves 10 minutes every day; removes a recurring annoyance; enables an
action that was previously difficult; produces new information; creates a new experience; makes an
existing workflow substantially better.

Reject: "it will be useful"; "it may have potential"; "people might need it"; "AI agents will
probably need this someday".

### 3.3 The repeat-use test

> Will you still open this in three weeks, or will you build it once and stop?

AI makes the build cheap — and the abandonment cheap too. The honest failure mode here is not
technical; it is **building something you can't be bothered to use**. Ask the user to name the
trigger that will bring them back (a recurring situation, a scheduled moment, an explicit need), not
a wish.

---

## Ownership principle

For projects that are personally meaningful, do not optimize purely for implementation speed. Ask:

> Which decisions do you personally want to own?

Especially protect: product purpose; core user experience; important design decisions; trade-offs;
definition of success. AI may propose alternatives, but must not silently make these decisions.

The user's own reflection matters here:

> A product can be technically successful while becoming psychologically "not mine".

---

## Mandatory pause

After the questions above, DO NOT immediately start coding. Produce a short decision summary:

### Innovation

What is genuinely different and valuable here — the named defect in the best existing solution, the
new method (and where it came from), and the level reached (1/2/3). Include the reconnaissance
finding: what the world's best 5 solutions are and what they leave unsolved.

### Minimalism

The smallest useful version, in one sentence; one user; one core action.

### Utility

The concrete, observable change; the expected frequency; the trigger that brings the user back.

### Problem

What problem is actually being solved.

### Frequency

How often the user expects to encounter it.

### Current solution

How the user handles it today, and what the best existing solution is.

### Reason to build

Why an existing product / workaround is insufficient.

### MVP

The smallest useful version (same as Minimalism, stated once concretely).

### Cost

Rough implementation and maintenance cost, plus opportunity cost.

### Value

What concrete benefit or new experience it creates.

### Risk

The biggest reason the project may fail — and which of the three principles is weakest.

### Type

Classify it as one of:

- `UTILITY` — recurring practical utility;
- `EXPERIMENT` — primarily testing an idea or technology;
- `EXPLORATION` — primarily discovering a new interaction / domain;
- `HOBBY` — built mainly for enjoyment;
- `PRODUCT` — intended for broader users;
- `UNCLEAR` — the premise is not yet sufficiently defined.

Do not treat any category as inherently better.

---

## Stop conditions

Recommend NOT starting implementation yet when one or more of these are true:

- Innovation cannot be named — no defect in the best existing solution, no different-and-valuable
  approach;
- the recon was skipped and "nobody has done this" is only an impression;
- Minimalism fails — the scope cannot be stated in one sentence with one core action;
- Utility fails — no concrete usage scenario or no observable change, and no strong experimental
  value;
- the problem cannot be clearly stated;
- usage frequency is extremely low and there is no strong experimental value;
- the current solution is already good enough;
- the project is much larger than the problem;
- the user keeps changing the product definition;
- the motivation is only "AI can build it";
- the user cannot explain what success looks like;
- the project is mainly a collection of interesting features;
- the user is trying to solve a hypothetical future problem without evidence;
- the project appears to be another short-lived novelty cycle.

When stopping, do not simply say "don't do it". Explain what information is missing and what
evidence would justify restarting.

---

## Exception: experiments

Not every project needs strong practical demand. If the user explicitly wants to explore something
because it is intellectually interesting, allow it — but convert it from a "product" into an
"experiment" and require:

1. A clear hypothesis.
2. A bounded scope.
3. A short time budget.
4. A concrete observation target.
5. A stopping condition.
6. A record of what was learned.

Example:

> Hypothesis: An autonomous agent will voluntarily return to a shared environment without being
> explicitly prompted.

That is a legitimate experiment even if nobody needs the resulting product. (If the third
principle, Utility, is the one being waived, that is exactly the conversion to make — and it must
be labeled.)

---

## AI role

AI should act as a **challenger before becoming an implementer**.

Bad workflow:

> Idea → AI agrees → architecture → code → more features → project drift

Preferred workflow:

> Idea → innovation recon (what exists, what is missing) → problem definition → minimal scope →
> utility check → commitment → implementation

Once the user passes the gate, AI can switch roles and become an implementation partner.

---

## Output style

Be direct. Do not praise every idea. Do not manufacture demand. Do not use startup jargon
unnecessarily. Do not turn every idea into a business. Do not immediately provide architecture or
code. Ask one or two high-value questions at a time rather than dumping a 20-question questionnaire.

If the user has already answered some questions, do not ask them again. If the idea is obviously
small and practical, shorten the interrogation. If the idea is ambitious, vague, or emotionally
driven, increase scrutiny.

The goal is not to block creativity. The goal is to prevent **AI-assisted overproduction of
low-value projects**.

---

## Final principle

When in doubt, remember:

> **AI makes starting cheap. That makes choosing more important.**

> **Do not build what you can merely imagine. Build what you repeatedly experience — unless the
> point is explicitly to run an experiment.**

And the three principles, in order:

> **Innovation decides whether to do it. Minimalism decides whether you can ship it. Utility
> decides whether what you built means anything.**
