# Information Architecture

## 1. What is it?

Information architecture (IA) is the structural design of shared information environments: how content is divided into parts, how those parts are grouped and labelled, how they relate to one another, and how people find their way through them. In web and product work, IA answers the questions that precede any screen design — what content exists, into what categories it is organised, by what principle, called what, and reachable by which routes. The classic formulation treats IA as the combination of *organisation schemes*, *labelling systems*, *navigation systems* and *search systems* [canonical — Rosenfeld, Morville & Arango, *Information Architecture for the World Wide Web*].

IA sits between user research and interface design. Research tells you what users need and how they think (their mental models, see [UX fundamentals](ux-fundamentals.md)); IA encodes that understanding as a structure; components such as bars, tabs and breadcrumbs — the province of [UI fundamentals](ui-fundamentals.md) — then render the structure. Note the boundary with the information-design domain: charts, diagrams and other *data visualisation* are treated in [Data visualisation](../information-design/data-visualisation.md); this file concerns the organisation of content, not the visual encoding of data.

## 2. Why does it matter?

Structure is findability. Content that exists but cannot be found is, from the user's perspective, nonexistent; IA failures surface as abandoned searches, duplicated pages, "orphan" content nobody reaches, and support questions that answer themselves once the site is organised. IA also determines scale behaviour: a structure that works for 30 pages collapses at 300 unless it was designed for growth, and retrofitting structure onto an established site is far more expensive than getting it right first.

IA is also where user language meets organisational language. Teams naturally label things by their org chart and internal jargon; users search and expect by their own vocabulary. The labelling and testing methods in this file (card sorting, tree testing) exist precisely to arbitrate that conflict with evidence rather than the loudest internal opinion.

## 3. Core principles

### 3.1 Organisation schemes

There are a small number of fundamental ways to organise content [canonical — Rosenfeld, Morville & Arango]:

| Scheme | Organises by | Example | Risk |
|---|---|---|---|
| Hierarchical (taxonomy) | Category → subcategory → item | Website sections; product categories | Deep or bushy trees; wrong top level poisons everything below |
| Sequential | A fixed order of steps | Checkout, onboarding, courses | Only fits genuinely linear content |
| Faceted | Multiple independent attributes | E-commerce filter by price/size/colour/brand | Needs clean metadata; too many facets overwhelm |
| Alphabetical | Name | Directories, indexes | Only when users know the exact name |
| Chronological | Time | News, activity feeds, archives | Rarely sufficient alone |
| Audience- or task-based | Who the user is / what they want to do | "For students / For staff"; "Buy / Sell" | Audiences overlap; tasks interleave |

Two structural variables dominate usability across all schemes: *depth* (levels) and *breadth* (items per level). The professional convention is to prefer broader, shallower structures — roughly up to seven top-level groups and two to four levels deep as a starting range — because each extra level compounds navigation cost (conventional starting point; test with tree testing below rather than obeying a fixed number). Hierarchies should also be *polyhierarchical only deliberately*: allowing one item under two parents is occasionally right (a recipe under both "Vegan" and "Desserts"), but every ambiguity multiplies maintenance and user confusion.

### 3.2 Labelling

A label is the word that stands for a whole category or page — and the entire findability of that content rides on it. Good labels share three properties: they use the *user's* vocabulary (validated by research, not invented internally); they are *distinct* (no two labels that users cannot reliably tell apart, such as "Resources" and "Information"); and they are *consistent* in grammatical form (all nouns, or all verbs) and scope across the site. Convention beats cleverness: users understand "Contact", "Pricing" and "Search" instantly, and a creatively vague label ("Solutions") forces every visitor to interpret. Ambiguity is the enemy — a label that means two things or half a thing will send half its users down the wrong path.

### 3.3 Navigation structures

Navigation is the interactive expression of the IA. The recurring structural patterns:

- **Hierarchies** (main navigation mirrors the taxonomy): the default for content sites; every page should be reachable in the number of clicks its importance justifies.
- **Hubs and spokes** (hub-and-spoke): central landing pages (hubs) radiating to detail pages (spokes); suits galleries, product detail flows, campaigns; weak where users need to move *between* spokes.
- **Faceted navigation**: filter panels over a result set; the IA is carried by metadata rather than fixed pages; demands clean, complete attributes per item.
- **Linear/wizard flows**: for processes with mandatory order; navigation reduces to next/back with a visible position indicator.
- **Search-first**: for very large or opaque corpora, search becomes the primary route and the taxonomy serves search results.

Structural pattern and component are separate decisions: a hierarchy can be rendered as a sidebar, a top bar with dropdowns, or a mega-menu (component guidance in [UI fundamentals](ui-fundamentals.md)). Two structural invariants are non-negotiable regardless of pattern: the user can always tell where they are (highlighted current section, breadcrumbs for deep trees), and can always get back one level and to the root.

### 3.4 Findability

Beyond the navigation, IA determines whether content is *findable*: reachable, guessable and searchable. Practical requirements: every page has a descriptive `<title>` and heading; URL, breadcrumb and navigation label agree (section 5.3); search respects synonyms and the users' vocabulary; and no content is a dead end — every page offers the next logical step. Rosenfeld and Morville's formulation remains the standard mental model: users move through a space of organisation systems, labelling systems, navigation systems and search systems simultaneously, and all four must agree [canonical].

Two tiers of navigation carry almost every site: **global** navigation (the product-wide areas, persistent across the site) and **local** navigation (the sections and siblings within one area). Confusing the tiers is a classic IA defect — a local tool promoted into the global bar makes every page carry a permanent menu of choices only relevant in one corner. Footer navigation is the conventional home of the third tier: content everyone expects to find but nobody needs in the main bar (legal, careers, contact, sitemap).

### 3.5 Search as an IA system

Search is not a bolt-on; it is the fourth system alongside organisation, labelling and navigation [canonical]. Treating it as IA means deciding: the *scope* (what content is indexed — pages only, or documents, products, help articles?), the *vocabulary* (synonyms and user terms mapped to internal terms — "refund" finding "returns policy"), the *result presentation* (grouped by content type? best-guess first?), and the *zero-results design* (suggestions, popular pages, contact route — never a blank page). Search logs are also an IA instrument: queries with zero or abandoned results are findability defects in query language, and they feed straight into the labelling and structure decisions of sections 5.1–5.2.

## 4. How it works

IA is developed iteratively between research and interface design:

1. **Content inventory** — list everything that must exist (pages, documents, functions), with attributes (audience, topic, format, freshness). At scale this becomes a content model: entity types and their relations.
2. **Grouping** — cluster the inventory by user-meaningful principles. This is done *with users* through card sorting, not only by the team.
3. **Structure** — choose the primary scheme (3.1), set depth/breadth, resolve polyhierarchy.
4. **Labelling** — draft labels from the users' own words surfaced by the sort.
5. **Validation** — tree test the draft structure before building; test task completion on the built site afterwards.
6. **Documentation** — a site map (the full tree as a diagram or outline) and navigation spec, which become the contract for designers and developers.

The loop matters because IA hypotheses fail regularly: the team's first grouping is usually closer to the org chart than to user mental models, and only user evidence — not internal debate — settles it.

## 5. Practical application

### 5.1 Card sorting

Card sorting uncovers users' mental models of content groupings: participants organise a deck of content cards into groups they name themselves. Variants: **open** (participants create and name groups — reveals the model itself), **closed** (participants sort into your predefined categories — tests your labels) and **hybrid** (your categories plus the option to add new ones). Run with 15–30 participants online or in person [search-verified: NN/g describes card sorting as the method for how people categorise content, https://www.nngroup.com/articles/card-sorting-tree-testing-differences]. Read the output for: high-agreement clusters (safe categories), scattered cards (ambiguous content — often needs splitting or rewriting), label wordings that recur across participants (candidate labels), and similarity matrices that visualise which items belong together in users' minds. Card sorting answers *how users group*; it does not by itself validate whether the resulting navigation works — that is tree testing's job.

