---
name: imperial-agent-governance
description: Portable Agent Skills package for a role-based multi-agent workflow using taizi, zhongshu, menxia, shangshu, and worker departments. Use when the user wants multi-agent orchestration, role-based delegation, planning-review-dispatch pipelines, imperial-role collaboration patterns, or explicitly uses @taizi as the only public entry token.
description_zh: 这是一个可移植的 Agent Skills 包，用于基于 taizi、zhongshu、menxia、shangshu 和执行部门的角色化多 Agent 工作流。当用户需要多 Agent 编排、基于角色的委派、规划-审议-调度流水线、朝廷式分工协作模式，或显式使用 @taizi 作为唯一公开入口时使用。
metadata:
  short-description: Portable imperial agent governance workflow
  short-description_zh: 可移植的朝廷式 Agent 治理工作流
---

# Imperial Agent Governance
朝廷式 Agent 治理工作流

This skill defines a portable multi-agent operating model based on the roles `taizi`, `zhongshu`, `menxia`, `shangshu`, and the worker departments.
这个 skill 定义了一套可移植的多 Agent 协作模型，核心角色为 `taizi`、`zhongshu`、`menxia`、`shangshu` 和各执行部门。

This is the only skill that needs to be published for the portable package.
这是通用主包里唯一需要发布的 skill。
It includes the former `taizi` entry behavior inside the main skill instead of relying on a second trigger skill.
它已经把原先单独 `taizi` 入口 skill 的行为并入主 skill，不再依赖第二个触发 skill。

This package is designed to work as a self-contained Agent Skills package.
这个包被设计成一个自包含的 Agent Skills 包。
Do not assume Codex-specific global files such as `~/.codex/config.toml` or `~/.codex/AGENTS.md`.
不要假设运行环境一定有 `~/.codex/config.toml` 或 `~/.codex/AGENTS.md` 这类 Codex 专属全局文件。
Enforce role boundaries, routing rules, and workflow behavior through this skill and its references.
角色边界、路由规则和工作流行为，都应通过这个 skill 及其 references 自身来约束。

For bilingual files in this skill, prefer reading the English line first.
对于这个 skill 下的双语文件，优先读取英文行。
If the English content is already sufficient, skip the Chinese counterpart to save tokens.
如果英文内容已经足够，就跳过对应的中文内容以节省 token。
Read the Chinese counterpart only when exact Chinese wording is required or the English content is not enough.
只有在需要精确中文表述，或英文内容本身不够时，才读取对应的中文部分。
Treat Chinese lines as human-reference annotations by default, not as primary model context.
默认把中文行当作给人看的参考注释，而不是给模型读取的主上下文。

Use this skill when:
在以下场景使用这个 skill：

- the user wants multi-agent design or orchestration
- 用户需要多 Agent 设计或编排
- the user wants role-based delegation rules
- 用户需要基于角色的委派规则
- the user refers to imperial roles or ministry-based collaboration
- 用户提到朝廷式角色或六部协作
- the user wants a planner, reviewer, dispatcher, and worker split
- 用户需要规划、审议、调度、执行分层模型
- the user input contains `@taizi`
- 用户输入中包含 `@taizi`

Do not force this skill onto trivial single-step tasks.
不要把这个 skill 强行套到简单的一步式任务上。

## Workflow
工作流

### Entry rule
入口规则

`@taizi` is the only public entry token for this portable skill.
`@taizi` 是这个通用 skill 唯一允许的公开入口 token。
If the user input contains `@taizi`, treat that as explicit activation of this governance model.
如果用户输入中包含 `@taizi`，就把它视为显式启用这套治理模型。
No request may bypass directly to `zhongshu`, `menxia`, `shangshu`, or any worker department.
任何请求都不能直接绕过进入 `zhongshu`、`menxia`、`shangshu` 或执行部门。

Use this default path for substantial tasks:
对于重要任务，使用以下默认路径：

`taizi -> zhongshu -> menxia? -> shangshu -> worker(s) -> shangshu`

`taizi` must first classify the request into one of these internal modes:
`taizi` 必须先把请求归类到以下内部模式之一：

- `6A`: new feature development
- `6A`：新增功能开发
- `6AYH`: progressive optimization or refactor
- `6AYH`：渐进式优化或重构
- `PPW`: project inventory and process clarification
- `PPW`：项目盘点与流程梳理
- `generic governance`: all other substantial engineering tasks
- `generic governance`：其他需要工程治理的任务

