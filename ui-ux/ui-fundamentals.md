# UI Fundamentals

## 1. What is it?

A user interface (UI) is built from components — reusable units such as buttons, inputs, cards, tables, modals and alerts — each with an internal anatomy (its parts and their arrangement), a visual hierarchy (how strongly it pulls the eye) and a set of states (how it responds to the user and to the system). UI fundamentals is the discipline of assembling these units so a screen communicates instantly: what is here, what can I do, what is happening, what went wrong. This file is the component-level companion to the principle-level treatment in [UX fundamentals](ux-fundamentals.md) and the behaviour-over-time treatment in [Interaction design](interaction-design.md).

A component is more than a styled shape: it is a contract. It promises that clicking does what it says, that its states reflect reality, and that it behaves consistently wherever it appears. Interfaces feel professional when that contract is kept across every instance, and feel broken when a single instance violates it.

## 2. Why does it matter?

Components are where abstract principles become pixels. A heuristic like "recognition rather than recall" only exists on screen because a button visibly declares itself, a field visibly shows what it wants, and an error visibly says what to fix. Component quality is also where interfaces most visibly succeed or fail: users do not perceive your grid or your token system — they perceive that the button works when clicked, the form forgives a mistake, the modal can be escaped, and the empty state explains what to do next.

For an AI agent producing interfaces, component literacy is the highest-leverage knowledge in this library. Most generated UI fails on predictable component defects — a hover state nobody defined, a disabled button that still submits, a table that collapses into unreadable soup, an error message that says "Invalid input" with no cure. Mastering the anatomy, states and composition rules below prevents exactly those defects. Component anatomy and variant systems are also the raw material of design systems: see [Design tokens](../design-systems/design-tokens.md) for how their values are encoded and governed.

## 3. Core principles

### 3.1 Component anatomy

Most components decompose into a small vocabulary of parts. Naming them precisely is what makes variants, documentation and consistent implementation possible:

| Part | Example (button) | Example (input field) |
|---|---|---|
| Container | The button box (padding, radius, fill) | The field box and border |
| Content | Label text or icon | The value typed by the user |
| Leading / trailing adornment | Icon before or after the label | Search icon left; clear button right |
| Helper text | Rarely used on buttons | Persistent hint below the field |
| Status affordance | Spinner inside the button while submitting | Valid checkmark or error text below |
| Interaction surface | The whole hit region (≥ 44×44 pt; see [Responsive design](responsive-design.md)) | The whole field, including label click target |

Two anatomy rules prevent most component bugs. First, the *interaction surface* should be at least as large as the visual container — a small visible icon with a generous invisible hit area is correct; the reverse is a tap-miss factory. Second, every anatomy slot is optional *by design*: document which slots a variant supports, so an input without helper text is a deliberate minimal variant rather than an accidental omission.

#### A component documented as markup

Anatomy is best fixed in markup, where slots, states and accessibility land in one place:

```html
<button class="btn btn--primary" type="submit" aria-label="Create project">
  <span class="btn__icon" aria-hidden="true">+</span>
  <span class="btn__label">Create project</span>
</button>

<!-- Field anatomy: label, input, adornment, helper, error -->
<div class="field">
  <label class="field__label" for="card-number">Card number</label>
  <div class="field__control">
    <input id="card-number" class="field__input" inputmode="numeric"
           autocomplete="cc-number" aria-describedby="card-hint card-error" />
    <span class="field__adornment" aria-hidden="true"><!-- card icon --></span>
  </div>
  <p class="field__hint" id="card-hint">16 digits, no spaces needed.</p>
  <p class="field__error" id="card-error" hidden>Enter the 16-digit number from your card.</p>
</div>
```

The naming (`btn__icon`, `field__error`) is the BEM convention — block, element, modifier — a widely used convention for keeping anatomy explicit in class names [canonical]. Note that the state hooks (`hidden`, `aria-describedby`, `aria-label`) are part of anatomy, not decoration: a component spec that describes only the visual slots is incomplete.

