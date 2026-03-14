# GSD Context OS Skill Factory

该目录用于承载可注入、可验证、可演化、可 Git 版本化的 skill 控制平面定义。

## 当前规则

- skill 通过统一命名与 registry metadata 发现，不通过目录发现
- 正式命名使用：`GSDT-<family>-<domain>-<capability>[-<variant>]`
- 文风采用中文为主、英文强调关键术语
- 本仓库当前处于 skills 的设计、规划、规范与建造阶段
- 后续由消费方项目中的 planner 把 skill 注入其自身 phase 文档
- skill 注册表位于 `skills/registry.yaml`

## 当前优先级（M0）

- `GSDT-anc-using-GSDT`
- `GSDT-meta-GSD-skill-creator`
- naming / registry / versioning / injection rules

## 目录说明

当前目录结构仅作为存储便利层，不作为语义索引层。

- `skills/`
- `skills/registry.yaml`

是否使用某个 skill，必须先看：

1. `AGENTS.md`
2. `.gsdt-context/GLOBAL-CONTEXT.md`
3. `.gsdt-context/milestones/<M>-CONTEXT.md`
4. `skills/registry.yaml`
5. 对应 `SKILL.md`

## 设计原则

- Skill 只承载控制平面，长知识下沉到 references。
- 对消费方项目而言，accepted context docs / phase docs > planner 注入 skill > 根规则说明。
- 每个 skill 必须定义 `Trigger`、`Boundary`、`Output Contract`、`Verification`、`Handoff`、`Versioning`。
- 每个 skill 必须纳入 Git 管理，并具备可追溯版本语义。
