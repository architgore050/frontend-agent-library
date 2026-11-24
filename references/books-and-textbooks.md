# Books and Textbooks

## 1. What is this file?

This file gives one full entry per core book from the mission's research list (§2.1, twenty items), plus the additional foundational texts the repository actually relies on. For each core book it records: full bibliographic data with a verification status, what the book covers, its key contributions to design practice, how a future agent can legitimately access it, and an honest note about what *this project* actually saw. It is the "library catalogue" layer; [Bibliography](bibliography.md) is the inventory layer, and [Source Accessibility](source-accessibility.md) classifies reading access in depth.

The point of the entry structure is reuse. When an agent needs the reasoning behind a rule — say, why a 12-column grid, or why one message per slide — the entry points to the book that supplies the reasoning and tells the agent exactly how far its knowledge of that book can be trusted.

A second use is scope control. Twenty books contain far more than any project needs; the "What it covers" and "Key contributions" lines let an agent decide which pages of which books are relevant before spending effort on access. If a task needs only the distinctive-assets argument, the entry for Sharp's book says so — no need to work through Wheeler's full process again. Conversely, when a task is process-heavy (building a brand kit from a fixed logo), the reading pathways in section 11 sequence the books so the agent reads in dependency order rather than alphabetically.

## 2. Why it matters

Books carry the load of *why* in this library. Web sources (standards, guidelines, research articles) are cited for checkable specifics; books are cited for principles, process and judgement. An agent that cites *Grid Systems* for "why margins must relate to the grid" is leaning on a canonical work it has not opened — legitimate, as long as the citation says so. An agent that invents a page number, or quotes a sentence it never saw, breaks the repository's research-integrity rule. These entries exist so that neither failure happens: they state precisely what was verified, what is general professional knowledge, and what must be checked before use.

They also protect against the opposite failure: over-claiming authority. Several of these books disagree with each other — Tschichold the modernist and Tschichold the classicist are different authors in spirit; Samara licenses what Müller-Brockmann forbids. The entries and the overlap table in section 10 record which voice the library follows for which purpose, so a future agent inherits a position rather than a contradiction.

## 3. Access status — the honesty statement

**No book in this list was accessed as full text during this project.** No full-text access is claimed anywhere in the repository. What this project actually saw, on 2026–11–24 (initial build plus a second verification pass the same day), were publisher catalogue pages, retailer listings, review pages and academic citation entries surfaced by web search — plus one publisher product page fetched in full: Princeton Architectural Press's page for *Thinking with Type* (the fetch attempt on Wiley's catalogue page for *Designing Brand Identity* returned HTTP 403, so Wiley data remains search-verified only). Fifteen of the twenty core books now have at least their publisher, edition or year confirmed against such results; the remainder are recorded from general professional knowledge and marked accordingly.

| # | Book | Data verified this session | Tag for this project |
| --- | --- | --- | --- |
| 1 | Wheeler & Meyerson, *Designing Brand Identity* (6th ed.) | Yes — Wiley catalogue page, ISBNs | [canonical], data [search-verified] |
| 2 | Olins, *The Brand Handbook* | Yes — academic citations (T&H, 2008) | [canonical], data [search-verified] |
| 3 | Aaker, *Building Strong Brands* | Yes — academic citations (Free Press, 1996) | [canonical], data [search-verified] |
| 4 | Rossman & Duerden, *Designing Brand Experiences* | Corrected — their book is *Designing Experiences*, Columbia Business School Publishing, 2019 (JSTOR entry, review listings); no Routledge title surfaced | [canonical], data [search-verified] |
| 5 | Neumeier, *The Brand Gap* | Year and subtitle yes; publisher canonical | [canonical] |
| 6 | Lupton, *Thinking with Type* (3rd ed.) | Yes — PA Press product page fetched in full (ISBN 9781797226828, 256 pp, 12 March 2024) | [canonical], data [accessed] |
| 7 | Bringhurst, *The Elements of Typographic Style* | Yes — Typographica review, 1st-ed ISBN | [canonical], data [search-verified] |
| 8 | Müller-Brockmann, *Grid Systems* | Yes — Niggli catalogue page, ISBN | [canonical], data [search-verified] |
| 9 | Samara, *Making and Breaking the Grid* | Edition existence yes; publisher canonical | [canonical] |
| 10 | Tschichold, *The New Typography* | No (1928 original via repo citations) | [canonical] |
| 11 | Meggs & Purvis, *Meggs' History of Graphic Design* (7th ed.) | Yes — ISBN via listings; 7th-edition co-authors Sandra Maxa and Mark Sanders confirmed | [canonical], data [search-verified] |
| 12 | Lupton (ed.), *Graphic Design Thinking* | Yes — PA Press product page (2011, 184 pp) | [canonical], data [search-verified] |
| 13 | Lupton & Phillips, *Graphic Design: The New Basics* | No (repo citations, PA Press 2008) | [canonical] |
| 14 | McAlhone & Stuart, *A Smile in the Mind* | Revision year yes — Phaidon 2016; first-edition year conflicting across listings (1996 canonical; a 2001 US printing seen) | [canonical], data [search-verified] |
| 15 | Lidwell, Holden & Butler, *Universal Principles of Design* | Yes — retailer listing, ISBN | [canonical], data [search-verified] |
| 16 | Rams, *Ten Principles for Good Design* | Primary source is the Vitsoe page (fetched by the history files, 2026-11-23) | [accessed] via Vitsoe; book sources [canonical] |
| 17 | Norman, *The Design of Everyday Things* | Revised 2013 edition confirmed | [canonical], data [search-verified] |
| 18 | Brown, *Change by Design* | Year and subtitle confirmed | [canonical], data [search-verified] |
| 19 | Fletcher, *The Art of Looking Sideways* | Year via repo citation (Phaidon, 2001) | [canonical] |
| 20 | Munari, *Design as Art* | No | [canonical], data unverified |

**Access tiers.** Following the mission's source-accessibility classes, the books in this file sit in tier 2 or 3 — "authorised previews" (publisher sample pages, Google Books previews) and "publisher descriptions" — never tier 1 ("full-text open access"). The only genuinely open-access items in the wider corpus are: the Vitsoe ten-principles page (CC BY-NC-ND 4.0), Massimo Vignelli's *The Vignelli Canon* (free PDF from RIT's Vignelli Center), Brad Frost's *Atomic Design* (published free-to-read by its author), and W3C standards.

**What "verified" concretely meant this session.** For the verified rows, the evidence was: one publisher product page fetched in full (PA Press, *Thinking with Type* third edition — the only publisher page this build opened directly; the Wiley catalogue page for Wheeler and Meyerson returned HTTP 403 to the fetcher and therefore stays search-verified); catalogue and retailer listings for the rest. That listing layer comprises: Wiley catalogue pages for Wheeler and Meyerson's sixth edition and Meggs' seventh edition (ISBNs in the page addresses); the Niggli catalogue page for *Grid systems*; Typographica's review page for Bringhurst's version 4.0; retailer listings supplying ISBN-10s for *Thinking with Type*, *Universal Principles of Design* and *Grid systems*; a library catalogue record for Samara's third edition; O'Reilly listings confirming the *Meggs'* seventh-edition ISBN and its additional co-authors Sandra Maxa and Mark Sanders; PA Press's product page for *Graphic Design Thinking* (publication date 09/01/2011, 184 pages); JSTOR's catalogue entry and trade-review listings fixing Rossman and Duerden's book as *Designing Experiences* (Columbia Business School Publishing, 2019); retailer listings for the 2016 revised and expanded *A Smile in the Mind*; a design-school notice for the *Meggs'* seventh edition; and academic citation pages (a Sage book's bibliography and a Lund University thesis) pinning *The Brand Handbook* to Thames & Hudson 2008 and *Building Strong Brands* to Free Press 1996. That is the entire evidential base: catalogue metadata, not content.

