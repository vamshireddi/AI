# AI Learning Journey — vamshireddi/AI

## Project
GitHub Pages site at `vamshireddi.com/AI/` — visual study guides for the UT Austin / GreatLearning PGP in AI & ML program.

## Structure
```
greatlearning/
  index.html                          ← Landing page (module list)
  prework-ai-python/index.html        ← Pre-Work guide
  module-01-python-foundations/index.html  ← Module 01
  module-02-machine-learning/index.html   ← Module 02
  module-03-advanced-ml/index.html        ← Module 03
```

## Conventions
- Each module is a self-contained single HTML file (`index.html`) with all CSS/JS inline
- Dark theme default (#0f172a), light mode toggle
- Tabbed navigation with emoji icons
- OG + Twitter card meta tags on every page (use `og-image.jpg?v=4` from vamshireddi.com)
- Author credit with LinkedIn link in subtitle
- Style must match Module 03 format: cheat sheet, concept map, prerequisites, visual diagrams, quizzes

## Deployment
- Push to `main` → auto-deploys via GitHub Pages
- Custom domain: vamshireddi.com/AI/
- Cloudflare CDN in front

## Rules
- NEVER commit .claude/, memory files, or plan files
- NEVER store API keys, tokens, or credentials
- All content is public — no private/sensitive information in this repo
