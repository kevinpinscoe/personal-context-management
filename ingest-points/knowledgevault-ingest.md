# Ingest Point: KnowledgeVault Manual Ingest

## Summary

Manually curated files saved to a topic-organized directory tree under `~/KnowledgeVault/personal-knowledge-base/ingest/`. Content is dropped here by hand — web article clippers, screenshots, downloads, and typed notes. There is no automation and no tracking database; the PCM pipeline must manage its own record of what has been processed.

## Location

```
~/KnowledgeVault/personal-knowledge-base/ingest/
```

Excludes `emails/` — that subdirectory is covered by `email-incoming.md` and `email-notes.md`.

## Directory Layout and Topic Taxonomy

The path encodes the topic and subtopic and should be used directly as Obsidian tags:

```
ingest/
├── ai/
│   ├── agentic/
│   ├── ai-prompt-voice/
│   ├── chatgpt/
│   ├── claude/
│   ├── devex-in-the-age-of-ai/     # deeper research project with AI summaries
│   └── examples/
├── creating-and-design/
├── infrastructure/
│   ├── containers/
│   ├── home-enterprise-lab-cloud-environment/
│   ├── hosting/
│   ├── k8s/
│   ├── proxmox/
│   └── virtual-machines/
├── mindmaps/
├── personal/
│   ├── habits/
│   │   ├── reading/
│   │   └── writing/
│   └── rationality-and-behavior/
├── software-development/
├── software-product-launch/
├── software-tools/
├── speaking-and-communicating/      # includes MP4 + transcript scripts
└── writing-prompts/
```

## File Types

| Extension | Count | Role | PCM action |
|---|---|---|---|
| `.md` | 33 | Primary content — notes, articles, transcripts, AI summaries | Process |
| `.html` | 7 | Sidecar to `article.md` — original HTML snapshot | Skip (use `article.md`) |
| `.jpg` / `.png` / `.gif` / `.jpeg` | 17 | Screenshots, diagrams, LinkedIn posts | Skip or flag for manual review |
| `.pdf` | 1 | Saved document | Extract text (e.g. `pdftotext`) before processing |
| `.mp4` | 1 | Video file (Harvard speaking course) | Skip; use accompanying `.md` transcript |
| `.py` / `.sh` | 4 | Download/transcription helper scripts | Skip |
| `.bak` / `.gitignore` / `.codex` | misc | Operational artifacts | Skip |

## Content Patterns

### Web articles (clipper-saved)

Saved as a pair inside a slug-named subdirectory:

```
<topic>/<article-slug>/
├── article.md    ← preferred input — Pandoc-converted Markdown
└── index.html    ← original snapshot — skip unless article.md is unusable
```

**Quality warning:** `article.md` quality depends on the source page. Pages with heavy JavaScript rendering (X/Twitter, SPA frontends) produce HTML-in-Markdown artifacts. Check the first 10 lines — if they contain CSS class names or `:::` fenced divs, fall back to `index.html` or skip.

### Standalone Markdown files

Direct `.md` files not inside a slug subdirectory — manually typed notes, AI-generated summaries, video transcripts. These are generally clean and ready to process without preprocessing.

### Images

Standalone images are typically screenshots of LinkedIn posts, diagrams, or infographics. They have no accompanying text file. Skip during automated pipeline runs; flag for separate manual review.

## Tag Derivation

Convert the directory path relative to `ingest/` into Obsidian tags by replacing `/` with `/`:

```
ingest/ai/claude/lessons-from-building-claude-code.../article.md
→ tags: [ingest/manual, ai, ai/claude]

ingest/infrastructure/proxmox/5-proxmox-fixes.md
→ tags: [ingest/manual, infrastructure, infrastructure/proxmox]
```

## Processing / Tracking

There is no SQLite database. The pipeline must track processed items externally. Recommended approach (to be decided):

- **Option A — delete after processing:** remove the source file (and its `index.html` sidecar) once the Obsidian note is written. Simple; the absence of the file is the record.
- **Option B — move to `processed/` subtree:** mirror the topic hierarchy under a `processed/` sibling directory. Preserves originals; directory walk excludes `processed/`.
- **Option C — manifest file:** append processed file paths to a `.processed-manifest` file at the ingest root. Allows re-runs to skip already-processed items without moving files.

Decision to be made before first pipeline run.

## Preprocessing Notes

- Strip the `article.md` artifact check (CSS class names in first 10 lines → fall back or skip).
- For PDFs: run `pdftotext <file>.pdf -` and pass the text output to the AI agent.
- Ignore `.obsidian.old/`, `.claude/`, `.codex`, `.gitignore`, and `*.bak` files during directory walk.
- The `devex-in-the-age-of-ai/` subdirectory contains pre-generated AI summaries (Claude and ChatGPT variants) — these may be ingested directly rather than re-summarized.

## Example Transformation Output (Obsidian note)

```markdown
---
source: knowledgevault-manual
date: 2026-06-13
origin-path: infrastructure/proxmox/5-proxmox-fixes.md
tags: [ingest/manual, infrastructure, infrastructure/proxmox]
---

# 5 Proxmox Fixes

> Key excerpt or summary here.

---
*Manually saved to KnowledgeVault ingest on 2026-06-13*
```
