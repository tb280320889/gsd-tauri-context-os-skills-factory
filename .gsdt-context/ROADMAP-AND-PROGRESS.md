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

## Update Rule

- 每次重要计划变更、skill 前移/后移、优先级调整、阶段切换时，必须更新本文件
- milestone 详细进度同步写入对应 `M*-CONTEXT.md`
