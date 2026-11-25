---
name: frontend-design
description: >-
  The frontend-agent-library's central design workflow. Use when building,
  designing, redesigning, restyling, polishing or reviewing any website or web
  frontend: a landing page, company or product site, SaaS app, dashboard,
  e-commerce store, editorial site, portfolio, campaign or immersive
  experience. Runs a seven-phase workflow — understand, establish design
  direction (via Taste Skill and Be Ambitious), research inspiration, plan
  assets, implement, inspect and refine in a real browser, preserve knowledge —
  routing to this library's knowledge files per project type so agents produce
  distinctive, accessible, fast, production-ready frontends instead of the
  generic AI look. Triggers: building or reviewing any web UI, "make this look
  professional", "this looks generic/AI-made", frontend design tasks.
license: MIT
---

# Frontend Design Workflow

Build the right design for the right product, with exceptional execution. This skill is the routing layer for the **frontend-agent-library** — a knowledge base of design foundations, visual styles, typography, colour, motion, UX psychology, assets, inspiration references and QA methods. Its job: get you to the right 3–8 files for the task at hand, in the right order, and enforce the process that separates deliberate design from the generic AI look.

**Companion skills:** invoke **Taste Skill** (`design-taste-frontend`) for design taste, build rules and its real-browser checker/gate on landing-page-class builds; invoke **Be Ambitious** (`be-ambitious`) at the start of substantial projects to raise altitude, depth and range. See [skills/README.md](../README.md) for install/verify.

## Ground rules (all phases)

1. **Consult before deciding.** Read the routed files before making the decision they govern. A decision made from defaults is the generic look.
2. **Context efficiency.** Never read the whole library. This skill routes; each domain file states when it applies. Read mandatory files fully; consult additional ones as the work touches their subject.
3. **The claim-strength discipline.** Distinguish established principles, professional conventions and recommendations ([README §G](../../README.md)); verify volatile facts (URLs, versions, licences) before repeating them.
4. **Accessibility and performance are floors, not phases** — they apply continuously ([../../accessibility/wcag-fundamentals.md](../../accessibility/wcag-fundamentals.md), [../../frontend-engineering/performance.md](../../frontend-engineering/performance.md)).
5. **Honesty is a design constraint.** No invented logos-as-social-proof, testimonials, figures, or AI-people-as-customers. Mark assumed facts ([../../ui-ux/ux-fundamentals.md](../../ui-ux/ux-fundamentals.md) §5.7).

## Phase 1 — Understand

Understand the product, its users and the objective before anything visual: what is sold, who buys it, the one main action, the real material available (logo, screenshots, photos, copy, data), the type of frontend (landing page, dashboard, editorial, commerce, immersive, app). Write it down — this is the brief every later phase checks against.

Routes: [../../methodology/research-and-discovery.md](../../methodology/research-and-discovery.md) (mandatory); [../../ui-ux/ux-fundamentals.md](../../ui-ux/ux-fundamentals.md) (mandatory for app-class builds); [../../branding/brand-fundamentals.md](../../branding/brand-fundamentals.md) if brand foundations are unclear.

**Be Ambitious hook:** for substantial builds, run the ambition pass now — the goal beyond the goal, depth and range picks ([skills/be-ambitious](../be-ambitious/SKILL.md)). Better, not bigger.

## Phase 2 — Establish design direction

Determine the visual direction deliberately: the style position, palette behaviour, typography approach, layout grammar, motion character — written as decisions, not vibes.

1. Invoke **Taste Skill** — its kind-of-business decision, page plans, palette/pairing dealing and house rules govern landing-page-class builds. Where the taste skill covers the ground, it wins; this library supplies the theory beneath it.
2. Name the style position with the vocabulary: [../../visual-styles/README.md](../../visual-styles/README.md) → [interface styles](../../visual-styles/interface-styles.md) and [texture/period styles](../../visual-styles/texture-and-period-styles.md); the fit decision framework (§6 of interface styles) is mandatory.
3. Foundations for the direction: [../../foundations/principles-of-design.md](../../foundations/principles-of-design.md) and [../../foundations/composition.md](../../foundations/composition.md) (mandatory for any layout work); [../../graphic-design/art-direction.md](../../graphic-design/art-direction.md) to defend the direction.
4. Typography: [../../typography/typeface-selection.md](../../typography/typeface-selection.md) + [../../typography/font-pairing.md](../../typography/font-pairing.md) (mandatory). Colour: [../../colour/palette-development.md](../../colour/palette-development.md) (mandatory) with [../../colour/colour-accessibility.md](../../colour/colour-accessibility.md) checks.
5. Encode as tokens ([../../design-systems/design-tokens.md](../../design-systems/design-tokens.md)) and CSS architecture ([../../frontend-engineering/css-architecture.md](../../frontend-engineering/css-architecture.md)).

