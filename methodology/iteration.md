# Iteration

## 1. What is it?

Iteration is the practice of improving a design through deliberate, recorded rounds of change — each round driven by specific feedback, tested against specific expectations, and compared against what came before. It is deliberately *not* the same as "tweaking until it looks right": an iteration is a change with a reason, and a loop that terminates on evidence rather than fatigue.

Iteration occupies the space between selection and delivery: the direction has been chosen (see [Ideation](ideation.md), [Moodboards](moodboards.md)); now it must be made correct, coherent and production-ready through structured review cycles (see [Design critique](design-critique.md)).

## 2. Why does it matter?

First drafts are systematically wrong in predictable ways: hierarchy is muddled, contrast fails on some pairings, the composition works at one size but not another, the wording doesn't match the objective. None of this is discovered by staring — it is discovered by structured review, and it is fixed by iteration. Teams that skip structured iteration produce designs that *look* finished and quietly fail their objectives; teams that iterate without structure churn indefinitely, changing things because they can, losing coherence with every round.

The discipline matters for both directions of failure. Too little iteration ships known defects; too much iteration destroys the design's original logic (death by a thousand preferences) and consumes the schedule. Deliberate iteration is the middle path: every change justified, every round compared, every stoppage earned.

## 3. Core principles

- **Deliberate change, not drift.** Each round changes specific things for specific reasons. "I made some adjustments" is drift; "I increased heading scale by one step and moved the CTA above the fold because critique step 3 failed" is iteration.
- **One hypothesis per round.** Each round states what it expects to fix: "after this change, the schedule should be scannable in under five seconds on a 375px viewport." The next review tests the hypothesis, not everything again.
- **Feedback is triaged before it becomes change.** Not all feedback deserves action. Classify first (defect / objective conflict / preference), then decide (see [Design critique](design-critique.md) §6).
- **Change as little as possible per round, but enough.** One variable at a time keeps cause and effect legible; but trivial one-item rounds waste review cycles. A working round handles one coherent cluster of fixes.
- **Stop on criteria, not on vibes.** Diminishing returns, checklist completion, and feedback convergence are the legitimate stop signals; boredom and deadline pressure are not criteria, though deadlines are real constraints.
- **Version and record.** Every round is saved and described. Without versioning you cannot compare, cannot roll back, and cannot explain the final state (see [Brand guidelines](../branding/brand-guidelines.md) on decision documentation).

## 4. How it works

### 4.1 What to change between rounds

A round should change one of the following, in rough priority order — never everything at once:

1. **Objective failures** — the artefact doesn't meet its communication objective (wrong emphasis, missing information, wrong audience tone). Highest priority; these are defects against the brief.
2. **Accessibility and legibility failures** — contrast pairs below WCAG thresholds, text too small, touch targets too small, missing states. Non-negotiable; verified with tools, not opinion (see [Accessible colour](../accessibility/accessible-colour.md), [WCAG fundamentals](../accessibility/wcag-fundamentals.md)).
3. **Hierarchy and composition defects** — unclear reading order, competition between elements, broken alignment (see [Composition](../foundations/composition.md), [Information hierarchy](../information-design/information-hierarchy.md)).
4. **Consistency defects** — deviations from the established rules: token drift, spacing violations, a second accent colour creeping in (see [Visual consistency](../design-systems/visual-consistency.md)).
5. **Polish** — micro-adjustments of spacing, optical alignment, kerning. Legitimate, but only after classes 1–4 are clean; polish first is a classic smell.

What *not* to change between rounds without explicit re-opening of the direction: the core concept, the palette structure, the type voice. Changing these mid-iteration is not iteration; it is a new design round and should be labelled as such (back to [Moodboards](moodboards.md) or [Ideation](ideation.md)).

### 4.2 Capturing feedback into a change list

Every review produces raw commentary. Convert it into a change list before touching the file:

| Field | Content | Example |
| --- | --- | --- |
| ID | Round + sequence | R3-04 |
| Source | Who/what said it | Critique step 8 (accessibility); stakeholder comment |
| Class | Defect / conflict / preference | Defect |
| Finding | What specifically fails | Amber on off-white measures 2.1:1 for body text |
| Action | What will change | Body text switches to ink; amber restricted to accents ≥24px |
| Expected result | The round's hypothesis | All text pairs pass WCAG AA (4.5:1) |
| Status | Open / done / rejected (with reason) | Done |

