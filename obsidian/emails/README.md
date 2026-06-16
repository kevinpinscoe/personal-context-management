# obsidian/emails/ — Distilled Content from Email Ingest

Distilled knowledge extracted from newsletter and self-mailed note ingest sources.

## What Belongs Here

- Key takeaways from newsletters and subscription emails that passed the interest filter
- Self-mailed notes that have been expanded and cleaned up into reference knowledge
- Actionable items surfaced from email content: tools, techniques, decisions

## Frontmatter Template

```yaml
---
title: ""
created: YYYY-MM-DD
category: emails
sources:
  - incoming@incoming.example.com (newsletter: Name, YYYY-MM-DD)
  - notes@notes.example.com (self-note, YYYY-MM-DD)
tags:
  - pcm-output
  - emails
---
```

## Content Notes

- Strip all PII from the source email before writing the note. Attribution via
  the `sources` frontmatter field is sufficient — do not reproduce sender names,
  email addresses in body text, or unrelated personal details.
- Self-mailed notes often contain rough context. Expand and normalize them into
  a reusable reference form.
- If the email's content clearly belongs in another category (`ai/`, `infrastructure/`,
  etc.), write it there instead and omit this directory.

## See Also

- [obsidian/README.md](../README.md) — promotion workflow and frontmatter rules
- [ingest-points/email-incoming.md](../../ingest-points/email-incoming.md)
- [ingest-points/email-notes.md](../../ingest-points/email-notes.md)
