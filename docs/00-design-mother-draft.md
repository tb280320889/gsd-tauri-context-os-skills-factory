# 设计母稿：跨端 App · GSD Context OS Skills Factory

## 1. 项目定性

本项目不是技术 pack 仓，也不是普通的 agent 提示词集合仓。
它的正式定性应为：

> 一个面向 GSD（Discuss / Plan / Execute / Verify）工作流的 **Context OS Skill Factory**。  
> 它持续产出、维护、版本化并治理一组可被 planner 按 milestone / phase 注入到执行上下文中的 skills，
> 用于支撑跨端应用、浏览器插件、Tauri、本地服务、数据层、链上扩展、验证体系、2OSS 治理，以及产品自身的 2Agent 亲和化演进。

在当前阶段，更准确地说：

> 它是一个面向 `GSD + Tauri2 跨端 App` 项目的 skills 工具集工厂，
> 后续会作为 submodule / vendored toolkit 被多个 GSD 项目引入。
> 当前仓库的主要工作不是直接开发消费方产品，而是进行 **skills 的设计、规划、规范与建造**。

它服务的对象不是最终用户，而是：
- Project-Researcher / Planner
- Executor / Debugger / Verifier 子链路
- 模板仓 / 产品仓 / GSD Application Factory 流水线

## 2. 扭转后的核心判断

### 2.1 原 pack 概念正式升级为 skill family
此前定义的 frontend-pack / tauri-pack / verify-pack / 2Agent Pack 等，不再继续视为静态知识包。
它们现在统一改写为：

- 可触发
- 可裁剪
- 可注入
- 可版本化
- 可验证
- 可迭代

的 **skill family**。

### 2.1.1 skill 的统一命名主键
本工厂中的 skill 不以目录结构作为发现与索引主轴，而以 **统一命名主键** 作为主轴。

推荐命名格式：

- `GSDT-<family>-<domain>-<capability>`
- 必要时允许扩展为：`GSDT-<family>-<domain>-<capability>-<variant>`

其中：

- `GSDT`：项目级统一前缀，用于跨仓识别与聚合
- `family`：skill 家族前缀，如 `anc` / `dom` / `nbr` / `gov` / `meta` / `adp` / `ver`
- `domain`：所属领域或主对象
- `capability`：能力名
- `variant`：可选技术分支或运行模式

目录仅作为存储便利层（storage convenience），不作为语义索引层（semantic discovery layer）。
planner 与其他 agent 在发现、选择、引用 skill 时，必须优先读取 `skill_name` 与 registry metadata，而不是根据目录树猜测其职责。

### 2.2 skill 的首要职责
每个 skill 的首要职责不是堆积背景知识，而是承担以下控制平面角色：

1. 声明触发条件与适用 phase
2. 声明允许消费的真相源与优先级
3. 声明 agent 的职责边界与禁止越界项
4. 声明输出、验证、失败证据与 handoff 契约
5. 声明与邻域 skill 的衔接关系

### 2.2.1 skill 的方法论定位
skill 不是为了替代模型智能本身，也不是为了重新打包模型已经具备的通用开发能力。

skill 的价值在于：

- 弥补 agent 在特定知识领域的专精鸿沟
- 收敛 agent 的注意力、边界与行为模式
- 注入高价值的经验、最佳实践、方法论与 RAG 入口
- 让强通用 agent 更稳定地表现为某个具体领域的高级专家

可以用一句英文原则概括：

> Skill is not for replacing model intelligence; it is for activating domain excellence.

### 2.2.2 避免重复造轮子的优先级
在创建任何新 skill 之前，必须优先检查可复用资产，遵循：

- `search-first`
- `official-first`
- `reuse-first`

优先级建议为：

1. official MCP / official skill
2. 高质量开源 MCP / skill / workflow
3. 官方 agent-friendly docs / `llms.txt`
4. 官方 docs / reference / migration guides
5. 工程师最佳实践
6. 自建新的 skill 主体

也就是说：只有在现有高质量资产不能很好覆盖时，才应该创建新的 skill 主体。

