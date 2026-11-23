# Visual Consistency

## 1. What is it?

Visual consistency means the *same rules are applied everywhere*, not that every screen looks identical. Two surfaces are consistent when the same decision (a token, a component, a spacing rule) produces the same visual outcome in both; they are inconsistent when the same situation is treated differently for no reason — one form uses 16px label spacing and another uses 12px, one product's danger colour is red and another's is orange.

The distinction matters because consistency is routinely misread as uniformity. Copying the same pixels everywhere is brittle: it cannot survive dark mode, density variants or new platforms. Applying the same *rules* everywhere is robust: the rule "muted text uses `color.text.secondary`" produces different pixels in light and dark themes yet remains perfectly consistent. A design system is, at root, a machine for enforcing rule-level consistency; see [Design tokens](design-tokens.md) for the mechanism and [Component systems](component-systems.md) for the behavioural half.

The distinction also sets the boundary with its neighbouring file: [Visual identity](../branding/visual-identity.md) governs which brand assets exist and how they look; consistency governs how those assets and the system's decisions are *applied* everywhere. A brand refresh changes tokens; consistency work distributes them.

Consistency also has a temporal dimension: a product is consistent over time when its decisions change only through deliberate, documented revisions — not through accretion of small undocumented drift. That is why this file treats drift detection as a first-class practice rather than an optional nicety.

A final scope note: consistency is a property of *systems of decisions*, so this file assumes some decision layer already exists — tokens, components, guidance. If none exists yet, build the smallest viable one first ([Design tokens](design-tokens.md) and [Component systems](component-systems.md) cover the mechanics); auditing consistency before any decisions are written down measures nothing and produces no fixes.

## 2. Why does it matter?

**Perceptual fluency.** Users learn interface patterns once and reuse that learning everywhere. When the same component behaves identically across screens, recognition replaces re-reading: attention goes to content and tasks, not to decoding new controls. When patterns shift subtly between screens, users must re-verify each time, which raises error rates and slows tasks.

**Trust and perceived quality.** Small inconsistencies read as carelessness. Users cannot name the reason (spacing rhythm, mismatched radii), but they reliably perceive the effect: "this feels rough" or "this looks unfinished". Perceived quality tracks rule-following more closely than it tracks decoration — which is also why consistency work is best argued in terms of outcomes (task success, error rates, perceived polish) rather than in terms of tidiness.

**Team scaling.** Consistency is what lets two designers or two engineers produce compatible output without constant coordination. The rules substitute for conversation; this is why consistency becomes more valuable, not less, as team count grows (see section 6 on multi-team settings).

**Accessibility.** Several consistency rules are accessibility rules in disguise: consistent focus indication placement, consistent error presentation, colour never used alone for meaning. Inconsistent application makes some users' experience depend on which screen they landed on.

**Cheaper change.** A consistent system changes in one place. An inconsistent one requires a survey before every change, because nobody knows how many divergent implementations exist.

**Onboarding shrinks.** New designers and engineers learn one rule set instead of reverse-engineering per-screen conventions. The same property makes the system legible to AI agents, which otherwise have no way to infer which of several competing local conventions is the sanctioned one.

## 3. Core principles

1. **Consistency of rules beats consistency of pixels.** Define decisions once (tokens, components, guidance) and let every surface resolve from them. If you find yourself demanding identical pixels across contexts with different needs, re-express the requirement as a rule with parameters.
2. **Consistency should be visible where it helps, invisible where it costs.** Consistent *navigational* and *interactive* elements (where things are, how actions look) pay off constantly; enforcing identical *content* layout everywhere is often harmful, because content varies.
3. **Internal consistency outranks external familiarity.** Within one product, your own rules govern: an internal convention applied everywhere beats mixing borrowed conventions from different systems. Across an ecosystem of products, converge on shared conventions — that is what makes GOV.UK services feel like one government.
4. **Deviation must be intentional, documented and justified.** The test for any inconsistency is: can the team explain *why* this case differs, in a sentence, and is the reason written down? "It looked better at the time" is not a reason; "this surface sits over imagery, so text carries a scrim" is.
5. **Consistency applies to states and behaviour as much as to looks.** A button that is visually identical but closes modals on one screen and not another is inconsistent. Behavioural consistency (keyboard support, focus handling, what happens on error) matters more than hue.
6. **Detect drift mechanically, not by memory.** Human review catches famous inconsistencies, not long-tail ones. Lint rules, token-consumption checks and automated screenshots catch the rest.
7. **Prefer deleting over permitting.** When two rules compete (two allowed danger colours, two allowed card paddings), the consistent system usually wins by permitting one — every additional permitted option is a future inconsistency waiting for a deadline.

