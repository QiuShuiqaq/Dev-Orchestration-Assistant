# Fixed Development Commands

Use this file when the user wants a standard way to start software, web, or app development work in Chinese. These commands are designed to keep one clear stage active at a time.

## How To Use

- Put the workflow prefix at the start of the message.
- Write the business context right after the prefix.
- Add constraints like deadline, budget, team size, platform, legacy limits, and deployment environment when they matter.
- Keep one command focused on one stage. If the stage changes, start a new command.

## Core Commands

### `需求分析：`

Use when the goal is still fuzzy and the product problem is not yet well-scoped.

Template:

```text
需求分析：我要做一个[产品/功能]，面向[目标用户]，核心目标是[业务目标]。请先帮我明确范围、关键约束、验收标准、非目标和风险。
```

### `规划：`

Use when the scope is clear enough and the next need is task breakdown.

Template:

```text
规划：基于这个需求/现有项目，帮我拆成按顺序执行的任务，给出依赖关系、每步产出和验证方式。
```

### `技术选型：`

Use when stack choice depends on business constraints and tradeoffs.

Template:

```text
技术选型：这个项目要解决[业务场景]，约束是[预算/周期/团队能力/平台要求]。请先比较方案，再推荐最合适的技术栈和理由。
```

### `数据库设计：`

Use when business entities and query patterns are becoming clear.

Template:

```text
数据库设计：这个系统包含[核心实体]，主要操作是[关键流程]，查询重点是[高频查询]。请帮我设计表结构、关系、索引和迁移注意点。
```

### `设计接口：`

Use when modules or services need stable boundaries.

Template:

```text
设计接口：请为[模块/服务]设计接口，覆盖[核心操作]，并说明请求结构、返回结构、错误处理、版本兼容和边界约束。
```

### `做新功能：`

Use when the work is ready to implement.

Template:

```text
做新功能：在当前项目里实现[功能名]。请按小步递进方式完成，先确认相关代码结构，再分 slice 实现并在每步后验证。
```

### `调试：`

Use when behavior is wrong or tests/builds fail.

Template:

```text
调试：[现象描述]。已知信息有[报错/日志/复现步骤]。请先定位根因，再给最小修复方案，并补上回归验证。
```

### `UI验收：`

Use when a page or flow needs browser-based verification.

Template:

```text
UI验收：检查[页面/流程]在[桌面端/移动端]的交互、布局、可访问性和关键路径是否正常，优先给出真实问题和复现步骤。
```

### `性能优化：`

Use only when there is evidence of slowness or a performance budget.

Template:

```text
性能优化：[页面/接口/任务]存在[慢的现象或指标]。请先测量和定位瓶颈，再给出可验证的优化方案和前后对比。
```

### `上线发布：`

Use before production rollout.

Template:

```text
上线发布：这次要发布[功能/版本]，影响范围是[用户/模块]。请帮我整理发布清单、监控点、灰度方案和回滚方案。
```

### `代码审查：`

Use after implementation and before merge.

Template:

```text
代码审查：请 review 这次改动，重点看正确性、可维护性、边界条件、潜在回归和测试覆盖。
```

### `修CI：`

Use when GitHub Actions or PR checks fail.

Template:

```text
修CI：这条 GitHub Actions/PR check 挂了。请先看失败点、总结根因，再给出修复方案。
```

### `回评审：`

Use when addressing PR comments.

Template:

```text
回评审：帮我处理这个 PR 的 review comments，按问题分组，逐条落实修改并总结回复思路。
```

### `复盘：`

Use after an important change, incident, launch, or design decision.

Template:

```text
复盘：请把这次[项目/改造/事故/发布]的背景、关键决策、取舍、结果、遗留问题和后续动作整理下来。
```

### `自动化脚本：`

Use when repetitive engineering work should become a reusable command.

Template:

```text
自动化脚本：把[重复任务]做成一个可复用的 CLI/脚本，要求输入输出清晰、便于集成，并说明如何验证。
```
