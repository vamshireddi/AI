# CLAUDE.md — AI Learning Journey (vamshireddi/AI)

Claude Code reads this file. Other agents (Codex, Cursor, Copilot, Gemini) read `AGENTS.md` in the same directory. **Both files carry the same rules** — if you edit one, keep the other in sync.

## TL;DR

Public GitHub Pages site at `https://vamshireddi.com/AI/` — visual study guides for Vamshi's UT Austin / GreatLearning PGP in AI & ML program. Each module is a single self-contained `index.html` with inline CSS/JS, dark theme default, tabbed navigation with emoji icons, and mandatory OG/Twitter card meta tags + sticky breadcrumb nav.

**For the full rules, conventions, publishing shell template, authoring workflow, and hard constraints, see [`AGENTS.md`](./AGENTS.md) in this directory.** It is the canonical source of agent guidance for this repo.

## Quick reference

- **Live:** `https://vamshireddi.com/AI/`
- **Repo:** `vamshireddi/AI` (public, `main` branch)
- **Deploy:** push to `main` → `pages-build-deployment` auto-runs (~45 sec) → live

## Current module structure

```
index.html                                      ← Master AI Journey hub
greatlearning/index.html                        ← PGP program landing page
greatlearning/prework-ai-python/index.html      ← Pre-Work
greatlearning/module-01-python-foundations/index.html
greatlearning/module-02-machine-learning/index.html
greatlearning/module-03-advanced-ml/index.html  ← Week 3 content added 2026-04-11
```

## Top-priority rules

- **OG + Twitter card meta tags on every deployed page.** Non-negotiable. See `AGENTS.md` for the template.
- **Sticky breadcrumb `<nav>` at top of `<body>`** linking `AI Journey / GreatLearning / Module NN`.
- **Author credit with LinkedIn link** in the `<h1>` subtitle.
- **Inline CSS/JS only.** Ignore linter warnings that suggest externalizing.
- **Don't commit `.claude/`, memory files, or agent plans.** `CLAUDE.md` and `AGENTS.md` themselves are fine (public agent docs).
- **Diff before republishing.** If a draft is older than the deployed version, it's stale — stop and ask.

## When in doubt

Read `AGENTS.md` for the full specification, or ask the user. Do not guess about the publishing shell — the canonical example is `greatlearning/module-03-advanced-ml/index.html`.
