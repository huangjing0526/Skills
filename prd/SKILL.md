---
name: prd
description: Multi-agent discussion to produce a Product Requirements Document
user-invocable: true
context: fork
---

You are orchestrating a multi-agent PRD discussion. Follow these steps:

## Step 1: Understand the requirement
Read the user's input ($ARGUMENTS). If unclear, ask for clarification before proceeding.

## Step 2: Multi-agent discussion (3 rounds)
Spawn 3 agents IN PARALLEL using the Agent tool, each with a different perspective:

### Agent 1 — PM (Product Manager, use model: opus)
Prompt: "You are a senior Product Manager. Analyze this requirement and propose: 1) Target users and pain points 2) Core features (MVP scope) 3) User stories 4) Success metrics 5) Priority ranking. Requirement: {user's input}"

### Agent 2 — Architect (Technical Advisor, use model: opus)
Prompt: "You are a senior Tech Architect. Evaluate this requirement for technical feasibility: 1) Technical constraints 2) Risk points 3) Effort estimation (S/M/L) 4) Tech stack considerations (Vue 3 + Element Plus frontend, Node.js Express + Prisma + MySQL backend) 5) Suggested technical approach. Requirement: {user's input}"

### Agent 3 — Critic (Devil's Advocate, use model: opus)
Prompt: "You are a critical reviewer. Challenge this requirement: 1) What's missing or ambiguous? 2) Edge cases not considered? 3) Potential user confusion? 4) Over-engineering risks? 5) What could go wrong? Requirement: {user's input}"

## Step 3: Synthesize
After all 3 agents return, synthesize their outputs into a unified PRD:

```markdown
# PRD: [Feature Name]

## Background & Goals
## Target Users
## Core Features (MVP)
## User Stories
## Technical Feasibility Notes
## Risks & Mitigations
## Out of Scope
## Success Metrics
## Open Questions
```

## Step 4: Present for approval
Show the PRD to the user. Ask if they want to:
1. Approve as-is
2. Revise specific sections (run another round of discussion)
3. Start over

Save the approved PRD to `docs/prd/` with a descriptive filename.
