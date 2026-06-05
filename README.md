# Automation Builder

A Claude skill that **builds you a custom skill to automate a task in your business.**

You describe something you do by hand. Automation Builder interviews you about how you do it
today, checks what's *actually* possible to automate right now (live research, not stale
guesses), designs the automation with your approval, then **builds and tests a custom skill**
you can run again and again. It assumes you're smart but not a coder the whole way through.

Built by [Edge AI](https://joinedgeai.com).

---

## Install

### Claude Code
Paste this to Claude Code:

> Install the automation-builder skill: clone `https://github.com/amart-builder/automation-builder.git` into `~/.claude/skills/automation-builder`, then confirm `~/.claude/skills/automation-builder/SKILL.md` exists. If anything fails, explain what to do in plain language.

Then start a new session and type `/automation-builder`.

To update later, paste: *"Update my automation-builder skill — pull the latest from its GitHub repo."*

### Claude desktop app / Cowork / claude.ai
1. Download **[automation-builder.zip](https://github.com/amart-builder/automation-builder/releases/latest/download/automation-builder.zip)**.
2. Open **Settings → Skills** (under Capabilities).
3. Click **+** and upload the zip.
4. Start a new chat and type `/automation-builder`.

Requires a Claude Pro, Max, or Team plan with code execution enabled.

---

## What's inside
- `SKILL.md` — the skill itself.
- `reference/generated-skill-template.md` — the template it uses for the skills it builds.
