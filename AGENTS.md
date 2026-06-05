# AGENTS.md

Guidance for future coding agents working in this repository.

## Project Shape

- This is a Python Jupyter notebook project for AI history examples.
- Treat the repository as notebook-first, not as an installable Python package.
- Keep `pyproject.toml` configured for environment management with `[tool.poetry] package-mode = false`.
- Current notebook sources live under `notebooks/`.
- `poetry.lock` is committed and should stay in sync with `pyproject.toml`.

## Setup

Use Poetry for the project environment:

```sh
poetry install
```

Launch JupyterLab through Poetry:

```sh
poetry run jupyter lab
```

Run Python scripts through Poetry when possible:

```sh
poetry run python notebooks/fuzzy_logic_plot.py
```

## Dependency Changes

- Add runtime notebook dependencies to the `[project] dependencies` list in `pyproject.toml`.
- After changing dependencies, update `poetry.lock`.
- If `poetry lock` fails because Poetry tries to write to an unwritable user cache, use:

```sh
POETRY_CACHE_DIR=/private/tmp/poetry-cache POETRY_VIRTUALENVS_IN_PROJECT=true poetry lock
```

- Verify Poetry metadata and lock consistency with:

```sh
poetry check --lock
```

## Notebook Work

- Avoid rewriting whole `.ipynb` files unless the notebook content genuinely changed.
- Keep generated checkpoint files out of commits; `.ipynb_checkpoints/` is ignored.
- Keep notebook helper code small and local unless a repeated pattern clearly needs extraction.
- If adding plots or deterministic examples, prefer reproducible code cells and checked-in helper scripts over hidden manual state.

## Git Hygiene

- Before editing, check `git status --short` and preserve unrelated user changes.
- Do not delete or revert existing notebook edits unless the user explicitly asks.
- Keep changes scoped; this repo is intentionally small.
