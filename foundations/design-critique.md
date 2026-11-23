# Design Critique

## 1. What is it?

Design critique is the discipline of looking at visual work and producing a
reasoned, evidence-based judgement: what works, what fails, why, and how confident
that diagnosis is. It is the counterpart to production skill — the ability to *see*
what a composition is actually doing, independent of intention and of personal
taste. This file teaches critique as analysis: identifying visual problems,
explaining why a composition works or fails, separating taste from design reasoning,
and avoiding arbitrary aesthetic suggestions.

A working definition, adapted from Boris Müller's essay *Design Critique Culture*: a
critique is a focused discussion and analysis of an artefact, in which observations
are backed by reasoning — "critiques are not about quick verdicts", and opinions are
only useful when they are justified ("Design Critique Culture", 2022) [accessed].
Müller's ground rule doubles as this file's core ethic: *criticise the design, never
the designer*; and "if a critique is not analytical, fair, and supportive — it is
not a critique" [accessed].

A deliberate split of responsibility governs this file. Here: how to *see* and
*judge* — observation protocols, defect vocabulary, causal explanation,
taste-vs-reasoning tests. The *process* — who reviews, in what order, roles,
scheduling and decision handling — belongs to [Design critique
process](../methodology/design-critique.md), which should be read alongside this
one. Likewise, the quantitative scoring machinery is in [Design quality
framework](../evaluation/design-quality-framework.md); this file supplies the
qualitative reasoning that scores are built on.

## 2. Why does it matter?

Without critique ability, an agent can produce designs but cannot improve them
reliably. Every revision cycle starts with a judgement call: what is actually wrong?
Guessing produces the two classic wastes — redesigning what was fine (style churn)
and "fixing" symptoms while causes remain (adding space to a layout whose real
problem is conflicting focal points). A critique vocabulary turns revision into
diagnosis and makes improvement convergent rather than random.

Critique discipline also guards against the most common failure of automated and
human feedback alike: *taste leakage*. "Make the blue lighter" is a preference; "the
call to action has insufficient value contrast against the background, so users may
miss it" is a reason. Only the second can be debated, tested and generalised.
Müller's analysis stresses exactly this: critique requires reasoning — visual and
verbal arguments behind observations — because bare like/dislike cannot be
discussed, only complied with or resented [accessed]. An agent that can articulate
*why* its design choices hold up is also far more robust when challenged: it can
either defend the choice with evidence or concede it with understanding.

Finally, critique is the bridge between design and users. Most visual defects are
invisible to their maker and obvious to a stranger; structured critique simulates
the cold eye of an audience before the audience arrives. It is the cheapest
usability test available, and the observation protocols below make that simulation
systematic rather than impressionistic.

## 3. Core principles

### 3.1 Describe before you judge

The first discipline of critique is separating *observation* from *evaluation*.
Untrained viewers leap to verdicts ("looks cluttered"); trained critics first
inventory what is present: how many type sizes, where the masses sit, what contrasts
exist, which alignments are real. Most design failures are relational — a good
element in the wrong relationship — and relationships are invisible until described.

A compact observation protocol: (1) *Inventory* — list the element families (type
levels, colour groups, shape vocabulary, image treatments) and their counts; (2)
*Structure* — identify the dominant mass, the alignments, the grouping boundaries;
(3) *Reductions* — squint, greyscale, thumbnail, blur: note what survives each; (4)
*Trace* — mark where the eye goes first, second, third; (5) *Compare* — against the
artefact's stated goal and against its own internal system. Only after these steps
should judgements be formed, and each judgement should cite an observation as
evidence.

The protocol also disciplines critique of *your own* work, where attention is biased
by intention: you see what you meant, not what is there. The reduction steps exist
to defeat intention-bias — you cannot squint your way into seeing the design you
hoped for.

### 3.2 Evaluate against purpose, not style

