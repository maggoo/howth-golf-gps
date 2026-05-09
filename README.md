# ⛳ GolfLine – Howth Golf Club GPS

A progressive web app (PWA) GPS caddie for **Howth Golf Club, Dublin**.

## Features

- 📍 **Live GPS distance** to green — works the moment you open it, no setup needed
- 📐 **Front / Middle / Back** distances to each green
- 🗺 **Satellite course map** with OSM fairway, green, bunker and rough overlays, plus a live routing line from your position to the green
- 📋 **Full scorecard** — all 18 holes with colour-coded scoring (eagle/birdie/par/bogey), front 9, back 9 and total vs par
- ⛳ **Auto hole advance** — prompts when you get within 30m of the green
- 📍 **Survey mode** — walk each green and mark Front / Mid / Back to save precise GPS coordinates, permanently replacing the estimated positions
- 📤 **Export survey data** — copy your surveyed green positions and send to update the app permanently
- 🏌️ White / Yellow / Red tee distances for all 18 holes (metres or yards)

## How to Use

### Distance
Open the app — GPS locks and immediately shows distance to the current hole's green. No marking needed.

### Survey a Green (one-time, improves accuracy permanently)
1. Walk to the **front edge** of the green → tap **Front**
2. Walk to the **middle** → tap **Mid**
3. Walk to the **back edge** → tap **Back**
4. The hole button glows green — distances now use your real positions
5. Tap **Export** to copy the data and send it for a permanent app update

### Scorecard
Tap the 📋 Card tab. Enter your score for each hole — colour coding updates automatically.

### Auto-Advance
The **AUTO** badge in the top right is on by default. When you walk within 30m of the green it asks if you want to advance to the next hole. Tap to disable if you prefer manual control.

## Install on Android
1. Open `https://maggoo.github.io/howth-golf-gps/` in **Chrome**
2. Tap ⋮ → **Add to Home Screen**
3. Allow location when prompted

## Install on iPhone
1. Open the URL in **Safari**
2. Tap Share → **Add to Home Screen**

## Getting Updates
After new files are pushed to GitHub, the installed app updates **automatically in the background** within 24 hours. You don't need to uninstall and reinstall. To force an immediate update, open the URL in Chrome (not the installed app) and hard reload.

## Course Data
Scorecard from the official Howth Golf Club scorecard — White/Yellow/Red tees, par 71.
Green positions seeded from OpenStreetMap, refined by the in-app survey system.
Map imagery from Esri satellite. Course overlays from OpenStreetMap via Overpass API.

---
*Built with Leaflet · Esri · OpenStreetMap*
