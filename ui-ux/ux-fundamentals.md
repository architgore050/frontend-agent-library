# UX Fundamentals

## 1. What is it?

User experience (UX) design is the practice of shaping how a person interacts with a product so that their goals are achieved efficiently, confidently and without avoidable frustration. It is distinct from — but precedes — visual interface design: UX decides what the user must do, in what order, with what support, before a single pixel of the interface is styled. The discipline rests on the study of users as they really are, not as we imagine them to be: people with limited attention, incomplete knowledge of the system, and urgent goals. Core concepts in this file — mental models, affordances, feedback, cognitive load and error prevention — form the vocabulary that every later decision (layout, components, interaction timing) depends on.

The term covers a family of activities: user research (learning what people need), information architecture (organising content, see [Information architecture](information-architecture.md)), interaction design (defining behaviour over time, see [Interaction design](interaction-design.md)), and usability evaluation (checking whether the result works). This file gives the foundations that cut across all four.

## 2. Why does it matter?

Poor UX has measurable costs: users abandon tasks, call support, make errors with real consequences (wrong address, failed payment, lost data), and quietly churn. Good UX has the mirror-image benefits — higher completion rates, fewer support tickets, and trust that transfers to the rest of the brand. For an AI agent producing interfaces, the concepts here are the fastest route to quality: most "obviously broken" interfaces fail not on aesthetics but on missing feedback, unaffordant controls, overwhelming density or unprotected escape routes.

UX also protects accessibility and inclusivity by construction. A design that relies on users holding a precise mental model of the system, remembering hidden steps or recovering from preventable errors disadvantages exactly the users with the least time, skill or patience. Designing for the distracted first-time user under stress produces interfaces that work better for everyone.

Finally, UX is the layer that decides *whether the design is finished*: a screen is not done when it looks right, but when a representative user can reach their goal through it, recover from a mistake in it, and explain afterwards what it does. Every later file in this library supplies techniques; this one supplies the definition of done.

## 3. Core principles

### 3.1 Mental models

A mental model is the user's internal, approximate theory of how the system works. Don Norman distinguished three entities: the *designer's model* (how the designer thinks it works), the *user's model* (what the user believes) and the *system image* (everything the user can actually see, hear and touch) [canonical]. The system image is the only channel through which the designer's model reaches the user; if the interface contradicts the user's prior model — a shopping basket that empties without confirmation, a "Save" that silently discards — the user will misbehave in perfectly logical ways given their wrong theory.

Design consequences: build on models users already have (files and folders, shopping basket, playback controls); when the system must deviate from a familiar model, teach the new model inside the interface itself, not in documentation. Users' mental models are drawn from other software they use, which is why consistency with platform conventions matters (see heuristic 4 below).

### 3.2 Affordances and signifiers

An affordance is a relationship between an object and an agent that makes a certain action possible — a flat plate affords pushing, a handle affords pulling. Don Norman popularised the term for interface design, and later sharpened it: what designers actually control is *signifiers* — perceivable cues that communicate where an affordance exists [canonical]. A button that looks raised or filled signals clickability; a link that is blue and underlined signals navigation; a drag handle of six dots signals reordering.

The practical rule for interfaces: every actionable element must visibly declare itself, and every thing that looks actionable must be. Flat design eroded this when it stripped affordance cues from buttons; the industry's recovery (raised or filled primaries, distinct link styling) shows that perceived affordance is not decoration but information. Distinguish affordance (the possibility of action) from signifier (the sign that advertises it): a gesture-only control has an affordance but no signifier and will be undiscovered.

### 3.3 Feedback

Feedback is the system's response to a user action, telling the user what just happened and what state the system is now in. Effective feedback is immediate (before the user doubts the input was registered), visible (in the user's current focus of attention, not a distant corner), proportional (major actions get major confirmations, minor ones barely a ripple) and honest (never claims success it did not achieve). Nielsen's first usability heuristic — visibility of system status — is precisely a feedback principle [accessed].

The perceptual *timing* rules for feedback (what must happen within 0.1 s, 1 s, 10 s) are a discipline of their own and are covered in [Interaction design](interaction-design.md). At the principle level: no feedback is the single most reliable way to make a working system feel broken, because users repeat inputs, abandon processes or assume failure.

