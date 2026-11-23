# Component Systems

## 1. What is it?

A component system is the organised library of reusable interface pieces — buttons, inputs, dialogs, cards, tables — together with the rules for how they are built, named, combined and documented. The individual component is the unit of reuse; the *system* is what makes dozens or hundreds of such units coherent: shared tokens for their visual values, a consistent API style, documented states and variants, and predictable versioning.

A component in this sense has three inseparable aspects. Its **anatomy** is what it is built from (slots, sub-elements, internal structure). Its **API** is what consumers control (props, configuration, events, defaults). Its **states** are what it can be (default, hover, focus, disabled, loading, error, empty). Systems that document only the picture of a component — a button rendered in isolation — and ignore API and states produce libraries that look good in a catalogue and behave badly in real products. The three aspects are also the three things a consumer evaluates before adopting a component: what is it made of, what can I control, and what will it do in every situation I put it in.

The distinction between a *component library* and a *design system* matters: the library is the code and designs; the system additionally includes foundations, tokens, documentation and governance. A component system file like this one covers the library side — the engineering and interface-design craft of the components themselves. In practice the boundary is porous by design: a component system without foundations drifts visually, and foundations without components stay theory, so this file assumes and links to both neighbours.

## 2. Why does it matter?

**Reuse compounds.** A well-built component is written once and used in every product, screen and team afterwards. Each new consumer multiplies the return on the original investment and, equally important, multiplies the amount of testing the component receives in real conditions.

**Consistency of behaviour, not just appearance.** Two teams can style a button identically and still produce different products if one closes a modal on Escape and the other does not. A shared component guarantees interaction decisions — keyboard support, focus handling, error display — travel with the visuals. This is where most of a component's accessibility value lives: keyboard paths, visible focus and screen-reader semantics are implemented once and inherited everywhere.

**Velocity with guardrails.** Teams move faster because common problems (form validation display, empty states, loading) are already solved, but the guardrails keep that speed from fragmenting the product: the fastest path is the system path.

**Reviews get smaller.** When components are the vocabulary, a design or pull-request review checks composition ("which components and which props?") rather than re-litigating pixel decisions. That is what makes scaling to many teams possible at all.

The cost of *not* having a component system shows up as quadratic rework: every screen solves the same problems (validation display, focus management, empty states) slightly differently, so every screen needs its own testing, its own accessibility fixes and its own redesign. What looks like "just a few styles" in the first product becomes a maintenance fleet by the third. A component system pays its costs once; the alternative pays them per screen.

## 3. Core principles

1. **One component, one job.** A component should have a single clear responsibility that can be stated in a sentence. `Button` handles press actions; it does not also format dates. Components that accrete "just one more prop" responsibilities become unmaintainable.
2. **Props are the contract; slots are the escape hatch.** Props cover the *controlled* configuration space; slots (child content injection) cover the *unanticipated* content space. A good component gives consumers a way to compose without demanding a fork of the component.
3. **Sensible defaults, minimal required configuration.** A component should render correctly with zero props (beyond content), and every default should be the choice most consumers want — because every default is what most consumers will silently accept.
4. **Tokens in, not raw values.** Components consume design tokens (see [Design tokens](design-tokens.md)) for colour, spacing, radius and type. This is what makes them themable and keeps the system's visual layer single-sourced.
5. **States are first-class.** Every interactive component must define its interactive states (hover, focus-visible, active, disabled, loading) and its content states (empty, loading, error) — not as an afterthought in CSS, but as part of the API and documentation.
6. **Composition over configuration.** When a component grows five or more boolean props that toggle sub-features, prefer splitting into composable parts (`Dialog`, `Dialog.Header`, `Dialog.Body`) rather than a mega-component with combinatorial prop explosion.
7. **Behaviour is part of the visual design.** What happens on Escape, where focus lands when a dialog closes, whether a form preserves input after a failed submit — these are design decisions with implementations, not implementation details. A system that treats them as engineering leftovers produces components that look consistent and behave inconsistently.

## 4. How it works

### 4.1 Anatomy: slots, props and states

