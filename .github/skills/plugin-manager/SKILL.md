---
name: plugin-manager
description: >-
  This skill should be used when the user asks to "add a plugin",
  "create a new skill", "add an agent to a plugin", "add hooks",
  "add an MCP server", "register an external plugin",
  "update marketplace.json", or "scaffold a plugin folder".
  Manages the copilot-plugins repository structure and marketplace manifest.
---

# Plugin Manager

Manage plugins, skills, agents, hooks, and MCP servers in the `copilot-plugins` repository while keeping the directory structure and marketplace manifest consistent.

## Repository Layout

```
.github/plugin/marketplace.json   # Marketplace manifest (all plugins listed here)
plugins/<name>/
  plugin.json                      # Plugin manifest
  README.md                        # Plugin docs with source attribution
  LICENSE                          # License file (copied from source when applicable)
  skills/<skill-name>/
    SKILL.md                       # Skill definition (YAML frontmatter + body)
    PROMPT.md                      # Optional supplementary instructions
    references/                    # Optional reference material
  agents/<agent-name>.agent.md     # Optional custom agents
  hooks/
    hooks.json                     # Optional hook configuration
    scripts/                       # Optional hook scripts
  .mcp.json                        # Optional MCP server definitions
```

## Decision Flow

Determine what the user wants to add, then follow the matching workflow.

| Request | Workflow |
|---------|----------|
| Whole plugin (local copy) | Add Plugin → Option B |
| Whole plugin (external reference) | Add Plugin → Option A |
| Skill to existing plugin | Add Skill |
| Custom agent to a plugin | Add Agent |
| Hooks to a plugin | Add Hooks |
| MCP server to a plugin | Add MCP Server |

## Workflow: Add a Plugin

Ask the user: **Add the plugin to this repository, or just reference an external source?**

### Option A — Reference Only

1. Collect the GitHub repo (`owner/repo`), a commit SHA or tag, and a short description.
2. Add an external-source entry to `.github/plugin/marketplace.json`. See **`references/templates.md` → Marketplace Entry (external)** for the JSON shape.
3. Add the plugin to the **External plugins** table in the root `README.md`.
4. Confirm with the user.

### Option B — Add Locally

1. Create `plugins/<plugin-name>/plugin.json`. See **`references/templates.md` → plugin.json**.
2. Create `plugins/<plugin-name>/README.md`. See **`references/templates.md` → README.md**. When the plugin originates from an external source, add an `Upstream Sources` section at the bottom with a table mapping local skill paths to upstream URLs.
3. Create skill folders under `plugins/<plugin-name>/skills/<skill-name>/` with a `SKILL.md`. Every `SKILL.md` requires YAML frontmatter with `name` and `description`. The description must contain trigger phrases for activation.
4. Add a local-source entry to `.github/plugin/marketplace.json`. See **`references/templates.md` → Marketplace Entry (local)**.
5. Add the plugin to the **Local plugins** table in the root `README.md`.
6. Follow the license handling procedure in **`references/license-policy.md`** when copying from an external source.
7. Confirm the full set of created files with the user.

## Workflow: Add a Skill

1. List existing plugins and their skills by scanning `plugins/*/plugin.json`.
2. Suggest which existing plugin the new skill fits into based on topic overlap.
3. Ask the user: **Add this skill to `<suggested-plugin>`, or create a new plugin?**
4. If existing plugin: create the skill folder under that plugin's `skills/` directory and update the plugin's `README.md` to document the new skill.
5. If new plugin: follow Add Plugin → Option B.
6. Every `SKILL.md` must have YAML frontmatter with at least `name` and `description`. The description must contain trigger phrases.

## Workflow: Add an Agent

1. List existing plugins by scanning `plugins/*/plugin.json`.
2. Suggest which plugin the agent fits into based on topic overlap.
3. Ask the user: **Add this agent to `<suggested-plugin>`, or create a new plugin?**
4. Create the agent file at `plugins/<plugin-name>/agents/<agent-name>.agent.md` with YAML frontmatter (`description`, `tools`) and a body defining persona, constraints, and approach. See **`references/templates.md` → Agent file**.
5. Update the plugin's `README.md` to document the new agent.

## Workflow: Add Hooks

1. List existing plugins by scanning `plugins/*/plugin.json`.
2. Suggest which plugin the hooks fit into.
3. Ask the user: **Add these hooks to `<suggested-plugin>`, or create a new plugin?**
4. Create or update `plugins/<plugin-name>/hooks/hooks.json`. See **`references/templates.md` → hooks.json**. Supported events: `SessionStart`, `UserPromptSubmit`, `PreToolUse`, `PostToolUse`, `PreCompact`, `SubagentStart`, `SubagentStop`, `Stop`.
5. Place hook scripts in `plugins/<plugin-name>/hooks/scripts/`. Use `${CLAUDE_PLUGIN_ROOT}` for paths — plugins are installed outside the workspace.
6. Update the plugin's `README.md` to document the hooks.

## Workflow: Add MCP Server

1. List existing plugins by scanning `plugins/*/plugin.json`.
2. Suggest which plugin the MCP server fits into.
3. Ask the user: **Add this MCP server to `<suggested-plugin>`, or create a new plugin?**
4. Create or update `plugins/<plugin-name>/.mcp.json`. See **`references/templates.md` → .mcp.json**. Use `${CLAUDE_PLUGIN_ROOT}` for paths referencing files within the plugin directory.
5. Update the plugin's `README.md` to document the MCP server.

## Constraints

- DO NOT modify skills, agents, hooks, or plugins that already exist unless explicitly asked.
- DO NOT invent skill or agent content — ask the user for the domain knowledge or source material.
- DO NOT skip the `marketplace.json` update — every plugin must be registered there.
- DO NOT skip the LICENSE file when copying from an external source.
- ALWAYS warn the user about non-permissive licenses before proceeding (see `references/license-policy.md`).
- ALWAYS confirm the plan with the user before creating files.

## Additional Resources

### Reference Files

For templates and detailed policies, consult:
- **`references/templates.md`** — JSON and markdown templates for all file types (plugin.json, README.md, marketplace entries, hooks.json, .mcp.json, agent files)
- **`references/license-policy.md`** — Permissive license list, warning procedure, and copying rules
