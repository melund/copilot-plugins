# Copilot-plugins

A personal agent plugin marketplace for VS Code and GitHub Copilot CLI. Skills are distributed as [agent plugins](https://code.visualstudio.com/docs/copilot/customization/agent-plugins) that can be discovered, installed, and updated directly from VS Code or the Copilot CLI.

## Available plugins

### Local plugins

| Plugin | Skills | Description |
|--------|--------|-------------|
| `conda-packaging` | conda-forge, rattler-build | Conda packaging operations — fix failing builds, create new packages, migrate recipes, build conda packages |
| `data-visualization` | matplotlib-data-visualization, pydantic-evals | Chart design and data storytelling with matplotlib; evaluation of non-deterministic functions with pydantic-evals |
| `typst` | typst | Modern markup-based typesetting system for scientific documents, presentations, and math |
| `sqlalchemy` | sqlalchemy | Python SQL toolkit and ORM — engine management, declarative mapping, sessions, queries |
| `human-writing-en` | human-writing-en | English writing style that reads as human-authored, not AI-generated |
| `joss-review` | joss-review | Guide for reviewing Journal of Open Source Software (JOSS) submissions |
| `presentation-design` | presentation-design | Slide design and storytelling guidelines for all presentation tools |

### External plugins

These reference upstream repositories directly:

| Plugin | Source | Description |
|--------|--------|-------------|
| `anthropic-skills` | [anthropics/skills](https://github.com/anthropics/skills) | Document processing skills (PowerPoint, Word, Excel, PDF) |
| `scientific-skills` | [k-dense-ai/claude-scientific-skills](https://github.com/k-dense-ai/claude-scientific-skills) | Literature review, peer review, Polars DataFrame library |

## Installation

### VS Code

1. Enable agent plugins (preview feature):

   ```jsonc
   // settings.json
   "chat.plugins.enabled": true
   ```

2. Add this marketplace to your VS Code settings:

   ```jsonc
   // settings.json
   "chat.plugins.marketplaces": [
       "melund/skill-forge"
   ]
   ```

3. Open the Extensions view (`Ctrl+Shift+X`), type `@agentPlugins` in the search bar, and browse the available plugins. Select **Install** on any plugin you want to use.

### Copilot CLI

```bash
# Register the marketplace
copilot plugin marketplace add melund/skill-forge

# Browse available plugins
copilot plugin marketplace browse melund-skill-forge

# Install a plugin
copilot plugin install conda-packaging@melund-skill-forge
```

## Repository structure

```
.github/
  plugin/
    marketplace.json          # Marketplace manifest
plugins/
  conda-packaging/
    plugin.json               # Plugin manifest
    skills/
      conda-forge/            # SKILL.md + references/
      rattler-build/          # SKILL.md + references/
  data-visualization/
    plugin.json
    skills/
      matplotlib-data-visualization/
      pydantic-evals/
  typst/
    plugin.json
    skills/typst/             # SKILL.md + PROMPT.md + references/
  sqlalchemy/
    plugin.json
    skills/sqlalchemy/        # SKILL.md + PROMPT.md
  human-writing-en/
    plugin.json
    skills/human-writing-en/
  joss-review/
    plugin.json
    skills/joss-review/
  presentation-design/
    plugin.json
    skills/presentation-design/
```

## Adding a new plugin

1. Create a directory under `plugins/<plugin-name>/` with a `plugin.json` manifest and a `skills/` subdirectory.
2. Place `SKILL.md` files (with YAML frontmatter containing `name` and `description`) in `skills/<skill-name>/`.
3. Add the plugin entry to `.github/plugin/marketplace.json`.

See the [plugin reference](https://docs.github.com/en/copilot/reference/cli-plugin-reference) for the full `plugin.json` and `marketplace.json` schemas.
