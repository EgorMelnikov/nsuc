# Club Records Page — Design Spec

Date: 2026-06-06

## Overview

A new self-contained HTML snippet (`club-records.html`) for the NSUC TidyHQ site showing the all-time heaviest fish per species caught in club competition history. Source data: `NSUC Trophy History.xlsx` (annual competition winners 1957–2025).

## Page Structure

File: `club-records.html`
Root class: `nsuc-records`
Format: same self-contained snippet as `about.html` and `trophy-fish-2026.html` — `<style>` block + single root `<div>`, no `<html>`/`<head>`/`<body>`.

Layout (top to bottom):
1. Hero banner — gradient matching `trophy-fish-2026.html` style; title "Club Records"; tagline "All-time records — North Shore Underwater Club"
2. "Premier Species" section (h2) — 6 species card grid
3. "Regular Species" section (h2) — 12 species card grid
4. Note callout — explains records are all-time bests from club competition history

## Card Component

Each `.nsuc-record-card`:
- **Photo area** — fixed height ~160px, inline SVG fish silhouette (greyscale placeholder). Real photos can be swapped in later by replacing the SVG with an `<img>`.
- **Species name** — `Arial/Helvetica`, bold, `#00558b`, centred
- **Weight** — large `Georgia` serif number (e.g. `35.00 kg`), prominent, centred
- **Member name** — smaller `Arial`, `#555`, centred

Grid: `display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem`

Card style: left `4px solid #00558b` border, `#f0f7fc` background, `border-radius: 6px`, consistent with existing `nsuc-card` pattern.

Vacant records (no history data): weight and member replaced with "Vacant" in grey italic.

## Record Data

All-time bests computed from `NSUC Trophy History.xlsx`. Flathead excluded (trophy retired 2023). Sand Whiting, Silver Trevally, Yellow Spot Sawtail included as Vacant (added to competition recently, no history).

### Premier Species

| Species | Weight | Member |
|---|---|---|
| Kingfish | 35.00 kg | P. Sheppard |
| Mulloway | 34.40 kg | A. Moderer |
| Cobia | 29.95 kg | A. Price |
| Spanish Mackerel | 26.20 kg | N. Blyth |
| Dolphin Fish | 8.80 kg | J. Williams |
| Snapper | 7.30 kg | J. Howard |

### Regular Species

| Species | Weight | Member |
|---|---|---|
| Bonito | 5.24 kg | A. Scott |
| Rock Blackfish | 5.15 kg | D. Fitzgerald |
| Salmon | 4.16 kg | G. Kroie |
| Blue Morwong | 3.42 kg | C. Maloney |
| Red Morwong | 2.34 kg | M. Walsh |
| Red Rock Cod | 2.17 kg | A. Price |
| Luderick | 1.94 kg | A. Price |
| Bream | 1.69 kg | M. Bonnici |
| Goatfish | 1.66 kg | J. Chan |
| Sand Whiting | — | Vacant |
| Silver Trevally | — | Vacant |
| Yellow Spot Sawtail | — | Vacant |

## Design System Compliance

- CSS class prefix: `nsuc-`
- Colour palette: primary blue `#00558b`, dark blue `#003f6b`, card bg `#f0f7fc`
- Body font: Georgia serif; headings/labels: Arial sans-serif
- `h2`: uppercase, `#00558b`, `border-bottom: 2px solid #00558b`
- Hero: `linear-gradient(135deg, #003f6b 0%, #00558b 60%, #0077b6 100%)`
- Responsive: single column on mobile (`max-width: 600px`)
