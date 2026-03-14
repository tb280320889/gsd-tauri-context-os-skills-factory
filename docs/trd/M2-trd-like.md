# M2 TRD-like：建立宿主技能线与在线研究能力层

## 1. 文档目的
本文件用于定义 M2 阶段的技术目标、边界、产物、验证方式与退出标准，
作为 Planner 进行 phase 注入与 handoff 的真值输入之一。

## 2. 阶段目标
将 WXT 与 Tauri 宿主能力独立 skill 化，并把在线研究策略与搜索 provider 适配层正式拆开。

## 3. 范围

### In Scope
- `GSDT-dom-host-wxt`
- `GSDT-dom-host-tauri2`
- `GSDT-nbr-integration-cross-boundary`
- `GSDT-adp-research-tavily-remote-mcp`

### Out of Scope
- SurrealDB 升级路线
- 多链隔离 skill
- 2Agent CLI / MCP 暴露
- 重型 release/community 工作

## 4. 输入前提
- 已存在设计母稿与 M0-MX 总大纲
- `.gsdt-context` 与 M0/M1 context 已稳定
- `GSDT-gov-online-research-official-first` 已在 M0 建立为 policy 基线
- 项目接受 accepted context docs > injected skills > root-like rules 的上下文优先级

## 5. 关键问题陈述
本阶段要解决的不是“多写几个 skill”，而是要解决：
1. 当前阶段的核心控制面是否稳定
2. 当前阶段的 skill 是否具备明确边界
3. 当前阶段的输出与验证是否可复制
4. 当前阶段是否为下一阶段留下可接续的 handoff

## 6. 主要技术工作项
1. WXT skill 初版
2. Tauri 2 skill 初版
3. integration skill 初版
4. online research policy skill
5. Tavily remote MCP adapter skill

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
- 把搜索 provider 当成治理规则，导致 provider 锁定
- WXT 与 Tauri 混写，边界污染
- integration skill 越权回收领域实现细节

## 12. 阶段实施备注
- 宿主 skill 可独立按 phase 注入
- 官方优先研究策略可复用
- Tavily 等 provider 被限制在 adapter 层
- 联调阶段有独立最小 skill 闭包
- `online-research-official-first` 已前移到 M0，本阶段不再重复定义 policy 层

## 13. 退出标准
- 需要显式拆出 research policy 与 provider adapter
- WXT 与 Tauri 的验证规范必须独立
- integration 只关心跨域闭包，不应重新定义各领域内部实现
