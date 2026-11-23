# Colour theory

## 1. What is it?

Colour theory is the body of knowledge that describes how colours are organised, how they relate to one another, and how combinations of colours are perceived. It has two halves. The physical half defines what colour is — light of different wavelengths, described by models such as RGB, HSL and CMYK. The perceptual half describes how humans organise colours into relationships — hue, saturation, value, temperature, and the scheme families (complementary, analogous, triadic and so on) that designers use to compose palettes.

For an agent doing design work, colour theory is the vocabulary layer underneath everything else in this domain. Before an agent can build a palette ([Palette development](palette-development.md)), predict the emotional reading of a colour ([Colour psychology](colour-psychology.md)), keep it accessible ([Colour accessibility](colour-accessibility.md)) or implement it ([Colour in code](colour-in-code.md)), it needs the concepts defined here. Colour is also one of the basic visual elements alongside line, shape and texture; see [Elements of design](../foundations/elements-of-design.md) for that wider context.

One framing note before the definitions: colour is not a property an object *has* — it is what happens when light, surface and visual system interact. That is why the same brand colour behaves differently on a screen, a poster and a cotton tote, and why the vocabulary below separates what a colour *is* (dimensions, models) from what it *does* (temperature, contrast, schemes).

## 2. Why does it matter?

Colour decisions are among the most frequent and most visible decisions in any design. A wrong typeface is noticeable; a wrong colour system poisons every screen, poster and slide simultaneously. Because colour feels intuitive, it is also the area where untrained intuition fails most expensively: teams pick hues they personally like, then discover the palette cannot produce accessible text, cannot survive a dark theme, or cannot be reproduced in print.

Understanding the underlying mechanics rather than memorising hex codes is what makes colour knowledge transferable across projects, events and organisations. An agent who knows what value and saturation actually control can derive a fifty-colour token system from three brand colours. An agent who knows the difference between additive and subtractive colour can predict, before any proof is printed, which brand colours will shift on paper. The knowledge base's key use case — extending a fixed event logo into a complete brand kit — is precisely this: the logo gives you a few fixed colours, and theory tells you how to build everything else around them.

The field has a history worth knowing at headline level, because it explains the vocabulary. Newton's *Opticks* (1704) established that white light decomposes into a spectrum, replacing older colour cosmologies with a physical account. Goethe's *Theory of Colours* (1810) pushed back with a perceptual and psychological account — wrong as physics, foundational as phenomenology. Munsell (1905) gave design its first workable three-dimensional ordering system (hue/value/chroma), the Bauhaus teachers — Itten above all — turned ordering into teachable schemes, and Albers (1963) demonstrated experimentally that colour perception is contextual. Every section of this file descends from one of those five steps [canonical].

## 3. Core principles

### 3.1 The three dimensions of colour

Every colour can be described by three perceptual dimensions. Different fields name them differently, but the dimensions themselves are stable:

| Dimension | Also called | What it controls | Example |
|---|---|---|---|
| Hue | — | Which colour family it belongs to (red, green, blue…) | 210° in HSL = blue |
| Saturation | chroma, intensity | How far the colour is from neutral grey | 100% = vivid pure hue; 0% = grey |
| Value | lightness, brightness, tone | How light or dark the colour is | 0% = black, 50% = pure hue, 100% = white (in HSL) |

The Munsell system, an early and still influential colour-order system, uses the terms *hue*, *value* and *chroma*; the widely taught formulation comes from Johannes Itten's colour-circle teaching at the Bauhaus [canonical]. HSL (used in CSS) calls the third axis *lightness*. Be careful with one trap: HSL lightness is a mathematical mixing value, not perceived brightness — a pure yellow (`hsl(60, 100%, 50%)`) looks dramatically lighter than a pure blue (`hsl(240, 100%, 50%)`) even though both have "50% lightness". This is why perceptually uniform spaces such as OKLCH exist (see [Colour in code](colour-in-code.md)).

It is worth seeing the levers separately. Holding hue at 210° (blue) and value at 50% while walking saturation down gives: `#007FFF` (100%, vivid), `#267FD9` (70%, softened), `#4D7FB2` (40%, muted — note the hue reads unchanged). Holding hue and saturation while walking value gives the tint/shade table below. Any perceived "colour difference" can be traced to which of these three axes moved, which is why palette reviews should name the axis ("this button is one value darker") rather than "this blue is wrong".

