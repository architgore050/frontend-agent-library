# Inspiration Patterns

## 1. What is it?

The reusable design patterns extracted across the [website reference collection](websites/README.md) — the distilled "moves" an agent can deliberately apply, each traced to its source references and the craft files that govern its implementation. Patterns are translation aids, not templates: the anti-copying rules ([contributing.md](contributing.md) §6) apply — a pattern names the *why* and the shape; the pixels remain yours.

## 2. How to use it

Find the pattern by what you are building ([use-case-index.md](use-case-index.md) routes project → entries → patterns). Each pattern names: what it is, why it works, the references that do it, and the governing craft file. Implementation always defers to the craft file — the pattern is the shortcut to the *decision*, not to the code.

## 3. The patterns

### Hero sections

- **The one-screen promise** — promise + product surface + one accent moment on the first screen; nothing else. *References:* [Stripe](websites/references/stripe.md), [Linear](websites/references/linear.md), [Family](websites/references/family.md). *Governs:* [../../skills/frontend-design/SKILL.md](../skills/frontend-design/SKILL.md) hero rules; taste-skill "one section per screen".
- **The big-type confidence hero** — oversized display type, one artifact, brief copy. *References:* [Vercel](websites/references/vercel.md). *Governs:* [../../typography/typographic-hierarchy.md](../typography/typographic-hierarchy.md).
- **The editorial hero** — serif-accent headline over composed imagery; authority first. *References:* [Ramp](websites/references/ramp.md). *Governs:* [../../typography/font-pairing.md](../typography/font-pairing.md).
- **The kinetic hero** — display type that animates its meaning, once. *References:* [Superlist](websites/references/superlist.md), [Apple](websites/references/apple.md). *Governs:* [../../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md).

### Colour and atmosphere

- **Monochrome + one signature** — near-total monochrome, one reserved brand moment. *References:* [Stripe](websites/references/stripe.md) (gradient), [Vercel](websites/references/vercel.md) (inversions). *Governs:* [../../colour/palette-development.md](../colour/palette-development.md).
- **Hue zones** — maximal palette organised by section ownership. *References:* [Superlist](websites/references/superlist.md), [Figma](websites/references/figma.md). *Governs:* [../../colour/palette-development.md](../colour/palette-development.md) accent systems.
- **Atmosphere gradients** — soft multi-hue blends as ground, content on calm surfaces. *References:* [Family](websites/references/family.md). *Governs:* [../../visual-styles/interface-styles.md](../visual-styles/interface-styles.md) §4.1; contrast checks mandatory.
- **Dark-theme as system** — elevation/contrast logic native to dark, not inverted light. *References:* [Linear](websites/references/linear.md), [Vercel](websites/references/vercel.md). *Governs:* [../../colour/colour-in-code.md](../colour/colour-in-code.md).

### Sections and surfaces

