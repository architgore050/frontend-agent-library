# Typeface Selection

## 1. What is it?

Typeface selection is the decision process that turns "we need a font" into a defensible, verifiable choice of a specific family (or families) for a specific project. It is the bridge between typographic fundamentals ([Typography fundamentals](typography-fundamentals.md)) and the systems built on the choice: pairing ([Font pairing](font-pairing.md)), hierarchy ([Typographic hierarchy](typographic-hierarchy.md)) and the brand's visual voice ([Visual identity](../branding/visual-identity.md)).

A selection decision has four distinct strands that this file treats in turn:

1. **Personality fit** — does the face's voice match the brand and the content?
2. **Functional fit** — can readers actually use it: legibility, readability, size range, medium?
3. **Coverage fit** — does it support every language, script and symbol the product needs?
4. **Rights and delivery fit** — can you legally and practically use it where you need it, at acceptable performance cost?

Projects that fail at selection almost always fail on strand 3 or 4 *after* the design work is done — a face chosen for beauty, then discovered to lack the accented characters of the audience's language, or to cost per-seat licence fees nobody budgeted. This file's goal is to move all four checks to the front of the process.

The strands also run on different clocks. Personality and functional fit are design-time questions — they can be revisited cheaply before anything ships. Coverage and rights are ship-time questions: a coverage gap discovered after translation starts, or a licence gap discovered after launch, costs redesigns, re-negotiations or emergency face swaps. The file's structure reflects that asymmetry: the design-time strands (3.1–3.2) are judgement calls with shared vocabulary, while the ship-time strands (3.3, 3.6, 4) are verification procedures with checklists — and verification procedures are where agents and junior designers can be trusted to run the process alone.

## 2. Why does it matter?

Typography is the voice of the text; the typeface choice is the accent. Two products with identical layouts and identical copy read completely differently in a neo-grotesque versus a warm humanist serif — the choice signals institutional versus friendly, engineered versus crafted, new versus established. Because type covers most of the visual surface ([Typography fundamentals](typography-fundamentals.md)), the selection compounds across every screen and page; it is one of the few decisions that is expensive to reverse late.

The functional strand matters because a face that fights its content imposes friction on every reader. A data-dense dashboard in a high-contrast display serif, or a long-form journal in a tight geometric sans, taxes attention on every line. And the rights strand matters commercially: web font licensing differs from desktop licensing, free licences have conditions (see 6), and unverified licensing is a genuine legal exposure for any organisation shipping a product.

One more reason selection deserves process: it is a decision made once and consumed everywhere. Every later artefact — the design system's components, the marketing site, the printed programme, next year's event kit — inherits the choice silently. A defensible, documented selection compounds; an undocumented one forces every future contributor to re-derive the rationale or ignore it, and both outcomes erode the system ([Visual identity](../branding/visual-identity.md); the reuse pattern in [Editorial design](editorial-design.md) 5.3).

## 3. Core principles

### 3.1 Selecting for brand personality

Typefaces carry personality through their historical associations and their formal qualities (contrast, rhythm, terminals — see [Typography fundamentals](typography-fundamentals.md) 4). The mapping below is a professional convention grounded in genre history — a strong central tendency to start from, not a law; deliberate inversions can be powerful when the brand position calls for tension.

| Brand position | Conventional type voice | Typical class |
|---|---|---|
| Heritage, craft, literary | Warm serif with historical roots | Old-style / transitional serif |
| Authority, institution, news | Neutral, disciplined serif or serif+sans system | Transitional serif / neo-grotesque |
| Technology, engineering, data | Clean, low-contrast, systematic sans | Neo-grotesque / humanist sans |
| Modern, minimal, fashion-led | Geometric or high-contrast faces | Geometric sans / didone display |
| Friendly, education, community | Rounded or humanist sans, generous forms | Humanist sans |
| Sturdy, industrial, promotional | Slab serif, robust and unambiguous | Slab |
| Playful, handmade, personal | Script or quirky display voice (display-only) | Script / decorative |

