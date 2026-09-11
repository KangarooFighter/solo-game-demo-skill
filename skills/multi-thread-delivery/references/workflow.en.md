# Solo Game Demo Development Skill — Workflow

Organize parallel work into a delivery team with clear outputs, dependencies, and a finish line. The default responsibilities are coordination and design, implementation and integration, specialist deliverables, and verification and release. They do not require four new task windows, particular models, a fixed technology stack, or a prescribed directory layout. Follow the user's choice of roles and team size.

## Identify the requested mode

- **Design or package a collaboration workflow:** Deliver the workflow or skill. Do not also start the project, create tasks, change code, or reorganize files.
- **Start or continue project collaboration:** Inspect the existing project, tasks, and authorization; establish the minimum current state; then delegate work that can progress independently.
- **Resume interrupted work or check progress:** Recover the facts first and preserve completed work. A status request does not itself authorize changes or publication.
- **Handle a small task:** When coordination would cost more than it saves, check the relevant responsibilities and finish in the current task. Explain that additional windows are unnecessary.

This skill does not require a project to add `docs/`, `.agents/`, a board, or CI. It does not move or rename existing files, install software automatically, or change global settings. Reuse existing coordination documents. If the user prohibits project writes, keep the current state and assignments in the coordinating conversation or an external location the user has already specified. The skill itself is not a state store across projects.

## 1. Establish the minimum current state

Read applicable `AGENTS.md` files, project guidance, relevant entry points, and workspace changes, limited to what this round needs. Find existing related tasks. Do not infer a task's identity from its title or reuse task IDs from another project. Record:

- The project, round, bounded objective, and what must be preserved, explicitly replaced, or excluded.
- Each role's actual task ID, working directory or worktree, owner, and writable paths.
- Task status, dependencies, interface versions, and the applicable source, document, or asset baseline.
- Shared resource holders, accepted evidence, the next action, and any missing user authorization.

Maintain **one authoritative summary of the current state**. Keep earlier rounds and failed attempts as separate historical references. Update the summary directly instead of appending statements that earlier content has been superseded. The coordinator maintains it; other roles report changes back. Link large logs and summarize their key conclusions.

Read [handoffs.en.md](handoffs.en.md) before the first actual assignment. Read [codex-tools.en.md](codex-tools.en.md) before using task coordination tools or resuming interrupted work.

## 2. Assign roles and define parallel work

| Responsibility | Accountable for | Main boundary |
| --- | --- | --- |
| 01 Coordination and design | Requirements, contracts, critical path, conflict resolution, acceptance, and the final response | Do not duplicate all implementation work; reassign file ownership before taking over code. |
| 02 Implementation and integration | Core functionality, interface adaptation, tests, and integration of specialist outputs | Give shared integration entry points one owner; multiple roles must not edit the same shared files concurrently. |
| 03 Specialist deliverables | The UI, art, data, research, content, or other outputs the project actually needs | Write within agreed paths or provide standalone deliverables; specify requirements, provenance, and integration instructions. |
| 04 Verification and release | Risk review, builds and packaging, versions, and delivery checks | Prepare verification early when possible; release and external actions depend on actual authorization. |

The current task usually handles role 01. A single user task may combine a few responsibilities. An independent subagent can review high-risk work without requiring a permanent fifth window. Reuse existing tasks first. Create a new user-visible task only when the user explicitly requests one. Use available subagent tools for bounded internal work; a subagent is not the same as a new user-visible task.

Divide work into independently acceptable outputs. Parallelize preparation and implementation where conflicts are unlikely. Dependent owners can continue against agreed interfaces. Do not invent assignments merely to keep everyone busy. Owners may clarify interfaces directly, but must notify the coordinator and affected parties before changing scope, contracts, shared baselines, or release conditions.

## 3. Manage files and shared resources

In a shared workspace, each file or generated directory has one writing owner at a time. A designated integrator edits shared entry points and performs integration. Other roles provide independent files or proposed changes. Record existing uncommitted user changes and work around them or resolve overlapping ownership; do not claim them as part of your own delivery.

For separate worktrees, specify the starting baseline, output branch or commit, and merge order. Passing checks in a worktree does not mean the integrated version passes. Do not assume files are automatically shared between tasks. Preserve the user's chosen local working mode; do not move existing tasks merely to apply this skill.

