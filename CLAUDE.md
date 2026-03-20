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

1. **CSS** (`<style>`) — Design system using CSS custom properties (`--ink`, `--paper`, `--accent`, `--accent2`, `--muted`, `--rule`, `--white`). Layout uses CSS Grid and Flexbox. Responsive breakpoint at 900px via media query. Typography uses Google Fonts (Playfair Display, DM Sans, Noto Sans SC/Serif SC).

2. **HTML** — Semantic sections: navigation → hero → about (skills, competencies) → case study 1 (五羊牌雪糕 brand repositioning) → case study 2 (即时设计 × 杰士邦 cross-brand campaign) → insights → contact.

3. **JavaScript** (`<script>`) — Intersection Observer for scroll-triggered fade-up animations (threshold: 0.12) and dynamic navigation highlighting based on scroll position. No frameworks or libraries.

## Key Conventions

- Content is primarily in Chinese with English headings/labels
- All styles and scripts are inline — no separate CSS/JS files
- CSS class naming uses descriptive hyphenated names (e.g., `case-hero-band`, `strategy-flow`, `kpi-grid`, `risk-grid`, `budget-table`)