**A caution on search results.** General web searches for several of these books surface full-text PDF uploads on third-party sites. These are unauthorised copies; this project did not use them, and future agents must not use or cite them as access routes. Legitimate routes are the publisher pages, authorised previews, and public or academic libraries — the "Legitimate access" line in every entry below.

**Re-verification cadence.** Catalogue metadata is stable, but editions change: a "verify before citing" flag in this file is an instruction, not decoration. An agent working on a task that depends on one of the flagged books should spend one lookup on the publisher page and update the entry, rather than propagating the flag forward.

## 4. Core books — branding and visual identity

The branding canon splits into process (Wheeler), identity management (Olins), equity economics (Aaker), experience (Rossman and Duerden) and judgement (Neumeier). An agent extending a fixed logo into a brand kit needs the first and last most urgently; the middle three explain *why* the kit must govern architecture, touchpoints and personality.

### 1. Designing Brand Identity — Alina Wheeler and Rob Meyerson

- **Bibliographic data.** Alina Wheeler; sixth edition co-authored with Rob Meyerson. *Designing Brand Identity: A Comprehensive Guide to the World of Brands and Branding*, 6th ed., Wiley, ISBN 978-1-119-98482-5 (a companion-format ISBN 978-1-119-98481-8 also appears on the catalogue page). First published 2003; the sixth edition is dated 2024 by trade citations and the publisher page lists current formats. [search-verified 2026-11-24 — Wiley catalogue page, retailer listing]
- **What it covers.** The branding process as a sequence of phases and deliverables: strategy, identity design, brand architecture, governance and management, with case studies throughout. The book is known for deconstructing branding into a universal, phased methodology with named deliverables.
- **Key contributions.** Process discipline for identity work — it gave the profession a shared vocabulary for phases (research → strategy → design → launch → governance) and for artefacts (brand guidelines, architecture diagrams). The repository's branding domain leans on it for the strategy-to-identity sequence and the governance vocabulary.
- **Legitimate access.** Wiley catalogue page: https://www.wiley.com/en-us/shop/graphic-design/designing-brand-identity-a-comprehensive-guide-to-the-world-of-brands-and-branding-6th-edition-p-9781119984825 [search-verified 2026-11-24]; authorised previews via Google Books; public and academic libraries (WorldCat).
- **Access note for this project.** [canonical] — catalogue-level verification only. Cited in eight domain files; see [Bibliography](bibliography.md) §4.1.

### 2. The Brand Handbook — Wally Olins

- **Bibliographic data.** Wally Olins, *The Brand Handbook*, Thames & Hudson, London, 2008. [search-verified 2026-11-24 — multiple academic citation entries]. Olins (1930–2014) also wrote *Corporate Identity* (Phaidon) and *On Brand* (Thames & Hudson, 2004) — both cited by the repository. [canonical]
- **What it covers.** How organisations build and manage brand and corporate identity, structured around Olins' model of identity working through product, environment, communication and behaviour — the "identity vectors" the repository's brand-fundamentals file attributes to him.
- **Key contributions.** The separation of *identity* (what the organisation is and does) from *image* (what audiences perceive), and the argument that identity is managed through behaviour and environment as much as through communication. This distinction underlies the repository's treatment of brand governance.
- **Legitimate access.** Thames & Hudson's catalogue (publisher site); authorised previews; libraries.
- **Access note for this project.** [canonical] — year and publisher confirmed only via citation listings; no content accessed.

### 3. Building Strong Brands — David A. Aaker

- **Bibliographic data.** David A. Aaker, *Building Strong Brands*, The Free Press, New York, 1996; a UK printing under Simon & Schuster, London, 2002, appears in academic citations. [search-verified 2026-11-24 — academic citation entries]
- **What it covers.** Brand equity as an asset to be built and measured: brand identity planning, brand positioning, brand architecture (branded house versus house of brands), and the brand-equity model Aaker developed across his series (*Managing Brand Equity*, 1991; *Building Strong Brands*, 1996; *Brand Leadership*, with Joachimsthaler, 2000 — the wider series is general professional knowledge).
- **Key contributions.** Made "brand equity" an operating concept: brand awareness, perceived quality, associations and loyalty as measurable assets. The repository's brand-architecture file leans on Aaker's branded-house / house-of-brands / endorsed spectrum.
- **Legitimate access.** Simon & Schuster catalogue; authorised previews; libraries. A published academic review of the earlier *Managing Brand Equity* (David C. Smith, *Journal of Marketing Research*) is indexed at https://www.jstor.org/stable/1252048 [accessed, carried over from brand-fundamentals].
- **Access note for this project.** [canonical] — citation-level verification only.

### 4. Designing Brand Experiences — J. Robert Rossman and Mathew D. Duerden

