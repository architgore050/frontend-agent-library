# Design System Audit

## 1. What is it?

A structured audit method for design systems: a procedure for measuring how well a design system — its tokens, components, documentation and implementations — holds together as a single, trustworthy infrastructure. It covers token coverage (are values hardcoded anywhere?), component API consistency, documentation completeness, state coverage per component, accessibility conformance per component, and drift between design and code. It ends in a scored report with a prioritised remediation plan.

This audit is the meta-level check behind [website-visual-qa.md](website-visual-qa.md): site QA asks "does this page obey the system?"; the audit asks "is the system itself whole, consistent and actually used?" It assumes the token model described in [../design-systems/design-tokens.md](../design-systems/design-tokens.md).

## 2. Why does it matter?

A design system's value is leverage: one fix propagates everywhere. Every token bypass, undocumented component and drifted implementation destroys that leverage — the system stops being a single source of truth and becomes a suggestion. Unlike an artefact defect (visible on one page), system defects are usually invisible until they multiply: the hardcoded hex value on one page becomes a rebrand that misses 40 screens; the undocumented state becomes an error state invented five different ways.

The audit exists to catch this decay early and quantitatively. A scored audit also gives the system team an argument for remediation work: "token coverage 62%, down 7 points this quarter" moves budget in a way that "things feel inconsistent" does not.

## 3. Core principles

**Principle 1 — Audit the system, not the artefacts.** The unit of analysis is the token list, the component inventory, the documentation set and the codebase — not individual pages (those belong to [website-visual-qa.md](website-visual-qa.md)). Artefact-level symptoms (a misaligned card) matter here only as evidence of a system gap.

**Principle 2 — Single source of truth is testable.** For every design decision (colour, spacing, radius, type, motion), the audit asks: is there exactly one authoritative definition, and do all implementations reference it? Duplicates and bypasses are findings even when they currently look identical, because they *will* drift.

**Principle 3 — Coverage, conformance and adoption are three different numbers.** Coverage: does the system define what is used? Conformance: do implementations match the definition? Adoption: how much of the product actually consumes the system? A system can score high on conformance (well built) and low on adoption (rarely used) — the report must state all three separately.

**Principle 4 — Accessibility is per-component, not aspirational.** Each component must conform in each of its states. A button that passes in default state and fails in focus is a failing button. The audit inherits criteria from [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md) and test methods from [../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md).

**Principle 5 — Score to compare, not to certify.** The scoring model (§5.7) makes audits comparable over time and across teams. A score is a management instrument; it does not certify "accessibility compliant" or replace conformance testing.

## 4. How it works

The audit runs in six phases, in order. Each phase produces findings with evidence, and the final phase scores the system. Budget roughly: one auditor-day per phase for a mid-sized system; the phases are separable, so partial audits are legitimate if reported as such.

**Phase 1 — Inventory.** List every token (by category: colour, spacing, type, radius, elevation, motion — per [../design-systems/design-tokens.md](../design-systems/design-tokens.md)), every component (by name, variants, states), every documentation page, and every known implementation (Figma libraries, code packages, platform codebases).

**Phase 2 — Token coverage and bypass analysis.** Diff every hardcoded value in implementations against the token list (§5.1). Output: token coverage rate and a bypass list.

**Phase 3 — Component API and state audit.** For each component: API consistency check (§5.2) and the full state matrix (§5.3).

**Phase 4 — Accessibility conformance per component.** Run the per-component criteria (§5.4) on each component in each state, using the methods of [../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md).

**Phase 5 — Documentation completeness.** Check every component and token against the documentation rubric (§5.5).

**Phase 6 — Drift detection and scoring.** Diff design definitions against code implementations (§5.6), compute the scores (§5.7), and produce the report with a prioritised remediation plan.

## 5. Practical application

### 5.1 Token coverage (bypass analysis)

What to check: every place a raw value can hide — component code (colours, sizes, radii), stylesheets, native platform styles, design files (Figma styles not linked to library tokens), email templates, exported documents. A value that equals a token is still a finding: it is a *duplicate definition*, not a use.

How: (1) extract the token list with resolved values; (2) scan implementations for raw values (regex/hex scan for colours, px/rem scans for sizes); (3) classify each hit: **matches a token** (bypass — replace with reference), **no token exists** (coverage gap — create the token), or **intentional exception** (must be documented to pass). Compute: token coverage = token-referenced values ÷ (token-referenced + hardcoded, excluding documented exceptions).

Pass criteria: coverage ≥ 95% for colour (the category where bypasses hurt most); every remaining hardcoded value either has a filed gap ticket or a documented exception. Anything below is scored and remediated (§5.7).

Typical findings: `#4a5568` duplicated from a pre-system era; spacing values at 17/23 px from hand-tuned pages; a component library importing raw values "temporarily".

### 5.2 Component API consistency

What to check, across the whole component inventory: naming conventions (one pattern for variants/sizes: `size="sm|md|lg"` everywhere, not `small` in one component and `sm` in another); prop semantics (same prop means the same thing in every component — `disabled` always disables interaction, never merely styles); event naming; composition patterns (does the system consistently use slots/children rather than one-off `children` hacks); and variant/state vocabulary matching design-file naming (the Figma variant names and code API names correspond one-to-one).

