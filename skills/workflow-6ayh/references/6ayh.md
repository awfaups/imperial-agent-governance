# 6AYH Workflow

## When to use

Use when the task is clearly about gradual optimization, refactoring, performance work, or reducing maintenance cost without a big rewrite.

## Required documents

- `docs/[YYYY_MM_DD]_[中文任务名]_vN/01_ALIGNMENT_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/02_DESIGN_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/03_TASK_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/04_APPROVE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/05_ACCEPTANCE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/06_FINAL_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/07_TODO_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/99_REFERENCES_[中文任务名].md`

## Rules

- use the current date and append a bundle version, for example `docs/2026_04_16_首页优化_v1/`
- if the same feature is optimized again, increment to `v2`, `v3`, and so on
- initialize the doc skeleton before optimization work
- every optimization step must have rollback and validation
- any code-changing step must document target file paths, line ranges, and before/after code context

