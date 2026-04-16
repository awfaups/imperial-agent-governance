# SDD Workflow

## Core principle

The specification is the source of truth. Plan, implementation, tests, and acceptance must derive from the approved spec bundle.

## Required documents

- `docs/[YYYY_MM_DD]_[中文任务名]_vN/01_SPEC_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/02_PLAN_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/03_DESIGN_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/04_TASK_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/05_APPROVE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/06_IMPLEMENTATION_LOG_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/07_ACCEPTANCE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/08_FINAL_[中文任务名].md`

## Rules

- use the current date and append a bundle version, for example `docs/2026_04_16_支付重构_v1/`
- if the same topic is rerun, increment to `v2`, `v3`, and so on
- initialize `01_SPEC` using the bundled template
- block implementation until `01_SPEC`, `02_PLAN`, and `05_APPROVE` exist
- if code changes are planned or completed, record target file paths, line ranges, before context, and after context
- stop and return for clarification if the spec is not strong enough to derive tasks

