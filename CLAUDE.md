# CLAUDE.md — personal-context-management

Guidance for Claude Code when working in this repository.

## Rules enforcement

Rules in `rules/` are ground documents for this knowledge base. **They are mandatory unless the human explicitly overrides a specific rule in the current session.**

| Rule file | What it governs |
|---|---|
| `rules/file-naming-rules.md` | File and directory naming conventions |
| `rules/rules-directory-layout.md` | Required directory structure and file placement |
| `rules/moc-section-order.md` | Required section order within every MOC file |

### How to apply the rules

- Before creating or moving any file, check `rules/file-naming-rules.md`. Names must be lowercase, hyphen-separated, no spaces. Exceptions: `README.md`, `AGENTS.md`, `RUNBOOK.md`.
- Before adding or restructuring directories, check `rules/rules-directory-layout.md`. Content must land in the correct functional directory.
- Before creating or editing any MOC file, check `rules/moc-section-order.md`. Sections must appear in the order: Overview → Child MOCs → Notes → Related MOCs. Child MOCs must precede Notes.
- If a request would violate a rule in `rules/`, **stop and challenge the request before making any change.** State which rule would be violated and ask the human to confirm or override before proceeding.

### Challenging a rule violation

When the human asks for something that would break a rule, respond like this:

> This would violate `rules/<rule-file>.md`: [quote the relevant rule].
> Do you want to override this rule for this change? If yes, I will proceed. If no, I can suggest an alternative.

The human may override any rule. The challenge is mandatory; silent compliance is not acceptable.

## Directory layout (summary)

See `rules/rules-directory-layout.md` for the authoritative layout. Short form:

| Directory | Required | Purpose |
|---|---|---|
| `moc/` | Yes | Maps of content |
| `notes/` | Yes | Evergreen notes |
| `runbooks/` | Yes | Step-by-step operational procedures |
| `references/` | Yes | Source summaries and external research |
| `lcc/` | Yes | Library of Congress Classification outlines |
| `journal/` | Yes | Dated daily notes (`YYYY-MM-DD.md`) |
| `attachments/` | Yes | Images, PDFs, and other supporting files |
| `templates/` | Yes | Reusable note templates |
| `archive/` | Yes | Retired or superseded content |
| `docs/` | Yes | Human-shaped supplementary documentation |
| `scripts/` | Yes | Utility scripts for ingest and vault management |
| `rules/` | Yes | Ground rules — do not delete or move |
| `obsidian/` | Yes (PCM) | AI-distilled output mirroring PersonalKnowledgeVault categories |
| `ingest-points/` | Yes (PCM) | Ingest pipeline configuration driven by `interests.yaml` |
| `ingest-holding/` | Yes (PCM) | Temporary staging for ingest candidates |
| `uncategorized/` | Optional | Notes without a clear home — triage regularly |

## docs/ tracking rule

`docs/` is human-shaped — AI and scripts should not write here. If it exists:

- All files not excluded by `.gitignore` must be staged, committed, and pushed to origin.
- Do not leave `docs/` files untracked. If you find untracked files there, report them and stage them.
- Check for untracked files in `docs/` with: `git ls-files --others --exclude-standard docs/`

## Related documentation

- `README.md` — repository overview and workflow
- `RUNBOOK.md` — operational reference
- `rules/` — knowledge base ground rules
