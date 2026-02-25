# 📊 Data Usage Dashboard

A modern, responsive web dashboard to visualize data usage statistics with interactive charts, dark mode support, and PDF export capability.

## ✨ Features

- 📈 Interactive charts powered by Chart.js
- 🌙 Automatic dark mode (based on system preference)
- 📱 Fully responsive design (mobile + desktop)
- 🧾 Export dashboard as PDF
- 🎨 Clean UI using Tailwind CSS
- ⚡ Fast single‑page app build

## 🧱 Tech Stack

- HTML5
- Tailwind CSS (CDN)
- Chart.js
- html2pdf.js
- JavaScript (ES Modules)
- Vite build output

## 📁 Project Structure

```
project-root/
│
├── index.html            # Main HTML entry point
├── assets/
│   └── index-*.js        # Compiled JavaScript bundle
└── README.md
```

## 🚀 Getting Started

### Option 1 — Run Locally (Simple)

1. Download or clone the project
2. Open `index.html` in your browser

> ⚠️ Some browsers block module scripts when opened directly. If charts do not load, use Option 2.

---

### Option 2 — Run with Local Server (Recommended)

#### Using VS Code Live Server

1. Install **Live Server** extension
2. Right‑click `index.html`
3. Click **Open with Live Server**

#### Using Node.js (Vite Preview)

```bash
npm install -g serve
serve .
```

Then open the shown URL in your browser.

## 🖨️ Exporting as PDF

Click the **Export to PDF** button inside the dashboard to download a printable version of the current view.

Powered by `html2pdf.js`.

## 🌙 Dark Mode

Dark mode is enabled automatically based on your system theme.

You can modify this behavior in `index.html`:

```html
<script>
if (window.matchMedia("(prefers-color-scheme: dark)").matches) {
  document.documentElement.classList.add("dark");
}
</script>
```

## 🛠️ Customization

### Change Charts

Edit the JavaScript bundle source (before build) or update chart configuration inside your project source files.

### Styling

Modify Tailwind classes in the components to adjust layout, colors, and spacing.

## 📦 Deployment

You can deploy this dashboard to any static hosting service:

- GitHub Pages
- Netlify
- Vercel
- Firebase Hosting
- Any shared hosting

Simply upload all project files and ensure `index.html` is in the root directory.

## 🧩 Dependencies (CDN)

The project uses CDN links, so no installation is required:

- Tailwind CSS
- Chart.js
- html2pdf.js

## 📄 License

This project is free to use for educational and personal purposes.

---

💡 If you need advanced features (login system, database integration, real‑time data, etc.), extend the dashboard with a backend or API.

