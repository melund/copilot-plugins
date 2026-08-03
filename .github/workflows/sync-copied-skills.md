---
description: >
  Compares locally copied skills against their original upstream sources and
  creates up to 3 PRs with the most valuable updates found.
on:
  schedule: weekly
  skip-if-match: 'is:pr is:open in:title "sync-copied-skills"'
permissions:
  contents: read
tools:
  github:
    toolsets: [repos]
  web-fetch:
network:
  allowed:
    - defaults
    - github
safe-outputs:
  create-pull-request:
    max: 3
  noop:
    max: 1
---

# Sync Copied Skills

You are an agent that keeps locally copied skills up to date with their original
upstream sources.

## Context

This repository contains plugins under `plugins/`. Some plugins have skills that
were copied from external repositories. The `plugins/<plugin>/README.md` files
declare copied-skill origins in a markdown section named `Upstream Sources`
at the bottom:

```markdown
## Upstream Sources

| Local Path | Upstream URL | Synced Ref |
|------------|--------------|------------|
| `skills/some-skill` | https://github.com/org/repo/tree/main/path/to/skill | `a1b2c3d` |
```

- `Local Path` — a relative path within the plugin folder.
- `Upstream URL` — a browsable GitHub URL pointing to the original skill
  directory, following the pattern
  `https://github.com/<owner>/<repo>/tree/<branch>/<path>`.
- `Synced Ref` — the **upstream commit SHA** that the local copy was last
  reconciled against. This is the merge base for a three-way comparison. It may
  be empty if the skill has never been synced by this workflow.

### Why the baseline matters

The local copy is **not** expected to be identical to the upstream copy. Local
edits (customizations, fixes, extra sections) are intentional and must be
preserved. A naive two-way diff between the local file and the current upstream
file cannot tell the difference between:

- Content that upstream **added** (should be pulled into local), and
- Content that was **added locally** and never existed upstream (must be kept),
  or content that upstream **removed** (may or may not apply locally).

To avoid clobbering local customizations, this workflow performs a **three-way
merge**. It compares three versions of each file:

- **base** — upstream at the recorded `Synced Ref`.
- **theirs** — upstream at its current HEAD.
- **ours** — the current local copy.

Only the genuine upstream changes (`base` → `theirs`) are candidates for
applying. Any content that exists in `ours` but not in `base`/`theirs` is a
local customization and is left untouched.

## Your Task

### Step 1 — Discover copied skills

1. List all plugin directories under `plugins/`.
2. For each plugin, read `plugins/<plugin>/README.md`.
3. Parse the markdown section named `Upstream Sources`.
4. If the section contains a markdown table with `Local Path` and `Upstream URL`
  columns, record every row as `(local_path, upstream_url, synced_ref)`. The
  `Synced Ref` column is optional and may be empty or absent.
5. Skip plugins without an `Upstream Sources` section.

### Step 2 — Determine the current upstream commit

For each `(local_path, upstream_url, synced_ref)` row:

1. Parse the upstream URL into `<owner>`, `<repo>`, `<branch>`, and `<path>`.
2. Using the GitHub tools, find the **current upstream HEAD commit SHA** that
   last modified `<path>` on `<branch>` (list commits for the repo filtered by
   that path and take the newest). Call this `head_ref`.
3. If `head_ref` equals `synced_ref`, the skill is already in sync with upstream —
   there is nothing to pull. Skip it.

### Step 3 — Compute the genuine upstream changes (three-way)

For each skill that has a newer `head_ref`:

1. **If `synced_ref` is empty or absent (bootstrap case):** the workflow has no
   baseline, so it **cannot** safely tell upstream additions apart from local
   customizations. Do **not** modify any local file content in this case.
   Instead, record `head_ref` as the new baseline (handled in Step 6) so future
   runs have a merge base. Treat this skill as a "baseline-only" update: it may
   produce a PR that only updates the `Synced Ref` column, or be skipped in
   favour of skills with real content changes.
