# 跨端 App · GSD Context OS Skills Factory 文档包

本包用于沉淀以下三类核心产物：

1. 设计母稿（新的项目定性、分层、协议、治理与演进路线）
2. M0-MX 开发大纲（按里程碑推进 skill factory 的建设顺序）
3. skill 开发方法论文档（用于跨 session / 跨 agent 保持原则稳定）
4. beads 工作流文档（用于任务、依赖、进度跟踪）
5. 各 M 阶段 TRD-like 文档（用于后续切分 phase、分派 planner / executor / verifier）

当前补充约束：

- skill 的发现方式以统一命名与 registry metadata 为主，而不是目录结构
- skill 必须带项目统一前缀，例如 `GSDT-*`
- skill 必须纳入 Git 管理并具备版本可追溯性
- skill 文风采用中文为主、英文强调关键术语
- 项目优先建设 `GSDT-anc-using-GSDT` 与 `GSDT-meta-GSD-skill-creator`
- 本仓库未来会作为其他 GSD 项目的 submodule / vendored toolkit 被引入
- `using-*` skill 会承担仓库级与领域级的双层索引职责

## 文件索引

- `00-design-mother-draft.md`
- `01-M0-MX-skill-development-outline.md`
- `02-skill-development-methodology.md`
- `03-beads-workflow-guide.md`
- `trd/M0-trd-like.md`
- `trd/M1-trd-like.md`
- `trd/M2-trd-like.md`
- `trd/M3-trd-like.md`
- `trd/M4-trd-like.md`
- `trd/M5-trd-like.md`
- `trd/MX-trd-like.md`
- `appendix/skill-authoring-standard.md`
- `appendix/truth-source-and-research-policy.md`
- `appendix/skill-registry-seed.md`

## 上下文体系

为了让后续你和其他 agent 在全新上下文下，仍然能按 `M0 -> M1 -> M2 -> ...` 的方式持续开发 skills，
本仓库引入专用的 `.gsdt-context` 上下文体系：

- `.gsdt-context/GLOBAL-CONTEXT.md`：长期稳定的项目真值与全局规则
- `.gsdt-context/ROADMAP-AND-PROGRESS.md`：跨 session 的路线图与进度快照
- `.gsdt-context/milestones/M0-CONTEXT.md`
- `.gsdt-context/milestones/M1-CONTEXT.md`
- `.gsdt-context/milestones/M2-CONTEXT.md`
- `.gsdt-context/milestones/M3-CONTEXT.md`
- `.gsdt-context/milestones/M4-CONTEXT.md`
- `.gsdt-context/milestones/M5-CONTEXT.md`
- `.gsdt-context/milestones/MX-CONTEXT.md`

其中：

- `AGENTS.md` 保持精简，只放所有 agent 都必须读到的最小硬规则
- milestone context 承担分阶段长期信息，避免在新上下文中丢失关键开发约束
- 当前 phase 文档承担当前小批次迭代目标与注入结果
- 之所以不用 `.planning` 作为本仓库主目录，是为了避免与消费方 GSD 项目的 workflow 目录语义冲突

## 使用建议

- `00` 作为总设计母稿，可作为 Project-Researcher / Planner 的高层输入之一。
- `01` 作为项目群级开发大纲，用于排布 M0-MX 的推进顺序。
- `trd/` 目录下文档用于具体 milestone 的 phase 拆分与 handoff。
- `appendix/` 目录用于约束 skill 写法、真相源分级、在线研究策略与 skill 注册表种子结构。

## 推荐落地方式

- 模板仓引入该文档包中的原则后，再把其中可执行部分转译为实际 skill。
- 产品仓只消费经 planner 按 phase 注入的 skill，不直接消费本母仓的全量文档。
- 本仓库先完成 skills 的设计、规划、规范与建造，再由外层桥接指引接入具体消费方项目。
