# Design Quality Framework

## 1. What is it?

The design quality framework is the master evaluation methodology for this library: a repeatable procedure for judging any designed artefact — poster, brand kit, website, slide deck, social asset or design system — against explicit criteria. It exists so that an agent does not evaluate "by feel". Instead of producing a vague impression ("looks good but the colours are off"), the evaluator produces a structured review: dimension-by-dimension findings, evidence for each finding, a severity for each defect, a prioritised correction plan and a re-evaluation loop.

The framework separates two kinds of judgement, and this separation is its most important rule:

- **Objective criteria** — measurable against a standard or a number: contrast ratio, alignment to a grid, adherence to a type scale, coverage of component states, file resolution, presence of required information. These can be tested mechanically or with tooling.
- **Subjective criteria** — matters of taste and context: whether a palette feels warm or cold, whether a layout feels energetic or calm, whether an illustration style suits the brand. These are legitimate to evaluate, but must be labelled as subjective, argued with reasons, and never presented as failures of fact.

Every domain checklist in this directory ([poster-checklist.md](poster-checklist.md), [website-visual-qa.md](website-visual-qa.md), [brand-identity-checklist.md](brand-identity-checklist.md), [social-media-checklist.md](social-media-checklist.md), [presentation-checklist.md](presentation-checklist.md), [design-system-audit.md](design-system-audit.md)) is a specialisation of this framework. When you evaluate an artefact type not covered by a checklist, apply this file directly.

## 2. Why does it matter?

Evaluation is where design quality is actually enforced. Without a framework, reviews drift: each reviewer notices different things, subjective disagreement is mistaken for factual error, and correction work is prioritised by whoever argues loudest. Three concrete problems the framework solves:

1. **Coverage gaps.** An unstructured reviewer checks what is easy to see (colours, spelling) and skips what requires method (focus states, print bleed, contrast on disabled elements). A dimension checklist guarantees each area is visited once.
2. **Unactionable feedback.** "Make it pop" is not a correction. A framework forces each defect to be described with evidence (what was measured, where it occurs), classified by severity, and paired with a proposed correction that can be verified after the fix.
3. **Unbounded subjectivity.** Agents (and humans) often present preferences as laws. Separating objective from subjective criteria protects the review's credibility: the objective findings are defensible, and the subjective ones are explicitly framed as judgement calls with reasoning, consistent with the critique method in [../foundations/design-critique.md](../foundations/design-critique.md).

There is also a self-service angle: this library is written for agents evaluating their own output. A framework turns "review your work" from a rubber stamp into a loop that measurably improves the artefact between iterations.

## 3. Core principles

**Principle 1 — Evaluate against the brief, not against taste.** Every artefact has a communication objective and an intended audience; these come first (step 1–2 of the review methodology in §5). A design that fails its objective fails, even if it is fashionable. A design that achieves an unglamorous objective is a success even if it is not exciting. Everything judged "subjectively" must be argued relative to the objective.

**Principle 2 — Objective criteria are testable, subjective criteria are argued.** If a claim can be verified with a number or a binary check (contrast ratio ≥ 4.5:1; logo present and unmodified; all headings use scale tokens), it belongs in the objective column and the verdict is pass/fail. If it cannot (harmony of the palette, quality of the concept), it belongs in the subjective column and must be written as a reasoned judgement, ideally with a concrete suggestion. Never blur the two: an objective claim without a measurement is an assertion, and a subjective claim written as fact is an overreach.

**Principle 3 — Evidence before verdict.** Every finding states: where the defect occurs (screen, breakpoint, slide, component), what was observed, what was expected (the standard, token or convention violated), and how severe it is. A finding without location and evidence cannot be verified or fixed.

**Principle 4 — Severity drives priority.** Not all defects deserve equal attention. The framework classifies each defect as blocker, major, minor or polish (§6) and orders the correction list accordingly. Fixing polish items while a blocker stands is wasted work.

**Principle 5 — Corrections are proposals, then the artefact is re-evaluated.** A correction proposal states the change, why it fixes the defect, and the risk it introduces (e.g. "raise body text to 18 px — may force the footer to wrap at 320 px"). After corrections are applied, the affected dimensions are re-tested, closing the loop (§6). One correction often introduces a new defect elsewhere; the loop exists to catch that.

