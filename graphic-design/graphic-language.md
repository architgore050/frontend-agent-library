# Graphic Language

## 1. What is it?

A graphic language is the system of repeatable visual elements — geometric shapes, abstract motifs, lines, borders, patterns, textures, gradients, layering behaviours, graphic effects and motion behaviours — that a brand uses *beside and beyond* its logo. Where the logo identifies the organisation in one concentrated mark, the graphic language surrounds every piece of content with a recognisable visual texture: the angled colour blocks behind photographs, the dotted dividers between sections, the repeated circular badge motif, the way panels slide in on the website. It is the difference between a brand that owns a logo and a brand that owns a look.

The term sits between two neighbours. A **visual identity** (see [Visual identity](../branding/visual-identity.md)) is the complete system: logo, colour, typography, imagery, voice. A **style** (see [Visual styles](visual-styles.md)) is a broad aesthetic family such as Swiss or minimalist. The graphic language is the middle layer: the specific, owned vocabulary of graphic elements that a particular organisation deploys, usually built on top of a chosen style. Two companies can both work in a Swiss style; their graphic languages — their actual shapes, rules and motifs — should be unmistakably different.

This file owns the method for building that vocabulary from *any* source. When the source is an existing, fixed logo — the common case when extending an event or organisation brand into a full kit — the analysis of the logo itself is covered in [Fixed logo analysis](../branding/fixed-logo-analysis.md); this file picks up where that analysis ends and turns its findings into a working language.

## 2. Why does it matter?

**Recognition without the logo.** In most communications the logo is small, cornered or absent — a social post, a slide footer, a wayfinding sign, a lanyard. What makes those artefacts read as "ours" is the graphic language: the recurring shapes, angles, textures and compositional habits that repeat across touchpoints. Strong brands are recognisable from a cropped detail, and that recognisability comes almost entirely from the language, not the mark. If every asset is designed from scratch with unrelated decoration, the audience never accumulates the visual memory that makes instant recognition possible.

**Coherence instead of decoration.** The most common failure in applied graphic design is *decorative soup*: each poster, slide or banner gets its own unrelated shapes, blobs, gradients and flourishes, none of which relate to the brand or to each other. The result looks busy, feels arbitrary and builds no equity. A graphic language exists precisely to prevent this: it constrains what may appear, how it is treated, at what sizes and in what positions, so that variation between assets comes from content, not from new decoration.

