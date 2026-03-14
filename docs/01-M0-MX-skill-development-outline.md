# M0-MX 开发大纲：GSD Context OS Skills Factory

## 0. 总体推进原则

### 0.1 先控制平面，后扩领域面
先做：
- Root / Planner / Researcher
- `using-GSDT`
- `GSD-skill-creator`
- skill 写法母规范
- skill naming 与 registry 规范
- truth-source policy
- verify 与回归框架

后做：
- 具体 domain skill
- host skill
- 链上 skill
- 2Agent 高级能力

### 0.2 先协议稳定，后批量生产
在 M0-M1 阶段，不追求 skill 数量，而追求：
- 注入协议正确
- AGENTS.md 驱动的发现协议成立
- skill name prefix 索引成立
- 边界清晰
- handoff 清晰
- 回归机制成立
- Git versioning 与生命周期治理成立

### 0.2.1 先建索引层，再扩 skill 面
在 skill factory 的早期，必须先把 agent 的发现入口与理解入口搭稳。

因此优先顺序应为：

1. 仓库级 `using-GSDT`
2. 元 skill `GSD-skill-creator`
3. using-* 二层索引
4. 再逐步扩 domain / neighbor / governance skills

### 0.3 先最小可靠，再扩展复杂性
先默认本地优先：
- SQLite
- Tauri / WXT 二选一 host 注入
- SvelteKit 前端基线
- verify / evidence 基线

同时坚持：
- skill 主组织维度是 domain，不是 phase
- phase 是 small-batch iteration unit，例如 `v0.1.0` / `v0.1.1`
- planner 在每个 phase 只注入最小 skill 闭包，而不是铺开整仓
- 当前仓库首先关注 skill system 自身，而不是过早代入消费方项目的复杂实现细节

复杂能力如：
- SurrealDB
- 多链
- agent-native
- 重型 release/community 自动化
应后置为 opt-in 扩展线。

## M0：建立 GSD 注入内核

### 目标
把“AGENTS.md -> planner 发现 skill -> 注入 phase 文档”的根协议定死，
并建立 skill 命名、元 skill、Git versioning 的基础纪律。

### 必做
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

### 关键产出
- Root Skill 协议
- `using-GSDT` 主编排说明
- using-* 二层索引体系设计
- AGENTS.md 生成规则
- skill naming convention（带 `GSDT-` 前缀）
- skill registry 元数据约束
- truth-source seed registry
- official-first / reuse-first research policy
- 外部项目 phase 注入与优先级规则
- phase handoff 雏形
- Git versioning 与 lifecycle 基线
- context preservation / milestone progress 维护机制

### 不做
- 大量 domain skill
- 大量链上扩展
- 复杂 2Agent 暴露

### 完成标准
- planner 可通过 `AGENTS.md` 发现并按 phase 注入 skill
- executor 不再默认拿全量上下文
- skill 不再依赖目录结构做索引，而依赖统一命名与 registry
- skill 有可追溯的 Git 管理方式
- using-* 已形成一级入口，且二层索引方案已明确
- official-first / search-first / context-isolated 方法论已固化为长期真值

## M1：建立通用工程主干

### 目标
在 M0 元规范稳定后，把跨大多数项目都会复用的基础 domain skill 落稳。

### 必做
- `GSDT-gov-global-architecture`
- `GSDT-ver-verify-evidence`
- `GSDT-meta-skill-authoring-governor`
- `GSDT-dom-frontend-sveltekit`
- `GSDT-dom-backend-axum`
- `GSDT-dom-data-sqlite-sqlx`

### 关键产出
- skill 写法母规范
- skill 回归与评测样例
- 前后端 / SQLite / 验证的基线 skill
- 输出契约与失败证据模板
- domain-first + neighbor-assisted 的选型样例

### 完成标准
- 普通 local-first / web 项目可以闭环
- 真相源、验证、回归机制可用
- domain baseline skill 形成最小集合