**Principle 6 — Distinguish principle, convention, recommendation and preference.** As set out in [../foundations/principles-of-design.md](../foundations/principles-of-design.md): some criteria are established principles (hierarchy, contrast), some are professional conventions (bleed of 3 mm in print, 24 pt minimum slide body text), some are context-dependent recommendations (accent colour usage depends on the brand), and some are subjective preferences. The review should say which is which, so the designer knows what is negotiable.

## 4. How it works

### 4.1 The evaluation dimensions

The framework evaluates ten dimensions. For each: what it covers, objective criteria where they exist, and subjective criteria (always labelled).

#### Dimension 1 — Visual hierarchy

What it covers: whether the artefact's ordering of attention matches its message ordering — primary message first, secondary next, tertiary last.

| Type | Criteria |
| --- | --- |
| Objective | Squint test: number of attention "levels" identifiable is ≤ 3 per view; largest/most contrasted element matches the primary message; exactly one dominant element per view; heading-to-body size ratio ≥ 1.5 (conventional starting point); if a scale exists, all sizes drawn from it (see type adherence, §4.1.2) |
| Subjective (labelled) | Whether the felt reading order tells the intended story; whether emphasis feels earned rather than decorative |

How to evaluate: blur the artefact (or squint at it) and list the elements that still read, in order. Compare that list to the message order from the brief. Misalignment between the two is the core hierarchy defect.

#### Dimension 2 — Typography

What it covers: typeface choices, sizes, weights, line lengths and spacing.

| Type | Criteria |
| --- | --- |
| Objective | Line length ≈ 45–75 characters for body text (conventional range); body line height ≈ 1.4–1.6 × font size for running text (conventional); number of typefaces per artefact ≤ 2–3 families; minimum sizes respected for the medium (web body ≥ 16 px conventional; slide body ≥ 24 pt per published accessibility guidelines, see [presentation-checklist.md](presentation-checklist.md)); no faux bold/italic (real weights used); type scale adherence if a scale is defined |
| Subjective (labelled) | Voice and personality of the type pairing; whether the chosen faces suit the brand's tone |

#### Dimension 3 — Colour

What it covers: palette discipline, functional use of colour, and legibility of every text/background pair.

| Type | Criteria |
| --- | --- |
| Objective | Every text/background pair meets contrast: 4.5:1 normal text, 3:1 large text, 3:1 UI components and graphical objects (WCAG 2.1 AA); colour is never the only carrier of meaning; number of hues per artefact within the defined palette (0 stray colours); colour roles (primary/secondary/accent/neutral) applied consistently, per [../design-systems/design-tokens.md](../design-systems/design-tokens.md) if tokens exist |
| Subjective (labelled) | Palette mood versus brand personality; balance of colour weight across the composition |

#### Dimension 4 — Composition

What it covers: layout, alignment, spacing, balance and the use of the canvas.

| Type | Criteria |
| --- | --- |
| Objective | Every visible edge aligns to the grid or to another element's edge (within tolerance, e.g. ≤ 1 px on screen, ≤ 0.5 mm in print); margins/padding drawn from the spacing scale or divisibly related (e.g. multiples of 8 px — conventional); no content inside the safe area margin; optical balance checkable by quadrant-weight inspection; no unintentional overflow or clipped content |
| Subjective (labelled) | Whether negative space feels deliberate; tension, movement and visual weight distribution as expressive qualities |

#### Dimension 5 — Consistency

What it covers: same rules applied to same situations, across screens, slides, pages or items in a set.

| Type | Criteria |
| --- | --- |
| Objective | Repeated elements (headers, footers, buttons, captions, logo placement) are pixel-identical or token-identical across the set; same information type rendered in the same style everywhere (all dates one format, all prices one format); iconography from one family and one stroke weight; grid and margins constant across sibling artefacts |
| Subjective (labelled) | Whether deliberate variation (e.g. section colour changes in a deck) reads as rhythm rather than inconsistency |

#### Dimension 6 — Accessibility

What it covers: usability by people with visual, motor and cognitive impairments; standards conformance.

