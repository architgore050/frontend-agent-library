# Website Visual QA

## 1. What is it?

A quality-assurance method and checklist for the visual layer of a website: spacing and alignment, type scale adherence, colour token adherence, component state coverage, responsive behaviour, image quality, consistency against the design system, contrast, and broken-layout detection. It complements functional QA (does the checkout work?) with visual QA (does the checkout *look* correct everywhere?). It is the web-specific application of [design-quality-framework.md](design-quality-framework.md), and it assumes any design system in play has its own audit method ([design-system-audit.md](design-system-audit.md)).

Visual QA is a pass over a *built* site — real browser, real data, real devices — not a critique of static mockups. Its output is a defect list in the standard review report format (§6).

## 2. Why does it matter?

Websites accumulate visual defects in a way static artefacts do not: content management systems inject unpredictable text lengths, third-party embeds arrive with their own styles, one engineer ships a page with hardcoded colours while the rest use tokens, and a component update silently changes a button on forty pages. Each defect is individually small; collectively they erode trust — users read visual inconsistency as unreliability.

For an agent evaluating its own or a team's output, visual QA is also the point where the design's theory becomes measurable: the type scale, spacing scale and colour tokens defined during design ([../design-systems/design-tokens.md](../design-systems/design-tokens.md)) are either obeyed in the DOM or they are not. The accessibility criteria (contrast, focus, reflow) are tested here in their real rendered state, using the methods of [../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md).

## 3. Core principles

**Principle 1 — Audit against a defined system, and say what the system is.** Every adherence check (spacing, type, colour) requires a reference: the token list, the type scale, the grid spec. Where no system exists, the QA report states that explicitly and evaluates internal consistency instead (same rule applied everywhere) — you cannot fail "token adherence" for a site that has no tokens.

**Principle 2 — Test rendered states, not just the default view.** The default page state is maybe 20% of the visual surface. Buttons hover, inputs error, menus open, images fail to load, text overflows. State coverage (§5.4) is the part of visual QA most often skipped and most often where majors hide.

**Principle 3 — Test at real widths, down to 320 px.** WCAG 1.4.10 reflow requires content to reflow at 320 CSS px width (equivalent to a 1280 px viewport at 400% zoom) without horizontal scrolling. This is an objective standard, not a convention, and it doubles as the extreme-case stress test for layout robustness.

**Principle 4 — Measure, don't eyeball.** DevTools inspection, computed styles and screenshots with overlays turn "looks off" into "this heading is 27 px — not on the 24/32 scale". The QA report carries numbers.

**Principle 5 — Distinguish defect from decision.** Some apparent defects are deliberate (intentional truncation, a one-off hero without a grid). The QA reviewer records them as such — flagged for design sign-off — rather than as failures, mirroring the objective/subjective split in [design-quality-framework.md](design-quality-framework.md).

## 4. How it works

The QA workflow is a fixed route through the site, repeated at a fixed set of viewports, with per-dimension checks performed once per page type (homepage, listing, detail, form, content page) rather than on every page. The full procedure:

1. **Prepare:** inventory page types; define the viewport set (e.g. 320, 360, 768, 1024, 1440 px — minimum set includes 320 for reflow, a mid phone, a tablet, and one desktop); gather the reference system (tokens, scale, grid spec) or note its absence.
2. **Sweep each page type** at each viewport, running the checks in §5.
3. **Exercise states** on interactive components (§5.4).
4. **Record defects** with location, viewport, evidence (number/screenshot) and severity per the model in [design-quality-framework.md](design-quality-framework.md).
5. **Report** using the template in §6; prioritise; re-evaluate after fixes.

## 5. Practical application — the checks

### 5.1 Spacing and alignment audit

What to check: vertical rhythm (are gaps between sections and elements from the spacing scale or divisibly related, e.g. multiples of 8 px — conventional), consistent margins per page type, edge alignment (columns, cards, icons, text baselines against the grid), and equal-width elements actually equal in the DOM.

How: pick one page per type; inspect computed margins/paddings of ~20 representative elements in DevTools and list the distinct values; compare against the scale. Overlay a screenshot with column guides at each viewport to catch misaligned edges (tolerance ≤ 1 px screen, excluding intentional optical alignments).

Pass criteria: all sampled spacing values are on-scale (or a documented exception); grid edges align within tolerance; no orphan misalignments introduced by CMS content.

Typical defects: magic numbers (17 px, 23 px gaps); two card components with different internal padding; a section whose left edge sits 4 px off the grid at exactly one breakpoint.

### 5.2 Type scale adherence

What to check: every rendered font size, weight, family and line height against the defined scale ([../design-systems/design-tokens.md](../design-systems/design-tokens.md) §typography). Body text ≥ 16 px (conventional floor for web); line length ≈ 45–75 characters for measure of running text (conventional); real font files loading (no faux bold/italic from synthesised styles); headings form a coherent ladder (h1 > h2 > …) and match semantic heading levels.

