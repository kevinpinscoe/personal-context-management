# Personal Context Management

This repository collects my workflow for building a Personal Context Management
(PCM) system in Obsidian.

PCM is about capturing what matters right now so tools, people, and AI can work
with the right background. It is not just a knowledge archive. It is an
operating context for current goals, constraints, preferences, active projects,
recent decisions, and the working assumptions that shape useful assistance.

## PKM vs PCM

Personal Knowledge Management (PKM) is about managing what I know:

- notes
- references
- research
- bookmarks
- project docs
- runbooks
- troubleshooting history

Personal Context Management (PCM) is about managing what should already be known
before helping me act:

- who I am
- how I work
- what I am focused on now
- what constraints matter
- what decisions have already been made
- what preferences should guide output
- what context an AI agent needs to operate usefully

A simple rule:

> If it teaches me something, it belongs in PKM. If it changes how assistance
> should behave, it belongs in PCM.

## Why Obsidian

Obsidian is the workspace for this system because it is local-first, Markdown
based, linkable, searchable, and flexible enough to act as the working memory for
human and AI-assisted workflows.

In this approach, the vault is not the final product. The vault is the substrate:
the place where context, memory, tasks, decisions, and handoffs can live so that
future work starts with less re-explaining.

## Intended Workflow

This repo is for designing the workflows and structure behind my own PCM
Obsidian vault. The goal is to define repeatable patterns for:

- storing durable personal and project context
- keeping current goals and priorities visible
- recording active decisions and why they were made
- maintaining task and project continuity across sessions
- capturing preferences that should guide AI-assisted work
- separating long-term knowledge from active operating context
- making the vault useful without turning folder maintenance into the main job

## Core Ideas

- **Context over cataloging**: The system should help with current action, not
  just organize old information.
- **The vault as working memory**: Obsidian holds the context an assistant or
  future version of me needs to resume work quickly.
- **Agent-ready notes**: Files should be clear enough for AI tools to read,
  summarize, update, and apply.
- **Low-maintenance structure**: The system should reduce friction, not create
  another taxonomy project.
- **Human judgment stays on top**: Automation can maintain context, but I still
  decide priorities, direction, and final output.

## Core Model

Folders are for storage.
MOCs are for navigation.
Links are for relationships.
Classification is for orientation.

A note should usually live in one simple place, but it may be linked from many
topic pages. This avoids forcing every note into a single rigid hierarchy when
the same note may belong to several subjects.

## Repository Layout

```
├── archive/          # Retired or superseded content
├── attachments/      # Images, PDFs, and other supporting files
├── ingest-holding/   # Temporary staging for ingest candidates
├── ingest-points/    # Ingest pipeline configuration (one file per source)
├── journal/          # Dated daily notes (YYYY-MM-DD.md)
├── lcc/              # Library of Congress Classification outlines
├── moc/              # Maps of content
├── notes/            # Evergreen notes
├── obsidian/         # AI-distilled output mirroring vault categories
├── references/       # Source summaries and external research
├── rules/            # Ground rules — naming conventions and layout
├── runbooks/         # Step-by-step operational procedures
├── templates/        # Reusable note templates
├── uncategorized/    # Notes without a clear home — triage regularly
├── home.md           # Vault entry point
├── interests.md      # Personal interests and focus areas
└── interests.yaml    # Machine-readable interests for the ingest pipeline
```

## What Belongs in Each Folder

### `home.md`

The front door. Links to major MOCs, active study areas, and recent work. Does
not try to list every note.

Treat it like the front page of a private wiki.

### `moc/`

Maps of Content. Navigation hubs that link to notes by topic, project,
classification, or place.

A note can appear in multiple MOCs. MOCs should contain context and links —
they should not become long mixed-content articles.

### `notes/`

Evergreen working notes. Use broad LCC-style prefixes in filenames.

Keep notes in this folder unless there is a strong reason to move them
elsewhere. Avoid deep topic folders under `notes/`; use MOCs and links instead.

### `runbooks/`

Step-by-step operational procedures — how to do a thing.

### `references/`

Source summaries, documentation links, bibliographic notes, and external
research. Put the source URL or citation in frontmatter when possible. This
folder is for material that supports knowledge work but is not itself the main
working note.

### `lcc/`

LCC outline files downloaded from the Library of Congress. Each file
(`lcco-<class>.md`) covers one class letter or letter group. When classifying a
new MOC or note, read the relevant file here to identify the correct class code
and label. This is the authoritative lookup source for all classification
decisions in this vault.