A design is judged against its job: audience, message, medium and constraints.
Müller's essay grounds critique in a dual purpose — the utilitarian (project goals)
and the idealistic (aesthetic and conceptual excellence, "even in app design you
should strive for beauty") [accessed]. Both matter, but neither is *style*. Judging
a booking form by poster standards, or a poster by dashboard standards, produces
confident nonsense.

In practice: state the artefact's goal in one sentence first; if the goal is
unclear, that is the first finding — not a licence to apply personal standards. Then
evaluate two axes. *Effectiveness*: does the arrangement deliver the message
(hierarchy, grouping, flow, legibility)? *Craft*: is the system executed
consistently (alignment, spacing, vocabulary)? Style — the legitimate choices (serif
or sans, warm or cool) — is evaluated only for *internal consistency*, not
correctness. This is the key distinction for avoiding arbitrary aesthetic
suggestions.

### 3.3 Reason from mechanism, not analogy

Mechanism-based reasoning has three properties analogy lacks. It is *falsifiable* —
"users will not find the link because proximity groups it with the unrelated block
above" predicts a testable outcome. It *transfers* — the same diagnosis applies to
the next artefact. And it *survives disagreement* — two critics citing different
mechanisms can compare them; two critics citing different brands cannot. When you
cannot name a mechanism for your reaction, label it as untested intuition (section
3.6) rather than disguising it as analysis.

Mechanism-based reasoning has three properties analogy lacks. It is *falsifiable* —
"users will not find the link because proximity groups it with the unrelated block
above" predicts a testable outcome. It *transfers* — the same diagnosis applies to
the next artefact. And it *survives disagreement* — two critics citing different
mechanisms can compare them; two critics citing different brands cannot. When you
cannot name a mechanism for your reaction, label it as untested intuition (section
3.6) rather than disguising it as analysis.

### 3.4 Grade findings, not feelings

Critique output should be a graded list of findings, each with location, evidence,
causal explanation and severity. Grading prevents treating a hairline misalignment
and a missing call to action as equivalent items. A workable three-tier scale
(synthesis of common practice; process-level ordering lives in [Design critique
process](../methodology/design-critique.md)):

- **Blocking** — defeats the artefact's primary goal: no legible focal point, unreadable text, ambiguous grouping of task-critical controls. Must be fixed before polish.
- **Significant** — damages communication or trust: weak hierarchy between levels, inconsistent component anatomy, near-miss alignments, contrast that fails in greyscale.
- **Polish** — refinements that matter only after the tiers above are clear: spacing rhythm, optical adjustments, micro-consistency.

Grading also forces honesty about confidence: a blocking claim ("users will miss
this") is a prediction and should say what evidence would settle it (a five-second
test, a usability session); a polish claim can rest on craft convention.

### 3.5 Diagnose causes, not symptoms

Most reported visual problems are symptoms; the cause is usually a failed
*relationship*. The vocabulary table in section 4 pairs each common symptom with its
likely causal mechanisms, and the discipline is to travel that full path before
proposing fixes. Example: a "cluttered" hero section — inventory shows three
competing salient elements; mechanism: salience budget overspent, dominance unclear;
cause: no rank decision in the brief; remedy follows from cause (decide the primary
message and demote the rest decisively) rather than from symptom (randomly shrinking
things).

Proposing *problems* rather than solutions is also fairer to the maker: Müller notes
constructive critique may be purely descriptive — naming a problem without
prescribing the fix — because the presenter holds the context and is better placed
to choose the remedy [accessed]. Aim for problem-first feedback with illustrative
remedies, not directive orders.

### 3.6 Separate taste from reasoning

Taste is legitimate — it shapes style choices and signals — but it must be
*labelled* and never dressed up as analysis. Four tests separate the two:

1. **Observability**: can the claim be traced to a visible feature ("the heading and the badge are within 8 px") or only to a reaction ("it feels dated")?
2. **Mechanism**: does the claim cite a perceptual or behavioural consequence, or only an analogy and preference?
3. **Generality**: would a different competent critic, given the goal, tend to agree — or is it squarely within the artefact's legitimate style space?
4. **Falsifiability**: does it predict a testable outcome ("five seconds and the viewer cannot name the action")?

Reformulating taste into reasoning or honest preference is the practical skill.
"Make it pop" → tested: "the primary action ties with the photograph in weight; if
it must be found first, give it the highest value contrast in the composition — or
confirm the photograph is the intended focal point." "I don't like this colour" →
honest preference: "a style choice, not a defect; the palette is consistent and
passes contrast; changing it is valid either way." The first has a mechanism and a
test; the second is labelled so it can be weighed correctly.

### 3.7 Critique systems, not just artefacts

Every artefact is an instance of a system (a brand kit, a component library, a
document template), so critique must check both levels: is *this artefact*
effective, and is it *systematic* — would its decisions extend sanely to the next
artefact? The swap test (paste this component elsewhere in the kit) and the
vocabulary count (shapes, weights, spacings in play) make this concrete. A beautiful
poster that requires bespoke spacing for every future event is a weak system
outcome, especially in brand-kit work — the repository's core use case.

This systems view also changes the meaning of "consistency findings": a deviation is
not automatically a defect. Ask whether it is *meaningful* (variety with a job — the
single emphasised keynote in a uniform programme) or *accidental* (drift).
Deliberate deviation is design; accidental deviation is error; critique must
distinguish them, ideally by asking the maker.

## 4. How it works

Critique proceeds in passes, each pass answering one question. *Pass 1 — Goal*: what
is this artefact for, for whom, under what constraints? If unknown, obtaining it is
the first action. *Pass 2 — Inventory*: what elements and vocabulary are present, in
what counts? *Pass 3 — Structure*: what is dominant, what is grouped, what paths
exist? Reductions (squint, greyscale, thumbnail) provide the perceptual evidence.
*Pass 4 — Diagnosis*: match observed structure against required structure (from goal
+ principles); list defects with mechanisms. *Pass 5 — Grading and proposal*:
severity, confidence, and illustrative remedies.

The defect vocabulary below is the connective tissue between seeing and diagnosing.
Each row: the symptom a viewer reports, what is actually observable, the likely
mechanism, and where the causal root usually sits. It is a diagnostic map, not an
exhaustive catalogue; terms specific to type and colour detail are in their own
domains.

| Symptom ("it looks...") | What is observable | Likely mechanism / cause | Typical root |
| --- | --- | --- | --- |
| "...cluttered" | Too many equal-weight elements; weak or absent grouping gaps | Salience budget overspent; proximity grouping missing | No hierarchy decision made before layout |
| "...empty" or "unfinished" | Large unshaped margins; masses drifting apart | Negative space passive rather than shaped | Space never designed; grid too loose for content |
| "...off-balance" | One heavy mass with no counterweight; axis visibly tipped | Asymmetry mistaken for balance; missing deliberate counterweight | Placement by convenience, not weight |
| "...confusing" | Two+ elements of near-equal salience; eye has no entry | Competing focal points; dominance undefined | Two messages promoted at once |
| "...cheap" | Inconsistent vocabulary: mixed corners, weights, spacings | Repetition broken; system absent | Component-level thinking, no system level |
| "...amateurish" | Near-alignments, almost-equal spacing, edge-crowding | Unresolved tension; accidental rhythm | Manual placement without snapping to a system |
| "...hard to read" | Insufficient value contrast; text over textured/busy ground | Figure–ground ambiguity; contrast below legibility needs | Style (texture, subtlety) prioritised over function |
| "...dull" | Uniform masses; no dominant scale; no deliberate deviation | Variety absent; everything middle-weight | Risk-averse uniformity; emphasis never spent |
| "...messy" | Deviations everywhere; no two items share anatomy | Variety without unity | Exceptions accumulated unmanaged |
| "...lost" (can't find X) | Target element near-zero salience; or placed outside attention field | Salience too low; position outside expected scanning zone | Decorative priority over task priority |
| "...generic" | Correct but characterless: default ratios, no signature elements | Composition serves no specific message | Template applied without goal-derived decisions |
| "...dated" | Vocabulary internally consistent but period-marked | Legitimate style, not a defect | Taste claim — label it, then decide with the maker |

Reading the last two rows correctly matters most: "generic" and "dated" are
frequently *not defects* — they are either unmet ambition (fixable with goal-derived
composition) or taste (decidable, not correctable). Misclassifying taste as defect
is the root cause of arbitrary aesthetic feedback.

## 5. Practical application

**Critiquing your own output (the agent loop).** After generating a design, run the
protocol you would run on a colleague's: goal sentence, inventory, reductions,
trace, graded findings. This loop — produce, critique, revise — is the minimum
standard for any design output here, ending with a one-line self-audit: "the
artefact's goal is X; the composition delivers X via Y; remaining risks are Z". Tie
the loop to the checklists in [Elements of design](elements-of-design.md),
[Principles of design](principles-of-design.md), [Composition](composition.md) and
[Gestalt and perception](gestalt-and-perception.md).

**Critiquing work you did not make.** Ask for (or infer) the goal first; critique
the artefact against it, never against what *you* would have made. Name mechanisms,
cite observations, grade severity, mark confidence. Offer illustrative remedies
sparingly and mark them optional. Where a claim depends on user behaviour, propose
the cheapest test that would settle it — a five-second test, a greyscale check, one
moderated session — before asserting certainty.

**Receiving critique.** The same discipline inverts: separate findings from
verdicts, ask for the observation behind any reaction, translate taste claims into
decisions (accept, decline, or explore — all legitimate), and treat blocking
findings as predictions to be tested rather than orders. Müller's rule applies to
receiving too: feedback "needs to be interpreted", not executed as a to-do list
[accessed].

**A worked mini-critique.** Event poster, fixed logo, goal "sell tickets to a local
music festival". Observations: logo top-right at modest scale; artist name centre,
slightly larger but lower value contrast; diagonal band behind name; ticket URL
bottom-left, small. Trace: viewers name the *photograph* first. Diagnosis: the
photograph, not the message, is the dominant mass; artist name and logo tie for
second; flow never reaches the URL. Grade: blocking (focal point contradicts the
goal). Mechanism: salience budget spent on decoration. Illustrative remedy
(optional): demote the photograph (smaller scale or a scrim), raise the name's value
contrast, give the URL the only saturated accent. Every step cites observation and
mechanism — nothing is "make it pop".

## 6. Decision framework

When judging whether a finding is worth raising — and how to phrase it — run it
through this filter:

| Question | If yes... | If no... |
| --- | --- | --- |
| Can I point to the exact visible feature? | Proceed to mechanism | It is a vibe; either observe more or label as intuition |
| Can I name the mechanism and its consequence? | Proceed to grading | Study the artefact further or mark low confidence |
| Does it touch the artefact's stated goal? | High priority candidate | Check whether it is a consistency/system issue |
| Is it a defect, a deliberate deviation, or taste? | Defect → grade it | Deviation → verify intent; taste → present as decision, not fix |
| Would evidence be cheap to get? | Propose the test | State the confidence level explicitly |
| Is the remedy mine to give? | Offer illustratively, optional | Keep it problem-first; let the maker choose |

And when in doubt about whether something is *good*: return to Müller's dual purpose
— does it serve the goal, and does it hold as craft? A finding that fails both tests
is noise; a finding that passes both is praise with substance, and praise with
substance belongs in critique as much as defects do ("start positive" is Müller's
own facilitation rule [accessed]).

## 7. Examples

**Example 1 — poster, blocking finding.** Finding: "the 'Book now' region ties with
the background illustration in value; five-second trace shows viewers naming the
illustration first." Mechanism: salience competition; dominance contradicts the goal
(bookings). Grade: blocking. Evidence proposal: five-second test with five viewers.
A different critic following the same protocol would land nearby — this is
reasoning, not opinion.

**Example 2 — form, significant finding.** Finding: "spacing between the 'Card
number' label and its field equals the spacing between fields, so the label–input
pairing is ambiguous on mobile." Mechanism: proximity grouping (see [Gestalt and
perception](gestalt-and-perception.md)). Grade: significant. Illustrative remedy:
adopt a spacing-step system — intra-group spacing one step, inter-group two steps.

