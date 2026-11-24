# Tools and Software

## 1. What is this file?

This file documents the practical design-tool ecosystem: collaborative design, production graphics, fast content production, AI-assisted imagery, colour tooling, typography resources, frontend implementation and accessibility testing. It is deliberately maintained separately from the design theory in the rest of the repository, because software capabilities and pricing change far faster than the principles — treat every capability and price statement here as bearing a "re-verify before relying on it" label, per the provenance discipline in [Source accessibility](source-accessibility.md).

Each tool entry covers: primary purpose; best use cases; limitations; relevant workflows; cost and licensing (only where verified this session — otherwise "verify current pricing"); and alternatives. Two standing rules govern every recommendation in this file. First, do not assume a paid subscription is available: an agent should default to plans and tools that work at zero cost unless verified otherwise. Second, prefer free and open-source tools where capabilities are comparable, but never recommend inferior software simply because it is free — the licence does not make the output good, and a tool that cannot produce print-ready or accessible output is not saved by its price tag.

## 2. How to read the tool entries

Cost and licensing claims are marked with one of three statuses:

- **[verified this session]** — the fact was read from the vendor's own page on 2026-11-24; still re-check before financial commitments, since pricing pages change.
- **[search-verified]** — seen only in search results; more provisional.
- **[verify current pricing / capabilities]** — general professional knowledge only; the fact is stable enough to plan around but must be confirmed against the vendor before it appears in a deliverable.

Capability statements follow the same discipline: entries whose facts come from a fetched vendor page say so; everything else is general professional knowledge about long-established tools. Established tools (Illustrator, Photoshop, GIMP, Inkscape) change slowly, so their capability descriptions are reliable; young products and anything AI-related change monthly, so those entries carry the strongest re-verification warnings. When choosing between tools, use the decision table in section 11; when a tool choice has workflow consequences for code, cross-check [Frontend implementation](../ui-ux/frontend-implementation.md) and [Design tokens](../design-systems/design-tokens.md).

## 3. Collaborative design

### 3.1 Figma

**Primary purpose.** Browser-based collaborative interface design: multiplayer editing, components, design tokens as variables, prototyping, developer handoff (Dev Mode), plus adjacent products (FigJam whiteboarding, Slides) in the same account.

**Best use cases.** UI and web design with live collaboration; design systems with shared libraries; handoff to developers via inspect mode; comment-based review. For an agent producing UI work, Figma's free Starter plan is genuinely usable for small projects: the pricing page [verified this session] states Starter includes unlimited drafts, UI kits and templates, and limited version history (30 days), with unlimited free viewers ("invite as many people as you want to view, comment, inspect, or export from your Figma files—for free!") and AI usage on a credit allowance (150 credits/day, capped at 500/month on Starter). Paid tiers unlock unlimited files and projects (Professional), team-wide libraries (Professional+) and org-wide design systems with shared fonts (Organization+).

**Limitations.** The Starter plan's structural limits matter for systems work: variables modes are capped at 10 on Starter and 20 on Professional, with Organization and Enterprise unlimited via extended collections [verified this session], which constrains multi-theme token work on free plans; team-wide shared libraries require a paid tier, so a free team cannot share components as a true library across files; Starter also caps custom Figma Slides templates at 5 [verified this session]. Version history at 30 days is a real risk on free plans for long-running projects. Desktop app needed for some offline work; heavy files degrade in-browser.

**Cost and licensing.** Per the pricing page [verified this session], prices in USD per seat per month: Starter free; Professional $16 full seat (also $12 Dev seat, $3 Collab seat); Organization $55 (Dev $25, Collab $5); Enterprise $90 (Dev $35, Collab $5). Monthly AI credits come with full seats (3,000 Professional, 3,500 Organization, 4,250 Enterprise; Dev and Collab seats 500/month at every tier), with pay-as-you-go add-ons. Verify current pricing before quoting beyond this date.

**Relevant workflows.** Build components and variables first, publish a library, then compose screens; hand off with Dev Mode; export SVG/PNG assets for production; tokens can be mirrored to code via the token pipelines in section 9.3.

**Alternatives.** Penpot (open source, section 3.2), Sketch (macOS-only), Adobe XD (effectively end-of-life as a product — verify current status), Lunacy (free, Windows-friendly).

### 3.2 Penpot

