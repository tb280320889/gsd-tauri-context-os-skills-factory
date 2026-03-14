# Appendix：Skill Registry Seed（种子结构）

## 1. 分类
### Anchor
- GSDT-anc-using-GSDT
- GSDT-anc-gsd-root-router
- GSDT-anc-project-researcher
- GSDT-anc-phase-planner

### Governance
- GSDT-gov-minimal-2oss
- GSDT-gov-global-architecture
- GSDT-gov-docs-governance
- GSDT-gov-truth-source-registry
- GSDT-gov-skill-registry-index
- GSDT-gov-skill-lifecycle-governance
- GSDT-gov-release-community
- GSDT-gov-oss-governance

### Domain
- GSDT-dom-frontend-sveltekit
- GSDT-dom-host-wxt
- GSDT-dom-host-tauri2
- GSDT-dom-backend-axum
- GSDT-dom-data-sqlite-sqlx
- GSDT-dom-data-surreal
- GSDT-dom-chain-base
- GSDT-dom-chain-ton-tma
- GSDT-dom-chain-solana

### Cross-boundary
- GSDT-nbr-integration-cross-boundary
- GSDT-ver-verify-evidence
- GSDT-gov-online-research-official-first
- GSDT-adp-research-tavily-remote-mcp
- GSDT-nbr-wallet-boundary-patterns
- GSDT-ver-onchain-verify-safety

### 2Agent
- GSDT-dom-2agent-headless
- GSDT-dom-2agent-cli
- GSDT-dom-2agent-mcp
- GSDT-dom-2agent-native
- GSDT-ver-2agent-readiness-review
- GSDT-nbr-phase-handoff-contracts

### Meta
- GSDT-meta-GSD-skill-creator

## 2. 每个 skill 建议维护字段
- skill_name
- skill_version
- family
- domain
- capability
- stage_target
- status
- trigger
- visible_to
- hidden_from
- depends_on
- conflicts_with
- truth_sources
- outputs
- verification
- handoff_to
- git_path
- compatibility_notes
- last_reviewed
- notes

## 3. 冲突处理建议
1. accepted context docs 高于任何 skill
2. planner 注入的 phase skill 高于常驻 governance skill
3. Root Skill 只做路由，不覆盖领域判断
4. policy 高于 adapter
5. domain skill 不得覆盖项目真值
6. integration skill 不得回收领域内部实现控制权

## 4. 发现原则
- 发现顺序应优先依赖 `skill_name`、`family`、`domain`、`capability`
- `git_path` 只用于定位文件，不用于表达正式语义
- 不允许根据目录命名推断 skill 的选择优先级