How: script or manually collect `getComputedStyle` font properties for all text elements on each page type; deduplicate; compare to the scale. Check the mobile widths separately — scale steps often differ there by design, which must itself be documented.

Pass criteria: zero sizes off-scale; heading ladder monotonic; body meets the floor; measure within range on text-heavy pages.

Typical defects: hardcoded `font-size: 18.5px` from an old design; h3 visually larger than h2 (ladder break); a CMS-rich-text style that bypasses the scale; faux-bold Arial rendering because the brand font failed to load.

### 5.3 Colour token adherence

What to check: every used colour value against the token list — backgrounds, text, borders, shadows, SVG fills. Any hardcoded value duplicating a token is drift; any value not in the system is a stray colour. Verify the semantic colours (success/warning/error) use the semantic tokens, not ad-hoc reds and greens.

How: sample computed styles (or crawl the compiled CSS) for all `color`, `background-color`, `border-color`, `fill`, `stroke`; deduplicate; diff against tokens. Then check *pairing*: for each text/background combination actually rendered, compute the contrast ratio — 4.5:1 normal text, 3:1 large text and UI components (WCAG AA; method in [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md)). Automated checkers (axe, Lighthouse) catch most pairs; manual sampling catches pairs inside images and embeds.

Pass criteria: zero off-token values (or all exceptions documented); zero failing contrast pairs among *actually rendered* combinations, including hover/disabled states.

Typical defects: `#4a5568` hardcoded on one page; disabled-button text at 2.1:1; placeholder text in an input under 4.5:1; link colour inside a CMS-styled article failing on the tinted background.

### 5.4 Component state coverage

What to check, per interactive component (buttons, links, inputs, selects, checkboxes, tabs, accordions, cards, nav items): **default, hover, focus-visible, active/pressed, disabled, loading (if async), error (inputs), and selected/on states** — each visually designed, token-driven, and distinguishable.

How: exercise every state manually per component type; screenshot each; verify focus is visible via keyboard tabbing (focus-visible styling present — never `outline: none` without a replacement); verify disabled communicates disabled *and* still meets ≥ 3:1 for its boundary (WCAG non-text contrast — verify current criterion text); verify error states convey meaning with more than colour alone (icon + message text).

Pass criteria: full state matrix exists for each component family; focus visible on every interactive element; no state uses colour as the sole signal.

Typical defects: no focus style at all (keyboard users lost); hover state defined but active missing (no press feedback); error state = red border only; loading state = layout jump because no reserved space.

### 5.5 Responsive checks

What to check, at each viewport in the set, down to 320 px: no horizontal page scroll (the reflow standard); no clipped, overlapping or wrapped-into-illiteracy elements; images and video scale preserving aspect ratio (`max-width: 100%`); tables either scroll inside their own container or adapt; navigation usable at touch width (target size ≥ 44 × 44 px conventional, ≥ 24 × 24 px per WCAG 2.5.8 AA — verify against current WCAG); breakpoints produce deliberate layouts, not accidental reflows; content priority preserved (hero/message first on mobile).

How: resize across the set; at 320 × 256 CSS px explicitly test reflow per the WCAG condition (1280 px window at 400% zoom is an equivalent condition); screenshot each breakpoint and compare structure; inspect for `overflow-x` leaks with a quick `document.querySelectorAll('*')` scroll-width script or DevTools.

Pass criteria: no horizontal scroll at any tested width; all content reachable and readable; tap targets pass; no element overlaps at any width.

Typical defects: a fixed-width sidebar widget forcing scroll at 320 px; a logo lockup overlapping the hamburger at 360 px; a data table blowing out the article column; an absolutely-positioned badge colliding with wrapped text on tablet.

### 5.6 Image and media quality

What to check: resolution appropriate to rendered size (no visible upsampling; no 2 MB hero where ~150–200 KB WebP/AVIF suffices — conventional target); correct aspect ratios (no stretched faces/logos); alt text present for meaningful images (decorative images `alt=""`); logo and icon assets crisp at 2× DPR; video posters and caption availability.

How: audit key media per page type: natural size vs. rendered size; file weight; visual inspection at 200% zoom for artefacts; check `alt` attributes in the DOM.

Pass criteria: no visible quality defects; weights reasonable for the medium; alt text complete (functional QA overlaps here — record visual anomalies only, per scope).

### 5.7 Consistency against the design system

What to check: same component, same look — buttons of the same variant identical across pages; spacing above/below headings uniform; icon style singular; date/number formats uniform; page headers/footers identical module-for-module. Where the design system defines the component ([design-system-audit.md](design-system-audit.md)), the live site must match the documented anatomy.

