# CLAUDE.md

Persistent context for Claude Code working in this repo.

## Tech Stack

- **Single static `index.html` file.** No build step, no bundler, no
  package manager, no framework. All HTML, CSS, and JS are inline in
  this one file.
- **Vanilla JS only.** No React, no libraries beyond Leaflet (map
  rendering, loaded via CDN `<script>` tag) and Google Fonts (Inter,
  DM Mono).
- **GitHub Pages** serves the site directly from the repo root on the
  `main` branch. No CI/CD pipeline — pushing to `main` is the deploy.
- Other files: `manifest.json` (PWA manifest), `icon-192.png` /
  `icon-512.png` (app icons), `README.md` (user instructions).
- Do not introduce a build step, npm, or a framework unless explicitly
  asked. The simplicity is intentional — the user edits/uploads this
  file by hand via the GitHub web UI.

## Deployment Quirks

- **`manifest.json` `start_url` and `scope` must be the full absolute
  URL**: `https://maggoo.github.io/howth-golf-gps/`. Relative paths
  (`/` or `./`) caused a 404 on "Add to Home Screen" install. Do not
  change these back to relative paths.
- **Icons must be PNG, not SVG.** An SVG icon caused install failures
  on Android. `icon.svg` is legacy and unused — ignore it.
- **PWA caching is aggressive.** After pushing a change to `main`:
  1. Wait ~30–60s for GitHub Pages to rebuild (check the Actions tab).
  2. The installed home-screen app updates automatically in the
     background, but on an unpredictable schedule (up to ~24h).
  3. To force an update: open the URL directly in **Chrome** (not the
     installed app icon) and hard-reload, or clear site data in
     Chrome settings.
  4. Uninstalling/reinstalling the PWA is a last resort, not normally
     needed.
- There is no backend and no server-side code. Don't suggest adding
  one for this project.

## Scorecard Data Rules

- **Never invent or estimate scorecard values** (hole names, par,
  stroke index, white/yellow/red tee distances). These must always
  come from the official Howth GC scorecard, which the user has
  photographed and shared. If a value is needed and not already in
  `HOLES` in `index.html`, ask the user for a photo of the scorecard
  rather than guessing or reusing data from a different course.
- The current `HOLES` array in `index.html` reflects the real
  scorecard, transcribed from user-provided photos. Treat it as
  ground truth unless the user says it's wrong.
- **Hole 3 "Bloody Stream" is par 4 for men, par 5 for ladies.** This
  has been mis-set before — the men's `HOLES` array entry must stay
  `par:4`. Don't "fix" it back to 5 without checking with the user.
- Totals to sanity-check against if re-entering scorecard data: White
  5700m / Par 71, Yellow 5437m / Par 71, Red (Ladies) 4943m / Par 72.
- Hole names, in order: Ireland's Eye, Aideens, Bloody Stream,
  Knocknabohill, Summit, Black Linn, Baily, St. Fintan's, Rockabill,
  Ui Maine, Ben Edar, The Tank, Carrickbrack, DublinBay, Farnan's,
  Shielmartin, Cottage, Hog's Back.

## GPS Coordinate Status: Surveyed vs Estimated

Green coordinates come from three sources, in priority order:

1. **`surveyData`** (runtime, browser `localStorage`, key
   `howth_survey_v1`) — the user's most recent in-app GPS survey
   (Front/Mid/Back marked while standing on the green). Highest
   priority; lets the user re-survey to improve accuracy over time.
2. **`SURVEYED`** (hardcoded in `index.html`) — coordinates the user
   has previously walked, exported from the app, and asked to have
   baked permanently into the code. **Currently surveyed: holes 1, 3,
   4, 5, 8, 17, 18.** All other holes (2, 6, 7, 9–16) are NOT
   surveyed — do not assume they're accurate.
3. **`EST`** / live OSM fetch — rough hardcoded guesses or
   OpenStreetMap data, used only as a fallback for unsurveyed holes.
   Flagged in the UI as "(est.)". Known to be inaccurate.

When the user pastes a new JSON export from the app's Export button:
- Merge it into `SURVEYED` in `index.html`.
- Only update/add the hole numbers present in the export — never
  remove or alter holes not included in that export.
- Keep the survey UI (`localStorage`, Front/Mid/Back buttons, Export)
  intact — the user intends to keep re-surveying holes over multiple
  visits, even after data is baked in.
- After merging, hand back the updated `index.html` only — other
  files are unaffected by survey updates.