2. **If `synced_ref` is present:** fetch each relevant file at **both** refs:
   - **base** — `https://raw.githubusercontent.com/<owner>/<repo>/<synced_ref>/<path>/<file>`
   - **theirs** — `https://raw.githubusercontent.com/<owner>/<repo>/<head_ref>/<path>/<file>`

   Fetch the upstream `SKILL.md` and any `references/` files that exist at either
   ref. Also read the local file (**ours**) at
   `plugins/<plugin>/<local_path>/<file>`.
3. Compute the **upstream diff** = `base` → `theirs` for each file. This is the
   set of additions, removals, and edits that actually happened upstream since
   the last sync. Ignore trivial whitespace or formatting-only differences.
4. A difference that appears only between `ours` and `theirs` but **not** in the
   `base` → `theirs` diff is a local customization — **do not** treat it as an
   upstream change and **do not** remove or overwrite it.

### Step 4 — Evaluate and rank changes

Across all copied skills, rank the genuine upstream changes (`base` → `theirs`)
by importance. Give higher weight to:

- New reference material that covers previously undocumented topics.
- Bug fixes, corrected instructions, or updated commands.
- Genuinely useful new sections in SKILL.md.

Give lower weight to:

- Cosmetic rewording with no new information.
- Changes that are irrelevant to how the skill is used locally.

### Step 5 — Apply updates as a three-way merge

Pick the **top 3** changes ranked by importance (each for a **different skill**).
For each one, apply the upstream `base` → `theirs` changes onto the local
(**ours**) copy, as a three-way merge:

- **Add** what upstream added, integrating it into the local file while keeping
  the existing local style, indentation, and formatting conventions.
- **Update** sections upstream changed, but re-apply the change on top of any
  local edits to the same area rather than discarding the local version.
- When upstream **removed** something that is still present locally, only remove
  it locally if it is clearly obsolete upstream content; if it overlaps with a
  local customization, keep the local content.
- **Never delete local-only content** (sections present in `ours` but never in
  `base`/`theirs`). Those are intentional local customizations.

If a genuine upstream change conflicts irreconcilably with a local
customization, prefer preserving the local content and describe the conflict in
the PR body so a human can resolve it.

If no genuine upstream changes are found across any skill (all `head_ref` equal
`synced_ref`, or the only differences are local customizations), call the `noop`
safe output with a message explaining that all copied skills are already up to
date.

### Step 6 — Create pull requests

Create **one PR per updated skill** (up to 3 PRs total). For each PR:

1. Create a new branch from the default branch.
2. Commit the updated skill files **and** the updated `Synced Ref` value for that
   skill in `plugins/<plugin>/README.md` (set it to `head_ref`). Update the
   `Synced Ref` even in the bootstrap case where no content changed.
3. Create the PR with:

- **Title**: `sync-copied-skills: update <plugin>/<skill> from upstream`
- **Body**: A concise summary that includes:
  - Which skill was updated and why.
  - A link to the upstream source, and the `base` → `theirs` commit range
    (`<synced_ref>..<head_ref>`) that was applied.
  - A brief description of what changed **upstream** (not a raw local-vs-upstream
    diff), and an explicit note of any local customizations that were preserved.
  - Any unresolved conflicts a human should review.
  - A note that this was generated automatically by the sync-copied-skills workflow.

## Guidelines

- Update up to **three** skills per run, each in its own PR, to keep PRs small and reviewable.
- Do not modify files outside the skill being updated, except the `Synced Ref`
  cell for that skill in the plugin `README.md`.
- Do not alter `plugin.json`.
- Always base decisions on the **upstream** `base` → `theirs` diff, never on a
  raw local-vs-upstream comparison. The local copy is allowed to diverge.
- Never remove or overwrite local-only customizations.
- If there is nothing to update, use the `noop` safe output — do not create
  an empty PR.
- Preserve the local file's indentation and line-ending style when applying
  changes.
