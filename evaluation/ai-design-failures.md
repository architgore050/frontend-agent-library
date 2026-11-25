# AI Design Failure Modes

## 1. What is it?

A field guide to the recognisable failure modes of AI-generated (and generic-template) frontend design — how to spot each one in a rendered page, and the concrete corrective for each. It is the diagnostic companion to the visual QA pass ([website-visual-qa.md](website-visual-qa.md)), the taste layer's enforcement ([../../skills/taste/SKILL.md](../../skills/taste/SKILL.md) "the generic AI look"), and the reason this library exists in its current form: an agent cannot avoid these failures if it cannot name them.

## 2. Why does it matter?

AI frontends fail in *patterned* ways: the same gradients, the same card rhythms, the same copy tics, the same unconsidered states. Users now recognise the look instantly — it reads as "AI-made", which has become a trust penalty. Every failure below is fully avoidable with decisions this library teaches elsewhere; the guide's job is to connect each failure to its corrective file so a QA pass ends in fixes, not shrugs. The guide is deliberately not a rule that all designs must be unconventional — a restrained, minimal design can be exceptional when it is intentional; these failures describe the *unintentional* default.

## 3. How to use it

Run the recognition pass over the *rendered* page (screenshots at real widths — the QA loop), not the source code. Each failure below carries: **recognise** (the visual tell), **why it happens** (the generative root cause), and **corrective** (the file that owns the fix). Findings enter the QA defect list with severity per the [design quality framework](design-quality-framework.md).

## 4. The failure catalogue

### 4.1 The generic purple gradient

**Recognise:** a blue-violet gradient (the model-culture default hue family) behind heroes, buttons or backgrounds, unrelated to any brand decision. **Why:** training-data fashion — the gradient was the median "modern hero" and models regress to it. **Corrective:** a designed colour system — palette developed from the brand ([../../colour/palette-development.md](../../colour/palette-development.md)); atmosphere from the direction, not the default ([../../visual-styles/texture-and-period-styles.md](../../visual-styles/texture-and-period-styles.md) §7). The taste-skill bans violet outright for good reason; this library's softer rule: no gradient that the palette cannot justify.

### 4.2 Repetitive rounded cards

**Recognise:** every surface is the same medium-radius card with the same shadow, in uniform grids, at equal weights. **Why:** card-based UI is the safest generative pattern; without hierarchy decisions, everything becomes a card. **Corrective:** hierarchy before structure ([../../foundations/principles-of-design.md](../../foundations/principles-of-design.md)); varied composition per section ([composition](../../foundations/composition.md)); bento or editorial structures when the content genuinely varies ([../../visual-styles/interface-styles.md](../../visual-styles/interface-styles.md) §4.7).

### 4.3 Default-looking SaaS layouts

**Recognise:** hero → three feature columns → logos → testimonial → pricing → footer CTA, the exact template with the brand's logo pasted on. **Why:** the most-common training layout. **Corrective:** the design direction names a position ([../../skills/frontend-design/SKILL.md](../../skills/frontend-design/SKILL.md) phase 2); section plans are derived from *this* product's story ([../../methodology/research-and-discovery.md](../../methodology/research-and-discovery.md)); patterns are applied as decisions ([../patterns.md](../patterns.md)), not as the template.

### 4.4 Excessive glassmorphism

**Recognise:** glass panels on glass panels, blur stacking until nothing reads. **Why:** the "premium" reflex. **Corrective:** one atmosphere moment per page ([../../visual-styles/interface-styles.md](../../visual-styles/interface-styles.md) §4.1 limits), fallbacks and contrast checks ([../../accessibility/accessible-colour.md](../../accessibility/accessible-colour.md)).

### 4.5 Random gradients and effects

**Recognise:** gradients, glows, blobs and effects scattered without a system — each one individually plausible, collectively noise. **Why:** effects are the cheapest way to look "designed". **Corrective:** the atmosphere layer order and one-texture-system rule ([../../visual-styles/texture-and-period-styles.md](../../visual-styles/texture-and-period-styles.md) §3, §7); motion and effect budgets ([../../motion-and-interaction/motion-principles.md](../../motion-and-interaction/motion-principles.md)).

