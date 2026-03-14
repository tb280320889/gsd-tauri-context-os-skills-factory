# Appendix：Truth Source 与 Online Research Policy（种子版）

## 1. 真相源层级
- T0：accepted context docs / accepted TRD-like / ADR / contract
- T1：官方 MCP / 官方结构化入口
- T2：官方 docs / 官方 AI docs / 官方 llms.txt
- T3：项目内文档 / 代码 / 脚本 / 测试命令
- T4：logs / trace / replay / Sentry / runtime evidence
- T5：社区资料 / 社区 MCP / 第三方博客

## 2. 研究行为原则
- 有官方 MCP，优先官方 MCP
- 无官方 MCP，则优先官方 docs / AI docs / llms.txt
- 项目内真值高于网上找到的泛化建议
- 社区资料只能补强，不能覆盖官方入口
- 对时效性强内容要记录 freshness 与日期
- skill 中引用的研究结论应可通过 Git history 追溯其引入与修改背景

## 3. policy 与 adapter 的分离
### Policy Skill
- `online-research-official-first`
- 定义：何时搜索、搜什么、如何分级、如何引用、如何记录结论

### Provider Adapter Skill
- `tavily-remote-mcp-adapter`
- 定义：具体如何通过 Tavily Remote MCP 发起搜索/提取、默认参数、失败降级路径

## 4. 为什么不能把 provider 写成通用根规则
- provider 只是能力层，不是真值层
- provider 会更换，不应绑死根协议
- provider 的失败模式、配额、认证、时延都属于 adapter concern

## 5. 官方入口种子注册
建议在 truth-source-registry 中维护以下字段：
- ecosystem
- official_mcp
- official_docs
- official_ai_docs
- official_llms
- local_project_truth
- community_supplements
- status
- last_reviewed
- notes

## 5.1 与 skill registry 的关系
- truth source policy 是 policy layer，不直接替代 skill registry
- 具体 skill 通过 `skill_name` 与 `truth_sources` 字段引用真相源策略
- planner 选择 skill 时，应结合 `skill_name`、`truth_sources`、`status`、`skill_version` 判断是否适合当前 phase

## 6. 对本工厂相关生态的建议写法
- Svelte/SvelteKit：优先官方 MCP 与官方 llms/AI docs
- Tauri 2：优先官方 docs、tests、mocking、logging；社区 MCP 仅补强
- WXT：优先官方 docs 与官方 llms
- GitHub：优先官方 MCP
- Playwright：优先官方 MCP / 官方 docs
- Base：优先官方 MCP，其次官方 llms/docs
- TON/TMA：优先官方 docs，社区 MCP 降级为补强
- Solana：优先官方 MCP 与官方 docs
- Sentry：优先官方 docs / API / agent monitoring 资料

## 7. 命名与边界提醒
- provider adapter skill 不得承担 root policy 角色
- `GSDT-gov-online-research-official-first` 负责 policy
- `GSDT-adp-*` 负责具体 provider 接入
