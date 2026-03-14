# M0 CONTEXT

## Milestone

- Milestone: `M0`
- Theme: 建立 skills 工厂根协议与元 skill 基线

## Goal

冻结本仓库的最小控制面，使其他 GSD 项目在引入本仓库后，能通过 `AGENTS.md + .gsdt-context + skill registry` 正确发现、选择、注入 skills。

当前更精确的状态是：

- 已进入 `M0`
- 但仍处于 `bootstrap / architecture freeze` 子阶段
- 当前重点是先冻结方法论、索引层、上下文隔离与版本化规则，而不是批量铺开 skill 数量

## Must Deliver

- `GSDT-anc-using-GSDT`
- `GSDT-meta-GSD-skill-creator`
- `GSDT-anc-gsd-root-router`
- `GSDT-anc-project-researcher`
- `GSDT-anc-phase-planner`
- `GSDT-gov-online-research-official-first`
- `GSDT-gov-skill-registry-index`
- `GSDT-gov-truth-source-registry`
- `GSDT-gov-docs-governance`
- `GSDT-gov-minimal-2oss`
- `GSDT-ver-skill-eval-regression`
- naming convention
- registry seed
- Git versioning 基线
- milestone context system

## Priority

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

## In Scope

- skill factory 根协议
- using-* 一级索引
- meta skill 生产规范
- 仓库级 context system
- skill development methodology 固化
- search-first / official-first / reuse-first 策略
- milestone 进度记录与 context 持续维护机制

## Out Of Scope

- 大量 domain skill 铺开
- 高复杂度产品实现细节
- 多链与高级 2Agent 暴露

## Success Criteria

- 新 agent 只读 `AGENTS.md + .gsdt-context` 就能理解当前开发阶段
- planner 能为后续消费方项目稳定输出注入规则
- skill 不再依赖目录结构被发现
- M0 的方法论在跨 session / 跨 agent 下不丢失

## Progress Snapshot

- `GSDT-anc-using-GSDT`: draft 已创建
- `GSDT-meta-GSD-skill-creator`: draft 已创建
- `skill registry seed`: 已落地为 `skills/registry.yaml`
- `milestone context system`: 已建立 `.gsdt-context`
- `M0 skill list reprioritization`: 已确认，已前移 registry / truth-source / research policy