| Type | Criteria |
| --- | --- |
| Objective | Contrast per WCAG 2.1 AA (above); WCAG 1.4.10 reflow: content reflows without horizontal scrolling at 320 CSS px width (equivalent to 1280 px viewport at 400% zoom); minimum target size for interactive elements (conventional: ≥ 44 × 44 px per WCAG 2.5.5 AAA target / ≥ 24 × 24 px under 2.5.8 AA — verify against current WCAG); focus visible on every interactive element; text alternatives present; content readable without colour alone |
| Subjective (labelled) | Clarity of plain language; tolerance of cognitive load choices |

Accessibility has its own domain files: [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md) for the standards and [../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md) for test methods. This framework does not duplicate them; it consumes their criteria as inputs.

#### Dimension 7 — Responsiveness

What it covers (web only): behaviour across viewport sizes and devices.

| Type | Criteria |
| --- | --- |
| Objective | No horizontal page scroll at any tested width down to 320 CSS px (WCAG reflow condition); no clipped or overlapping elements at standard breakpoints (commonly 360, 768, 1024, 1440 — test set is a project decision); images scale without distortion (aspect ratio preserved); tap targets sized correctly on touch widths; text wraps rather than truncates unless truncation is intended and signalled |
| Subjective (labelled) | Whether the mobile layout preserves the priority of content or merely stacks it |

#### Dimension 8 — Brand compliance

What it covers: conformance to the identity rules of the organisation or event.

| Type | Criteria |
| --- | --- |
| Objective | Logo reproduced from official assets, not recreated; logo clear space respected; logo not stretched, recoloured, re-stacked or placed on a low-contrast ground; official colour values used verbatim (HEX/RGB/CMYK/Pantone as specified); approved typefaces used, or documented substitutes; if a guideline document exists, no rule contradicted |
| Subjective (labelled) | Whether flexible interpretation of the identity (e.g. an allowed "tone" of the palette) has been pushed beyond its spirit |

Brand kits are checked in depth by [brand-identity-checklist.md](brand-identity-checklist.md).

#### Dimension 9 — Information accuracy

What it covers: the factual content of the artefact — often the highest-severity dimension of all, because a wrong date is worse than an ugly poster.

| Type | Criteria |
| --- | --- |
| Objective | Names, dates, times, venues, prices, URLs, contact details and version numbers verified against the source of truth (brief, database, calendar); spelling and grammar checked; numbers add up (totals, percentages, chart values match the data); no placeholder text remains ("lorem ipsum", "XXX", "TBC"); QR codes and links resolve to the intended destination; translations consistent if multi-language |
| Subjective (labelled) | Whether information density suits the audience's familiarity (expert vs. general public) |

#### Dimension 10 — Production quality

What it covers: technical readiness of the deliverable for its medium.

| Type | Criteria |
| --- | --- |
| Objective | Print: bleed present (commonly 3 mm — confirm with the printer), safe area respected, resolution ≥ 300 DPI at final size, CMYK (or as specified) colour mode, fonts embedded/outlined; web: assets exported at correct sizes and formats, no unused heavy assets, favicon and metadata set; video/motion: safe margins for captions, correct frame rate; all exports open and render correctly |
| Subjective (labelled) | Whether asset naming and file organisation follow the project's conventions |

### 4.2 Weighting by artefact type

Not every dimension matters equally everywhere. The per-artefact checklists apply these weightings; the general ordering below guides where to look first:

| Artefact | First-order dimensions | Note |
| --- | --- | --- |
| Poster | information accuracy, hierarchy at distance, production quality | Read at 2–5 m; a print defect ruins the run |
| Brand kit | brand compliance, colour/type system, documentation quality | Output is the rules themselves |
| Website | accessibility, responsiveness, consistency, information accuracy | Continuous use, many states |
| Social assets | platform fit, readability at feed size, set consistency | Seen small, briefly, in a stream |
| Presentation | projection legibility, data slide quality, narrative flow | Seen large, once, in sequence |
| Design system | token coverage, component consistency, documentation | Output is the infrastructure |

## 5. Practical application

### 5.1 The review procedure

