# Dev-Orchestration-Assistant

A Codex skill bundle for orchestrating software delivery across three main application classes:

- desktop software
- mobile software
- web software

It is designed for a workflow where the spec is confirmed first, then Codex continues autonomously through:

- design
- implementation planning
- implementation
- testing and verification
- packaging
- garbage cleanup

## Included Skills

This repository contains four skills:

1. `dev-orchestration-assistant`
2. `development-workflow-router`
3. `desktop-software-delivery`
4. `mobile-software-delivery`
5. `web-software-delivery`

## What The Bundle Does

The top-level orchestration skill routes software work by runtime surface and delivery model.

- desktop requests go to the desktop delivery skill
- mobile requests go to the mobile delivery skill
- web requests go to the web delivery skill

The workflow router skill adds Chinese command-based stage routing for broader engineering work.

Each platform delivery skill then drives the project through the full delivery loop after spec approval.

## Install

Copy the included skill folders into your local Codex skills directory.

Typical Windows location:

```text
C:\Users\<you>\.codex\skills
```

After copying, your skills directory should contain:

```text
.codex\skills\
  dev-orchestration-assistant\
  development-workflow-router\
  desktop-software-delivery\
  mobile-software-delivery\
  web-software-delivery\
```

## Recommended Usage

### Desktop

```text
桌面开发：这个项目的 spec 已确认。请自主完成后续设计、实现、测试、打包和清理。
```

### Mobile

```text
移动开发：这个项目的 spec 已确认。请自主完成后续设计、实现、测试、打包和清理。
```

### Web

```text
网页开发：这个项目的 spec 已确认。请自主完成后续设计、实现、测试、打包和清理。
```

### Generic software request

```text
软件编排：我要做一个软件产品，请先判断应该走桌面、移动还是 Web 链路，再给出后续推进方式。
```

### Stage-based Chinese development commands

```text
需求分析：我要做一个中小商家库存管理系统，先帮我明确范围、约束、验收标准和非目标。
```

```text
规划：基于现有 spec，把 MVP 拆成按顺序执行的任务，并标明每一步怎么验证。
```

```text
做新功能：在当前项目里实现库存预警功能，按小步递进方式完成并在每步后验证。
```

## Notes

- The skill bundle assumes you already have supporting implementation skills available in your Codex environment, such as planning, implementation, testing, review, and cleanup skills.
- Packaging still pauses when signing credentials, store accounts, or deployment secrets are required and unavailable.
