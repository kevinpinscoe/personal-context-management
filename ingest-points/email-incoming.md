# Ingest Point: Incoming Email (Newsletters & Subscriptions)

## Summary

Subscription newsletters, Medium.com articles, and miscellaneous email distributions delivered to `incoming@incoming.example.com`. Postfix on `mail1.example.com` receives them; a nightly job copies them to a local drop directory.

## Addresses

| Role | Address |
|---|---|
| Delivery address | `incoming@incoming.example.com` |
| Receiving MTA | `mail1.example.com` (Postfix) |

## Location

```
~/KnowledgeVault/personal-knowledge-base/ingest/emails/incoming/
```

## Directory Layout

Each email lands as a timestamped subdirectory containing one file:

```
incoming/
├── 20260508154158/
│   └── message.eml
├── 20260509105906/
│   └── message.eml
└── ...
```

- **Directory name**: delivery timestamp in `YYYYMMDDHHmmss` format (UTC, from Postfix envelope).
- **`message.eml`**: full RFC 2822 message including all headers, MIME parts, and body.
- Duplicate deliveries within the same second get a `-N` suffix (e.g. `20260530180842-1`).

## Format Details

- Standard RFC 2822 email with a leading mbox-style `From <sender> <timestamp>` envelope line.
- Bodies are typically `text/html` (newsletters) or `multipart/alternative` with both `text/plain` and `text/html` parts.
- Images are usually external references, not inline attachments.
- DKIM-signed by the sending domain; no special handling needed.

## Preprocessing Notes

- Strip all HTML and extract readable text before passing to an AI agent; newsletters are heavily styled.
- Prefer the `text/plain` MIME part when present — it is cleaner than the HTML equivalent.
- Filter on `To:` header containing `incoming@incoming.example.com` to confirm correct drop.
- The `Subject:` and `From:` headers are sufficient to identify the source publication before full parsing.
- Unsubscribe links and tracking pixels are present in most newsletters; ignore them during transformation.

## Volume

~68 messages as of 2026-06-13. New messages arrive nightly.

## Example Transformation Output (Obsidian note)

```markdown
---
source: email-incoming
from: newsletter@example.com
date: 2026-05-08
subject: "Weekly Digest: AI Tools"
tags: [ingest/email, ingest/newsletter]
---

# Weekly Digest: AI Tools

> Extracted summary or key excerpt here.

---
*From: newsletter@example.com — delivered to incoming@incoming.example.com*
```
