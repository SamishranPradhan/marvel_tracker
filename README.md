# Marvel Watch Tracker

A single-file, no-install tracker for every Marvel movie, series and animated show, organised by universe, with checkmarks so you can see exactly what you've watched.

> Unofficial fan project. Not affiliated with, endorsed by, or sponsored by Marvel or The Walt Disney Company. Marvel and all related names are trademarks of their respective owners.

## Features

- **11 universes, 126 titles:** the MCU (by phase), Sam Raimi's and Marc Webb's Spider-Man films, Sony's Spider-Man Universe, Spider-Verse, Fox's X-Men and Fantastic Four films, Blade, the Marvel Television shows, Spider-Noir and Ghost Rider. Announced but unreleased titles are included.
- **One-tap checkmarks** for titles, whole sections, or whole universes, plus a live progress bar and profile stats.
- **Search and universe filters** to focus on one franchise.
- **Mark all visible watched** with confirmation, and **Undo mark all**.
- **Add, edit and delete your own titles**, including brand-new universes, with **Undo delete**. Built-in titles can be corrected (title and year) too.
- **Library:** every title in one list, filterable by watched/unwatched and sortable by year or title.
- **Watch order:** release order (by exact date) or chronological order (the MCU follows Marvel's official timeline on Disney+; Fox X-Men uses an approximate in-universe order).
- **Release dates:** a full date for every title, with Released/Upcoming filters.
- **Marvel news:** saved headlines, plus a best-effort live feed (see limitations).
- **Export / Import** your progress, custom titles and profile name as a JSON file.

Everything except the news page lives in the 3-dot menu next to your profile.

## Quick start

1. Download `index.html` (the tracker is a single file).
2. Open it in any modern browser. That's it. No build step, no dependencies.

## Publish on GitHub Pages

1. Create a public repository and upload the file as `index.html`.
2. Go to **Settings, then Pages**, set **Source** to **Deploy from a branch**, choose **main** and **/ (root)**, and save.
3. After a minute your tracker is live at `https://<your-username>.github.io/<repo-name>/`.

To push an update, upload the new `index.html` over the old one.

## How your data is stored

There is no server and no database. Your checkmarks, custom titles, title corrections and profile name are saved in your browser's `localStorage`, under keys beginning with `marvel-tracker-`.

- Progress is **private to that browser on that device**. It does not sync between browsers or devices.
- Clearing site data for the page erases it. Use **Export progress** now and then as a backup.
- To move progress between devices, export on one and import on the other. Importing **replaces** current progress with the file's contents, and the app asks you to confirm first. Files exported from a different app are rejected.

## Updating the title list

The data lives at the top of the `<script>` block in `index.html`:

| Constant | Purpose |
| --- | --- |
| `BASE_UNIVERSES` | Universes, sections and `["Title","Year"]` entries |
| `RELEASE_DATES` | Exact dates (`YYYY-MM-DD`, or `YYYY-MM` / `YYYY` if unconfirmed) keyed by universe id and title |
| `WATCH_ORDER` | Chronological order lists |
| `NEWS_SNAPSHOT` | Saved news headlines |

When you add a title to `BASE_UNIVERSES`, add its date to `RELEASE_DATES` using the exact same title text. You can also add titles from inside the app without editing code.

## Known limitations

- **Live news:** the news page tries to load a live headline feed through a third-party RSS-to-JSON service. Browsers, some hosts and the Claude chat preview can block that request, and the service can rate-limit. When it fails, the page shows the saved headlines instead.
- **No accounts or login.** Progress is local only.
- **Dates and announcements change.** Release dates and unreleased titles were gathered in October 2026 and will drift. Month-only or year-only entries are not confirmed dates.
- **Chronological order** for Fox's X-Men films is approximate, and titles missing from an official timeline are listed after it by release date.
- Editing a title through the app keeps its checkmark. Changing a title or year directly in the source code changes its internal id, so that title's checkmark resets.

## Browser support

Any current version of Chrome, Edge, Firefox or Safari.

## License

Add a license of your choice (for example MIT) before publishing.
