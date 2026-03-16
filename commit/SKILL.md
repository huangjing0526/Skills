---
name: commit
description: Auto-generate commit message and commit changes
user-invocable: true
---

You are handling a git commit. Follow these steps:

## Step 1: Review changes
- Run `git status` and `git diff` to understand all changes
- Group changes by area: frontend, backend, database, config, etc.

## Step 2: Generate commit message
Format: `<type>(<scope>): <description>`

Types: feat, fix, refactor, style, docs, test, chore, perf
Scope: frontend, backend, db, config, etc.

Examples:
- `feat(frontend): add user list page with search and pagination`
- `fix(backend): handle null values in order calculation`

If changes span multiple areas, use the most significant one as scope.

## Step 3: Stage and commit
- Stage relevant files (avoid .env, node_modules, etc.)
- Create the commit with the generated message
- Show the result

If $ARGUMENTS is provided, use it as additional context for the commit message.