How: build a component API matrix (component × props × values) from the code and from the design library; diff the two; flag every deviation from the shared vocabulary.

Pass criteria: one documented naming pattern, zero conflicts; design-library variant names map 1:1 to code props; no two components define the same concept differently. Typical findings: `colour` vs `tone` vs `variant` meaning the same thing across three components; `size="large"` alongside `size="lg"`.

### 5.3 State coverage per component

What to check, per interactive component: the full state matrix exists in *both* design and code — default, hover, focus-visible, active/pressed, disabled, loading, error (inputs), selected/on, empty (containers), and any platform-specific states. Each state must be visually designed (not left to browser defaults), token-driven, and accessible (§5.4).

How: build the matrix (component × states × design/code) and mark each cell: defined / undefined / undocumented. Undefined states are coverage gaps; defined-but-undocumented states are documentation gaps; both are findings.

Pass criteria: every state cell for every interactive component is defined in design, implemented in code, and documented. Common gaps in practice: focus-visible, loading (async buttons), error on disabled inputs, empty states for list containers.

### 5.4 Accessibility conformance per component

What to check, per component per state: contrast of every text and non-text boundary (4.5:1 text, 3:1 large text and UI components — WCAG AA); visible focus treatment; keyboard operability (reachable, operable, no traps); correct semantics and roles (native elements preferred; ARIA only where needed); state communicated programmatically (`aria-expanded`, `aria-disabled`, `aria-invalid`), not only visually; target sizes (≥ 24 × 24 px WCAG 2.5.8 AA; ≥ 44 × 44 px is the stronger 2.5.5 convention — verify current criterion text); colour-independent signalling.

How: per component, run the manual keyboard/reader pass plus automated scans, then record conformance per state. The component-level verdict is the *worst* state's verdict: a button that fails contrast only in its disabled state is a failing button until that state passes (or the failure is documented as an accepted exception with a compensating mechanism).

Pass criteria: every component conforms in every state, or carries a documented, ticketed exception. Method details and tooling are in [../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md); definitions in [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md).

### 5.5 Documentation completeness

What to check, per component: definition (what it is, when to use and when *not* to use); anatomy (parts labelled); variants and states shown with visual examples; do/don't guidance; content guidelines (voice of labels, character limits); accessibility notes (expected keyboard behaviour, ARIA contract); design-library and code references with version; changelog. Per token: name, resolved value(s), usage intent, and where *not* to apply it.

How: score each component page against the rubric (a simple count of sections present and populated — empty sections fail, per the no-placeholder rule); spot-check that code snippets compile and examples match the current API (stale examples are a drift finding, §5.6).

Pass criteria: 100% of components have definition, anatomy, variant/state gallery, accessibility notes and references; token pages complete for all categories. A component "in the library but not documented" is treated as unreleased.

### 5.6 Drift detection (design ↔ code)

