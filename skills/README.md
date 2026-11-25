# Agent Skills

## 1. What is this directory?

The library's executable layer: three agent skills that turn the knowledge base into practice. Skills are discoverable instruction packages (a `SKILL.md` with frontmatter plus supporting files) that agents such as Claude Code, Codex and compatible runtimes can load and follow. This file is the integration architecture: what each skill is, how they complement one another, how to install and verify them, and how to update the vendored ones without losing upstream work.

| Skill | Source | Role |
| --- | --- | --- |
| [frontend-design/](frontend-design/SKILL.md) | This library (original) | The central orchestration workflow — routes every frontend task through the library's knowledge and the two other skills |
| [taste/](taste/SKILL.md) | Vendored upstream: [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) v2.5.1 | Design taste, build rules, copy rules, the real-browser checker and finish gate — the anti-slop execution layer |
| [be-ambitious/](be-ambitious/SKILL.md) | Vendored upstream: [robonuggets/be-ambitious](https://github.com/robonuggets/be-ambitious) | Felix Rieseberg's ambition methodology (altitude, depth, range) as agent steps — raises the standard of the work |

## 2. How the skills complement one another

- **Be Ambitious** runs first on substantial projects: it decides the *standard* — the goal beyond the goal, expert-level depth, range from other disciplines. It shapes the brief.
- **frontend-design** runs next: it routes the work through the library — direction, inspiration, assets, implementation, QA — the *knowledge* and *process*.
- **Taste Skill** governs the craft on landing-page-class builds: its house rules, page plans, dealt palettes/pairings, copy voice, and its checker/gate enforce the result in a real browser. Where taste-skill covers the ground, it wins; this library supplies the theory beneath it and the workflow around it.

They are designed as a stack: Be Ambitious → frontend-design (which invokes taste) → taste's gate at finish. Each is also usable alone.

## 3. Attribution and licensing

- **Taste Skill** — MIT Licence, © 2026 Leonxlnx. Vendored complete and unmodified (`skills/taste/`), including its `LICENSE`, `CHANGELOG.md` and upstream README (kept at [taste/UPSTREAM-README.md](taste/UPSTREAM-README.md)). Upstream commit at vendor time: `d1a2bb41d927083ac7118f60cfc9cdf711810ea0` (v2.5.1, 2026-11-07 release). Website: https://tasteskill.dev
- **Be Ambitious** — MIT Licence, © 2026 RoboNuggets. Vendored unmodified (`SKILL.md`, `LICENSE`, upstream README at [be-ambitious/UPSTREAM-README.md](be-ambitious/UPSTREAM-README.md)). Upstream commit at vendor time: `dc116a3ebd8cf772e4d0930626f67369bd60399d`. Its methodology derives from Felix Rieseberg's article "How to be more ambitious: a tutorial for humans with models" (https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/) — a community skill, **not** an official Anthropic product.
- **frontend-design** — this library's own MIT-licensed skill.

Do not rewrite vendored `SKILL.md` files; fixes to upstream behaviour belong upstream (§7). Project-specific knowledge belongs in the library's knowledge files, not in the vendored skills.

## 4. Installation

### 4.1 Claude Code — project-local (recommended for projects using this library)

Claude Code discovers skills in `.claude/skills/<install-name>/` inside the working project. The install names come from each skill's frontmatter: `design-taste-frontend`, `be-ambitious`, `frontend-design`.

```bash
# from your project root, with this repository cloned alongside (adjust paths):
ln -s ../../frontend-agent-library/skills/taste  .claude/skills/design-taste-frontend
ln -s ../../frontend-agent-library/skills/be-ambitious  .claude/skills/be-ambitious
ln -s ../../frontend-agent-library/skills/frontend-design  .claude/skills/frontend-design
```

(Or copy the folders instead of symlinking; symlinks stay current with `git pull`.) Verify discovery: ask the agent "which skills are available?" — all three should be listed; or run `/skills` if your version supports it.

### 4.2 Claude Code / Codex — user-level

The repository includes the upstream installer, adapted to this layout:

```bash
./install-skills.sh            # link all three into ~/.claude/skills
./install-skills.sh --codex    # link into ~/.codex/skills instead
./install-skills.sh --all-agents
./install-skills.sh design-taste-frontend   # link one
```

It reads install names from each `SKILL.md` frontmatter and symlinks (directory junctions on Windows). The original upstream installer logic is preserved inside it.

### 4.3 As a Claude Code plugin

The repository carries [.claude-plugin/marketplace.json](../.claude-plugin/marketplace.json), so the whole library can be added as a plugin marketplace and its skills installed as one plugin:

```text
/plugin marketplace add architgore050/frontend-agent-library
/plugin install frontend-agent-library@frontend-agent-library
```

### 4.4 Other agent environments

Skills are folders with a frontmatter `SKILL.md` — most agent runtimes that support skills accept them by copying/symlinking into their own skills directory (Codex: `~/.codex/skills`; generic: any `skills/` directory the runtime scans). The taste-skill additionally ships Codex/agents-marketplace manifests upstream (documented in its UPSTREAM-README). Agents without skill support can still follow `skills/frontend-design/SKILL.md` as a plain workflow document — it is written to work both ways.

## 5. Verification

After installing, verify each skill end-to-end once:

- **frontend-design:** start a small task ("design a landing page for X") and confirm the agent loads the workflow and routes to library files.
- **be-ambitious:** run a prompt through it (its own example: `/be-ambitious fix the crash in the login screen`) and confirm it produces the altitude ladder and rewritten prompt.
- **taste-skill (functional check):** its gate needs Node 22+ and Chrome/Edge/Chromium; verify the full toolchain on a test page:
  ```bash
  node <install-dir>/scripts/gate.mjs --start index.html --kind place --category "cafe" --primary "Book a table"
  ```
  followed by `node <install-dir>/scripts/gate.mjs index.html` after the page exists; the expected terminal line is `GATE: PASS`/`FAIL`/`SETUP`. If the Stop-hook fires when the agent finishes a build, discovery is confirmed.

## 6. When to invoke which

- Any frontend build/review → **frontend-design** (it will pull in the others).
- Substantial/new project, ambiguous scope → **Be Ambitious** first.
- Landing page, company/product site, shop, hotel/cafe/studio, SaaS marketing build → **Taste Skill** governs the build itself (its checker and gate run at finish).
- Dashboard/product UI/editorial/app work → **frontend-design** routes the library; taste's craft rules still inform (house rules, copy voice) even where its gate does not run.

## 7. Updating the vendored skills

Preserve upstream changes rather than diverging:

1. Fetch upstream (`git clone --depth 1` each upstream repo, or `git pull` an existing clone).
2. Diff the upstream skill folder against `skills/taste/` (and `skills/be-ambitious/`).
3. Replace the vendored folders with the upstream state; keep this repository's own additions out of the vendored tree (this README and the upstream-README copies live beside, not inside, the skill folders' logic).
4. Record the new upstream commit hash and version in this file (§3) and in [../../PROJECT_STATUS.md](../PROJECT_STATUS.md).
5. Commit per the repository convention (`docs(skills): update taste-skill to vX.Y.Z (upstream @ hash)`) and re-run the §5 verification.

If a local change to vendored files is ever unavoidable (a bug fix needed before upstream releases it), mark it clearly in the commit message and file header, and propose it upstream.

## 8. Related topics

- [frontend-design workflow](frontend-design/SKILL.md) — the central process.
- [Taste skill](taste/SKILL.md) — the craft/gate layer (see its References section for its own docs).
- [Be Ambitious](be-ambitious/SKILL.md) — the ambition methodology.
- [Library README](../README.md) — routing and ground rules for the knowledge base.
- [PROJECT_STATUS.md](../PROJECT_STATUS.md) — integration status and verification evidence.
