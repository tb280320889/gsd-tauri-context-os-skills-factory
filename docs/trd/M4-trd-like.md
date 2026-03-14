# M4 TRD-like：建立链上技能线与链域隔离策略

## 1. 文档目的
本文件用于定义 M4 阶段的技术目标、边界、产物、验证方式与退出标准，
作为 Planner 进行 phase 注入与 handoff 的真值输入之一。

## 2. 阶段目标
将 Base、TON/TMA、Solana 三条链完全隔离 skill 化，并建立钱包、签名、交易、风险等级与验证规范。

## 3. 范围

### In Scope
- `GSDT-dom-chain-base`
- `GSDT-dom-chain-ton-tma`
- `GSDT-dom-chain-solana`
- `GSDT-nbr-wallet-boundary-patterns`
- `GSDT-ver-onchain-verify-safety`

### Out of Scope
- 多链大杂烩统一 skill
- 把社区 MCP 抬成官方主线
- 把链上 skill 泛化到所有项目默认注入

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
1. 三条链的独立 skill 初版
2. 钱包/签名/交易边界模板
3. testnet/mainnet 风险等级策略
4. onchain verify 与 mock/sandbox 策略

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
- 不同链的容器、钱包、权限和开发模型混淆
- 社区资料质量不稳，导致真相源层级错位
- 读写链上动作的安全边界不充分

## 12. 阶段实施备注
- Base / TON / Solana skill 各自独立
- 钱包与交易边界被模板化
- mock / sandbox / verify 路线清晰
- 无跨链混写污染

## 13. 退出标准
- 每条链必须独立 skill 化
- 官方入口优先级必须显式标注
- read-only 与 write actions 的风险等级必须分层
- testnet/mainnet 切换策略必须写明
