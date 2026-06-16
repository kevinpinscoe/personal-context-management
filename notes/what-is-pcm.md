---
title: "PKM vs PCM"
source: "https://chatgpt.com/c/6a2d411a-6740-83ea-9ac9-83275cec7512"
author:
published:
created: 2026-06-13
description: "ChatGPT conversation with 4 messages"
tags:
  - "clippings"
---
<audio autoplay="" playsinline=""></audio>

[Skip to content](#main)

[

New chat](/)

![Profile image](https://cdn.auth0.com/avatars/ki.png)

## Chat history

[ChatGPT](/)

- [
	New chat
	CtrlShiftO
	](/)
-

[

Library

](/library)[

Apps

](/apps)

More

- [
	Clipboard Management for Tahoe
	](/c/69f3b070-0dec-83ea-82b2-bc5be773e9f0)

- kitty term emulator
- Work
- Fedora linux
- Obsidian
- raspberry-pi
-

[

](/)

- [
	PKM vs PCM
	](/c/6a2d411a-6740-83ea-9ac9-83275cec7512)
- [
	Clear Cache for Site
	](/c/6a2bf7f2-4d88-83ea-8ef1-b52b689b74f3)
- [
	GMRS License Application Guide
	](/c/6a2c9fcf-0250-83ea-acc0-7f076f38cf5b)
- [
	Package Management Systems
	](/c/6a2d13fa-9284-83ea-abd6-4a0e9177cc2c)
- [
	Sunfire X4450 Fedora Compatibility
	](/c/6a2c9a7a-199c-83ea-8f57-c71ca3870099)
- [
	Nebra HNT Indoor Miner Use
	](/c/6a2c9126-20dc-83ea-81d5-cff1c7c287ed)
- [
	Ham Radio Equipment Identification
	](/c/6a2c904e-6088-83ea-b0a5-27f943b9a137)
- [
	Hardwiring TecNec FSL-1
	](/c/6a2c842c-b8f0-83ea-976e-caee11ee32d4)
- [
	Box contents clarification
	](/c/6a2c522f-2a44-83ea-8957-5d15c0fa1c7a)
- [
	OpenBao Unseal and 1PW
	](/c/6a2c09ed-5ac4-83ea-b321-eeb854bc165d)
- [
	Reword GitHub About Section
	](/c/6a2c32ee-9eb4-83ea-ab2e-79b8f5588b0a)
- [
	CHIRP source and alternatives
	](/c/6a2c2fee-1338-83ea-8ae7-9593a47de93f)
- [
	Matomo website config change
	](/c/6a2be09d-b058-83ea-80c9-867473c53a6e)
- [
	Datagiggle Drawing Request
	](/c/6a2b10d5-4d40-83ea-8f0a-5e2d8b06bffb)
- [
	Trouble Ticket Rewording
	](/c/6a2adca7-b118-83ea-9da6-bc2dfb05ae25)
- [
	Master of Tools Design
	](/c/6a2ad52c-2754-83ea-96a7-5921a59e1c8f)
- [
	Epic vs Epoch in Sprint
	](/c/6a2ac47b-6d94-83ea-b8c1-ac2667b4539d)
- [
	Disable Voicemail Notifications
	](/c/6a2abbbd-d834-83ea-9956-9e814ef39096)
- [
	Firefox RSS Feed Issue
	](/c/6a2aad29-87f4-83ea-b80c-06fe26c656a4)
- [
	Hacker News RSS Feeds
	](/c/6a2aabc2-2184-83ea-9e31-b7dd22c6f1ba)
- [
	Husky vs Mise
	](/c/6a2a985a-732c-83ea-9cad-fcdd17cbf9eb)
- [
	Fish vs Zsh Comparison
	](/c/6a2a943b-f134-83ea-9808-0a5526851be4)
- [
	ComfyUI Use Case
	](/c/6a29e4ab-9fc0-83ea-8d36-da9aa4df3db0)
- [
	iPhone Voicemail Spam Fix
	](/c/6a29c307-86ec-83ea-92b7-decb7562e1cb)
- [
	Open-source AWS SSM Alternatives
	](/c/6a29817b-921c-83ea-bd2b-e5d8ace0b41e)
- [
	Amazon Corretto Overview
	](/c/6a297f0b-fcd4-83ea-a033-5cc3ff02da66)
- [
	DMARC Report Explanation
	](/c/6a29698c-a074-83ea-84c4-2c1103489f4f)
- [
	GitHub Repo Description Help
	](/c/6a295311-60cc-83ea-91b6-b4fa682680f8)

![Profile image](https://cdn.auth0.com/avatars/ki.png)

Kevin Inscoe

Plus

#### You said:

what is personal context management vs personal knowledge management

  

#### ChatGPT said:

**Personal knowledge management (PKM)** is about managing what you know.

**Personal context management (PCM)** is about managing what matters right now so tools, people, and AI can act with the right background.

Think of it this way:

| Concept | Main question | Examples |
| --- | --- | --- |
| **Personal Knowledge Management** | “What do I know, and how do I keep it useful?” | Notes, research, bookmarks, project docs, how-to guides, troubleshooting notes, decisions, references |
| **Personal Context Management** | “What should be known about me, this situation, this project, or this task right now?” | Preferences, current goals, constraints, active projects, recent decisions, environment details, working assumptions |

PKM is usually a **library**.

PCM is more like a **working memory / operating context**.

For example, in your case:

```
PKM:- Notes about Fedora 42- OpenBao setup guide- Matomo API documentation- Ham radio licensing notes- Kubernetes runbooks- GitOps architecture notesPCM:- I prefer GitOps over click-ops- I use Fedora KDE and macOS- I prefer VS Code/vim, not nano- I am currently working on OpenBao auto-unseal- This repo should use app/librewolf, not browser-config/librewolf- I need answers that account for ADHD and visual scanning
```

A practical distinction:

**PKM stores durable knowledge.**  
It answers: “What information might I need again?”

**PCM stores active operating assumptions.**  
It answers: “What should the system already know before helping me?”

In AI workflows, this distinction matters a lot.

A PKM system might be Obsidian, MediaWiki, Markdown files, Git repos, PDFs, bookmarks, and runbooks.

A PCM system might be a `me.md`, `project-context.md`, `CLAUDE.md`, `AGENTS.md`, Codex instructions, ChatGPT memory, repo-specific conventions, current sprint notes, active constraints, and environment facts.

A simple rule:

```
If it teaches you something, it belongs in PKM.If it changes how assistance should behave, it belongs in PCM.
```

Examples:

```
PKM note:"How DKIM, SPF, and DMARC work."PCM note:"For getunclutter.com, email is currently handled through Improvmx and Gmail forwarding."
```
```
PKM note:"How to configure LibreWolf policies.json."PCM note:"For my LibreWolf repo, the root path must be app/librewolf."
```
```
PKM note:"OpenBao auto-unseal options."PCM note:"I am currently evaluating IAM Roles Anywhere instead of long-lived AWS keys."
```

A good personal system usually needs both:

```
Personal Knowledge Management        ↓Long-term notes, docs, referencesPersonal Context Management        ↓Current state, preferences, constraints, decisionsAI / automation / future you        ↓Better answers with less re-explaining
```

For your style of work, I would describe the split like this:

```
PKM = my knowledge basePCM = my operating context
```

A good repo layout could reflect that:

```
personal-system/├── knowledge/│   ├── linux/│   ├── aws/│   ├── kubernetes/│   ├── ham-radio/│   └── notes/├── context/│   ├── me.md│   ├── current-projects.md│   ├── preferences.md│   ├── environments.md│   └── active-decisions.md└── runbooks/    ├── backup-restore.md    ├── openbao.md    └── librewolf.md
```

Bottom line:

**Personal knowledge management is about remembering information. Personal context management is about making that information actionable in the current situation.**

  

#### You said:

I am creating a github repo for this reword this for an about statement: "My workflow to create a PCM. Managing what matters right now so tools, people, and AI can act with the right background.

  

#### ChatGPT said:

Use this:

**A personal context management workflow for capturing what matters now, so tools, people, and AI can work with the right background.**

Slightly shorter GitHub About version:

**Personal context management workflow for keeping tools, people, and AI aligned with the right background.**

More explicit version:

**My workflow for building a personal context management system that captures current goals, constraints, preferences, and decisions for better human and AI-assisted work.**

Do you like this personality?

  

ChatGPT can make mistakes. Check important info.

<audio class="fixed start-0 bottom-0 hidden h-0 w-0" autoplay="" crossorigin="anonymous"></audio>

<iframe height="1" width="1" style="position: absolute; top: 0px; left: 0px; border: medium; visibility: hidden;"></iframe>

1Password menu is available. Press down arrow to select.

<iframe style="display: none;" src="https://chatgpt.com/backend-api/sentinel/frame.html?sv=20260423af3c"></iframe>
