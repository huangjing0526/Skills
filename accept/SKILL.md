---
name: accept
description: Multi-agent acceptance review — verify implementation matches PRD
user-invocable: true
context: fork
---

You are orchestrating a multi-agent acceptance review. This happens after testing passes, before commit.

## Step 1: Gather context
- Read the relevant PRD from `docs/prd/`
- Read the implementation plan from `docs/plan/`
- Run `git diff main...HEAD` (or appropriate base) to see all changes
- If $ARGUMENTS specifies a feature, focus on that

## Step 2: Multi-agent review (spawn IN PARALLEL)

### Agent 1 — PM Acceptance (model: opus)
Prompt: "You are a PM doing acceptance review. Compare the implementation against the PRD:
1) Are all user stories implemented?
2) Does the UX match expectations?
3) Any missing features?
4) Any features that deviate from the PRD?
PRD: {prd content}
Changes: {diff summary}"

### Agent 2 — Code Reviewer (model: opus)
Prompt: "You are a senior code reviewer. Review these changes for:
1) Code quality and readability
2) Security issues (SQL injection, XSS, auth bypasses)
3) Performance concerns
4) Error handling completeness
5) API design consistency
Tech stack: Vue 3 + Element Plus, Express + Prisma + MySQL
Changes: {diff content}"

### Agent 3 — Critic (model: opus)
Prompt: "You are a QA critic. Challenge the implementation:
1) Edge cases not handled?
2) What happens with bad/missing input?
3) Concurrent access issues?
4) i18n coverage (vue-i18n)?
5) What would break in production?
Changes: {diff content}"

## Step 3: Synthesize verdict

```markdown
# Acceptance Review: [Feature]

## PM Verdict: PASS / FAIL
- Coverage: X/Y user stories implemented
- Issues: ...

## Code Quality: PASS / FAIL
- Issues: ...

## QA Concerns
- Issues: ...

## Overall: APPROVED / NEEDS REVISION
## Action Items (if any)
- [ ] ...
```

## Step 4: Present to user
If APPROVED: suggest proceeding to `/commit`
If NEEDS REVISION: list action items, offer to fix them
