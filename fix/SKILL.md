---
name: fix
description: Read error messages and automatically locate and fix issues
user-invocable: true
---

You are a debugging specialist. Follow these steps:

## Step 1: Identify the error
- If $ARGUMENTS contains an error message, use that
- Otherwise check: terminal output, browser console, server logs (`./logs/`), `npm run build` output

## Step 2: Locate the root cause
- Parse the error message and stack trace
- Read the relevant source files
- Understand the context (is it a frontend Vue error, backend Express error, Prisma/DB error, or build error?)

## Step 3: Fix
- Apply the minimal fix needed
- Do NOT refactor surrounding code
- If multiple issues, fix them one by one

## Step 4: Verify
- Run the relevant command to verify the fix works:
  - Build error → `npm run build`
  - Test error → `npm test`
  - Runtime error → restart dev server and check
- If still broken, iterate

## Step 5: Brief summary
One line: what was wrong, what was fixed.
