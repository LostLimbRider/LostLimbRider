# AGENTS.md

## What this is

Static website for Lost Limb Riders (nonprofit motorcycle community for amputees). Two HTML pages, a PHP guestbook API, and image assets. No build step, no package manager, no tests, no CI.

## Structure

- `index.html` — Landing page with inline CSS + JS (guestbook form uses localStorage client-side)
- `mission.html` — Mission proposal page (static, self-contained)
- `api/guestbook.php` — PHP backend for guestbook (reads/writes `data/guestbook.json`)
- `data/guestbook.json` — Guestbook data store (JSON array, file-locked writes)
- `assets/` — Images and a zip archive

## Gotchas

- CSS and JS are **inlined** in each HTML file — no external stylesheets or scripts except image references.
- The guestbook has **two independent implementations**: client-side localStorage (in `index.html`) and server-side PHP (`api/guestbook.php`). They are not wired together; the HTML form uses localStorage only.
- The PHP API uses `GUESTBOOK_ADMIN_KEY` env var for admin actions (download/clear).
- `index.html` references `assets/LLR COVER POSTER.png` (space in filename) as a background image — this file is not committed.
- No linting, formatting, or typechecking commands exist.
