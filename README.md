# 📊 DataPulse — Data Usage Dashboard

A modern, mobile-first web dashboard for tracking and visualizing monthly data usage. Built with React 19 and a polished design system that adapts to light and dark themes.

---

## ✨ Features

- **Dashboard View** — Hero summary card with total consumption, monthly average, peak usage, and a next-month forecast derived from a linear trend
- **Analytics View** — Canvas-rendered line chart with gradient fill, average reference line, and an animated bar chart for quick month comparisons
- **History View** — Chronological log grouped by year; tap any month to select it for CSV/PDF export, or tap the 📷 icon to view the bill screenshot
- **Screenshot Modal** — Bottom-sheet overlay showing the raw bill image for any recorded month
- **Ring Gauges** — Circular progress indicators comparing current, average, forecast, and yearly-average usage against the peak month
- **Sparkline** — Lightweight SVG sparkline on the hero card for at-a-glance trend
- **Forecast Engine** — Linear extrapolation from the last three months to predict next-month usage
- **Month-over-month badges** — Colour-coded ▲/▼ percentage change on every history row
- **Dark mode** — Full CSS-variable theming that follows the system colour scheme automatically
- **Export buttons** — CSV and PDF export UI (ready for backend integration)
- **Smooth animations** — `slideUp`, `fadeIn`, and `sheetUp` keyframe animations on every panel

---

## 🧱 Tech Stack

| Layer | Technology |
|---|---|
| UI framework | React 19 (via compiled Vite bundle) |
| Styling | Custom CSS variables + DM Sans / DM Mono fonts |
| Charts | Native Canvas API (line chart) + SVG (sparkline) |
| Build tool | Vite (output: `index-Bfyz_xh5.js`, `index-C2uqWzKy.css`) |
| PDF export | html2pdf.js (CDN) |
| Font loading | Google Fonts CDN |

---

## 📁 Project Structure

```
project-root/
│
├── index.html                  # HTML entry point; loads Tailwind CDN, Chart.js CDN, html2pdf CDN
├── assets/
│   ├── index-Bfyz_xh5.js      # Compiled React application bundle
│   └── index-C2uqWzKy.css     # Compiled stylesheet (design tokens + component styles)
├── screenshots/                # Bill screenshot images referenced by each month entry
│   ├── Screenshot_Mar_2026.jpg
│   ├── Screenshot_Feb_2026.jpg
│   └── ...
└── README.md
```

---

## 📊 Data Model

Monthly usage entries are defined in the bundle as a static array. Each record has the following shape:

```js
{
  month: "Feb 2026",        // Display label
  usage_gb: 414,            // Data used in GB
  screenshot: "Screenshot_Feb_2026.jpg",  // Filename inside /screenshots/
  status: "ongoing"         // Optional; marks the current in-progress month
}
```

To add a new month, update the `hf` array in the source before rebuilding, or replace the bundle with one that contains your updated data.

---

## 🚀 Getting Started

### Option 1 — Static file server (recommended)

```bash
npm install -g serve
serve .
```

Open the URL printed in the terminal. This avoids browser restrictions on ES module cross-origin requests.

### Option 2 — VS Code Live Server

1. Install the **Live Server** extension
2. Right-click `index.html` → **Open with Live Server**

### Option 3 — Python (no npm required)

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080`.

> ⚠️ Opening `index.html` directly as a `file://` URL will block module scripts in most browsers. Always use a local server.

---

## 🖼️ Adding Bill Screenshots

Place screenshot images inside a `/screenshots/` folder at the project root. The filename must match the `screenshot` field in the data record exactly (case-sensitive). Supported formats: JPEG, PNG, WebP.

---

## 🖨️ Exporting Data

- **Export CSV / Export PDF** buttons appear in the History view and in the multi-select bar when months are selected.
- PDF export is powered by `html2pdf.js` loaded from CDN.
- CSV export logic can be wired to the existing button handlers in the source.

---

## 🌙 Dark Mode

Dark mode activates automatically via `@media (prefers-color-scheme: dark)`. All colours are CSS custom properties (`--bg`, `--surface`, `--accent`, etc.) defined in `index-C2uqWzKy.css`, so the entire palette swaps with a single media query.

To force a specific mode, add or remove the `dark` class on `<html>` in `index.html`.

---

## 📐 Views at a Glance

| View | Key components |
|---|---|
| **Dashboard** | Hero card · stat cards · ring gauges · sparkline |
| **Analytics** | Canvas line chart · bar chart · top-3 months leaderboard |
| **History** | Year-grouped list · multi-select · screenshot modal · export bar |

Navigation is handled by a fixed bottom tab bar with animated active indicators.

---

## 📦 CDN Dependencies

No local `node_modules` needed at runtime. The following libraries are loaded from CDN:

- **Tailwind CSS** — utility classes used in `index.html` body
- **Chart.js** — imported in HTML head (available globally if needed for extensions)
- **html2pdf.js** — PDF export

The React runtime and all application code are bundled inside `index-Bfyz_xh5.js`.

---

## 🛠️ Customisation

### Update data
Edit the source data array and rebuild with Vite, or directly patch the `hf` variable in the bundle for quick changes.

### Change accent colour
Edit `--accent` and related variables in `index-C2uqWzKy.css`.

### Add real export logic
Wire up the `export-btn-csv` and `export-btn-pdf` button `onClick` handlers in the React source to generate and download files from the selected month state.

### Connect a backend
Replace the static `hf` array with a `fetch()` call inside the `useEffect` to pull live usage records from an API.

---

## 🚢 Deployment

Upload all files (keeping the folder structure intact) to any static host:

- **Netlify / Vercel** — drag-and-drop the project folder
- **GitHub Pages** — push to a `gh-pages` branch
- **Firebase Hosting** — `firebase deploy`
- **Any shared host** — FTP upload, ensure `index.html` is in the web root

No server-side processing is required.

---

## 📄 License

Free to use for personal and educational projects.

---

💡 **Want real-time data?** Extend this dashboard with a lightweight backend (Node.js, Python, etc.) to fetch live usage metrics from your ISP's API or a router and push them into the data array dynamically.