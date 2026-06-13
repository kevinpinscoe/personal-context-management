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

## Possible Vault Components

The exact structure may evolve, but a PCM vault can include files such as:

- `me.md`: identity, preferences, working style, and durable personal context
- `current-projects.md`: active projects and open loops
- `preferences.md`: tool, writing, communication, and workflow preferences
- `active-decisions.md`: recent decisions and the reasons behind them
- `task-board.md`: current priorities, waiting items, and completed work
- `daily-notes/`: daily context, handoffs, and session summaries
- `people/`: notes about collaborators, contacts, and relationship context
- `environments.md`: machines, operating systems, tools, and constraints

## Source Notes

The initial thinking for this repo comes from the two Markdown files currently in
this directory:

- `what-is-pcm.md`
- `pkm-is-dead-long-live-pcm-obsidian-is-different-now.md`

Together, they define the repo's direction: move beyond maintaining a personal
knowledge library and build a practical operating layer for Obsidian, AI tools,
and day-to-day work.