### 5.2 Tree testing

Tree testing (reverse card sorting) evaluates a draft or existing hierarchy in isolation: participants are given tasks ("find the refund policy") and navigate a text-only tree by clicking categories, without any visual design. Output metrics: success rate per task, directness (first-click-to-success vs wandering), and time [search-verified: https://www.nngroup.com/articles/tree-testing]. Tree testing is cheap and fast because it strips away everything but the structure, so failures are unambiguously IA failures; it is the standard pre-build validation for a new sitemap and the diagnostic for a live site whose users report "can't find things". The two methods pair deliberately: card sort to *build* the tree, tree test to *verify* it; iterate the labels and groupings that produce failures, and re-test.

### 5.3 URL structure

URLs are part of the IA: users read them, share them, and use them to infer position. Working conventions (engineering and SEO practice — treat as professional convention, not law): mirror the hierarchy but keep paths shallow and human-readable (`/products/chairs/` rather than `/content/item?id=8812`); use hyphen-separated lowercase words; keep a single canonical form per page (avoid `/about` and `/about-us/` both resolving with equal standing); never let restructuring break URLs without redirects — permanent (301) redirects from old to new preserve both users and search standing; and keep the URL stable even when the page's position in the nav changes, since external links will not move. Breadcrumbs should agree with the URL path where both exist; disagreement between the two visible hierarchies is a classic IA bug.

### 5.4 Site maps

A site map is the documented tree: every page or content type, its parent, and its navigation role (top level, footer, search-only). Keep two artefacts: the *logical* sitemap (content model and hierarchy, the IA artefact proper) and the *XML sitemap* (the machine-readable list served to search engines — an engineering deliverable that should be generated from the content system, not drawn by hand). The logical sitemap earns its keep as the review instrument: stakeholders who cannot read wireframes can read a tree, and structural errors (two parents, orphan pages, seven-item-deep chains) are visible in seconds.

### 5.5 Boundary with information design

Keep the two domains distinct: IA organises *pages and content* into navigable structure; information design (charts, diagrams, infographics) organises *data* into perceivable form on a page. They meet where a page presents data — the IA decides where that page lives and what it is called; the chart's own visual design belongs to [Data visualisation](../information-design/data-visualisation.md). Confusing the two produces "reorganise the menu" answers to what are actually chart-legibility problems, and vice versa.

### 5.6 Content models and metadata

Beyond the page tree, IA at scale is a content model: the entity types (article, product, event, person), their attributes, and their relations ("article *authored by* person", "product *belongs to* category"). The model matters because facets, filters, related-content and search all run on metadata, not prose: an e-commerce facet over "colour" exists only if every product carries a colour attribute, filled consistently. Model work precedes structure work for large sites: define the entities and required attributes first, and the navigation schemes follow almost mechanically from the attributes users care about. A useful audit question per entity: "if this attribute were empty on half the records, which user-facing feature breaks?"

### 5.7 IA for applications versus websites

The same vocabulary applies, but the centre of gravity differs:

| Aspect | Content website | Application |
|---|---|---|
| Primary object | Pages and documents | Objects and operations (projects, orders, records) |
| Structure | Hierarchy of topics | Task and object model (lists → detail → edit) |
| Navigation | Menus, breadcrumbs | Sidebars, tabs, in-app search, command palettes |
| Labelling risk | Marketing vagueness | Internal jargon leaking to users |
| Validation | Card sort, tree test | Task-based usability tests on flows |

Applications are "IA-heavy" in a quieter way: the structure lives in the object model and the routes between states, and a wrong object model (tasks modelled as ad-hoc lists of unrelated screens) costs far more to fix than any label. URL structure matters differently too — application URLs should encode the object and view (`/projects/17/settings`) so states remain shareable and restorable.

### 5.8 Content audit

An audit is the systematic review of existing content before restructuring: inventory every item (URL, title, type, owner, analytics), then judge each against usefulness, accuracy, freshness and overlap. The output is a disposition per item — keep, rewrite, merge, retire — which shrinks the IA problem to its real size. Audits regularly reveal that a third of a site's content attracts no traffic and overlaps another page; carrying it into the new structure multiplies the migration cost and dilutes the tree. For agent-driven projects, the audit is the step that prevents "reorganising" content that should simply be deleted.

### 5.9 The IA documentation pack

The working deliverables that keep IA decisions durable: the **content model** (entities, attributes, relations), the **site map** (the tree, with navigation roles marked), the **label glossary** (every label and its scope, so future pages use the same words), and the **decision log** (why "Billing" holds refunds; which polyhierarchies are deliberate). Documentation is what lets a team extend the structure a year later without relitigating it — the pack is the institution's memory of its own IA reasoning.

## 6. Decision framework

1. **What is the primary organising principle?** Pick the dominant scheme from 3.1 by asking: what attribute do users bring to the task — a known name (alphabetical), a known category (hierarchy), known attributes (facets), or nothing (search-first)?
2. **How deep must it go?** Start shallow and broad; add a level only when a level would hold a disciplined single topic.
3. **Whose vocabulary?** Every label from user evidence (card sort, search logs, support tickets); internal terms are candidates, not defaults.
4. **Does every item have exactly one home?** Resolve polyhierarchy deliberately, with cross-links rather than duplicate pages.
5. **What happens at zero?** Empty categories, no search results, no content for an audience — the empty states are IA surfaces too (see [UI fundamentals](ui-fundamentals.md)).
6. **Is the structure testable before build?** Tree test the draft; fix failures before pixels.
7. **Does it survive growth?** Simulate next year's content volume; a scheme that only works at today's size is deferred debt.

## 7. Examples

**Card sort rescuing a label.** A university site labels its staff directory "Staff Portal". A card sort shows participants put "find a person's contact details" under "Contact" or "Directory" — never "Portal". Renaming the section "Directory" and moving portal services under "Staff" raises findability without touching visual design: the structure was sound, the label was not.

**Tree testing a migration.** Before rebuilding a support site, a tree test of the draft hierarchy gives "cancel my subscription" a 62% direct success rate, with most failures entering "Billing" when the team had filed it under "Account". Moving the task under "Billing" (users' model of *where money tasks live*) raises direct success; the cost was one afternoon, versus rebuilding after launch.

**Facets beating hierarchy.** A furniture retailer's fixed category "Small sofas" competes with users who think "2-seater, under £400, grey". Faceted navigation over the attributes users actually filter by (seats, price, colour) finds the item in one pass; the fixed category required guessing the team's wording. The IA lesson: when users think in attribute combinations, structure by facets.

**URL and breadcrumb agreement.** `/support/refunds/` carrying the breadcrumb "Support / Refunds" gives a user three mutually reinforcing position signals; a page at `/cms/node/4412` labelled "Refunds" gives none. Same content, different findability — the URL is IA surface.

**A conference site structured end to end.** Card sorting over ~40 content items (sessions, speakers, tickets, venue, sponsors) yields clusters the team drafts into this tree, which then goes straight into a tree test:

```text
Home
├── Programme
│   ├── Schedule (by day)
│   ├── Speakers (faceted by track)
│   └── Workshops
├── Tickets
│   ├── Pricing
│   └── Group bookings
├── Venue & travel
└── About
    ├── Code of conduct
    └── Sponsors
```

The tree test shows "find the student discount" failing (users enter Tickets, not About, where the team had filed eligibility rules) and "find speaker X" succeeding. One move — discount rules under Tickets — and a re-test: the structure ships with evidence behind every label.

**Content model before structure.** A recipe site starts by modelling entities (recipe, ingredient, cuisine, author) with required attributes (cook time, diet tags) before drawing any navigation. The facets users expect — filter by diet, sort by time — fall out of the attributes, and the editorial hierarchy becomes a view over the model rather than a separate universe of pages.

**Search logs as an IA instrument.** A help centre's zero-result queries cluster around "delete account" — a task the site answers in three scattered pages called "Data controls", "Cancellation" and "Privacy". One page, labelled the way users ask ("Delete your account"), replaces all three; the label comes straight from the logs.

## 8. Common mistakes

- **Mirroring the org chart.** Structure by department produces labels users cannot decode and duplicated content where departments overlap.
- **Label by committee without evidence.** Vague,Safe-sounding labels ("Solutions", "Resources") that satisfy stakeholders and strand users. Test them.
- **Inconsistent labels.** "Contact" in the header, "Get in touch" in the footer, "Talk to us" on the page — each re-interpretation costs the user certainty.
- **Deep, narrow trees.** Seven levels of single-item categories turn every retrieval into a click quest; flatten and broaden.
- **Ambiguous polyhierarchy by accident.** Content reachable under two parents *unintentionally* breeds duplicate pages and divergent updates; make multi-parent a deliberate, documented decision.
- **Testing structure only after build.** Tree testing exists to catch structural failure cheaply before design investment; skipping it couples IA errors to redesign costs.
- **Breaking URLs on restructure.** Reorganising without permanent redirects destroys the accumulated findability of every external link to the site.
- **Treating search as the fix.** "We'll just add search" papers over a structure users cannot traverse; search complements structure, it does not replace it.

## 9. Evaluation checklist

- The primary organisation scheme matches how users think about the domain (validated by research, not assumption).
- Every label uses user vocabulary; labels are distinct from each other and consistent in form and scope.
- Depth stays shallow; every important page reachable within the click budget its importance justifies.
- Current location is always visible (nav highlight and, in deep trees, breadcrumbs).
- Every page offers back one level and root; no dead ends.
- URL, breadcrumb and navigation label agree; canonical URL per page; restructures redirect permanently.
- Card sort run before structuring; tree test run before build; both iterated on failure.
- Search respects user vocabulary and synonyms; search results link into the real structure.
- Site map documented and current; orphan and duplicate pages resolved.
- Data-heavy pages distinguished from structural problems — chart issues routed to [Data visualisation](../information-design/data-visualisation.md).

## 10. Related topics

- [UX fundamentals](ux-fundamentals.md) — mental models and research methods that feed IA decisions
- [UI fundamentals](ui-fundamentals.md) — the navigation components (bars, tabs, breadcrumbs) that render structure
- [Responsive design](responsive-design.md) — how structure adapts across devices (e.g. navigation collapse)
- [Data visualisation](../information-design/data-visualisation.md) — charts and diagrams; the data-visualisation counterpart
- [Web typography](../typography/web-typography.md) — legibility of labels and wayfinding text
- [Gestalt and perception](../foundations/gestalt-and-perception.md) — perception of grouped structure on the page
- [Brand architecture](../branding/brand-architecture.md) — multi-brand organisations whose structures constrain site IA

## 11. References

- Louis Rosenfeld, Peter Morville & Jorge Arango, *Information Architecture for the World Wide Web* ("the polar bear book"), 4th edition, O'Reilly, 2015 [canonical] — organisation schemes, labelling, navigation and search systems
- Nielsen Norman Group, "Card Sorting vs. Tree Testing", https://www.nngroup.com/articles/card-sorting-tree-testing-differences [search-verified 2026-11-23]
- Nielsen Norman Group, "Tree Testing: Evaluate Menu Labels and Categories", https://www.nngroup.com/articles/tree-testing [search-verified 2026-11-23]
- Nielsen Norman Group, "Information Architecture: Study Guide", https://www.nngroup.com/articles/ia-study-guide [search-verified 2026-11-23]
- Jakob Nielsen, "10 Usability Heuristics for User Interface Design", https://www.nngroup.com/articles/ten-usability-heuristics/ [accessed 2026-11-23]
- Jakob Nielsen, *Usability Engineering*, Academic Press, 1993 [canonical] — small-sample iterative testing rationale
- Peter Morville, *Ambient Findability*, O'Reilly, 2005 [canonical] — findability as the IA outcome
- Depth/breadth figures in 3.1 are conventional starting points; validate per project with tree testing
- Don Norman, *The Design of Everyday Things* [canonical] — mental models underlying IA organisation schemes
