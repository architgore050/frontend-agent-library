# Project Status — Frontend Agent Library

## 1. What this file is

This file is the repository's research progress and coverage report (mission §14): the completion state of every domain, with verifiable evidence; the sources that were and were not successfully accessed; the known limitations; the outstanding research opportunities; and the validation status. It is written honestly: a domain is marked complete only where its files carry the full standard template with substantive content — not merely because the files exist. Build date: **2026-11-24**.

The counts below were computed on 2026-11-24 with `find` and `wc` over the actual tree, not copied from earlier estimates. Where this file and a domain file disagree about a count, recompute — the tree is the authority.

## 2. Build summary

| Measure | Value |
| --- | --- |
| Knowledge domains (directories) | 15 + a `references/` source layer (16 top-level directories) |
| Substantive domain files | 89 |
| Router and status files | 2 (README.md, PROJECT_STATUS.md) |
| Total files | 91 |
| Total lines (all files) | see table in section 3 (24,165 lines of domain content plus the two root files) |
| Files with the standard numbered template | 89 of 89 |
| Files with a tagged References section | 89 of 89 |
| Placeholder scan (TODO / TBD / XXX / "to be added") | clean — the only matches for "placeholder" in the tree are legitimate subject matter (form-field placeholder guidance, checklist items testing for placeholder content) |
| README relative links verified | 91 of 91 resolve (90 library files + this file), checked programmatically on 2026-11-24 |

## 3. Domain completion

File and line counts per directory, with an honest completeness assessment. "Complete" means: all files carry the standard template, content is substantive (not stubs), cross-links and provenance-tagged references are present, and the domain answers the mission sections assigned to it.

| Directory | Files | Lines | Completeness | Notes |
| --- | --- | --- | --- | --- |
| branding/ | 10 | 2,749 | Complete | Deepest domain, as the mission's founding use case (fixed-logo extension) requires. Strategy → identity → logo systems → fixed-logo analysis → guidelines → governance chain is unbroken. |
| references/ | 7 | 2,857 | Complete | Source layer: bibliography, books, curricula, professional guidelines, case studies, tools, source-accessibility index. The heaviest consumer of live web facts; ages fastest (see section 7). |
| typography/ | 7 | 2,105 | Complete | Full craft chain from anatomy to browser delivery; leans canonical (craft books) plus MDN for implementation. |
| foundations/ | 5 | 1,891 | Complete | Longest individual files in the library (principles of design is the single longest at 450 lines); the perceptual base every other domain cites. |
| graphic-design/ | 6 | 1,604 | Complete | Identity vocabulary beyond logo/colour/type, including art direction and visual styles. |
| ui-ux/ | 6 | 1,622 | Complete | UX → UI → interaction → IA → responsive → implementation; pairs with design-systems/ and accessibility/. |
| applications/ | 6 | 1,465 | Complete | Six production surfaces with their constraint logic; [Marketing assets](applications/marketing-assets.md) is the thinnest at 182 lines but carries the full template. |
| colour/ | 5 | 1,373 | Complete | Theory → psychology → palettes → accessibility → code. Noted limitation: rests almost entirely on canonical books plus MDN, with no fetched primary source of its own (see section 8). |
| design-systems/ | 5 | 1,316 | Complete | Tokens → components → documentation → governance → consistency; strongest implementation-source base (official system documentation). |
| methodology/ | 7 | 1,187 | Complete, on the thin side | Process layer complete with all template sections, but the domain's files are the shortest on average (1187/7 ≈ 170 lines); see section 4. |
| evaluation/ | 7 | 1,238 | Complete | One master framework plus six artefact checklists. Checklists are deliberately compact — they apply the master method rather than restate it; shortness is by design, not omission. |
| accessibility/ | 4 | 1,031 | Complete | WCAG structure, colour, typography, testing; normative numbers backed by W3C/WAI sources. |
| imagery/ | 5 | 1,148 | Complete | Selection, treatment, rights, photography, AI generation; licence and platform-terms sources are heavily `[accessed]`. |
| layout/ | 3 | 878 | Complete, narrowest scope | Three files, but each is deep (grid systems 354 lines). Coverage is representative rather than exhaustive — no separate file for editorial/multi-page layout (that craft lives in [Editorial design](typography/editorial-design.md)). |
| history/ | 3 | 877 | Complete, narrowest scope | Eras, philosophies, thirteen designer profiles. Deliberately a context domain, not a survey; museum and encyclopaedia sources plus canonical surveys. |
| information-design/ | 3 | 824 | Complete, narrowest scope | Hierarchy, data visualisation, diagrams and infographics; smallest domain by lines. Deep enough for routing use, but the thinnest candidate for future expansion. |

