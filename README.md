# UnitMap

> An open, zero-dependency real estate unit visualizer for property teams and buyers.

---

## Vision

Real estate sales teams today manage availability through spreadsheets, WhatsApp messages, and printed floor plans. Buyers walk into a site office and ask "which units are left?" — and the answer is a phone call to someone who has the latest Excel file.

**UnitMap exists to replace that with a single URL.**

The vision is a lightweight, shareable, always-current map of a property project — one that any developer, broker, or buyer can open in a browser, instantly see what is available, filter by what matters to them, and make faster, more confident decisions. No apps to install. No accounts to create. No backend to maintain.

We believe property visualization should be:

- **Visual-first** — a map, not a table
- **Instantly shareable** — a static URL, not a login portal
- **Easy to set up** — JSON + SVG, not a SaaS platform
- **Fast and offline-friendly** — no server round-trips for every interaction

---

## Goals

### 1. Make availability visible at a glance
A buyer or consultant should be able to open the tool and understand the entire project — what is sold, blocked, and available — within seconds, without reading any documentation.

### 2. Remove the spreadsheet from the sales floor
Property teams should be able to update unit status directly in the tool and share the updated view immediately, eliminating the lag between a booking and the team knowing about it.

### 3. Be easy enough to set up that one person can do it in an afternoon
Adding a new project should require only three things: a JSON file of unit data, an SVG floor plan with labeled unit paths, and a one-line entry in the project registry. No code changes to the core app.

### 4. Work on any device, anywhere
The tool must function on a sales agent's phone on-site, on a buyer's laptop at home, and on a large display at a site office — without any installation or configuration.

### 5. Stay zero-dependency and open
The project will never require a build tool, a framework, or a paid service to run. Everything needed to deploy it is already in this repository.

---

## Who It Is For

| User | How they use it |
|------|----------------|
| **Property developer** | Embeds the map on their project microsite or shares a GitHub Pages link with channel partners |
| **Sales / CRM team** | Opens the tool on a tablet or laptop during site visits to show buyers live availability |
| **Channel partner / broker** | Gets a shareable link to the latest project map without chasing the developer for updates |
| **Buyer** | Browses units independently, filters by budget and preferences, shortlists before visiting |

---

## What We Are Building Toward

The current version is the foundation. The direction ahead includes:

- **Comparison view** — side-by-side unit comparison for shortlisted plots
- **Booking flow** — lightweight form to express interest or hold a unit, with email notification
- **Export** — generate a PDF summary of available units matching a filter set
- **Multi-floor / tower support** — navigate between floors or towers within a single project
- **Audit trail** — timestamped log of status changes per unit
- **Embed widget** — drop the map into any existing website with a single `<script>` tag

---

## Quick Start

No installation needed. Clone and open:

```bash
git clone https://github.com/sandeep9583/plot.git
cd plot
open index.html        # macOS
# or just open index.html in any browser
```

To deploy publicly, push to `main` — GitHub Pages handles the rest via the included workflow.

---

## Adding a Project

1. Create `data/<project-id>.json` with your unit list
2. Create `svg/<project-id>.svg` with `<path class="unit" data-unit-id="U1" ...>` per unit
3. Register the project in `data/projects.json`
4. Push — done

See [OVERVIEW.md](./OVERVIEW.md) for the full data format reference.

---

## License

MIT — free to use, modify, and deploy.
