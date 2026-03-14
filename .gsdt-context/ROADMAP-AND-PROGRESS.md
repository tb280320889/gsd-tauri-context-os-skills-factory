# ROADMAP AND PROGRESS

## Purpose

本文件用于作为跨 session / 跨 agent 的阶段计划与进度快照，
避免重要里程碑排序、前移/后移决策、当前完成状态只停留在临时对话中。

## Current Milestone Status

- `M0`: in_progress
- `M1`: pending
- `M2`: pending
- `M3`: pending
- `M4`: pending
- `M5`: pending
- `MX`: pending

## M0 Skill Plan

### P0
- `GSDT-anc-using-GSDT`
- `GSDT-meta-GSD-skill-creator`
- `GSDT-gov-online-research-official-first`
- `GSDT-gov-skill-registry-index`

### P1
- `GSDT-anc-gsd-root-router`
- `GSDT-anc-project-researcher`
- `GSDT-anc-phase-planner`
- `GSDT-gov-truth-source-registry`

### P2
- `GSDT-gov-docs-governance`
- `GSDT-gov-minimal-2oss`
- `GSDT-ver-skill-eval-regression`

## Decisions Already Locked

- skill 命名统一为 `GSDT-<family>-<domain>-<capability>[-<variant>]`
- skill 发现方式为 `name-and-registry driven`
- 本仓库使用 `.gsdt-context`，不使用 `.planning` 作为主上下文目录
- 本仓库当前处于 skills 的设计、规划、规范与建造阶段
- `using-*` 是一级/二级索引体系的重要组成部分
- `truth-source-registry` 与 `skill-registry-index` 已从 MX 前移到 M0
- `online-research-official-first` 已从 M2 前移到 M0
- `skill-eval-regression` 已从 M1 前移到 M0

## Current Progress Snapshot

- `GSDT-anc-using-GSDT`: draft created
- `GSDT-meta-GSD-skill-creator`: draft created
- `skills/registry.yaml`: created
- `.gsdt-context`: initialized
- methodology docs: added
- beads initialized and adopted for issue tracking
- beads workflow guide added and linked from `AGENTS.md`
- M0 skill tasks have been split into beads issues with dependency links

## M0 Beads Task Snapshot

- `gsd-tauri-context-os-skills-factory-p8o`: `GSDT-gov-online-research-official-first` (P0)
- `gsd-tauri-context-os-skills-factory-t5m`: `GSDT-gov-skill-registry-index` (P0)
- `gsd-tauri-context-os-skills-factory-e04`: `GSDT-anc-gsd-root-router` (P1, depends on registry)
- `gsd-tauri-context-os-skills-factory-epf`: `GSDT-anc-project-researcher` (P1, depends on research policy)
- `gsd-tauri-context-os-skills-factory-jss`: `GSDT-anc-phase-planner` (P1, depends on registry + root-router)
- `gsd-tauri-context-os-skills-factory-k3u`: `GSDT-gov-truth-source-registry` (P1, depends on research policy)
- `gsd-tauri-context-os-skills-factory-71q`: `GSDT-gov-docs-governance` (P2, depends on root-router)
- `gsd-tauri-context-os-skills-factory-8fl`: `GSDT-ver-skill-eval-regression` (P2, depends on registry)
- `gsd-tauri-context-os-skills-factory-lp0`: `GSDT-gov-minimal-2oss` (P2, depends on docs-governance)

## Current Ready Work

- `gsd-tauri-context-os-skills-factory-p8o`
- `gsd-tauri-context-os-skills-factory-t5m`
- `gsd-tauri-context-os-skills-factory-366`

## Update Rule

- 每次重要计划变更、skill 前移/后移、优先级调整、阶段切换时，必须更新本文件
- milestone 详细进度同步写入对应 `M*-CONTEXT.md`

## Next Session Handoff Template

当你在全新 session 中唤起新的 agent 时，建议最少给出如下提示：

```text
请先按顺序阅读以下文件，再继续当前工作：
1. AGENTS.md
2. .gsdt-context/GLOBAL-CONTEXT.md
3. .gsdt-context/ROADMAP-AND-PROGRESS.md
4. .gsdt-context/milestones/M0-CONTEXT.md
5. docs/02-skill-development-methodology.md
6. docs/03-beads-workflow-guide.md

当前状态：
- 我们已经在 M0，且处于 bootstrap / architecture freeze 子阶段
- 已完成 GSDT-anc-using-GSDT 与 GSDT-meta-GSD-skill-creator 的 draft
- M0 beads tasks 已拆分，先看 bd ready
- 当前优先做的 task 是：GSDT-gov-online-research-official-first 与 GSDT-gov-skill-registry-index

要求：
- 全程使用中文
- 开始正式工作前先运行 bd ready / bd list
- 重要决策必须回写到 .gsdt-context
```

如果你想更短，也可以用这一版：

```text
请先读 AGENTS.md、.gsdt-context/GLOBAL-CONTEXT.md、.gsdt-context/ROADMAP-AND-PROGRESS.md、.gsdt-context/milestones/M0-CONTEXT.md，然后执行 bd ready。我们当前在 M0 bootstrap 阶段，优先任务是 GSDT-gov-online-research-official-first 与 GSDT-gov-skill-registry-index。重要决策必须回写 context docs。
```