Serialize only resources that actually conflict: the same Git index or worktree switch, import cache, database migration, test device, occupied port, or UI session. Independent directories and devices do not need a global lock; unrelated documentation and static review can continue. Record the holder, operation scope, release conditions, and processes you started. A timeout does not authorize killing an unknown process or taking another owner's write access.

## 4. Assign work and agree on conditional handoffs

Every assignment includes at least an ID and revision, objective, input baseline, writable and forbidden paths, dependencies, observable acceptance criteria, and a completion report. Avoid assignments such as “keep improving.” Dependencies must refer to real prerequisite outputs and must not create circular waits.

Within the user's existing authorization, agree on **conditional handoffs in advance**. For example: “Once interface checks pass and assets are available, 02 may integrate the specified entry point”; or “Once editors release the candidate, 04 may package it under the agreed gates.” Technical gates do not grant new permissions. The coordinator may pass on only authorization already granted by the user. Resolve any new permission needed for remote pushes, public releases, installation, or overwrites before that action; passing tests does not imply it.

In one message, the sender states completed facts, supporting evidence, and what the recipient may do next. Do not describe a handoff as both complete and still awaiting approval. A sufficiently authorized handoff needs no extra confirmation round. A tool accepting an assignment does not establish that the work is complete. If the recipient's first action reveals an environment or baseline mismatch, report it before proceeding.

## 5. Communicate, wait, and recover

Associate messages with the task ID and revision. Report events: work started, an interface changed, a dependency became ready, a blocker appeared, work is ready for acceptance, or work finished. Show the user meaningful design decisions, progress, risks, and results. Avoid repeated acknowledgments, raw logs, and unchanged polling updates.

The coordinator may dispatch independent assignments in a batch and wait using returned cursors. Continue other useful coordination work while dependencies run. Do not periodically resend identical authorization, broadcast unrelated messages to every role, or trigger all tasks after completion just to collect acknowledgments. Write necessary shared state updates once.

Distinguish communication interruptions, execution failures, and missing user authorization. Before resuming, check task status, existing outputs and processes, the latest revision, and the last outer process exit status. Send the original owner one recovery message with the differences and next action. Do not start a duplicate writer until the earlier execution is confirmed to have ended. Keep reports that do not match the current baseline as historical evidence; they cannot trigger new integration or release.

## 6. Verify according to the changes

Before implementation, define bounded completion criteria and verification proportional to risk. Do not copy test counts, fixed screenshot counts, or an entire release ceremony from another project. Role reports must distinguish at least “written,” “run,” “verified,” and “delivered.”

The verification record identifies actual input versions, commands or actions, outer completion status, key output, original logs or results, coverage, and limitations. Passing assertions do not prove that execution had no errors. A success field inside a script does not replace the actual process exit status. Describe real deliverables, controlled fixtures, synthetic inputs, default environments, and human usability checks separately; none substitutes for another. Do not simply add the counts of overlapping checks.

Reuse passing evidence when its inputs, dependencies, and environment are unchanged. Rerun the relevant scope when there are new changes, failures, integration differences, or a specific unresolved concern. Do not lower new acceptance criteria to preserve an earlier pass count. When distributing a new rules revision, identify which earlier checks remain applicable, which are superseded, and which must be added.

Independent review focuses on contracts, high-risk boundaries, and actual deliverables. Do not ask every role to repeat the same full suite. Verify a final package or target environment only when packaging or deployment is part of the objective; do not impose executable application acceptance on a writing-only task. Preserve original failure evidence and the new run after revision, with retention proportional to risk. Committing every screenshot and auditing every blob are not default requirements for every project.

## 7. Close the round at a defined endpoint

Before completion, check the actual deliverables, operating or usage instructions, relevant verification, unfinished scope, and the version or release status the user requested. Establish authorization, destination, and results separately for Git commits, tags, and remote pushes. If no remote exists, do not invent an address or create a public repository. Complete authorized local delivery and accurately report any unfinished external publication.

Use a candidate snapshot or release freeze to prevent deliverables changing during verification. A freeze has a scope and release conditions; it must not permanently block later iterations. Switch the stable entry point only when that action was already authorized and its gates pass. Retain a rollback path proportional to risk.

Once this round's completion criteria are met, give one self-contained response covering the result, entry point, important limitations, and release status. Release resources you hold. Stop only automated follow-ups that are complete and belong to this round; leave unrelated automations alone. A roadmap does not authorize another implementation round. An acknowledgment with no new facts after the final response does not call for another announcement of completion.
