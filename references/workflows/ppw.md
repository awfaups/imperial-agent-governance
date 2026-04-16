# PPW Workflow

### Activation

When the user input contains `@PPW` or clearly requests project-process inventory, output exactly:

> ✅ 项目流程梳理工作流（PPW）已激活
> 当前阶段：A1 – 项目资产盘点（Inventory）

### Stage ownership

- A1 Inventory: `intake` + `platform`
- A2 Goals: `planner`
- A3 Flows: `planner` + `docs-spec`
- A4 Contracts: `planner` + `docs-spec`
- A5 Risks: `review-gate` + `security`
- A6 Gaps: `planner` + `data-ops`
- A7 Sign-off: `orchestrator` + `docs-spec`

### Required documents

- `docs/[YYYY_MM_DD]_[中文任务名]_vN/01_INVENTORY.md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/02_GOALS.md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/03_FLOWS.md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/04_CONTRACTS.md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/05_RISK_REGISTER.md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/06_ROADMAP.md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/07_CONSENSUS.md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/08_DECISIONS.md`

### Document bootstrap

- create or update the required files under the active project's root `docs/`
- default the bundle version to `v1`, then increment for revisits
- `intake` must place the required-document list into the first task card
- `planner` must turn the list into a phased project-document plan
- `orchestrator` must dispatch `docs-spec` when files are missing
- do not move beyond A1 while the project fact base is still missing

### Control rules

- record facts, verified information, and explicit decisions only
- do not invent roadmap items without evidence
- if critical repositories, environment config, or secret provenance are missing, stop before A2
