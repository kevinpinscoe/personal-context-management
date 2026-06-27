# Ingest Point: Glean RSS Reader (MCP)

> **⚠️ RETIRED for PCM ingest.** Glean is superseded by a self-hosted RSS reader
> with proper API key support — see [oksskolten.md](oksskolten.md). This file is kept
> for history. Do not resume the REST-auth work described below.

## Why it was retired

Glean has two interfaces with two different auth systems:

| Surface | Accepts | Exposes the Like (curation) signal? |
|---|---|---|
| **MCP** | long-lived API token | ❌ No — only `is_read` |
| **REST** | JWT from interactive login only | ✅ Yes — `GET /api/entries?is_liked=true` |

The curation model requires querying the liked set headlessly. The REST API
that exposes likes only accepts a JWT obtained through an interactive login —
there is no long-lived API token for REST. This means the pipeline cannot run
without storing a personal password, which is unacceptable.

The MCP interface accepts the API token but cannot see likes at all, so it
cannot determine which articles the human has curated for ingest.

## What it taught us

The right tool exposes the curation signal through its API using a scoped,
revocable token — not through a session JWT that requires an interactive login
to obtain. See [oksskolten.md](oksskolten.md) for a reader that gets this right.

## Original pipeline (for reference)

Before the retirement decision, the intended flow was:

1. Authenticate via `POST /api/auth/login` → JWT.
2. Query `GET /api/entries?is_liked=true`.
3. Distill each entry into an Obsidian note.
4. Clear the like via `DELETE /api/entries/{id}/reaction` after distillation.

The pattern is sound — the auth mechanism is what made it unworkable headlessly.

## Example Transformation Output (Obsidian note)

```markdown
---
title: "Article Title"
source: glean
date: 2026-06-22
url: https://example.com/article
sources:
  - https://example.com/article (glean, liked)
tags: [ingest/glean, ingest/rss, pcm-output]
---

# Article Title

> Summary or key excerpt here.

[Original](https://example.com/article)
```