## M2：建立 host 技能线

### 目标
把宿主能力彻底隔离 skill 化，防止 host 污染基础前端 skill。

### 必做
- `GSDT-dom-host-wxt`
- `GSDT-dom-host-tauri2`
- `GSDT-nbr-integration-cross-boundary`
- `GSDT-adp-research-tavily-remote-mcp`

### 关键产出
- host-specific 约束与验证规范
- 官方入口优先研究策略
- 搜索 provider adapter 层
- 跨边界联调契约

### 完成标准
- WXT 与 Tauri 都能独立被 phase 注入
- 搜索能力与研究策略分离
- integration phase 有独立 skill 闭包

## M3：建立高级数据与观测扩展线

### 目标
支持复杂数据形态与更强 runtime observability，但不回流污染 baseline。

### 必做
- `GSDT-dom-data-surreal`
- `GSDT-dom-observability-runtime`
- `GSDT-nbr-diagnostics-local-log`
- `GSDT-dom-mobile-cross-platform` 或 `GSDT-dom-host-tauri-mobile`

### 关键产出
- 升级条件文档
- runtime 观测成熟度提升
- 本地诊断与日志归档策略
- 复杂数据线的 opt-in 路线

### 完成标准
- baseline 与 upgrade path 清晰隔离
- 运行期诊断能力提升
- 跨移动端能力有独立入口

## M4：建立链上技能线

### 目标
把 Base / TON TMA / Solana 完全 skill 化隔离，避免多链混写。

### 必做
- `GSDT-dom-chain-base`
- `GSDT-dom-chain-ton-tma`
- `GSDT-dom-chain-solana`
- `GSDT-nbr-wallet-boundary-patterns`
- `GSDT-ver-onchain-verify-safety`

### 关键产出
- 链上 skill 家族
- 钱包/签名/交易边界模板
- testnet/mainnet 风险等级策略
- mock / sandbox / verify 规范

### 完成标准
- 三条链各自独立 skill
- 官方入口优先级清晰
- 社区 MCP 不再被误抬为主线

## M5：建立 2Agent 技能线

### 目标
让产品从 human-first 稳定演进为 agent-friendly。

### 必做
- `GSDT-dom-2agent-headless`
- `GSDT-dom-2agent-cli`
- `GSDT-dom-2agent-mcp`
- `GSDT-ver-2agent-readiness-review`
- `GSDT-nbr-phase-handoff-contracts`

### 关键产出
- 2Agent 成熟度模型
- action 抽象策略
- CLI 与 MCP 暴露规范
- 审批、幂等、审计、权限、安全要求
- phase handoff 正式模板

### 完成标准
- 产品的 agent-facing surface 有正式设计路线
- 不是所有产品都 MCP 化，但可被评估是否值得推进
- destructive actions 的安全边界清晰

## MX：持续迭代与治理阶段

### 目标
让 skill factory 进入持续生产与自我治理状态。

### 必做
- `GSDT-gov-skill-lifecycle-governance`
- `GSDT-ver-skill-audit-postmortem`
- `GSDT-gov-release-community`

### 关键产出
- skill 注册表
- truth-source 注册表
- 生命周期治理
- 回归与事故后修复流程
- 对外发布与社区化资料

### 完成标准
- skill 不只是能写出来，还能被维护、退役、审计、刷新
- 整个工厂能支撑多项目、多团队、多阶段复用

## 建议的里程碑推进顺序

1. M0：根协议
2. M1：母规范 + baseline
3. M2：host + research
4. M3：升级路径
5. M4：链上隔离
6. M5：2Agent
7. MX：治理与长期演化

## 交付建议

每个 M 阶段至少交付四类产物：
1. Skill 文稿
2. References / templates / examples
3. Eval / regression 样例
4. 阶段性 TRD-like 文档与退出准则

并建议补充三类配套产物：
5. skill registry metadata
6. Git versioning / compatibility notes
7. planner 用的注入示例与排除示例