### 3.2 Visual hierarchy in interfaces

Hierarchy is the deliberate ranking of what the eye attends to first, second, third. In interfaces it is produced by four levers — size, weight, colour/contrast and position — supported by grouping (proximity and enclosure; see [Gestalt and perception](../foundations/gestalt-and-perception.md)) and whitespace (see [Spacing and proportion](../layout/spacing-and-proportion.md)). A screen has one primary action, a handful of secondary ones, and everything else must recede. Hierarchy is how a screen answers "what am I supposed to look at?" before the user has to think.

The practical test is the *five-second view*: screenshot the screen, shrink or blur it, and check that the primary action and the page's purpose still dominate. If everything shouts, nothing is heard — equal visual weight for all elements is the most common hierarchy failure, and is why "one primary button per view" (section 5.2) exists.

### 3.3 States — the discipline that makes or breaks UI

Every interactive component exists in a series of states, and the interface's perceived quality is determined less by its default appearance than by how well its states are designed. The canonical set:

| State | When it applies | Design requirement |
|---|---|---|
| Default | Resting, before interaction | Baseline appearance; action clearly signified |
| Hover | Pointer over the element (mouse only) | Subtle change (fill shift, underline); must not move layout |
| Focus | Keyboard focus lands on it | Visible, high-contrast indicator (outline or ring); never removed (see [WCAG fundamentals](../accessibility/wcag-fundamentals.md)) |
| Active | Being pressed | Slightly darker/pressed appearance; instant feedback |
| Disabled | Action unavailable now | Reduced contrast but still ≥ 3:1 (WCAG); cursor not-allowed; keep tooltip or explanation of why |
| Loading | Action submitted, awaiting result | Inline spinner or progress; input blocked or clearly queued |
| Error | Validation or action failed | Error text + colour + aria indication; field remains editable |
| Success / selected | Action completed or item chosen | Confirmation cue; selected state distinct from hover |

