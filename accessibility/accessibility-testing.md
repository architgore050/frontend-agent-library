# Accessibility Testing

## 1. What is it?

Accessibility testing is the set of procedures that verify a design or implementation can actually be perceived, operated and understood by people with disabilities — not that it merely passes a linting score. It combines four complementary layers: **automated tool scans** (fast, partial), **manual keyboard testing** (fast, high-yield), **screen-reader testing** (slower, reveals the experience of blind and low-vision users) and **visual stress-testing** (zoom, reflow, spacing, colour). This file is the procedural playbook for those layers and for wiring them into design review; the criteria being tested are mapped in [WCAG fundamentals](wcag-fundamentals.md).

A core professional claim, supported by the tools' own documentation: automation finds only a subset of issues. WebAIM describes WAVE as helping authors by "facilitat[ing] human evaluation"; Deque sells semi-automated guided tests and manual expert testing on top of its own engine, and even markets its automated tools as finding "up to 80% of issues" in favourable stacks [accessed]. The practical rule stands regardless of the exact number: **tools find what is detectable; humans find what is usable.**

## 2. Why does it matter?

Testing is where accessibility claims become true. Without it, teams ship products that conform in the design file but fail in the DOM: components with perfect Figma states but no keyboard support, palettes verified in the brand deck but broken on real backgrounds, forms labelled in the component library but assembled without labels.

Three facts shape the whole discipline:

1. **Automated tools cannot test most of what matters experientially.** No tool can reliably judge whether an `alt` text is *appropriate*, whether focus order is *sensible*, whether a heading structure *makes sense*, or whether a flow is *usable* with a screen reader. WAVE's philosophy of focusing on issues that "impact end users" still requires human confirmation of its flags [accessed].
2. **The highest-severity failures are manual-only.** Keyboard traps, missing focus indicators on custom components, illogical reading order and confusing dynamic updates rarely trip automated rules.
3. **Testing at design time is the cheap pass.** A contrast check in the palette stage costs seconds; the same failure found in QA costs a redesign. This is why the workflow below starts in design review, not in the browser.

## 3. Core principles

1. **Layered strategy** — automate everything automatable, then spend scarce human attention where automation is blind: keyboard, screen reader, cognition, judgement calls (appropriate alt text, sensible headings).
2. **Test the task, not the page** — pick the critical user journeys (sign-up, ticket purchase, contact) and walk them end-to-end; page-by-page auditing misses process-level failures that break WCAG conformance of whole processes.
3. **Real settings, real tools** — test with the actual user setup: browser zoom, OS reduce-motion, a real screen reader with default speech rate (resist the urge to slow it down — users do not).
4. **Record evidence, not vibes** — a finding states the success criterion, the reproduction steps, the affected journey and a suggested fix; "it feels inaccessible" is not actionable.
5. **Shift left** — the same checks exist in design review (palettes, states, target sizes, content structure), in build (linting, unit-level ARIA assertions), and in QA (full pass); the cost of a failure rises at every stage.
6. **Test the promise, not the ideal** — judge against the version and level the project committed to, and record which permutations were covered (themes, breakpoints, locales); an audit that silently tested only desktop-light-mode says less than its page count suggests.

## 4. How it works

### 4.1 Manual keyboard testing walk-through

Unplug the mouse (or simply refuse to touch it) and perform the critical journeys. Keyboard testing is the highest-yield manual technique and takes 10–20 minutes per journey.

| Step | What to do | What it checks |
|---|---|---|
| 1. Load page | Observe where focus lands on first Tab | Should be first interactive element or a skip link; not `body` with no visible response |
| 2. Skip link | Tab once from the top | A "skip to main content" link appears and works (2.4.1) |
| 3. Walk the page | Tab through the *entire* page | Focus order matches visual/logical order (1.3.2, 2.4.3); nothing unreachable (2.1.1) |
| 4. Watch focus | At every stop, look at the indicator | Visible on every element (2.4.7); ≥ 3:1 (1.4.11); never obscured by sticky headers or banners (2.4.11) |
| 5. Operate controls | Enter/Space on buttons and links; arrows on menus, sliders, tabs; Esc on modals and dropdowns | Native keyboard behaviour or implemented ARIA pattern (2.1.1, 4.1.2); no traps (2.1.2) |
| 6. Forms | Tab into every field, submit empty, submit invalid | Labels announced logically; errors identified in text (3.3.1, 3.3.2); focus moves somewhere sensible |
| 7. Modals | Open, Tab inside, Esc out, reopen | Focus is contained then returned to the trigger (2.1.2) |
| 8. Zoom stress | Repeat the walk at 200% and 400% zoom | Nothing becomes unreachable; no page-level horizontal scroll at 1280 px/400% (1.4.10, 1.4.4) |

