# Bibliography

## 1. What this file is

This is the consolidated bibliography for the whole repository: every book, paper, standard and web source that the 81 domain files rely on, deduplicated and organised by domain and source type. It was compiled programmatically — an inventory of every `## 11. References` section and every external link in the repository, collected with `grep`, then deduplicated and grouped. It is the single place to answer "where does this library's knowledge come from?" without reading all 81 files.

Two sibling files complete the reference apparatus: [Books and Textbooks](books-and-textbooks.md) gives full per-book entries for the core canon (publisher data, contributions, legitimate access routes), and [Source Accessibility](source-accessibility.md) classifies how openly each source can actually be read. This file records *what* is cited and with what provenance; those files record *how* to get at it.

## 2. How to read the tags

Every entry below carries a provenance tag. The tag system is defined in the repository brief and is honoured exactly — a tag is never upgraded, and entries carried over from domain files keep the tag the domain file gave them:

- `[accessed]` — the page was fetched and read during this project, by the domain agent that cited it (project build date 2026-11-23).
- `[search-verified]` — the source appeared in search results (title plus URL) but the page itself was not fetched. Entries marked `[search-verified 2026-11-24 — this file]` were verified by the bibliography build itself.
- `[canonical]` — a well-established work attributed from general professional knowledge: no page numbers, no invented quotes.
- "Carried over" means the entry was inherited from a domain file's own reference list; the tag reflects that file's work, not a fresh verification by this file.

One caution applies to every entry: the repository was built on 2026–11–23/24. Web sources move. Before an agent treats a URL load-bearing, re-check that it still resolves and still says what is claimed.

## 3. Inventory snapshot

| Measure | Count | Method |
| --- | --- | --- |
| Domain files with reference sections | 81 | `find *.md` excluding `references/`, `README.md` |
| Reference-section lines | ~716 | extraction of all `## 11. References` bodies |
| Lines tagged `[accessed]` | 177 | `grep -c '\[accessed'` on extracted sections |
| Lines tagged `[search-verified]` | 144 | `grep -c '\[search-verified'` |
| Lines tagged `[canonical]` | 208 | `grep -c '\[canonical'` |
| Unique external URLs | 208 | `grep -rhoE 'https?://…'` over the domain files, sorted and deduplicated (recomputed 2026-11-24) |
| Unique cited book titles | ~134 | extraction of italic-marked titles from reference sections (includes journals and essays; recomputed 2026-11-24) |

Counts are lines, not claims: one line can carry several facts, and the same URL is often cited by several files (the heaviest are `brand.mit.edu/applying-brand/do-dont` — 9 citations, `merchants.ubereats.com/.../co-marketing-tools` — 9, and `www.buffalo.edu/brand/identity/usage/Clear-space.html` — 8, all in the branding domain). The rough split tells its own story: the library leans on ~200 canonical books for principles, and on ~200 web sources for checkable specifics (standards, metrics, sizes, licences).