Three cautions. First, personality is carried by the *system* — weight range, spacing, scale — as much as by the family; a geometric sans set in a warm, generous system does not read cold. Second, genre conventions decay: a geometric sans no longer signals "avant-garde" when every start-up uses one; differentiation may require a less common class or a distinctive superfamily. Third, personality is subjective; test the shortlist with stakeholders on real copy, not on "Aa" specimen tiles, and treat the mapping above as the opening question rather than the answer.

A more granular mapping, from brand adjectives to the formal properties that carry them (use it to interrogate a shortlist: which properties are doing the work?):

| Adjective | Formal property that carries it | Where to verify |
|---|---|---|
| Trustworthy, established | Moderate contrast, sturdy stems, conservative apertures | Body weight at text size |
| Modern, precise | Even rhythm, near-monolinear strokes, generous spacing | Headline tracking and scale |
| Warm, human | Open apertures, modulated strokes, humanist proportions | Lowercase at small size |
| Bold, confident | Heavy display weight, tight tracking, strong contrast | Display step at hero size |
| Playful, informal | Quirky terminals, unusual proportions, casual rhythm | One display voice, used sparingly |
| Premium, crafted | High stroke contrast, fine serifs, restrained scale | Display sizes only; fragility below |

The table's use is diagnostic as much as generative: when a design "feels wrong" in a chosen face, one of these rows is usually violated — a premium adjective carried by a sturdy slab, or trust carried by a hairline didone at text size. Name the intended adjective, then check which property is failing to express it.

### 3.2 Legibility and readability, defined precisely

The two words are often used interchangeably; in typography they are distinct and both matter.

- **Legibility** is a property of the design of letterforms: how *discriminable* individual characters and word shapes are. It is measured at the level of the glyph: can you tell b from d, l from 1, rn from m, at the target size and rendering conditions? Legibility is driven by anatomy — x-height, apertures, stroke contrast, letterform distinctness ([Typography fundamentals](typography-fundamentals.md) 4.1–4.2). A face can be perfectly legible and still unpleasant to read in bulk.
- **Readability** is a property of the *setting*: how comfortably continuous text can be read over time. It is driven by the composition — measure (line length), line height, paragraph spacing, alignment, contrast of the text against its background, and the reader's fatigue over paragraphs ([Typesetting](typesetting.md) covers the mechanics). A beautifully legible face set at 90-character measure and 1.2 line height has excellent legibility and poor readability.

The practical split: when text *fails to be understood* (misread labels, ambiguous codes), investigate legibility and the face; when text *is understood but tiring* (rereading lines, losing your place), investigate readability and the setting. Selection decisions are mostly legibility decisions; typesetting decisions are mostly readability decisions. Accessibility requirements layer on top of both — sizing, spacing and contrast thresholds live in [Accessible typography](../accessibility/accessible-typography.md).

### 3.3 Language support and script coverage

This is the most frequently skipped check and the most expensive to miss. A face "supports a language" only if it contains every character that language's orthography needs — including diacritics (é, ñ, ü, č, ś), language-specific punctuation (guillemets «», the Polish §, Spanish inverted marks), and the numerals and locale conventions of the audience. Consequences of weak checking: fallback fonts silently substitute for missing glyphs, producing the typographic patchwork of mismatched accents mid-word — visible in any European language set in a face whose Latin-Extended coverage is partial.

Checks worth running on every project:

- List the actual languages of your content *and your users' names* (user-generated names are the classic edge case: the interface may be English while names arrive in Vietnamese, Turkish or Yorùbá).
- Verify coverage per face in the family, not just the family: some families ship different character sets in different weights.
- Test that fallback behaviour is deliberate (see [Web typography](web-typography.md) on fallback stacks) rather than accidental.
- For non-Latin scripts (Arabic, Devanagari, CJK, Thai), treat the script's face as a separate selection decision: script conventions (baseline behaviour, joining, rhythm) are different enough that a companion face must be designed *for* the script. Many major families have script companions designed to the same voice (e.g. the Arabic or Cyrillic companions of established superfamilies); where they do not, pick the best-designed script face rather than the closest visual match.

What to verify per script, as a checklist table:

