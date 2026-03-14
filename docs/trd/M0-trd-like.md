# M0 TRD-like：建立 GSD 注入内核

## 1. 文档目的
本文件用于定义 M0 阶段的技术目标、边界、产物、验证方式与退出标准，
作为 Planner 进行 phase 注入与 handoff 的真值输入之一。

## 2. 阶段目标
冻结 skill factory 的最小根协议，确保 skill 不再以全量知识包方式暴露，
而是以可被外部 GSD 项目 planner 发现、选择、注入的最小语境单元运行。

## 3. 范围

### In Scope
- `GSDT-anc-using-GSDT`
- `GSDT-meta-GSD-skill-creator`
- `GSDT-anc-gsd-root-router`
- `GSDT-anc-project-researcher`
- `GSDT-anc-phase-planner`
- `GSDT-gov-online-research-official-first`
- `GSDT-gov-skill-registry-index`
- `GSDT-gov-truth-source-registry`
- `GSDT-gov-minimal-2oss`
- `GSDT-gov-docs-governance`
- `GSDT-ver-skill-eval-regression`

### Out of Scope
- 大量 domain skill
- 链上 skill
- 2Agent 高级能力
- 复杂观测与多宿主联调

## 4. 输入前提
- 已存在设计母稿与 M0-MX 总大纲
- `.gsdt-context` 已初始化
- 仓库级 `AGENTS.md` 已建立 read order 与最小硬规则
- 项目接受 accepted context docs > injected skills > root-like rules 的上下文优先级

## 5. 关键问题陈述
本阶段要解决的不是“多写几个 skill”，而是要解决：
1. 当前阶段的核心控制面是否稳定
2. 当前阶段的 skill 是否具备明确边界
3. 当前阶段的输出与验证是否可复制
4. 当前阶段是否为下一阶段留下可接续的 handoff

## 6. 主要技术工作项
1. `using-GSDT` 仓库级入口
2. `GSD-skill-creator` 元 skill
3. registry / truth-source / versioning 种子体系
4. official-first / reuse-first research policy
5. context preservation / milestone progress 维护机制

## 7. skill 设计要求
- 每个 skill 必须先定义触发条件，再定义允许真相源，再定义执行与输出契约
- 每个 skill 必须写清禁止越界项
- 每个 skill 必须写清与邻域 skill 的交接条件
- 复杂细节应沉入 `references/`，`SKILL.md` 保持控制平面职责
- 对需要在线搜索的场景，必须区分 research policy 与 provider adapter

## 8. 真相源要求
- T0：accepted context docs / accepted TRD-like / ADR / contract
- T1：官方 MCP / 官方结构化入口
- T2：官方 docs / 官方 AI docs / 官方 llms.txt
- T3：项目内 README / AGENTS / 代码 / 脚本 / 测试命令
- T4：logs / trace / replay / Sentry / screenshots / reports
- T5：社区资料（仅作补强）

## 9. 输出契约
本阶段输出至少应包含：
- skill 列表与状态
- 每个 skill 的边界摘要
- 注入矩阵或 phase 触发说明
- references / templates / examples 清单
- 验证摘要
- 未解决风险与下一阶段建议

## 10. 验证要求
- 对新增/更新 skill 进行至少一组样例驱动评测
- 检查是否存在上下文膨胀、越界、真相源顺序错误
- 检查是否遗漏输出契约或失败证据约束
- 对需要 provider adapter 的 skill，检查是否与 policy 分离

## 11. 风险与约束
- Root Skill 写得过厚，重新变成大知识包
- Planner 不足够强，导致上下文切分失效
- 关键方法论只停留在对话中，未回写到 context docs
- M0 期间过早转向大量 domain skills，导致返工

## 12. 阶段实施备注
- 当前已进入 M0，但处于 bootstrap / architecture freeze 子阶段
- 已建立 `.gsdt-context` 作为仓库专用 context system
- 已创建 `GSDT-anc-using-GSDT` 与 `GSDT-meta-GSD-skill-creator` draft
- 已确认 registry / truth-source / research policy 前移到 M0

## 13. 退出标准
- M0 期间优先产出控制平面，不要沉迷领域细节
- 所有文稿必须服务于 phase 注入，不应写成百科说明