Rules of conversion: every actionable item needs a class; every defect gets an action and an expected result; preferences are recorded and explicitly deferred (not silently dropped — stakeholders notice); conflicts go back to objectives before becoming actions. Items without a class are how design churn begins.

### 4.3 Comparing variants systematically

Comparison is how you know a change worked. Methods, from cheapest to most expensive:

- **Before/after, same artefact, same view.** Side-by-side at identical size and crop; annotate what changed and why. Prevents "I think it's better" claims that dissolve under scrutiny.
- **Variant matrix.** When several solutions to one problem exist (three hierarchy treatments), put them in a grid with the evaluation criteria as columns; score, then decide (the criteria table from [Ideation](ideation.md) §4.4).
- **Change one variable at a time** when the cause matters: if round 3 changes scale *and* spacing, you cannot know which fixed the scan. Where a change is cheap to isolate, isolate it.
- **Test at the extremes.** Check the artefact at its smallest and largest intended size, in the least favourable medium (e.g. grayscale print, low-end phone) — a comparison that only passes in the presentation context is not a pass.
- **Measure what can be measured.** Contrast ratios, text sizes, line lengths, tap-target dimensions, file weights — these are numbers; record the numbers per round rather than impressions.

### 4.4 Knowing when to stop

Stop signals, in order of legitimacy:

1. **Checklist completion:** the evaluation checklist (see [Design quality framework](../evaluation/design-quality-framework.md) and [Design critique](design-critique.md) §9) passes, including the accessibility checks.
2. **Feedback convergence:** the same complaints have stopped appearing from independent reviewers; the change list has no open defect-class items.
3. **Diminishing returns:** the last round changed things nobody could articulate as a problem, or improvements now require re-opening the direction. A practical heuristic: if two consecutive rounds produce only class-5 (polish) changes that reviewers cannot spontaneously point to, iteration is done.
4. **Constraint exhaustion:** budget or deadline reached. Legitimate, but be honest: state what was deferred, and record it as an open item rather than calling the design perfect.

Non-signals that feel like stops: "it looks good to me now" (one viewer, no criteria), "we're out of time so it must be right", "the client stopped replying".

### 4.5 Versioning design work

- **Name versions, don't overwrite.** `badge-v1`, `badge-v2`, … or dated snapshots. The working file is separate from released snapshots.
- **Version the rounds, not the saves.** A version corresponds to one iteration round with its change list; five intermediate saves within a round don't need five versions.
- **Keep a changelog.** One list per artefact: version, date, change summary (from the change list), open items. This is what lets a future agent (or you, in three weeks) reconstruct the reasoning.
- **Mark the approved version.** The version that passed review and any stakeholder sign-off is labelled explicitly (`v4-approved`), so later experiments branch from it rather than drifting from it.
- **Record the rationale with the version.** Why v4's heading is 56px and not 48px belongs in the changelog entry, not in memory. This links iteration to design rationale (see [Design critique](design-critique.md) §5).

## 5. Practical application

### 5.1 Worked round (event badge, continued from the ideation example)

- **Input:** v3 of the badge fails critique steps 3 and 8: name not legible at 3 metres (12pt name type); amber-on-off-white body text at 2.1:1 contrast.
- **Change list:** R4-01 (defect, step 3): name type 12pt → 28pt, weight 600; R4-02 (defect, step 8): body text to ink #1E2733, amber restricted to the accent rule; R4-03 (preference, stakeholder): "prefer rounded corners" — deferred, recorded with reason (conflicts with logo's sharp geometry).
- **Hypothesis:** after R4, name legible at 3m and all text pairs ≥4.5:1.
- **Verification:** contrast computed programmatically; badge printed at actual size and read at 3m; before/after captured.
- **Result:** R4-01, R4-02 verified done; R4-03 remains deferred with written reason. Changelog updated; `v4` snapshot saved.

## 6. Decision framework

| Question | If yes | If no |
| --- | --- | --- |
| Does the feedback class as a defect against objective or accessibility? | Fix in the next round; highest priority | Continue triage |
| Does it conflict with the agreed direction/rules? | Discuss against objectives; possibly re-open the direction deliberately | Fix within the direction |
| Is it a preference? | Record, defer, and tell the stakeholder it is deferred | Do not silently drop or silently obey |
| Does the round change the concept, palette or type voice? | Label it a new design round, not iteration | Proceed as a normal iteration |
| Can the change's effect be isolated? | Change one variable and compare | Cluster coherent fixes and say so |
| Are two consecutive rounds producing only invisible polish? | Stop; iteration is done | Keep iterating on the open defect list |

