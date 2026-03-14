# M1 TRD-like：建立通用工程主干与元 skill 基线

## 1. 文档目的
本文件用于定义 M1 阶段的技术目标、边界、产物、验证方式与退出标准，
作为 Planner 进行 phase 注入与 handoff 的真值输入之一。

## 2. 阶段目标
建立可复用的 baseline skill 集，并把 skill 本身的写法、验证与回归纳入正式工程治理。

## 3. 范围

### In Scope
- `GSDT-gov-global-architecture`
- `GSDT-ver-verify-evidence`
- `GSDT-meta-skill-authoring-governor`
- `GSDT-dom-frontend-sveltekit`
- `GSDT-dom-backend-axum`
- `GSDT-dom-data-sqlite-sqlx`

### Out of Scope
- WXT / Tauri 宿主细节
- 多链支持
- SurrealDB 复杂数据路线
- Agent-native 深水区

## 4. 输入前提
- 已存在设计母稿与 M0-MX 总大纲
- `.gsdt-context` 与 M0 context 已稳定
- M0 已产出 registry / truth-source / research policy / eval seed 基线
- 项目接受 accepted context docs > injected skills > root-like rules 的上下文优先级

## 5. 关键问题陈述
本阶段要解决的不是“多写几个 skill”，而是要解决：
1. 当前阶段的核心控制面是否稳定
2. 当前阶段的 skill 是否具备明确边界
3. 当前阶段的输出与验证是否可复制
4. 当前阶段是否为下一阶段留下可接续的 handoff

## 6. 主要技术工作项
1. skill 写法母规范
2. baseline domain skill 初版
3. verify / failure evidence 模板
4. skill 回归测试样例
5. 输出契约与验证契约模板

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
- skill 数量增加但边界不稳
- baseline skill 被写成“全项目规范总集”
- verify 只写测试清单，未覆盖失败证据链

## 12. 阶段实施备注
- baseline 工程 skill 集形成最小闭环
- verify / evidence 能作为一等产物出现
- skill authoring 与 skill regression 有实际模板可复用
- `GSDT-ver-skill-eval-regression` 已在 M0 前移，M1 直接消费其种子能力

## 13. 退出标准
- M1 的重点是建立母规范与最小可靠集合
- 新增 skill 必须带最小评测样例
- 优先覆盖前后端、本地数据、验证三条主线