The framework follows the eleven-step review methodology established for this library (mission §7.4), expanded with evidence and severity steps:

1. **Identify the communication objective.** What must the audience know, feel or do? If there is no brief, write one sentence yourself and state it in the review as an assumption.
2. **Identify the intended audience and context of use.** Distance, device, speed of viewing, expertise.
3. **Evaluate visual hierarchy** (§4.1, dimension 1) — squint test, reading order versus message order.
4. **Evaluate typography** — scale adherence, sizes, line measures.
5. **Evaluate colour** — palette discipline, contrast pairs measured.
6. **Evaluate composition** — alignment audit, spacing audit, canvas use.
7. **Evaluate consistency** — compare every repeated element across the set.
8. **Evaluate accessibility** — run the objective tests from §4.1 dimension 6; for web, follow [../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md).
9. **Evaluate responsiveness, brand compliance, information accuracy and production quality** — the remaining dimensions relevant to the artefact type.
10. **Identify defects** — one defect record per finding, each with location, evidence, violated standard and severity (§6).
11. **Prioritise corrections, propose them, and re-evaluate** after fixes are applied (§6).

Steps 3–8 correspond to the theory domains: hierarchy and composition rest on [../foundations/principles-of-design.md](../foundations/principles-of-design.md); the critique stance itself is elaborated in [../foundations/design-critique.md](../foundations/design-critique.md) and [../methodology/design-critique.md](../methodology/design-critique.md).

### 5.2 Tools and measurement methods

- **Contrast:** compute ratio from relative luminance of the two colours; use any WCAG-based contrast checker or the formula in [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md). Record the actual ratio in the report, not just "fail".
- **Alignment:** on screen, inspect pixel positions via dev tools or a screenshot with overlaid guides; in print, check against the grid in the source file. Tolerance: exact for grid edges; ≤ 1 px drift acceptable for optical alignment cases.
- **Type scale adherence:** list every distinct font size in the artefact; compare against the defined scale. Any size not on the scale (or not a documented exception) is a finding.
- **Colour token adherence:** sample every used colour value; compare against the token list. Hardcoded values that duplicate a token are findings (see [design-system-audit.md](design-system-audit.md) for the full method).
- **Reflow/zoom:** set viewport to 320 × 256 CSS px (or zoom a 1280 px window to 400%) and inspect for horizontal scrolling and overlaps.
- **Squint/blur test:** rasterise the artefact, blur it heavily (or view from distance), list the readable elements in order.
- **Distance test (print/environment):** place the artefact at its realistic viewing distance; if that is impossible, the sizing convention in [poster-checklist.md](poster-checklist.md) provides estimates.

### 5.3 The review report template

```markdown
# Design review report

- Artefact: <name, version>
- Reviewed by / date:
- Objective (from brief or assumed): <one sentence>
- Audience and context: <who, where, at what distance/device>

## Summary
<3–5 sentences: overall verdict, count of blockers/majors/minors/polish,
the single most important correction.>

## Findings

| # | Dimension | Location | Observation (evidence) | Expected / standard | Severity | Proposed correction |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Colour | Footer CTA, mobile 360px | Measured 2.9:1 | WCAG AA 4.5:1 for normal text | Blocker | Darken CTA background to token `colour.primary.700` |

## Subjective observations (labelled as judgement)
- <Observation + reasoning + suggestion. State clearly that these are opinions.>

## Assumptions
- <Anything the review assumed because no brief/source of truth existed.>

## Re-evaluation
| # | Original finding | Fix applied? | Re-test result | Resolved |
| --- | --- | --- | --- | --- |
```

## 6. Decision framework

### 6.1 Defect identification

A defect is any gap between what the artefact is and what the applicable standard, token, brief or established principle requires. Write one record per defect — do not merge ("typography is bad" is not a record; "caption at 11 px below the 12 px minimum, on 6 slides" is). Each record names the dimension, location, evidence and violated standard, per Principle 3.

### 6.2 Severity classification