**Example 3 — brand kit, system finding.** Finding: "the event poster introduces a
third corner radius not present in the logo or any component." Mechanism: vocabulary
inflation; repetition broken. Grade: significant at system level even though the
artefact looks fine — a *system* defect invisible in the single artefact, the pass
most critics skip.

**Example 4 — taste correctly handled.** Comment: "I'd have used a serif headline."
Response: classified as style preference; verified the sans headline is internally
consistent, legible and message-appropriate; logged as a decision for the maker, not
a defect. The conversation stays analytical — the difference between critique and
taste arbitration.

## 8. Common mistakes

- **Equal-weight lists.** Presenting a missing call to action and a slightly off margin as siblings; grading exists to prevent this.

## 9. Evaluation checklist

For a critique you are about to deliver, confirm:

- Did you state the artefact's goal and audience in one sentence before judging?
- Does every defect finding cite an observable feature (location, count, measurement or trace result)?
- Does every significant finding name its mechanism (Gestalt, salience, weight, load, flow)?
- Are findings graded (blocking / significant / polish) and does the order follow the grades?
- Have you separated defects from deliberate deviations (intent checked) and from taste (labelled as such)?
- Are remedies illustrative, optional and cause-directed — never symptom patches?
- Does the critique cover the system level (vocabulary counts, swap test), not only the artefact?
- Have you included substantive praise where the design earns it, with the same evidence standard?
- Are behavioural claims ("users will miss it") marked as predictions with the cheapest test named?
- Would a competent third critic, following the same protocol, recognise your reasoning even where they disagree?

