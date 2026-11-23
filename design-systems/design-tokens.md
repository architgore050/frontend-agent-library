# Design Tokens

## 1. What is it?

A design token is the smallest named design decision: a name paired with a value, stored in a platform-neutral file so that the same decision can be applied everywhere design meets code. Typical examples are `color.text.primary = #1f1f1f`, `spacing.md = 16px` and `radius.card = 8px`. The name carries the *intent* ("this is the primary text colour"), while the value carries the *implementation* (a specific hex code) — and the two are deliberately kept apart so either can change without breaking the other.

Atlassian's design-system documentation describes tokens as "the single source of truth to name and store design decisions" — a formulation worth memorising because it captures both halves: tokens are a *naming system* and a *storage system* at the same time. A token file is therefore not a stylesheet, a theme or a library; it is a catalogue of decisions that other artefacts (CSS, iOS, Android, Figma styles) are generated from.

Tokens sit at the bottom of the design-system stack: foundations define principles, tokens encode the numeric decisions, components consume the tokens, and documentation explains the whole. When an agent builds or audits a UI, the token layer is usually the right place to start reading, because it answers most "why does this look like this?" questions in one file.

## 2. Why does it matter?

**Consistency becomes mechanical.** Without tokens, every colour and spacing value is retyped by hand in dozens of files, and drift is inevitable. With tokens, there is exactly one definition of `color.text.muted`, and every consumer references it. Consistency stops depending on memory and starts depending on a build.

**Change becomes cheap and safe.** Rebranding from one accent colour to another is a one-line edit plus a rebuild, not a search-and-replace across hundreds of files. Because the token name stays stable (`color.action.primary`), nothing downstream needs to be renamed — the *meaning* is unchanged even though the *value* changed.

**Theming becomes a layer, not a fork.** Light/dark modes, brand variants and density variants are handled by swapping what the semantic token names point to, not by duplicating every component. This is why semantic tiers (see section 4) exist at all.

**Design and code finally speak the same language.** A designer saying "use the muted text colour" and a developer writing `var(--color-text-muted)` refer to the same decision. The token file is the shared contract, reviewable in pull requests like any other code.

**Agents benefit directly.** For an AI agent generating or refactoring UI, a token file is the compact, machine-readable context that answers "what values am I allowed to use?" — turning an open-ended styling problem into a constrained selection problem.

## 3. Core principles

1. **Encode decisions, not pixels.** A token should answer "what is this for?", not merely "what number is this?". `space.150 = 12px` is weak; `spacing.control.gap = 12px` ("gap between an icon and its label in a control") is strong because the name survives a reorganisation of the scale.
2. **Separate what a value is from what it means.** Primitive tokens hold raw values; semantic tokens hold purpose. Never let a purpose ("danger") leak into a primitive ("red-500"), and never let a raw value leak into a semantic name ("blue-button").
3. **Platform-neutral source, platform-specific output.** The token file is written once, in a format such as the DTCG JSON format (section 4), and transformed into CSS custom properties, Swift, Kotlin, XML or design-tool styles by a build step. Nobody edits the generated output by hand.
4. **Reference, never repeat.** A semantic token should point at a primitive (`color.text.danger = {color.red.600}`), and a component token should point at a semantic. Duplication of values across tiers defeats the entire model.
5. **Names are the API.** The token name is what every consumer reads and writes, so it changes more slowly and more reluctantly than the values behind it. Naming is therefore an interface-design exercise, not a labelling exercise.
6. **Constrain the palette of allowed values.** A token system only pays off if it is finite. An endless tail of one-off tokens (`spacing.7.half`, `blue.really.dark`) recreates the chaos tokens were meant to remove.

## 4. How it works

### 4.1 Token categories

A mature system tokenises these categories (the Atlassian foundations page groups its styles in a comparable set: colour, typography, spacing, grid, elevation, border, radius, iconography, motion):

| Category | Token purpose | Example values |
| --- | --- | --- |
| Colour | Text, backgrounds, borders, accents, states | `#0b57d0`, `rgba(0,0,0,0.6)` |
| Spacing | Gaps, padding, layout rhythm | `4px`, `8px`, `16px` steps |
| Typography | Font family, size, weight, line height, letter spacing | `16px / 24px / 400`, composite style objects |
| Radius | Corner rounding per component class | `4px` (inputs), `8px` (cards), `999px` (pills) |
| Elevation / shadow | Depth cues for layered surfaces | `0 1px 2px rgba(0,0,0,0.3)` |
| Border | Width and style | `1px solid` |
| Motion | Durations and easing curves | `150ms`, `cubic-bezier(0.4, 0, 0.2, 1)` |
| Opacity | Disabled, scrim, overlay levels | `0.38`, `0.32` |
| Z-index | Stacking order bands | `100` (dropdown), `1000` (modal) |
| Breakpoints | Responsive thresholds | `480px`, `768px`, `1024px` |

