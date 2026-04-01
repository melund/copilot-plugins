---
sources:
    "skills/marimo-notebook": "https://github.com/marimo-team/skills/tree/main/skills/marimo-notebook"
    "skills/anywidget": "https://github.com/marimo-team/skills/tree/main/skills/anywidget"
    "skills/marimo-batch": "https://github.com/marimo-team/skills/tree/main/skills/marimo-batch"
    "skills/wasm-compatibility": "https://github.com/marimo-team/skills/tree/main/skills/wasm-compatibility"
---
# Marimo

Skills for working with [marimo](https://marimo.io/) reactive Python notebooks.

## What it does

| Area | Examples |
|------|----------|
| Notebook authoring | Write marimo notebooks with correct cell structure, PEP 723 metadata, reactivity patterns |
| Custom widgets | Generate anywidget components with JavaScript/CSS for interactive visualizations |
| Batch jobs | Prepare notebooks for scheduled CLI runs with Pydantic-based configuration |
| WASM compatibility | Check whether a notebook can run in WebAssembly (Pyodide) environments |

## Skills

### `marimo-notebook`

Activates when writing or editing marimo notebooks. Covers cell structure, reactivity, script mode, PEP 723 dependencies, testing, and best practices.

### `anywidget`

Activates when generating custom interactive widgets using anywidget for marimo notebooks. Covers vanilla JS rendering, CSS styling, and marimo wrapping.

### `marimo-batch`

Activates when preparing a marimo notebook for scheduled or CLI-driven batch runs. Uses Pydantic models for configurable parameters with both UI and CLI support.

### `wasm-compatibility`

Activates when checking whether a marimo notebook is compatible with WebAssembly environments (playground, community cloud, exported WASM HTML). Reports package and code-pattern issues.

## Prerequisites

- Python 3.12+
- [uv](https://docs.astral.sh/uv/) or pip
- marimo (`uv pip install marimo`)
