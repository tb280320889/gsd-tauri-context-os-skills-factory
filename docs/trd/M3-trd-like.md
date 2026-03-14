# M3 TRD-like：建立高级数据、观测与跨移动端扩展线

## 1. 文档目的
本文件用于定义 M3 阶段的技术目标、边界、产物、验证方式与退出标准，
作为 Planner 进行 phase 注入与 handoff 的真值输入之一。

## 2. 阶段目标
在不污染 baseline 的前提下，为复杂数据形态、强化运行期观测和跨移动端扩展建立 opt-in skill 路线。

## 3. 范围

### In Scope
- `GSDT-dom-data-surreal`
- `GSDT-dom-observability-runtime`
- `GSDT-nbr-diagnostics-local-log`
- `GSDT-dom-mobile-cross-platform` 或 `GSDT-dom-host-tauri-mobile`

### Out of Scope
- 多链链上集成
- 2Agent 深层协议
- release/community 自动化体系全量展开

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
1. SurrealDB 升级条件与 skill 草案
2. 运行期观测 skill
3. 本地诊断日志 skill
4. 跨移动端宿主扩展 skill

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
- 复杂能力过早进入 baseline
- 观测能力只停留在工具名罗列，未形成证据流
- 跨移动端需求与桌面需求混成一个模糊宿主 skill

## 12. 阶段实施备注
- baseline 与高级扩展路线清晰隔离
- 运行期观测与诊断有正式 skill 入口
- SurrealDB 等复杂能力不再混入基础数据线

## 13. 退出标准
- M3 是 upgrade path，不是默认主线
- 所有新增 skill 都必须写明进入条件、替代关系与退出方式
- 观测能力必须覆盖 logs / trace / replay / Sentry / 本地诊断文件
