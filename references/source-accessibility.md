# Source Accessibility

## 1. What is this file?

This file is the repository's source-accessibility index (mission §10): a classified inventory of the sources the knowledge base relies on, stating for each *how it was or was not accessed* and therefore *how much weight a claim drawn from it can bear*. The repository cites hundreds of URLs and dozens of canonical works across its domain files. Those citations are not equally trustworthy: some pages were fetched and read in full, some were verified only as search results, some are public brand manuals whose content can change without notice, and some canonical books have never been opened by any contributing agent. Future agents who cannot tell these cases apart will eventually present an unverified claim as a settled fact — this file exists to make that distinction mechanical.

The inventory was compiled in two ways, both during this project: by scanning the References sections of every populated domain file (all 81 substantive files, extracting URLs and canonical citations), and by fetching a set of key sources directly during the references phase. This file is one of a small set of source registers maintained in this directory, each with a distinct cut over the same underlying citations: [Bibliography](bibliography.md) organises sources by subject; [Books and textbooks](books-and-textbooks.md) and [Academic curricula](academic-curricula.md) register the canonical print and teaching layer; [Professional guidelines](professional-guidelines.md) covers professional-body sources; and [Case studies](case-studies.md) and [Tools and software](tools-and-software.md) are the heaviest consumers of live web sources, whose verification status matters most. Use this file when the question is *how well was this source actually accessed*, not *what does it cover*.

## 2. Provenance tags used across the repository

Every reference list in this repository tags each source with exactly one of these tags. The definitions below are normative for all future files.

| Tag | Meaning | What you may claim from it |
| --- | --- | --- |
| `[accessed]` | The page or work was fetched and read (or key parts read) during this project, on the recorded access date. | Facts as stated by the source, with the access date noted. Re-verify anything time-sensitive (pricing, version numbers, product capabilities). |
| `[search-verified]` | The source appeared in search results this project (title and URL seen in tool output) but the page was not fetched. | The existence and apparent relevance of the source. Specific claims attributed to it remain unverified until fetched. |
| `[canonical]` | A well-established work attributed from general professional knowledge. No page numbers, no invented quotes. | Widely accepted ideas at the level of attribution (author, title, thesis). Any specific figure, quote or page reference is forbidden under this tag. |