### 4.6 Generic stock imagery and repetitive AI imagery

**Recognise:** the handshake-and-whiteboard family; or five AI images with five different styles and light directions. **Why:** assets sourced without an art direction; generation without a style sheet. **Corrective:** the needs-first acquisition workflow ([../../assets/acquisition-workflow.md](../../assets/acquisition-workflow.md)), family treatment ([../../imagery/image-treatment.md](../../imagery/image-treatment.md)), generation style sheets ([../../assets/image-generation.md](../../assets/image-generation.md) §5.4), and the taste-skill's harder rule — the client's own subject leads.

### 4.7 Poor typography

**Recognise:** default font stacks, one weight, no scale, cramped measure, centre-everything. **Why:** typography requires decisions the model defaults past. **Corrective:** the type stack ([../../typography/web-typography.md](../../typography/web-typography.md)), scale discipline ([../../typography/typographic-hierarchy.md](../../typography/typographic-hierarchy.md)), and typography *as the design* where the direction calls for it ([../../typography/typeface-selection.md](../../typography/typeface-selection.md)).

### 4.8 Weak hierarchy

**Recognise:** everything shouts at the same volume; the eye has no reading order. **Why:** emphasis applied evenly (the Von Restorff inversion). **Corrective:** one primary message per surface, deliberate isolation ([../../ux-psychology/design-laws.md](../../ux-psychology/design-laws.md) §3.3), the hierarchy-first principle ([../../foundations/principles-of-design.md](../../foundations/principles-of-design.md)).

### 4.9 Spacing incoherence

**Recognise:** cramped sections next to empty ones; magic numbers; inconsistent gutters. **Why:** spacing generated per-element instead of from a scale. **Corrective:** the closed spacing scale ([../../layout/spacing-and-proportion.md](../../layout/spacing-and-proportion.md)) and the token architecture ([../../frontend-engineering/css-architecture.md](../../frontend-engineering/css-architecture.md)).

### 4.10 Unnecessary animation

**Recognise:** fade-ins on every section, parallax on text, perpetual loops, scroll-jacking. **Why:** animation added for "life" without purpose. **Corrective:** the purpose test and motion hierarchy ([../../motion-and-interaction/motion-principles.md](../../motion-and-interaction/motion-principles.md) §8); the honest scroll rules ([../../motion-and-interaction/scroll-experiences.md](../../motion-and-interaction/scroll-experiences.md) §3).

### 4.11 Generic iconography and decoration without purpose

**Recognise:** mismatched icon families, random emoji-as-icons, decorative blobs with no meaning. **Corrective:** one icon family ([../../assets/icons.md](../../assets/icons.md) §5), real brand marks for real products (Simple Icons), and the decoration test — every element answers "what does it explain?".

### 4.12 Unconsidered mobile layouts

**Recognise:** desktop layout squeezed; overlapping elements at 390 px; tap targets unreachable; horizontal scroll at 320 px. **Why:** mobile treated as a resize, not a design. **Corrective:** responsive-first craft ([../../ui-ux/responsive-design.md](../../ui-ux/responsive-design.md)), reflow verification ([website-visual-qa.md](website-visual-qa.md) §5.5), the taste-skill's phone checks (collide, tap-size, off-viewport).

### 4.13 Inconsistent visual language

**Recognise:** two button styles, three radii, mixed shadows; each surface plausible, the whole incoherent. **Corrective:** the token system ([../../design-systems/design-tokens.md](../../design-systems/design-tokens.md)), one-system QA check ([website-visual-qa.md](website-visual-qa.md) §5.7).

### 4.14 Copy tics and slop words

**Recognise:** "Unlock", "Elevate", "Seamless", "Empower", "revolutionary"; two-fragment headings; invented stat strips; the same sentence rhythm everywhere. **Why:** the model-copy median. **Corrective:** the taste-skill's copy layer and lint (`copy-lint.mjs`, `copy-voice.md`); the voice card ([../../skills/frontend-design/SKILL.md](../../skills/frontend-design/SKILL.md) phase 5 copy rules); facts only, marked assumptions.

### 4.15 Complex interfaces without need