Common walk-through failures: focus jumps to the top after a dropdown opens; a carousel or date-picker that swallows Tab; `tabindex` values fighting the DOM order; icon-only controls with no accessible name (they read as "button, button, button").

**Touch and mobile additions.** Keyboard testing has a touch counterpart for the same modality rules: operate the journey with one thumb only (2.5.1 — no required multi-point gestures); check that any drag-only interaction (sliders, reordering, map panning) has a tap alternative (2.5.7); measure hit targets in the running layout, not the design file, and verify the 24 px spacing exception never leaves two small controls touching (2.5.8); rotate the device to confirm orientation works both ways (2.5.2); and check that tilt or device-motion triggers have a UI alternative (2.5.4). Also test the OS-level settings from Section 4.5 on a real device — emulators do not reproduce text-size overrides, reduce-motion and display scaling together.

**Dynamic content needs a second keyboard pass.** The static walk proves the rendered page; the dynamic pass proves the behaviour: open every dropdown, trigger every loading state, submit every form error, dismiss every modal, and re-walk from wherever focus lands. The failures that live only here — focus landing nowhere after a dialog closes, a spinner that steals focus every second, a newly revealed section that focus skips past — are the ones that make keyboard users abandon the flow entirely, and no automated scan executes interactions for you.

### 4.2 Screen-reader basics (NVDA and VoiceOver)

Screen-reader testing verifies what assistive technology actually announces. The two most-accessible options for testers: **NVDA** (free, Windows) and **VoiceOver** (built into macOS and iOS). Basic command vocabulary below is stable and long-standing but should be verified against current documentation before training others [canonical — verify with WebAIM's NVDA/VoiceOver guides or the vendors' key-command lists].

**NVDA (Windows):** the modifier key ("NVDA key") is Insert or Caps Lock depending on layout. Essential moves: start/stop speech (NVDA+Space or Ctrl), next/previous heading (H / Shift+H), heading levels (1–6 keys), next/previous link (K), next/previous button (B), next landmark (D), elements list (NVDA+F7) for a full outline, form mode toggling (NVDA+Space). Typical session: open the Elements list first — headings and landmarks reveal the page skeleton in seconds — then walk the journey linearly with the arrow keys, listening to every announced name, role and state.

**VoiceOver (macOS):** the modifier is Ctrl+Option ("VO"). Essential moves: navigate (VO+Arrow keys), next heading (VO+Command+H), rotor (VO+U) for headings/links/landmarks/tables, read all (VO+A). On iOS, swipe gestures mirror these and the screen curtain (triple-press side button, if configured) removes visual crutches.

| Task | NVDA | VoiceOver (macOS) |
|---|---|---|
| Next/previous heading | H / Shift+H | VO+Command+H / VO+Shift+Command+H |
| Headings of a given level | 1–6 number keys | VO+Command+Level (where offered) |
| Next/previous link | K / Shift+K | VO+Command+L (links list varies) |
| Landmarks/regions | D / Shift+D | VO+U rotor, choose Landmarks |
| Elements list (full outline) | NVDA+F7 | VO+U (rotor) |
| Buttons | B / Shift+B | Rotor → Buttons |
| Toggle forms/focus mode | NVDA+Space | VO+Shift+Down Arrow within a control |
| Read from current position | NVDA+Down Arrow (say-all) | VO+A |
| List of form fields | NVDA+F7 → Forms | Rotor → Form controls |

