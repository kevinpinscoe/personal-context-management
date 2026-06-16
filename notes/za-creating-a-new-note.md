---
title: "Creating a new note"
aliases:
  - "how to create a new note"
type: note
classification: ZA
classification_label: "Information resources"
classification_source: lcc
classification_detail: ZA4050-4480
classification_detail_label: "Electronic information resources"
primary_moc: "How to use this Knowledge Base"
related_mocs:
  - "Personal Knowledge Management"
  - "Maps of Content"
tags:
  - knowledge-base
  - note-taking
  - navigation
created: 2026-06-15
updated: 2026-06-15
---

# Creating a new note

A top-level MOC is "top-level" because you decide it is useful as a front-door category. A lower-level MOC is "lower-level" because you decide it is better reached through another topic.

There is no objective database rule that makes Linux top-level and systemd lower-level. It depends on how you use the vault.

For example:

- If Linux is one of your major knowledge areas, Linux is top-level and systemd is lower-level.
- If your work is deeply centered on init systems, systemd could become top-level.
- If dermatology is a major research area, Skin Conditions is top-level.
- If it is only one small personal reference area, it might stay lower-level under Health.

So the practical rule is:

```text
Top-level MOC = a place you want to start from.
Lower-level MOC = a place you want to arrive at through another place.
```

A useful test:

```text
Would I be annoyed if this was missing from home.md?
Would I be annoyed if every similar-sized topic was added to home.md?
```

If both answers are yes, it probably needs a parent MOC rather than being on home.md.

For another AI, the safest behavior is:

```text
Do not promote a MOC to home.md unless it is clearly broad, durable, and repeatedly useful as an entry point.
When uncertain, create or update the MOC, then link it from the nearest broader MOC instead of home.md.
```
