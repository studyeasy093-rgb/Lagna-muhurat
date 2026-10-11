# Lagna Muhurta

A single-file, offline web app that works out the day's lagna (rising sign) windows for any saved birth chart and rates each window for starting new work. It follows the Parāśarī (BPHS) house logic together with the classical muhurta filters.

## What it shows

- A 24-hour lagna wheel, from sunrise to the next sunrise, with a live "now" needle
- The current rising sign and its verdict, plus the next clear window
- Day filters: Chandrabala, Tarabala, Moon strength, and ghatak items
- A window finder for career, money, contracts, travel, property, study, health and puja
- Every lagna window, split as panchaka, Rahu kalam, Yamaganda, Gulika, Bhadra, gandanta and Tarabala change
- Panchanga: tithi, nakshatra, yoga and karana, each with end times
- The three-layer event formula:
  - L1: Vimshottari MD, AD and PD
  - L2: transit planets on the natal degrees of the dasha lords
  - L3: ascendant and Moon crossings of those degrees
  - A 12-month scan of coming L2 contacts
- Transits scored with the natal Ashtakavarga, plus Sade Sati status
- Birth profiles: enter anyone's date, time and place of birth (a built-in city list fills in coordinates). The app calculates the chart, Ashtakavarga and Vimshottari dasha, and every daily result switches to that person
- Export and import of all profiles as a JSON file, with a copy-and-paste text option as a fallback
- Light, dark and auto themes, and a saved "where you are today" place

## Run it

Open `index.html` in any browser. It needs no internet connection, no build step and no dependencies. The web fonts load when you are online; without them the page falls back to system fonts.

## Host it on GitHub Pages

1. Create a new repository and upload `index.html`, `README.md` and `.nojekyll`.
2. In the repository, go to Settings, then Pages.
3. Under "Build and deployment", choose "Deploy from a branch". Select `main` and `/ (root)`, then save.
4. The app will appear at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

## Accuracy

All astronomy is computed in the page itself:
- Sun: Meeus low-precision theory
- Moon: Meeus/ELP 60-term series
- Mercury to Saturn: JPL Keplerian elements
- Ayanamsa: Lahiri

These were checked against the Astrodienst sidereal ephemeris for 2026 and against an AstroSage birth chart:

| Quantity | Agreement |
|---|---|
| Ascendant, Sun and Moon | within about 1′ |
| Other planets | within about 0.1° |
| Sunrise and sunset | within about 10 seconds |

Rahu and Ketu default to the mean node, as AstroSage does. You can switch to the true node in settings.

Dasha dates follow AstroSage's calendar arithmetic (years, months and 30-day months), so they match AstroSage printouts. The planetary elements are valid for 1800–2050.

## Birth profiles

Use "Add a person" in the Birth profiles section, then switch charts from the selector at the top. Profiles are saved in the browser's local storage, so they stay on that device and browser. Use "Export all" to save a backup, and "Import file" to restore it or move it to another device. Importing merges by profile id, so re-importing an export updates those profiles instead of duplicating them.

Optional fields per profile:
- **Lagna and Moon degrees from a printed report.** The Vimshottari balance depends on the Moon to the arc-second, so entering a report's values makes dasha dates match that report exactly.
- **Ghatak items** (bad day, tithis, nakshatra, yoga, karana, prahar, lagna, rashi), usually copied from a report.

A first-time visitor sees one built-in profile, defined as `SEED_PROFILE` in `index.html`.

## Privacy

The built-in profile's birth data is stored in plain text inside `index.html`, and exported JSON files contain every saved profile's birth details. If you publish the repository or GitHub Pages site as public, anyone can read those birth details. Use a private repository if you want to keep them to yourself. Note that GitHub Pages from a private repository needs a paid GitHub plan.

## Disclaimer

This is a study tool for Jyotisha. It reports what the classical rules say about a moment; it is not professional advice.
