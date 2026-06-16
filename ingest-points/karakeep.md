# Ingest Point: Karakeep (Bookmarks + Tags)

## Status

**PENDING** — prerequisites must be completed before this ingest point is active. See `../TODO.md`.

## Summary

[Karakeep](https://karakeep.kevininscoe.com) is a self-hosted bookmarking and read-later service with tag-based organization. The PCM pipeline will query the Karakeep API by tag to retrieve bookmarks of interest and transform them into Obsidian notes.

## Instance

| Item | Value |
|---|---|
| **URL** | https://karakeep.kevininscoe.com |
| **Dashboard / Tags** | https://karakeep.kevininscoe.com/dashboard/tags |
| **API base** | https://karakeep.kevininscoe.com/api/v1 |

## Prerequisites (Blocking)

1. **Tag cleanup** — current tags are inconsistent; normalize before the pipeline depends on them. See `../TODO.md` for tracking.
2. **API credentials** — generate a Karakeep API token with read-only scope. Store per `~/ai/directives/storing-secrets.md`. See `../TODO.md`.

## Planned Integration

Once prerequisites are complete:

- AI agent queries the Karakeep API for bookmarks under selected tags.
- Each bookmark (title, URL, tags, notes/highlights) is transformed into an Obsidian note under `../obsidian/from-karakeep/`.
- Tag selection criteria (which tags to ingest, and when) to be defined alongside the general interest-selection logic.

## API Notes

Karakeep exposes a REST API. Key endpoints (once credentials exist):

| Endpoint | Purpose |
|---|---|
| `GET /api/v1/bookmarks` | List bookmarks (supports `?tag=` filter) |
| `GET /api/v1/tags` | List all tags |

Authentication: Bearer token in `Authorization` header.

## Example Transformation Output (Obsidian note)

```markdown
---
source: karakeep
date: 2026-06-13
url: https://example.com/article
tags: [ingest/karakeep, <karakeep-tag>]
---

# Article Title

> User note or highlight here (if present).

[Original](https://example.com/article)
```
