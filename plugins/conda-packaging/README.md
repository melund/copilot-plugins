---
sources:
    "skills/conda-forge": "https://github.com/pavelzw/skill-forge/tree/main/recipes/conda-forge"
    "skills/rattler-build": "https://github.com/pavelzw/skill-forge/tree/main/recipes/rattler-build"
---
# Conda Packaging

Conda packaging plugin that helps AI agents build, debug, and publish conda
packages through conda-forge and rattler-build workflows.

## What it does

This plugin provides end-to-end support for conda packaging tasks:

| Area | Examples |
|------|----------|
| New packages | Create recipes via staged-recipes, generate from PyPI with grayskull |
| Failing builds | Analyze CI logs with cf-job-logs, reproduce locally, apply minimal fixes |
| Recipe migration | Convert meta.yaml (v0) to recipe.yaml (v1) format |
| Cross-compilation | Add ARM/cross-compilation support to feedstocks |
| Package building | Build, debug, inspect, and patch conda packages with rattler-build |

## Skills

### `conda-forge`

Activated when working with conda-forge feedstocks or staged-recipes. Handles the
full feedstock lifecycle: forking, recipe creation, local testing, CI failure
diagnosis, conda-smithy rerendering, and PR submission. Requires `gh`, `git`,
`rattler-build`, `conda-smithy`, and `cf-job-logs`.

### `rattler-build`

Activated when building conda packages with rattler-build. Covers recipe authoring
(single and multi-output), local builds, build debugging, patch creation, and
package inspection. Includes reference material for the recipe.yaml format,
compiler handling, and virtual packages.

## Prerequisites

- [pixi](https://pixi.sh/) — used to run tools without global installs
- `gh` (GitHub CLI), `git`, `curl`, `jq`
- Network access for fetching sources and interacting with conda-forge
