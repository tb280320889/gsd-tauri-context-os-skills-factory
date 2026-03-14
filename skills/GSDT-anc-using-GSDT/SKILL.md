---
name: GSDT-anc-using-GSDT
description: 主介绍与主编排 skill，指导各类 agent 如何发现、理解、选择并使用本仓库中的其他 skills。
skill_version: 0.1.0
status: draft
---

# 角色定位 / Intent

`GSDT-anc-using-GSDT` 是本仓库的主介绍与主编排 skill。

它负责告诉 agent：

- 这个仓库是什么
- 应该何时使用这个仓库
- 如何发现 skill
- 如何选择 skill
- 如何让消费方项目的 planner 把 skill 注入其当前 phase 文档
- 如何通过 `using-*` 建立一级与二级索引
- 如何在执行阶段只消费最小 skill 闭包

它不替代消费方项目的 phase 文档，也不替代具体领域 skill。

# Trigger

在以下场景应优先加载或引用：

- agent 第一次接触本 skill 仓库
- planner 需要理解本仓库的 skill 选择与注入规则
- executor / debugger / verifier 需要确认自己应消费哪些 skills
- 需要解释本仓库的 naming / registry / versioning / injection rules
- 需要解释 `using-*` skill 如何作为索引层工作

# Applicable Roles

- planner
- project-researcher
- executor
- debugger
- verifier

# Scope

本 skill 负责：

- 解释本仓库的使用方法与边界
- 强化 `name-and-registry driven` 的发现原则
- 强化 `planner-led injection` 的注入原则
- 强化消费方项目 context docs 的优先级与渐进式披露原则
- 指导 agent 正确衔接 `GSDT-meta-GSD-skill-creator` 与后续正式 skill
- 指导 agent 通过仓库级 `using-*` 与领域级 `using-xxx-*` 快速定位 skill

本 skill 不负责：

- 替代具体 `GSDT-dom-*` skill 提供领域实现细节
- 替代 `GSDT-meta-GSD-skill-creator` 生产新 skill
- 替代 phase 文档做最终项目真值判断

# Core Understanding

本仓库是一个 `Context OS Skill Factory`，不是普通文档仓，也不是简单 prompt 集合。

它服务的对象主要是：

- planner
- researcher
- executor / debugger / verifier
- 模板仓 / 产品仓 / GSD Application Factory 流水线

它的核心机制是：

1. 在 `AGENTS.md` 中硬性让 planner 知道本 skill 仓库的存在与规则
2. planner 根据消费方项目当前 phase 的目标，选择合适的 skill 闭包
3. planner 把结果写入消费方项目的 phase 文档
4. 其他 agent 只消费 phase 文档中的 injected skill set

# Discovery Rules

- 发现 skill 时，优先依据 `skill_name` 与 registry metadata
- 正式命名格式为：`GSDT-<family>-<domain>-<capability>[-<variant>]`
- 不得通过目录结构推断 skill 语义
- `git_path` 只用于定位，不用于决定优先级

# Selection Rules

planner 在一个 phase 中选择 skill 时，应遵循：

1. 先读取消费方项目当前 phase 目标、约束、边界、版本批次
2. 判断本轮 `primary domain`
3. 选择 `1` 个主 `GSDT-dom-*` skill
4. 补充 `0-N` 个 `GSDT-nbr-*` / `GSDT-gov-*` / `GSDT-ver-*` / `GSDT-adp-*`
5. 记录显式排除项，避免上下文膨胀

phase 是 `small-batch iteration unit`，不是 domain 分类单位。

# Priority Rules

上下文优先级必须严格遵守：

1. 消费方项目当前 phase / accepted TRD-like / ADR / contracts
2. planner 注入到当前 phase 文档中的 skill 闭包
3. `GSDT-anc-*` 类说明与路由 skill

# Output Contract

当本 skill 被用于指导 planner 或其他 agent 时，最低应产出以下确认信息：

- `Current Phase Goal`
- `Selected Primary Domain Skill`
- `Selected Neighbor Skills`
- `Excluded Skills And Reasons`
- `Output Contract`
- `Verification Contract`
- `Handoff Notes`

# Boundary

- 不得把整仓 skill 全量注入到一个 phase
- 不得让 executor / debugger / verifier 自行扩展 skill 集合
- 不得让目录结构替代命名规则与 registry
- 不得让 root-like skill 覆盖消费方项目真值

# Neighbor Skills And Handoff

- 当需要创建或重构 skill 时，handoff 给 `GSDT-meta-GSD-skill-creator`
- 当需要规划 phase 注入时，handoff 给 `GSDT-anc-phase-planner`
- 当需要项目前置研究时，handoff 给 `GSDT-anc-project-researcher`
- 当需要具体领域执行时，handoff 给相应 `GSDT-dom-*`

# Versioning

- 当前版本：`0.1.0`
- 当前状态：`draft`
- 后续应通过真实 planner 注入案例反复打磨

# Lifecycle

- `draft`: 建立仓库的主介绍与主编排说明
- `experimental`: 已用于部分项目接入与注入测试
- `stable`: 已支撑多轮 phase 注入且规则稳定
- `deprecated`: 被新的仓库使用说明协议替代
- `archived`: 历史保留
