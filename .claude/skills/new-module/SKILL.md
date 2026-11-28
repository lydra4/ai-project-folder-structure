---
name: new-module
description: Create a new Python module in src/ with a matching test in tests/, following this project's conventions. Use when the user asks to add, create, or write a new module, function, class, or feature in src/.
---

# New module

Reference examples: `src/utils/general_utils.py` and `tests/test_general_utils.py`. Match their style.

## Module (`src/<area>/<module>.py`)

1. Place it in an existing `src/<area>/` folder if one fits; otherwise create the folder with an empty `__init__.py`.
2. Add `logger = logging.getLogger(__name__)` at module level. Use the logger, never `print`.
3. Type-hint every parameter and return value (mypy `disallow_untyped_defs` is on). Use modern syntax: `str | PathLike`, `list[str]`.
4. Give parameters sensible defaults where appropriate (e.g. paths relative to repo root like `./config/...`).
5. Error handling per CLAUDE.md: choose EAFP or LBYL by context, catch specific exceptions, and on fallback log why.
6. Read settings from Hydra configs in `config/` rather than hard-coding values.
7. Keep lines at or under 120 characters.

## Test (`tests/test_<module>.py`)

1. Import with `from src.<area>.<module> import <name>`.
2. Use pytest fixtures with `tmp_path` and `monkeypatch`; never touch real files outside `tmp_path`.
3. Use `unittest.mock.patch` for external calls.
4. Cover: the happy path, each `except` branch, defaults, and edge cases. Use `@pytest.mark.parametrize` for multiple inputs.
5. Use `caplog` to assert on important log messages.
6. Name tests `test_<expected_behaviour>` and annotate them `-> None`.

## Finish

1. Run `make check` and `make test`; fix failures before reporting.
2. Report what was created and show the coverage line for the new module.
