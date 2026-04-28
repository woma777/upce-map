
# 🗺️ UPCE Campus Map — Food & Services

> An interactive, bilingual map of food and service facilities at the **University of Pardubice (UPCE)**.  
> Single HTML file · No server required · Gemini AI integration · Czech / English

---

## 📸 What It Does

The UPCE Campus Map is a self-contained web application that helps students and visitors find food, services, and facilities across the University of Pardubice campus. It runs entirely in the browser — just open the file and it works.

**Core features:**

- 🗺 **Interactive Leaflet map** centred on the real UPCE campus (Studentská, Pardubice) with accurate building-level marker positions
- 📍 **14 verified POI markers** covering canteen, cafés, vending machines, ATM, copy centre, library, study rooms, student affairs, health centre, and more
- 🌐 **Czech / English language switch** — all names, descriptions, addresses, and AI prompts update instantly
- 🕐 **Live open/closed status** — each facility shows a real-time colour dot (🟢 open · 🔴 closed · 🟡 24/7) based on current system time
- 🔍 **Live search** — filters both the sidebar list and map markers as you type
- 🏷 **Category filter chips** — All · Food · Café · Vending · ATM · Print · Study · Service · Health
- 📋 **Slide-up detail panel** — tap any marker or list item to see full address, hours, status, notes
- ✦ **Gemini AI summaries** — generates a friendly student-oriented summary for any facility on demand
- 🗂 **Collapsible sidebar** with toggle button (hamburger/chevron)
- 🗺 **Map style switcher** — Voyager · Light · Smooth tile themes (CartoDB + Stadia, no Referer restriction)
- 💾 **Persistent API key** — stored in `localStorage`, survives page reload
- 📱 **Responsive** — sidebar overlays the map on screens narrower than 600 px

---

## 🏛 Campus Locations Covered

| # | Facility | Category | Hours |
|---|----------|----------|-------|
| 1 | Hlavní menza UPCE / Main Canteen | 🍽 Food | 10:30–14:30 |
| 2 | Gallery Café (Rektorát) | ☕ Café | 08:00–18:00 |
| 3 | Kavárna FEI / FEI Faculty Café | ☕ Café | 08:00–16:00 |
| 4 | Automat FES / Snack Machine | 🥤 Vending | 24/7 |
| 5 | Automat Koleje / Dorm Vending | 🥤 Vending | 24/7 |
| 6 | Copy centrum / Copy Center | 🖨 Print | 08:00–15:00 |
| 7 | Bankomat ČSOB / ATM | 💳 ATM | 24/7 |
| 8 | Tichá studovna – Knihovna / Library Study Zone | 📚 Study | 08:00–20:00 |
| 9 | Počítačová učebna FChT / Computer Lab | 💻 Study | 08:00–18:00 |
| 10 | Studijní oddělení / Student Affairs | 🏛 Service | 09:00–15:00 |
| 11 | Správa kolejí a menz / Dorms Admin | 🎓 Service | 09:00–14:00 |
| 12 | Zdravotní středisko / Health Centre | 🏥 Health | 08:00–14:30 |
| 13 | Bufet FChT / FChT Buffet | 🥗 Food | 07:30–14:00 |
| 14 | Informační centrum / Info Centre | 📮 Service | 09:00–15:00 |

---