Treat this table as a session starter, not a reference: key bindings evolve between releases, so confirm against the current WebAIM guides or vendor command lists before writing training material [canonical — verify]. The *method* is stable regardless of bindings: outline first (headings and landmarks), then linear walk, then interaction. A good session sounds like a confident narrator: it names every control with its state ("Filters, collapsed, button"), never announces an unlabeled gap ("button", "blank", "graphic"), and moves through the page in the same order your eyes would. Silence is a finding too — a chart that announces nothing, a modal whose opening goes unannounced, a search result count that arrives unheard all fail perception, not operation. Keep the speech rate at default: comprehension at natural speed is the actual user experience, and slowing it down hides timing problems in dynamic announcements.

What to listen for, in priority order: page title is descriptive; heading structure is logical and complete; images announce their *purpose* (or nothing, if decorative) — not "image", not filenames; form fields announce label + required + error state; buttons announce name *and* state (expanded, selected, loading); dynamic updates (toasts, result counts) are announced (4.1.3) without stealing focus; link text is meaningful out of context ("read more" × 12 is a failure).

### 4.3 Automated tools: what each catches and misses

All three verified tools below are legitimate daily drivers; their differences are scope and presentation, not truth.

**WAVE (WebAIM, Utah State University)** [accessed]. A suite including a web tool (paste a URL) and browser extensions for Chrome, Firefox and Edge — the extensions matter because they work on password-protected, local and highly dynamic pages that the web tool cannot reach. WAVE overlays icons directly on the page, flagging errors (missing alt text, empty buttons, broken labels), contrast errors, alerts (areas needing human review), plus structural features and ARIA usage. Strengths: the in-page overlay shows *where* issues are, and its "alerts" categories deliberately route humans to judgement calls. Misses: everything interaction-dependent — focus behaviour, keyboard traps, dynamic announcements — and it cannot confirm alt-text *quality*.

**axe-core (Deque)** [accessed]. The open-source rules engine ("released as open source in 2015") that powers Deque's axe DevTools browser extensions (Chrome, Firefox, Edge) and the wider axe product family, and — via its APIs — most CI/CD accessibility pipelines. Strengths: developer-oriented output (rule ID, impact, element, fix guidance), zero-false-positive design philosophy, embeddability in unit and end-to-end tests and build pipelines. Misses: same class as all automation — cognitive, visual-judgement and interaction-dependent criteria; Deque fills those with its guided (semi-automated) tests and manual expert testing.

**Lighthouse (Chrome)** [accessed]. An open-source auditing tool built into Chrome DevTools (Lighthouse tab → Analyze page load), runnable via `npm install -g lighthouse` and the CLI, as a Node module for CI, or through PageSpeed Insights. Its accessibility category reports failed audits with fix guidance. Strengths: zero setup, present in every Chrome install, CI-friendly. Misses: it scores only a subset of checks and is known within the docs ecosystem as one signal among many — a high Lighthouse accessibility score is *not* a conformance claim; it leaves manual checks listed in the report unscored.

**Cross-cutting what-automation-misses list** (use it as the manual agenda): appropriate alt text; sensible heading hierarchy and landmark structure; focus order and visibility; keyboard operability and traps; dynamic status announcements; contrast on gradients, images and composited overlays; target size and spacing in real layouts; confusing labels, error messages and flows; motion and autoplay controls.

Mapping criteria to layers makes the division of labour explicit (qualitative synthesis of the sources above — individual tools change their rule sets between releases):

| Area | Automated (WAVE / axe / Lighthouse) | Manual only |
|---|---|---|
| Missing alt attributes, empty buttons/labels | Detectable | Judging *appropriateness* |
| Text contrast against flat backgrounds | Detectable | Gradients, images, overlays, composited states |
| Non-text contrast (borders, icons, focus rings) | Partial | Real-state judgement in running UI |
| Missing labels on inputs | Detectable | Label clarity and instruction quality |
| Heading structure existence | Detectable | Sensibleness and hierarchy quality |
| Keyboard reachability | Partial (focus-order rules) | Traps, order sensibleness, custom widget behaviour |
| Focus visibility | Partial (some rules) | Contrast, obscuration by sticky content (2.4.11) |
| Target size | Partial | Real layout collisions and spacing-exception judgement |
| Reflow/resize/spacing tolerance | Not detectable | Entirely manual (zoom and override tests) |
| Status messages, dynamic announcements | Not detectable | Entirely manual (screen-reader session) |
| Language correctness, link purpose, error clarity | Partial to none | Entirely manual (content review) |

