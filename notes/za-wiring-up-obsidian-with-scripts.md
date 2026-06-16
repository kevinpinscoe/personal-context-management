---
title: "Wiring up Obsidian with scripts"
aliases:
  - "obsidian shell commands"
  - "wire obsidian to vault scripts"
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
  - obsidian
  - scripts
  - workflow
created: 2026-06-15
updated: 2026-06-15
---

# Wiring up Obsidian with scripts

Recommended setup: use the Obsidian **Shell commands** community plugin.

The plugin can run system commands from Obsidian's command palette or hotkeys. Use only trusted commands because these scripts can create and modify vault files.

## Important detail

`new-note.sh` and `new-moc.sh` are interactive scripts. They use terminal prompts, so they should be launched in a terminal window rather than run silently in the background.

## Linux examples

For GNOME Terminal:

```bash
gnome-terminal --working-directory=/path/to/your/vault -- bash -lc './scripts/new-note.sh; echo; read -rp "Press Enter to close..."'
```

```bash
gnome-terminal --working-directory=/path/to/your/vault -- bash -lc './scripts/new-moc.sh; echo; read -rp "Press Enter to close..."'
```

For KDE Konsole:

```bash
konsole --workdir /path/to/your/vault -e bash -lc './scripts/new-note.sh; echo; read -rp "Press Enter to close..."'
```

## Obsidian setup

1. Install the community plugin `Shell commands`.
2. Enable it.
3. Open Shell Commands settings.
4. Add a command named `Vault: New classified note`.
5. Paste the terminal command that runs `scripts/new-note.sh`.
6. Add a command named `Vault: New MOC`.
7. Paste the terminal command that runs `scripts/new-moc.sh`.
8. Open `Settings > Hotkeys`.
9. Search for the shell command names.
10. Bind `Ctrl+N` to `Vault: New classified note`.
11. Bind `Ctrl+M` to `Vault: New MOC`.

If `Ctrl+N` is already assigned to Obsidian's built-in new note command, remove or change that binding first.

## Noninteractive scripts

Noninteractive scripts can be wired directly as command-palette actions:

```bash
/path/to/your/vault/scripts/check-vault.sh
```

Examples:

- `scripts/check-vault.sh`
- `scripts/find-classification.sh`
- `scripts/list-unlinked-notes.sh`
- `scripts/triage-uncategorized.sh`

Keep `new-note.sh` and `new-moc.sh` terminal-based unless they are later rewritten to accept command-line arguments or use GUI prompts.