How: pick the three most reused components; visit five instances each across different pages; diff screenshots and computed styles. Check cross-page invariants (header, footer, card grids) pixel-side-by-side at one fixed viewport.

Pass criteria: instances of the same variant are visually and computationally identical; no page-local overrides outside documented exceptions.

Typical defects: a landing-page button with custom radius; two pagination styles on different listing pages; a section that re-implements the card component locally with 2 px different padding.

### 5.8 Broken layout detection

What to check — the extreme-content stress pass, the part functional QA never covers: longest realistic strings (very long words, unbroken URLs, long names) overflowing containers; empty states (no data) rendering sanely; very many items in a list/menu; missing images (broken icon or alt text overflow); RTL or long translated strings if the site is multi-language; large CMS-injected headings overflowing mobile.

How: deliberately inject or simulate worst cases on a staging environment: a 40-character unbroken string, an empty search result, a deleted hero image, a five-line headline. Record what breaks.

Pass criteria: worst cases degrade gracefully — wrap, truncate with ellipsis + tooltip, or scroll within their own container; nothing overlaps or escapes.

### 5.9 The browser-automation inspection loop

What to check — the *rendered* result through real browser automation, replacing "the code compiles" with "the page is right": visual hierarchy as actually perceived, typography as actually rendered, composition and spacing as actually laid out, asset quality as actually delivered, interactions as actually behave, console cleanliness, and the AI-failure tells ([ai-design-failures.md](ai-design-failures.md)) that only exist in the pixels.

How: this library is **tool-agnostic** — it does not assume a specific MCP server, tool names or configuration. The capability model any browser tool must supply is:

1. **Open a real page** (local dev server or built output) at a set of viewport sizes (the §4 set down to 320).
2. **Capture screenshots** — full page and per-section, at each viewport; read them (visually, as images) rather than trusting code.
3. **Interact** — click through navigation, exercise hover/focus/active states, open menus, submit forms; capture each state.
4. **Inspect layout programmatically** where the tool allows (scroll-width checks for horizontal overflow, element collision at 320, tap-target sizes) — the scripted equivalents of §5.5's checks.
5. **Read the console** — errors and warnings are QA findings.
6. **Compare across viewports** — structure preserved, priority retained, nothing overlapping.

The loop: capture → read → log findings (with viewport and evidence) → fix → re-capture. Where a mechanised gate exists (the taste-skill's checker and finish gate — [../../skills/taste/SKILL.md](../skills/taste/SKILL.md) §4 step 6), it runs as the automation layer for steps 2–4; the human/agent eye still owns the aesthetic judgement (§3 principle 5's defect-vs-decision split). Agents without browser automation fall back to static analysis plus the discipline of simulating states (devtools-style testing by whoever runs the build) — and record that limitation in the QA report.

Pass criteria: the rendered page passes the §5.1–5.8 checks *as observed in captures*; the console is clean; the meta-test of [ai-design-failures.md](ai-design-failures.md) ("what marks this as generic?") has been answered and its findings logged.

Typical defects found only in render: a hero image cropped through its subject at 390 px (fine at 1440); a hover state that flashes layout shift; a WebGL scene that never paused off-screen; the generic-AI look that no code review notices.

## 6. Decision framework

Classify every defect with the blocker/major/minor/polish model. Web-specific anchors:

- **Blocker:** horizontal scroll or clipped content at 320 px (reflow failure); invisible focus on a critical path; contrast < 3:1 on essential text; component state missing on a primary journey (e.g. no error state on checkout inputs); layout overlap making content unreadable at a standard width.
- **Major:** failing contrast on secondary text; token/type/colour drift at scale; inconsistent component instances across pages; missing hover/active/disabled states on common components; image quality defects on hero media.
- **Minor:** isolated off-scale value; single misalignment; one page's image weight; format inconsistency in one list.
- **Polish:** optical refinements, shadow harmonisation, nicer empty states.

Order fixes by severity, then effort, then dependency (token fixes first — they clear many page-level findings at once). Each fix re-enters the loop: re-run the affected check plus any check a fix could break (a spacing fix changes wrapping; a token fix changes contrast).

## 7. Examples

**Example 1 — marketing site, 6 page types, 5 viewports.** Findings: (1) 320 px: pricing table forces 40 px horizontal scroll — Blocker (reflow); (2) checkout inputs have no error state — Blocker (primary journey); (3) 18 px `#4a5568` hardcoded on 14 pages vs token `text.body` — Major (drift); (4) tab focus ring invisible on dark nav — Blocker (keyboard); (5) team photos at 480 px natural size rendered 600 px wide — Major (quality); (6) footer link colour 4.1:1 — Minor/Major boundary case, recorded Major because footer links are essential navigation. Corrections ordered: reflow → focus → error states → token sweep → image re-export.

