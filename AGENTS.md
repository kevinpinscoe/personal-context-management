# Repository Guidelines

## Project Structure & Module Organization

This repository documents and prototypes a Personal Context Management system for
Obsidian. Top-level docs explain the intent and operating process:

- `README.md`: project overview and core concepts.
- `RUNBOOK.md`: operational workflow for adding docs, templates, and scripts.
- `notes/`: source essays and thinking that inform the project direction.
- `docs/`: workflow documentation. Currently a placeholder directory.
- `vault/`: Obsidian vault template files. Currently a placeholder directory.
- `scripts/`: automation for setup, generation, or maintenance. Currently a
  placeholder directory.

Keep live Obsidian vault content out of this repo unless it is a reusable
template or documented workflow.

## Build, Test, and Development Commands

There is no application build step. Most work is Markdown editing.

- `mise install && mise doctor`: prepare optional tool versions if `mise.toml`
  is activated.
- `bash -n scripts/<script-name>.sh`: syntax-check a shell script.
- `bash scripts/<script-name>.sh`: run or dry-run a script when supported.
- `git status`: confirm the working tree before and after changes.

## Coding Style & Naming Conventions

Write Markdown with clear headings, short sections, and concrete examples. Use
kebab-case file names for docs and notes, such as `docs/context-refresh.md`.
Prefer fenced code blocks for commands. For shell scripts, use `#!/bin/bash`,
make executable scripts with `chmod +x`, and keep behavior explicit and
idempotent where possible.

## Testing Guidelines

No formal test framework is configured. Validate documentation changes by
reading rendered Markdown and checking links or paths mentioned in the text.
Validate scripts with `bash -n` before running them. If a script mutates files,
include a dry-run mode or document expected outputs in `RUNBOOK.md`.

## Commit & Pull Request Guidelines

This repository currently has no committed Git history to infer conventions
from. Follow the runbook convention:

- `docs: add vault template workflow`
- `feat: add vault setup script`
- `fix: correct runbook command`
- `chore: update placeholders`

Pull requests should include a short summary, changed paths, verification steps,
and screenshots only when documenting visual Obsidian behavior. Link related
issues or decisions when available.

## Security & Configuration Tips

Do not commit secrets, private vault data, personal credentials, or machine-local
paths. Treat `vault/` as templates only. Keep `.claude`, `.codex`, and other
agent-local state untracked unless explicitly documenting reusable behavior.
