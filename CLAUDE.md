# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Single-file, zero-build portfolio site. Everything lives in `index.html` — HTML, CSS, and JavaScript all in one file. No framework, no bundler, no dependencies beyond Google Fonts (loaded via CDN).

## Local preview

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000`. Opening `index.html` directly in a browser will block local video/image loading.

## Architecture

The entire site is driven by two data structures at the top of the `<script>` block in `index.html`:

- **`I18N`** — bilingual (sv/en) strings for all static UI text, keyed by string ID. Elements in the HTML use `data-i18n` (textContent) or `data-i18n-html` (innerHTML) attributes; `applyStatic()` walks these on each language switch.
- **`PROJECTS`** — array of project objects (planks, dartvision, blackjack). Each project holds all content, asset paths, tech stack, and bilingual copy for both the card view and the full detail overlay.

**Key rendering flow:**
1. `renderCards()` — generates project cards in `#projList` from `PROJECTS`.
2. `openProject(id)` — injects a full-screen overlay (`#detail`) with hero video, overview, how-it-works steps, gallery, and feature list — all built from the project's data object.
3. `setLang(l)` — updates `lang`, calls `applyStatic()` + `renderCards()`, and re-renders the open detail overlay if one is open.

**Asset layout:**
```
assets/
  videos/    ← background videos per project (planks.mp4, dartvision.mp4, blackjack.mp4)
  img/       ← screenshots referenced in each project's gallery[]
  cv/        ← Theodor-Landell-CV-SV.pdf and Theodor-Landell-CV-EN.pdf
```

The CV link in the contact section switches between the two PDF files depending on active language (`applyStatic()` handles this).

## Adding or editing a project

All project content is in the `PROJECTS` array. Each entry needs: `id`, `hue` (CSS color), `video`, `poster`, `thumb`, `title`/`titleEn`, `year`, `meta`, `tagline`, `card`, `tech`, `role`, `overview`, `how`, `features`, and `gallery`.

Gallery items with `half: true` are paired into two-column grids; items without it span full width.

## Design tokens

CSS custom properties are defined in `:root`. Per-project accent color is passed via `--hue` on the card/detail element and used throughout child styles.
