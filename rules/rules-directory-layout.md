# Required Repository Directory Layout

This rule defines the minimum directory layout for this knowledge base.

When scaffolding or repairing the repository, create every required directory and every required file listed below. Example topic files are shown only to explain where content belongs; do not create example files unless they are specifically needed.

## Required Files

- `home.md`

## Required Directories

- `moc/`
- `notes/`
- `runbooks/`
- `references/`
- `lcc/`
- `journal/`
- `attachments/`
- `templates/`
- `archive/`
- `docs/`
- `scripts/`
- `rules/`

## PCM-Specific Directories

These directories are required in this repo (personal-context-management-private) and do not exist in the source knowledge base vault:

- `obsidian/` — AI-distilled output mirroring PersonalKnowledgeVault categories; subdirectories mirror ingest category names
- `ingest-points/` — ingest pipeline configuration files; driven by `interests.yaml`
- `ingest-holding/` — temporary holding area for ingest candidates before classification

## Empty Directory Convention

When a required directory is empty, place a `.gitkeep` file inside it so git tracks the directory. Remove the `.gitkeep` once real content is added.

## Required Templates

Create these files inside `templates/`:

- `moc-note-template.md`
- `note-template.md`
- `runbook-template.md`
- `reference-note-template.md`
- `daily-note-template.md`
- `default-note-template.md`

## Optional Directories

These directories are not required but are recognized and governed by this rule if present:

- `uncategorized/` — temporary holding area for notes that arrived without a clear home. Triage regularly; notes here should either be promoted, linked, classified, archived, or deleted.

## Example Layout

The following tree shows the expected organization. Files marked as examples are illustrative only and are not required.

```text
.
├── home.md
├── moc/
│   └── linux.md                             # example
├── notes/
│   └── qa76-linux-kernel.md                 # example
├── runbooks/
│   └── check-loaded-kernel-modules.md       # example
├── references/
│   └── linux-kernel-documentation.md        # example
├── lcc/
│   ├── lcco-q.md                            # example — Science class outline from LoC
│   └── lcco-t.md                            # example — Technology class outline from LoC
├── journal/
│   └── 2026-06-15.md                        # example
├── attachments/
│   └── linux-kernel-boot-flow.png           # example
├── templates/
│   ├── moc-note-template.md
│   ├── note-template.md
│   ├── runbook-template.md
│   ├── reference-note-template.md
│   ├── daily-note-template.md
│   └── default-note-template.md
├── archive/
│   └── old-linux-kernel-index.md            # example
├── docs/
│   └── vault-design-reference.md            # example
├── scripts/
│   └── download-lcc-outline.sh              # example
├── rules/
│   └── rules-directory-layout.md
├── obsidian/                                # PCM-specific
│   └── ai/                                  # example category
├── ingest-points/                           # PCM-specific
│   └── rss-feeds.md                         # example
├── ingest-holding/                          # PCM-specific
└── uncategorized/                           # optional
```

## Placement Rules

- Put map-of-content notes in `moc/`.
- Put evergreen notes in `notes/` using a broad lowercase LCC-style prefix in the filename when useful (e.g. `qa76-linux-systemd-timers.md`). Group by topic subdirectory only when volume warrants it.
- Put step-by-step operational procedures in `runbooks/`.
- Put source summaries, documentation links, and external research notes in `references/`.
- Put LCC outline files downloaded from the Library of Congress in `lcc/`. When classifying a new note or MOC, read the relevant `lcco-<class>.md` file to identify the correct class code and label.
- Put dated daily notes in `journal/` using `YYYY-MM-DD.md`.
- Put images, PDFs, and other supporting files in `attachments/`.
- Put reusable note templates in `templates/`.
- Put retired or superseded content in `archive/`.
- Put reference material used when researching and shaping vault structure in `docs/`. Track and push all files not excluded by `.gitignore`.
- Put utility scripts for ingesting articles or modifying vault content in `scripts/`.
- Put vault ground rules in `rules/`. If a requested change conflicts with a rule, prefer the rule or explicitly document the exception.
- If `uncategorized/` exists, triage it regularly — promote, classify, archive, or delete notes; do not leave them there indefinitely.
- Put AI-distilled output in `obsidian/` under the appropriate category subdirectory.
- Put ingest pipeline configuration in `ingest-points/`, driven by `interests.yaml`.
- Stage ingest candidates in `ingest-holding/` before classification and promotion.
