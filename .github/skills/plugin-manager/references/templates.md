# Templates

All templates used by the plugin-manager skill when scaffolding files.

## plugin.json

```json
{
  "name": "<plugin-name>",
  "description": "<one-line description>",
  "version": "1.0.0",
  "author": { "name": "melund" },
  "license": "<SPDX-ID>",
  "keywords": ["<keyword1>", "<keyword2>"]
}
```

## README.md

When the plugin originates from an external source, include a `sources` frontmatter block. Omit the block for original plugins.

```markdown
---
sources:
    "skills/<skill-name>": "<source-url>"
---
# <Plugin Name>

<Short description of what the plugin does.>

## What it does

| Area | Examples |
|------|----------|
| ... | ... |

## Skills

### `<skill-name>`

<When this skill activates and what it covers.>

## Prerequisites

- <Required tools or runtimes>
```

## Marketplace Entry (local)

Add to the `plugins` array in `.github/plugin/marketplace.json`:

```json
{
  "name": "<plugin-name>",
  "description": "<description>",
  "version": "1.0.0",
  "source": "./plugins/<plugin-name>"
}
```

## Marketplace Entry (external)

Add to the `plugins` array in `.github/plugin/marketplace.json`:

```json
{
  "name": "<plugin-name>",
  "description": "<description>",
  "version": "1.0.0",
  "source": {
    "source": "github",
    "repo": "<owner/repo>",
    "ref": "<commit-sha-or-tag>"
  }
}
```

## SKILL.md

Every skill requires YAML frontmatter with `name` and `description`. The description must contain trigger phrases for activation.

```markdown
---
name: <skill-name>
description: >-
  <Multi-line description explaining when this skill should be used.
  Include specific trigger phrases and scenarios.>
license: <SPDX-ID>
---

# <Skill Title>

<Instructional body content in imperative/infinitive form.>
```

## Agent file

Place at `plugins/<plugin-name>/agents/<agent-name>.agent.md`:

```markdown
---
description: "<Use when... trigger phrases for subagent discovery>"
tools: [<minimal set of tool aliases>]
---

<Persona definition, constraints, and approach in imperative form.>
```

## hooks.json

Place at `plugins/<plugin-name>/hooks/hooks.json`:

```json
{
  "hooks": {
    "<EventName>": [
      {
        "type": "command",
        "command": "${CLAUDE_PLUGIN_ROOT}/hooks/scripts/<script-name>"
      }
    ]
  }
}
```

Supported events: `SessionStart`, `UserPromptSubmit`, `PreToolUse`, `PostToolUse`, `PreCompact`, `SubagentStart`, `SubagentStop`, `Stop`.

Place hook scripts in `hooks/scripts/`. Always use `${CLAUDE_PLUGIN_ROOT}` for paths inside hook commands — plugins are installed outside the workspace at runtime.

## .mcp.json

Place at `plugins/<plugin-name>/.mcp.json`:

```json
{
  "mcpServers": {
    "<server-name>": {
      "command": "<executable>",
      "args": ["<arg1>", "<arg2>"],
      "env": {}
    }
  }
}
```

Use `${CLAUDE_PLUGIN_ROOT}` for any paths referencing files within the plugin directory.