**Slots** are named places where consumers inject content. A card might expose `header`, `media`, `body` and `footer` slots. Slots keep structure system-owned and content consumer-owned — the component guarantees layout, spacing and alignment while the consumer supplies meaning. In HTML-centric terms, a slot is the component's documented child-content contract.

**Props** (attributes, parameters) are the configuration knobs. The prop set *is* the component's API, so it deserves the same care as any public interface. A prop should be: named in domain language (`onConfirm`, not `func1`); typed; given a sensible default; and documented with *when to use it*. Boolean props should read as assertions of state (`disabled`, `loading`, `invalid`).

**States** are the values the component's appearance and behaviour can take over time. The professional baseline for an interactive control:

| State | Meaning | Typical treatment |
| --- | --- | --- |
| Default | Resting, enabled | Baseline token styling |
| Hover | Pointer over, still actionable | Slight background/opacity shift |
| Focus-visible | Keyboard focus | Visible focus ring — never removed |
| Active / pressed | Being pressed | Darker/denser variant of default |
| Disabled | Not interactive | Reduced contrast, no pointer events; set `aria-disabled` |
| Loading | Action in progress | Spinner text or inline progress; often disables re-submission |
| Invalid / error | Validation failure | Danger token colour plus text, not colour alone |
| Empty | No content yet | Guided empty state, not blank space |

Content states (loading, empty, error) are often exposed as props (`loading`, `error`) or as sub-components, so that every list, table and card in the product handles them the same way.

Two practices keep state design honest. First, **states are designed, not derived**: a hover state guessed at implementation time ("just darken it 10%") produces a library of subtly different hovers; the state table above should be settled in design before build, with tokens per state where the system supports it (`color.action.primary-press` exists precisely so the pressed state is not improvised). Second, **state coverage is a completeness measure for the whole library**: if the gallery shows a component only in its default state, the component is roughly one-seventh documented — the missing six-sevenths is where consumers meet the real product.

### 4.2 Variants and modifiers

A **variant** is a named, sanctioned appearance or behaviour difference within one component. GOV.UK's Button page is a clean model: default (primary call to action), start (service start pages), secondary (secondary actions), warning (destructive, irreversible actions, used sparingly), and inverse (for dark backgrounds) — each with its own class (`govuk-button--start` etc.) and its own usage rule. Variants are closed sets: a consumer picks from the documented list; they do not invent one by overriding internals.

A **modifier** (often a size or density prop: `size="sm|md|lg"`, `density="compact"`) changes degree rather than kind. Keep the matrix finite and intentional: every variant × size × state combination multiplies the cases to design, test and document. The GOV.UK guidance also shows the discipline variant lists need — warning buttons "should be used very sparingly" and pages should not carry multiple primary calls to action, because variant variety without usage rules recreates visual noise.

Variants should be implemented with tokens, not forked stylesheets: `button.primary.background = {color.action.primary}` means a variant is a token mapping plus a usage rule, which is also what makes the variant themable.

Manage the matrix explicitly. Variants × sizes × states is a product, and its size is the system's maintenance surface. Two disciplines keep it finite: document the *supported* combinations (a small table in the component's docs beats an implicit "everything works with everything"), and prefer orthogonal modifiers so combinations degrade sensibly (a disabled `sm` warning button should simply be the warning button at its disabled state, not a separately designed case). When a new variant is requested, ask what usage rule it would carry — a variant with no rule is usually a one-off style escaping its page.

### 4.3 API design thinking

Naming. Names should match the consumer's mental model, follow platform conventions (React `onChange`, web attributes `disabled`, ARIA vocabulary where relevant), and stay consistent across the library — if a header exists in `Card`, `Dialog` and `Table`, call it the same thing in all three. Renaming a widely consumed prop is a breaking change, so precision at the start saves deprecation pain later.

Defaults. Defaults encode the system's opinion and are read by the majority of consumers. Default the accessible and safe behaviour: sensible `type` for buttons, visible focus, error messages attached to inputs, and content overflow handled gracefully. A default that must be overridden for accessibility in most usages is a defect in the default.