| Script | Verify beyond the basics |
|---|---|
| Latin (with diacritics) | Full Latin-Extended coverage; language-specific marks (č, ś, ů, ñ); inverted marks and guillemets where relevant |
| Cyrillic | Regional variants (Bulgarian/Serbian letterform preferences); numerals and punctuation |
| Greek | Polytonic vs monotonic needs; final-sigma handling |
| Arabic / Persian | Joining quality, contextual forms, digit style (Eastern Arabic vs Arabic numerals), kashida behaviour |
| Devanagari and Indic | Conjuncts, matras, headline (shirorekha) alignment; complex shaping quality |
| CJK | Count of glyphs actually needed (thousands), regional variants (JP/SC/TC/K), vertical setting if relevant |
| Thai / Lao / Khmer | Stacking behaviour, mark placement, line-breaking rules (no spaces between words) |

Shaping quality is the deep check for complex scripts: the face must work with the platform's text-shaping engine, and poorly drawn contextual forms are visible to every native reader even if invisible to the designer. When a project serves a script the team cannot evaluate internally, the right move is a review by a native reader — a cheap step compared to relaunching.

### 3.4 Family size, weights and the cost of each

Every additional weight is a file to ship and a licence dimension to pay for. A disciplined default for a product: two or three weights of the text face (Regular, Medium or SemiBold, Bold), plus an italic where content needs emphasis, plus the display voice if one exists. Hierarchy needs are real but can be met with weight *steps of 100–200*, size steps and colour rather than by licensing six weights ([Typographic hierarchy](typographic-hierarchy.md)). Variable fonts change the economics: one file can carry the full weight range — see [Web typography](web-typography.md) for the delivery trade-offs.

### 3.5 Web font performance as a selection criterion

Performance belongs in selection, not just implementation, because the chosen *number of files* is decided here. Every static weight and style is a separate file; a four-weight family with italics is eight requests' worth of payload, while a variable font can carry the same range in one (see [Web typography](web-typography.md) 4 for the mechanics). The selection-level guidance:

- **Prefer variable fonts when many weights are needed** — the payload story is usually better than several static files, and hierarchy gains intermediate steps ([Typographic hierarchy](typographic-hierarchy.md)).
- **Count files, not faces** — a two-face system with three weights each is a six-file commitment; the pairing decision ([Font pairing](font-pairing.md)) should be taken knowing that cost.
- **Remember subsetting and formats are engineering's job, but coverage is yours** — the character set you require (3.3) directly determines how much can be subsetted away; a face pulled in for three accented characters can carry its whole extended set with it.
- **Treat load behaviour as a design constraint** — a display face that arrives late will ship with `font-display: optional` and sometimes not appear at all; choose display faces that degrade gracefully ([Web typography](web-typography.md) 4.2).

None of this means performance dictates the choice: it means the choice is made *knowing* the delivery consequences, which is the difference between a selection and a wish.

### 3.6 Font compatibility

"Will these fonts work everywhere they need to?" has four distinct layers, each failing differently:

- **Format compatibility** — WOFF2 is universal in current browsers; print and desktop contexts need the foundry's OTF/TTF builds; very old embedded environments may need WOFF or TTF. Check the format matrix of your platforms before committing, and note that a licence permitting web use may not include the desktop formats the print run needs (4.1).
- **Cross-platform rendering** — the same file renders differently across operating systems (antialiasing, hinting, subpixel strategies have all diverged historically) and across screen densities. The audit discipline of [Typography fundamentals](typography-fundamentals.md) 5.1 applies per platform, not just per size: what passes on a high-DPI phone can fail on a low-DPI external monitor.
- **Metric compatibility with fallbacks** — every face implies a fallback story: what renders before it loads (web), what renders for characters it lacks (3.3), and what renders on platforms without it. Metrics that differ produce reflow and size jumps ([Web typography](web-typography.md) 4.3); a face whose open-source lookalike exists (or whose foundry supplies metric-adjusted fallbacks) degrades gracefully.
- **Design-system compatibility** — the face must behave in the contexts the system will put it in: variable-axis support where the system animates, tabular figures where tables exist, and italic coverage where emphasis appears. This is compatibility with *your own components*, and it is the layer most often discovered late.

The practical habit: add a "compatibility row" to the selection record — formats, fallback stack, tested platforms — so the next team inherits the answers, not the archaeology.

## 4. How it works: the licensing landscape

