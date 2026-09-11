# Tool adaptation and authorization boundaries

Read this before task coordination or recovery. This is a capability guide, not a fixed API schema. Follow the tools actually available in the current session, their descriptions, platform rules, and user instructions. Capabilities differ by client and environment. If a tool is unavailable, say so; do not invent sent messages or completion records, or install an unrequested plugin to fill the gap.

## User-visible tasks and internal subagents

Use the routes below only where those capabilities are available.

| Purpose | Capability route | Notes |
| --- | --- | --- |
| Reuse an existing user task | `list_threads` → `read_thread` when needed | Check project, host, working directory, and status. Use the actual task title when referring to it; do not present its summary as its title. |
| Create an explicitly requested user task | `list_projects` → `create_thread` | The current task can coordinate. Create only the missing roles. |
| Assign follow-up work to an existing task | `send_message_to_thread` | The message is a visible work instruction, not a general notification channel. Avoid acknowledgments with no action. |
| Delegate a bounded parallel subtask | Available capabilities such as `collaboration.spawn_agent` and `followup_task` | Delegate concrete work that can finish independently while the main task continues useful work. This does not create a separate user-visible task window. |
| Wait for user tasks | `wait_threads` | Use returned hosts and cursors; batch within the tool's limits. Use `timeoutMs: 0` for a snapshot when supported. |
| Wait for internal subagents | Available collaboration wait or status capabilities | Keep these separate from user task tools; an agent ID is not a `threadId`. |
| Show a deliverable | `open_in_codex` or an available preview capability | Open only a verifiable result. Showing a panel does not mean its content has run. |

When creating a project task, use the actual `projectId` and `isGitRepository` returned by `list_projects` and follow the current tool's defaults for local and worktree environments. Preserve an explicit user choice to work in the saved local directory. Do not invent a branch name or starting state, or switch to an unknown branch. Follow environment conventions when a new branch is needed. A returned `clientThreadId` means setup is in progress; do not use it as a `threadId` for messaging or waiting. Resolve the actual task ID first.

If the user has not explicitly requested new tasks, reuse existing tasks, use internal subagents, work in the current task, or suggest roles. A four-role template does not authorize four new windows. If task tools are unavailable, provide copyable assignments and state that they have not been sent. Continue work that can be completed in the current environment.

Do not hard-code any model in the skill. Preserve the user's current configuration and existing task settings by default. When the user specifies a model, use an exact name supported by the current tool. Do not silently upgrade or downgrade, or claim that a model switch occurred when it did not. Do not use another task to bypass model or tool permissions.

## Handoffs, freezes, and environments

A logical handoff in an assignment differs from the product's `handoff_thread` operation. The former transfers responsibility for files or resources; the latter may interrupt a running task and move Git working state. Do not invoke that physical move for an ordinary assignment handoff unless it is necessary and appropriately authorized.

In a shared local workspace, coordinate exclusive access to the index, shared files, and runtime resources that actually conflict. Separate worktrees may edit in parallel, but must not concurrently change shared refs or release to the same destination. Acceptance evidence must identify the worktree or merged version checked. The integrator checks interfaces and content; another task's passing tests do not justify skipping integration checks where the integrated version differs.

If a freeze is needed, specify the candidate and file scope, unrelated work that may continue, release conditions, and next owner. Transfer write access only after the current owner stops writing. A timeout or long silence does not prove that resources have been released. Manage only processes and locks you own and have verified; do not close unrelated user applications.

## Waiting and interruption recovery

Save the latest cursor. When status is unchanged, continue waiting at a reasonable interval instead of repeatedly reading full task histories or sending the same prompt. If work appears stalled, perform one relevant status or original-artifact check, send one precise recovery instruction or blocker inquiry, and wait for a change. Do not start a second writer while the original owner may still be running.

Respect current tool limits for long waits and choose calls short enough to allow necessary communication. Unchanged status does not need repeated “still in progress” updates. Normal updates can explain new decisions or verified partial results.

A successful dispatch proves only that the platform accepted a message. A subtask's completion report does not replace verification of critical outputs. Read original results, outer command status, or the target application when needed. Mark unavailable telemetry as unavailable; do not infer background execution, window focus, or human usability.

## Automations and external release

Use product capabilities such as `automation_update` only when the user requests later, recurring, ongoing follow-up, or monitoring. Look for an existing automation with the same objective before creating another. Collaboration alone does not justify scheduling a heartbeat. Do not use shell sleep or cron to imply persistent background capabilities. Follow the platform's notification and stopping rules. Do not promise execution while the machine is off or permissions are missing.

The skill's coordinator authorization and conditional handoffs coordinate work only within the user's existing authorization; they do not replace it. If remote addresses, release visibility, overwrite targets, or installation scope are unspecified, complete independent work that is in scope, then stop and explain before an action requiring new permission. Requests to continue working or avoid questions do not expand that authorization.

## Maintenance references

These sources describe product mechanisms; they do not provide official endorsement of this skill's four-role convention. Initially packaged on 2026-09-11. When tools change, check the actual schemas and relevant official documentation instead of sending requests copied from fixed examples.

- [Official skill documentation](https://learn.chatgpt.com/docs/build-skills): `SKILL.md`, progressive loading, and skill discovery.
- [Official worktree documentation](https://learn.chatgpt.com/docs/environments/git-worktrees): isolated checkouts and parallel tasks.
- [Official subagent documentation](https://learn.chatgpt.com/docs/agent-configuration/subagents): bounded parallel work, synthesized results, and context costs.