Reading automated results well is a skill of its own. WAVE's overlay distinguishes its icon categories deliberately: red icons are errors (unambiguous failures such as missing alt text or empty labels), blue icons are accessibility *features* worth recognising (landmarks, skip links — presence, not problems), orange icons are alerts that require a human decision (heading structure, link-text quality), and the contrast panel reports actual ratios for text it can measure. Axe DevTools output, by contrast, reads like a code review: rule ID, WCAG reference, impact, offending selector and fix suggestion, designed for triage in an issue tracker. Lighthouse sits between, with each failed audit linking to its rationale. Understanding the category semantics prevents the two classic overreactions: "fix every red and orange blindly" (some alerts are fine once reviewed) and "clear the blue icons" (they usually mark the good things you built).

### 4.4 Contrast checking

For colour pairs, use a checker that reports the numeric ratio and the AA/AAA verdict for normal and large text: WebAIM's contrast checker and the contrast readouts built into Chrome/Firefox DevTools colour pickers are the standard choices [canonical — verify current UI]. Rules of interpretation (from the WCAG Understanding pages, see [Accessible colour](accessible-colour.md)): ratios are exact and unrounded; check the worst point under gradients and images; check composited colours under overlays; component boundaries and focus indicators need 3:1 against adjacent colours, which is a *different* measurement than text contrast.

A quick DevTools procedure keeps this routine rather than heroic: inspect the text element, open the colour swatch beside the `color` value, and read the contrast line against the computed background; DevTools flags AA/AAA and lets you suggest compliant replacements. For pairs the inspector cannot resolve (text over images, tokens resolved at runtime), sample the rendered pixels and compute from the formula instead. Record the numbers, not just the verdict — recorded ratios are what turn a design system's pairs into reusable, pre-verified tokens (see [Colour in code](../colour/colour-in-code.md)).

### 4.5 Visual stress-testing

| Test | How | Checks |
|---|---|---|
| Zoom 200% | Browser zoom to 200% (1.4.4) | No clipped or lost content, no broken layouts, no disabled zoom |
| Reflow 400% | 1280 px viewport at 400% zoom ≡ 320 CSS px width (1.4.10) | Single-dimension scrolling; tables may scroll in own container |
| Text spacing | Apply line height 1.5×, paragraph 2×, letter 0.12×, word 0.16× (1.4.12) — bookmarklet or injected CSS | No clipping, overlap or lost controls |
| Reduced motion | Enable OS "Reduce motion"; reload (maps to `prefers-reduced-motion`) | Parallax, scaling and autoplay motion stop or degrade gracefully |
| Dark mode | Toggle `prefers-color-scheme` or the site theme switch | Contrast and non-text contrast re-verified on dark surfaces |
| Forced colours / high contrast | Windows High Contrast mode or `forced-colors` emulation | Content remains visible; icons and states not colour-dependent |

Implementation pattern for reduced motion (media feature is Baseline, widely available since January 2020, per MDN [accessed]):

```css
/* motion effects by default */
.panel-enter {
  animation: slide-in 0.4s ease-out;
}

/* user opt-out: replace movement with opacity */
@media (prefers-reduced-motion: reduce) {
  .panel-enter {
    animation: fade-in 0.4s ease-out;
  }
}
```

### 4.6 Content and cognitive testing

Automated tools and even screen-reader sessions under-test the Understandable principle, so it needs its own short procedure. Walk each template checking: the page title and `lang` match the content (3.1.1); link text works out of context (2.4.4 — read the link list alone); error messages say what happened and what to do next (3.3.1/3.3.3), in plain language; instructions appear before the fields they govern (3.3.2); nothing changes context without warning on input (3.2.2 — focus jump or auto-submit on select is the classic failure); navigation and help stay in consistent places across pages (3.2.3/3.2.4); and abbreviations, jargon and acronyms are expanded on first use where the audience requires it (3.1.4). Reading-level criteria (3.1.5) are AAA and rare, but for legal, medical or compliance-heavy content, providing a plain-language summary is the working interpretation. A useful heuristic borrowed from plain-language practice: could a tired reader on a phone complete this journey without re-reading anything?

### 4.7 A design/frontend pass checklist (condensed)