### 4.1 Desktop vs web licensing

Commercial font licensing splits along the *place of use*, and the two licence kinds are usually sold separately:

- **Desktop licences** cover installing the font on machines and using it inside documents, logos, print and images. They are typically priced per user, per machine or per organisation tier.
- **Web font licences** cover serving the font as part of a product: priced per domain, per page view band, or flat. Embedding in a native mobile app is usually a third category (app/embedded licences); EPUB, broadcast and hardware embedding are further categories.

Professional practice when a commercial face is in play: read the licence for the *exact* use (a logo use, a template sold to customers, and a web app each may need different rights), verify who in the organisation is licensed, and record the licence in the design-system documentation. When in doubt, ask the foundry — licence terms are usually negotiable and clarified quickly.

The licence categories, as a comparison of what each typically covers (exact terms vary by foundry — this table is the professional map, not a substitute for reading the actual licence):

| Use | Typical licence category | Common pricing basis |
|---|---|---|
| Installed in documents, print, images | Desktop | Per user / per machine / org tier |
| Served from a website's own assets | Web font | Per domain, per page-view band, or flat |
| Embedded in a native mobile app | App / embedded | Per app title, per platform |
| Embedded in EPUB / PDF documents | Publish / document embed | Per title or per edition |
| Used in broadcast / film | Broadcast | Per production |
| Inside hardware / firmware | Hardware / OEM | Negotiated per device |
| Sold onward inside templates | Resale / template | Usually explicitly restricted; negotiate |

The two failure patterns to watch: using a desktop-only licence to serve web fonts (a contractual violation even if technically trivial), and building a logo in a face whose licence forbids logo use or requires an upgrade tier. Both surface during due diligence, rebrand or audit — years after the "free" decision.

### 4.2 The SIL Open Font License (OFL)

The OFL is the dominant free/libre font licence and the licence of most of the Google Fonts collection. Key facts, verified from the licence's own site:

- The current version is **OFL 1.1** (released 26 February 2007, unchanged since). It is a free, libre and open-source licence written specifically for fonts. [accessed]
- It permits **use** in essentially any context — books, posters, logos, websites, embedding in apps and software — including commercial use, with no acknowledgement required. [accessed]
- It permits **study, modification and redistribution**, with the condition that redistributed modified fonts remain under the OFL and are distributed in editable (source) form where provided. [accessed]
- It does **not** permit selling the font files *alone* as the product; charging is acceptable when the fonts are bundled with software or services. [accessed]
- Authors keep copyright and may declare **Reserved Font Names (RFNs)**: modified versions may not reuse the protected name, so derivatives must be renamed. Some Google Fonts families use RFNs — relevant if you fork or subset-and-rename. [accessed]

Practical consequence: OFL fonts are safe for commercial web and product use, including self-hosting and subsetting, subject to keeping the licence file with redistributed copies and respecting RFNs on modifications.

### 4.3 Google Fonts and other free sources

The Google Fonts catalogue (fonts.google.com) serves open-source fonts; its underlying repository organises families by licence directory, and states that most families use the SIL Open Font License v1.1, with some under Apache 2.0 and the Ubuntu families under the Ubuntu Font Licence v1.0. The repository's own guidance is to read the licence for every font used. [accessed]

Two delivery routes exist: the Google Fonts hosted API (serves optimised, subsetted files) and self-hosting from the repository or via third-party distribution packages (e.g. Fontsource npm packages, which the repository itself references). [accessed] The trade-offs — performance, privacy, control — are covered in [Web typography](web-typography.md) 5. Free does not mean unverified: even within the catalogue, check per-family licence files, and check that a font *offered* on a third-party site is legitimately distributed — pirate distributions of commercial faces are common.

The delivery routes compared, since the choice affects selection as well as engineering:

| Route | Advantages | Costs |
|---|---|---|
| Hosted API (e.g. Google Fonts) | Automatic subsetting and optimisation; zero asset pipeline; instant catalogue breadth | Third-party dependency and request; data leaves your domain; less control over versions |
| Self-hosted files | Full control; one origin; works offline/air-gapped; consistent caching | You replicate subsetting, format and cache policy yourself |
| Distribution packages (npm) | Versioned like code; audit-friendly; works with bundlers | Update cadence follows the package, not the foundry |

