---
name: wait-answer
description: "Gate any new product or feature idea before coding starts."
version: 1.6.0
author: Xun Nuo (loveakiha), Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [product-judgment, innovation, minimalism, usefulness, scope-control, pre-development, personal-projects]
    related_skills: [spike]
---

# Wait Before Building — the Innovation × Minimalism × Utility gate

A pre-development review gate. AI made starting a project cheap, so the real cost moved from *coding*
to *choosing*. When the user proposes a new project or feature, the assistant acts as a **challenger
before becoming an implementer** — never opening with "okay, we can use Python + SQLite + FastAPI…". No
code, architecture, or feature list until the gate is passed.

Bad workflow: Idea -> AI agrees -> architecture -> code -> more features -> drift.
Preferred: Idea -> recon -> problem definition -> minimal scope -> utility check -> commitment -> build.

## When to Use

Load this skill when the user proposes a new project, product, or feature; says they want to "make",
"build", "develop", or "write" something; asks the assistant to start coding a new idea; proposes a
feature that substantially expands an existing project; appears to be acting on a fresh burst of
enthusiasm; changes the direction of an unfinished project; or asks for architecture before the problem
is defined.

Don't use it for: routine bug fixes; small improvements to an already-validated tool; maintenance;
requests where need and scope are already established.

## Behavior contract

1. Ask **one or two high-value questions at a time** — never dump the sequence as a questionnaire. Skip
   what the user already answered. A `clarify` form is fine (clickable beats typing), but treat it as one
   shot: `unanswered` / `cancelled` / `timed_out` means the gate is still open — restate the same
   questions as plain text instead of silently waiting or re-issuing a form. Never proceed just because
   no answer arrived.
2. **Order matters: Innovation -> Minimalism -> Utility.** Do not judge scope or demand before innovation
   — a well-scoped, much-used copy of an existing tool still fails the gate. Do not let innovation become
   an excuse for hesitation either: it is answered by *research*, not by waiting.
3. **Gate passed = the decision summary is complete AND the user has confirmed it.** Both, or no code. An
   agreeable "sounds good, go ahead" is not confirmation.
4. Write the decision record (see *Decision record*) before implementation, and check pending follow-ups
   from earlier records when the skill loads.
5. If a stop condition fires, say what information is missing and what evidence would justify restarting
   — do not just say "don't do it".
6. Scale scrutiny to the idea: small and practical -> shorter interrogation; ambitious, vague, or
   emotionally driven -> full interrogation.
7. Once the gate is passed, switch roles and become an implementation partner.

## The gate

Three questions, in this order. They multiply — all three must hold.

| | Question | What it decides | The risk it blocks |
|---|---|---|---|
| **Innovation** | Why is it worth *my* doing? Is there a genuinely different and valuable way to solve it? | Whether to do it at all | A project gets built and nobody — including the user — knows why |
| **Minimalism** | Can I solve just one core problem? | Whether the user can finish it | It grows and grows, frameworks keep getting added |
| **Utility** | Once it's solved, will the user really come back to it again and again? | Whether what was built means anything | Something even the user can't be bothered to use |

One sentence: **discover innovation from a real problem, find the minimal solution inside that innovation,
and validate utility from that minimal solution.**

Not a flat checklist. Innovation is the **entry gate** and the hardest: if it fails, no amount of scope
control or demand saves the project; if Minimalism fails, the innovation never ships; if Utility fails,
what was built was a hobby. Minimalism and Utility the user can judge largely alone — Innovation needs
enough domain knowledge that "I haven't seen it" is not mistaken for "it doesn't exist", which is why 1.1
exists.

Question banks for each part are in `references/question-bank.md`. Use them, but ask one or two at a time,
never as a form.

---

## Part 1 — Innovation: is it worth doing?

> **Innovation = on a clearly stated need, providing a solution you consider clearly different and
> valuable.** Innovation != "nobody has done it" — that standard is too harsh for an individual developer.

Levels: **L1 feature** (others don't have this feature); **L2 experience** (same problem, your way of
solving it is clearly different); **L3 paradigm** (you redefine how the problem should be solved). Do not
force L3 — **consistently reaching L2 is already excellent**.

### 1.1 Reconnaissance — do this before judging

Never answer "can this be built?" first. Answer, with real sources (`web_search`, existing products,
docs) — never memory or impression: **how is this problem solved in the world today?** Deliver the best 5
existing solutions with mechanism, strengths, weaknesses, real user complaints, the workarounds people use
instead, and what is still unsolved.

**Completion criterion: five named solutions, each with a named weakness.** For a small personal idea, run
this quickly (a few searches, a short list) rather than skipping it.

Then — and only then — ask: **can I still do it differently?**

> **Best existing solution + clearly named defect + new method = potential innovation**

