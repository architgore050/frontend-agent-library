# Illustration

## 1. What is it?

Illustration, in a brand context, is drawn or rendered imagery — characters, scenes, spot graphics, diagrammatic pictures — produced to the brand's own visual rules and used where photography cannot or should not go. It is an identity component in the same register as type and colour: a consistent illustration style becomes as recognisable as a logotype, and a set of illustrations that obey the brand's graphic language (see [Graphic language](graphic-language.md)) can explain, charm and humanise in ways camera imagery cannot.

The scope of this file is illustration as part of a brand system: defining the style, deciding when to use it, organising how it is produced (commissioned, sourced, or generated with AI assistance), and assembling individual images into a system. For a working example of the system logic, Atlassian's design system organises product illustration into named roles — spot illustrations, low-fidelity UI diagrams, ambient patterns — and restricts collage-style work to marketing [accessed]; that role-based structure is the pattern this file generalises.

## 2. Why does it matter?

**Illustration goes where photography cannot.** A photograph shows what exists; an illustration shows what a service *means*. Empty states, error messages, abstract benefits ("your data, everywhere"), future features, sensitive topics and hypothetical scenarios have no photograph to take — or their real photograph would be awkward, generic or dispiriting. This is why product UX relies on illustration so heavily: it can show an empty inbox with warmth and a hint of personality without faking a screenshot of someone else's data.

**A consistent style is a recognition asset.** Human-drawn qualities — line weight, colour handling, level of abstraction, character design — are as distinctive as any logo element. When every illustration follows the same rules, the audience begins to recognise the brand's imagery without the logo attached, exactly as with the graphic language tests in [Graphic language](graphic-language.md). Conversely, illustrations sourced ad hoc from different stock libraries in different styles are the fastest way to make a brand look assembled rather than designed.

**It carries emotion with control.** Illustration sets its own reality: proportions, colour, weather, energy and mood are all decisions rather than constraints. That control makes it the safest tool for emotional moments in a product — celebration, empathy, encouragement — because the emotional register is chosen, not captured. The same control makes it dangerous when unmanaged: mismatched emotional registers across illustrations read as mood disorder in the brand.

## 3. Core principles

### 3.1 Purpose first

Every illustration needs a stated job: explain a concept, mark a state (empty, error, success), set tone for a moment, or decorate a defined surface. An illustration without a job is a cost and a distraction. Atlassian's guidance is explicit that teams should decide first whether an illustration is necessary, that visuals must support the user's goal rather than decorate, and that excessive illustration increases cognitive load [accessed]. The same test applies to print and campaign work: if removing the illustration loses nothing but colour, it probably should be removed.

### 3.2 One style, defined by rules not by samples

An illustration *style* is a set of learnable, enforceable rules: line weight and consistency, level of abstraction, colour behaviour (palette share, shading method), proportions and character construction, background treatment, and level of detail. Write these rules down as a one-page style definition; samples alone (a folder of approved images) cannot be extended by new artists or new tools without drift. The style definition is a sub-ruleset of the brand's vocabulary ruleset and inherits its geometry — the illustration's corners, curves and shapes should agree with the brand's motif geometry (see [Graphic language](graphic-language.md), section 4.3).

The abstraction ladder deserves explicit handling because it is the most common drift axis. Picture a five-rung ladder from literal to abstract: photograph-like rendering, stylised realism, simplified-cartoon, iconic-flat, geometric-abstract. Styles fail not by sitting on a rung but by sliding between rungs image by image — a cartoon face here, an iconic silhouette there. Fixing the rung in writing (as the style definition does) turns a taste dispute into a checkable rule, and it also decides the medium question: flat and iconic work vectorises cleanly and scales everywhere, while realistic rendering commits the brand to heavier assets and more skilled hands.

### 3.3 Consistency across the set, hierarchy across the system

Individual images must look like siblings — same hand, same logic — while the *system* organises them into roles with different visual weight: a hero illustration may be detailed and colourful, spots stay small and simple, ambient patterns stay quiet. This mirrors the hero/support/accent tier logic of [Graphic language](graphic-language.md). The consistency rules are non-negotiable at every tier (one brand always looks like one brand); the detail level and colour richness are the sanctioned variables between tiers.

### 3.4 Illustration obeys the brand's constraints

Illustrations inherit the same obligations as every other element: colour from the palette (see [Palette development](../colour/palette-development.md)), contrast for any image that carries meaning (see [Colour accessibility](../colour/colour-accessibility.md)), inclusive representation in depicted people, and no un-sanctioned effects. Where illustrations appear near text or carry information, the accessibility rules in [WCAG fundamentals](../accessibility/wcag-fundamentals.md) apply to them as graphical objects.

## 4. How it works

### 4.1 Defining the style: the eight decisions

