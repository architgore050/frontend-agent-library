# Palette development

## 1. What is it?

Palette development is the process of turning colour theory and brand intent into a working, role-based colour system: a small set of colours, each assigned a job (primary, secondary, accent, neutral, background, semantic), expanded into tint/shade ramps, checked for accessibility, documented with exact values, and tested in real layouts.

It sits between [Colour theory](colour-theory.md) (which explains relationships and dimensions) and [Colour in code](colour-in-code.md) (which implements the results as tokens and CSS). The distinction matters in practice: theory answers "what colours could relate to these brand colours?", palette development answers "which exact colours play which roles, in what proportions, documented how?", and code answers "how are they named, stored and themed?".

## 2. Why it matters?

An undocumented palette is a decision tax paid on every future screen. Without roles and ramps, each designer or agent invents "a slightly darker blue" for the next hover state, and within weeks the product carries twenty near-identical blues that no one can defend. A developed palette, by contrast, makes most colour decisions pre-made: any new component asks "which role do I need?" and gets a token.

For the brand-kit case — extending a fixed event logo into a complete system — palette development is the phase where a logo becomes a brand. The logo supplies two or three fixed colours. A developed palette supplies the other ninety-five per cent of every future artefact: backgrounds, text, borders, states, charts, print. Doing this once, properly, is what keeps the kit reusable across future projects and organisations.

There is also a quality argument. Colour failures (contrast, ambiguity, drift) are almost never caused by bad hue choices; they are caused by missing structure. The structure described here is what allows the later stages — accessibility checks, theming, tokenisation — to be mechanical rather than heroic.

One expectation to set before the procedure: the output of palette development is not "some nice colours" but a *contract*. The contract says which colour plays which role, in what proportion, under what constraints, and with what measured behaviour. Everything downstream — components, print, slides, sub-brands — either honours the contract or amends it in documentation. Colour decisions made outside the contract are how systems rot.

## 3. Core principles

### 3.1 Roles first, colours second

A palette is an *organisation*, not a bag of colours. Every colour must earn its place by having a job:

| Role | Job | Typical share | Examples |
|---|---|---|---|
| Primary | Brand carrier; main actions, headers, key surfaces | dominant brand colour | `primary-600` for buttons |
| Secondary | Supporting brand hue; secondary surfaces, illustrations | significant but less than primary | sidebar, tag backgrounds |
| Accent | Attention spike; CTAs, highlights, notifications | small | a warm gold on a cool blue scheme |
| Neutral | Text, borders, dividers, shadows | large (all the "non-colour" work) | grey ramps |
| Background | Page and surface fields | largest area | off-white `#FAFAF8`, near-black `#111418` |
| Semantic | Meaning independent of brand: success, warning, error, info | small, fixed | green/amber/red/blue (conventional hues) |

Two consequences follow from role-based thinking. First, *background and neutral are roles, not afterthoughts* — they occupy most of the visual field and deserve deliberate design. Second, *accent is defined by scarcity*: if the accent colour is on every card, it is a secondary, and attention has nowhere to go.

Background strategy is the most underrated decision in the table, because it sets the canvas everything else is judged on:

| Choice | Character | Use when | Trade-off |
|---|---|---|---|
| Pure white `#FFFFFF` | clinical, maximal clarity | dashboards, tools, print-matched brand | can read stark; shadows less visible |
| Off-white tint `#FAFAF8`–`#F8F7F3` | soft, editorial, warm or cool | long-form reading, brand warmth | slight colour cast in screenshots |
| Brand-tinted ground (ramp step 50) | strongly on-brand | event sites, campaign pages | text contrast must be re-tested on the tint |
| Dark surface (near-black, e.g. `#111418`) | premium, low-glare | dark themes, media, night use | glare if text too bright; shadows useless |

Whatever the choice, the background value joins the contrast matrix as a first-class pair partner — it is the colour every other colour meets.

### 3.2 Proportion: the 60-30-10 idea and its limits

