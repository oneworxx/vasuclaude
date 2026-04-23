---
name: obsidian-inbox
description: Capture a Claude response as a raw draft in Vasu's Obsidian Inbox for later processing. Use when the content is exploratory, incomplete, or Vasu wants to decide later where it belongs. Lands in Inbox/ at stage annamaya. Companion skill is obsidian-planet for direct placement in the knowledge graph.
---

# obsidian-inbox

You are saving a Claude response into Vasu Bhatt's Obsidian vault as a raw capture in `Inbox/`. This is the **annamaya** layer — unprocessed matter. Vasu will refine it later.

## The vault

Located at `C:\Users\vasue\Documents\Vasu Brain\`. Read `CLAUDE.md` in that directory if you need identity context — but the core rule is:

> **Only the output is the knowledge.** Do not preserve the prompt, reason for capture, or any meta. After ten years, only the content will matter.

## What to write

### Filename
Evocative, specific, title-cased. Not generic. Example: `Spanda — The First Pulse.md`, not `Philosophy Session.md`.

Full path: `C:\Users\vasue\Documents\Vasu Brain\Inbox\[Evocative Title].md`

### Frontmatter

```yaml
---
title: "[Evocative title]"
domain: [bindu | mind | build | create | life]   ← best guess; Vasu will refine
stage: annamaya
type: idea
source: claude-session
created: [today's date in YYYY-MM-DD]
processed: false
tags:
  - [2–5 lowercase tags drawn from the content]
---
```

### Body

1. Preserve the full content of the Claude response. Do **not** summarize, compress, or reinterpret.
2. Keep the original structure (headers, lists, emphasis).
3. Embed `[[wikilinks]]` at the point of mention for:
   - Books named → `[[Book Title]]`
   - People named → `[[Person Name]]`
   - Ventures named → `[[Bindu Rekha]]`, `[[Oneworx]]`, `[[Coffee for Thoughts]]`, `[[Knademy]]`, `[[Mapin]]`, `[[DELP]]`
   - Core concepts → `[[Concept]]`
4. End with a `## Connects To` section listing 3–6 wikilinks to relevant vault notes (existing or to-be-written).

### Do NOT add

- No "Why Captured" or "Prompt" sections.
- No "Architect's Lens" callouts.
- No "Vasu's Application" sections.
- No "Open Question" at the end.
- No AI-generated interpretations, summaries, or commentary.
- No resonances or connections Vasu didn't imply.

## Multiple ideas?

If the response contains several clearly distinct atomic ideas that don't share one thread, pause and ask:

> "I see [N] distinct ideas here: [A], [B], [C]. Save as one combined inbox note, or split into [N] atomic notes?"

Do not split without asking.

## Process

1. Read the content carefully. Identify the core subject, entities (books/people/ventures/concepts), and suggested domain.
2. Choose an evocative filename.
3. Scan the vault briefly for obvious existing notes to link (no deep search needed — `planet` does that work; `inbox` is quick capture).
4. Write the file using the `Write` tool.
5. Confirm to Vasu with a one-line summary:
   > *Saved to Inbox: `[filename]` — [one-sentence gist]. Awaiting processing.*

## Philosophy

Inbox is the annamaya layer — raw, unprocessed, still undigested. Its job is to hold content safely until Vasu decides where it belongs. Do not over-engineer it. Do not attempt full backlinking, domain placement, or stage advancement. Those are `planet`'s job.