| Operation | Axis moved | Start → end | Perceived result |
|---|---|---|---|
| Tint | value up | `#007FFF` → `#80BFFF` | lighter, airier |
| Shade | value down | `#007FFF` → `#0059B2` | deeper, more serious |
| Tone | saturation down | `#007FFF` → `#407FBF` | calmer, less electric |
| Hue shift | hue only | hue 210 → 240 | new meaning, same energy |

These three dimensions matter because they are the levers you actually control. Most palette work is not about choosing more hues — it is about manipulating value and saturation of a small hue set to create hierarchy, states and nuance.

A caution about the naming of the second and third axes: HSL's *saturation* is defined relative to the hue's own maximum, and its *lightness* is a mixing ratio. Identical HSL numbers therefore do not imply identical appearance across hues. Munsell's chroma is specified per-hue for exactly this reason. In practice, use the three dimensions to reason and communicate, but verify appearance with your eyes or a perceptual space (OKLCH) before shipping numbers.

### 3.2 Temperature

Temperature is the perceptual "warmth" of a colour: reds, oranges and yellows are conventionally warm; blues, greens and violets are conventionally cool. The division sits roughly between red-violet and yellow-green on the wheel, with some colours (magenta, some greens) reading either way depending on neighbours.

Temperature is relative, not absolute. A yellow-green next to a blue-green reads warm; the same green next to orange reads cool. Warm colours appear to advance toward the viewer and read as energetic or urgent; cool colours appear to recede and read as calm or distant. This advance/recede behaviour is a convention of perception in graphic contexts rather than a physical law, but it is reliable enough to design with: warm accents pull attention on cool backgrounds far more than the reverse.

Temperature leaks into parts of the palette designers treat as "non-colour". Grey is never perfectly neutral in practice — mixing grey from a hue biases it (a blue-grey, a warm grey), and flat unmodulated greys next to saturated brand hues can look dirty by simultaneous contrast. The professional convention is to give neutrals a deliberate temperature bias matching the brand's dominant temperature, decided once in the palette and reused everywhere (see [Palette development](palette-development.md) step 3). A related convention: shadows in illustration and UI tint toward the ambient hue rather than pure black, because pure black shadows read as holes rather than depth.

### 3.3 Tint, shade and tone

Three words describe systematically mixing a hue with white, black or grey. They are commonly confused, and the distinction matters when you document a palette:

| Term | Mixed with | Effect | Example (hue 210°) |
|---|---|---|---|
| Tint | white | lighter, softer | 75% lightness → `#80BFFF` |
| Shade | black | darker, deeper | 35% lightness → `#0059B2` |
| Tone | grey | duller, more muted | 50% saturation → `#407FBF` |

A *ramp* or *scale* is an ordered sequence of tints and shades of one hue. Ramps are the backbone of scalable palettes — a primary colour that ships with a ten-step ramp can serve backgrounds, borders, text and dark themes without inventing new colours on the fly (see [Palette development](palette-development.md)).

The three terms are worth practicing until they are reflexive, because they are how palette documentation communicates intent. "Darken the primary" is ambiguous (value or saturation?); "use shade 700" is a specification. Likewise, a design that feels "too bright" may need a *tone* adjustment (less saturation) where a *tint* (more white) would wash it out. When a reviewer says a palette feels heavy, the diagnostic question is which axis to move: value for hierarchy, saturation for energy, hue for meaning.

### 3.4 Additive versus subtractive colour

Screens and print make colour in fundamentally opposite ways:

- **Additive (light):** a screen starts from black and adds red, green and blue light. Mixing all three at full intensity gives white. RGB, HEX and HSL all describe additive colour.
- **Subtractive (pigment):** paper starts from white and subtracts (absorbs) wavelengths with cyan, magenta, yellow and black inks. Mixing all inks gives near-black. CMYK describes subtractive colour.

Two practical consequences follow. First, no screen colour has an exact guaranteed print equivalent: a vivid screen colour can simply be outside the gamut (reproducible range) of a CMYK press, so converting RGB to CMYK shifts it — usually duller and darker. Concretely, the pure screen green `#00FF00` has no ink-only equivalent: a press cyan-magenta-yellow mix that approaches it lands as a noticeably darker leaf green. The failure is silent in the file and visible on the proof, which is why gamut is checked at production time, not in the artwork.