The 60-30-10 rule — roughly 60% of the visible area in a dominant colour, 30% in a secondary, 10% in an accent — originated in interior design and was later borrowed by web and UI practice (see References; characterised as a rule of thumb, not a measured law). It encodes one solid perceptual idea: *dominance requires area scarcity at the top end* — an accent works only if almost nothing else competes at that intensity.

Its limits are real, though. It describes **perceived area**, not token counts or element counts — ten thin accent lines can read as less area than one big accent panel. In UI work the dominant area is almost always **background/neutral**, so the working interpretation is usually "neutrals dominate, brand hue second, accent scarce"; the brand primary may legitimately be well below 60% of pixels. Data-dense dashboards and editorial layouts routinely violate the split and still succeed, because grouping and layout do proportion work that raw colour area cannot.

Use it as a sanity check, not a formula. If your palette "reads as 60-30-10-ish" it is probably balanced; if the accent is everywhere, it is broken regardless of percentages. Write the intended split into the documentation (section 5.1) so future contributors inherit the intent rather than guessing it.

### 3.3 Palette expansion: ramps and scales

A palette ships as ramps, not as isolated values. The conventional structure in design systems is an 11-step scale labelled 50, 100, 200 … 900, 950, where the middle step is close to the brand colour. The specific step count is a convention, not a standard. What matters is that the ramp is *predictable* (consistent lightness progression), *spaced* (adjacent steps distinguishable on screen), and *anchored* (one step matches the official brand value).

Expansion rules of thumb — conventional starting points, always verified by eye and by contrast check:

- Keep hue constant along a ramp, or drift it deliberately toward warm in shades — a common craft trick to keep dark steps from going muddy.
- Move value evenly; in HSL terms adjust lightness in consistent increments, and reduce saturation slightly at the extreme light steps so tints do not look neon.
- Tints (toward white) serve backgrounds, selected states and charts; shades (toward black) serve hover states, pressed states and text on tinted surfaces.
- Generate ramps programmatically rather than by eye: OKLCH relative-colour syntax or a small script produces uniform scales (see [Colour in code](colour-in-code.md) for the CSS techniques).

Example — an 11-step HSL ramp for a primary blue `#0F6BAE` (computed, contrast measured with the WCAG formula):

| Step | Hex | Contrast on white |
|---|---|---|
| 50 | `#F1F8FE` | 1.07:1 |
| 100 | `#D5EBFB` | 1.23:1 |
| 200 | `#A6D5F7` | 1.56:1 |
| 300 | `#72BDF3` | 2.04:1 |
| 400 | `#43A6EF` | 2.64:1 |
| 500 | `#1490EB` | 3.38:1 |
| 600 | `#0F6BAE` | 5.00:1 |
| 700 | `#0C578D` | 7.60:1 |
| 800 | `#094067` | 10.82:1 |
| 900 | `#062B46` | 14.57:1 |
| 950 | `#041A2A` | 17.70:1 |

The contrast column shows why ramps are accessibility infrastructure. Once built, "text must pass AA" is satisfied by reaching for step 600+ on white, and "AAA" by step 700+, without re-testing each time. Steps below 500 are tint territory — decorative, fills, selected backgrounds — and must never carry text. See [Colour accessibility](colour-accessibility.md) for the ratio requirements.

Spacing deserves one explicit check: adjacent steps must remain distinguishable in actual use, not just in the ramp view. A conventional practice is to keep lightness increments roughly even (the ramp above moves ~6–7 percentage points per step) and to test the two steps that will really sit next to each other — a card on a page background, a border on a card. If two adjacent steps are indistinguishable on the device you ship on, collapse or re-space them; a ramp step that cannot be told apart from its neighbour is inventory, not value.

### 3.4 Semantic colours

Semantic colours encode meaning: success, warning, error, info (the conventional set). Design each one as a mini-palette — a foreground step for text and icons (dark enough to pass contrast on light backgrounds) and a background step for banners and badges — rather than a single hex.

