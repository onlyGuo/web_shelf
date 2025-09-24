# Repository Guidelines

## Project Structure & Module Organization
`index.html` in the repository root contains the entire UI: semantic HTML markup, inline CSS for the iOS-style layout, and vanilla JavaScript that manages folders, bookmarks, and background themes via `localStorage`. Keep new assets lightweight and reference them from the same file unless you introduce a clearly scoped subdirectory (e.g., `assets/` for images). The `.idea/` folder only stores IDE metadata and should remain untouched in reviews.

## Build, Test, and Development Commands
No bundler or build step is required; open the page directly or run a lightweight static server for live testing:
- `python3 -m http.server 8080` — serve the site locally at `http://localhost:8080/index.html`.
- `open index.html` (macOS) — quick spot-check without starting a server.
Document any new tooling inside this guide if you add it.

## Coding Style & Naming Conventions
Match the existing four-space indentation in HTML, CSS, and JavaScript. Favor descriptive `const`/`let` declarations and camelCase for functions (`renderItems`, `saveData`). Keep CSS selectors scoped to existing class patterns; prefer extending current utility styles instead of adding global overrides. If you add linting or formatting, configure it to preserve these defaults and note the command above.

## Testing Guidelines
Run manual smoke tests in modern Chromium, Safari, and Firefox: load the page, add/edit/delete bookmarks and folders, toggle edit mode, and confirm persistence after refresh (driven by `localStorage`). When adjusting visuals, verify responsiveness around 375px and 1200px breakpoints. If you add automated tests (e.g., Playwright), store them under `tests/` and document the invocation command here.

## Commit & Pull Request Guidelines
There is no established Git history yet, so default to Conventional Commits (e.g., `feat: add folder color picker`). Reference related issues in the body, include before/after screenshots for UI changes, and describe manual QA steps performed. PRs should stay focused; split large refactors into smaller reviews.

## Data & Configuration Notes
The app persists state in browser `localStorage` keys (`webshelf_items`, `webshelf_folders`, `webshelf_background`). When debugging, clear these keys via devtools or offer a reset button. Avoid shipping secrets or remote dependencies; everything should remain client-side.