**Recognise:** every feature crammed into the first screen; five CTAs; twelve-item navs. **Why:** completeness mistaken for quality. **Corrective:** progressive disclosure ([../../ux-psychology/design-laws.md](../../ux-psychology/design-laws.md) §3.8), cognitive-load budgeting (§3.18), the feature-section discipline.

### 4.16 Inaccessible contrast and states

**Recognise:** grey-on-grey text, invisible focus, colour-only errors. **Why:** aesthetics prioritised over the floors. **Corrective:** the WCAG floors ([../../accessibility/wcag-fundamentals.md](../../accessibility/wcag-fundamentals.md)) — non-negotiable in every style ([../../visual-styles/interface-styles.md](../../visual-styles/interface-styles.md) §3 principle 3); the state matrix ([../../ui-ux/ui-fundamentals.md](../../ui-ux/ui-fundamentals.md)).

### 4.17 Inappropriate style for the product

**Recognise:** Y2K gloss on a pension tool; brutalism on a hospital; glassmorphism on a dense trading UI. **Why:** fashion without fit. **Corrective:** the fit decision framework ([../../visual-styles/interface-styles.md](../../visual-styles/interface-styles.md) §6); atmosphere belongs to marketing surfaces, not working ones ([../../visual-styles/texture-and-period-styles.md](../../visual-styles/texture-and-period-styles.md) §8).

### 4.18 The lying interface

**Recognise:** fake logos as "trusted by", invented testimonials, pre-checked consents, fake progress bars, dashboards of random numbers. **Why:** generative filler filling trust-shaped holes. **Corrective:** honesty as a design constraint ([../../ui-ux/ux-fundamentals.md](../../ui-ux/ux-fundamentals.md) §5.7); honest defaults and progress ([../../ux-psychology/design-laws.md](../../ux-psychology/design-laws.md) §3.19, §3.10); the taste-skill's "no invented reviews, quotes, customers or figures" — blockers, not preferences.

## 5. The recognition pass

1. **Screenshot first** (real widths, real states) — failures are visible in render, not in code.
2. **Run the catalogue** (§4) as a checklist; each recognised failure enters the QA defect list with its corrective file named.
3. **Check the meta-failures:** would this page be identifiable as "AI-made"? Which three features say so? Those three are the priority findings.
4. **Verify the fixes in render** — the QA loop, not a one-pass assumption.

## 6. Common mistakes

- **Fighting the wrong failure** — adding maximalist "personality" to fix what is actually a hierarchy problem; the catalogue names the specific corrective per failure.
- **De-branding as de-AI-ing** — stripping everything distinctive to be "safe"; the goal is *intentional* design, and minimalism done deliberately is not a failure (§2).
- **Code-only review** — the failures live in the render; the pass is visual.
- **One-pass detection** — fixes reflow and re-reveal; the loop re-runs.

## 7. Evaluation checklist

- [ ] Recognition pass run over rendered screenshots at real widths.
- [ ] Each recognised failure logged with its corrective file and severity.
- [ ] The meta-test answered: what, specifically, marks this as generic?
- [ ] Priority findings fixed first (lying interface, accessibility, hierarchy), style refinements after.
- [ ] Re-render confirms fixes; no new failure introduced by the fix.

## 8. Related topics

- [Website visual QA](website-visual-qa.md) — the procedural QA this pass joins.
- [Design quality framework](design-quality-framework.md) — severity and reporting.
- [Taste skill](../../skills/taste/SKILL.md) — the enforcement layer (checker + gate) that mechanises much of this catalogue.
- [Design laws](../../ux-psychology/design-laws.md) — the psychological mechanisms behind hierarchy and honesty failures.
- [Visual styles](../../visual-styles/README.md) — the vocabulary for intentional alternatives.

## 9. References

- This file is the library's synthesis of documented AI-design failure patterns across the taste-skill research, professional practice and the corrective files it links; the "AI-made look" as a recognised user-facing phenomenon is treated as established professional observation.
- Leonxlnx, taste-skill research corpus — the slop taxonomy (copy tells, generic patterns) informing §4.14 and several entries. https://github.com/Leonxlnx/taste-skill [accessed 2026-11-25]