Second, "the same colour" means only "the same coordinates in the same model". A HEX value pasted into print artwork is a wish, not a result. This is why colour profiles exist and why [Colour in code](colour-in-code.md) treats CMYK conversion as a manufacturing step, not a formula. The perceptual study of how these systems interact is Josef Albers' *Interaction of Color* (1963), whose central lesson — colour is perceived in context, never in isolation — underpins most of this domain [canonical].

### 3.5 Colour models and when each matters

| Model | Encodes | Format examples | Matters when |
|---|---|---|---|
| RGB | Red, green, blue channel intensities (additive) | `rgb(15 107 174)` | Screens generally; pixel-level work |
| HEX | RGB packed into hexadecimal notation | `#0F6BAE`, `#0F6BAECC` | Design handoff, tokens, documentation — it is the de facto interchange format |
| HSL | Hue, saturation, lightness (human-readable RGB) | `hsl(207 84% 37%)` | Deriving ramps and variants by hand; readable parametric colour |
| CMYK | Cyan, magenta, yellow, black ink coverage (subtractive) | `C75 M45 Y25 K5` (conventional print notation) | Print production; values must be converted per output profile |
| OKLCH / Lab | Perceptually organised coordinates | `oklch(52% 0.13 240)` | Modern CSS palettes, uniform ramps, contrast-aware variation |

HEX is not a different colour model — it is a compact spelling of RGB. `#0F6BAE` and `rgb(15 107 174)` are the same colour. The reason HEX dominates documentation is precision and terseness, while HSL dominates palette *construction* because a designer can reason "same hue, more lightness" in the notation itself.

A modern workflow uses HEX/RGB for fixed values, HSL or OKLCH for generated variation, and CMYK only at the print boundary. The code-level details of each notation — syntax, alpha handling, gamut behaviour — are in [Colour in code](colour-in-code.md).

When choosing a notation *for documentation specifically*, optimise for the reader, not the machine. HEX is greppable and diffs cleanly, which makes it the right unit for tokens and guidelines. HSL is self-explaining — a reviewer can see "same hue, lighter" in the numbers — which makes it the right unit for describing *relationships* in a design rationale. State which model a document is using, and never present a CMYK value alongside RGB values in the same table without a note that they are not interchangeable.

### 3.6 Perceptual phenomena to expect

A short list of effects that recur in review situations, so they can be named rather than argued about:

- **Simultaneous contrast:** the same colour looks different on different backgrounds — a mid-grey reads lighter on black and darker on white, and a hue picks up a bias toward its background's complement. This is the central lesson of Albers' *Interaction of Color* [canonical] and the reason palette evaluation must happen on real backgrounds, not on isolated swatches.
- **Vibration:** two high-saturation complements at similar value, set edge to edge, produce an unstable afterimage-like shimmer at the boundary. The fix is structural, not cosmetic: separate the fields (border, gap), or drop the value or saturation of one side.
- **Assimilation (spreading):** a colour overlaying fine detail (thin stripes, halftone textures) appears to take on the detail colour, softening it. Relevant when using tints over textured or image backgrounds.
- **Metamerism:** two colours that match under one illuminant can diverge under another — the standard print-shop failure mode when brand colour is checked under office lighting but shipped under daylight. Print proofs should be assessed under the agreed standard illuminant with the printer (established print-production practice).
- **Advance and recede:** warm, saturated colours appear closer; cool, desaturated colours appear further. A convention of perception reliable enough to build depth cues with, but relative — judge against each design's own neighbours.
- **Colour constancy:** the visual system compensates for illuminant changes, so a surface keeps reading "the same colour" across lighting shifts until a comparison object breaks the illusion. Practical consequence: a palette can look consistent on a screen wall but diverge on mixed print stocks — the neutralising context disappeared, so the differences surface.

Testing for these phenomena is mostly structural: view the design against its real backgrounds and its neighbours (simultaneous contrast), at the boundary between complements (vibration), over texture (assimilation), and on the actual output substrate under the actual light (metamerism, constancy). Each phenomenon is an argument for evaluating applied work rather than swatch sheets — a theme the rest of this domain repeats.

