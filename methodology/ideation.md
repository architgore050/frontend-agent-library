# Ideation

## 1. What is it?

Ideation is the deliberate generation of many candidate solutions before any of them is judged — the divergent phase of design work (see [Design thinking](design-thinking.md)). It covers the techniques used to produce options (sketching, Crazy 8s, SCAMPER, forced connections, worst-possible-idea, constraint prompts) and the discipline that separates useful ideation from decoration: generating before judging, and selecting by criteria rather than by taste.

Ideation is not brainstorming theatre. Its output is a pool of options diverse enough that the eventual choice is a real choice, plus the criteria that make the choice defensible.

## 2. Why does it matter?

The first idea is almost never the best idea, but it is reliably the most *protected* idea. Once a solution exists and looks reasonably good, teams unconsciously defend it, evaluate alternatives as threats, and stop exploring. Every subsequent hour is spent decorating a possibly wrong answer. A structured ideation round is the cheapest insurance against this: it costs minutes, it produces alternatives the team can honestly compare, and — just as valuable — it produces *evidence* that the chosen direction was selected rather than defaulted.

For an agent the stakes are identical but the mechanism differs. An agent's first output is generated in seconds and looks finished, which makes premature convergence even easier: polished output invites acceptance. Deliberately generating and discarding several candidates before refining one is how an agent earns the right to say "we considered X, Y and Z; here is why B wins" (see [Design critique](design-critique.md) and the evaluation framework in [Design quality framework](../evaluation/design-quality-framework.md)).

## 3. Core principles

- **Quantity before quality.** Divergence and convergence are different cognitive modes and interfere with each other. Generating while judging yields fewer, safer ideas. Separate the modes in time.
- **Separate the creator from the critic.** During generation, no idea is evaluated — including your own. Evaluation is a different, later pass with different questions.
- **Diverge deliberately, converge deliberately.** Know which mode you are in and signal it ("next 20 minutes are generation only — flaws stay unmentioned").
- **Constraints breed ideas.** A blank page paralyzes; a sharp constraint ("one colour", "type only", "no new shapes beyond the logo") forces the search for unexpected solutions. Constraints are inputs to ideation, not enemies of it.
- **Variation beats iteration of one.** Explore *different* concepts, not progressively smaller refinements of the first one. Diversity is the point (see [Moodboards](moodboards.md) §4.2 on three distinct directions).
- **Selection by criteria, not taste.** Ideas are compared against explicit criteria tied to the brief — fit to objectives, distinctiveness, feasibility, accessibility, extensibility — never ranked by "which I like best".

## 4. How it works

### 4.1 The techniques

**Crazy 8s.** A fast sketching exercise popularised by the Google Ventures Design Sprint: fold a sheet into eight panels and sketch eight distinct ideas in eight minutes — roughly one per minute. The rules matter: sketch, don't polish; no idea may repeat; you must fill all eight slots even when you "run out" at four, because ideas five to eight are where the obvious options end and the interesting ones start. For UI work, run it per screen state (empty state, error state); for graphic work, per artefact face. Works solo or in groups; in groups, keep sketches private until the sharing round to avoid anchoring. `[search-verified]`

**Thumbnail sketching.** The older, quieter parent of Crazy 8s: many small, fast, low-fidelity compositions (a few centimetres each) exploring layout, hierarchy and shape language before committing to one. Thumbnails are cheap enough that composition problems get solved at stamp size, where fixing them costs seconds instead of hours. Standard practice in graphic design education. `[canonical]`

**SCAMPER.** A checklist for transforming an existing idea into variants — Substitute, Combine, Adapt, Modify/Magnify, Put to another use, Eliminate, Reverse/Rearrange. Originating from Alex Osborn's brainstorming checklist and popularised by Bob Eberle as a creativity-teaching acronym, SCAMPER suits design work especially well when *re*-designing something that exists (a page, a poster, a kit component). Applied to an event badge: Substitute the material metaphor (paper → fabric laminate); Combine badge and schedule; Adapt the poster's cropped-type rule to the badge format; Magnify the logo; Eliminate all text but the name; Reverse the colour scheme. `[search-verified]`

