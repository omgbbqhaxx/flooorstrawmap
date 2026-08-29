# flooor strawmap

A work-in-progress draft roadmap for the [flooor](https://flooor.fun) protocol on Base.

**Next release — Cobalt, September 2026.** After that, releases carry placeholder names (D\*, E\*, F\*) until their scope firms up.

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

The map is a CSS grid: one column per release, one row per layer (A auction, V vault, S surface).
Each box is a `div.box`, with `--headliner` (dark), `--offchain` (dashed), or `--shipped` (faint) modifiers.
North stars live in the `.northstars` block on the right. Bump the revision date in the legend and in the header meta after a change.

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
