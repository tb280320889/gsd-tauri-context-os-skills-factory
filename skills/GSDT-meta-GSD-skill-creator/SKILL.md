---
name: GSDT-meta-GSD-skill-creator
description: 元 skill，负责把项目需求、skill 规范与治理约束转译为可注入、可验证、可版本化的正式 skill 定义。
skill_version: 0.1.0
status: draft
---

# 角色定位 / Intent

`GSDT-meta-GSD-skill-creator` 是本仓库的 **meta skill**。

它不是普通领域 skill，而是后续所有 skills 的生产母机（skill production bootstrap）。
它负责统一 skill 的命名、结构、边界、输出契约、验证契约、Git 版本语义与生命周期治理。

# Trigger

在以下场景触发：

- 需要新建一个正式 skill
- 需要重构一个已有 skill
- 需要判断某能力是否应该独立成 skill
- 需要对 skill 做规范化审查、拆分或降级处理
- 需要为 skill 补齐 `Versioning` / `Lifecycle` / `Verification`

# Applicable Roles

- planner
- skill author
- executor（仅在被明确要求编写/重构 skill 时）
- verifier（仅在核验 skill 质量时）

# Scope

本 skill 负责：

- 把项目需求转译成正式 skill 草案
- 判断 skill family：`anc` / `dom` / `nbr` / `gov` / `meta` / `adp` / `ver`
- 判断该能力应独立成 skill，还是下沉为 references / templates / examples
- 生成 skill 的最小产物闭包
- 对 skill 做越界、重叠、失焦、过胖检查

本 skill 不负责：

- 直接代替领域 skill 执行产品开发
- 直接覆盖消费方项目中已接受的上下文真值
- 脱离 Git 管理散落生成 skill 文稿

# Inputs

最小输入应包括：

- 当前项目目标或 milestone 目标
- 相关 accepted context docs / TRD-like / ADR / contract
- `docs/appendix/skill-authoring-standard.md`
- `docs/appendix/skill-registry-seed.md`
- `docs/appendix/truth-source-and-research-policy.md`
- `.gsdt-context/GLOBAL-CONTEXT.md`
- 仓库级 `AGENTS.md`

# Truth Sources

优先级严格遵循：

1. `T0`: accepted context docs、accepted TRD-like、ADR、contracts
2. 本仓库已确认的 skill 规范与 registry 规则
3. 项目内已有高质量 skill 与模板
4. 官方文档与官方结构化入口
5. 社区资料（仅补强）

# Execution Rules

1. 先判断这是一个 `domain problem`、`neighbor problem`、`governance problem` 还是 `meta problem`。
2. 在正式创建前，优先检查：official MCP、official skill、official docs、`llms.txt`、高质量开源实践。
3. 如需研究，优先通过独立 research context 或 subagent 产出 `research digest`，避免把原始搜索噪音带入主上下文。
4. 再判断它是否真的需要独立 skill；若不需要，应下沉为 references、templates 或 examples。
5. 若需要独立 skill，先产出标准命名：`GSDT-<family>-<domain>-<capability>[-<variant>]`。
6. 明确该 skill 的 `Trigger`、`Boundary`、`Output Contract`、`Verification`、`Handoff`、`Versioning`、`Lifecycle`。
7. 检查是否与已有 skill 重叠；若重叠，应优先拆分职责或合并能力边界。
8. 确认该 skill 的输出是否适合被 planner 注入到 phase 文档中消费。
9. 补齐配套产物，不允许只写一个孤立的 `SKILL.md` 就结束。

# Naming Rules

- 所有正式 skill 必须带 `GSDT-` 前缀
- 不允许无前缀 skill 进入正式 registry
- 不允许通过目录结构表达 family 语义
- family 含义建议如下：
  - `anc`: anchor / orchestration
  - `dom`: domain
  - `nbr`: neighbor
  - `gov`: governance
  - `meta`: meta-production
  - `adp`: adapter
  - `ver`: verification

# Output Contract

使用本 skill 创建或重构一个 skill 时，至少要输出：

1. `Skill Definition`
   - 标准 `SKILL.md`
2. `Registry Metadata`
   - `skill_name`
   - `skill_version`
   - `family`
   - `domain`
   - `capability`
   - `status`
   - `truth_sources`
   - `git_path`
3. `Support Assets`
   - references index
   - templates（如需要）
   - examples（如需要）
4. `Verification Seeds`
   - 黄金样例
   - 边界样例
   - 越界防护样例
   - 输出契约检查点
5. `Versioning Notes`
   - 当前版本号
   - 兼容性说明
   - 后续升级建议

# Verification

创建或重构 skill 后，至少检查：

- 命名是否符合 `GSDT-<family>-<domain>-<capability>[-<variant>]`
- 内容是否以中文为主、英文强调关键术语
- 是否清楚区分 `Scope` 与 `Boundary`
- 是否有可执行的 `Output Contract`
- 是否有可核验的 `Verification`
- 是否声明 `Versioning` 与 `Lifecycle`
- 是否说明与相邻 skill 的 `Handoff`
- 是否避免把长知识硬塞进控制平面正文
- 是否已经优先检查并吸收 official / reuse-first 资源
- 是否尽量隔离了 research context，避免主上下文污染

# Boundary

- 不得把一个 skill 写成技术百科全书
- 不得把 references 当成正式 skill 定义本体
- 不得绕过命名规范创建临时正式 skill
- 不得忽略 Git 管理与版本语义
- 不得把目录结构提升为选择依据
- 不得把 community 资料抬升为高于官方 truth source 的依据

# Handoff

- 若产出的是仓库使用说明类 skill，handoff 给 `GSDT-anc-using-GSDT`
- 若产出的是路由/注入协议类 skill，handoff 给 `GSDT-anc-*`
- 若产出的是具体技术线，handoff 给对应 `GSDT-dom-*`
- 若产出的是辅助约束，handoff 给 `GSDT-nbr-*` / `GSDT-gov-*` / `GSDT-ver-*`

# Versioning

- 当前版本：`0.1.0`
- 当前状态：`draft`
- 进入 `stable` 前至少应完成一轮真实 skill 生产验证
- 重要变更应在 Git history 中可追溯，并补充 compatibility notes

# Lifecycle

- `draft`: 当前阶段，用于建立首版母规范
- `experimental`: 已用于少量 skill 生产，仍在调优
- `stable`: 已支撑多类 skill 生产且规则基本稳定
- `deprecated`: 被新的 skill production protocol 替代
- `archived`: 仅保留历史参考价值
