# Diagrams and infographics

## 1. What is it?

Diagrams and infographics are the *schematic and narrative* branches of information design. A diagram represents relationships that are not inherently numeric — steps, decisions, structures, durations, flows — using conventional marks: boxes, arrows, icons, tracks. An infographic combines data, imagery and editorial text into a narrative artefact that argues a point as it informs. Both differ from a chart, which plots measured values (see [Data visualisation](data-visualisation.md)); a diagram's content is logical or conceptual, and an infographic's content is a story built partly from data and partly from design.

The family covered here: flowcharts and decision trees, process and sequence diagrams, timelines, organisational charts, network/relationship diagrams, spatial layouts (venue and seating plans), and the composed infographic. Each type answers a different reader question — *what happens next, what order, when, who reports to whom, how are things connected, where is it* — and choosing the wrong type is the most common failure in the category.

Historical anchor: Otto Neurath's Isotype (the International System of Typographic Picture Education), developed with Marie Neurath and Gerd Arntz from the mid-1920s Vienna Method of Pictorial Statistics onwards, established that standardised, reduced pictograms — repeated units, consistent style, no decoration beyond meaning — could carry statistics to a non-expert public; Neurath's own book *International Picture Language* (1936) remains the best exposition, and "visual education" was the movement's stated motive [search-verified, Wikipedia and isotyperevisited.org in search results]. Isotype is the ancestor of every modern pictogram system (see [Influential designers](../history/influential-designers.md) on Aicher).

## 2. Why does it matter?

Much of the information people must absorb is not tabular data but *structure*: a sign-up flow, an approval chain, a year's milestones, a venue's layout. Prose handles structure poorly — it forces the reader to assemble the map from sentences — while a diagram puts the map on the page where the eye can traverse it in any direction. For wayfinding, onboarding, training, event programmes and process documentation, the diagram is not decoration; it is the fastest honest representation available.

Infographics matter for a different reason: they are the format in which data meets the general public. A well-built infographic layers the story (headline), the evidence (data marks) and the explanation (annotation), and can carry a complex argument to an audience that would never open the report. A badly built infographic is worse than none — it trains the audience to treat graphics as decoration and distrust the data (see the honesty discipline in [Data visualisation](data-visualisation.md), which infographics inherit wholesale).

For an agent, this category is high-volume in event and marketing work: programmes, schedules, venue maps, registration flows, "how it works" explainers, sponsor structures. The evaluation skills here are applied constantly.

## 3. Core principles

Synthesis of the sources in section 11:

1. **Type follows question.** Choose the diagram type by the reader's question (sequence? decision? hierarchy? geography?), not by which shape looks attractive.
2. **Convention before invention.** Diagram languages work because they are shared — a diamond means decision, an arrow means direction or causation, a box means entity. Invent conventions only when the stock vocabulary cannot carry the meaning, and then teach them explicitly in a key.
3. **One organising idea per diagram.** A diagram answering three questions is three diagrams. Overloaded schematics fail the same way overloaded charts do.
4. **Reduction without distortion.** Isotype's discipline: reduce the visual to its meaning-bearing core, but never alter structure to beautify (Neurath's team's rule was that the picture must not distort the facts [search-verified — the movement's anti-distortion stance]). Schematic maps may bend geography for legibility, but the distortion must be systematic and acknowledged, never accidental.
5. **Icon + label, always.** A pictogram is an assumption until labelled. Isotype itself paired icons with text; unlabelled icons fail the reader who cannot decode the reference, and the label costs little.
6. **The narrative is designed, not appended.** In an infographic, sequence and emphasis *are* the argument: what the reader meets first, second and last is editorial structure and must be authored (see [Information hierarchy](information-hierarchy.md)).

## 4. How it works

### 4.1 Choosing the diagram type