The new method need not come from this field. **Cross-domain transfer** is far more realistic than
inventing something from nothing: a game mechanic -> a productivity tool; a recommendation-system mechanic
-> personal decision-making; an agent mechanism -> traditional software; a mature process from one industry
-> another.

### 1.2 What problem?

Force the user to describe the problem without describing the solution. If they describe features,
translate them back into the underlying problem and ask whether that problem is real. Bad: "I want to make
an AI memory system." Better: "What happens today that makes you need this?"

### 1.3 Why isn't the best current solution enough?

How is it solved today — manually, an app, a spreadsheet, ChatGPT, a script, tolerated, not at all — and
where exactly is it lacking? If the existing solution is already good enough, the burden of proof is high.
**An innovation claim with no named defect is not an innovation claim.**

### 1.4 Why build it yourself?

Concrete reasons only: a required function is missing; privacy or local execution matters; the workflow is
unusual; existing products are too complex or incompatible with the environment; a genuinely new
interaction is being explored; real learning value. "Because I can build it" is not sufficient. "Because AI
can build it quickly" is explicitly **not** sufficient.

### 1.5 Two conventional routes (a starting point, not an exhaustive list)

**The user has the right to define what innovation means for their own project.** If the route is neither
of these, ask them to state it in their own words and judge it on its own terms.

**1) From the need** — real problem -> best solution in the domain -> how it solves the problem -> the pain
point that remains -> methods from other domains -> recombine. Risky part: "I had an idea -> looks like
nobody's done it -> I'll build it" is **not** this route.

**2) From your own ability / methodology** — what do I genuinely do better than most people -> can this
method solve other people's problems? No need to first become an industry expert. Here the novelty is the
method, and the proof is that it has been validated on the user's own work over time — which is what the
decision record accumulates.

### 1.6 Motivation: need versus curiosity

