# Ingest Point: Glean RSS Reader (MCP)

## Summary

[Glean](https://glean.kevininscoe.com) is a self-hosted RSS reader with a native MCP interface. The PCM pipeline connects to it via MCP rather than parsing local files — the AI agent calls Glean's MCP tools directly to search, list, and retrieve articles from subscriptions.

## Credential Status

**Token is in 1Password.** Migration to OpenBao is pending — see `../TODO.md`.

## Instance

| Item | Value |
|---|---|
| **URL** | https://glean.kevininscoe.com |
| **MCP endpoint** | https://glean.kevininscoe.com/mcp/mcp |
| **Auth** | Bearer token (`Authorization: Bearer <token>`) |
| **Token location** | 1Password (migration to OpenBao pending) |

## MCP Configuration

```json
{
  "mcpServers": {
    "glean": {
      "url": "https://glean.kevininscoe.com/mcp/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_TOKEN"
      }
    }
  }
}
```

## Available MCP Tools

| Tool | Purpose |
|---|---|
| `search_entries` | Search articles by keyword |
| `get_entry` | Get full article details by ID |
| `list_entries_by_date` | List articles within a date range |
| `list_subscriptions` | List all subscriptions in the reader |

## PCM Pipeline Usage

Unlike the file-based ingest points, Glean is queried live via MCP:

1. Agent calls `list_subscriptions` to understand available feeds.
2. Agent calls `list_entries_by_date` or `search_entries` to find candidate articles.
3. Agent calls `get_entry` to retrieve full article content.
4. Article is transformed into an Obsidian note under `../obsidian/from-glean/`.
5. No local SQLite cleanup required — Glean manages its own read/unread state.

## Preprocessing Notes

- Use `search_entries` with interest keywords rather than ingesting all articles — Glean may have high volume across all subscriptions.
- `list_entries_by_date` is useful for bounded daily/weekly ingestion runs.
- Interest/selection criteria (which keywords, which subscriptions to prioritize) to be defined alongside the general pipeline selection logic — see `../TODO.md`.

## Example Transformation Output (Obsidian note)

```markdown
---
source: glean
subscription: "Example Feed Name"
date: 2026-06-13
url: https://example.com/article
tags: [ingest/glean, ingest/rss]
---

# Article Title

> Summary or key excerpt here.

[Original](https://example.com/article)
```