| Reader question | Right type | Conventions | Watch for |
| --- | --- | --- | --- |
| What are the steps, and what happens next? | Flowchart / process diagram | Boxes = steps; diamonds = decisions; arrows = flow direction; one start, explicit ends | Crossing arrows; unlabelled decision branches |
| Which path applies to *me*? | Decision tree | Hierarchical branches, mutually exclusive, collectively exhaustive options at each node | Overlapping conditions; missing "else" branches |
| When do things happen, and what overlaps? | Timeline / Gantt | Ordered track; duration = length; milestones = markers | Timelines pretending to be calendars; crowding |
| Who reports to whom? | Org chart | Top-down tree; one parent per node; depth = seniority | Dual-reporting drawn as two boxes instead of dotted lines |
| How do things connect overall? | Network / relationship diagram | Nodes and edges; layout encodes clustering | Hairball graphs; edge direction lost |
| How much flows between stages? | Flow / Sankey diagram | Width = quantity; stages ordered by process | Decorative widths; missing totals |
| Where is it? | Schematic plan / map | Anchors to real geography; consistent orientation; numbered stops | Unlabelled zones; north-up assumptions in venue plans |
| How does a system work? | Explainer / mechanism diagram | Parts, inputs/outputs, sequence of actions | Mixing abstraction levels (some parts detailed, others vague) |

#### Diagram, prose, or table?

Before committing to a diagram, confirm the diagram is the right container at all — three failures recur when it is not:

| Situation | Right container | Why |
| --- | --- | --- |
| The steps are strictly sequential with no branches and no parallelism | Numbered prose list | A flowchart with one path is a list with decoration |
| The reader must look up one fact among many (dates, contact points) | Table | Diagrams optimise traversal, not lookup |
| The structure has 20+ nodes of one kind | Table or split diagrams | Comprehension collapses past the practical node budget |
| The relations have direction, branches or parallelism | Diagram | This is the diagram's home ground — prose forces readers to assemble the map |
| The argument is the sequencing of evidence (narrative) | Infographic or document | Structure alone does not carry the claim |

The table's logic in one sentence: diagrams earn their cost when the *shape* of the relations is the message; prose and tables win when the content of the steps is the message and the order is trivial.

### 4.2 Diagram conventions

Conventions are the grammar that lets a diagram be read without instruction. The core set, worth following unless there is a specific reason not to:

- **Flow direction is meaningful.** Left-to-right and top-to-bottom are the dominant reading orders; a diagram whose main flow contradicts them needs a very good reason. In right-to-left scripts, mirror the flow deliberately.
- **Shape semantics are shared.** Rectangles for processes, diamonds for decisions, rounded ends for start/terminators, cylinders for stores, arrows for flow, dotted lines for optional or conditional relations. Use one language per diagram — importing shape meanings from two different standards confuses experts more than it delights anyone.
- **Every branch is labelled.** A decision diamond without labelled exits ("Yes/No", the actual conditions) forces the reader to guess the logic. Flowcharts fail in print exactly there.
- **Crossings and reversals cost comprehension.** Route connectors, orthogonal bends and consistent spacing (a grid, as in circuit-diagram discipline) exist to keep the graph traceable. When crossings exceed a handful, restructure: split into two diagrams, or re-layout around the main axis.
- **A key teaches invented conventions.** Any symbol, line style or colour used beyond the standard vocabulary gets a key. Colour in diagrams must obey the encoding rules of [Data visualisation](data-visualisation.md) — categorical for kinds, sequential for magnitude — and survive grayscale.
- **Schematic licence is systematic.** Beck's London Underground map is the canonical case: geography compressed, topology exact. Bend geography only on an explicit, repeatable rule (45°/90° angles, fixed station spacing) and say so if precision matters.

#### Building a decision tree

Decision trees fail in predictable ways, so their construction deserves a fixed procedure. Enumerate the decision points from the reader's first question downward; at each node, write the conditions and check they are **mutually exclusive** (no case satisfies two branches) and **collectively exhaustive** (every case has a branch — including "otherwise" and "not applicable"); order branches by frequency or importance; terminate every branch in an outcome stated in the reader's terms ("You need a visa" not "Refer to policy 4.2"); and test the tree with real cases — at least one per branch, plus the awkward cases that live between branches. Present the tree with the question restated at the top ("Do you need a visa for the festival?"), because a tree detached from its question reads as bureaucracy rather than help. If the tree exceeds roughly a dozen nodes, split it: eligibility in one tree, logistics in another, cross-referenced.