## 4. How it works — colour relationships and schemes

### 4.1 The colour wheel

The traditional colour wheel arranges twelve hues in a circle: three primaries (red, yellow, blue in the classic RYB teaching model), their mixed secondaries (orange, green, violet), and six tertiary mixes between them. Scheme names are defined as positions on this wheel — a complementary pair sits opposite, an analogous run sits adjacent.

The wheel is a *teaching model*, not a physical device: hue relationships on actual screens (and in perceptually uniform spaces) do not match RYB wheel positions exactly. Use the wheel for relationships and language, not for numeric hue angles; numeric hues belong to colour models such as HSL or OKLCH.

For reference, the hue numbers you will actually meet in code: in HSL, the 0°/120°/240° axes are red, green and blue, with 30° orange, 60° yellow, 180° cyan and 300° magenta between them (a definition of the model). In OKLCH the angles are perceptually calibrated and differ — for example red sits near 41°, not 0° [accessed, MDN]. The practical rule: when writing CSS, take hue numbers from the model you are writing in and sanity-check the rendered result, rather than porting wheel positions or angles across models.

Reading schemes off real artwork is a two-step skill: place the hues you see on the wheel, then read the relationship. A logo with hues at roughly opposite positions is a de facto complementary brand; a run of three neighbours is analogous. The naming is not pedantry — it tells you which failure modes to expect (complementary pairs vibrate; analogous runs go flat) and which corrections the scheme tradition already knows how to make.

### 4.2 The scheme families

Each scheme is a structural recipe for a palette. What follows is what each is, the perceptual effect it tends to produce, and when it is appropriate — as context-dependent guidance, not law. Every family also ships with a build note (how to construct it) and an evaluation note (how to tell it is working).

A word on how to read the build/evaluate notes: they assume the palette has roles to fill ([Palette development](palette-development.md)) and a value plan to satisfy (section 4.4). A scheme recipe applied without roles produces a pretty swatch card; applied with roles and a value plan, it produces a usable design system.

**Complementary** — two hues opposite on the wheel (blue/orange, red/green, yellow/violet). Maximum hue contrast: each colour makes the other look more saturated, so the pair is vivid and attention-grabbing. Appropriate for accents, calls to action, sport and event brands, and anywhere one element must dominate a page.

At equal saturation and area the pair vibrates and tires the eye; the standard correction is to let one hue dominate and use its complement sparingly, or to soften one side toward tint or tone. *Build:* pick the dominant hue from the brand, take its opposite as accent, then separate their values by two ramp steps so the pair does not compete at equal value. *Evaluate:* squint at the layout — the accent should be findable in one glance, and no boundary should shimmer.

**Analogous** — two to four neighbouring hues (blue, blue-green, green). Low hue tension; reads as harmonious, cohesive and calm because the palette already exists in nature (foliage, water, skin). Appropriate for editorial design, dashboards, wellbeing and heritage contexts. The risk is monotony and weak hierarchy: analogous schemes need value contrast (a dark and a light step) to stay legible.

*Build:* choose a 30–60° span around the dominant hue, and assign each neighbouring hue a different job (fields vs lines vs illustration) so hues do not compete for the same role. *Evaluate:* check the design in greyscale — if it still reads, the value structure is carrying the hierarchy the hues cannot.

**Triadic** — three hues evenly spaced on the wheel (red, yellow, blue). Balanced vibrancy with more variety than complementary and more structure than analogous. Appropriate for children's brands, playful products, and categories needing three distinguishable colour codes. It can look unsophisticated if all three are fully saturated; common practice moderates one or two toward tone.

*Build:* place the brand hue on one vertex, demote the other two to tone versions, and reserve full saturation for the smallest areas. *Evaluate:* count how many elements carry full-saturation colour — if the answer is "many", the scheme is shouting.

**Split-complementary** — a hue plus the two neighbours of its complement (blue with red-orange and yellow-orange). Delivers much of complementary's punch with a safer, more nuanced range and a built-in warm/cool tension. Often recommended as a first scheme when pure complementary feels too loud — a professional convention rather than a rule.

