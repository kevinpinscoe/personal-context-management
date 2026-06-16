# Ingest Point: Notes Email (Self-Mailed Notes)

## Summary

Notes, ideas, and quick captures mailed by the user to `notes@notes.example.com` from `user@example.com`. Postfix on `mail1.example.com` receives them; a nightly job copies them to a local drop directory.

## Addresses

| Role | Address |
|---|---|
| Delivery address | `notes@notes.example.com` |
| Receiving MTA | `mail1.example.com` (Postfix) |
| Sending address | `user@example.com` |

## Location

```
~/KnowledgeVault/personal-knowledge-base/ingest/emails/notes/
```

## Directory Layout

Same structure as the incoming newsletter drop:

```
notes/
├── 20260508141145/
│   └── message.eml
├── 20260508141841/
│   └── message.eml
└── ...
```

- **Directory name**: delivery timestamp in `YYYYMMDDHHmmss` format (UTC, from Postfix envelope).
- **`message.eml`**: full RFC 2822 message including all headers and body.

## Format Details

- Sent from Gmail; DKIM-signed by `gmail.com`.
- Bodies are typically `text/plain` (quick typed notes) or `multipart/alternative` when sent from a mobile client.
- Subject line is the note title or topic — use it as the Obsidian note title.
- No newsletters, no tracking pixels, no unsubscribe links.

## Preprocessing Notes

- Prefer `text/plain` MIME part — these are personal notes, not formatted HTML.
- The `Subject:` header maps directly to the Obsidian note title.
- The `Date:` header is the authoritative capture timestamp.
- No filtering needed: all messages in this drop are self-authored captures.
- Body may contain URLs, code snippets, or freeform text — pass as-is to the AI agent for structuring.

## Volume

~17 messages as of 2026-06-13. New messages arrive as the user sends them (delivered nightly).

## Example Transformation Output (Obsidian note)

```markdown
---
source: email-notes
date: 2026-05-08
subject: "Idea: RSS pipeline filter by domain"
tags: [ingest/email, ingest/self-note]
---

# Idea: RSS pipeline filter by domain

> Original note body here, lightly formatted.

---
*Self-mailed to notes@notes.example.com on 2026-05-08*
```
