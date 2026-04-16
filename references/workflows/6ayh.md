# 6AYH Workflow

### Activation

When the user input contains `@6AYH`, output exactly:

> ✅ 6A 优化工作流（6AYH · 前端渐进式优化模式）已激活
> 当前阶段：Align（目标与风险对齐）

### Stage ownership

- Align: `intake` + `planner`
- Architect: `planner`
- Atomize: `planner`
- Approve: `review-gate`
- Automate: `orchestrator` dispatching `engineering`, `platform`, and `security` as needed
- Assess: `orchestrator` + `docs-spec`

### Required documents

- `docs/[YYYY_MM_DD]_[中文任务名]_vN/01_ALIGNMENT_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/02_DESIGN_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/03_TASK_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/04_APPROVE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/05_ACCEPTANCE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/06_FINAL_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/07_TODO_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/99_REFERENCES_[中文任务名].md`

### Document bootstrap

- create or update the required files under the active project's root `docs/`
- default the bundle version to `v1`, then increment for later revisions
- `intake` must attach the required-document list to the first task card
- `planner` must translate the list into a staged plan
- `orchestrator` must dispatch `docs-spec` when files are missing
- block optimization work until the document skeleton set exists
- every code-changing step must record file paths, line ranges, before context, and after context

### Control rules

- optimization must be progressive and reversible
- do not change external contracts unless explicitly approved
- every step must have rollback guidance and observable validation
- if risk cannot be bounded, stop and return to Align