| Severity | Definition | Typical examples | Action rule |
| --- | --- | --- | --- |
| **Blocker** | Prevents the artefact from functioning or misleads the audience. Must be fixed before release. | Wrong date/price; unreadable text pair (contrast < 3:1); broken layout (content clipped/overlapping); logo visibly wrong; print file missing bleed; CTA missing | Fix before anything else; artefact not releasable |
| **Major** | Materially degrades quality or accessibility but artefact still works. | Contrast 3:1–4.5:1 on secondary text; hierarchy inverted (minor message dominant); inconsistent spacing across a set; missing focus states; type off-scale in prominent places | Fix in the current cycle; schedule explicitly |
| **Minor** | Localised flaw, small degradation, few viewers affected. | One misaligned caption; a stray non-token colour in one corner; slightly long line measure | Fix when convenient; batch with related work |
| **Polish** | Improvement opportunity; no degradation. | Better optical alignment; more refined micro-spacing; nicer empty state | Log for later; never blocks release |

Classification rules of thumb: anything touching information accuracy is at least major (wrong facts are blockers); anything that makes content unreadable to a whole class of users is a blocker or major; the same visual error repeated across a set is one severity level higher than an isolated instance, because it damages the system rather than one artefact.

### 6.3 Prioritisation

Order corrections by (1) severity, (2) fix effort, (3) dependency. Within equal severity, cheap fixes come first if they unblock others; expensive subjective rework comes last. A useful rule for agents: **never propose a correction that costs more than the defect's damage**. A minor spacing flaw on a one-off internal slide does not justify rebuilding the template.

### 6.4 Correction proposals

Each proposal states: the change (concrete, actionable), the standard or reasoning that justifies it, and the risk it introduces. Example:

> **Defect:** CTA button text 13 px on light green background, measured contrast 2.9:1 (fails WCAG 1.4.3).
> **Proposal:** Set text to token `text.inverse` (white) on `colour.primary.700` (measured 5.6:1). Risk: on the yellow variant card, `primary.700` is already used for the tag — acceptable, different component; re-test after applying.

### 6.5 Re-evaluation loop

After corrections: re-run the objective tests for every touched dimension (contrast re-measured, alignment re-checked, exports re-opened), confirm each original finding is resolved or has become a new finding, and update the report's re-evaluation table. Expect one or two loop iterations for major rework; if a third iteration surfaces new majors, the underlying decision (palette, layout system) is wrong, and the review should escalate to that decision rather than continue patching.

## 7. Examples

**Example 1 — Poster review (condensed).** Brief: one-day festival poster, seen on a street wall at ~3 m. Findings: (1) date printed as "12 March" but the event is 13 March — Blocker, information accuracy; (2) main title at 48 pt — at 3 m this reads, but the venue line at 14 pt fails the distance convention (~1 inch letter height per 10 ft comfortable viewing) — Major; (3) logo 8 mm from the trim edge, inside a 3 mm bleed zone risk — Major, production; (4) two non-palette tints used for the decorative shapes — Minor, colour discipline; (5) the decorative shapes could echo the festival's wave motif more literally — Polish, subjective. Priorities: 1 → 3 → 2 → 4 → 5.

**Example 2 — Website review (condensed).** Findings: (1) at 320 px width the hero overflows horizontally by 24 px — Blocker (WCAG reflow); (2) form inputs lack a visible focus ring on the checkout path — Blocker (keyboard users cannot see position); (3) body text uses hardcoded `#4a5568` instead of token `text.body` on 14 pages — Major, consistency/token drift; (4) error states shown by red border alone, without message text — Major (colour as sole carrier of meaning); (5) hero image 2.4 MB PNG where an ~150 KB WebP suffices — Minor, production. The re-evaluation loop then found the token fix caused the footer nav to wrap awkwardly at 360 px — a new Minor, logged in the same report.

**Example 3 — Subjective finding written correctly.** "The palette reads colder than the brief's 'warm welcome' positioning; this is a judgement, not a conformance failure. Swapping the neutral ramp's blue-grey for a warm grey (e.g. shifting hue slightly toward yellow) may be worth testing against the objective criteria unchanged." — labelled subjective, reasoned, reversible, and it does not claim a rule was broken.

## 8. Common mistakes

