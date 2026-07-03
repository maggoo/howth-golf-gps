# ⛳ HackAround — Howth Golf Club GPS

A progressive web app (PWA) GPS caddie built specifically for **Howth Golf Club, Dublin**.

Live at: **https://maggoo.github.io/howth-golf-gps/**

---

## Features

### 📍 GPS Distance
- Live distance to the current hole's green, updated continuously as you walk. 
- **Front / Middle / Back** distances calculated from GPS-surveyed green positions. 
- All 18 greens have been physically walked and surveyed for accuracy. 
- Distances shown in metres or yards (preference saved between sessions). 

### 🗺 Course Map
- Satellite imagery of Howth Golf Club
- Numbered red pins at each green's surveyed position
- Live routing line from your position to the current green
- Your position updates in real time as you walk

### 📋 Scorecard
- Full 18-hole scorecard with hole names, par, and stroke index
- Colour-coded scoring: eagle (gold), birdie (green), par (white), bogey (orange), double+ (red)
- Front 9, Back 9, and total vs par summaries
- Persists during your round

### 🏌 Club Distances
- Shot tracker: mark start, walk to where it landed, mark end
- Select the club you used — distance is recorded
- Builds lifetime averages per club across all rounds
- Shows average, best, and number of shots per club
- Data persists in localStorage across all sessions

### 📍 Location Sync
- When you unlock your phone, the app re-acquires GPS and checks which green you're closest to
- If you've played several holes without checking the app, it automatically prompts to switch to the right hole
- Works across all 18 holes, not just the next one

### 🔍 Survey Mode
- Tap **SURVEY** in the header to enable
- Walk to Front / Mid / Back of any green and tap to record the GPS position
- Overrides the baked-in default positions for that hole
- Tap **Export** (via ··· menu) to export your new readings
- Hidden by default during normal play

---

## Scorecard Data

| Tee | Total | Par |
|-----|-------|-----|
| White | 5,700m | 71 |
| Yellow | 5,437m | 71 |
| Red (Ladies) | 4,943m | 72 |

Hole 3 (Bloody Stream) is par 4 for men, par 5 for ladies.

Holes in order: Ireland's Eye, Aideens, Bloody Stream, Knocknabohill, Summit, Black Linn, Baily, St. Fintan's, Rockabill, Ui Maine, Ben Edar, The Tank, Carrickbrack, DublinBay, Farnan's, Shielmartin, Cottage, Hog's Back.

---

## Navigation

- **Swipe left** — next hole
- **Swipe right** — previous hole
- Tap hole number circles to jump to any hole directly

---

## Install on Android
1. Open `https://maggoo.github.io/howth-golf-gps/` in **Chrome**
2. An install banner will appear — tap **Install**
3. Or tap ⋮ → **Add to Home Screen**
4. Allow location when prompted
5. Tap **Tap to Start GPS** if GPS doesn't start automatically

## Install on iPhone
1. Open the URL in **Safari** (not Chrome)
2. Tap the Share button → **Add to Home Screen**
3. Open the app and tap **Tap to Start GPS**
4. Allow location access when prompted
5. If denied previously: Settings → Privacy → Location Services → Safari → While Using App

---

## Getting Updates
After changes are pushed to GitHub, the installed app updates automatically in the background within ~24 hours. To force an update, open the URL directly in Chrome and hard reload.

---

*Built with Leaflet · Esri satellite imagery · Vanilla JS · GitHub Pages*