**Primary purpose.** Open-source design and prototyping platform positioned for designer–developer collaboration, made by KALEIDOS. The vendor page [verified this session] describes it as "the open-source design platform for teams that need scalable collaboration" and highlights responsive design with CSS Grid and Flex layouts, components and shared libraries, native design tokens, an open file format built on open standards (CSS, HTML, SVG, JSON), and an open MCP server for AI-agent workflows.

**Best use cases.** Teams that need design-tool capability without per-seat licensing or with data/self-hosting requirements; open-source projects; workflows where designs must round-trip cleanly to real code, because the design model is built on the same layout primitives as the web. Its positioning explicitly includes AI agents as users, which matters for this repository's audience.

**Limitations.** Smaller ecosystem than Figma: fewer community templates, plugins and third-party integrations; some advanced prototyping and handoff niceties trail the market leader. The vendor page confirms free sign-up and self-hosting but does not state the specific licence name — commonly reported as MPL 2.0 [verify current licence on the project's repository]. Feature velocity is high, which cuts both ways.

**Cost and licensing.** Free to sign up [verified this session]; self-hosted installation available [verified this session]; hosted plan details were not on the fetched page — verify current pricing on the vendor's pricing page.

**Relevant workflows.** Design with auto-layout (Flex/Grid), define native design tokens, inspect code that "matches design", export SVG natively. For agent-driven pipelines, the MCP server and open file format allow programmatic reading and writing of design files without vendor APIs.

**Alternatives.** Figma (section 3.1) when ecosystem depth or client familiarity is required.

## 4. Production and graphic design

### 4.1 Adobe Illustrator

**Primary purpose.** Industry-standard vector editor for logos, icons, illustration and print production.

**Best use cases.** Logo and identity production where precise Bézier control, robust CMYK handling, and interoperability with print vendors are required; building logo variant sheets and clear-space artwork (see [Logo systems](../branding/logo-systems.md)).

**Limitations.** Subscription-only licensing — significant because this file's standing rule is not to assume paid subscriptions. Steep learning curve; macOS/Windows only (no Linux); proprietary file formats complicate open pipelines.

**Cost and licensing.** Subscription-based; single-app and Creative Cloud plans exist [verify current pricing]. Some regions/education tiers differ.

**Relevant workflows.** Vector logo construction on grids, colour separations, export to EPS/PDF/SVG for print and web, integration with the wider Adobe pipeline.

**Alternatives.** Affinity Designer (one-time licence), Inkscape (free, open source), CorelDRAW (Windows-centric).

### 4.2 Adobe Photoshop

**Primary purpose.** Raster image editor: photo retouching, compositing, print pre-press, texture and treatment work.

**Best use cases.** Photography post-production for brand imagery ([Photography](../imagery/photography.md)); compositing campaign visuals; preparing images for print with CMYK conversion and soft-proofing.

**Limitations.** Subscription cost; heavy system requirements; overkill for simple social graphics, where Canva-class tools are faster (section 5); raster output does not scale — vector work belongs in Illustrator or Affinity Designer.

**Cost and licensing.** Subscription-based [verify current pricing]; Photography-plan bundle historically the cheapest legal route to Photoshop + Lightroom.

**Relevant workflows.** Non-destructive editing with layers and smart objects; batch actions for sized derivatives of campaign imagery; export presets for web formats.

**Alternatives.** GIMP (free), Affinity Photo (one-time licence), Krita (free, painter-oriented), Photopea (browser-based, freemium).

### 4.3 Affinity Designer

**Primary purpose.** Professional vector (and mixed vector/raster) design application sold without subscription.

**Best use cases.** Logo, icon and illustration production when a paid tool is acceptable but subscriptions are not; print work with full CMYK; a credible Illustrator substitute for most identity work.

**Limitations.** Smaller plugin/scripting ecosystem than Adobe; some print vendors assume Adobe file formats; version-2 licensing terms changed relative to version 1 — verify whether the current release is one-time purchase or has subscription elements before buying [verify current licensing].

**Cost and licensing.** Historically a one-time purchase per platform [verify current pricing and licence model]. Note for agents: Adobe completed an acquisition of the Affinity business in 2024 [verify current product direction], so the classic "no subscription" positioning should be re-checked rather than assumed.

**Relevant workflows.** Precise vector logo construction with symbols and constraints; persona switching between vector and raster modes; export presets matching print/vendor specs.

**Alternatives.** Illustrator (industry standard), Inkscape (free).

### 4.4 Inkscape

**Primary purpose.** Free and open-source vector editor (SVG-native) for logo construction, icons and print-ready vector artwork.

**Best use cases.** Zero-budget identity work; SVG-centric pipelines (the web's vector format); agents producing editable vector deliverables without licensing constraints; scripted/automated SVG manipulation via its command-line interface.

**Limitations.** UI is less polished than commercial rivals; CMYK support is weaker than print-professional tools — fine for PDF/X export via workarounds but check vendor requirements; performance degrades on very complex artwork; no native multi-artboard model comparable to Adobe's.

**Cost and licensing.** Free and open source under the GNU GPL [stable, well-established — verify current version].

**Relevant workflows.** SVG-first logo drawing with layers and alignment tools; path boolean operations for mark construction; document/export scripting for batch asset generation.

**Alternatives.** Illustrator, Affinity Designer, Vectr/Boxy SVG (simpler browser tools).

### 4.5 GIMP

**Primary purpose.** Free and open-source raster editor covering most photo-editing and compositing needs.

**Best use cases.** Image sizing, colour adjustment, cropping and format conversion for web and social deliverables; compositing on a zero budget; scriptable batch processing via Script-Fu.

**Limitations.** UI and workflow ergonomics trail Photoshop; CMYK and soft-proofing support is limited, making it weak for serious print pre-press; some professional plugins absent. It is free, and for the jobs listed above it is capable — but do not claim it replaces Photoshop for colour-critical print work.

**Cost and licensing.** Free and open source under the GNU GPL [stable, well-established — verify current version].

**Relevant workflows.** Batch resize/format conversion of image sets; basic retouching; export to web formats with compression control.

**Alternatives.** Photoshop, Affinity Photo, Krita (stronger for digital painting), Photopea.

## 5. Fast content production

### 5.1 Canva

**Primary purpose.** Template-driven browser design tool for fast production of social posts, presentations, documents and simple collateral by non-specialists.

**Best use cases.** High-volume, deadline-driven content where the brand can be expressed through templates: social calendars, slide decks, simple posters. Brand Kit features (logo upload, palette and font locking) exist to keep non-designers on-system [verify which Brand Kit capabilities are free vs paid before relying on them].

**Limitations.** Template gravity: output converges on Canva's house look unless templates are custom-built; limited vector control for logo work (do not produce primary logo assets in Canva); export formats are serviceable but not print-production grade in the free tier (bleed/CMYK handling limited); offline work impossible. For an agent, its value is speed, not identity-system construction.

**Cost and licensing.** Direct fetch of the pricing page was blocked (HTTP 403) this session. [search-verified] from Canva's own pricing page snippet: K-12 educational organisations and not-for-profits can access most premium features free. Third-party reporting [search-verified, dated July 2026, treat as unverified] puts Canva Pro at about US$18/month or US$144/year with free-plan storage around 5 GB. Verify current pricing before any budget assumption.

**Relevant workflows.** Define brand colours/fonts once, then template the recurring formats ([Social media](../applications/social-media.md), [Presentations](../applications/presentations.md)); lock templates before handing to non-designers.

**Alternatives.** Adobe Express, Figma Slides/FigJam for lightweight decks, Penpot + custom templates for open pipelines.

## 6. AI-assisted imagery

**Standing warnings.** Capabilities, models and prices in this category change monthly; nothing here should be quoted from memory at use time. Rights questions dominate: training-data provenance, output copyright status and commercial-use terms vary by vendor and jurisdiction — the repository's detailed treatment lives in [AI image generation](../imagery/ai-image-generation.md) and [Image rights](../imagery/image-rights.md). For brand work, prefer tools that offer indemnification or clear commercial terms, and always keep AI imagery consistent with the brand's [image treatment](../imagery/image-treatment.md) rules.

### 6.1 Adobe Firefly

**Primary purpose.** Adobe's generative image family, integrated into Creative Cloud and available standalone; trained with an emphasis on licensed/Adobe Stock content and positioned for commercially safe use.

**Best use cases.** Imagery inside Adobe workflows; organisations that need a vendor position on commercial safety; style-matching to existing brand assets.

**Limitations.** Quality competitive but not always class-leading; generative credits constrain volume [verify current credit model]; brand consistency across generations still needs art direction ([Art direction](../graphic-design/art-direction.md)).

**Cost and licensing.** Bundled credits with Creative Cloud subscriptions; standalone free tier has existed [verify current plan and credit limits]. Indemnification terms apply to enterprise plans [verify].

**Alternatives.** Midjourney, Stable Diffusion (self-hosted), DALL·E/ChatGPT image tools, Ideogram (strong text rendering).

### 6.2 Midjourney

**Primary purpose.** Independent text-to-image service known for strong aesthetics; prompt-driven via web interface (Discord historically).

**Best use cases.** Moodboards and concept exploration ([Moodboards](../methodology/moodboards.md)); campaign-quality illustration and imagery where style freedom matters more than exact reproducibility.

**Limitations.** No free tier as of the repository's recorded terms [search-verified via repository citation of Midjourney's Terms of Service]; limited fine control and reproducibility (seed/model drift); commercial terms and default licence scope must be read from the current ToS before client use — see [Image rights](../imagery/image-rights.md).

**Cost and licensing.** Subscription-based with paid tiers [verify current pricing]. Verify commercial-use rights per tier.

**Alternatives.** Firefly for commercially safer workflows; Stable Diffusion for self-hosted control; Ideogram for typography-bearing images.

### 6.3 Other notable tools

- **Stable Diffusion (open weights)** — self-hostable, fully controllable, fine-tunable to a brand's style; requires technical setup and GPU resources; licence/terms per model version [verify per release].
- **DALL·E / ChatGPT image generation (OpenAI)** — conversational iteration, strong instruction-following; terms of use govern ownership and usage [search-verified via repository citation of OpenAI's terms; verify current terms].
- **Ideogram, Flux and similar** — compete on prompt fidelity and in-image text rendering [verify current capabilities].
- For non-generative sourcing, licensed stock and free-licence libraries are often the better choice — see [Image selection](../imagery/image-selection.md).

## 7. Colour

### 7.1 Coolors

**Primary purpose.** Fast palette generation and exploration: palette generator with lock/refine workflow, contrast checking, palette extraction from images.

**Best use cases.** Early-stage palette ideation ([Palette development](../colour/palette-development.md)); generating candidate ramps quickly; sharing palettes with clients as links.

**Limitations.** Generated palettes are not automatically accessible — check contrast separately ([Colour accessibility](../colour/colour-accessibility.md)); web tool gates some features behind accounts/pro tier [verify current feature gates].

**Cost and licensing.** Free core with Pro features [verify current pricing]. 

**Alternatives.** Adobe Color, internal token files, palette functions in design tools.

### 7.2 Adobe Color

**Primary purpose.** Adobe's colour web service: harmony-rule exploration from a colour wheel, extraction from images, accessibility checking (contrast deficiency simulation) and theme sharing.

**Best use cases.** Harmony-rule-based palette construction tied to colour theory ([Colour theory](../colour/colour-theory.md)); simulating how palettes read under colour-vision deficiency; capturing palettes from reference photography.

**Limitations.** Requires an Adobe account for saving/sharing; harmony output still needs manual contrast verification against WCAG thresholds.

**Cost and licensing.** Free with an Adobe account [verify current state].

**Alternatives.** Coolors; the accessibility checkers below; building scales directly in OKLCH in code ([Colour in code](../colour/colour-in-code.md)).

### 7.3 Accessible colour contrast checkers

**Primary purpose.** Verifying foreground/background contrast ratios against WCAG thresholds (1.4.3 minimum 4.5:1 for normal text, 3:1 for large text and UI; 1.4.11 non-text 3:1) — the canonical numbers live in W3C's Understanding documents (https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html, https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).

**Best use cases.** Checking palette pairs before committing them to tokens; auditing existing UI; validating colour-on-image overlays. Well-known checkers: WebAIM Contrast Checker (webaim.org/resources/contrastchecker), browser extensions and built-in checks in tools like Stark for Figma [verify current availability].

**Limitations.** Contrast ratio is necessary but not sufficient for accessibility — it cannot catch contrast-between-adjacent-colors issues, colour-blindness confusion beyond simulation, or motion/animation issues (see [Accessibility testing](../accessibility/accessibility-testing.md) for the full test stack).

**Cost and licensing.** WebAIM's checker is free [stable, well-established].

**Alternatives.** Compute ratios directly in code (WCAG formula) during token builds — preferable in automated pipelines ([Design tokens](../design-systems/design-tokens.md)).

## 8. Typography

### 8.1 Google Fonts

**Primary purpose.** Google's library of open-source-licensed web fonts with stylesheet-based serving and download.

**Best use cases.** Zero-cost, commercially safe typography for web and products: the developer documentation [verified this session] states all fonts are released under open-source licences and may be used in any non-commercial or commercial project. Serving via a stylesheet link is the documented path; families can also be downloaded for self-hosting [self-hosting not discussed on the fetched page — verify current download/self-host flow on fonts.google.com].

**Limitations.** Ubiquity: the most popular families read as generic because everyone uses them — a distinctiveness problem for brand work ([Typeface selection](../typography/typeface-selection.md)); selection quality varies; pairing requires deliberate work ([Font pairing](../typography/font-pairing.md)). The Fonts Developer API can query the available family list programmatically [verified this session].

**Cost and licensing.** Free, open-source licences (OFL/Apache/UFL families dominate the catalogue [well-established; verify per family — licence appears on each family's page]). Commercial use permitted [verified this session].

**Relevant workflows.** Choose families, then self-host with subsetting for performance ([Web typography](../typography/web-typography.md)) or serve via Google's CSS API for speed of setup.

**Alternatives.** Fontsource (section 8.2), commercial foundries and marketplaces for exclusivity.

### 8.2 Fontsource

**Primary purpose.** Self-hosting made convenient: open-source fonts packaged as npm packages for direct installation into JavaScript/frontend projects.

**Best use cases.** Frontend projects that want versioned, dependency-managed fonts without third-party runtime requests — improves performance, privacy and reliability versus CDN font loading; aligns font versions across environments.

**Limitations.** Catalogue is a subset of available open-source fonts [verify current catalogue coverage]; adds a package dependency per family; not a discovery tool for new typefaces.

**Cost and licensing.** Free and open source (MIT-licensed project distributing openly licensed fonts) [well-established; verify current licence and coverage].

**Relevant workflows.** `npm install @fontsource/<family>`, import weights in the app entry, subset further if needed; pairs with token pipelines ([Design tokens](../design-systems/design-tokens.md)).

**Alternatives.** Google Fonts CSS API (fastest setup), self-hosting raw files from Google Fonts downloads.

### 8.3 Font pairing and specimen tools

**Primary purpose.** Testing and choosing typeface combinations: interactive specimen and pairing sites (for example Typewolf's recommendations and Fontpair for Google Fonts combinations [general knowledge; verify current availability]) plus in-tool sample boards.

**Best use cases.** Evaluating candidate pairings on real copy before committing ([Font pairing](../typography/font-pairing.md)); checking weights/axes availability; building specimen sheets for brand documentation.

**Limitations.** Curated pairings are starting points, not endorsements for your context; specimens render idealised copy — always re-test with the project's actual text and sizes.

**Cost and licensing.** Pairing/specimen sites are predominantly free to browse [verify per site].

**Alternatives.** Build a specimen page in the actual product; use font-family testing inside Figma/Penpot libraries.

## 9. Frontend implementation

### 9.1 CSS

**Primary purpose.** The web's styling language — the final medium in which every digital brand decision lands: colour, type, spacing, layout, motion and state.

**Best use cases.** All web deliverables. Modern CSS (custom properties, `oklch()` colour, grid/flex layout, container queries) implements most design-system needs natively [see MDN references in [Colour in code](../colour/colour-in-code.md) and [Responsive layouts](../layout/responsive-layouts.md)].

**Limitations.** Consistency at scale requires discipline: raw CSS without tokens drifts; cross-browser differences persist at the edges; print fidelity is limited.

**Cost and licensing.** Free; standardised by W3C/WHATWG [stable].

**Relevant workflows.** Tokens as custom properties; component-scoped styles; design-system CSS architecture documented in [Frontend implementation](../ui-ux/frontend-implementation.md).

### 9.2 Tailwind CSS

**Primary purpose.** Utility-first CSS framework: styling composed from small single-purpose utilities generated from a config/token file.

**Best use cases.** Rapid, consistent UI construction when a team adopts its conventions; enforcing spacing/colour/type scales mechanically through the config; good fit for agent-generated frontends because utility output is predictable and diffable.

**Limitations.** Encodes its own scale conventions, which can silently override a brand's intended rhythm if unconfigured; utility-heavy markup hurts readability for newcomers; requires build tooling; class soup risk without component abstraction.

**Cost and licensing.** Free and open source (MIT) for the core framework [stable, well-established — verify current version and any paid adjacent offerings].

**Relevant workflows.** Define brand scales in the theme config (colours, type, spacing) so utilities emit token-consistent output; combine with design tokens via CSS custom properties ([Design tokens](../design-systems/design-tokens.md)).

**Alternatives.** Plain CSS with custom properties, CSS Modules, component-library frameworks (e.g. Bootstrap for opinionated defaults [verify current relevance]).

### 9.3 Storybook

**Primary purpose.** Workshop for building and documenting UI components in isolation across frameworks, with controls, docs pages and visual/interaction testing hooks.

**Best use cases.** Component systems: browsing states of every component; documenting usage next to live code; regression testing via snapshot/interaction addons. It is the standard living-documentation layer for component systems ([Component systems](../design-systems/component-systems.md), [Documentation](../design-systems/documentation.md)).

**Limitations.** Setup and maintenance cost; docs drift from code if not enforced; does not design — it documents built components, so it complements rather than replaces design tools.

**Cost and licensing.** Free and open source (MIT) [well-established — verify current version].

**Relevant workflows.** One story per component state; accessibility addons (see section 10); publish as the team's reference UI.

**Alternatives.** Framework-native playgrounds (HMR dev pages), custom documentation sites, design-tool-based libraries.

### 9.4 Design token pipelines

**Primary purpose.** Single-source design values (colour, type, spacing, radii) transformed into platform artefacts — CSS custom properties, Sass variables, iOS/Android assets, documentation — so every platform reads the same truth.

**Key tools.** Style Dictionary (open-source build system by Amazon; transforms token JSON into platform outputs [repository-cited: https://github.com/style-dictionary/style-dictionary, https://styledictionary.com]); the Design Tokens Community Group draft format as the emerging interchange standard [repository-cited: https://www.designtokens.org/TR/drafts/format/ — draft status, verify current adoption]; Figma variables as the design-side source; Tokens Studio as a popular Figma plugin for exporting token files [verify current plugin status].

**Best use cases.** Any multi-platform or multi-team brand: define once, transform everywhere; automated accessibility checks on token pairs before build ([Colour accessibility](../colour/colour-accessibility.md)).

**Limitations.** Pipeline complexity (build steps, sync between design tool and repo); DTCG format still stabilising; governance needed or token files rot ([Brand governance](../branding/brand-governance.md)).

**Cost and licensing.** Style Dictionary free/open source [stable]; plugin and sync-tool pricing varies [verify current pricing].

**Alternatives.** Hand-maintained CSS custom properties (fine for small systems), framework-specific theming.

### 9.5 Figma-to-code workflows

**Primary purpose.** Translating design-tool files into production frontends: from manual Dev Mode inspection to code generators and plugins.

**Best use cases.** Handoff inspection (measurements, tokens, assets) is mature and reliable; generated code suits boilerplate and prototypes; AI-assisted generation (including MCP-based flows in Figma and Penpot) is improving quickly [capabilities change monthly — verify current state before relying on generated code for production].

**Limitations.** Generated code is rarely production-grade without refactoring: semantics, accessibility and responsive behaviour need engineering review; token mapping must exist on both sides or values drift. Treat generation as an accelerator, not a substitute for the implementation guidance in [Frontend implementation](../ui-ux/frontend-implementation.md).

**Cost and licensing.** Inspection is included in Figma seat types (Dev Mode gated per the seat table [verified this session]); generator plugins vary [verify per plugin].

**Alternatives.** Penpot's code-first inspection; direct build from annotated specs; design-engineer pair work.

## 10. Accessibility

### 10.1 WAVE

**Primary purpose.** WebAIM's web accessibility evaluation tool: in-browser overlay annotating a page with errors (missing alt text, contrast failures, empty links) and structural features (headings, landmarks, ARIA).

**Best use cases.** Fast first-pass audits and teaching: the visual overlay makes issues concrete for designers, not just QA engineers. Use after any layout or content change ([Website visual QA](../evaluation/website-visual-qa.md)).

**Limitations.** Automated checks catch only a minority of WCAG issues — manual keyboard, focus and screen-reader testing remain mandatory; single-page scope.

**Cost and licensing.** Free browser extension and web tool [stable, well-established — verify current version].

**Alternatives.** axe DevTools, Lighthouse, site-wide crawlers for large estates.

### 10.2 axe (Deque)

**Primary purpose.** Accessibility rules engine (axe-core) embeddable in tests and browser DevTools; the de-facto standard automated rules library, powering many integrations.

**Best use cases.** CI-integrated accessibility regression: run axe-core in unit/E2E tests so contrast, labels and ARIA regressions fail builds. For agent-built frontends this is the cheapest continuous guarantee ([Accessibility testing](../accessibility/accessibility-testing.md)).

**Limitations.** Automated rules cover a subset of WCAG success criteria; results must be triaged — violations need fixes, incompletes need human review.

**Cost and licensing.** axe-core free and open source (MPL) [well-established — verify current licence]; Deque's DevTools Pro and training are paid [verify current pricing].

**Alternatives.** Lighthouse audits, WAVE for visual review, Pa11y CI runners.

### 10.3 Lighthouse

**Primary purpose.** Chrome DevTools/CI auditing for performance, accessibility, SEO and best practices, returning scored reports.

**Best use cases.** Broad quality gates during development and in CI (headless runs); accessibility category gives a quick scored view that drives axe-core underneath for part of its checks.

**Limitations.** Scores are environment-sensitive; accessibility scoring is coarse (binary passes within the audited subset); not a substitute for manual assistive-technology testing.

**Cost and licensing.** Free, open source, shipped with Chrome [stable — verify current docs at developer.chrome.com/docs/lighthouse].

**Alternatives.** PageSpeed Insights for hosted reporting, WebPageTest for deeper performance work.

### 10.4 W3C contrast guidance

**Primary purpose.** The normative source for contrast requirements: WCAG 2.2 Understanding documents define the ratios (4.5:1 / 3:1 thresholds under SC 1.4.3 and 1.4.11) and the definitions (large text, incidental text, UI components).

**Best use cases.** Settling disputed contrast questions and writing token rules: cite the Understanding page, not a blog ([WCAG fundamentals](../accessibility/wcag-fundamentals.md)).

**Limitations.** Ratios are thresholds, not aesthetics guidance; the APCA community debate on perceptual contrast is not part of the current normative text [verify current status of WCAG 3 drafts before citing].

**Cost and licensing.** Free, open standards [stable].

**Companions.** WAI tutorials for images and structure; the checkers in section 7.3 implement these numbers.

## 11. Tool selection by task

| Task | Default choice (no budget assumed) | Upgrade path | Avoid |
| --- | --- | --- | --- |
| Logo construction | Inkscape (free) | Affinity Designer / Illustrator | Canva — no vector control |
| Photo retouching | GIMP | Photoshop / Affinity Photo | — |
| UI/screen design with collaboration | Penpot (free, open) | Figma (Starter free; paid for libraries) | — |
| Design tokens | Figma variables / Penpot tokens + Style Dictionary | Commercial sync tools | Hand-synced values across files |
| Social/content templates | Canva free tier + brand palette/fonts | Canva Pro Brand Kit | Building primary identity assets there |
| Palette exploration | Coolors / Adobe Color | — | Trusting generated palettes without contrast checks |
| Contrast verification | WCAG formulas in code; WebAIM checker | Stark/axe integrations | Eyeballing |
| Web fonts | Google Fonts / Fontsource (self-host) | Commissioned or licensed foundry faces | Unlicensed "free download" sites |
| AI imagery | Vendor free tiers for exploration | Paid tiers for production volume | Using output without checking rights terms |
| Component documentation | Storybook | Zeroheight-class SaaS [verify pricing] | Static slide decks as docs |
| Accessibility audit | WAVE + Lighthouse + axe-core in CI | Deque DevTools Pro, expert audit | Automated checks alone |

The default column works at zero cost and is genuinely production-capable; the upgrade path is justified when collaboration scale, print colour fidelity, or support contracts are real requirements — not hypothetical ones.

## 12. Common mistakes

- **Assuming paid subscriptions.** Building a workflow that requires Pro seats locks out agents and small organisations; design the pipeline so the free tier of each tool suffices, then pay only for verified bottlenecks.
- **Choosing free over capable.** GIMP cannot replace Photoshop for CMYK print pre-press, and Canva cannot build a logo system; the licence saving evaporates when the deliverable has to be redone professionally.
- **Quoting prices from memory.** Every price in this file decays; the only safe formulation is the verified date plus "verify current pricing" ([Source accessibility](source-accessibility.md)).
- **Letting generated code ship unreviewed.** Figma-to-code output without semantic, responsive and accessibility review produces inaccessible markup that looks finished.
- **One tool for every job.** Vector, raster, layout and content tasks have different optimal tools; forcing one application produces mediocre artefacts and slow work.
- **Ignoring licence scope, not just price.** A free asset with a non-commercial licence is unusable for a client event; check usage terms, not just cost ([Image rights](../imagery/image-rights.md)).
- **Skipping the manual accessibility pass.** WAVE/Lighthouse/axe catch a minority of issues; keyboard, focus and screen-reader checks are still required ([Accessibility testing](../accessibility/accessibility-testing.md)).

## 13. Evaluation checklist

Before committing a tool to a project pipeline:

- [ ] Cost verified against the vendor's page this session, and the project works on the free tier if no budget is confirmed.
- [ ] Licence terms cover the actual use (commercial, print, redistribution where relevant).
- [ ] Output formats match the deliverable's requirements (vector for logos, CMYK for print, accessible markup for web).
- [ ] The tool integrates with the token pipeline rather than introducing a second source of truth ([Design tokens](../design-systems/design-tokens.md)).
- [ ] Alternatives were compared on capability, not on price alone.
- [ ] A re-verification date exists for volatile facts (pricing, plan limits, AI capabilities).
- [ ] The choice is recorded with its rationale so the next agent can audit it.

## 14. Related topics

- [Design tokens](../design-systems/design-tokens.md) — the pipeline section 9.4 implements.
- [Component systems](../design-systems/component-systems.md) and [Design system documentation](../design-systems/documentation.md) — where Storybook fits.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — CSS architecture behind section 9.
- [Colour accessibility](../colour/colour-accessibility.md) and [Accessibility testing](../accessibility/accessibility-testing.md) — the verification stack behind sections 7.3 and 10.
- [Web typography](../typography/web-typography.md) — loading and licensing fonts in practice.
- [AI image generation](../imagery/ai-image-generation.md) and [Image rights](../imagery/image-rights.md) — the theory and law behind section 6.
- [Source accessibility](source-accessibility.md) — provenance rules for the verified/unverified markers used here.
- [Bibliography](bibliography.md) and [Professional guidelines](professional-guidelines.md) — source context for this file's claims.

## 15. References

Verified this session (accessed 2026-11-24):

- Figma, "Pricing" — plan table, seat types, Starter limits, variables-mode counts, AI-credit allowances. https://www.figma.com/pricing/ [accessed; re-verified in a same-day pass]
- Penpot, homepage — open-source positioning, free sign-up, self-hosting, native design tokens, open file format, MCP server. https://penpot.app/ [accessed]
- Google Fonts, developer documentation — open-source licences, free commercial use, stylesheet serving, Fonts Developer API. https://developers.google.com/fonts/ [accessed]

Search-verified this session:

- Canva, "Plans and pricing" page (fetch blocked; snippet only) — free premium access for K-12 and not-for-profits. https://www.canva.com/en/pricing [search-verified]
- Third-party Canva pricing report, July 2026 (snippet) — treat as unverified. [search-verified]

Cited in the repository (pages not fetched this session):

- Style Dictionary. https://styledictionary.com and https://github.com/style-dictionary/style-dictionary [search-verified via repository citations]
- Design Tokens Community Group draft format. https://www.designtokens.org/TR/drafts/format/ [search-verified via repository citations]
- Storybook, "Why Storybook". https://storybook.js.org/docs/get-started/why-storybook [search-verified via repository citations]
- W3C/WAI WCAG 2.2 Understanding: Contrast Minimum and Non-Text Contrast. https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html, https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html [search-verified via repository citations]
- WAVE. https://wave.webaim.org/ ; axe. https://www.deque.com/axe/ ; Lighthouse. https://developer.chrome.com/docs/lighthouse/overview/ [search-verified via repository citations]
- Midjourney Terms of Service; OpenAI terms of use. https://docs.midjourney.com/hc/en-us/articles/32083055291277-Terms-of-Service, https://openai.com/policies/row-terms-of-use [search-verified via repository citations]

Unmarked entries throughout sections 4–10 (Illustrator, Photoshop, Affinity, Inkscape, GIMP, Coolors, Adobe Color, Fontsource, Tailwind, and capability descriptions generally) are the author's synthesis of long-established general professional knowledge; where a claim is volatile it is marked "verify current" in the text, per [Source accessibility](source-accessibility.md).
