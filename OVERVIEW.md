# UnitMap — Project Overview

## What It Is

**UnitMap** is an interactive, browser-based real estate plot and unit availability visualizer. It lets property consultants and buyers explore residential projects visually — clicking units on a map to see details, filtering by price, facing, type, and status, and updating availability in real time. No backend or installation required.

---

## Tech Stack

| Layer       | Technology                                      |
|-------------|-------------------------------------------------|
| Frontend    | HTML5, CSS3, Vanilla JavaScript (ES6+)          |
| Data        | JSON                                            |
| Graphics    | SVG (interactive unit maps)                     |
| Fonts       | Google Fonts — DM Sans, JetBrains Mono          |
| Deployment  | GitHub Pages via GitHub Actions                 |

The entire application lives in a single `index.html` with embedded CSS and JS. No frameworks, no build step, no dependencies to install.

---

## Project Structure

```
plot/
├── index.html                  # Single-page application (HTML + CSS + JS)
├── data/
│   ├── projects.json           # Registry of all projects
│   ├── emerald-towers.json     # Unit data for Emerald Towers
│   └── sunrise-heights.json    # Unit data for Sunrise Heights
├── svg/
│   ├── emerald-towers.svg      # Interactive map — Emerald Towers
│   ├── sunrise-heights.svg     # Interactive map — Sunrise Heights
│   ├── emerald.png             # Reference image — Emerald Towers
│   └── sunrise.png             # Reference image — Sunrise Heights
└── .github/workflows/
    └── static.yml              # GitHub Pages auto-deploy workflow
```

---

## Sample Projects

### Emerald Towers
- **Location:** HITEC City, Hyderabad
- **Developer:** Emerald Developers
- **Units:** 38 plots (U1–U38)
- **Type:** Residential plots
- **Area:** 115–190 sqyd
- **Price range:** ₹69L – ₹1.14Cr
- **Facings:** North, South

### Sunrise Heights
- **Location:** Gachibowli, Hyderabad
- **Developer:** Prestige Realty
- **Units:** 6 apartments (U1–U6)
- **Types:** 1BHK, 2BHK, 3BHK
- **Area:** 80–101 sqyd
- **Price range:** ₹62L – ₹80L
- **Facings:** East, West, North, South

---

## Core Features

### Interactive SVG Map
- Units are `<path>` elements in an SVG file with `data-unit-id` attributes
- Clicking a unit opens its details in the sidebar
- Hovered/selected units glow with a color-coded highlight
- Unit labels (plot numbers) are overlaid dynamically

### Status Color Coding
| Status    | Color  |
|-----------|--------|
| Available | Green  |
| Blocked   | Yellow |
| Sold      | Red    |

### Filters (real-time)
- **Status** — Available / Blocked / Sold
- **Facing** — North / South / East / West
- **Unit Type** — Plot / 1BHK / 2BHK / 3BHK
- **Price Range** — slider with formatted display (₹87L, ₹1.08Cr)
- Match counter updates live as filters change

### Pan & Zoom
- **Mouse:** scroll to zoom, click-drag to pan
- **Touch:** pinch-to-zoom, swipe to pan
- HUD buttons for zoom in / out / reset view

### Unit Management
- Change a unit's status (Available → Blocked → Sold) directly in the UI
- Changes reflect immediately on the map and in all filter counts

### Theme Support
- Light / dark mode toggle
- Preference saved to `localStorage`
- SVG label colors adapt to the active theme

### Responsive Layout
- **Desktop (≥ 900px):** side-by-side map + sidebar
- **Mobile (< 900px):** stacked layout

---

## Data Format

### `projects.json`
```json
[
  {
    "id": "emerald-towers",
    "name": "Emerald Towers",
    "location": "HITEC City, Hyderabad",
    "dataFile": "data/emerald-towers.json",
    "svgFile": "svg/emerald-towers.svg"
  }
]
```

### Unit entry (inside a project data file)
```json
{
  "id": "U1",
  "name": "Plot 1",
  "type": "Plot",
  "area": "130 sqyd",
  "facing": "South",
  "price": 8500000,
  "status": "available"
}
```

---

## Deployment

The app is deployed automatically to **GitHub Pages** on every push to the `main` branch via `.github/workflows/static.yml`. There is no build process — the repository is served as-is.

---

## Adding a New Project

1. Create a JSON data file in `data/<project-id>.json` following the unit entry format above.
2. Create an SVG map in `svg/<project-id>.svg` with `<path class="unit" data-unit-id="U1" ...>` elements per unit.
3. Register the project in `data/projects.json`.
4. Push to `main` — GitHub Pages auto-deploys.