## 🛠 Technology Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| HTML5 | Native | Document structure |
| CSS3 | Native | Layout, design tokens, transitions |
| JavaScript (ES2020) | Native | All app logic — no framework |
| [Leaflet.js](https://leafletjs.com) | 1.9.4 (cdnjs) | Interactive map, markers, flyTo |
| CartoDB Voyager tiles | CDN | Default map background (no Referer restriction) |
| CartoDB Positron tiles | CDN | Fallback map style |
| Stadia Alidade Smooth | CDN | Second fallback map style |
| [Gemini API](https://ai.google.dev) | gemini-1.5-flash | AI facility summaries |
| Google Fonts | CDN | DM Sans + Space Mono typography |
| localStorage | Browser native | API key persistence |

> **Why no OpenStreetMap tile server?**  
> OSM's volunteer servers block requests that have no `Referer` HTTP header — which is exactly what happens when you open a local HTML file. CartoDB and Stadia serve the same OSM data through their own CDNs without this restriction.

---

## 🚀 Deployment

### Option 1 — Open Locally (simplest, no setup)

```bash
# Just download the file and open it
open upce-map.html          # macOS
start upce-map.html         # Windows
xdg-open upce-map.html      # Linux
```

No server, no build step, no dependencies to install. The file is fully self-contained.

---

### Option 2 — GitHub Pages (free, public URL)

1. Create a new GitHub repository (can be public or private with Pages enabled)

2. Upload `upce-map.html` and rename it to `index.html`:
   ```bash
   git init
   cp upce-map.html index.html
   git add index.html
   git commit -m "Add UPCE campus map"
   git remote add origin https://github.com/YOUR_USERNAME/upce-map.git
   git push -u origin main
   ```

3. Go to your repo → **Settings** → **Pages** → Source: `main` branch → `/root`

4. Your map is live at:
   ```
   https://YOUR_USERNAME.github.io/upce-map/
   ```

> ✅ Free · ✅ HTTPS · ✅ No server needed · ✅ Custom domain supported

---

### Option 3 — Netlify Drop (instant, no account needed)

1. Go to [netlify.com/drop](https://app.netlify.com/drop)
2. Rename `upce-map.html` → `index.html`
3. Drag and drop the file onto the page
4. Get an instant public URL like `https://random-name-123.netlify.app`

> Takes under 30 seconds. No signup required for a temporary URL.

---

### Option 4 — Vercel

```bash
npm install -g vercel

# Create a folder with your file as index.html
mkdir upce-map && cp upce-map.html upce-map/index.html
cd upce-map

vercel
# Follow the prompts — choose defaults
```

Your app deploys to `https://upce-map.vercel.app` (or similar).

---

### Option 5 — Any Static Web Server

The file works on **any static file host** — no PHP, Node, or database required.

```bash
# Python (built-in, good for local testing)
python3 -m http.server 8080
# then open http://localhost:8080/upce-map.html

# Node.js (npx, no install)
npx serve .
# then open http://localhost:3000/upce-map.html

# VS Code Live Server extension
# Right-click upce-map.html → Open with Live Server
```

Other compatible hosts: **Cloudflare Pages**, **Firebase Hosting**, **Surge.sh**, **Render**, any shared cPanel hosting, university web space.

---

## 🤖 Enabling AI Summaries (Gemini API)

The AI summary feature requires a free Google Gemini API key.

**Step 1 — Get a free API key**

1. Go to [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
2. Sign in with a Google account
3. Click **Create API key** → copy the key (starts with `AIza…`)

**Step 2 — Enter the key in the app**

1. Open the map in your browser
2. Click the **⚙ Settings** icon in the sidebar
3. Paste your API key and click **Save**
4. The key is stored in your browser's `localStorage` — you only need to do this once per browser

**Step 3 — Generate a summary**

1. Click any marker or list item to open its detail panel
2. Click **Generate Summary** (or **Generovat shrnutí** in Czech)
3. A friendly, student-oriented summary appears in about 2–3 seconds

> **Note:** The free Gemini tier (AI Studio) includes generous usage limits suitable for personal and educational use. No billing is required.

---

## 📁 File Structure

```
upce-map.html          ← the entire application (single file)
README.md              ← this file
```

The HTML file includes everything inline:

```
upce-map.html
├── <head>
│   ├── Leaflet CSS          (loaded from cdnjs CDN)
│   └── Google Fonts         (loaded from fonts.googleapis.com)
├── <style>                  (~290 lines of CSS)
│   ├── CSS custom properties / design tokens
│   ├── Sidebar layout + collapse animation
│   ├── POI list + filter chips
│   ├── Slide-up detail panel
│   ├── Settings modal
│   ├── Toast notification
│   └── Leaflet popup + tooltip overrides
├── <body>
│   ├── #sidebar             (brand, controls, search, chips, list, footer)
│   ├── #map-wrap            (toggle button, Leaflet map, map controls, detail panel)
│   └── #settings-modal + #toast
└── <script>                 (~290 lines of JavaScript)
    ├── POIS[]               (14 POI data objects with CZ+EN bilingual fields)
    ├── Map init + tile provider chain with auto-fallback
    ├── Sidebar toggle
    ├── Language switching
    ├── Category filter + live search
    ├── renderList()
    ├── selectPOI() + detail panel
    ├── isOpen()             (real-time open/closed status)
    ├── generateAISummary()  (Gemini API call)
    ├── Settings + localStorage
    ├── cycleTiles()         (map style switcher)
    └── resetView() + toast
```

---

## ⚙️ Configuration

All configurable values are at the top of the `<script>` block.

**Changing the default language:**
```js
let lang = 'cz';   // change to 'en' for English default
```

**Changing the default map style:**
```js
loadTiles(0);   // 0 = Voyager, 1 = Light, 2 = Smooth
```

**Changing the map start position / zoom:**
```js
const map = L.map('map', {
  center: [50.03660, 15.77420],  // lat, lng — UPCE campus
  zoom: 16,
});
```

**Adding a new POI:**
```js
{
  id: 15,
  cat: 'cafe',           // food | cafe | vending | atm | print | study | service | health
  icon: '☕',
  color: '#9b7fda',
  bg: 'rgba(155,127,218,.18)',
  lat: 50.03682,         // latitude  (get from maps.google.com or mapy.cz)
  lng: 15.77348,         // longitude
  cz: { name: 'Název CZ', desc: 'Popis CZ', address: 'Adresa CZ' },
  en: { name: 'Name EN', desc: 'Description EN', address: 'Address EN' },
  hours: '08:00 – 17:00',
  alwaysOpen: false,
  note: null             // or { cz: 'Poznámka', en: 'Note' }
}
```

---

## 🐛 Known Issues

| Issue | Impact | Notes |
|-------|--------|-------|
| Gemini API key visible in browser network tab | Low | Acceptable for student/personal use. For public deployment, proxy the API call through a backend. |
| Hours parser — single range only | Low | Facilities with split hours (e.g. 09:00–12:00, 13:00–15:00) are evaluated on the first range only. |
| No offline support | Low | Map tiles and Gemini both require internet. A Service Worker could cache tiles for offline use. |
| POI positions are approximate | Low | Coordinates verified via OpenStreetMap — not GPS-surveyed on the ground. A few metres of drift possible. |

---

## 🗓 Changelog

### v2.0 — Milestone 2
- Fixed Firefox map stripe rendering bug (`map.invalidateSize()` on load + resize)
- Replaced OSM tile server with CartoDB/Stadia providers (fixes "Access blocked — Referer required" error when opening as a local file)
- All 14 POI markers repositioned to accurate building-level coordinates on the real UPCE campus
- Added sidebar toggle (hamburger/chevron) with CSS transition and map resize
- Added live open/closed status calculated from current system time
- Added category filter chips (8 categories)
- Added live search filtering list + map markers simultaneously
- Added slide-up detail panel with full facility info
- Added hover tooltips on all map markers
- Added Gemini AI summary integration in detail panel with loading/error states
- Added map style switcher (Voyager / Light / Smooth)
- Added toast notification system
- Added Reset View button
- API key now persisted in localStorage
- Full bilingual data (CZ + EN) for all 14 POIs including descriptions, addresses, and notes

### v1.0 — Milestone 1
- Basic Leaflet map with POI markers
- Czech / English language switch
- Settings modal for API key entry
- Gemini API integration (not yet wired to UI)

---

## 👤 Author

UPCE student project · University of Pardubice  
Built with [Leaflet.js](https://leafletjs.com) · [Gemini AI](https://ai.google.dev) · [CartoDB](https://carto.com) tiles

---

## 📄 Licence

This project is for educational purposes. Map data © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors.