1. **Design artefacts**: contrast pairs verified; target sizes ≥ 24 × 24 px (44 × 44 px primary); states for hover/focus/disabled/error designed; error message placement defined; heading and content structure drafted.
2. **Build**: semantic elements used (no div-buttons); landmarks and one `h1`; labels wired; `lang` set; viewport allows scaling; `prefers-reduced-motion` honoured; status messages announced.
3. **QA pass**: WAVE or axe scan on every template; fix or triage every flag; keyboard walk of every journey; screen-reader walk of one journey per template; visual stress tests above.
4. **Record**: findings logged with criterion numbers; fixes verified by re-running the failing test, not by assuming.

## 5. Practical application: integrating accessibility into design review

The cheapest testing happens before code exists. A five-minute review gate per screen catches the majority of design-stage failures:

- **Contrast**: every text/background pair and component boundary measured (design-tool plugins with WCAG contrast readouts make this routine — verify the plugin's maths against a trusted checker before adopting it).
- **States**: does the design *show* focus, hover, disabled, error? A state that does not exist in the file will not exist in the build.
- **Targets**: icon buttons and list-row controls measured against 24 × 24 px minimum, 44 × 44 px preferred for primary actions.
- **Structure**: heading outline and content order sketched in the file; alt-text strategy noted for imagery; chart labels decided (linking to [Data visualisation](../information-design/data-visualisation.md)).
- **Content**: link text, button labels and error messages written for meaning ("Add 2 × adult tickets", not "Click here").

Then attach the automated layer to the pipeline (axe in unit tests, Lighthouse in CI) so regressions are caught mechanically, and reserve human sessions for journeys, screen readers and judgement calls. Schedule a full manual pass at every major release, not only at launch — regressions arrive with every redesign.

### 5.1 Recording findings so they get fixed

A finding is only useful if someone can reproduce and verify it. One row per issue, structured like this:

| Field | Example |
|---|---|
| Summary | "Checkout button has no visible focus indicator" |
| Location | `/checkout`, "Buy tickets" button, step 2 of 3 |
| Reproduction | Tab to the button; `outline: none` in `.btn:focus` |
| Criterion | SC 2.4.7 (AA); failure technique F78 |
| Severity | Blocker (keyboard users cannot aim their action) |
| Suggested fix | Replace with `:focus-visible` outline at ≥ 3:1 (C40/C45) |
| Verification | Re-run keyboard walk step 4 on the fixed build |

Findings follow the severity order in 6.3, and the audit itself gets a cadence: full pass per major release, automated scan per merge, keyboard walk per new component, screen-reader walk per new template. The pass closes only when every open finding has an owner, a severity and a verification method recorded in the table above. Grouping findings by component rather than by page turns the audit into a component-library work plan, which is usually the cheapest repair path.

### 5.2 Wiring automation into the build

Keep automation as a regression trip-wire, not a quality certificate. A minimal, tool-agnostic pipeline shape:

```bash
# run once per pull request; fail the build on new errors
npx axe-cli https://staging.example.org/tickets --exit
npx lighthouse https://staging.example.org/ --only-categories=accessibility \
  --output=json --output-path=./lighthouse.json
```

The axe CLI and Lighthouse CLI are the Node-based entry points for both tools [accessed]. Two cautions: automated runs against a staging URL only cover publicly rendered HTML — authenticated states and interaction-dependent content need scripted browser runs of the same engines; and scores must be *compared to a baseline*, because absolute scores shift as rules evolve. Pair the pipeline with the manual gates from Section 4.6.

### 5.3 Testing with real users

Simulation finds conformance failures; people find usability failures that conformance never captures. Where the stakes justify it (public ticketing, government-facing, accessibility-first brands), schedule sessions with actual assistive-technology users: they surface real settings mixes (screen reader + zoom + high contrast), task strategies, and the frustration points no ruleset encodes. Compensation and recruitment through disability organisations is standard practice; plan extra time, and never treat one participant as representative of a whole disability group [canonical professional practice]. Even without a formal study, a standing feedback route in the accessibility statement (see [WCAG fundamentals](wcag-fundamentals.md)) brings real-world failures back to the team.

## 6. Decision framework

### 6.1 Which layer when

| Situation | Primary method | Why |
|---|---|---|
| Every pull request / template change | Automated (axe/Lighthouse/WAVE) | Fast, repeatable, catches the detectable subset |
| Any new or modified component | Keyboard walk | Highest-yield manual test; interaction bugs are invisible to tools |
| New page template or journey | Keyboard + screen-reader walk | Verifies announced structure and the end-to-end experience |
| Palette, theme or dark-mode change | Contrast checker on every pair + visual tests | Ratios change silently; overlays recomposite |
| Content-heavy release | Screen reader on headings/links/alt + readability review | Structure and text quality dominate |
| Touch-first feature (drag, pinch, sliders) | Touch-device session + pointer-gesture checks (2.5.x) | Modality rules need real input hardware |
| Theme, density or token change | Full contrast/focus/target re-verification | Permutations silently recompose every pair |
| Before major release | Full pass (all layers) + one session with real assistive-technology users if possible | User testing reveals what simulation misses |

### 6.2 Tool choice

Use WAVE for fast visual diagnosis during design QA (the overlay is its differentiator), axe-core in code and CI (developer-grade output, pipeline integration), Lighthouse for a quick recurring score and regression trip-wire (built into Chrome). They overlap by design — running two is normal; disagreeing results usually mean one measured compositing or state the other did not. What matters more than the choice is the discipline around it: one designated tool per layer with a documented configuration, so scan results stay comparable over time, and every tool's output is treated as *findings to triage*, never as a to-do list executed without review — each flag is either confirmed as a real issue or dismissed with a reason, and both outcomes are recorded.

### 6.3 Triaging findings

Severity order: (1) lock-outs (no keyboard path, unlabelled required field, trap); (2) blockers for whole groups (contrast under threshold on primary text, missing alt on meaningful images, target size under 24 px on core controls); (3) friction (predictability, announcements, spacing tolerance); (4) polish (AAA enhancements). Fix categories 1–2 before release, log 3–4 with owners and dates.

## 7. Examples

**Ten-minute pass on an event page.** WAVE extension flags two empty buttons (icon-only, no name) and three contrast errors on a hero gradient; keyboard walk finds focus lost after "Filters" opens and the sticky header covering the focused "Buy tickets" link (2.4.11); at 400% zoom the ticket cards overlap. Four findings, all fixed in a day; without the pass, all four would have shipped.

**Screen-reader session on a form.** NVDA announces "edit text, blank" for the email field (no label association), the error message appears but is never announced (not a status message), and the submit button reads "button". Fixes: `<label for>`, `aria-describedby` or role="status" for the error, and real text in the button.

**Zoom test on a schedule grid.** At 320 CSS px the day-columns force page-level horizontal scrolling — a 1.4.10 failure. The columns are not a data table, so the exemption does not apply; the fix stacks the columns vertically on narrow viewports, keeping the table view at larger widths.

**Dark-mode regression.** A theme update inverts surfaces but not the focus token: the light-mode ring at 3.2:1 against white measures roughly 1.8:1 against the new dark navy — invisible exactly where keyboard users need it. The catch procedure is the pair-list re-verification from [Accessible colour](accessible-colour.md) (5.2 dark-mode notes) plus a keyboard walk in dark mode; the fix is a dedicated dark focus token. The lesson generalises: every theme, density or viewport change re-opens the contrast, focus and target-size tests even though no feature code changed.

**Content review on a programme page.** Tools report zero errors, but the link list reads "Read more" nine times with no distinguishing context (2.4.4), the filter select auto-submits and reloads the page on change without warning (3.2.2), and the "VIP packages" section is announced only as a bold paragraph because nobody used a heading (2.4.6, 1.3.1). None of this is machine-detectable today; all of it is found in the content-and-cognitive walk of 4.6, which is why that walk exists.

## 8. Common mistakes

- **Treating a 100/100 Lighthouse score as conformance** — it audits a subset and leaves manual checks unscored [accessed]; the score is a regression trip-wire, not a certificate.
- **Testing only the home page.** Failures cluster in flows: checkout, search, forms. Audit journeys.
- **Screen-reader theatre**: running a reader at slow speed with speech preview instead of navigating by heading and landmark like a real user; the two experiences differ completely.
- **Automated-scan complacency on both sides**: dismissing scans as useless (they catch real, cheap-to-fix classes) or trusting them fully (they miss the experiential majority).
- **Skipping zoom/spacing tests** because "the layout is responsive" — responsiveness and reflow tolerance are different properties (see [Accessible typography](accessible-typography.md)).
- **Fixing without re-verifying** the exact failing test, allowing silent regressions.
- **Testing with dev-only data** — empty states, long German-style strings, 12-character names and error states never get exercised.
- **One-and-done audits**: an audit without a re-test plan decays immediately; findings need owners, and fixes need the failing test re-run on the next build.
- **Forgetting the theme/density matrix**: light, dark, compact and default spacing are separate permutations; a change to any one re-opens contrast, focus and target-size checks.
- **Ignoring the tester's own OS settings** — reduce-motion, forced colours and dark mode are one toggle away and catch whole classes of issues.

## 9. Evaluation checklist

- [ ] Automated scan (WAVE or axe) run on every template; every error either fixed or triaged with a reason.
- [ ] Full keyboard walk completed for every critical journey: reachable, visible, non-obscured focus; Enter/Space/Esc/arrows behave; no traps.
- [ ] Screen-reader session completed on one journey per template: title, headings, landmarks, labels, alt text, states, status announcements verified.
- [ ] Contrast pairs verified numerically, including gradients, overlays, hover/focus states and dark mode ([Accessible colour](accessible-colour.md)).
- [ ] Visual stress tests executed: 200% zoom, 400%/320 CSS px reflow, text-spacing overrides, reduced motion, forced colours.
- [ ] Findings logged with success-criterion numbers, repro steps and severity; fixes re-verified with the failing test.
- [ ] Design-review gate exists: contrast, states, targets, structure and content checked before build.
- [ ] Automated checks wired into CI so regressions fail the build.
- [ ] Findings tracked with owners and re-verified fixes; audit re-run after any theme, template or component-library update.
- [ ] A full manual pass scheduled for every major release; user testing with assistive-technology users planned where feasible.

## 10. Related topics

- [WCAG fundamentals](wcag-fundamentals.md) — the criteria each test maps to.
- [Accessible typography](accessible-typography.md) — the spacing, zoom and reflow properties being tested.
- [Accessible colour](accessible-colour.md) — the measurement rules behind contrast checking.
- [UI fundamentals](../ui-ux/ui-fundamentals.md) — component states that keyboard testing exercises.
- [Website visual QA](../evaluation/website-visual-qa.md) — the broader review pipeline this plugs into.
- [Web typography](../typography/web-typography.md) — implementation details of the type system under test.
- [Data visualisation](../information-design/data-visualisation.md) — testing charts for accessible meaning.

## 11. References

- WebAIM (Utah State University), *WAVE Accessibility Evaluation Tool* — tool suite, forms (web tool, extensions for Chrome/Firefox/Edge, APIs), human-evaluation philosophy — <https://wave.webaim.org/> [accessed 2026-11-23]
- Deque Systems, *axe* product page — axe-core engine (open-sourced 2015), axe DevTools extensions, guided/manual testing layers, "up to 80% of issues" claim, CI/CD integration — <https://www.deque.com/axe/> [accessed 2026-11-23]
- Google, *Lighthouse Overview* — DevTools/npm CLI/Node/PageSpeed Insights workflows, audit categories — <https://developer.chrome.com/docs/lighthouse/overview/> [accessed 2026-11-23]
- MDN Web Docs, *prefers-reduced-motion* — values, OS settings mapping, Baseline status (January 2020), implementation pattern — <https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion> [accessed 2026-11-23]
- W3C, *Understanding WCAG 2.2* pages for 1.4.10, 1.4.12 and 2.4.7 — test procedures referenced above — <https://www.w3.org/WAI/WCAG22/Understanding/reflow.html>, <https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html>, <https://www.w3.org/WAI/WCAG22/Understanding/focus-visible.html> [accessed 2026-11-23]
- WebAIM NVDA and VoiceOver screen-reader guides; vendor key-command lists [canonical — verify current commands before training]
- Percentage-of-issues figures beyond the Deque claim: not verified this session; treat any "automation finds X%" figure as tool-vendor marketing until checked [search-verified caveat]