## 10. Related topics

- [Elements of design](elements-of-design.md) — the inventory vocabulary critiques are built from.
- [Principles of design](principles-of-design.md) — the relationships most defects trace back to.
- [Gestalt and perception](gestalt-and-perception.md) — the perceptual mechanisms cited as evidence.
- [Composition](composition.md) — focal points, flow and tension: the most common locus of blocking findings.
- [Design critique process](../methodology/design-critique.md) — who reviews, in what order, roles and decision handling (the process half of this split).
- [Design quality framework](../evaluation/design-quality-framework.md) — turning these qualitative judgements into consistent scores.
- [UI fundamentals](../ui-ux/ui-fundamentals.md) — usability context for interface findings.

## 11. References

- Müller, Boris — "Design Critique Culture", Medium (Prof. for Interaction Design, FH Potsdam), 2022 (definition; reasoning over verdicts; criticise the design, never the designer; descriptive critique; dual purpose; Connor & Irizarry's *Discussing Design* referenced within). https://borism.medium.com/design-critique-culture-b7350baab11c [accessed 2026-11-23]
- Connor, Adam & Irizarry, Aaron — *Discussing Design: Giving and Receiving UX Design Feedback*, O'Reilly, 2015 (utilitarian purpose of critique; roles and intent) [canonical]
- Budiu, Raluca — "Memory Recognition and Recall in User Interfaces", Nielsen Norman Group, 2024 (evidence standard for behavioural claims about finding and noticing). https://www.nngroup.com/articles/recognition-and-recall/ [accessed 2026-11-23]
- Gordon, Kelley — "5 Principles of Visual Design in UX", Nielsen Norman Group, 2020 (evaluation heuristics: can users parse the visual; where to look). https://www.nngroup.com/articles/principles-visual-design [accessed 2026-11-23]
- Pernice, Kara — "F-Shaped Pattern of Reading on the Web", Nielsen Norman Group, 2017 (scanning evidence used in trace-based findings). https://www.nngroup.com/articles/f-shaped-pattern-reading-web-content/ [accessed 2026-11-23]
- Arnheim, Rudolf — *Art and Visual Perception*, University of California Press, 1954/1974 (perceptual forces as the analytical language of visual judgement) [canonical]
- Berkun, Scott — "How to Run a Design Critique" (widely cited practitioner guide on critique conduct) [canonical]

The defect vocabulary table (section 4), the taste tests (section 3.6) and the
decision filters (section 6) are a synthesis of the sources above with standard
professional practice, written for this repository; the severity tiers are a
conventional starting point, and the process-level protocol they plug into is
specified in [Design critique process](../methodology/design-critique.md).