## 7. Examples

- **Effective round (§5.1):** two defects fixed with one hypothesis, verified by measurement; a preference deferred with a recorded reason — the pattern to copy.
- **Churn example (anti-pattern):** five consecutive rounds adjusting heading size down then up then down again as different reviewers disagreed. Root cause: feedback was never triaged — each reviewer's preference became an action. Fix: resolve the disagreement once against the objective ("readable at arm's length on a lanyard"), then stop.
- **Coherence erosion (anti-pattern):** a kit whose components were each "improved" in separate unversioned rounds, ending with four shades of the accent colour and two heading treatments. Fix: version per artefact with a kit-level consistency check each round (see [Visual consistency](../design-systems/visual-consistency.md)).

## 8. Common mistakes

- **Changing without a hypothesis.** Rounds that "try some things" produce motion, not progress, and make the next review re-test everything.
- **Treating all feedback as equal.** A defect and a preference weighed the same guarantees churn; triage first.
- **Over-polishing early.** Spending round 1 on kerning while the hierarchy is broken.
- **Silently obeying or silently dropping preferences.** Both destroy trust; record and communicate.
- **No before/after discipline.** Without comparison, "better" is unfalsifiable and regressions go unnoticed.
- **Version sprawl or version silence.** `final-v2-FINAL-new.psd` is version theatre; no versions at all loses the rollback and the rationale. One version per round, with a changelog, is the working norm.
- **Iterating past the stop signals.** Re-opening settled decisions in the name of polish; the concept, palette and type voice are not iteration's subjects.
- **Losing the constraints mid-loop.** Later rounds drift from the fixed logo's geometry or the sampled palette; re-run the constraint check every few rounds.

## 9. Evaluation checklist

- [ ] Each round has a stated hypothesis and a change list with classified items.
- [ ] Every defect-class item has an action, an expected result and a verification method.
- [ ] Preferences are recorded with an explicit status (deferred/rejected/accepted) and reason.
- [ ] Before/after comparisons exist for each round, at identical size and context.
- [ ] Measurable properties (contrast, sizes, dimensions) are recorded as numbers per round.
- [ ] Versions correspond to rounds, with a changelog and an explicitly marked approved version.
- [ ] Iteration stopped on a listed stop signal, and deferred items are documented as open.
- [ ] No round silently changed the concept, palette structure or type voice.

## 10. Related topics

- [Design critique](design-critique.md) — the structured review that generates the change list.
- [Design thinking](design-thinking.md) — the test/iterate loops within the larger process.
- [Ideation](ideation.md) — what happens before iteration starts (selection, not refinement).
- [Moodboards](moodboards.md) — where the rules that iterations must respect come from.
- [Design quality framework](../evaluation/design-quality-framework.md) — the criteria completion is measured against.
- [Visual consistency](../design-systems/visual-consistency.md) and [Design tokens](../design-systems/design-tokens.md) — the consistency layer iterations must not erode.
- [Brand identity checklist](../evaluation/brand-identity-checklist.md) — kit-level completion criteria.
- [Design systems governance](../design-systems/governance.md) — who may change what after launch.

## 11. References

- This file is a synthesis of the sources below and of standard professional practice; no single source owns the method.
- Nielsen Norman Group, "Design Critiques: Encourage a Positive Culture to Improve Design Work" (2016) — review discipline that feeds change lists. `[search-verified]` https://www.nngroup.com/articles/design-critiques (accessed 2026-11-23)
- Stanford d.school, *An Introduction to Design Thinking: Process Guide* — the test-and-iterate loop framing. `[search-verified]` https://web.stanford.edu/~mshanks/MichaelShanks/files/509554.pdf (accessed 2026-11-23)
- W3C, *Web Content Accessibility Guidelines (WCAG)* — the measurable pass criteria referenced by stop signals. `[canonical]`
- Jake Knapp, *Sprint* (2016) — prototype-and-test round structure in compressed form. `[canonical]`
- The change-list format, triage classes and stop-signal heuristics are this file's synthesis; treat numeric heuristics (e.g. "two polish-only rounds") as conventional starting points, not external standards.