*Build:* use one of the two off-complements as the working accent and hold the other in reserve for charts or states. *Evaluate:* confirm the two accents are distinguishable from each other at a glance, since they are hue-neighbours.

**Monochromatic** — one hue with multiple tints, shades and tones. Maximally cohesive and the easiest scheme to keep accessible, because all hierarchy comes from value and saturation. Appropriate for minimal editorial work, internal tools, dark themes, and brands with one strong signature hue. If the single hue is mid-value the design can lack contrast; add near-black or near-white neutrals.

*Build:* generate an 11-step ramp (see [Palette development](palette-development.md)) and forbid any colour outside it. *Evaluate:* every hierarchy relationship should survive with hue differences removed.

**Tetradic (double complementary)** — two complementary pairs, four hues. The richest structure and the hardest to balance; usually managed by designating one hue dominant and treating the other three as accents. Appropriate for information-rich systems (data categories, wayfinding) where four distinguishable colour codes genuinely exist.

*Build:* form the two pairs on the wheel, then enforce area order (dominant, secondary, two scarce) in the documentation itself. *Evaluate:* remove any one hue and check the design still communicates — if it collapses, the scheme was doing work a label should do.

**Warm palette** — built mainly from warm hues with warm-leaning neutrals. Reads energetic, intimate, appetising; food contexts conventionally use warm hues for this reason. **Cool palette** — cool hues with cool neutrals; reads calm, technical, trustworthy-by-convention. A **balanced warm/cool scheme** uses temperature itself as the hierarchy device: a single warm accent on a cool field is the most reliable attention magnet in graphic design.

*Build:* bias the neutrals to match (warm greys for warm palettes, cool for cool) so backgrounds do not fight the hues. *Evaluate:* check the neutral bias first — a mismatched neutral reads as "something is off" before any hue is consciously noticed.

### 4.3 Comparison table

| Scheme | Hues | Perceived effect | Best for | Watch out for |
|---|---|---|---|---|
| Complementary | 2 | Max contrast, vivid | CTAs, sport, events | Vibration at equal strength |
| Analogous | 2–4 | Harmonious, calm | Editorial, dashboards | Weak hierarchy |
| Triadic | 3 | Balanced vibrancy | Playful, categorical | Childish if over-saturated |
| Split-complementary | 3 | Punchy but nuanced | Safer dramatic palettes | Still needs area control |
| Monochromatic | 1 | Cohesive, elegant | Minimal, dark themes, single-hue brands | Insufficient contrast |
| Tetradic | 4 | Rich, complex | Data codes, wayfinding | Dominance must be enforced |
| Warm / cool | any | Mood via temperature | Food, tech, wellbeing | Temperature is relative to neighbours |

### 4.4 Schemes ride on value structure

A scheme is the hue plan; a working page also needs a value plan. Two designs can use the identical complementary pair and succeed or fail purely on how value is distributed. The working version gives the background the lightest value, the primary content a mid value, text the darkest, and reserves the extreme contrast pair for the one element that must win attention. The failing version spreads both hues across similar mid values, and the page reads flat regardless of how correct the hue relationships are.

The practical sequence when composing: (1) lay out the value structure first — background, surface, text, imagery — as light-to-dark zones; (2) distribute the scheme's hues into that structure so the dominant hue owns the largest area; (3) place the accent hue at the point where the value structure already converges (a headline, a primary action), not at random. This is why monochromatic schemes are so forgiving — the hue plan is trivially consistent, and all compositional effort goes where the perceptual leverage is, in value. Proportion guidance for step 2 is in [Palette development](palette-development.md) section 3.2.

## 5. Practical application

### 5.1 From logo to palette (the brand-kit case)

When extending an existing logo into a full kit, the logo's colours are fixed facts; the scheme is chosen *around* them. A workable procedure:

1. Extract the logo's dominant hue(s) and check their HSL values. Note whether the logo is single-hue or already multi-hue.
2. If single-hue: choose a scheme by desired personality — complementary for energetic events, analogous for calm ones — and place the logo hue as the anchor of that scheme.
3. If the logo is already two-hue: identify whether the pair is near-complementary, near-analogous or neither, and build the rest of the palette in the same relational logic rather than fighting it.
4. Add neutrals biased toward the logo hue's temperature (a blue logo gets slightly cool greys).
5. Hand the result to the structured procedure in [Palette development](palette-development.md), which adds roles, ramps and semantic colours.

