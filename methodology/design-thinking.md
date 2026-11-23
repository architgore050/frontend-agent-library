# Design thinking

## 1. What is it?

Design thinking is a human-centred, non-linear process for solving problems that combines empathy for the people affected, disciplined problem definition, divergent idea generation, and early prototyping with testing. The best-known articulation of a five-stage model — Empathise, Define, Ideate, Prototype, Test — is associated with Stanford University's d.school and the design firm IDEO, both of which popularised the model in the 2000s. A second widely used framework, the Double Diamond, was introduced by the UK Design Council (first published in 2005 and later repackaged as the "Framework for Innovation") and describes four phases — Discover, Define, Develop, Deliver — organised as two diamonds of divergent and convergent thinking.

Neither model is a law of nature. They are teaching devices: simplified maps that make the *shape* of a good design process visible — going wide before narrowing, defining the problem before generating answers, and testing before committing. For an agent, the value is less in following the stages ritually and more in knowing which mode of thinking (empathy, definition, divergence, convergence, testing) a given task needs.

## 2. Why does it matter?

Design work fails most often for process reasons, not craft reasons. Beautifully executed artefacts routinely ship with the wrong problem, the wrong audience, or an idea that was never tested against reality. Design thinking exists because these failures are predictable and preventable: most bad outcomes trace back to skipping empathy (nobody looked at the audience), skipping definition (the brief was ambiguous and nobody noticed), or converging too early (the first attractive idea won).

For an AI agent the frameworks have a second, practical value: they are shared vocabulary. When a client, a designer, or a reviewer says "we're still in discovery" or "this is too early to converge", the agent must know what that implies — more references, more questions, no final direction yet. An agent that can locate its task on the map can also choose the right deliverable: research notes during Discover, a problem statement at the end of Define, three distinct directions during Develop, a polished artefact only at Deliver.

## 3. Core principles

The frameworks share a small number of load-bearing principles. Everything else is scaffolding.

| Principle | What it means | What happens without it |
| --- | --- | --- |
| Human-centred framing | Decisions are justified by what real audiences need, perceive and do, not by what the designer likes | Output that satisfies the author, not the audience |
| Divergence before convergence | Generate many options before choosing; go wide on the problem before narrowing the solution | Premature convergence on the first attractive idea (see [Ideation](ideation.md)) |
| Problem definition as its own step | A written, agreed problem statement separates "what are we solving" from "how" | Endless rework because nobody knows what "done" or "right" means |
| Tangibility early | Prototypes and sketches make thinking testable sooner than words do | Debates about abstractions that no artefact can settle |
| Iteration and testing | Feedback loops are built into the process, not bolted on at the end | One-shot delivery, defended rather than revised |
| Reframing | The problem itself may be re-defined as understanding deepens | Solving the wrong problem efficiently |

These principles are established design canon (IDEO and d.school teaching, Design Council publications). When they conflict with a client's explicit, informed preference, the client wins — but the agent should name the trade-off it is accepting.

## 4. How it works

### 4.1 The d.school five stages

The Stanford d.school model describes five stages. They are presented sequentially for teaching, but in practice the model is explicitly non-linear: teams loop back as they learn.

1. **Empathise** — understand the people you design for: observe behaviour, interview, immerse. Output: raw insight about needs, motivations and constraints.
2. **Define** — synthesise that insight into a focused, actionable problem statement (often phrased as a point of view: user, need, insight). Output: a problem worth solving, agreed by stakeholders.
3. **Ideate** — generate many candidate answers, from obvious to wild, before judging. Output: a large pool of options (see [Ideation](ideation.md)).
4. **Prototype** — make selected ideas tangible cheaply and quickly: sketches, mock-ups, storyboards, rough builds. Output: artefacts that invite reaction.
5. **Test** — put prototypes in front of real people, observe, collect feedback — and feed it back into earlier stages. Output: validated, revised directions.

The classic d.school teaching documents stress that the stages are *modes*, not gates: skilled practitioners slide between them. This matters for agents: discovering mid-project that the problem statement was wrong is a normal event, not a process failure.

### 4.2 The Double Diamond

The Design Council's Double Diamond describes four phases in two diamonds. The first diamond is about the problem; the second is about the solution.

- **Discover** (diverge) — explore the problem space widely: research, stakeholder input, audits, interviews. Deliberately broad.
- **Define** (converge) — synthesise findings into a clear, agreed brief or problem definition.
- **Develop** (diverge) — explore solutions widely: moodboards, sketches, multiple design directions, prototypes.
- **Deliver** (converge) — test, select, refine, produce and launch the chosen solution.

The diamond shape encodes the core rhythm: each diamond widens (divergent thinking) then narrows (convergent thinking). The most common real-world distortion is collapsing both diamonds into one straight line — "brief in, artwork out" — which silently skips problem exploration and idea exploration at once.

### 4.3 How the models relate

