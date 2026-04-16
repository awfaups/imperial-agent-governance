---
name: workflow-ppw
description: Standalone PPW workflow skill for project inventory and process clarification. Use when the task is already confirmed as PPW, the user explicitly requests @PPW, or the request is clearly about project inventory, asset mapping, current-state clarification, or process discovery. Produces dated and versioned workflow docs under the active project's root docs/YYYY_MM_DD_中文任务名_vN/ directory.
---

# Workflow PPW

Use this skill when the workflow type is already known to be `PPW`.

If the request still needs global intake, routing, or cross-role governance, enter through `@intake` first and use this skill as the workflow detail layer.

Activation response:

> ✅ 项目流程梳理工作流（PPW）已激活
> 当前阶段：A1 – 项目资产盘点（Inventory）

This skill enforces:

- inventory and process-clarification workflow only
- required docs as mandatory deliverables
- docs under `docs/YYYY_MM_DD_中文任务名_vN/`
- fact-based output instead of speculative conclusions

Read next: `references/ppw.md`