**Efficiency and scale.** A defined vocabulary plus a ruleset turns design into assembly: designers and non-designers (volunteers running an event's social accounts, for instance) produce consistent work quickly because most decisions are already made. This matters enormously for distributed teams and for event brands, where many hands produce many artefacts in a short window. It is also the precondition for templating and automation — a design system or a set of social-media templates can only be built on top of a stable vocabulary.

**Extensibility.** A language with a small set of well-chosen elements and clear rules scales to new formats the brand has never used — a stage backdrop, a phone wallpaper, an animated story frame — without a redesign. That is the practical goal of the method in this file: take the fixed source (usually a logo), derive a vocabulary, write the ruleset once, then generate everything else. The scenario that makes this urgent is the **fixed-logo brand kit**: an event or organisation whose mark is already published and cannot change, yet whose poster, social, signage and web presence must now be produced in volume. There the graphic language is not a stylistic luxury; it is the only remaining degree of freedom, and everything the audience will recognise must be built from it.

## 3. Core principles

### 3.1 Derivation: a vocabulary must come from somewhere

Every element in a graphic language should be traceable to a stated source: the geometry of the logo, a brand attribute, or a deliberately chosen style. Derivation is what makes a language feel *owned* rather than borrowed. A diagonal ribbon motif means something when it echoes a diagonal in the logotype; the same ribbon on a brand with a purely circular logo is noise. When you cannot answer "where does this element come from?", you are decorating, not designing. The three derivation methods are described in section 4.1.

### 3.2 Economy of means

A language needs few elements, treated many ways. Four to six core elements — a shape family, a line treatment, one pattern, one gradient behaviour — are enough to carry an entire brand across print, screen and environmental applications, provided each element has several sanctioned treatments (scale, colour, density, crop). More elements than that and coherence collapses under its own weight; fewer and the brand starts to feel monotonous at scale. Professional practice consistently favours a narrow vocabulary reused with discipline over a wide vocabulary used once each — a principle that echoes the modernist "less is more" tradition [canonical].

### 3.3 Rules before assets

The ruleset is the language; the assets are just its outputs. Write the rules — which elements exist, how they are treated, at which sizes, in which positions — *before* producing posters, templates or backgrounds. Assets made without rules cannot be audited or extended: when a new format arrives, there is nothing to consult. The ruleset document described in section 4.2 is deliberately short (one to two pages); its value is that it is short enough to be read and followed by everyone who touches the brand.

### 3.4 Hierarchy of elements

Not all elements are equal. Define three tiers:

| Tier | Role | Typical elements | Frequency |
| --- | --- | --- | --- |
| Hero | Carries the brand on flagship surfaces — covers, stage backdrops, key visuals | Signature motif, hero pattern, dominant gradient | On most major assets, used boldly |
| Support | Adds texture and continuity without competing with content | Secondary pattern, line family, border treatments, small motifs | On most assets, used quietly |
| Accent | Moments of emphasis and delight — section markers, badges, dividers | Spotlight shapes, motion flourishes, corner devices | Occasionally, at points of emphasis |

The hierarchy prevents the classic failure of every asset shouting: hero elements dominate in hero places, support elements stay quiet behind content, and accents appear only where the eye should pause. The same tier logic applies to type scale (see [Typographic hierarchy](../typography/typographic-hierarchy.md)) and to pattern hierarchies (see [Patterns and textures](patterns-and-textures.md)).

### 3.5 Consistency with controlled variation

Repetition builds recognition; identical repetition builds fatigue. A good ruleset therefore defines not only what is fixed but what is allowed to vary: a motif may rotate or flip but not distort; a pattern may appear in two colourways but not in arbitrary recolourings; a diagonal band may sit top-left or bottom-right but not mid-canvas under text. Variation axes should be enumerated in the ruleset so that designers know exactly how much freedom they have — this is what keeps twenty different posters feeling like one brand.

### 3.6 Ownership versus borrowing

An element only earns a place in the language when the brand could plausibly "own" it — when the connection to a source (logo geometry, attribute, chosen style adapted to the brand) is arguable in one sentence. Generic decoration that any brand could use — a stock blob, a random starburst, a trendy grain passed from project to project — builds recognition for nothing and, at worst, for someone else. The ownership test is also a defensive tool: when a stakeholder requests "something like [other brand]'s background", the test converts the request into "which of our elements, treated in that spirit?" instead of an import.

## 4. How it works

### 4.1 Derivation methods

#### From logo geometry

The most common and most robust source, especially when the logo is fixed and cannot change (the typical event-brand situation). The method:

1. **Inventory the logo's construction.** Identify its underlying geometry: which shapes (circles, squares, triangles, arcs), which angles (30°? 45°?), which curves, which stroke weights, which alignments. Strip away letters and depictive detail until only construction remains — this is the analysis step detailed in [Fixed logo analysis](../branding/fixed-logo-analysis.md).
2. **Extract candidate motifs.** From that construction, derive abstract elements: an arc becomes a crescent shape; a 45° cut becomes a corner treatment for panels and images; the logo's stroke weight becomes the line family; its counter shape (the hole in an "A" or "O") becomes a badge or dot motif. Candidates should be *simpler* than the logo, not copies of it.
3. **Reduce.** Test each candidate for distinctiveness (does it still evoke the logo when seen alone?), for neutrality (can it sit behind content without stealing attention when needed?) and for extensibility (can it be tiled, scaled, cropped, animated?). Keep the survivors; discard the rest.

Deriving from logo geometry guarantees the language cannot drift away from the mark, which is why it is the default for fixed-logo situations such as established events and organisations.

#### From brand attributes

When the logo is too literal, too generic or too decorative to yield usable geometry, derive from attributes instead. List the brand's personality terms — for example "energetic, precise, local" — and translate each into a visual quality: energetic → diagonals, saturated colour, motion blur; precise → thin hairlines, exact grid alignment, sharp corners; local → a motif drawn from the venue's architecture or the city's street grid. The mapping must be argued in writing (attribute → quality → element) so that the language can be evaluated, not just felt. Colour psychology guidance for this translation lives in [Colour psychology](../colour/colour-psychology.md), and the general technique of translating abstract qualities into visual decisions is a core art-direction skill (see [Art direction](art-direction.md)).

#### From a chosen historical style

A third source is a deliberately adopted style — Swiss, Bauhaus, Constructivist, editorial — whose characteristic elements (grids, primary geometry, diagonals, generous white space) are filtered through the brand. This is legitimate and common, but the style must be *selected for fit* (see the decision framework in [Visual styles](visual-styles.md)) and then *adapted*: the brand takes the style's principles and merges them with logo-derived geometry, otherwise the result is a costume the brand wears rather than a language it owns. Historical background for the major movements is in [Design philosophies](../history/design-philosophies.md).

In practice the strongest languages combine sources: Swiss-style grid discipline + logo-derived diagonal + brand-attribute colour behaviour.

### 4.2 The vocabulary ruleset

The ruleset is a short written specification — ideally one or two pages — with five parts. Writing it as a structured document (even as JSON for tooling, as below) forces precision and makes audits possible.

```json
{
  "elements": {
    "motif-slash": {
      "source": "45-degree cut from logo counter",
      "forms": ["band", "corner-clip", "divider"],
      "may": ["rotate ±90° steps", "recolor with palette", "scale 1x–8x"],
      "mayNot": ["stretch non-uniformly", "add drop shadow", "overlap body text"]
    },
    "pattern-dots": {
      "source": "dot grid derived from logo construction lines",
      "variants": ["support-dense", "support-sparse", "accent-single"],
      "opacity": ["100%", "24%", "12%"]
    },
    "line-hairline": {
      "source": "logo stroke weight",
      "weights": ["1px", "2px"],
      "use": ["dividers", "frame borders", "underline accents"]
    }
  },
  "placement": {
    "anchors": ["top-left", "bottom-right"],
    "keepClear": ["text columns", "logo exclusion zone"]
  },
  "combination": {
    "maxElementsPerAsset": 3,
    "heroNeeds": ["one hero element at 60%+ canvas dominance"],
    "forbiddenPairs": ["pattern-dots + motif-slash both at full opacity"]
  }
}
```

The five parts of a ruleset:

1. **Allowed elements.** The closed list. Anything not listed does not exist in the language.
2. **Treatments.** For each element: permitted colours (palette references only, see [Palette development](../colour/palette-development.md)), opacities, rotations, crops, stroke weights. Enumerated lists ("100% / 24% / 12%") prevent the drift of arbitrary quarter-opacities.
3. **Sizes.** Scale bounds and density limits, ideally expressed against the brand's spacing scale:
   - Minimum size per element (below which the element loses its identity — usually when internal detail merges).
   - Maximum size per element (above which it becomes a composition rather than a vocabulary element).
   - Pattern tile sizes and their permitted display densities.
   - If the brand has a spacing scale, tie element margins to it so language and layout breathe on the same rhythm.
4. **Placements.** Where elements may sit: anchored corners, margin bands, behind-image zones; and the keep-clear areas (text columns, logo exclusion zone, faces in photography).
5. **Combinations.** Which elements may co-occur, how many per asset, and which pairs are forbidden — the part most often omitted and most often needed.

For human readers, the same ruleset is often circulated as a short Markdown or PDF page. A usable excerpt:

```markdown
## Motif: slash (hero tier)
Source: 45° cut from the logo counter.
Forms: divider band, corner clip, stepped echo.
May: rotate in 90° steps; scale 1x–8x; palette colours only.
May not: stretch non-uniformly; take shadows or gradients; cross body text.
Placements: anchored top-left or bottom-right; keep-clear = text columns.
Pairs with: pattern-dots at ≤24% opacity only; never with gradient--ambient.
```

A ruleset that lives only in a designer's head is not a ruleset. If it is not written down well enough that a new contributor can produce a compliant asset on the first try, it is not finished.

### 4.3 Element catalogue

Each entry below names the element class, its role in the language, and working guidance. Numeric values marked "conventional" are starting points to adapt, not laws.

#### Geometric vocabulary

The set of primitive shapes the brand owns: one or two shapes plus their natural derivatives. Derive from logo construction where possible. Define a shape's canonical proportions — for example a 2:1 rectangle, an equilateral-cornered triangle, a circle of fixed diameter steps — so that every occurrence can be checked against the rule. Geometric primitives are perceptually strong: closure and simplicity make them legible even at small sizes (see [Gestalt and perception](../foundations/gestalt-and-perception.md)).

Working guidance:

- Keep primitives on a shared construction grid; shapes that share a grid combine cleanly, shapes from different grids fight.
- Define the legal operations per shape: rotate (in fixed steps), scale (within bounds), mirror. Never skew, distort or free-rotate — deformation breaks the "owned geometry" impression.
- Give each primitive a name in the ruleset ("chip", "slash", "orb") so reviews can discuss elements unambiguously.

#### Abstract motifs

Single, non-repeating compositions built from the vocabulary — a cluster of three slashes, an orbit of dots around an implied circle, a stepped stack of chips. Motifs give the language a "voice" beyond flat patterns: they are the elements people actually remember. Keep the motif count low (two to four) and give each a defined job: section markers, award badges, background flourishes behind hero imagery.

A motif should pass three checks before joining the language: **distinctiveness** (it reads as this brand, not any brand), **neutrality** (it can sit behind content at low emphasis without disturbing reading), and **extensibility** (it survives cropping to 50%, scaling to 300%, and animation). A motif that fails neutrality becomes a hero-only element — note that in the ruleset rather than discovering it in production.

#### Lines and borders

Define a line family: weights, allowed colours, corner behaviour, and sanctioned positions. A consistent line family is the cheapest recognition device in the entire vocabulary — a hairline used the same way on every asset ties a system together almost invisibly.

| Line role | Conventional weight | Typical use |
| --- | --- | --- |
| Hairline | 1px / 0.5–0.75pt print | Column dividers, table rules, quiet frames |
| Standard | 2px / 1–1.5pt print | Underline accents, image borders, motif strokes |
| Bold | 4px+ / 3pt+ print | Statement frames, rule blocks, hero accents |

Borders belong to this family, not to a separate logic. Specify when frames are allowed (image containers, quote blocks, coupon panels), what offset the frame keeps from its content (conventional: one unit of the spacing scale, so frame and content breathe together), and the frame's corner treatment, which must match the motif corner geometry. A framed image whose corners disagree with the logo's corner geometry is the most common quiet incoherence in applied work.

#### Shapes as containers

Decide which shapes crop or contain content: photographs in circles, in clipped-corner rectangles, in full-bleed bands with one straight edge. Container shapes are among the most visible language decisions because they appear wherever imagery appears — every page, every slide, every post. Restrict the set to one primary container shape and at most one secondary, and keep its corner geometry consistent with the motif geometry. Implementation guidance: apply container shapes as reusable masks or CSS `clip-path`/`border-radius` recipes rather than re-drawing them per asset, so the geometry cannot drift. The imagery side — what goes inside the containers — is directed in [Photography](../imagery/photography.md).

#### Patterns

Tiled arrangements of vocabulary elements, from whisper-quiet dot grids to statement wallpapers. Patterns are the workhorse of a graphic language because they fill large surfaces with identity at zero content cost. Construction, tiling and scale rules are owned by [Patterns and textures](patterns-and-textures.md); the graphic language's job is to define which patterns exist, their tier (hero/support), and their sanctioned colourways.

#### Textures

Non-geometric surface qualities — grain, noise, paper feel, halftone screens, scanner artefacts. Textures are the highest-risk element class: applied broadly they read as dirt, applied deliberately they read as character. A halftone texture on a Constructivist-styled music festival is a decision; a random grunge overlay on a bank's annual report is a mistake.

- Restrict textures to defined surfaces: image treatments, band backgrounds, poster grounds — never body-text backgrounds.
- Always specify intensity in the ruleset (conventional: 3–8% opacity overlay for a subtle grain; 15–25% for a deliberate statement texture).
- Prefer one texture, consistently applied, over several textures rotated by mood.

#### Layering

Define stacking semantics: what sits behind content, what sits over imagery, what floats above. Give sanctioned opacity steps and, if blend modes are used, name the allowed ones. Layering rules are what make collaged compositions feel designed rather than pasted — they connect directly to depth and hierarchy in [Principles of design](../foundations/principles-of-design.md).

```css
/* Conventional starting layering recipe, adapt to the brand scale */
.layer--ground   { position: absolute; z-index: 0; opacity: 0.12; }  /* pattern/motif wash */
.layer--image    { position: absolute; z-index: 1; }
.layer--tint     { position: absolute; z-index: 2; mix-blend-mode: multiply; opacity: 0.24; }
.layer--content  { position: relative; z-index: 3; }                  /* text always wins */
.layer--accent   { position: absolute; z-index: 4; }                  /* deliberate emphasis only */
```

Rules worth writing down: text never shares a layer with texture (readability first — see [Typesetting](../typography/typesetting.md)); tint layers use only palette colours at defined opacities (8%, 16%, 24% are conventional steps); accent layers are rationed — one per composition unless the tier is hero.

#### Gradients

Specify gradient types the brand uses (linear, radial, conic, mesh), their geometry (angle ranges, focal placement), and their colour behaviour (adjacent palette stops, or hue-shifted pairs). Gradients date quickly when loud and trend-driven; they survive when built from the brand palette with restrained ranges. As a conventional starting point: soft linear gradients of 10–30° hue difference read as ambient light; steep multi-stop gradients read as decoration and demand a reason.

```css
/* Language-defined gradient recipes (conventional starting points) */
.gradient--ambient {
  /* soft light wash: adjacent palette stops, one direction only */
  background: linear-gradient(135deg, var(--c-primary) 0%, var(--c-primary-soft) 100%);
}
.gradient--duotone {
  /* image tint: multiply blend, two palette stops */
  background: linear-gradient(to top, var(--c-secondary) 0%, var(--c-primary) 100%);
}
```

Forbid per-asset gradient invention: two recipes, used everywhere, outlast ten creative gradients used once. Implementation details and dark-mode behaviour live in [Colour in code](../colour/colour-in-code.md).

#### Visual effects

Shadow, blur, glow, grain, distortion, glitch, chromatic aberration. Every effect in the language needs a written rule: what it signals (elevation? emphasis? nostalgia? unease?), where it applies, and its parameter range — for example "shadows: single direction, one blur radius, one opacity". Unruled effects are the fastest route to incoherence because they multiply silently: each designer adds one "small" shadow, and a year later nothing matches. If the brand works in a brutalist or deliberately raw register (see [Visual styles](visual-styles.md)), the rule may be "no effects at all" — the absence is then the signature.

#### Graphic repetition

The rhythmic use of repeated elements — rows of slashes, repeated badges, stepped echoes of the motif shrinking into the distance. Repetition is how a language creates energy and motion on a static page, and it is the perceptual bridge between a single motif and a pattern. Define repeat behaviour in the ruleset:

- **Axis**: horizontal, vertical, or diagonal (fixed to the motif angle if one exists).
- **Count or density**: bounded ranges, for example "3–7 repeats" or "spacing between 0.5× and 2× the motif height" (conventional).
- **Progression**: even spacing for calm, arithmetic progression for acceleration, shrinking scale for depth.

Repetition must terminate cleanly — a repeat that runs off-canvas should do so symmetrically or with an obvious fade, not stop awkwardly one unit short of the edge.

#### Motion language

On screen, the vocabulary extends into time: how things enter, exit, and respond. A brand that always moves with the same ease and tempo becomes recognisable in video, interface and presentation alike — motion is the only element class the audience experiences bodily, which is why it carries so much personality.

| Behaviour | Conventional duration | Typical easing | Notes |
| --- | --- | --- | --- |
| State feedback (hover, press) | 100–200ms | ease-out | Instant enough to feel physical |
| Element entrance | 200–400ms | brand ease (one curve, reused) | The brand's "handwriting" |
| Element exit | 100–200ms | ease-in or linear | Exits are faster than entrances |
| Large panel / scene change | 400–600ms | brand ease | Rationed; never on every scroll |

Choreography rules: staggered delays for repeated items (conventional: 40–80ms steps), one entrance choreography per scene, and no looping ambient motion near text. Motion must respect reduced-motion accessibility settings — provide static equivalents for every animated behaviour (see [WCAG fundamentals](../accessibility/wcag-fundamentals.md)). The general perceptual principles behind why motion reads as energy or calm are covered in [Principles of design](../foundations/principles-of-design.md).

### 4.4 Testing coherence

A language is coherent when a viewer can tell "this belongs to the brand" from elements alone. Four practical tests:

1. **The logo-strip test.** Remove the logo from five assets of different types (poster, slide, social post, banner, document). Show them side by side. If they still read as one family, the language works; if they read as five unrelated designs, the vocabulary or its rules are too weak.
2. **The element census.** List every graphic element across a sample of ten assets. Count distinct elements and off-ruleset occurrences. A healthy language shows few distinct elements and high repetition; a census that keeps finding new one-off shapes is the signature of decorative soup.
3. **The attribution test.** Show a single asset (no logo) to people familiar with the brand and ask whose it is. Unscientific, but a majority attribution is strong evidence the language carries identity on its own.
4. **The ruleset audit.** Check a sample of assets against the ruleset: only listed elements, only sanctioned treatments, sizes within bounds, placements legal. Failures here are correction opportunities, not style opinions — the ruleset is the contract.

## 5. Practical application

The typical assignment: a fixed event logo must become a complete brand kit (posters, social frames, slides, signage, lanyards, website hero). A working sequence:

1. **Analyse the source.** Run the logo analysis (geometry inventory → candidate motifs) per [Fixed logo analysis](../branding/fixed-logo-analysis.md). Output: a page of construction notes and six to ten candidate elements.
2. **Choose derivation mix.** Decide the weight of logo-derived vs attribute-derived vs style-derived elements. Default: logo-derived core, attribute-derived colour and motion behaviour, style-derived compositional discipline.
3. **Reduce to the vocabulary.** Select 4–6 elements across the tiers (one hero motif, one pattern, one line family, one gradient behaviour, one accent). Write one sentence per element naming its source and its job.
4. **Write the ruleset.** Produce the five-part ruleset (elements, treatments, sizes, placements, combinations) from section 4.2. Keep it to one or two pages.
5. **Prove it on a page.** Before mass production, design the three hardest artefacts (usually: a busy content-heavy schedule page, a minimal cover, a small social avatar frame) strictly under the ruleset. Iterate the ruleset — not the artefacts — until all three work. This is where vocabulary weaknesses surface cheaply: a motif that collapses at avatar size, a pattern that fights a dense schedule table, a gradient that swallows a headline. Fixing them now costs a ruleset edit; fixing them after two hundred posters have been printed costs money and credibility.
6. **Build master assets.** Produce the reusable masters: pattern tiles (SVG), motif library (SVG), gradient recipes, line styles, motion specs. Structure them like a miniature design system so templates can consume them.
7. **Template the long tail.** Turn the masters into templates for each touchpoint (see [Applications](../applications/) for format-specific work) so that non-designers extend the kit without inventing new graphics.
8. **Audit and correct.** Run the four coherence tests (section 4.4) at milestones — before print, mid-campaign. Correct by tightening rules, not by adding elements. When a genuine gap appears (a needed element that does not exist), extend the ruleset deliberately, once, and document it.

## 6. Decision framework

**How many elements?** Start at four. Add an element only when a repeated, documented need appears that the existing set cannot express. Retire elements that have not been used across the last audit cycle. The vocabulary is a living but slowly-changing set — quarterly change at most, never per-asset.

**Which derivation source?**

| Situation | Primary source | Rationale |
| --- | --- | --- |
| Fixed logo, established brand (typical event case) | Logo geometry | Cannot change the mark; language must visibly belong to it |
| Logo is literal or pictorial (e.g. an animal, a building) | Brand attributes + one extracted abstract element | Pictorial detail does not abstract well; attributes carry the language |
| New brand, logo still open | Attributes first, then design logo and language together | Co-designed marks and languages fit perfectly |
| Brand feels cold or generic | Chosen style + attributes | A style supplies compositional character that a bare vocabulary lacks |
| Multi-event or multi-sponsor family | Shared structural vocabulary + per-event accent layer | One recognisable framework, one swappable accent element per edition |
| Rebrand or refresh in progress | Attributes of the *new* identity + geometry of any surviving mark | Keeps continuity visible while the system changes |

**When may the rules be broken?** Only deliberately, only rarely, and only at the tier of hero elements on flagship surfaces (a key visual may break placement rules for impact). Breakage must be visible as *intent* — an audience should feel "they did that on purpose", not "someone ignored the guide". Support-tier and accent-tier elements follow the rules everywhere, because their consistency is exactly what licenses the hero-tier freedom.

**Who arbitrates?** Name one owner of the ruleset (an art director or brand lead, see [Art direction](art-direction.md)). Ambiguities and proposed extensions go to the owner; the owner logs every decision in the ruleset's changelog. Without an arbiter, rules erode through a series of individually reasonable exceptions — the drift is slow, cumulative and only visible at the next audit.

## 7. Examples

**Logo-derived diagonal family (illustrative composite).** An event logo built from a 45°-cut square yields: corner-clipped image containers (45° cut on one corner), a slash motif used as a divider between programme items, a diagonal band behind hero photography anchored to the top-left, and stepped echoes of the slash for motion transitions. Every element traces to the same angle; the kit reads as one family whether or not the logo is present. (Synthesis of the method sources below; not a specific documented case.)

**Attribute-derived language (illustrative composite).** A community festival brand with the attributes "warm, handmade, local" and a pictorial logo that resists abstraction derives instead: a paper-grain texture on poster grounds (handmade), a rounded line family at 2px with softly irregular hand-drawn dividers (warm), a container shape of a gently tilted rectangle (handmade informality, bounded to ±2° so it stays deliberate), and motion with slow, soft ease entrances (unhurried). The language is defensible without logo geometry because every element maps to a written attribute.

**Historical precedent — the grid as language [canonical].** Josef Müller-Brockmann's concert posters for the Tonhalle Zürich treated the modular grid itself as visible graphic language: arcs and concentric rings generated geometrically, repeated across a series, so that the *system*, not any single poster, carried the identity. The lesson generalises: the strongest graphic languages expose their generating system.

**Historical precedent — a corporate motif [canonical].** IBM's long-standing 8-bar striped motif, developed under Paul Rand's identity work, reduced the company name to a pure rhythm of horizontal bars; the bars could wrap, animate and scale independently of the logotype. It remains a standard example of a logo-derived abstract motif carrying a language across media.

**Product-system precedent [accessed].** Atlassian's design system restricts product illustration to defined roles — spot illustrations, low-fidelity UI diagrams, ambient background patterns — with collage-style illustration reserved for marketing, and states that excessive illustration increases cognitive load. This is a graphic language operating as rules, not assets: the same discipline this file prescribes, documented publicly.

## 8. Common mistakes

- **Decorative soup.** New, unrelated shapes on every asset; no census would find repeats. Correction: freeze the element list, run the logo-strip test, delete anything unsanctioned.
- **Copying the logo literally.** Elements that are miniature logos rather than abstractions compete with the mark and look like stamps. Correction: simplify candidates one step further than feels comfortable.
- **Too many elements, each used once.** The language becomes a sticker sheet. Correction: enforce the tier hierarchy and the max-elements-per-asset rule from the combinations section.
- **No size or opacity bounds.** Motifs drift to arbitrary scales and half-opacities; subtle incoherence accumulates. Correction: enumerate treatments (section 4.2) and audit against them.
- **Effects without rules.** One-off shadows, glows and blurs multiply silently, especially late in a project. Correction: name allowed effects and parameter ranges; treat everything else as off-language.
- **Vocabulary ignored for "special" assets.** The launch poster or stage design abandons the language, then every asset after it looks impoverished by comparison. Correction: hero-tier assets may bend placement and scale rules, never element identity.
- **Motion as an afterthought.** Static rules only; then animations introduce foreign easing, foreign shapes, foreign timing. Correction: write the motion language into the same ruleset as the static one.
- **Vocabulary inflation during events.** Under deadline pressure each new artefact demands "just one more shape"; by the final push the language is a junk drawer. Correction: the arbiter merges genuine needs into existing elements (a new divider becomes a sanctioned treatment of the line family) rather than approving new elements.
- **Auditing only at the end.** Incoherence compounds; a final audit finds twenty small drifts that would have been five one-week fixes. Correction: run the element census and ruleset audit at every major milestone, per the sequence in section 5.

## 9. Evaluation checklist

- [ ] Every element in use traces to a stated source (logo geometry, attribute, or chosen style).
- [ ] The vocabulary is a closed list of roughly 4–6 core elements, tiered hero/support/accent.
- [ ] A written ruleset exists covering elements, treatments, sizes, placements and combinations.
- [ ] Each element has enumerated treatments (colours from the palette, defined opacities, rotation and scale bounds).
- [ ] Keep-clear rules protect text columns and the logo exclusion zone.
- [ ] The logo-strip test passes across five asset types without the logo.
- [ ] An element census of ten assets shows high repetition and few one-offs.
- [ ] Patterns, icons, illustration and photography all follow the same geometry (links: [Patterns and textures](patterns-and-textures.md), [Iconography](iconography.md), [Illustration](illustration.md), [Photography](../imagery/photography.md)).
- [ ] Motion behaviours (durations, easing, choreography) are specified and respect reduced-motion preferences.
- [ ] Rules can be broken only deliberately, at hero tier, and visibly as intent.

## 10. Related topics

- [Fixed logo analysis](../branding/fixed-logo-analysis.md) — analysing a fixed logo to extract construction geometry and candidate motifs.
- [Visual identity](../branding/visual-identity.md) — the complete identity system this language belongs to.
- [Visual styles](visual-styles.md) — the aesthetic families a language may be built upon.
- [Patterns and textures](patterns-and-textures.md) — construction, tiling and implementation of the pattern elements.
- [Iconography](iconography.md) — the icon system, itself a sub-vocabulary of the language.
- [Illustration](illustration.md) — illustration as an element of the language.
- [Art direction](art-direction.md) — the decision discipline that keeps the language consistent in use.
- [Elements of design](../foundations/elements-of-design.md) — the perceptual raw material (point, line, shape, texture) the vocabulary is built from.
- [Gestalt and perception](../foundations/gestalt-and-perception.md) — why simple geometric vocabularies read so strongly.
- [Design philosophies](../history/design-philosophies.md) — historical background for style-derived languages.
- [Colour in code](../colour/colour-in-code.md) — implementing gradients and colour treatments in CSS.

## 11. References

- Tate, "Bauhaus" (art-term entry) — community-of-artists teaching model and aim to bring art into everyday life. https://www.tate.org.uk/art/art-terms/b/bauhaus [accessed 2026-11-23]
- Wikipedia, "International Typographic Style" — Ernst Keller's content-first teaching (Kunstgewerbeschule Zürich, 1918); grids described as the most legible and harmonious means of structuring information; flush-left ragged-right setting; Univers, Helvetica (Max Miedinger with Eduard Hoffmann, from Neue Haas Grotesk); *New Graphic Design* periodical, 1959. https://en.wikipedia.org/wiki/International_Typographic_Style [accessed 2026-11-23]
- Atlassian Design System, "Illustrations" — role-based illustration usage (spot, low-fidelity UI, ambient pattern; collage for marketing only); guidance that illustration should support the message and that excessive illustration increases cognitive load. https://atlassian.design/foundations/illustrations [accessed 2026-11-23]
- Josef Müller-Brockmann, *Grid Systems in Graphic Design*, Niggli, 1981 — modular grids and geometric construction as visible design systems [canonical]
- Philip B. Meggs and Alston W. Purvis, *Meggs' History of Graphic Design*, Wiley — standard history underlying the movement and corporate-identity examples above [canonical]
- IBM/Paul Rand corporate identity work, including the 8-bar motif — standard design-history example [canonical]
- Material Design, "System icons" (icon-grid keyline construction) — relevant when the vocabulary defines icon geometry. https://m2.material.io/design/iconography/system-icons.html [search-verified]
- Smashing Magazine, "The Split Personality of Brutalist Web Development" — brutalism as unconcerned rather than intentionally broken aesthetics. https://www.smashingmagazine.com/2020/01/split-personality-brutalist-web-development [search-verified]
