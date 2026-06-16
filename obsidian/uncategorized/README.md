# obsidian/uncategorized/ — Staging Area

Holding area for AI-distilled output that does not clearly belong in any other
category, or where categorization was deferred to human review.

## What Belongs Here

- Output files where the category was not obvious during pipeline processing
- Notes that span multiple categories and need a human decision on placement
- Anything the pipeline flagged as uncertain

## Frontmatter Template

```yaml
---
title: ""
created: YYYY-MM-DD
category: uncategorized
move-to: ""       # fill in the target category before promoting
sources:
  - https://...
tags:
  - pcm-output
  - uncategorized
---
```

## Review Process

1. Open each file and read the content.
2. Decide on the correct category from the available `obsidian/` directories.
3. Fill in `move-to:` in the frontmatter.
4. Move the file to the correct directory and update its `category` field.
5. Commit and push.

This directory should be emptied regularly. If files accumulate here without
being reviewed, the interest filter in `interests.md` may need to be sharpened.

## See Also

- [obsidian/README.md](../README.md) — promotion workflow and frontmatter rules
- [interests.md](../../interests.md) — interest filter driving content selection
