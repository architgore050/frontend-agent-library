# Data visualisation

## 1. What is it?

Data visualisation is the graphical representation of quantitative or categorical data, built so that a reader can perceive patterns, compare magnitudes and draw conclusions faster and more reliably than by reading the raw numbers. It sits inside information design as the discipline concerned specifically with *data*: values measured or counted in the world. It is distinct from a diagram, which shows schematic or logical relationships (see [Diagrams and infographics](diagrams-and-infographics.md)), and from an infographic, which wraps data in an editorial narrative.

The field has two strands that a designer must keep in view at all times. The first is analytical: the chart is an instrument for the reader's own reasoning, and its job is to be accurate and effortful where accuracy matters. The second is presentational: the chart is a communication, and its job is to make one honest finding land quickly. Almost every controversy in visualisation practice — how much to decorate, whether to truncate an axis, whether to annotate — comes from these two strands pulling against each other.

Foundational figures to know by name: William Playfair, who invented the line, bar and pie chart in the late eighteenth century; Florence Nightingale, whose polar-area diagrams argued a public-health case; Charles Joseph Minard, whose flow map of Napoleon's 1812 campaign is a canonical study in multivariate restraint; Jacques Bertin, who systematised how marks carry meaning; and Edward Tufte, whose books set the modern vocabulary of data-ink, chartjunk and small multiples.

## 2. Why does it matter?

Human perception is extraordinarily good at judging visual properties and poor at comparing text values in memory. A reader scanning a bar chart extracts relative magnitudes preattentively — before conscious attention — whereas reading the same twelve numbers in a table requires holding each in working memory. This is the core argument of the field: graphics use the visual system's parallel processing, tables force serial processing. It is also the core *risk*: the same perceptual machinery accepts distortions without complaint, so a badly encoded chart misleads as fluently as a good one informs.

For an agent producing or reviewing design work, data visualisation matters for three concrete reasons. First, dashboards, reports, event communications and marketing assets routinely embed data claims, and the agent must choose encodings that support the claim. Second, visualisation failures are evaluation failures — a client reviewing a report will spot a 3D pie chart or an unreadable legend before they spot a kerning error. Third, visualisation decisions interact with accessibility, colour and layout decisions elsewhere in the design system, so they must be made systematically rather than chart by chart.

The stakes are asymmetric. A slightly clunky chart still communicates. A misleading chart — through a truncated axis, a distorted area or a cherry-picked range — communicates a false conclusion confidently. Honesty failures are worse than aesthetic failures.

Cognition sets the budget for everything that follows. Working memory holds roughly four chunks at once under load (a widely cited figure from cognitive psychology — treat it as an order of magnitude, not a law), which is why a chart with five encoded dimensions overwhelms while the same information split into small multiples reads easily. Perception also has known biases a designer must work with rather than against: the eye reads larger as more important, saturated as more urgent, and steeper as faster-growing. Every chart is an argument conducted through these biases; the honest designer uses them to *direct attention*, never to *distort magnitude* — the line between the two is exactly the line between emphasis and misleading visualisation.

## 3. Core principles

These principles are the synthesis of the sources listed in section 11; where a principle belongs to a named author it is attributed.