Spacing, typography and colour carry the most decisions in practice; see [Spacing scales](../layout/grid-systems.md), [Web typography](../typography/web-typography.md) and [Colour in code](../colour/colour-in-code.md) for the underlying craft.

### 4.2 Token tiers

Most systems settle on three tiers. The layering is what turns a bag of constants into a themable system:

1. **Primitive (also called global or core) tokens** — the raw inventory: `color.blue.500 = #2e6fe0`, `spacing.400 = 16px`. They describe the *palette and scale*, never intent. If a primitive is referenced directly by a component, that is a smell: it bypasses the meaning layer.
2. **Semantic (also called alias) tokens** — intent-bearing names that reference primitives: `color.text.primary = {color.gray.900}`, `color.action.primary = {color.blue.600}`, `spacing.card.padding = {spacing.400}`. These are the tokens components are supposed to consume, and the tokens themes override.
3. **Component tokens** — decisions scoped to one component, referencing semantic tokens: `button.primary.background = {color.action.primary}`. They exist so a component can be restyled wholesale without disturbing siblings that share the same semantic token.

The tier idea is not unique to any one system: Material Design 3 popularised a reference → system → component layering (its `md.sys.color.*` style names are the widely cited example), and several large product token systems use comparable alias layers. The three names above are the common professional vocabulary; treat exact tier labels as conventional rather than standardised.

### 4.3 Naming grammar

A workable convention composes names from **category → property → variant → state**, in that order, so sorting and filtering group related tokens naturally:

```text
color.text.danger            category: colour · property: text · variant: danger
color.background.surface     category: colour · property: background · variant: surface
spacing.inset.md             category: spacing · property: inset · variant: md
font.body.lg.size            category: font · role: body · variant: lg · property: size
radius.card                  category: radius · property: card
```

Rules that hold up in practice (professional convention, not law):

- Use lower-case, hyphen- or dot-separated names consistently; pick one separator per platform and stick to it.
- Never encode a raw value in the name (`color.blue.500` is fine because it names the *primitive slot*, but `color.blue.2e6fe0` is not).
- Prefer intent words (`danger`, `action`, `surface`, `muted`) over visual words (`red`, `bright`, `dark`) anywhere above the primitive tier.
- Keep depth shallow — more than about four path segments usually signals the tier boundaries have blurred.
- Design for alphabetical order: `color.background.*`, `color.border.*`, `color.text.*` groups itself once sorted.

### 4.4 File formats: the DTCG design-tokens format

The Design Tokens Community Group (DTCG), operating under the W3C, publishes a format draft for exchanging tokens between tools. The draft is formally a **Draft Community Group Report, not a W3C Standard** — it is explicitly marked as a preview that tools are not yet expected to implement in full — but its vocabulary has become the de facto reference for token files, and tools such as Style Dictionary advertise DTCG forward-compatibility. Key facts from the draft:

- A token file is **JSON**; the recommended media type is `application/design-tokens+json` and the recommended file extensions are `.tokens` or `.tokens.json`.
- **"An object with a `$value` property is a token"**; a group is any JSON object without `$value`. A node cannot be both at once.
- Token properties: `$value` (required), `$type`, `$description`, `$deprecated`, `$extensions` (vendor data under reverse-domain keys such as `org.example.tool-a`).
- Groups can carry `$type` (inherited by child tokens), `$description`, `$extends` (deep-merge inheritance from another group) and `$extensions`.
- Names are case-sensitive JSON strings that **must not begin with `$`** and **must not contain `{`, `}`, or `.`** (both are reserved by reference syntax).
- Tools must not guess a token's type from its value; an explicit `$type` or inherited group `$type` is required.
- Aliases use curly braces: `{color.blue.500}` resolves to another token's `$value`. JSON Pointer (`$ref`, e.g. `#/colors/blue/$value/components/0`) reaches arbitrary sub-properties. Circular references are errors that must be detected.

Representative DTCG syntax (structure as shown in the draft):

