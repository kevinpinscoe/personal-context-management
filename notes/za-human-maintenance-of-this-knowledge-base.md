---
title: "Human Maintenance of this Knowledge Base"
aliases:
  - "human maintenance of this knowledge base"
  - "maintaining the knowledge base without ai"
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
  - maintenance
  - workflow
  - classification
created: 2026-06-15
updated: 2026-06-15
---

# Human Maintenance of this Knowledge Base

If AI tools became unavailable, this vault should remain maintainable through a small repeatable human workflow and a few simple scripts. The goal is to remove judgment from everything except the actual classification choice.

## Core Workflow

Use this process every time a rough note becomes durable:

1. Capture the rough note in `uncategorized/` or `journal/YYYY-MM-DD.md`.
2. Decide whether it belongs in `notes/`, `moc/`, `references/`, or `runbooks/`.
3. Search local LCC files for likely classification terms:

```bash
rg -i "linux|operating systems|software" lcc/
```

4. Pick a broad classification code, not a perfect formal call number.
5. Create the note from the appropriate template.
6. Add frontmatter: `title`, `classification`, `classification_label`, `primary_moc`, and tags.
7. Link the note from its primary MOC.
8. If no suitable MOC exists, create one.
9. Periodically review `uncategorized/` and cleanup queues.

## Helpful Scripts

Create small scripts under `scripts/`:

```text
scripts/new-note.sh
scripts/new-moc.sh
scripts/find-classification.sh
scripts/check-vault.sh
scripts/list-unlinked-notes.sh
scripts/triage-uncategorized.sh
```

`new-note.sh` should prompt for title, classification code, classification label, primary MOC, and tags, then create a lowercase hyphenated file in `notes/` from `templates/note-template.md`.

`new-moc.sh` should prompt for title, classification code, classification label, whether it is top-level, related MOCs, and tags, then create a lowercase hyphenated file in `moc/`.

If a MOC is marked top-level, the script should print a reminder to consider adding it manually to `home.md`. It should not edit `home.md` automatically because top-level status is a human navigation judgment.

## Classification Helper

Use a simple search helper instead of inventing a complex classifier:

```bash
scripts/find-classification.sh "knowledge management"
```

The script can be as simple as:

```bash
rg -i -C 3 "$*" lcc/
```

## Validation

`scripts/check-vault.sh` should check that:

- filenames are lowercase
- filenames contain no spaces
- required directories exist
- required templates exist
- notes have frontmatter
- notes have `title`
- notes have `type`
- notes in `notes/` have `classification`
- MOCs have `type: moc`
- no new content is added to `ingest/` or `Ingest/`

Run it before commits:

```bash
bash scripts/check-vault.sh
```

## Weekly Review

Once a week:

1. Open `home.md`.
2. Check whether top-level MOCs still feel right.
3. Open `moc/how-to-use-this-knowledge-base.md`.
4. Review `uncategorized/`.
5. Promote useful journal entries.
6. Link orphaned notes into MOCs.
7. Archive dead material.

## Standard

Do not try to perfectly classify everything. The goal is:

```text
Good enough to find again.
Good enough to group with nearby notes.
Good enough for a future human to understand why it is there.
```

The system works if note creation is easy, classification is broad, and MOCs stay curated.