Total domain content: 89 files, 24,165 lines. Root files: README.md (the routing manual, rewritten from a 9-line stub on 2026-11-24) and this file.

## 4. Thin spots

The spec threshold for "thin" is roughly 150 lines. Twelve files fall below ~185 lines. All carry the full template and a tagged References section — none is incomplete — but they are the first candidates if the library is deepened:

| File | Lines | Assessment |
| --- | --- | --- |
| [Social media checklist](evaluation/social-media-checklist.md) | 132 | Thinnest file in the library. Complete as an artefact checklist; could grow platform-specific appendices. |
| [Presentation checklist](evaluation/presentation-checklist.md) | 139 | Complete as an artefact checklist. |
| [Poster checklist](evaluation/poster-checklist.md) | 148 | Complete; print-production rows make it dense despite the length. |
| [Design critique (process)](methodology/design-critique.md) | 149 | Complete — a procedure file, not a survey; length is appropriate to an eleven-step protocol. |
| [Iteration](methodology/iteration.md) | 150 | Complete; the loop mechanics are fully specified. |
| [Design thinking](methodology/design-thinking.md) | 163 | Complete; deliberately treats models as teaching devices, not exhaustive surveys. |
| [Research and discovery](methodology/research-and-discovery.md) | 164 | Complete; pairs with the deeper [Brand discovery](branding/brand-discovery.md). |
| [Ideation](methodology/ideation.md) | 170 | Complete. |
| [Design system audit](evaluation/design-system-audit.md) | 170 | Complete; scored rubric format. |
| [Brand identity checklist](evaluation/brand-identity-checklist.md) | 174 | Complete; the H1–H8 item structure carries the weight. |
| [Website visual QA](evaluation/website-visual-qa.md) | 176 | Complete. |
| [Marketing assets](applications/marketing-assets.md) and [AI-assisted design](methodology/ai-assisted-design.md) | 182 each | Complete; shortest of their domains. |

No file is missing a required template section. The pattern is honest and structural: checklist and procedure files are short by design because they delegate depth to the master framework and the domain files they apply.

## 5. Sources successfully accessed

Per the repository's inventory snapshot ([Bibliography](references/bibliography.md), section 3, recomputed 2026-11-24): 177 reference lines tagged `[accessed]`, 144 tagged `[search-verified]`, 208 tagged `[canonical]`, across 208 unique external URLs and roughly 134 unique cited titles in the 81 domain reference sections counted by that scan.

Directly fetched and read during the references phase, on 2026-11-24 (full detail in [Source accessibility](references/source-accessibility.md), section 4.1):

- GOV.UK Design System (design-system.service.gov.uk) — components, patterns, governance model; re-fetched in the same-day verification pass, which refined the component count to 37 components and 30 patterns.
- US Web Design System (designsystem.digital.gov) — v3.14.0 and its category tallies; re-fetched same day.
- MIT Brand Guide Do/Don't page (brand.mit.edu) — the case-studies file's primary brand-manual evidence; succeeded on retry after a first-attempt timeout.
- Figma pricing (figma.com/pricing) — full plan table, seat types, AI-credit allowances.
- Penpot (penpot.app) — open-source status, self-hosting, native tokens.
- Google Fonts developer documentation (developers.google.com/fonts) — served through a machine-translation layer; facts usable, wording not quotable.

