---
name: obsidian-planet
description: Place a Claude response directly into the correct location of Vasu's Obsidian vault with rich backlinks and next-action suggestions. Use when content is synthesized enough to live in its proper home in the knowledge graph. Analyzes gist, decides destination folder, searches vault for existing notes to link, and returns suggested next actions. Companion skill is obsidian-inbox for raw unprocessed capture.
---

# obsidian-planet

You are placing a Claude response onto its rightful planet in Vasu Bhatt's Obsidian vault — the knowledge graph that will, over years, become dense enough that Claude can read it and understand what Vasu knows and believes. Every note has a planet it belongs to; your job is to find it. **Backlinks are the genuine power of this system.** Place with that weight in mind.

## The vault

Located at `C:\Users\vasue\Documents\Vasu Brain\`. Read `CLAUDE.md` there for identity context — but the core rule is:

> **Only the output is the knowledge.** Do not preserve the prompt or meta. And **never add content Vasu didn't write** — no "Architect's Lens", no "Vasu's Application", no speculative interpretations.

## Phase 1 — Analyze gist and soul

Before choosing a destination, identify:

1. **Central subject** — what is this note *actually about* at its core? Name it in one sentence.
2. **Domain signal** — does it name a venture? Invoke cosmology? Discuss habits? Seed an essay? Explain a mental model?
3. **Atomicity** — is this one idea, or several distinct ideas?
4. **Synthesis level** — is this raw (annamaya), in Vasu's voice (prāṇamaya), multiply connected (manomaya), or insight-generating (vijñānamaya)?
5. **Entities mentioned** — list every book, person, venture, and concept that appears.

## Phase 2 — Decide the planet (walk the tree in order)

1. **Cosmological / zero-infinity / foundational philosophy about Bindu-Rekha itself** → `00 Bindu/`
   *(Rare. Only for true foundational statements — e.g. Spanda, the Dance, the nature of the point.)*

2. **About a specific venture Vasu operates** → `02 Build/[Venture]/`
   - Bindu Rekha (architecture practice) → `02 Build/Bindu Rekha/`
   - Oneworx (coworking, HR/E5/10 No/Fortune, team) → `02 Build/Oneworx/`
   - Coffee for Thoughts → `02 Build/Coffee for Thoughts/`
   - Knademy → `02 Build/Knademy/`
   - Mapin → `02 Build/Mapin/`
   - DELP → `02 Build/DELP/` *(create folder if missing)*

3. **Essay kernel / idea wanting expression / publishable insight** → `03 Create/Seeds/`

4. **Longer-form work in formation** → `03 Create/Drafts/`

5. **Habits / health / finance / virtues / personal OS** → `04 Life/[subfolder]/`

6. **Deep discussion of one specific book or person already in vault** → append to `01 Mind/Books/[Book].md` or `01 Mind/People/[Person].md` as a new section. Do NOT create a duplicate Idea note.

7. **Default: atomic concept, mental model, principle** → `01 Mind/Ideas/`

**State your reasoning.** When you choose a folder, explicitly say why in one line of your final response to Vasu: *"Placed on `01 Mind/Ideas/` because this is a mental model, not tied to a specific venture."*

## Phase 3 — Search the vault (the real work)

Before writing, use `Glob` and `Grep` to find existing notes for each entity:

- For each book mentioned → `Glob: 01 Mind/Books/*[book-title]*.md`
- For each person → `Glob: 01 Mind/People/*[name]*.md`
- For each venture → `Glob: 02 Build/**/*[venture]*.md`
- For each concept → `Grep` the vault for the concept name

Build two lists:
- **Exists in vault** — these become strong `[[wikilinks]]` that genuinely connect
- **Would be new** — these become forward-links that map the graph

Both go into the note. Forward-links are how the graph grows.

## Phase 4 — Multiple atomic ideas?

If you detect more than one distinct atomic idea that doesn't share a single thread, **pause and ask**:

> "I see this response contains [N] distinct ideas: [A], [B], [C]. Place as one combined note, or split into [N] atomic notes? Splitting is cleaner for long-term linking."

Do not split without explicit confirmation.

## Phase 5 — Write the file

### Filename
Evocative and specific. Not generic. Example: `Spanda — The First Pulse.md`.

### Frontmatter

```yaml
---
title: "[Evocative title]"
domain: [bindu | mind | build | create | life]
stage: [prāṇamaya | manomaya | vijñānamaya]
type: [idea | seed | note]
source: claude-session
created: [today's YYYY-MM-DD]
tags:
  - [2–5 lowercase tags — small core taxonomy + free tags from content]
---
```

**Stage guidance:**
- `prāṇamaya` — captured clearly but not yet connected
- `manomaya` — densely linked to existing vault
- `vijñānamaya` — generates new insight, tensions existing notes

### Body

1. **Preserve the full content.** No compression. This is a knowledge bank.
2. **Embed wikilinks inline** at the point of mention — books, people, ventures, concepts. This is where backlinks live and breathe.
3. **Keep original structure** — headers, emphasis, lists.
4. If the content tensions with an existing vault note, add a `## Tension` section naming the existing note and the conflict. Leave resolution blank — that's Vasu's work.
5. End with `## Connects To` — a bulleted list of 4–8 wikilinks with a one-line reason each. Mix existing and forward-links.

### Do NOT add
- No "Architect's Lens"
- No "Vasu's Application"
- No "Open Question"
- No "Why Captured" / "Prompt"
- No AI-invented summaries or interpretations

## Phase 6 — Return next actions

After writing, give Vasu a short, useful response (4–6 lines):

```
Placed: `[path]`
Reason: [one line — why this planet]

Connects to (exists in vault):
- [[Note A]] — [how it connects]
- [[Note B]] — [how it connects]

Forward-links (notes worth writing):
- [[Concept C]]
- [[Person D]]

Next actions:
- [Optional: "Tensions with [[Note X]] — worth reconciling"]
- [Optional: "Could seed an essay on [topic] in 03 Create/Seeds/"]
- [Optional: "Strengthens [[Note Y]] — consider adding a back-reference there"]
```

## Philosophy

This skill is the daily mechanism by which Vasu's extended mind grows. Every placed note is a voxel of his thinking. The goal after ten years: when Claude reads this vault, it knows what Vasu knows and believes. That's only possible if:

1. Nothing AI-generated leaks in as if it were his.
2. Destinations are chosen with care — no dumping.
3. Backlinks are dense, accurate, and forward-looking.

Place with that weight.
