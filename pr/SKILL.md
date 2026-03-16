---
name: pr
description: Create a pull request with auto-generated description
user-invocable: true
---

You are creating a pull request. Follow these steps:

## Step 1: Analyze changes
- Run `git log main..HEAD --oneline` (or appropriate base branch) to see all commits
- Run `git diff main...HEAD --stat` to see changed files
- Read key changed files to understand the full scope

## Step 2: Generate PR
Use `gh pr create` with:

- **Title**: Short, descriptive (under 70 chars)
- **Body**:
```markdown
## Summary
- Bullet points of what changed and why

## Changes
- Frontend: ...
- Backend: ...
- Database: ...

## Test plan
- [ ] How to test these changes

## Screenshots
(if frontend changes)
```

## Step 3: Report
Show the PR URL to the user.

If $ARGUMENTS contains a target branch or additional context, use it.