- **Presenting taste as conformance.** "The green is wrong" without a token, standard or measured failure is a preference, not a finding. Label it or verify it.
- **Objective claims without measurement.** "Low contrast" stated without the pair of colours and the ratio cannot be verified or re-tested. Always record the number.
- **Reviewing without the brief.** Judging hierarchy before knowing the intended message order produces confident nonsense. Steps 1–2 exist for this.
- **Merging defects.** One record per defect; merged records hide locations and make re-evaluation impossible.
- **Fixing polish while blockers stand.** Severity ordering exists because review cycles are finite.
- **Ignoring the loop.** Every correction can create a new defect (a bigger font reflows a layout; a darker colour breaks a relationship). Re-test touched dimensions, always.
- **Evaluating the artefact out of context.** A poster judged on screen at 100% zoom is being evaluated as a picture, not as a poster; a website judged only at 1440 px is being evaluated as a mockup, not as a website.
- **Checklist as ceiling.** Passing every item does not mean the design is good; the checklist catches conformance failures, while the subjective section (done honestly) is where excellence is argued for.

## 9. Evaluation checklist

- [ ] Communication objective and audience stated before any judgement was made.
- [ ] Every one of the ten dimensions visited at least once (or explicitly marked not applicable with a reason).
- [ ] Every objective finding includes: location, evidence (measurement or binary result), and the violated standard.
- [ ] Every subjective finding is explicitly labelled as judgement, with reasoning and a suggestion.
- [ ] Every text/background contrast pair measured; ratios recorded.
- [ ] All repeated elements compared across the full set for consistency.
- [ ] Information accuracy verified against a source of truth, not skimmed.
- [ ] Production/medium checks performed (bleed/DPI/colour mode for print; breakpoints and exports for web).
- [ ] Each defect classified blocker/major/minor/polish; correction order derived from it.
- [ ] Each correction proposal includes the change, justification and risk.
- [ ] Re-evaluation performed after fixes; results recorded in the report.
- [ ] Report uses the template in §5.3 and states assumptions openly.

## 10. Related topics

- [../foundations/design-critique.md](../foundations/design-critique.md) — the critique mindset this framework operationalises.
- [../foundations/principles-of-design.md](../foundations/principles-of-design.md) — theory behind the hierarchy, composition and colour criteria.
- [../methodology/design-critique.md](../methodology/design-critique.md) — critique as a repeatable process and workshop format.
- [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md) — the standards behind dimension 6.
- [../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md) — test methods for accessibility criteria.
- [../design-systems/design-tokens.md](../design-systems/design-tokens.md) — token model referenced by the consistency and adherence checks.
- [../information-design/data-visualisation.md](../information-design/data-visualisation.md) — criteria for chart-heavy artefacts (data slide and infographic reviews).
- [poster-checklist.md](poster-checklist.md) · [brand-identity-checklist.md](brand-identity-checklist.md) · [website-visual-qa.md](website-visual-qa.md) · [social-media-checklist.md](social-media-checklist.md) · [presentation-checklist.md](presentation-checklist.md) · [design-system-audit.md](design-system-audit.md) — artefact-specific applications of this framework.

## 11. References

This framework is a synthesis of the sources below plus the library's own theory domains; where a criterion is a widely used rule of thumb rather than a standard, it is marked "conventional starting point" in the text.

- W3C Web Accessibility Initiative, "Understanding Success Criterion 1.4.10: Reflow" (WCAG 2.1), https://www.w3.org/WAI/WCAG21/Understanding/reflow.html — source for the 320 CSS px / 400% zoom reflow condition. [search-verified, accessed 2026-11-23]
- Deque University, "1.4.10 Reflow (AA)", https://dequeuniversity.com/resources/wcag2.1/1.4.10-reflow — corroborating explanation of the reflow condition. [search-verified, accessed 2026-11-23]
- W3C, "Web Content Accessibility Guidelines (WCAG) 2.1" — contrast ratios (1.4.3, 1.4.11), reflow (1.4.10), target size (2.5.5/2.5.8). [canonical]
- Josef Müller-Brockmann, *Grid Systems in Graphic Design*, Niggli — basis for grid alignment criteria. [canonical]
- Ellen Lupton, *Thinking with Type*, Princeton Architectural Press — basis for typographic measure and hierarchy conventions. [canonical]
