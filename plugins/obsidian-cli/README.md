# Obsidian CLI

Control Obsidian vaults from the terminal using the official Obsidian CLI (v1.12+). Covers 130+ commands for notes, daily notes, search, properties, tags, tasks, links, bookmarks, templates, plugins, sync, themes, and developer tools.

## What it does

| Area | Examples |
|------|----------|
| Note operations | Read, create, append, prepend, move, rename, delete notes |
| Daily notes | Open, read, append, prepend to today's daily note |
| Search | Full-text search with folder scoping, JSON output, context matching |
| Metadata | Read/set/remove frontmatter properties, list tags and aliases |
| Tasks | Query, filter, and toggle checkbox tasks across the vault |
| Graph analysis | Backlinks, outgoing links, orphans, unresolved wikilinks |
| Vault management | Plugins, themes, sync, bookmarks, templates, CSS snippets |
| Developer tools | JavaScript eval, screenshots, DOM/CSS inspection, DevTools |

## Skills

### `obsidian-cli`

Activates when the user wants to interact with an Obsidian vault — reading or writing notes, searching, managing tasks, properties, tags, links, or any other vault operation via CLI. Also triggers for vault automation and CLI scripting workflows.

## Prerequisites

- Obsidian Desktop v1.12.0+
- CLI enabled in Settings → Command line interface
- Obsidian desktop app running (CLI communicates via IPC)

## Upstream Sources

| Local Path | Upstream URL |
|------------|--------------|
| `skills/obsidian-cli` | https://github.com/pablo-mano/Obsidian-CLI-skill/tree/main/plugins/obsidian-cli/skills/obsidian-cli |