The domain files' own `[accessed]` layer (the 177 tagged lines) is dominated by two open, stable source families: W3C/WAI standards and Understanding documents (every accessibility number in the library traces to them) and the Nielsen Norman Group article corpus (the most reused professional-reference domain after W3C), alongside tool documentation, licences and platform terms in imagery/ and design-systems/.

## 6. Sources that could not be accessed

Recorded honestly rather than silently dropped, per the no-fabrication rules:

- **Canva pricing (canva.com)** — HTTP 403 to automated fetching. Only search-snippet evidence exists; all Canva cost claims in the library carry "verify current pricing".
- **Material Design 3 tokens page (m3.material.io)** — fetched but returned no body (JavaScript-rendered site); repository citations of it are `[search-verified]`, not accessed.
- **Event-branding sources** — the three Olympic/event-identity leads (IOC brand guidelines PDF, The Olympic Design archive, USOPC Rule 40 deck) were verified to exist via search results but not fetched; one fetch attempt timed out and did not succeed on retry. Until one is fetched, no specific claim about any event identity's emblem, palette or typography appears in the library — recorded as leads in [Source accessibility](references/source-accessibility.md), section 4.9.
- **University syllabi** — none fetched; the repository scan surfaced no syllabus URLs, so canonicity rests on `[canonical]` attribution and the curricula survey instead.
- **Canonical print works** — the ~208 `[canonical]` attributions (Albers, Arnheim, Müller-Brockmann, Tufte, Aaker, Norman and others) were not accessed as texts; they carry attribution-level claims only, by rule.
- **Bot-blocked and transient** — the Federal Register AI-registration guidance was bot-blocked at access time and is tagged accordingly; two fetch timeouts occurred, one of which (MIT) succeeded on the documented retry.
- **Single-use URLs** — 125 of the 208 unique URLs (about 60 per cent) occur exactly once, mostly platform-specific sizes in applications/ files. These are the most perishable entries in the library and should be treated as leads to re-check, not settled data.

## 7. Known limitations

- **Reference material, not current specifications.** Platform sizes, tool pricing, design-system versions and standards drafts change without notice; the library dates and tags every volatile figure, and consumers must re-verify before external use.
- **Canonical-heavy theoretical domains.** Colour, typography and branding rest substantially on `[canonical]` attribution rather than fetched primary texts — legitimate under the tag rules, but it means specific figures in those domains are conventional starting points more often than in accessibility or design-systems.
- **No rendered examples.** The library is text-only; it teaches with descriptions, tables and code snippets rather than image assets, by design (assets would age and carry rights questions of their own).
- **Narrowest domains are narrow deliberately.** history/, layout/ and information-design/ (three files each) cover their routing obligations without aiming to be surveys; expansion candidates are listed in section 8.
- **Provenance-tag counts are line counts, not claim counts.** One reference line can carry several facts, and one line can carry two tags; the inventory's numbers measure citation effort, not verified-claim volume.
- **Validation depth.** The checks recorded in section 9 are structural plus mechanical surface checks (existence, counts, links, template structure, placeholder scan, British-spelling spot-check, code-block syntax). A full content-accuracy audit — re-reading every numeric claim against its tagged source — has not been performed and would be the next major validation effort.
- **British spelling, English only.** Non-English sources are cited where relevant (for example the ISO-style identity-manual tradition) but the library itself is uniform English.

## 8. Outstanding research opportunities

1. **Fetch one event-identity source.** The single highest-value open fetch is the IOC Olympic Brand Guidelines PDF (publicly served, ~138 pages); promoting it to `[accessed]` would let the event-collateral and fixed-logo files carry specific, sourced event-identity practice.
2. **Give colour a fetched primary source.** The colour domain has no fetched peer-reviewed or primary source; one good fetch (for example a peer-reviewed colour-appearance or CVD-prevalence paper) would materially raise the domain's evidential weight.
3. **Promote load-bearing `[search-verified]` sources.** The WCAG Understanding pages behind the library's most-repeated numbers (4.5:1, 3:1, reflow, target size) are one fetch each away from `[accessed]`.
4. **Deepen the thin list in section 4**, starting with the social media checklist and the methodology domain, if the library's scope grows.
5. **Consolidate single-use vendor citations.** Repeated practical conventions currently spread across one-off vendor URLs (bleed, sign-letter heights, social image sizes) should be consolidated into the owning repository file citing the best available source, per the policy in [Source accessibility](references/source-accessibility.md), section 5.2.
6. **Rossman and Duerden's experience-design book** enters the library through [Books and textbooks](references/books-and-textbooks.md) only; it is not yet cited by any domain file. Note the mission's title is a variant — the published book is *Designing Experiences*, Columbia Business School Publishing, 2019.