Selection-level consequences: an air-gapped or privacy-sensitive product rules out the hosted route before any face is chosen; a compliance-heavy organisation may prefer package-distributed OFL fonts because their provenance is auditable like any dependency. Decide the route *with* the face, not after it.

### 4.4 Licence verification procedure

Before any face enters a codebase or a brand kit:

1. **Identify the family and exact version** — variants and forks differ in rights.
2. **Locate the licence text** — the LICENSE/OFL.txt file shipped with the font, the foundry's EULA, or the catalogue entry.
3. **Classify the licence** — OFL/Apache/Ubuntu (free, self-hostable), commercial web licence, trial licence (often *forbidden* in production — a very common violation).
4. **Match uses against permissions** — web serving, app embedding, logo use, template/derivative distribution, subsetting (rarely restricted, but check; web.dev notes subsetting permission should be confirmed). [accessed]
5. **Record it** — file the licence text and the verification note with the design system; future maintainers should not have to redo the research.
6. **Budget renewals** — commercial web licences are often view-band-based; traffic growth can exceed the tier.

A worked verification, to show the procedure in motion: a team shortlists a face from a commercial foundry's catalogue for a marketing site, a printed brochure and (later) a native companion app. Step 2 finds the EULA with three licence products on one page. Step 3 classifies them: desktop (per-seat), web (per-domain, view-band), app (per-title). Step 4 matches uses: the site needs the web licence on the marketing domain — but the product dashboard lives on a different domain, so it needs its own entry or an upgrade to a multi-domain tier; the brochure is covered by two desktop seats for the designers; the native app is *not* covered by either and would need the app licence before launch. Step 5 files the EULA and a note mapping each surface to its licence; step 6 adds a reminder that the web tier's view band must be revisited if traffic triples. Ten minutes of procedure replaced three potential violations.

## 5. Practical application: a selection workflow

### 5.1 Requirements before candidates

Write the requirements down *before* browsing catalogues, so the search is filtered rather than inspirational:

- **Roles needed**: text face only, or text + display + mono? (See [Font pairing](font-pairing.md).)
- **Size range**: smallest and largest sizes actually used.
- **Languages**: the verified list from 3.3.
- **Styles**: weights, italics, figures style (tabular needed?), widths.
- **Delivery**: web (self-hosted or hosted), print, app — and therefore the licence class.
- **Voice**: three adjectives the brand should project.

Three questions to put to stakeholders while writing that list, because each changes the answer: *Where will this actually ship?* (a logo licence is a different product from a web app licence — 4.1); *Whose names will appear in it?* (the language list is user-generated, not just content-generated — 3.3); *What happens next year?* (an event brand kit reused annually needs faces with licences and formats that survive the next edition — see [Visual identity](../branding/visual-identity.md)).

### 5.2 The shortlist funnel

1. **Filter** catalogues (Google Fonts, foundry sites) by class, weights and language support. Keep the filters strict — a shortlist of 3–5 candidates beats a library of 30.
2. **Audit anatomy** per candidate with the specimen test from [Typography fundamentals](typography-fundamentals.md) 5.1, at your real sizes.
3. **Test on real content**: set the product's actual worst-case strings — longest words, accented names, densest table — not lorem ipsum.
4. **Pair-check**: if a display or secondary face is needed, run candidates through the pairing evaluation in [Font pairing](font-pairing.md).
5. **Verify licence and coverage** per 4.4 and 3.3.
6. **Record the decision**: rationale, licence, weights, fallbacks — the note becomes part of the design system.

Applied to the repository's core scenario, the funnel becomes the event-brand procedure: the fixed logo already fixes the voice; the funnel selects the *supporting* cast — a quiet text face that will never fight the logo, a mono voice for dates and room codes, coverage verified for the event's international audience, licences that permit the kit's reuse next year, and delivery that works on the event venue's flaky Wi-Fi as well as at home ([Visual identity](../branding/visual-identity.md); [Editorial design](editorial-design.md) 5.3 for the programme system the selection feeds).

## 6. Decision framework

