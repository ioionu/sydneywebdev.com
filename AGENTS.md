# AGENTS.md

Single-page static site. No build, no tests, no linter, no CI — just edit files in the repo root.

## Layout

- `index.html` — the entire page (CSS inline in `<style>`, canvas game JS inline). Only page in the site.
- Root-level assets referenced by absolute path on the live site: `logo.svg`, `favicon.ico`, `sydneywebdev.png` (og:image uses `https://sydneywebdev.com/sydneywebdev.png`, so keep it at the root).
- `main.py` — dev-only livereload wrapper. The commented-out `lessc` line is dead; no LESS is used.

## Commands

- Dev server: `uv run main.py` (Python 3.11 via `uv`, `.python-version`; livereload is a dev dependency in `pyproject.toml`). Auto-reloads the browser on change.
- No test/typecheck/lint commands exist; verify by opening the page in a browser.

## Deployment

- Branch is `master` (not `main`). `origin` is a GitHub mirror (`ioionu/sydneywebdev.com`); deploy by pushing `master` to the `piku` remote (also `piku-old` and `web` remotes exist).
- `Procfile` (`static: /`) and `ENV` (`NGINX_HTTPS_ONLY`, `NGINX_SERVER_NAME`) are Heroku-style staticfile config; keep them in sync if the deploy target's domain changes.