**Example 2 — the loop catching a regression.** Fixing (1) by allowing the table to scroll horizontally inside its own container introduced a new defect: the container's scrollbar overlays the last column on macOS. Re-evaluation logged it as Minor; correction: reserved scrollbar gutter. This is the normal shape of a QA loop — the report's re-evaluation table records both.

**Example 3 — no design system exists.** The site has no tokens; §5.1–5.3 switch to internal-consistency mode: the report records the 14 distinct spacing values and 9 greys actually in use as a *finding about the system gap* (systemic, Major), evaluates uniformity of repeated elements, and recommends tokenising as the highest-leverage correction. The QA verdict distinguishes the site's local defects from the missing infrastructure.

## 8. Common mistakes

- **QA at one viewport, usually 1440 px.** Most defects live at 320–400 px and in state changes. The fixed viewport set exists to prevent this.
- **Checking pages, not states.** The default render passes while hover, focus, error and loading are broken. §5.4 is a mandatory route, not an optional extra.
- **Contrast checked in the mockup only.** Rendered reality differs (CSS variables, overlays, CMS themes). Measure in the browser.
- **Treating token drift as cosmetic.** Drift is systemic: it multiplies with every new page and blocks future refactors; it is at least Major.
- **Ignoring CMS extremes.** Real content is longer, shorter and weirder than the demo content; the stress pass in §5.8 is where "it worked with the placeholder text" designs are caught.
- **Reporting without viewports.** "The card is misaligned" is unverifiable; "card grid misaligned by 4 px at 768 px, column 2, listing page" is fixable.
- **Skipping the loop.** Layout fixes reflow neighbours; token fixes shift contrast; re-run touched checks every time.

## 9. Evaluation checklist

- [ ] Viewport set fixed in advance, including 320 px reflow condition.
- [ ] Every page type swept at every viewport (or a documented subset with reasons).
- [ ] Spacing values sampled and diffed against the scale; magic numbers listed.
- [ ] Type properties collected per page type; zero off-scale sizes; heading ladder monotonic.
- [ ] Colour values diffed against tokens; every rendered text pair contrast-measured, including states.
- [ ] Full state matrix exercised per component family; focus visible everywhere; no colour-only signals.
- [ ] No horizontal scroll, clipping or overlap at any tested width; tap targets pass.
- [ ] Media audited for resolution, weight, aspect and alt text.
- [ ] Reused components diffed across pages; system gap recorded if no tokens exist.
- [ ] Stress pass executed: long strings, empty states, missing images, large headings.
- [ ] Browser-automation loop executed (§5.9): captures read at every viewport, states exercised, console clean — or the limitation recorded.
- [ ] Defects classified and ordered; corrections carry risk; re-evaluation table completed.

## 10. Related topics

- [design-quality-framework.md](design-quality-framework.md) — master method, severity model, report template.
- [design-system-audit.md](design-system-audit.md) — auditing the system the site should adhere to.
- [../accessibility/accessibility-testing.md](../accessibility/accessibility-testing.md) — detailed accessibility test procedures beyond visual scope.
- [../accessibility/wcag-fundamentals.md](../accessibility/wcag-fundamentals.md) — contrast, reflow and target-size definitions.
- [../design-systems/design-tokens.md](../design-systems/design-tokens.md) — the token model referenced by adherence checks.
- [../foundations/principles-of-design.md](../foundations/principles-of-design.md) — underlying composition and hierarchy theory.
- [../information-design/data-visualisation.md](../information-design/data-visualisation.md) — deeper criteria for charts embedded in pages.
- [ai-design-failures.md](ai-design-failures.md) — the generic-AI failure catalogue this QA pass should include.
- [../../motion-and-interaction/motion-principles.md](../motion-and-interaction/motion-principles.md) — the motion budget and reduced-motion checks the loop verifies.

## 11. References

This file is a synthesis of the library's theory files, the QA sources below and standard professional practice.

- W3C Web Accessibility Initiative, "Understanding Success Criterion 1.4.10: Reflow" — 320 CSS px / 400% zoom condition. https://www.w3.org/WAI/WCAG21/Understanding/reflow.html [search-verified, accessed 2026-11-23]
- Deque University, "1.4.10 Reflow (AA)", https://dequeuniversity.com/resources/wcag2.1/1.4.10-reflow — corroborating reflow guidance. [search-verified, accessed 2026-11-23]
- W3C, "Web Content Accessibility Guidelines (WCAG) 2.1" — contrast (1.4.3/1.4.11), reflow (1.4.10), target size (2.5.5/2.5.8). [canonical]
- Deque, axe-core automated accessibility rules — basis for automated contrast/state scanning mentioned in §5.3. [canonical]
- Brad Frost, *Atomic Design*, 2016 — component consistency and design-system adherence framing. [canonical]