Step 3 deserves emphasis because multi-hue logos are the common case for events. The diagnostic question is which hue leads: the one with more logo area, higher saturation, or the one carrying the logo's focal element. That hue becomes the palette's primary; the other is either promoted to a permanent secondary role (if its area in the logo is significant) or demoted to accent (if it is a small flourish). What must not happen is building a fresh scheme and trying to fit both logo hues into it post-hoc — that produces palettes where the logo looks pasted on rather than native.

A sixth step is worth adding for kits that will live a long time: record the scheme decision itself ("complementary, blue-led, gold accent") in one sentence at the top of the palette documentation. Future maintainers extend the kit correctly only if they know what relational logic the original choice followed — without it, the first new hue is chosen by taste and the system's coherence quietly ends.

### 5.2 A worked micro-example

Take the same starting point two ways to see the procedure bite. A logo carries a mid-blue, `hsl(207 84% 37%)`.

- **Energetic sports event:** scheme = complementary. The blue anchors; its accent is a warm orange (hue ≈ 27° in HSL terms). The orange ships as a two-step ramp (500 for badges, 700 for text-capable accent), the blue gets the full ramp, neutrals are cool. Proportion: blue dominates, orange is scarce.
- **Calm research conference:** scheme = analogous. Neighbours at hue 187 (blue-green) and hue 227 (indigo-leaning blue) take the secondary and illustration roles at reduced saturation; no accent at all; neutrals cool. Hierarchy carried by value.

Same logo, same extraction procedure, opposite personalities — the decision variable was the scheme, and every downstream value followed from it. The full role/ramp/semantic layer for the first variant is worked end-to-end in [Palette development](palette-development.md) section 5.2.

### 5.3 Choosing a scheme from intent

Match the scheme to the message, not to taste. If the design must shout (sale, launch, match day), complementary or split-complementary with a warm accent. If it must recede (documentation, data entry), analogous or monochromatic with restrained saturation. If it must organise (four product categories), tetradic or triadic with strict area control. [Brand personality](../branding/brand-personality.md) and [Colour psychology](colour-psychology.md) supply the intent vocabulary.

| Intent | Starting scheme | Saturation posture | Neutrals |
|---|---|---|---|
| Must shout | Complementary / split | High on accent only | Cool, quiet |
| Must reassure | Analogous | Medium, even | Warm-tinted |
| Must organise | Triadic / tetradic | Matched values, moderated saturation | Near-neutral |
| Must disappear | Monochromatic | Low, except one action | Deep, dark-friendly |

## 6. Decision framework

Read the table by row: find your goal, take the preferred structure, and treat the "avoid" column as the specific failure mode that goal attracts. The framework is a starting position for design discussion, not a substitute for evaluation:

| If the goal is… | Prefer… | Avoid… |
|---|---|---|
| Instant attention on one element | Complementary accent on a quiet field | Multiple competing accents |
| Long reading comfort | Analogous/monochromatic, low saturation, strong value contrast | Saturated complementary body text |
| Category differentiation | Triadic/tetradic with area control | Near-analogous hues for categories |
| One-hue brand strength | Monochromatic + neutrals | Adding random second hues |
| Print safety | Tones and desaturated hues (wider CMYK gamut) | Neon screen greens/oranges for critical print elements |
| Dark theme future-proofing | A full ramp of one hue rather than several orphan hues | Scheme chosen only for its light-theme look |
| Multi-surface kit (screen + print + merch) | Scheme built from tones, not full-saturation hues | Palettes whose identity depends on one out-of-gamut colour |

The table gives a starting position, not a verdict. Two goals listed together ("instant attention" and "long reading comfort" on one page) are a genuine design tension, resolved by structure: the quiet scheme carries the reading field, and the loud accent is confined to one element and one place per screen. When two rows of the table disagree, the goal higher in the page's hierarchy wins, and the other goal is satisfied by a different surface — not by compromising both on the same element.

## 7. Examples

Each example names the scheme and the structural decision that made it work:

