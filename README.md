# CYBER-SPEED ⚡

A sleek, cyberpunk-styled **browser speed test** that measures **ping, download, and upload** with a reactive gauge and neon UI. Mobile-friendly, zero-backend, and privacy-respecting.

Live Demo: *(add your GitHub Pages link here)*

---

## ✨ Features

* **Ping test** (HTTP latency estimate)
* **Download throughput** with live gauge updates
* **Upload throughput** with smart sandbox detection (Drive/Docs/opaque origins)
* **ISP & location lookup** (best-effort)
* **Responsive UI** designed for mobile & desktop
* **Neon cyberpunk aesthetic** (Share Tech Mono + Tailwind)

---

## 🧠 How it works

* **Ping:** HEAD request to a tiny CDN asset to approximate round-trip latency.
* **Download:** Streams a 50 MB file from Cloudflare and computes Mbps over time.
* **Upload:**

  * Tries sending data to Cloudflare’s `__up` sink using `fetch` with `no-cors`.
  * If running in a **sandboxed/opaque origin** (e.g., `blob:…usercontent.goog`) that blocks POSTs, the app detects it and shows **`Blocked`** instead of crashing the sequence.
* **ISP/Location:** Queries `ipapi.co` for a best-effort display (falls back gracefully if blocked).

---

## 🔧 Tech Stack

* **HTML5 + Vanilla JS**
* **Tailwind CSS** (via CDN)
* **Google Fonts:** Share Tech Mono
* Endpoints:

  * Download: `https://speed.cloudflare.com/__down?bytes=50000000`
  * Upload: `https://speed.cloudflare.com/__up`
  * IP/Geo: `https://ipapi.co/json/`

---

## 🖥️ UI & Controls

* **INITIATE**: starts Ping → Download → Upload in sequence (with small pauses).
* **Gauge**: animates from 0 → current Mbps; capped visually at 150 Mbps by default.
* **RERUN**: appears after a sequence completes.

---

## 📱 Mobile-first Notes

* Viewport locked for minimal scrolling.
* SVG gauge sized for small screens.
* Buttons large and tap-friendly.

---

## 🔒 Privacy

* No user data is stored or sent to any backend controlled by this app.
* Third-party endpoints are used strictly for measuring connection quality or getting IP/ISP:

  * Cloudflare speed sinks (download/upload)
  * ipapi.co for IP/geo (gracefully handles failure)

---

## 🧩 Edge Cases & Sandboxes

Some environments block cross-origin POSTs (e.g., Google Drive/Docs preview, certain in-app browsers).
This app **detects** those cases and:

* Shows **`Blocked`** for upload (instead of erroring)
* Completes the rest of the tests normally

Hosting on a normal origin (e.g., GitHub Pages) enables full functionality.

---

## ⚙️ Configuration Tips

* **Gauge max** (default 150 Mbps): adjust `maxSpeed` in `updateGauge()` to fit your audience.
* **Download size**: currently 50 MB for better accuracy on fast links (`__down?bytes=50000000`).
* **Upload sizes**: runs multiple (1/2/5 MB) and takes the best reading when allowed.

---

## 🧪 Troubleshooting

* **Upload says “Blocked”**: you’re likely in a blob/sandboxed viewer. Open via a normal origin (local server or GitHub Pages).
* **ISP shows “Unavailable”**: IP/geo service is blocked or rate-limited; it will fall back automatically.
* **Slow/unstable results**: Wi-Fi interference, VPNs, or browser throttling can affect readings. Try a wired connection or another browser.

---

## 🗺️ Roadmap (nice-to-haves)

* Multi-server selection (EU/US/Asia)
* Jitter & packet-loss approximations
* Shareable result cards (image export)
* Theme toggle (neon ↔ minimal)
* PWA install support

---

## 📜 License

MIT — do whatever you want, just keep the license.

---

## 🙌 Credits

* Cloudflare Speed Test sinks for bandwidth endpoints
* ipapi.co for IP & ISP info
* Typeface: Share Tech Mono (Google Fonts)
* Built with ❤️ (and a sprinkle of AI copilot)

---

## 🖼️ Screenshots

*Add your screenshots here*

```
/assets/screenshot-01.png
/assets/screenshot-02.png
```

---

## 🏷️ Badges (optional)

You can add shields if you like:

```
![status](https://img.shields.io/badge/status-active-brightgreen)
![license](https://img.shields.io/badge/license-MIT-blue)
![made-with](https://img.shields.io/badge/made%20with-HTML5%20%7C%20JS%20%7C%20Tailwind-orange)
```