### 2.3 渐进式披露是一级原则
项目中的 skill 不能对所有 agent 平铺展开。
应遵守：

- Root Skill：全员可见，但只负责规则锚点
- Project-Researcher / Planner：高层可见，用于初始化与路由
- Domain Executor：只看当前 `.planning` phase + 邻域 skill
- Integration / Verify：只在联调与验证阶段获得跨域最小闭包

### 2.3.1 当前仓库与消费方项目的区别
需要严格区分：

- 当前仓库：skills factory，自身以设计、规划、规范与建造为主
- 消费方项目：真正使用这些 skills 的 GSD 产品仓

因此：

- 本仓库可以维护自己的上下文体系与 skill 规范
- 消费方项目再通过外层桥接方式，把这些 skills 接入其自身 `.planning` / phase workflow
- 当前仓库不应直接把消费方项目的 `.planning` 目录当作自己的主工作目录

### 2.4 Domain-first，而不是 phase-first
本项目中的 phase 是一个 **small-batch iteration unit**，不是领域分类单位。

例如：

- `frontend v0.1.0`
- `frontend v0.1.1`
- `backend v0.2.0`

它们表达的是小步迭代批次，而不是“一个 phase 对应一个完整领域”。

因此 skill 的主组织维度应为：

- `domain skill`：长期稳定、按领域复用
- `neighbor skill`：围绕当前迭代切片做最小补充

planner 在 phase 内的选择原则应是：

- 选定 `1` 个 primary domain skill
- 按需补充 `0-N` 个 neighbor / governance / verify skill
- 禁止把 phase 当作一级 skill 分类目录

### 2.5 using-* 的双层索引体系
本工厂不只需要正式 skill 本体，还需要一层可被 agent 快速消费的使用说明索引层。

建议建立：

- 一级索引：`GSDT-anc-using-GSDT`
  - 负责解释整个仓库如何被使用
- 二级索引：`using-<domain>-<topic>` 或等价命名的 `GSDT-anc-using-*`
  - 负责解释某个领域 skill family 如何被理解、选择、搭配与注入

这些 `using-*` skill 的职责不是替代领域 skill，而是降低发现成本与组合成本。

## 3. 三层体系

## 3.1 常驻治理层（2OSS Discipline Layer）
2OSS 不是收尾动作，而是从 Day 0 常驻的治理纪律。

### 作用
- 私有仓阶段即保持 OSS-ready
- 模板仓与产品仓共享治理纪律
- 提前适配未来 public / community / AI-ready / agent-friendly 演进

### 包含
- repo baseline
- license / security / contribution / governance baseline
- docs baseline
- AI-ready docs / llms / MCP baseline
- CI / checks / release baseline
- 日志、trace、失败证据、Sentry、runtime observability baseline
- skill 版本化 / 退役 / 相容策略

## 3.2 模板与项目生成层（Template Bootstrap / App Factory Layer）
负责把 skill factory 接入具体项目。

### 包含
- GSD-APP-FACT 引入说明
- new-project / project-researcher 机制
- planner 注入机制
- AGENTS.md 生成与 Root Skill 引用
- `.planning` 初始化结构
- submodule / vendoring / 同步机制

## 3.3 具体产品开发层（Phase-bound Product Development Layer）
负责在具体 milestone / phase 内，为当前任务注入最小必要 skill。

### 构成
- anchor skills
- governance skills
- domain skills
- integration skills
- verify skills
- 2Agent skills

## 4. 全局注入协议

### 4.1 根协议
所有 agents 必读 Root Skill（超精简规则锚点）。
本工厂对 GSD 的主注入链路简化为：

> `AGENTS.md` 强制让 planner 知道本 skill 仓库及其规则；
> planner 基于当前 `.planning` phase 目标选择合适 skill；
> planner 将选中的 skill 注入到 phase 上下文文档；
> executor / debugger / verifier 只消费 phase 文档中的注入闭包。

Project-Researcher / Planner 负责按 `.planning` 当前 phase，把必要 skill 注入执行上下文。
executor / debugger / verifier 以 `.planning` 为最高优先级消费上下文，实现渐进式披露。