## 4. How it works

### 4.1 The dimensions of consistency

Consistency is not one property but a family. Auditing and designing for consistency means checking each dimension separately:

| Dimension | What "consistent" means | Typical mechanism |
| --- | --- | --- |
| Spacing | Same gaps for same relationships (label→field, icon→text) | Spacing token scale; audit for off-scale values |
| Typography | Same roles use same styles (headings, body, captions) | Type tokens mapped to roles, not to elements |
| Colour | Same meaning uses same colour (danger, success, links) | Semantic colour tokens; never raw hex in components |
| Elevation | Same layering language (card vs overlay vs modal) | Elevation/shadow tokens; a small closed set of levels |
| Radius | Same component classes share corner treatment | Radius tokens per component class |
| Iconography | Same visual family, stroke weight, grid, metaphors | One icon set; documented metaphor conventions |
| Motion | Same durations/easings for same interaction types | Duration/easing tokens (enter, exit, emphasised) |
| Layout/grid | Content aligned to the same grid and gutters | Grid tokens and layout components |
| Content | Same voice, terminology, capitalisation, error phrasing | Content style guide (see [Documentation](documentation.md)) |
| Interaction | Same controls behave the same (keyboard, focus, dismissal) | Shared components; behaviour tests |

The Atlassian foundations list — tokens, spacing, grid, colour, typography, motion, iconography, elevation, border, radius — is a good checklist of the visual dimensions a system should cover; the interaction and content dimensions are supplied by components and content guidance respectively.

Two boundaries deserve care when listing dimensions. First, some dimensions are *paired*: radius and border shape each other (a 999px radius on a 1px-bordered input is a different design language than the same radius on a flat surface), so audit them together. Second, some dimensions are *emergent*: alignment is not a token but the product of grid, spacing and layout rules — auditing alignment directly ("do all list rows share the same left edge?") is legitimate even though no `alignment` token exists.

The table is also a scoping tool. A system starting out should not attempt all ten dimensions at once: colour, spacing and typography carry the most user-visible decisions and are the most mechanically checkable, so they come first; iconography and motion follow once the token layer can support them; content consistency rides on the documentation infrastructure. Attempting the full table before the mechanisms exist produces a list of rules nothing enforces.

### 4.2 What consistency is built from

A system produces consistency through four layers, in order of authority:

1. **Tokens** fix the values (colour, spacing, type, radius, elevation, motion). Anything consuming tokens is consistent by construction.
2. **Components** fix structure and behaviour. When a pattern is a component, its consistency is enforced by code reuse rather than by vigilance.
3. **Rules for what is not a component** — guidance for one-off layouts: alignment expectations, image treatment, empty states. These are the majority of real screen area and the most common drift source.
4. **Review and tooling** — the enforcement layer: design review against guidance, code linting against token/component use, and visual regression checks.

The first two layers make consistency *default*; the second two make it *resilient*. A system that relies only on review (layer 4) without defaults will drift, because enforcement depends on who is in the room.

A concrete reading of the layers: the rule "same relationships get same gaps" is *enforced* by a spacing token (`spacing.control.gap`) consumed by every form component; the rule "one primary action per view" is *enforced* by component guidance plus review; the rule "images from the CMS get a fixed aspect ratio" is enforced by a written layout rule with no component at all. Note how the enforcement mechanism moves from code to prose as the decisions become judgement-shaped — the mistake is forcing everything into one mechanism, either by componentising what is really a judgement or by reviewing what is really a mechanical rule.

