---
created: 2026-06-13T19:23
"modified: ": 2026-06-16T00:00
---
# File Naming Rules

Rules in `/rules` are ground documents for this knowledge base. When making changes in this vault, follow these rules. If a requested change conflicts with a rule, challenge the request and clarify before changing the vault.

Filesystem names must always be lowercase, contain no spaces, and use hyphens to separate words for human clarity.

This rule applies to file and directory names only. It does not apply to Markdown headings, note titles, aliases, tags, classification labels, MOC names, or other frontmatter values. Those values may use normal capitalization, spaces, punctuation, and formal classification codes when useful.

Examples of valid filenames:

```text
moc/linux.md
moc/compute-infrastructure.md
notes/qa76-linux-systemd-timers.md
references/linux-kernel-documentation.md
journal/2026-06-15.md
```

Examples of valid frontmatter values inside those files:

```yaml
title: "Linux systemd timers"
aliases:
  - "systemd timers"
classification: QA76
classification_label: "Computer software / operating systems"
primary_moc: "QA76 - Computer software"
```

For top-level MOCs, prefer plain human-topic slugs such as `moc/linux.md` or `moc/compute-infrastructure.md`. Store classification codes and labels in frontmatter. Classification codes may still appear in ordinary note filenames when useful as shelf markers.

Exceptions: `README.md`, `AGENTS.md`, and `RUNBOOK.md` may use uppercase names because they are conventional top-level documentation files.
