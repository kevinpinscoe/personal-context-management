# Ingest Point: Self-Hosted RSS Reader (oksskolten pattern)

## Status

This ingest point describes the **preferred curation model** for PCM ingest from
RSS feeds. The worked example uses [oksskolten](https://github.com/babarot/oksskolten)
— an AI-native self-hosted RSS reader — but the pattern applies to any reader
that exposes its curation signal through a scoped API key.

See [glean.md](glean.md) for the predecessor that was retired when its API design
made headless ingest unworkable.

## Why this pattern

The pipeline needs to query the curated set headlessly (no browser session, no
stored password). A reader with proper API key support lets you:

- Authenticate with a revocable, scoped token (`Authorization: Bearer <key>`)
- Query exactly the articles you liked: `GET /api/articles?liked=1`
- Clear the like after distillation so the item ages out naturally

Readers that expose likes only through a JWT from an interactive login cannot be
automated without storing a personal password — avoid them for this use case.

## Reader: oksskolten

| Item | Value |
|---|---|
| **Source** | https://github.com/babarot/oksskolten |
| **Description** | AI-native self-hosted RSS reader; SQLite backend; multi-arch GHCR images |
| **Auth** | Scoped API key (`Authorization: Bearer ok_…`), created in Settings → API tokens |
| **REST API** | Fastify-based; full CRUD on articles, feeds, categories |
| **AI features** | On-demand summarize/translate; AI chat; exposes an MCP server |

Deploy as a Docker Compose service. Store the API key in your secret manager
(e.g. Vault, 1Password, or equivalent) — never on disk or in git. Set the base
URL in the same secret store entry for easy retrieval by automation.

## Curation signal — Like

The ingest signal is **Like** (`liked_at`). Read articles in the **Unread** view;
click the heart when you want an article kept. Everything else ages out.

| Need | Call |
|---|---|
| Authenticate (headless) | `Authorization: Bearer ok_<key>` (scope `read,write`) |
| **Select the curated set** | `GET /api/articles?liked=1` |
| Per-item actions | `POST /api/articles/:id/like` · `/bookmark` · `/read` |
| **Dedup after distill** | toggle the like off (`POST /api/articles/:id/like`) so the item ages out |
| Hide read articles in the UI | `GET /api/articles?unread=1` |

Article schema carries `read_at`, `bookmarked_at`, `liked_at` timestamps; list
filters: `liked`, `bookmarked`, `unread`, `read`, `feed_id`, `category_id`, `sort`.

## PCM pipeline flow

1. **Auth** — read API key from your secret manager; send as `Bearer ok_…`.
2. **Select** — `GET /api/articles?liked=1`.
3. **Enrich** — use the article's full text and URL. Optionally call the MCP
   server (`search`, `summarize`) for richer content.
4. **Distill** — write an Obsidian note under the matching `../obsidian/` category,
   following `../rules/` and LCC classification. Record `source: oksskolten` in
   frontmatter; put the original URL in `sources:`.
5. **Dedup** — toggle the like off so the item becomes purgeable.

## Credentials

Store the API key and base URL together in your secret manager. Automation reads
them at runtime — never write them to disk or commit them to git.

```bash
# Example: HashiCorp Vault / OpenBao
vault kv put secret/rss-reader api_key="ok_…" base_url="https://your-reader.example.com"

# Retrieve at runtime
API_KEY=$(vault kv get -field=api_key secret/rss-reader)
BASE_URL=$(vault kv get -field=base_url secret/rss-reader)
```

## Example Transformation Output (Obsidian note)

```markdown
---
title: "Article Title"
source: oksskolten
date: 2026-06-27
url: https://example.com/article
sources:
  - https://example.com/article (rss reader, liked)
tags: [ingest/rss, pcm-output]
---

# Article Title

> Summary or key excerpt here.

[Original](https://example.com/article)
```

## Open items (adapt to your setup)

- [ ] Deploy oksskolten (or equivalent reader) and expose it on your network
- [ ] Create a `read,write` API key in the reader's settings
- [ ] Store the key and base URL in your secret manager
- [ ] Decide on a retention/purge policy for read, un-liked articles
- [ ] Wire the `GET /api/articles?liked=1` call into your ingest script