### 4.3 Detecting inconsistency

Practical detection methods, from cheapest to most thorough:

- **Token-consumption linting.** Flag raw values in code where a token should be (`#2e6fe0`, `padding: 13px`). Every hit is a candidate inconsistency. This is the single highest-yield automated check; a stylelint-class rule expresses it in a few lines:

```css
/* stylelint configuration (sketch): */
"declaration-property-value-allowed-list": {
  "/^color/": ["/^var\\(--color-/"],
  "/^padding|^margin|^gap/": ["/^var\\(--space-/"]
}
```

With rules like these, the build fails on `color: #2e6fe0` and `padding: 13px`, converting consistency from a review opinion into a merge gate. The same pattern applies in design tools through library styles and linters that report off-library fills.

- **Automated visual regression.** Screenshot every story/state on change; diffs expose unintended shifts. The Storybook gallery (see [Component systems](component-systems.md)) makes states enumerable, which is what makes this feasible.
- **Scale-adherence audits.** Extract all spacing and type values from rendered CSS and compare against the scale; report off-scale usage counts per product. A histogram of font sizes that shows 37 distinct values is the fastest way to demonstrate drift to stakeholders.
- **Component-usage analysis.** Count how often teams build bespoke implementations of patterns the system already provides (home-grown modals, hand-rolled date inputs). Each bespoke build is potential inconsistency.
- **Paired-property audits.** Check semantic pairs deliberately: text/surface contrast combinations, danger-colour usage across flows, focus-ring appearance per control. Inconsistencies hide in pairings, not in isolated values.
- **Human walkthroughs.** Task-based reviews ("open the settings page, then the checkout") expose behavioural inconsistency that static checks miss.
- **Newcomer test.** Ask someone who has never used the product to predict where a control will appear on an unfamiliar screen; correct predictions measure how much the consistency is doing real perceptual work rather than merely existing in the token file.
- **Version census.** List which version of the token package and component library each consuming product resolves to; every laggard is a surface the system's current rules do not govern.

Interpret every detection result the same way, regardless of method: a finding is a *signal*, not a verdict. The signal asks which of three things is true — the instance is wrong, the rule is wrong, or the rule is missing. Automated tooling finds instances; deciding among the three options still requires the judgement framework in section 6, which is why detection and classification are paired practices rather than alternatives.

GOV.UK's component guidance demonstrates the decision-record side of the same practice: its Button page documents *why* each variant exists and cites research (green start buttons improving click-through rates), so reviewers can distinguish justified deviation from drift — an inconsistency is only "an inconsistency" when no documented reason exists.
### 4.4 Consistency in multi-team and multi-platform settings

At scale, consistency changes from a craft habit to a distributed problem:

