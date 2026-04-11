# AGENTS.md — AI Learning Journey (vamshireddi/AI)

> Read by Codex, Cursor, Copilot, Gemini, and any other agent that respects the `AGENTS.md` convention. Claude Code also reads `CLAUDE.md` in this same directory — the two files carry the same rules.

## What this repo is

Public GitHub Pages site for **Vamshi Krishna Reddy Bandaru's AI Learning Journey** — visual study guides for the UT Austin / GreatLearning PGP in AI & ML program (2025–2026 cohort).

- **Live:** `https://vamshireddi.com/AI/` (custom domain, Cloudflare CDN in front of GH Pages)
- **Repo:** [`vamshireddi/AI`](https://github.com/vamshireddi/AI) — public, `main` branch, served from root
- **Deployment:** push to `main` → `pages-build-deployment` workflow auto-deploys in ~45 sec

### Current module structure

```
index.html                                      ← Master AI Journey hub
greatlearning/index.html                        ← PGP program landing page
greatlearning/prework-ai-python/index.html      ← Pre-Work (AI Landscape + Python)
greatlearning/module-01-python-foundations/index.html
greatlearning/module-02-machine-learning/index.html
greatlearning/module-03-advanced-ml/index.html  ← includes Week 3 content as of 2026-04-11
```

Future module directories will follow the same pattern: `greatlearning/module-NN-<slug>/index.html`.

## Hard conventions (do not "improve" these away)

1. **Each module is a single self-contained `index.html`** with all CSS and JavaScript inline. No external CSS/JS files, no build step. Ignore linter warnings that suggest externalizing styles — that's a deliberate choice so the page renders instantly with zero dependencies.
2. **Dark theme default** (`#0f172a`) with a light-mode toggle. Use the existing CSS custom properties (`--bg`, `--bg-surface`, `--text`, `--text-muted`, `--accent`, `--accent2`, `--accent3`, `--border`, `--success`) and their `body.light` overrides. Do not invent a new color system.
3. **Tabbed navigation with emoji icons.** Each module has a sticky-ish nav at the top (Cheat Sheet → Concept Map → Prerequisites → content sections → Mistakes). See `greatlearning/module-03-advanced-ml/index.html` — that's the canonical shape.
4. **Module structure template:** cheat sheet, concept map, prerequisites, visual diagrams, hands-on code blocks, quizzes, "common mistakes" section.
5. **Real-life examples for every concept.** Don't strip analogies or examples to make guides "more concise." The pedagogy is "every concept explained from scratch, no assumptions."
6. **Author credit is mandatory** in the `<h1>` subtitle:
   ```html
   <small>Notes prepared by: <a href="https://www.linkedin.com/in/vamshireddi/" target="_blank" style="color:#60a5fa; text-decoration:none;">Vamshi Krishan Reddy Bandaru</a></small>
   ```

## Publishing shell — required on every module page

Every deployed module page MUST include the following in `<head>` directly after `<title>`:

```html
<meta name="description" content="<concise page description>">
<meta name="author" content="Vamshi Krishna Reddy Bandaru">

<!-- Open Graph / Social Sharing -->
<meta property="og:type" content="article">
<meta property="og:title" content="<page title with module number>">
<meta property="og:description" content="<same as meta description>">
<meta property="og:image" content="https://vamshireddi.com/og-image.jpg?v=4">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:url" content="https://vamshireddi.com/AI/greatlearning/<module-path>/">
<meta property="og:site_name" content="Vamshi Krishna Reddy Bandaru — AI Learning Journey">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="<same as og:title>">
<meta name="twitter:description" content="<same as og:description>">
<meta name="twitter:image" content="https://vamshireddi.com/og-image.jpg?v=4">

<link rel="canonical" href="https://vamshireddi.com/AI/greatlearning/<module-path>/">
```

And a sticky breadcrumb `<nav>` at the very top of `<body>`:

```html
<nav style="position: sticky; top: 0; z-index: 1000;
            background: var(--bg-surface); border-bottom: 1px solid var(--border);
            padding: 10px 24px; font-size: 0.9rem;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            -webkit-font-smoothing: antialiased;
            display: flex; align-items: center; gap: 0;">
  <a href="../../../" style="color: var(--accent); text-decoration: none;">AI Journey</a>
  <span style="color: var(--text-muted); margin: 0 8px;">/</span>
  <a href="../../" style="color: var(--accent); text-decoration: none;">GreatLearning</a>
  <span style="color: var(--text-muted); margin: 0 8px;">/</span>
  <span style="color: var(--text-muted);">Module NN: <Title></span>
</nav>
```

**When adding a new module page, copy these blocks verbatim and update only the descriptive strings and path segments.** Missing OG cards is a blocker — the user has explicitly said OG + Twitter cards are required on every deployed page.

## Content authoring workflow

Vamshi typically drafts new module guides in a scratch folder at `/Users/vkrb/Projects/GreatLearning AI ML/` (local machine). Those drafts frequently lack the publishing shell above — they are raw authoring files.

When moving a draft into this repo:

1. **Diff first.** Compare the new draft against the currently deployed file for that module. If the draft is older or smaller than what's deployed, it is a **stale draft** — STOP and ask the user before publishing.
2. **Port into the existing shell.** Don't overwrite blindly. Preserve the deployed file's `<head>` meta block, breadcrumb nav, author credit, and footer. Replace only the body content that actually changed.
3. **Verify OG tags + canonical URL** still point at the correct module path.
4. **Show the diff to the user** before committing.
5. **Commit + push to `main`.** GitHub Pages auto-deploys.
6. **Verify the live URL** (`https://vamshireddi.com/AI/greatlearning/<module-path>/`) after deploy completes. Note that Cloudflare has a ~10 min cache; hard-refresh may be needed.

## Hard rules (never violate)

- **NEVER commit `.claude/`, memory files, agent plans, or any Claude/agent internal artifacts to this repo.** `CLAUDE.md` and `AGENTS.md` themselves are fine — they're public agent instructions. Internal memory and planning files are not.
- **NEVER store API keys, tokens, or credentials.** All content is public.
- **NEVER create a duplicate "publishing" repo.** This IS the publishing repo.
- **NEVER `git init` inside the scratch authoring folder** (`/Users/vkrb/Projects/GreatLearning AI ML/`) or add it as a remote. That folder has a throwaway local repo with no remote and should stay that way.
- **NEVER request `delete_repo` scope.** If cleanup is needed, tell Vamshi to delete manually via the GitHub UI.
- **NEVER `--force` push to `main`** without explicit permission.
- **NEVER strip analogies, real-world examples, or visual diagrams** to make a guide "cleaner." The detailed teaching style is the point.

## When stuck

Ask the user. Don't guess. A previous agent tried to create a duplicate published repo from the scratch folder — don't be that agent.