A style definition answers, in writing:

1. **Line behaviour.** Is there an outline? What weight, in relation to the brand's line family? Uniform or expressive? Are lines closed and clean, or loose and textured?
2. **Abstraction level.** How simplified is reality? (Iconic-flat, stylised-realistic, semi-abstract, abstract-geometric — a ladder; pick a rung and stay on it.)
3. **Colour method.** Flat fills, limited shading, or full rendering? How many colours per image? What share of the brand palette appears, and how are neutrals handled?
4. **Shape language.** Rounded or sharp corners, organic or geometric construction — agreed with the brand's container shapes and motifs.
5. **Proportions and character construction.** If characters exist: head-to-body ratio, feature style, movement rules; drawn once as a construction sheet.
6. **Detail ceiling.** Maximum complexity per tier (hero can be detailed; spots cannot).
7. **Background treatment.** Transparent, a defined scene box, or an integrated environment; and how illustrations meet brand patterns and gradients.
8. **Light and shadow logic.** One light direction? Cast shadows or none? Highlight behaviour?

Two or three pages covering these decisions, plus four to six reference images per tier, is a complete starter style guide. In compressed form, a style definition reads like this excerpt:

```markdown
## Illustration style definition — [brand]
Line: 2px uniform outline, rounded caps, colour = ink token; no interior hatching.
Abstraction: stylised-realistic (rung 3 of 5); bodies simplified, faces minimal.
Colour: max 4 fills per image, all from palette; shading = one flat tint per shape.
Shape: corner radius 8px on containers; organic curves forbidden (brand is geometric).
Characters: 1:3 head-to-body; construction sheet v2 is canonical.
Detail ceiling: hero = full; scene = medium; spot = 3 shapes max.
Backgrounds: transparent by default; scene box 4:3 when environment needed.
Light: single top-left source; cast shadows as flat 20% ink shapes only.
```

The excerpt is deliberately enforceable: every line can be checked on a new image in seconds, which is what makes the style survive a second artist, a stock purchase, or an AI generation session.

### 4.2 When illustration beats photography

| Situation | Choose | Reason |
| --- | --- | --- |
| Abstract concepts, benefits, "how it works" | Illustration | No honest photograph exists; diagrams clarify |
| Empty, error and success states | Illustration (spots) | Controlled emotion; no fake screenshots [accessed] |
| Sensitive or hypothetical scenarios | Illustration | Removes likeness and staging problems |
| Character-driven storytelling | Illustration | Characters are ownable and repeatable |
| Proof, trust, real people, real places | Photography | Authenticity demands the camera (see [Photography](../imagery/photography.md)) |
| Product, food, venue, people features | Photography | Viewers expect literal truth |
| Cultural or campaign moments needing gravitas | Photography, or illustration informed by a strong style | Depends on the brand's voice |

The two media can coexist in one system — many brands pair illustrative explanation with photographic proof — provided each has a defined lane and the treatments (crops, palettes, framing) harmonise through the graphic language.

### 4.3 The illustration system: roles

Structure the set into named roles, each with its own spec:

- **Hero.** Large, detailed, emotional; key visuals, campaign covers, feature launches. One or two exist per campaign; they may break density rules but not style rules.
- **Spot.** Small, single-concept images for empty states, errors, wins and section markers; colourful for emphasis, neutral for routine moments [accessed]. Constraint-heavy: must read at 80–120px.
- **Scene.** Medium compositions for onboarding, feature tours and explanations; often diagrammatic. If depicting interfaces, use stylised UI — never real screenshots, which create a confusing screen-within-a-screen effect [accessed].
- **Character.** Mascots and recurring figures; require the heaviest construction documentation (turnarounds, expressions, poses, do-not list) because they are the most visible and most often drawn by different hands.
- **Ambient / pattern.** Background texture-level illustration that sets mood without depicting anything specific [accessed]; implemented like brand patterns (see [Patterns and textures](patterns-and-textures.md)).

Each role gets its spec in the same format as the ruleset: sizes, density, colour richness, allowed contexts. Collage and high-noise styles are, following Atlassian's example, reserved for marketing surfaces where busyness is acceptable [accessed].

## 5. Practical application

### 5.1 Commissioning

Commission when the style must be owned and extended for years. The brief carries: purpose and audience, the style definition (section 4.1), technical specs (section 5.4), the roles list with example sizes, the palette and geometry constraints, and the usage licence (scope, exclusivity, years, media). Ask candidates for consistency proof — three drawings of *different subjects in the same rules* — rather than portfolio pieces alone, since range is easy and consistency is the skill. Contract for source files and an agreed method for future additions (the same artist, or a documented handover pack that any competent illustrator can follow).

A commissioning checklist that prevents most disputes:

- [ ] Style definition and reference images attached, not described in prose alone.
- [ ] Deliverable list with exact sizes, roles and file formats (SVG sources included).
- [ ] Palette tokens and motif geometry supplied; corner and line rules stated.
- [ ] Inclusive-representation expectations stated for depicted people.
- [ ] Revision rounds and what counts as a style change vs a subject change agreed.
- [ ] Licence scope, credit norms and source-file ownership in the contract.
- [ ] Review procedure named: who checks against the style definition, at which milestones.

### 5.2 Sourcing

Stock and marketplace illustration is viable when volume is high and budget low, but it must be filtered hard: search by style keywords, pick *one* library collection (a coherent set by one artist or studio), verify the licence covers your media (web, print, merchandise), and expect to recolour and simplify to the brand rules. Never mix collections from visibly different hands. The result should be re-styled enough to become the brand's own: palette substitution, background removal, consistent corner behaviour. If more than about half of each image must be reworked, commissioning was the cheaper path.

### 5.3 AI-generated illustration

AI tools can draft, explore and iterate quickly, and can fill volume needs once a style is defined. The working pattern that preserves consistency: define the style first (section 4.1), use approved brand illustrations as reference inputs where rights allow, generate candidates against the written rules, then clean up and vectorise so the result meets the technical spec. Treat every output as a draft needing human art direction — checking proportion logic, palette compliance, anatomy, and the absence of artefacts — before it enters the system. Rights and ethical considerations (training-data provenance, licence terms of the tool, disclosure norms) must be checked for the tool and jurisdiction in use; a full treatment of prompt craft, rights and workflow lives in [AI image generation](../imagery/ai-image-generation.md), which owns that topic.

### 5.4 Technical specifications

- **Formats.** SVG for flat and vector-style work (crisp at any size, restyleable, small); PNG at 2× for raster or heavily textured pieces; WebP/AVIF for photographic-grade rendering on the web. Animations: Lottie (JSON) for vector motion, or short optimised video.
- **Canvas and export.** Draw on a consistent artboard grid; export with the same padding rules as the icon system (see [Iconography](iconography.md)); name files by role and subject (`spot-empty-inbox.svg`, not `final2.svg`).
- **Recolouring.** Keep palette colours as named variables or swatches in the source so dark-mode and campaign variants are mechanical, not redrawn; see [Colour in code](../colour/colour-in-code.md) for CSS-side handling.
- **Dark mode.** Plan it at definition time: either a dark variant per role or a colour logic (outlines and fills from palette tokens) that survives both modes; test contrast of meaningful elements in both (see [Colour accessibility](../colour/colour-accessibility.md)).
- **Weight.** Budget SVG size (conventional ceiling: tens of kilobytes per spot image, low hundreds for heroes) and total per-page illustration weight; simplify paths before export.

A minimal SVG discipline example — named palette variables, documented viewBox, consistent padding:

```html
<!-- spot-empty-inbox.svg — role: spot; viewBox 0 0 120 96; safe margin 8 -->
<svg viewBox="0 0 120 96" role="img" aria-labelledby="t d">
  <title id="t">Empty inbox</title>
  <desc id="d">A tray with a single letter, drawn in the brand line style.</desc>
  <g fill="none" stroke="var(--ink)" stroke-width="2" stroke-linecap="round">
    <!-- geometry only; colours resolve from palette tokens -->
  </g>
</svg>
```

Accessible naming (`role="img"` with title and description where the image carries meaning, or `aria-hidden="true"` where it is decorative) belongs to the icon and image accessibility rules — see [WCAG fundamentals](../accessibility/wcag-fundamentals.md).

## 6. Decision framework

**Illustrate or photograph?** Start from the table in 4.2; if the content is literal and trust-sensitive, photograph; if it is conceptual, emotional or state-based, illustrate; if both needs coexist, define lanes. When neither is affordable, typography and pattern carry the surface alone — that is a legitimate, often elegant outcome.

**Commission, source, or generate?**

| Situation | Path | Why |
| --- | --- | --- |
| Long-lived identity, characters, high visibility | Commission | Ownership, consistency, extension rights |
| One-off campaign, tiny budget | Source + re-style | Speed and cost; coherence via filtering |
| Style defined, volume needed, drafting/exploration | AI-assisted generation with human direction | Volume economics; control via rules and review |
| Highly technical or safety-critical diagrams | Commission (or diagram tooling) | Accuracy accountability |

**How much illustration overall?** Scale to the brand's voice: a playful consumer brand may run illustration on most surfaces; a serious institution may restrict it to explanation moments. Cap density per page — one hero or a few spots, never both competing — following the cognitive-load guidance [accessed].

## 7. Examples

