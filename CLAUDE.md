# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal academic website for Yanhao Wang (Assistant Professor, Alberta School of Business). Single-page site built with Quarto, deployed to GitHub Pages at `www.yanhaowang.com`.

## Build & Deploy

```bash
quarto render          # Render index.qmd → index.html (+ site_libs/, search.json)
quarto preview         # Local dev server with live reload
```

Deployment is manual: run `quarto render` locally, then commit and push the generated HTML to `master`. GitHub Pages serves directly from the repository root (no CI/CD pipeline).

## Architecture

- **`_quarto.yml`** — Quarto config: cosmo theme, no navbar, no TOC, MathJax, output to root dir
- **`index.qmd`** — The entire site content (bio, papers, publications) in one Quarto markdown file
- **`style.css`** — Custom styles: Palatino font, navy color scheme, `.button-13` class for buttons
- **`index.html`** — Generated output (committed to git for GitHub Pages)
- **`site_libs/`** — Generated Quarto dependencies (Bootstrap 5, etc.)
- **`_freeze/`** — Quarto execution cache (engine: knitr)
- **`files/cv/`** — CV as LaTeX source (`cv.tex`) and compiled PDF (`cv.pdf`)
- **`files/paper/`** — Research paper PDFs linked from the site
- **`images/`** — Headshot photos
- **`CNAME`** — Custom domain: `www.yanhaowang.com`

## Key Conventions

- The site renders only `index.qmd` (configured in `_quarto.yml` render list)
- Output dir is `"."` (root), so generated files live alongside source files
- Navbar is disabled; this is a single-page layout
- Styling uses inline HTML in `index.qmd` combined with `style.css` — both must be considered when making visual changes
- Paper links point to PDFs in `files/paper/`; the CV links to `files/cv/cv.pdf`
- The `master` branch is the deploy branch (not `main`)
