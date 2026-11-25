# Contributing Inspiration

## 1. What is it?

The workflow agents follow to add references to the inspiration library — the evaluation bar, the inspection method, the entry template, the index update, and the commit conventions — plus the anti-copying rules that govern how references translate into project work. It exists so the collection grows honestly: no duplicates, no unverified links, no transplanted designs.

## 2. When to contribute

Whenever project work surfaces an exceptional site: during phase 3 of the frontend workflow ([../../skills/frontend-design/SKILL.md](../../skills/frontend-design/SKILL.md) research phase), during asset searches, or during QA research. The bar (§3) filters; contribution is not automatic.

## 3. The evaluation bar

A site is worth adding when at least three of these hold:

1. **Craft above category** — execution quality visibly exceeds the site's industry norm.
2. **A named lesson** — the site demonstrates a move worth teaching (a pattern, a system, a discipline).
3. **Durability** — the site's value is not a single campaign moment that will vanish (or the entry records the campaign and its date).
4. **Distinctiveness with system** — memorable *and* internally coherent (novelty alone is not craft).
5. **Legal clarity** — publicly accessible, no authentication bypass needed to study it.

## 4. Inspecting the site

Use available browser automation (the library is tool-agnostic — see [../../evaluation/website-visual-qa.md](../../evaluation/website-visual-qa.md) §8 for the capability model):

- **Capture what is permitted:** full-page and viewport screenshots for *internal reference material* where technically practical. Store captured material in the repository only when legally and technically appropriate — screenshots of public marketing pages for study purposes are generally acceptable; **never scrape behind authentication, bypass access restrictions, or copy protected assets or source code**.
- **Record observations, not copies:** the entry template's fields are the deliverable. Note navigation, interactions, responsive behaviour, scroll effects, motion hierarchy.
- **Check the facets:** the visual style(s) (name them with the [visual-styles vocabulary](../../visual-styles/README.md)), typography approach, colour behaviour, notable sections.
- If automation is unavailable, a good structured entry with the direct URL is still valuable — the template works from careful manual inspection.

## 5. Writing the entry

Follow the 16-field template ([websites/README.md](websites/README.md) §4) exactly. Rules:

- **Provenance:** record the access date; describe design direction from what you actually observed; mark volatile specifics in *what to verify live*; never invent tech stacks, metrics or quotes ([../../README.md](../../README.md) §H).
- **Honesty about limits:** if you could not inspect something (mobile, WebGL on your hardware), say so in the entry.
- **Style naming:** use the library's vocabulary so the index facets stay consistent.
- **Placement:** `inspiration/websites/references/<slug>.md` with a stable, lowercase-hyphen slug.

## 6. The anti-copying rules

These govern every use of the collection, not just contributions:

1. **Study the why, build your own what.** A reference informs decisions (hierarchy, palette behaviour, motion hierarchy); it is never transplanted (markup, styles, assets, copy).
2. **No code, copy, asset or signature-effect copying.** The taste-skill states it as its own "never" ([../../skills/taste/SKILL.md](../../skills/taste/SKILL.md) §6); the library enforces it everywhere.
3. **Significant inspiration is disclosed** in project notes — "the pricing layout follows the Stripe transparency pattern" is honest practice; silent imitation is not.
4. **No clone requests.** "Rebuild X's site" briefs are redirected to "build this product's site using the same *kind* of system" ([../../methodology/research-and-discovery.md](../../methodology/research-and-discovery.md)).
5. **Trademarks and brands stay theirs.** Brand marks are used to identify real products ([../../assets/icons.md](../../assets/icons.md) Simple Icons policy), never to decorate or imply endorsement.

## 7. Updating the index and patterns

- Add the entry to **every relevant facet** of [websites/website-index.md](websites/website-index.md) (industry, style, sections, interaction, typography, colour, project type).
- If the entry demonstrates a new named move, add the pattern to [../patterns.md](../patterns.md) with its reference trace, in the same commit.
- Check for duplicates first: search the index for the site and its obvious aliases.

## 8. Commit conventions

Follow the repository's per-file discipline ([../../PROJECT_STATUS.md](../../PROJECT_STATUS.md) §10):

```text
docs(inspiration): reference — <Name> (<one-line position>)
docs(inspiration): index — add <Name> to <facets>
docs(inspiration): patterns — add <pattern name> from <Name>
```

One commit per file; the index and pattern changes are separate commits traceable to the entry that caused them.

## 9. Common mistakes

- **Contributing below the bar** — "nice site" is not a named lesson; the evaluation bar is three-of-five.
- **Inventing specifics** — unobserved tech stacks or metrics; the provenance rules treat this as fabrication.
- **Index skipped** — an entry not indexed does not exist for routing ([websites/website-index.md](websites/website-index.md) §3).
- **Storing scraped assets** — screenshots for study where appropriate; never protected assets or source code.
- **Pattern without a trace** — a pattern with no reference trace is an opinion, not knowledge.

## 10. Related topics

- [Website collection](websites/README.md) — the template this workflow feeds.
- [Directories](directories.md) — where candidates are discovered.
- [Patterns](patterns.md) — the extraction layer.
- [Skills/frontend-design](../../skills/frontend-design/SKILL.md) — phase 7 (preserve knowledge) invokes this file.
- [Case studies](../../references/case-studies.md) — identity-level analyses in the source layer (different unit: brand systems, not sites).