### 4.2 上下文优先级
1. `.planning` 当前 phase 文档
2. planner 注入的邻域 skill
3. Root Skill

### 4.3 Root Skill 的严格职责
Root Skill 只做三件事：
1. 角色/阶段路由规则
2. 优先级规则
3. 渐进式披露机制

Root Skill 不承载：
- 全量领域细节
- 全量框架知识
- 全量技术栈说明
- 具体实现教程
- 产品真值替代物

### 4.4 AGENTS.md 的角色
`AGENTS.md` 是当前阶段面向 GSD planner 的 **mandatory entrypoint**。

它至少负责：

1. 告诉 planner 去哪里发现本仓 skills 与 registry
2. 强制声明 skill 发现遵循 naming + registry，而不是目录结构
3. 强制声明注入结果必须落入 `.planning` 当前 phase 文档
4. 强制声明上下文优先级：`.planning` > injected skills > root rules
5. 强制声明 phase 只应持有最小 skill 闭包，避免全仓平铺注入

同时 `AGENTS.md` 必须保持精简，因为它会在全新上下文下高频进入 agent 上下文窗口。
长期规则、阶段目标与复杂说明应下沉到仓库专用 context docs 与 using-* skill 中。

## 5. 核心 skill 家族

## 5.1 Anchor Skills
- `GSDT-anc-gsd-root-router`
- `GSDT-anc-project-researcher`
- `GSDT-anc-phase-planner`
- `GSDT-anc-using-GSDT`

## 5.2 Governance Skills
- `GSDT-gov-minimal-2oss`
- `GSDT-gov-global-architecture`
- `GSDT-gov-docs-governance`
- `GSDT-gov-release-community`
- `GSDT-gov-oss-governance`
- `GSDT-meta-skill-authoring-governor`
- `GSDT-ver-skill-eval-regression`
- `GSDT-gov-truth-source-registry`

## 5.3 Domain Skills
- `GSDT-dom-frontend-sveltekit`
- `GSDT-dom-host-wxt`
- `GSDT-dom-host-tauri2`
- `GSDT-dom-backend-axum`
- `GSDT-dom-data-sqlite-sqlx`
- `GSDT-dom-data-surreal`
- `GSDT-dom-chain-base`
- `GSDT-dom-chain-ton-tma`
- `GSDT-dom-chain-solana`

## 5.4 Cross-boundary Skills
- `GSDT-nbr-integration-cross-boundary`
- `GSDT-ver-verify-evidence`
- `GSDT-gov-online-research-official-first`
- `GSDT-adp-research-tavily-remote-mcp`

## 5.5 2Agent Skills
- `GSDT-dom-2agent-headless`
- `GSDT-dom-2agent-cli`
- `GSDT-dom-2agent-mcp`
- `GSDT-dom-2agent-native`

## 5.6 Meta Skills
- `GSDT-meta-GSD-skill-creator`

### 5.6.1 `GSDT-meta-GSD-skill-creator` 的优先级
在本工厂早期，优先开发的不是大量普通 skill，而是 `GSDT-meta-GSD-skill-creator`。

它是本工厂的元 skill（meta skill），负责统一：

- skill 命名
- skill 写法
- skill 边界
- skill 输出契约
- skill 验证契约
- skill Git 版本化与生命周期治理

它应成为后续所有 skill 生产的母机（skill production bootstrap）。

### 5.6.2 `GSDT-anc-using-GSDT` 的角色
`GSDT-anc-using-GSDT` 是面向所有 agents 的主介绍与编排 skill。

它负责：

- 解释本仓库是什么、何时应被使用
- 说明 planner 如何发现、选择、注入其他 skills
- 说明 executor / debugger / verifier 如何仅消费当前 phase 注入闭包
- 说明命名规则、优先级规则、最小注入原则与越权边界

它不是 Root Skill 的替代品，而是本仓库的使用说明与 orchestration guide。

## 6. 真相源体系