Why states make or break UI: states are where feedback happens (Nielsen's visibility of system status [accessed]). A button without a hover state feels dead under the mouse; without a focus state it is unreachable by keyboard users and fails WCAG 2.4.7; without a loading state users click again and double-submit; without a disabled-with-explanation state users click an inert control repeatedly and lose trust. State design is cheap — a few CSS rules per component — and its absence is the signature of amateur work. The rule for agents: when generating any interactive component, enumerate the full state table *before* styling, and never ship a component whose states are undefined.

### 3.4 Composition: screens are sentences

Screens communicate through composition, not just components. The established conventions: one primary action per view; the primary content in the largest, highest-contrast area; supporting metadata smaller and quieter; destructive actions separated from constructive ones; related controls grouped (proximity). These are professional conventions, not laws — dashboards legitimately show many equals, and editorial pages may deliberately subvert hierarchy — but deviation should be a choice with a reason, not drift.

### 3.5 Consistency as the multiplier

Composition rules earn their keep only when applied *consistently*: the same component behaves identically on every screen, the same information always sits in the same region, the same severity always wears the same colour. Consistency is what turns individual correct decisions into a system users can learn once and predict forever — it is heuristic 4 (consistency and standards [accessed]) operating at component scale. The practical instrument is a component inventory: a generated or maintained list of every component variant in use, reviewed so that three near-identical "buttons" collapse into one component with variants. Where a design system exists ([Design tokens](../design-systems/design-tokens.md)), the inventory is its first audit surface; where it does not, an informal inventory page still catches the drift that otherwise accumulates invisibly.

## 4. How it works

A component-based workflow, whether in code or in a design tool, follows the same steps:

1. **Inventory** the actions and information the screen must present.
2. **Select components** for each need — form field for input, card for a preview unit, alert for a system message — preferring the established component over an invented one, because established components carry users' expectations (heuristic 4, consistency and standards [accessed]).
3. **Define the state table** for each instance (section 3.3), including which states are actually reachable (a form field inside a read-only view needs no error state).
4. **Compose the layout** on a grid ([Grid systems](../layout/grid-systems.md)) with a spacing scale, ranking elements by the hierarchy levers.
5. **Wire the states** in code: CSS pseudo-classes (`:hover`, `:focus-visible`, `:active`, `:disabled`) for synchronous states, and JavaScript-driven classes or data attributes (`data-loading`, `aria-invalid`) for asynchronous ones (see [Frontend implementation](frontend-implementation.md) for the CSS mechanics).

In code, states split into two kinds. *User-input states* are free and synchronous — the browser fires `:hover`, `:focus`, `:active` for you. *Data states* (loading, error, empty, success) depend on the application and must be explicitly rendered by the developer. Interfaces break most often at the seam between the two: a form that clears its pending state on validation error but not on network error, or a list that renders nothing (rather than an empty state) when the query returns zero rows.

## 5. Practical application

### 5.1 Forms

Forms are the highest-stakes component family: they are where users enter effort, make commitments and meet most errors.

**Labels and placeholders.** Every field needs a persistent, visible label placed outside or above the field. Using the placeholder as the label is harmful — the NN/g analysis documents that hints vanish on typing, users cannot check their answers afterwards, error recovery requires re-reading each field, and pre-filled-looking fields are skipped [accessed]. Placeholders are acceptable as *supplementary* examples or format hints ("e.g. name@company.com") alongside a real label; essential instructions must live outside the field and persist. Floating labels (which move above the field on focus) are an improvement but can still read as pre-filled data.

```html
<label for="email">Work email</label>
<input id="email" type="email" autocomplete="email"
       aria-describedby="email-hint email-error" />
<p id="email-hint">We only use this for order updates.</p>
<p id="email-error" hidden>Please include an “@” — e.g. name@company.com.</p>
```

**Validation timing.** Three defensible timings, each with a trade-off: (a) *validate on blur* — the default choice; catches errors as the user leaves the field, before they have scrolled away; (b) *validate on submit* — least intrusive; correct for short forms, but defers all feedback; (c) *live validation while typing* — only for constraints the user cannot self-check (username availability, password strength), and only *after* the user has finished typing or left the field; validating a half-typed email address is noise. Never validate aggressively before first interaction ("Prerequisite for a good experience: the user has not yet been scolded"). These timings are professional convention with solid rationale, not laws — the convention exists because eager validation is one of the most-complained-about form behaviours.

**Error messages.** An error message answers three questions in the user's vocabulary: what went wrong ("Enter a valid email address"), why it matters or what the format is ("It should look like name@company.com"), and where to act (inline, adjacent to the field, not a summary at the top with no anchor). Never blame the user; never use codes alone; never rely on colour alone. Keep the user's input — never clear a field because it failed validation. Multi-field failure gets both an inline message per field and a summary with jump links; success gets an equally clear confirmation.

#### Form structure patterns

Beyond individual fields, whole-form structure decides whether users finish:

- **One column is the safe default.** Single-column forms are completed faster and with fewer errors than multi-column layouts (the pattern is a professional convention with strong tracking-history behind it); two columns only for genuinely parallel short fields (first name / last name).
- **Group related fields** with spacing or a `<fieldset>` with a legend — grouping is read as meaning (Gestalt proximity; see [Gestalt and perception](../foundations/gestalt-and-perception.md)).
- **Split long forms into a wizard** with a visible step indicator and per-step validation, or reveal optional sections progressively ([Interaction design](interaction-design.md)); keep the total effort visible ("Step 2 of 3") so users can budget their attention.
- **Ask only what the flow needs now.** Every additional field has a completion cost; optional fields that no one uses are a design debt, not a feature.
- **Support machine completion**: correct `type` and `autocomplete` attributes so browsers and password managers fill correctly; never break paste into fields (blocking paste is a hostile pattern that "protects" against nothing and burdens everyone).
- **The primary action states its consequence**: "Pay £24.00" rather than "Submit", so the commitment step names its own cost.

### 5.2 Buttons

Button variants encode an action hierarchy:

| Variant | Role | Typical treatment |
|---|---|---|
| Primary | The one main action of the view | Solid fill (brand colour), strongest contrast |
| Secondary / outline | Alternative, less frequent action | Outline or tinted fill |
| Tertiary / text | Minor or auxiliary actions | Text-only, hover underline or tint |
| Destructive | Deletion, irreversible actions | Red fill or red text, separated spatially |
| Ghost / icon | Compact toolbars, repeated rows | Icon + tooltip; only when the meaning is unambiguous |

Rules that carry real weight: **one primary button per view** (two primaries cancel each other out); primary placed where the eye lands last in the reading order of its group (bottom-right in dialogs for LTR languages is the conventional seat); destructive actions physically separated from confirmatory ones; labels are verbs ("Create project", not "OK"); and the button's own loading state replaces its label with an inline spinner and disables re-submission. The disabled state should ideally say *why* — "Submit" disabled with a helper line "Required fields missing" beats a grey button the user pokes in confusion.

Icon-only buttons are a special case worth their own rule: an icon without a text label must carry an accessible name (`aria-label`) and, unless the icon is conventionally unambiguous (magnifier for search, X for close), a tooltip or adjacent text. Ambiguous icon-only buttons save space and cost comprehension — a bad trade except in toolbars where repetition would bury the meaning.

### 5.3 Navigation components

Three components carry wayfinding, each answering a different question (structure models themselves are in [Information architecture](information-architecture.md)):

- **Bars** (top navigation, side navigation): the persistent map of the product's top-level areas. Current location is marked (active state); on mobile, bars collapse into a menu — but the current area must remain visible even collapsed.
- **Tabs**: views *within* one context — sibling content the user switches between without leaving the page. Current tab is visually anchored; tab count beyond roughly 5–7 signals the content wants grouping instead.
- **Breadcrumbs**: the hierarchical path ("Home / Women / Shoes / Running") for deep trees; every level is a working link, the current level is plain text. They answer "where am I?" in a way top navigation cannot for deep pages.

Convention to respect: tabs switch content without navigation (do not reload the page or change the URL context users expect to persist); breadcrumbs mirror the URL and information hierarchy, not the user's accidental path. Accessibility essentials: `<nav>` landmarks, `aria-current="page"` for the active item, and full keyboard operability.

One adjacent component decision belongs with navigation: **how long lists end**. Pagination (discrete pages, addressable URLs, a clear total) suits search results and archives; **infinite scroll** suits discovery feeds where users never need to reach "the end" or compare positions; **"Load more"** is the compromise that preserves page position without paginating. The deciding questions: does the user ever need to bookmark or share a specific position (yes → pagination or anchor-preserving load-more), and does footer content matter (yes → infinite scroll is hostile, because the footer recedes forever as the user approaches it).

### 5.4 Cards

A card is a self-contained preview unit — media, title, description, metadata, and at most one or two actions — that invites a single "open" behaviour. Cards work because enclosure plus padding makes each unit perceptually whole (Gestalt common region; see [Gestalt and perception](../foundations/gestalt-and-perception.md)). Anatomy discipline: every card in a grid has the same internal structure even if slots are empty; the whole card is the click target when there is one action; hover elevates or tints rather than moves content. The most common card failure is content anarchy — three cards with different image heights, tag rows and button placements in one grid, which destroys the scannability that justified cards.

```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 1.5rem;               /* verified behaviour of gap: see Frontend implementation */
}
.card:hover { box-shadow: 0 4px 12px rgb(0 0 0 / 0.12); }
```

### 5.5 Tables

Tables present multi-record data for comparison and lookup. The rules that keep them usable: align text left, numbers right (magnitudes compare down the column when units align); one idea per column with a self-explanatory heading; a sticky header for long lists (implemented with `position: sticky` — mechanics in [Frontend implementation](frontend-implementation.md)); row hover to hold the reading line; primary actions per row visible, secondary ones in an overflow menu; and a defined mobile behaviour — usually converting to stacked cards or hiding low-priority columns, not horizontal scroll of a 12-column monster. Sorting indicators and row-selection states are part of the state table, not afterthoughts. Dense data also raises accessibility needs: real `<table>` markup with `<th scope>` — never a grid of `<div>`s.

Choosing the presentation for structured records is a small decision framework of its own: a **table** when users compare values across records (numbers, dates, statuses side by side); **cards** when each record is rich enough to deserve media and its own actions and comparison is secondary; a **list** when each record is one or two lines and scanning names matters. The failure is forcing one shape everywhere — cardifying a pricing comparison table destroys the comparison; tabulating product galleries destroys the browsing.

### 5.6 Modals

A modal dialog interrupts the flow to demand a decision: confirm a destructive action, complete a focused sub-task, or display an urgent message. Because interruption has a real cognitive cost, the bar for using one is: the task cannot complete in-context, and the user must not be able to ignore it. Anything that could be a side panel, an inline section or a toast should be. Escape hatches are non-negotiable: a visible close control, `Escape` key dismissal, click-outside dismissal for simple confirmations, focus moved into the dialog on open and returned to the trigger on close, and background scrolling disabled. Modals must never trap keyboard focus or stack casually; a modal opening a modal is a design smell. For forms inside modals, keep the primary action bottom-right and never let the dialog content scroll out of view of its own submit button.

The modal family also has lighter relatives, and picking the right one lowers the interruption cost:

| Variant | Interruption level | Use for |
|---|---|---|
| Confirmation dialog | High | Irreversible or expensive actions, with explicit consequences |
| Form / task dialog | High | Focused sub-task that must not be ignored (rename, move) |
| Side panel / drawer | Medium | Detail views where the list should remain visible |
| Bottom sheet (mobile) | Medium | Actions and filters within thumb reach |
| Popover | Low | Compact controls and previews anchored to a trigger |
| Toast / snackbar | Low | Transient outcomes (auto-dismiss; undo offered where relevant) |

### 5.7 Alerts

Alerts are system-initiated messages with severity semantics that users learn once and trust forever:

| Severity | Meaning | Typical colour | Persistence |
|---|---|---|---|
| Info | Context the user should know | Neutral/blue | Dismissible |
| Success | Action confirmed | Green | Auto-dismiss or brief |
| Warning | Proceeding may cost something | Amber | Stays until resolved or acknowledged |
| Danger | Something failed or will fail | Red | Stays until resolved |

The contract: never use danger colour for a warning-grade event, or users will learn that red means noise. Alerts state the event, its consequence and the remedy in one or two lines; inline alerts appear adjacent to what they concern (a payment failure belongs next to the payment section, not floating at the top of a long page); and every persistent alert carries a dismiss action unless ignoring it has real consequences. Alert floods — several simultaneous banners — mean the design should consolidate into one message with a list.

Placement semantics deserve their own line: *inline* (inside the section it concerns) for contextual failures; *banner* (top of the content area) for page-level conditions like unsaved changes or maintenance; *toast* (bottom corner) for outcomes the user just triggered, never for information they need to find later — a toast is the least findable placement and the first thing users miss. Choosing banner when toast would do, or vice versa, is the most common alert-placement error.

### 5.8 Empty, loading and error states

These three "nothing to show" states are where interfaces quietly lose users, because the designer saw them last and least:

- **Empty states** (zero results, first use, cleared inbox) must do three jobs: explain *why* it is empty ("No projects match 'finance'"), offer *the way out* (clear the filter, create the first project), and set expectations for what will appear here. An empty state that is a shrug ("Nothing here") is a dead end; one with a primary action converts.
- **Loading states** communicate that work is in progress. Verified NN/g guidance: give feedback for any action longer than about 1 second; looped spinners suit delays of roughly 2–9 seconds; percent-done progress bars suit 10 seconds or more [accessed]. **Skeleton screens** — grey shapes previewing the coming layout — are the preferred pattern for content whose structure is known before its data, because they reduce perceived wait and avoid layout shift when content arrives; a spinner is appropriate when the arriving layout is unknown. Skeletons should mirror the real layout closely, or the reveal will feel like a bait-and-switch.

A related choice is **optimistic versus pessimistic rendering**. Optimistic UI shows the expected result immediately (the "like" increments, the item appears in the list) and rolls back visibly on failure — it feels fast but demands honest failure handling; pessimistic UI waits for the server and shows the loading state instead — slower-feeling, simpler to keep truthful. The decision rule: optimism only where rollback is cheap and visible (likes, adding to a list, marking read), pessimism where correctness carries the interaction (payments, destructive actions).
- **Error states** distinguish *what* failed for the user: input errors (fixable inline), connectivity errors (offer retry), permission errors (say who to contact), and server errors (apologise, keep the user's work, offer a way back). Every error state must preserve the user's entered data and name a concrete next step.

### 5.9 Selection controls

Choosing the right control for a choice is a small but high-frequency decision, and the wrong control makes simple choices slow or ambiguous:

| Control | Fit | Anti-fit |
|---|---|---|
| Checkbox | One independent yes/no option among several | Instant state change (a switch reads as applied immediately) |
| Switch/toggle | A setting that applies immediately | Options requiring a submit step (state mismatch: looks applied before it is) |
| Radio group | One choice among 3–5 visible options | Long lists (use a select) |
| Select/dropdown | One choice among many (>5) | Options users compare (values hidden until opened) |
| Segmented control | 2–5 mutually exclusive *view* modes | Actions (they look like views, not verbs) |
| Slider | Continuous magnitude with a visible range | Precise discrete entry (pair with a numeric input) |

Two contract rules keep these honest. A **switch** promises immediate application — if the change actually needs a "Save" step, a checkbox is the honest control. A **dropdown** hides its values behind a click, so it is wrong for choices users need to compare (dates on a booking form); show options as radios or a visible list whenever comparison matters.

### 5.10 Working with component libraries

Most real work happens on top of an existing library (Material UI, Carbon, Polaris, shadcn-style collections, or an in-house system). The library changes the job from *designing components* to *selecting, configuring and extending them well*:

| Situation | Practice |
|---|---|
| The library has the component | Use it unmodified; restyle only via its supported theming surface (tokens, CSS variables) |
| The library is close but not exact | Compose its primitives; check the variant/prop documentation before forking |
| No library component fits | Build custom, but match the library's state table, sizing and a11y contract so it reads as native |
| Library defaults look generic | Customise the token layer (colour, radius, type), not one-off overrides on instances |

The failure modes are consistent: fighting the library with per-instance overrides (which forks its look without inheriting its fixes), and silently forking a component (which splits future bug fixes). Where a design system owns tokens, the library consumes them — see [Design tokens](../design-systems/design-tokens.md) and, for the code mechanics, [Frontend implementation](frontend-implementation.md).

## 6. Decision framework

Choosing and configuring components, in order:

1. **Is there an established component for this?** Use it. Custom components pay a discoverability tax (heuristic 4 [accessed]).
2. **What is the action hierarchy?** One primary; secondaries demoted; destructive isolated.
3. **Which states are reachable?** Enumerate default/hover/focus/active/disabled/loading/error/success for every interactive instance; anything reachable must be designed.
4. **Interrupt or inline?** Modal only if the flow must stop; alert only if the system must speak; otherwise inline content.
5. **What does the empty path show?** For every list, table and search: the zero-results design.
6. **What is the failure path?** For every submit and fetch: the error design, including data preservation.
7. **Does the whole still have hierarchy?** Apply the five-second view (3.2) after composition.

## 7. Examples

**A state-complete button.** One button, full state table:

```css
.btn-primary { background: var(--color-primary); color: #fff; }
.btn-primary:hover  { background: var(--color-primary-strong); }
.btn-primary:focus-visible { outline: 2px solid var(--color-primary); outline-offset: 2px; }
.btn-primary:active { transform: translateY(1px); }
.btn-primary[disabled] { background: var(--color-neutral-300); cursor: not-allowed; }
.btn-primary[data-loading="true"] { pointer-events: none; opacity: 0.8; }
```

The `:focus-visible` variant styles keyboard focus without punishing mouse users — the current convention for reconciling visibility of focus with aesthetics; removing focus styles entirely fails WCAG 2.4.7.

**Form error recovery.** A user enters "zoe.example.com" into an email field, submits. Weak version: red border only, summary "Form contains errors". Strong version: on blur, inline text "Include an '@' — e.g. zoe@studio.com", `aria-invalid="true"`, focus moved to the field, typed text preserved. The strong version repairs the error in one gesture; the weak one costs a hunt across the form.

**Modal versus inline.** "Rename tag" — a two-character edit — belongs inline (click the name, edit in place), because interruption outweighs focus benefit. "Delete workspace and all its 14 projects" belongs in a modal that names the count and requires typing the workspace name, because the cost of a mistake is catastrophic and irreversible. Same component family, opposite verdicts — the decision framework (section 6, point 4) makes the difference explicit.

**Sticky header collision.** A page combines a sticky global header and a sticky table header. Both implement `position: sticky; top: 0` and, on scroll, the table header scrolls *under* — or worse, over — the global header, because both compete for the same viewport edge. Repair: offset the table header by the global header's height (`top: var(--header-height)`), give the global header the higher z-index token, and verify at the smallest tested viewport where heights differ. The defect is invisible in the default screenshot and obvious at 320 px — which is why state and stacking checks belong in the viewport matrix of [Responsive design](responsive-design.md).

**The switch that lied.** A settings form used switches for "Email me order updates" and "Share usage data", with a Save button at the bottom. Users flipped the switch, assumed the change applied, and left — half of them later reported "I turned that off". The control promised immediate application; the form delivered it only on Save. Repair: checkboxes (honest about deferred application) or per-switch immediate saves (honest about immediacy). Either repairs the contract; keeping the switch with a Save button does not.

## 8. Common mistakes

- **Placeholder-as-label.** Documented harms: vanishing hints, unverifiable answers, harder error fixing, fields mistaken for pre-filled [accessed]. Persistent labels always.
- **Focus states removed for aesthetics.** Keyboard users lose the only indicator of position; fails WCAG. Use `:focus-visible` if the default outline offends.
- **Disabled with no explanation.** A greyed button is a wall. Add a helper line or tooltip stating the missing condition.
- **Every action opens a modal.** Interruption overload; users lose their place and context. Reserve modals for decisions the user cannot ignore.
- **Alerts with wrong severity.** Red banners for routine information train users to ignore red.
- **Skeletons that lie.** Skeleton shapes wildly different from the arriving content cause a jarring reflow; mirror the real layout or use a spinner.
- **Tables as decoration.** Data tables built from divs with no `th`, no alignment rules and no sticky header on long lists; comparison becomes impossible.
- **One state table for all contexts.** A field in a read-only view, a button in a toolbar, a card in a dense list — each needs only its reachable states; enforcing the full table everywhere bloats interfaces.
- **Inventing components.** A custom "pill-with-chevron-multiselect" where a `<select>` works costs users a learning curve and you weeks of state bugs.
- **Switches in forms with a Save step.** Immediate-application affordance over deferred application; the state users see is not the state the system has (5.9).
- **Dropdowns for comparable choices.** Dates, plans and sizes hidden behind a closed select force memory and re-opening; show values.
- **Toasts carrying information users must find again.** A toast disappears — anything that matters after a few seconds belongs inline or in a persistent place.

## 9. Evaluation checklist

- Every interactive component has a written or coded state table covering default, hover, focus, active, disabled and its data states.
- Focus is always visible; `:focus-visible` used where mouse aesthetics matter.
- Exactly one primary button per view; destructive actions separated and labelled with verbs.
- Every form field: persistent label, persistent hints where needed, placeholder used only as example/format hint.
- Validation runs on blur or submit (never eagerly before first interaction); error messages name the problem, the fix, and appear adjacent to the field.
- Modals: visible close, `Escape` works, focus is trapped while open and restored on close, background scroll locked.
- Alerts: severity colour matches semantics; each persistent alert dismissible unless action is required; inline where possible.
- Every list, table and search has a designed empty state with an offered action.
- Async actions > 1 s show a state (spinner 2–9 s, progress bar ≥ 10 s [accessed]); user data survives every error path.
- Tables: left-aligned text, right-aligned numbers, sticky headers for long lists, defined mobile behaviour.
- Selection controls match their semantics: switches only for immediate application; dropdowns only where comparison does not matter; every icon-only button has an accessible name.
- Modals used at minimum interruption level (popover/drawer where a dialog is overkill); toasts only for transient outcomes.
- Form structure: one column by default, grouped fields, correct `type`/`autocomplete`, paste never blocked, primary action names its consequence.
- The five-second view passes: primary action and page purpose dominate the visual field.

## 10. Related topics

- [UX fundamentals](ux-fundamentals.md) — the principles (feedback, affordances, heuristics) these components implement
- [Interaction design](interaction-design.md) — timing, motion and micro-interactions for these components' states
- [Frontend implementation](frontend-implementation.md) — the CSS that realises these components
- [Responsive design](responsive-design.md) — component behaviour across viewports and touch targets
- [Design tokens](../design-systems/design-tokens.md) — encoding component colour, spacing and type decisions as reusable values
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — contrast, focus visibility and semantic requirements in detail
- [Web typography](../typography/web-typography.md) — type choices inside components
- [Colour accessibility](../colour/colour-accessibility.md) — contrast ratios behind state and severity colours
- [Website visual QA](../evaluation/website-visual-qa.md) — systematic checking of built screens against this checklist

## 11. References

- Jakob Nielsen, "10 Usability Heuristics for User Interface Design", Nielsen Norman Group, https://www.nngroup.com/articles/ten-usability-heuristics/ [accessed 2026-11-23]
- Katie Sherwin, "Placeholders in Form Fields Are Harmful", Nielsen Norman Group, https://www.nngroup.com/articles/form-design-placeholders/ [accessed 2026-11-23]
- Katie Sherwin, "Progress Indicators Make a Slow System Less Insufferable", Nielsen Norman Group, https://www.nngroup.com/articles/progress-indicators/ [accessed 2026-11-23]
- Jakob Nielsen, "Response Times: The 3 Important Limits", Nielsen Norman Group, https://www.nngroup.com/articles/response-times-3-important-limits/ [accessed 2026-11-23]
- Apple, Human Interface Guidelines, Buttons, https://developer.apple.com/design/human-interface-guidelines/buttons [search-verified 2026-11-23] (44×44 pt hit region)
- Google, Material Design, Spacing methods, https://m2.material.io/design/layout/spacing-methods.html [search-verified 2026-11-23] (48×48 dp touch targets, 8 dp separation)
- MDN Web Docs, CSS `gap`, https://developer.mozilla.org/en-US/docs/Web/CSS/gap [accessed 2026-11-23]
- Don Norman, *The Design of Everyday Things*, Basic Books, 2013 [canonical]
- W3C, Web Content Accessibility Guidelines (WCAG) 2.2 [canonical] — focus visible (2.4.7), contrast minima (1.4.3), target size (2.5.8); details in [WCAG fundamentals](../accessibility/wcag-fundamentals.md)
- Design-system component documentation conventions (Material Design, Apple HIG, Carbon, Polaris) [canonical]
- Nick Wirth / BEM community, BEM naming convention [canonical] — block/element/modifier class naming used in the anatomy example
