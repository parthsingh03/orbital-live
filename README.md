# ORBITAL LIVE 🛰️

**Live demo:** https://parthsingh03.github.io/orbital-live/


A real-time 3D tracker for everything orbiting Earth — **15,967 objects** propagated live with SGP4 in a Web Worker, rendered on an interactive Three.js globe.

## Features

- **Live 3D globe** — Three.js Earth with day/night shading, atmosphere glow, and orbit controls (rotate / zoom)
- **15,967 tracked objects** across Space Stations, Starlink, OneWeb, Navigation, and Other
- **Real orbital mechanics** — positions propagated with SGP4 (`satellite.js`) in a Web Worker at 4 Hz, with main-thread interpolation for smooth motion
- **Time controls** — UTC clock with 1× / 60× / 600× / live speed
- **Search** — find any object by name or NORAD catalog ID
- **Click to inspect** — latitude, longitude, altitude, velocity, orbital period, inclination, and TLE epoch
- **Toggles** — orbit path, ground footprint, and camera follow per object; category visibility filters with live counts

## Data

Two-line element sets (TLEs) from **CelesTrak**, cached in `localStorage` and auto-refreshed every 2 hours. A TLE snapshot (`tle-snapshot.js`, October 2026) ships as a fallback because CelesTrak doesn't send CORS headers — so the app works fully offline.

## Run it

No build step. All libraries are vendored locally (`vendor/`), so it works without internet:

```bash
python3 -m http.server
# then open http://localhost:8000/index.html
```

Double-clicking `index.html` also works.

## Tech

Three.js (3D globe), satellite.js (SGP4 propagation), Web Workers (4 Hz propagation off the main thread), vanilla JavaScript. No frameworks, no build tools, no API keys.