The hue choices (green/amber/red/blue) are conventions, and their conventionality is exactly their value: users read them without instruction. They are also a standing accessibility hazard, since red/green pairs are the classic colour-vision-deficiency trap. Every semantic signal must carry a non-colour cue — icon, label, position — as [Colour accessibility](colour-accessibility.md) requires. De-conflict semantic hues from the accent so an error never shares the accent's colour.

A semantic mini-palette in practice, for the success state: text/icon step `#1B7F3B` (5.07:1 on white — safe for small text), background tint `#EAF6EE` (light enough that any dark text on it still passes), and the pairing rule "icon always accompanies the colour" written into the template. Three lines per state, four states — twelve lines of documentation that eliminate every future "what green do we use for success?" conversation.

### 3.5 Dark and light themes

Dark and light themes are two *derivations* of one palette, not two palettes. Build the light theme first (it constrains text contrast more naturally), then derive dark by role, not by inversion:

- Backgrounds invert their logic: light theme backgrounds are near-white with dark text; dark theme backgrounds are near-black with light text. Avoid pure `#000000`/`#FFFFFF` extremes, which produce glare and haloing (conventional practice; rationale is perceptual).
- Brand hues usually need a lightness shift, not a swap. The primary that passes AA as dark text on white (step 600) will need its lighter sibling (step 300–400) as text on a dark surface, and the deep step 700–900 becomes surface tint.
- Shadows stop working in dark themes; elevation moves to surface lightness steps.
- Semantic colours brighten slightly and lose saturation so they do not smear on dark surfaces.
- The mechanism is always tokens + `prefers-color-scheme` (see [Colour in code](colour-in-code.md)); the palette work here is choosing *which ramp step* serves each role in each theme.

Record both themes' role-to-step mapping in the documentation. A dark theme designed per-element later, without this mapping, is how "the same palette" quietly forks into two inconsistent systems.

### 3.6 Data palettes: categorical, sequential, diverging

Any palette that feeds charts needs three extra scales, and they are built differently from brand ramps:

- **Categorical** — for unordered classes. Requirements: roughly equal perceived lightness across categories (so no class looks "more"), hue separation, and CVD safety with pattern/label redundancy. Limit categories to what readers can hold — around 6–8 distinguishable colours is the conventional ceiling; beyond that, group or repeat with patterns.
- **Sequential** — for ordered magnitude (light = low, dark = high). Built from a single hue ramp (or a white→brand ramp), ordered strictly by value. Never use multiple hues for ordered data — readers cannot tell which direction the order runs.
- **Diverging** — for data with a meaningful midpoint (below/above target). Two hue ramps meeting at a neutral midpoint, with the midpoint tied to the neutral value. Hue choice must respect CVD rules: red/green diverging scales are the classic accessibility failure, so pair with value ordering (dark ends, light middle) that survives greyscale.

Choosing between them is a question about the data, not taste: unordered classes → categorical; single ordered magnitude → sequential; deviation around a reference point → diverging. When a chart mixes the three (categories of ordered sub-scores), nest the scales — categorical hues, sequential lightness within each hue — rather than blending the logics, which produces charts that are simultaneously ambiguous about class and about magnitude.

Document data scales in the same template as brand colours (section 5.1), with each scale's roles and step meanings written down. Charts are where undocumented palettes die first, because every new chart re-asks "which three colours?".

## 4. How it works — the step-by-step method

A repeatable procedure, from brand personality to tested palette:

**Step 0 — Inventory constraints.** Before choosing anything, list what is fixed and what is free: logo colours, an existing product palette this must coexist with, accessibility requirements, output surfaces (web only? print signage? merchandise?). Constraints discovered after Step 6 cost ten times the effort.

**Step 1 — Intent.** Write one sentence of brand personality for the colour system (e.g. "confident, technical, energetic"). Pull hue strategy from [Colour theory](colour-theory.md) and audience meaning from [Colour psychology](colour-psychology.md). If extending a logo, extract and fix its colours now — they are constraints.

