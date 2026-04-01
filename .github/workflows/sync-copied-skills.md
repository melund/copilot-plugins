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
use YAML front-matter with a `sources` map to declare where each skill
originated:

```yaml
---
sources:
    "skills/some-skill": "https://github.com/org/repo/tree/main/path/to/skill"
---
```

The `sources` map keys are relative paths within the plugin folder and the values
are browsable GitHub URLs pointing to the original skill directory.

## Your Task

### Step 1 — Discover copied skills

1. List all plugin directories under `plugins/`.
2. For each plugin, read `plugins/<plugin>/README.md`.
3. Parse the YAML front-matter. If there is a `sources` block, record every
   `(local_path, upstream_url)` pair. Skip plugins without `sources`.

### Step 2 — Fetch upstream content and compare

For each `(local_path, upstream_url)` pair:

1. Convert the browsable GitHub URL to raw content URLs. The upstream URL
   follows the pattern
   `https://github.com/<owner>/<repo>/tree/<branch>/<path>`.
   To fetch a file from that tree, use
   `https://raw.githubusercontent.com/<owner>/<repo>/<branch>/<path>/<file>`.
2. Fetch the upstream `SKILL.md` and any files in the `references/` directory
   that also exist locally.
3. Read the corresponding local file at
   `plugins/<plugin>/<local_path>/SKILL.md` (and `references/*`).
4. Diff each file. Note meaningful additions, removals, and changes.  
   Ignore trivial whitespace or formatting-only differences.

### Step 3 — Evaluate and rank changes

Across all copied skills, rank the meaningful upstream changes by importance.
Give higher weight to:

- New reference material that covers previously undocumented topics.
- Bug fixes, corrected instructions, or updated commands.
- Genuinely useful new sections in SKILL.md.

Give lower weight to:

- Cosmetic rewording with no new information.
- Changes that are irrelevant to how the skill is used locally.

### Step 4 — Apply updates

Pick the **top 3** changes ranked by importance (each for a **different skill**).
For each one, apply the upstream change to the local copy, keeping the existing
local style and formatting conventions intact. A single change may span multiple
files within the same skill.

If no meaningful changes are found across any skill, call the `noop` safe output
with a message explaining that all copied skills are already up to date.

### Step 5 — Create pull requests

Create **one PR per updated skill** (up to 3 PRs total). For each PR:

1. Create a new branch from the default branch.
2. Commit only the files belonging to that one skill.
3. Create the PR with:

- **Title**: `sync-copied-skills: update <plugin>/<skill> from upstream`
- **Body**: A concise summary that includes:
  - Which skill was updated and why.
  - A link to the upstream source.
  - A brief description of what changed.
  - A note that this was generated automatically by the sync-copied-skills workflow.

## Guidelines

- Update up to **three** skills per run, each in its own PR, to keep PRs small and reviewable.
- Do not modify files outside the skill being updated.
- Do not alter the README.md front-matter or the plugin.json.
- If there is nothing to update, use the `noop` safe output — do not create
  an empty PR.
- Preserve the local file's indentation, line-ending style, and front-matter
  format when applying changes.
