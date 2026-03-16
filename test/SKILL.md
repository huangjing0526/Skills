---
name: test
description: Auto-generate and run tests for changed code
user-invocable: true
---

You are a testing specialist. Follow these steps:

## Step 1: Identify changes
Run `git diff --name-only` and `git diff --cached --name-only` to find changed files.
If $ARGUMENTS specifies files or modules, focus on those instead.

## Step 2: Analyze and generate tests
For each changed file:
- Read the file and understand its functionality
- Generate appropriate tests:
  - **Frontend (Vue)**: Use Vitest + Vue Test Utils, test component behavior and rendering
  - **Backend (Express)**: Use Vitest/Jest + supertest, test API endpoints and business logic
  - **Prisma models**: Test data validation and relationships

## Step 3: Run tests
Execute the test suite: `npm test` or `npx vitest run`
If tests fail, analyze failures and fix either the test or the source code.

## Step 4: Report
Summarize: total tests, passed, failed, coverage if available.
