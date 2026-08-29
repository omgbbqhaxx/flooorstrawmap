# flooor strawmap

A work-in-progress draft roadmap for the [flooor](https://flooor.fun) protocol on Base.

**Stage 1 — Cobalt, September 2026.** Every stage after it unlocks at a protocol market cap — $5M, $10M, $100M, $1B+, $1T+ — rather than on a date.

## Live site

[omgbbqhaxx.github.io/flooorstrawmap](https://omgbbqhaxx.github.io/flooorstrawmap/)

## Structure

- `index.html` — Full-screen map (pan + zoom) with the sidebar FAQ. The roadmap itself is plain HTML in the `.grid` block — edit boxes there.
- `faq.html` — Standalone FAQ page
- `shared.css` — Shared styles and design tokens
- `flooor.svg` — flooor mark
- `og-card.png` / `og-card.svg` — Open Graph card assets
- `.nojekyll` — tells GitHub Pages to serve the files as-is

## Editing the map

The map is a CSS grid: one column per stage (Cobalt, then the market-cap milestones), one row per layer (L listings, V vault and sponsors, S surface).
Each box is a `div.box`, with `--headliner` (dark), `--offchain` (dashed), or `--shipped` (faint) modifiers.
North stars and tasks live in the `.northstars` and `.tasks` blocks on the right, outside the timeline, and the sponsor schedule above the map is the `.board` section — its numbers are sample data until real sponsors sign up. Bump the revision date in the legend and in the header meta after a change.

Regenerate the OG card after editing `og-card.svg`:

```
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless --screenshot=og-card.png \
  --window-size=1200,630 "file://$PWD/og-card.svg"
```

## Development

Serve locally with any static server, e.g.:

```
python3 -m http.server 8765
```

## Deployment

Hosted on GitHub Pages from `main`. Push to `main` and the site rebuilds.

The site is served from a subpath (`/flooorstrawmap/`), so keep every asset link relative
and route the FAQ panel with the `#faq` hash rather than a `/faq` path — GitHub Pages has no rewrites.