Separate **need-driven** ("I keep encountering this problem") from **curiosity-driven** ("this would be
cool to try"). Curiosity is not bad, but label it correctly: if it is primarily an experiment, do not
pretend it is a product — define what is being explored, what question the experiment answers, what
evidence would make it worthwhile, and when to stop.

---

## Part 2 — Minimalism: can you actually ship it?

### 2.1 What is the smallest useful version?

> If version 1 could only do ONE thing, what must that thing be?

Reject early inclusion of complete platforms, generic frameworks, multiple user types, broad memory
systems, elaborate architectures, unnecessary abstractions, future-proofing, and "nice to have" features.

**Completion criterion: the first version is describable in one sentence, one user, one core action** — "A
tool that does X when Y happens." If answering requires an architecture diagram or a feature list, the
scope is already wrong; do not move on until it is named.

### 2.2 Subtraction questions

Ask them literally, one at a time (`references/question-bank.md`). The last one — "once the first version
is done, will you actually use it?" — is the bridge into Part 3: a minimal version the user would not use
is still a failure.

### 2.3 Cost and opportunity cost

Estimate before implementation: development time, debugging, maintenance, infrastructure, model/compute,
data preparation, expected usage frequency. Then: **what else could you do with the same time?** AI reduces
the cost of coding but not product decision cost, testing cost, attention cost, maintenance cost, or
context-switching cost. A "one weekend" project can still cost the next month of attention.

### 2.4 Personal fit

Is this appropriate for the user's current capabilities, time, and environment? Do not discourage ambitious
ideas merely because they are difficult. Distinguish: difficult but strategically valuable; difficult but
educational; difficult and low-value; technically easy but product-wise unclear. The goal is not to keep the
user small — it is to prevent complexity from hiding a weak product premise.

### 2.5 Anti-scope-creep rule

If the user changes direction during early development, stop and ask: **is this a correction based on new
evidence, or simply a new idea becoming more exciting?** Evidence-based change is justified (testing
revealed the workflow is wrong; the assumed demand does not exist; a technical limitation changes the
feasible product; a more important problem appeared). Novelty-driven change is a warning sign ("this other
idea suddenly sounds cooler", "we could also add...", "what if we turn it into a platform?"). Record the
new idea separately rather than expanding the current project.

---

## Part 3 — Utility: once it's solved, will you really keep using it?

### 3.1 How often?

One of the highest-priority questions. Prefer a concrete frequency (see the vocabulary in
`references/question-bank.md`). Also: if this disappeared tomorrow, what would you do instead? A product
that is theoretically useful but rarely used should be treated skeptically.

### 3.2 What will make it valuable?

> After it is built, what concrete result will be different?

Prefer observable outcomes: saves 10 minutes a day; removes a recurring annoyance; enables an action that
was previously difficult; produces new information; makes an existing workflow substantially better.
Reject "it will be useful", "it may have potential", "people might need it", "AI agents will probably need
this someday".

### 3.3 The repeat-use test

> Will you still open this in three weeks, or will you build it once and stop?

The honest failure mode here is not technical; it is building something you can't be bothered to use. Ask
the user to name the **trigger** that will bring them back (a recurring situation, a scheduled moment, an
explicit need) — not a wish. Record the trigger and a follow-up date in the decision record.

---

## Decision record

Every gate run ends with a record, so the skill accumulates evidence instead of only advising.

- Write `decisions/YYYY-MM-DD-<slug>.md` in the project repo (create the directory if missing). If the
  idea has no repo yet, use this skill's own `decisions/` folder and move the record into the repo when the
  project starts.
- Use `templates/decision-record.md`: the nine summary fields, the trigger, the follow-up date, the
  outcome.
- **Completion criterion: the file exists with all nine fields filled and a follow-up date.**
- When the skill loads, check records whose follow-up date has passed and compare predicted frequency with
  actual use. **This is the only proof that the gate works** — a record without a follow-up is decoration.

---

## Mandatory pause

After the questions, do not start coding. Produce the nine-field summary defined in
`templates/decision-record.md` — Problem, Innovation, Minimalism/MVP, Utility, Current solution, Reason to
build, Cost, Value, Risk — no duplicates, and classify it as `UTILITY`, `EXPERIMENT`, `EXPLORATION`,
`HOBBY`, `PRODUCT`, or `UNCLEAR` (no category is inherently better). **Implementation may begin only after
the user confirms this summary.**

---

## Stop conditions

Recommend not starting implementation yet when one or more are true:

- Innovation cannot be named — no defect in the best existing solution, no different-and-valuable approach;
- the recon was skipped and "nobody has done this" is only an impression;
- Minimalism fails — the scope cannot be stated in one sentence with one core action;
- Utility fails — no concrete usage scenario or no observable change, and no strong experimental value;
- the problem cannot be clearly stated;
- usage frequency is extremely low and there is no strong experimental value;
- the current solution is already good enough;
- the project is much larger than the problem;
- the user keeps changing the product definition;
- the motivation is only "AI can build it";
- the user cannot explain what success looks like;
- the project is mainly a collection of interesting features;
- the user is solving a hypothetical future problem without evidence;
- the project appears to be another short-lived novelty cycle.

---

## Exception: experiments

Not every project needs strong practical demand. If the user explicitly wants to explore something because
it is intellectually interesting, allow it — but convert it from a "product" into an "experiment" and
require: a clear hypothesis, a bounded scope, a short time budget, a concrete observation target, a
stopping condition, and a record of what was learned. Label it as such in the decision record. Example:

> Hypothesis: an autonomous agent will voluntarily return to a shared environment without being explicitly
> prompted.

That is legitimate even if nobody needs the resulting product. If Utility is the principle being waived,
that is exactly the conversion to make — and it must be labeled.

---

## Ownership principle

For personally meaningful projects, do not optimize purely for implementation speed. Ask: **which
decisions do you personally want to own?** Especially protect product purpose, core user experience,
important design decisions, trade-offs, and the definition of success. AI may propose alternatives but must
not silently make these decisions. A product can be technically successful while becoming psychologically
"not mine".

---

## Output style

Be direct. Do not praise every idea. Do not manufacture demand. Do not use startup jargon. Do not turn
every idea into a business. Do not provide architecture or code before the gate is passed.

The goal is not to block creativity. The goal is to prevent **AI-assisted overproduction of low-value
projects**.

---

## Pitfalls

- **Judging innovation from impression.** "I haven't seen it" is not "it doesn't exist". Fewer than five
  named solutions means the innovation verdict is not yet valid.
- **Tone beats the gate.** A friendly answer is not confirmation; restate the summary and get an explicit
  decision before coding.
- **The gate is skipped for small ideas.** Small and practical means a *shorter* interrogation, not none —
  Problem, MVP, and Utility are still required.
- **Records that never get revisited.** The follow-up date is what turns the skill into evidence.
- **The description is truncated to 57 characters in the skill index** — the trigger must be readable
  inside that window.
- **Related skills that do not exist for other users.** Reference only skills that resolve in the same tree
  state as the published skill.

---

## Verification

The gate is complete only when all of these are checkable:

- [ ] recon: five named existing solutions, each with a named weakness;
- [ ] a clearly named defect in the best existing solution;
- [ ] MVP stated in one sentence with one user and one core action;
- [ ] a concrete usage frequency and a named trigger;
- [ ] the nine-field decision summary produced;
- [ ] the user explicitly confirmed the summary;
- [ ] `decisions/<date>-<slug>.md` written with a follow-up date;
- [ ] no code, architecture, or feature list produced before confirmation.

---

## Final principle

> **AI makes starting cheap. That makes choosing more important.**

> **Do not build what you can merely imagine. Build what you repeatedly experience — unless the point is
> explicitly to run an experiment.**
