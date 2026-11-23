# Image treatment

## 1. What is it?

Image treatment is the layer of post-capture processing and graphic handling applied to photographs: colour grading, duotone and colour overlays, cropping, masking, borders and frames. In a brand system, treatment is what turns images from heterogeneous sources — commissioned shoots, stock, archives, generated plates — into one recognisable family. It is also a technical discipline: preparing images at the right resolution, in the right format, at the right compression, with the right accessibility text, and delivering them responsively on the web.

The brand decision (is treatment part of the identity, and which treatments) belongs with [Photography](photography.md) and [Visual identity](../branding/visual-identity.md). This file covers the treatments themselves, the recipes, and the technical preparation needed for an image to perform on screen without breaking accessibility or performance.

## 2. Why does it matter?

Treatment solves the coherence problem directly. Every library mixes sources with different white balance, contrast and saturation; a single shared grade erases most of that difference, which is why grading is often called the great equaliser. Treatment also adds ownability: a duotone in brand colours or a signature crop style becomes a recognisable fingerprint that survives even when the underlying photos change — viewers recognise the treatment before they recognise the subject.

The technical half matters because it is where good-looking designs fail in production. An image exported without compression planning turns a fast page into a slow one; a missing `alt` attribute excludes screen-reader users (and fails WCAG 1.1.1 Non-text Content, Level A — see the W3C WAI Images Tutorial, which states that "Images must have text alternatives that describe the information or function represented by them" [accessed]); an over-tall hero shipped to phones wastes data and time. Treatment decisions therefore have quality, accessibility and performance consequences simultaneously.

## 3. Core principles

**Unify without falsifying.** A grade should harmonise colour and tone while keeping the image truthful: protect skin tones, avoid shifting a recognisable brand colour past its tolerance, and never grade so hard that the subject becomes unreadable. The line between harmonising and misrepresenting matters legally as well as ethically — some licences restrict derogatory or misleading modification (see [Image rights](image-rights.md)).

**One system, not many.** One default grade, one duotone recipe, one overlay family — treatments scale by being few and defined. If every designer invents an overlay, the brand has none.

**Treatment serves legibility.** Overlays exist so text stays readable over images; duotones exist so images recede behind content. When the treatment destroys the image's information or the text's contrast, it has failed — text-over-image contrast follows the same ratios as text-on-colour (see [Colour accessibility](../colour/colour-accessibility.md)).

**Grade to a reference.** Consistency comes from comparing every treated image against one approved reference set, not from memory or feel.

**Decorative versus informative changes the rules.** A purely decorative treatment (background texture, washed-out backdrop) may be hidden from assistive technology with an empty `alt`; an informative image carries its meaning in its alt text regardless of treatment. The full decision logic is in [WCAG fundamentals](../accessibility/wcag-fundamentals.md).

## 4. How it works

### 4.1 The treatment vocabulary

**Colour grading.** The base treatment: shared adjustments to white balance, exposure, contrast, saturation and (optionally) a signature split-tone. As a conventional recipe applied to every image in a library: correct white balance first (aim all images into one temperature family), match exposure against the reference set, lift or set shadows per the style, protect skin tones from hue shifts, then apply the saved preset or LUT. Mechanics matter: one preset, applied identically, is what makes mixed sources match (see [Photography](photography.md), section 4.4).

**Duotone.** The photograph is reduced to a two-colour map — shadows mapped to one brand colour, highlights to another. Recipe (any editor): desaturate to greyscale; adjust the greyscale contrast so tones span the full range; map the gradient from colour A (dark) to colour B (light); optionally re-introduce 5–10% original luminosity detail so the subject stays readable. Duotones read as bold and graphic, and are the standard rescue for images that clash with the palette. A CSS equivalent uses blend modes:

```css
.duotone {
  background-color: var(--brand-dark);   /* colour A: shadows */
}
.duotone img {
  filter: grayscale(100%) contrast(1.1);
  mix-blend-mode: screen;                /* map highlights onto colour B */
  opacity: 0.85;
}
```

For crisp brand-colour output, bake the duotone into the exported file (gradient-map in an editor) rather than relying on runtime CSS; the CSS route is for prototypes and thumbnails.

