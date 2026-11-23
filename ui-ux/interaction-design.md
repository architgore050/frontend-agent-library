# Interaction Design

## 1. What is it?

Interaction design defines how a system behaves *over time* in response to the user: how quickly it responds, how it communicates that response, how change between states is animated, and how much of the system's capability is revealed at each moment. Where [UX fundamentals](ux-fundamentals.md) establishes what must happen (feedback, error prevention, recognition) and [UI fundamentals](ui-fundamentals.md) establishes what components look like, this file governs the fourth dimension — timing, motion and progressive disclosure — that turns a static screen into a usable product.

The material divides into four questions. How fast must the system react (latency and feedback timing)? How should transitions be staged (micro-interactions and animation)? When is motion justified at all (purpose, and `prefers-reduced-motion`)? And how much should be visible at once (direct manipulation versus menus, progressive disclosure)?

## 2. Why does it matter?

Time is invisible in a screenshot, yet it dominates perceived quality. A screen that is beautiful but responds in two seconds with no acknowledgement feels broken; a plain screen that responds instantly and moves coherently feels alive and trustworthy. Users judge systems on responsiveness more harshly than on almost any visual detail, and motion — used well — is the clearest channel for explaining cause and effect: where a panel came from, what the click affected, what is loading.

Motion also carries risk. Animation used decoratively delays users, distracts, and for some people causes real discomfort: people with vestibular disorders can experience dizziness or nausea from large-scale panning, parallax and scaling movement. Respecting the user's reduced-motion setting is therefore an accessibility obligation, not a stylistic preference — the mechanism is verified and standard (`prefers-reduced-motion`, section 5.3).

## 3. Core principles

### 3.1 Feedback timing and latency perception

The canonical numbers come from Nielsen's *Usability Engineering* (1993), building on Miller (1968) and Card, Robertson and Mackinlay (1991), and they have remained stable for decades [accessed, canonical]:

| Response time | User perception | Design requirement |
|---|---|---|
| 0.1 s | System reacts instantaneously; feels like direct manipulation | Show the result; no special feedback needed |
| 0.1–1 s | Delay noticed; flow of thought stays uninterrupted | Some acknowledgement is wise (button press state); no spinner needed |
| 1–10 s | Attention held, but waiting is felt | Show a busy indicator (spinner in the 2–9 s range per NN/g guidance [accessed]) |
| > 10 s | Attention drifts to other tasks | Percent-done progress bar, rough time estimate, and a way to cancel |

Two refinements worth carrying. First, NN/g's progress-indicator guidance sets the practical thresholds: immediate feedback for anything over about 1 second, looped animation for 2–9 second delays, and percent-done indicators for 10 seconds or more [accessed]. Second, some interaction-design literature and style guides quote finer bands (roughly 100 ms for "instant" and 100–300 ms for "immediate" feedback); treat those as conventional refinements of the same principle rather than separately verified facts — the verified core is the 0.1 s / 1 s / 10 s triple.

Nielsen also documents the counter-intuitive case: systems can be *too* fast. Instant transitions can cause users to miss what changed (overshooting scroll, content flashing by), so change should be made perceivable — with a brief animation or by timing from a real clock — rather than simply maximally fast [accessed]. Latency perception is also about *perceived* speed: starting a transition immediately (optimistic UI showing the item added to the basket before the server confirms) reads as faster than a slightly quicker response that starts late, provided failures are honestly rolled back.

A practical consequence: measure *perceived* latency — the time from gesture to first visible response — separately from total completion time. A search that streams partial results immediately feels faster than one that waits to return everything at once, even at identical total time; the first painted response buys most of the perceived speed. Optimistic rendering is the same trick applied to writes, with the honesty rule that failures must roll back visibly ([UI fundamentals](ui-fundamentals.md) treats the data-state side).

### 3.2 Micro-interactions

