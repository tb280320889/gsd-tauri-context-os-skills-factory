# M5 TRD-like：建立 2Agent 技能线与 agent-facing surface 规范

## 1. 文档目的
本文件用于定义 M5 阶段的技术目标、边界、产物、验证方式与退出标准，
作为 Planner 进行 phase 注入与 handoff 的真值输入之一。

## 2. 阶段目标
让产品从 human-first 平滑演进为 agent-friendly，把 headless、CLI、MCP、agent-native 的成熟度和进入条件写成正式 skill。

## 3. 范围

### In Scope
- `GSDT-dom-2agent-headless`
- `GSDT-dom-2agent-cli`
- `GSDT-dom-2agent-mcp`
- `GSDT-ver-2agent-readiness-review`
- `GSDT-nbr-phase-handoff-contracts`

### Out of Scope
- 对所有产品一刀切要求做到 agent-native
- 在尚未 headless 化前直接暴露 MCP
- 把 destructive actions 作为默认可用动作

## 4. 输入前提
- 已存在设计母稿与 M0-MX 总大纲
- `.gsdt-context` 与前序 milestone context 已稳定
- Root-like rules 已通过仓库级 `AGENTS.md` 固化
- 项目接受 accepted context docs > injected skills > root-like rules 的上下文优先级

## 5. 关键问题陈述
本阶段要解决的不是“多写几个 skill”，而是要解决：
1. 当前阶段的核心控制面是否稳定
2. 当前阶段的 skill 是否具备明确边界
3. 当前阶段的输出与验证是否可复制
4. 当前阶段是否为下一阶段留下可接续的 handoff

## 6. 主要技术工作项
1. 2Agent 成熟度模型文档
2. headless/CLI/MCP skill 初版
3. readiness review 模板
4. phase handoff 正式模板与最小交付包定义

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
- 跳级推进，导致动作层与权限模型不稳
- 只讲 agent 体验，不讲审计、幂等、安全与审批
- handoff 仍旧口头化，没有正式输出契约

## 12. 阶段实施备注
- 2Agent 成熟度路线正式成文
- readiness review 可作为阶段检查点
- phase handoff 有正式模板
- 产品是否推进到 CLI/MCP 有判断框架而非凭感觉

## 13. 退出标准
- 优先形成 action-oriented、schema-oriented 的设计
- 先 read-only，再谨慎放写操作
- destructive actions 必须要求审批、审计、幂等与 timeout 策略
