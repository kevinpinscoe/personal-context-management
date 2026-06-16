# obsidian/software-tools/ — Tools to Evaluate or Adopt

Distilled assessments of software tools, libraries, CLIs, services, and platforms
that crossed the interest filter and are worth evaluating or have already been adopted.

## What Belongs Here

- Tool discovery notes: what it is, what problem it solves, why it passed the filter
- Evaluation results: tried it, here is what happened
- Adoption decisions: decided to use it, here is how
- Rejection notes: considered it, here is why it was passed on

## Frontmatter Template

```yaml
---
title: ""
created: YYYY-MM-DD
category: software-tools
status: ""        # discovered | evaluating | adopted | rejected
subcategory: ""   # e.g. cli, library, service, platform, monitoring, database
sources:
  - https://...
tags:
  - pcm-output
  - software-tools
---
```

## Content Notes

- Always include a `status` field — it answers "where did this end up?" at a glance.
- For evaluations and adoptions, include the version or date tested.
- For rejections, record the reason so the same tool is not re-evaluated without cause.

## See Also

- [obsidian/README.md](../README.md) — promotion workflow and frontmatter rules
- [obsidian/ai/](../ai/README.md) — for AI-specific tool evaluations
- [obsidian/infrastructure/](../infrastructure/README.md) — for infrastructure tooling
