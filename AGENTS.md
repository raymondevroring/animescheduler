# Anime Scheduler

**Zero-dependency static HTML app.** Just open `index.html` in a browser — no server, no build step, no package.json.

## Data model

- **Anime data** → IndexedDB (`AnimeTrackerDB`, store `seasons`, keyed by season name). JSON files in root (`anime-*.json`) are user exports/backups, **not** loaded by the app at runtime.
- **Preferences** (theme, zoom, default season) → `localStorage` key `anime_prefs_v1`.
- State schema version 5 (`"v":5`). Migration from old `localStorage` keys (`anime_v5_*`) runs automatically on first load.
- Each item has a `label` field (string, defaults to `""`). Import normalizes missing `label` from old exports to `""`.
- **Label definitions** (name, URL, hex color) stored in `prefs.labels` array in localStorage. Four defaults on first load.

## Season & navigation

- Seasons range: **Winter 2025** through **Fall 2028** (`BASE_YEAR=2025`).
- URL hash: `#winter-2026` (lowercase, hyphenated). Also supports direct linking via `#Season-YYYY`.
- Season select dropdown + prev/next arrows in topbar.

## Integrations

- **AniList** — GraphQL `https://graphql.anilist.co` fetches episode count per title.
- **MyAnimeList** — link-out search URL (`https://myanimelist.net/search/all?q=...`).

## No tests, no CI, no linter, no typecheck.

Edit `index.html` directly. All logic, markup, and styles are in one file (~1280 lines).