**Colour overlays.** A flat or gradient brand colour laid over the image at partial opacity — most often to create a text-safe zone on heroes. Conventional starting points: 40–70% opacity for full overlays behind body text, or a gradient from ~80% at the text edge fading to ~10% across the image; always verify the resulting text contrast (WCAG's contrast minimums apply — see [Colour accessibility](../colour/colour-accessibility.md)). An overlay so heavy that the image becomes a dark rectangle means the underlying image was the wrong choice: re-select rather than hide it ([Image selection](image-selection.md)).

**Crops.** Cropping is treatment: a changed crop changes the image's meaning. Rules worth fixing brand-wide: retain master files uncropped ([Photography](photography.md), section 4.6); keep faces within safe zones (eyes in the upper third, no slicing through joints); plan the crop per delivery ratio rather than reusing one crop everywhere; and crop for the composition the slot needs, not whatever the master's centre happens to be.

**Masks.** Cropping into shapes — circles, arches, brand-symbol silhouettes. Masks tie imagery to the graphic language and can echo the logo's geometry (a masked image is distinct from the logo itself; the boundary rules around the logo live in [Fixed logo analysis](../branding/fixed-logo-analysis.md)). Use masks sparingly: one mask shape as a signature reads as intentional; many shapes read as a template store.

**Borders and frames.** Rules, rounded corners, inset frames or full-bleed handling. Full-bleed communicates immersion; framed images communicate editorial calm. A frame width or corner radius should reuse existing tokens from the design system rather than inventing values.

### 4.2 Technical preparation

**Resolution.** Prepare masters large enough for the largest intended use, then export down. Conventional starting points (verify against current device targets): web content images at ~1600–2400 px on the long edge; full-width heroes at 2400–2880 px wide; 2× exports for high-density screens of any fixed-size slot. Never upscale a small source to hit a target — softness cannot be graded away.

**Formats.** Each format has a job:

| Format | Best for | Notes |
| --- | --- | --- |
| AVIF | Modern photo delivery | Strong compression; verify browser support targets |
| WebP | General photo and UI imagery on the web | Broad support; good default |
| JPEG | Universal photo fallback | Quality 70–85 is the conventional sweet spot; progressive encoding for large files |
| PNG | Flat graphics, transparency, screenshots | Lossless; large for photos — not a photo format |
| SVG | Icons, logos, simple illustration | Vector, scales losslessly; not for photographs |

A robust delivery pattern is AVIF/WebP first with a JPEG fallback via the `<picture>` element, as shown below.

**Compression.** Compress once, at export, from the master. Re-compressing an already-compressed file doubles artefacts; this is the most common quality bug in real pipelines. Conventional targets to design against: content images roughly ≤ 200 KB, heroes ≤ 300–500 KB (verify against your performance budget). Pair compression with lazy loading (`loading="lazy"`) for below-the-fold images so heroes stay priority-loaded.

**Alt text basics.** Every `<img>` needs its text alternative decided at treatment time, not bolted on at QA. Per the W3C WAI Images Tutorial [accessed]: informative images get a short description of their essential information; decorative images get a null alternative (`alt=""`) so screen readers skip them; functional images (an image that is a link or button) describe the action, not the picture; images of text repeat the words verbatim; complex images (charts, diagrams) need a full text equivalent nearby. Related success criteria: WCAG 1.1.1 Non-text Content (A) and 1.4.5 Images of Text (AA). The WCAG detail and testing method live in [WCAG fundamentals](../accessibility/wcag-fundamentals.md). Treatment interacts with alt text directly: a duotone or overlay does not change what the image means, but a crop can (a wide scene cropped to a detail changes the essential information).

### 4.3 Responsive image behaviour

One file cannot serve every screen, so the browser needs alternatives. There are two problems with two separate mechanisms:

**Resolution switching (`srcset` + `sizes`) — same image, different sizes.** The browser picks the smallest candidate that still fills the slot. Widths (`w`) describe the file's intrinsic width; `sizes` describes the slot:

```html
<img
  srcset="scene-480w.jpg 480w, scene-800w.jpg 800w, scene-1600w.jpg 1600w"
  sizes="(width <= 600px) 480px, 800px"
  src="scene-800w.jpg"
  alt="Attendees in a sunlit workshop space" />
```

The browser considers viewport, pixel density and network, finds the first matching media condition in `sizes`, and loads the closest candidate — if no exact match, the first larger one, scaled down ([accessed] per MDN's Responsive images guide). For fixed-size images at high pixel density, the simpler `x` descriptors (`1x`, `2x`) replace `sizes`. Browsers without support fall back to `src`.

Two stability and performance complements belong with every delivery decision. First, reserve space for images in the layout — setting `width` and `height` (or an aspect-ratio rule) on the `<img>` prevents the page from reflowing when the file arrives, the layout-shift failure known as CLS; the dimensions describe the intrinsic image and are corrected by CSS sizing rules. Second, scope lazy loading honestly: `loading="lazy"` suits below-the-fold content, while heroes and any above-the-fold image should stay eager so the largest visible element renders fast (conventional practice — verify against the project's performance budget in [Frontend implementation](../ui-ux/frontend-implementation.md)).

**Art direction (`<picture>`) — different crops per context.** When mobile needs a tighter crop of the same photograph, `<picture>` swaps content:

```html
<picture>
  <source media="(width < 800px)" srcset="hero-800w-tight.jpg" />
  <source media="(width >= 800px)" srcset="hero-1600w-wide.jpg" />
  <img src="hero-1600w-wide.jpg" alt="Festival main stage at dusk" />
</picture>
```

The first matching `<source>` wins; the inner `<img>` (always present, with `src` and `alt`) is the fallback — this is where alt text lives. MDN's guidance: use `srcset` for resolution switching and `<picture>` for genuine art direction, not routinely. [accessed] Broader implementation context (performance budgets, caching, CDN resizing) lives in [Frontend implementation](../ui-ux/frontend-implementation.md).

## 5. Practical application

A treatment pipeline that holds a library together:

1. **Acquire** — masters archived uncropped and ungraded ([Photography](photography.md)).
2. **Grade** — apply the shared preset; compare against the reference set in a grid.
3. **Crop** — produce the ratio family the layout needs (16:9 hero, 1:1 grid, 4:5 social as a typical set).
4. **Treat** — apply duotone/overlay/mask only where the design system calls for it.
5. **Export** — per format table and compression targets; one pass from master.
6. **Deliver** — `srcset`/`sizes` (or `<picture>` for art-directed crops), lazy loading below the fold.
7. **Describe** — alt text decided per slot with the informative/decorative/functional test.
8. **Log** — record source, licence and modification status (see [Image rights](image-rights.md)); some licences constrain the modifications permitted.

Name exports so provenance survives handover: a conventional pattern is `subject_context_variant_size.format` (for example `courtyard_hero_warm_1600w.avif`), with masters kept in an originals directory that exports never overwrite. Names are the last line of defence against re-compressing a compressed file or shipping a draft: if a file's name does not say what it is, it does not go into the library. Generated plates follow the same pipeline from step 2 onward — they are just another acquisition path at step 1 ([AI image generation](ai-image-generation.md)).

## 6. Decision framework

Choose treatment per slot:

- **Default to the plain grade.** Clean, graded photography is the workhorse; treatment earns its place where there is a job to do.
- **Reach for duotone when** the source clashes with the palette, the image must recede behind content, or you want a signature graphic look across mixed-quality sources.
- **Reach for an overlay when** text sits on the image and contrast fails without it; prefer a gradient anchored at the text edge over a blanket dark wash.
- **Reach for a mask when** the system needs imagery tied to its graphic language (echoing logo geometry or grid shapes — [Grid systems](../layout/grid-systems.md)); limit to one signature shape.
- **No treatment** when the photograph's own realism is the message (testimonial, documentation) — heavy treatment on a truth-carrying image undermines it.
- **Format**: photos → AVIF/WebP with JPEG fallback; transparency or flat graphics → PNG; icons and simple marks → SVG.
- **Delivery**: same image at many sizes → `srcset` + `sizes`; different crops per screen → `<picture>`.

A treatment budget keeps the vocabulary honest — decide per context which treatments are allowed:

| Context | Allowed treatments |
| --- | --- |
| Documentary / testimonial imagery | Plain grade only |
| Content and article imagery | Grade, restrained crop |
| Hero imagery | Grade, overlay for text, art-directed crops |
| Backgrounds and social templates | Full vocabulary: duotone, masks, treatments |
| Logos and wordmarks | Never treated — real assets composited untouched |

## 7. Examples

- **Hero with text-safe zone.** A wide festival image, cropped 21:9, plus a bottom-anchored gradient overlay (80% → 10%) in a dark brand tone; headline contrast verified against the overlaid area; `sizes` written from the layout's actual slot widths; decorative context image hidden with `alt=""` only if it truly carries no information.
- **Mixed-source gallery unified by duotone.** Six sponsors' contributed photos of incompatible quality and colour, all run through one gradient-map duotone in brand colours — the gallery reads as designed despite the source chaos.
- **Art-directed hero.** Desktop shows a wide environmental crop of the venue; mobile swaps to a tight portrait crop via `<picture>` — same photograph, same alt text, two compositions, no overflow (see [Responsive layouts](../layout/responsive-layouts.md)).
- **The rescue that failed.** A meaningless handshake photo graded, duotoned and masked to fit the palette — every technique correct, still meaningless. Treatment cannot fix selection; re-run the sourcing decision ([Image selection](image-selection.md)).

## 8. Common mistakes

- **Double compression.** Exporting from an already-compressed source, producing banding and smearing. Always compress once, from the master.
- **Upscaling.** Interpolating a small image to hero size. Re-source instead.
- **Overlay as cover-up.** A near-black blanket hiding an unsuitable image and killing its information. Fix the selection.
- **Duotone everywhere.** The signature treatment applied to all images until the site reads as flat wallpaper. Budget treatments per context.
- **Contrast drift.** Text over an overlay that passes WCAG on the mock's brightest area but fails where the image is light. Verify contrast across the whole text area ([Colour accessibility](../colour/colour-accessibility.md)).
- **Missing or false alt text.** `alt="image"` on every photo, or an informative image left decorative (`alt=""`). Apply the WAI category test per slot [accessed].
- **One crop for every slot.** Reusing a 16:9 crop in a 1:1 tile and losing the subject. Export per ratio from the master.
- **Draft and master confusion.** Working files and graded exports living in the same directory, so an ungraded or draft image ships by accident. Fix with the originals/exports separation and the naming pattern in section 5.
- **Ignoring licence limits on modification.** Some licences (for example ND-type Creative Commons terms) forbid exactly the cropping and grading this file describes (see [Image rights](image-rights.md)).

## 9. Evaluation checklist

- One grading preset exists, and a grid review of the last ten treated images shows no style breaks.
- Duotone/overlay recipes are documented (colours, opacity, blend mode) and reused, not reinvented.
- Text-over-image contrast passes WCAG minimums across the entire text area.
- Every informative image has meaningful alt text; every genuinely decorative one has `alt=""`; functional images describe their action.
- Exports are single-pass from masters at documented resolutions; no upscaled files in the library.
- Photo delivery uses `srcset`/`sizes` (and `<picture>` where crops change per context) with a JPEG or `src` fallback.
- Below-the-fold images lazy-load; heroes stay priority-loaded.
- File sizes sit inside the performance budget (conventional targets: content ≤ 200 KB, heroes ≤ 300–500 KB).
- Treatments applied are permitted by each image's licence (no ND terms violated).
- Exports carry provenance-preserving names, and originals live in a directory exports never overwrite.
- Images reserve layout space via width/height or aspect-ratio rules, so pages do not reflow on load.
- Below-the-fold delivery is lazy-loaded and heroes stay eager, per the documented budget.
- Exports are single-pass from masters; no file in the library has been compressed twice.
- The treatment budget per context (section 6) is respected in the latest delivered set.
- Masters remain archived, uncropped and ungraded.

## 10. Related topics

- [Photography](photography.md) — the style and grade definitions that treatments implement.
- [Image selection](image-selection.md) — sourcing decisions that determine what treatment must fix.
- [AI image generation](ai-image-generation.md) — generated plates pass through the same treatment pipeline.
- [Image rights](image-rights.md) — licences constrain how far treatment may go.
- [WCAG fundamentals](../accessibility/wcag-fundamentals.md) — the accessibility requirements behind alt text and contrast.
- [Frontend implementation](../ui-ux/frontend-implementation.md) — performance, caching and delivery infrastructure.
- [Colour accessibility](../colour/colour-accessibility.md) — contrast ratios for text over overlays.
- [Grid systems](../layout/grid-systems.md) — slot sizes that drive `sizes` values and mask geometry.
- [Responsive layouts](../layout/responsive-layouts.md) — the layout contexts art-directed crops serve.

## 11. References

- W3C WAI, "Images Tutorial" (informative, decorative, functional, images of text, complex images; WCAG 1.1.1 and 1.4.5), https://www.w3.org/WAI/tutorials/images/. [accessed 2026-11-23]
- MDN Web Docs, "Responsive images" (`srcset`/`sizes`, `x` descriptors, `<picture>`, fallback behaviour), https://developer.mozilla.org/en-US/docs/Web/HTML/Responsive_images, including the adapted code examples above. [accessed 2026-11-23]
- Opacity ranges, resolution targets, compression settings and file-size budgets are conventional starting points, not standards; verify against current device targets and the project's performance budget.
- The treatment-budget table and the export-naming pattern are this file's own synthesis of the sources above and of standard production practice.
- Duotone and grading recipes are this file's own synthesis of standard photographic practice.