- **Product at real size** — the interface itself is the imagery, working, un-cropped. *References:* [Linear](websites/references/linear.md), [Notion](websites/references/notion.md), [Stripe](websites/references/stripe.md). *Governs:* taste-skill §2 (the client's subject leads).
- **Feature reveals, one idea per section** — short sections, single promise each. *References:* [Linear](websites/references/linear.md), [Apple](websites/references/apple.md). *Governs:* [../../information-design/information-hierarchy.md](../information-design/information-hierarchy.md).
- **Bento summaries** — mixed-tile compositions for feature overviews. *References:* the bento style ([../../visual-styles/interface-styles.md](../visual-styles/interface-styles.md) §4.7). *Governs:* same.
- **Data trust surfaces** — real numbers with real chart craft as marketing. *References:* [Ramp](websites/references/ramp.md), [Stripe](websites/references/stripe.md). *Governs:* [../../information-design/data-visualisation.md](../information-design/data-visualisation.md).
- **Use-case grids** — galleries that let every visitor find themselves. *References:* [Notion](websites/references/notion.md). *Governs:* [../../ui-ux/information-architecture.md](../ui-ux/information-architecture.md).
- **Template/marketplace galleries** — filterable, previewed, honest thumbnails. *References:* [Vercel](websites/references/vercel.md), [Notion](websites/references/notion.md). *Governs:* [../../ui-ux/ui-fundamentals.md](../ui-ux/ui-fundamentals.md).

### Motion

- **One dealt moment per page** — a countable signature moment; the rest is quiet feedback. *References:* every entry; the taste-skill codifies it. *Governs:* [../../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md) §hierarchy.
- **Origin-aware transitions** — elements animate from where they came (modal from trigger, card to page). *References:* [Linear](websites/references/linear.md), [Lusion](websites/references/lusion.md). *Governs:* [../../motion-and-interaction/animation-libraries.md](../motion-and-interaction/animation-libraries.md) (Motion's shared layout).
- **Scrubbed storytelling** — scroll position as the timeline; skippable, reversible, reduced-motion-safe. *References:* [Apple](websites/references/apple.md), [Igloo](websites/references/igloo.md). *Governs:* [../../motion-and-interaction/scroll-experiences.md](../motion-and-interaction/scroll-experiences.md) §5.3.
- **Loading as a designed moment** — styled, informative, honest loading states. *References:* [Lusion](websites/references/lusion.md), [Igloo](websites/references/igloo.md). *Governs:* [../../ui-ux/interaction-design.md](../ui-ux/interaction-design.md) §5.
- **Micro-delight budget** — small personality moments where trust already exists. *References:* [Arc](websites/references/arc.md), [Family](websites/references/family.md). *Governs:* [../../motion-and-interaction/microinteractions.md](../motion-and-interaction/microinteractions.md).

### Voice and trust

- **Copy as brand craft** — one voice everywhere, including errors and legal-adjacent pages. *References:* [Arc](websites/references/arc.md), [Notion](websites/references/notion.md). *Governs:* taste-skill copy layer (`copy-voice.md`).
- **Pricing transparency** — tabular, comparison-friendly, honest ([../../ux-psychology/design-laws.md](../ux-psychology/design-laws.md) defaults honesty). *References:* [Stripe](websites/references/stripe.md), [Linear](websites/references/linear.md). *Governs:* [../../frontend-engineering/forms-and-data-display.md](../frontend-engineering/forms-and-data-display.md).
- **Changelog as proof** — product velocity as the social proof. *References:* [Linear](websites/references/linear.md). *Governs:* content strategy judgment.
- **The quiet frame** — one neutral zone (usually nav) that lets a loud system read. *References:* [Superlist](websites/references/superlist.md). *Governs:* [../../visual-styles/interface-styles.md](../visual-styles/interface-styles.md) §4.6.

### Architecture

- **Immersive face + practical index** — the cinematic front with a conventional, usable surface behind it. *References:* [Lusion](websites/references/lusion.md), [Igloo](websites/references/igloo.md). *Governs:* [../../motion-and-interaction/scroll-experiences.md](../motion-and-interaction/scroll-experiences.md) §5.4.
- **Two-layer navigation** — minimal global nav + strong local nav on deep surfaces. *References:* [Apple](websites/references/apple.md). *Governs:* [../../ui-ux/information-architecture.md](../ui-ux/information-architecture.md).

## 4. Common mistakes

- **Pattern as template** — copying the pixels instead of the decision; the anti-copying rules apply to patterns as to sites.
- **Pattern without its governing file** — the craft files carry the implementation rules; a pattern applied without them reproduces the failure modes they prevent.
- **Stacking conflicting patterns** — one hero pattern per page; two colour systems per identity; the references each commit to one position.

## 5. Extending

Patterns are extracted from entries during contribution ([contributing.md](contributing.md) §7): if a new entry demonstrates a move worth naming, add it here with its reference trace in the same commit.
