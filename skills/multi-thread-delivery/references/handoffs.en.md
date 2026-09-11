# Reusable assignments and handoffs

Use these for initial assignments, interface changes, and recovery. Adjust the fields to the risk; a short task can combine several into one paragraph. Do not mechanically generate a document set. Prefer existing project records. If project writes are prohibited, keep the information in the coordinating conversation or a user-specified external location. These are message templates, not a required file tree.

## Current state summary

```text
Project / round: project identifier, round, current objective, bounded endpoint
Authorization: implementation / environment actions / local version actions / external release; mark unknowns
Rules: what to preserve, replace, and exclude
Baseline: actual commit or relevant file fingerprints; identify ownership of uncommitted changes
Role mapping: responsibility → task_id / host / actual directory or worktree
Tasks: ID@revision | owner | status | input contract | writable paths | dependencies
Shared resources: resource → holder / scope of use / release conditions
Valid evidence: object version → verification scope / result / original location / limitations
Next action: actor / conditions met / missing authorization or external dependency
```

Update the summary to reflect current facts. Keep historical references separate from current holders and freeze conditions. Natural-language role names are fine; numbered roles are optional. Another project must not inherit this summary's task IDs, paths, remotes, or permissions.

## Assignment

```text
Task: PROJECT-TASK@revision
Objective: an outcome the user can observe
Context: decisions and input references needed for this round, without copying the entire conversation
Environment: project / actual directory or worktree / input baseline and interface revision
May modify: precise files, directories, or standalone outputs
Must not modify: user changes, shared entry points, areas owned by other roles
Dependencies: the required output; work that can proceed while waiting
Acceptance: core success path, relevant failure paths, required delivery format
Authorized follow-up: may perform C when A/B are satisfied; external actions excluded from this authorization
Invalidation conditions: requirement / interface / baseline changes that require coordination before proceeding
Report: changes, actual runs and exit status, output paths, limitations, resource release, next owner
```

## Status and events

Suggested task states: queued → in progress → ready for acceptance → done. Mark execution failures or missing external conditions as blocked; mark work replaced by new rules as superseded. An unavailable shared device is a dependency, not proof that the entire project has failed. Every status needs a next action, not just the word “blocked.”

A useful message header is `Task ID@revision | event | recipient`. Events can include `STARTED / READY / HANDOFF / BLOCKED / CONTRACT_CHANGE / DONE`. These are conventions, not a protocol to install or native product commands.

```text
GAME-ASSETS@2 | HANDOFF | 02
Completed: icons and three state variants; the interface remains UI-2.
Evidence: actual asset paths, previews, check results, and the scope of those checks.
Baseline: fingerprints of this asset version; shared entry points were not changed.
Resources: preview process stopped and the agreed device released.
Next: under the existing authorization, 02 may integrate the assets into the specified components and run the relevant integration checks.
Limitations: narrow-screen and keyboard integration remain to be checked by 02 after integration.
```

The recipient can proceed under the existing authorization. The sender does not need to repeat “formally approved.” If authorization is insufficient, identify the specific action that lacks permission instead of asking every participant a broad “can we continue?”

## Changes and recovery

```text
Round revision changes from 2 to 3: what the new requirement changes; which constraints stay in effect.
Affected tasks: IDs; whether earlier outputs remain usable, need partial rework, or are superseded.
Shared files: where the previous owner must stop writing; when the next owner may begin.
Evidence impact: unchanged checks that remain reusable; affected checks that must be rerun.
Continuing authorization: previously authorized actions that remain valid; external actions that must pause.
```

A recovery message contains only the current summary and differences: the last verified completion point, current observations, and the next bounded action. Do not assert that the previous round succeeded without checking. When new input interrupts work, first distinguish a replacement requirement, an addition, and a progress question.

## Ready-to-use prompts

Creating user-visible tasks requires an explicit request to create them:

> Use $multi-thread-delivery to start my project. Keep coordination in this conversation and create three other independent tasks for implementation, specialist deliverables, and verification and release. Reuse matching tasks if this project already has them. The project location and objective are as follows… Preserve the existing directory structure. Define writable paths, interfaces, acceptance criteria, and conditional handoffs before starting work.

Iterating with an existing team:

> Use $multi-thread-delivery to organize the next round. Reuse this project's existing tasks without creating new windows. Change… Preserve… Exclude… Update responsibilities and acceptance criteria according to the impact. Continue when the previously authorized handoff conditions are satisfied, and deliver a usable result.

Improving the workflow without executing the project:

> Use $multi-thread-delivery to review our collaboration workflow. Deliver only improvements to roles, assignments, and handoffs. Do not create tasks, modify project files, or trigger a release.
