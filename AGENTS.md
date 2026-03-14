# AGENTS.md

## Mission

本仓库是一个面向 `GSD + Tauri2 跨端 App` 项目的 skills 工具集工厂。
它会在后续作为 submodule / vendored toolkit 被多个 GSD 项目引入，用于给 planner 提供统一的 skills 发现、选择、注入与维护规则。

## Read Order

所有 agent 进入本仓库后，默认按以下顺序理解上下文：

1. `AGENTS.md`
2. `.gsdt-context/GLOBAL-CONTEXT.md`
3. `.gsdt-context/ROADMAP-AND-PROGRESS.md`
4. `.gsdt-context/milestones/<M>-CONTEXT.md`
5. 当前 phase 文档
6. 被 planner 注入的 skill 闭包

## Core Rules

1. Skill discovery is **name-and-registry driven**, not directory-driven.
2. Skill injection is **planner-led**.
3. Planner 必须把选中的 skills 写入当前 phase 文档。
4. Executor / Debugger / Verifier 默认只消费当前 phase 文档中的 injected skill set。
5. 项目 accepted context docs / phase docs 永远高于任何 skill 文稿。
6. 本仓库当前处于“skills 的设计、规划、规范与建造”阶段；你和用户默认处于架构师/设计师角色。
7. 创建新 skill 前，优先复用 official MCP / official skill / official docs / `llms.txt` / 高质量开源实践。
8. 每个 milestone 开发必须尽量保持独立上下文，避免长上下文污染。
9. 任何重要决策、方法论、优先级调整、阶段进度都必须回写到对应 context docs，不能只停留在临时对话中。

## Naming Convention

所有正式 skill 必须命名为：

- `GSDT-<family>-<domain>-<capability>`
- 或 `GSDT-<family>-<domain>-<capability>-<variant>`

其中 `family` 使用：`anc` / `dom` / `nbr` / `gov` / `meta` / `adp` / `ver`。

禁止：

- 按目录结构推断 skill 语义
- 使用不带 `GSDT-` 前缀的正式 skill 名称

## Planner Workflow

1. 读取 `.gsdt-context/GLOBAL-CONTEXT.md` 与对应里程碑上下文。
2. 读取当前 phase 目标、边界、约束、版本批次。
3. 选择 `1` 个 primary `GSDT-dom-*` skill。
4. 按需选择 `0-N` 个 `GSDT-nbr-*` / `GSDT-gov-*` / `GSDT-ver-*` / `GSDT-adp-*`。
5. 记录显式排除项。
6. 将结果写入当前 phase 文档。

## Injection Constraints

默认每个 phase 只应注入最小 skill 闭包：

- `1` 个 primary `GSDT-dom-*`
- `0~3` 个 `GSDT-nbr-*`
- `0~2` 个 `GSDT-gov-*` / `GSDT-ver-*`
- `GSDT-anc-using-GSDT` 可作为常驻使用说明 skill 被引用

## Versioning

- 所有 skill 必须受 Git 管理
- 所有 skill 必须具备 `skill_version` 或等价版本字段
- 重要变更必须可通过 Git history / notes 追溯

## Current Focus

优先建设：

1. `GSDT-anc-using-GSDT`
2. `GSDT-meta-GSD-skill-creator`
3. using-* 二层索引体系
4. naming / registry / versioning / milestone context system

## Landing the Plane (Session Completion)

**When ending a work session**, you MUST complete ALL steps below. Work is NOT complete until `git push` succeeds.

**MANDATORY WORKFLOW:**

1. **File issues for remaining work** - Create issues for anything that needs follow-up
2. **Run quality gates** (if code changed) - Tests, linters, builds
3. **Update issue status** - Close finished work, update in-progress items
4. **PUSH TO REMOTE** - This is MANDATORY:
   ```bash
   git pull --rebase
   bd sync
   git push
   git status  # MUST show "up to date with origin"
   ```
5. **Clean up** - Clear stashes, prune remote branches
6. **Verify** - All changes committed AND pushed
7. **Hand off** - Provide context for next session

**CRITICAL RULES:**
- Work is NOT complete until `git push` succeeds
- NEVER stop before pushing - that leaves work stranded locally
- NEVER say "ready to push when you are" - YOU must push
- If push fails, resolve and retry until it succeeds