| Work phase | d.school stage | Double diamond phase | Thinking mode |
| --- | --- | --- | --- |
| Understanding the audience and context | Empathise | Discover | Divergent |
| Writing the problem statement / brief | Define | Define | Convergent |
| Exploring directions, moodboards, sketches | Ideate | Develop (start) | Divergent |
| Prototyping and testing candidates | Prototype + Test | Develop → Deliver | Mixed |
| Production and handover | (implied by Test) | Deliver | Convergent |

A third model, the Design Sprint (popularised by Jake Knapp at Google Ventures, a five-day compressed cycle from problem to tested prototype), is useful for agents because it shows the same rhythm at a smaller timescale: map → sketch → decide → prototype → test.

## 5. Practical application

### 5.1 Mapping the frameworks to design work an agent actually does

For typical frontend/brand design tasks, the frameworks translate into a concrete sequence of agent deliverables:

1. **Discover / Empathise** — read the brief and all supplied material; run secondary research; collect stakeholder answers; audit existing brand assets. Deliverable: research notes and a list of constraints (see [Research and discovery](research-and-discovery.md)).
2. **Define** — write a one-paragraph problem statement and a set of design implications ("the audience is X, therefore Y must hold"). Deliverable: an agreed brief. If the brief is ambiguous, this is where the agent asks questions — before generating anything visual.
3. **Develop / Ideate** — build a moodboard with multiple distinct directions; extract attributes; generate candidate approaches. Deliverable: 2–3 directions with stated attributes (see [Moodboards](moodboards.md), [Ideation](ideation.md)).
4. **Prototype / Test** — apply one direction to a real artefact (a page, a poster, a brand kit page); run a structured self-critique; revise. Deliverable: iterations plus a critique record (see [Design critique](design-critique.md), [Iteration](iteration.md)).
5. **Deliver** — produce final assets, document decisions and rationale, record AI involvement where relevant (see [AI-assisted design](ai-assisted-design.md)).

### 5.2 Recognising which mode you are in

Agents drift out of the correct mode when they lack an explicit signal. Useful checks:

- Asked for "something creative" with no audience information? You are in Discover/Empathise: gather before generating.
- Stakeholders disagree about which direction to pick? Return to Define: restate the objectives and criteria before voting.
- A design exists but "something feels off"? You are in Develop/Test: run a structured critique, not a vibe check.
- The artefact is nearly final and someone proposes a new concept? Check the cost of re-opening the first diamond; sometimes the honest answer is "that is a new project".

### 5.3 Exercises from established design education

- **The wallet exercise** (d.school Bootcamp Bootleg tradition): pairs interview each other about the contents and meaning of their wallets, then redesign one for the partner. Teaches empathise → define → ideate → prototype → test in under two hours. `[canonical]`
- **"How might we…?" reframing** (IDEO canon): turn every insight or complaint into a "How might we…" question, converting problems into prompts. "Users find the form long" → "How might we reduce the number of decisions the form asks for?" `[canonical]`
- **30 Circles** (attributed to IDEO/d.school creativity exercises): three minutes, thirty circles, turn as many as possible into recognisable objects. Teaches fluency over perfection — most people finish far fewer circles when they polish each one. `[canonical]`
- **Crazy 8s** (Google Ventures Design Sprint): eight sketches in eight minutes. A divergence exercise; see [Ideation](ideation.md). `[search-verified]`

## 6. Decision framework

Use design thinking where it helps; know where it is the wrong tool.

| Situation | Recommended posture |
| --- | --- |
| Ambiguous brief, unclear audience, new brand | Full framework: invest heavily in Discover/Define before any visual work |
| Established brand system, routine production task | Compress discovery; go straight to Define (restate constraints) → Deliver, with a critique pass |
| Time-boxed sprint, one artefact | Design Sprint pattern: one day of divergence maximum, then converge hard |
| Client has already decided the direction | Do not run process theatre; execute, but still run the critique checklist to catch defects |
| Exploratory art direction, no fixed deliverable | Stay in divergence deliberately longer; multiple moodboards before any high-fidelity work |

**Where design thinking is criticised — and when the criticism is right.** Common criticisms: (1) *process theatre* — meetings, sticky notes and stage names that consume time without changing the outcome; (2) the linear cartoon encourages teams to think they have "done empathy" after two interviews; (3) for well-understood, high-craft work (e.g. refining an existing design system), the ceremony adds nothing. These criticisms are fair when the framework is followed ritually. The agent's defence is proportionality: scale the process to the ambiguity of the problem. A one-hour task needs a five-line version of the process (constraints → three options → self-critique → pick); a rebrand needs the full diamonds.

## 7. Examples

### 7.1 Event brand kit extension (the repository's reference scenario)