Controlled vs uncontrolled. Form-adjacent components should support both: uncontrolled (consumer rarely reads the value) with sensible internal state, and controlled (consumer owns state via `value` + `onX`) when they need to drive it. Document which mode a component is in — ambiguity here is a classic source of subtle bugs. The practical rule: default to uncontrolled for low-stakes inputs, because it keeps consumer code minimal; require controlled for anything where the value drives other UI, because two sources of truth for state that other components display is the root of desynchronisation bugs.

Events and callbacks. Name events after what happened, not what the consumer should do (`onDismiss`, not `closeDialog`). Forward native attributes where reasonable, and never swallow accessibility semantics (e.g. a custom `onClick` layer on a link must keep the native element underneath so keyboard and screen-reader behaviour survive).

A minimal contract sketch shows how these considerations land in one place:

```ts
interface ButtonProps {
  children?: SlotContent;                 // slot: free-form content
  variant?: 'primary' | 'secondary' | 'warning';  // closed variant set
  size?: 'sm' | 'md' | 'lg';              // modifier: degree, not kind
  type?: 'button' | 'submit';             // accessible default matters (see below)
  disabled?: boolean;
  loading?: boolean;                      // content/state as first-class prop
  onClick?: (event: MouseEvent) => void;  // what happened, not what to do
}
```

Reading the sketch deliberately: `variant` is closed (consumers pick from sanctioned kinds, they do not pass raw colours); `size` is a modifier (degree of the same thing); `children` is the slot escape hatch; `loading` acknowledges a state as part of the API; and `type` defaulting to `'button'` rather than `'submit'` is a classic example of an accessible, safe default — accidental form submissions from decorative buttons are a recurring production bug.

### 4.4 Composition patterns

- **Compound components**: a parent plus named children sharing context — `<Tabs>`, `<Tabs.List>`, `<Tabs.Panel>`. Scales well for components with distinct internal regions and avoids boolean-prop explosion.
- **Slot injection**: children land in documented slots (`Card.Header`), giving layout guarantees with content freedom.
- **Wrapper / polymorphic components**: `as` or `render` props let a component change its underlying element (a button rendering as a link) — powerful for semantics, dangerous for accessibility if used to bypass the native element.
- **Headless patterns**: behaviour without styling, consumed via hooks or render props, letting teams keep their own presentation. Appropriate where appearance must vary wildly but behaviour must not.
- **Layout vs content separation**: components that own spacing and alignment (layout) should not hard-code content assumptions (fixed label lengths, one-line values). This is the boundary where components most often fail in new products.

A compound-component sketch makes the pattern concrete — the parent owns behaviour and context, the children own placement:

```html
<Tabs>
  <Tabs.List aria-label="Billing options">
    <Tabs.Tab>Monthly</Tabs.Tab>
    <Tabs.Tab selected>Annual</Tabs.Tab>
  </Tabs.List>
  <Tabs.Panel tab="Monthly">…</Tabs.Panel>
  <Tabs.Panel tab="Annual" selected>…</Tabs.Panel>
</Tabs>
```

The alternative as a single configured component would need props like `tabsList`, `tabIndex`, `panelContent` and manual ARIA wiring at every call site; the compound form keeps the keyboard interaction model and ARIA roles in one implementation while letting each consumer assemble its own content.

### 4.5 When to make a component — and when not to

Make a component when: the pattern is (or will be) used in more than one place; it encodes a behavioural decision (focus, keyboard, validation) that must not drift; it will be tested and documented once for many consumers; or its existence creates shared vocabulary that reviews rely on.

Do **not** make a component when: it is a one-off decoration specific to a single page (a local style suffices); it is a thin variant achievable with existing props or composition; the abstraction is speculative ("someone might need this"); or combining two existing components already solves it. Also do not make a component when the "component" is actually *content* — a branded banner whose essence is a campaign message belongs in the campaign codebase, not the library. A useful professional heuristic is the rule of three — tolerate duplication until the third occurrence reveals the real variation space; premature abstraction freezes the wrong API. The cost of a wrong component is higher than the cost of duplicated markup: a wrong component gets consumed everywhere before the mistake is visible, and fixing it becomes a breaking change.

