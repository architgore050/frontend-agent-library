# Contributing

## 1. What this repository is

The **frontend-agent-library**: a Markdown knowledge base and skill set that makes AI coding agents better at designing and building websites — visually distinctive, accessible, fast and production-ready. Contributions are welcome in two layers: the **knowledge base** (design/UX/engineering knowledge, inspiration references, asset catalogues) and the **skills layer** (the `skills/` packages agents load). See the [README](README.md) for the library's structure and ground rules, and [PROJECT_STATUS.md](PROJECT_STATUS.md) for current coverage and thin spots.

## 2. Before you write

- **Inspect first.** Read the domain you are contributing to and the [README](README.md)'s routing rules. Do not duplicate an existing file — extend it ([website-visual-qa.md](evaluation/website-visual-qa.md) grew by adding §5.9, not by spawning a parallel QA file).
- **Follow the template.** Knowledge files use the standard 11-section numbered structure (what/why/principles/how/application/decision framework/examples/mistakes/checklist/related/references). Catalogue and reference files adapt it, but stay monotonic, end with References, and keep the house density: decision-usable statements, tables for comparisons, concrete examples.
- **House rules:** British spelling, English only; repository-relative cross-links (test every link before committing); no placeholder sections; content over length — a complete 150-line file beats a padded 400-line one.

## 3. Provenance (non-negotiable)

- Every factual claim carries a tag: `[accessed YYYY-MM-DD]` (you fetched and read it), `[search-verified YYYY-MM-DD]` (seen in search results only), `[canonical]` (attribution-level from professional knowledge — no quotes, figures or page numbers).
- Never invent URLs, capabilities, metrics, prices or licences. Fetch failures are recorded, not hidden — see [references/frontend-phase-sources.md](references/frontend-phase-sources.md) for the worked example.
- Volatile facts (prices, versions, repository statuses, licence terms) are re-verified before use in deliverables and dated when you verify them.
- Verification methods worth recording: note *how* you verified (HTTP check, GitHub API, browser inspection) so the next contributor can re-trace it.

## 4. Adding knowledge files

1. Choose the domain directory (create one only for a genuinely new domain — see [PROJECT_STATUS.md](PROJECT_STATUS.md) §3 for the current map).
2. Write the file on the template; cross-link at least three related files; end with tagged References.
3. Update the **router**: add the file to the [README](README.md) routing table (mandatory vs additional, respecting the minimum route) and to the repository map (section J). An unlinked file will not be found by agents — the router is the contract.
4. Update [PROJECT_STATUS.md](PROJECT_STATUS.md) (domain counts, completeness note).

## 5. Adding inspiration references

Follow [inspiration/contributing.md](inspiration/contributing.md): the three-of-five evaluation bar, the 16-field entry template, the faceted index update, and the anti-copying rules (study the why, never transplant code/copy/assets). Screenshots for study are acceptable where legally appropriate; never scrape behind authentication or copy protected assets or source code.

## 6. Extending the asset catalogues

Only verified sources: check the site live, record its licence (read the actual licence page), record the verification method and date, and add it to the right catalogue file ([assets/](assets/README.md)) with the same entry discipline as its neighbours. Unresolvable or ambiguous resources go to the unresolved list ([inspiration/directories.md](inspiration/directories.md) §9) — never invented into a URL.

## 7. Skills changes

- `skills/frontend-design/` (this library's own skill) — improvements welcome; keep it a router, not a textbook: new knowledge belongs in knowledge files it links to.
- `skills/taste/` and `skills/be-ambitious/` are **vendored upstream** — do not modify them. Fix bugs upstream; the update procedure is [skills/README.md](skills/README.md) §7.

## 8. Commit conventions

- **One commit per file**, message naming domain and slug: `docs(colour): palette-development — role-based palette construction and testing`.
- Root files (`README.md`, `PROJECT_STATUS.md`, `CONTRIBUTING.md`, `LICENSE`) get their own commits (`docs(root): …`).
- Never batch unrelated files; re-verification edits commit alone so access-date bumps stay traceable.
- README and PROJECT_STATUS updates land in the same change-set as the files that caused them (separate commits, same push).

## 9. Reporting defects

- A file whose guidance conflicts with its tagged source: fix the citing file, refresh its access date, commit it alone.
- A dead link: fix every referencing file, not just the router.
- Broken or misleading skill behaviour: report with the verification steps you ran (skills/README.md §5).
- Provenance errors (a wrong URL, a mis-tagged claim): correct the citing file and note the correction in the commit message.
