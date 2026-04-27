# Changelog

All notable changes to EnvScout are documented here.

## Unreleased

### Phase 1 — Core Refactor
- Migration of scanner engine to clean architecture
- `core/models.py`: `VEnvInfo` and `ScanResult` dataclasses
- `core/detector.py`: unified venv detection
- `core/scanner.py`: three scan modes (streaming, batch, parallel)
- `utils/profiler.py`: clean cProfile decorator
- Basic test suite

---

## v0.0.1 — Phase 0 Foundation

- Project structure established
- `pyproject.toml` with uv + hatchling
- CLI skeleton with Typer + Rich
- Pre-refactor scanner functional (venv, virtualenv, conda, poetry, pipenv, tox, uv)