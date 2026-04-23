---
name: obsidian-chat
description: For use in Claude.ai chat — not Claude Code. When Vasu says "capture this" or "save to obsidian", output a fully formatted Obsidian note as a markdown code block that he can copy-paste manually into his vault Inbox or Drafts folder. The note includes a destination_hint so that when he later opens it in Claude Code and runs obsidian-planet, it knows exactly where to place it and what connections to find.
---

# obsidian-chat

This is the Claude.ai chat version of Vasu's Obsidian capture workflow.

## What this skill does

When Vasu says **"capture this"**, **"save to obsidian"**, or **"obsidian this"** — analyze the current conversation and output a pre-formatted Obsidian note as a markdown code block ready to copy-paste.

No file tools. No vault access. The note goes to Vasu's clipboard → he pastes it into his vault manually. Later he opens Claude Code and runs `obsidian-planet` to place it properly with full vault search and backlinks.

---

## Vasu's vault — context without access

**Vault structure:**
```
Vasu Brain/
├── 00 Bindu/          → foundational cosmology, zero-infinity, Bindu-Rekha philosophy
├── 01 Mind/Ideas/     → atomic ideas, mental models, principles
├── 01 Mind/Books/     → book notes
├── 01 Mind/People/    → person notes
├── 02 Build/          → ventures (Bindu Rekha / Oneworx / Coffee for Thoughts / Knademy / Mapin / DELP)
├── 03 Create/Seeds/   → essay kernels, ideas wanting expression
├── 03 Create/Drafts/  → longer-form work in formation
├── 04 Life/           → habits, health, finance, virtues
└── Inbox/             → raw capture, unprocessed
```

**Vasu's ventures:**
- Bindu Rekha Architects — architecture practice
- Oneworx — coworking centers (HR / E5 / 10 No / Fortune), Bhopal
- Coffee for Thoughts — the pause in the sequence
- Knademy — learning/play venture
- DELP — design outsourcing, India → international
- Mapin — early digital venture

**Processing stages (Panchkosha):**
- `annamaya` — raw capture
- `prāṇamaya` — in own words
- `manomaya` — multiply connected
- `vijñānamaya` — generates insight

---

## Step 1 — Read the conversation

Identify:
1. **The core subject** — what is this actually about? One sentence.
2. **Domain signal** — venture? cosmology? habit? essay seed? mental model?
3. **Atomicity** — one idea or several distinct ideas?
4. **Entities** — books, people, ventures, concepts named.
5. **Save target** — should this go to `Inbox/` or `03 Create/Drafts/`?
   - `Inbox/` → raw, exploratory, needs Vasu's synthesis
   - `03 Create/Drafts/` → more formed, closer to a publishable piece

## Step 2 — If multiple distinct ideas

Ask before outputting:

> "I see [N] distinct ideas here: [A], [B], [C]. Capture as one note, or split into [N] separate notes?"

Wait for confirmation. Do not assume.

## Step 3 — Output the note

Output a single markdown code block (so Vasu can copy cleanly). Structure:

~~~markdown
---
title: "[Evocative specific title — not generic]"
domain: [bindu | mind | build | create | life]
stage: annamaya
type: [idea | seed | note]
source: claude-session
created: [today's date YYYY-MM-DD]
processed: false
save_to: [Inbox/ | 03 Create/Drafts/]
destination_hint: "[where obsidian-planet should look, and why — e.g. '01 Mind/Ideas/ — this is an atomic mental model about X, not tied to a specific venture']"
tags:
  - [2–5 lowercase tags from content]
---

[Full content of the response — preserved completely, no compression, no summarizing]

## Connects To (unverified — Claude Code will confirm)
- [[Possible link A]]
- [[Possible link B]]
- [[Possible link C]]
- [[Forward link D — does not exist yet but should]]
~~~

---

## Rules

- **Only the output is the knowledge.** Do not include the prompt, the reason for capture, or any meta.
- **Preserve the full content.** No compression. No summarizing. This is a knowledge bank.
- **No AI-invented content.** No "Architect's Lens", no "Vasu's Application", no open questions you invented.
- **Wikilinks are guessed** — you have no vault access. Mark the Connects To section clearly as "unverified — Claude Code will confirm". Claude Code's `obsidian-planet` does the real search later.
- **The `destination_hint` is critical.** Write it in plain language — e.g. *"02 Build/Oneworx/ — this is about occupancy strategy for the coworking centers, not a general mental model."* This is what `obsidian-planet` reads first when Vasu returns to process it.
- **Evocative filenames.** `Spanda — The First Pulse` not `Philosophy Notes`.

---

## After outputting

Tell Vasu in one line:

> *"Copy the note above → paste into `[Inbox/ | 03 Create/Drafts/]` → when you're ready, open Claude Code and run `obsidian-planet` to place it properly."*

---

## Setup instructions (for Vasu)

To use this in Claude.ai:
1. Go to **claude.ai → Projects → New Project**
2. Name it: `Obsidian Capture`
3. Paste the entire body of this skill (below the frontmatter) as the **Project Instructions**
4. In any conversation inside that Project, say **"capture this"** and Claude will output the formatted note.

Alternatively, start any claude.ai conversation with: *"Follow these instructions for this session: [paste skill body]"* — then proceed with your actual conversation.