**Test the direction** as a moodboard before production ([../../methodology/moodboards.md](../../methodology/moodboards.md)).

## Phase 3 — Research inspiration

Find references appropriate to *this* product — and extract decisions, not pixels ([../inspiration/contributing.md](../../inspiration/contributing.md) §6 anti-copying rules).

1. Route from [../inspiration/use-case-index.md](../../inspiration/use-case-index.md) (mandatory).
2. Read the relevant collection entries ([../inspiration/websites/website-index.md](../../inspiration/websites/website-index.md)); browse directories with their filters ([../inspiration/directories.md](../../inspiration/directories.md)) — timeboxed.
3. Extract patterns ([../inspiration/patterns.md](../../inspiration/patterns.md)) into the plan: what this build takes from each reference and why.
4. Check the plan against the failure catalogue it must avoid: [../../evaluation/ai-design-failures.md](../../evaluation/ai-design-failures.md) (mandatory read once per project).

## Phase 4 — Plan assets

Identify the visual needs (slots, subjects, ratios, palette constraints) *from the design*, then acquire:

1. Run the acquisition workflow ([../../assets/acquisition-workflow.md](../../assets/acquisition-workflow.md) — mandatory): needs list → candidates → evaluation → route decision (sourced vs generated) → optimise → verify → record.
2. Source per asset class: [photography](../../assets/photography.md), [illustrations](../../assets/illustrations.md), [icons](../../assets/icons.md), [textures](../../assets/textures-and-materials.md), [3D](../../assets/3d-assets.md), [typography sources](../../assets/typography.md), [video/motion](../../assets/video-and-motion.md), [sound](../../assets/sound.md), [backgrounds/effects](../../assets/backgrounds-and-effects.md).
3. Generate when sourcing cannot hit the need: [../../assets/image-generation.md](../../assets/image-generation.md) (style sheet, seeds, sets, AI-tell QA).
4. Licences and provenance: [../../assets/licensing-and-provenance.md](../../assets/licensing-and-provenance.md) — the manifest is part of done.

## Phase 5 — Implement

Choose the stack from requirements — never by habit ([../../frontend-engineering/technology-selection.md](../../frontend-engineering/technology-selection.md) mandatory; record the decision).

1. **Stack:** technology-selection decision record; components from the verified ecosystem ([../../github-resources/catalogue.md](../../github-resources/catalogue.md)).
2. **Structure and layout:** [../../layout/grid-systems.md](../../layout/grid-systems.md), [../../layout/responsive-layouts.md](../../layout/responsive-layouts.md), [../../ui-ux/frontend-implementation.md](../../ui-ux/frontend-implementation.md) (mandatory); tokens per phase 2.
3. **Copy:** write all copy first, in one voice, facts marked — the taste-skill copy layer governs landing-class builds; [../../methodology/ai-assisted-design.md](../../methodology/ai-assisted-design.md) for the general AI-production loop.
4. **Motion:** purpose + hierarchy + interruptibility + reduced motion ([../../motion-and-interaction/motion-principles.md](../../motion-and-interaction/motion-principles.md) mandatory when animating); one library per layer ([../../motion-and-interaction/animation-libraries.md](../../motion-and-interaction/animation-libraries.md)); scroll patterns ([../../motion-and-interaction/scroll-experiences.md](../../motion-and-interaction/scroll-experiences.md)); micro-layer and sound ([../../motion-and-interaction/microinteractions.md](../../motion-and-interaction/microinteractions.md)).
5. **Dense surfaces:** forms/tables/charts ([../../frontend-engineering/forms-and-data-display.md](../../frontend-engineering/forms-and-data-display.md)) with the psychology floors ([../../ux-psychology/design-laws.md](../../ux-psychology/design-laws.md)).
6. **Accessibility throughout** ([../../accessibility/wcag-fundamentals.md](../../accessibility/wcag-fundamentals.md), [accessible colour](../../accessibility/accessible-colour.md), [accessible typography](../../accessibility/accessible-typography.md)) and **performance budgets** ([../../frontend-engineering/performance.md](../../frontend-engineering/performance.md)).

## Phase 6 — Inspect and refine

The build is not done when the code compiles; it is done when the rendered result passes QA.