- **Single source, many consumers.** All teams consume one token package and one component library. Distribution must be versioned and deprecation-managed (see [Governance](governance.md)); otherwise teams fork, and forking is inconsistency by another name.
- **Upgrade discipline keeps rule-versions aligned.** Because rules live in shipped artefacts (token packages, component versions), a product lagging three major versions behind the system is *definitionally* inconsistent with it — old rules, applied with care, are still the wrong rules. Publishing a compatibility window ("we support the current and previous major") and a burn-down of out-of-window products turns version lag from invisible drift into a managed queue.
- **Platform-appropriate, rule-consistent.** A web and a native app will differ in pixels (platform conventions differ) yet can share semantic tokens and naming (`color.text.primary` resolves differently per platform). Consistency of *meaning* across platforms, consistency of *pixels* within a platform.
- **Contribution flows keep the centre honest.** When teams need something the system lacks, the healthy path is a contribution request, not a private workaround. A governance model that makes contribution slower than a workaround guarantees drift (Nathan Curtis's team-models writing contrasts centralised and federated approaches to exactly this balance).
- **Intentional variation, declared centrally.** Multi-brand or multi-tier systems often *need* variation (a consumer brand vs an enterprise brand). The scalable answer is variant theming at the token layer — a declared, supported difference — rather than per-team improvisation.

One multi-team trap deserves its own name: **consistency of the system about itself**. When the component library's own website renders buttons differently from the library's code, or the token documentation lists values the build no longer produces, the system teaches consumers that its guidance is optional. Consumers model what the system does, not what it says — so the docs site, the gallery and the published packages must resolve from the same sources as the products, and a mismatch there is the highest-visibility inconsistency the system can commit.

### 4.5 When intentional variation is correct

Consistency is a means, not a virtue; the following variations are correct *because* they serve users:

- **Responsive re-layout.** A grid collapsing to one column on mobile is inconsistent in pixels and perfectly consistent in rules.
- **Context-emphasis.** A destructive action styled as a warning variant in a confirmation dialog, but as plain text in a list — difference in prominence follows difference in consequence.
- **Reduced-motion and accessibility settings.** Motion tokens resolving to near-zero under reduced-motion preferences is rule-consistent and user-serving.
- **Platform conventions.** A date picker native to iOS and a web one differ; forcing web patterns onto native degrades usability for convention-following users.
- **Progressive disclosure.** An expert console may reveal advanced options inline that a consumer product hides behind a disclosure; the *rule* (advanced settings are one level from their context) stays constant while its expression varies with audience expertise.
- **Domain-specific density.** A trading screen and a marketing page legitimately use different density levels — expressed as a density token set, not ad-hoc compression.

The evaluation question is always: does the difference encode a *reason the user can benefit from*, and is that reason documented? If yes, it is variation, not drift.

A micro-example shows the discrimination working. A product team asks for red buttons on the checkout page because "payments feel more serious there". Drift reading: it contradicts `color.action.primary` and fragments the action vocabulary. Variation reading: perhaps — but only if the *reason* is about the user (research showing mis-presses on payment confirmation) rather than the stakeholder's feeling, the change is expressed as a declared variant (`button.action.payment`) with a documented rule ("payment confirmation only"), and the same rule is applied everywhere payment confirmation occurs. Same request; three tests decide whether it is variation or the first domino of drift.

### 4.6 Motion and content: the overlooked dimensions

Motion consistency is easy to neglect because motion is transient, yet it is highly perceptible. The rule-based approach mirrors colour: a small closed set of duration tokens (fast for feedback, base for transitions, slow for large surface changes) and one or two easing tokens (a standard ease for most transitions, an emphasised curve for enter/exit of overlays), consumed by every animated component. Inconsistency shows up as modals that fly in at 400ms while dropdowns snap at 80ms — each individually defensible, collectively noisy. The same tokens should encode the accessibility fallback: motion reduced to near-zero under reduced-motion preferences is a rule applied consistently, not a per-component kindness (see section 4.5).

Content consistency behaves identically. Terminology ("delete" vs "remove" vs "discard" for the same operation), capitalisation, error-message voice and number/date formatting are consistency dimensions with their own token-like mechanism: a content style guide functioning as the source of truth, referenced from component docs (see [Documentation](documentation.md)). An interface can be pixel-perfect at the token level and still feel inconsistent when its labels disagree about the same concept.

## 5. Practical application

Running a consistency pass on a product, concretely:

1. **Inventory the dimensions.** For each row of the table in 4.1, extract the current values in use (a rendered-CSS scrape for spacing/type/colour is usually enough).
2. **Compare against the scale.** Mark every off-scale value; group them into (a) mistakes, (b) intentional-but-undocumented, (c) gaps in the scale itself. Category (c) is important: drift clusters where the system has no answer.
3. **Fix the mechanism, not just the instances.** Each off-scale value gets either a token change (the scale was wrong), a code fix (the value is wrong), or a documented exception (the context justifies it). Fixing instances without a mechanism guarantees recurrence.
4. **Add the automated check.** Turn every recurring mistake class into a lint rule or CI check before moving on; the audit's value compounds only if it becomes continuous.5. **Re-test behaviourally.** Walk the key flows with keyboard and a screen reader; check error, empty and loading states across screens. Visual consistency without behavioural consistency is cosmetic.
6. **Publish the deltas.** Report counts ("danger colour defined 4 ways; now 1", "31 off-scale spacings; now 3 documented exceptions") — visible numbers are what sustain leadership support for the work.

A worked audit record shows the shape of the output — findings classified per the fix categories in step 3:

| Finding | Classification | Fix |
| --- | --- | --- |
| `padding: 13px` on product cards across two services | Mistake | Replace with `spacing.card.padding`; add lint rule |
| Danger buttons rendered in orange in one legacy flow | Mistake | Re-map to `color.danger.default`; fix in token layer |
| Compact table density in the admin console, 8px rhythm | Intentional, undocumented | Document as a supported `density="compact"` theme; declare it |
| No token for icon-to-label gap; every component guesses 2–6px | Scale gap | Add `spacing.inline.icon-gap`; migrate the five values |
| Modals use 400ms entry, dropdowns 80ms, same easing nowhere | Scale gap | Introduce duration tokens (`motion.fast/base/slow`) and one easing token |

The classifications matter because they route to different owners: mistakes go to code fixes, undocumented intentions become declared themes, and scale gaps are token-layer work — an audit that treats all three as "clean up odd values" will fix the first two and quietly lose the third.

For a new system rather than an existing product: adopt tokens and the core twenty components first (see [Component systems](component-systems.md)), because retrofitting consistency is roughly an order of magnitude more expensive than starting with defaults.

Cadence matters as much as method. Run the mechanical checks continuously (on every merge, via the lint and visual-regression gates), the dimension audits quarterly (a different dimension each quarter cycles through the full table in a year), and the behavioural walkthroughs per major feature. The quarterly audit needs to stay small enough to actually happen: a two-hour pass over one dimension, producing the classification table in step 3, beats an annual audit that never gets scheduled.

## 6. Decision framework

**How much consistency is enough?** Ask who depends on the pattern:
- High-frequency, safety-relevant patterns (navigation, destructive actions, form errors): strict rule-consistency, enforced by tooling.
- Medium-frequency patterns (cards, lists, filters): token-and-component defaults with documented flexibility.
- Expressive surfaces (marketing pages, illustrations): looser rules, but still consistent in *family* (icon style, type family, colour range).

**Is this drift or intentional variation?** Three checks: (1) Is there a user-serving reason? (2) Is it documented where the next team will find it? (3) Is it reproducible — would we make the same choice again in the same context? Any "no" means drift; fix it through the mechanism, not the symptom.

**Which inconsistency to fix first?** Rank by (user confusion × frequency × fix cost). Behavioural inconsistencies (inconsistent error handling, focus behaviour) outrank visual ones; dimension-wide drift (all spacing) outranks single-instance quirks; cheap automated fixes outrank refactors.

**Enforce by tooling or by review?** Both, split by failure type: tooling for mechanical rules (token use, scale adherence, allowed components), human review for judgement calls (layout quality, content voice). Rules that could be checked by a machine and are left to review will be checked by nobody.

**One system or per-brand variants?** If the brands share users, channels and accessibility obligations, run one tokenised system with declared brand themes (variants at the token layer); fork into separate systems only when the differences are structural (different component behaviours, different platforms), not merely visual. Forked systems re-grow the same foundations expensively; themed systems share everything except the decisions that genuinely differ.

**When is consistency work finished?** Never as a state — only as a capability. The honest success measure is not "zero inconsistencies found" but "inconsistencies are found by tooling within one change cycle, and every finding has a named mechanism that prevents recurrence".

**What does the framework look like in a review?** Compressed into questions a reviewer can hold in their head: Is this value in the token file? If no — is it a new decision (propose the token) or a violation (fix it)? Is this difference between two screens explained by the rules? If no — which screen is wrong, and what mechanism would have caught it earlier? Would two teams, shown the same brief, produce the same choice here? If no — the rule is missing, and the review's output is the rule, not just the fix.

## 7. Examples

- **GOV.UK Design System** — the strongest public example of cross-organisation consistency: dozens of government services share one component and pattern library, with per-component research notes justifying decisions, so consistency is defensible rather than merely imposed. Its warning-button guidance (sparingly, only for irreversible actions) shows consistency *rules*, not just consistent pixels.
- **Atlassian foundations** — a broad tokenised foundation set (spacing, grid, colour, typography, elevation, border, radius, iconography, motion) serving many products: the multi-product case for rule-level consistency.
- **Material Design 3** — one rule system generating many themes: apps that look different yet remain recognisably consistent because tokens and components are shared. Useful as the canonical demonstration that consistency ≠ uniformity.
- **Storybook-based galleries** — the standard engineering mechanism for consistency checking: every state rendered side by side, plus visual-regression diffs, makes drift visible before release rather than after.
- **Spacing scale adherence as a worked dimension** — take one dimension and follow it through the whole method: define the scale (token file), consume it (layout components), lint it (stylelint allowed-list, as in section 4.3), audit it (rendered-CSS scrape), classify the residue (mistake / intention / gap), and feed gaps back into the scale. Any of the ten dimensions in section 4.1 can be run through the same loop; the loop, not any single pass, is what keeps a system consistent over years.

## 8. Common mistakes

- **Enforcing uniformity instead of rules.** Mandating identical pixel layouts across contexts (marketing page vs settings screen) damages both; express the requirement as a parameterised rule instead.
- **Auditing values without fixing mechanisms.** A clean-up sprint that changes 200 hard-coded values but leaves raw literals allowed in code reproduces the mess within a quarter.
- **Treating new variants as achievements.** Every new variant, level or tone added to a closed set weakens the set's consistency guarantee; growth should be governed (see [Governance](governance.md)), not celebrated.
- **Ignoring behavioural consistency.** Screens can look perfectly consistent while Escape closes some dialogs and not others; audits that only inspect screenshots miss the class of issues users complain about most.
- **Undocumented exceptions.** An approved deviation with no written rationale becomes the precedent for the next deviation; the system drifts one "special case" at a time.
- **Consistency theatre in docs.** Guidance stating "be consistent" with no rules, scales or examples enforces nothing; effective guidance names the token, the value and the when/when-not.
- **Changing the rule and the consumers in one motion.** When a decision changes (new elevation scale), changing the tokens and rewriting every consumer simultaneously is a migration disguised as a fix; change the token, let consumers resolve on their own schedule, and treat stragglers as a version-lag queue (section 4.4).
- **Per-team theming forks.** Copying the token file into a product and editing it locally severs the single source of truth; variants belong in the token layer as declared themes.
- **Auditing only the newest product.** Consistency reviews that cover the latest rebuild while legacy surfaces go unexamined leave the largest drift untouched; scope audits to *flows*, not to repositories, because users cross those boundaries without caring which team owns the code.
- **Retro-fitting everything at once.** Big-bang consistency projects stall; sequence by the ranking in section 6 and ship dimension by dimension.
- **Consistency by screenshot review only.** Looking at rendered pages catches the dramatic misses and nothing else; most drift (off-scale spacing, near-identical-but-not colours) is invisible to the eye and obvious to a script.
- **Adding tokens to fix drift.** When a scan finds 30 off-scale spacings, the reflex to create 30 new tokens preserves every mistake; the correct move is to classify (mistake/gap/intention) and usually to map the values onto existing scale steps.
- **Fixing design and code separately.** A drift fixed in the mockups but not the code (or vice versa) re-inconsistents itself within a sprint; every fix lands in the token/component layer where both read from.
- **Copy-paste audits across systems.** Reusing another organisation's checklist without its mechanisms (their lint configs, their gallery tooling) produces reports with no fixes; consistency work is the loop, not the report.

## 9. Evaluation checklist

- [ ] Every visual dimension in the 4.1 table has an owned mechanism (token, component, or written rule).
- [ ] A scan for raw values (hex, px) in component code returns (near) zero hits, or only documented exceptions.
- [ ] Spacing and type values in rendered output cluster on the defined scale; a count of distinct values exists and trends downward.
- [ ] Semantic colour roles (danger, success, links, focus) resolve to one token per meaning across products.
- [ ] Focus indication, error presentation and disabled states are identical across all controls.
- [ ] Empty, loading and error states exist and match for every data-bearing component.
- [ ] Intentional deviations are documented with reasons and owners; the list is finite and reviewed.
- [ ] Automated checks (token lint, visual regression) run on every change; failures block merge.
- [ ] Multi-platform surfaces share semantic token names even where pixel values differ.
- [ ] Motion durations and easings resolve to the system's duration/easing tokens, with a reduced-motion fallback defined once.
- [ ] Terminology for recurring concepts (delete/remove, sign in/log in) is defined in one content source and used identically.
- [ ] A task-based walkthrough (keyboard + screen reader) across key flows finds no unexplained behavioural differences.
- [ ] No product is more than one major version behind the system's token/component packages, and any lag is a tracked, owned queue.
- [ ] The system's own surfaces (docs site, gallery, published packages) resolve from the same sources and show no self-inconsistency.
- [ ] Fixes land in the shared mechanism (token, component, rule) rather than in individual instances.
- [ ] Audit scope covers legacy and rebuilt surfaces alike; findings are counted per flow, not per repository.
- [ ] Dimension audits run on a schedule (a rotating dimension per quarter), not as one-off projects.
- [ ] Every audit finding carries a classification (mistake / intention / scale gap) and an owner for its fix.
- [ ] New automated checks were created for recurring drift classes, and the lint config is versioned with the system.

## 10. Related topics

- [Design tokens](design-tokens.md) — the value layer that makes rule-consistency enforceable.
- [Component systems](component-systems.md) — the structural layer: shared components make behaviour consistent by construction.
- [Documentation](documentation.md) — where consistency rules are published so consumers can follow them.
- [Governance](governance.md) — how new variants and exceptions are approved without drift.
- [Design system audit](../evaluation/design-system-audit.md) — the formal evaluation built on these checks.
- [Gestalt and perception](../foundations/gestalt-and-perception.md) — why users perceive similarity and difference the way they do.
- [Spacing and proportion](../layout/spacing-and-proportion.md) — the spacing craft behind the spacing dimension.
- [Typographic hierarchy](../typography/typographic-hierarchy.md) — the type-role consistency dimension.
- [Colour accessibility](../colour/colour-accessibility.md) — contrast rules that consistency checks must respect.
- [Brand governance](../branding/brand-governance.md) — the brand-side counterpart to system-level consistency.

## 11. References

- Atlassian Design System, *Foundations*. https://atlassian.design/foundations/ [accessed 2026-11-23]. Source for the foundations dimension list (tokens, spacing, grid, colour, typography, motion, iconography, elevation, border, radius).
- GOV.UK Design System, *Button component*. https://design-system.service.gov.uk/components/button/ [accessed 2026-11-23]. Variant usage rules and research citation (green start buttons and click-through) exemplifying documented, justified variation.
- GOV.UK Design System, homepage. https://design-system.service.gov.uk/ [accessed 2026-11-23]. Cross-service consistency model (shared styles, components and patterns maintained by GDS).
- Material Design 3, *Design tokens*. https://m3.material.io/foundations/design-tokens [accessed 2026-11-23; page body did not render in fetch]. One-rule-system/many-themes framing drawn from general professional knowledge of the system [canonical].
- Nathan Curtis (EightShapes), *Team Models for Scaling a Design System*. https://medium.com/eightshapes-llc/team-models-for-scaling-a-design-system-2cf9d03be6a0 [search-verified 2026-11-23]. Centralised vs federated contribution context for section 4.4.
- Storybook, *Why Storybook*. https://storybook.js.org/docs/get-started/why-storybook [accessed 2026-11-23]. Isolated per-state rendering as the mechanism behind galleries and visual regression.
- Section 4.2's four-layer model and the decision framework in section 6: synthesis of the sources above with general professional practice; presented as conventional guidance rather than a single-source claim.