A micro-interaction is a single small feedback loop: flick a switch and it toggles with a 100 ms sweep, pull to refresh and the spinner engages, like a post and the heart pops. Their structure is usually described as trigger → rules → feedback → loop [canonical — Dan Saffer, *Microinteractions*]. Their purpose is not delight for its own sake: each micro-interaction confirms a cause (this press was registered), communicates an effect (the toggle is now on), and prevents error (the disabled state explains why nothing happened).

Rules of thumb for making them earn their place: they should finish within roughly 100–200 ms (conventional range — long enough to perceive, short enough to never queue), they should originate from the element the user acted on, and they should never block the next action. If you cannot say what a micro-interaction *communicates*, delete it — decorative motion that conveys nothing adds delay and cognitive noise.

Worked examples, each with the job it does: a button whose inline spinner replaces its label while submitting (confirms the press, blocks double-submit); a pull-to-refresh with a rubber-band release (makes the gesture's threshold visible); a filter chip that dims while its results load (keeps cause and effect connected); a form field that shakes once on invalid submit (locates the error without a page jump). Each finishes in well under a second, none blocks the next action, and removing any of them would cost information, not just charm.

### 3.3 Transitions and animation purpose

Animation in interfaces has legitimate, enumerable jobs:

| Purpose | Example | Typical pattern |
|---|---|---|
| State continuity | Panel slides from the edge it "lives" in | 200–300 ms ease-out |
| Cause and effect | Card expands into detail page (shared element) | ~300 ms; origin and destination visible |
| Attention | New item highlighted briefly on insert | Flash or fade, ≤ 1 s |
| Progress | Skeleton to content fade; progress bar | Tied to real progress |
| Orientation | Page transition preserving context | ~300 ms direction slide |

Conventional duration ranges (professional conventions, not verified laws): micro-feedback 100–200 ms; standard transitions 200–400 ms; larger spatial movements up to ~500 ms. Above roughly half a second, animation starts to feel like waiting. Conventional easing logic: *ease-out* (fast start, gentle landing) for entrances — the element appears responsive then settles; *ease-in* for exits; *ease-in-out* for elements moving between two visible positions; linear only for genuinely continuous processes (progress bars, spinners). The flat values matter less than the rule they encode: motion should explain where things come from and go, never simply decorate.

| Curve | Behaviour | Use for |
|---|---|---|
| `ease-out` | Fast start, decelerating landing | Entrances; elements appearing |
| `ease-in` | Slow start, accelerating exit | Exits; elements leaving |
| `ease-in-out` | Slow at both ends, fast in between | Elements moving between two visible positions |
| `linear` | Constant speed | Continuous processes (progress bars, spinners), never entrances |
| `cubic-bezier(...)` custom | Authored curve | Signature motion in a design system; keep a small fixed set |

Keep a *fixed set* of curves and durations in the design system rather than bespoke values per component — consistent motion reads as craft, inconsistent motion reads as noise.

### 3.4 Direct manipulation versus menus

Direct manipulation — pointing at and moving visible objects with immediate visible results — engages users more strongly than mediated command, because objects are visible, actions are reversible-looking, and feedback is continuous [canonical — Shneiderman's "direct manipulation" term; details of the model in UX fundamentals]. But it scales poorly to large collections (thousands of rows) and hides its actions behind gestures with no signifiers. Menus and commands scale to any breadth, self-document their options and suit beginners, but bury frequent actions behind navigation.

The professional pattern is *layered interaction*: direct manipulation as the primary model with menus/commands as accelerators. Drag a column to reorder a table (direct manipulation, discoverable, slow) and expose "Move left / Move right" in the header menu (mediated, fast once learned). The interaction-designer's test for each gesture-only action: is there a visible, reachable alternative for users who will never discover the gesture?

### 3.5 Progressive disclosure

Progressive disclosure reveals complexity in layers matched to the user's current need: show the common case first, hide the rare and advanced behind an explicit affordance ("More options", an accordion, a settings panel). It is the primary defence against Hick's-law overload and against minimalist design becoming *useless* design (heuristic 8's "minimalist" does not mean "featureless" [accessed]). What must be disclosed upfront: what the screen is for, the primary action, and enough context to decide. What may be deferred: advanced parameters, secondary metadata, help text.

Progressive disclosure has failure modes, and they are common enough to state as rules. It is not hiding *necessary* information (the price or the required field is never progressive); it is not breaking search (hidden content should still be findable — accordions that hide content from Ctrl+F need care); and it is not burying (more than two levels of hiding reliably strands users — heuristic 6 says recognition beats recall [accessed]).

The pattern set, with fit and risk:

| Pattern | Fit | Risk |
|---|---|---|
| Accordion | FAQ-like lists; genuinely parallel items | Content hidden from find-in-page; one-open-at-a-time feels restrictive |
| In-page tabs | Sibling views within one context | Non-active content invisible to scanning; overuse fragments pages |
| Wizard | Mandatory-order processes | Artificially linearises tasks that are actually free-form |
| "Show more" | Long feeds with a natural end-point | Endless appending defeats orientation and pagination |
| Advanced settings panel | Configuration genuinely rare for the audience | Buries settings that turned out to be common |
| Popover | Contextual detail without navigation | Fragile on touch; content truncation |

### 3.6 Timing and accessibility

Timing interacts with accessibility directly: interfaces that punish slow users — session dialogs that vanish before they can be read, carousels that rotate away, tooltips that disappear mid-read — fail users with motor or cognitive limitations. WCAG's timing criteria (2.2.1 Timing Adjustable: time limits can be turned off, adjusted or extended; 2.2.2 Pause, Stop, Hide: moving content that starts automatically and lasts more than five seconds can be paused or stopped) are the formal layer [canonical]; the design stance is the same as reduced motion: the user keeps control of the clock. Toasts that auto-dismiss should hover long enough to be read comfortably (conventionally ≥ 4–5 s, longer for longer text) and offer undo rather than punishing a missed read.

## 4. How it works

Interaction design is specified as a behaviour table, then implemented. For any component or flow: list every trigger (click, hover, key press, timer, system event), and for each, define the response (what changes, how fast, with what feedback, and what happens if it fails). This table — not a storyboard — is the deliverable that survives implementation, because it makes the invisible dimension explicit and reviewable.

Implementation splits by synchrony. *Synchronous* transitions (hover, focus, menu opening) are pure CSS and run at frame rate; *asynchronous* feedback (fetch results, saves) needs state machines that render pending/success/error states per [UI fundamentals](ui-fundamentals.md), with timing tuned to the verified bands in 3.1. The CSS mechanics — transitions, keyframe animations, `prefers-reduced-motion` media queries — are in [Frontend implementation](frontend-implementation.md); this file governs when and how long, that file how.

### 4.1 Specifying interactions as state machines

The most robust format for interaction behaviour is an explicit state machine: the states a component can occupy (idle, loading, loaded, error, empty), the events that move it between them (submit, success, failure, retry, timeout), and the required feedback per transition. A component specified this way has no undefined states — the classic "stuck spinner" and silent failure come from a state with no defined exit. The specification is also directly implementable: each state becomes a data attribute or class, each transition a handler, and the machine is testable by driving events and asserting state (mapping neatly onto the component state tables of [UI fundamentals](ui-fundamentals.md)). For anything with retries, timeouts or races — typeahead search, concurrent edits, payment flows — the state machine stops being documentation nicety and becomes the only reliable specification.

## 5. Practical application

### 5.1 Tuning feedback to the wait

Classify every async action by expected duration and give it the matching treatment: under 1 s — no indicator beyond the pressed state (a spinner that flashes for 200 ms is noise [accessed]); 1–2 s — button enters a loading state, label preserved; 2–9 s — spinner plus context ("Saving…" in the button or adjacent); 10 s or more — progress bar with rough estimate ("About 2 minutes remaining") and a cancel affordance; unbounded — step counts instead of percentages, since a lying percentage is worse than an honest count [accessed]. Where you can make the operation faster, do that first: an indicator is compensation, not a cure.

### 5.2 Choreographing transitions

For multi-element changes (list reordering, panel opening over a grid), sequence the motion: the *actor* moves first and fastest; secondary elements follow within ~50–100 ms of each other (conventional stagger). Keep every transition under ~400 ms so the user never waits on choreography, and design the *end* state first — animation is judged by where it lands, not how it travels. Transitions between routes should preserve spatial logic: a detail view sliding in from the right should exit to the right; back must visibly reverse forward, or the spatial metaphor collapses.

### 5.3 Reduced motion

Respect the operating-system setting. The verified mechanism: `@media (prefers-reduced-motion: reduce)` matches when the user has enabled reduce motion (widely available since January 2020; enabled via macOS "Reduce motion", Windows animation settings, or Android 9+ "Remove animations") [accessed]. The standard implementation removes or replaces non-essential motion while keeping opacity-based feedback (which does not trigger vestibular responses) — see the worked pattern in [Frontend implementation](frontend-implementation.md). What survives under reduced motion: instant state changes, opacity fades, focus indicators, progress indication. What should go: parallax, large scaling and panning, animated 3D, auto-playing decorative movement.

### 5.4 Deciding what to disclose

Audit each screen with three questions: what does a *first-time* user need to act (show it); what does a *returning* user need repeatedly (make it one click, then an accelerator — heuristic 7 [accessed]); what does an *expert* want (put it behind a stable affordance, never a moving menu). Collapse advanced fields behind "More options" only when they are genuinely rare for the primary audience; misclassifying a common task as advanced is the standard failure of this pattern.

### 5.5 Latency perception tactics

When the wait cannot be removed: acknowledge instantly (optimistic UI where rollback is safe); show structure before data (skeleton screens per [UI fundamentals](ui-fundamentals.md)); keep the user's focus busy (progress indicators reduce perceived time — NN/g cites a study in which users seeing a moving progress bar were willing to wait on average three times longer [accessed]); and never let the interface freeze silently — an unresponsive-feeling page is the strongest single signal of a broken system.

### 5.6 Conventional latency budgets for common operations

The verified 0.1/1/10-second limits govern feedback mechanics (3.1); teams also plan against conventional budgets for what operations should *cost* — starting points to adapt to context, not specifications:

| Operation | Conventional budget | Notes |
|---|---|---|
| Interaction acknowledgement (hover, toggle) | ≤ 100 ms | Instant-feel band |
| Search-as-you-type first response | ≤ 100 ms, input debounced ~300 ms | Debounce so half-typed words do not fire |
| Page-level meaningful content | ≤ 1 s | Skeletons for the remainder |
| Form validation response | ≤ 1 s after blur | Inline, adjacent to the field |
| Save / persist | ≤ 2 s, clear completion state | Optimistic only where rollback is safe |
| Bulk / report operations | Progress indication + cancel | Percent-done past 10 s [accessed] |

Where an operation cannot meet its budget, the honest responses are to make it faster (cache, precompute, paginate) or to reset expectation deliberately (state the wait, show progress) — never to hide the wait behind an indefinite spinner.

### 5.7 Interruptible, predictable motion

Two properties separate professional motion from gimmickry. *Interruptible*: a transition in progress must yield to the user's next action — a menu mid-open that closes instantly on a second click, a panel that can be re-opened during its own exit animation. Locked-in animations (an overlay that must play out before the page responds) make the interface feel like it is refusing input. *Predictable*: the same interaction always takes the same time and path; durations that vary with network luck or content length read as randomness, so distinguish the *animation* (fixed, authored) from the *wait* (variable, indicated). A timing review of a built screen walks every interactive element, records its response time and transition duration, and checks each against these two properties plus the budgets above.

## 6. Decision framework

For each new interaction, answer in order:

1. **What is the fastest honest response?** If under 0.1 s, no feedback apparatus is needed; if not, design the acknowledgement first, the speedup second.
2. **Which band does it fall into?** < 0.1 s / 0.1–1 s / 2–9 s / ≥ 10 s — apply the matching indicator (3.1).
3. **What does the transition explain?** Name the thing the motion communicates (origin, cause, change). If nothing, remove it.
4. **Is it discoverable?** Every gesture has a visible alternative; every hidden option has a stable affordance.
5. **Does it survive reduced motion?** Specify the `prefers-reduced-motion` variant alongside the default, not afterwards.
6. **Is the common case on the surface?** Progressive disclosure hides rarity, never necessity.
7. **Can it be interrupted?** Long animations and long operations both need an exit.

## 7. Examples

**A save that respects the bands.** An autosaving editor: keystrokes render instantly (0.1 s band, no indicator); after a pause the status line shows "Saving…" (entering the 1 s+ band); on completion it reads "Saved just now" and fades to neutral. If saving fails, the status turns persistent and red with a "Retry" button — the optimistic UI is rolled back honestly. Each element maps to a verified band; none of the feedback could be removed without a user-visible cost.

**A menu with a visible alternative.** A table row supports drag-to-reorder and a kebab menu with "Move up / Move down". A keyboard-only user, a touch user and a mouse user all have a path; the gesture costs experts nothing and hides nothing essential. This is layered interaction (3.4) working as designed.

**Progressive disclosure done and ruined.** A settings page that shows six common preferences with "Advanced preferences" behind one expander is right. The same page with four accordion levels — "Notifications" > "Channels" > "Email" > "Digest frequency" — buries a common setting three levels deep; users stop finding it (recognition over recall fails). The fix is re-grouping the top level, not more hiding.

**Reduced motion variant.** A modal that scales in from 0.96 with a 200 ms ease-out by default renders, under `prefers-reduced-motion: reduce`, as a simple opacity fade of the same duration. The affordance (a new layer appeared, background dimmed) is identical; the vestibular trigger (scaling) is gone.

**The honest rollback.** A "save changes" action renders optimistically (status line flips to "Saved" at once). On network failure it reverts to "Changes not saved — retry or copy your text", the textarea stays editable, and focus moves to the retry button. The optimism of 3.1 survives here only because the failure path is honest; the same optimism without rollback would display "Saved" for lost work — a trust defect wearing a timing costume.

**The filter that waits.** A results grid re-queries on every keystroke; results flicker under the user's typing. Repair: debounce input by ~300 ms (conventional), cancel stale requests, dim the grid while refreshing. Perceived speed improves more than actual speed does — the first response (the dim) is instant; completion follows the network.

**The carousel that failed 2.2.2.** An auto-rotating hero carousel changes slides every 4 s with no pause control; users attempting to read slide 3 watch it disappear. Repair per the timing-accessibility stance of 3.6: pause on hover/focus, a visible pause control, rotation stopped after any user interaction, and a reduced-motion variant that shows a static slide. Every requirement traces to a named criterion, not taste.

**A toast with undo, timed honestly.** Deleting a contact shows no confirmation dialog; instead the row disappears immediately and a toast reads "Contact deleted — Undo", persisting 5 s (long enough to read; the 2.2.2 spirit — the user controls the clock). After 5 s the deletion finalises silently. Fast for the common case, recoverable for the mistake, and honest about the moment the safety net closes — each property traceable to a verified rule in this file rather than to habit.

## 8. Common mistakes

- **Spinner for sub-second operations.** Flashes of animation under ~1 s are distracting and unreadable [accessed]; show nothing beyond the press state.
- **Endless spinner for long jobs.** Past ~10 s an indeterminate spinner reads as a frozen system; use percent-done or step counts [accessed].
- **Decorative motion everywhere.** Animation without a communicative job adds delay and dilutes the transitions that mean something.
- **No reduced-motion variant.** Shipping motion without a `prefers-reduced-motion` path excludes users with vestibular disorders; the media query is standard and cheap [accessed].
- **Hover-only interactions.** Menus and tooltips that exist only under the pointer are unreachable on touch and for keyboard users; pair hover with click/focus equivalents.
- **Burying the common case.** Progressive disclosure applied to frequent tasks strands users; audit by frequency, not by visual clutter alone.
- **Fixed animation durations regardless of distance.** A 300 ms slide that works for a small panel looks wrong for a full-page transition; scale duration with the distance travelled (conventional practice).
- **Hiding cost until the end.** Disclosing the price, the data usage or the destructive consequence only at the final step is dark-pattern territory, not progressive disclosure.
- **Debounce without cancelling.** Typeahead that fires debounced requests without cancelling earlier ones can render stale results out of order; cancel in-flight requests or ignore non-latest responses.
- **Locked-in animations.** Transitions that must play out before the interface accepts input make the design feel like it is refusing commands (5.7).
- **Auto-advancing content without pause controls.** Carousels and rotating banners that users cannot stop or slow violate the timing-accessibility stance of 3.6.

## 9. Evaluation checklist

- Every async action has feedback matched to its expected duration band (none < 1 s; spinner 1–9 s; percent-done ≥ 10 s [accessed]).
- Every transition communicates origin, cause or change; decorative-only motion removed.
- Standard transitions complete within ~200–400 ms; nothing animates longer than ~500 ms.
- `prefers-reduced-motion: reduce` variant exists for all non-essential motion; opacity-only under reduced motion.
- Every gesture-driven action has a visible, reachable alternative.
- Advanced or rare options are disclosed progressively; required information and costs are always visible before commitment.
- Optimistic UI is used only where failure can be rolled back visibly and honestly.
- Long operations offer cancellation or a clear escape; estimates are honest ("about…") rather than falsely precise.
- Multi-element choreography is staggered, ends within the budget, and the end state was designed first.
- Interface changes are perceivable at the "too fast" boundary (brief highlight or animation rather than instant swap [accessed]).

## 10. Related topics

- [UX fundamentals](ux-fundamentals.md) — feedback, affordances and heuristics underlying these timing rules
- [UI fundamentals](ui-fundamentals.md) — the component states that interaction timing animates between
- [Frontend implementation](frontend-implementation.md) — CSS transitions, keyframes and the `prefers-reduced-motion` pattern
- [Responsive design](responsive-design.md) — touch interaction and targets across devices
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — animation-related accessibility criteria in full
- [Gestalt and perception](../foundations/gestalt-and-perception.md) — why continuity and motion guide attention
- [Website visual QA](../evaluation/website-visual-qa.md) — verifying interaction behaviour in built pages

## 11. References

- Jakob Nielsen, "Response Times: The 3 Important Limits", Nielsen Norman Group, https://www.nngroup.com/articles/response-times-3-important-limits/ [accessed 2026-11-23] — 0.1 s / 1 s / 10 s limits; attribution to Miller 1968 and Card et al. 1991; "too fast" case
- Katie Sherwin, "Progress Indicators Make a Slow System Less Insufferable", Nielsen Norman Group, https://www.nngroup.com/articles/progress-indicators/ [accessed 2026-11-23] — looped vs percent-done thresholds, perceived-time study
- Jakob Nielsen, "10 Usability Heuristics for User Interface Design", Nielsen Norman Group, https://www.nngroup.com/articles/ten-usability-heuristics/ [accessed 2026-11-23]
- MDN Web Docs, `prefers-reduced-motion`, https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion [accessed 2026-11-23] — values, vestibular-disorder rationale, availability since January 2020
- Dan Saffer, *Microinteractions: Designing with Details*, O'Reilly, 2013 [canonical] — trigger/rules/feedback/loop structure
- Ben Shneiderman et al., *Designing the User Interface*, Pearson [canonical] — direct manipulation
- Jakob Nielsen, *Usability Engineering*, Academic Press, 1993 [canonical]
- Duration and easing ranges in sections 3.2–3.3 are conventional starting points drawn from platform style-guide practice (Apple HIG and Material Design motion guidance) — verify against the current platform guides for any given project [canonical]
