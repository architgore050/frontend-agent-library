# WCAG Fundamentals

## 1. What is it?

The Web Content Accessibility Guidelines (WCAG) are the World Wide Web Consortium's (W3C) international standard for making web content — text, images, sounds, video and the markup and code behind them — more accessible to people with disabilities. W3C describes its purpose as providing "a single shared standard for web content accessibility" that meets the needs of individuals, organisations and governments internationally. Because it is a technical standard rather than an introductory tutorial, this file translates it into the decisions a designer or frontend developer actually makes: what to build, what to verify, and at what level.

WCAG is organised around four principles — content must be **Perceivable**, **Operable**, **Understandable** and **Robust** (the "POUR" acronym). Under each principle sit guidelines, and under each guideline are testable success criteria, each assigned to a conformance level A, AA or AAA. The standard is maintained by the W3C Accessibility Guidelines Working Group (AG WG) within the Web Accessibility Initiative (WAI).

[WCAG 2 at a Glance](https://www.w3.org/WAI/standards-guidelines/wcag/glance/) [accessed] is the fastest WAI overview of the principles and guidelines; this file is the domain's map of the whole standard, with deep dives elsewhere: text rules in [Accessible typography](accessible-typography.md), colour rules in [Accessible colour](accessible-colour.md) and procedures in [Accessibility testing](accessibility-testing.md). The division of labour across the domain: this file carries the framework — principles, conformance, semantic HTML, ARIA and the daily-criteria table; the typography and colour files carry their families' rules and measurement; the testing file carries every procedure and tool. When a design decision touches two domains (a type colour, a chart label), read both files — the criteria interlock more than they overlap.

## 2. Why does it matter?

Accessibility work is usually justified on four grounds, and a good practitioner knows all four rather than arguing from ethics alone.

- **Legal and contractual**: WCAG 2.1/2.2 Level AA is the reference level in most public-sector regulations. The European Standard EN 301 549 (used for the European Accessibility Act) uses WCAG 2.2 in its 2026 version, and WCAG 2.2 is published as the ISO standard ISO/IEC 40500:2025 [accessed, W3C overview]. Many procurement contracts and design system policies name WCAG 2.1 AA or 2.2 AA explicitly.
- **Practical reach**: disabilities affecting vision, hearing, motor control and cognition cover a very large share of any audience, and situational limitations (bright sun, one hand on a train, noisy room) expose the same failures to everyone.
- **Build quality**: most WCAG criteria reward the same things good engineering rewards — semantic HTML, real text instead of text baked into images, visible focus, predictable behaviour, resilient layouts. Accessibility failures are usually design-system failures.
- **Ethics and inclusion**: equal access to information, events and services is a reasonable end in itself; for public-facing events and organisations it is also an expectation.

The cost asymmetry matters most: fixing contrast in a palette takes minutes; retrofitting keyboard support onto a click-only component after launch takes days. This is why the decision framework below pushes verification into design review, not just QA.

A final framing that keeps the work proportionate: WCAG is a floor for *equivalence of experience*, not a ceiling for design quality. Meeting the criteria does not make an interface pleasant, and failing one does not always mean unusable — the standard deliberately excludes pure aesthetics. Teams that internalise this stop arguing about edge-case conformance and start asking the better question: for each of the four principles, is the experience genuinely equivalent for every audience the product serves?

## 3. Core principles

The four principles classify *what* accessibility problem a criterion addresses. Every success criterion belongs to exactly one principle, which makes POUR a useful mental checklist during design review.

| Principle | The question it asks | Typical guideline themes |
|---|---|---|
| **Perceivable** | Can users sense the content with at least one of their senses? | Text alternatives (1.1), captions and multimedia alternatives (1.2), adaptable presentation (1.3), distinguishable content — contrast, colour use, audio control (1.4) |
| **Operable** | Can users operate the interface, whatever their input method? | Keyboard access (2.1), enough time (2.2), seizures and motion (2.3), navigation and wayfinding (2.4), input modalities — pointer targets, dragging, motion (2.5) |
| **Understandable** | Can users understand the content and predict how the interface behaves? | Readable text (3.1), predictable behaviour (3.2), input assistance and error handling (3.3) |
| **Robust** | Will the content keep working as technologies change and vary? | Compatibility with assistive technologies (4.1) — in practice this is earned through valid, semantic markup and correct ARIA |

WCAG 2.2 contains 13 guidelines distributed across these principles [accessed, WAI overview]. As a designer you work mostly with 1.4 (Distinguishable), 2.4 (Navigable), 2.5 (Input Modalities) and 3.3 (Input Assistance); as a developer you additionally own 1.1, 1.3, 2.1 and 4.1.

| # | Guideline | Principle | One-line intent |
|---|---|---|---|
| 1.1 | Text Alternatives | Perceivable | Every non-text element has a text equivalent |
| 1.2 | Time-based Media | Perceivable | Audio and video have transcripts, captions, audio description |
| 1.3 | Adaptable | Perceivable | Structure and relationships are programmatically determinable; content reorders sensibly |
| 1.4 | Distinguishable | Perceivable | Contrast, colour use, audio control, reflow, text spacing, images of text |
| 2.1 | Keyboard Accessible | Operable | Everything works without a mouse or trackpad |
| 2.2 | Enough Time | Operable | Timers, pauses, stoppable moving content |
| 2.3 | Seizures and Physical Reactions | Operable | No flashing beyond limits; motion animation can be disabled |
| 2.4 | Navigable | Operable | Skip links, page titles, focus order, focus visibility, target size, location |
| 2.5 | Input Modalities | Operable | Pointer gestures, dragging, target size, motion actuation |
| 3.1 | Readable | Understandable | Language set; unusual words, abbreviations, reading level |
| 3.2 | Predictable | Understandable | Consistent behaviour, no surprise context changes |
| 3.3 | Input Assistance | Understandable | Labels, instructions, error handling, redundant entry, accessible authentication |
| 4.1 | Compatible | Robust | Name/role/value exposed; status messages announced (4.1.1 Parsing is obsolete in 2.2) |

Treat this table as the domain map: whenever a review finding feels unfamiliar, locating its guideline gives you the family of related criteria to check next — a focus problem is never just 2.4.7 but also 2.4.11, 1.4.11 and the 2.4.3 focus order.

Each principle also translates into concrete review questions a designer can ask without opening the standard. For **Perceivable**: does every image have the right alternative, every video captions, every state enough contrast, every structure both visual and programmatic? For **Operable**: can the whole journey be completed with one input method (keyboard, touch, pointer), are targets big enough, is nothing time-limited against the user? For **Understandable**: is the language set, are errors explained in plain text, would a first-time user predict what each control does? For **Robust**: are we using native elements and tested patterns, so behaviour survives updates and varied assistive technology? These questions deliberately compress entire guidelines; they work because the expensive failures almost always show up in them. A useful discipline in design review is to answer each from the artefact in front of you (the Figma file, the spec) rather than deferring all of them to QA, where they cost an order of magnitude more to fix.

## 4. How it works

### 4.1 Success criteria and conformance levels

Each success criterion (SC) is a numbered, testable statement — for example SC 1.4.3 "Contrast (Minimum)". The number encodes principle, guideline and criterion order (1.4.3 = Perceivable, guideline 1.4, third criterion). Every SC is assigned to a level:

- **Level A** — the highest-priority baseline: without these, some assistive-technology users are locked out entirely (no keyboard access, no text alternatives, unlabelled form fields).
- **Level AA** — the accepted professional and regulatory target: includes contrast thresholds, reflow, visible focus, adequate pointer target size. Most laws and procurement standards reference AA.
- **Level AAA** — enhanced guidance for specific populations (7:1 contrast, reading level, target size 44 × 44 CSS px). Not achievable for all content in all situations; W3C does not require AAA site-wide, and it is normally applied selectively.

This tiering is itself important doctrine: A is the floor, AA is the target, AAA is a menu of improvements to apply where they make sense. Treating AAA as the general goal leads to paralysis; treating AA as optional leads to exclusion.

### 4.2 Conformance requirements

Conformance applies to whole pages, and all content on a page must conform (conformance is not partial), including content from third parties, unless content is excepted (e.g. legally required alternatives). Pages that are part of a process must conform together. Two practical consequences:

1. You cannot "make the important parts accessible" and ship the rest; a broken cookie banner or embedded map breaks conformance of the page it sits on.
2. WCAG is content-level — a conforming *component library* is still your responsibility to combine correctly.

Additional conformance mechanics worth knowing: conformance is assessed against *complete web pages* (a half-built page cannot conform); for processes (multi-step checkout, booking), every page in the process must conform for any of them to conform; and "web page" is interpreted broadly — states and views of a single-URL application count as distinct pages when content changes meaningfully. These mechanics are why audits group findings by page *and* by journey: a journey-level trap can invalidate conformance of every page it crosses.

### 4.3 Versions and current status

WCAG 2.x versions are additive: each version keeps all existing criteria unchanged and adds new ones, so content conforming to WCAG 2.2 also conforms to 2.1 and 2.0 [accessed, WAI overview].

| Version | Published | Added | Status |
|---|---|---|---|
| WCAG 2.0 | 11 December 2008 | — | Existing standard; referenced by older regulations |
| WCAG 2.1 | 5 June 2018 (updates 21 Sep 2023, 12 Dec 2024, 6 May 2025) | 1 guideline, 17 SCs | Existing standard |
| WCAG 2.2 | 5 October 2023 (update 12 Dec 2024) | 9 SCs | **Current version**; one criterion (4.1.1 Parsing) made obsolete |
| WCAG 3 | early draft only | — | W3C Accessibility Guidelines 3.0, formerly "Silver"; no conformance model yet |

W3C encourages using the latest version; it states explicitly that "WCAG 2.2 does not deprecate or supersede WCAG 2.1", so both may be named in law simultaneously. The working default in this knowledge base is **WCAG 2.2 Level AA**, with 2.1-only criteria checked when a contract names 2.1. Note the small delta: 2.2 removes nothing but 4.1.1 and adds criteria concentrated on low vision (focus appearance, target sizes) and cognition (accessible authentication, redundant entry).

### 4.4 Techniques, failures and how criteria are tested

Beneath the success criteria sit two families of *advisory* material: sufficient techniques (published methods that satisfy a criterion — e.g. G18 for text contrast, C40 for a two-colour focus indicator) and failure techniques (documented common mistakes — e.g. F78, removing focus outlines). Techniques are not the law: they are one acceptable way to meet a criterion, and the Understanding documents say alternative methods that meet the criterion are equally valid. This matters practically — teams sometimes defend a design by claiming a technique is satisfied when the criterion itself is not, or reject an innovative pattern because it is not a named technique. Judge the criterion, use techniques as recipes. Testing follows the same structure: each criterion in the Quick Reference links to its Understanding page with test procedures, and automated tools implement subsets of the test rules; the manual methods in [Accessibility testing](accessibility-testing.md) cover what the rules cannot.

### 4.5 The three layers of WCAG documentation

The standard ships with supporting material that is worth reading before interpreting any criterion: the normative specification (Understanding) documents give intent, benefits, examples and techniques per criterion; the Quick Reference ("How to Meet WCAG") filters everything by level and technique; WAI's "Easy Checks" and evaluation guidance support informal review. Never design from a second-hand summary of a criterion — read the Understanding page, because exceptions and edge cases live there and frequently change whether your pattern passes.

### 4.6 Conformance claims in practice

A formal conformance claim (rare outside public-sector work, but useful in procurement and event tenders) names the version and level met, the date, the technologies relied upon, and any content excluded. Two honest-practice notes: a claim of "WCAG 2.2 AA" is only as good as the most recent full evaluation — teams should date and scope their claims rather than leave them perpetual; and because 2.2 conformance implies 2.1 and 2.0 conformance [accessed], teams building to 2.2 can safely promise the older levels that some contracts still name. Avoid claiming AAA site-wide: W3C's own positioning is that AAA is not required for entire sites and may not be achievable for all content [canonical — verify wording in the conformance section of the standard before quoting]. The safer pattern used across this knowledge base is a published accessibility statement naming the target level, known gaps and a feedback route.

### 4.7 Where WCAG does not reach

Knowing the standard's edges prevents both overclaiming and under-scoping. WCAG governs *web content*; WAI's WCAG2ICT guidance extends its application to non-web ICT such as native apps and documents [accessed, WAI overview], but team practice still has gaps the criteria do not measure: the *quality* of alt text, the clarity of error messages, the burden of cognitive load, conversation-like flows, and overall usability with assistive technology — conformance is necessary, not sufficient. Documents attached to event sites (PDFs, tickets) and emails inherit the same duties but are frequently untested; treat them as in scope. Finally, WCAG does not cover native platform conventions automatically (a mobile app is judged by WCAG2ICT mapping plus platform guidance), so hybrid products need the web checklist *and* the platform's accessibility rules. Say what you tested and what you did not — the audit trail matters as much as the score.

## 5. Practical application

### 5.1 Semantic HTML: the foundation

The Robust principle is earned through markup, not sprinkled on afterwards. Native HTML elements carry built-in keyboard behaviour, roles, states and names that assistive technologies already understand:

- **Headings** (`h1`–`h6`) in a logical order with no skipped levels provide the document outline screen-reader users navigate by — they are a structure contract, not a font-size style.
- **Landmark elements** (`header`, `nav`, `main`, `footer`, `aside`) give repeat users a way to jump between page regions.
- **Buttons vs. divs** is the classic test of a frontend developer's accessibility literacy: `<button>` gets Enter and Space activation, focus inclusion and a role for free; a `<div onclick>` gets none of them, and patching all three with ARIA and key handlers is slower and error-prone.

```html
<!-- accessible by default -->
<button class="tag" type="button">Remove ticket</button>

<!-- the same idea patched up: more code, more failure modes -->
<div class="tag" role="button" tabindex="0"
     onclick="removeTicket()" onkeydown="if (event.key===' '||event.key==='Enter') removeTicket()">
  Remove ticket
</div>
```
- **Links vs. buttons**: use `<a href>` when it navigates, `<button>` when it acts; screen-reader users query both lists deliberately.
- **Lists and tables**: real `<ul>`/`<ol>`/`<table>` markup so relationships survive linearisation; data tables need `<th>` scope.
- **Labels**: every input gets an explicit `<label for>`; placeholder text is not a label (it disappears on entry and often fails contrast).

### 5.2 ARIA basics

ARIA (Accessible Rich Internet Applications) supplements HTML semantics for components HTML cannot express (tab panels, tree views, custom toggles). Its use is governed by conventions, and the most important is the **First Rule of ARIA** [canonical]: do not use ARIA if a native HTML element or attribute exists that does the job. ARIA is a last resort that adds obligations — you must now maintain roles, states and keyboard support manually. Related working principles: ARIA only changes *what assistive technology announces*, never adds behaviour (ARIA buttons are not clickable), and incorrect ARIA is worse than none because it lies to the user. If you reach for ARIA, copy a tested pattern from the WAI ARIA Authoring Practices Guide rather than inventing roles [canonical].

### 5.3 Alternative text in practice

SC 1.1.1 is deceptively simple: "every image needs alt text" hides three distinct decisions. **Equivalence**: the alternative conveys the image's *purpose in context*, which differs by use — a portrait photo on a speaker page warrants "Speaker Anne Chen, event host", while the same photo decorating a header warrants `alt=""` (decorative). **Appropriateness cannot be automated**: a tool can detect a missing `alt` attribute, but only a human can judge whether "chart.png" describes the data in a chart. For informative images, keep the alternative short (aim for a sentence) and put the detail in surrounding text or a long description; for charts and diagrams, state the message ("Ticket sales doubled between June and July"), not the visual mechanics. **Complex images** (infographics, maps, diagrams) need a text alternative adjacent to the image, because the chart itself will be perceived by many users only through that text. Logotype text in images is the one case where the alternative equals the visible text verbatim. Related criteria: 1.4.5 (no images of text except logotypes) and the graphical-object half of 1.4.11, which applies to parts of graphics needed for understanding [accessed].

### 5.4 Keyboard navigation and focus order

Keyboard support is the operability backbone: users of switch devices, sip-and-puff controllers, screen-reader keyboard modes and injured-while-typing users all depend on it. The working rules from 2.1.1, 2.1.2, 2.4.3, 2.4.7 and 2.4.11:

- **Reachable**: every function reachable by Tab (or an explicit arrow-key pattern for composite widgets). If a control is clickable but not focusable, it fails.
- **Order**: focus order follows the visual and logical reading order; `tabindex="1+"` is almost always wrong — use DOM order, with `tabindex="0"` only to bring non-focusable custom elements into the sequence and `tabindex="-1"` for programmatic moves.
- **Visible and unobscured**: the indicator is visible (2.4.7), meets non-text contrast (1.4.11), and is never hidden behind sticky headers, cookie banners or chat widgets (2.4.11).
- **Operable**: native elements give Enter/Space free; composite widgets follow the ARIA Authoring Practices Guide keyboard tables [canonical].
- **Escapable**: modals, dropdowns and tour overlays release focus (Esc or an explicit close button); nothing traps it (2.1.2).
- **Not stolen**: avoid scripts that blur focused elements (failure F55) and avoid `setTimeout` focus jumps that fight the user.

Test this layer with the walk-through in [Accessibility testing](accessibility-testing.md); most keyboard failures are invisible in static screenshots, which is precisely why design review must specify focus states explicitly.

### 5.5 The criteria you meet daily

The table below compiles the success criteria a designer or frontend developer touches most often, with the numbers and thresholds verified from W3C sources where marked. SC numbers and titles are from the WCAG 2.2 standard [canonical]; entries marked [accessed] were verified against the normative Understanding pages this session.

| SC | Title (Level) | What it requires in practice |
|---|---|---|
| 1.1.1 | Non-text Content (A) | Every meaningful image gets an appropriate text alternative; decorative images get empty `alt=""`; complex images get short `alt` plus adjacent description |
| 1.3.1 | Info and Relationships (A) | Visual structure (headings, lists, labels, table headers) exists programmatically, not just visually |
| 1.3.5 | Identify Input Purpose (AA) | Common fields (name, email, phone) support autofill via `autocomplete` |
| 1.4.1 | Use of Colour (A) | Colour is never the only visual means of conveying information or indicating action |
| 1.4.2 | Audio Control (A) | Auto-playing audio longer than 3 s can be paused or volume-controlled |
| 1.4.3 | Contrast (Minimum) (AA) [accessed] | Text ≥ **4.5:1**; large text ≥ **3:1** (large = ≥ 18 pt / 24 px, or ≥ 14 pt bold / ~18.66 px); logos, inactive and purely decorative text exempt |
| 1.4.4 | Resize Text (AA) | Text can be resized up to 200% without loss of content or functionality |
| 1.4.5 | Images of Text (AA) | Use real text instead of text inside images, except logotypes |
| 1.4.10 | Reflow (AA) [accessed] | No two-dimensional scrolling at **320 CSS px** width (1280 px viewport at 400% zoom); data tables, maps, video, games excepted |
| 1.4.11 | Non-text Contrast (AA) [accessed] | UI component boundaries, states and meaningful graphics ≥ **3:1** against adjacent colours |
| 1.4.12 | Text Spacing (AA) [accessed] | No loss of content when the user sets line height 1.5×, paragraph spacing 2×, letter spacing 0.12×, word spacing 0.16× |
| 2.1.1 | Keyboard (A) | Every function works from a keyboard |
| 2.1.2 | No Keyboard Trap (A) | Focus can always leave a component (modals close with Esc or other means) |
| 2.3.3 | Animation from Interactions (AAA) [canonical] | Motion animation triggered by interaction can be disabled — implement via `prefers-reduced-motion` |
| 2.4.4 | Link Purpose (In Context) (A) | Link text describes its destination or equivalent context exists |
| 2.4.6 | Headings and Labels (AA) | Headings and labels describe topic or purpose |
| 2.4.7 | Focus Visible (AA) [accessed] | Keyboard focus indicator is visible; no exception permits removing it |
| 2.4.11 | Focus Not Obscured (Minimum) (AA, 2.2) | The focused item is not hidden by author-created content (sticky headers, banners) |
| 2.5.7 | Dragging Movements (AA, 2.2) | Any action that drags has a non-drag alternative (click, press, slider arrows) |
| 2.5.8 | Target Size (Minimum) (AA, 2.2) [accessed] | Pointer targets ≥ **24 × 24 CSS px**, or pass the 24 px spacing-circle test; inline links, user-agent controls and essential exceptions apply |
| 3.1.1 | Language of Page (A) | `<html lang>` is set correctly |
| 3.1.5 | Reading Level (AAA) [canonical] | Supplementary content for text needing more than lower-secondary reading level — rare, but relevant for legal or medical copy |
| 3.3.1 | Error Identification (A) | Errors are described in text and identified with the field |
| 3.3.2 | Labels or Instructions (A) | Required inputs and expected formats are labelled |
| 3.3.7 | Redundant Entry (A, 2.2) | Previously entered information is auto-populated or available to re-select |
| 3.3.8 | Accessible Authentication (AA, 2.2) | No cognitive function test (memorised passwords, puzzles) without an alternative — this affects login and OTP flows |
| 4.1.2 | Name, Role, Value (A) | Custom components expose name, role and state programmatically |
| 4.1.3 | Status Messages (AA) | Toasts, loading states and results are announced without moving focus |

Numbers bolded in this table were verified this session against the Understanding pages listed in the references; the remaining titles and levels are standard knowledge from the normative WCAG 2.2 specification and should be re-checked against [the current standard](https://www.w3.org/TR/WCAG22) when quoting conformance claims.

### 5.6 Screen readers and linearisation

A screen reader consumes the page as a stream: it reads the DOM order, announces each element's role, name and state, and builds navigable lists (headings, links, form fields, landmarks). This exposes a failure class invisible to sighted review called **linearisation** problems: a visually perfect layout can announce in nonsense order, because CSS `order`, absolute positioning or grid re-arrangement decoupled the visual sequence from the DOM sequence (SC 1.3.2 Sequence, A). Designers own the visual order; developers own the DOM order; both must match. Related practical habits: give every page a descriptive `<title>`; use `aria-hidden="true"` only to hide genuinely decorative content from the stream; never use visually-hidden text as a substitute for visible labels (some users navigate by eye only); and keep focus-visible text readable when revealed. Screen-reader *testing* is a procedural topic covered in [Accessibility testing](accessibility-testing.md); the structural criteria it verifies live here.

### 5.7 Motion sensitivity

WCAG 2.3 covers seizures and vestibular reactions. Flashing content is constrained by SC 2.3.1 (A), and SC 2.3.3 Animation from Interactions (AAA) asks that motion animation triggered by interaction can be disabled. In practice this is implemented with the `prefers-reduced-motion` media query, which is Baseline "widely available" in browsers since January 2020 [accessed, MDN] and maps to OS settings such as macOS "Reduce motion", Windows animation settings and Android's "Remove animations". Treat reduced-motion support as standard practice for any interface with parallax, scaling or auto-playing movement; see the implementation pattern in [Accessibility testing](accessibility-testing.md) and the visual-risk reasoning in [Website visual QA](../evaluation/website-visual-qa.md).

### 5.8 Forms, status feedback and responsive accessibility

Forms concentrate accessibility risk: 3.3.1, 3.3.2 and 3.3.8 above, plus 1.3.5 and 4.1.3. The working rules: label every field, mark required state in text (not colour alone), place error messages adjacent to the field and programmatically linked (`aria-describedby`), never rely on placeholder as the only label, support autofill, and announce dynamic results (search counts, toasts) as status messages rather than stealing focus. Payment and authentication flows deserve special attention because SC 3.3.8 (Accessible Authentication) rules out memorisation-only barriers.

**Responsive accessibility** is the habit of re-checking these guarantees at every breakpoint rather than only at desktop width. Reflow (1.4.10) and resize (1.4.4) are the normative core, but practical verification covers more: target sizes must hold in compact mobile layouts (2.5.8), sticky mobile headers and bottom bars must not obscure focus (2.4.11), touch layouts must keep hover-reliant affordances available by touch (2.5.1 pointer gestures — any multi-pointer or path-based gesture needs a single-pointer alternative), and landscape/portrait orientation must both work (2.5.2 orientation, AA in 2.1). A component that passes at 1440 px and fails at 320 px is not accessible; run the visual stress tests in [Accessibility testing](accessibility-testing.md) at each breakpoint as part of the design pass.

## 6. Decision framework

### 6.1 Choosing a conformance target

Ask three questions, in order:

1. **What does the contract or law name?** Public-sector and regulated work usually names WCAG 2.1 AA or 2.2 AA — that becomes a hard floor, not a preference.
2. **What is the audience?** Public-facing event, ticketing or information sites justify AA as a floor and selective AAA (contrast 7:1, enhanced target size, visual presentation) for primary reading paths.
3. **Where does AAA pay?** Apply AAA where a specific population dominates the audience or where it costs nothing (e.g. 44 × 44 px targets on primary call-to-action buttons cost little and help everyone on touch).

### 6.2 Prioritising fixes when you cannot fix everything

Order by lock-out severity rather than by tool output. First: things that make content *impossible* to reach (keyboard traps, missing labels on required fields, unperceivable content). Second: things that make content *hard* (contrast, target size, focus visibility). Third: things that make content *uncomfortable* or slower (predictability, status announcements, reading level). This maps cleanly onto A > AA > AAA but is quicker to apply on a mixed, partially-conforming product.

### 6.3 Semantic-first test

For any component decision, ask in sequence: Is there a native HTML element for this? If yes, use it. If no, is there a tested ARIA pattern? If yes, copy it exactly. If no, redesign toward something simpler. Most "accessibility bugs" are component-choice bugs made three screens earlier.

## 7. Examples

**Event site, brand kit rollout.** A headline treatment in brand colour must still pass 4.5:1 against the page background (or 3:1 if it is ≥ 24 px); the logo itself is exempt under 1.4.3 but buttons built from brand colours are not — they fall under 1.4.11 for component boundaries. See [Accessible colour](accessible-colour.md) for the testing workflow.

**Ticket selector.** A 20 × 20 px icon-only "remove ticket" control fails 2.5.8 unless undersized targets are spaced so 24 px circles around each bounding box do not intersect; the safer fix is 24 × 24 px or larger hit areas, ideally 44 × 44 px (AAA 2.5.5) on primary controls. Icon-only buttons additionally need accessible names (1.1.1, 4.1.2).

**Countdown timer with parallax.** Auto-playing ambient motion gets a pause control (1.4.2 for audio, 2.2.2 for movement) and the whole layer is gated behind `@media (prefers-reduced-motion: reduce)`, replacing motion with opacity or position-stable alternatives.

**Cookie banner.** A sticky banner that covers the focused "Checkout" button breaks 2.4.11; a modal that traps focus with no Esc route breaks 2.1.2; grey placeholder-style text at 2.4:1 breaks 1.4.3. All three are found in a ten-minute keyboard-plus-tool pass (see [Accessibility testing](accessibility-testing.md)).

**Reading a conformance matrix honestly.** A vendor claims "WCAG 2.1 AA conformant" for a ticketing widget. The useful questions follow directly from the standard: which *version and level* (2.1 AA does not include 2.2's target-size and focus-not-obscured criteria); was the claim about the widget alone or the pages it renders on (conformance attaches to whole pages); does it rely on specific technologies (a claim that depends on mouse input is not keyboard-accessible); and how old is the evaluation. This pattern — version, scope, dependencies, date — also applies to your own statements, and it is the structure to demand in procurement conversations.

**Extending an event logo into a brand kit.** The logo itself is exempt from contrast as a logotype, but everything the kit generates around it is not: heading colours derived from logo colours must be re-tested against text thresholds (usually impossible at logo lightness — the kit therefore defines a darker text-variant of the brand hue); a one-page website generated from the kit inherits the checklist above automatically; and the kit's tokens should record verified pairs so every future page starts conformant (method in [Colour accessibility](../colour/colour-accessibility.md) and [Colour in code](../colour/colour-in-code.md)).

**Search results, announced correctly.** A query returns 14 sessions. Visually, the count updates; programmatically, nothing changes unless the count lives in a status-message container (`role="status"` or an equivalent live region), because 4.1.3 exists precisely for this: results announced without focus jumping to them or to the top of the list. The same pattern covers toasts, saved-state confirmations and filter counts — the announcement is the criterion, not the toast's styling.

## 8. Common mistakes

- **Treating WCAG as a developer-only concern.** Many criteria are decided in design: contrast, target size, focus styling, information density, error message placement. A developer cannot fix a 2.4:1 brand pairing by markup.
- **Chasing tool scores instead of people.** A green automated report means roughly "no automatically detectable failures", not "accessible". Manual keyboard, screen-reader and cognitive review remain essential (see [Accessibility testing](accessibility-testing.md)).
- **ARIA as decoration.** Adding `role="button"` to a `<div>` without keyboard handlers, or duplicating native elements with redundant roles, makes output worse. First rule of ARIA: prefer native HTML.
- **Removing focus outlines** (`outline: none` with no replacement) violates 2.4.7 — there is no exception permitting removal; failures F55 and F78 exist precisely for this.
- **Disabling user scaling** (`maximum-scale=1` or `user-scalable=no`) to keep a layout tidy violates 1.4.4 and harms low-vision users more than any layout nicety helps.
- **Assuming large numbers of AAA wins means a strong product.** Conformance thinking starts at the bottom: an AAA contrast score on a page whose form fields are unlabelled is still inaccessible.
- **Ignoring the "mode of operation" wording of 2.4.7** by claiming some user agent hides focus: the author must ensure at least one mode of operation shows focus visibly.
- **Shipping third-party embeds without checking them.** Embedded ticketing widgets, maps and chat tools are page content: an inaccessible embed breaks the page's conformance, and the fix — an accessible alternative path — must be planned before procurement, not after.
- **Forgetting obsolete-but-live differences between 2.1 and 2.2 audits.** Teams testing to 2.1 miss the 2.2 criteria (target size, focus not obscured, accessible authentication) that regulators adopting 2.2 will check; teams testing only 2.2 must still note that some contracts name 2.1.
- **One-off "accessibility sprints"** that fix a release and stop: conformance decays with every change; the checklist above only holds if review gates and automated regressions keep applying it.

## 9. Evaluation checklist

- [ ] Every page has one `h1`, a logical heading order and landmark regions (`main`, `nav`, `header`, `footer`).
- [ ] All interactive elements are native elements or follow a tested ARIA pattern with working keyboard support (Tab, Enter, Space, Esc, arrows where applicable).
- [ ] Text contrast ≥ 4.5:1 (≥ 3:1 for ≥ 24 px or bold ≥ 18.66 px text) — verify with the workflow in [Accessible colour](accessible-colour.md).
- [ ] Component boundaries, focus indicators and meaningful icons ≥ 3:1 against adjacent colours (1.4.11).
- [ ] Focus indicators are visible on every interactive element and never removed (2.4.7), and sticky content never obscures the focused item (2.4.11).
- [ ] Pointer targets ≥ 24 × 24 CSS px or spaced so 24 px circles do not intersect (2.5.8); primary actions aim for 44 × 44 px.
- [ ] Layout survives 400% zoom at 1280 px viewport width with no page-level horizontal scrolling (1.4.10) and 200% text resize (1.4.4).
- [ ] Text-spacing overrides (1.5 line height, 2× paragraph, 0.12× letter, 0.16× word) cause no clipping or overlap (1.4.12).
- [ ] Motion and auto-playing media can be paused or reduced; `prefers-reduced-motion` is honoured.
- [ ] Every image has an appropriate alternative; every form field has a visible label; errors are text-identified; status changes are announced.
- [ ] `<html lang>` is set; link text makes sense out of context; the page can be fully operated by keyboard with no traps.
- [ ] Third-party embeds (ticketing, maps, chat, video) were tested with the same checklist or have an accessible alternative path.
- [ ] An accessibility statement exists naming the target version and level, known gaps and a feedback route.

## 10. Related topics

- [Accessible typography](accessible-typography.md) — text spacing, sizing and readability in depth.
- [Accessible colour](accessible-colour.md) — contrast rules, testing and dark mode.
- [Accessibility testing](accessibility-testing.md) — procedures, tools and the full audit workflow.
- [Colour accessibility](../colour/colour-accessibility.md) — palette construction side of the same rules.
- [Colour in code](../colour/colour-in-code.md) — tokenising accessible values into CSS variables.
- [Web typography](../typography/web-typography.md) — general web type decisions these constraints shape.
- [UI fundamentals](../ui-ux/ui-fundamentals.md) — components, states and interaction patterns.
- [Website visual QA](../evaluation/website-visual-qa.md) — the review pipeline accessibility testing plugs into.
- [Data visualisation](../information-design/data-visualisation.md) — accessible charts and the 1.4.11 graphical-object rule.

## 11. References

- W3C Web Accessibility Initiative, *WCAG 2 Overview* — <https://www.w3.org/WAI/standards-guidelines/wcag/> [accessed 2026-11-23]
- W3C Web Accessibility Initiative, *WCAG 2 at a Glance* — <https://www.w3.org/WAI/standards-guidelines/wcag/glance/> [accessed 2026-11-23]
- W3C, *Understanding SC 1.4.3 Contrast (Minimum)* (WCAG 2.2) — <https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html> [accessed 2026-11-23]
- W3C, *Understanding SC 1.4.11 Non-text Contrast* (WCAG 2.2) — <https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html> [accessed 2026-11-23]
- W3C, *Understanding SC 1.4.12 Text Spacing* (WCAG 2.2) — <https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html> [accessed 2026-11-23]
- W3C, *Understanding SC 1.4.10 Reflow* (WCAG 2.2) — <https://www.w3.org/WAI/WCAG22/Understanding/reflow.html> [accessed 2026-11-23]
- W3C, *Understanding SC 2.4.7 Focus Visible* (WCAG 2.2) — <https://www.w3.org/WAI/WCAG22/Understanding/focus-visible.html> [accessed 2026-11-23]
- W3C, *Understanding SC 2.5.8 Target Size (Minimum)* (WCAG 2.2) — <https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html> [accessed 2026-11-23]
- MDN Web Docs, *prefers-reduced-motion* — <https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion> [accessed 2026-11-23]
- W3C, *Web Content Accessibility Guidelines (WCAG) 2.2* (normative spec) — <https://www.w3.org/TR/WCAG22> [canonical; verify criteria not fetched this session]
- W3C WAI, *ARIA Authoring Practices Guide* (First Rule of ARIA and component patterns) — <https://www.w3.org/WAI/ARIA/apg/> [canonical]
