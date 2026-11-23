# Design critique (method)

## 1. What is it?

This file defines a **repeatable critique process**: a fixed sequence of eleven review steps, facilitation guidance for running reviews, and the discipline for receiving critique and separating taste from reasoning. It is the operational, procedural counterpart to the judgment skills described in [Design critique](../foundations/design-critique.md) — that file teaches *how to evaluate*; this file teaches *how to run the evaluation, every time, the same way*, so results are comparable across artefacts, reviewers and projects.

The process comes from the repository's mission specification (§7.4) and encodes the order in which professional reviews are actually conducted: purpose first, audience second, then the sensory layers (hierarchy, type, colour, composition), then system-level properties (consistency, accessibility), then defects, then prioritisation, then re-evaluation.

## 2. Why does it matter?

Unstructured review is unreliable: whatever the reviewer notices first gets the attention, order effects dominate, and two reviews of the same artefact find different things. A fixed process fixes this. It guarantees full coverage (accessibility is checked in step 8 even when the artefact looks fine); it makes reviews comparable (the same steps every time means the same vocabulary every time); it produces a triageable output (step 10 sorts findings by importance instead of by whoever spoke loudest); and it closes the loop (step 11 re-evaluates instead of assuming the fix worked).

For an agent, the process is also the self-review instrument: before presenting work, the agent runs all eleven steps itself and fixes what it finds. Work that has passed a structured self-critique arrives with its defects already removed and its reasoning already documented.

## 3. Core principles

- **Purpose before pixels.** No visual evaluation happens until the communication objective and intended audience are stated. Judging without them measures taste, not performance.
- **Fixed order, full coverage.** The eleven steps run in order and all of them run — even when early steps pass. The order encodes dependency: accessibility findings override polish opinions; consistency findings require the rules to exist.
- **Describe before judging.** Each step begins with observation ("the CTA is the fourth-largest element") before evaluation ("but the objective needs it first"). Descriptions can be agreed; opinions cannot.
- **Findings, not solutions.** A critique identifies what fails and why. Solutions are drafted afterwards, in the iteration round (see [Iteration](iteration.md)); mixing them turns review into redesign.
- **Reasoning over taste.** Every finding must connect to an objective, a rule, a standard or an audience fact. "I don't like the green" is data about the speaker; "the green fails 4.5:1 against the background, which is required" is a finding.
- **Everything is recorded.** A critique that leaves no record cannot drive a change list or survive a later challenge (see [Iteration](iteration.md) §4.2).

## 4. How it works

### 4.1 The eleven-step review process

Run the steps in order. For each artefact, record per step: observations, findings (classified later in step 10), and pass/fail where a check is objective.

1. **Identify the communication objective.** What must this artefact achieve — inform, persuade, enable an action, identify? State it in one sentence with the success signal ("registrations", "schedule found in 5 seconds"). If no objective can be stated, stop the critique and get one: this is a brief failure, not a design failure.
2. **Identify the intended audience.** Who is this for, in what context and on what device? Pull from the discovery characterisation (see [Research and discovery](research-and-discovery.md)). Every later step is judged *for this audience*, not for reviewers.
3. **Evaluate visual hierarchy.** Squint at the artefact or view it blurred: does the importance order (what the objective demands) match the perceptual order (what stands out)? Check one dominant element, clear reading path, deliberate grouping (see [Information hierarchy](../information-design/information-hierarchy.md), [Composition](../foundations/composition.md)).
4. **Evaluate typography.** Legibility (size, line length, line height against conventions), hierarchy of weights and scales, consistency of families and cases, rendering at target sizes, and fit to the brand's type rules.
5. **Evaluate colour.** Palette harmony with the brand rules, proportion of accent colour, meaning and consistency of functional colours, and — recorded as numbers — contrast ratios of every text pair (see [Colour theory](../colour/colour-theory.md)).
6. **Evaluate composition.** Alignment, balance, use of space, edge behaviour, responsiveness of the layout to its container, and whether the grid logic survives the intended size range.
7. **Evaluate consistency.** Against the established system: tokens, spacing scale, type scale, icon style, imagery treatment, tone of voice. Checklist against the relevant rules source (see [Visual consistency](../design-systems/visual-consistency.md), [Brand guidelines](../branding/brand-guidelines.md)).
8. **Evaluate accessibility.** Contrast ratios (computed, not eyeballed), minimum text sizes, alt/label provisions for non-decorative imagery, colour-independence of information (no meaning carried by colour alone), motion and timing where relevant (see [WCAG fundamentals](../accessibility/wcag-fundamentals.md), [Accessible colour](../accessibility/accessible-colour.md), [Accessible typography](../accessibility/accessible-typography.md)).
9. **Identify defects.** The mechanical pass: typos, wrong dates, broken layouts, missing assets, misaligned prints, placeholder text, wrong logo variant, export errors. Zoom through multiple scales (25%, 100%, 400%) and proofread every string. Defects are objective; they do not need discussion to be valid.
10. **Prioritise corrections.** Classify every finding (defect / objective failure / accessibility failure / consistency drift / preference) and sort by severity × effort: fix accessibility failures and defects first, objective failures second, drift third, preferences last or never. This sorted list *is* the iteration change list (see [Iteration](iteration.md) §4.2).
11. **Re-evaluate.** After corrections are applied, re-run the failed steps only — plus a quick full pass to catch regressions introduced by the fixes (a contrast fix that breaks the palette harmony is a classic regression). Re-evaluation continues until the failed steps pass or the stop signals from [Iteration](iteration.md) §4.4 fire.