- **Teal-and-orange poster convention:** film and event posters commonly grade imagery so warm skin tones sit against teal shadows — a working complementary pair, usually with the warm hue limited to faces and key elements. Describes a widespread professional convention, not a rule [canonical].
- **Monochromatic banking interface:** a single blue hue used at ramp steps 50 (background), 100 (cards), 600 (primary actions), 900 (text) — hierarchy from value alone. Common pattern in financial products, where blue is a category convention (see [Colour psychology](colour-psychology.md) for why that convention is cultural, not causal).
- **Analogous wellbeing brand:** sage green primary with green-blue secondary and warm-grey neutrals; the near-lack of hue tension is the point, and all hierarchy is carried by value.
- **Tetradic wayfinding:** four hall colour-codes (blue, orange, green, violet) at matched lightness so the codes differ in hue only — deliberate, because the code must be recognisable as *colour*, with names and numbers always printed alongside (see [Colour accessibility](colour-accessibility.md)).
- **Print-restrained triadic:** a children's book publisher uses the red/yellow/blue triad, but two vertices are tone versions (dusty red, ochre) and only small motifs carry full saturation — the vibrancy survives in the details, the pages stay calm.
- **Warm-neutral failure corrected:** a warm terracotta brand set on default cool-grey backgrounds read "clinical" in review; retinting the neutrals warm (same values, hue bias shifted toward yellow) fixed it without touching a single brand colour — an illustration of section 3.6's neighbour effects and the neutral-bias build note above.
- **Categorical chart set:** a five-series dashboard chart uses the tetradic-plus-accent hues at matched value, each series additionally distinguished by marker shape and direct labels — the scheme supplies hue separation, but the accessibility layer ([Colour accessibility](colour-accessibility.md)) supplies the redundancy that keeps it legible under CVD.
- **Dark-first media product:** a video platform's identity is a monochromatic deep-indigo ramp on near-black surfaces; the same ramp serves the light theme in reverse order. Shows why single-hue schemes are the cheapest to theme (one ramp, two orderings).
- **Scheme misread corrected by extraction:** a team assumed a two-hue logo was "red + blue = complementary"; on the wheel the hues sat one-third apart — a triad missing its third. The corrected palette completed the triad with a tone of yellow instead of fighting the existing relationship, and the logo stopped looking stranded.

### 5.4 Extracting colour from existing artwork

Real palettes usually start from artwork, and extraction has its own small failure modes. The rule of thumb throughout: sample deliberately, record what you did, and never treat an automatic picker's output as a brand decision:

- **Sample the flat interior, not the edge.** Picking a logo colour from an anti-aliased edge returns a contaminated blend; sample the centre of a flat area, or vector-source the original file.
- **Gradients need a policy.** A gradient logo has no single colour; sample both ends, define which end anchors the brand hue, and decide whether the gradient itself ships as a brand asset or gets flattened to its anchor for text-capable uses.
- **Check the sampled value, not just the hue.** A gorgeous logo blue at 22% lightness cannot carry white text or dark text usefully; the palette must reach for neighbouring ramp steps anyway, so generate them at extraction time.
- **Photography is not a palette source.** Dominant-colour analysis of a photo captures lighting, not brand; use photography to choose mood, then pick deliberately.
- **Document what you extracted, with the tool.** "Sampled from vector logo, flat region, 3 samples averaged" is reproducible; "I eyedropped it" is not, and six months later nobody can tell which hex is the brand value versus a sampling accident.

## 8. Common mistakes

- **Confusing HSL lightness with perceived brightness**, then wondering why "50% lightness" blue and yellow look nothing alike. Fix: judge with your eyes or OKLCH, not the L number.
- **Adding hues to fix a flat design** when the real problem is missing value contrast. A monochromatic palette with a proper dark step beats a five-hue palette at equal value.
- **Treating scheme recipes as guarantees.** A triadic palette built from three garish hues at equal area will fail; the recipes describe relationships, and success still depends on saturation, value and area.
- **Pasting HEX into print** and expecting the same colour. Screen and print gamuts differ; convert through a profile at production time.
- **Using RYB wheel angles as CSS hue values.** The wheel and HSL hue angles disagree; pick one system (prefer the actual colour model you are coding in) for numbers.
- **Forgetting temperature is relative** — judging a green "warm" in isolation and discovering it reads cold next to the brand orange.
- **Evaluating swatches instead of layouts.** Simultaneous contrast (section 3.6) means a palette that looks balanced on swatch cards can fail on the real background; always review applied, in context.
- **Mixing colour models mid-system.** A ramp half in HSL and half in OKLCH will have invisible steps and double steps; pick one generation model per ramp.
- **Chasing a scheme name instead of a perception.** "It must be triadic" is not a requirement; the requirement is the perceptual outcome the scheme usually delivers. If another structure delivers it more safely on this project, use that.
- **Evaluating on a single calibrated monitor.** The audience sees the palette on cheap phones, projectors and prints; a palette tuned to one studio display is tuned to nobody.