**Step 2 — Primary.** Choose the hue and value that carries the brand. Test that at least one nearby ramp step passes WCAG AA (4.5:1) as text on white *and* that white text passes on it as a filled button. A primary that cannot do either will force ugly exceptions later.

**Step 3 — Backgrounds and neutrals.** Choose the background using the strategy table in 3.1, then a neutral ramp biased toward the primary's temperature. Define text steps: near-black for headings/body (e.g. `#111418`), mid-grey for secondary text — verifying each passes the required contrast (see [Colour accessibility](colour-accessibility.md)).

**Step 4 — Accent.** Add one attention colour, typically complementary or split-complementary to the primary. Verify dark text passes on it — light accents usually need dark text (white on the gold `#E8B33D` measures only 1.92:1, while near-black measures 9.07:1). If the accent will sit adjacent to the primary, check 3:1 non-text separation.

**Step 5 — Secondary.** If the brand needs a supporting hue, add it inside the chosen scheme family (analogous neighbour, triadic sibling). Cap the count: a small brand kit runs well on 2 hues + accent + neutrals.

**Step 6 — Semantic set.** Assign success/warning/error/info hues, each with a text-capable foreground step and a background tint step. All four computed here pass 4.5:1 on white: `#1B7F3B` (5.07:1), `#B45309` (5.02:1), `#B42318` (6.57:1), `#175CD3` (5.99:1). De-conflict semantic hues from the accent.

**Step 7 — Expansion.** Generate ramps for primary, secondary, accent and each semantic hue (see 3.3). Record which step of each ramp serves which sub-role (button, border, background, text). If charts are in scope, build the data scales of 3.6 in the same pass.

**Step 8 — Proportion plan.** Map roles onto the 60-30-10 idea for your context (section 3.2): name the dominant surface colour, the secondary field colour, and the scarce accent.

**Step 9 — Documentation.** Write the palette down in the template below — roles, exact values, usage rules, contrast notes. Undocumented is undelivered.

**Step 10 — Evaluation.** Run the testing procedure (section 5.3): contrast matrix, colour-vision simulation, on-brand check, real-layout review. Fix at ramp level (regenerate), not by sprinkling exceptions.

Two process notes on the sequence. The order matters more than the individual steps: backgrounds before accent, because contrast against the ground constrains what an accent can be; ramps before themes, because themes are re-assignments of ramp steps. And the loop is not linear in practice — evaluation routinely sends you back to Step 2 with evidence, which is fine; what is not fine is quietly keeping the failing colour and lowering the standard instead.

## 5. Practical application

### 5.1 Documentation template

```markdown
## Palette: <project/event name>  (v1.0, <date>)

### Brand hues
| Role        | Token            | Hex      | Usage rules                          | Contrast notes                     |
|-------------|------------------|----------|--------------------------------------|------------------------------------|
| Primary     | blue-600         | #0F6BAE  | Primary buttons, links, headers      | 5.00:1 on white; white text passes AA on it |
| Primary dark| blue-700         | #0C578D  | Hover/pressed, text on tint-50       | 7.60:1 on white (AAA)              |
| Accent      | gold-500         | #E8B33D  | Highlights, badges; max ~10% of area | Near-black text on it: 9.07:1; never white text |
| Secondary   | teal-600         | #0E7C86  | Illustration, secondary surfaces     | 4.95:1 on white                    |

### Neutrals & backgrounds
| Role        | Token      | Hex      | Usage                              |
|-------------|------------|----------|------------------------------------|
| Background  | bg-page    | #FAFAF8  | Page background (light theme)      |
| Surface     | bg-card    | #FFFFFF  | Cards, modals                      |
| Text        | text-900   | #111418  | Headings, body                     |
| Text muted  | text-600   | #4B5563  | Secondary text (7.56:1 on white)   |
| Border      | border-300 | #D4D8DD  | Dividers, card borders             |

### Semantic
| Meaning | Text/icon | Background tint | Non-colour cue           |
|---------|-----------|-----------------|--------------------------|
| Success | #1B7F3B   | #EAF6EE         | Check icon + label       |
| Warning | #B45309   | #FDF3E3         | Triangle icon + label    |
| Error   | #B42318   | #FDECEA         | Alert icon + label       |
| Info    | #175CD3   | #EAF1FB         | Info icon + label        |

### Theme notes
Light is default. Dark theme: backgrounds #111418/#1A1F26, text #E8EAED
(13.74:1 on #1A1F26), primary as text = blue-300 #72BDF3 (9.05:1 on #111418).

### Prohibitions
- Never white text on gold accent. Never red/green pair as the only distinction.
- Accent never used for body text.
```

