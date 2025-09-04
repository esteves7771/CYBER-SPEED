Got it ✅
Here’s your updated README with your GitHub screenshot embedded.

---

# CYBER-SPEED ⚡

A sleek, cyberpunk-styled **browser speed test** that measures **ping, download, and upload** with a reactive gauge and neon UI. Mobile-friendly, zero-backend, and privacy-respecting.

Live Demo: *(add your GitHub Pages link here)*

![CYBER-SPEED Screenshot](https://github.com/esteves7771/CYBER-SPEED/blob/main/Screenshot%202025-09-04%20at%2018.31.07.png?raw=true)

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

## 🧪 Troubleshooting

* **Upload says “Blocked”**: you’re likely in a blob/sandboxed viewer. Open via a normal origin (local server or GitHub Pages).
* **ISP shows “Unavailable”**: IP/geo service is blocked or rate-limited; it will fall back automatically.
* **Slow/unstable results**: Wi-Fi interference, VPNs, or browser throttling can affect readings. Try a wired connection or another browser.

---

## 🗺️ Roadmap

* Multi-server selection (EU/US/Asia)
* Jitter & packet-loss approximations
* Shareable result cards (image export)
* Theme toggle (neon ↔ minimal)
* PWA install support

---

## 🙌 Credits

* Cloudflare Speed Test sinks for bandwidth endpoints
* ipapi.co for IP & ISP info
* Typeface: Share Tech Mono (Google Fonts)
* Built with ❤️ (and a sprinkle of AI copilot)