**Role-based product system [accessed].** Atlassian's public guidance defines spot illustrations, low-fidelity UI illustrations and ambient patterns as the product roles, restricts collage to marketing, forbids real screenshots inside explanatory illustrations, and frames the whole system with "illustration should work with the message, not replace it". This is the reference pattern for role-driven illustration systems, and its role names are widely reused across the industry [search-verified for the wider pattern; accessed for the source page].

**Character system (illustrative composite).** A delivery-service brand commissions a courier character with a documented construction sheet (three-view turnaround, eight expressions, ten poses, palette tokens, prohibited uses). Every artist and every AI generation session works from the sheet, so the character stays one character across app states, print and merchandise — consistency by documentation, not by luck.

**Style-adapted sourcing (illustrative composite).** An event brand with no illustration budget sources a single-artist spot set from a stock library, substitutes the event palette, removes the library's backgrounds, and applies its own corner geometry to the crops. The images pass the brand's language audit because treatment rules did the work that bespoke art would otherwise have done.

**The state-map discipline (illustrative composite).** A product team maps every user state to an illustration register before drawing anything: empty states get neutral spots, errors get calm and apologetic spots, milestones get colourful celebration spots, onboarding gets scene diagrams. Because the map exists, six months of feature work produces a coherent set — new engineers order illustrations against the map instead of re-deciding the tone each time. The map is to illustration what the ruleset is to the graphic language.

## 8. Common mistakes

- **Style drift by accumulation.** Images commissioned or sourced over years in different hands and styles until the set looks like a group exhibition. Correction: write the style definition, audit the set, retire or re-style outliers, and require new work to pass the rules.
- **Emotion mismatch.** A cheerful spot on a fatal-error page; a sombre hero on a celebration. Correction: map emotional register per role and per state; check the map during review.
- **Real screenshots as illustration.** Creates the screen-within-a-screen confusion Atlassian warns about [accessed]. Correction: stylised UI for explanatory scenes.
- **Illustration overload.** Every surface decorated, users drowning in pictures. Correction: purpose-first rule, per-page density caps, ambient instead of literal where mood suffices [accessed].
- **Dark mode as an afterthought.** Illustrations recoloured at the end, ending up muddy or low-contrast. Correction: plan colour logic at definition time; test in both modes.
- **Undocumented characters.** A mascot redrawn by each new artist until it is five different characters. Correction: construction sheets and a do-not list, enforced at review.
- **AI output shipped unreviewed.** Artefacts, anatomy errors, style mismatch and unclear rights entering the brand. Correction: human art direction on every output; rights check per tool; see [AI image generation](../imagery/ai-image-generation.md).

## 9. Evaluation checklist

- [ ] Every illustration in use has a stated purpose and a role (hero, spot, scene, character, ambient).
- [ ] A written style definition covers line, abstraction, colour method, shape language, proportions, detail ceiling, backgrounds and light.
- [ ] The illustration geometry agrees with the brand's motifs and container shapes.
- [ ] All colours come from the palette, with dark-mode behaviour defined and tested.
- [ ] Spots remain legible at their smallest deployed size; heroes hold detail at full size.
- [ ] No real screenshots inside explanatory illustrations; emotional registers match their states.
- [ ] Licences cover all deployed media; AI-assisted images passed human review and a rights check.
- [ ] A sample audit shows one hand across the set; outliers are scheduled for re-styling or retirement.
- [ ] File naming, export sizes and formats follow the technical spec.

## 10. Related topics

- [Graphic language](graphic-language.md) — the vocabulary and ruleset illustration inherits.
- [Patterns and textures](patterns-and-textures.md) — ambient illustration implemented as pattern.
- [Iconography](iconography.md) — the smaller-scale drawn system and its export specs.
- [AI image generation](../imagery/ai-image-generation.md) — prompt craft, rights and workflow for AI-assisted imagery.
- [Photography](../imagery/photography.md) — the literal-truth medium and its art direction.
- [Palette development](../colour/palette-development.md) and [Colour accessibility](../colour/colour-accessibility.md) — the colour rules illustration must obey.
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — contrast and non-text content obligations.
- [Visual identity](../branding/visual-identity.md) — where illustration sits in the wider system.

## 11. References

- Atlassian Design System, "Illustrations" — roles (spot, low-fidelity UI, ambient pattern, collage for marketing only); decide necessity first; "illustration should work with the message, not replace it"; excessive illustration increases cognitive load; no real screenshots in explanatory illustration. https://atlassian.design/foundations/illustrations [accessed 2026-11-23]
- Carbon Design System (IBM) — example of an enterprise design system documenting illustration alongside other visual foundations. https://www.carbondesignsystem.com [search-verified]
- Synthesis note: sections 3–6 are this project's synthesis of system-design practice, the Atlassian guidance above, and general brand-identity methods; they are not attributed to a single source.
