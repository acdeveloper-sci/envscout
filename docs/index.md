# EnvScout

**Cross-platform tool to discover and manage Python virtual environments.**

`EnvScout` scans your filesystem and finds every Python virtual environment —
regardless of whether it was created with `venv`, `conda`, `poetry`, `uv`, or others.

## Features

- Fast BFS scanner with early pruning and parallel multithreaded mode
- Multi-type detection: venv, virtualenv, conda, poetry, pipenv, tox, uv, and more
- Cross-platform: Windows, Linux, macOS
- Rich terminal output with live progress and summary stats
- CLI interface (TUI and GUI planned)

## Quick Install

```bash
pip install envscout
# or
uv add envscout
```

## Quick Start

```bash
envscout scan /path/to/projects
```

See the [User Guide](user-guide/installation.md) to get started.