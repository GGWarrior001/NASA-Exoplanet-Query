# 🪐 NASA Exoplanet Archive Query

A single-page web app that lets you query and explore confirmed exoplanets from the [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/) — no installation or build step required.

![Space-themed UI with star field, query filters, and a sortable results table](https://img.shields.io/badge/live-open%20index.html-00e5ff?style=flat-square&logo=nasa)
![License: MIT](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

---

## ✨ Features

- **Live data** — fetches the full confirmed-exoplanet catalogue directly from NASA's [TAP service](https://exoplanetarchive.ipac.caltech.edu/docs/TAP/usingTAP.html) on every page load
- **Four filters** — narrow results by Discovery Year, Discovery Method, Host Star Name, or Discovery Facility
- **Sortable table** — click any column header to sort ascending, descending, or back to default
- **Host-star links** — each host star links directly to its NASA Exoplanet Archive overview page
- **Space aesthetic** — animated star field, scanline overlay, and retro sci-fi typography (Orbitron + Share Tech Mono)
- **Zero dependencies to install** — React 18 and Babel are loaded from CDN; just open the file

---

## 🚀 Getting Started

Because the app is a single HTML file with no build step, you can run it in two ways:

### Option 1 — Open directly in a browser

```bash
# Clone the repo
git clone https://github.com/GGWarrior001/NASA-Exoplanet-Query.git
cd NASA-Exoplanet-Query

# Open in your default browser
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

> **Note:** Some browsers block `fetch()` for `file://` URLs. If the data doesn't load, use Option 2.

### Option 2 — Serve locally (recommended)

Any static file server works. For example, with Python:

```bash
python -m http.server 8080
```

Then visit **http://localhost:8080** in your browser.

Or with Node.js (`npx` — no install needed):

```bash
npx serve .
```

---

## 🔍 How to Use

1. **Wait for the catalogue to load** — the app contacts the NASA TAP service and indexes all confirmed exoplanets (~5,700+ records).
2. **Select one or more filters** from the dropdowns:
   | Filter | Description |
   |---|---|
   | Discovery Year | Year the planet was confirmed |
   | Discovery Method | e.g. Transit, Radial Velocity, Imaging |
   | Host Star Name | The star the planet orbits |
   | Discovery Facility | Observatory or mission (e.g. Kepler, TESS) |
3. **Click "Execute Query"** to see matching results.
4. **Sort results** by clicking any column header (cycles: ascending → descending → off).
5. **Click a host star name** to open its full profile on the NASA Exoplanet Archive.
6. **Click "Clear"** to reset all filters and results.

---

## 🛠️ Tech Stack

| Technology | Role |
|---|---|
| [React 18](https://react.dev/) (via CDN) | UI components and state management |
| [Babel Standalone](https://babeljs.io/docs/babel-standalone) (via CDN) | In-browser JSX transform |
| [NASA TAP Service](https://exoplanetarchive.ipac.caltech.edu/TAP/sync) | Live exoplanet data |
| [Orbitron](https://fonts.google.com/specimen/Orbitron) / [Share Tech Mono](https://fonts.google.com/specimen/Share+Tech+Mono) | Google Fonts |
| Plain HTML + CSS | Layout and animations |

### Data source

Data is queried from the `pscomppars` table (Planetary Systems Composite Parameters) via an [ADQL TAP query](https://exoplanetarchive.ipac.caltech.edu/docs/TAP/usingTAP.html):

```sql
SELECT pl_name, hostname, disc_year, discoverymethod, disc_facility
FROM pscomppars
```

---

## 📁 Project Structure

```
NASA-Exoplanet-Query/
├── index.html   # Entire application — HTML, CSS, and React/JSX
├── LICENSE      # MIT License
└── README.md    # This file
```

---

## 📄 License

This project is licensed under the [MIT License](LICENSE). © 2026 Tarun Kumar K.G