A fourth status, `verify`, is used inside documents (not as a reference tag) for facts that are plausible but unconfirmed — for example "verify current pricing". A `verify` marker is a promise to the reader that the statement is provisional; it must not be silently dropped when text is edited. Tag discipline is enforced at the point of writing, not after: when a file is reviewed (see [Design critique](../foundations/design-critique.md) and the repository's evaluation checklists), every reference entry should carry exactly one tag, and an untagged entry is treated as unverified regardless of how familiar the source sounds.

### 2.1 Worked examples

Correct usage, `[accessed]`: a file states "USWDS v3.14.0 lists 48 components" with a reference entry for https://designsystem.digital.gov/ tagged `[accessed]` and dated — the number was read from the fetched page, so the specific figure is supportable (and should carry its date, because version numbers age).

Correct usage, `[canonical]`: a file attributes the idea that colour interaction is perceptual, not just physical, to "Albers, *Interaction of Color*, Yale University Press, 1963" — the thesis and imprint are well established; no page number or quote is attached.

Incorrect usage: attaching "as Arnheim wrote on page 34..." to a `[canonical]` entry — the page number cannot be known without access, so it would be a fabrication by definition. The correct form is either to fetch the work, or to restate the idea in one's own words and attribute the thesis at attribution level.

## 3. Access-level classification

The mission defines seven access levels. The table below states what each level is, what it lets a citing agent claim, and the characteristic risk of over-trusting it.

| Level | Definition | Supports | Risk if over-trusted |
| --- | --- | --- | --- |
| Full-text open access | The complete work is publicly readable (standards, MDN, open documentation). | Specific facts, numbers, quotes with attribution. | Page content changes; record the access date and re-check time-sensitive details. |
| Authorised previews | Partial official access sanctioned by the rights holder (sample chapters, public media kits, preview sites). | What the preview actually shows, clearly scoped. | Assuming the preview represents the whole work. |
| Publisher descriptions | A publisher's or vendor's page *about* a work or product, not the work itself. | Existence, scope, claimed positioning. | Treating marketing copy as neutral evidence. |
| Abstracts | Summary-only access (abstract pages, paywalled papers). | Findings as summarised, flagged as abstract-level. | Paraphrasing beyond the abstract's claims. |
| Secondary reviews | Third-party articles, blog posts, aggregator content. | Context, professional opinion, leads to primary sources. | Citing a secondary source for a fact that has a primary source. |
| University syllabi | Reading lists and course outlines. | Evidence of canonical status; links to open materials. | Citing the syllabus as if it were the reading itself. |
| Public brand manuals | Officially published brand/identity guidelines (universities, companies, governments). | Named rules of that organisation (colours, clear space, typefaces) as of the access date. | Treating another organisation's rules as general law; manuals change and pages move. |
| Canonical-not-accessed | Established works cited from professional knowledge without direct access. | Attribution-level claims only, tagged `[canonical]`. | Inventing quotes, figures, editions or page numbers. |

### 3.1 How levels map to tags

The access level is about the *source*; the provenance tag is about *this project's relationship to it*. The mapping is straightforward but worth stating: full-text open access + fetched = `[accessed]`; full-text open access or brand manual + seen only as URL/repository citation = `[search-verified]`; canonical-not-accessed = `[canonical]`. Publisher descriptions and abstracts can carry any tag depending on how they were reached — what the level adds is a *limit on the claim*, applied in section 8. When you cannot determine a source's level, default to the most restrictive interpretation: claim less than you might until you have fetched it.

Two edge cases deserve explicit rules. First, a canonical work *with* access: if you actually obtain the book or paper (a legal open scan, a library copy digitised by the publisher), it stops being canonical-not-accessed and becomes `[accessed]` — the tag then changes, and page numbers become permissible, because they are now real. Second, a source with split versions: a standard whose current version is open and whose draft (like WCAG 3) is elsewhere is two sources, not one — cite the version you used, because claims attached to the wrong version are the most common silent citation error in standards work.

### 3.2 Deciding the level in practice

When classifying a new source, ask three questions in order. *Is the complete work on the page I fetched?* If yes, full-text open access. *If not, does the page exist to advertise or summarise the work?* Then it is a publisher description (vendor pages, book landing pages) or an abstract (academic records), and claims are bounded accordingly. *Does the page present someone else's work to me?* — reviews, blog coverage, syllabi — then it is secondary, and its value is as a lead to the primary source. The classification takes under a minute once the habit exists, and it prevents the most common over-claim: treating a review of a book, or a vendor page about a tool, as if it were the book or the tool.

## 4. Inventory by access level

### 4.1 Fetched and read this project (`[accessed]`, access date 2026-11-24)

| Source | URL | What was taken from it |
| --- | --- | --- |
| GOV.UK Design System homepage — Government Digital Service | https://design-system.service.gov.uk/ | Purpose statement, component inventory (37 components and 30 patterns enumerated in the navigation), governance model, contribution criteria, GOV.UK Frontend v6.6.0 |
| US Web Design System homepage — GSA | https://designsystem.digital.gov/ | Mission, v3.14.0, navigation tallies (47 component pages / 3 pattern groups / 5 templates / 8 token categories / 15 utilities), "dozens of agencies and nearly 200 sites", open-source maintenance |
| MIT Brand Guide, Do/Don't page | https://brand.mit.edu/applying-brand/do-dont | Logo, seal and lock-up rules; 1-inch clear space; 30–40% ratio; Neue Haas Grotesk Medium; MIT red; surface-scoped rules; sub-brand eligibility (events excluded) |
| Figma pricing page | https://www.figma.com/pricing/ | Full plan table (Starter free; Professional $16 full seat, $12 Dev, $3 Collab; Organization $55; Enterprise $90), seat types, Starter limits (30-day history, 10 variable modes, free viewers), variables modes by tier (Professional 20; Organization/Enterprise unlimited), AI-credit allowances |
| Penpot homepage — KALEIDOS | https://penpot.app/ | Open-source status, free sign-up, self-hosting, native design tokens, open file format, MCP server |
| Google Fonts developer documentation — Google | https://developers.google.com/fonts/ | Open-source licensing, free commercial use, stylesheet-based serving, Fonts Developer API |

Notes on fetch quality: the Google Fonts page was served through a machine translation layer (content substance usable; wording is not quotable). The Material Design 3 tokens page (https://m3.material.io/foundations/design-tokens) was fetched but returned no page body — it is a JavaScript-rendered site; treat repository citations of it as `[search-verified]`, not accessed. Canva's pricing page (https://www.canva.com/pricing/) returned HTTP 403 to automated fetching; see 4.4 for what was verified about it instead.

A same-day re-verification pass repeated four of the six fetches (GOV.UK, USWDS, MIT do/don't, Figma pricing) later on 2026-11-24. It confirmed the substance of every page and refined two figures: the GOV.UK navigation enumerates 37 components and 30 patterns (a first pass had recorded "roughly 35"), and the USWDS category counts are tallies of navigation links (47 component pages), not totals stated on the page. The MIT fetch succeeded only on a second attempt after a first-attempt timeout — see 5.1, failure mode 5. The pass cost four fetches and materially improved accuracy; it is the working proof of the re-verification policy in section 9.1.

### 4.2 Full-text open access — cited in the repository, not fetched this project

These are cited across the repository's domain files and are, to general professional knowledge, fully open documentation. They were seen as URLs in the repository scan. Re-fetch before quoting specific text.

- W3C/WAI standards and guidance: WCAG 2.2 (https://www.w3.org/TR/WCAG22), Understanding WCAG documents (contrast-minimum, non-text-contrast, contrast-enhanced, reflow, text-spacing, focus-visible, target-size-minimum), WAI tutorials (https://www.w3.org/WAI/tutorials/images/), ARIA Authoring Practices Guide (https://www.w3.org/WAI/ARIA/apg/), the Visual Contrast of Text Subgroup wiki. The repository leans on these for every normative accessibility number.
- MDN Web Docs: CSS colour values incl. `oklch` and `color()`, `prefers-color-scheme`, `prefers-reduced-motion`, `color-gamut` (developer.mozilla.org) — the repository's implementation-layer ground truth for CSS behaviour.
- Design systems: GOV.UK components (https://design-system.service.gov.uk/components/button/), Material 2/3 (m2/m3.material.io), Atlassian Design System (https://atlassian.design/foundations/), Carbon Design System (https://www.carbondesignsystem.com), Material Design UI pack (https://www.mdui.org/en/design/1/style/icons.html).
- Tool and standards documentation: Style Dictionary (https://styledictionary.com, https://github.com/style-dictionary/style-dictionary), Design Tokens Community Group draft format (https://www.designtokens.org/TR/drafts/format/), Storybook (https://storybook.js.org/docs/get-started/why-storybook), Open Font License (https://openfontlicense.org/), WAVE (https://wave.webaim.org/), axe (https://www.deque.com/axe/), Lighthouse (https://developer.chrome.com/docs/lighthouse/overview/), Unsplash licence (https://unsplash.com/license).
- Institutional and cultural references: Vitsoe on Rams and good design (https://www.vitsoe.com/us/about/good-design, https://www.vitsoe.com/us/about/dieter-rams), Tate on Bauhaus (https://www.tate.org.uk/art/art-terms/b/bauhaus), Getty on the Bauhaus (https://www.getty.edu/research/exhibitions_events/exhibitions/bauhaus/new_artist/history/), Wikipedia on the International Typographic Style (https://en.wikipedia.org/wiki/International_Typographic_Style), Edward Tufte's books page (https://www.edwardtufte.com/books/).
- Nielsen Norman Group articles (nngroup.com): visual-design principles, Gestalt proximity, design critiques, ten usability heuristics, response-time limits, form-design placeholders, progress indicators, card sorting vs tree testing, stakeholder interviews — the repository's most heavily reused professional-reference domain after W3C.
- Legal and regulatory: US Copyright Office AI materials (https://www.copyright.gov/ai), Federal Register AI registration guidance (https://www.federalregister.gov/documents/2023/03/16/2023-05321/...), OpenAI terms (https://openai.com/policies/row-terms-of-use), Midjourney terms (https://docs.midjourney.com/hc/en-us/articles/32083055291277-Terms-of-Service).

### 4.3 Public brand manuals — cited in the repository, not fetched this project

These publish official identity rules. Content is authoritative for the organisation named, changes without notice, and is *not* general design law.

- MIT Brand Guide: https://brand.mit.edu/applying-brand/do-dont (fetched this project — see 4.1).
- University at Buffalo brand identity, clear-space rules: https://www.buffalo.edu/brand/identity/usage/Clear-space.html
- Uber brand user guide: https://assets.uber.com/d/k4nuxdZ8MC7E/user-guide
- Spotify newsroom media kit: https://newsroom.spotify.com/media-kit/logo-and-brand-assets
- Uber Eats merchant co-marketing tools: https://merchants.ubereats.com/us/en/resources/learning-center/co-marketing-tools

### 4.4 Publisher/product descriptions and partial access

- Canva pricing: https://www.canva.com/en/pricing — direct fetch blocked (HTTP 403). A search snippet from this page, seen this project, states that K-12 educational organisations and not-for-profits can access most premium features free. Third-party reporting (dated July 2026, seen only as a search snippet) puts Canva Pro at about US$18/month or US$144/year with 5 GB free storage; treat as unverified and always write "verify current pricing" for Canva costs.
- Figma and Penpot pages: fetched this project (4.1).

### 4.5 Secondary and professional reviews — cited in the repository, not fetched

Use for context and leads; prefer the primary source when one exists.

- Medium: EightShapes essays on defining design systems and team models (medium.com/eightshapes-llc/...), Design Bootcamp essays on logo grid systems and the 60-30-10 colour rule, a design-system adoption critique (medium.com/@disco_lu/...), a Style Dictionary walkthrough (didoo.medium.com/...).
- Smashing Magazine on brutalist web development (https://www.smashingmagazine.com/2020/01/split-personality-brutalist-web-development).
- Accessibility secondary explainers: Deque University WCAG reference pages (dequeuniversity.com), Digital A11y on SC 1.4.11 (https://www.digitala11y.com/understanding-sc-1-4-11-non-text-contrast).
- Print and production vendors: Pannier Graphics letter-height visibility chart, SpeedPro on large-format resolution, Papersizes.org on A sizes, Polotno bleed calculator, Template.net and beehiiv on email image sizes, Recurpost on social image sizes. Vendor blogs of this kind are useful for practical conventions (sign letter heights, bleed) but are marketing-adjacent; verify any number against a second source before making it load-bearing.
- Brand consultancies and vendors: Splash Creative brand-audit checklist, Stryve and Baron Sauvage and Vivaldi on brand architecture, Bynder and Templafy brand-asset-management pages, zeroheight help-centre adoption article, Harvard Business School Online on positioning statements, GV Sprint page (https://www.gv.com/sprint).
- Aggregators and miscellany: Goodreads quote pages, Figma resource-library mood-board article (https://www.figma.com/resource-library/how-to-make-a-mood-board), Colour Blind Awareness (https://www.colourblindawareness.org/colour-blindness).

### 4.6 Academic sources — mixed access, cited in the repository, not fetched

- Annual Review of Psychology article (https://www.annualreviews.org/content/journals/10.1146/annurev-psych-010213-115035) — publisher page with abstract-level access only; do not cite specifics beyond the abstract without obtaining the text.
- PubMed Central article (https://pmc.ncbi.nlm.nih.gov/articles/PMC4383146) — PMC is by policy a full-text open-access repository; the URL was seen in the repository scan and should be fetched before quoting.
- Michael Shanks, Stanford, PDF book chapter (https://web.stanford.edu/~mshanks/MichaelShanks/files/509554.pdf) — publicly hosted academic PDF; treat as full-text open access once fetched and read.

### 4.7 University syllabi

No syllabus was fetched this project, and the repository scan surfaced no syllabus URLs. Syllabi remain a listed access level for future use: when one is found, record it here with its URL, the institution, and which readings it canonises — syllabi are evidence of canonical status, not substitutes for reading the works. If a future agent needs to *establish* canonicity (for example, to justify tagging a book `[canonical]`), a university syllabus that lists it is exactly the right evidence to record in this section.

### 4.8 Canonical works — not accessed, attributed from general knowledge

Cited across the repository with the `[canonical]` tag; the full register by subject appears in section 6. Attribution-level claims only; never attach page numbers, quotes or specific figures to these without obtaining the work.

### 4.9 Event-branding leads — search-verified, not fetched

The event-branding case that [Case studies](case-studies.md) section 4.11 sketches could not be fetched this project; three sources were verified to exist through search results and are recorded here as leads, not as read sources:

- International Olympic Committee, *Olympic Brand Guidelines* (PDF, ~138 pages): https://stillmed.olympics.com/media/Documents/International-Olympic-Committee/Olympic-brand/Olympic-Brand-Guidelines.pdf — the rights holder's full brand manual, publicly served; likely the richest single fetchable event-identity source in this domain.
- The Olympic Design (Olympic Foundation for Culture and Heritage), "Milano Cortina 2026 — Look of the Games": https://www.theolympicdesign.com/olympic-games/the-look-of-the-games/milano-cortina-2026 — per-Games identity documentation; the fetch attempt timed out this project (5.1, failure mode 5).
- United States Olympic & Paralympic Committee, "Guidelines for brands (non-Olympic and Paralympic)", Rule 40 registration deck: https://rule40registration.teamusa.org/Assets/doc/2026/Rule40_UpdatedDeck_081325.pdf — third-party co-brand rules; the Milano Cortina 2026 blackout window of 30 January – 24 February 2026 is known from the search snippet only.

Until one of these is fetched, no specific claim about any event identity's emblem, palette or typography may be made in this repository. All three are publicly served documents, so a future agent should be able to promote them to `[accessed]` with one fetch each; per section 9.1, the access date and the citing-file updates then follow mechanically.

## 5. Repository citation patterns (observed this project)

The scan of all reference sections produced measurable patterns that future agents should know before adding sources. Counts below are occurrences of each URL string across the repository's reference sections, as observed in the scan output:

- The most reused URLs are institutional and normative: the MIT do/don't page (6 occurrences across branding files), the Uber Eats co-marketing page (5), NN/g's visual-design principles (4), the Buffalo clear-space page (4), the GOV.UK Design System root and its Button component page (3 each), Atlassian's illustrations foundations page (3), and NN/g's Gestalt-proximity and design-critique articles (3 each). A small set of reusable, stable, open pages is doing most of the citation work — exactly the intended behaviour of a knowledge base.
- W3C/WAI URLs dominate by volume when counted by domain rather than by page: every accessibility-related file cites multiple Understanding documents. The pattern to preserve: *normative sources for normative claims*.
- Tool documentation (Style Dictionary, Storybook, designtokens.org, Carbon, Material) clusters in the design-systems directory — the repository keeps implementation sources with implementation files, which makes re-verification cheap because a source's citing files are predictable from its subject.
- One-off vendor URLs (print vendors, size guides, consultancies) appear once each, mostly in applications and evaluation files. This is the riskiest citation class: single-use vendor pages move or die silently. Future agents should prefer consolidating repeated practical conventions (for example bleed or sign-letter-height guidance) into one repository file that cites the best available source, rather than sprinkling one-off vendor citations across files.
- No syllabus URLs and no paywalled-journal PDFs were found in domain files; the academic citations present are one annual-review abstract, one PMC article and one university-hosted PDF. The repository's scholarly weight is deliberately carried by `[canonical]` attributions instead — legitimate, provided section 2's rules are respected.

### 5.1 Source-health risks observed this session

The fetching performed this project surfaced four failure modes that future agents should expect and plan around; each was observed on a real source:

1. **JavaScript-rendered pages return empty bodies to automated fetches.** The Material 3 tokens page (m3.material.io) responded with a title and no content. Such sites are not unverifiable — they are verifiable in a browser but not by simple tooling. Mark them `[search-verified]` unless a render-capable method is available, and note the limitation.
2. **Bot-blocking returns hard failures.** Canva's pricing page returned HTTP 403. Vendor pricing pages are the most likely class to block automated access, which is exactly why pricing claims need the "verify current pricing" treatment rather than cached numbers.
3. **Translation and localisation layers distort text.** The Google Fonts developer page arrived through a machine-translation layer; the substance (open-source licences, free commercial use) survived, but any wording is unsafe to quote. When a fetched page arrives translated, record facts only, never phrasing.
4. **Citation formatting noise.** The repository scan found URLs carrying trailing punctuation (commas, closing brackets) from Markdown rendering, and the same source cited with slightly different URL forms in different files. Neither affects validity, but both break mechanical re-verification: when adding sources, copy URLs cleanly, and prefer one canonical URL form per source across the repository.
5. **Timeouts are transient more often than not — retry once.** Two pages timed out at 60 seconds this project: the MIT do/don't page succeeded on immediate retry and became the case-studies file's best evidence base, while an Olympic design-archive page did not (recorded in 4.9 as unfetched). A timeout is evidence of slow serving, not proof a source is unreadable; a single retry is cheap and can convert a "missing" source into an `[accessed]` one. Record which outcome occurred, because "timed out twice" is genuine evidence for classifying a source as unreachable by simple tooling.

None of these is exotic; all four will recur. The practical consequence is that "fetched" is a stronger claim than it looks — a fetch can succeed and still yield no usable text — so access dates should be recorded alongside *what was actually obtained*, as done in 4.1's notes.

### 5.2 Implications for future additions

Three working policies follow from the observed patterns. First, *consolidate practical conventions*: when several files would each cite a different vendor page for the same convention (bleed sizes, sign letter heights, social image dimensions), write the convention into one repository file citing the best available source, and let the other files link to it — one citation to maintain instead of five, and one place to re-verify. Second, *prefer stable canonical URLs*: cite the root documentation page a vendor promises to keep (a standard's Understanding page, a tool's docs home) rather than deep links into dated release notes, unless the dated version is the point. Third, *record failures, not just successes*: a fetch that failed, was blocked, or returned no body is information the next agent needs (it changes which claims are supportable), so note it where the source is cited — as done for Material 3 and Canva in sections 4.1 and 4.4.

## 6. Canonical works register (by subject)

The repository's `[canonical]` citations, consolidated from the reference-section scan, grouped by the subject where each does its work. All entries are attribution-level only.

| Subject area | Works (author, title, publisher, year where recorded) |
| --- | --- |
| Vision, perception and composition | Rudolf Arnheim, *Art and Visual Perception*, University of California Press, 1954/1974; Arnheim, *The Power of the Center*, University of California Press, 1982 |
| Colour | Josef Albers, *Interaction of Color*, Yale University Press, 1963; Faber Birren, *Color Psychology and Color Theory* — period practitioner literature, treat claims critically |
| Layout and grids | Josef Müller-Brockmann, *Grid Systems in Graphic Design* (niggli); Alan MacEachren, *How Maps Work*, 1995 (extended visual variables for geographic representation) |
| Data visualisation | Edward Tufte, *Envisioning Information* / *The Visual Display of Quantitative Information* (Graphics Press) — titles per the author's own books page (4.2) |
| Branding and identity | Alina Wheeler, *Designing Brand Identity*, Wiley, 5th ed. 2017; Byron Sharp, *Building Distinctive Assets*, Oxford University Press, 2018; David A. Aaker, *Managing Brand Equity*, Free Press, 1991; Al Ries and Jack Trout, *Positioning*, McGraw-Hill, 1981 |
| UX and interaction | Don Norman, *The Design of Everyday Things*, revised ed. 2013; Ben Shneiderman et al., *Designing the User Interface*, Pearson; Dan Saffer, *Microinteractions*, O'Reilly, 2013; Connor and Irizarry, *Discussing Design*, O'Reilly, 2015; Jakob Nielsen's ten usability heuristics (NN/g) |
| Ideation and method | Alex Osborn, *Applied Imagination*, 1953; Bob Eberle, *SCAMPER* (populariser of the acronym) |
| Design systems | Brad Frost, *Atomic Design*, 2016 |
| History and criticism | John Berger, *Ways of Seeing*, BBC/Penguin, 1972; Roland Barthes, "Rhetoric of the Image" (1964), in *Image–Music–Text*; Dieter Rams, *Less and More*, Gestalten, 2015; the Vitsoe pages on Rams (4.2) as open web companions |
| Professional bodies | AIGA brand and identity design resources — professional convention for logo variant sets, clear space and misuse rules |
| Standards and specification bodies | W3C/WAI standards (WCAG, ARIA APG, WAI tutorials) — normative, open access (4.2); Design Tokens Community Group draft format (4.2, draft status); the ISO-style corporate identity manual tradition — the documentation genre itself, cited canonically |

When a new canonical work is added, insert it into the matching row (or a new row) and record where it was first cited, so the register stays a finding aid rather than a second bibliography — the alphabetical detail belongs in [Bibliography](bibliography.md). Rows exist for the *job* a work does in this repository, not for academic taxonomy: a file reaching for a colour-perception argument should find Albers and Arnheim under vision and colour without knowing the library sciences behind the classification.

## 7. Access-date register

Access dates are recorded per citation in each file's References section in the form "accessed 2026-11-24". The dates known from this project's fetching are 2026-11-24 (all six sources in 4.1, four of which were re-fetched in the same-day verification pass noted there). URLs seen only in the repository scan have no access date of their own; their date of record is the date the citing domain file was written, which each domain file states in its own References section. When you re-verify a source, update its access date in the files that cite it rather than silently relying on the old date. For sources with no verifiable date at all (a claim inherited from general knowledge), the honest form in text is "as of this writing" plus a `verify` marker where the fact is volatile.

## 8. What each level allows you to claim

The epistemics, as a rule table for agents:

1. **Fetched this project** → you may state facts as the source states them, with the access date; flag anything volatile (prices, versions, capabilities) for re-verification at use time.
2. **Open access, cited but unfetched** → you may rely on the general content at the level the repository already uses it; fetch before quoting text, numbers or figures.
3. **Public brand manual** → you may state "organisation X requires Y as of DATE"; you may never generalise to "brands must Y".
4. **Publisher description** → claim only existence, scope and positioning; mark evaluative statements as the publisher's own.
5. **Abstract / secondary review** → claim the finding as reported; label the level ("per the abstract", "per NN/g's article"); chase the primary source for load-bearing claims.
6. **Canonical-not-accessed** → attribute ideas at attribution level with `[canonical]`; a quote, page number or statistic attached to a canonical tag is a fabrication by definition.
7. **Unknown provenance** → if a claim in the repository cannot be traced to one of the levels above, treat it as unverified: either verify it now or mark it `verify` in the text.
8. **`verify` markers** → a claim marked `verify` in any file may be planned around but not asserted; before it appears in a deliverable aimed outside the repository, it must be verified or removed.
9. **Quotes** → short attributed quotations only from `[accessed]` sources, only where the wording itself matters, and never from translation layers (4.1's notes) or `[canonical]` entries. Anything longer than a clause should be paraphrased in original language per the repository's brief.

## 9. Guidance for future agents

### 9.1 Re-verifying a source

1. Fetch the URL; if it times out, retry once before classifying the source as unfetchable (5.1, failure mode 5); if it moved, search for the title plus publisher, and record both the old URL (marked moved) and the new one.
2. Confirm the substance still supports the claim made in the repository; if it does not, edit the citing file, not just this index — this index records status, the citing files carry the claims.
3. Update the citation line in the citing file: refresh the access date and switch the tag from `[search-verified]` to `[accessed]` only after you actually read it.
4. Note volatile fields (pricing, version numbers, plan names) in the text as "verify current" rather than copying values that will expire. A useful habit: when you fetch a volatile fact, write the fact *and* its date into the text ("v3.14.0 as of 2026-11-24"), so the next agent can see immediately whether it needs re-checking.
5. Re-verify on a needs basis, not on a schedule: volatile sources (pricing, AI tools, versioned systems) before any use in a deliverable; stable sources (standards, books) only when quoting.

### 9.2 Adding a new source

1. Classify it into one of the levels in section 3 *before* citing it, and choose claims the level supports (section 8).
2. Add it to the citing file's References with author/title/publisher/year where known, the URL, the access date, the tag, and — for anything below full open access — a one-line note of the access limitation (mission §10's required fields: author, title, edition, publisher, year, URL, access date, source type, access limitations).
3. If the source is a new canonical book, cite it by author, title, publisher and year from verifiable bibliographic information (a publisher page or library record you actually saw), and tag `[canonical]` without quotes or page numbers; then add it to the register in section 6.
4. Prefer primary over secondary sources for facts; use secondary sources for professional interpretation and to discover primary sources.
5. If you found nothing usable, say so in the file ("no reliable public source located") rather than filling the gap with a weak citation — an honest gap is repairable; a fabricated source is not.

### 9.3 The no-fabrication rule

Never fabricate a citation to make the repository appear academically rigorous (mission §10). Concretely: never invent a URL, DOI, page number, edition, quote, statistic or date; never convert "I believe this is true" into "Smith (2019) showed"; never reuse a URL you have not seen in your own tool output this session. Where a statement is your synthesis of several sources, say so — write "synthesis of the sources below" or "the repository's own analysis" rather than attributing the synthesis to one author, and label original practical frameworks developed here as syntheses. When in doubt, omit the citation and keep the claim plainly worded, or mark it `verify`.

### 9.4 A worked verification pass

Suppose a domain file claims "WCAG requires 4.5:1 contrast for normal text" citing the Understanding Contrast Minimum page as `[search-verified]`, and your task needs the number. The correct pass: fetch https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html, confirm the 4.5:1 threshold and its scope (normal text, with 3:1 for large text), update the citing file's reference line to `[accessed]` with today's date, and, if you cite the *large text* boundary too, add that page. Total cost is one fetch; the repository's most-load-bearing numbers are worth exactly this. The same pass applied to a `[canonical]` claim ends differently: you fetch the Understanding page for contrast, but for "Arnheim on visual weight" there is usually no fetchable text — the correct action is to keep the attribution vague rather than to substitute an internet summary and silently upgrade it to a primary claim.

### 9.5 Verifying the reference-layer files themselves

The reference files in this directory ([Bibliography](bibliography.md), [Books and textbooks](books-and-textbooks.md), [Academic curricula](academic-curricula.md), [Professional guidelines](professional-guidelines.md), [Case studies](case-studies.md), [Tools and software](tools-and-software.md) and this file) are the heaviest consumers of volatile web facts in the repository, and they age fastest: pricing changes, version numbers advance, brand pages move. A periodic pass over this layer should therefore check, in order of volatility: tool prices and plan limits (most volatile — re-verify before any budget-relevant use), version numbers of design systems and standards (re-verify before citing in a deliverable), brand-manual URLs (move silently), and only then the canonical attributions, which are stable by definition. The same-day re-verification pass recorded in 4.1 is the model: four fetches caught two imprecise figures and one transient failure mode. Re-verification should also read the citing files, not just this index — a corrected figure in 4.1 is useless while the citing file still states the old one (as done for the component counts in [Case studies](case-studies.md)).

### 9.6 Citation record template

New reference entries should carry all the mission §10 fields in a consistent form, so that this index can be regenerated mechanically. A compact template that fits the repository's existing style:

```markdown
- Author/organisation, *Title* (edition), publisher, year — one line on what it supports here. URL [tag, access date YYYY-MM-DD; access limitation if any]
```

For a standard with no personal author, the organisation is the author (W3C/WAI); for a book accessed only as canon, omit URL and state "no public full text verified". The three tag values and their boundaries are defined in section 2; when a source has a *limitation* (abstract-only, bot-blocked, translation layer, partial preview), the limitation goes in the entry — a citation that hides its limitation is misrepresenting its own evidence.

## 10. Related topics

- [Bibliography](bibliography.md) — the same sources organised by subject, with fuller bibliographic detail.
- [Books and textbooks](books-and-textbooks.md) — the canonical print layer and how to work with it.
- [Academic curricula](academic-curricula.md) — university teaching structures; also where syllabus evidence for canonicity belongs.
- [Professional guidelines](professional-guidelines.md) — professional-body guidance and codes the repository relies on.
- [Case studies](case-studies.md) — the applied layer whose evidence bases depend on this index.
- [Tools and software](tools-and-software.md) — the tool file with the strictest verify-current-pricing discipline.
- [Design quality framework](../evaluation/design-quality-framework.md) — how source-backed claims feed evaluation work.

## References

- Mission document, §10 "Citations and source management" — the requirements this file implements (uploaded mission file, not a public URL).
- BRIEF for knowledge-base authors (`/home/z/my-project/scripts/kb/BRIEF.md`) — the provenance-tag definitions in section 2 are normative for the whole repository.
- All inventories in section 4 and the pattern data in section 5 were compiled by scanning the References sections of the repository's 81 substantive domain files during this project, plus the direct fetches listed in 4.1 [accessed 2026-11-24]. Canonical entries in section 6 reproduce attributions recorded in those reference sections.