| Question | If yes | If no |
|---|---|---|
| Must the face be free and self-hostable? | OFL families (Google Fonts catalogue first) | Commercial families become candidates; budget and record the licence |
| Does content include scripts beyond Latin? | Select per-script companions; verify join/spacing quality | Latin-only check suffices |
| Is text data-dense (tables, codes, timers)? | Require tabular figures and strong l/1/I distinctness | Standard figures fine |
| Is the size range wide (11 px to 60 px+)? | Prefer optical sizing or a text/display split | One robust text face may suffice |
| Is the face load-bearing for brand personality? | Allow a distinctive display voice | Default to a robust neutral text face |

Two compatibility questions complete the framework, following 3.6: *Does the face behave on every platform the product ships to?* (formats, rendering, fallback metrics); and *Does it behave inside every component the system will build?* (variable axes, tabular figures, italics). A face that answers "no" to either needs a documented workaround before selection, not after.

Explicitly subjective, convention and law: the personality mapping (3.1) is professional convention; legibility vs readability (3.2) are established distinctions; the OFL facts (4.2) are licence law as published; "two or three weights" (3.4) is a conventional starting point — adjust to the product's real hierarchy needs.

A closing calibration for agents using this file: run the procedure in order and let earlier steps constrain later ones. Requirements (5.1) prune the catalogue; anatomy audits ([Typography fundamentals](typography-fundamentals.md) 5.1) prune the shortlist; the pairing evaluation ([Font pairing](font-pairing.md) 4) prunes combinations; licence and coverage verification (4.4, 3.3) prune what is actually shippable. The funnel is designed so that taste operates on a small, already-verified set — not so that taste operates on everything and verification cleans up afterwards. When the funnel yields a single survivor, that is a good outcome, not a suspicious one.

## 7. Examples

**Example 1 — the missing accents.** A European event brand chooses a striking display face for headlines; months later, translations arrive and é, ø, ž fall back to a system font mid-headline. The fix costs redesign work: either a face with proper Latin-Extended support, or a deliberate two-face system with a companion for extended scripts. The check at selection time costs minutes.

**Example 2 — the trial licence in production.** A team uses a foundry's free *trial* web fonts (often watermarked or usage-restricted) for a launch site. The licence verification step (4.4, step 3) exists precisely to catch this before launch rather than after.

**Example 3 — data density kills the darling.** A dashboard shortlists a high-contrast serif for its editorial charm. The audit at 12 px on real tables shows hairlines shimmering and proportional figures making columns wobble; the team keeps the serif for prose surfaces and selects a robust neo-grotesque with tabular figures for data surfaces — a split documented in the design system.

**Example 4 — personality inversion done deliberately.** A fintech brand wanting to signal warmth against a category of cold blue dashboards selects a warm old-style serif for headlines over a humanist sans body — an inversion of the "technology = neutral sans" convention, applied deliberately at the *display* level while keeping the body functional. The convention served as the baseline that made the inversion legible as a choice.

**Example 5 — the air-gapped constraint.** A public-sector tool cannot call third-party hosts. The hosted-API route dies at the requirements stage (5.1, "delivery"), narrowing the search to OFL families that self-host cleanly; the team selects from the open catalogue and records each family's licence file in the repository. The constraint made selection *faster*, not slower, because half the market was filtered before browsing began.

**Example 6 — weight creep.** A product begins with Regular and Bold; two years later it ships Light, Medium, SemiBold, ExtraBold and Black — each a file, a licence dimension, and a hierarchy ambiguity, since four of them compete to mean "emphasis". The audit against [Typographic hierarchy](typographic-hierarchy.md) 3.4 collapses the family back to Regular / SemiBold / Bold, with the variable-font option noted for the future ([Web typography](web-typography.md) 4.1).

## 8. Common mistakes