### `journal/`

Dated daily notes. Name files `YYYY-MM-DD.md`.

### `attachments/`

Images, PDFs, screenshots, exported diagrams, and files embedded by Obsidian.
Keeping attachments separate prevents root-folder clutter.

### `templates/`

Reusable note skeletons. Templates reduce friction and keep notes consistent.

### `archive/`

Retired, superseded, historical, or inactive content. Archive does not mean
deleted — it means the content is not part of the active working map.

### `rules/`

Vault ground rules and layout constraints. Rules in this directory are
mandatory — not suggestions.

- All filenames must be lowercase, contain no spaces, and use hyphens to
  separate words. Exception: `README.md`, `AGENTS.md`, and `RUNBOOK.md` may
  use uppercase names.
- See `rules/file-naming-rules.md` and `rules/rules-directory-layout.md` for
  the full set.

### `ingest-points/`

Documents each content source available to the PCM pipeline. Each file
describes a source (email, RSS, bookmarks, saved files) and how it is accessed.

### `ingest-holding/`

Temporary staging area for ingest files that have been retrieved but not yet
processed.

### `obsidian/`

AI-distilled output ready to be dropped into the live Obsidian vault. Mirrors
the category structure of PersonalKnowledgeVault.

### `uncategorized/`

Temporary holding area for notes that arrived without a clear home. Triage this
folder regularly — notes here should be promoted, linked, classified, archived,
or deleted.

## Rules

Ground rules for this knowledge base live in `rules/`. They govern file naming
and directory placement. Claude Code is configured in `CLAUDE.md` to enforce
these rules and challenge any request that would violate them. The human may
override a rule by explicitly confirming the exception.

Key rules:

- All filenames must be lowercase, contain no spaces, and use hyphens to
  separate words. Exception: `README.md`, `AGENTS.md`, and `RUNBOOK.md` may
  use uppercase names.
- Content must land in the correct functional directory as defined in
  `rules/rules-directory-layout.md`.
- Before creating or moving any file, check `rules/file-naming-rules.md`.
- Before adding or restructuring directories, check
  `rules/rules-directory-layout.md`.
- If a request would violate a rule, stop and challenge the request before
  making any change.

## LCC Classification Model

This knowledge base uses a Library of Congress Classification (LCC)-inspired
top-level map.

Why use a classification? Because naming is hard. Instead of inventing my own
subject system, I wanted to reuse an established classification scheme.
Classifications help me place notes into broad subject areas, supplement Maps
of Content, and provide structured metadata for building knowledge-relationship
graphs. A classification gives me a stable subject scaffold, while MOCs give me
human-curated navigation. They complement each other.

The authoritative Library of Congress Classification schedules are maintained
by the Library of Congress:

```text
https://www.loc.gov/aba/publications/FreeLCC/freelcc.html
```

This vault does not attempt to become an authoritative cataloging system. It
uses LCC as a practical classification spine for personal knowledge management.

### LCC Lookup Model

The `lcc/` directory contains the LCC outline files downloaded directly from
the Library of Congress. Each file covers one class letter or letter group and
is named using the pattern:

```text
lcco-<class>.md
```

Examples:

```text
lcc/
├── lcco-a.md    — General Works
├── lcco-b.md    — Philosophy, Psychology, Religion
├── lcco-q.md    — Science
├── lcco-t.md    — Technology
└── lcco-z.md    — Bibliography, Library Science
```

When assigning a classification to a new MOC or note, read the relevant
`lcco-*.md` file(s) to identify the best matching class code and label. Start
with the class letter most likely to cover the subject, then narrow down from
there.

### Classification Lookup Workflow

When creating a new note or MOC, use this flow:

```text
1.  Read the user request.
2.  Identify the main subject of the proposed note.
3.  Identify the most likely LCC class letter for the subject.
4.  Open the corresponding lcco-<class>.md file in lcc/.
5.  Read the outline to confirm the best class code and label.
6.  Select one primary classification.
7.  Select a broad filename prefix from that classification.
8.  Create the MOC page if it does not already exist.
9.  Create the note from the correct template.
10. Add frontmatter with classification, title, MOC links, tags, and status.
11. Link the note from the relevant MOC pages.
12. If more than one classification fits, record secondary classifications in
    frontmatter.
```

The lookup result should be practical, not overly formal. The goal is to place
the note where it will be found again.

