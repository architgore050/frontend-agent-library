# Information hierarchy

## 1. What is it?

Information hierarchy is the deliberate ordering of content so that a reader's attention meets the material in the order of its importance and logic. Where [Typographic hierarchy](../typography/typographic-hierarchy.md) implements ordering through type scale, weight and style, this file covers the structural layer *beyond typography*: which information comes first, what is grouped with what, what is revealed progressively, how many levels of detail are carried simultaneously, and how redundancy and emphasis are used to make the order legible to a scanning reader.

Hierarchy is usually described as a property of the artefact, but it is better described as a *contract with the reader*: the design promises that the first thing you see is the most important thing, the second thing is the context for it, and anything further down can be found when needed. When the contract is kept, readers can scan — that is, extract the document's skeleton from headings, leads and emphasis alone. When the contract is broken, every reader pays full attention to everything, or abandons the page.

The mechanisms available are four: **ordering** (importance and sequence), **grouping** (what belongs together), **layering** (how many levels are available at once), and **emphasis** (including deliberate redundancy). This file covers all four, plus progressive disclosure as the interactive layering strategy.

## 2. Why does it matter?

Attention is the scarcest resource in any design. Eye-tracking research on scanning behaviour (F-pattern scanning in Jakob Nielsen's studies [canonical]) shows that readers of dense pages read few full paragraphs: they sample headings, first lines and emphasised elements. If those sampled elements are chosen by the layout rather than by importance, the reader's impression of the content is an accident. Hierarchy is therefore the difference between a reader who gets the argument from a ten-second scan and one who gets a random sample.

Hierarchy also carries meaning directly, not just attention. Grouping asserts "these belong together"; sequencing asserts "this follows from that"; layering asserts "this is the detail level of that". These assertions are content: an annual report that groups all risk disclosures inconsistently is making a (probably unintended) claim about how risks relate. An agent that treats hierarchy as decoration rather than assertion will produce layouts that lie structurally.

Finally, hierarchy is the shared backbone of every other discipline in this library: editorial pages, dashboards, brand kits, posters and UI screens are all information hierarchies with different mechanics. Getting the structural layer right makes every downstream styling decision easier, because styling then *encodes* an order that already exists rather than inventing one.

## 3. Core principles

Synthesis of the sources in section 11:

1. **Order by importance, then by logic.** The default order is: the single most important thing first (headline, hero figure, verdict), then the organising context (what this is, who it is for), then the supporting structure, then detail and exceptions. Where logic demands a different order (a recipe lists ingredients before the method for good reasons), the *importance* order reasserts itself in emphasis instead.
2. **One primary element per view.** A view — a page, a screen, a slide, a poster panel — should have one element that wins the first fixation. Two equal competitors split attention and both lose; the viewer scans without an entry point. This is the composition problem too (see [Composition](../foundations/composition.md)), but its informational cause is usually undecided importance.
3. **Group by the reader's question, not the author's convenience.** The grouping that matters is the one that answers "if I read this, do I need that next?". Grouping by internal project history or by source system is the most common structural lie in reports and dashboards.
4. **Limit levels to what the reader can hold.** Three to four levels of simultaneous detail (headline → lead → section → detail) is the conventional ceiling for linear documents; more levels force the reader to track nesting mentally, which fails under scanning. Progressive disclosure (section 4.3) replaces deeper nesting in interactive contexts.
5. **Make levels distinguishable by more than one cue.** Level differences should be visible in at least two properties (size + position, or spacing + colour, or format + wording) so the order survives inattention, grayscale, translation and responsive reflow — the redundancy principle of section 4.5.
6. **Decide emphasis deliberately; everything else is hierarchy by accident.** Every bolded number, boxed callout and enlarged heading claims attention. An artefact with many competing emphases has none.

## 4. How it works

Two reading models underpin every mechanism below. The **linear reader** receives each element in order and needs sequence logic; the **scanning reader** samples the page — headings, leads, emphasised items — and needs the skeleton to stand alone. Real audiences are mixed, and the same individual shifts modes mid-document: scan first, read deeper only where interested. Hierarchy design is therefore the design of *two simultaneous paths* through the same content: a full path and a skeleton path, both coherent. Every mechanism in this section either orders the full path (ordering, grouping), builds the skeleton (layering, progressive disclosure) or protects the skeleton under degraded conditions (redundancy, emphasis discipline).

### 4.1 Ordering: importance and sequence

Two ordering logics exist, and mature artefacts combine them:

- **Importance (top-down):** the classic news structure — conclusion first, evidence after. Headline → lead paragraph → supporting sections → detail/appendix. This is the correct default for business reports, dashboards, event communications and most web pages, because readers may stop at any moment and must not stop before the point.
- **Sequence (process):** chronological or step order — tutorials, recipes, forms, instructions. Here the order is fixed by the task, so importance is expressed by *emphasis* (what the step risks if skipped) rather than by position.

The standard failure is a hybrid that serves neither: a report that opens with methodology (sequence logic) before the finding (importance logic) makes the reader work for the verdict. The correction is a structural pattern borrowed from journalism and consulting: **BLUF / pyramid structure** — bottom line up front, then the supporting argument in descending order of importance, with evidence and method at the end. Method sections belong in an appendix unless the method *is* the message.

### 4.2 Grouping: proximity, boundaries and wording

Grouping is implemented with the Gestalt mechanisms (proximity, similarity, enclosure — see [Gestalt and perception](../foundations/gestalt-and-perception.md)) plus an often-forgotten fourth: **wording**. Headings and captions assert group identity, and vague assertions ("Other", "Details", "Info") undermine otherwise sound visual grouping.

Practical mechanics, with conventional starting values:

| Mechanism | What it asserts | Working rule of thumb |
| --- | --- | --- |
| Proximity | Belonging | Space *within* a group clearly smaller than space between groups — a ratio near 1:2 is a conventional minimum; the gap, not the border, does most of the work |
| Similarity | Category membership | Same visual treatment for same-kind items (all event names styled alike) |
| Enclosure / rules | Explicit grouping | Boxes and rules assert strongly; use when proximity alone must be reinforced, and never nest enclosures more than two deep |
| Alignment | Shared structure | Shared left edges declare "these are siblings" more reliably than any decoration |
| Headings / captions | Group identity | Name the group with the reader's vocabulary, not the data model's ("Getting there", not "Logistics module") |

Sequence matters inside grouping too: items within a group should be ordered by the reader's logic (size, time, priority) — a "by importance" group with alphabetically random items reads as an unordered pile and quietly signals that no ranking exists.

#### Grouping failures and how they read

Grouping errors are structural lies, and readers feel them even when they cannot name them. The recurring ones:

- **Grouping by internal structure** (source system, author, project phase): the reader's questions do not map onto the groups, so nothing is where it is looked for. Regroup by reader question; keep internal taxonomy in the detail layer.
- **Grouping by size**: the biggest items clustered together, the rest in an unsorted "other". This asserts a ranking that usually does not exist. Sort the "other" by the same logic as the main group, or state why it is separate.
- **Enclosure without proximity**: boxes drawn around related items but spaced apart, or unrelated items sitting close together. Readers trust spacing over borders, so the border is read as noise.
- **Two logics mixed in one level**: some sections grouped by topic, others by audience, others by medium. The mixed taxonomy is invisible in the document tree and obvious to every reader. Pick one logic per level; allow the second logic only one level deeper.
- **"Other" as a group**: a catch-all that grows every revision. Treat its growth as a signal that a real group is waiting to be named.

### 4.3 Progressive disclosure

Progressive disclosure is the strategy of showing the level the reader needs now and revealing deeper levels on demand. In interactive contexts it is implemented by accordions, tabs, "read more" links, summaries/details elements, hover panels and step sequences; in print it is implemented by abstracts, sidebars, footnotes, appendices and "continued" structures.

The mechanics that make it work:

- **Reveal signals must be honest.** A collapsed section must promise recognisably what it contains ("Venue map and transport", not "More"). Readers pay a real cost for each click — a doubt tax — so the label is part of the hierarchy, not a UI detail.
- **The summary layer must stand alone.** If a page collapses most of its content, a reader who expands nothing must still receive the argument. Write summaries as complete statements, not as fragments that beg expansion.
- **Depth budget: two levels of disclosure.** Content beyond two click-depths is effectively hidden (readers rarely retrieve it). For genuinely deep material, restructure into separate pages with navigation (see [Information architecture](../ui-ux/information-architecture.md)) rather than nesting disclosure inside disclosure.
- **Default states are hierarchy decisions.** What is open, closed or partially open *is* the ordering. Default-closed everything ("clean design") often means the reader sees only headings — a page with no body. The test in section 9 catches this.

A minimal accessible disclosure uses the native element pair, which carries the accessibility contract for free:

```html
<details>
  <summary>Getting to the venue</summary>
  <p>Tram lines 4 and 11 stop at Riverside Gate, a five-minute walk from the main entrance. Parking is available in the East Deck (limited, pre-book only).</p>
</details>
```

### 4.4 Layering information levels

The layered-document model gives every substantial artefact three simultaneous levels, each answering a different reading mode:

| Level | Answers | Typical carriers | Reading mode |
| --- | --- | --- | --- |
| Headline / takeaway | "What is the point?" | Title, hero figure, lead sentence, verdict box | Scan |
| Summary / structure | "What is here and why should I care?" | Lead paragraphs, section headings, contents, key-stat strip | Skim |
| Detail | "What exactly?" | Body text, tables, specifications, footnotes, appendices | Read |

Annotation levels (the names, numbers, footnotes and sources that attach to content) follow the same logic, and are worth separating into their own layer scheme:

| Annotation level | Attaches to | Carries | Placement rule |
| --- | --- | --- | --- |
| Point annotation | A specific element (figure, term, mark) | The value or definition needed at the moment of reading | Beside the element it explains, never on another page |
| Local note | A section, table or chart | Method, caveats, units, retrieval date | Footer of the section it qualifies |
| Global apparatus | The whole artefact | Sources, abbreviations, contact points, version | Appendix or colophon — referenced, not repeated |

The discipline is that annotation *descends* in prominence: point annotations are the most visible, the global apparatus the quietest. Two classic failures are the reverse — a numbered apparatus of endnotes that forces the reader to hunt for the one note that matters now, and a methods paragraph promoted to the opening because nobody wanted to demote it (see section 4.1 on the verdict-first order).

The discipline is that **each level must be complete on its own terms**: the headline is a finding (not a topic label); the skim path — headings and leads read alone — tells a coherent story; the detail layer is precise enough to be quoted. This is the same principle as chart layering in [Data visualisation](data-visualisation.md) (takeaway title → marks → annotation) applied to documents. The standard test is the "skim transcript": read only titles and first sentences aloud; if the transcript is incoherent or repetitive, the layering has failed regardless of how elegant the typography is.

Annotation levels (the names, numbers, footnotes and sources that attach to content) follow the same logic: annotate *at the point of need* (the figure the sentence relies on sits beside it), defer *shared context* (method notes, sources) to the level below, and never let annotation outrank its parent content visually — a source note set in larger or hotter type than the finding it supports has inverted the order.

#### A level-style sheet

Writing the levels down once, as explicit styles, is what makes hierarchy systematic across an artefact — the document-level equivalent of Tschichold's Penguin rules. A typical sheet for a report or long page:

| Level | Style definition | Usage rule |
| --- | --- | --- |
| H1 / headline | Largest scale, heaviest weight, most whitespace above and below | One per artefact; carries the finding, not the topic |
| H2 / section | Second scale, medium weight, more space above than below | One logic of grouping per section level |
| H3 / subsection | Same scale as body but bold, tight to its text | Only under an H2; never skips a level |
| Lead / summary | Body size, regular weight, complete sentences | Every section opens with one; the skim path depends on it |
| Callout | Box or tint, body size, bold lead-in | One per view maximum; the strongest emphasis tool |
| Caption / annotation | Smallest scale, quiet colour | Subordinate to everything it touches |
| Fine print / apparatus | Smallest, grey, grouped at the bottom | Sources, methods, versions — referenced, not repeated |

Two rules make the sheet work: every level difference is visible in at least two cues (scale + weight, or scale + space), and the sheet travels — components, slides and email templates inherit it rather than reinventing it. When a new artefact seems to need a new level, first try to express it with the existing ones; most "missing levels" are actually missing emphasis decisions.

### 4.5 Redundancy and emphasis

Redundancy is the deliberate duplication of a signal in more than one channel so the order survives degraded conditions — inattention, grayscale, small screens, translation, or a reader who starts mid-document. Redundant encoding is standard in charts (colour + position, see [Data visualisation](data-visualisation.md)) and equally standard in layout:

- State the importance in **position** (top, left-edge reading start) and again in **format** (size, weight) and, where sensible, in **wording** ("Key change", "Summary", "Action required").
- Repeat the headline finding in the summary level; repeat the summary in the conclusion. In reports this feels old-fashioned and works; in web copy the equivalent is the front-loaded first paragraph plus the takeaway subheading.
- In responsive and multilingual contexts, redundancy is survival: colour-only or position-only emphasis is destroyed by reflow and by right-to-left or vertical scripts.

Emphasis is redundancy's spend limit. The working conventions (labelled as conventional starting points, since every brand system may override them):

- Emphasise no more than one element per paragraph and roughly one per screen or spread.
- Bold beats italics for attention; italics suit titles and quiet distinction; colour is the loudest and the first to fail (see [Accessible colour](../accessibility/accessible-colour.md)).
- Boxes, rules and tinted callouts cost more attention than type emphasis — reserve them for the few elements that must interrupt scanning.
- When everything is emphasised, the reader's trust in emphasis collapses; audit any artefact where more than about a tenth of the text is highlighted.

The emphasis toolbox, ordered roughly from quietest to loudest — pick the quietest tool that does the job, because every step up steals attention from the surrounding content:

| Tool | Attention cost | Right for | Failure mode when overused |
| --- | --- | --- | --- |
| Position (first slot, top placement) | None visible | The element every reader must meet | Nothing — position is free attention |
| Whitespace around an element | None visible | The hero figure, the primary chart | None — but it spends canvas, so budget it |
| Italic / different weight | Low | Terms, citations, quiet distinction | Invisible; reader misses the distinction |
| Bold type | Moderate | Key numbers, critical steps, warnings in prose | Diluted emphasis everywhere |
| Colour (brand accent) | High | Calls to action, the subject series in a chart | Accent inflation; fails for colour-blind readers |
| Larger size / display scale | High | Headlines, hero figures | Competing primaries |
| Callout box / rule / tint | Highest | The one interruption per view | The page becomes a set of competing posters |

### 4.6 Hierarchy under responsive and multilingual conditions

Reflow destroys single-cue hierarchies, so responsive design re-tests every hierarchy decision. Practical rules: carry the order into the DOM (or the print grid) rather than into absolute positions, so reflow preserves the ranking; keep level differences multi-cue (section 3, principle 5) because a size difference that survives desktop may be compressed by a narrow viewport; convert side-by-side hierarchies (callout beside text) into stacked ones with an explicit signal (rule, tint, heading) rather than relying on adjacency alone. In multilingual artefacts, headings that rely on length ("Support" → "Unterstützung der Teilnehmer") can break a single-line layout, and scripts that set vertically or right-to-left reassert the reading start position — so never encode "first" purely as top-left. Translation also scrambles emphasis conventions (bold carrying a different weight in another typographic tradition), which is one more reason the redundancy principle — stating importance in wording as well as styling — is non-negotiable for international work.

## 5. Practical application

A hierarchy-first workflow for any document, page or dashboard:

1. **Write the importance list before laying out anything.** One column, ranked: the ten most important things this artefact must deliver. This list, not the content inventory, drives the layout.
2. **Choose the ordering logic per artefact** (importance vs sequence, section 4.1) and write it down; flag where the two conflict.
3. **Draft the skeleton in prose first:** the headline, the section headings, the lead sentences. If the skeleton does not read as a coherent argument, no layout can fix it.
4. **Assign each skeleton element a level** (headline/summary/detail) and a group. Cut content that fits no group — it is either decoration or an omitted decision.
5. **Set the emphasis budget** before styling: which single element wins each view, and which two or three earn strong emphasis.
6. **Style the levels with at least two cues each** (see [Typographic hierarchy](../typography/typographic-hierarchy.md) for the type mechanics; [Spacing and proportion](../layout/spacing-and-proportion.md) for the spacing system).
7. **Run the tests in section 9** — the skim transcript and the ten-second view test — and fix the structure, not the styling, when they fail.

For artefacts that already exist — inherited reports, live dashboards, a brand's accumulated collateral — the same method runs in reverse as an audit: rank the artefact's actual firsts (what wins each view, what the scan path delivers), compare against a freshly written importance list, and log every place the two disagree. Those disagreements are the work list, ordered by how early they derail the reader. Audits routinely find the same three defects: a method section occupying the opening, groups named in internal vocabulary, and emphasis spent on decoration rather than the finding. Fixing the order is cheap at audit time and expensive at launch time, which is the practical argument for the skeleton-first workflow above.

## 6. Decision framework

1. **Who stops reading early?** If likely (most web and report audiences), importance ordering is mandatory: verdict first.
2. **Is the artefact a tool or a story?** Tools (forms, dashboards, specs) use task sequence with emphasis marking risk; stories (reports, campaigns) use importance ordering.
3. **How many levels does the medium allow?** Print and single pages: three simultaneous levels. Interactive: three levels plus up to two disclosure depths; beyond that, restructure into pages.
4. **What does each group claim?** Test groupings against the reader's questions; rename vague groups.
5. **Where is redundancy needed?** Degraded-context risks (print grayscale, reflow, translation, mid-document entry) each justify a redundant signal.
6. **What is the emphasis budget, and is it respected?** Count emphasised elements per view; reduce until one wins.

## 7. Examples

A worked skeleton shows the method at its smallest scale. Take an event-cancellation notice. The importance list reads: (1) the event is cancelled, (2) what ticketholders must do, (3) why, (4) who to contact, (5) refund mechanics. The skeleton becomes: headline "The 2026 Riverside Festival is cancelled" (level 1, first slot, largest scale); lead sentence "All ticketholders will be contacted by email today — here is what you need to do" (level 2, naming the audience); an action box "Check your inbox; refunds process automatically within ten working days" (level 2, callout — the one strong emphasis on the page); the reason and the background (level 3, body text); contact details and refund conditions in disclosure elements (level 3, collapsed). Notice the decisions the skeleton forces before any styling: verdict before reason, action as the single callout, mechanics demoted to disclosure. Styling then encodes a structure that already exists.

- **Event landing page.** Headline level: the event name and the one reason to attend, as the hero. Summary level: date, venue, programme highlights in a scannable strip. Detail level: speaker biographies, schedule table, FAQ in disclosure elements whose labels are written as reader questions. The order survives: a visitor who reads nothing but the hero and the strip still knows what, when, where and why.
- **Annual report.** Verdict first (chair's summary with the three key figures); skim path: section headings plus lead sentences telling the year's story; detail level: accounts, methodology and risk register. Redundancy: key figures repeated in the summary and again as large annotated numbers beside the relevant sections — deliberate, because report readers enter mid-document.
- **Dashboard.** Each view has one primary visual (the metric the screen exists for), a compact context row (comparatives, trend arrows), and detail available on interaction. Grouping follows the reader's questions (region → channel → campaign), never the data warehouse's table structure — the classic grouping failure.
- **Brand guidelines document.** Headline level: the rule itself ("one typeface family, three weights"). Summary: correct/incorrect examples. Detail: rationale and edge cases. The layers let a supplier comply in ten seconds and audit in ten minutes (see [Brand guidelines](../branding/brand-guidelines.md)).
- **Press release.** Importance ordering in its purest commercial form: the verdict and the quotation in the opening paragraph, the supporting figures next, boilerplate and notes last — a structure designed on the assumption that a journalist will cut from the bottom, because that is how the medium is consumed.

## 8. Common mistakes

| Mistake | Why it fails | Correction |
| --- | --- | --- |
| Method or history before the verdict | Readers stop before the point; the scan path yields no finding | Pyramid structure: bottom line up front, method to the end |
| Two competing heroes per view | No entry point; attention splits and both elements weaken | Rank and demote; one primary per view |
| Grouping by internal structure (source system, project history) | The reader's questions do not map; retrieval fails | Regroup by reader questions; rename in reader vocabulary |
| Vague disclosure labels ("More", "Info", "Other") | The reveal signal hides the hierarchy; doubt tax on every click | Label with the content ("Venue map and transport") |
| Everything emphasised | No emphasis remains; trust in signals collapses | Enforce the emphasis budget; demote or delete |
| Levels distinguished by one cue only (size alone) | Hierarchy fails under grayscale, reflow or inattention | Two cues minimum per level difference |
| Collapsed-by-default content with no standalone summary | The "clean" page is an index; readers who never expand get nothing | Write summaries as complete statements; open the primary layer |
| Annotation outranking content | Footnotes and sources visually beat the finding they support | Keep annotation quieter and subordinate; move shared notes down a level |
| Alphabetical or source-order lists inside importance groups | Implies no ranking exists | Order by the reader's logic; sort deliberately |
| Hierarchy rebuilt per page without a system | Levels drift across an artefact; readers re-learn each page | Define level styles once (see [Typographic hierarchy](../typography/typographic-hierarchy.md)) and reuse |
| Skeleton approved only after styling | Structure errors found late cost the most | Approve the prose skeleton (headings + leads) before design |
| Position-only "first" signal in responsive or translated layouts | Reflow, RTL scripts and translation scramble the order | State importance in wording and format, not position alone (section 4.6) |

## 9. Evaluation checklist

- The importance list exists and the layout visibly implements it.
- Every view (page, screen, slide, panel) has exactly one primary element.
- The skim transcript — headings plus lead sentences read alone — is coherent and non-repetitive.
- Each level (headline, summary, detail) is complete on its own terms.
- Groups answer reader questions, are named in reader vocabulary, and items are ordered by the reader's logic.
- Disclosure elements are honest, two levels deep maximum, with summaries that stand alone.
- Every level difference is signalled by at least two visual cues, and the hierarchy survives grayscale and reflow.
- The emphasis budget (about one strong emphasis per view) is respected.
- Annotation is subordinate to the content it supports.

## 10. Related topics

- [Typographic hierarchy](../typography/typographic-hierarchy.md) — the type-scale mechanics that signal the levels defined here.
- [Data visualisation](data-visualisation.md) — layering applied to charts; annotation levels in graphs.
- [Diagrams and infographics](diagrams-and-infographics.md) — hierarchy inside narrative graphics.
- [Gestalt and perception](../foundations/gestalt-and-perception.md) — the perceptual basis of grouping.
- [Composition](../foundations/composition.md) — the spatial mechanics of the primary element.
- [Spacing and proportion](../layout/spacing-and-proportion.md) — proximity ratios as a system.
- [Information architecture](../ui-ux/information-architecture.md) — hierarchy across a whole site or product.
- [Editorial design](../typography/editorial-design.md) — layered documents in long-form publishing.
- [Brand guidelines](../branding/brand-guidelines.md) — guidelines as a layered, rule-first artefact.
- [Presentations](../applications/presentations.md) — one primary element per slide.

## 11. References

- Jakob Nielsen / Nielsen Norman Group research on web scanning behaviour, including the F-pattern findings, and progressive disclosure: https://www.nngroup.com (articles on F-shaped pattern reading and progressive disclosure) [canonical — the studies and their site are well established; fetch for exact figures before quoting statistics].
- Jakob Nielsen, *Usability Engineering* (1993) — progressive disclosure [canonical].
- Paul Meehl's pyramid principle is popularised in Barbara Minto, *The Pyramid Principle: Logic in Writing and Thinking* (1985) — BLUF/pyramid structure for business documents [canonical].
- Don Norman, *The Design of Everyday Things* (revised ed. 2013) — hierarchy, feedback and information signalling [canonical].
- ISO 9241-210 on human-centred processes informing audience-first ordering [canonical].
- This file is a synthesis of the sources above with this library's own conventions; where a working rule (1:2 proximity, emphasis budgets, two-level disclosure) is stated without a source, treat it as a conventional starting point, not a measured law.