- **Choosing on specimen beauty alone.** "Aa" tiles hide small-size behaviour, real-copy texture and coverage gaps. Test on real content at real sizes.
- **Skipping the language check.** Missing diacritics surface after launch, in user names, and force emergency face swaps.
- **Assuming "free" means "any use".** Trial licences, personal-use licences and RFN conditions all exist even among free-looking downloads.
- **Ignoring weight/style coverage.** Synthesised faux-bold and faux-italic (see [Typography fundamentals](typography-fundamentals.md) 8) quietly degrade a design when the family lacks the called style.
- **Licensing only the desktop rights** for a web product (or vice versa); the two are distinct products of the foundry.
- **Over-licensing weights** the hierarchy never uses, multiplying file weight and licence cost.
- **One face for all scripts.** Latin-optimised faces applied to Arabic or Devanagari produce typographically illiterate settings; select per script.
- **Forgetting numerals.** Proportional figures in tables, text figures in all-caps settings — small anatomical choices with daily visibility.
- **Deciding delivery after the face.** The hosted/self-host/package route determines which faces are even eligible (privacy, offline, auditability); decide it with the face.
- **Choosing shaping-blind.** Selecting a non-Latin companion by visual similarity without a native reader's review of shaping quality (3.3) ships defects every native reader sees.
- **Collecting weights as options.** Every extra weight is a file, a licence dimension and a hierarchy dilution; licence the weights the hierarchy will actually use.

## 9. Evaluation checklist

- [ ] Requirements written before candidates browsed (roles, sizes, languages, styles, delivery, voice)
- [ ] Shortlist audited at real sizes, on real content, including worst-case strings
- [ ] Legibility checks passed (apertures, x-height, l/1/I, counters) at the smallest used size
- [ ] Readability implications assessed for the intended setting (measure, line height plan)
- [ ] Full language list verified per weight, including accented user names
- [ ] Script companions selected deliberately for non-Latin scripts
- [ ] Licence identified, classified and matched to every intended use (web, app, logo, print, subsetting)
- [ ] Licence text and verification note filed with the project
- [ ] Weight/style list minimal and sufficient; variable font considered where flexibility is needed
- [ ] Numerals style and spacing chosen for their contexts
- [ ] Personality mapping checked against brand voice, with any inversion deliberate
- [ ] Per-script verification completed for every script the product serves (3.3 table)
- [ ] Compatibility row recorded: formats, fallback stack, tested platforms (3.6)
- [ ] Delivery route decided with the face (hosted / self-host / package), not after
- [ ] Selection record filed: rationale, licence, weights, fallbacks, compatibility

## 10. Related topics

- [Typography fundamentals](typography-fundamentals.md) — the anatomy and classification vocabulary this file builds on
- [Font pairing](font-pairing.md) — combining the selected faces into a system
- [Typographic hierarchy](typographic-hierarchy.md) — putting the weights and sizes to work
- [Web typography](web-typography.md) — delivery, performance and fallbacks for the selected faces
- [Accessible typography](../accessibility/accessible-typography.md) — WCAG obligations that constrain selection for real audiences
- [Visual identity](../branding/visual-identity.md) — where the typeface sits in the wider brand system
- [Colour theory](../colour/colour-theory.md) — text/background contrast interacts with legibility choices

## 11. References

- SIL International, *SIL Open Font License* (OFL 1.1, 26 February 2007) — permissions, RFN concept, conditions on selling and modification. https://openfontlicense.org/ [accessed 2026-11-23]
- Google Fonts, *google/fonts* repository README — licence organisation of the catalogue (mostly SIL OFL v1.1; some Apache 2.0; Ubuntu Font Licence v1.0), guidance to read each font's licence, redistribution and Fontsource distribution. https://github.com/google/fonts [accessed 2026-11-23]
- web.dev (Google), "Font best practices" — subsetting and licence-permission note for subsetting, delivery optimisation context. https://web.dev/articles/font-best-practices [accessed 2026-11-23]
- Robert Bringhurst, *The Elements of Typographic Style* (Hartley & Marks, 4th ed. 2012) — the typographic standards background against which selection and setting decisions are framed. [canonical]
- Ellen Lupton, *Thinking with Type* (Princeton Architectural Press, 2nd ed. 2010) — legibility, readability and classification teaching. [canonical]
- Erik Spiekermann, *Stop Stealing Sheep & Find Out How Type Works* (Adobe Press, 3rd ed. 2013) — typeface personality and selection in practice. [canonical]
- Sections 3.1 (personality mapping), 3.4 (weight economy) and 5 (workflow) are synthesis of the sources above and of professional practice, stated as conventions rather than laws.
