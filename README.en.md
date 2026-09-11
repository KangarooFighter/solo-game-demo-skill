# Solo Game Demo Development Skill

**个人游戏demo开发Skill**

[中文](README.md) · English

[![GitHub stars](https://img.shields.io/github/stars/KangarooFighter/solo-game-demo-skill?style=social)](https://github.com/KangarooFighter/solo-game-demo-skill/stargazers) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**Build a game solo. Give your AI collaborators clear roles. Ship a playable demo.**

An instruction-based Codex skill for coordinating game design, code, art, verification, and delivery across tasks. It defines who edits what, when work can change hands, and what counts as done. It is not a game engine, a ready-made game, or a promise of bug-free games from one prompt.

## Four responsibilities, one playable result

| Role | Owns |
| --- | --- |
| 01 Design & coordination | Core loop, scope, task dispatch, decisions, and final acceptance |
| 02 Implementation & integration | Gameplay, interaction, AI where needed, audio, and functional tests |
| 03 Art & assets | Consistent visual resources, specifications, and integration notes |
| 04 Verification & delivery | Actual artifacts, relevant experience checks, packaging, and authorized version or release operations |

Four responsibilities do not mean four new windows every time. Reuse existing tasks and combine roles for small jobs. If task-management tools are unavailable, produce copyable briefs instead of claiming work was dispatched.

## What does it improve?

- **Overlapping edits** → One writer per shared file.
- **Everyone waiting for approval** → Conditional handoffs within authority already granted.
- **Conflicting status messages** → One current summary, with history kept separate.
- **Old tests passing a new release** → Evidence tied to its actual input revision.
- **Full regression for every tiny edit** → Verification proportional to change and risk.
- **Every task is “done,” but the game is not playable** → Finish a loop you can launch, play, conclude, and replay.

## Install

In a Codex environment with skill installation available, ask:

```text
Use $skill-installer to install skills/multi-thread-delivery
from https://github.com/KangarooFighter/solo-game-demo-skill.
```

The display name is **个人游戏demo开发Skill**. The invocation remains **`$multi-thread-delivery`** for compatibility with the earlier workflow. If a skill with that name is already installed, review the differences before updating it.

Alternatively, place `skills/multi-thread-delivery/` in the personal skill directory used by your client, not in your game's source root. Discovery varies by client; see the [official skill documentation](https://learn.chatgpt.com/docs/build-skills). This is not an officially curated skill or a published marketplace plugin.

## Start a demo

```text
Use $multi-thread-delivery to help me build a game demo.

Project location: your project directory
Core loop: what the player does and why it is fun, in a few sentences
Target platform: for example, macOS with keyboard and mouse
Engine: for example, Godot; keep the existing project's version
Must ship: a complete loop, opponents where needed, feedback, results, and retry
Out of scope: for example, networking, accounts, and complex progression

Use this conversation for design and coordination. Create three other tasks
for implementation and integration, art assets, and verification and delivery;
reuse matching tasks if they already exist.
Define file ownership, interfaces, and acceptance before working in parallel.
Preserve the existing project structure. Installation, pushing, and public
publishing require my explicit authorization for those actions.
```

For advice only, add “Design only: do not create tasks or modify files.” For an iteration, say “Reuse existing tasks; do not create new windows,” then specify the new requirements and rules that must remain unchanged.

## Chinese and English included

The skill loads one workflow in the user's language rather than both translations at once. Coordination, handoff templates, tool adaptation, and the game-demo guide are available in both languages. Godot is an example, not a required engine, model, or visual style.

[Skill entry point](skills/multi-thread-delivery/SKILL.md) · [English game workflow](skills/multi-thread-delivery/references/game-demo.en.md) · [中文游戏流程](skills/multi-thread-delivery/references/game-demo.zh-CN.md)

## Requirements and limits

Use an AI coding environment that can access the project and run its tools. User tasks, subagents, image generation, Git, and scheduled follow-ups depend on the host's capabilities and your authorization. A skill does not add missing tools, buy services, or guarantee execution while your computer is off.

Report rule tests, synthetic input, exported-app checks, and human playtesting separately. A screenshot does not establish audio quality, and a green assertion count does not establish an error-free run. Actual playtesting and judgment still matter.

This workflow grew out of repeated collaboration on a personal game prototype and independent scenario exercises. It is not a success-rate benchmark across all engines, clients, or projects. This repository shares the workflow only—not the original game's source, assets, private paths, or conversation history.

## Help improve it

Share stuck handoffs, unclear instructions, and real project experience in [Issues](https://github.com/KangarooFighter/solo-game-demo-skill/issues). Include your environment, expected and observed behavior, and a minimal reproduction. Remove secrets, private paths, and unpublished assets. If it helps you finish a playable demo, a Star is welcome.

[MIT License](LICENSE) · Copyright 2026 Brian Zhang (KangarooFighter)