- **Bibliographic data.** The mission lists this as *Designing Brand Experiences*, Routledge. Verification searches on 2026-11-24 found no Routledge book by these authors; the book the listings consistently attribute to J. Robert Rossman and Mathew D. Duerden is *Designing Experiences*, Columbia Business School Publishing, 2019 (indexed at https://www.jstor.org/stable/10.7312/ross19168 and reviewed in *strategy+business*, November 2019). [search-verified 2026-11-24 — JSTOR entry and review listings; the mission's title appears to be a variant — confirm the exact title before citing either form]
- **What it covers.** Brand experience as a designed outcome across the customer journey: touchpoints, experience platforms and the link between brand strategy and the experience an organisation actually delivers.
- **Key contributions.** Shifts the unit of branding from the artefact (logo, guideline) to the experience (sequence of touchpoints), giving teams a way to audit whether the designed experience matches the brand promise.
- **Legitimate access.** Columbia Business School Publishing / Columbia University Press catalogue (cup.columbia.edu); JSTOR's catalogue entry; libraries.
- **Access note for this project.** [canonical] — not yet cited by any domain file; introduced by this file for journey-based brand work. Catalogue data is search-verified; no content accessed.

### 5. The Brand Gap — Marty Neumeier

- **Bibliographic data.** Marty Neumeier, *The Brand Gap: How to Bridge the Distance Between Business Strategy and Design*, New Riders, 2003 (revised editions followed; the third-edition retitling *The Brand Flip* is separate). [search-verified 2026-11-24 — year and subtitle via academic citations; publisher canonical]
- **What it covers.** A short argument book: branding is not a logo, an identity system or a product — a brand is a person's gut feeling about a product, service or organisation — and companies fail when business strategy and design do not work as one collaborative discipline.
- **Key contributions.** The "brand is a gut feeling" definition, the three little questions (who are you, what do you do, why does it matter), and the charter-for-collaboration framing between strategists and designers. The repository quotes its logo/brand distinction via a Goodreads-indexed quote (https://www.goodreads.com/quotes/10836230-a-brand-is-not-a-logo-a-brand-is-not) [search-verified, carried over].
- **Legitimate access.** Publisher (Peachpit/New Riders) catalogue; authorised previews; libraries.
- **Access note for this project.** [canonical] — the gut-feeling definition is professional common knowledge; the Goodreads quote is the only directly sighted wording.

## 5. Core books — typography and editorial design

Here the canon runs from manifesto (Tschichold) through craft bible (Bringhurst) to contemporary teaching text (Lupton), with Müller-Brockmann supplying the structural and Samara the postmodern counterpoint. The library's typography rules trace to these five in a traceable way: hierarchy and classification to Lupton, setting and measure to Bringhurst, asymmetry and system to Tschichold and Müller-Brockmann, and deviation-as-method to Samara.

### 6. Thinking with Type — Ellen Lupton

- **Bibliographic data.** Ellen Lupton, *Thinking with Type: A Critical Guide for Designers, Writers, Editors, & Students*. First edition 2004; revised and expanded third edition, Princeton Architectural Press (a division of Chronicle Books), released 12 March 2024. ISBN 9781797226828 (ISBN-10 1797226827); 256 pages, paperback, list price USD 29.95. The publisher page states the third edition adds 32 pages of new content — more typefaces, sections on diverse writing systems, and topics including variable fonts, readability and accessibility. [accessed 2026-11-24 — publisher product page fetched in full: https://papress.com/products/thinking-with-type-3-edition]
- **What it covers.** Typography in three parts — Letter, Text, Grid — moving from letterform anatomy through text setting to grid organisation, with critical context on how typographic choices produce meaning, not just legibility. The first edition has been widely adopted in design programmes since 2004 (publisher page wording).
- **Key contributions.** A teachable structure for typography that pairs craft rules (classification, measure, leading, hierarchy) with critical reading. The repository's typography domain uses it as its spine: six files cite it for classification, pairing, setting and hierarchy reasoning.
- **Legitimate access.** Publisher product page: https://papress.com/products/thinking-with-type-3-edition [search-verified 2026-11-24]; authorised previews; libraries.
- **Access note for this project.** [canonical] for content; catalogue data [accessed] via the fetched PA Press page. Cited in seven typography files plus evaluation/design-quality-framework.

### 7. The Elements of Typographic Style — Robert Bringhurst

- **Bibliographic data.** Robert Bringhurst, *The Elements of Typographic Style*, Hartley & Marks. First edition 1992 (ISBN 0-88179-133-4); fourth edition "version 4.0" reviewed by Typographica in February 2013; a "version 4.1" printing also appears in listings. Roughly 350 pages in later printings. [search-verified 2026-11-24 — Typographica review, library and retailer listings]
- **What it covers.** Typographic craft as a single coherent system: page proportions and shapes, choosing and combining typefaces, shaping the page and the line, rhythm and proportion, and the "working principles" that give the book its authority among designers.
- **Key contributions.** The idea of *typographic style* as disciplined craft — measure, hanging punctuation, colour of the text block — plus memorable working principles that the typography domain cites for craft rules (typesetting, hierarchy, font pairing).
- **Legitimate access.** Hartley & Marks catalogue; authorised previews; libraries. The Typographica review is a reliable public description: https://typographica.org/typography-books/the-elements-of-typographic-style-4th-edition [search-verified 2026-11-24].
- **Access note for this project.** [canonical] — craft rules in the repository are attributed to the work without page numbers.

### 8. Grid Systems in Graphic Design — Josef Müller-Brockmann

- **Bibliographic data.** Josef Müller-Brockmann, *Grid systems in graphic design* (German: *Rastersysteme für die visuelle Gestaltung*), Verlag Niggli, 1981; bilingual German/English handbook for graphic designers, typographers and exhibition designers. ISBN 978-3-7212-0145-1 (ISBN-10 3-72120-145-0). [search-verified 2026-11-24 — Niggli catalogue page and retailer listings]
- **What it covers.** The Swiss-school grid method in full: why the grid exists, the arithmetic of column and row systems (including the widely used 12-column grid), typography and photography on the grid, and worked systems for books, posters and exhibitions.
- **Key contributions.** The canonical statement of grid thinking — that systematic spacing, a defined type-area and modular organisation produce objective, communicable design. It is the repository's most-cited book: twelve files across layout, foundations, applications, branding and history rely on it.
- **Legitimate access.** Publisher catalogue page: https://niggli.ch/en/products/rastersysteme-fur-die-visuelle-gestaltung [search-verified 2026-11-24]; authorised previews; libraries.
- **Access note for this project.** [canonical] — no content accessed; all grid arithmetic in the library is labelled as conventional practice attributed to the work.

### 9. Making and Breaking the Grid — Timothy Samara

- **Bibliographic data.** Timothy Samara, *Making and Breaking the Grid: A Graphic Design Layout Workshop*, Rockport Publishers; a third edition exists (library catalogue listing). First edition 2003 (Rockport, general professional knowledge). [search-verified 2026-11-24 — edition existence; publisher and first-edition year canonical]
- **What it covers.** A two-part layout workshop: first understanding and working with the traditional typographic grid, then deconstructing it — the "breaking" half that legitimises deliberate violations as design moves rather than accidents.
- **Key contributions.** Bridges the classical grid (Müller-Brockmann) and postmodern deconstruction, with project analyses showing *how* layouts succeed or fail. The repository's grid-systems file cites it for the break-the-grid vocabulary.
- **Legitimate access.** Publisher (Rockport/Quarto) catalogue; authorised previews; libraries.
- **Access note for this project.** [canonical] — catalogue-level verification only.

### 10. The New Typography — Jan Tschichold

- **Bibliographic data.** Jan Tschichold, *Die neue Typographie*, Bildungsverband der Deutschen Buchdrucker, Leipzig, 1928; English: *The New Typography: A Handbook for Modern Designers*, translated by Ruari McLean, University of California Press, 1995. Tschichold's later *The Form of the Book* (Hartley & Marks, English ed. 1991), which contains the Penguin Composition Rules, is also cited by the repository. [canonical; 1928 original and translations via repository citations]
- **What it covers.** The 1928 manifesto of modern typography: asymmetric layout, sans-serif working type, functionalist standards — written at the height of the New Typography movement. The later Tschichold (Form of the Book) represents his classical turn.
- **Key contributions.** Defined modern typographic modernism as rules, not taste: clarity, function, standardisation. The repository's visual-styles and editorial-design files use it as the historical anchor for asymmetric modern layout.
- **Legitimate access.** University of California Press catalogue; authorised previews; libraries.
- **Access note for this project.** [canonical] — the 1928 date and the McLean translation are general professional knowledge confirmed by repository citations; no content accessed.

## 6. Core books — graphic design theory and practice

These five supply the shared reference layer: the historical survey (Meggs), the ideation method (Lupton), the fundamentals vocabulary (Lupton and Phillips), the wit strategy (McAlhone and Stuart) and the cross-disciplinary principle lookup (Lidwell and colleagues). They are the books an agent should reach for when a question is "what is this called and why does it work?" rather than "what is the rule?".

### 11. Meggs' History of Graphic Design — Philip B. Meggs and Alston W. Purvis

- **Bibliographic data.** Philip B. Meggs; from later editions with Alston W. Purvis; the seventh edition additionally credits Sandra Maxa and Mark Sanders (confirmed in O'Reilly and retailer listings). *Meggs' History of Graphic Design*, 7th ed., Wiley, ISBN 9781119743293; earlier editions from Wiley across the 1990s–2010s. [search-verified 2026-11-24 — Wiley catalogue page, O'Reilly listings and a faculty notice at Maryland Institute College of Art, https://www.mica.edu/art-articles/details/mica-faculty-authors-meggs-history-of-graphic-design-7th-edition]
- **What it covers.** The standard English-language survey of graphic design: writing systems and early printing (Gutenberg's press, the 1455 Bible), the Industrial Revolution, the modern movements (Bauhaus, New Typography, Swiss/International Style), postwar American design and the digital era.
- **Key contributions.** Established graphic design history as a taught discipline with a periodised narrative. The repository's history domain follows its era framing; the seventh edition reportedly departs from strict chronology to help students reason across periods.
- **Legitimate access.** Wiley catalogue page: https://www.wiley.com/en-us/shop/graphic-design/meggs'-history-of-graphic-design-7th-edition-p-9781119743293 [search-verified 2026-11-24]; authorised previews; libraries.
- **Access note for this project.** [canonical] — narrative attributions in the history files are general knowledge, not quotes.

### 12. Graphic Design Thinking — Ellen Lupton

- **Bibliographic data.** Ellen Lupton (ed.), *Graphic Design Thinking: Beyond Brainstorming*, Princeton Architectural Press (Design Briefs series, published in collaboration with MICA), publication date 09/01/2011, 184 pages, 7 × 8.5 in. [search-verified 2026-11-24 — publisher product page https://papress.com/products/graphic-design-thinking-beyond-brainstorming and retailer listings]
- **What it covers.** Structured ideation for design work: question storming, concept matrixes, visual brainstorms, critiques and prototyping — techniques presented as repeatable workshop methods with case studies.
- **Key contributions.** Makes ideation teachable as design method rather than inspiration. It complements *Thinking with Type* (craft) and the repository's methodology domain (process): the ideation file's technique catalogue overlaps it conceptually.
- **Legitimate access.** PA Press catalogue; authorised preview; libraries.
- **Access note for this project.** [canonical] — no content accessed; do not quote or number techniques from memory.

### 13. Graphic Design: The New Basics — Ellen Lupton and Jennifer Cole Phillips

- **Bibliographic data.** Ellen Lupton and Jennifer Cole Phillips, *Graphic Design: The New Basics*, Princeton Architectural Press, 2008 (a second edition appeared later — general professional knowledge). [canonical — publisher and year via repository citations]
- **What it covers.** Design fundamentals rebuilt for design education: point, line, plane; scale, rhythm, balance; figure–ground, texture, transparency, layering, modularity, grids — each demonstrated with contemporary student and professional work.
- **Key contributions.** Replaced the classical "elements and principles" list with a studio-tested vocabulary. The repository's foundations domain (elements-of-design, composition) cites it for the point–line–plane progression and figure–ground.
- **Legitimate access.** PA Press catalogue; authorised previews; libraries.
- **Access note for this project.** [canonical] — vocabulary attributions only.

### 14. A Smile in the Mind — Beryl McAlhone and David Stuart

- **Bibliographic data.** Beryl McAlhone and David Stuart, *A Smile in the Mind: Witty Thinking in Graphic Design*, Phaidon. First edition 1996 (general professional knowledge; listings also show a Phaidon Inc Ltd printing dated September 2001, so treat the first-edition year as canonical rather than verified); Revised and Expanded Edition, Phaidon Press, 2016. [search-verified 2026-11-24 — revised edition via retailer listings; first-edition year canonical]
- **What it covers.** "Witty thinking" in graphic design: how ideas that play with language, images and expectations create memorable communication — one-liners, visual puns, double meanings — catalogued across international work.
- **Key contributions.** Legitimised wit as a *strategic* device, not decoration: the smile that signals an idea was understood. Relevant to the repository's graphic-language and logo-systems files when a fixed logo carries wordplay or double meaning.
- **Legitimate access.** Phaidon catalogue; authorised preview; libraries.
- **Access note for this project.** [canonical] — no content accessed.

### 15. Universal Principles of Design — William Lidwell, Kritina Holden and Jill Butler

- **Bibliographic data.** William Lidwell, Kritina Holden and Jill Butler, *Universal Principles of Design*, Rockport Publishers. First edition 2003 (general professional knowledge); *Revised and Updated* edition "125 Ways to Enhance Usability, Influence Perception, Increase Appeal…" ISBN 9781592535873 (ISBN-10 1592535879); an "Updated and Expanded Third Edition" ("200 ways") also appears in listings. [search-verified 2026-11-24 — retailer listings]
- **What it covers.** A cross-disciplinary encyclopaedia of design principles drawn from psychology, ergonomics and design practice — one principle per entry (Gestalt laws, Hick's law, Fitts's law, affordance, von Restorff effect, golden ratio, Ockham's razor) with a definition, evidence and usage guidance.
- **Key contributions.** Gave practitioners a one-page-per-principle reference that connects visual decisions to cognitive science. The repository cites its principle names via Laws of UX and NN/g research rather than the book itself; the books file records it as the print companion.
- **Legitimate access.** Publisher (Rockport/Quarto) catalogue; retailer listing https://www.amazon.com/Universal-Principles-Design-Revised-Updated/dp/1592535879 [search-verified 2026-11-24]; libraries.
- **Access note for this project.** [canonical] — principle definitions in the repository come from fetched web sources, not from this book.

## 7. Core books — design philosophy and creative thinking

The final five are attitude books: Rams for quality criteria, Norman for user-centred evaluation, Brown for organisational process, Fletcher and Munari for ways of seeing. They justify the library's evaluation checklists and its insistence that design reasoning be explicit rather than taste-based.

### 16. Dieter Rams — Ten Principles for Good Design

- **Bibliographic data.** Not a single book but a canonical statement, published and maintained by Vitsoe at https://www.vitsoe.com/us/about/good-design (licensed CC BY-NC-ND 4.0; fetched by the history files on 2026-11-23, including the phrasings "is my design good design?" and "Less, but better"). Book treatments include *Less and More: The Design Ethos of Dieter Rams*, Gestalten, 2015 [canonical]. [accessed via Vitsoe; books canonical]
- **What it covers.** Rams' ten criteria for good design: innovative, useful, aesthetic, understandable, unobtrusive, honest, long-lasting, thorough to the last detail, environmentally friendly, as little design as possible — formulated from his Braun work and published with Vitsoe's context on his career.
- **Key contributions.** The most-quoted quality framework in product and visual design; "less, but better" as an operating principle. The repository's design-philosophies and design-quality-framework files use it as their evaluation spine.
- **Legitimate access.** The Vitsoe page is openly licensed and directly readable; *Less and More* via Gestalten (gestalten.com) and libraries.
- **Access note for this project.** [accessed] for the Vitsoe page (by the history-domain agents); [canonical] for the book treatments.

### 17. The Design of Everyday Things — Don Norman

- **Bibliographic data.** Donald A. Norman, *The Design of Everyday Things*, Basic Books; first edition 1988 (as *The Psychology of Everyday Things*), revised and expanded edition 2013. [search-verified 2026-11-24 — revised edition confirmed in listings and citations; publisher and 1988 first edition canonical]
- **What it covers.** Why everyday objects fail their users and what good design does instead: affordances, signifiers, mapping, feedback, conceptual models, the seven stages of action, and the psychology of error. The 2013 revision updates the vocabulary for digital interfaces.
- **Key contributions.** Put the user's mental model at the centre of design evaluation. The repository's ux/ui-fundamentals and information-hierarchy files lean on its vocabulary for affordances and feedback.
- **Legitimate access.** Publisher (Basic Books) catalogue; authorised previews; libraries.
- **Access note for this project.** [canonical] — terminology attribution only.

### 18. Change by Design — Tim Brown

- **Bibliographic data.** Tim Brown, *Change by Design: How Design Thinking Transforms Organizations and Inspires Innovation*, HarperBusiness, 2009 (the UK subtitle variant "How Design Thinking Creates New Alternatives for Business and Society" also appears in citations). [search-verified 2026-11-24 — year and subtitles via academic citations; publisher canonical]
- **What it covers.** Design thinking as an organisational method from IDEO's CEO: the inspiration–ideation–implementation arc, human-centred observation, prototyping culture, and the difference between designing products and designing the systems around them.
- **Key contributions.** Made "design thinking" the standard bridge from studio practice to business process. The repository's design-thinking file and the design-philosophies file cite it for the human-centred framing.
- **Legitimate access.** Publisher (HarperCollins) catalogue; authorised previews; libraries.
- **Access note for this project.** [canonical] — process framing attribution only.

### 19. The Art of Looking Sideways — Alan Fletcher

- **Bibliographic data.** Alan Fletcher, *The Art of Looking Sideways*, Phaidon, 2001. [canonical — year via repository citations]
- **What it covers.** A vast notebook-style work of lateral thinking: images, anecdotes, wordplay and observations assembled to demonstrate how designers notice, connect and reframe. Not a manual — an argument about attention played out in pages.
- **Key contributions.** Models creative receptiveness: the designer's primary instrument is a way of seeing. The repository's ideation and moodboards files borrow its spirit (collection, juxtaposition) rather than specific content.
- **Legitimate access.** Phaidon catalogue; authorised preview; libraries.
- **Access note for this project.** [canonical] — no content accessed; do not cite chapter specifics.

### 20. Design as Art — Bruno Munari

- **Bibliographic data.** Bruno Munari, *Design as Art*; English edition published by Penguin (Penguin Classics reprint, 2009; first English appearance in the early 1970s) — **edition years from general professional knowledge; verify on the publisher page before citing**. Original Italian essays collected from the 1960s–70s. [canonical]
- **What it covers.** Munari's essays arguing that design is an art of daily life — on form, objects, messages, and the "designer of the second kind" who designs for the many rather than the few.
- **Key contributions.** Reframed the designer as a communicator serving everyone, not a fine artist serving taste — an early statement of the democratising spirit behind this repository's own mission.
- **Legitimate access.** Publisher catalogue; authorised preview; libraries.
- **Access note for this project.** [canonical] — no content accessed.

## 8. Additional foundational texts

Beyond the twenty mission-core books, the repository relies on these works, discovered during domain writing. The list was assembled the same way as the bibliography: extracting italic-marked titles from every domain file's reference section, deduplicating, and keeping the works that do real argumentative work (a framework, a vocabulary, a set of rules) rather than one-off mentions. Data provenance follows the same rules: repository-cited years and publishers are [canonical] unless noted. The full set of additional texts is inventoried in [Bibliography](bibliography.md) §4; the table below lists the ones worth an agent's attention first.

| Author(s) | Work | Publisher / year (status) | What the library uses it for |
| --- | --- | --- | --- |
| Jacques Bertin | *Sémiologie Graphique* | 1967; English *Semiology of Graphics*, 1983 [canonical] | Visual variables — the basis of the dataviz domain |
| Edward Tufte | *The Visual Display of Quantitative Information* | Graphics Press, 1983; 2nd ed. 2001 [canonical] | Chart junk, data-ink, lie factor |
| Edward Tufte | *Envisioning Information* | Graphics Press, 1990 [canonical] | Layering, small multiples, colour in information design |
| Edward Tufte | *Visual Explanations*; *Beautiful Evidence* | Graphics Press, 1997; 2006 [canonical] | Explanation structure; corruption-of-evidence caution |
| Rudolf Arnheim | *Art and Visual Perception* | University of California Press, 1954/1974 [canonical] | Perceptual weight, balance, gestalt grounding |
| Rudolf Arnheim | *The Power of the Center* | University of California Press, 1982 [canonical] | Compositional centrality |
| Margaret Mark; Carol S. Pearson | *The Hero and the Outlaw* | McGraw-Hill, 2001 [canonical] | The twelve brand archetypes behind brand-personality |
| Byron Sharp | *Building Distinctive Brand Assets* | Oxford University Press, 2018 [canonical] | Ownable distinctive assets (logo, colour, type as brand property) |
| Kevin Lane Keller | *Strategic Brand Management* | Pearson [canonical] | Customer-based brand equity pyramid |
| David A. Aaker | *Managing Brand Equity* | Free Press, 1991 [canonical] | Equity model predecessor; cited with its JMR review |
| Al Ries; Jack Trout | *Positioning: The Battle for Your Mind* | McGraw-Hill, 1981 [canonical] | Positioning as owning a slot in the prospect's mind |
| Wally Olins | *On Brand*; *Corporate Identity* | Thames & Hudson 2004; Phaidon [canonical] | Identity vectors; identity versus image |
| Robin Williams | *The Non-Designer's Design Book* | Peachpit Press [canonical] | CRAP teaching model (contrast, repetition, alignment, proximity) |
| Nancy Duarte | *slide:ology*; *Resonate* | O'Reilly 2008; Wiley 2010 [canonical] | Slide systems; audience-first message hierarchy |
| Garr Reynolds | *Presentation Zen* | New Riders [canonical] | Restraint and one-message slides |
| Massimo Vignelli | *The Vignelli Canon* | Free PDF, RIT Vignelli Center [canonical; URL carried over] | Grids, margins, "design is one" discipline |
| Paul Rand | *Thoughts on Design* | 1946 [canonical] | Design as problem-solving, not decoration |
| Milton Glaser | *Drawing is Thinking* | 2008 [canonical] | Drawing as reasoning |
| Otl Aicher | *Typographie* | 1988 [canonical] | Typographic systems; Munich 1972 pictograms elsewhere |
| Emil Ruder | *Typographie* | Niggli [canonical] | Swiss typographic craft (spacing, rhythm) |
| Erik Spiekermann; E. M. Ginger | *Stop Stealing Sheep & Find Out How Type Works* | Adobe Press, 3rd ed. 2013 [canonical] | Typeface personality, family thinking |
| Jan Tschichold | *The Form of the Book* | Hartley & Marks, English ed. 1991 [canonical] | Page proportions, margin canons, Penguin Composition Rules |
| Brad Frost | *Atomic Design* | 2016, free-to-read by the author [canonical] | Component inventories, system thinking |
| Steve Krug | *Don't Make Me Think* | [canonical] | Usability judgement shortcuts |
| Ben Shneiderman | *Designing the User Interface* | [canonical] | The eight golden rules lineage |
| Jakob Nielsen | *Usability Engineering* | [canonical] | Heuristic evaluation lineage |
| Louis Rosenfeld; Peter Morville | *Information Architecture for the World Wide Web* | O'Reilly [canonical] | IA foundations |
| Peter Morville | *Ambient Findability* | O'Reilly, 2005 [canonical] | Findability as IA outcome |
| Dan Saffer | *Microinteractions* | O'Reilly, 2013 [canonical] | Trigger/rules/feedback/loop structure |
| Ethan Marcotte | *Responsive Web Design* | A Book Apart, 2011 [canonical] | Fluid grids, flexible images, media queries |
| Luke Wroblewski | *Mobile First* | A Book Apart, 2011 [canonical] | Mobile-first prioritisation |
| Barbara Minto | *The Pyramid Principle* | 1985 [canonical] | BLUF / pyramid message ordering |
| Alex Osborn; Bob Eberle | *Applied Imagination*; *SCAMPER* | 1953; [canonical] | Brainstorming rules; the SCAMPER checklist |
| Josef Albers | *Interaction of Color* | Yale University Press, 1963 [canonical] | Relativity of colour perception |
| Johannes Itten | *The Art of Color* | Van Nostrand Reinhold [canonical] | Colour contrast types |
| Eva Heller | *Wie Farben wirken* | Reinbek, 1989 [canonical] | Cultural colour associations |
| John Berger; Susan Sontag; Roland Barthes | *Ways of Seeing*; *On Photography*; *Rhetoric of the Image* | 1972; 1977; 1964 [canonical] | Image meaning and audience framing |
| Kevin Lynch; Arthur & Passini | *The Image of the City*; *Wayfinding* | 1960; 1992 [canonical] | Legibility and decision-point wayfinding |

Books marked [canonical] carry general professional knowledge only — attribute by author and title, never by page number or quote, unless the page itself is fetched in a future session.

Four of the additional texts deserve fuller treatment, because whole domain files lean on their frameworks:

**Jacques Bertin, *Semiology of Graphics*.** Bertin's contribution is the visual-variable system — position, size, value, texture, colour, orientation, shape — as a grammar for encoding data. The data-visualisation file's chart-selection logic and the diagrams file's encoding choices are applications of this grammar. Access: the 1983 English translation (Esri Press reissue) via libraries; no content accessed this project. [canonical]

**Edward Tufte, *The Visual Display of Quantitative Information* and successors.** Tufte supplied the vocabulary of data-ink, chart junk, small multiples, the lie factor and the argument that graphical excellence is the well-designed presentation of interesting data. The presentation-checklist and data-visualisation files quote none of it verbatim but apply its concepts throughout. The author's own overview page, https://www.edwardtufte.com/books/ [canonical, carried over], is the legitimate description source. [canonical]

**Josef Albers, *Interaction of Color*.** The relativity of colour — the same colour reads differently against different surroundings, and colour is the most relative medium in art — grounds the palette-development file's insistence on testing palettes in context rather than judging swatches in isolation. Access: Yale University Press; an interactive edition exists (verify before citing). [canonical]

**Margaret Mark and Carol S. Pearson, *The Hero and the Outlaw*.** The twelve-archetype framework (innocent, explorer, sage, hero, outlaw, magician, regular guy, lover, jester, caregiver, creator, ruler) that brand-personality uses for personality mapping. Access: McGraw-Hill catalogue and libraries. [canonical]

**Johannes Itten, *The Art of Color*.** Itten's contribution is the seven contrast types (hue, light–dark, cold–warm, complementary, simultaneous, saturation, extension) and the idea that colour harmony can be studied systematically rather than felt intuitively. The palette-development file uses the contrast vocabulary when auditing whether a palette relies on one mechanism too heavily. Access: Van Nostrand Reinhold editions via libraries; the book is out of print in places, so library copy is the realistic route. [canonical]

**Robin Williams, *The Non-Designer's Design Book*.** Its four-part teaching model — contrast, repetition, alignment, proximity (the "CRAP" model) — is the fastest diagnostic vocabulary for judging a layout's failures. The principles-of-design file introduces it as the beginner-facing complement to Arnheim's perceptual theory. Access: Peachpit Press; current editions cover desktop and web layout. [canonical]

**John Berger, *Ways of Seeing* (with Sontag and Barthes nearby).** Berger's account of how images carry arguments — and how reproduction and context change their meaning — underpins the imagery domain's insistence that image *selection* is an editorial act with semantic consequences, not decoration. Sontag's *On Photography* and Barthes' *Rhetoric of the Image* supply the same argument from photography-theory angles; the photography file cites all three as a set. Access: Penguin (Berger); Farrar, Straus and Giroux (Sontag); libraries. [canonical]

**Kevin Lynch; Arthur and Passini.** *The Image of the City* (legibility of environments) and *Wayfinding: People, Signs, and Architecture* (decision-point signage) give the event-collateral file its signage logic: place signs at decision points, before the decision, not after. Access: MIT Press; libraries. [canonical]

## 9. Terminology index — which book supplies which vocabulary

When a domain file uses a term, this is where its authority comes from. Cite the book as [canonical] unless the passage was actually fetched. The index also shows the repository's dependencies at a glance: a single book (Müller-Brockmann) feeds twelve files, while some domains (accessibility) feed on standards rather than books at all — a deliberate split recorded in [Bibliography](bibliography.md) §6.

| Term / concept | Source work | Applied in |
| --- | --- | --- |
| Brand is a gut feeling; the three little questions | Neumeier, *The Brand Gap* | brand-fundamentals, brand-strategy |
| Identity vectors: product, environment, communication, behaviour | Olins, *The Brand Handbook* / *On Brand* | brand-fundamentals, visual-identity |
| Brand-equity model; brand-architecture spectrum | Aaker, *Building Strong Brands* / *Managing Brand Equity* | brand-architecture, visual-identity |
| Phased identity process and named deliverables | Wheeler & Meyerson, *Designing Brand Identity* | brand-guidelines, brand-governance, logo-systems |
| Twelve brand archetypes | Mark & Pearson, *The Hero and the Outlaw* | brand-personality |
| Distinctive asset theory | Sharp, *Building Distinctive Brand Assets* | brand-strategy, brand-fundamentals |
| Letter / Text / Grid structure; classification | Lupton, *Thinking with Type* | typography domain (six files) |
| Measure, hanging punctuation, text-block colour | Bringhurst, *The Elements of Typographic Style* | typesetting, typographic-hierarchy |
| Asymmetric typography; functional standards | Tschichold, *The New Typography* | visual-styles, editorial-design |
| Page proportions; Penguin Composition Rules | Tschichold, *The Form of the Book* | editorial-design |
| Swiss typographic craft (spacing, rhythm) | Ruder, *Typographie* | typesetting |
| Column systems; the 12-column grid; type-area | Müller-Brockmann, *Grid Systems* | grid-systems and eleven other files |
| Grid as workshop: working and breaking | Samara, *Making and Breaking the Grid* | grid-systems |
| Margins, "design is one" discipline | Vignelli, *The Vignelli Canon* | spacing-and-proportion, grid-systems |
| Point–line–plane; figure–ground | Lupton & Phillips, *The New Basics* | elements-of-design, composition |
| Perceptual weight and balance | Arnheim, *Art and Visual Perception* | composition, principles-of-design |
| CRAP (contrast, repetition, alignment, proximity) | Williams, *The Non-Designer's Design Book* | principles-of-design |
| Affordances, signifiers, mapping, feedback | Norman, *The Design of Everyday Things* | ui-fundamentals, ux-fundamentals, information-hierarchy |
| Visual variables | Bertin, *Semiology of Graphics* | data-visualisation |
| Data-ink, chart junk, small multiples, lie factor | Tufte, *The Visual Display…* | data-visualisation, presentation-checklist |
| Ten principles; "less, but better" | Rams via Vitsoe | design-philosophies, design-quality-framework |
| Inspiration–ideation–implementation arc | Brown, *Change by Design* | design-thinking, design-philosophies |
| Trigger / rules / feedback / loop | Saffer, *Microinteractions* | interaction-design |
| Fluid grids, flexible images, media queries | Marcotte, *Responsive Web Design* | responsive-design, responsive-layouts |
| BLUF / pyramid structure | Minto, *The Pyramid Principle* | information-hierarchy |
| Brainstorming rules; SCAMPER | Osborn; Eberle | ideation |
| Isotype working rules | Neurath; Neurath & Kinross | diagrams-and-infographics |
| Atomic design (atoms → components) | Frost, *Atomic Design* | design-system-audit, website-visual-qa |
| Legibility of environments; decision-point signage | Lynch; Arthur & Passini | event-collateral |
| Image meaning as editorial act | Berger, *Ways of Seeing* | image-selection, photography |

## 10. Choosing between overlapping books

Several of these books cover the same ground from different angles; this table records the library's preference order and the reason. Preference here is a working default, not a claim that the "over" book is weaker — only that it answers a different, usually later, question.

| Question | Prefer | Over | Why |
| --- | --- | --- | --- |
| First book on grids? | Müller-Brockmann | Samara, Vignelli | The canonical system statement; Samara assumes it |
| Typography craft rules? | Bringhurst | Lupton, Spiekermann | Bringhurst states the craft; Lupton adds criticism; Spiekermann adds personality |
| Brand definition for a short brief? | Neumeier | Aaker, Keller | Neumeier is the compact judgement call; Aaker/Keller are the measurement layer |
| Archetype selection? | Mark & Pearson | generic tone guides | The archetypes are its invention; everything else is derivative |
| Design-quality evaluation? | Rams (Vitsoe) | Lidwell et al. | Rams is a compact criteria set; Lidwell is an encyclopaedia to consult, not to follow |
| Ideation techniques? | Brown + Osborn/Eberle | Fletcher, Munari | Process books give repeatable method; Fletcher/Munari give attitude |
| History context? | Meggs | museum essays | Meggs is the survey; museums supply primary artefacts and dates |
| Dataviz encoding rules? | Bertin | Tufte, Lidwell | Bertin defines the variables; Tufte polishes the presentation; Lidwell summarises both |
| Palette reasoning? | Albers | Itten, Heller | Albers explains why context changes colour; Itten classifies contrasts; Heller adds culture |
| Image-selection argument? | Berger | Sontag, Barthes | Berger frames the editorial act; the other two supply the deeper theory |

## 11. Reading pathways by task

The core twenty plus the additional list cover most library tasks. Suggested sequences (first title = foundation):

- **Extend a fixed logo into a brand kit:** Wheeler & Meyerson (process) → Olins (identity vectors) → Neumeier (brand definition) → Sharp (distinctive assets) → Mark & Pearson (personality) — then the design-systems domain for the component layer.
- **Govern an existing brand system:** Wheeler & Meyerson (governance phases) → Olins (identity versus image) → Frost *Atomic Design* (component vocabulary) → the design-systems and evaluation domains for audit mechanics.
- **Build a typographic system:** Bringhurst (craft) → Lupton *Thinking with Type* (structure and criticism) → Spiekermann (selection voice) → Tschichold *The Form of the Book* (page discipline) → MDN/web typography sources for the screen layer.
- **Design a poster or document system:** Müller-Brockmann (grid) → Samara (structure and deviation) → Vignelli Canon (margins and restraint) → Tufte (if the content is data-bearing).
- **Audit a user interface:** Norman (mental models) → Krug (usability judgement) → Lidwell et al. (principle lookup) → NN/g articles for current research.
- **Develop a colour palette:** Albers (relativity) → Itten (contrasts) → Munsell (notation) → Heller (cultural meaning) → WCAG Understanding pages (contrast requirements).
- **Run ideation or a workshop:** Brown (design thinking) → Knapp *Sprint* (timeboxed method) → Osborn/Eberle (divergence tools) → Lupton *Graphic Design Thinking* (studio techniques) → Fletcher and Munari (attitude).
- **Contextualise a style choice:** Meggs (narrative) → Vitsoe's Rams page (quality criteria) → Tschichold and Müller-Brockmann (modernist lineage) → the repository's history domain.

Two notes on using the pathways. First, they are dependency-ordered, not difficulty-ordered: the first book supplies the frame the later ones assume. Second, they stop at books on purpose — for anything perishable (platform sizes, current licence terms, contrast thresholds) the pathway hands off to the web sources catalogued in [Bibliography](bibliography.md) §5, and for taught-programme context to [Academic Curricula](academic-curricula.md). A book is the wrong instrument when the question has a version number attached.

## 12. Common mistakes

1. **Treating a principle as law.** Bringhurst's rules are craft defaults for long-form print, not web requirements; Samara's "breaking" exists precisely because grids serve communication, not the reverse. The library marks conventions as conventions.
2. **Fabricating precision.** Quoting a sentence, page number or chapter from a book that was never opened. The honest form is "X's principle of … [canonical]".
3. **Citing pirated PDFs.** Full-text uploads of several of these books exist on unauthorised sites. Using them breaks integrity and legal norms; legitimate access is always the publisher, a preview, or a library.
4. **Mixing editions.** *Design of Everyday Things* changed vocabulary between 1988 and 2013 (affordances → signifiers); *Meggs'* seventh edition reordered the narrative. Cite the edition whose framing you mean.
5. **Using books for perishable data.** Platform sizes, licence terms and contrast thresholds come from web sources; books predate them.
6. **Attributing synthesis to one author.** When a repository passage blends several books, it must say so — the brief requires labelling syntheses as syntheses.
7. **Treating an unverified datum as verified.** Where an entry says "not verified this session", a future agent must fetch the publisher page before repeating the publisher, year or edition with confidence. After the second verification pass, the flagged list is down to one: Munari's English edition year (Rossman and Duerden's title, publisher and year, Lupton's *Graphic Design Thinking* year and the McAlhone and Stuart revision year were verified in that pass — the Rossman and Duerden title itself turned out to differ from the mission's wording).
8. **Chasing novelty over the library's anchors.** The books here are chosen because the repository's rules trace to them. A new, trendier title does not replace an anchor until its contribution is argued in a domain file and the terminology index is updated; until then it is a lead, not an authority.

## 13. Evaluation checklist

Before an agent cites any book from this file:

- Is the edition stated, and is the edition-specific claim true of that edition?
- Is the provenance tag correct — [accessed] only if the content was actually fetched this session?
- Is any quote verbatim from fetched output, with author and title, and short?
- Is the publisher/year/ISBN stated only where verified, or clearly marked as unverified?
- Would a sceptical reader know from the citation alone how much the agent actually saw?
- Is the claim a principle (book-appropriate) rather than perishable data (web-appropriate)?
- If the passage is a synthesis, is it labelled as one?
- If the entry was marked "not verified this session", has the publisher page been fetched before repeating its bibliographic data as fact?

## 14. Related topics

- [Bibliography](bibliography.md) — the full inventory these entries summarise.
- [Source Accessibility](source-accessibility.md) — access tiers and re-verification guidance.
- [Academic Curricula](academic-curricula.md) — how this reading list maps to taught programmes.
- [Professional Guidelines](professional-guidelines.md) — the standards corpus that complements these books.
- [Tools and Software](tools-and-software.md) — the practice tools these books teach you to reason about.
- [Case Studies](case-studies.md) — documented applications of the principles above.
- [Typography fundamentals](../typography/typography-fundamentals.md), [Grid systems](../layout/grid-systems.md), [Brand fundamentals](../branding/brand-fundamentals.md), [Design philosophies](../history/design-philosophies.md), [Design thinking](../methodology/design-thinking.md) — the domain files where these books are actually applied. Where a domain file's rules conflict with a book, the domain file's sources win: books supply reasoning, the library supplies current, verified specifics.

## 15. References

Verification evidence, recorded in two passes on 2026-11-24 (build pass; re-verification pass — both saw results in tool output).

Fetched in full [accessed, re-verification pass]: the Princeton Architectural Press product page for *Thinking with Type* 3rd ed., https://papress.com/products/thinking-with-type-3-edition (ISBN 9781797226828, 256 pages, 12 March 2024, publisher PA Press / Chronicle Books).

Fetch attempted and blocked [search-verified only]: the Wiley catalogue page for *Designing Brand Identity* 6th ed. (https://www.wiley.com/en-us/shop/graphic-design/designing-brand-identity-a-comprehensive-guide-to-the-world-of-brands-and-branding-6th-edition-p-9781119984825) returned HTTP 403 to the fetcher; its data rests on search results, not a fetch.

Surfaced in search results [search-verified, re-verification pass]: O'Reilly listings for *Meggs' History of Graphic Design*, 7th ed. (ISBN 9781119743293, crediting Philip B. Meggs, Alston W. Purvis, Sandra Maxa and Mark Sanders); a Valore listing for the 6th edition (Wiley, 2016) https://www.valore.com/products/meggs-history-of-graphic-design/9781118772058; the Niggli catalogue page for *Grid systems* https://niggli.ch/en/products/rastersysteme-fur-die-visuelle-gestaltung ("A handbook for graphic designers, typographers and exhibition designers"); Amazon https://www.amazon.com/Grid-systems-graphic-design-communication/dp/3721201450 and Rizzoli Bookstore listings for *Grid systems* (ISBN 9783721201451, "since 1981", 162 pages); Typographica's review of version 4.0 https://typographica.org/typography-books/the-elements-of-typographic-style-4th-edition (8 February 2013); a review page treating the 4th edition (2013) as current, https://guptadeepak.com/books/the-elements-of-typographic-style; PA Press's product page for *Graphic Design Thinking* https://papress.com/products/graphic-design-thinking-beyond-brainstorming (publication date 09/01/2011, 184 pages); JSTOR's catalogue entry for Rossman and Duerden's *Designing Experiences* https://www.jstor.org/stable/10.7312/ross19168 and the *strategy+business* review https://www.strategy-business.com/article/How-to-build-a-great-experience (Columbia Business School Publishing, 2019); AbeBooks https://www.abebooks.com/Smile-Mind-Revised-Expanded-Edition-Witty/32502995039/bd and Amazon https://www.amazon.com/Smile-Mind-Thinking-Graphic-Design/dp/0714833282 listings for *A Smile in the Mind* (Revised and Expanded Edition, 2016; a September 2001 Phaidon Inc Ltd printing of the first edition).

Carried over from the build pass [search-verified]: the Wiley catalogue page for *Meggs'* 7th ed. https://www.wiley.com/en-us/shop/graphic-design/meggs'-history-of-graphic-design-7th-edition-p-9781119743293; the MICA notice on the seventh edition https://www.mica.edu/art-articles/details/mica-faculty-authors-meggs-history-of-graphic-design-7th-edition; a retailer listing with ISBN-10 1797226827 for *Thinking with Type*; a library catalogue listing for *Making and Breaking the Grid* (third edition) https://www.librarycat.org/lib/encephalical/item/28563250; academic citation pages confirming *The Brand Handbook* (Thames & Hudson, 2008) at https://sk.sagepub.com/book/mono/brands-and-branding/back-matter/i1145 and *Building Strong Brands* (Free Press, 1996) at https://lup.lub.lu.se/luur/download?func=downloadFile&recordOId=1343693&fileOId=2433345; citation entries confirming *The Brand Gap* (2003), *Change by Design* (HarperBusiness, 2009) and *The Design of Everyday Things* revised edition (2013); Amazon listings for *Universal Principles of Design, Revised and Updated* (ISBN-10 1592535879) and *Grid systems* (ISBN-10 3721201450). Vitsoe's ten-principles page https://www.vitsoe.com/us/about/good-design was fetched by the history-domain files on 2026-11-23 [accessed, carried over]. All remaining bibliographic data is [canonical] and marked as such in the entries above. A caution observed during the re-verification pass: general searches for Bringhurst and Lupton surface full-text PDF uploads on third-party sites (for example readings.design and Scribd); these are unauthorised copies, were not used, and are never legitimate access routes.


