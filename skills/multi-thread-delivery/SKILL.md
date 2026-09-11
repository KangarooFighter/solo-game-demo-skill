---
name: multi-thread-delivery
license: MIT
description: "个人游戏demo开发Skill / Solo Game Demo Development Skill. Coordinate game-demo development across AI tasks: design, implementation, art, QA, and delivery. Use for multi-task project coordination and reusable handoffs; do not expand simple edits or advice-only requests into a new project."
---

# 个人游戏demo开发Skill

**Solo Game Demo Development Skill** · Invocation: `$multi-thread-delivery`

Help a solo creator organize design, implementation, art, and verification into a playable demo. This is an instruction-based workflow, not an engine, autonomous hosting service, or promise of bug-free games. The existing invocation name is retained for compatibility.

## Language / 语言

Use the user's language. Read **one complete workflow** before acting; do not load both translations unless comparing them:

- 中文：[协作流程](references/workflow.zh-CN.md)。
- English: [Coordination workflow](references/workflow.en.md).

When dispatching work or restoring a task, read the matching [Chinese handoffs](references/handoffs.zh-CN.md) / [English handoffs](references/handoffs.en.md) and [Chinese tool guide](references/codex-tools.zh-CN.md) / [English tool guide](references/codex-tools.en.md) as the workflow directs.

For game-demo implementation, additionally read the matching [中文游戏流程](references/game-demo.zh-CN.md) / [English game workflow](references/game-demo.en.md). For an advice-only request, read only what is needed to deliver advice; do not begin development.

## Essential boundaries / 核心边界

- Follow the user's requested scope, engine, model, role count, and language. Four responsibilities do not require four newly created windows.
- Reuse existing project tasks. Create user-visible tasks only when the user explicitly asks; use available subagents for bounded internal work.
- Keep existing project structure. Do not create coordination directories, install dependencies, move files, or publish anything merely because this skill is active.
- Assign one writer per shared file; isolate only genuinely conflicting resources. Handoffs do not grant new user permissions.
- Keep one current status summary, attach results to their real input revision, verify proportionally, and finish the agreed deliverable.
- No tools means no claimed dispatch. No live evidence means no claim of testing, deployment, human playtesting, or background execution.
