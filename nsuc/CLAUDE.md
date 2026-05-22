# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This repo contains code for custom pages hosted on the **North Shore Underwater Club (NSUC)** TidyHQ site. NSUC is a spearfishing club based on Sydney's Northern Beaches, Australia (est. 1952).

TidyHQ is a club/association management platform. Custom pages are built with HTML, CSS, and JavaScript and embedded into the TidyHQ site.

## Pages

| File | TidyHQ Page | Notes |
|------|-------------|-------|
| `about.html` | About the Club | Intro, history, meetings, competitions, safety, sponsors |
| `trophy-fish-2026.html` | 2026 Trophy Fish | Species records table + Tony Leslie Trophy; source data in `Trophy Fish 2026.xlsx` |

Pages are self-contained HTML snippets (no `<html>`/`<head>`/`<body>`) with a `<style>` block and a single root `<div class="nsuc-*">`. Ready to paste into TidyHQ's **Page Content** field.

## Reference Document

- `09_Welcome Doc.pdf` — Member welcome pack; the primary source of truth for club content, rules, competitions, and structure. Consult it when writing or updating page content.

## Design System

All pages share a consistent visual language established in `about.html`:

**Colours**
- Primary blue: `#00558b` (headings, borders, accents)
- Dark blue: `#003f6b` (hero/CTA backgrounds)
- Light blue: `#0077b6` (gradient end)
- Card background: `#f0f7fc`
- Safety/warning: `#fff8e1` background, `#f9a825` border, `#e65100` text
- Link on dark: `#7ec8e3`

**Typography**
- Body: Georgia / Times New Roman serif, `color: #1a1a1a`, `line-height: 1.7`
- Headings (h1–h3) and UI labels: Arial / Helvetica sans-serif
- `h2`: `#00558b`, uppercase, `border-bottom: 2px solid #00558b`

**CSS class naming:** all classes prefixed `nsuc-` (e.g. `nsuc-about`, `nsuc-hero`, `nsuc-card`, `nsuc-safety-box`, `nsuc-cta`)

**Reusable components:**
- `.nsuc-hero` — full-width gradient banner for page title
- `.nsuc-cards` — CSS grid (`auto-fit, minmax(220px, 1fr)`) of `.nsuc-card` tiles with left blue border
- `.nsuc-safety-box` — amber warning callout
- `.nsuc-cta` — dark-blue centred call-to-action footer block
- `.nsuc-sponsors` — grid of `.nsuc-sponsor-item` tiles with light border

When adding new pages, follow the same palette and component patterns for visual consistency across the site.

## Club Context (for page content)

- **Competitions:** Bo Hestridge Top 10 (monthly, Jan–Nov) and Alliman Shield (first Sunday monthly, inter-club). Governed by the USFA.
- **Meetings:** Last Wednesday of each month at Harbord Diggers, Freshwater.
- **Regulations:** NSW fishing licence required; DPI NSW bag/size limits apply.
- **Social:** Facebook page/group and Instagram @northshore_spearfishing.
- **Trophy claims:** must be submitted to Sports Secretary within one week of capture; require certified scales, photo evidence, and a witness.