**Forced connections.** Deliberately collide the problem with an unrelated stimulus — a random word, object, or image — and mine the collision ("queue" + conference badge → badges that form a visible queue pattern on the lanyard wall?). The stimulus must be truly unrelated to work; related stimuli just confirm what you already think. Useful when a direction feels exhausted. `[canonical]`

**Worst possible idea.** Invert the goal and generate deliberately terrible solutions ("make the schedule impossible to read", "hide the price until the third screen"), then reverse each into an insight: the failures you invent name the real constraints and success criteria — and often suggest the fix directly ("hide the price" inverted → "price visible at first glance" becomes a requirement). It also lowers the stakes: generating bad ideas on purpose breaks the fear of producing bad ideas by accident. Popularised in Design Sprint teaching. `[search-verified]` (method documented in sprint practice; use as canon)

**Constraint-based prompts.** Assign yourself artificial constraints that the brief does not impose, to force novelty: one colour only; type only, no imagery; everything centred; everything asymmetric; only the logo's own shapes as graphic elements. Each prompt produces a family of ideas and — often — a rule worth keeping (see [Moodboards](moodboards.md) §4.5). Constraint prompts are also how you test a rule's strength: if a direction survives "one colour only", its hierarchy device is robust.

### 4.2 Generating before judging

Osborn's classic brainstorming rules encode the principle: defer judgment, go for quantity, welcome wild ideas, build on others' ideas. `[canonical]` In practice, for an agent or a solo designer:

1. **Set a quota before starting.** "Twelve concepts for the badge" is a prompt that outperforms "some ideas". Quotas push past the obvious first four or five.
2. **Write, don't evaluate.** Capture each idea in one line or one thumbnail. The phrase "that won't work because…" is banned during generation; if you must, note the objection *beside* the idea for the later pass.
3. **Vary the technique.** Run one round per technique — thumbnails, then SCAMPER on the best thumbnail, then a constraint prompt — rather than one long undifferentiated session. Different techniques produce different *kinds* of ideas.
4. **Take a break between modes.** Even minutes of separation reduce carry-over of the judging mindset into generation and vice versa.
5. **Expect most ideas to die.** A productive session often yields one keeper from a dozen. The discard rate is not waste; it is the mechanism by which the keeper is findable.

### 4.3 Avoiding premature convergence on the first attractive idea

This is the failure ideation exists to prevent, and it deserves its own mechanics. Why it happens:

- **Anchoring:** the first idea becomes the reference point; later ideas are experienced as deviations from it rather than as equals.
- **Aesthetic-usability effect and polish bias:** the first idea gets refined first, so it *is* better-looking by the time alternatives are compared — a self-fulfilling advantage.
- **Sunk cost and defending:** effort invested in idea #1 creates ownership; critique of it feels personal, critique of alternatives feels free.
- **Fluency illusion:** early ideas come from memory (known patterns), so they arrive fast and feel right; original ideas arrive slower and feel wrong initially.

Countermeasures that work:

| Countermeasure | How |
| --- | --- |
| Quota before refinement | No refinement of any idea until the quota is met; the first idea gets no head start |
| Equal-fidelity comparison | Present all candidates at the same fidelity (see [Moodboards](moodboards.md) §4.6) — never refine the front-runner before comparing |
| Delay the decision | Generate, then wait (hours if possible, minutes if not) before judging; the gap weakens anchoring |
| Parallel variants, not serial | Build variants side-by-side in the same file/session rather than testing one then another |
| Separate modes formally | Judge in a different pass with different questions (criteria, not "do I like it") |
| Assign devil's advocacy | For the attractive front-runner, generate its three strongest objections before it can win |
| Track the discard rate | If session after session produces "the first idea was best", that pattern is a warning about process, not evidence of genius |

### 4.4 Selecting with criteria, not taste votes

Convergence is a scoring exercise, not a vote on vibes. Build the criteria from the brief and discovery implications, then score every surviving candidate.

Working criterion set (adapt weights per project):

