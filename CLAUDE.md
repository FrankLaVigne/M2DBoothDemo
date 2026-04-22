# Project notes for Claude

## Workflow

- Solo developer project. No PRs, no feature branches.
- When the user asks to "commit and push" (or finishes a task that warrants it),
  commit and push directly to `main`.
- Skip the "create a branch, open a PR" dance unless the user explicitly asks
  for it.

## Writing style

- **No em dashes anywhere in the repo** (not in `index.html` copy, speaker
  notes, README, commit messages, or PR bodies). Use a colon, comma,
  semicolon, or parentheses depending on context.
- This applies to both user-visible text (stage storylines, substories,
  headlines, details, panel copy, stat chips, tooltips) and internal docs.
- Before committing, grep for `—` across `*.html` and `*.md` and replace
  any hits with the grammatically correct alternative.