What to check: the same component as defined in the design library versus implemented in code — geometry (padding, radius, sizes), colour values, states, behaviour (motion, interaction outcomes), and naming (§5.2's mapping). Also version drift: multiple published versions in use; product teams pinned to old versions; design library ahead of code without a changelog.

How: for each component, overlay design-exported geometry against code computed styles on a reference page; diff the state screenshots side by side; compare token references (design uses token A, code hardcodes its resolved value — §5.1 overlap). Maintain a drift register: component, nature of drift, which side is wrong (design or code — the system's decision, stated explicitly).

Pass criteria: zero undocumented geometrical/colour drift; one published version per component in active use (or documented, dated deprecation); every drift entry has an owner and a decision. Drift is expected to exist; what fails is drift without a register, an owner or a decision.

### 5.7 Scoring model

Score five dimensions, each 0–100, weighted by the system's maturity and risk profile (defaults below; adjust weights to context and state the adjustment in the report):

| Dimension | Weight (default) | What it measures |
| --- | --- | --- |
| Token coverage | 25% | % of values token-referenced across implementations (§5.1) |
| Component conformance | 25% | % of components with complete state matrices and zero undocumented drift (§5.3, §5.6) |
| Accessibility conformance | 25% | % of components conforming in all states (§5.4) |
| Documentation completeness | 15% | % rubric sections present and populated (§5.5) |
| Adoption | 10% | % of product surface built from system components (measured via dependency analysis or page sampling) |

Grade bands (conventional, for tracking over time — not a certification): ≥ 90 healthy; 75–89 solid with a backlog; 60–74 remediation sprint needed; < 60 the system is not yet a system — remediate before extending it. Report each dimension separately with its evidence; a single total without the breakdown hides exactly what needs work.

## 6. Decision framework

Audit findings are classified with the standard severity model ([design-quality-framework.md](design-quality-framework.md)), with system-specific anchors:

- **Blocker:** an accessibility failure in a *default or critical* state of a widely adopted component (focus invisible on primary buttons; contrast < 3:1 on form labels); single-source-of-truth failure where a fix cannot propagate (token list diverged from code tokens).
- **Major:** state coverage gaps on common components; undocumented drift; API vocabulary conflicts; coverage < 95% on colour tokens; a component undocumented but in active use.
- **Minor:** documentation rubric gaps on low-traffic components; version pinning one release behind; exception values missing from the exception register.
- **Polish:** naming beautification, changelog formatting, example refreshes.

Remediation order: (1) blockers in default states; (2) single-source-of-truth repairs (token regrouping, API vocabulary decision) — they unblock everything else; (3) state matrix completion, worst-adopted components first; (4) drift register and decisions; (5) documentation to rubric; (6) adoption push. Re-audit the affected dimension after each remediation wave — the loop per [design-quality-framework.md](design-quality-framework.md) §6 — and track dimension scores over time (§5.7) rather than only fixing the list.

## 7. Examples

**Example 1 — mid-sized product system.** Inventory: 48 tokens, 22 components, 14 documented. Findings: colour coverage 71% (34 raw hex values, 29 matching tokens — Major set); 3 components lack focus-visible in design and code (Blocker for the form components, Major for the rest); API conflict `size="lg"` vs `size="large"` in Button vs Badge (Major); drift register empty but 4 components show 2 px radius mismatch (Major); documentation rubric 61% (Minor/Major mix). Scores: coverage 71, conformance 64, a11y 78, docs 61, adoption 83 → weighted ≈ 70 → remediation sprint band. Plan: token regrouping first, then focus states, then the vocabulary decision, then drift register.

**Example 2 — a "high score" that still fails.** System scores 88 overall, but accessibility conformance is 100% *only because* states without designs were excluded from the sample. Recomputing with the full state matrix (§5.3's defined/undefined/undocumented cells) drops a11y to 74 and exposes the sampling error. Lesson: score definitions must be stated in the report so numbers cannot flatter the system.

**Example 3 — adoption finding.** Conformance is high (94) but adoption 40%: product teams re-implement components locally because the system's modal lacks a loading state. The audit's output is a *system* fix (add the state) plus an adoption decision, not page-level patches — illustrating Principle 1.

## 8. Common mistakes

- **Sampling states.** Auditing default states only produces flattering, meaningless scores; the matrix is the method (§5.3).
- **Counting look-alikes as coverage.** A hardcoded value that happens to equal a token is a duplicate definition, not token usage (§5.1).
- **Treating drift as failure of one side.** The audit's job is to decide *which side is wrong* and record it; unresolved drift is the failure (§5.6).
- **Auditing code without the design library** (or vice versa). Half the drift lives in the gap between them.
- **One total score, no breakdown.** Scores exist to direct work; the per-dimension table is the report (§5.7).
- **Unreleased components counted as done.** "In the library" without documentation and state coverage is not part of the system (§5.5).
- **Audit as event.** A single audit decays; schedule the next one and track dimension trends (§6).
- **Certification confusion.** The score is internal management instrumentation; it never substitutes for WCAG conformance claims (Principle 5).

## 9. Evaluation checklist

- [ ] Phase order respected; partial audit explicitly labelled as partial.
- [ ] Full inventory produced: tokens, components, docs, implementations.
- [ ] Bypass scan executed; every hit classified (bypass / gap / documented exception); coverage % computed.
- [ ] API matrix built; naming vocabulary conflicts listed and decisions proposed.
- [ ] State matrix complete per interactive component, in design *and* code.
- [ ] Per-component, per-state accessibility conformance recorded; component verdict = worst state.
- [ ] Documentation rubric applied to every component and token category; empty sections fail.
- [ ] Drift register created with decisions on which side is wrong; versions reconciled.
- [ ] Five dimension scores computed with weights stated; breakdown reported, not just a total.
- [ ] Findings classified per system-specific severity anchors; remediation ordered per §6.
- [ ] Re-audit scheduled; dimension trend tracking in place.

## 10. Related topics

- [design-quality-framework.md](design-quality-framework.md) — master method, severity model and report template.
- [website-visual-qa.md](website-visual-qa.md) — artefact-level QA that consumes this system.
- [../design-systems/design-tokens.md](../design-systems/design-tokens.md) — the token model the audit verifies.
- [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md) — criteria behind §5.4.
- [../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md) — per-component test methods.
- [../foundations/principles-of-design.md](../foundations/principles-of-design.md) — consistency as a design principle.
- [../methodology/design-critique.md](../methodology/design-critique.md) — critique process framing for audit workshops.

## 11. References

This audit method is a synthesis of the library's theory files and established design-system practice; grading bands and default weights are marked conventional.

- Brad Frost, *Atomic Design*, 2016 — component inventory and system thinking conventions. [canonical]
- Nathan Curtis, "Components vs Variants" and related EightShapes articles on component API and documentation practice — professional convention for API consistency and documentation rubrics. [canonical]
- W3C, "Web Content Accessibility Guidelines (WCAG) 2.1" — contrast and target-size criteria applied in §5.4. [canonical]
- W3C Web Accessibility Initiative, "Understanding Success Criterion 1.4.10: Reflow", https://www.w3.org/WAI/WCAG21/Understanding/reflow.html — criteria referenced by component/platform checks. [search-verified, accessed 2026-11-23]
