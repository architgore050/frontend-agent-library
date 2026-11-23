# Principles of Design

## 1. What is it?

Principles of design are the rules of arrangement — the ways the ten [elements of
design](elements-of-design.md) are organised so that a composition communicates.
Where elements are the vocabulary, principles are the grammar: balance, contrast,
hierarchy, alignment, repetition, proximity, rhythm, movement, proportion, unity,
variety, emphasis, dominance and negative space. A principle is not a physical thing
you can point at; it is a *relationship between elements* that perception reliably
reads in a certain way.

The most important professional habit is to treat principles as a *system*, not a
list. They exist only in relation to one another: contrast is meaningless without
similarity to contrast against, hierarchy cannot exist without differentiation,
unity cannot be evaluated without the variety that threatens it. Fourteen
definitions in isolation produce designers who can name every principle yet apply
none; this file therefore spends as much effort on the *interactions* as on the
individual principles.

Two caveats frame everything that follows. First, principles are descriptive
generalisations about human perception before they are prescriptive rules — they
work because of how vision and attention behave, not because a style guide says so.
Second, they are defeasible: every principle can be deliberately broken for effect,
and much celebrated design is built on controlled violation. The skill is knowing
what a violation costs and whether the goal pays for it.

## 2. Why does it matter?

Principles matter because they are the difference between *decoration* and
*communication*. A design can contain beautiful elements and still fail if the
arrangement does not tell viewers what matters, what belongs together, and where to
look next. Nielsen Norman Group's summary of visual design in UX makes the
connection explicit: scale, visual hierarchy, balance and contrast are applied so
that users can "easily parse the visual" and know how to use it — and when users
cannot decide where to look, the hierarchy is missing ("5 Principles of Visual
Design in UX", 2020) [accessed].

For an AI agent, principles are the bridge between taste and reasoning. "This layout
feels wrong" is not actionable; "this layout has two competing dominant elements, so
the hierarchy is ambiguous" is. Principles convert aesthetic complaints into
diagnosable conditions, which is the foundation of [design
critique](design-critique.md) and of any repeatable [quality
framework](../evaluation/design-quality-framework.md).

Principles also matter because they are medium-independent: proximity groups a form
on a phone and columns on a poster by the same mechanism, and contrast drives a
restaurant menu and a dashboard alike. An agent that understands the system can move
between web, print and brand-kit work without relearning — exactly what the
repository's reuse goal requires.

## 3. Core principles

### 3.1 Balance

Balance is the distribution of visual weight around an axis. Weight — the combined
pull of size, value, colour, density and position — must feel settled, or the
composition reads as tilted or accidental. There are four working types.
*Symmetrical* balance mirrors content around an axis and reads as formal, stable and
official (certificates, government pages, luxury packaging). *Asymmetrical* balance
places unequal weights at unequal distances so that, like a see-saw with a heavy
child close to the pivot, the composition still settles — it reads as modern,
energetic and confident. *Radial* balance arranges content around a centre point.
*Mosaic* (crystalline) balance distributes many equal weights with no single focus,
as in mood-board walls.

The professional warning is Arnheim's: balance is judged *perceptually*, not
mathematically — a small dark element can outweigh a large pale one, and a shape
near the centre has more weight than the same shape near the edge (*Art and Visual
Perception*) [canonical]. NN/g likewise describes balance as distributing visual
signal evenly "not necessarily symmetrically", failing when one area dominates so
much that others become invisible [accessed]. Evaluate by squinting until detail
disappears and asking whether the remaining masses settle.

### 3.2 Contrast

Contrast is the juxtaposition of dissimilar elements — in value, colour, size,
weight, shape, direction or spacing — to signal that things differ in category,
function or behaviour. NN/g defines it exactly this way and notes that contrast is
the mechanism behind "the red delete button" convention: difference in colour tells
users that difference in consequence exists [accessed]. Contrast is also the raw
material of legibility; without value contrast, text disappears.

Contrast must be *deliberate and bounded*. Every strong contrast should mean
something (primary versus secondary action, heading versus body, interactive versus
static). Unbounded contrast — many unrelated differences at once — produces visual
noise instead of order. And contrast has costs: lowering text contrast to
de-emphasise content also reduces legibility (NN/g's caution), and WCAG thresholds
put hard floors under how weak contrast may become. Quantitative rules live in
[Colour theory](../colour/colour-theory.md); the principle here is that contrast is
a signal, and signals must stay interpretable.

### 3.3 Hierarchy

Hierarchy is the ordering of content by importance, made visible so the eye attends
to elements in the intended order. It is the master principle of informational
design: everything else (scale, contrast, placement, weight) exists largely to
*build* hierarchy. NN/g defines it as "guiding the eye on the page so that it
attends to different design elements in the order of their importance", achieved
through scale, value, colour, spacing and placement [accessed].

Hierarchies are built with three to five levels; more and users cannot track the
differences. Each level should differ from its neighbours on *at least two*
independent channels (size + weight, weight + colour, spacing + value) so the
distinction survives imperfect viewing. Test by asking a viewer to point to the most
important thing, then the second, without prompting — hesitation or disagreement
means the structure is weak. The mechanics of visual weight belong to [Gestalt and
perception](gestalt-and-perception.md); the point here is that hierarchy is an
outcome, and contrast, scale and dominance are its causes.

### 3.4 Alignment

Alignment is the arrangement of elements along common edges or axes. Its mechanism
is invisible structure: when elements share an edge, perception draws a line that
reads as order and intent; when edges almost-but-not-quite align, perception reads
error. Alignment is the cheapest way to make a design look deliberate — "nothing
should be placed arbitrarily; every item should have a visual connection to
something else on the page", as Robin Williams puts it in *The Non-Designer's Design
Book* [canonical].

Alignment comes in two families: *edge* alignment (left, right, centre) and *axis*
alignment (elements balancing around a shared axis without touching). Strong layouts
usually commit to one dominant alignment; centred-everything layouts are safe but
flat, and mixed alignments without logic look broken. In UI, alignment is
implemented through spacing systems and layout grids (see [Grid
systems](../layout/grid-systems.md)). The classic misuse is *near alignment* — items
off by one or two pixels — which reads as sloppiness rather than style.

### 3.5 Repetition

Repetition is the deliberate reuse of visual properties — colour, shape, type style,
spacing, components — so that different parts of an artefact read as one system. It
is the principle that turns a page into a *document* and a screen into an
*interface*: users learn a pattern once and recognise it everywhere. Repetition is
also the foundation of design systems and brand kits, where the goal is that any
page, slide or post produced later still belongs to the family.

Repetition must repeat *structure*, not just decoration: the same component anatomy
(padding, corner radius, label position) teaches far more than the same accent
colour. Too little repetition, and every screen feels disorienting; too much —
identical rows stretching down a page — produces monotony and the "bypassing" effect
where users skip repeated openings (see [Gestalt and
perception](gestalt-and-perception.md)). Note that repetition can *conflict* with
proximity: a repeated style scattered across a page does not group, and NN/g's
research shows proximity can overpower similarity cues [accessed].

### 3.6 Proximity

Proximity is the grouping of related items by placing them close together, and the
separation of unrelated items by space. It is, per NN/g, among the strongest
grouping principles — strong enough to overpower competing cues like colour or shape
similarity — and its practical reach is enormous: labels sit next to inputs,
captions next to images, related actions cluster in a toolbar [accessed]. Proximity
is the physical implementation of "things that relate, sit together", and it is
where most "cluttered design" complaints actually originate: the designer grouped by
*type of content* in their head but not in *space*.

Proximity works as a two-sided rule. The negative half — separating unrelated groups
— is violated even more often: a "Cancel" button three pixels from "Submit" is a
classic accidental pairing with real consequences. Spacing systems make proximity
scalable: define a small set of spacing steps, and require that the space between
related items is visibly smaller than the space between groups. The perceptual
mechanism is detailed in [Gestalt and perception](gestalt-and-perception.md).

### 3.7 Rhythm

Rhythm is the recurrence of elements or intervals at predictable pauses — regular,
flowing or progressive. Regular rhythm (equal-width cards, evenly spaced rows) reads
as orderly and calm; flowing rhythm (intervals that undulate) reads as organic;
progressive rhythm (each interval larger than the last) reads as acceleration and
crescendo. Rhythm is built from repetition plus *spacing discipline*: repetition
supplies the motif, spacing supplies the beat.

Rhythm matters most in multi-item artefacts — list rows, grid tiles, document
sections, poster series — telling the viewer "this is the pattern; deviations from
it are meaningful". That clause is rhythm's hidden power: an irregular beat
highlights the exception (see variety, below). Misuse takes the form of accidental
rhythm: intervals that are *almost* equal, which reads as error, or beats so
irregular the artefact feels scattered. Rhythm is evaluated by scanning the
composition and asking whether the eye could tap along.

### 3.8 Movement

Movement is the principle of guiding the eye along a path through the composition —
in static media through implied motion (diagonals, curves, repeated decreasing
shapes), in interactive media also through literal animation (transitions,
scrolling, parallax). Movement answers the question hierarchy leaves open: after the
viewer sees the most important element, *where do they go next?* A composition with
hierarchy but no movement is a one-liner; a composition with movement is a sentence.

In print, movement is built from direction (a diagonal band, a zigzag of aligned
images) and from pointed elements (arrows, faces looking toward content, converging
lines). In UI, movement includes scroll behaviour, transition choreography and the
sequence in which content reveals. Its professional caution is restraint: constant
or looping motion on screen competes with reading, and research-based guidance
suggests using animation sparingly and briefly (a pulse two or three times, never
continuously, is a sound conventional limit). Misuse: motion that *randomly*
redirects attention, or static compositions whose implied directions contradict each
other so the eye orbits without arriving.

### 3.9 Proportion

Proportion is the size relationship between parts and wholes — headline to page,
image to column, logo to card. It overlaps with scale (which is relative size as an
importance signal) but focuses on *fit*: does each part feel correctly sized for its
container and its role? Proportion systems have a long formal history — classical
ratio lore (golden ratio, root rectangles) from geometric aesthetics — and these
survive as useful conventions for dividing space, but they are conventions, not
laws; competent modern work usually prefers simple, systematic ratios (1×, 1.5×, 2×,
3×) that a whole team can reproduce.

Proportion failures are immediately legible as awkwardness: a logo too large for the
business card, a table crammed into a narrow column, a hero image that dwarfs its
own headline. The practical rule is *relation over decoration*: choose proportions
from a consistent system and check each part against its container at final size,
not in isolation. Proportion interacts strongly with hierarchy (bigger = more
important, so proportion is a hierarchy lever) and with balance (an oversized part
tilts the whole).

### 3.10 Unity

Unity is the sense that all parts of an artefact belong to the same design — same
family of shapes, colours, type, spacing and tone. Unity is produced mainly by
repetition and consistency, and it is what makes a brand kit recognisable across an
infinite range of future artefacts. A unified design survives partial viewing: users
see one corner of a poster, or one screen of an app, and still recognise the maker.

Unity is evaluated by the "swap test": if a component from one artefact were pasted
into another by the same organisation, would it fit without adjustment? If yes, the
system is unified. The failure mode of pursuing unity too far is monotony — pages so
consistent that nothing stands out and nothing feels alive. Unity therefore always
needs variety as its counterweight; the two form the central tension of section 4.

### 3.11 Variety

Variety is the introduction of controlled differences that hold attention, mark
transitions and prevent monotony. Where unity says "one family", variety says
"interesting members of it": one rotated card, one accent hue, one oversized numeral
in a document grid. The perceptual engine behind variety is the isolation effect —
the item that differs from its neighbours is the one noticed and remembered (the von
Restorff effect, catalogued in Laws of UX) [accessed].

Variety must be *structured*: a deliberate deviation from an established pattern,
not random difference. The classic failure is "everything is an exception" — when
many elements each differ in their own way, the design reads as chaos and no
deviation can signal anything. A workable ratio mindset (not a law): establish a
strong pattern with repetition, then break it in one or two places per view, where
the break carries the meaning. Variety is also the natural tool for transitions — a
change of pattern tells the audience a new section has begun.

### 3.12 Emphasis

Emphasis is the act of making one element dominant so that it is seen first — the
designed entry point of the composition. Emphasis is implemented by every
differentiating tool at once: higher scale, stronger value contrast, isolation
through space, unique colour, or pointed direction from neighbours. Its logic is
competitive: an element stands out only because the others *agree to recede*. This
produces the discipline's most quoted consequence — if everything is emphasised,
nothing is; emphasis is a budget, and spending it everywhere zeroes it out.

Emphasis should map to function: emphasise the element that serves the artefact's
goal (the call to action, the event name, the key figure), not the most photogenic
one. Misuse: competing focal points, emphasis by decoration rather than difference,
and weak emphasis where the intended focal element ties with the background in
weight. Testing is the five-second view: what did the viewer look at first? If not
the intended element, emphasis failed.

### 3.13 Dominance

Dominance is the *degree* of emphasis — how strongly one element outranks the field.
Where emphasis asks "which one?", dominance asks "by how much?". Compositions can be
strongly dominant (one hero, everything else clearly subordinate — typical for
posters and landing pages) or softly dominant (a gentle rank ordering — typical for
documents and dashboards). Dominance creates hierarchy's first step: without a
dominant element, the eye has no entry point and wanders.

Dominance interacts with balance (a strongly dominant element must be balanced by
distributed lesser weights) and with unity (the dominant element often carries the
brand's boldest attributes). The common misuse is *dominance without submission*: a
large headline plus several nearly-as-large sub-elements, a shouty composition with
two or three competing centres. The remedy is not to shrink the headline but to
lower the sub-elements' weight decisively.

### 3.14 Negative space

Negative space is the area not occupied by content — treated here as a principle (an
active design decision) rather than merely an element, because its power lies in
what it *does*: it separates (implementing proximity), isolates and therefore
emphasises, frames (giving dominance a stage), and paces (creating rhythm through
intervals). Negative space is "active" when shaped intentionally — its contours echo
and support the content — and "passive" when it is merely leftover.

The professional discipline is to design the space, not just the marks: a heading is
emphasised as much by the emptiness above it as by its size; a poster's logo gains
presence from the clearing around it. For brand work this becomes a hard
specification — logos require defined clear-space rules so negative space is
protected in every future application. The misuse is symmetrical: crowded layouts
(nothing can separate or emphasise) and over-emptied ones (relationships dissolve).
Both are failures to *decide* the space.

## 4. How it works

The principles form a system with three layers. At the bottom, perception supplies
the physics: elements carry weight, similarity and nearness create groups, and
differences draw attention. In the middle, principles are operations on those
physics: contrast *creates* differentiation, proximity *creates* grouping,
repetition *creates* expectation, emphasis *spends* differentiation on one element.
At the top, coherence emerges: hierarchy, rhythm and unity are not applied directly
anywhere — they *result* when the lower operations are arranged consistently.

This explains why the principles interact so tightly. Contrast supplies hierarchy's
raw material; dominance amplifies one contrast into an entry point; proximity groups
the rest; repetition makes the groups recognisable across the artefact; rhythm and
spacing discipline make the groups scannable; unity binds the whole; variety keeps
it alive. Remove any one and the effects upstream degrade. A useful diagnostic
habit: when a composition fails, do not hunt for the "broken principle" as a culprit
in isolation — trace which *relationship* between two principles is missing or
contradictory.

| Interaction | How the principles combine | Failure when ignored |
| --- | --- | --- |
| Contrast → hierarchy | Without value/size/weight differences, nothing can outrank anything; hierarchy is built from contrasts | Flat, uniform pages where every item looks equally important |
| Dominance → hierarchy | One decisively dominant element gives the eye an entry point and anchors the rank order | No entry point; the eye wanders and reads nothing in order |
| Emphasis + contrast | Emphasis exists only against a field of similarity; contrast must be saved to spend | Emphasising everything neutralises emphasis; or competing focal points |
| Proximity → grouping | Nearness groups; whitespace separates; stronger than most other cues | Related items drift apart; unrelated items fuse ("Submit" glued to "Cancel") |
| Repetition + spacing → rhythm | The repeated motif is the beat; the interval is the tempo | Accidental, almost-equal spacing reads as error; patterns never become scannable |
| Repetition → unity | Consistent component anatomy and properties make artefacts read as one family | Each screen feels new; no recognisability across a brand kit |
| Unity vs variety | Unity without variety is monotony; variety without unity is chaos | A sea of sameness, or noise where nothing signals |
| Balance ↔ alignment | Alignment provides the axes on which balance is judged | Lopsided or accidental-feeling pages despite effortful elements |
| Proportion ↔ hierarchy | Relative size is the fastest importance cue, so proportion is hierarchy's lever | Oversized secondary elements steal rank; undersized heroes fail |
| Movement ↔ rhythm | Rhythm provides the beats; movement walks the eye across them | Hierarchy without flow — a one-glance composition with no next step |
| Negative space ↔ emphasis | Space isolates, and isolation is emphasis; dominance needs a clearing | Emphasis attempted by decoration alone; crowded layouts that shout |
| Variety ↔ attention | The lone deviant item is noticed and remembered (isolation effect) | Deviations everywhere — so no deviation signals anything |
| Proximity vs similarity (conflict rule) | When grouping cues disagree, nearness usually wins | Repeated styles scattered across a page read as separate groups |

## 5. Practical application

Applying the principles starts with the artefact's goal, because principles are
budgeted, not maximised. A poster wants one strong dominant element and high
contrast; a tax form wants soft dominance, strong grouping and calm rhythm; a brand
kit wants maximal unity and minimal variety at the system level, with variety
delegated to content. The agent should first decide what the artefact must do, then
allocate.

A workable build order for any layout:

1. **Group first (proximity).** Cluster related content in space; separate unrelated clusters with visibly larger gaps. This single step fixes most "cluttered" complaints.
2. **Align second (alignment, balance).** Commit to a dominant alignment and a grid; check that weights settle around the axis (see [Grid systems](../layout/grid-systems.md)).
3. **Rank third (contrast, scale, dominance).** Establish three to five levels; make level-one decisively dominant; give each level two independent differentiators.
4. **Systematise fourth (repetition, unity).** Freeze the vocabulary — one shape family, one spacing scale, one accent palette — and repeat component anatomy everywhere.
5. **Pace fifth (rhythm, movement, negative space).** Even out the intervals, open breathing room around the dominant element, and add one implied path from entry to goal.
6. **Break last (variety, emphasis).** Introduce one or two deliberate deviations, placed where meaning benefits, and verify they are the *only* deviations in view.

Each step inherits the previous one; reordering usually causes rework (ranking
before grouping produces hierarchy that proximity then dismantles).

## 6. Decision framework

Choosing which principles to emphasise depends on artefact type and message. The
table below is a synthesis of the cited sources and standard practice — context can
override any row.

| Context | Lead principles | De-emphasise | Rationale |
| --- | --- | --- | --- |
| Event poster / hero page | Dominance, emphasis, contrast, movement | Even balance, fine rhythm | One message, one glance, high energy |
| Form / data entry UI | Proximity, alignment, repetition | Variety, dynamic movement | Grouping and predictability reduce errors and load |
| Long document / report | Hierarchy, rhythm, repetition, alignment | Strong dominance, variety | Sustained reading needs calm, systematic structure |
| Brand kit system | Unity, repetition, proportion (systematic) | Variety at system level | Recognition across future artefacts |
| Dashboard / dense UI | Proximity, hierarchy, negative space | Decoration-driven contrast | Dense content stays scannable only when grouped and ranked |
| Luxury / premium print | Negative space, proportion, restraint in contrast | Repetition-heavy clutter | Emptiness and discipline signal quality |
| Playful campaign | Variety, movement, asymmetrical balance | Symmetry, uniform rhythm | Energy and surprise match the message |

When two principles seem to conflict (unity versus variety, repetition versus
emphasis), resolve by asking which serves the artefact's primary goal at that
moment, and let the losing principle yield locally rather than globally — one
exception beats a rewritten system.

## 7. Examples

**UI — booking form.** Proximity puts each label close to its input and groups
personal, payment and confirmation fields with generous gaps (NN/g cites chunking
twelve fields into three groups of four as the perceptible improvement) [accessed].
Alignment gives all inputs one left edge; repetition makes every input identical in
height and radius; contrast marks the primary button in brand colour while
destructive actions are the only red. Failure to avoid: uniform spacing everywhere,
which erases the groups.

**Poster — festival announcement.** Dominance: the artist's name at extreme scale,
isolated by space. Balance: asymmetrical — the name block counterweighted by a
small, dark, high-contrast ticket URL in the opposite corner. Movement: a diagonal
image band leads from name to date to URL. Variety: the only rotation in the
composition is the "sold out" sticker — the deviation itself is the message.
Document contexts invert these choices (calm rhythm, soft dominance,
alignment-driven hierarchy) because sustained reading rewards restraint.

**Document — event programme.** Repetition builds the system: every session entry
shares anatomy (time, title, speaker, room, in the same order, the same weights).
Rhythm comes from equal vertical beats; hierarchy from three type levels; negative
space between sessions does the grouping that rules would otherwise need to do.
Emphasis appears exactly once per page — the keynote — proving the system's power:
because everything else is uniform, one deviation carries all the meaning.

## 8. Common mistakes

- **Principle soup.** Applying all fourteen to every artefact instead of budgeting a few leads; the result is over-designed noise.
- **Emphasis inflation.** Making everything bold, large and coloured; emphasis is comparative and collapses when spent everywhere.
- **Near-alignment and near-equal spacing.** Almost-relationships read as error; snap to the system or move decisively away from it.
- **Grouping by assumption.** Believing content is "related" conceptually while presenting it with uniform spacing — the user only sees space.
- **Symmetry as default.** Centring everything to feel safe, which flattens hierarchy and wastes asymmetry's expressive range.
- **Variety as decoration.** Random deviations that carry no meaning, so the design is busy and still monotonous.
- **Ignoring proximity's negative half.** Related-action clusters separated too widely; unrelated buttons fused together.
- **Contrast without meaning.** Differences applied for liveliness rather than to signal a real category change.
- **Breaking principles accidentally.** Violations are legitimate only when deliberate and paid for; accidental violations simply read as mistakes.

## 9. Evaluation checklist

- State the artefact's single most important element; confirm it is decisively dominant (scale or value contrast clearly beyond every rival).
- Squint: do the masses balance around the intended axis? Does any region dominate so strongly that others vanish?
- Are related items visibly closer than unrelated ones everywhere — including in footers, forms and toolbars?
- Count the hierarchy levels; are there three to five, each distinguishable on two channels, with a clear first, second and third?
- Is the vocabulary repeated (shape, colour, spacing, component anatomy) so any fragment of the artefact reads as one family?
- Is there one deliberate deviation per view at most, and does it carry meaning?
- Do the intervals form a steady rhythm, or are they almost-but-not-quite equal?
- Is there an implied path from the entry point to the goal, without contradictory directions?
- Is every strong contrast attached to a real difference in function or category?

## 10. Related topics

- [Elements of design](elements-of-design.md) — the raw materials these principles arrange.
- [Gestalt and perception](gestalt-and-perception.md) — the perceptual mechanisms the principles exploit.
- [Composition](composition.md) — principles at the scale of the whole canvas: focal points, flow, tension.
- [Grid systems](../layout/grid-systems.md) — the structural implementation of alignment and proportion.
- [Typography fundamentals](../typography/typography-fundamentals.md) — hierarchy's most-used instrument.
- [Colour theory](../colour/colour-theory.md) — contrast's quantitative rules and palette systems.
- [Design quality framework](../evaluation/design-quality-framework.md) — scoring designs against these principles systematically.
- [Design critique](design-critique.md) — diagnosing which principle relationship has failed.

## 11. References

- Gordon, Kelley — "5 Principles of Visual Design in UX", Nielsen Norman Group, 2020 (scale, hierarchy, balance, contrast, Gestalt). https://www.nngroup.com/articles/principles-visual-design [accessed 2026-11-23]
- Harley, Aurora — "Proximity Principle in Visual Design", Nielsen Norman Group, 2020 (proximity overpowering similarity; form chunking; responsive cautions). https://www.nngroup.com/articles/gestalt-proximity [accessed 2026-11-23]
- Yablonski, Jon — Laws of UX (von Restorff / isolation effect among similar objects). https://lawsofux.com/ [accessed 2026-11-23]
- Arnheim, Rudolf — *Art and Visual Perception: A Psychology of the Creative Eye*, University of California Press, 1954/1974 (perceptual balance; visual weight) [canonical]
- Williams, Robin — *The Non-Designer's Design Book* (contrast, repetition, alignment, proximity — the "CRAP" teaching model) [canonical]
- Müller-Brockmann, Josef — *Grid Systems in Graphic Design*, Niggli, 1981 (systematic structure behind alignment and rhythm) [canonical]

Sections 3–6 are a synthesis of the sources above; where numeric guidance appears
(three to five hierarchy levels, three to five spacing steps), it is a conventional
starting point from professional practice, not a measured constant, and should be
validated against the artefact's own testing.
