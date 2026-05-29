---
name: development-workflow-router
description: Routes long-term software, web, and app development work by Chinese workflow prefixes. Use when the user starts a request with phrases like "桌面开发：", "移动开发：", "网页开发：", "需求分析：", "规划：", "技术选型：", "数据库设计：", "设计接口：", "做新功能：", "调试：", "UI验收：", "性能优化：", "上线发布：", "代码审查：", "修CI：", "回评审：" , "复盘：" or "自动化脚本：". Use this skill to select exactly one primary specialist skill for the current stage, avoid multi-skill interference, and keep business goals ahead of technology choices.
---

# Development Workflow Router

## Overview

This skill is a routing policy for long-term product development. Its job is to map the user's current development stage to one primary specialist skill, keep context clean, and prevent multiple skills from competing for the same task.

For reusable Chinese prompt patterns and default wording, read `references/fixed-development-commands.md` when the user wants a command cheat sheet, prompt templates, or a standard way to start tasks.

## Core Rules

1. Treat the text before the first full-width or half-width colon as the workflow prefix.
2. Choose exactly one primary specialist skill for the current task.
3. Only add a second skill when it is clearly a post-check or utility, not a co-lead.
4. Do not let two implementation-planning skills or two review skills lead the same task.
5. Keep business constraints first. Do not force a technology stack before clarifying the product goal, scope, budget, timeline, and team constraints.

## Prefix Routing

### `桌面开发：`

- Primary skill: `desktop-software-delivery`
- Output: desktop subtype, stack direction, platform workflow, packaging expectations, and autonomous delivery path when the spec is approved.
- Guardrail: if the runtime surface is still unclear, clarify desktop assumptions before implementation.

### `移动开发：`

- Primary skill: `mobile-software-delivery`
- Output: mobile subtype, stack direction, platform workflow, packaging expectations, and autonomous delivery path when the spec is approved.
- Guardrail: if the target platform is still unclear, clarify iOS, Android, mini program, or other mobile assumptions before implementation.

### `网页开发：`

- Primary skill: `web-software-delivery`
- Output: web subtype, stack direction, platform workflow, packaging expectations, and autonomous delivery path when the spec is approved.
- Guardrail: if the delivery model is still unclear, clarify MPA, SPA, PWA, or embedded web assumptions before implementation.

### `需求分析：`

- Primary flow: use `define-goal` if the objective is still fuzzy, then hand off to `spec-driven-development`.
- Output: problem statement, users, scope, constraints, acceptance criteria, non-goals, and a draft spec.
- Guardrail: do not start coding from this prefix unless the user explicitly asks to skip analysis.

### `规划：`

- Primary skill: `planning-and-task-breakdown`
- Output: ordered task list, dependencies, verification steps, and implementation slices.
- Guardrail: if there is no clear spec yet, redirect to `需求分析：`.

### `技术选型：`

- Primary flow: keep this router in charge first.
- Evaluate business scenario, traffic, complexity, hiring cost, maintenance cost, delivery speed, platform coverage, and deployment constraints.
- Only after tradeoffs are clear should you recommend a stack and move to a specialist skill.
- Guardrail: do not anchor on a stack just because it is popular.

### `数据库设计：`

- Primary skill: `api-and-interface-design`
- Output: core entities, table boundaries, relationships, indexes, transaction constraints, migration concerns, and data access contracts.
- Guardrail: design the schema around business invariants and query patterns, not around ORM convenience alone.

### `设计接口：`

- Primary skill: `api-and-interface-design`
- Output: API contract, module boundaries, data shapes, versioning concerns, and misuse-resistant interfaces.

### `做新功能：`

- Primary skill: `incremental-implementation`
- Output: thin vertical slices with code, tests, and verification after each slice.
- Guardrail: if requirements or boundaries are unclear, pause and redirect to `需求分析：` or `规划：`.

### `调试：`

- Primary skill: `debugging-and-error-recovery`
- Output: reproduced issue, preserved evidence, root cause, minimal fix, and regression coverage.
- If the problem is specifically a GitHub Actions failure, prefer `gh-fix-ci`.

### `UI验收：`

- Primary skill: `playwright`
- Optional post-check: `web-design-guidelines` for UI and accessibility review, or `react-best-practices` when the codebase is React or Next.js.
- Output: real browser verification, failed steps, screenshots if useful, and concrete UI findings.
- Guardrail: do not use both optional post-check skills unless the user explicitly asks for both.

### `性能优化：`

- Primary skill: `performance-optimization`
- Output: baseline metrics, suspected bottleneck, proof from measurement, targeted fix, and before/after verification.
- Guardrail: do not optimize first and measure later.

### `上线发布：`

- Primary skill: `shipping-and-launch`
- Optional post-check: `code-review-and-quality` or `security-best-practices` only if the release risk is high and the user asks for an extra gate.
- Output: release checklist, rollout plan, monitoring plan, rollback path, and launch criteria.
- Guardrail: prefer observable and reversible releases over big-bang deploys.

### `代码审查：`

- Primary skill: `code-review-and-quality`
- Optional post-check: `security-best-practices` when the user asks for a security-focused pass or the change is sensitive.
- Output: findings first, then open questions, then a brief summary.

### `修CI：`

- Primary skill: `gh-fix-ci`
- Output: failing check summary, root cause hypothesis, fix plan, and implementation after confirmation if the skill requires it.

### `回评审：`

- Primary skill: `gh-address-comments`
- Output: grouped review comments, response plan, code changes, and a concise follow-up summary.

### `复盘：`

- Primary skill: `documentation-and-adrs`
- Output: what changed, why it changed, tradeoffs, lessons learned, follow-up actions, and durable project context for future work.
- Guardrail: focus on decisions and evidence, not vague retrospective filler.

### `自动化脚本：`

- Primary skill: `cli-creator`
- Output: a reusable CLI or automation entrypoint for repetitive engineering work.

## Operating Pattern

For each routed request:

1. Confirm which stage the prefix indicates.
2. Load only the primary skill needed for that stage.
3. Work through that stage fully before switching skills.
4. If a second skill is needed, use it strictly after the primary skill as a validation or tooling pass.
5. Tell the user when the request should move to the next stage.