```json
{
  "color": {
    "$type": "color",
    "blue": {
      "500": { "$value": { "colorSpace": "srgb", "components": [0.18, 0.43, 0.88] } },
      "700": { "$value": { "colorSpace": "srgb", "components": [0.10, 0.27, 0.60] } }
    }
  },
  "spacing": {
    "$type": "dimension",
    "400": { "$value": { "value": 16, "unit": "px" } }
  },
  "font": {
    "body": {
      "$type": "typography",
      "$value": {
        "fontFamily": "Inter",
        "fontSize": { "value": 16, "unit": "px" },
        "fontWeight": 400,
        "lineHeight": 1.5
      }
    }
  }
}
```

### 4.5 The transformation pipeline

Source tokens are rarely used directly by an application; a build step converts them into per-platform artefacts. The best-known tool is **Style Dictionary**, originally created by Danny Banks at Amazon, which describes itself as exporting tokens "to any platform — iOS, Android, CSS, JS, HTML, sketch files" and is documented on GitHub as "a build system for creating cross-platform styles". A pipeline has three stages:

1. **Parse** the source JSON (resolving aliases and references into a resolved tree).
2. **Transform** values per platform — e.g. convert a `dimension` token to `rem` for CSS web output, to `dp` for Android, to `pt` for iOS.
3. **Format** the output — CSS custom properties, SCSS variables, Swift constants, Kotlin objects, or a design-tool theme file.

For the web, the canonical target is CSS custom properties, which inherit through the DOM and can therefore be re-declared under a theme scope without any build-time trickery:

```css
:root {
  --color-action-primary: #2e6fe0;
  --color-text-primary: #1f1f1f;
}

[data-theme="dark"] {
  --color-action-primary: #7aa5f7;
  --color-text-primary: #e8e8e8;
}
```

### 4.6 Theming through the semantic layer

Because components consume semantic names, a theme is nothing more than a different set of *resolutions* for those names. A dark theme re-points `color.text.primary` from `color.gray.900` to `color.gray.100`; no component file changes. The same mechanism serves brand variants (different accent per product), density variants (compact spacing), and platform tuning. The practical consequence is a division of labour: primitives are the stable inventory, semantic tokens are the *contract*, and themes are interchangeable *implementations* of that contract.

## 5. Practical application: a worked example

This example walks the full chain from a raw brand palette to component code, using DTCG-style JSON and a CSS output. It is deliberately small enough to reproduce end to end.

**Step 1 — raw palette.** The brand team hands over: primary accent `#2e6fe0`, a darker press state `#1c4db3`, neutral text `#1f1f1f`, secondary text `#5f6368`, surface white `#ffffff`, danger `#c5221f`.

**Step 2 — primitive tokens** (`tokens/colour.primitives.json`). Values only, no intent. The scale anticipates states the brand palette did not mention (hover, subtle) so semantic layers never need raw values:

```json
{
  "color": {
    "$type": "color",
    "blue": {
      "500": { "$value": { "colorSpace": "srgb", "components": [0.18, 0.435, 0.878] } },
      "600": { "$value": { "colorSpace": "srgb", "components": [0.11, 0.302, 0.702] } }
    },
    "gray": {
      "900": { "$value": { "colorSpace": "srgb", "components": [0.122, 0.122, 0.122] } },
      "600": { "$value": { "colorSpace": "srgb", "components": [0.373, 0.388, 0.408] } },
      "0":    { "$value": { "colorSpace": "srgb", "components": [1, 1, 1] } }
    },
    "red": {
      "600": { "$value": { "colorSpace": "srgb", "components": [0.773, 0.133, 0.122] } }
    }
  }
}
```

**Step 3 — semantic tokens** (`tokens/colour.semantic.json`). Intent, referencing primitives via aliases:

```json
{
  "color": {
    "action": {
      "primary":       { "$type": "color", "$value": "{color.blue.500}" },
      "primary-press": { "$type": "color", "$value": "{color.blue.600}" }
    },
    "text": {
      "primary":   { "$type": "color", "$value": "{color.gray.900}" },
      "secondary": { "$type": "color", "$value": "{color.gray.600}" }
    },
    "surface": {
      "default":   { "$type": "color", "$value": "{color.gray.0}" }
    },
    "danger": {
      "default":   { "$type": "color", "$value": "{color.red.600}" }
    }
  }
}
```

**Step 4 — component tokens** (optional, only where a component owns a decision):

```json
{
  "button": {
    "primary": {
      "background":        { "$type": "color", "$value": "{color.action.primary}" },
      "background-press":  { "$type": "color", "$value": "{color.action.primary-press}" },
      "foreground":        { "$type": "color", "$value": "{color.gray.0}" },
      "radius":            { "$type": "dimension", "$value": { "value": 8, "unit": "px" } }
    }
  }
}
```