1. Run the visual QA pass ([../../evaluation/website-visual-qa.md](../../evaluation/website-visual-qa.md) — mandatory): full check set including the browser-automation loop (§5.9) at the fixed viewport set down to 320.
2. Run the AI-failure recognition pass ([../../evaluation/ai-design-failures.md](../../evaluation/ai-design-failures.md)) on the captures.
3. For landing-page-class builds, the taste-skill's checker and gate mechanise this: run its scripts and reach `GATE: PASS` ([skills/taste](../taste/SKILL.md) §4 step 6).
4. Accessibility testing ([../../accessibility/accessibility-testing.md](../../accessibility/accessibility-testing.md)) and performance measurement ([../../frontend-engineering/performance.md](../../frontend-engineering/performance.md) §5.6) join the same defect list.
5. Fix → re-inspect → repeat. Findings merge into one prioritised list (blockers first: reflow, focus, contrast, honesty).

## Phase 7 — Preserve knowledge

Record genuinely reusable discoveries; avoid polluting the library with project-specific noise.

1. Exceptional sites discovered during the project → the inspiration contribution workflow ([../inspiration/contributing.md](../../inspiration/contributing.md)) — evaluate, inspect, write the entry, update index/patterns, commit.
2. New patterns worth naming → [../inspiration/patterns.md](../../inspiration/patterns.md) with a reference trace.
3. Useful assets/sources discovered → the asset catalogues ([../../assets/README.md](../../assets/README.md)) — only with verification ([../../references/frontend-phase-sources.md](../../references/frontend-phase-sources.md) discipline).
4. One commit per file, message naming domain and slug ([../../PROJECT_STATUS.md](../../PROJECT_STATUS.md) §10).

## Routing table — by project type

Load the mandatory files for the build's type; consult others as touched:

| Project type | Mandatory route | Additional |
| --- | --- | --- |
| **Landing page / company site** | taste-skill (governs), Phase 2 route, [use-case index](../../inspiration/use-case-index.md) SaaS row, [ai-design-failures](../../evaluation/ai-design-failures.md), [website-visual-qa](../../evaluation/website-visual-qa.md) | [assets](../../assets/README.md) per slot, [patterns](../../inspiration/patterns.md) |
| **Dashboard / app surface** | [ux-fundamentals](../../ui-ux/ux-fundamentals.md), [ui-fundamentals](../../ui-ux/ui-fundamentals.md), [css-architecture](../../frontend-engineering/css-architecture.md), [forms-and-data-display](../../frontend-engineering/forms-and-data-display.md), [design-laws](../../ux-psychology/design-laws.md), [wcag](../../accessibility/wcag-fundamentals.md) | [data-visualisation](../../information-design/data-visualisation.md), [performance](../../frontend-engineering/performance.md) |
| **Cinematic / immersive** | [scroll-experiences](../../motion-and-interaction/scroll-experiences.md), [animation-libraries](../../motion-and-interaction/animation-libraries.md), [interface styles](../../visual-styles/interface-styles.md) §4.10–4.12, [performance](../../frontend-engineering/performance.md), [Lusion/Igloo entries](../../inspiration/websites/website-index.md) | [3d-assets](../../assets/3d-assets.md), [texture styles](../../visual-styles/texture-and-period-styles.md) |
| **E-commerce** | [use-case index](../../inspiration/use-case-index.md) e-commerce row, [forms-and-data-display](../../frontend-engineering/forms-and-data-display.md) (checkout), [Stripe entry](../../inspiration/websites/references/stripe.md), [image-selection](../../imagery/image-selection.md) | [colour psychology](../../colour/colour-psychology.md), [performance](../../frontend-engineering/performance.md) |
| **Editorial / publishing** | [editorial-design](../../typography/editorial-design.md), [typesetting](../../typography/typesetting.md), [grid-systems](../../layout/grid-systems.md), [Ramp entry](../../inspiration/websites/references/ramp.md) | [web-typography](../../typography/web-typography.md), [image treatment](../../imagery/image-treatment.md) |
| **Portfolio / small site** | Phase 2 route, [Family entry](../../inspiration/websites/references/family.md), [patterns](../../inspiration/patterns.md) §heroes/§footers, [website-visual-qa](../../evaluation/website-visual-qa.md) | [one-page references](../../inspiration/directories.md) §4 |

**Minimum route for any frontend task:** one foundations file + the owning domain file(s) + the matching evaluation file — never fewer.

## Never

- The generic AI look: default gradients, uniform card grids, template SaaS structure, slop copy, unconsidered states ([../../evaluation/ai-design-failures.md](../../evaluation/ai-design-failures.md)).
- Accessibility or honesty traded for style.
- Animation without purpose; scroll-jacking; non-interruptible motion.
- Unlicensed or unrecorded assets; invented social proof; AI imagery presented as real people.
- Reading the whole library into context; skipping the QA loop because the code "looks right".
