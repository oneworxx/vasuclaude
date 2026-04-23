---
name: obsidian-process
description: Use this skill when Vasu pastes a pre-formatted Obsidian note (output from /obsidian-chat) and says "process this", "place this", "save this to obsidian", or "planet this". Reads the destination_hint from the frontmatter, searches the vault for real backlinks, upgrades the unverified Connects To section, and writes the note to the correct vault location. This is the Claude Code companion to /obsidian-chat — it completes what chat could not do.
argument-hint: (paste the obsidian-chat output here, or include it in your message)
allowed-tools: [Write, Read, Glob, Grep]
---

# obsidian-process

You are completing a two-step capture workflow. Vasu used `/obsidian-chat` in Claude.ai to get a pre-formatted note. He has now pasted that note here in Claude Code. Your job: take the pre-built note, do the vault search that chat could not do, upgrade the backlinks, confirm or correct the destination, and write it to the vault.

Do not re-analyze or rewrite the content. The content is final. Only enhance the connections and place it.

## Input

The pasted markdown will be in `$ARGUMENTS` or in the most recent message. It will have:
- YAML frontmatter with `source: claude-session`, `processed: false`, `destination_hint`, `save_to`
- Full body content
- A `## Connects To (unverified — Claude Code will confirm)` section

## Steps

### Step 1 — Parse the note

Extract from frontmatter:
- `title`
- `domain`
- `destination_hint` — the plain-language placement guidance from Claude.ai
- `save_to` — Inbox/ or 03 Create/Drafts/ (where Vasu may have already saved it manually)
- `tags`
- All wikilinks already in the `## Connects To` section

Extract from body:
- Every book, person, venture, concept mentioned (entities for vault search)

### Step 2 — Confirm or correct destination

Read the `destination_hint`. Walk the placement decision tree (below) to confirm it makes sense given the content.

If the hint is clear and correct → proceed silently.
If the hint is ambiguous or seems wrong → tell Vasu in one line and suggest the correct folder before writing.

**Placement decision tree (walk in order, stop at first match):**
1. Cosmological / zero-infinity / Bindu-Rekha foundational → `00 Bindu/`
2. Named venture (Bindu Rekha / Oneworx / Coffee for Thoughts / Knademy / DELP / Mapin) → `02 Build/[Venture]/`
3. Essay kernel / publishable insight → `03 Create/Seeds/`
4. Longer-form in formation → `03 Create/Drafts/`
5. Habits / health / finance / virtues → `04 Life/[subfolder]/`
6. Deep discussion of one specific book or person → append to `01 Mind/Books/[Book].md` or `01 Mind/People/[Person].md`
7. Default: atomic concept / mental model → `01 Mind/Ideas/`

### Step 3 — Search the vault (the work obsidian-chat could not do)

For every entity extracted in Step 1, search:
```
Glob: 01 Mind/Books/*[title]*.md
Glob: 01 Mind/People/*[name]*.md
Glob: 02 Build/**/*[venture]*.md
Grep: vault for concept names
```

Build two lists:
- **Confirmed in vault** — these exist, wikilinks are strong
- **Not in vault** — keep as forward-links, they map the future graph

### Step 4 — Upgrade the note

Take the original note content. Make only these changes:
1. Replace `## Connects To (unverified — Claude Code will confirm)` with `## Connects To`
2. Replace the unverified link list with your confirmed list (verified + forward-links with one-line reason each)
3. Embed any newly confirmed `[[wikilinks]]` inline in the body where entities are mentioned (if they aren't already linked)
4. Update frontmatter:
   - Remove `processed: false` → set `processed: true`
   - Remove `save_to` field
   - Remove `destination_hint` field
   - Set `stage` to `prāṇamaya` (if not already set higher)

Do NOT change the body content. Do NOT add sections. Do NOT rewrite anything.

### Step 5 — Write the file

Write to the correct folder based on Step 2.

**Vault root:** `C:\Users\vasue\Documents\Vasu Brain\`
**Filename:** use the `title` from frontmatter as the filename.

If `save_to` was `Inbox/` and Vasu already saved it there manually, do NOT write a duplicate. Instead, write to the correct destination and tell Vasu to delete the Inbox copy.

### Step 6 — Return next actions

```
Placed: `[full path]`
Reason: [one line — confirmed or corrected from destination_hint]

Connects to (confirmed in vault):
- [[Note A]] — [how it connects]
- [[Note B]] — [how it connects]

Forward-links (not in vault yet — worth writing):
- [[Concept C]]
- [[Person D]]

Next:
- [Optional: "Tensions with [[X]] — worth reconciling"]
- [Optional: "Could seed an essay → 03 Create/Seeds/"]
- [Optional: "Strengthens [[Y]] — add a back-reference there"]
- [Optional: "Delete the copy in Inbox/ — this has been placed"]
```

## What Not to Do

- Do not rewrite or compress the content
- Do not add "Architect's Lens", "Vasu's Application", or any AI-invented section
- Do not change the title
- Do not remove any body content
- Do not silently change the destination without telling Vasu if you're overriding the hint