### 3.4 Cognitive load

Cognitive load is the demand a task places on working memory. It is usefully split into *intrinsic* load (the inherent difficulty of the task), *extraneous* load (difficulty added by the design itself — deciphering labels, hunting for controls, parsing dense screens) and *germane* load (the useful effort of actually learning or solving) [canonical — cognitive load theory, John Sweller]. Design should minimise the extraneous portion. Classic working-memory constraints apply: Miller's estimate of roughly seven chunks (Miller, *The Magical Number Seven, Plus or Minus Two*, 1956) and the later revision towards about four chunks (Cowan, 2001) both point the same way — users cannot hold many items, steps or options in mind at once [canonical].

Design tactics that follow: chunk long processes into steps (checkout as stages, not one page of 40 fields); make options visible rather than remembered (Nielsen's "recognition rather than recall" heuristic [accessed]); never force users to carry information from one screen to another (display the item name next to the delete confirmation); use defaults so the common case requires no thought; and offload memory onto the interface (show the selected plan during payment). Density guidelines follow the same logic: a wall of 30 simultaneous choices is not "rich", it is extraneous load wearing a data-rich costume — grouping, spacing and hierarchy (see [Spacing and proportion](../layout/spacing-and-proportion.md)) are load-management tools as much as aesthetic ones.

### 3.5 Constraints and error prevention

Constraints deliberately limit what the user can do, so that some errors become impossible rather than merely unlikely. Disable a submit button until required fields are valid; restrict a date input to real dates; make destructive actions require an explicit confirm. Norman lists constraints alongside affordances as fundamental design tools [canonical]. Error prevention is cheaper than error recovery: a designer's 5 minutes of constraint saves thousands of users' lost work. The fuller design playbook — slips versus mistakes, guard rails, undo — is in section 5.6.

### 3.6 Usability heuristics (Nielsen)

Jakob Nielsen and Rolf Molich developed a set of usability heuristics in 1990; Nielsen refined them in 1994 by factor analysis of 249 usability problems, and they have remained unchanged since [accessed]. They remain the most widely used expert-review checklist in the field:

| # | Heuristic | Core demand |
|---|---|---|
| 1 | Visibility of system status | Keep users informed through timely, appropriate feedback |
| 2 | Match between system and the real world | Speak the user's language; familiar words and conventions |
| 3 | User control and freedom | Provide clearly marked "emergency exits" — undo, cancel, back |
| 4 | Consistency and standards | Follow platform and product conventions; same words, same meaning |
| 5 | Error prevention | Prevent errors in the first place; confirm high-cost actions |
| 6 | Recognition rather than recall | Make objects, actions and options visible, not memorised |
| 7 | Flexibility and efficiency of use | Offer accelerators for experts; novices still supported |
| 8 | Aesthetic and minimalist design | Exclude irrelevant information that competes with essential content |
| 9 | Help users recognise, diagnose and recover from errors | Plain-language errors stating the problem and the fix |
| 10 | Help and documentation | Searchable, task-focused help listing concrete steps |

Treat these as *heuristics* — experience-based evaluation rules — not as laws that override evidence. They are used in heuristic evaluation: several reviewers walk an interface, checking each screen against each heuristic, then merge and severity-rate the findings. For an AI agent, the table above is a self-review checklist that catches a large fraction of common interface failures before any user ever sees the output.

### 3.7 Other usable principles worth knowing

Shneiderman's Eight Golden Rules of Interface Design (strive for consistency; enable frequent users to use shortcuts; offer informative feedback; design dialogs to yield closure; offer error handling; permit easy reversal of actions; support internal locus of control; reduce short-term memory load) [canonical] overlap heavily with Nielsen's list, which is itself evidence that these are stable findings rather than one author's taste. Fitts's law (movement time grows with distance to a target and shrinks with its size; Paul Fitts, 1954) justifies large, near touch targets and edge-anchored controls. Hick's law (choice reaction time grows with the number of options) justifies progressive disclosure and sensible defaults, though it applies to *random search among unfamiliar options* — not to well-learned menus [canonical]. Where these established principles conflict in a specific case, run a small user test; the principles frame the question, they do not answer it.

### 3.8 Measuring usability

Usability is measurable, and measurement is what turns "it feels awkward" into a prioritised defect list. The established core metrics:

| Metric | What it captures | How it is gathered |
|---|---|---|
| Task completion rate | Did users finish the defined task, unaided? | Moderated or unmoderated task tests |
| Time on task | How much effort the task costs | Task test timing (median, not mean — outliers skew means) |
| Error rate | Slips, wrong turns, retries per task | Observed task tests; logged analytics |
| Single Ease Question (SEQ) | Perceived difficulty of one task | One 7-point question immediately after each task |
| System Usability Scale (SUS) | Overall perceived usability of a product | 10-item questionnaire after a session [canonical] |
| Drop-off / funnel analytics | Where large populations abandon | Product analytics on live flows |

Two practices make these numbers usable rather than decorative. First, define tasks concretely ("change the delivery address of your most recent order") — vague tasks produce vague data. Second, treat a baseline as essential: a completion rate means nothing until it is compared against the previous design or a benchmark; iterate one variable at a time so improvements are attributable.

### 3.9 Jakob's Law: convention as an asset

Jakob's law — attributed to Jakob Nielsen's observation that users spend most of their time on *other* sites, and popularised in Jon Yablonski's *Laws of UX* collection [canonical] — explains why conventions are an asset rather than a creativity tax. Users arrive with habits formed across everything they have ever used: the cart icon top-right, the logo linking home, blue underlined links, the settings gear. Deviating from an entrenched convention forces every visitor to re-learn your interface, and the re-learning cost is paid per visitor, forever.

The practical stance: adopt conventions for *structural* decisions (navigation position, action placement, icon meanings); reserve invention for where the product genuinely differs, and teach the difference in the interface when you do. "Original" navigation is the most expensive originality in product design — users do not experience it as a fresh idea, they experience it as friction.

## 4. How it works

The UX process is a loop, not a waterfall: understand users → define the problem → design → test → revise. In practice for web and product work:

1. **Research** establishes who the users are, what they are trying to achieve, and under what conditions. Methods range from qualitative (interviews, observation) to quantitative (analytics, surveys).
2. **Journey and task mapping** turns research into a sequence: what the user does, thinks and feels from "has a need" to "goal met". It exposes the moments where the experience is won or lost.
3. **Architecture and interaction design** organise the content ([Information architecture](information-architecture.md)) and define the behaviour of the interface ([Interaction design](interaction-design.md)).
4. **Interface realisation** builds the screens from components with correct states — the subject of [UI fundamentals](ui-fundamentals.md) — inside a responsive layout ([Responsive design](responsive-design.md)).
5. **Evaluation** closes the loop: usability testing, heuristic review and measurement of task completion.

In agent-driven work the loop compresses but never disappears: research becomes the brief's stated audience and goals plus any available analytics; the "test" becomes the evaluation checklists of [Website visual QA](../evaluation/website-visual-qa.md) applied to the built output, plus real-user observation whenever the project allows it. What must never be skipped is the framing step — an interface produced without a stated user goal can be visually flawless and still answer no useful question.

Evaluation deserves emphasis: usability problems are notoriously invisible to their designers, because the designer holds a perfect mental model by construction. Even a five-user test (Nielsen's widely cited small-sample guidance for qualitative usability testing [canonical]) surfaces most of the major problems in a design. The cheap minimum viable loop is: define one concrete task ("buy a ticket for the 14th using a discount code"), hand a real interface to a real person who is not the designer, watch silently, note every hesitation, wrong turn and spoken confusion.

### 4.1 Framing before making

A process discipline that separates useful UX work from decorative UX work is framing: writing down, before any screen exists, the answers to three questions — *who* is this for (one audience segment, not "everyone"), *what* goal they bring (a single sentence per flow), and *how success is recognised* (the observable signal: task completed, order placed, question answered). The discipline comes from the double-diamond convention: divergent research, a converged definition, then divergent solutions and a converged delivery [canonical — the UK Design Council's Double Diamond model]. Skipping the first diamond is how interfaces become feature lists; skipping the definition is how teams argue about preferences instead of evidence.

For agent-driven work, framing converts directly into testable output: the "who" becomes the tone and density of the interface, the "what goal" becomes the primary action of each screen, and the "success signal" becomes the acceptance test the built screen is evaluated against (see [Evaluation checklist](#9-evaluation-checklist) below).

## 5. Practical application

### 5.1 User research methods overview

Choose methods by the question you are asking. There is no universal method; each answers a different class of question, and most projects need at least one qualitative and one quantitative source.

| Method | Question it answers | Type | When it fits |
|---|---|---|---|
| User interviews | Why do people behave this way? What motivates, confuses, annoys? | Qualitative, attitudinal | Early discovery; before designing anything new |
| Contextual inquiry / observation | What do people actually do (as opposed to what they say)? | Qualitative, behavioural | Complex workflows; workplace tools |
| Usability testing (moderated or unmoderated) | Can people complete tasks with this design? Where do they fail? | Qualitative, behavioural | Every significant design, at every stage of maturity |
| Card sorting / tree testing | How should content be grouped and labelled? (see [Information architecture](information-architecture.md)) | Quantitative-leaning, behavioural | Building or auditing navigation |
| Surveys | How widespread is an attitude or behaviour? | Quantitative, attitudinal | Validating a hypothesis at scale; satisfaction tracking |
| Analytics and log data | What do large numbers of users actually do? Where do they drop off? | Quantitative, behavioural | Live products; prioritising which flows to fix |
| A/B testing | Which of two variants performs better on a measurable outcome? | Quantitative, experimental | Optimising a working design; never a substitute for understanding *why* |

Two recurring cautions. First, self-reported and observed behaviour disagree routinely; people say they want one thing and do another, so treat interviews as hypothesis generators and behavioural methods as verifiers. Second, small-sample qualitative findings are directional, not statistical — five interviews reveal *categories* of problems, not percentages.

Method selection follows three practical rules. *Match the method to the decision*: a method is justified by what it will change (a card sort is worth running only if the structure is still open to change). *Triangulate*: never hang a major decision on one method; pair an attitudinal source with a behavioural one. *Weight cost against reversibility*: early, cheap methods (interviews, analytics reviews) before expensive ones (full usability studies), and the more expensive the change under discussion, the more evidence it deserves.

### 5.2 User journeys

A user journey map is a structured representation of one user's path towards one goal, expressed as stages. A usable map has, per stage: the user's **actions**, their **thoughts and questions**, their **emotional state** (often plotted as a satisfaction curve), the **touchpoints** (screens, emails, human contacts) and the **opportunities** (where the experience dips or breaks). The value is diagnostic and communicative: it converts scattered complaints into a shared picture of *where* the experience fails and *why*, and it forces the team to consider the parts of the experience they do not own (the confirmation email, the delivery).

A lighter-weight variant that suits agent-driven work is the **task flow**: the concrete sequence of steps for one defined task ("add an item to the basket and pay"). Task flows are directly testable — every step in the flow must exist in the interface, be findable, and provide feedback. Journey maps widen the lens to emotion and context; task flows narrow it to verifiable mechanics. Use both: the flow to guarantee the machine works, the map to understand the human using it.

A journey map for one goal reads as a table of stages, each stage carrying the same five rows:

| Row | Stage 1: Trigger | Stage 2: Choose | Stage 3: Book | Stage 4: Attend |
|---|---|---|---|---|
| Doing | Searches for events | Compares two dates | Enters details, pays | Receives ticket, travels |
| Thinking | "Anything on that weekend?" | "Is the Sunday sold out?" | "Is my payment accepted?" | "Where is the entrance?" |
| Feeling | Curious | Uncertain | Anxious | Relieved |
| Touchpoints | Search engine, site home | Event listing page | Booking form, payment | Email ticket, venue signage |
| Opportunity | Show dates on the home page | Live availability badge | Inline payment errors | Ticket with a map link |

The emotional row is the diagnostic engine: satisfaction dips mark the stages where redesign effort pays most, and each dip can be traced to a touchpoint that can actually be changed. When the dip's touchpoint is outside the team's control (venue signage, postal delays), the journey map still helps — it converts a complaint into a named, ownable opportunity or an explicit non-goal.

### 5.3 Navigation models

Navigation is how users move through a structure. The main structural models (hierarchy, hub-and-spoke, linear/wizard, faceted filtering and free-form networks) are described in depth in [Information architecture](information-architecture.md), together with the components that express them. At the UX level the governing facts are: users navigate by *recognising* labels rather than recalling hidden locations (heuristic 6 [accessed]); users arrive via search and deep links and need breadcrumbs or an obvious "you are here" signal; and the persistent navigation must answer three questions at all times — where am I, where can I go, how do I get back. A navigation model that satisfies those three questions is usable even if unoriginal; a clever one that fails them is unusable.

A quick diagnostic for any navigation: pick three representative destinations and ask, for each, whether a first-time visitor could (a) guess which top-level label would contain it, (b) confirm the choice from the label alone without clicking, and (c) retrace their path afterwards. Every "no" is a findability defect with a specific owner — a wrong label, a misfiled page, or a missing breadcrumb — and each lives in a different layer of the architecture (labelling, structure, wayfinding), which is why the three checks are worth separating.

### 5.4 Interaction models

An interaction model is the overall style of dialogue between user and system. The dominant models:

| Model | User role | Strengths | Costs |
|---|---|---|---|
| Direct manipulation | Points at and moves visible objects | Visible objects, rapid feedback, low memory load, feels natural | Requires a display-rich environment; gestures hide actions (no signifiers); harder to scale to thousands of objects |
| Menu- and form-driven | Chooses from presented options, fills fields | Scales to many options; self-documenting; good for beginners | Buries expert tasks behind navigation; menus grow into haystacks |
| Command / text entry | Types commands | Fast for experts; scriptable | High learning cost; recall, not recognition |
| Conversational | States intent in natural language | Low learning cost; flexible phrasing | Intent misinterpretation; weak discoverability of what is possible |

Real products blend models: a spreadsheet is direct manipulation of cells plus a command language (formula bar) plus menus. The design question is which model carries the primary task, and what support each model gets — direct manipulation needs affordance cues and undo; menus need good grouping and search; commands need completion and error tolerance. The timing and behavioural details of direct-manipulation interaction are treated in [Interaction design](interaction-design.md).

### 5.5 Affordances and feedback in practice

Applied to components, these principles produce concrete checks. Every clickable thing gets a cursor change and a hover/focus state; every tappable element on touch screens is at least the platform minimum size (44 pt on iOS, 48 dp on Android — verified figures in [Responsive design](responsive-design.md)); every loading action shows a state within the feedback window; every destructive action asks once, in the user's language, what will be lost. Where affordance is weak (a flat text link), strengthen the signifier rather than hoping users will experiment. Where feedback would be off-screen or delayed, bring it to the point of action — an inline "Saved" next to the field beats a toast at the screen's edge.

### 5.6 Error prevention and recovery

Norman's distinction between *slips* (right intention, wrong execution — typo, mis-click) and *mistakes* (wrong intention — genuinely misunderstanding what will happen) drives different preventions [canonical]:

- **Slips** are prevented by constraints at the point of action: constrained inputs (date pickers, dropdowns instead of free text), input masking, undo instead of confirmation for frequent low-cost actions, spacing between adjacent destructive controls (see touch-target spacing in [Responsive design](responsive-design.md)).
- **Mistakes** are prevented by making consequences visible *before* commitment: summaries before final submission ("You are about to delete 3 albums"), explicit cost warnings, and confirmation dialogs reserved for irreversible or expensive actions. Confirmation dialogs on every minor action train users to click through them, which removes their value exactly where it is needed.

Recovery design matters as much as prevention: an error message must state in plain language what went wrong, why, and what to do now (heuristic 9 [accessed]); and every irreversible-feeling action should have an exit (undo, cancel, back). When undo genuinely is impossible (sending an email, charging a card), slow the user down at that one point — confirm, retype, or review — because prevention is the only remaining line of defence. The component-level treatment (forms, validation timing, error message writing) is in [UI fundamentals](ui-fundamentals.md).

### 5.7 Trust: honesty as a design constraint

Users extend trust to an interface provisionally, and every interaction either confirms or spends it. The mechanics of trust are mostly mundane: the system does what it says, feedback matches reality, prices and terms appear before commitment, and nothing tries to trick the user. The recognised failure modes have names — *confirmshaming* (opt-out links worded to belittle the user), *hidden costs* revealed at the last step, *roach motels* (easy to subscribe, hard to leave), *disguised ads* styled as interface content [canonical — Harry Brignull's "dark patterns" taxonomy]. These patterns can raise short-term metrics and always cost long-term trust, and several are now also legal exposure rather than merely bad manners.

The design rule is symmetrical with error prevention: prevent the user's mistakes, and never manufacture the user's mistakes. A practical review question for every flow is "what does this screen gain by being *less* clear?" — if the answer is a conversion increase, the design is extracting rather than serving, and the decision needs to be made explicitly and honestly, not slipped into the interface.

### 5.8 Accessibility as UX

Accessibility is not a separate discipline bolted on at the end; it is UX applied to users with permanent, temporary or situational limitations. Most of the fundamentals above are also accessibility techniques: visible feedback (not colour-only), recognition over recall, large targets, plain-language errors, forgiving forms. The formal requirements and WCAG criteria live in [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — treat that file as the compliance layer and this one as the reasoning layer.

### 5.9 Running a five-user usability test

The script that makes the "minimum viable loop" of section 4 actually work, in five stages:

1. **Prepare one page**: the three tasks (concrete, realistic, ordered from easy to hard), the quiet room or call, and a silent observer's note sheet.
2. **Welcome (2 minutes)**: state that the design is being tested, not the person; there are no wrong answers; the facilitator cannot help, because helping would ruin the data.
3. **Think-aloud protocol**: ask the participant to narrate what they are looking at, what they expect to happen and what confuses them. The narration — not the clicks — is the data.
4. **Tasks, silently observed**: note (with timestamps) every hesitation, wrong turn, re-read, repeated click and verbal surprise. Resist explaining; if the participant is stuck for a very long time, mark it and move on.
5. **Debrief (5 minutes)**: ask what was hardest, what they would change, and one question per anomaly noted during the session.

Afterwards, merge the observer notes into issues, rank each by severity (blocking, serious, minor) and by the heuristic it violates, then fix and retest. This protocol is the discount-usability tradition in practice [canonical — Nielsen, *Usability Engineering*]; five participants will not produce statistics, but they reliably surface the blocking defects, which are the ones worth the next iteration.

## 6. Decision framework

When making or reviewing a UX decision, work through the questions in order:

1. **Goal**: what is the user's goal on this screen, in one sentence? If two goals compete, which wins and how is the loser demoted rather than deleted?
2. **Knowledge**: what does the user already know (mental model), and does the interface build on it? If it deviates, how is the new model taught *in* the interface?
3. **Action visibility**: is every possible next action signified somewhere perceivable? Is every signified action real?
4. **Memory load**: what must the user remember from a previous step or screen? Can the interface carry that memory instead?
5. **Feedback inventory**: list every action the user can take. For each: what does the system show, how fast, and where? Any action with no answer is a defect.
6. **Error surface**: what are the three most likely user errors here? For each — prevented by constraint, made visible before commitment, or recoverable by undo?
7. **Exit routes**: from every state, can the user cancel, go back, or undo without losing work?
8. **Honesty**: does anything on this screen gain by being less clear? If so, that is a trust cost being taken on purpose (5.7) — make it explicitly or remove it.

This framework doubles as an evaluation checklist (section 9) and as a self-review routine before delivering any interface. It deliberately asks about the negative space — errors, exits, memory — because that is where designs fail.

## 7. Examples

**Trust repaired by disclosure.** A subscription flow originally revealed the £9 monthly charge only after card entry; completion was high, refund requests and chargebacks higher. The repair — the price and the renewal date on the plan-selection screen, plus a plain-language "cancel anytime" line — lowered raw conversion slightly and lowered refunds and support contacts more. The lesson is section 5.7 in numbers: clarity extracted more durable value than the dark pattern did.

**Mental model violation fixed by feedback.** A settings page that silently autosaves contradicts the widely held model "nothing happens until I press Save". Two legitimate repairs: add a visible "Changes saved" indicator near the control the moment a change is committed (teaching the autosave model), or return to an explicit Save/Discard pair (honouring the existing model). Both resolve the conflict between the three models; leaving it unresolved leaves users who close the tab in fear of losing work.

**Recognition over recall.** A form requiring a sort code/format the user rarely types: showing the accepted format as a persistent hint beside the field costs one line and removes a recall demand; a disappearing placeholder costs the same line but fails precisely when the user has started typing (verified harms of placeholder-as-label in [UI fundamentals](ui-fundamentals.md)).

**Error prevention tiers.** Three designs for a "delete document" action, from weakest to strongest: (a) a confirmation dialog on every delete — safe but trains blind clicking; (b) a 5-second undo toast after deletion with no dialog — fast for the common case, recoverable for the rare mistake; (c) for bulk deletion of many documents, a dialog that names the count and the irreversibility. Choosing among these is a judgement about frequency and cost of error — exactly the kind of context-dependent decision the framework in section 6 forces.

**Heuristic evaluation in miniature.** A team reviewing a booking flow with the table in 3.6 finds: no progress indicator on the 8-second payment step (violates 1), a "Submit" on step 2 that really means "continue" (violates 4), and a card-rejection error that says "Error 502" (violates 9). Three defects, each mapped to a named heuristic, each with an obvious repair — that is the method working as intended.

**Analytics locating the real defect.** A product team debates redesigning the checkout page for weeks. The funnel analytics settle it: 92% of users who reach step 3 abandon, and step 3 is the only step that asks for account creation. The redesign that follows — guest checkout, with an optional account invitation after purchase — doubles completion without touching visual design. Research located the defect; aesthetics were never the problem.

**The five-user test paying for itself.** A charity donation page passes internal review. A five-person task test ("donate £20 in memory of a specific person") finds four of five users missing the tribute field, because it sits below the payment summary fold and has no label anchor. Moving it adjacent to the "who is this donation for?" wording and testing again raises in-field completion from 1/5 to 5/5. Total cost: an hour; the alternative was discovering the same fact in monthly donation figures.

## 8. Common mistakes

- **Designing for the ideal user.** Assuming users read, remember and follow instructions. Real users skim, interrupt and improvise; designs must survive that.
- **Asking users what they want and building it literally.** Stated preferences are unreliable predictors of behaviour; observe or test instead. Users are experts in their problems, not in the solutions.
- **Confirmation dialogs everywhere.** Frequent low-stakes confirmations habituate users to approve without reading, destroying the mechanism that protects high-stakes actions. Prefer undo for low stakes.
- **Feedback by colour alone.** A field that turns red without a text message fails colour-blind users and anyone unsure what red means here. Pair every colour signal with text or icon (see [Colour accessibility](../colour/colour-accessibility.md)).
- **Hidden affordances.** Gesture-only controls, icon-only buttons with no label or tooltip, and hover-only menus all have affordances without signifiers; they are undiscovered by new users and unusable on touch.
- **Journey maps as wallpaper.** A beautiful map that no decision ever consults is decoration. Tie each map to named opportunities and track whether they shipped.
- **Testing only the happy path.** Users fail, retry, go backwards and abandon. Test the error paths deliberately; they are half the experience.
- **Treating heuristics as laws.** Nielsen's list is a review instrument, not a rule engine. Heuristic violations are candidate problems; user evidence decides severity.
- **Skipping measurement baselines.** Redesigns launched without a recorded completion rate, time-on-task or error baseline can never prove improvement — the iteration loop loses its feedback signal (see 3.8).
- **Personas as fiction.** Invented "users" (marketing names with stock-photo backstories and no research behind them) reassert designer assumptions in a costume of authority; persona work is only as good as the evidence underneath it.
- **Research theatre.** Running one interview or one card sort to legitimise a decision already made. The ritual without the openness to being wrong costs credibility and money alike.

## 9. Evaluation checklist

- Every screen states (or makes obvious within one glance) where the user is and what the primary action is.
- Every interactive element has default, hover/focus and disabled states; every async action has a pending state and an outcome state.
- Every action produces perceivable feedback within the appropriate timing window (see [Interaction design](interaction-design.md)).
- No step requires information the user must memorise from another screen or earlier in the flow.
- Labels use the user's vocabulary, not internal or technical terms; terminology is identical across screens.
- The three most likely errors on each screen are constrained, surfaced before commitment, or recoverable via undo.
- Every multi-step flow can be cancelled or reversed without loss of work.
- Destructive actions are visually distinguished and either confirmed with explicit consequences or undoable.
- Error messages state what happened, why, and the next step — no codes without translation.
- Usability metrics (completion rate, time on task, error rate) are defined and a baseline exists for the current design.
- Every task in the primary task flow exists in the interface, is findable within the navigation, and returns feedback.
- Accessibility flows are treated as primary flows, not edge cases (keyboard-only, screen reader, 200% zoom).
- A first-time user can complete the primary task without instruction; a returning user can complete it faster.
- Structural conventions are followed deliberately (navigation placement, icon meanings); any deviation is taught in the interface.
- Nothing in the flow trades user clarity for a business metric without an explicit, reviewed decision (dark-pattern review, 5.7).

## 10. Related topics

- [Information architecture](information-architecture.md) — organising content and navigation structures
- [Interaction design](interaction-design.md) — feedback timing, micro-interactions, animation and latency perception
- [UI fundamentals](ui-fundamentals.md) — components, states, forms and the visual layer of these principles
- [Responsive design](responsive-design.md) — touch targets, content prioritisation across devices
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — the formal accessibility requirements underlying inclusive UX
- [Gestalt and perception](../foundations/gestalt-and-perception.md) — the perceptual machinery behind grouping, hierarchy and salience
- [Principles of design](../foundations/principles-of-design.md) — the general design vocabulary (contrast, emphasis, unity) applied here to interfaces
- [Grid systems](../layout/grid-systems.md) — the layout scaffolding that supports scannable, predictable screens

## 11. References

- Jakob Nielsen, "10 Usability Heuristics for User Interface Design", Nielsen Norman Group, https://www.nngroup.com/articles/ten-usability-heuristics/ [accessed 2026-11-23]
- Jakob Nielsen, "Response Times: The 3 Important Limits", Nielsen Norman Group, https://www.nngroup.com/articles/response-times-3-important-limits/ [accessed 2026-11-23]
- Katie Sherwin, "Placeholders in Form Fields Are Harmful", Nielsen Norman Group, https://www.nngroup.com/articles/form-design-placeholders/ [accessed 2026-11-23] (see [UI fundamentals](ui-fundamentals.md) for the form-design application)
- Don Norman, *The Design of Everyday Things*, revised edition, Basic Books, 2013 [canonical] — affordances, signifiers, feedback, mental models, constraints, slips and mistakes
- Jakob Nielsen, *Usability Engineering*, Academic Press, 1993 [canonical] — usability lifecycle, discount usability testing methods
- Ben Shneiderman et al., *Designing the User Interface*, Pearson [canonical] — the Eight Golden Rules of Interface Design
- George Miller, "The Magical Number Seven, Plus or Minus Two", *Psychological Review*, 1956 [canonical]; Nelson Cowan, "The Magical Number 4 in Short-Term Memory", *Behavioral and Brain Sciences*, 2001 [canonical] — working-memory capacity
- John Sweller, cognitive load theory (intrinsic / extraneous / germane load) [canonical]
- Paul Fitts, 1954 (Fitts's law); W. E. Hick, 1952 (Hick's law) [canonical]
- Apple, Human Interface Guidelines, Buttons and Accessibility, https://developer.apple.com/design/human-interface-guidelines/buttons and https://developer.apple.com/design/human-interface-guidelines/accessibility [search-verified 2026-11-23] (44×44 pt hit region; ~12 pt padding between targets)
- Google, Material Design, Spacing methods and Accessibility Help, https://m2.material.io/design/layout/spacing-methods.html, https://m3.material.io/foundations/designing/structure, https://support.google.com/accessibility/android/answer/7101858 [search-verified 2026-11-23] (48×48 dp targets, 8 dp separation)
- John Brooke, "SUS: A Quick and Dirty Usability Scale", 1996 [canonical] — the 10-item System Usability Scale
- UK Design Council, the Double Diamond model [canonical] — divergent/convergent process framing
- Harry Brignull, darkpatterns.org [canonical] — taxonomy of deceptive interface patterns
- Steve Krug, *Don't Make Me Think*, New Riders [canonical] — usability testing and first-use clarity
- Jon Yablonski, *Laws of UX*, lawsofux.com [canonical] — named principles including Jakob's Law (attribution to Jakob Nielsen's observation)