Also weigh *who* benefits. A component only one team will use may live in that team's codebase; a component three teams need belongs in the shared library — that boundary decision is governance (see [Governance](governance.md)).

### 4.6 Maturity levels

Public systems express component maturity so consumers know what they can rely on. The vocabulary varies by organisation (Material, GOV.UK and others publish component status), but the tiers are conventionally:

| Level | Meaning | Consumer expectation |
| --- | --- | --- |
| Experimental / alpha | Under active design; API unstable | Use for trials only; expect breaking changes |
| Beta | Design settled, hardening | Use with caution; changelog watch required |
| Stable / production | Supported, tested, documented | Safe default choice for new work |
| Deprecated | Scheduled for removal | Migrate away; replacement documented |

Publishing the level per component (in docs and in code metadata) lets teams adopt safely and gives the system team a roadmap language. GOV.UK's component pages model the accompanying transparency: usage guidance, research notes, and a "Recent changes" changelog table visible to all consumers.

Status should also *propagate*: a component is only as stable as its least stable dependency, so a beta component consuming an experimental primitive cannot claim stable itself. Where the library is versioned, this maps directly to release semantics — experimental components may ship in any release with a breaking change, stable ones may not. Consumers plan around published status, which is precisely why the status must be honest: upgrading silently between statuses breaks the same trust breaking versions do.

### 4.7 Versioning and deprecation basics

- **Version the library, not per-component**, using semantic versioning: patch for fixes, minor for additions (new props, new variants), major for removals and behaviour changes. Communicate which components a release touches in the changelog.
- **Deprecate before removing.** A deprecated prop or component keeps working, logs a warning naming the replacement, and carries a removal target version. Consumers migrate on their schedule; the system removes in the next major.
- **Never break silently.** Behaviour changes (e.g. focus handling) are breaking even when the props are unchanged; note them explicitly.
- **Label compatibility explicitly.** Publish which consumers each release is expected to serve (the current and previous major, say) and which paths are untested for older versions; a compatibility statement turns upgrade planning from guesswork into a queue, and makes version lag visible in audits (see [Visual consistency](visual-consistency.md)).
- **Codemods where possible.** For widely consumed libraries, automated migration scripts turn a painful major release into a routine one.

**In the component system specifically, versioning discipline has a component-level echo:** keep each component's public surface (props, slots, variants, states) enumerable, because you can only deprecate what you have listed, and SemVer claims ("this is additive") are only verifiable against an enumerated contract. The contract table from section 5.1 is what makes the claim checkable.
- **Keep the changelog human.** GOV.UK's "Recent changes" section — a table of what changed and when per component — is the standard consumers actually read; write entries as decisions ("Secondary buttons restyled for contrast"), not as commit dumps.
- **Publish removal timelines with the deprecation.** A deprecation without a removal version is a rumour; the strongest libraries pair every deprecation notice with the target release and a dashboard of remaining usage (see [Governance](governance.md)).

### 4.8 Storybook-style documentation

The dominant pattern for component documentation is the **story**: one component rendered in one defined state, isolated from application context. Storybook's documentation describes it as "a small, development-only, workshop that lives alongside your app", where "stories are a declarative syntax for supplying props and mock data to simulate component variations", built on Component Story Format — "an open standard based on JavaScript ES6 modules" so stories port across tools. The mechanics that matter conceptually:

- **Args** are the props fed to a story; controls generated from args let reviewers toggle props live and see each state (the docs' example feeds `histogramAccentColor: '#1EA7FD'` as an arg).
- **Isolation** — rendering "in an isolated iframe ... without interference from app business logic" — is what makes the workshop a *system* view rather than a product view: every state of every component is visible and comparable in one place.
- **Docs generation** — "Storybook also auto-generates documentation from those stories", giving prop tables and live examples from the same source of truth as the code.
- **Testing hooks** — the same stories drive interaction, accessibility and visual regression tests, and can be reused in Jest, Vitest, Playwright, Cypress or Chromatic, so documentation artefacts double as test fixtures.

The general principle outlives any tool: a component system should maintain one gallery where every component, variant and state is rendered, labelled and reachable — it is simultaneously the developers' test bench, the designers' review surface and the consumers' shopping catalogue.

### 4.9 Responsive behaviour as a component concern

Components, not pages, should own their responsive behaviour wherever the behaviour is intrinsic to the component. A table that can reflow to stacked cards, a dialog that becomes a full-screen sheet on narrow viewports, a navigation bar that collapses into a disclosure — each encodes decisions that would otherwise be re-implemented (differently) by every page. Two mechanisms do most of the work: **fluid sizing inside the component** (percentages, `clamp()`, container-relative units) so it adapts to whatever space it is given, and **documented breakpoints at which its layout switches**. Where the system has breakpoint tokens, components consume the tokens rather than private media-query values, so the whole system reflows coherently. The test of a responsive component: drop it into a narrow container it has never seen and verify it degrades gracefully without page-level fixes — the same isolation principle the story gallery applies to states, applied to widths.

### 4.10 Icon systems as a component class

Icons deserve the same contract discipline as any other component, because they fail in the same ways. The system-level mechanics: one delivered icon *set* (a single visual family — stroke weight, corner treatment, grid), exposed through one `Icon` component that takes a closed set of names, and sized through tokens (`size.icon.sm/md/lg`) so icon scale follows the type scale rather than ad-hoc pixel values. The component should enforce accessibility by default: decorative icons are hidden from assistive technology (`aria-hidden`), meaningful icons require a label or accompanying text, and — as the GOV.UK warning-button guidance puts it — colour alone must not carry meaning, so an icon accompanying a state (error, warning) is redundancy that helps everyone. The *metaphor* rules (when a magnifier means search, when to reuse an icon for a new concept, when to commission a new one) are consistency-of-language questions and belong with the iconography guidance in [Visual consistency](visual-consistency.md); the delivery mechanics belong here.

## 5. Practical application

Building out a small system, in order:

1. **Start from tokens.** Define colour, spacing and type tokens first (see [Design tokens](design-tokens.md)) — components built before tokens exist accumulate hard-coded values that block theming later.
2. **Build the ten to twenty components that cover 90% of screens**: Button, Text input, Select, Checkbox/Radio, Form field wrapper, Dialog, Card, Table, Tabs, Alert/Banner, plus primitives for text, stack/layout spacing and icon. Most product pages are compositions of these.
3. **Define each component's contract before styling it**: list its props, slots, variants, states and accessibility requirements. Write the usage guidance first; it exposes API confusion cheaply.
4. **Give every component a story per state**, not one story per component — the state gallery is what consumers actually need to see.
5. **Wire accessibility in from the start**: native elements underneath, keyboard paths, visible focus, `aria-disabled` alongside `disabled`, error text tied to inputs. Retrofitting is the classic failure mode.
6. **Document as you go** using the component-page anatomy in [Documentation](documentation.md): when to use, do/don't, anatomy, states, content rules, accessibility notes.
7. **Version and release deliberately**: changelog entries per component, deprecation warnings naming replacements, maturity labels in the docs.

### 5.1 A worked component contract: Button

Define the contract before the styling. The table below is what step 3 produces for a button, following the GOV.UK variant model and the states baseline from section 4.1:

| Aspect | Decision | Usage rule |
| --- | --- | --- |
| Variants | `primary`, `secondary`, `warning`, `inverse` | One primary action per view; warning reserved for irreversible actions; `inverse` only on dark surfaces |
| Sizes | `sm`, `md`, `lg` | `md` default; `sm` only inside dense layouts (tables, toolbars) |
| States | default, hover, focus-visible, active, disabled, loading | Focus-visible ring never removed; loading disables re-submission |
| Disabled policy | Prefer enabled-with-validation | Disabled only where research shows it aids comprehension; render `aria-disabled` alongside `disabled` |
| Content rules | Sentence case, verb-led label | "Start now", "Save and continue"; no truncated labels |
| Tokens consumed | `color.action.*`, `color.text.*`, `radius.control`, `spacing.inset.control*` | No raw hex or px in the component |
| Accessibility | Native `<button>` underneath; visible label; contrast ≥ 4.5:1 for text | Colour never the sole signal of the warning variant |

Then every state becomes a story — one per cell of the state gallery, not one per component:

```js
// Button.stories.js — Component Story Format
export default { component: Button };

export const Primary        = { args: { variant: 'primary', children: 'Start now' } };
export const Secondary      = { args: { variant: 'secondary', children: 'Find out more' } };
export const Warning        = { args: { variant: 'warning', children: 'Delete account' } };
export const PrimaryLoading = { args: { ...Primary.args, loading: true } };
export const Disabled       = { args: { variant: 'secondary', disabled: true } };
```

This single artefact serves four audiences at once: it documents the variant set for consumers, renders the state gallery for review, drives visual-regression tests, and gives designers a reference implementation against mockups. When the contract table and the stories disagree, one of them is wrong — the discrepancy itself is a useful review signal.

The same contract, once merged, becomes the component's page in the documentation (see [Documentation](documentation.md)): the table becomes the variant and state sections, the stories become the gallery, and the usage rules become the when-to-use guidance. Writing the contract first therefore costs almost nothing extra — it *is* the documentation, captured before implementation rather than reconstructed after.

## 6. Decision framework

**Build vs adopt vs wrap.** Adopt an existing library when your product's visual identity is flexible and its behaviour matches yours — customising tokens on a mature library is usually cheaper than maintaining your own. Build your own when brand identity or interaction patterns are genuinely distinctive (and budget for ongoing maintenance). Wrap an existing library when behaviour is good but appearance must fully match brand — you inherit tested behaviour and pay a thin styling layer. Re-evaluate after each major release of an adopted library.

**Prop vs variant vs new component.** Degree of the same thing (size, emphasis) → prop or modifier. Kind of the same thing, with usage rules (primary vs destructive) → named variant. Different job or different semantics → separate component. Two components whose variants are actually different jobs should be split, not parameterised into one.

**Is the component ready to be shared?** A promotion readiness check, in order: does it consume only tokens; does it cover all interactive and content states; does it pass keyboard and screen-reader use; does it have a finished documentation page; is its API written so a rename would not be needed tomorrow. Sharing an unready component distributes its incompleteness — and the first bug report from another team is usually cheaper than the review that would have caught it.

**Expose as prop or slot?** Structured, validated content → prop (a `Card` takes `title` as a prop so it can guarantee typography). Free-form or rich content → slot/children. When both exist, prefer slot for flexibility and prop for guarantees — and document which one affects layout.

**When to promote a pattern into the library.** Track repeated one-off implementations (the rule of three); promote when the variation space is understood, not merely when duplication is noticed. A promoted component without usage guidance will fork immediately.

**How much surface to expose?** Expose the smallest prop set that covers demonstrated needs, and grow it on evidence: every exposed prop is a promise to maintain, test and document indefinitely. Internal structure stays private — consumers who need to reach into a component to style its internals signal either a missing variant or a missing slot, and that request should go through the contribution flow (see [Governance](governance.md)), not around it.

**Where does the component live?** Team-local until a second team needs it; library once two do. Moving early costs coordination for nothing; moving late means merging two divergent implementations — the merge is usually harder than either original build, which is why the promotion trigger should be a tracked signal (a request, a duplication count) rather than a vibe.

**Retrofit or rebuild?** When adopting a system into a codebase with existing one-off components, wrap-and-replace incrementally (new screens use system components; screens convert opportunistically) rather than a big-bang rewrite. Track the conversion as the adoption metric discussed in [Governance](governance.md).

**Deprecate or fix?** Fix silently if no consumer could legitimately depend on the old behaviour (a crash, a security bug). Deprecate with a replacement if consumers can depend on it. Never change visual output in a patch release.

## 7. Examples

- **GOV.UK Design System** — roughly 37 published components (Accordion, Button, Checkboxes, Date input, Error summary, Tabs, Table, Text input, Warning text and more) each documented with "When to use this component", variant-by-variant "How it works", "Research on this component", "Recent changes" and contribution links. Its Button page is the reference example of variant discipline: warning buttons reserved for irreversible actions, one primary call to action per page, disabled buttons discouraged because they "have poor contrast and can confuse some users".
- **Storybook** — the canonical workshop tool: isolated stories per state, args-driven controls, auto-generated docs, and an addon ecosystem for interaction/accessibility/visual testing. Its "why Storybook" framing — hundreds of components with thousands of variations, debugged outside app context — is the clearest articulation of why a gallery matters. The same framing explains the gallery's *scale* problem: a system with 30 components × 5 variants × 7 states is a thousand stories, which is why state galleries are usually curated (core states rendered, edge states documented) rather than exhaustive.
- **Material Design 3 components** — every component publishes its token mappings (component-tier tokens referencing system tokens), demonstrating variant-and-token discipline at large scale.
- **Atlassian Design System** — foundations (tokens, colour, spacing, elevation, radius, iconography) consumed by components across many products; a useful example of a system optimised for multi-product internal adoption.
- **Date inputs as a case study in why components exist** — a date input is visually simple and behaviourally deep: keyboard entry, parsing, locale formats, error recovery, screen-reader announcement of fields. GOV.UK lists it among its ~37 components precisely because these decisions must not be re-solved per product; the pattern generalises to any component whose complexity is invisible in a screenshot.
- **Error summary as a case study in pattern components** — GOV.UK's Error summary component does one thing no single field can: it collects validation failures, places focus on itself when a form fails, and links each message to its field. It exists because the *behaviour* was being re-implemented inconsistently across services — exactly the promotion trigger described in section 4.5.

What these examples share is that the hard part of every component is invisible in its screenshot. A gallery of rendered buttons is trivially convincing; the reason component systems exist is everything else — the keyboard model, the state coverage, the token wiring, the content rules — which is also exactly the part that must be designed and documented deliberately rather than discovered in production.

## 8. Common mistakes

- **One story per component instead of per state.** The gallery that hides loading, error and empty states is documentation theatre; consumers discover real states in production.
- **Boolean-prop explosion.** `Card withShadow withBorder compact narrow` is a combinatorial API; most combinations are untested. Prefer variants or compound parts.
- **Overriding variant internals.** Consumers reaching into component internals to invent an undocumented variant breaks on every release; if the variant is genuinely needed, the correct move is to propose it through governance (see [Governance](governance.md)).
- **Missing focus-visible or wrong focus order.** The most common accessibility defect in component libraries, and the one audits find first.
- **Disabled as the only guard.** Disabled controls with no explanation strand users; GOV.UK's research-based caution (poor contrast, confusion) applies generally — prefer enabling with validation feedback where possible.
- **Components that hard-code token values.** A component with `background: #2e6fe0` instead of the action token silently exits the theme system.
- **Components that absorb app logic.** A date picker that knows about your billing cycle is not a component; it is an application wearing a component costume. System components stay domain-blind — the moment a shared component imports product logic, it can serve only one product.
- **Speculative abstraction.** Building a component "for later reuse" without a second real use case usually freezes the wrong API; duplicated markup is cheap, a wrong shared component is expensive.
- **No maturity labels.** Consumers cannot distinguish "rock solid" from "experiments welcome", so they either avoid the whole library or trust the wrong parts.
- **States designed after the component.** Retrofitting states onto a shipped component means inventing styling that was never designed (what does the *warning* variant look like disabled?), and the results differ subtly from the same state on sibling components; states are settled at contract time, not at bug-report time.
- **Reaching into internals for styling.** A public API that leaks class names or DOM structure invites consumers to depend on them, and then every internal refactor is breaking; if a styling surface is needed, it should be a documented prop, slot or token.
- **Ignoring direction and locale.** Components hard-coded for left-to-right layouts (left-aligned icons, margin instead of logical properties) break in right-to-left locales; logical CSS properties and mirroring tests belong in the baseline, not in a late retrofit.
- **One-off accessibility forks.** When a team adds its own focus handling or ARIA wiring to a system component locally, the fix dies with their copy; accessibility defects belong in the shared component so every consumer inherits the repair.
- **Breaking changes without migration notes.** A major version nobody can migrate to is a fork in disguise; ship codemods and changelog guidance with the breakage.
- **Hard-coded breakpoint media queries per component.** When each component invents its own `@media (max-width: 730px)`, the system reflows incoherently; consume breakpoint tokens or layout primitives instead.
- **Copy-paste variant forks.** "The warning button with slightly different padding, kept locally" is the beginning of a shadow library; route the need through the contribution flow instead (see [Governance](governance.md)).

## 9. Evaluation checklist

- [ ] Every component declares its props, slots, variants, states and events; the declared API matches actual behaviour.
- [ ] All interactive states (hover, focus-visible, active, disabled, loading, invalid) are designed, implemented and shown in the gallery.
- [ ] Content states (empty, loading, error) exist for data-bearing components (tables, lists, cards).
- [ ] Components consume tokens; no raw hex/px literals in component styles.
- [ ] Variant lists are closed and documented with usage rules, including when *not* to use each variant.
- [ ] Defaults are accessible and safe; no default requires overriding for correct keyboard or screen-reader behaviour.
- [ ] Native semantics are preserved under wrappers (real `<button>`, real `<a>`, labels tied to inputs).
- [ ] Library follows semantic versioning with a human-readable changelog; deprecations name replacements and removal versions.
- [ ] Maturity level is published per component and kept up to date.
- [ ] Icons ship through one component and tokenised sizes; decorative icons are hidden from assistive technology, meaningful ones are labelled.
- [ ] Components own their intrinsic responsive behaviour and are tested in containers narrower than any page provides.
- [ ] Every component imports no product-specific logic; the library stays domain-blind.
- [ ] Each component's documentation covers when to use, do/don't, anatomy, states, accessibility and content rules (see [Documentation](documentation.md)).

## 10. Related topics

- [Design tokens](design-tokens.md) — the visual decision layer components consume.
- [UI fundamentals](../ui-ux/ui-fundamentals.md) — the interface elements (buttons, forms, modals, alerts) that components implement.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — the engineering environment components ship into.
- [Documentation](documentation.md) — how component pages are structured and kept alive.
- [Governance](governance.md) — contribution, review and release processes around the library.
- [Visual consistency](visual-consistency.md) — the consistency guarantees a component system exists to provide.
- [Interaction design](../ui-ux/interaction-design.md) — the behaviour decisions components encode.
- [Interaction design](../ui-ux/interaction-design.md) — the behaviour decisions components encode.
- [Design system audit](../evaluation/design-system-audit.md) — evaluating components against these criteria at scale.
- [Responsive design](../ui-ux/responsive-design.md) — responsive behaviour expectations components must meet.

## 11. References

- GOV.UK Design System, *Button component*. https://design-system.service.gov.uk/components/button/ [accessed 2026-11-23]. Variant structure (default/start/secondary/warning/inverse), class naming, disabled-state caution, contrast requirement (WCAG 2.2 criterion 1.4.3), changelog ("Recent changes") and research sections.
- GOV.UK Design System, homepage. https://design-system.service.gov.uk/ [accessed 2026-11-23]. Component catalogue (~37 components), Styles/Components/Patterns split, maintenance by the Government Digital Service.
- Storybook, *Why Storybook* (official docs). https://storybook.js.org/docs/get-started/why-storybook [accessed 2026-11-23]. Quotes on the workshop model, stories as "a declarative syntax for supplying props and mock data", isolated-iframe rendering, Component Story Format, and auto-generated documentation.
- Atlassian Design System, *Foundations*. https://atlassian.design/foundations/ [accessed 2026-11-23]. Foundations topic coverage (tokens, spacing, colour, typography, elevation, border, radius, iconography, motion).
- Material Design 3 components and tokens. https://m3.material.io/foundations/design-tokens [accessed 2026-11-23; page body did not render in fetch]. Component-token tiering described from general professional knowledge [canonical].
- Nathan Curtis (EightShapes), *Team Models for Scaling a Design System*. https://medium.com/eightshapes-llc/team-models-for-scaling-a-design-system-2cf9d03be6a0 [search-verified 2026-11-23]. Federated vs centralised contribution context for the build/adopt/promote decisions in section 6.
- Maturity-level tiers (experimental/beta/stable/deprecated) and the rule-of-three heuristic: synthesis of professional convention across the systems cited above; no single standard exists.