### 6.1 分层
- T0：`.planning` 当前 phase / 已接受 TRD-like / ADR / contract
- T1：官方 MCP / 官方结构化入口
- T2：官方 docs / 官方 AI docs / 官方 llms.txt
- T3：项目内 AGENTS.md / README / 代码模式 / 测试命令 / 本地脚本
- T4：运行期真相源（日志 / trace / replay / Sentry / screenshots / reports）
- T5：社区 MCP / 社区资料 / 第三方补充

### 6.2 规则
- T0 永远高于任何 skill
- 任何 skill 不得把 T5 抬升为 T1/T2
- provider adapter 不得覆盖 research policy
- 在线搜索结果必须区分 official / community / uncertain
- search 能力本身是 adapter，不是 root policy

## 7. 为什么要新增元 skill

本项目未来的复杂度不只来自 domain skill，而是来自 skill 体系自身。

因此必须新增一层 meta skills：
- `skill-authoring-governor`：定义 skill 写法母规范
- `skill-eval-regression`：验证 skill 是否漂移、越界、回归
- `truth-source-registry`：统一维护官方入口与补充入口的状态
- `online-research-official-first`：统一在线研究行为策略
- `tavily-remote-mcp-adapter`：作为搜索能力 provider adapter，而不是治理层规则

## 8. 2Agent 作为正式主线

2Agent 不应被当成晚期附加项，而应被视为：

- 高 ROI 能力增强层
- 低投入的长期积累项
- skill factory 的正式组成部分

### 成熟度分级
1. Headless-ready
2. CLI-ready
3. MCP-ready
4. Agent-native

### 推进原则
- 先 headless，后 CLI，再 MCP
- 先 curated tools，后规模暴露
- 先 read-only，后谨慎写操作
- 所有 agent-facing surface 都要求 schema、日志、版本号、错误码、权限、安全、审计、超时、幂等性

## 9. 输出契约与 handoff 契约

当前体系不能只控制“注入什么”，还必须控制“退出时留下什么”。

每个 phase 至少要定义：
- phase 输出契约
- handoff 契约
- verify 契约
- failure evidence 契约

建议最小产物包括：
- 已修改对象列表
- 关键决策摘要
- 验证执行摘要
- 未解决风险
- 失败证据索引
- 需要注入的下一邻域 skill 建议

## 10. skill 生命周期

随着 skill 增多，必须维护生命周期治理。

同时必须具备 Git 管理能力。skill 不是一次性静态文稿，而是需要：

- Git history
- diff review
- tag / release 对齐的版本语义
- 变更说明
- 回滚与审计能力

建议每个 skill 至少维护：

- `skill_name`
- `skill_version`
- `status`
- `last_reviewed`
- `compatibility_notes`

建议状态：
- draft
- experimental
- stable
- deprecated
- archived

建议配套规则：
- 是否允许默认注入
- 是否仅允许 planner 显式注入
- 是否需要 feature flag
- 是否限制某类项目使用
- 是否需要定期重新核验 truth-source

### 10.1 Git Versioning 原则
- skill 必须纳入 Git 管理，不允许脱离仓库散落维护
- skill 的版本应可通过 Git tag、release note 或 commit lineage 追溯
- planner 在选择 skill 时，应优先稳定版本（stable）和最近核验版本
- 当使用 experimental skill 时，phase 文档中必须记录原因、风险与退出条件

## 10.2 语言风格原则
本工厂的 skill 文风采用：**中文为主，英文强调关键术语**。

建议：

- 叙述、说明、边界、例子以中文为主
- 契约字段、风险标签、输出标题、关键控制词用英文强调

例如：

- `Trigger`
- `Scope`
- `Boundary`
- `Output Contract`
- `Verification`
- `Handoff`
- `Versioning`
- `Lifecycle`

## 11. 结论

本项目的正式目标不是“整理技术知识”，而是构建一套：

> 以 `.planning` 为项目真值、以 Root Skill 为规则锚点、以 planner 为强制注入点、以 skill family 为最小语境单元、以 2OSS 与 2Agent 为长期纪律层的 GSD Context OS。

后续所有里程碑、TRD-like 文档、skill 规范与模板，都应围绕这一目标继续展开。