### Classification Prefix Model

Notes in `notes/` use a broad LCC-style prefix in the filename as a shelf
marker. This is not a full formal call number — it is a stable, visible subject
cue.

Pattern:

```text
class-topic-specific-description.md
```

Examples:

```text
qa76-linux-systemd-timers.md
qa76-linux-selinux-container-labels.md
tk5105-dns-record-types.md
tk5105-home-network-vlans.md
z665-obsidian-moc-model.md
sb-outdoor-water-sprinklers.md
```

Use broad prefixes. Avoid full formal call numbers in filenames — they are too
noisy and too rigid for working notes. Put detailed classification in frontmatter
instead.

### Classification versus Navigation

The classification prefix does not replace MOCs. A note can have one filename
prefix but still belong to many topics.

Example: `notes/qa76-linux-selinux-container-labels.md` may belong to all of
these MOCs:

```text
Linux / Fedora / SELinux / Containers / Docker / Security / Operations / Troubleshooting
```

Use this rule:

```text
Filename prefix = broad shelf
MOC links       = navigation
Backlinks       = relationships
Frontmatter     = metadata and classification details
```

## MOC Model

MOCs are the primary navigation layer. The folder structure is intentionally
shallow — depth lives in MOC pages and links, not in nested directories.

Conceptual path:

```text
home.md
└── MOC Index
    └── Computing
        └── Linux
            ├── qa76-linux-systemd-timers.md
            └── qa76-linux-selinux-container-labels.md
```

Actual path on disk:

```text
notes/
├── qa76-linux-systemd-timers.md
└── qa76-linux-selinux-container-labels.md
```

A good MOC answers:

```text
What is this topic?
Where should I start?
What are the most important notes?
What related topics exist?
What is current?
What is incomplete?
What is deprecated?
```

MOCs are curated. They do not need to automatically list every note.

### Top-Level MOCs versus Lower-Level MOCs

`home.md` should link only to top-level MOCs and current work areas. It should
not become a complete list of every MOC in the vault. Top-level MOC listings in
`home.md` should use human-friendly display names, not raw classification codes
or implementation-oriented filenames.

A top-level MOC is a broad navigation hub that someone could use as a starting
point when entering the vault cold. It should cover a durable area of knowledge,
help route new material, and reasonably be expected to collect many notes or
child MOCs over time.

Examples:

```text
Linux
AI
Compute Infrastructure
Software Development
Personal Knowledge Management
Health
```

A lower-level MOC is a narrower topic hub that belongs under a broader MOC. It
may still be important, but it should be reached through its parent rather than
listed directly on `home.md`.

Examples:

```text
systemd / SELinux / Docker / Fedora / Kernel Memory Management / Obsidian Templates / Maps of Content
```

Decision rule:

```text
If the MOC is a broad starting point for a major knowledge area → link it from home.md.
If the MOC is a subtopic, tool, technique, project, source, or temporary study cluster → link it from its parent MOC.
```

The distinction is about navigation scope, not importance. When uncertain, do
not promote a MOC to `home.md` — link it from the nearest broader MOC instead.

### MOC Naming

MOC filenames should be lowercase slugs with no spaces. Put the human-friendly
name in frontmatter `title` and use aliases when linking from other pages. Do
not put classification codes in top-level MOC filenames unless the page is
explicitly a classification shelf.

```text
moc/linux.md
moc/compute-infrastructure.md
moc/personal-knowledge-management.md
```

Classification-prefixed MOCs are for classification shelf pages only:

```text
Classification shelf MOC:  moc/qa76-computer-software.md
Working topic MOC:         moc/linux.md
```

Both may exist and link to each other.

## Frontmatter Schema

Detailed classification metadata belongs in frontmatter, not in the filename.

Example for a note:

```yaml
title: "Linux systemd timers"
aliases:
  - "systemd timers"
  - "linux timers"
classification: QA76
classification_label: Computer software / operating systems
classification_source: lcc
classification_detail: QA76.76
classification_detail_label: Operating systems
primary_moc: Linux
related_mocs:
  - Systemd
  - Operations
  - Automation
related_classifications: []
tags:
  - linux
  - systemd
  - timers
  - automation
status: current
```

Example for a note with broader classification:

```yaml
title: "Outdoor water sprinklers"
aliases:
  - "lawn sprinklers"
  - "garden sprinklers"
classification: SB
classification_label: Plant culture
classification_detail: SB450.9-467.8
classification_detail_label: Gardens and gardening
primary_moc: SB - Plant culture
related_mocs:
  - S - Agriculture
  - TC - Hydraulic engineering
related_classifications:
  - TC801-978
tags:
  - sprinklers
  - irrigation
  - gardening
  - lawn-care
  - outdoor-water
status: current
```

Use detailed values in frontmatter only when they help retrieval. Do not force
every note to have a highly specific classification.

### Note Titling

The displayed page title is set in the frontmatter `title` field — it should
not depend on the filename. Every note should include a `title` and at least
one alias.

For MOCs, include at least one alias with the `moc` prefix so MOCs are
discoverable from the quick switcher:

```yaml
title: "Linux"
aliases:
  - "moc linux"
  - "linux moc"
```

## New Note Creation Workflow

When creating a new note:

```text
1. Decide whether the request needs a note, a MOC, a runbook, a reference, or
   a journal entry.
2. If it is a note or MOC, perform LCC classification lookup.
3. Choose a broad classification prefix.
4. Create or update the relevant MOC using templates/moc-note-template.md —
   copy it, rename it, and fill it in.
5. Create the note using templates/note-template.md — copy it, rename it, and
   fill it in.
6. Add frontmatter.
7. Link the note from all relevant MOCs.
8. Add related links at the bottom of the note.
```

Preferred note filename:

```text
notes/class-topic-specific-description.md
```

Preferred MOC filename:

```text
moc/topic-name.md
```

Or, for classification shelf pages:

```text
moc/class-classification-label.md
```

## AI Navigation Rules

When working with this vault, AI tools should:

```text
1.  Start with home.md for broad questions.
2.  Use MOC pages for context before reading individual notes.
3.  Treat notes/ as source material, not the primary navigation system.
4.  Use links and backlinks to understand relationships.
5.  Treat classification prefixes as broad subject hints, not absolute truth.
6.  Consult lcc/ for classification lookup when creating new notes or MOCs.
7.  Prefer lcc/lcc-local-classification-map.md if it exists.
8.  Use converted LCC schedule Markdown files in lcc/ when the local map is
    insufficient.
9.  Treat archive/ as inactive unless historical information is requested.
10. Prefer notes marked status: current when conflicts exist.
11. Never assume a note belongs to only one topic.
```

## How It Works

Content enters the pipeline through one or more ingest points described in
`ingest-points/`. Each ingest point document defines a content source (email,
RSS, bookmarks, saved files) and how it is accessed.

Before processing, ingest files are filtered against `interests.md` — a
personal document created by the human with AI assistance that defines active
areas of interest. Files that do not match any interest are discarded. Files
that match are passed to an AI processing step.

The AI distills matched content down to actionable criteria only:

- Essential new knowledge
- Skills to learn
- Tools to evaluate
- Processes to consider for adoption

The distilled output is written to the `obsidian/` directory as Obsidian-ready
Markdown knowledge pages, ready to be dropped into the live vault.

## Design Principles

```text
Keep folders shallow.
Use MOCs for structure.
Use links for relationships.
Use LCC lookup for classification routing.
Use broad classification prefixes as shelf markers.
Do not use full formal call numbers in filenames.
Keep filenames unique and descriptive.
Do not force every note into only one category.
Use frontmatter for detailed metadata.
Use local lcc/ files for AI-assisted classification.
Treat archive/ as inactive unless historical context is needed.
Make the structure understandable to both humans and AI.
```

The result should feel like a personal library with a good index, not a maze
of folders.

## Related Documentation

- [RUNBOOK.md](RUNBOOK.md)
- [ingest-points/README.md](ingest-points/README.md)
- [PersonalKnowledgeVault](https://git.kevininscoe.com/kinscoe/PersonalKnowledgeVault) — distilled
  content from `obsidian/` may be promoted into this vault

## License

This repository uses a dual license. The applicable license depends on the file
type and purpose.

**Code and automation** — shell scripts, Python, Go, install scripts, config
generators, and other executable or machine-oriented source files — is licensed
under the [Apache License, Version 2.0](LICENSE-APACHE-2.0).

**Documentation, notes, and vault templates** — README.md, RUNBOOK.md,
AGENTS.md, `docs/`, `notes/`, vault templates, Markdown workflow explanations,
diagrams, and other written content — is licensed under the
[Creative Commons Attribution 4.0 International License](LICENSE-CC-BY-4.0).

Copyright (c) 2026 Kevin P. Inscoe
