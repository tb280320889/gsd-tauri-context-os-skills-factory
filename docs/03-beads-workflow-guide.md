# Beads Workflow Guide

## 1. 目的

本文件用于定义本仓库中 `bd (beads)` 的使用方式，
确保任务、依赖、阶段进度与跨 session 续接方式有统一规则。

本文件关注的是：

- beads 如何与本仓库配合
- beads 如何与 `.gsdt-context` 协同
- beads 适合跟踪什么，不适合跟踪什么

## 2. beads 在本仓库中的角色

`bd` 负责管理：

- issue / task / epic
- 依赖关系
- ready work
- 状态流转
- 跨 session 的工作项连续性

`bd` 不负责替代：

- `AGENTS.md` 的根规则
- `.gsdt-context` 中的长期真值
- milestone context 中的范围、优先级与已锁定决策
- skill 文稿本体

可以简单理解为：

- `.gsdt-context` 管“为什么、做到哪、什么规则不能忘”
- `bd` 管“接下来做什么、谁依赖谁、什么已经完成”

## 3. 本仓库的推荐 beads 用法

### 3.1 Issue 层级

推荐采用两层：

- `epic`
  - 表示一个 milestone 或一块大的持续工作
- `task`
  - 表示一个具体 skill、文档任务或治理任务

建议：

- 一个 milestone 至少一个 `epic`
- 每个正式 skill 最好对应一个 `task`
- 文档治理、registry、research policy 也可作为 `task`

### 3.2 依赖规则

优先用 `task -> task` 表达实际阻塞关系。

注意：

- `task` 不能用 `epic` 作为 blocker
- `epic` 更适合聚合与总览，不适合做精细阻塞图

## 4. 推荐工作流

### 4.1 开始新工作前

先看：

```bash
bd ready
bd list
bd show <issue-id>
```

### 4.2 创建任务

```bash
bd create --title "Draft GSDT-gov-online-research-official-first" --description "Create the policy skill for search-first / official-first / reuse-first." --type task --priority 0
```

### 4.3 开始执行

```bash
bd update <issue-id> --status in_progress
```

### 4.4 建立依赖

```bash
bd dep add <issue> <depends-on>
```

含义：

- `<issue>` 依赖 `<depends-on>`
- `<depends-on>` 完成后，`<issue>` 才 ready

### 4.5 完成工作

```bash
bd close <issue-id> --reason "Completed and reflected in context/docs"
```

## 5. 和 `.gsdt-context` 的协同规则

这是本仓库里最重要的纪律之一：

- `bd` 里创建了任务，不代表 context 已更新
- context 更新了，不代表 `bd` 的 issue 已同步关闭

因此每次重要工作至少要做两件事：

1. 更新 `bd` issue 状态
2. 更新对应的 `.gsdt-context` / roadmap / milestone docs

尤其以下信息，不能只留在 beads issue 中：

- 方法论变化
- skill 前移/后移
- milestone 范围变化
- 优先级变化
- 当前阶段进度快照

这些必须回写到：

- `.gsdt-context/GLOBAL-CONTEXT.md`
- `.gsdt-context/ROADMAP-AND-PROGRESS.md`
- `.gsdt-context/milestones/<M>-CONTEXT.md`

## 6. 当前已验证可用的常用命令

### 6.1 状态与健康检查

```bash
bd doctor
bd context
bd status
bd ready
bd list
```

### 6.2 创建与更新

```bash
bd create --title "..." --description "..." --type task --priority 1
bd create --title "..." --description "..." --type epic --priority 0
bd update <issue-id> --status in_progress
bd close <issue-id> --reason "..."
```

### 6.3 依赖与辅助

```bash
bd dep add <issue> <depends-on>
bd show <issue-id>
bd quickstart
bd prime
bd onboard
```

## 7. 当前仓库中的 beads 使用建议

建议用 beads 跟踪：

- M0 / M1 / M2 等 milestone epic
- 每个正式 skill 的创建任务
- registry / truth-source / docs governance 任务
- 验证与回归任务

不建议只依赖 beads 保存：

- 长期方法论
- context priority
- 仓库定位
- 已冻结的架构决策

这些都应写回 `.gsdt-context` 与核心文档。

## 8. Session 结束前检查

在结束一个工作 session 前，建议检查：

```bash
bd list
bd ready
bd close <done-issue-id>
git status
```

并确认：

- beads issue 状态与真实进度一致
- 重要决策已回写到 context docs
- Git 已提交并推送

## 9. 当前已存在的 beads 事项

截至当前阶段，已存在：

- M0 bootstrap epic
- beads workflow adoption task
- beads workflow documentation task

后续应继续把 M0 skill list 拆成正式 beads tasks。
