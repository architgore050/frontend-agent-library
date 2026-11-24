# Frontend Agent Library

A structured Markdown knowledge base for frontend design, graphic design, visual communication, branding, typography, colour, layout, UI/UX, design systems, accessibility and design evaluation. It exists so that an AI agent — or a human designer — can understand design principles, make informed decisions, execute design work and evaluate its own output without rediscovering fundamentals each time. Its founding use case is extending an already-fixed event logo into a complete, usable brand kit; the library is deliberately reusable across future projects, events and organisations.

The library is organised as sixteen top-level directories: fifteen knowledge domains plus a `references/` directory holding the source layer (bibliography, case studies, tool registry, source-accessibility index). Every substantive file follows the same template — what it is, why it matters, core principles, how it works, practical application, decision framework, examples, common mistakes, evaluation checklist, related topics, references — so an agent always knows what it will find and where. Cross-links use repository-relative paths and are extensive: follow them when a concept you need is defined elsewhere.

**This README is a routing manual, not a textbook.** Its job is to send you to the right two to six files for your task, in the right order, and to state the ground rules (routing discipline, provenance tags, constraints) that keep the library trustworthy. The library at a glance, verified 2026-11-24: 15 knowledge domains plus a source layer, 89 substantive files, 24,165 lines of domain content, every file built on one standard template, and every citation carrying a provenance tag. Status: complete as of 2026-11-24; see [PROJECT_STATUS.md](PROJECT_STATUS.md) for per-domain completion evidence, known limitations and validation status.

---

## A. How to use this knowledge base

1. **Consult before deciding.** Before making any substantial design decision — palette, typeface, grid, component shape, evaluation verdict — read the relevant domain files first. The library's purpose is to replace rediscovery with consultation; a decision made without reading the mandatory references for its task (section C) is a decision made from defaults and priors.
2. **Route by task, then read fully.** Start from the task-based routing table (section C) or, for the six major project types, from the task workflows (section D). Read every file listed as *mandatory* for your task from beginning to end — they were sized for full reads (roughly 130–450 lines each). Read *additional* references selectively as the work raises questions they answer.
3. **Read the referenced domain files, not just the ones in your directory.** Design decisions cross domains: a palette decision reaches into accessibility, a poster decision reaches into typography and grids. The routing table already accounts for this — trust it rather than browsing one directory only.
4. **Use each file's decision framework and evaluation checklist.** Sections 6 and 9 of every file are the operational parts: the decision framework turns the file's principles into a procedure, and the checklist verifies the result. An agent that reads only the exposition and skips the checklist has used the library half-way.
5. **Follow provenance tags when repeating specifics.** Numeric guidance (contrast ratios, platform sizes, version numbers) is tagged by how it was verified. See section H and [Source accessibility](references/source-accessibility.md) before repeating any specific figure outside this library.
6. **When starting a whole project, not a single decision**, combine section D's reading sequence with the appropriate evaluation file up front, so the pass criteria are known before production begins.
7. **If your task is not in the table**, route it yourself by the same logic: the artefact type sends you to [applications/](applications/posters.md), the discipline to the matching domain directory, the intended outcome (a verdict, a pass/fail) to [Evaluation](evaluation/design-quality-framework.md). Then follow the minimum route in section B.
8. **If you are new to design**, read in this order first: [Principles of design](foundations/principles-of-design.md), then [Gestalt and perception](foundations/gestalt-and-perception.md), then the domain of your task. The foundations vocabulary is assumed by every other file; skipping it makes the rest read as unexplained jargon.

A note on scope: the authoring brief that governed how this library was written (`/home/z/my-project/scripts/kb/BRIEF.md`, outside this repository) is for authors, not consumers. Everything a consumer agent needs — routing, provenance rules, constraints — is self-contained in this README and in the files it links.

## B. Routing rules

- **Mandatory references** are files whose subject the task cannot be done correctly without. Read them fully before starting work. If you skip one, say so and why in your working notes; silent skipping defeats the routing system.
- **Additional references** deepen, specialise or verify. Consult them when the task actually touches their subject — a dark-mode palette needs [Colour in code](colour/colour-in-code.md); a poster for print needs the production parts of [Posters](applications/posters.md). Do not read additional references speculatively before the mandatory ones.
- **Minimum route.** Every design task, whatever its size, touches at least: one foundations file (principles or composition), the one or two domain files that own the artefact, and the matching evaluation file. That trio is the irreducible core — the routing table never goes below it.
- **Conflicts.** When two files appear to disagree, resolve by specificity: an artefact-specific file (e.g. a checklist) governs its artefact; a foundations file governs the general case. Where disagreement persists, the distinction to apply is stated inside the files themselves: established principles > professional conventions > context-dependent recommendations > subjective preference, in that order of authority.
- **Extending routes.** New task types should be added to the routing table with the same discipline: mandatory = cannot do the task without; additional = useful on contact with their subject. Every link added must resolve (test before committing — see section K) and the row must respect the minimum route above.
- **Depth calibration.** The library teaches reasoning, not just rules. If a file seems to state a "law", check its own framing: most numeric values are labelled as real sourced figures or as conventional starting points. Carry that framing into your output — do not upgrade a convention into a law when writing for users.
- **Reading budget.** A typical task needs three to six mandatory files; if your plan requires reading more than eight before any work begins, the task is probably several tasks — split it and route each part. Reading additional references before the mandatory ones is the commonest misuse of this router.

## C. Task-based routing table

Columns: the agent's task; files to read fully (**mandatory**); files to consult as the work touches their subject (**additional**). All links are repository-relative and verified. Where a row lists a checklist, read it before production, not only after.

