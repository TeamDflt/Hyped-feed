# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repo manages the featured events feed for the **Hyped** countdown timer app. It contains:
- `featured.json` — the feed data consumed by the Hyped app
- A local HTML editor page for editing `featured.json` without touching the JSON directly

## Data Schema

### `featured.json`

Top-level fields:
- `version` — Integer. Increment when making breaking schema changes.
- `updated_at` — ISO 8601 date string. Update whenever the file is modified.
- `timers` — Array of featured countdown event objects.

Timer object fields:
| Field | Type | Description |
|---|---|---|
| `id` | string | Unique slug identifier |
| `name` | string | Display name of the event |
| `target_timestamp` | number | Unix timestamp in **milliseconds** |
| `category` | string | One of: `GAME`, `SPORTS`, `PREMIERE`, `MUSIC`, `CONCERT`, `MILESTONE` |
| `image_url` | string\|null | URL for event imagery |
| `notes` | string | Short description or tagline |
| `target_timezone` | string | IANA timezone string (e.g. `America/New_York`) |
| `is_live_event` | number | `1` if the event is live/ongoing, `0` otherwise |

## Editor

`editor.html` is a local, self-contained UI for editing `featured.json` without touching the JSON directly.

**How to use:**
1. Open `editor.html` in a modern browser (Chrome or Edge recommended — requires File System Access API).
2. Click **Open JSON** and select `featured.json`.
3. Add, edit, reorder, or delete timers through the UI.
4. Press **Save JSON** (or `Cmd+S`) to write changes back to the file. `updated_at` is updated automatically.

No server, no build step, no dependencies.
