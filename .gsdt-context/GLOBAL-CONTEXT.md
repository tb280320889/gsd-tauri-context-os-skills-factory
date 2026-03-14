# GLOBAL CONTEXT

## Project Identity

- Project Name: `GSD + Tauri2 Context OS Skills Factory`
- Project Prefix: `GSDT`
- Project Type: `skills toolkit factory for GSD projects`
- Intended Integration Mode: `submodule / vendored toolkit`
- Primary Audience: planner / executor / debugger / verifier / skill authors

## Current Role

本仓库当前不是某个具体产品仓，也不是直接执行产品 phase 的工作目录。

本仓库当前正在做的事情是：

- skills 的设计
- skills 的规划
- skills 的规范定义
- skills 的建造

因此你和用户在本仓库中的默认角色是：

- architect
- designer
- skill system builder

## Mission

本项目的目标，是为一类 `GSD + Tauri2 跨端 App` 项目提供可复用的 skills 工具集。

这些 skills 后续会被其他 GSD 项目以 submodule / vendored toolkit 的方式引入，
再由外部项目中的 planner 按其自己的 `.planning` phase 文档进行选择与注入。

本仓库自身不把 `.planning` 作为主上下文目录，以避免与消费方项目的 GSD workflow 目录发生语义冲突。

## Long-lived Truth

- skill discovery 必须是 `name-and-registry driven`
- skill injection 必须是 `planner-led`
- 对消费方项目而言，accepted context docs / phase docs 高于 skill 文稿
- phase 是 `small-batch iteration unit`，不是 skill 一级分类
- skill 主组织维度是 `domain-first`
- 正式 skill 命名必须为 `GSDT-<family>-<domain>-<capability>[-<variant>]`
- 所有 skill 必须受 Git 管理，并具备版本可追溯性
- 文风采用中文为主、英文强调关键术语
- 本仓库必须同时支持 `using-*` 的一级与二级索引体系

## Skill Methodology

- Skill is not for replacing model intelligence; it is for activating domain excellence.
- 创建 skill 前必须优先检查：official MCP / official skill / official docs / `llms.txt` / 高质量开源实践
- 方法论遵循：`search-first`、`official-first`、`reuse-first`
- 只有在已有高质量资产无法覆盖时，才自己创造新的 skill 主体
- skill 的目标是弥补 agent 在特定领域的专精鸿沟，而不是重复模型已有的通用知识

## Context Isolation Discipline

- 每个 milestone 必须独立上下文
- 每个 phase 必须局部化，不在单一长上下文中混开发多个 milestone
- research 与 skill 落地尽量分离
- 如需在线研究，可让用户补充 web/LLM 结果，或启动独立 subagent 完成 research digest
- 主上下文只保留 research digest 与最终可执行结论，不长期保留原始搜索噪音

## Context Preservation Discipline

- 任何重要的总结、方法论、优先级调整、skill 前移/后移决策，都必须回写到长期 context docs
- milestone context 必须持续更新 `Progress Snapshot`
- 如果开发计划、范围、依赖发生变化，必须同步更新对应 milestone context 与 TRD-like 文档
- 不允许把关键决策只停留在临时对话中
- preserving context quality is a permanent rule, not a one-time cleanup action

## Skill Families

- `anc`: anchor / orchestration
- `dom`: domain
- `nbr`: neighbor
- `gov`: governance
- `meta`: meta-production
- `adp`: adapter
- `ver`: verification

## Using Skill Index Strategy

- `GSDT-anc-using-GSDT`：仓库级主介绍与主编排 skill
- 后续每个重要领域应有各自的 `using-xxx-yyy` 二层索引 skill
- `using-*` skill 的作用是帮助 agent 快速理解“某一层 skill 该怎么用”，而不是承载全部领域知识

## Required Core Skills

- `GSDT-anc-using-GSDT`
- `GSDT-meta-GSD-skill-creator`

## Context Priority In This Repository

1. 当前被接受的仓库上下文文档
2. `.gsdt-context/ROADMAP-AND-PROGRESS.md`
3. `.gsdt-context/milestones/<M>-CONTEXT.md`
4. `.gsdt-context/GLOBAL-CONTEXT.md`
5. planner 注入的 skill 闭包
6. 仓库中的其他说明文档

## Factory Discipline

- 每个 milestone 必须有独立上下文文档
- 每个 phase 设计文档必须引用所属 milestone 上下文
- planner 必须在 phase 文档中记录：选择了什么、排除了什么、为什么
- executor / debugger / verifier 默认不自行扩展 skill 集合
- 本仓库优先关注 skill system 本身，不提前把产品实现复杂度带进来

## Versioning Discipline

- 每个正式 skill 必须有 `skill_version`
- 重要变更必须能从 Git history 中追溯
- `experimental` skill 被使用时必须标明风险与退出条件

## Current Factory Focus

当前阶段优先做：

1. `GSDT-anc-using-GSDT`
2. `GSDT-meta-GSD-skill-creator`
3. using-* 二层索引体系
4. registry / versioning / milestone context system
5. skill development methodology 的固化
