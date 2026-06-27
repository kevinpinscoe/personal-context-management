# RUNBOOK.md — personal-context-management

## Metadata

| Field | Value |
|---|---|
| **Owner** | Kevin P. Inscoe |
| **Last Updated** | 2026-06-27 |
| **Last Tested** | 2026-06-13 |
| **Expected Duration** | 5–30 minutes depending on task |
| **Risk Level** | Low |
| **Repo** | https://github.com/kevinpinscoe/personal-context-management |

---

## Purpose

Operational reference for working in this repository. Covers adding vault
templates, maintaining workflow docs, running scripts, and keeping the repo
healthy.

---

## When to Use This Runbook

- **Use when:** Adding vault template files, writing workflow docs, adding or
  testing scripts, or returning to this repo after a gap.
- **Do NOT use when:** Working directly inside a live Obsidian vault — that is a
  separate system. This repo designs and documents the PCM structure; the vault
  is where it runs.

---

## Prerequisites

- [ ] `git` installed and SSH key configured for `github.com`
- [ ] Text editor installed (Vim recommended)
- [ ] Obsidian installed (optional — needed only when testing `vault/` template
  files against a real vault)
- [ ] If `mise.toml` is present in the repo: run `mise install && mise doctor`
  before proceeding

---

## Stack

| Component | Details |
|---|---|
| **Language / Runtime** | Bash, Python, Go (scripts only; no runtime required for docs) |
| **External Services** | GitHub (remote hosting) |
| **Databases / File Stores** | None |
| **Credentials / Secrets** | None required for core repo work |

---

## Step-by-Step Procedure

### Step 0 — Check rules before creating files

Before creating or moving any file, review the rules in `rules/`:

- `rules/file-naming-rules.md` — names must be lowercase, hyphen-separated, no spaces
- `rules/rules-directory-layout.md` — content must land in the correct functional directory
- `rules/moc-section-order.md` — MOC files must follow Overview → Child MOCs → Notes → Related MOCs

If unsure which directory a file belongs in, check the placement rules table in
`rules/rules-directory-layout.md`.

---

### Step 1 — Add a vault template file

**Why:** Vault templates define the structure and frontmatter for PCM files used
in Obsidian.

```bash
vim vault/<filename>.md
```

**Expected output:** A new Markdown file in `vault/`.

**If this fails:** Confirm you are in the correct repo directory:
```bash
git remote get-url origin
```

---

### Step 2 — Add a workflow doc

**Why:** Workflow docs describe how to build or use the PCM system.

```bash
vim docs/<workflow-name>.md
```

---

### Step 3 — Add or update a script

**Why:** Scripts automate vault setup, config generation, or install tasks.
Scripts live in `scripts/` and are covered by the Apache-2.0 license.

```bash
vim scripts/<script-name>.sh
chmod +x scripts/<script-name>.sh

# Test before committing
bash -n scripts/<script-name>.sh   # syntax check
bash scripts/<script-name>.sh      # dry run if the script supports it
```

---

### Step 4 — Commit and push changes

```bash
git add <files>
git commit -m "<type>: <short description>"
git push
```

**Commit type examples:** `docs:`, `feat:`, `fix:`, `chore:`

**Expected output:** Changes visible on GitHub at
https://github.com/kevinpinscoe/personal-context-management

---

## Verification

```bash
git status          # must be clean
git log --oneline -5
```

**Success criteria:** Working tree clean, latest commit visible on GitHub.

---

## Rollback Procedure

1. Identify the commit to revert: `git log --oneline`
2. Revert cleanly: `git revert <commit-hash>`
3. Push the revert: `git push`

Use `git revert` (not `git reset`) to preserve history.

---

## Escalation

| Condition | Contact | How |
|---|---|---|
| Accidental force push or lost commit | Kevin P. Inscoe | Self — check GitHub commit history via web UI |

---

## Troubleshooting

| Symptom | Likely Cause | Resolution |
|---|---|---|
| Commit rejected (signing error) | SSH signing key not configured | Run `git config --global gpg.format ssh` and follow `~/Projects/private/gitops/signing-plan.md` |
| Push rejected | Stale local branch | Run `git pull --rebase origin main` then push |
| `.claude` appears in `git status` | `.gitignore` not applied | Confirm `**/.claude` is in `.gitignore`; run `git rm --cached .claude -r` if it was staged |
| Script not executable | Missing execute bit | Run `chmod +x scripts/<name>.sh` |

---

## Logs

```bash
# Recent commits
git log --oneline -10

# Show what changed in last commit
git show --stat

# Show full diff of last commit
git show
```

---

## Maintenance Notes

- **Last game-day test:** 2026-06-13
- **Next scheduled review:** As needed
- **Known drift risks:** Vault template structure may diverge from the live
  Obsidian vault over time if templates are not kept in sync with actual vault
  usage