Two types deserve their own conventions because they are the most common in organisational and event work. **Organisational charts:** one node per person or unit, depth representing seniority, direct reports solid, dual-reporting as dotted or secondary connectors rather than duplicated boxes; keep depth to four or five levels before a chart becomes unreadable — at larger scale, publish one top-level chart plus per-department charts. Labels carry role and name, and vacant or merged roles should be visible rather than drawn as if filled, because an org chart is also an accountability document. **Network and relationship diagrams:** nodes sized or coloured by a stated variable and edges labelled when direction or weight matters; when the graph exceeds roughly two dozen nodes, cluster first (by function, region or community) and draw the cluster graph, then the detail graphs — the overview-plus-detail decomposition mirrors the small-multiples logic in [Data visualisation](data-visualisation.md). Hairball networks — hundreds of edges with no clustering — communicate nothing except density.

#### Colour and shape redundancy in diagrams

Diagrams obey the same redundancy discipline as charts. Every distinction that matters should be carried by at least two variables: shape (box vs diamond) plus label, line style (solid vs dotted) plus wording ("optional"), colour plus position. Colour alone must never carry a decision branch, a mandatory step or an exception — grayscale printing and colour-vision deficiency are normal conditions, not edge cases (see [Accessible colour](../accessibility/accessible-colour.md)). A useful audit pass: print the diagram in grayscale and ask whether every distinction the reader must make is still visible.

#### Arrow semantics worth agreeing on

Arrows carry more meaning than any other diagram mark, so their conventions deserve explicit agreement before a diagram is drawn:

- **Solid arrowhead, solid line**: the primary flow — sequence, causation or movement. One meaning per diagram, never two.
- **Open or hollow arrowhead**: generalisation or inheritance ("is a"), mainly in org and classification diagrams — keep it out of process diagrams to avoid confusion.
- **Dashed line**: optional, conditional or informational relation; pair with wording ("if approved").
- **Double-headed arrows**: only for genuine bidirectional relations; overused, they signal indecision about the flow's actual direction.
- **No arrowhead (plain line)**: association without direction — the default in network diagrams whose edges have no flow.
- **Labelled arrows**: any arrow whose meaning is not plain sequence gets words ("approved", "after 30 days", "leads to"). The label is part of the mark, not an annotation.

An audit pass: cover all arrow labels and ask whether the diagram's structure survives; then uncover them and ask whether any arrow now says something the structure contradicts. Both passes should pass.

### 4.3 Timeline and sequence design

Timelines are the most frequently needed diagram in event and marketing work, and the most frequently mangled. The mechanics that matter:

- **One time unit per track.** Mixing days and months on one axis misleads; if the programme needs month-level and day-level detail, use two tracks.
- **Duration must be visible where it matters.** For schedules, a Gantt-style bar (length = duration) beats a dot (milestone) whenever durations vary; dots suit pure milestone histories.
- **Overlap must be structural.** Parallel workstreams need parallel lanes, not interleaved single-track entries.
- **The "now" marker.** In any live or campaign timeline, a marked current position turns the graphic from a list into a status device.
- **Capacity discipline.** Beyond roughly ten to fifteen entries per track, a timeline becomes a table with decoration; move detail into a table and keep the graphic for the shape of the story (see the tables-versus-charts reasoning in [Data visualisation](data-visualisation.md)).

### 4.4 Infographic structure: narrative + data + hierarchy

An infographic is an editorial artefact. Its standard structure has four working parts:

1. **Headline — the argument.** States the finding ("Registration is up 40% and mobile is why"), not the topic ("2026 Registration Report"). Same takeaway-title discipline as charts.
2. **Lead — orientation.** One sentence of scope and source, plus the origin and date of the data. This is also where the infographic earns honesty credentials: unattributed data is the category's most common defect.
3. **Body — a sequenced mix of data marks and diagram types.** Each section answers one question; sections are ordered by the narrative's logic (often importance-first, per [Information hierarchy](information-hierarchy.md)). Data sections follow chart discipline (encoding, axes, colour); schematic sections follow diagram discipline (conventions, labels).
4. **Footer — provenance and next step.** Sources with dates, methodology notes where relevant, credits, and — in marketing use — the call to action. The footer's presence distinguishes an infographic from a poster.

**Avoiding decoration-as-information.** The category's signature failure is imagery that *looks* like content but carries none: an oversized icon whose size encodes nothing, a hand-drawn arrow that implies a relationship the data does not show, a background illustration competing with the numbers. The tests:

- **The deletion test:** remove the element; if no meaning is lost, it is decoration and must either earn meaning (scale, position, colour encoding something) or move to the background frame.
- **The encoding test:** any size, colour or position that a reader could interpret as data must actually encode data — an icon scaled by a non-data quantity (popularity ranked alphabetically) is a lie in the chart sense (see [Data visualisation](data-visualisation.md) section 4.7).
- **The unit test:** repeated icons (one icon = 1,000 people) must be counted and captioned; the Isotype unit-count method only works when the unit is stated and the count is exact.

#### The Isotype unit-count method, worked

Isotype's statistical graphics encode quantity by *repetition of identical units*, not by scaling one icon — because readers cannot judge area, but they can count [search-verified, Isotype literature]. The working procedure: state the unit explicitly ("one figure = 500 attendees"), draw the quantity in whole units (round to the nearest unit and say the rounding), keep every unit identical in size, style and colour (variation must encode a category difference, never decoration), arrange units in rows of a fixed count so magnitudes compare as lengths of rows, and caption the chart with the unit statement. Compare: "attendance grew from 2,400 to 3,700" becomes four rows of five figures against seven rows of five, each row captioned with its year — the growth reads by length, not by squinting at icon areas. The method's power and its limit are the same: it suits round, moderate quantities; fine-grained or fractional data belongs in a proper chart (see [Data visualisation](data-visualisation.md)).

### 4.5 Icon and label pairing

Icons in information graphics follow Isotype's working rules [search-verified, Isotype literature]:

- **Icon + label is the default pair.** The label is not a caption afterthought; it is part of the unit. Unlabelled icons are acceptable only where the icon is a well-learned public standard (wayfinding toilet symbols, transport pictograms — the Aicher lineage).
- **One style family.** Icons in one artefact come from one construction system — same grid, same stroke weight, same corner logic — or the set reads as clip-art collage (see [Iconography](../graphic-design/iconography.md) for building and auditing icon sets).
- **Consistent abstraction level.** Do not mix a filled pictogram, an outline icon and an illustration in one legend row; pick one register and keep it.
- **Silhouette first.** Isotype and Munich 1972 both built recognisability on reduced silhouettes; if the icon cannot be identified at its final size in grayscale, it is too detailed.
- **Cultural check.** Gestures, animals and colours carry different meanings across audiences; verify the pictogram vocabulary against the actual audience rather than assuming universality.

## 5. Practical application

A workflow for any diagram or infographic task:

1. **Write the reader's question** ("how do I register?", "what happens through the year?"). Choose the type from the section 4.1 table; if two questions are competing, plan two graphics.
2. **Collect and verify the content.** For process diagrams: walk the actual process with the person who runs it; the gaps between documented and real flow are where diagrams misinform. For infographics: confirm every number's source and date before design begins — and check that the numbers are *comparable* (same definitions, same periods), because an infographic quoting three differently-defined statistics is a construction of confusion, not of knowledge. Keep a source list as a working file; it becomes the footer's provenance block (see section 4.4) and, in a client context, the audit trail that protects everyone involved.
3. **Draft the structure in words** — boxes and branch labels, or the infographic's section list with the headline argument. Approve this skeleton before styling; structure errors found later cost the most.
4. **Apply conventions.** Flow direction, shape semantics, labels on every branch and node, key for any invention. Build on a grid so spacing and alignment are systematic (see [Grid systems](../layout/grid-systems.md)).
5. **Apply the hierarchy.** One primary element per view; annotation subordinate to content; takeaway headline for infographics (see [Information hierarchy](information-hierarchy.md)).
6. **Audit for decoration-as-information** with the three tests in section 4.4, and audit icons as pairs (section 4.5).
7. **Test at final size and in grayscale,** including the "explain it to me" test: hand it to a colleague for sixty seconds and ask them to narrate it back; the narration reveals which conventions failed.

One further audit pass matters for diagrams that will be displayed physically or projected: the **distance test**. A programme board, poster panel or slide diagram must be legible from its actual reading distance — as a rule of thumb, minimum text sizes grow roughly by a factor of three to four between desk reading and room reading, and route lines must be traceable from across a hall (verify exact sizes against your display conditions rather than trusting any fixed figure). The distance test usually forces the correct structural decision: fewer entries, bigger units, detail deferred to a handout or QR-linked page. That is the right trade — a diagram's job at distance is the shape of the information, not the numbers, which the companion material carries (see [Presentations](../applications/presentations.md) and [Posters](../applications/posters.md)).