If `taizi` auto-classifies the request as `6A`, `6AYH`, or `PPW`, output that workflow's activation response exactly as defined in the workflow references before continuing.
如果 `taizi` 自动将请求归类为 `6A`、`6AYH` 或 `PPW`，那么在继续之前，必须先按工作流参考文件中的定义原样输出对应激活响应语句。

### Stage guidance
阶段指引

- `taizi`: normalize the request, extract intent, assign title and tags
- `taizi`：规范化请求、提取意图、生成标题和标签
- `zhongshu`: decompose the task, define execution steps, choose likely worker departments
- `zhongshu`：拆解任务、定义执行步骤、选择可能参与的执行部门
- `menxia`: review for quality, risk, ambiguity, and policy fit; either reject to `zhongshu` or approve to `shangshu`
- `menxia`：从质量、风险、歧义和规则适配角度做审议；要么驳回给 `zhongshu`，要么批准给 `shangshu`
- `shangshu`: dispatch to workers, track returns, aggregate outputs
- `shangshu`：把任务派给执行部门、跟踪返回结果并做汇总
- workers: execute within their domain and return only to `shangshu`
- 执行部门：只在自己的职责范围内执行，并且只能把结果回给 `shangshu`

## Source of truth
事实来源

Read these reference files when you need precise behavior:
需要精确定义时，请读取以下参考文件：

- `references/agents.json`
- `references/role-permissions.md`
- `references/routing-rules.json`
- `references/task-card.schema.json`
- `references/role-prompts.json`
- `references/workflow-routing.json`
- `references/engineering-governance.md`
- `references/taizi-classification.md`

Read these workflow files when the selected internal mode needs them:
当选中的内部模式需要对应工作流细节时，请读取以下文件：

- `references/workflows/6a.md`
- `references/workflows/6ayh.md`
- `references/workflows/ppw.md`

## Routing policy
路由规则

Route from `shangshu` by tags:
由 `shangshu` 根据标签进行派单：

- code, bugfix, feature, algorithm, performance -> `bingbu`
- `code`、`bugfix`、`feature`、`algorithm`、`performance` -> `bingbu`
- docs, api, report, spec -> `libu`
- `docs`、`api`、`report`、`spec` -> `libu`
- data, cost, reporting, resource -> `hubu`
- `data`、`cost`、`reporting`、`resource` -> `hubu`
- security, compliance, audit -> `xingbu`
- `security`、`compliance`、`audit` -> `xingbu`
- deploy, cicd, tooling, automation -> `gongbu`
- `deploy`、`cicd`、`tooling`、`automation` -> `gongbu`
- agent, permission, training, registry -> `libu_hr`
- `agent`、`permission`、`training`、`registry` -> `libu_hr`

If no worker matches, return to `zhongshu` for replanning.
如果没有匹配到合适的执行部门，就回到 `zhongshu` 重新规划。

## Review policy
审议规则

Send the task through `menxia` when any of the following is true:
当满足以下任一条件时，任务必须经过 `menxia`：

- the task is high risk
- 任务风险较高
- the task spans multiple worker departments
- 任务跨多个执行部门
- the acceptance criteria are unclear
- 验收标准不清晰
- the task touches security, compliance, deployment, or permissions
- 任务涉及安全、合规、部署或权限

## Task-card requirements
任务卡要求

Use a structured task card rather than a loose message. Required fields:
使用结构化任务卡，而不是松散的自由文本。必填字段如下：

- `task_id`
- `title`
- `from`
- `to`
- `goal`
- `brief`
- `tags`
- `constraints`
- `deliverables`
- `review_required`
- `status`

## Output discipline
输出纪律

- record why each handoff happened
- 记录每次 handoff 发生的原因
- keep worker outputs scoped to their own domain
- 执行部门的输出必须严格限制在自身职责范围内
- aggregate final results in `shangshu`
- 最终结果必须由 `shangshu` 汇总
- do not let workers bypass the handoff graph
- 不允许执行部门绕过 handoff 图
- when a workflow needs a fixed activation response, output that response verbatim before continuing
- 当某个工作流要求固定激活响应时，必须先原样输出该响应再继续
- when in doubt about role boundaries, follow `references/role-permissions.md` before acting
- 当你不确定角色边界时，先遵循 `references/role-permissions.md` 再行动
- for bilingual references, avoid reading both language versions unless needed
- 对于双语参考内容，除非确有需要，否则不要同时读取两种语言版本
