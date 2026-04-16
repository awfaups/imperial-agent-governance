# SDD Workflow

### Activation

When the user input contains `@sdd`, or clearly requests spec-driven development, output exactly:

> ✅ Spec-Driven Development 工作流（SDD）已激活
> 当前阶段：Spec（规格定义）

### Core principle

The specification is the source of truth. Plan, implementation, tests, and acceptance must derive from the approved spec bundle.

### Stage ownership

- Spec: `intake` + `planner`
- Plan: `planner`
- Approve: `review-gate`
- Execute: `orchestrator` dispatching `engineering`, `docs-spec`, `platform`, and `security` as needed
- Verify: `orchestrator` + `docs-spec`

### Required documents

- `docs/[YYYY_MM_DD]_[中文任务名]_vN/01_SPEC_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/02_PLAN_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/03_DESIGN_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/04_TASK_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/05_APPROVE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/06_IMPLEMENTATION_LOG_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/07_ACCEPTANCE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/08_FINAL_[中文任务名].md`

Recommended starter template:

- `references/templates/01_SPEC.template.md`

### Document bootstrap

- create or update the required files under the active project's root `docs/`
- default the bundle version to `v1`, then increment for reruns
- `intake` must place the required-document list and initial bundle version into the first task card
- `planner` must derive implementation from the approved spec instead of freehand planning
- `orchestrator` must block execution until `01_SPEC`, `02_PLAN`, and `05_APPROVE` exist
- initialize `01_SPEC` from `references/templates/01_SPEC.template.md`

### Code-change recording

If SDD touches code, record for every change target:

- file path
- line range
- before context
- after context
- why the change is required by the spec

### Self-run rule

SDD may continue from spec to plan to execution without repeated user prompts only when:

- the spec is explicit enough to derive tasks
- risk is bounded and review has passed
- code-change targets are documented
- the active project's `docs/` bundle has been initialized

If any condition fails, stop at the current stage and return to `intake` or `planner` with a blocking notice.