For web delivery, structure an infographic as real content, not one baked image, whenever it must be findable, translatable or accessible:

```html
<figure>
  <h3>How registration works</h3>
  <ol class="flow">
    <li><strong>Choose your pass</strong> — full event or single day.</li>
    <li><strong>Register online</strong> — takes about five minutes.</li>
    <li>Decision: is the pass for a team of five or more?
      <ul>
        <li>Yes → the coordinator invoices you in one transaction.</li>
        <li>No → payment is taken at registration.</li>
      </ul>
    </li>
    <li><strong>Receive confirmation</strong> — badges arrive by email.</li>
  </ol>
  <figcaption>Registration flow, verified against the 2026 process on 12 November 2026.</figcaption>
</figure>
```

The styled version of this list draws the arrows and diamonds with CSS; the document keeps the meaning for screen readers, search and translation — the same content-first pattern as the chart skeleton in [Data visualisation](data-visualisation.md).

#### Building an icon family for a project

When no existing icon family fits, construct one rather than sourcing mixed sets — the Aicher/Isotype discipline in six steps:

1. **Fix the grid and stroke** — one construction grid, one stroke weight, one corner radius, stated numerically in the guidelines.
2. **Draw the core metaphors first** — the three to five concepts that will repeat most (entry, time, location, price, contact); these set the family's visual logic.
3. **Derive the rest from the core** — new icons recombine core elements rather than introducing new drawing styles; if an icon needs a new logic, either the set is wrong or the concept is out of scope.
4. **Test silhouettes at final size in grayscale** — identification must survive without colour or detail.
5. **Pair every icon with its label** and check the pair reads as one unit at reading distance.
6. **Publish the rules** — grid, strokes, do/don't examples — so downstream producers extend the family instead of diluting it (see [Iconography](../graphic-design/iconography.md) and [Brand guidelines](../branding/brand-guidelines.md)).

## 6. Decision framework

1. **Is the content data or structure?** Measured values → chart ([Data visualisation](data-visualisation.md)). Steps, relations, geography, narrative → diagram/infographic.
2. **What is the one reader question?** Map it to the type table; split competing questions.
3. **Does a standard diagram language already cover it?** Use conventions first; invent only with a key.
4. **How much can the audience hold?** If the structure needs more than about a screen or a spread, decompose: overview diagram + detail diagrams.
5. **Is this a composition or an asset?** Marketing infographics need the narrative discipline (headline, lead, provenance, CTA); documentation diagrams need convention discipline above all.
6. **What is the honesty budget?** List every encoding (sizes, colours, arrow semantics) and verify each encodes something true.

## 7. Examples

- **Registration flow for an event site.** Vertical flowchart, five steps, one decision with labelled branches, icons+labels for each step, the whole thing implemented as a styled ordered list so it survives translation and screen readers.
- **Multi-track programme.** Parallel lanes (one per stage), Gantt-style durations, a "now" marker during the live event, detail deferred to the full schedule table.
- **Public-explainer infographic.** Headline argument; lead with source and date; three body sections ordered importance-first, each one question; icon units counted and captioned (Isotype method); footer with sources, retrieval dates and the call to action.
- **Venue wayfinding graphic.** Schematic plan anchored to real geography, numbered stops matching physical signage, icon+label pairs from one pictogram family, orientation consistent with the entrance the reader actually uses.
- **Approval chain in an internal system.** Org-chart-style diagram of the sign-off path, dotted connectors for the optional finance review, one solid path from submission to approval, and a footnote defining who acts when a reviewer is absent — the accountability reading of the chart is as important as the flow.
- **"How it works" explainer for a product page.** Three-panel sequence diagram: inputs, the transformation in the middle, outputs; each panel one icon+label pair and one sentence; the technical detail (accuracy rates, method notes) deferred to a linked document rather than crammed into panel three.

## 8. Common mistakes

