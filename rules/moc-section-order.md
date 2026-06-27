---
created: 2026-06-27
modified: 2026-06-27
---
# MOC Section Order Rule

Rules in `/rules` are ground documents for this knowledge base. When making changes in this vault, follow these rules. If a requested change conflicts with a rule, challenge the request and clarify before changing the vault.

## Required section order for MOC files

Every MOC file in `moc/` must use the following section order:

```text
## Overview
## Child MOCs      ← omit only if the MOC is a confirmed leaf (no children will ever exist)
## Notes
## Related MOCs
```

**Child MOCs must appear before Notes.** This order exists so that readers and AI agents navigating the hierarchy can immediately drill down to a more specific MOC before reading individual notes. Putting Notes first buries the hierarchy under content.

## Rationale

MOCs are navigation hubs, not content pages. The first action a reader takes in a MOC is to decide whether to go deeper (follow a child MOC) or start reading notes. Surfacing the drill-down path at the top makes that decision fast.

## Applying this rule

- When creating a new MOC, copy `templates/moc-note-template.md` — it already uses the correct order.
- When editing an existing MOC, move `## Child MOCs` above `## Notes` if it is not already there.
- **Do not omit `## Child MOCs`** unless the MOC is definitively a leaf node (a terminal topic with no plausible subtopics). Even an empty `## Child MOCs` section is preferable to omitting it for non-leaf MOCs.
- If a MOC currently has no children, write the section with a placeholder:
  ```markdown
  ## Child MOCs

  None yet.
  ```

## Challenge clause

If a human asks to add sections or reorder a MOC file in a way that would place `## Notes` above `## Child MOCs`, stop and challenge the request:

> This would violate `rules/moc-section-order.md`: Notes must appear after Child MOCs in every MOC file.
> Do you want to override this rule for this change? If yes, I will proceed. If no, I can place the content in the correct order.
