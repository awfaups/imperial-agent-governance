# SDD Workflow
SDD 工作流

## Activation
激活规则

When the user input contains `@sdd`, or clearly requests spec-driven development, output exactly:
当用户输入中包含 `@sdd`，或明确要求规格驱动开发时，必须原样输出：

> ✅ Spec-Driven Development 工作流（SDD）已激活
> 当前阶段：Spec（规格定义）

## Core principle
核心原则

The specification is the source of truth. Plan, implementation, tests, and acceptance must derive from the approved spec bundle.
规格是事实源。计划、实现、测试和验收都必须从已批准的规格文档包派生。

## Stage ownership in the imperial model
在朝廷式模型中的阶段归属

- Spec: `taizi` + `zhongshu`
- Spec（规格定义）：`taizi` + `zhongshu`
- Plan: `zhongshu`
- Plan（计划设计）：`zhongshu`
- Approve: `menxia`
- Approve（审批）：`menxia`
- Execute: `shangshu` dispatching `bingbu`, `libu`, `gongbu`, `xingbu` as needed
- Execute（执行）：由 `shangshu` 根据需要调度 `bingbu`、`libu`、`gongbu`、`xingbu`
- Verify: `shangshu` + `libu`
- Verify（验证）：`shangshu` + `libu`

## Required documents
必需文档

- `docs/[YYYY_MM_DD]_[中文任务名]_vN/01_SPEC_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/02_PLAN_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/03_DESIGN_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/04_TASK_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/05_APPROVE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/06_IMPLEMENTATION_LOG_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/07_ACCEPTANCE_[中文任务名].md`
- `docs/[YYYY_MM_DD]_[中文任务名]_vN/08_FINAL_[中文任务名].md`

Recommended starter template:
推荐起始模板：

- `references/templates/01_SPEC.template.md`

## Document bootstrap
文档初始化规则

When SDD is selected, these files must be created or updated under the current active project's root `docs/` directory before implementation starts.
当选中 SDD 时，必须先在当前打开项目根目录下的 `docs/` 目录中创建或更新这些文件，然后才能开始实施。

- use the current date as a directory prefix and append a bundle version, for example `docs/2026_03_23_支付重构_v1/`
- 目录名前缀必须使用当前日期并追加版本号，例如 `docs/2026_03_23_支付重构_v1/`
- when the same topic is rerun, increment the bundle version to `v2`, `v3`, and so on
- 当同一主题再次运行时，目录版本号递增为 `v2`、`v3` 等
- `taizi` must put the required-document list and initial `document_bundle_version` into the first task card
- `taizi` 必须把必需文档清单和初始 `document_bundle_version` 写入首张任务卡
- `zhongshu` must derive implementation steps from the approved spec instead of freehand coding plans
- `zhongshu` 必须从已批准规格推导实施步骤，而不是脱离规格自由规划
- `shangshu` must block execution until `01_SPEC`, `02_PLAN`, and `05_APPROVE` exist
- `shangshu` 必须在 `01_SPEC`、`02_PLAN` 和 `05_APPROVE` 存在之前阻止进入执行
- initialize `01_SPEC` using `references/templates/01_SPEC.template.md`
- 初始化 `01_SPEC` 时应优先使用 `references/templates/01_SPEC.template.md`

## Code-change recording rules
代码变更记录规则

If SDD touches code, the docs must record each change target with:
如果 SDD 涉及代码修改，文档必须为每个改动目标记录：

- target file path
- 目标文件路径
- line range
- 行号范围
- before code context
- 修改前代码上下文
- after code context
- 修改后代码上下文
- why the change is required by the spec
- 为什么该改动由规格要求产生

## Self-run rule
自跑规则

SDD may continue from spec to plan to execution without repeated user prompts only when:
只有在以下条件成立时，SDD 才能在不反复等待用户补充的情况下，从规格推进到计划再推进到执行：

- the spec is explicit enough to derive tasks
- 规格足够明确，能够推导出任务
- risk is bounded and review has passed
- 风险有边界，且已通过审议
- code-change targets are documented
- 代码改动目标已经被文档化
- the active project's `docs/` bundle has been initialized
- 当前项目的 `docs/` 文档包已经初始化

If any of the above is false, stop at the current stage and return to `taizi` or `zhongshu` with a blocking notice.
如果以上任一条件不成立，就在当前阶段停止，并带着阻塞说明回退到 `taizi` 或 `zhongshu`。