| Agent task | Mandatory references | Additional references |
| --- | --- | --- |
| Build a complete brand kit from scratch | [Brand fundamentals](branding/brand-fundamentals.md), [Brand discovery](branding/brand-discovery.md), [Brand strategy](branding/brand-strategy.md), [Visual identity](branding/visual-identity.md) | [Brand personality](branding/brand-personality.md), [Palette development](colour/palette-development.md), [Typeface selection](typography/typeface-selection.md), [Logo systems](branding/logo-systems.md), [Brand guidelines](branding/brand-guidelines.md) |
| Analyse and extend a fixed logo into a brand system | [Fixed-logo analysis](branding/fixed-logo-analysis.md), [Logo systems](branding/logo-systems.md), [Visual identity](branding/visual-identity.md) | [Brand guidelines](branding/brand-guidelines.md), [Brand identity checklist](evaluation/brand-identity-checklist.md), [Graphic language](graphic-design/graphic-language.md), [Case studies](references/case-studies.md) |
| Select brand colours | [Colour theory](colour/colour-theory.md), [Colour psychology](colour/colour-psychology.md), [Palette development](colour/palette-development.md) | [Colour accessibility](colour/colour-accessibility.md), [Accessible colour](accessibility/accessible-colour.md), [Brand personality](branding/brand-personality.md), [Colour in code](colour/colour-in-code.md) |
| Choose fonts for a project | [Typography fundamentals](typography/typography-fundamentals.md), [Typeface selection](typography/typeface-selection.md), [Font pairing](typography/font-pairing.md) | [Brand personality](branding/brand-personality.md), [Web typography](typography/web-typography.md), [Accessible typography](accessibility/accessible-typography.md) |
| Create a poster | [Posters](applications/posters.md), [Composition](foundations/composition.md), [Typographic hierarchy](typography/typographic-hierarchy.md) | [Grid systems](layout/grid-systems.md), [Poster checklist](evaluation/poster-checklist.md), [Image treatment](imagery/image-treatment.md), [Visual identity](branding/visual-identity.md) |
| Design a website | [UX fundamentals](ui-ux/ux-fundamentals.md), [UI fundamentals](ui-ux/ui-fundamentals.md), [Responsive design](ui-ux/responsive-design.md) | [Information architecture](ui-ux/information-architecture.md), [Interaction design](ui-ux/interaction-design.md), [Frontend implementation](ui-ux/frontend-implementation.md), [Grid systems](layout/grid-systems.md), [WCAG fundamentals](accessibility/wcag-fundamentals.md) |
| Create a design system | [Design tokens](design-systems/design-tokens.md), [Component systems](design-systems/component-systems.md), [Visual consistency](design-systems/visual-consistency.md) | [Documentation](design-systems/documentation.md), [Governance](design-systems/governance.md), [Spacing and proportion](layout/spacing-and-proportion.md), [Design system audit](evaluation/design-system-audit.md) |
| Generate a moodboard | [Moodboards](methodology/moodboards.md), [Brand personality](branding/brand-personality.md), [Visual styles](graphic-design/visual-styles.md) | [Research and discovery](methodology/research-and-discovery.md), [Image selection](imagery/image-selection.md), [Colour psychology](colour/colour-psychology.md) |
| Review a design (judge quality) | [Design quality framework](evaluation/design-quality-framework.md), [Design critique (judgement)](foundations/design-critique.md) | The matching artefact checklist in [Evaluation](evaluation/design-quality-framework.md), [Gestalt and perception](foundations/gestalt-and-perception.md), [Principles of design](foundations/principles-of-design.md) |
| Run a facilitated critique process | [Design critique (process)](methodology/design-critique.md), [Design critique (judgement)](foundations/design-critique.md) | [Design quality framework](evaluation/design-quality-framework.md), [Iteration](methodology/iteration.md) |
| Create an infographic | [Diagrams and infographics](information-design/diagrams-and-infographics.md), [Information hierarchy](information-design/information-hierarchy.md), [Data visualisation](information-design/data-visualisation.md) | [Grid systems](layout/grid-systems.md), [Iconography](graphic-design/iconography.md), [Poster checklist](evaluation/poster-checklist.md) |
| Create social media assets | [Social media graphics](applications/social-media.md), [Social media checklist](evaluation/social-media-checklist.md), [Visual identity](branding/visual-identity.md) | [Image treatment](imagery/image-treatment.md), [Typographic hierarchy](typography/typographic-hierarchy.md), [Marketing assets](applications/marketing-assets.md) |
| Create certificates and formal documents | [Certificates and formal documents](applications/certificates-and-documents.md), [Typesetting](typography/typesetting.md), [Brand identity checklist](evaluation/brand-identity-checklist.md) | [Typography fundamentals](typography/typography-fundamentals.md), [Brand guidelines](branding/brand-guidelines.md) |
| Create event collateral | [Event collateral](applications/event-collateral.md), [Visual identity](branding/visual-identity.md), [Fixed-logo analysis](branding/fixed-logo-analysis.md) | [Logo systems](branding/logo-systems.md), [Posters](applications/posters.md), [Brand governance](branding/brand-governance.md) |
| Prepare a presentation | [Presentations](applications/presentations.md), [Presentation checklist](evaluation/presentation-checklist.md), [Typographic hierarchy](typography/typographic-hierarchy.md) | [Data visualisation](information-design/data-visualisation.md), [Image selection](imagery/image-selection.md), [Visual consistency](design-systems/visual-consistency.md) |
| Audit a design system | [Design system audit](evaluation/design-system-audit.md), [Design tokens](design-systems/design-tokens.md), [Visual consistency](design-systems/visual-consistency.md) | [Governance](design-systems/governance.md), [Documentation](design-systems/documentation.md), [Accessibility testing](accessibility/accessibility-testing.md) |
| Write brand guidelines | [Brand guidelines](branding/brand-guidelines.md), [Visual identity](branding/visual-identity.md), [Logo systems](branding/logo-systems.md) | [Brand governance](branding/brand-governance.md), [Palette development](colour/palette-development.md), [Typeface selection](typography/typeface-selection.md) |
| Generate imagery with AI | [AI image generation](imagery/ai-image-generation.md), [Image rights](imagery/image-rights.md), [AI-assisted design](methodology/ai-assisted-design.md) | [Image selection](imagery/image-selection.md), [Image treatment](imagery/image-treatment.md), [Brand personality](branding/brand-personality.md) |
| Make a chart or data graphic | [Data visualisation](information-design/data-visualisation.md), [Information hierarchy](information-design/information-hierarchy.md) | [Gestalt and perception](foundations/gestalt-and-perception.md), [Colour in code](colour/colour-in-code.md), [Design tokens](design-systems/design-tokens.md) |
| Apply accessibility to a design | [WCAG fundamentals](accessibility/wcag-fundamentals.md), [Accessible colour](accessibility/accessible-colour.md), [Accessible typography](accessibility/accessible-typography.md) | [Accessibility testing](accessibility/accessibility-testing.md), [Colour accessibility](colour/colour-accessibility.md), [UI fundamentals](ui-ux/ui-fundamentals.md) |
| Produce marketing and campaign assets | [Marketing assets](applications/marketing-assets.md), [Social media graphics](applications/social-media.md) | [Brand strategy](branding/brand-strategy.md), [Image selection](imagery/image-selection.md), [Brand governance](branding/brand-governance.md) |
| Build an icon set | [Iconography](graphic-design/iconography.md), [Graphic language](graphic-design/graphic-language.md) | [Visual identity](branding/visual-identity.md), [UI fundamentals](ui-ux/ui-fundamentals.md), [Accessible colour](accessibility/accessible-colour.md) |
| Establish a spacing and proportion system | [Spacing and proportion](layout/spacing-and-proportion.md), [Design tokens](design-systems/design-tokens.md) | [Grid systems](layout/grid-systems.md), [Typographic hierarchy](typography/typographic-hierarchy.md), [Component systems](design-systems/component-systems.md) |
| Check image licensing and rights | [Image rights](imagery/image-rights.md), [Image selection](imagery/image-selection.md) | [AI image generation](imagery/ai-image-generation.md), [Photography](imagery/photography.md) |
| Design a multipage document (report, brochure, programme) | [Editorial design](typography/editorial-design.md), [Typesetting](typography/typesetting.md), [Grid systems](layout/grid-systems.md) | [Typographic hierarchy](typography/typographic-hierarchy.md), [Certificates and formal documents](applications/certificates-and-documents.md), [Font pairing](typography/font-pairing.md) |
| Produce a logo variant and usage set | [Logo systems](branding/logo-systems.md), [Visual identity](branding/visual-identity.md) | [Fixed-logo analysis](branding/fixed-logo-analysis.md), [Brand guidelines](branding/brand-guidelines.md), [Iconography](graphic-design/iconography.md) |
| Set up brand governance after launch | [Brand governance](branding/brand-governance.md), [Brand guidelines](branding/brand-guidelines.md) | [Design system audit](evaluation/design-system-audit.md), [Tools and software](references/tools-and-software.md), [Design quality framework](evaluation/design-quality-framework.md) |
| Plan an end-to-end AI-assisted design workflow | [AI-assisted design](methodology/ai-assisted-design.md), [AI image generation](imagery/ai-image-generation.md) | [Design critique (process)](methodology/design-critique.md), [Image rights](imagery/image-rights.md), [Iteration](methodology/iteration.md) |
| Choose imagery for a brand | [Image selection](imagery/image-selection.md), [Photography](imagery/photography.md) | [Image treatment](imagery/image-treatment.md), [Image rights](imagery/image-rights.md), [Brand personality](branding/brand-personality.md) |
| Direct the visual output of a campaign | [Art direction](graphic-design/art-direction.md), [Visual identity](branding/visual-identity.md) | [Visual styles](graphic-design/visual-styles.md), [Marketing assets](applications/marketing-assets.md), [Graphic language](graphic-design/graphic-language.md) |
| Create a brand architecture for a family of brands | [Brand architecture](branding/brand-architecture.md), [Brand strategy](branding/brand-strategy.md) | [Brand fundamentals](branding/brand-fundamentals.md), [Brand governance](branding/brand-governance.md), [Logo systems](branding/logo-systems.md) |
| Write documentation for a design system | [Documentation](design-systems/documentation.md), [Component systems](design-systems/component-systems.md) | [Design tokens](design-systems/design-tokens.md), [Governance](design-systems/governance.md), [Accessibility testing](accessibility/accessibility-testing.md) |
| Set up a dark mode or theme system | [Colour in code](colour/colour-in-code.md), [Design tokens](design-systems/design-tokens.md) | [Colour theory](colour/colour-theory.md), [Accessible colour](accessibility/accessible-colour.md), [Visual consistency](design-systems/visual-consistency.md) |
| Evaluate a built website visually | [Website visual QA](evaluation/website-visual-qa.md), [Design quality framework](evaluation/design-quality-framework.md) | [Accessibility testing](accessibility/accessibility-testing.md), [Design system audit](evaluation/design-system-audit.md), [WCAG fundamentals](accessibility/wcag-fundamentals.md) |
| Implement a responsive frontend | [Responsive design](ui-ux/responsive-design.md), [Frontend implementation](ui-ux/frontend-implementation.md), [Responsive layouts](layout/responsive-layouts.md) | [Web typography](typography/web-typography.md), [Colour in code](colour/colour-in-code.md), [Accessibility testing](accessibility/accessibility-testing.md) |

