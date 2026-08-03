# OKF

Author and maintain [Open Knowledge Format (OKF)](https://github.com/GoogleCloudPlatform/knowledge-catalog/tree/main/okf)
v0.1 knowledge vaults — a directory tree of markdown files with YAML frontmatter,
browsable in Obsidian and ingestible by AI assistants.

## What it does

| Area | Examples |
|------|----------|
| Capture | Summarize durable knowledge from a session into concept notes |
| Merge | Per-fact decision: enrich an existing note, create a new one, or skip |
| Integrity | Strict augmentation — preserve existing headings, merge `tags`, refresh `timestamp` |
| Bookkeeping | Update `index.md` descriptions and append dated `log.md` entries |
| Portability | Works against any OKF/Obsidian vault; resolves the target vault per invocation |

## Skills

### `okf-update-notes`

Activates when you invoke `/okf-update-notes` (or ask to "add a note to my OKF
vault" / "summarize this concept into my notes"). It resolves the target vault,
distills the session into discrete facts, decides per fact whether to enrich an
existing note, mint a new one, or skip, and applies OKF v0.1 augmentation rules.
Model auto-invocation is disabled so it only runs when you ask for it explicitly.

The skill bundles a vendored copy of the OKF v0.1 specification at
[`references/okf-spec-v0.1.md`](./skills/okf-update-notes/references/okf-spec-v0.1.md)
so it is self-contained.

## Prerequisites

- A target OKF/Obsidian vault (a directory of markdown files). The skill asks for
  or resolves the vault path on each run.

## Upstream Sources

The bundled specification is a verbatim copy of the upstream OKF spec. Refresh it
manually when the format revises.

| Local Path | Upstream URL | Synced Ref |
|------------|--------------|------------|
| `skills/okf-update-notes/references/okf-spec-v0.1.md` | https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md | |
