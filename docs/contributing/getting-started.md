# Contributing to EnvScout

!!! note "Work in progress"
    This page will be completed in Phase 2.

## Requirements

- Python 3.11+
- [uv](https://docs.astral.sh/uv/)
- Git

## Setup

```bash
git clone https://github.com/acdeveloper-sci/envscout.git
cd envscout
uv sync --dev
```

## Run tests

```bash
uv run pytest
```

## Lint and type check

```bash
uv run ruff check envscout/
uv run ruff format envscout/
uv run mypy envscout/
```

## Submitting changes

- Branch from `dev`
- Follow the code style guidelines
- Ensure all checks pass before opening a PR
- Write clear commit messages (imperative mood: "Add", "Fix", "Refactor")