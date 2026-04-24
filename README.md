# EnvScout

<!-- Badges -->
![Python](https://img.shields.io/badge/python-3.11%2B-blue?logo=python&logoColor=white)
![PyPI](https://img.shields.io/pypi/v/envscout?color=blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-alpha-orange)
![Platform](https://img.shields.io/badge/platform-windows%20%7C%20linux%20%7C%20macos-lightgrey)

**Cross-platform tool to discover and manage Python virtual environments.**

`envscout` scans your filesystem and finds every Python virtual environment —
regardless of whether it was created with `venv`, `conda`, `poetry`, `uv`, or others.
Fast, cross-platform, and built with a clean CLI interface.

---

## Features

- **Fast BFS scanner** with early pruning and optional parallel multithreaded mode
- **Multi-type detection:** venv, virtualenv, conda, poetry, pipenv, tox, uv, hatch, rye
- **Cross-platform:** Windows, Linux, macOS
- **Rich terminal output** with live progress, colors, and summary stats
- **Export:** save environment lists and requirements
- **Interfaces:** CLI (stable) · TUI (planned) · GUI (planned)

---

## Installation

> **Note:** envscout is currently in alpha. PyPI release coming in v0.1.0.

```bash
# With pip
pip install envscout

# With uv (recommended)
uv add envscout
```

---

## Quick Start

```bash
# Scan current directory
envscout scan

# Scan a specific path
envscout scan /home/user/projects

# Scan in parallel mode (faster on large trees)
envscout scan /home/user/projects --parallel

# Save results to file
envscout scan /home/user/projects --save envs.txt
```

---

## Usage

```
Usage: envscout [OPTIONS] COMMAND [ARGS]...

Options:
  --help  Show this message and exit.

Commands:
  scan     Scan for Python virtual environments.
  inspect  Show packages installed in an environment.  [planned]
  export   Export requirements or reports.             [planned]
  clean    Clean or normalize requirements.            [planned]
  info     Show system info and envscout version.      [planned]
```

### `scan` options

```
Usage: envscout scan [PATH] [OPTIONS]

Arguments:
  PATH          Directory to scan. Defaults to current directory.

Options:
  -p, --parallel        Enable parallel scan mode.
  -w, --workers N       Number of worker threads (default: CPU count).
  -s, --save FILE       Save environment list to file.
  -b, --batch           Batch mode: show results at end instead of live.
  -v, --verbose         Enable verbose/debug output.
  --profile             Enable cProfile profiling.
  --help                Show this message and exit.
```

---

## Supported Environment Types

| Type         | Tool                 | Detection method                 |
| ------------ | -------------------- | -------------------------------- |
| `venv`       | Python stdlib `venv` | `pyvenv.cfg` present             |
| `virtualenv` | `virtualenv` package | `activate` script present        |
| `conda`      | Anaconda / Miniconda | `conda-meta/` directory          |
| `poetry`     | Poetry               | `pyproject.toml` + `poetry.lock` |
| `pipenv`     | Pipenv               | `Pipfile` + `Pipfile.lock`       |
| `tox`        | tox                  | `tox.ini` present                |
| `uv`         | Astral uv            | `.python-version` + `uv` markers |
| `hatch`      | Hatch                | *(planned)*                      |
| `rye`        | Rye                  | *(planned)*                      |

---

## Performance

envscout uses a BFS algorithm with early pruning: once a virtual environment
is found, its entire subtree is skipped. This makes it significantly faster
than naive recursive directory walks.

```
Benchmark (10,000 directories, 35 environments):
  Sequential:       5.0s
  Parallel (4c):    1.8s   — 2.8x speedup
  Parallel (8c):    1.3s   — 3.8x speedup
```

> Speedup is sublinear because filesystem I/O is the bottleneck, not CPU.

---

## Roadmap

| Phase | Description                              | Status        |
| ----- | ---------------------------------------- | ------------- |
| 0     | Foundation: structure, docs, tooling     | ✅ Done        |
| 1     | Core refactor: models, detector, scanner | 🔄 In progress |
| 2     | Complete CLI + first PyPI release        | ⏳ Pending     |
| 3     | TUI (Textual)                            | ⏳ Pending     |
| 4     | GUI cross-platform                       | ⏳ Pending     |
| 5     | Advanced features + AI integration       | 🔮 Future      |

See [`docs/ROADMAP.md`](docs/ROADMAP.md) for full details.

---

## Development

### Requirements

- Python 3.11+
- [uv](https://docs.astral.sh/uv/)

### Setup

```bash
git clone https://github.com/acdeveloper-sci/envscout.git
cd envscout
uv sync --dev
```

### Run tests

```bash
uv run pytest
```

### Lint and type check

```bash
uv run ruff check envscout/
uv run ruff format envscout/
uv run mypy envscout/
```

---

## Project Structure

```
envscout/
├── envscout/
│   ├── core/          # Scanner engine — no UI dependencies
│   ├── interfaces/
│   │   ├── cli/       # Typer CLI
│   │   ├── tui/       # Textual TUI (planned)
│   │   └── gui/       # Desktop GUI (planned)
│   └── utils/         # Profiler, platform helpers
├── tests/
├── docs/
└── pyproject.toml
```

---

## Contributing

Contributions are welcome. Please read the guidelines before opening a PR:

- All code and documentation must be written in **English**
- Follow the code quality rules in [`docs/PYTHON_GUIDELINES.md`](docs/PYTHON_GUIDELINES.md)
- Run the full check before submitting: tests, mypy, ruff
- See [`docs/CONTEXT.md`](docs/CONTEXT.md) for full project context

---

## License

MIT License — see [`LICENSE`](LICENSE) for details.

---

## Author

**Adolfo J. Cardozo S.**
[ACAI — Advanced Computing & Artificial Intelligence](https://github.com/acdeveloper-sci)