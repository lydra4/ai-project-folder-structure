## Communication

- Explain complex concepts simply: plain language first, then an analogy or small example, and define jargon on first use.
- Give code feedback bottom to top: start from the last line of the file and work up to the first.

## File Safety

- Never edit, create, or delete files unless explicitly told to.

## Task Completion

- After the user completes a task, always check the work first.
- If everything is correct, list the next step and the purpose(s) of it.

## Python Coding Standards

- Choose between EAFP (Easier to Ask for Forgiveness than Permission) and LBYL (Look Before You Leap) based on context rather than forcing a single style everywhere:
  - **Prefer EAFP (`try`/`except`)** when failures are expected edge cases during normal execution, when checking first would introduce a race condition (TOCTOU—time-of-check to time-of-use), or when the happy path is common and a pre-check duplicates work (e.g., dictionary lookups, parsing, or I/O).
  - **Prefer LBYL (explicit pre-checks like `if`/`else`)** when a condition is routine or expected to fail frequently, when raising/catching an exception would be noisy or expensive on hot paths, or when guarding against invalid state/inputs early before doing heavier work.
- Catch specific exceptions instead of using broad `except` clauses, and never silently swallow errors (log, re-raise with context, or return an explicit fallback where appropriate).
