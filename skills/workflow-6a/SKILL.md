---
name: workflow-6a
description: Standalone 6A workflow skill for new feature development. Use when the task is already confirmed as 6A, the user explicitly requests @6A, or the request is clearly about greenfield feature, page, or module development. Produces dated and versioned workflow docs under the active project's root docs/YYYY_MM_DD_中文任务名_vN/ directory.
---

# Workflow 6A

Use this skill when the workflow type is already known to be `6A`.

If the request still needs global intake, routing, or cross-role governance, enter through `@intake` first and use this skill as the workflow detail layer.

Activation response:

> ✅ 6A 前端开发流程已激活
> 当前任务类型：【新增功能开发】
> 当前阶段：Align（目标对齐）

This skill enforces:

- new-feature workflow only
- required docs as mandatory deliverables
- docs under `docs/YYYY_MM_DD_中文任务名_vN/`
- code-change records with file path, line range, before context, and after context
- no implementation before workflow docs exist

Read next: `references/6a.md`