Where the tags concentrate, by domain (lines in that domain's reference sections that mention the tag):

| Domain | accessed | search-verified | canonical | Dominant source style |
| --- | --- | --- | --- | --- |
| accessibility | high | medium | low | W3C/WAI fetched pages |
| imagery | high | high | low | licences and platform terms |
| applications | medium | high | medium | trade/production pages, size guides |
| foundations | high | low | high | NN/g articles + canonical theory |
| ui-ux | high | medium | medium | NN/g corpus + product guidelines |
| branding | medium | medium | high | canonical strategy books + public brand manuals |
| typography | medium | low | high | canonical craft books + MDN |
| design-systems | medium | medium | medium | official system documentation |
| history | medium | medium | high | museum/encyclopaedia pages + canonical surveys |
| colour | low | low | high | canonical colour theory + MDN |
| methodology | medium | medium | medium | process guides and NN/g methods |
| evaluation | low | low | medium | checklists referencing everything above |

### 3.1 Known gaps and limits of this inventory

- Rossman and Duerden's brand-experience book (mission §2.1) is not yet cited by any domain file; it enters the library through [Books and Textbooks](books-and-textbooks.md) only. Verification searches (2026-11-24) also showed the mission's title is a variant: the book these authors published is *Designing Experiences*, Columbia Business School Publishing, 2019.
- The colour domain rests almost entirely on canonical books plus MDN; it has no fetched primary source of its own. If colour claims are ever load-bearing, fetch peer-reviewed literature first.
- 125 of the 208 unique URLs (about 60 per cent) occur exactly once across the domain files — mostly the applications files' platform-specific sizes. These are the most perishable entries in the library; treat them as leads to re-check, not as settled data.
- A few links recorded by domain files were bot-blocked at access time (notably the Federal Register AI-copyright guidance) and are tagged accordingly rather than silently trusted.
- Tag counts overlap where one reference line carries two tags, so the three tag columns do not sum to the total reference-line count.

## 4. Books by domain

Full bibliographic detail and access routes for the twenty mission core books live in [Books and Textbooks](books-and-textbooks.md); entries here stay at inventory level. `→ cited in` lists the domain files that actually rely on the work.

### 4.1 Branding and visual identity

- Wheeler, Alina; Meyerson, Rob — *Designing Brand Identity: A Comprehensive Guide to the World of Brands and Branding*, 6th ed., Wiley, ISBN 978-1-119-98482-5. [search-verified 2026-11-24 — this file] → cited in brand-architecture, brand-discovery, brand-governance, brand-guidelines, brand-strategy, fixed-logo-analysis, logo-systems, visual-identity.
- Olins, Wally — *The Brand Handbook*, Thames & Hudson, 2008. [search-verified 2026-11-24 — this file] → cited in brand-guidelines, visual-identity.
- Olins, Wally — *On Brand*, Thames & Hudson, 2004; *Corporate Identity*, Phaidon. [canonical] → cited in brand-fundamentals.
- Aaker, David A. — *Building Strong Brands*, Free Press, New York, 1996. [search-verified 2026-11-24 — this file] → introduced by the books file; cited in the branding domain's equity discussions.
- Aaker, David A. — *Managing Brand Equity*, Free Press, 1991; and Smith, David C., review of *Managing Brand Equity*, *Journal of Marketing Research* (JSTOR 1252048). [canonical] → cited in brand-architecture, brand-fundamentals, visual-identity.
- Neumeier, Marty — *The Brand Gap: How to Bridge the Distance Between Business Strategy and Design*, New Riders, 2003 (revised "backpanel" editions later). [search-verified 2026-11-24 — this file, year and subtitle; publisher canonical] → cited in brand-fundamentals, brand-personality, brand-strategy.
- Rossman, J. Robert; Duerden, Mathew D. — *Designing Experiences*, Columbia Business School Publishing, 2019 (JSTOR 10.7312/ross19168) — the mission titles it *Designing Brand Experiences*; no Routledge edition surfaced in verification searches. [search-verified 2026-11-24 — this file] → mission-listed; not yet cited by domain files.
- Mark, Margaret; Pearson, Carol S. — *The Hero and the Outlaw: Building Exceptional Brands Through the Power of Archetypes*, McGraw-Hill, 2001. [canonical] → cited in brand-personality.
- Sharp, Byron — *Building Distinctive Brand Assets*, Oxford University Press, 2018. [canonical] → cited in brand-strategy, brand-fundamentals.
- Keller, Kevin Lane — *Strategic Brand Management*, Pearson. [canonical] → cited in brand-fundamentals.
- Ries, Al; Trout, Jack — *Positioning: The Battle for Your Mind*, McGraw-Hill, 1981. [canonical] → cited in brand-strategy.

### 4.2 Typography and editorial design

- Lupton, Ellen — *Thinking with Type*, 3rd revised and expanded ed., Princeton Architectural Press, March 2024 (1st ed. 2004). [search-verified 2026-11-24 — this file] → cited in editorial-design, font-pairing, typeface-selection, typesetting, typographic-hierarchy, typography-fundamentals, design-quality-framework.
- Bringhurst, Robert — *The Elements of Typographic Style*, Hartley & Marks; 1st ed. 1992 (ISBN 0-88179-133-4), 4th ed. "version 4.0" reviewed February 2013, a 4.1 printing also listed. [search-verified 2026-11-24 — this file] → cited in accessible-typography, editorial-design, font-pairing, typeface-selection, typesetting, typographic-hierarchy, typography-fundamentals, graphic-design-history.
- Tschichold, Jan — *Die neue Typographie*, 1928; English: *The New Typography*, University of California Press, trans. Ruari McLean. *The Form of the Book*, Hartley & Marks, English ed. 1991 (incl. the Penguin Composition Rules). [canonical] → cited in visual-styles, editorial-design, graphic-design-history, influential-designers.
- Ruder, Emil — *Typographie*, Niggli. [canonical] → cited in typesetting, graphic-design-history.
- Spiekermann, Erik; Ginger, E. M. — *Stop Stealing Sheep & Find Out How Type Works*, Adobe Press, 3rd ed. 2013. [canonical] → cited in font-pairing, typeface-selection, typography-fundamentals.
- Aicher, Otl — *Typographie*, 1988. [canonical] → cited in influential-designers.
- The typography domain's spine is Lupton's *Thinking with Type*; Bringhurst supplies the craft rules and Spiekermann the selection voice. Together they cover classification, pairing and setting judgement; nothing else typography-side is load-bearing.

### 4.3 Layout, grids and composition

- Müller-Brockmann, Josef — *Grid Systems in Graphic Design* (*Rastersysteme für die visuelle Gestaltung*), Niggli, 1981, bilingual German/English, ISBN 9783721201451. [search-verified 2026-11-24 — this file] → cited in layout/grid-systems, foundations/composition, foundations/principles-of-design, applications/presentations, applications/posters, applications/certificates-and-documents, branding/fixed-logo-analysis, branding/visual-identity, evaluation/design-quality-framework, methodology/design-critique, graphic-design/graphic-language, typography/editorial-design.
- Samara, Timothy — *Making and Breaking the Grid*, Rockport; a third edition exists. [search-verified 2026-11-24 — this file, edition existence; publisher canonical] → cited in layout/grid-systems.
- Vignelli, Massimo — *The Vignelli Canon*, distributed as a free PDF by the Vignelli Center for Design Studies, RIT (https://www.rit.edu/vignellicenter/sites/rit.edu.vignellicenter/files/documents/The%20Vignelli%20Canon.pdf). [canonical; URL carried over] → cited in layout/grid-systems, layout/spacing-and-proportion, influential-designers.
- Müller-Brockmann, Josef — *History of the Poster*; *Poster Designs*. [canonical] → cited in influential-designers, poster-checklist.
- Kandinsky, Wassily — *Point and Line to Plane*. [canonical] → cited in foundations (element vocabulary).

### 4.4 Graphic design history and theory

- Meggs, Philip B.; Purvis, Alston W. (with Sandra Maxa and Mark Sanders joining on the seventh edition) — *Meggs' History of Graphic Design*, 7th ed., Wiley, ISBN 9781119743293 (earlier editions Wiley, multiple years). [search-verified 2026-11-24 — this file] → cited in graphic-language, visual-styles, graphic-design-history, influential-designers.
- Lupton, Ellen; Phillips, Jennifer Cole — *Graphic Design: The New Basics*, Princeton Architectural Press, 2008. [canonical] → cited in composition, elements-of-design.
- Rand, Paul — *Thoughts on Design*, 1946. Glaser, Milton — *Drawing is Thinking*, 2008. Fletcher, Alan — *The Art of Looking Sideways*, Phaidon, 2001. Munari, Bruno — *Design as Art*. [canonical] → cited in influential-designers; Fletcher and Munari also mission-core (see books file).
- Arnheim, Rudolf — *Art and Visual Perception*, University of California Press, 1954/1974; *The Power of the Center*, 1982. [canonical] → cited in composition, design-critique (foundations), elements-of-design, principles-of-design.
- Rubin, Edgar — *Synsoplevede Figurer*, 1915 (figure–ground, Rubin's vase). [canonical] → cited in gestalt-and-perception.
- Sullivan, Louis ("form follows function"); Mies van der Rohe ("less is more"); Venturi, Robert — *Complexity and Contradiction in Architecture*, 1966. [canonical] → cited in design-philosophies.
- Rams, Dieter — "Ten Principles for Good Design", published by Vitsoe (https://www.vitsoe.com/us/about/good-design, CC BY-NC-ND 4.0) and *Less and More: The Design Ethos of Dieter Rams*, Gestalten, 2015. [accessed, per history files] → cited in design-philosophies, influential-designers.
### 4.5 Colour

- Albers, Josef — *Interaction of Color*, Yale University Press, 1963. [canonical] → cited in colour-theory, palette-development.
- Itten, Johannes — *The Art of Color*, Van Nostrand Reinhold. [canonical] → cited in colour-theory.
- Goethe, Johann Wolfgang von — *Theory of Colours* (*Zur Farbenlehre*), 1810. Newton, Isaac — *Opticks*, 1704. [canonical] → cited in colour-theory (historical layer).
- Munsell, A. H. — *A Color Notation*, 1905 (hue/value/chroma). [canonical] → cited in colour-theory.
- Heller, Eva — *Wie Farben wirken* (How Colours Affect), Reinbek, 1989. [canonical] → cited in colour-psychology.
- Birren, Faber — *Color Psychology and Color Theory* — historical practitioner literature; treat period claims critically. [canonical] → cited in colour-psychology.
- Cross-cultural colour–emotion claims in the repository rest on a fuzzy-set research study indexed on ResearchGate, "Universal vs Contextual Color-Emotion Associations: A Fuzzy Approach" (https://www.researchgate.net/publication/383310497_Universal_vs_Contextual_Color-Emotion_Associations_A_Fuzzy_Approach). [search-verified, per colour files] → cited in colour-psychology.

### 4.6 Information design and data visualisation

- Bertin, Jacques — *Sémiologie Graphique*, 1967; English *Semiology of Graphics*, 1983 translation. [canonical] → cited in data-visualisation (visual variables).
- Tufte, Edward — *The Visual Display of Quantitative Information* (1983; 2nd ed. 2001), *Envisioning Information*, *Visual Explanations*, *Beautiful Evidence*, Graphics Press (overview: https://www.edwardtufte.com/books/). [canonical; URL carried over] → cited in data-visualisation, diagrams-and-infographics, presentation-checklist.
- MacEachren, Alan — *How Maps Work*, 1995. [canonical] → cited in data-visualisation.
- Neurath, Otto — *International Picture Language*, 1936; Neurath, Marie; Kinross, Robin — *The transformer: principles of making Isotype charts*, 2009. [canonical] → cited in diagrams-and-infographics.
- Lynch, Kevin — *The Image of the City*, 1960. Arthur, Paul; Passini, Romedi — *Wayfinding: People, Signs, and Architecture*, 1992. [canonical] → cited in event-collateral (wayfinding).
- Minto, Barbara — *The Pyramid Principle: Logic in Writing and Thinking*, 1985. [canonical] → cited in information-hierarchy (message-first ordering).
- Duarte, Nancy — *Resonate*, Wiley; *slide:ology*, O'Reilly. Reynolds, Garr — *Presentation Zen*, New Riders. Kawasaki, Guy — "The 10/20/30 Rule of PowerPoint". [canonical] → cited in presentations, marketing-assets, presentation-checklist.

### 4.7 UX, UI and interaction

- Norman, Donald A. — *The Design of Everyday Things*, Basic Books; original 1988, revised and expanded edition 2013. [search-verified 2026-11-24 — this file, 2013 revised edition; publisher canonical] → cited in information-hierarchy, information-architecture, ui-fundamentals, ux-fundamentals.
- Krug, Steve — *Don't Make Me Think*. [canonical] → cited in ux-fundamentals.
- Shneiderman, Ben — *Designing the User Interface*. Nielsen, Jakob — *Usability Engineering*. [canonical] → cited in ui-ux (heuristics lineage).
- Rosenfeld, Louis; Morville, Peter — *Information Architecture for the World Wide Web*. Morville, Peter — *Ambient Findability*, O'Reilly, 2005. [canonical] → cited in information-architecture.
- Saffer, Dan — *Microinteractions: Designing with Details*, O'Reilly, 2013. [canonical] → cited in interaction-design, frontend-implementation.
- Marcotte, Ethan — "Responsive Web Design", *A List Apart*, 2010; *Responsive Web Design*, A Book Apart, 2011. Wroblewski, Luke — *Mobile First*, A Book Apart, 2011. [canonical] → cited in responsive-design, responsive-layouts, frontend-implementation.
- Connor, Adam; Irizarry, Aaron — *Discussing Design: Giving and Receiving UX Design Feedback*, O'Reilly, 2015. [canonical] → cited in design-critique (foundations and methodology).

### 4.8 Design thinking, methodology and critique

- Brown, Tim — *Change by Design: How Design Thinking Transforms Organizations and Inspires Innovation*, HarperBusiness, 2009. [search-verified 2026-11-24 — this file, year and subtitle; publisher canonical] → cited in design-philosophies, design-thinking.
- IDEO — "An Introduction to Design Thinking: Process Guide" and *Bootcamp Bootleg* (process framing). Knapp, Jake — *Sprint*, Simon & Schuster, 2016 (https://www.gv.com/sprint). [canonical; URL carried over] → cited in design-thinking, research-and-discovery.
- Osborn, Alex — *Applied Imagination*, 1953 (brainstorming rules). Eberle, Bob — *SCAMPER: Creative Games and Activities for Developing Imagination* (popularised the acronym). [canonical] → cited in ideation.
- Design Council (UK) — "Framework for Innovation: Design Council's evolved Double Diamond" (https://www.designcouncil.org.uk/resources/framework-for-innovation). [canonical; URL carried over] → cited in design-thinking.
- Müller, Boris — "Design Critique Culture" (https://borism.medium.com/design-critique-culture-b7350baab11c). [accessed, per foundations files] → cited in design-critique (both copies).

### 4.9 Imagery and photography

- Berger, John — *Ways of Seeing*, BBC / Penguin, 1972. Sontag, Susan — *On Photography*, Farrar, Straus and Giroux, 1977. Barthes, Roland — *Rhetoric of the Image* (1964), in *Image–Music–Text*. [canonical] → cited in image-selection, photography.
- Freeman, Michael — *The Photographer's Eye*, Focal Press, 2007. [canonical] → cited in photography.
- Edwards, Betty — *Drawing on the Right Side of the Brain*, Tarcher/Putnam, 1979/2012. [canonical] → cited in composition (negative-space perception).

### 4.10 Design systems

- Frost, Brad — *Atomic Design*, 2016 (free-to-read on the author's site in book form). [canonical] → cited in design-system-audit, website-visual-qa.
- The design-systems domain is otherwise web-sourced: GOV.UK Design System, Material Design (M2/M3), Atlassian Design System, Carbon, Storybook, Style Dictionary, W3C Design Tokens Community Group — see section 5.3–5.4.

## 5. Web sources by category

The 208 unique URLs fall into ten families. Grouping rule: a source sits in the category of what it *governs* (a licence under 5.5 even if cited by an imagery file), and per-platform size guides are grouped under print/production-adjacent 5.6 only when they specify physical or canvas dimensions. Tags here are the original project tags recorded by the domain files (build date 2026-11-23); `→ cited in` lists the relying files.

- Baseline HQ, "4 Grid Systems" (column-grid walkthrough), cited by layout/grid-systems. [canonical, carried over]
- Civic Brand, "Vector, Raster, JPG, EPS, PNG — What's the Difference?", https://www.civicbrand.com/insights/articles/vector-raster-jpg-eps-png-whats-the-difference — cited by applications for export-format decisions. [canonical, carried over]
- Shutterstock Help Centre, "Standard vs Enhanced licence" comparison, https://www.shutterstock.com/help/en/articles/10617089-shutterstock-standard-image-license-vs-enhanced-image-license. [search-verified, carried over]
- Google Android accessibility help (contrast and display settings), https://support.google.com/accessibility/android/answer/7101858. [canonical, carried over]
- ConnectMachine, "Name Badge Size" guidance, https://www.connectmachine.ai/blog/name-badge-size — one-off badge-size corroboration. [search-verified, carried over]
- Presentations.ai, "What font size is best for presentations", https://www.presentations.ai/blog/what-font-size-is-best-for-presentations — one-off slide-type-size corroboration. [canonical, carried over]

### 5.1 Standards bodies

- W3C, *Web Content Accessibility Guidelines (WCAG) 2.2*, https://www.w3.org/TR/WCAG22 — the normative standard. [search-verified, carried over]
- W3C WAI, "Understanding WCAG 2.2" success-criterion pages (contrast-minimum, contrast-enhanced, non-text-contrast, reflow, text-spacing, focus-visible, target-size-minimum) under https://www.w3.org/WAI/WCAG22/Understanding/ — the interpretive companion. [accessed, carried over]
- W3C WAI, "WCAG 2 at a Glance" and "Standards/Guidelines" overview pages, https://www.w3.org/WAI/standards-guidelines/wcag/glance/ and https://www.w3.org/WAI/standards-guidelines/wcag/. [accessed/search-verified, carried over]
- W3C WAI, "Images Tutorial", https://www.w3.org/WAI/tutorials/images/. [accessed, carried over]
- W3C WAI, ARIA Authoring Practices Guide, https://www.w3.org/WAI/ARIA/apg/. [canonical, carried over]
- W3C Silver Task Force wiki, "Visual Contrast of Text Subgroup", https://www.w3.org/WAI/GL/task-forces/silver/wiki/Visual_Contrast_of_Text_Subgroup. [accessed, carried over]
- W3C Design Tokens Community Group format draft, https://www.designtokens.org/TR/drafts/format/. [canonical, carried over]
- MDN Web Docs (developer.mozilla.org) — CSS reference pages (clamp, gap, minmax, repeat, oklch, color values, text-wrap, variable fonts, grid layout, prefers-reduced-motion, responsive images). The single most-cited source family in the repository (~18 pages across typography, colour, layout, ui-ux, imagery). [accessed, carried over]

### 5.2 UX research and education

- Nielsen Norman Group articles (https://www.nngroup.com/articles/...) — principles-visual-design (Gordon), gestalt-proximity (Harley), f-shaped-pattern (Pernice), minimize-cognitive-load (Whitenton), recognition-and-recall (Budiu), ten-usability-heuristics, response-time limits, design-critiques, card-sorting/tree-testing/ia-study-guide, form-design-placeholders, progress-indicators, tone-of-voice-dimensions, stakeholder-interviews. ~15 distinct articles, cited by foundations, ui-ux, methodology and branding-discovery files. [accessed, carried over]
- Laws of UX, Jon Yablonski, https://lawsofux.com/. [accessed, carried over]
- Baymard Institute, line-length readability research, https://baymard.com/research-articles/line-length-readability. [search-verified, carried over]
- The eLearning Coach, "Design for Bottom-Up and Top-Down Processing", https://theelearningcoach.com/learning/design-for-bottom-up-and-top-down-processing. [accessed, carried over]
- Deque University WCAG interpretation pages and axe tool, https://deque.com/axe/ and https://dequeuniversity.com/resources/wcag2.1/1.4.10-reflow. [accessed/search-verified, carried over]
- DigitalA11y, "Understanding SC 1.4.11 Non-text Contrast", https://www.digitala11y.com/understanding-sc-1-4-11-non-text-contrast. [canonical, carried over]
- IxDF, "What are Grid Systems?" (Encyclopedia of Human-Computer Interaction). [canonical, carried over]

### 5.3 Design-system documentation

- GOV.UK Design System, https://design-system.service.gov.uk/ and component pages (e.g. button). [accessed, carried over] → design-systems (all five files).
- Material Design 3, https://m3.material.io/foundations/design-tokens and structure pages; Material 2, https://m2.material.io/design/layout/spacing-methods.html, iconography/system-icons. [accessed, carried over] → design-systems, layout, ui-ux, iconography.
- Atlassian Design System, https://atlassian.design/foundations/ (incl. tokens and illustration foundations). [accessed, carried over] → design-systems, graphic-design.
- IBM Carbon Design System, https://www.carbondesignsystem.com. [canonical, carried over] → illustration, branding-strategy context.
- Storybook docs, https://storybook.js.org/docs/get-started/why-storybook. [search-verified, carried over] → component-systems, documentation.
- Style Dictionary, https://styledictionary.com and https://github.com/style-dictionary/style-dictionary. [canonical, carried over] → design-tokens.
- Google Fonts repository, https://github.com/google/fonts. [canonical, carried over] → typeface-selection (licensing).

### 5.4 Brand guideline sites (public examples)

- MIT Brand Guide, "do/don't" application pages, https://brand.mit.edu/applying-brand/do-dont — the most-cited single URL in the repository (9 citations). [accessed, carried over]
- University at Buffalo identity, "Clear space", https://www.buffalo.edu/brand/identity/usage/Clear-space.html. [accessed, carried over]
- Uber Eats merchant brand resources, https://merchants.ubereats.com/us/en/resources/learning-center/co-marketing-tools. [accessed, carried over]
- Spotify newsroom media kit (logo and brand assets), https://newsroom.spotify.com/media-kit/logo-and-brand-assets. [accessed, carried over]
- University of Missouri brand guidelines, photography, https://brand.missouri.edu/brand-visuals/photography. [search-verified, carried over]
- University of Maryland icons guidance (mdui.org page referenced for icon style), https://www.mdui.org/en/design/1/style/icons.html. [canonical, carried over]

### 5.5 Licensing, copyright and AI policy

- Creative Commons, "About CC Licences", https://creativecommons.org/share-your-work/cclicenses/. [accessed, carried over]
- Unsplash Licence and Terms, https://unsplash.com/license, https://unsplash.com/terms. [search-verified, carried over]
- Shutterstock licence structure and Help Centre, https://www.shutterstock.com/license. [search-verified, carried over]
- U.S. Copyright Office AI initiative, https://www.copyright.gov/ai; Federal Register, "Copyright Registration Guidance: Works Containing Material Generated by Artificial Intelligence" (March 2023), https://www.federalregister.gov/documents/2023/03/16/2023-05321/copyright-registration-guidance-works-containing-material-generated-by-artificial-intelligence. [search-verified/accessible per imagery files]
- OpenAI Terms of Use, https://openai.com/policies/row-terms-of-use; Midjourney Terms of Service, https://docs.midjourney.com/hc/en-us/articles/32083055291277-Terms-of-Service. [accessed, carried over]

### 5.6 Print and production

- Pannier Graphics, "Letter Height Visibility Chart", https://www.panniergraphics.com/blog/letter-height-visibility-chart-for-outdoor-sign-readability. [accessed, carried over]
- papersizes.org, ISO 216 A-series, https://www.papersizes.org/a-paper-sizes.htm; papersizes.io, https://papersizes.io/a. [search-verified, carried over]
- SpeedPro, large-format DPI by viewing distance, https://www.speedpro.com/mesa-gilbert/what-resolution-is-best-for-large-format. 4over4, "300 DPI Rule…", https://www.4over4.com/guide/print-resolution-explained-dpi-settings-for-quality. Forest Printing DPI guide, https://www.forest-printing.com/guides/dpi-viewing-distance. [search-verified, carried over]
- Event badge sizes: ConferenceBadge, https://www.conferencebadge.com/blog/event-badge-sizes; PC Nametag, https://www.pcnametag.com/custom-name-tags-event-badges/standard-event-badges.html. [search-verified, carried over]
- Email/newsletter widths: beehiiv, https://www.beehiiv.com/blog/best-email-image-size; Template.net, https://www.template.net/graphic-design/email-newsletter-sizes. [search-verified, carried over]
- PowerPoint slide sizes: Microsoft Support, "Change the size of your PowerPoint slides", https://support.microsoft.com/en-us/powerpoint/change-the-size-of-your-powerpoint-slides. [search-verified, carried over]
- Social-media sizing: RecurPost Instagram guide, https://recurpost.com/instagram-scheduler/instagram-post-size-guide. [accessed, carried over]

### 5.7 Methodology, critique and ideation

- IDEO, "An Introduction to Design Thinking: Process Guide" (PDF hosted via Stanford's Michael Shanks course page, https://web.stanford.edu/~mshanks/MichaelShanks/files/509554.pdf). [canonical/search-verified, carried over]
- The Decision Lab, "SCAMPER" (acronym breakdown), https://thedecisionlab.com/reference-guide/philosophy/scamper. [search-verified, carried over]
- Designorate, "A Guide to the SCAMPER Technique for Design Thinking", https://www.designorate.com/a-guide-to-the-scamper-technique-for-design-thinking. [search-verified, carried over]
- Wikipedia, "SCAMPER", https://en.wikipedia.org/wiki/SCAMPER. [search-verified, carried over]
- Boris Müller, "Design Critique Culture", https://borism.medium.com/design-critique-culture-b7350baab11c. [accessed, carried over]
- NN/g "Design Critiques: Encourage a Feedback Culture", https://www.nngroup.com/articles/design-critiques. [accessed, carried over]
- Google Ventures, "The Design Sprint", https://www.gv.com/sprint. [canonical, carried over]
- Figma, "How to Make a Mood Board", https://www.figma.com/resource-library/how-to-make-a-mood-board. [canonical, carried over]
- NN/g stakeholder interviews, card-sorting/tree-testing comparisons and IA study guide (URLs under https://www.nngroup.com/articles/). [accessed, carried over]

### 5.8 Design-system community and adoption

- EightShapes, "Team Models for Scaling a Design System", https://medium.com/eightshapes-llc/team-models-for-scaling-a-design-system-2cf9d03be6a0. [accessed, carried over]
- Omlet, "How Leaders Measure Design System Adoption" and "How design system leaders define and measure adoption", https://www.omlet.dev/blog/how-leaders-measure-design-system-adoption. [search-verified, carried over]
- Design Systems Collective, "AI in Design Systems: Smarter UX, Faster Workflows and Better Collaboration", https://www.designsystemscollective.com/ai-in-design-systems-smarter-ux-faster-workflows-and-better-collaboration-cfac2cc236cf. [search-verified, carried over]
- Bynder, brand-management platform overview, https://www.bynder.com/en/solutions/teams/brand-management; Templafy, brand asset management, https://www.templafy.com/brand-asset-management. [canonical, carried over]

### 5.9 Museums, encyclopaedias and history

- The J. Paul Getty Museum, "History of the Bauhaus", https://www.getty.edu/research/exhibitions_events/exhibitions/bauhaus/new_artist/history/. [accessed, carried over]
- The Metropolitan Museum of Art, "The Bauhaus, 1919–1933", https://www.metmuseum.org/essays/the-bauhaus-1919-1933. [canonical, carried over]
- Tate, "Bauhaus" art-term entry, https://www.tate.org.uk/art/art-terms/b/bauhaus. [canonical, carried over]
- Encyclopædia Britannica, "Johannes Gutenberg" and "Printing press", https://www.britannica.com/biography/Johannes-Gutenberg, https://www.britannica.com/technology/printing-press. [search-verified, carried over]
- Wikipedia, "Swiss Style (design)", "International Typographic Style", "Bauhaus", "The Elements of Typographic Style", "SCAMPER" (accessed per domain files). [search-verified, carried over]
- Print Magazine, "Swiss Style: The Principles, the Typefaces & the Designers", https://www.printmag.com/featured/swiss-style-principles-typefaces-designers. [search-verified, carried over]

### 5.10 Other practitioner sources

- Vitsoe, "Dieter Rams: ten principles for good design" and biography, https://www.vitsoe.com/us/about/good-design, https://www.vitsoe.com/us/about/dieter-rams. [accessed/search-verified, carried over]
- Harvard Business School Online, "How to Craft the Perfect Brand Positioning Statement", https://online.hbs.edu/blog/post/brand-positioning-statement. [search-verified, carried over]
- Smashing Magazine, "Split Personality… Brutalist Web Development", https://www.smashingmagazine.com/2020/01/split-personality-brutalist-web-development. [search-verified, carried over]
- web.dev (Google), "Responsive Web Design Basics" and "Font Best Practices", https://web.dev/articles/responsive-web-design-basics, https://web.dev/articles/font-best-practices. [accessed, carried over]
- Apple Human Interface Guidelines, https://developer.apple.com/design/human-interface-guidelines/ (buttons, accessibility). [accessed, carried over]
- Colour Blind Awareness, https://www.colourblindawareness.org/colour-blindness. [canonical, carried over]
- Verywell Mind, colour psychology overview, https://www.verywellmind.com/color-psychology-2795824. [canonical, carried over]
- Fast Company, "The Golden Ratio: Design's Biggest Myth", https://www.fastcompany.com/3044877/the-golden-ratio-designs-biggest-myth; Figma resource library mood-boards and golden-ratio pages. [canonical/search-verified, carried over]
- Figma mood-board resource, https://www.figma.com/resource-library/how-to-make-a-mood-board. [canonical, carried over]
- JSTOR 1252048, David C. Smith's review of *Managing Brand Equity*, *Journal of Marketing Research*, https://www.jstor.org/stable/1252048. [accessed, carried over]
- Google Ventures Sprint, https://www.gv.com/sprint; Design Council Double Diamond, https://www.designcouncil.org.uk/resources/framework-for-innovation. [canonical, carried over]

## 6. Source-to-domain coverage map

| Domain | Primary book anchors | Primary web anchors |
| --- | --- | --- |
| branding | Wheeler/Meyerson; Olins; Aaker; Neumeier; Mark & Pearson; Sharp | MIT, Buffalo, Uber Eats, Spotify guidelines; HBS Online |
| typography | Lupton; Bringhurst; Tschichold; Ruder; Spiekermann | MDN CSS typography; web.dev fonts; Baymard |
| layout | Müller-Brockmann; Samara; Vignelli; Kandinsky | Material spacing; MDN grid/flex |
| colour | Albers; Itten; Munsell; Heller | MDN oklch; W3C contrast Understanding pages |
| accessibility | — (standards-led) | WCAG 2.2 + WAI tutorials + Deque |
| information-design | Bertin; Tufte; Neurath; MacEachren | NN/g scanning research |
| ui-ux | Norman; Krug; Saffer; Marcotte; Wroblewski | NN/g corpus; Apple HIG; Material |
| design-systems | Frost, *Atomic Design* | GOV.UK; Material 3; Atlassian; Carbon; Style Dictionary; Design Tokens CG |
| methodology | Brown; Knapp; Osborn/Eberle; Connor & Irizarry | IDEO guides; Design Council; NN/g research methods |
| history | Meggs; Rams/Vitsoe; designer monographs | Getty; Met; Tate; Britannica; Print Magazine |
| imagery | Berger; Sontag; Barthes; Freeman | licences (CC, Unsplash, Shutterstock); copyright.gov; platform terms |
| applications | Müller-Brockmann (posters/docs); Duarte; Reynolds | papersizes; Pannier; SpeedPro; platform size guides |

## 7. Maintenance rules for future agents

1. Add an entry to the domain file's own `## 11. References` first; this bibliography is rebuilt from those sections, not the other way round.
2. Keep tags honest: `[accessed]` only for pages actually fetched in the working session, `[search-verified]` for search-result-confirmed sources, `[canonical]` for attributed general knowledge. Never promote a tag without new evidence, and never invent a URL, edition or date.
3. Record author, title, edition, publisher, year, URL, access date, source type and access limitations for new entries (mission §10). State limitations explicitly — "publisher description only", "abstract only", "bot-blocked".
4. When several sources support one synthesis, cite them jointly and label the passage as a synthesis; label original frameworks as the project's own.
5. Re-verify URLs before relying on them; mark stale or bot-blocked links rather than silently dropping them, as the imagery files already do.
6. Prefer primary sources (standards, official guidelines, publishers) over aggregators; treat listicles as leads, not authority.

## 8. Related topics

- [Books and Textbooks](books-and-textbooks.md) — full entries for the core canon.
- [Source Accessibility](source-accessibility.md) — the source-accessibility index the mission requires.
- [Academic Curricula](academic-curricula.md) — how this corpus maps onto taught design programmes.
- [Professional Guidelines](professional-guidelines.md) — the standards and guidelines corpus in operational form.
- [Case Studies](case-studies.md) — documented design outcomes that the sources above ground.

## 9. References

This file *is* the reference apparatus; its own sources are the repository's 81 reference sections (inventoried by grep on 2026-11-24) plus the verification searches run during this build. Bibliographic claims made for the first time here rest on the following search-verified results (seen in tool output on 2026-11-24): the Wiley catalogue page for *Designing Brand Identity* 6th edition (ISBN 978-1-119-98482-5), the Wiley catalogue page for *Meggs' History of Graphic Design* 7th edition (ISBN 9781119743293), the Princeton Architectural Press product page for *Thinking with Type* 3rd edition, the Typographica review of *The Elements of Typographic Style* version 4.0, the Niggli catalogue page for *Grid Systems in graphic design* (ISBN 9783721201451), Amazon listings for *Thinking with Type* (ISBN-10 1797226827), *Universal Principles of Design, Revised and Updated* (ISBN-10 1592535879) and *Grid systems in graphic design* (ISBN-10 3721201450), a library catalogue listing for *Making and Breaking the Grid* (third edition), the MICA notice of the *Meggs'* seventh edition, and academic citation pages confirming *The Brand Handbook* (Thames & Hudson, 2008), *Building Strong Brands* (Free Press, 1996), *The Brand Gap* (2003), *Change by Design* (HarperBusiness, 2009) and *The Design of Everyday Things* (revised and expanded, 2013). Everything else is carried over from domain-file tags as recorded above. A second verification pass ran the same day (2026-11-24) and is recorded in full in [Books and Textbooks](books-and-textbooks.md) §15; its load-bearing results: the PA Press product page for *Thinking with Type* was fetched in full ([accessed] — ISBN 9781797226828, 256 pages, 12 March 2024); the Wiley catalogue page returned HTTP 403 and stays [search-verified]; fresh searches re-surfaced the Niggli and Typographica pages, O'Reilly listings confirming the *Meggs'* seventh-edition ISBN and co-authors Sandra Maxa and Mark Sanders, the PA Press page for *Graphic Design Thinking* (2011, 184 pages), JSTOR's entry fixing Rossman and Duerden's book as *Designing Experiences* (Columbia Business School Publishing, 2019), and listings for the 2016 *A Smile in the Mind* revised edition. The §3 inventory statistics were recomputed on the same basis and date (208 unique URLs in the domain files; 125 cited exactly once; ~134 italic-marked titles).

