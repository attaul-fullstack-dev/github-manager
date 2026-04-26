# GitHub Manager

A single-file vanilla-JS web app to manage your GitHub account from the browser — repos, files, commits, gists, notifications — without ever opening github.com.

> Just open `index.html` in any modern browser. No build, no server, no dependencies to install.

## Features

- **Dashboard** — profile card, total repos / stars / forks, top-5 stars chart, recently updated repos, unread notification badge
- **Repositories** — search, filter (visibility + language), sort, create, rename, delete (typed-name confirm), fork external
- **File Explorer + Editor** — branch selector, breadcrumb navigation, syntax-highlighted viewer with line numbers, in-file find (with prev/next), edit + commit, single-file upload, ZIP upload (one file per commit, with progress bar), delete
- **Commits** — paginated history, lazy-loaded commit details (full message, author, SHA, file diff stats)
- **Search** — repos and users via the GitHub Search API
- **Notifications** — list unread, filter by type, mark one or all read
- **Gists** — list, create, edit (rename + content), delete, copy URL, public/secret toggle
- **Settings** — paste / verify / disconnect PAT, rate-limit info

## Tech

| Layer | Detail |
|---|---|
| File | `index.html` (single file, ~2.2k LOC) |
| Language | HTML5 + Vanilla JS (ES6+) + CSS3 |
| Auth | GitHub PAT (Personal Access Token) |
| API | GitHub REST API v3 (`https://api.github.com`) |
| Storage | `localStorage` (PAT, cache, UI state) |
| CDN libraries | Chart.js, JSZip, highlight.js |

## Run it

```bash
# Option A — open the file directly
xdg-open index.html        # Linux
open index.html            # macOS

# Option B — serve locally (any static server works)
python3 -m http.server 8080
# then visit http://localhost:8080
```

## PAT setup

1. Go to <https://github.com/settings/tokens?type=beta> (fine-grained) or <https://github.com/settings/tokens/new> (classic)
2. Required permissions: **repo** (read/write), **gist**, **notifications**, **read:user**
3. Open the app → **Settings** → paste the token → **Save & verify**

The token is stored in `localStorage` and sent only to `api.github.com`. Nothing is uploaded anywhere else.

## Theme

Dark mode only. Accent `#a855f7` (purple). Mobile-friendly with a bottom nav under 768px.

## Routes

Hash-based: `#dashboard`, `#repos`, `#explorer/<owner>/<repo>[/<branch>[/<path>]]`, `#commits/<owner>/<repo>`, `#search`, `#notifications`, `#gists`, `#settings`.

## License

MIT.