The template's value is the *columns*: every colour carries usage rules and measured contrast, so downstream agents never re-derive them. Keep the prohibitions section — undocumented exceptions are how palettes decay.

Naming follows the roles, not the hues. `--color-action` survives a rebrand from blue to green; `--blue-600` as a component-facing name does not. The convention that scales: primitives named by hue-and-step (`blue-600`), semantic aliases named by role (`color-action`, `text-muted`), components consuming only aliases. The full naming architecture is specified in [Design tokens](../design-systems/design-tokens.md).

At handoff, the template maps directly onto implementation: tokens as CSS custom properties and a token JSON file ([Colour in code](colour-in-code.md), [Design tokens](../design-systems/design-tokens.md)), swatch styles in design tools named by token, and the print specification (if any) attached per critical colour. One source of truth, four outputs.

### 5.2 Worked example — extending an event logo

Given a conference logo: blue `#0F6BAE` wordmark with a gold `#E8B33D` star. The two logo colours are near-complementary (cool blue, warm gold) — so the palette follows complementary logic instead of inventing a new scheme:

- Primary: blue ramp anchored at `#0F6BAE` (600), ramp as in 3.3; blue-50 for tinted surfaces, blue-900 for text-on-blue-50.
- Accent: the logo gold, restricted to highlights and badges, dark text only.
- Neutrals: cool greys (`#FAFAF8` background, `#111418` text, `#D4D8DD` borders).
- Semantic: standard hues from the template (none collide with the gold accent).
- Proportion: neutrals dominate, blue second, gold scarce — the "60-30-10" reading is "neutral 60+, blue 30, gold <10".

Everything above is checkable from the tables; the kit now survives new artefacts (badges, signage, slides) without new colour decisions. Note what the procedure did *not* do: it did not add a third brand hue, and it did not move the logo colours — both are the most common well-meant vandalisms of a logo system.

### 5.3 Testing procedure

1. **Contrast matrix.** For every text colour × background pair you actually use, compute the WCAG ratio (script or checker) and mark AA/AAA/fail. Verify at least: body text, muted text, text-on-primary, text-on-accent, semantic text on its tint.
2. **Colour-independence audit.** View every state/status in greyscale: if two states become indistinguishable, add icon/label/pattern, not more hue.
3. **Colour-vision simulation.** Render key screens through deuteranopia/protanopia simulation (tools listed in [Accessibility testing](../accessibility/accessibility-testing.md)). Semantic and chart colours are the usual failures.
4. **On-brand check.** Compare palette against logo colours side by side; hues must feel like the same family (temperature bias intact).
5. **Real-layout review.** Apply to actual screens at 60-30-10 intuition level — is the accent scarce? is hierarchy legible? Adjust at ramp/token level and re-run steps 1–3.
6. **Both themes, every time.** Run steps 1–5 per theme if a dark theme ships; a light-only pass misses every dark-theme failure by construction.

A useful definition of done: a new designer or agent can build a complete new page — including a form with validation errors and a chart with three series — using only the documented tokens, without inventing a colour, and the result passes the contrast matrix unchanged. If they had to improvise, a role or ramp step is missing from the documentation.