**Step 5 — transform to CSS** (pipeline output, not hand-written):

```css
:root {
  --color-action-primary: #2e6fe0;
  --color-action-primary-press: #1c4db3;
  --color-text-primary: #1f1f1f;
  --color-text-secondary: #5f6368;
  --color-surface-default: #ffffff;
  --color-danger-default: #c5221f;
  --button-primary-radius: 8px;
}
```

**Step 6 — component consumption.** The component references semantic (or its own component) tokens only:

```css
.button-primary {
  background: var(--color-action-primary);
  color: var(--color-text-primary-inverse, #ffffff);
  border-radius: var(--button-primary-radius);
}
.button-primary:active {
  background: var(--color-action-primary-press);
}
```

**Step 7 — theme by re-pointing.** A dark theme swaps resolutions in one scope block; the component above is untouched:

```css
[data-theme="dark"] {
  --color-action-primary: #7aa5f7;
  --color-action-primary-press: #a3c1fa;
  --color-text-primary: #e8e8e8;
  --color-text-secondary: #9aa0a6;
  --color-surface-default: #121212;
}
```

If a later rebrand changes the accent to green, only `color.blue.*` values (and their names, kept for stability) are edited at the primitive tier; every semantic token, component token and theme continues to resolve correctly.

## 6. Decision framework

**How many tiers do I need?**
- One tier (flat list) suits a single-page tool or prototype: cheap, but theming is impossible without duplication.
- Two tiers (primitive + semantic) is the default for product teams; add component tokens only when a component needs its own restyling surface. Three tiers is the professional standard; four or more is almost always over-engineering.
- Skip the semantic tier only for genuinely one-off artefacts (a poster, a single campaign page) where no theming or reuse is expected.

**When should something become a token?**
- Tokenise when the value is used in more than one place, is part of the brand, or must survive theming.
- Do not tokenise layout one-offs ("this hero is offset 37px") — those belong in the local stylesheet. A token that exists to name a value used exactly once is documentation overhead, not a system.

**Which format should the source file use?**
- For new multi-platform systems, DTCG-style JSON is the safest choice: it is tool-neutral, and major pipelines (including Style Dictionary) already handle it.
- For a small web-only system, a plain JSON or JS/TS module transformed to CSS custom properties is enough; adopt the full DTCG surface (`$type`, `$extensions`) only when your tooling actually consumes it.

**Which values should be themable?**
- Anything users perceive under different conditions: colour, elevation, radii in some systems, motion duration (reduced-motion). Fixed dimensions (a 1px hairline) usually stay primitive-only.

**Naming review questions:** Can a new designer predict what `color.border.focus` looks like? Does the name survive a palette change? Does sorting the file group related tokens? Would two people independently invent the same name for the same decision? If any answer is no, revise before the name is consumed anywhere.

## 7. Examples

- **Atlassian Design System** structures its foundations around tokens plus styles (colour, typography, spacing, grid, elevation, border, radius, iconography, motion), documenting tokens separately for design-tool use, code use and migration — a useful model for how token documentation splits by audience.
- **GOV.UK Design System** encodes its decisions in styles and accessible components rather than publishing a DTCG file; its Button guidance demonstrates the *decision* side of tokens (e.g. inverse buttons on dark backgrounds must meet the 4.5:1 contrast ratio of WCAG 2.2 criterion 1.4.3) — a reminder that a token value is ultimately an accessibility decision, not just a brand one.
- **Material Design 3** is the canonical reference for tiered tokens at scale, with reference → system → component layers and `md.sys.*` / `md.comp.*` naming; its published token list is one of the largest public examples.
- **Style Dictionary** is the canonical open-source pipeline example: one JSON source transformed to CSS, SCSS, JS, iOS and Android outputs, with DTCG forward-compatibility demonstrated by its own conversion demo.

## 8. Common mistakes

- **Semantic names that encode appearance.** `color.text.blue` breaks the day the decision becomes green. Appearance belongs in primitive names only.
- **Components consuming primitives directly.** Every direct `{color.blue.500}` reference in a component is a theming leak; route it through a semantic token.
- **Too many one-off tokens.** A scale with `spacing.87` signals an unmanaged file. Keep scales small and gap-based (e.g. a 4px base grid with named steps) so decisions stay comparable.
- **Editing generated output.** Hand-edits to generated CSS variables are silently lost on the next build. Treat generated files as build artefacts, committed only if your pipeline expects it, and never edited.
- **Circular or dangling references.** Two semantic tokens that alias each other, or an alias pointing at a deleted primitive, must fail the build — wire reference validation into CI rather than hoping tooling catches it at runtime.
- **Values without units or types.** Untyped `"$value": 16` for spacing forces every consumer to guess px vs rem; the DTCG draft forbids type-guessing for good reason. Always declare `$type` (or inherit it from a group).
- **Token sprawl across repositories.** When each service forks its own copy, "single source of truth" is gone. Keep one source package, version it, and distribute via the package registry.
- **Documenting values instead of decisions.** A token page that lists hex codes without usage rules ("use `color.text.secondary` for supporting copy") teaches nobody anything the file does not already say.

