---
name: okf-update-notes
description: >-
  Summarize new knowledge and merge it into an Open Knowledge Format (OKF)
  v0.1 / Obsidian knowledge vault. Use when the user invokes it explicitly to
  "add a note to my OKF vault", "summarize this concept into my notes",
  "capture this in my knowledge base", or "update my notes". Resolves the target
  vault, then decides per fact whether to enrich an existing note, create a new
  note, or skip, following OKF augmentation rules and updating index.md / log.md.
license: BSD-3-Clause
disable-model-invocation: true
---

# OKF: Update Notes from a Session

Merge knowledge produced during a session into an OKF v0.1 knowledge vault
(a directory of markdown files with YAML frontmatter, browsed with Obsidian)
without clobbering existing content.

The full OKF v0.1 specification is bundled at [`references/okf-spec-v0.1.md`](./references/okf-spec-v0.1.md).
Consult it for the authoritative rules on frontmatter, links, index files, and logs.

## When to use

- The user explicitly asks to capture/save knowledge into their OKF vault.
- Trigger phrases: "add a note to my OKF vault", "summarize this concept into my
  notes", "capture this in my knowledge base", "update my notes".

Do **not** use for transient chit-chat, or to log a daily plan (that belongs in a
`Journal/` daily note, not a concept note).

## Step 0 — Resolve the target vault

This skill is vault-agnostic and is used from several machines (and sometimes
WSL), so the vault root differs per environment. Resolve it in this order:

1. **Explicit path.** If the user named a vault path or folder in the request, use
   that and skip to confirmation.
2. **Registry lookup.** Read the vault registry at
   [`/memories/okf-vaults.md`](/memories/okf-vaults.md) (create it lazily — see
   format below). Determine the current **environment key** and look for a matching
   entry:
   - Environment key = `<os>:<hostname>`, e.g. `windows:LAPTOP-ABC`,
     `wsl:LAPTOP-ABC`, `linux:workstation`, `darwin:mac-mini`.
   - Detect it with a quick shell probe, e.g.
     `uname -s -n` (POSIX/WSL — WSL reports a `Microsoft`/`WSL` kernel string) or
     `$env:COMPUTERNAME` + `$PSVersionTable.OS` (PowerShell on Windows).
   - **Verify the recorded path still exists** before trusting it. If it's gone
     (repo moved/renamed), treat as a miss and re-ask.
3. **Ask and save.** If no matching, valid entry exists, ask the user for the vault
   root path for *this* environment, then append it to the registry under the
   current environment key. Never overwrite another environment's entry.

Because agent memory does not reliably sync across machines, expect the registry
to be empty on a machine you haven't used the skill on before — that's normal;
just ask once and record it.

Confirm the resolved root once ("Using vault `<path>` for `<env-key>`"), then treat
all paths below as relative to it.

### Registry format (`/memories/okf-vaults.md`)

A flat list, one entry per environment key. Keep it minimal:

```markdown
# OKF vault locations

- windows:LAPTOP-ABC — C:\Users\molu\repos-personal\Memex
- wsl:LAPTOP-ABC — /mnt/c/Users/molu/repos-personal/Memex
- linux:workstation — /home/molu/vaults/Memex
```

Notes:
- The same physical vault can appear under multiple keys with different path
  syntaxes (a Windows checkout accessed from WSL via `/mnt/c/...`, or a separate
  clone). Store whatever root works for the environment you're running in.
- If several vaults exist on one machine, either key them more specifically
  (`windows:LAPTOP-ABC:work`) or fall back to asking which one.

## Vault conventions

- Concept = one non-reserved `.md` file. Concept ID = path minus `.md`.
- Reserved files: `index.md` (directory listing), `log.md` (change history). Never
  treat these as concept notes.
- Frontmatter: `type` (required) + `title`, `description` (one sentence), `tags`,
  `timestamp` (ISO 8601), `resource` (optional URL).
- Suggested `type` vocabulary: `Playbook`, `Reference`, `Plan`, `Idea`, `Meeting`,
  `Talk`, `Journal`, `Concept` (fallback). Unknown types are tolerated.
- Links: prefer bundle-root-absolute (`/work/New artifact server.md`); Obsidian
  `[[wikilinks]]` are acceptable too.

## Procedure

1. **Summarize.** Distill the session into a short list of discrete, durable facts.
   Drop anything transient, speculative, or already recorded.

2. **Locate candidates.** For each fact, read the relevant folder's `index.md` to
   see what already exists, then fully read the best-matching note before deciding.
   Do not decide from the filename alone.

3. **Decide per fact** (one of three):
   - **Enrich existing** — the fact belongs to an existing concept. Read the current
     note, then apply the augmentation rules below.
   - **Create new** — only if the fact is a standalone, reusable concept that doesn't
     fit an existing note. Gate against noise: skip if it's a passing remark, an
     overview/intro with no reusable substance, or duplicates an existing note.
   - **Skip** — irrelevant, low-signal, or already covered. Skipping is fine.

4. **Apply the change** using the augmentation rules.

5. **Record.** Refresh the note's `timestamp`. If the change is significant, add a
   dated entry to that folder's `log.md` (create it if absent; newest first). Update
   the affected `index.md` description if the note's summary changed.

6. **Report.** End with one line: how many notes you enriched, created, and skipped.

## Augmentation rules (enriching an existing note)

Treat the existing note as the source of truth; fold new content into it.

- **Frontmatter:** keep `type`, `title`, `resource` verbatim. Merge `tags` (union,
  never replace). Refresh `timestamp` to now (ISO 8601 UTC). Only refine
  `description` if the new content yields a more accurate one-sentence summary.
- **Body:** preserve every existing `#` heading, in order, with the same wording.
  You may extend prose, add bullets to existing lists, add `##` subsections, or add
  new top-level headings **after** the existing ones. You may **not** drop, rename,
  or wholesale-rewrite existing headings/content.
- If the new material doesn't fit the existing structure, create a separate note and
  cross-link it, or skip — do not force it in.

## New note template

```markdown
---
type: <Playbook | Reference | Plan | Idea | Meeting | Talk | Concept>
title: <human-readable name>
description: <one sentence>
tags: [<tag>, <tag>]
timestamp: <ISO 8601 UTC>
resource: <optional canonical URL>
---

<1–3 paragraph description of what this is and how it's used.>

# <conventional headings as applicable: Schema / Examples / Steps / Citations>
```

## Conventional headings

Use when applicable: `# Schema`, `# Examples`, `# Steps`, `# Citations`. Under
`# Citations`, list external sources numbered: `[1] [Title](https://…)`. Cite only
sources you actually consulted; never invent URLs.

## log.md format

```markdown
# Update Log

## YYYY-MM-DD
* **Update**: Enriched [Calendar sync](/work/Calendar sync.md) with scheduled-task details.
* **Creation**: Added [New reference](/work/some-note.md).
```