### 4.2 Facilitation: running a review

- **Who attends:** the designer/author (presents intent, listens), the facilitator (runs the steps, enforces rules), one to three reviewers (at least one not involved in the project — fresh eyes find what familiarity hides), and the requester/stakeholder when objectives or priorities are in question. Four to six people is the working maximum; beyond that, conversations fragment.
- **Before:** distribute the artefact and state the objective and audience in the invitation (steps 1–2 pre-filled). Reviewers arrive having looked, not seeing for the first time.
- **Timeboxing:** 30–45 minutes for a single artefact is the working norm; 10–15 minutes per artefact when reviewing several. The author speaks first (intent), the room works through the steps, the facilitator closes by reading back the prioritised findings. If time runs out, cut depth, not steps.
- **Rules to state upfront** (echoing NN/g's guidance that rules and expectations be established before the session): critique the work, not the person; describe before judging; give reasons tied to objectives and rules; the author asks clarifying questions but does not defend; decisions about what changes happen after the session, not during it. `[search-verified]`
- **Output:** the recorded findings table, sorted and classified, handed to the author as the change-list input.

### 4.3 Receiving critique

The author's job during critique is to *collect*, not to defend.

- **Listen fully, then ask clarifying questions:** "Which objective does that finding connect to?" "Can you point to the rule it breaks?" Questions convert vague discomfort into usable findings — and vague findings often dissolve under them.
- **Record everything, decide later.** Even findings you believe are wrong go in the record with their class. Sorting happens in step 10, not in the room.
- **Separate the artefact from the self.** Findings attach to artefacts and rules. A designer whose identity absorbs every finding will defend, and defending teaches reviewers to stop giving real feedback.
- **Follow up publicly.** Publish what was changed and what was deferred with reasons. Reviewers who see their feedback processed keep giving it; reviewers whose feedback vanishes into silence stop.

### 4.4 Separating taste from reasoning

The critique's authority comes from this separation, and it applies to every finding in every step:

| Statement | Class | What it needs to become actionable |
| --- | --- | --- |
| "The schedule is hard to scan on a phone" | Observation of a failure against the objective | Confirm with the objective and audience context; then it is an objective failure |
| "The amber body text measures 2.1:1" | Measured accessibility failure | None — it is already actionable (must be fixed) |
| "This blue feels cold" | Taste/preference | Connect to brand personality or audience evidence, or record as deferred preference |
| "I'd use a different font" | Solution proposal without finding | Ask for the finding behind it ("what fails with the current one?") |
| "It looks dated" | Taste with a hidden attribute claim | Extract the attribute (which visual cues read as dated?) then reason about it |

The judgment vocabulary — what makes an evaluation well-reasoned rather than mere preference — is developed in [Design critique](../foundations/design-critique.md); this file supplies the process that keeps that vocabulary in order. Facilitators should convert taste statements into attribute questions rather than dismissing them: taste is often real signal wearing imprecise words.

## 5. Practical application

### 5.1 Self-critique protocol for agents

Before presenting any artefact, the agent runs the eleven steps alone and records the findings table. Practical adjustments: use the objective and audience from the brief verbatim (never invent an easier objective than the brief's); compute every contrast pair programmatically (see [AI-assisted design](ai-assisted-design.md) on why a model's contrast claims cannot be trusted); check at the extremes (smallest size, narrowest viewport, grayscale); proofread every string character by character, as defect-class findings from skipped proofreading are the most common self-critique failure. Present the artefact with the findings table attached: defects found and fixed, plus open items with classes. This is what distinguishes "reviewed work" from "work that survived nobody looking".

### 5.2 Worked mini-example (event poster, fixed logo)

- Step 1: objective = "announce date/venue, drive ticket-page visits"; success signal = "date and venue read in 3 seconds at poster distance".
- Step 3: blurred view shows the *sponsor block* dominating over the date — hierarchy failure vs objective.
- Step 5: amber CTA on off-white measures 2.1:1 — accessibility failure (recorded as number).
- Step 8: date/venue distinguished by colour alone — colour-independence failure.
- Step 9: venue name misspelled — defect.
- Step 10 sorted list: ① misspelling (defect), ② contrast 2.1:1 (accessibility), ③ colour-only distinction (accessibility), ④ sponsor dominance (objective), ⑤ "poster feels busy" (preference — deferred).
- Step 11 after fixes: contrast pair now 7.3:1 (computed); date/venue also bolded (colour-independent); sponsor block reduced one step; full pass confirms no regression. Poster passes.

## 6. Decision framework

| Situation | Action |
| --- | --- |
| No written objective | Stop; get the objective first — visual steps without it are taste sessions |
| Disagreement between reviewers on a step | Return to the objective/rule the step serves; if none decides it, classify as preference and defer |
| A finding has no reason attached | Ask for the connection to objective/rule/audience; without it, it is preference |
| Finding requires re-opening the direction | Route to [Moodboards](moodboards.md)/[Ideation](ideation.md); label it a design round, not a correction |
| Reviewer proposes solutions mid-review | Capture the finding, note the proposal, move on; solutions are drafted in the iteration round |
| Time insufficient for all steps | Compress depth, keep order; never silently skip accessibility or defects |
| Stakeholder overrides a reasoned finding | Record the override, the evidence, and the accepted risk — the record is the deliverable |

## 7. Examples

- The §5.2 poster example shows the full loop: objective → ordered findings → classified, prioritised corrections → re-evaluation with regression check.
- **Facilitation example:** a 40-minute session, five attendees: author states intent (2 min), steps 1–2 pre-filled, steps 3–8 produce six findings, step 9 finds two typos, step 10 sorts them, facilitator reads back the list. One deferred preference, recorded with reason. Total output: one change list, no redesign debates.
- **Taste-vs-reason example:** "the poster looks boring" becomes, after attribute questioning, "the headline is the same weight as the sponsor block" — an observation, connected to the objective ("event name must dominate"), and fixed in one round.

## 8. Common mistakes

- **Skipping steps 1–2.** Judging artefacts without objectives measures the reviewer's taste and settles nothing.
- **Skipping accessibility "because it looks fine".** Contrast failures are invisible to confidence; they are found by computation, which is why step 8 is fixed in the sequence.
- **Reviewing without fresh eyes.** Everyone involved in the work shares its blind spots; one uninvolved reviewer is the minimum, not a luxury.
- **Solutions displacing findings.** The session becomes redesign by committee; the change list becomes incoherent.
- **Defending in the room.** The author's rebuttals teach reviewers to pre-soften feedback; the record gets shorter every session.
- **Unprioritised output.** Forty unsorted comments guarantee that the important and the trivial get equal airtime; step 10 exists to prevent this.
- **No re-evaluation.** Fixes assumed to work that quietly broke something else; step 11 is the loop's closing bracket.
- **Losing the record.** Findings that live only in the meeting evaporate before the next round; the findings table feeds [Iteration](iteration.md) §4.2.

## 9. Evaluation checklist

- [ ] Objective and audience were stated (steps 1–2) before any visual evaluation.
- [ ] All eleven steps ran, in order; none silently skipped.
- [ ] Contrast and other measurable checks are recorded as computed numbers.
- [ ] Every finding carries a class and a reason connected to objective, rule, standard or audience.
- [ ] Defects were hunted at multiple zoom levels with full proofreading.
- [ ] Corrections were prioritised by severity × effort, accessibility and defects first.
- [ ] Re-evaluation re-ran the failed steps and included a regression pass.
- [ ] At least one uninvolved reviewer participated (for group reviews).
- [ ] The findings table is recorded and handed to the iteration change list.
- [ ] Deferred preferences are documented with reasons.

## 10. Related topics

- [Design critique](../foundations/design-critique.md) — the judgment skills this process deploys (what makes critique reasoned).
- [Iteration](iteration.md) — the change-list and re-evaluation mechanics this process feeds.
- [Design quality framework](../evaluation/design-quality-framework.md) — the quality criteria underlying several steps.
- [Design thinking](design-thinking.md) — the test mode inside the larger process.
- [Research and discovery](research-and-discovery.md) — the objectives and audience facts steps 1–2 depend on.
- [Moodboards](moodboards.md) — the rules that step 7 checks consistency against.
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) and [Accessible colour](../accessibility/accessible-colour.md) — the standards behind step 8.
- [Brand guidelines](../branding/brand-guidelines.md) — the consistency reference for step 7.

## 11. References

- Mission specification §7.4 (this repository) — the eleven-step sequence is taken directly from it; per-step guidance is this file's elaboration of standard practice.
- Nielsen Norman Group, "Design Critiques: Encourage a Positive Culture to Improve Design Work" (2016) — establish rules and expectations beforehand; critique-as-culture framing. `[search-verified]` https://www.nngroup.com/articles/design-critiques (accessed 2026-11-23)
- UX Collective, "Improving design critiques" (2025) — distinction between critique and direction-giving feedback. `[search-verified]` https://uxdesign.cc/improving-design-critiques-0e4d075ead2f (accessed 2026-11-23)
- W3C, *Web Content Accessibility Guidelines (WCAG)* — contrast thresholds and perceptibility requirements used in step 8. `[canonical]`
- Josef Müller-Brockmann, *Grid Systems in Graphic Design* — the composition evaluation tradition behind step 6. `[canonical]`
- The findings-class taxonomy (defect / objective / accessibility / consistency / preference) and the severity × effort prioritisation are this file's synthesis of common studio practice; treat as conventions of this library, not external standards.
