# Architecture

!!! note "Work in progress"
    This page will be completed in Phase 1.

## Overview

EnvScout follows a strict **core/interfaces separation**:

- `core/` — scanner engine with zero UI dependencies
- `interfaces/` — CLI, TUI (planned), GUI (planned)
- `utils/` — shared utilities (profiler, platform helpers)

**Key rule:** `core/` never imports from `interfaces/`.
All interfaces consume core — never the reverse.

## Project Structure

```
envscout/
├── envscout/
│   ├── core/           # Engine — no UI dependencies
│   │   ├── scanner.py
│   │   ├── detector.py
│   │   ├── inspector.py
│   │   ├── exporter.py
│   │   └── models.py
│   ├── interfaces/
│   │   ├── cli/
│   │   ├── tui/        # Planned
│   │   └── gui/        # Planned
│   └── utils/
│       ├── profiler.py
│       └── platform.py
└── tests/
```