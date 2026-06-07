# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a single-file static personal portfolio website hosted on GitHub Pages at `jeevanoss.github.io`. The entire site lives in `index.html` — there is no build step, no package manager, and no dependencies beyond Google Fonts loaded via CDN.

## Development

Preview the site by opening `index.html` directly in a browser, or serve it locally:

```bash
python3 -m http.server 8080
```

Deploy by pushing to the `master` branch — GitHub Pages publishes automatically.

## Architecture

Everything is in `index.html`: HTML structure, all CSS in a `<style>` block, and a small `<script>` block at the bottom. The file is organised in clear comment-delimited sections: `NAV`, `HERO`, `SKILLS`, `ECOMMERCE`, `PASSIONS`, `VILLAGE`, `INTEGRAW`, `DIGIKADA`, `CONTACT`, and `FOOTER`.

**Design tokens** — all colours are CSS custom properties on `:root`:
- `--ink` / `--ink-mid` / `--ink-light` — dark text scale
- `--cream` / `--cream-dark` — page background tones
- `--leaf` / `--leaf-light` — green accent
- `--saffron` / `--saffron-light` — orange/amber accent

**Scroll reveal** — elements with class `reveal` start invisible (`opacity:0; transform:translateY(24px)`). A small `IntersectionObserver` script at the bottom of `<body>` adds class `in` when they enter the viewport, triggering the CSS transition.

**Responsive** — a single `@media (max-width: 768px)` block handles all mobile layout changes (nav links hidden, grids collapse to 1 column, hero stacks vertically, `.iw-brand` hidden).

**Sections with dark backgrounds** — `#skills` and `#digikada` use `var(--ink)`, `#integraw` uses `#042C53`, and `#passions` uses `var(--cream-dark)`. Each overrides `.section-label`, `.section-title`, and `.section-body` colours locally.
