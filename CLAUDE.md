# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static brochure website for 建昶精機 (Jian Chang Precision) — a Taiwanese CNC Swiss turning manufacturer. Bilingual (Traditional Chinese + English). No build step, no dependencies, no package manager.

To preview: open any `.html` file directly in a browser, or use a simple local server (e.g. `python -m http.server 8080`).

## Architecture

All pages share a single stylesheet: `css/style.css`. Per-page styles are inlined in `<style>` blocks inside each page's `<head>` — keep page-specific rules there, not in the shared CSS.

**Pages:**
- `index.html` — hero, industries strip, why-choose-us, parts gallery
- `capabilities.html` — machines, tolerances, materials grid
- `parts.html` — product showcase with part images from `images/`
- `industries.html` — vertical markets overview
- `industry-optical.html` — deep-dive on optical communications (only sub-industry page so far)
- `rfq.html` — quote request form (client-side only, no backend)
- `contact.html` — address, phone, map

**Shared layout pattern:** Every page uses the same `<header>` (logo + nav + CTA button) and `<footer>` markup copied manually — there is no templating system. When updating nav links or footer content, update all pages.

## CSS conventions

CSS custom properties are defined in `:root` in `css/style.css`:
- `--blue` (#0f4c81) — primary brand color, headings, links
- `--accent` (#f59e0b) — CTA buttons, highlights
- `--dark` (#111827) — body text, dark header backgrounds
- `--gray` (#6b7280) — secondary text
- `--border` (#e5e7eb) — dividers and card borders

Responsive breakpoints are handled per-page in their inline `<style>` blocks; the shared CSS handles only the header/footer/button/utility classes.

## Images

Product part photos live in `images/`. Filenames are in Traditional Chinese describing the part (e.g. `0.7mm白鐵插銷.jpg`). When adding new part images, follow the same naming convention.