## 9. Evaluation checklist

- [ ] Can you name each palette colour's hue, approximate saturation and value?
- [ ] Does the scheme have one clear dominant hue/area, or a deliberate reason for equality?
- [ ] Are tints/shades/tone used systematically (ramps), rather than ad-hoc eyeballed variants?
- [ ] Does hierarchy come from value contrast, not only hue difference?
- [ ] For screen work: are all values specified in one model consistently (HEX/RGB/HSL)?
- [ ] For print work: have critical colours been converted via a profile, not assumed?
- [ ] Can you state, for any two adjacent coloured elements, which dimension differentiates them (hue, value, saturation)?
- [ ] Is there one dominant hue/area, and does every full-saturation colour sit inside it deliberately?
- [ ] Do the neutrals carry a deliberate temperature bias consistent with the dominant hue?
- [ ] Have the scheme's known failure modes (from section 4.2) been specifically checked?
- [ ] Would the scheme still communicate under red-green colour-vision deficiency (see [Colour accessibility](colour-accessibility.md))?

## 10. Related topics

- [Palette development](palette-development.md) — turning schemes into role-based, documented palettes.
- [Colour psychology](colour-psychology.md) — what colours communicate, and the limits of those claims.
- [Colour accessibility](colour-accessibility.md) — contrast, colour-independence and CVD-aware construction.
- [Colour in code](colour-in-code.md) — HEX/RGB/HSL/OKLCH/CMYK mechanics, tokens, theming.
- [Elements of design](../foundations/elements-of-design.md) — colour within the full element set.
- [Brand personality](../branding/brand-personality.md) — the intent that scheme choice should serve.
- [Brand guidelines](../branding/brand-guidelines.md) — where scheme decisions are recorded for reuse.
- [Accessible colour](../accessibility/accessible-colour.md) — the accessibility domain's colour reference.

## 11. References

- Albers, J., *Interaction of Color*, Yale University Press, 1963. [canonical]
- Itten, J., *The Art of Color*, Reinhold Publishing, 1961 (original German 1961). Colour circle, tint/shade/tone teaching tradition. [canonical]
- Munsell, A. H., *A Color Notation*, 1905; the Munsell colour-order system (hue/value/chroma). [canonical]
- Goethe, J. W. von, *Theory of Colours*, 1810. Early systematic account of colour perception and colour relationships. [canonical]
- Newton, I., *Opticks*, 1704. Spectral decomposition of white light; the origin of the physical account of colour. [canonical]
- W3C, *CSS Color Module Level 4* (defines HSL, OKLCH and the `color()` function; terminology for colour spaces and gamuts). Verified via the MDN pages below. [accessed 2026-11-23]
- MDN Web Docs, "color_value/color" — `color()` syntax and predefined colour spaces. https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/color [accessed 2026-11-23]
- MDN Web Docs, "color_value/oklch" — OKLCH components and perceptual lightness. https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/oklch [accessed 2026-11-23]
- Colour Blind Awareness, "About Colour Blindness". https://www.colourblindawareness.org/colour-blindness [accessed 2026-11-23]
- Contrast ratios and tint/shade/tone hex values in tables were computed with the WCAG relative-luminance formula and HSL mixing (script in the authors' workspace); see [Colour accessibility](colour-accessibility.md) for the formula. [synthesis]
- The scheme build/evaluate notes and the perceptual-phenomena list are the authors' synthesis of the canonical sources above and standard professional practice. [synthesis]
- Scheme-position claims in section 4.2 (which scheme suits which context) are context-dependent professional guidance, deliberately graded as such; none should be applied without the evaluation step. [synthesis]
