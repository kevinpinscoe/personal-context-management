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