| Mistake | Why it fails | Correction |
| --- | --- | --- |
| Diagram type chosen for looks | The reader's question is unanswered; the graphic is wallpaper | Start from the question-to-type table |
| Unlabelled decision branches | The logic cannot be traced; readers guess | Label every exit from every diamond |
| Unlabelled icons | Assumptions presented as facts; decoding fails for outsiders | Icon + label as the default pair |
| Decoration that reads as data | Icon sizes and arrow flourishes imply encodings that do not exist | Deletion and encoding tests; strip or justify |
| Geography bent accidentally in schematic maps | Errors misinform (wrong adjacency, wrong distance) | Bend only on a systematic, stated rule |
| One hairball network diagram | Structure invisible; comprehension collapses | Cluster, then split into overview + detail diagrams |
| Timeline as table-with-decorations | Too many entries; the shape of the story is lost | Cap entries per track; move detail to a table |
| Infographic with no provenance | Unattributed numbers; audience cannot check | Lead and footer carry source, date, method |
| Mixed icon families | Clip-art collage effect; set reads as unprofessional | One construction system, one abstraction level |
| Whole-infographic-as-image (web) | Not searchable, translatable or accessible | Build as real content; draw with CSS/SVG; or provide full text equivalent |
| Decision tree with overlapping conditions | Two paths claim the same case; the reader cannot resolve it | Make branches mutually exclusive and collectively exhaustive; add the "otherwise" branch |
| Org chart drawn from the org's self-image rather than actual reporting | Accountability document misinforms new starters | Verify against the live reporting lines; show vacancies explicitly |
| Mixed abstraction levels in one diagram | Some parts detailed, others vague; the reader cannot calibrate | One level per diagram; link out for deeper detail |
| Sankey or flow widths without stated totals | Widths imply quantities no one can verify | State totals at each stage; keep the unit in the caption |

## 9. Evaluation checklist

- The diagram type answers one stated reader question; competing questions are split.
- Conventions follow the shared vocabulary; any invented symbols have a key.
- Flow direction, shape semantics and branch labels are present and consistent.
- Every icon is paired with a label unless it is an established public standard.
- Any visual variable that could be read as data (size, colour, position) encodes something true, or is confined to the background frame.
- The infographic has a takeaway headline, an orientation lead with source and date, a sequenced body, and a provenance footer.
- Hierarchy: one primary element per view; annotation subordinate.
- The graphic survives grayscale and final-size viewing; the "narrate it back" test passes.
- Web delivery is content-first (or provides a complete text equivalent).

## 10. Related topics

- [Data visualisation](data-visualisation.md) — the numeric sibling: encoding, honesty and colour rules inherited by infographics.
- [Information hierarchy](information-hierarchy.md) — layering, ordering and emphasis within diagrams and infographic narratives.
- [Iconography](../graphic-design/iconography.md) — building and auditing the icon families that diagram work depends on.
- [Gestalt and perception](../foundations/gestalt-and-perception.md) — why proximity, enclosure and similarity carry grouping in diagrams.
- [Grid systems](../layout/grid-systems.md) — the alignment backbone for schematic layouts.
- [Accessible colour](../accessibility/accessible-colour.md) and [Colour accessibility](../colour/colour-accessibility.md) — diagram palettes that survive colour-vision deficiency.
- [Posters](../applications/posters.md) and [Presentations](../applications/presentations.md) — distance-legibility rules for diagram-heavy artefacts.
- [Influential designers](../history/influential-designers.md) — Neurath's Isotype method and Aicher's Munich 1972 pictogram system.
- [Graphic design history](../history/graphic-design-history.md) — Swiss Style's information-design legacy.

## 11. References

- Otto Neurath, *International Picture Language* (1936) — the standard exposition of Isotype technique; "visual education" as the movement's motive [search-verified via Wikipedia: https://en.wikipedia.org/wiki/Isotype_(picture_language), 2026-11-23].
- Isotype Revisited (project on the Isotype history), "Introduction" — Neurath as the leading figure of Isotype, spanning political economy, sociology, philosophy, urbanism: https://isotyperevisited.org/2012/08/introduction.php [search-verified 2026-11-23].
- Marie Neurath and Robin Kinross, *The transformer: principles of making Isotype charts* (2009) — Isotype's working rules, including the anti-distortion stance [canonical].
- Otl Aicher's Munich 1972 pictogram programme and Beck's schematic Underground map as canonical cases of systematic diagram design [canonical].
- Edward Tufte, *Envisioning Information* (1990) and *Visual Explanations* (1996) — layering, avoiding distortion, explanatory graphics [canonical].
- This file is a synthesis of the sources above with the conventions of this library; conventional starting values (entry caps per track, key requirements) are stated as such, not as measured laws.