Full WCAG framework and tool workflows live in [WCAG fundamentals](../accessibility/wcag-fundamentals.md) and [Accessibility testing](../accessibility/accessibility-testing.md); this section is the palette-construction loop only.

## 6. Decision framework

This table converts the common "do we need X?" questions into concrete commitments. Answer the questions in order for a new project; the first "yes" usually reshapes the steps that follow:

| Question | If yes | If no |
|---|---|---|
| Are logo colours fixed? | Treat as constraints; build scheme around them (5.2) | Choose hue strategy from personality first |
| Does the product have dense data UI? | Widen neutral ramp; restrain accent; extra chart ramp (3.6) | Standard 6-role kit suffices |
| Is a dark theme required now? | Derive dark alongside light (3.5); test both | Still record dark derivations in docs for later |
| More than 2 brand hues needed? | Add triadic/tetradic siblings with area control | Stay at primary + accent |
| A colour keeps failing contrast? | Move to the next ramp step; never tweak the hex ad hoc | — |
| Print collateral in scope? | Approve a CMYK print spec per critical colour at handoff | Ship HEX/sRGB only |
| Charts planned? | Document categorical/sequential/diverging scales now (3.6) | — |
| Long-form reading surfaces? | Off-white ground + AAA body text target | Standard AA targets |
| Multiple sub-brands or event years expected? | Define what is fixed (logo hues) vs variable (themes) in the documentation | — |
| Community or third-party contributors? | Publish prohibitions and naming rules early; they are the first thing violated | — |
| Palette will outlive the current designers/agents? | Record scheme rationale and association rules, not just hexes | — |

## 7. Examples

Three archetypal palettes (values are constructed examples; contrast figures computed):

- **Technical event (worked above):** blue `#0F6BAE` + gold `#E8B33D` accent, cool neutrals, standard semantics. Complementary logic, scarce accent. Measured: primary 5.62:1 on white in both directions; accent text-safe only with near-black text (9.07:1).
- **Calm wellbeing service:** sage green primary `#3E7C59` (4.96:1 on white — passes AA with a slim margin), analogous secondary `#6FA287` (2.92:1 — decorative and fill roles only, never text), warm off-white `#F8F7F3`, brown-grey text `#2B2B27` (13.26:1 on the ground). Hierarchy carried by value; semantics stay conventional green/red.
- **Editorial culture magazine:** monochromatic warm red ramp anchored at `#8C2F39` (7.57:1 on the cream ground `#FBF6EF` — AAA), near-black `#141414` text (17.13:1), no accent — identity comes from the ramp's texture. Demonstrates the value-led hierarchy described in [Colour theory](colour-theory.md) section 4.4.

Each archetype shows a different balance of the same six roles. The event palette spends its contrast budget on the accent, the wellbeing palette on text comfort, the editorial palette on the brand ramp itself.

A fourth archetype worth naming — **dark-first product** (media, developer tools): near-black grounds `#111418`/`#1A1F26`, text `#E8EAED` (13.74:1 on `#1A1F26`), the brand hue's light step as action (9.05:1), deep steps demoted to surface tint. The lesson generalises: in dark themes the ramp's *ordering* inverts, its hue identity does not.

## 8. Common mistakes

Each of these is a real decay pattern with a documented fix — most palettes fail through accumulation of small deviations, not one bad decision:

- **Palette-as-collection:** colours added per request ("we need a purple now") with no role, no ramp, no documentation. Fix: every addition enters through the role table.
- **Accent inflation:** the attention colour appears in cards, titles and borders until nothing stands out. Fix: enforce scarcity in documentation ("accent = highlights and badges only").
- **Ramps generated by eye:** steps uneven, adjacent steps indistinguishable, official brand value lost. Fix: generate programmatically, anchor one step to the brand value.
- **Semantic hues colliding with brand hues:** error red used as a decorative brand red confuses meaning; keep semantic hues visually distinct or clearly darker/lighter.
- **Dark theme by inversion:** pure black/white swap produces glare, broken shadows and weird hue shifts. Fix: derive by role with lightness-shifted brand hues.
- **Skipping the testing loop** because "the colours look fine" — until the first contrast audit finds body text at 2.97:1. Fix: run the matrix before handoff; it costs minutes.
- **Documenting hex without usage rules.** A hex alone answers nothing; the usage column is the actual specification.
- **Building brand ramps but not chart scales.** The first new chart then invents three colours on the spot; add categorical/sequential scales in the same documentation pass (3.6).
- **Treating the secondary as a smaller primary.** A secondary hue appearing at 40% area with its own full-saturation treatments competes with the brand hue; secondaries usually work better slightly toned down.
- **Letting the accent into the semantic layer.** When the accent doubles as the error colour (or the success colour), attention and meaning fuse; the accent then fires on every error banner and the semantic set loses its distinctness.
- **Inheriting an old palette without its contract.** Taking the hexes from a previous project while ignoring its role rules imports the colours and loses the system — re-read the documentation or rebuild the roles before reusing anything.

## 9. Evaluation checklist

- [ ] Every colour has a role, a token name, a hex and a usage rule.
- [ ] Primary passes AA both ways (text on white; white text on primary).
- [ ] Accent is scarce in real layouts and supports sufficient text contrast on it.
- [ ] Neutrals are deliberately temperature-biased, not default pure grey.
- [ ] Ramps are anchored to brand values, evenly spaced, with contrast recorded per step.
- [ ] Semantic colours have text + background steps and a non-colour cue each.
- [ ] Dark theme derived by role; both themes pass the contrast matrix.
- [ ] 60-30-10 sanity check passes (accent reads scarce; neutrals dominate).
- [ ] Chart scales (if applicable) documented with the same rigour as brand ramps.
- [ ] Greyscale and CVD simulation reviewed.
- [ ] A stranger can build a compliant page using only the documentation (definition of done, 5.3).
- [ ] Scheme rationale and prohibitions are recorded, not just hexes.
- [ ] Both themes' role-to-step mappings are in the documentation, not in someone's memory.

## 10. Related topics

- [Colour theory](colour-theory.md) — schemes, ramps' underlying dimensions, tint/shade/tone.
- [Colour accessibility](colour-accessibility.md) — the ratio targets and colour-independence rules used here.
- [Colour psychology](colour-psychology.md) — reading audience associations before Step 1.
- [Colour in code](colour-in-code.md) — tokens, CSS custom properties, ramp generation, theming.
- [Design tokens](../design-systems/design-tokens.md) — token architecture and naming layers.
- [Brand personality](../branding/brand-personality.md) — the intent input for Step 1.
- [Grid systems](../layout/grid-systems.md) — layout proportion working alongside colour proportion.
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — the normative framework behind the contrast targets.
- [Accessibility testing](../accessibility/accessibility-testing.md) — full tool-based testing procedures.

## 11. References

- The 60-30-10 rule's interior-design origin and UI adoption: "The 60–30-10 rule of colour", Medium Design Bootcamp. https://medium.com/design-bootcamp/the-60-30-10-rule-of-colour-c2748068b8aa [search-verified 2026-11-23]
- The documentation template, worked example and step-by-step method are the authors' synthesis of the sources above and standard design-system practice; the template is offered as a starting point to adapt, not a standard. [synthesis]
- WCAG contrast thresholds used throughout (4.5:1 / 3:1 / 7:1, non-text 3:1): W3C WAI Understanding docs listed in [Colour accessibility](colour-accessibility.md). [accessed 2026-11-23]
- MDN Web Docs, "color_value/oklch" — perceptually uniform ramp generation basis. https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/oklch [accessed 2026-11-23]
- Ramp tables, contrast figures and the worked example palette were computed with HSL mixing and the WCAG relative-luminance formula (script in the authors' workspace). Semantic hexes are constructed examples chosen to pass AA on white. [synthesis]
- Itten, J., *The Art of Color* — the tint/shade/tone and proportion teaching tradition underlying ramps. [canonical]
