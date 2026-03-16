---
name: plan
description: Multi-agent technical planning with architecture discussion
user-invocable: true
context: fork
---

You are orchestrating a multi-agent technical planning session. Follow these steps:

## Step 1: Gather context
Read the relevant PRD from `docs/prd/` if it exists. Read $ARGUMENTS for additional context. Scan the current codebase structure to understand what exists.

## Step 2: Multi-agent discussion (spawn IN PARALLEL, model: opus for all)

### Agent 1 — Architect
Prompt: "You are a senior architect. Based on this PRD/requirement, design the implementation plan:
1) Component/module breakdown
2) API design (RESTful endpoints)
3) Database schema changes (Prisma models, MySQL)
4) Frontend pages and components (Vue 3 + Element Plus)
5) State management (Pinia stores)
6) File structure for new code
7) Implementation order and dependencies
Tech stack: Vue 3.4+ (Composition API, script setup), Vite 5, Element Plus, Vue Router 4, Pinia, vue-i18n | Node.js Express 4.x, Prisma ORM, MySQL
PRD/Requirement: {context}"

### Agent 2 — PM
Prompt: "You are a PM reviewing a technical plan. Check:
1) Does the plan fully cover all PRD requirements?
2) Is anything over-engineered for MVP?
3) Is the user experience well thought out?
4) Are there missing user flows?
PRD/Requirement: {context}"

### Agent 3 — Critic
Prompt: "You are a technical critic. Challenge the plan:
1) Security vulnerabilities?
2) Performance bottlenecks?
3) Scalability concerns?
4) Error handling gaps?
5) Is the scope too large? What can be cut?
PRD/Requirement: {context}"

## Step 3: Synthesize into implementation plan

```markdown
# Implementation Plan: [Feature Name]

## Overview
## Architecture Diagram (text)
## Database Changes
  - New/modified Prisma models
  - Migration notes
## API Endpoints
  | Method | Path | Description |
## Frontend Changes
  - New pages/routes
  - New components
  - Store changes
## Backend Changes
  - New routes/controllers
  - Service layer changes
## Task Breakdown
  - [ ] Task 1 (frontend/backend, size S/M/L)
  - [ ] Task 2 ...
## Implementation Order
## Risks & Mitigations
```

## Step 4: Present for approval
Show the plan. Ask user to approve, revise, or restart.
Save approved plan to `docs/plan/` with a descriptive filename.
