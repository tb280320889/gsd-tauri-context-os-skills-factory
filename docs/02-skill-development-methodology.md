# Skill Development Methodology

## 1. 方法论定位

本文件用于固化本仓库在长期 session、跨 agent、跨 milestone 开发中的核心方法论，
避免后续在全新上下文下丢失关键原则。

它服务于：

- skill authors
- planner
- researcher
- verifier
- 未来被桥接接入的外部 GSD 项目

## 2. Skill 的本质

skill 不是为了替代 model intelligence，也不是为了重复堆砌模型已经很强的通用知识。

skill 的目标是：

- 快速弥补 agent 在特定领域的专精鸿沟
- 收敛 agent 的注意力与行动边界
- 注入高价值的经验、最佳实践、方法论与 RAG 入口
- 让强通用 agent 更稳定地表现为某个具体领域的高级专家

可以用一句话概括：

> Skill is not for replacing model intelligence; it is for activating domain excellence.

## 3. 避免重复造轮子的优先级

在创建任何新 skill 之前，必须优先检查已有高质量资产，遵循 `search-first`、`official-first`、`reuse-first`。

推荐优先级：

1. `Official MCP / Official Skill First`
   - 官方提供的 MCP、tools、skills、agent guide
2. `High-quality Open-source MCP / Skill`
   - 顶尖开发者、成熟开源项目中已验证的 skill / workflow
3. `Official Agent-friendly Docs`
   - 官方 AI docs、`llms.txt`、结构化 agent 友好文档
4. `Official Human Docs`
   - 官方 docs、API docs、reference、migration guides
5. `Engineering Best Practices`
   - 工程师最佳实践、架构经验、验证策略、失败模式总结
6. `New Skill Logic`
   - 只有在前述内容仍不能很好覆盖时，才自己创造新的 skill 主体

## 4. Skill 创建前必须回答的问题

在正式创建 skill 前，至少先回答以下问题：

1. 这个 skill 要弥补的具体鸿沟是什么？
2. 这个鸿沟是否已被 official MCP / official skill / official docs 覆盖？
3. 它真的值得独立成一个 skill，还是更适合作为 `using-*` / references / templates？
4. 它属于哪个 `domain`，而不是哪个 phase？
5. 它注入时的最小闭包是什么？
6. 它退出时必须留下什么 `Output Contract` 与 `Verification`？

## 5. Skill 的四层结构

为了避免所有内容都挤进同一类 skill，建议长期采用四层结构：

- `using skill`
  - 负责导航、索引、编排、使用说明
- `domain skill`
  - 负责某领域核心知识、最佳实践、边界、常见坑
- `neighbor skill`
  - 负责验证、联调、handoff、局部约束等邻域补充
- `meta skill`
  - 负责生产其他 skills

## 6. 上下文隔离纪律

本项目后续必须坚持 `independent context by milestone`，避免长上下文污染。

硬要求：

- 每个 `M` 阶段必须有独立 context 文档
- 每个 phase 的设计与执行应尽量局部化
- 不在一个超长连续上下文里混开发多个 milestone
- 研究任务与最终 skill 落地任务应尽量分离

这是性能纪律，不是形式主义。
如果上下文持续膨胀，agent 表现会显著下降。

## 7. 研究与落地的推荐流程

很多 skill 的质量，取决于是否先做独立 research，而不是直接写正文。

推荐流程：

1. 明确 skill 目标与边界
2. 启动独立 research context 或 research subagent
3. 优先查找：
   - official MCP
   - official skill
   - official docs / `llms.txt`
   - 高质量开源实践
4. 输出 `research digest`
   - 哪些可以直接复用
   - 哪些只能参考
   - 哪些仍需自己设计
5. 回到主上下文
6. 用 `GSDT-meta-GSD-skill-creator` 落地正式 skill

## 8. Git 作为基础设施

skill 是持续演化的，不是一次性文稿。

因此 Git 不是附加项，而是基础设施：

- 命名演进
- 边界收敛
- references 更新
- lifecycle 调整
- regression 修复
- 版本对比
- 回退与审计

每个 skill 至少应具备：

- `skill_version`
- Git history 可追溯
- 重要变更说明
- compatibility notes

## 9. 对 M0 的具体含义

当前我们已经进入 `M0`，但仍处于 `bootstrap / architecture freeze` 子阶段。

这意味着当前重点不是批量铺开大量 skill，而是先冻结：

- skill factory 的生产方法论
- naming / registry / versioning
- using-* 索引体系
- meta skill 的生产规则
- context isolation discipline

## 10. 当前最重要的三个方向

在 M0 中，优先级最高的是：

1. `GSDT-anc-using-GSDT`
2. `GSDT-meta-GSD-skill-creator`
3. `search-first / official-first / reuse-first / context-isolated` 的治理方法