| Criterion | Question | Evidence source |
| --- | --- | --- |
| Objective fit | Does it serve the stated communication objective? | Problem statement, [Research and discovery](research-and-discovery.md) |
| Audience fit | Will the target segments read it correctly? | Audience characterisation |
| Distinctiveness | Does it differentiate, and is the differentiation *intended*? | Landscape scan |
| Feasibility | Can it be produced at required quality within budget/deadline? | Constraint list |
| Accessibility | Can it meet contrast, legibility and perceptibility requirements? | WCAG maths; [Accessible colour](../accessibility/accessible-colour.md) |
| Extensibility | Does it survive application across the full kit (badge → website → banner)? | Application check |
| Constraint harmony | Does it respect the fixed elements (logo, mandated colours)? | Visual audit |

Method: score each candidate 1–3 per criterion *with a written reason for every score*. The written reasons are the value — they convert a taste vote into a documented decision (see [Brand guidelines](../branding/brand-guidelines.md) on rationale). Dot voting is acceptable only for *narrowing a large pool*, never for the final choice: unstructured voting rewards the familiar and the loud, and hides the reasoning.

## 5. Practical application

### 5.1 Agent-scale ideation session (event badge, fixed logo)

1. **Frame:** objective = "recognisable at 3 metres, name legible, harmonises with the fixed logo"; constraints from the visual audit.
2. **Generate (no judging):** eight thumbnails in eight minutes (Crazy 8s pattern); then SCAMPER the two most distinct; then one constraint prompt ("logo shapes only").
3. **Pool:** ~14 candidates, recorded one line each.
4. **Gap:** stop; on return, strike duplicates and dead-on-arrival items (leave them visible — the record matters).
5. **Score:** five survivors scored on the criterion table with reasons; two tie on score; tie broken by extensibility, with the reason written down.
6. **Forward:** the three most distinct survivors become the three moodboard directions — ideation output is moodboard input.

### 5.2 Classic design-education exercises

- **Crazy 8s** as §4.1. `[search-verified]` — the canonical sprint warm-up.
- **30 Circles** (IDEO/d.school canon): 30 blank circles, 3 minutes, turn as many as possible into objects. Trains fluency and shows how perfectionism kills quantity. `[canonical]`
- **SCAMPER** `[search-verified]` — often taught as a worksheet: one existing design, seven rows, one variant per row.
- **Worst possible idea** `[search-verified]` — often run before requirements gathering precisely because the inverted failures elicit criteria.
- **Thumbnail sketching** `[canonical]` — standard in graphic design curricula as the first response to any brief.

## 6. Decision framework

| Situation | Recommended technique |
| --- | --- |
| Blank page at project start | Thumbnails + Crazy 8s to build the pool fast |
| Redesign of something existing | SCAMPER on the current design; constraint prompts to test its rules |
| Direction feels exhausted | Forced connections with a truly random stimulus |
| Team afraid of bad ideas | Worst possible idea round, then inversion |
| Suspected premature convergence | Quota + equal-fidelity parallel variants before any refinement |
| Large pool needs narrowing | Dot voting to shortlist, then criteria scoring for the decision |
| Final choice between 2–3 candidates | Criteria scoring table with written reasons |

## 7. Examples