1. **Start from the question, not the data.** Every visualisation answers a question the audience is asking ("which region grew fastest?", "where is the budget going?"). Name the question before choosing the chart. The Data Visualisation Catalogue organises its whole selection system by communication purpose rather than by chart name, and notes that "while the allocation of each chart into specific functions isn't a perfect system, it still works as a useful guide" [accessed].
2. **Encode the data in the strongest variable.** Position along a common scale is the most accurately judged visual property; it should carry the most important dimension whenever possible (Bertin; Cleveland and McGill's experimental work reached the same conclusion — see section 4.3).
3. **Show the data, honestly and completely.** Tufte's dictum that "graphical excellence" reveals the data without distortion [canonical]. The chart must not change the story the numbers tell.
4. **Minimise non-data ink — with judgement.** Tufte's data-ink ratio is a powerful simplification tool and a poor absolute law; see section 4.4 for the modern critique.
5. **Layer the information.** A chart is itself an information hierarchy: headline takeaway, then data marks, then axis and labels, then annotation. See [Information hierarchy](information-hierarchy.md).
6. **Design for the least privileged reader.** Colour-blind readers, grayscale printing, small screens and low-quality projections are all real contexts. Redundant encoding is the cheapest insurance (section 4.5).
7. **Make the chart self-explanatory.** Labels beat legends; a takeaway title beats a descriptive title; annotation beats reader inference. A reader should not need the surrounding prose to survive the chart.

## 4. How it works

### 4.1 Tables versus charts

The first selection decision is not "which chart?" but "chart or table at all?". Tables and charts are different instruments, and choosing wrongly wastes the reader's effort in either direction.

| Situation | Better choice | Reason |
| --- | --- | --- |
| Reader must look up one exact value | Table | Charts force estimation; tables give the number |
| Few values (fewer than ~5) with a single message | Chart or bolded text | A chart is ceremony for data a sentence can carry |
| Many values across two dimensions | Table | Precise two-dimensional lookup; a chart of it becomes cluttered |
| Pattern, trend or shape is the message | Chart | Perception finds trends in geometry instantly |
| Comparing magnitudes across categories | Chart (bar) | Position/length encoding beats mental subtraction |
| Mixed units or mixed precision in one row set | Table | One chart per unit; a table handles heterogeneity |
| Data will be quoted or reused | Table | The table is the citable artefact; the chart is the argument |

A common professional pattern is the chart-plus-table pair: the chart carries the pattern, and a compact table beneath it carries the exact values for readers who need them. This is a deliberate use of redundancy (see [Information hierarchy](information-hierarchy.md), section on redundancy).

**Designing the table itself** deserves the same discipline as the chart. Right-align numerals so digits stack vertically for comparison; carry units in the column header rather than repeating them in every cell; sort rows by the reader's logic (value, time) rather than by data-entry order; round consistently to the precision the decision needs. Prefer book-style tables — no vertical rules, light horizontal rules separating logical groups only — and reserve zebra striping for genuinely wide tables where tracking across columns is hard. A table that repeats the chart's takeaway as its caption earns its place in the pair.

### 4.2 Chart selection by data relationship

The standard selection matrix asks one question: *what relationship in the data is the visualisation supposed to reveal?* The main relationship families, and the appropriate chart types for each:

| Data relationship | Question it answers | First-choice charts | Use with care |
| --- | --- | --- | --- |
| Composition (part-to-whole) | How does a total divide? | Stacked bar; single 100% stacked bar; treemap | Pie/donut only with few slices and clear ordering |
| Comparison | Which is bigger? | Bar chart (horizontal for long labels); dot plot; bullet chart | Radar charts; double-encoded grouped bars |
| Distribution | How are values spread? | Histogram; box plot; strip/bee swarm plot; violin plot | Over-plotted scatter for large samples |
| Relationship | Do two (or three) variables move together? | Scatter plot; bubble chart (third variable as area); heatmap for dense grids | Bubble charts exaggerate if area is mis-scaled |
| Trend over time | How does a series evolve? | Line chart; slope graph for two periods; area chart for a single cumulative series | Stacked area with many unstable series |
| Flow / process | How does quantity move through stages? | Sankey diagram; funnel chart | Sankeys with many crossing flows |
| Location | Where geographically? | Choropleth map; symbol map | Choropleths with uneven region sizes |
| Hierarchy | What nests inside what? | Tree diagram; treemap; sunburst (secondary) | Sunbursts beyond two levels |

The Data Visualisation Catalogue browses by purpose — Comparisons, Proportions, Relationships, Hierarchy, Distribution, Data over time and others — which mirrors this matrix [accessed]. Note the split: "proportions" and "part-to-a-whole" are both composition families, and "data over time" is the trend family.

A pie chart deserves its own warning because it is the most misused type in marketing work. Readers judge angles and areas far less accurately than lengths, so a pie works only when there are roughly two to five slices, one dominant slice, and a takeaway that does not depend on precise comparison of adjacent slices. A donut has the same properties, with the one advantage that a single headline figure can sit in the hole. When in doubt, a 100% stacked bar ordered by size outperforms either.

#### Design details for the core chart types

Choosing the type is half the decision; the other half is the construction details that determine whether the encoding reads cleanly.

- **Bar charts.** Start the value axis at zero — length encodes quantity, and truncation rescales it (see section 8). Sort bars by value unless the categories have a natural order (months, grades). Keep gaps between bars at roughly half the bar width as a conventional starting point. Use horizontal bars when category labels are long; label values at the bar end when exact numbers matter. Colour one series, not one bar, unless a single bar is the subject of the argument (then brand hue for it, neutral grey for context).
- **Line charts.** Time on the x-axis with evenly spaced ticks; y-axis truncation is honest for lines (position encoding, not length) but must be visibly marked. Four to six y-tick labels are sufficient. Direct-label each line at its endpoint where possible; beyond about five series, split into small multiples. Never connect discrete categories with lines — a line asserts continuity between its points.
- **Scatter plots.** Annotate the outliers you want remembered. Use smaller marks or transparency when overplotting (a rough conventional threshold: beyond about a thousand points). If you fit a trend, state the model in a note and phrase the title as association, not causation.
- **Histograms.** Bin choice changes the story: too few bins hide the shape, too many manufacture noise. A common starting rule is Sturges' formula (1 + log₂ n bins) for moderate samples; in practice, try two or three bin widths, keep the one that reveals, and disclose the bin width in the caption. For comparing two distributions, prefer side-by-side box plots to overlapping heavy fills.
- **Heatmaps.** Sequential palette only, with lightness carrying the magnitude. Sort rows and columns by a meaningful order rather than alphabetically, annotate the cells that matter, and show the scale explicitly — colour ramps cannot be read absolutely.
- **Pie/donut (when justified).** Two to five slices; largest slice starting at twelve o'clock and proceeding clockwise by size (conventional); direct labels with name and percentage; the donut hole holds exactly one figure, not two competing ones.

#### Small multiples and faceting

Small multiples — Tufte's term for repeated instances of one small chart, all sharing scales and design [canonical] — are the standard answer to "too many dimensions for one chart". The mechanics that make them work: identical axes and scales across every instance (or the comparison dies); panels ordered by a meaningful dimension (region size, year); minimal per-panel ink because the shared design carries the axes; and instances labelled inside their panels rather than in a shared legend. Modern BI "faceting" implements exactly this pattern. Reach for small multiples when a single chart would need more than three visual variables; they convert dimensionality into eye movement, which readers handle far better than multi-variable clutter.

#### Axes, ticks and gridlines

Axis construction has conventional defaults that carry most charts; deviate deliberately or not at all.

- Zero baseline for bars and areas; y-axis truncation only for line and dot plots, and only visibly marked.
- Four to six y-tick labels are enough; more clutter the scale without adding reading power.
- Avoid rotated labels — rotation is a symptom that the chart needs redesign (shorter labels, horizontal bars, grouped ticks), not a fix.
- Gridlines behind the data, in the lightest ink on the page; horizontal only for most charts; the zero baseline may be slightly heavier than the rest.
- Annotate the axis wherever a reader could misread it ("inflation-adjusted", "log scale", " provisional data").
- Date axes use real time spacing: missing periods show as gaps, not compressed ticks, and irregular intervals are never drawn as regular ones.

#### One chart or several?

When a third variable must join the view, choose the strategy deliberately rather than by default:

- **Encode within** (colour points or bars by category): workable up to roughly four categories; verify the palette and add direct labels where possible.
- **Facet into small multiples**: the default beyond four categories, and for stacked series that move independently (stacked areas shift for two reasons at once).
- **Split into two linked charts**: when the third variable needs its own scale or its own question answered.
- **Animate**: only when change over time *is* the message; animation as entrance decoration destroys the preattentive read and cannot be reproduced in print.

### 4.3 Bertin's visual variables

Jacques Bertin, in *Sémiologie Graphique* (1967), analysed graphics as a sign system: data is carried by *marks* (points, lines, areas) whose *visual variables* can be manipulated [canonical]. The classic variables are:

| Variable | Description | Best suited to carry |
| --- | --- | --- |
| Position | Placement on a plane or scale | Quantitative and ordinal data — the most accurate variable |
| Size (length, area, volume) | Extent of the mark | Quantitative data, ordered by accuracy: length > area > volume |
| Value (lightness) | Light-to-dark of a mark | Ordered/quantitative data; the backbone of sequential palettes |
| Texture / grain | Fineness of pattern | Ordered data; redundant encoding alongside value |
| Colour (hue) | Spectral identity | Categorical data; poor for magnitude |
| Orientation | Angle of the mark | Categorical data with few classes |
| Shape | Form of a point symbol | Categorical data, especially scattered points |

Bertin also described what each variable can *do*: some variables are *selective* (the eye can instantly isolate all marks sharing a value — hue is strongly selective), some *associative* (marks differing in the variable still read as a group), some *ordered* (the reader perceives an ordering, as in lightness), and only position is fully *quantitative* (magnitudes can be read off). This explains the discipline's central rule: magnitude belongs to position, size and value; category belongs to hue, shape and orientation.

Later writers extended the variable set — colour saturation, crispness, resolution, transparency and motion in work such as MacEachren's, and position/length/angle/slope/area per Cleveland and McGill's perceptual accuracy ranking [canonical]. For practical work the additions that matter are saturation (a second ordered variable, useful in diverging palettes) and motion (extremely preattentive, and therefore to be used sparingly and never decoratively in dashboards).

### 4.4 Data-ink ratio — Tufte, with modern critique

Edward Tufte's *The Visual Display of Quantitative Information* (1983; 2nd edition 2001) defines data-ink as the non-erasable ink of a graphic — the ink that carries the data itself — and proposes the ratio:

```
data-ink ratio = data-ink / total ink used to draw the graphic
```

and directs the designer, other things being equal, to *erase non-data-ink* and *erase redundant data-ink* [canonical]. The books that established this vocabulary, alongside *Envisioning Information* (1990), *Visual Explanations* (1996), *Beautiful Evidence* (2006) and *Seeing with Fresh Eyes* (2020), are listed and sold on Tufte's own site [accessed]. Companion concepts from the same programme: **chartjunk** (decoration that displaces data), **small multiples** (the same small chart repeated across a comparison dimension), **sparklines** (word-sized inline graphics), and the **slopegraph** (a two-time-point comparison chart).

The corrective value of the idea is enormous: grids every 0.5 units, drop shadows on bars, 3D effects, gradient fills and heavy borders are all ink that competes with the data. Applied as an absolute law, however, it has known weaknesses, and the modern consensus treats it as one consideration among several:

- **Redundancy aids reading.** Repeating the value label on a bar duplicates data-ink and measurably speeds reading. Tufte himself flags redundancy as a trade-off; practice has come down on the side of purposeful redundancy for presentational charts.
- **Decoration can aid memory.** Research on chart embellishment (notably Bateman et al.'s "useful junk" experiments [canonical]) found that embellished charts, while slower to read initially, were better remembered later. For marketing and event contexts — where the chart is a memory object, not an instrument — light, thematic decoration is defensible.
- **Aesthetics carry brand value.** A chart in a brand report participates in the brand system (see [Visual identity](../branding/visual-identity.md)); pure maximal-ratio charts read as unstyled. The resolution is to style the frame (typography, colour, spacing) while keeping the *data encoding* clean.
- **Empty space is not waste.** Whitespace carries no ink at all and is one of the strongest grouping and emphasis tools (see [Spacing and proportion](../layout/spacing-and-proportion.md)).

A practical restatement: maximise the ratio of ink that answers the reader's question, not the ratio of data-ink alone. Labels and annotations answer questions and therefore count as working ink.

### 4.5 Colour encoding

Colour in charts carries *meaning*, so palette choice is a data decision before it is a brand decision. Three canonical palette families:

| Family | Structure | Use for | Example logic |
| --- | --- | --- | --- |
| Sequential | Light-to-dark single hue (or single-hue ramp) | Ordered, quantitative values | Income, density, temperature magnitude |
| Diverging | Two hues ramping from a neutral midpoint | Values around a meaningful centre | Profit/loss, above/below average, change vs baseline |
| Categorical (qualitative) | Distinct, equally light hues | Unordered categories | Product lines, regions, user segments |

Rules of thumb that follow from this structure (conventional starting points, widely taught):

- Categorical palettes degrade beyond about eight hues; beyond that, readers cannot match legend to slice. Group small categories into "Other" or facet.
- In a sequential ramp, *value* (lightness) must do the work; hue differences alone will not imply order.
- Diverging palettes need a real, meaningful midpoint — colouring values that merely happen to straddle an arbitrary mean divergently is a dishonest encoding.
- Do not mix families in one chart: a categorical palette applied to an ordered variable destroys the order.

**Colour-blind safety** is non-negotiable, since roughly one in twelve men and one in two hundred women has some form of colour-vision deficiency (commonly cited figures — verify against current sources before quoting in published work). The key techniques, expanded in [Accessible colour](../accessibility/accessible-colour.md) and [Colour accessibility](../colour/colour-accessibility.md):

- Never encode meaning in red-vs-green distinction alone.
- Prefer the well-tested categorical ramps (e.g. Okabe–Ito, viridis) when hand-picking is not warranted.
- Build redundancy: differ lightness, position, shape or direct labels so the chart survives grayscale.
- Check contrast between adjacent data colours and against the background, not only text against background.

Brand palettes need not be abandoned: often one brand hue carries the hero series and neutral greys carry context series — which simultaneously solves emphasis (see [Information hierarchy](information-hierarchy.md)) and palette scarcity.

**Building a palette in practice.** Start from the data families the product needs (how many categorical series at maximum? does anything diverge around a centre?). Pick or construct a categorical ramp with verified distinguishability, then a sequential ramp in the brand's primary hue (varying lightness, not hue, across the ramp), and reserve the diverging pair for the rare real midpoints. Test all three in grayscale and against colour-vision deficiency simulation before they enter the design system, and document the rules — "which family for which data type" — in the guidelines so the next chart does not reinvent them (see [Brand guidelines](../branding/brand-guidelines.md)). The palette is part of the information design, with the same status as type scale or spacing units; treat palette drift chart by chart as the defect it is.

### 4.6 Labels, legends and annotation

Annotation is the layer that converts a picture into an argument. The standard hierarchy of text on a chart, from largest job to smallest:

1. **Takeaway title** — states the finding ("Churn doubled after the March pricing change"), not the contents ("Churn rate by month"). This is the headline layer of the chart's information hierarchy.
2. **Axis labels and units** — variable name and unit ("Revenue (GBP millions)"). Omitting units is the most common honesty defect in published charts.
3. **Data labels** — exact values on marks where the exact value matters. Use selectively; labelling every mark is chartjunk by another name.
4. **Direct series labels** — label lines/bars at the data itself where space allows, replacing legends. Legends force a two-step lookup (mark → legend key → label); direct labels make the mark self-explanatory. Reserve legends for many-series charts, maps and dense scatters.
5. **Annotation notes** — event markers ("Product launch 14 Mar"), threshold lines, a source line and (for time series) the retrieval date.

Number formatting conventions worth adopting as defaults: round to the precision the decision needs (two significant digits for a presentation chart); use thousands separators; state currency and units in the axis label rather than repeating "£" on every tick; and never let a legend use abbreviations the axis does not define.

One annotation family is routinely omitted and is the difference between a claim and a finding: **uncertainty**. Sample sizes (n = …), confidence or credible intervals, margin-of-error notes and "preliminary data" flags belong on the chart, not in the prose — a difference shown without any statement of its uncertainty is a claim without a test. Represent intervals with error bars or shaded bands, state n for survey charts, and mark provisional figures visibly (hatched fill or a "provisional" tag) so a reader cannot mistake an estimate for a settled value.

#### Interactivity and static output

Interactive charts and their static exports are different artefacts and need different annotation budgets. Interactivity moves exact values into tooltips, zoom and filters — which works on screen and disappears everywhere else. The static export (report page, slide, social post, PDF) must be self-contained: every value the takeaway depends on must be readable without a hover. The professional discipline is to design the static version first, then add interaction as an enhancement, and to remember that charts designed for a 4K monitor are illegible printed or embedded at half size — test at final render size, not in the design tool's canvas.

### 4.7 Simplification without distortion

Simplification is legitimate when it removes *ink*; it becomes distortion when it removes or reshapes *information*. Useful tests:

- **The aggregation test.** Aggregating twelve monthly points to four quarters is legitimate if the question is annual; it is distortion if the claim is about monthly volatility that smoothing now hides.
- **The exclusion test.** Removing a series (e.g. an inconvenient control group) changes the comparison, not just the clutter. Exclusions must be visible and justified in a note.
- **The rescale test.** Log scales are legitimate for data spanning orders of magnitude, and dishonest when applied silently to data a lay reader will read linearly. Log axes must be visibly marked.
- **The encoding test.** If a simplification changes the perceptual judgement (3D perspective changing apparent slice size, area scaling by diameter instead of area), it is distortion, not simplification.

#### Reading time series honestly

Time series carry their own honesty traps beyond axis truncation. **Seasonality** — weekly, quarterly or annual rhythms — makes any short window lie by omission: a March-only chart of retail sales will show a slump that is merely seasonal. Show the same period in previous years, or state the seasonal context in a note. **Baseline changes** — a new product, a revised definition, a merged region — create a step that the chart must annotate, because unexplained steps read as performance swings. **Per-capita normalisation** is the difference between "our city has the most cases" and "our city has the highest rate"; absolute counts flatter large entities, so state which is shown and why. **Deflator choices** (nominal vs inflation-adjusted currency) similarly change every trend. The general rule: the chart's note should make it possible for a competent sceptic to reproduce your comparison — that is the minimum standard for a statistical graphic that argues anything.

## 5. Practical application

A repeatable workflow for producing a single chart:

1. **Write the question and the takeaway first.** If you cannot state the takeaway in one sentence, the chart is not ready to be drawn.
2. **Inspect the data.** Range, outliers, missing values, sample size. Outliers decide the axis strategy; missing values decide the encoding (gaps, not zero-fills).
3. **Choose the relationship family and chart type** using the section 4.2 matrix.
4. **Assign variables.** Most important quantitative dimension → position/length. Categories → hue/shape/direct labels. Order → value/lightness. Write down the assignment; it becomes the legend you may not need.
5. **Draft, then subtract.** Remove gridlines beyond the minimum, remove the legend if direct labels fit, move the takeaway into the title. Every removal should have a reason.
6. **Annotate.** Units, source, retrieval date, event markers that the takeaway relies on.
7. **Test on three readers.** Can they state the takeaway, read one exact value, and identify one series — in under ten seconds, without help?

#### Application at dashboard scale

Dashboards are hierarchies of charts, and they inherit every rule above plus layout discipline. The most important metric takes the primary position (top-left in left-to-right reading) and the strongest visual weight; supporting charts group by the reader's questions, never by the data warehouse's table structure; shared filters and time ranges sit in one consistent place; and every chart carries its own takeaway title. Cap a single dashboard view at roughly six to nine charts (a conventional ceiling) — beyond that, split views by question. Alignment comes from the grid (see [Grid systems](../layout/grid-systems.md)); the layering of metric, context and detail comes from [Information hierarchy](information-hierarchy.md).

For web implementation, a minimal accessible skeleton for a bar chart looks like this:

```html
<figure class="chart" role="img"
        aria-label="Bar chart: newsletter signups by month, January to June 2026.
                    Signups rose from 340 in January to 980 in June, peaking at 1,050 in May.">
  <figcaption>Newsletter signups doubled over the first half of 2026</figcaption>
  <table class="chart-data">
    <caption class="visually-hidden">Newsletter signups by month, 2026</caption>
    <tr><th scope="row">Jan</th><td>340</td></tr>
    <tr><th scope="row">Feb</th><td>420</td></tr>
    <tr><th scope="row">Mar</th><td>560</td></tr>
    <tr><th scope="row">Apr</th><td>730</td></tr>
    <tr><th scope="row">May</th><td>1,050</td></tr>
    <tr><th scope="row">Jun</th><td>980</td></tr>
  </table>
</figure>
```

```css
.chart-data { display: block; }
.chart-data tr { display: flex; align-items: center; gap: 0.5rem; }
.chart-data th { inline-size: 3rem; text-align: right; font-weight: normal; }
.chart-data td {
  background: var(--brand);           /* one hue; neutrals for context series */
  color: #fff;
  inline-size: calc(var(--v) / 1050 * 24rem);  /* length encodes value */
  padding: 0.25rem 0.5rem;
}
```

This pattern — a real `<table>` visually restyled as a chart — keeps screen readers, copy-paste and search working while giving sighted readers the bar encoding. Note the figure carries: a takeaway caption, a unit-free but labelled value column, and an `aria-label` that states the finding.

## 6. Decision framework

Answer these questions in order; each answer narrows the choice.

1. **Is the message one sentence?** If yes, consider whether a chart is needed at all (bolded figure or sentence may be stronger).
2. **Does the reader need exact values or a pattern?** Exact → table; pattern → chart; both → chart + compact table.
3. **Which relationship family is the question about?** Composition / comparison / distribution / relationship / trend / flow / location / hierarchy → section 4.2 row.
4. **How many dimensions must the reader hold at once?** Above three, split into small multiples rather than one overloaded chart.
5. **Which variables encode which dimension?** Position for magnitude, hue for category, lightness for order. Any dimension that only colour carries must survive a redundancy check.
6. **Is any aspect of the presentation capable of changing a judgement?** Axis truncation, area scaling, dual axes, 3D — if present, justify or remove.
7. **Does it pass the ten-second test** with a colour-blind reader and a grayscale print?

## 7. Examples

**Trend, one series.** Monthly event registrations across a year. Line chart, time on x-axis, direct label on the final point, annotation at the campaign start date. Takeaway title: "Registrations tripled in the six weeks after the campaign launch."

**Composition, five parts.** Marketing budget split. Horizontal 100% stacked bar, largest segment first, brand hue for the segment the argument concerns and greys for the rest, values labelled in-segment. A pie would be defensible here; the stacked bar is better because adjacent segments compare by length, not angle.

**Distribution, two groups.** Session durations for mobile vs desktop. Box plots side by side on a common axis, annotated with medians. The takeaway ("desktop sessions are 40% longer but far more variable") is visible in the geometry without reading a single number.

**Relationship, two variables.** Advertising spend vs conversions across twenty campaigns. Scatter plot with spend on x, conversions on y, one annotated outlier ("launch campaign, not comparable"). A bubble adding budget as area is tempting but usually overloads the read; small multiples per channel communicate more.

## 8. Common mistakes

| Mistake | Why it misleads | Correction |
| --- | --- | --- |
| Truncated y-axis on a bar chart | Bar length encodes value from zero; truncating makes small differences look huge | Start bars at zero; if showing fine differences, use a dot plot or line chart where truncation is honest, and mark the truncation visibly |
| Dual y-axes | Two arbitrary scalings imply correlation the reader cannot verify | Split into stacked panels or small multiples with a shared x |
| 3D pie / 3D bar charts | Perspective distorts area and angle systematically | Flat charts; drop the third dimension entirely |
| Cherry-picked time range | Selecting a flattering window changes the trend's direction | Show the full relevant period or justify the window in a note |
| Rainbow / many-hue sequential palette | Hue has no order; readers cannot rank colours | Sequential single-hue ramp; value carries the order |
| Pie with 8+ slices | Angle comparison fails; legend lookup collapses | Group into "Other" or switch to a sorted bar chart |
| Stacked area with unstable series | Middle bands shift for two reasons at once (own change + change below) | Small multiples of each series, or stacked bars with visible segment labels |
| Area scaled by diameter | Circles appear to grow slower than their values | Scale area by value (radius by its square root) or use length encoding |
| Legend detached from data | Two-step lookup; errors under time pressure | Direct labels at the data; legend only when unavoidable |
| Missing units or source | The chart cannot be checked or reused | Units in axis label; source and retrieval date in a footnote |
| Line chart for discrete categories | The line asserts continuity between unrelated items | Bars or dot plots for categorical data |
| Overlapping heavy-filled histograms | Occluded areas hide both distributions | Side-by-side box plots, or outline histograms with transparency |
| Error bars or sample sizes omitted | A noisy difference presented as a finding | State n, show intervals; flag provisional values |
| Charts authored for one canvas size only | Illegible when embedded, printed or projected | Test at final render size; design the static version first |
| Interaction-only annotations (tooltip-dependent charts) | The exported or printed chart loses its exact values | Self-contained static version first; interaction as enhancement |
| Small multiples with inconsistent scales | Panels cannot be compared; the faceting lies | Share axes and scales across all instances, or say why not |
| Seasonal window presented as a trend | Normal rhythms read as performance changes | Show the same period in prior years or state the seasonality |

Two honesty failures deserve emphasis because they are common in professional marketing work and are not always intentional. The first is the silently truncated axis: a report generator's default axis often starts at the data minimum, which turns a 2% change into a visually dramatic swing. The second is the selective range: choosing the window since the last low point manufactures an upward trend. Both are corrected by the discipline in section 4.7, and both are the kinds of defect a reviewer should actively hunt for (see [Design critique](../foundations/design-critique.md)).

## 9. Evaluation checklist

- The takeaway is stated in the title, and the title states a finding rather than a topic.
- The chart type matches the data relationship (section 4.2), or the deviation is justified.
- The most important dimension is carried by position or length, not by hue alone.
- Categorical / sequential / diverging colour logic matches the data type; the palette survives colour-blind viewing and grayscale.
- Axes start where the encoding demands (zero for bars); any truncation is visible and justified.
- Units, source and retrieval date are present.
- Labels sit at the data where possible; any legend is necessary and ordered to match the data order.
- Non-data decoration is brand-frame styling only, never inside the plot's data region.
- An exact value can be read within ten seconds, and the chart reads correctly in grayscale.
- A screen-reader or text-only reader receives the finding via caption, `aria-label` or accompanying table.
- Series counts are within reading limits (about five lines, four encoded categories) or split into facets.
- Any third variable is carried by a deliberate strategy (encode within, facet, or linked charts), not by accident.

Two extended cases show the checklist at work. **Case: quarterly performance pack.** The draft used a 3D pie for channel mix (eight slices, exploded), a truncated bar chart for regional growth, and a dual-axis chart combining ad spend and revenue. The rebuild: a horizontal 100% stacked bar with in-segment labels for mix; a bar chart on a zero baseline, with a dot plot inset for the fine differences; spend and revenue as two stacked panels sharing the time axis, correlation argued in the note rather than implied by axis trickery. Every takeaway title states a finding; the note block carries source, retrieval date and the definition of "channel". **Case: dashboard conversion.** A twelve-chart dashboard regrouped by reader question into three views of four charts each; the primary metric promoted to a large annotated figure in each view's top-left; the legend set replaced with direct labels; palettes reduced to brand hue plus greys with the diverging pair reserved for the variance view. Both rebuilds changed no data and no finding — only the encoding — which is the point: honesty failures are construction failures, and they are fixable in construction.

## 10. Related topics

- [Information hierarchy](information-hierarchy.md) — layering takeaway, data, annotation; emphasis and redundancy.
- [Diagrams and infographics](diagrams-and-infographics.md) — schematic relationships, process and narrative graphics.
- [Accessible colour](../accessibility/accessible-colour.md) and [Colour accessibility](../colour/colour-accessibility.md) — contrast and colour-vision deficiency.
- [Colour theory](../colour/colour-theory.md) — the underlying colour system.
- [Gestalt and perception](../foundations/gestalt-and-perception.md) — why encodings and groupings read the way they do.
- [Typographic hierarchy](../typography/typographic-hierarchy.md) — the text layers around the chart.
- [Grid systems](../layout/grid-systems.md) — aligning multi-chart dashboards.
- [Presentations](../applications/presentations.md) — charts designed for projection distances.
- [Design critique](../foundations/design-critique.md) — reviewing charts for honesty, not just style.

## 11. References

- Edward Tufte, *The Visual Display of Quantitative Information* (1983; 2nd ed. 2001), *Envisioning Information* (1990), *Visual Explanations* (1996), *Beautiful Evidence* (2006), *Seeing with Fresh Eyes* (2020). Graphics Press. Titles, dates and page counts verified on the author's site: https://www.edwardtufte.com/books/ [accessed 2026-11-23]. Data-ink ratio, chartjunk, small multiples, sparklines and slopegraphs attributed as canonical concepts of these works [canonical].
- Jacques Bertin, *Sémiologie Graphique* (1967; English translation *Semiology of Graphics*, 1983). Visual variables and their selective/associative/ordered/quantitative properties [canonical].
- William S. Cleveland and Robert McGill, "Graphical Perception: Theory, Experimentation, and Application to the Development of Graphical Methods" (1984). Perceptual ranking of encodings [canonical].
- The Data Visualisation Catalogue, https://datavizcatalogue.com/search.html — purpose-based chart selection categories and selection guidance, including the quoted caveat on category allocation [accessed 2026-11-23].
- Scott Bateman et al., "Useful Junk? The Effects of Visual Embellishment on Comprehension and Memorability of Charts" (CHI 2010). Embellished charts and memorability [canonical].
- Alan MacEachren, *How Maps Work* (1995). Extended visual variables for geographic representation [canonical].
- William Playfair's late-eighteenth-century inventions of the line, bar and pie chart; Florence Nightingale's polar-area diagrams (1858); Charles Joseph Minard's flow map of the 1812 Russian campaign (1869) — canonical history recounted in Tufte and standard histories of statistical graphics [canonical].