## D. Task workflows (reading sequences)

Ordered sequences for the six major project types. Read in this order; the position of each file is deliberate — strategy before craft, criteria before production.

### D1. Developing a brand identity

1. [Brand fundamentals](branding/brand-fundamentals.md) — vocabulary: brand, identity, logo, image; what is actually being decided.
2. [Research and discovery](methodology/research-and-discovery.md) and [Brand discovery](branding/brand-discovery.md) — the research phase that informs every later choice.
3. [Brand strategy](branding/brand-strategy.md) — positioning, difference, reason to believe; the brief the design must answer.
4. [Brand personality](branding/brand-personality.md) — the trait set that type, colour and imagery must express.
5. [Visual identity](branding/visual-identity.md) — the component system that carries the personality.
6. Craft the components: [Palette development](colour/palette-development.md), [Typeface selection](typography/typeface-selection.md), [Graphic language](graphic-design/graphic-language.md), [Imagery](imagery/image-selection.md) as needed.
7. Record the system: [Brand guidelines](branding/brand-guidelines.md); plan its upkeep with [Brand governance](branding/brand-governance.md).
8. Evaluate before delivery: [Brand identity checklist](evaluation/brand-identity-checklist.md).

### D2. Extending an existing logo into a brand system

1. [Fixed-logo analysis](branding/fixed-logo-analysis.md) — the founding methodology: extract constraints and affordances from the mark you cannot change.
2. [Logo systems](branding/logo-systems.md) — variants, clear space, minimum sizes, file formats for the existing mark.
3. [Visual identity](branding/visual-identity.md) — the system the mark will anchor.
4. Derive the supporting components so they agree with the mark: [Palette development](colour/palette-development.md) (start from the logo's colours), [Typeface selection](typography/typeface-selection.md) and [Font pairing](typography/font-pairing.md), [Graphic language](graphic-design/graphic-language.md).
5. Apply to real surfaces: [Applications](applications/posters.md) directory — posters, social, event collateral — reading the file for each surface you must produce.
6. Write the rules down: [Brand guidelines](branding/brand-guidelines.md), so people outside the room can reproduce the system.
7. Evaluate: [Brand identity checklist](evaluation/brand-identity-checklist.md) — the pass criterion is a kit usable everywhere by people who were not in the room.

### D3. Creating a website

1. [UX fundamentals](ui-ux/ux-fundamentals.md) — goals, flows, friction; what the site must let people achieve.
2. [Information architecture](ui-ux/information-architecture.md) — content division, labelling, findability.
3. [Interaction design](ui-ux/interaction-design.md) — feedback, states, timing; how the interface behaves over time.
4. [UI fundamentals](ui-ux/ui-fundamentals.md) — component anatomy, hierarchy, forms.
5. Structure the visual layer: [Grid systems](layout/grid-systems.md), [Spacing and proportion](layout/spacing-and-proportion.md), [Typographic hierarchy](typography/typographic-hierarchy.md) — or, if a design system exists, its tokens and components instead: [Design tokens](design-systems/design-tokens.md), [Component systems](design-systems/component-systems.md).
6. Build correctly: [Responsive design](ui-ux/responsive-design.md), [Frontend implementation](ui-ux/frontend-implementation.md), [Web typography](typography/web-typography.md).
7. Accessibility throughout, not at the end: [WCAG fundamentals](accessibility/wcag-fundamentals.md).
8. Verify the built result: [Website visual QA](evaluation/website-visual-qa.md) and [Accessibility testing](accessibility/accessibility-testing.md).

### D4. Creating a poster

1. [Posters](applications/posters.md) — the defining constraint: one glance, one distance, no interaction.
2. [Principles of design](foundations/principles-of-design.md) and [Composition](foundations/composition.md) — the arrangement vocabulary.
3. [Typographic hierarchy](typography/typographic-hierarchy.md) — the reading order the passer-by will follow.
4. [Grid systems](layout/grid-systems.md) — the framework that holds the composition together.
5. Imagery if used: [Image selection](imagery/image-selection.md), [Image treatment](imagery/image-treatment.md).
6. Identity compliance: [Visual identity](branding/visual-identity.md) (the poster must belong to its brand family).
7. Evaluate: [Poster checklist](evaluation/poster-checklist.md) — including the print-production items, which are pass/fail, not aesthetic.

### D5. Developing a design system

1. [Design tokens](design-systems/design-tokens.md) — the smallest named decisions; the system's foundation layer.
2. [Component systems](design-systems/component-systems.md) — the reusable units built on the tokens.
3. [Visual consistency](design-systems/visual-consistency.md) — the property the whole system exists to produce.
4. [UI fundamentals](ui-ux/ui-fundamentals.md) and [Interaction design](ui-ux/interaction-design.md) — the states and behaviours components must cover.
5. [Documentation](design-systems/documentation.md) — the layer that turns assets into a system people can use.
6. [Governance](design-systems/governance.md) — contribution, versioning, adoption; how the system survives contact with teams.
7. Audit what you built: [Design system audit](evaluation/design-system-audit.md); keep the site layer honest with [Website visual QA](evaluation/website-visual-qa.md).

### D6. Evaluating an existing design

1. [Design quality framework](evaluation/design-quality-framework.md) — the master method; every checklist below applies it.
2. [Design critique (judgement)](foundations/design-critique.md) — how to look, and how to separate taste from reasoning.
3. The artefact's own checklist: [poster](evaluation/poster-checklist.md), [social](evaluation/social-media-checklist.md), [presentation](evaluation/presentation-checklist.md), [brand identity](evaluation/brand-identity-checklist.md), [website](evaluation/website-visual-qa.md), [design system](evaluation/design-system-audit.md) — use the matching one.
4. Domain criteria for what you see: [Gestalt and perception](foundations/gestalt-and-perception.md), [Principles of design](foundations/principles-of-design.md), [Accessible colour](accessibility/accessible-colour.md) as the artefact requires.
5. If a formal review is wanted: [Design critique (process)](methodology/design-critique.md) — the fixed review sequence that makes results comparable.
6. Turn findings into change: [Iteration](methodology/iteration.md) — one reason per round, termination on evidence.

## E. Knowledge dependencies

Concepts build on each other; reading order matters. The dependencies below are the load-bearing ones (mission §5D plus the additional edges the files themselves declare).

| Decision or concept | Depends on | Read first |
| --- | --- | --- |
| Typeface selection | Brand personality and communication objectives | [Brand personality](branding/brand-personality.md) → [Typeface selection](typography/typeface-selection.md) |
| Colour selection | Brand positioning, colour theory, accessibility | [Brand strategy](branding/brand-strategy.md), [Colour theory](colour/colour-theory.md), [Colour accessibility](colour/colour-accessibility.md) → [Palette development](colour/palette-development.md) |
| Layout decisions | Hierarchy, composition, grid systems | [Principles of design](foundations/principles-of-design.md), [Composition](foundations/composition.md), [Grid systems](layout/grid-systems.md) → [Responsive layouts](layout/responsive-layouts.md) |
| Component design | Interaction principles, design-system foundations | [Interaction design](ui-ux/interaction-design.md), [UI fundamentals](ui-ux/ui-fundamentals.md), [Design tokens](design-systems/design-tokens.md) → [Component systems](design-systems/component-systems.md) |
| Evaluation of any artefact | All theory domains | The relevant domain files → [Design quality framework](evaluation/design-quality-framework.md) |
| Moodboards | Discovery findings, personality, style literacy | [Research and discovery](methodology/research-and-discovery.md), [Brand personality](branding/brand-personality.md), [Visual styles](graphic-design/visual-styles.md) → [Moodboards](methodology/moodboards.md) |
| Imagery treatment | Identity rules and rights | [Visual identity](branding/visual-identity.md), [Image rights](imagery/image-rights.md) → [Image treatment](imagery/image-treatment.md) |
| Icon design | Graphic language and interface states | [Graphic language](graphic-design/graphic-language.md), [UI fundamentals](ui-ux/ui-fundamentals.md) → [Iconography](graphic-design/iconography.md) |
| Brand guidelines | The finished identity and its governance | [Visual identity](branding/visual-identity.md), [Logo systems](branding/logo-systems.md) → [Brand guidelines](branding/brand-guidelines.md) |
| Charts and diagrams | Perception, hierarchy, colour semantics | [Gestalt and perception](foundations/gestalt-and-perception.md), [Information hierarchy](information-design/information-hierarchy.md) → [Data visualisation](information-design/data-visualisation.md) |
| Accessibility conformance | WCAG criteria plus the domain's construction rules | [WCAG fundamentals](accessibility/wcag-fundamentals.md) with [Accessible colour](accessibility/accessible-colour.md) / [Accessible typography](accessibility/accessible-typography.md) |
| AI-assisted production | The craft file plus the process discipline | The relevant craft file (e.g. [AI image generation](imagery/ai-image-generation.md)) with [AI-assisted design](methodology/ai-assisted-design.md) |

The general pattern: **strategy files precede craft files; craft files precede application files; application files precede their checklists.** When in doubt, read upstream before downstream.

## F. Quick reference: foundational principles

Concise, decision-usable statements of the library's most important principles. Each is developed, with limits and counter-cases, in the file linked.

- **Hierarchy before decoration.** Decide the reading order — what is seen first, second, third — before choosing any visual treatment. Hierarchy is the one property every artefact needs. ([Typographic hierarchy](typography/typographic-hierarchy.md), [Information hierarchy](information-design/information-hierarchy.md))
- **Contrast is luminance, not hue.** WCAG 2.2 AA requires 4.5:1 for normal text and 3:1 for large text and UI components; vivid palettes pass if light/dark relationships are strong. ([Accessible colour](accessibility/accessible-colour.md), [WCAG fundamentals](accessibility/wcag-fundamentals.md))
- **One primary message per surface.** A poster is sampled in seconds, a slide glanced once; every artefact that competes for attention wins by reducing what it asks the viewer to take in. ([Posters](applications/posters.md), [Presentations](applications/presentations.md))
- **Spacing communicates relationships.** Proximity groups, similarity classifies: related items belong closer than unrelated ones, and equal spacing reads as equal importance. Set spacing deliberately, not as leftovers. ([Gestalt and perception](foundations/gestalt-and-perception.md), [Spacing and proportion](layout/spacing-and-proportion.md))
- **Grid before content.** Establish the column framework and align everything to it; alignment is the cheapest single improvement to any layout, and its absence is the most visible amateur marker. ([Grid systems](layout/grid-systems.md))
- **Use a closed spacing scale.** Draw every margin, padding and gap from one small set of values (a 4/8 px base is the conventional starting point); one-off distances are how systems decay. ([Spacing and proportion](layout/spacing-and-proportion.md), [Design tokens](design-systems/design-tokens.md))
- **Type mechanics set reading comfort.** Body measure of roughly 45–75 characters, leading around 1.4–1.6 of font size, left-aligned rag rather than forced justification — conventional starting points, correct more often than not. ([Typesetting](typography/typesetting.md), [Typography fundamentals](typography/typography-fundamentals.md))
- **Colour roles beat colour choices.** Assign each colour a job (primary, secondary, accent, neutral, semantic) and expand into ramps; test every palette for colour-vision deficiency before committing. ([Palette development](colour/palette-development.md), [Colour accessibility](colour/colour-accessibility.md))
- **Consistency means same rules, not identical screens.** Two surfaces are consistent when the same decisions produce the same outcomes there — the test is the rule applied, not the pixels matched. ([Visual consistency](design-systems/visual-consistency.md))
- **A logo never stands alone.** Clear space, minimum size, approved variants and misuse rules are what make a mark usable by people who were not in the room; they are part of the logo, not paperwork about it. ([Logo systems](branding/logo-systems.md), [Fixed-logo analysis](branding/fixed-logo-analysis.md))
- **Constraints are design material.** Platform canvas and safe zones, print bleed, viewing distance and duration shape the artefact before taste does — read the application file for the surface before designing for it. ([Applications](applications/posters.md) directory, [Social media graphics](applications/social-media.md))
- **Evaluate by criteria, not taste.** The review order is purpose, audience, then the sensory layers, then system properties, then defects; name what a judgement is based on or withhold it. ([Design quality framework](evaluation/design-quality-framework.md), [Design critique (judgement)](foundations/design-critique.md))
- **Iterate with a reason per round.** An iteration is a change driven by specific feedback and tested against an expectation; "tweaking until it looks right" is not iteration and does not terminate. ([Iteration](methodology/iteration.md))
- **Check provenance before repeating a specific.** Contrast ratios, platform sizes, version numbers and prices age and vary; the tag on the source tells you how much weight the figure can bear (section H). Volatile facts travel with a "verify current" marker, not as settled truth. ([Source accessibility](references/source-accessibility.md))

## G. Important constraints

- **Reference material, not project requirements.** This library supplies principles, methods and professional defaults. It is not a substitute for the actual brief, the organisation's own brand rules, the platform's current specifications, or the project's budget and timeline. Where the library and the project's real requirements disagree, the requirements win.
- **Not a substitute for human judgement.** The library makes design reasoning explicit so an agent can exercise judgement, not so it can avoid it. Checklists produce findings; the verdict and the trade-offs remain decisions, and taste-sensitive calls (which of three acceptable directions to pursue) should be surfaced as options with reasoning, not silently resolved.
- **Not current technical specification.** Platform image sizes, browser support, tool pricing, design-system versions and standards drafts all change. The library records figures with access dates and tags; before any external deliverable, re-verify volatile facts against the live source. Treat every numeric value as dated until checked.
- **Provenance honesty is non-negotiable.** Every source in this library carries a provenance tag (section H). Never invent a URL, quote, page number, statistic, date or edition; never attach a quote or figure to a `[canonical]` attribution; never reuse a URL you have not seen in your own tool output. Where a statement is synthesis, say so rather than borrowing an authority. The full rules: [Source accessibility](references/source-accessibility.md), section 9.
- **Established, conventional, recommended, preferred.** The library distinguishes four claim strengths — established design principles, professional conventions, context-dependent recommendations, and subjective preferences — and expects output to respect the distinction. Presenting a convention as a law is an error even when the convention is good.
- **Rights and licensing travel with assets.** Image licences, font licences and brand-manual permissions are attached to specific uses; consult [Image rights](imagery/image-rights.md) before any asset leaves a draft, and never treat another organisation's brand manual as general design law.
- **British spelling, English only.** The library is written in English with British spelling (colour, organisation, visualisation, behaviour); keep that convention in anything derived from it.

## H. Provenance tags

Every reference list in every file tags each source with exactly one of three tags. When you repeat a claim from this library, the tag tells you how much weight it can bear:

| Tag | Meaning | What you may claim from it |
| --- | --- | --- |
| `[accessed]` | The page or work was fetched and read (or key parts read) during this project, on the recorded access date. | Facts as the source states them, with the access date. Re-verify anything time-sensitive (prices, versions, capabilities). |
| `[search-verified]` | The source appeared in search results during this project (title and URL seen in tool output) but the page was not fetched. | The existence and apparent relevance of the source. Specific claims attributed to it remain unverified until fetched. |
| `[canonical]` | A well-established work attributed from general professional knowledge (author, title, thesis). No page numbers, no quotes, no figures. | Attribution-level claims only. Any quote, page number or statistic attached to this tag would be a fabrication by definition. |

A fourth marker, `verify`, appears inside body text (not as a reference tag) for plausible-but-unconfirmed facts — chiefly volatile ones such as tool pricing. A `verify` marker may be planned around but must not be asserted as fact in any deliverable. The definitions above are normative for the whole repository and are maintained, with access-level classifications and worked examples, in [Source accessibility](references/source-accessibility.md) (its section 2); the consolidated bibliography is [Bibliography](references/bibliography.md).

## I. Cross-cutting themes

Six threads run through every domain; recognising them is what turns sixty-odd separate files into one coherent practice.

- **Hierarchy first.** Every domain returns to visual hierarchy: foundations define it, typography and layout implement it, information design orders content with it, and every evaluation checklist tests for it before anything aesthetic.
- **Perception before prescription.** Rules in this library are downstream of how human vision works — Gestalt organisation, luminance contrast, reading mechanics. When a rule and its perceptual reason conflict with a project's context, the reason is what generalises.
- **System over artefact.** Single artefacts are applications of systems: identities are systems of components bound by rules; design systems are the same idea for interfaces. The recurring question is not "does this look good?" but "does the rule produce this outcome everywhere?"
- **Constraint-driven craft.** The application files treat the medium's constraints — distance and duration for posters, feed chrome for social, projection for slides, bleed for print — as the starting point of design, not an afterthought.
- **The evaluation loop.** Production files pair with evaluation files: propose → verify → apply → evaluate. Every checklist in `evaluation/` applies the master framework in [Design quality framework](evaluation/design-quality-framework.md), and the methodology files supply the process that makes evaluation repeatable.
- **Provenance discipline.** The library's credibility rests on honest tagging and the no-fabrication rules (sections G–H). This discipline is itself a design principle for agents: an unsupported claim in a design argument is the visual equivalent of a misaligned grid — the whole artefact loses trust.

## J. Repository map

Sixteen directories, ninety files (including this README). One-line descriptions; every link verified.

**Root**
- [README.md](README.md) — this routing manual: how to use, routing rules, task table, workflows, dependencies, quick reference, constraints, provenance tags, maintenance.

**[accessibility/](accessibility/wcag-fundamentals.md)** — the WCAG layer: what the standard requires and how to meet and test it.
- [WCAG fundamentals](accessibility/wcag-fundamentals.md) — the standard's structure (POUR principles, levels A/AA/AAA) translated into designer and developer decisions; the normative base for all accessibility numbers.
- [Accessible colour](accessibility/accessible-colour.md) — the rules-and-testing side of colour accessibility: exact contrast thresholds, measurement, dark-mode specifics.
- [Accessible typography](accessibility/accessible-typography.md) — resilient type: minimum sizes, user resizing, reflow, text-spacing overrides, line length and alignment.
- [Accessibility testing](accessibility/accessibility-testing.md) — the procedural playbook: automated scans, manual keyboard, screen-reader and visual stress-testing, wired into design review.

**[applications/](applications/posters.md)** — artefact-specific execution for the surfaces agents most often produce.
- [Posters](applications/posters.md) — single-sheet passers-by communication: one glance, one distance, print production included.
- [Social media graphics](applications/social-media.md) — feed, story, carousel and profile assets under platform constraints, produced as consistent sets.
- [Presentations](applications/presentations.md) — projected slide sequences: glance legibility, data slides, deck-level visual narrative.
- [Certificates and formal documents](applications/certificates-and-documents.md) — print documents whose job is to confer authority and record facts.
- [Event collateral](applications/event-collateral.md) — venue graphics: banners, wayfinding, badges, merchandise, sponsor boards.
- [Marketing assets](applications/marketing-assets.md) — conversion-oriented campaign graphics, judged on action taken, not only aesthetics.

**[branding/](branding/brand-fundamentals.md)** — the largest domain: strategy through governance, including the fixed-logo methodology.
- [Brand fundamentals](branding/brand-fundamentals.md) — the vocabulary underneath every branding decision: brand vs identity vs logo, message vs perception.
- [Brand discovery](branding/brand-discovery.md) — the structured research phase: organisation, audience, competitors, existing assets.
- [Brand strategy](branding/brand-strategy.md) — the deliberate choices that define the brand before anything is designed.
- [Brand personality](branding/brand-personality.md) — the human-trait construct (formalised by Jennifer Aaker) that type, colour and imagery must express.
- [Brand architecture](branding/brand-architecture.md) — how multiple brands relate: branded house, house of brands, endorsement, sub-brands.
- [Visual identity](branding/visual-identity.md) — the coordinated system of visible elements and the rules that bind them.
- [Logo systems](branding/logo-systems.md) — the complete logo asset set: variants, clear space, minimum sizes, file formats, misuse rules.
- [Fixed-logo analysis](branding/fixed-logo-analysis.md) — building a full identity around a logo that already exists and cannot change; the repository's founding use case.
- [Brand guidelines](branding/brand-guidelines.md) — writing the brand book so anyone, human or agent, can produce on-brand work.
- [Brand governance](branding/brand-governance.md) — keeping the identity consistent after launch: approvals, asset versioning, drift detection.

**[colour/](colour/colour-theory.md)** — colour from physics to code.
- [Colour theory](colour/colour-theory.md) — the physical and perceptual halves: models, harmonies, interaction of colours.
- [Colour psychology](colour/colour-psychology.md) — associations with meaning and emotion, reasoned per audience, culture and context rather than as folklore.
- [Palette development](colour/palette-development.md) — turning intent into a role-based palette: primary, secondary, accent, neutrals, semantic, ramps.
- [Colour accessibility](colour/colour-accessibility.md) — the construction side: palettes that survive colour-vision deficiency and degraded viewing conditions.
- [Colour in code](colour/colour-in-code.md) — notations (HEX, RGB, HSL, OKLCH), gamuts, screen-to-print conversion, colour tokens.

**[design-systems/](design-systems/design-tokens.md)** — the interface-system layer, from tokens to governance.
- [Design tokens](design-systems/design-tokens.md) — the smallest named design decisions, stored platform-neutrally; the system's foundation.
- [Component systems](design-systems/component-systems.md) — the organised library of reusable interface pieces and the rules for building and combining them.
- [Documentation](design-systems/documentation.md) — the explanatory layer: what each asset is, when to use it, when not, and how.
- [Governance](design-systems/governance.md) — contribution, review, versioning, adoption measurement, deprecation.
- [Visual consistency](design-systems/visual-consistency.md) — same rules everywhere: the property the system exists to produce, and how drift starts.

**[evaluation/](evaluation/design-quality-framework.md)** — reusable evaluation: one master framework plus artefact checklists.
- [Design quality framework](evaluation/design-quality-framework.md) — the master evaluation methodology every checklist applies.
- [Brand identity checklist](evaluation/brand-identity-checklist.md) — item-by-item brand-kit evaluation: what to check, how, and pass criteria.
- [Website visual QA](evaluation/website-visual-qa.md) — the visual pass over a built site: spacing, tokens, states, responsive behaviour, defects.
- [Design system audit](evaluation/design-system-audit.md) — scored audit of token coverage, component APIs, documentation, accessibility and drift.
- [Poster checklist](evaluation/poster-checklist.md) — hierarchy at distance, contrast, print production, identity compliance.
- [Social media checklist](evaluation/social-media-checklist.md) — platform dimensions and safe zones, feed-size readability, template consistency.
- [Presentation checklist](evaluation/presentation-checklist.md) — projection legibility, data slides, deck-level sequence.

**[foundations/](foundations/principles-of-design.md)** — the perception and composition layer everything else builds on.
- [Elements of design](foundations/elements-of-design.md) — the raw components: line, shape, form, colour, value, texture, space, type, and their behaviour.
- [Principles of design](foundations/principles-of-design.md) — the rules of arrangement applied to those elements: balance, contrast, emphasis, rhythm, unity and their limits.
- [Composition](foundations/composition.md) — arranging elements on a canvas so the whole reads as intended: focal points, visual weight, movement.
- [Gestalt and perception](foundations/gestalt-and-perception.md) — how the visual system organises marks: proximity, similarity, closure, continuity, figure–ground.
- [Design critique (judgement)](foundations/design-critique.md) — the discipline of looking: producing reasoned, criteria-based judgements and separating taste from analysis.

**[graphic-design/](graphic-design/graphic-language.md)** — the identity's visual vocabulary beyond logo, colour and type.
- [Graphic language](graphic-design/graphic-language.md) — the system of motifs, shapes, borders, patterns and effects used beside and beyond the logo.
- [Iconography](graphic-design/iconography.md) — icon families sharing one construction logic: grid, stroke, corners, optical sizing.
- [Patterns and textures](graphic-design/patterns-and-textures.md) — repeated elements filling surfaces and surface qualities changing how colour reads.
- [Illustration](graphic-design/illustration.md) — drawn or rendered imagery produced to the brand's own rules, and when to choose it over photography.
- [Art direction](graphic-design/art-direction.md) — making and defending the visual decisions that keep a brand's output coherent across surfaces.
- [Visual styles](graphic-design/visual-styles.md) — coherent aesthetic families (Swiss, Bauhaus, editorial, brutalism) as raw material for direction, not costumes.

**[history/](history/graphic-design-history.md)** — context that explains why current practice looks as it does.
- [Graphic design history](history/graphic-design-history.md) — the major eras in order, each with what it contributed to present practice.
- [Design philosophies](history/design-philosophies.md) — convictions about what design is for, centring on Rams' ten principles and their critics.
- [Influential designers](history/influential-designers.md) — thirteen profiles whose working methods remain directly usable (Müller-Brockmann, Rand, Bass, Vignelli, Rams and others).

**[imagery/](imagery/photography.md)** — the image layer: choosing, treating, licensing and generating.
- [Photography](imagery/photography.md) — photography as an identity component: what every brand photo claims about the brand.
- [Image selection](imagery/image-selection.md) — which visual belongs in a slot, and whether to commission, buy, draw, generate or go without.
- [Image treatment](imagery/image-treatment.md) — grading, overlays, cropping and masking that turn heterogeneous photos into one consistent family.
- [Image rights](imagery/image-rights.md) — ownership, licences, releases and the documentation that proves permission.
- [AI image generation](imagery/ai-image-generation.md) — diffusion-model production: prompting, consistency, evaluation and its limits as a brand tool.

**[information-design/](information-design/information-hierarchy.md)** — making complexity readable.
- [Information hierarchy](information-design/information-hierarchy.md) — ordering content so attention meets it in the order of importance and logic.
- [Data visualisation](information-design/data-visualisation.md) — charts built so patterns are perceived before numbers are read; chart-type selection and encodings.
- [Diagrams and infographics](information-design/diagrams-and-infographics.md) — schematic (flows, structures, processes) and narrative branches of information design.

**[layout/](layout/grid-systems.md)** — the structural layer of any canvas.
- [Grid systems](layout/grid-systems.md) — column and row frameworks (the Müller-Brockmann tradition) that align all content.
- [Spacing and proportion](layout/spacing-and-proportion.md) — closed spacing scales, modular proportion, spacing tokens.
- [Responsive layouts](layout/responsive-layouts.md) — fluidity, reflow and breakpoints at the layout level.

**[methodology/](methodology/design-thinking.md)** — the process layer: how design work is actually run.
- [Research and discovery](methodology/research-and-discovery.md) — turning an ambiguous brief into an informed one; the test is whether a finding changes a decision.
- [Design thinking](methodology/design-thinking.md) — the stage models (d.school, Double Diamond) as teaching devices for modes of thinking, not rituals.
- [Ideation](methodology/ideation.md) — generating many candidates before judging any, and selecting by criteria rather than taste.
- [Moodboards](methodology/moodboards.md) — making a visual direction concrete and discussable before production begins.
- [Iteration](methodology/iteration.md) — deliberate, recorded rounds of change, each with a reason, terminating on evidence.
- [Design critique (process)](methodology/design-critique.md) — the repeatable eleven-step review procedure; the operational counterpart of the foundations file.
- [AI-assisted design](methodology/ai-assisted-design.md) — where AI genuinely helps in the workflow, and the propose → verify → apply → evaluate loop that keeps it safe.

**[references/](references/bibliography.md)** — the source layer: bibliography, case studies, tools, provenance.
- [Bibliography](references/bibliography.md) — the consolidated, deduplicated bibliography with an inventory snapshot and coverage map.
- [Books and textbooks](references/books-and-textbooks.md) — one full entry per core book from the mission's research list, with verification status and access routes.
- [Academic curricula](references/academic-curricula.md) — what real design-education programmes teach and in which sequence.
- [Professional guidelines](references/professional-guidelines.md) — analyses of publicly accessible brand and design guidelines from seven organisations.
- [Case studies](references/case-studies.md) — real identities and design systems analysed through ten standard questions, with cross-cutting lessons.
- [Tools and software](references/tools-and-software.md) — the design-tool ecosystem with a strict verify-current-pricing discipline.
- [Source accessibility](references/source-accessibility.md) — the provenance index: access levels, what each allows you to claim, fetch failures recorded, re-verification procedures.

**[typography/](typography/typography-fundamentals.md)** — the full typographic craft, from anatomy to browser delivery.
- [Typography fundamentals](typography/typography-fundamentals.md) — anatomy, classification, and the mechanics of legibility and readability.
- [Typeface selection](typography/typeface-selection.md) — the decision process from requirement to a defensible, verifiable family choice.
- [Font pairing](typography/font-pairing.md) — combining display, text and functional voices into a working system.
- [Typographic hierarchy](typography/typographic-hierarchy.md) — role-based treatments and scales that communicate order before a sentence is read.
- [Typesetting](typography/typesetting.md) — continuous-text craft: measure, leading, alignment, paragraph handling.
- [Editorial design](typography/editorial-design.md) — organising type across multipage artefacts: books, reports, programmes.
- [Web typography](typography/web-typography.md) — browser delivery: responsive sizing, font loading, CSS control, accessibility obligations.

**[ui-ux/](ui-ux/ux-fundamentals.md)** — the interface layer: experience, components, behaviour, implementation.
- [UX fundamentals](ui-ux/ux-fundamentals.md) — shaping interaction so goals are met efficiently and without avoidable frustration; core heuristics.
- [UI fundamentals](ui-ux/ui-fundamentals.md) — component anatomy, states, hierarchy and forms.
- [Interaction design](ui-ux/interaction-design.md) — system behaviour over time: feedback, timing, motion, progressive disclosure.
- [Information architecture](ui-ux/information-architecture.md) — content division, grouping, labelling and findability.
- [Responsive design](ui-ux/responsive-design.md) — one interface serving every viewport and input method, including the mobile-specific hazards.
- [Frontend implementation](ui-ux/frontend-implementation.md) — translating design decisions into correct, maintainable CSS and structure.

## K. Maintenance notes

- **Adding or changing a file.** Follow the standard template (what/why/principles/how/application/decision framework/examples/mistakes/checklist/related/references), end every substantive file with a tagged References section, cross-link with repository-relative paths, and update this README's routing table and repository map plus [PROJECT_STATUS.md](PROJECT_STATUS.md) in the same change. A file that enters the library unlinked from the router will not be found by agents — the router is the contract.
- **Commit-per-file convention.** Each file is committed individually, one commit per file, with a message naming the domain and file slug (for example `docs(colour): palette-development — role-based palette construction and testing`); README and PROJECT_STATUS each get their own commit. Never batch unrelated files into one commit, so history stays reviewable domain by domain and a bad file can be reverted alone. (Authoring agents in this project did not run git themselves, per the brief; the convention governs whoever integrates the work.)
- **Re-verification policy.** Volatile facts (tool pricing, platform sizes, version numbers) are re-verified before use in any external deliverable, on a needs basis rather than a schedule; stable sources (standards, books) are re-verified only when quoting. The procedure, including retry-on-timeout and the tag-change rules, is in [Source accessibility](references/source-accessibility.md), section 9. Update the citing file's access date when you re-verify — not just the index.
- **Link hygiene.** Every link in this README resolves as of 2026-11-24 (checked programmatically; see PROJECT_STATUS.md). When adding links, test them before writing; when moving or renaming a file, update every referencing file, not only the router.
- **Keeping the router honest.** The routing table is the most consequential part of this README: when a new file changes the right route for an existing task, update the row rather than leaving the route stale. Extending routes is covered in section B.
- **Reporting defects.** If a file's guidance conflicts with its live source or with a standard, fix the citing file and refresh its access date — never edit the provenance index alone (the index records status; the citing files carry the claims). Confirmed corrections to a domain file should be committed as that file's own commit (section above).
- **Provenance of this build.** All ninety files were written by domain agents working from a shared brief (repository authoring rules at `/home/z/my-project/scripts/kb/BRIEF.md`, outside this repository); access dates in reference sections are 2026-11-23 (domain research) and 2026-11-24 (references-phase fetches and re-verification). Completion evidence, thin spots and validation status: [PROJECT_STATUS.md](PROJECT_STATUS.md).