## 9. Evaluation checklist

- [ ] Every colour, spacing, radius, elevation and motion value in components resolves to a token, not a raw literal.
- [ ] Primitive tokens contain no intent words; semantic tokens contain no raw values.
- [ ] Semantic tokens reference primitives; no duplicated values across tiers.
- [ ] Names follow one consistent grammar (category–property–variant) and sort meaningfully.
- [ ] A theme (dark mode or a brand variant) can be applied by re-declaring semantic tokens only, with no component edits.
- [ ] The token source file lives in one versioned place, with changes reviewed and changelogged.
- [ ] A build step transforms tokens to each target platform; nobody edits generated files.
- [ ] Token names, values and usage rules are documented, including when *not* to use each token.
- [ ] Reference validation (dangling aliases, cycles, missing types) runs automatically.
- [ ] Contrast-checked pairings (text on surface, action on surface) are verified, not assumed — e.g. body text meets the 4.5:1 ratio of WCAG 2.2 criterion 1.4.3.

## 10. Related topics

- [Colour in code](../colour/colour-in-code.md) — implementing palettes, colour spaces and conversion details behind colour tokens.
- [Web typography](../typography/web-typography.md) — font sizing, line height and fluid type decisions that typography tokens encode.
- [Grid systems](../layout/grid-systems.md) — the spacing and grid scales that spacing tokens formalise.
- [Component systems](component-systems.md) — how components consume tokens and expose variants.
- [Visual consistency](visual-consistency.md) — consistency as applied rules, of which tokens are the mechanism.
- [Documentation](documentation.md) — how token usage guidelines are written up.
- [Governance](governance.md) — who may add, change or deprecate tokens, and how that is decided.
- [Design system audit](../evaluation/design-system-audit.md) — evaluating a live system, including its token layer.
- [Colour theory](../colour/colour-theory.md) — the perceptual reasoning behind building a primitive palette.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — the broader engineering context tokens plug into.

## 11. References

- Design Tokens Community Group (W3C), *Design Tokens Format Module 2025.10* — Draft Community Group Report. https://www.designtokens.org/TR/drafts/format/ [accessed 2026-11-23]. Source for the format's JSON structure, `$value`/`$type`/`$description`/`$extensions`/`$extends` properties, naming restrictions, alias and `$ref` syntax, and its status as a draft (not a W3C Standard).
- Style Dictionary — project homepage. https://styledictionary.com [accessed 2026-11-23]. Source for the cross-platform export claim and DTCG forward-compatibility.
- Style Dictionary — GitHub repository. https://github.com/style-dictionary/style-dictionary [search-verified 2026-11-23]. "A build system for creating cross-platform styles."
- Didoo (Davido), *How to manage your Design Tokens with Style Dictionary*. https://didoo.medium.com/how-to-manage-your-design-tokens-with-style-dictionary-98c795b938aa [search-verified 2026-11-23]. Origin attribution: developed by Danny Banks at Amazon.
- Atlassian Design System, *Foundations*. https://atlassian.design/foundations/ [accessed 2026-11-23]. Token definition ("single source of truth to name and store design decisions") and the foundations topic list.
- Atlassian Design System, *Design tokens*. https://atlassian.design/foundations/tokens [accessed 2026-11-23]. Documentation split (explained / in code / in design / token list / migration).
- GOV.UK Design System. https://design-system.service.gov.uk/ [accessed 2026-11-23]. Styles / Components / Patterns organisation, maintained by the Government Digital Service.
- GOV.UK Design System, *Button component*. https://design-system.service.gov.uk/components/button/ [accessed 2026-11-23]. Variant guidance, disabled-state caution, 4.5:1 contrast requirement (WCAG 2.2, criterion 1.4.3).
- Material Design 3, *Design tokens*. https://m3.material.io/foundations/design-tokens [accessed 2026-11-23; page body did not render in fetch]. The reference → system → component tiering and `md.sys.color.*` naming in section 4.2 are attributed from general professional knowledge of this system [canonical], not from the fetched page text.
