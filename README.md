# claude-skills

> Personal Claude Code skill library — Vasu Bhatt  
> These skills extend Claude Code's behaviour via the `/` slash command system.

---

## What are Claude Code Skills?

Skills are folders inside `~/.claude/skills/` (Mac/Linux) or `C:\Users\vasue\.claude\skills\` (Windows). Each folder contains a `SKILL.md` file that instructs Claude how to behave for a specific task. They appear instantly in Claude Code's slash command list.

---

## Skills in this repo

### `obsidian-planet`
Full Obsidian vault intelligence — understands vault structure, links notes, suggests placement, and formats outputs as native Obsidian markdown with proper frontmatter, tags, and wikilinks.

### `obsidian-inbox`
Processes raw captures from the Obsidian inbox — classifies, titles, tags, and routes notes to the correct folder in the vault structure.

### `obsidian-chat`
Formats any Claude response as a ready-to-paste Obsidian note inside a markdown codeblock. Trigger with "obsidian-chat", "capture this", or "save to obsidian."

### `obsidian-process`
End-to-end processing pipeline — takes unstructured thinking, voice notes, or raw text and converts it into clean, linked, tagged Obsidian notes ready for the vault.

---

## Installation

### On a new Mac/Linux device
```bash
mkdir -p ~/.claude/skills
cd ~/.claude/skills
git clone https://github.com/YOUR_USERNAME/claude-skills.git .
```

### On a new Windows device
```bash
mkdir C:\Users\%USERNAME%\.claude\skills
cd C:\Users\%USERNAME%\.claude\skills
git clone https://github.com/YOUR_USERNAME/claude-skills.git .
```

Verify by opening Claude Code — all skills appear in the `/` slash command list immediately.

---

## Updating skills

After editing any `SKILL.md` on any device:

```bash
git add .
git commit -m "update: skill-name — what changed"
git push
```

On other devices:
```bash
git pull
```

---

## Adding a new skill

```bash
mkdir ~/.claude/skills/new-skill-name
touch ~/.claude/skills/new-skill-name/SKILL.md
# edit SKILL.md, then:
git add .
git commit -m "new: new-skill-name"
git push
```

---

## Folder structure

```
claude-skills/
├── obsidian-planet/
│   └── SKILL.md
├── obsidian-inbox/
│   └── SKILL.md
├── obsidian-chat/
│   └── SKILL.md
├── obsidian-process/
│   └── SKILL.md
└── README.md
```

---

*Part of the Bindu Rekha Group systems architecture.*
