# UPCE Campus Map — Food & Services

> **An interactive, bilingual campus guide for the University of Pardubice.**  
> Single HTML file · No server required · Czech / English · Gemini AI summaries · Real-time open/closed status

---

## Screenshot

<!-- ============================================================
     INSERT SCREENSHOT HERE
     Recommended: full-browser capture of the app at ~1400 px wide
     showing the sidebar open with the map centred on Studentská
     ============================================================ -->

&nbsp;

---

## Table of Contents

1. [Description](#description)
2. [Features](#features)
3. [Requirements & Dependencies](#requirements--dependencies)
4. [Installation & Deployment](#installation--deployment)
5. [Usage](#usage)
6. [AI Summary Feature](#ai-summary-feature)
7. [Adding or Editing Locations](#adding-or-editing-locations)
8. [Changing Default Settings](#changing-default-settings)
9. [Known Issues](#known-issues)
10. [Project History](#project-history)
11. [Technology Stack](#technology-stack)

---

## Description

UPCE Campus Map is a client-side web application that helps students and visitors find food and service facilities on the University of Pardubice campus. It displays **14 verified points of interest** — canteen, cafés, vending machines, ATM, copy centre, library study zones, student affairs, health centre, and more — on an interactive map centred on Studentská street in Pardubice.

The entire application is packaged as **one self-contained `.html` file**. There is no backend, no database, no build step, and nothing to install. Opening the file in a browser is all that is required.

### Campus locations covered

| # | Facility (EN) | Facility (CZ) | Category | Hours |
|---|---------------|---------------|----------|-------|
| 1 | Main University Canteen | Hlavní menza UPCE | Food | 10:30 – 14:30 |
| 2 | Gallery Café | Gallery Café | Café | 08:00 – 18:00 |
| 3 | FEI Faculty Café | Kavárna FEI | Café | 08:00 – 16:00 |
| 4 | Snack Machine (FES) | Automat FES | Vending | 24 / 7 |
| 5 | Vending – Student Dorms | Automat – Koleje | Vending | 24 / 7 |
| 6 | Copy Center | Copy centrum | Print | 08:00 – 15:00 |
| 7 | ČSOB ATM | Bankomat ČSOB | ATM | 24 / 7 |
| 8 | Quiet Study Zone – Library | Tichá studovna – Knihovna | Study | 08:00 – 20:00 |
| 9 | Computer Lab – FChT | Počítačová učebna FChT | Study | 08:00 – 18:00 |
| 10 | Student Affairs Office | Studijní oddělení | Service | 09:00 – 15:00 |
| 11 | Dorms & Catering Admin | Správa kolejí a menz | Service | 09:00 – 14:00 |
| 12 | UPCE Health Centre | Zdravotní středisko UPCE | Health | 08:00 – 14:30 |
| 13 | FChT Faculty Buffet | Bufet FChT | Food | 07:30 – 14:00 |
| 14 | UPCE Information Centre | Informační centrum UPCE | Service | 09:00 – 15:00 |

---

## Features

- **Interactive Leaflet map** centred on the real UPCE campus at building-level coordinate accuracy
- **Czech / English language switch** — all names, descriptions, addresses, and AI prompts update instantly
- **Live open / closed status** — colour dot per facility calculated from the current system time (🟢 open · 🔴 closed · 🟡 24 / 7)
- **Live search** — filters both the sidebar list and map markers as you type
- **Category filter chips** — All · Food · Café · Vending · ATM · Print · Study · Service · Health
- **Slide-up detail panel** — tap any marker or list item for full address, hours, status, and optional notes
- **Gemini AI summaries** — on-demand student-oriented summary per facility
- **Collapsible sidebar** with smooth CSS transition; map resizes correctly after animation
- **Map style switcher** — Voyager, Light, or Smooth themes (CartoDB + Stadia CDNs, no Referer restriction)
- **Hover tooltips** on every marker showing the facility name in the active language
- **Persistent API key** — stored in `localStorage`, survives page reload
- **Mobile responsive** — sidebar becomes a full-width overlay below 600 px
- **Automatic tile fallback** — if the primary CDN fails the app switches providers silently

---

## Requirements & Dependencies

### Browser

| Browser | Minimum version |
|---------|----------------|
| Chrome / Chromium | 90 + |
| Firefox | 88 + |
| Edge | 90 + |
| Safari | 14 + |

### Internet connection

An internet connection is required for:
- Loading map tiles from CartoDB / Stadia
- Generating AI summaries via the Gemini API
- Loading fonts from Google Fonts

The application UI and sidebar load instantly from the local file. The map tiles and AI features degrade gracefully if offline.

### Gemini API key

Only required for the AI summary feature. The key is free. See [AI Summary Feature](#ai-summary-feature) for how to obtain one.

### External libraries (loaded automatically from CDN)

Nothing to install. All libraries load at runtime.

| Library | Version | Source | Purpose |
|---------|---------|--------|---------|
| Leaflet.js | 1.9.4 | cdnjs.cloudflare.com | Interactive map, markers, animations |
| DM Sans | — | fonts.googleapis.com | Body text |
| Space Mono | — | fonts.googleapis.com | Labels and badges |

### Map tile providers

| Provider | Style | Role |
|----------|-------|------|
| CartoDB Voyager | Street map (colour) | Primary |
| CartoDB Positron | Street map (light grey) | Fallback 1 |
| Stadia Alidade Smooth | Street map (muted) | Fallback 2 |

> **Why not OpenStreetMap tiles?**  
> OSM volunteer servers require a `Referer` HTTP header. Opening a local HTML file sends no Referer, so OSM returns a 403 "Access blocked" error. CartoDB and Stadia serve the same OSM data through their own CDNs without this restriction.

---

## Installation & Deployment

### Option 1 — Open locally *(recommended for personal use)*

No installation. Download `upce-map.html` and open it.

```bash
# macOS
open upce-map.html

# Windows
start upce-map.html

# Linux
xdg-open upce-map.html
```

The file runs from your Downloads folder, a USB drive, or any local path.

---

### Option 2 — GitHub Pages *(free public URL)*

```bash
# Clone or create a repository, then:
cp upce-map.html index.html

git add index.html
git commit -m "Deploy UPCE Campus Map"
git push

# Enable GitHub Pages:
# Repository → Settings → Pages → Source: main branch / root
# Live at: https://YOUR_USERNAME.github.io/REPO_NAME/
```

---

### Option 3 — Netlify Drop *(instant, no account required)*

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Rename the file to `index.html`
3. Drag and drop onto the page
4. Receive an instant URL such as `https://random-name.netlify.app`

---

### Option 4 — Vercel

```bash
npm install -g vercel

mkdir upce-map && cp upce-map.html upce-map/index.html
cd upce-map
vercel
# Accept all defaults — deployed in ~30 seconds
```

---

### Option 5 — Any static web server

```bash
# Python (built-in, no install)
python3 -m http.server 8080
# Open: http://localhost:8080/upce-map.html

# Node.js (no install)
npx serve .
# Open: http://localhost:3000/upce-map.html

# VS Code
# Right-click upce-map.html → Open with Live Server
```

Compatible with any host that serves static files: **Cloudflare Pages**, **Firebase Hosting**, **Surge.sh**, **Render**, shared cPanel hosting, or university web space.

---

## Usage

### Interface overview

<!-- ============================================================
     INSERT ANNOTATED INTERFACE SCREENSHOT HERE
     Suggested annotations:
       → Sidebar toggle button (hamburger, top-left)
       → CZ / EN language buttons
       → Settings gear icon
       → Search input
       → Category filter chips
       → A POI list item with green / red status dot
       → A map marker
       → Reset View button (top-right of map)
       → Map Style button (top-right of map)
     ============================================================ -->

&nbsp;

### Controls reference

| Control | Location | Action |
|---------|----------|--------|
| ☰ / › Toggle | Top-left corner | Collapse or expand the sidebar |
| **CZ** / **EN** | Sidebar — top row | Switch all text to Czech or English |
| ⚙ icon | Sidebar — top row | Open Gemini API key settings |
| Search box | Sidebar | Filter facilities by name or description in the active language |
| Category chips | Sidebar | Show only facilities of a chosen type |
| POI list item | Sidebar | Fly map to marker, open the detail panel |
| Map marker | Map | Same as clicking a list item |
| Marker hover | Map | Show the facility name as a tooltip |
| ⌖ Reset View | Map — top-right | Return to campus overview, clear search and filter |
| 🗺 Map Style | Map — top-right | Cycle between Voyager, Light, and Smooth tile themes |
| Detail panel handle / ✕ | Detail panel | Close the detail panel |
| **Generate Summary** | Detail panel | Request an AI description (requires API key) |

### Finding a facility — step by step

1. Open `upce-map.html` in your browser.
2. The map loads centred on the UPCE Rektorát at zoom 16.
3. Optionally use the **category chips** or **search box** to narrow the list.
4. Click a **map marker** or a **sidebar item**.
5. The detail panel slides up with address, hours, live status, and any notes.
6. Click **Generate Summary** for an AI description (API key needed).

### Detail panel

<!-- ============================================================
     INSERT DETAIL PANEL SCREENSHOT HERE
     Recommended: select a facility (e.g. Gallery Café or Main Canteen)
     so the panel shows name, category badge, address, hours,
     a green/red status dot, and the Generate Summary button
     ============================================================ -->

&nbsp;

---

## AI Summary Feature

Clicking **Generate Summary** (or **Generovat shrnutí** in Czech) sends a prompt to **Gemini 1.5 Flash** and shows a short, student-oriented description of the selected facility in the detail panel.

### Getting a free API key

1. Go to [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
2. Sign in with any Google account
3. Click **Create API key**
4. Copy the key — it starts with `AIza…`

The free tier includes generous usage limits suitable for personal and educational use.

### Entering the key

1. Click the **⚙** icon in the sidebar
2. Paste your key into the field
3. Click **Save**

The key is stored in `localStorage` as `"upce_gemini_key"` and loaded automatically on every subsequent visit.

### How it works

The prompt is constructed from the selected POI's bilingual data and sent to:

```
POST https://generativelanguage.googleapis.com/v1beta/models/
     gemini-1.5-flash:generateContent?key=YOUR_KEY
```

The response (max 80 words, with a practical tip) replaces the placeholder text in the detail panel. Loading and error states are handled in-place.

### Security

The API key is sent as a URL query parameter and is visible in the browser's network tab. For personal use this is fine. For a public deployment, proxy the request through a server-side function (e.g. a Cloudflare Worker) so the key is never exposed to the client.

---

## Adding or Editing Locations

All POI data lives in the `POIS` array at the top of the `<script>` block in `upce-map.html`. Each entry has this shape:

```javascript
{
  id: 15,                         // unique integer, increment from the last entry
  cat: 'cafe',                    // food | cafe | vending | atm | print | study | service | health
  icon: '☕',                     // emoji shown in the marker circle and list
  color: '#9b7fda',               // hex — marker ring colour
  bg: 'rgba(155,127,218,.18)',    // rgba — marker background tint
  lat: 50.03682,                  // latitude  — from mapy.cz or openstreetmap.org
  lng: 15.77348,                  // longitude
  cz: {
    name: 'Název v češtině',
    desc: 'Popis místa pro studenty.',
    address: 'Ulice 1, Pardubice'
  },
  en: {
    name: 'Name in English',
    desc: 'Description for students.',
    address: 'Street 1, Pardubice'
  },
  hours: '08:00 – 17:00',         // used for display and live open/closed calculation
  alwaysOpen: false,              // true → shows 24/7 gold dot, bypasses hours parser
  note: { cz: 'Poznámka', en: 'Note' }  // optional extra info — set to null if unused
}
```

**Finding coordinates:** Right-click any building on [mapy.cz](https://mapy.cz) or [openstreetmap.org](https://www.openstreetmap.org) and copy the latitude / longitude shown in the context menu.

**Hours parser:** The live status evaluates only the first time range in the `hours` string. If a facility has split hours (e.g. `"09:00–12:00, 13:00–15:00"`), the second window is not checked. Set both windows explicitly if needed, or mark the facility with a note.

---

## Changing Default Settings

Edit the values directly in the `<script>` block inside `upce-map.html`:

```javascript
// ── Language shown on load ──────────────────────────────────
let lang = 'cz';          // 'cz' or 'en'

// ── Map start position and zoom ─────────────────────────────
const map = L.map('map', {
  center: [50.03660, 15.77420],   // lat, lng — UPCE Rektorát
  zoom: 16,
});

// ── Reset View target (keep in sync with centre above) ──────
map.flyTo([50.03660, 15.77420], 16, { duration: 0.8 });

// ── Default tile style ──────────────────────────────────────
loadTiles(0);   // 0 = Voyager, 1 = Positron (light), 2 = Stadia Smooth
```

---

## Known Issues

| Issue | Notes |
|-------|-------|
| API key visible in browser network tab | Acceptable for personal use. Use a backend proxy for public deployments. |
| Hours parser handles one time range only | Facilities with split hours show status based on the first range only. |
| No offline support | Map tiles and Gemini API require internet. |
| Coordinates not GPS-surveyed | Verified against OSM building outlines; a few metres of drift is possible for some buildings. |

---

## Project History

This application was developed across three milestones as part of a course on AI-assisted development at the University of Pardubice.

| Milestone | Key changes |
|-----------|-------------|
| **1 — Foundation** | Leaflet map, CZ / EN toggle, API key settings panel. Known issues: English names incomplete, descriptions not rendered, Gemini API call not wired to UI, Firefox stripe rendering bug. |
| **2 — Fixes & Expansion** | Firefox bug fixed structurally (`map.invalidateSize()` on load + resize). Full bilingual data model for all 14 POIs. Gemini wired to Generate Summary button. Category chips, live search, detail panel, open / closed status, sidebar toggle, mobile layout. |
| **3 — Final Phase** | OSM tiles replaced with CartoDB / Stadia fallback chain (fixes local-file Referer block). All 14 coordinates re-verified to building level. Hover tooltips. README and deployment documentation written. |

---

## Technology Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| HTML5 | — | Document structure |
| CSS3 | — | Layout, design tokens, transitions, responsive breakpoints |
| JavaScript ES2020 | — | All application logic — no framework, no build step |
| Leaflet.js | 1.9.4 | Interactive map, custom div markers, flyTo animations |
| CartoDB Voyager tiles | — | Primary map background (no Referer restriction) |
| CartoDB Positron tiles | — | Fallback map style |
| Stadia Alidade Smooth | — | Second fallback map style |
| Gemini 1.5 Flash | — | AI facility summary generation |
| Google Fonts (DM Sans + Space Mono) | — | Typography, loaded via CDN link |
| localStorage | Browser native | API key persistence across sessions |

---

*University of Pardubice · Studentská 95, 532 10 Pardubice*  
*Map data © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors · Tiles © [CartoDB](https://carto.com/attributions) and [Stadia Maps](https://stadiamaps.com/)*
