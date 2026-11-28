---
name: check-work
description: Check changes the user just made and report whether they are correct. Use when the user says "please check", "is it correct", "I made the change", or "check my work".
---

# Check work

1. Run `git status --short -uall` and `git diff` to find every changed and untracked file.
2. Validate each file by type:
   - `.py`: `ruff check`, `ruff format --check`, `mypy` on the file; `make test` if src/ or tests/ changed.
   - `.json`: `python -m json.tool <file>`.
   - `.yaml`/`.yml`: `pre-commit run check-yaml --files <file>`.
   - `.claude/skills/`: each skill is at `.claude/skills/<name>/SKILL.md` and its frontmatter `name` matches the folder.
   - `.claude/settings.json`: valid JSON with only `allow`, `ask`, `deny` under `permissions`.
3. Compare against what was agreed earlier in the conversation and flag anything missing or different.
4. Report feedback bottom to top (last line of the file first).
5. Do not edit any files; only report.
6. If correct: say so, give the next step and its purpose(s), and suggest a commit message using the `commit-message` skill.