## 9. Validation status

**Validated 2026-11-24.** A full mechanical validation pass ran over all 91 Markdown files with `/home/z/my-project/scripts/kb/validate_kb.py` (Python 3, stdlib only; full output in `/home/z/my-project/scripts/kb/validation-report.txt`). Result: **clean — 0 open issues**. Every non-issue finding was individually reviewed and recorded as an accepted exception with a written reason (84 in total); nothing was silently waved through. The earlier checks listed in previous revisions of this section remain true and are superseded by this pass.

Checks run, and what they found:

- **Internal links.** Every relative markdown link in all 91 files was extracted (code blocks excluded) and resolved against the tree. One dead link found and fixed: methodology/ai-assisted-design.md pointed at a non-existent `references/index.md` (now targets [Source accessibility](references/source-accessibility.md), section 9). Three links pointed at directories rather than files — two in [Marketing assets](applications/marketing-assets.md) (`../ui-ux/`) and one in [Graphic language](graphic-design/graphic-language.md) (`../applications/`) — retargeted to concrete files.
- **README routes.** Every `*.md` path mentioned anywhere in README.md (links, tables, prose, inline code) exists. The README's two mentions of the authoring brief are absolute paths outside the repository and are marked as such in its text.
- **Placeholders.** Scanned for TODO, TBD, FIXME, XXX, lorem ipsum, 待补充, 【, runs of underscores and "to be added/completed" across all files including code blocks: no actual placeholder remains. The 44 raw matches were reviewed and are all intentional: PROJECT_STATUS.md quoting the scan's own token list (12), the fillable analysis worksheet in [Fixed-logo analysis](branding/fixed-logo-analysis.md) whose blanks are the deliverable's form fields (28), and checklist or prose items instructing users to search their output for placeholder text (4).
- **Coverage.** All 89 expected domain files exist; the shortest (evaluation/social-media-checklist.md, 132 lines) is above the 120-line thin threshold; per-directory totals match section 3.
- **Structure.** Every file starts with an H1; no duplicate H1 titles across the repository; every domain file over 150 lines contains a References or Related topics section.
- **Template.** All 89 domain files carry 11 numbered H2 sections in strictly increasing order. Two real defects were fixed in this pass: [Art direction](graphic-design/art-direction.md) had "Practical application" at H3 level (promoted to numbered H2 section 5), and [Iconography](graphic-design/iconography.md) numbered its sections 8–12 with 7 skipped (renumbered 7–11, so References is section 11 as everywhere else — the exception previously noted in section 2 is gone). Five accepted deviations, all in `references/`: bibliography (9 sections), case-studies and source-accessibility (10 each), books-and-textbooks and tools-and-software (15 each) — source-layer files whose section structures are adapted to their subject as the authoring brief permits; all are monotonic and end with a tagged References section. 87 renamed-section titles across the library are recorded as informational (the brief allows renaming where the topic warrants).
- **Tagged references.** All 89 domain files end with a References section carrying provenance tags — `[accessed]` / `[search-verified]` / `[canonical]`, written with the access date inside the brackets — 89 of 89.
- **British spelling.** Prose spot-check for American variants (color, center, organize/organization, visualize, behavior, analyze, gray, noun "license"; code blocks, inline code, URLs, reference-list lines, italicised original titles and direct quotations excluded) found 12 genuine American spellings, all fixed across 6 files: "People-centered" → "People-centred" ([Photography](imagery/photography.md)); "licenses"/"license" nouns → "licences"/"licence" ([Brand discovery](branding/brand-discovery.md) ×3, [Brand identity checklist](evaluation/brand-identity-checklist.md), [Web typography](typography/web-typography.md)); "adjacent-colors" → "adjacent-colours" ([Tools and software](references/tools-and-software.md)); "grays"/"gray ban" → "greys"/"grey ban" ([Case studies](references/case-studies.md) ×4, in our own prose — direct quotations of source wording keep the source's spelling). The 35 remaining matches are accepted exceptions — 23 in domain files plus 12 in this file's own account of the scan: original work titles (*Interaction of Color*, *The Art of Color*, *A Color Notation*, *Color Psychology and Color Theory*, *The Power of the Center*), product and institution names (Adobe Color, RIT Vignelli Center, IBM Brand Center, Shutterstock Help Center), direct quotations, the Lighthouse UI label "Analyze page load", and verb uses of "license" (correct British usage).
- **Code examples.** Every fenced CSS block in the library — including all blocks in typography/web-typography.md, layout/*.md and ui-ux/frontend-implementation.md — has balanced braces and only plausible property or `@font-face` descriptor names; every fenced JSON block parses. HTML examples are not mechanically validated. No fixes were needed.
- **Accessibility sources.** All four `accessibility/` files cite w3.org sources.

Also established during this pass: the heading-numbering anomalies first seen in four branding files (brand-discovery, brand-guidelines, brand-strategy, fixed-logo-analysis) are the embedded fillable templates' own headings inside fenced markdown blocks, not document-structure errors.

What remains open (unchanged): a full content-accuracy audit of numeric claims against their tagged sources; a provenance-tag discipline pass over every reference line (this pass verified that tags are present and consistently formatted, not that each entry's URL is live); and re-verification of volatile figures at the moment of any external use. These are recorded as outstanding rather than claimed as done.

## 10. Commit-per-file convention

The repository follows a **one commit per file** convention, to be applied when the work is integrated (authoring agents did not run git, per the brief):

- Each file is committed individually with a message naming the domain and the file slug, for example `docs(colour): palette-development — role-based palette construction and testing`.
- README.md and PROJECT_STATUS.md each receive their own commit (`docs(root): ...`).
- Never batch unrelated files into a single commit: per-file history keeps review, blame and revert domain-scoped, and lets a defective file be rolled back without touching its neighbours.
- Re-verification edits follow the same rule: the file whose citations were refreshed is committed alone, so an access-date bump is traceable to its file.

## 11. Appendix A — per-file line counts

Computed with `find`/`wc` on 2026-11-24; the evidence base for sections 3 and 4. Root files are listed at the end.

| File | Lines |
| --- | --- |
| **accessibility/** (4 files) | **1031** |
| `accessibility/accessibility-testing.md` | 273 |
| `accessibility/accessible-colour.md` | 227 |
| `accessibility/accessible-typography.md` | 241 |
| `accessibility/wcag-fundamentals.md` | 290 |
| **applications/** (6 files) | **1465** |
| `applications/certificates-and-documents.md` | 230 |
| `applications/event-collateral.md` | 264 |
| `applications/marketing-assets.md` | 182 |
| `applications/posters.md` | 297 |
| `applications/presentations.md` | 232 |
| `applications/social-media.md` | 260 |
| **branding/** (10 files) | **2749** |
| `branding/brand-architecture.md` | 242 |
| `branding/brand-discovery.md` | 291 |
| `branding/brand-fundamentals.md` | 296 |
| `branding/brand-governance.md` | 246 |
| `branding/brand-guidelines.md` | 280 |
| `branding/brand-personality.md` | 277 |
| `branding/brand-strategy.md` | 281 |
| `branding/fixed-logo-analysis.md` | 289 |
| `branding/logo-systems.md` | 288 |
| `branding/visual-identity.md` | 259 |
| **colour/** (5 files) | **1373** |
| `colour/colour-accessibility.md` | 251 |
| `colour/colour-in-code.md` | 275 |
| `colour/colour-psychology.md` | 249 |
| `colour/colour-theory.md` | 299 |
| `colour/palette-development.md` | 299 |
| **design-systems/** (5 files) | **1316** |
| `design-systems/component-systems.md` | 301 |
| `design-systems/design-tokens.md` | 331 |
| `design-systems/documentation.md` | 207 |
| `design-systems/governance.md` | 227 |
| `design-systems/visual-consistency.md` | 250 |
| **evaluation/** (7 files) | **1238** |
| `evaluation/brand-identity-checklist.md` | 174 |
| `evaluation/design-quality-framework.md` | 299 |
| `evaluation/design-system-audit.md` | 170 |
| `evaluation/poster-checklist.md` | 148 |
| `evaluation/presentation-checklist.md` | 139 |
| `evaluation/social-media-checklist.md` | 132 |
| `evaluation/website-visual-qa.md` | 176 |
| **foundations/** (5 files) | **1891** |
| `foundations/composition.md` | 359 |
| `foundations/design-critique.md` | 345 |
| `foundations/elements-of-design.md` | 345 |
| `foundations/gestalt-and-perception.md` | 392 |
| `foundations/principles-of-design.md` | 450 |
| **graphic-design/** (6 files) | **1604** |
| `graphic-design/art-direction.md` | 214 |
| `graphic-design/graphic-language.md` | 350 |
| `graphic-design/iconography.md` | 234 |
| `graphic-design/illustration.md` | 203 |
| `graphic-design/patterns-and-textures.md` | 202 |
| `graphic-design/visual-styles.md` | 401 |
| **history/** (3 files) | **877** |
| `history/design-philosophies.md` | 241 |
| `history/graphic-design-history.md` | 324 |
| `history/influential-designers.md` | 312 |
| **imagery/** (5 files) | **1148** |
| `imagery/ai-image-generation.md` | 301 |
| `imagery/image-rights.md` | 200 |
| `imagery/image-selection.md` | 199 |
| `imagery/image-treatment.md` | 198 |
| `imagery/photography.md` | 250 |
| **information-design/** (3 files) | **824** |
| `information-design/data-visualisation.md` | 335 |
| `information-design/diagrams-and-infographics.md` | 247 |
| `information-design/information-hierarchy.md` | 242 |
| **layout/** (3 files) | **878** |
| `layout/grid-systems.md` | 354 |
| `layout/responsive-layouts.md` | 257 |
| `layout/spacing-and-proportion.md` | 267 |
| **methodology/** (7 files) | **1187** |
| `methodology/ai-assisted-design.md` | 182 |
| `methodology/design-critique.md` | 149 |
| `methodology/design-thinking.md` | 163 |
| `methodology/ideation.md` | 170 |
| `methodology/iteration.md` | 150 |
| `methodology/moodboards.md` | 209 |
| `methodology/research-and-discovery.md` | 164 |
| **typography/** (7 files) | **2105** |
| `typography/editorial-design.md` | 233 |
| `typography/font-pairing.md` | 243 |
| `typography/typeface-selection.md` | 289 |
| `typography/typesetting.md` | 293 |
| `typography/typographic-hierarchy.md` | 287 |
| `typography/typography-fundamentals.md` | 400 |
| `typography/web-typography.md` | 360 |
| **ui-ux/** (6 files) | **1622** |
| `ui-ux/frontend-implementation.md` | 373 |
| `ui-ux/information-architecture.md` | 206 |
| `ui-ux/interaction-design.md` | 220 |
| `ui-ux/responsive-design.md` | 192 |
| `ui-ux/ui-fundamentals.md` | 337 |
| `ui-ux/ux-fundamentals.md` | 294 |
| **references/** (7 files) | **2857** |
| `references/academic-curricula.md` | 507 |
| `references/bibliography.md` | 301 |
| `references/books-and-textbooks.md` | 408 |
| `references/case-studies.md` | 395 |
| `references/professional-guidelines.md` | 552 |
| `references/source-accessibility.md` | 251 |
| `references/tools-and-software.md` | 443 |
| **Root** (2 files) | **601** |
| `README.md` | 350 |
| `PROJECT_STATUS.md` | 251 |
