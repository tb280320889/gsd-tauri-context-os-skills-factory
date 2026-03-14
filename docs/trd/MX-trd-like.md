# MX TRD-like：持续迭代、注册表治理与长期维护

## 1. 文档目的
本文件用于定义 MX 阶段的技术目标、边界、产物、验证方式与退出标准，
作为 Planner 进行 phase 注入与 handoff 的真值输入之一。

## 2. 阶段目标
让 skill factory 从一次性文稿集合，演进为可审计、可回归、可退役、可长期复用的生产系统。

## 3. 范围

### In Scope
- `GSDT-gov-skill-lifecycle-governance`
- `GSDT-ver-skill-audit-postmortem`
- `GSDT-gov-release-community`

### Out of Scope
- 继续无节制新增 skill 而不治理
- 只修单个 skill，不做全局一致性校验
- 忽略 truth-source 失效与版本漂移

## 4. 输入前提
- 已存在设计母稿与 M0-MX 总大纲
- `.gsdt-context` 与前序 milestone context 已稳定
- `GSDT-gov-truth-source-registry` 与 `GSDT-gov-skill-registry-index` 已在 M0 建立 seed 版
- 项目接受 accepted context docs > injected skills > root-like rules 的上下文优先级

## 5. 关键问题陈述
本阶段要解决的不是“多写几个 skill”，而是要解决：
1. 当前阶段的核心控制面是否稳定
2. 当前阶段的 skill 是否具备明确边界
3. 当前阶段的输出与验证是否可复制
4. 当前阶段是否为下一阶段留下可接续的 handoff

## 6. 主要技术工作项
1. skill 注册表
2. truth-source 注册表
3. 生命周期治理规则
4. 审计与事故后修复流程
5. 对外发布与社区化资料模板

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
- skill 数量增长后冲突增多
- truth-source 过期，技能持续引用旧入口
- experimental skill 长期悬挂，影响稳定性

## 12. 阶段实施备注
- 工厂具备注册表、生命周期、审计、退役机制
- skill 可持续演化而不是越积越乱
- 版本漂移与 truth-source 漂移有应对路径
- registry 与 truth-source 在 MX 阶段主要做成熟化、审计与刷新，而非从零开始

## 13. 退出标准
- MX 不是一个终点，而是常驻治理线
- 必须明确 stable / deprecated / archived 状态
- 必须定期刷新官方入口、llms、MCP、社区适配器状态
