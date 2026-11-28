---
name: commit-message
description: Suggest a Conventional Commit type and description for the current changes. Use when the user asks for a commit message, git message, or commit type.
---

# Commit message

1. Run `git status` and `git diff` (including untracked files) to see what changed.
2. Pick one type:
   - `feat`: new capability in src/ or the template
   - `fix`: bug fix
   - `docs`: README, CLAUDE.md, comments only
   - `build`: dependencies, Dockerfile, env.yaml, requirements files
   - `ci`: .github/workflows
   - `test`: tests only
   - `refactor`: code change with no behavior change
   - `chore`: tooling/config (e.g. .claude/, .pre-commit-config.yaml, .vscode/)
3. Write the description: lowercase, imperative ("add", not "added"), under 60 characters, no trailing period.
4. If the change touches several areas, suggest splitting the commit.
5. Output the one-line message in a code block, plus an optional body.