- **Badge ideation (§5.1):** quota of eight produced seven near-duplicates of "standard layout" — and one outlier (type cropped by the logo's geometry) that scored highest on distinctiveness and became the direction. The outlier only existed because the quota forbade stopping at five.
- **Premature convergence caught:** an agent's first landing-page concept was polished and presented alone; the stakeholder approved it from politeness. Re-run properly: three equal-fidelity variants, criteria scoring revealed the first one failed the mobile-first implication entirely. Cost of the catch: one hour. Cost of not catching it: the build.
- **Worst-possible idea yielding criteria:** "make the ticket page impossible to scan" produced "put each price on a separate screen", inverted into a real requirement — "all prices visible in one view" — that outlasted every design round.

## 8. Common mistakes

- **Judging while generating.** Kills quantity and keeps only safe ideas. Separate the modes formally.
- **Stopping at the first good idea.** The quota exists precisely because "good" at idea #1 is an anchor, not a verdict.
- **Refining the front-runner early.** Unequal fidelity is a hidden vote. Compare at equal fidelity (see [Moodboards](moodboards.md)).
- **Brainstorm without a frame.** "Give me ideas" produces generic output; frame with the objective, audience and one sharp constraint first.
- **Dot voting as the decision.** It narrows, it does not decide; and it rewards loud voices and familiar patterns.
- **Keeping the record invisible.** Discarded ideas and scoring reasons are the documentation of *why* the winner won; losing them makes every later challenge restart from zero (see [Iteration](iteration.md)).
- **Treating constraints as obstacles.** The brief's fixed logo and mandated colours are the most productive ideation prompts available; use them, don't route around them.
- **Accepting AI's first output as the pool.** A single AI-generated concept is the definition of premature convergence; prompt for many distinct variants and re-score them yourself (see [AI-assisted design](ai-assisted-design.md)).

## 9. Evaluation checklist

- [ ] A quota was set and met before any evaluation happened.
- [ ] The pool contains structurally different ideas (different hierarchy devices, imagery treatments, layout logic), not variations on one.
- [ ] Generation and judging happened in separate passes, with at least a short gap.
- [ ] Candidates were compared at equal fidelity, side-by-side.
- [ ] Selection used written criteria tied to the brief, with a reason recorded for every score.
- [ ] The front-runner's three strongest objections were articulated before it won.
- [ ] The discard pool and scoring record are preserved in the decision documentation.
- [ ] The winner is described as "selected because…" — not "I liked…".

## 10. Related topics

- [Design thinking](design-thinking.md) — where ideation sits; diverge/converge cycles.
- [Moodboards](moodboards.md) — how surviving candidates become three presentable directions.
- [Research and discovery](research-and-discovery.md) — where criteria and constraints come from.
- [Iteration](iteration.md) — deliberate change after selection; what to change between rounds.
- [Design critique](design-critique.md) — the structured judging pass that convergence deserves.
- [Design quality framework](../evaluation/design-quality-framework.md) — the evaluation vocabulary for criteria.
- [Composition](../foundations/composition.md) — the craft axes thumbnails manipulate.
- [Brand personality](../branding/brand-personality.md) — the attribute targets ideas must hit.

## 11. References

- Google Design Sprint Kit, "Crazy 8's" — "a fast sketching exercise that challenges people to sketch eight distinct ideas in eight minutes"; core Design Sprint method. `[search-verified]` https://designsprintkit.withgoogle.com/methodology/phase3-sketch/crazy-8s (accessed 2026-11-23)
- Google Ventures, "The Design Sprint" — five-day process framing. `[search-verified]` https://www.gv.com/sprint (accessed 2026-11-23)
- The Decision Lab, "SCAMPER" — acronym: Substitute, Combine, Adapt, Modify, Put to another use, Eliminate, Reverse. `[search-verified]` https://thedecisionlab.com/reference-guide/philosophy/scamper (accessed 2026-11-23)
- Designorate, "A Guide to the SCAMPER Technique for Design Thinking" (2015) — SCAMPER's use in design practice. `[search-verified]` https://www.designorate.com/a-guide-to-the-scamper-technique-for-design-thinking (accessed 2026-11-23)
- Wikipedia, "SCAMPER" — structure and educational origin of the checklist. `[search-verified]` https://en.wikipedia.org/wiki/SCAMPER (accessed 2026-11-23)
- Bob Eberle, *SCAMPER: Creative Games and Activities for Developing Imagination* — the popularising source of the acronym, built on Alex Osborn's brainstorming checklist. `[canonical]`
- Alex Osborn, *Applied Imagination* (1953) — original brainstorming rules: defer judgment, quantity breeds quality, welcome wild ideas, combine and improve. `[canonical]`
- Stanford d.school, *Bootcamp Bootleg* — 30 Circles and related fluency exercises. `[canonical]`
- Jake Knapp, *Sprint* (2016) — Crazy 8s and worst-possible-idea in sprint context. `[canonical]`
- Premature-convergence mechanics (anchoring, polish bias, sunk cost) are this file's synthesis of standard design-education teaching; not attributed to a single source.