- **Discover/Empathise:** the fixed event logo exists; the agent audits where it came from, what palette and type it already implies, who attends the event (audience analysis) and what artefacts are needed (website header, badges, slides, social banners).
- **Define:** problem statement — "extend the existing logo into a coherent kit that reads as one family across print and screen, without altering the mark".
- **Develop:** three moodboard directions built from attributes extracted from the logo (see the worked example in [Moodboards](moodboards.md)).
- **Prototype/Test:** each direction applied to one shared artefact (e.g. a badge) so stakeholders compare like with like; structured critique per artefact.
- **Deliver:** chosen direction finalised into a token table, typography and colour rules, exported assets, decision log.

### 7.2 A compressed run

A client asks for "a quick landing page tweak to make the pricing clearer". Full process is disproportionate. The agent runs: Empathise/Discover compressed to reading the page and one question to the stakeholder; Define — "visitors cannot compare plans"; Develop — two layout variants of the pricing block; Test — self-critique against the communication objective; Deliver — one variant applied. Total process overhead: minutes, not days.

## 8. Common mistakes

- **Running the stages as a checklist.** Doing two interviews and declaring empathy complete. The stages are modes to revisit, not gates to clear once.
- **Skipping Define.** Divergent work without an agreed problem statement produces three directions stakeholders cannot compare because nobody remembers what problem they solve.
- **Converging inside the moodboard.** Presenting one direction that is really the first idea decorated. See [Ideation](ideation.md) on premature convergence.
- **Process theatre.** Workshops and stage names with no artefacts or decisions between them. If a stage produces nothing, shorten it.
- **Testing on the wrong people.** Asking team members who already know the project to stand in for the audience. Their knowledge masks confusion the real audience will feel.
- **Treating the model as approval for stopping.** "We did Test, so we are done." Iteration stops on evidence (see [Iteration](iteration.md)), not on stage completion.
- **Using the vocabulary to hide decisions.** "It's still discovery" as a way of avoiding commitment. Frameworks are for making decisions legible, not deferring them.

## 9. Evaluation checklist

- [ ] A written problem statement exists and was agreed before visual work started.
- [ ] The audience is described from evidence, not from the author's assumption.
- [ ] At least two, ideally three, genuinely distinct directions were generated before one was chosen (divergence happened).
- [ ] The choice between directions is justified by criteria tied to the problem statement, not by the author's taste.
- [ ] At least one artefact was reviewed with a structured critique before delivery.
- [ ] The process was scaled to the ambiguity: trivial tasks did not get workshop theatre, ambiguous tasks did not get one-shot delivery.
- [ ] Decisions and their rationale are documented somewhere a future agent can find them.

## 10. Related topics

- [Ideation](ideation.md) — divergence techniques and how to avoid premature convergence.
- [Moodboards](moodboards.md) — the concrete Develop-phase instrument.
- [Research and discovery](research-and-discovery.md) — the concrete Discover-phase instrument.
- [Iteration](iteration.md) — how deliberate change rounds work after the first prototype.
- [Design critique](design-critique.md) — the structured review that powers the Test/Define loops.
- [AI-assisted design](ai-assisted-design.md) — how each stage is executed with AI tools and what still needs human approval.
- [Brand discovery](../branding/brand-discovery.md) — the branding-domain counterpart of the Discover/Define diamonds.
- [Design quality framework](../evaluation/design-quality-framework.md) — the evaluation counterpart used when converging.

## 11. References

- Stanford d.school, *An Introduction to Design Thinking: Process Guide* (Institute of Design at Stanford) — five-stage model: Empathise, Define, Ideate, Prototype, Test; stages as modes, non-linear. `[search-verified]` https://web.stanford.edu/~mshanks/MichaelShanks/files/509554.pdf (accessed 2026-11-23)
- Interaction Design Foundation, "The 5 Stages in the Design Thinking Process". `[search-verified]` https://ixdf.org/literature/article/5-stages-in-the-design-thinking-process (accessed 2026-11-23)
- Design Council (UK), "Framework for Innovation" (the Double Diamond as Framework for Innovation). `[search-verified]` https://www.designcouncil.org.uk/resources/framework-for-innovation (accessed 2026-11-23 — page served a bot-verification interstitial; attribution verified via search result metadata and the Wikipedia summary below)
- Wikipedia, "Double Diamond (design process model)" — Design Council UK attribution; divergent/convergent definition. `[search-verified]` https://en.wikipedia.org/wiki/Double_Diamond_(design_process_model) (accessed 2026-11-23)
- Google Ventures, "The Design Sprint" — five-day process: design, prototype, test ideas with customers. `[search-verified]` https://www.gv.com/sprint (accessed 2026-11-23)
- Jake Knapp, *Sprint: How to Solve Big Problems and Test New Ideas in Just Five Days* (2016) — Design Sprint canon. `[canonical]`
- IDEO, design thinking method cards and teaching materials — "How might we" framing; human-centred design canon. `[canonical]`
- Stanford d.school, *Bootcamp Bootleg* — wallet exercise, 30 Circles and other classroom exercises. `[canonical]`
