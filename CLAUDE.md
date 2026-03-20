# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-page portfolio website for an advertising professional (叶海仁 / Ye Hairen). The entire site is a self-contained static HTML file (`portfolio.html`) with inline CSS and JavaScript — no build system, no package manager, no external dependencies beyond Google Fonts CDN.

## Development

No build or install steps required. Open `portfolio.html` directly in a browser or serve it with any static file server:

```
python3 -m http.server 8000
```

There are no tests, linters, or CI/CD pipelines configured.

## Architecture

**Single file: `portfolio.html`** (~47KB)

The file contains three embedded layers:

1. **CSS** (`<style>`) — Design system using CSS custom properties (`--ink`, `--paper`, `--accent`, `--accent2`, `--muted`, `--rule`, `--white`). Layout uses CSS Grid and Flexbox. Single responsive breakpoint at `max-width: 900px` collapses all multi-column grids to single-column. Typography uses Google Fonts (Playfair Display, DM Sans, Noto Sans SC/Serif SC).

2. **HTML** — Sections with IDs used for navigation anchors:
   - `#hero` — two-column grid with intro + stats
   - `#about` — skills bars, competency cards, education/tools
   - `#case1` — Case Study 1: 五羊牌雪糕 brand repositioning (uses `div.case-study`, not `<section>`)
   - `#case2` — Case Study 2: 即时设计 × 杰士邦 cross-brand campaign (also `div.case-study`)
   - `#insights` — 3-column grid of insight cards with hover inversion
   - `#contact` — dark-background CTA with email/LinkedIn/resume links

3. **JavaScript** (`<script>`) — Two behaviors, no frameworks:
   - **Scroll animations**: IntersectionObserver (threshold: 0.12) applies fade-up to `.case-hero-band`, grid children, `.kpi-item`, `.risk-card`, `.reflection-item`, `.insight-card`, `.tl-item`, `.opt-item`, `.flow-step`. New animated elements must be added to the selector in the JS.
   - **Active nav**: scroll listener highlights the current section's nav link by matching `section[id]` and `div.case-study[id]`.

## Key Conventions

- Content is primarily in Chinese with English headings/labels
- All styles and scripts are inline — no separate CSS/JS files
- CSS class naming uses descriptive hyphenated names (e.g., `case-hero-band`, `strategy-flow`, `kpi-grid`, `risk-grid`, `budget-table`)
- Case studies follow a consistent pattern: `case-hero-band` → sub-headed sections separated by `.ornament` dividers → specialized grids/tables per section
- Contact links (email, LinkedIn, resume) use placeholder `href="#"` values — these need real URLs before deployment
