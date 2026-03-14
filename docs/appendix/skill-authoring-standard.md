# Appendix：Skill Authoring Standard（种子版）

## 1. 目的
本标准用于约束本工厂中的 skill 写法，使 skill 成为可注入、可验证、可演化的控制平面单元，而不是失控的知识包。

## 2. 每个 skill 最小应包含的内容
1. 触发条件
2. 适用角色
3. 适用 phase
4. 允许真相源与优先级
5. 执行规则
6. 输出契约
7. 验证要求
8. 禁止越界项
9. 邻域 skill 与 handoff 条件
10. Git 版本字段与生命周期状态

## 2.1 命名规范
本工厂 skill 统一采用：

- `GSDT-<family>-<domain>-<capability>`
- 必要时允许：`GSDT-<family>-<domain>-<capability>-<variant>`

其中：

- `GSDT`：项目统一前缀
- `family`：`anc` / `dom` / `nbr` / `gov` / `meta` / `adp` / `ver`
- `domain`：领域或主对象
- `capability`：能力名
- `variant`：可选变体

禁止通过目录名表达 skill 的正式语义。
正式语义必须由 `skill_name` 与 registry metadata 承担。

## 3. `SKILL.md` 推荐结构
- frontmatter: `name`, `description`, `skill_version`, `status`
- 角色与任务
- 输入与 phase 条件
- 真相源优先级
- 执行规则
- 输出契约
- 验证与失败证据
- 禁止越界项
- 邻域 skill 与升级/降级路径
- references 导航

## 4. 重要写法原则
- 控制平面优先，长知识下沉 references
- 写“何时触发”，不是只写“这个 skill 讲什么”
- 写“不要做什么”，不是只写“可以做什么”
- 写“退出时要留下什么”，不是只写“执行步骤”
- 对需要在线搜索的 skill，必须区分 policy 与 provider adapter
- 中文为主，英文强调关键术语
- 命名、版本、生命周期、兼容性必须显式可读

## 5. 输出模式
### 刚性输出适用场景
- phase handoff
- verify report
- failure evidence report
- readiness review

### 柔性输出适用场景
- strategy memo
- architecture notes
- comparative analysis

## 6. 资源组织建议
- `SKILL.md`: 控制平面
- `references/`: 真相源索引、补充细节、术语表
- `templates/`: 输出模板
- `examples/`: 高价值少量示例
- `checks/` / `scripts/`: 校验与自动化逻辑

## 7. 生命周期建议
- draft
- experimental
- stable
- deprecated
- archived

## 7.1 Versioning 建议
- 每个 skill 必须纳入 Git 管理
- `skill_version` 应与 Git history 或 release note 可追溯关联
- 重要升级要记录 compatibility notes
- experimental skill 必须记录风险与退出条件

## 8. 评测建议
每个 skill 至少维护：
- 1 个黄金样例
- 1 个边界样例
- 1 个越界防护样例
- 1 个输出契约检查点

## 9. 推荐语言风格
- 说明正文以中文为主
- 以下重点字段建议保留英文：
  - `Trigger`
  - `Scope`
  - `Boundary`
  - `Output Contract`
  - `Verification`
  - `Handoff`
  - `Versioning`
  - `Lifecycle`
