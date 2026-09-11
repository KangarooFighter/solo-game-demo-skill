# Solo game demo development reference

This reference adds game-specific decisions to the coordination workflow; read it only for game design or implementation work.
Determine whether the user wants a new build, an iteration, or design advice; design requests do not automatically authorize implementation.

## Define a finite playable loop

- State what the player does, what feedback they receive, and when this iteration ends.
- Agree on a playable path through entry, the core action, its result, completion or failure, and another attempt.
- Choose ending conditions that fit the game; exploration, narrative, and sandbox demos need not add victory, defeat, or combat.
- Identify the target device, input method, intended experience, delivery format, and work excluded from this iteration.
- Use observable behavior and deliverables for acceptance, rather than asset counts or development time.
- Put gameplay extensions into follow-up suggestions; deliver when the agreed conditions are met without extending development on your own.

## Establish a greybox before integrating final assets

1. Use simple shapes, placeholder scenes, and temporary feedback to verify core controls and the complete loop.
2. Tune the relationship between the 3Cs: Character, Camera, and Controls.
3. Check movement, viewpoint, input response, and necessary interaction prompts; prompts should explain currently available actions.
4. Give key actions recognizable visual and audio feedback, and check that feedback matches the actual outcome.
5. Once the core gameplay works, integrate final art, animation, sound, and UI, then reassess readability and game feel.

Players should still understand critical states when audio is unavailable; match feedback intensity to the chosen style and platform.
Art can explore style and specifications during the greybox stage; avoid producing final assets in bulk before gameplay dimensions settle.
Develop opponent AI only when the loop requires opponents, with complexity determined by the actual gameplay.
When opponents are needed, first verify necessary perception, actions, and failure handling; games without opponents do not need an enemy system by default.

## Engine, environment, and responsibilities

Respect the user's engine and version, and reuse a viable existing project; Godot is an example option, not a default requirement.
If the engine is undecided, offer a small set of choices based on the target platform, existing assets, and user experience before implementing.
Inspect available tools first; address missing dependencies only when building, importing, or exporting actually requires them.
Dependency installation must fit existing authorization; when required permission is missing, identify the dependency, purpose, and affected delivery.
Activating this skill does not itself authorize software installation, global configuration changes, or restructuring the project.

| Default responsibility | Game demo result and boundary |
| --- | --- |
| 01 Coordination and design | Define the gameplay loop, experience goals, asset contracts, and acceptance; maintain current status. |
| 02 Implementation and integration | Implement controls, scenes, and gameplay; own agreed shared entry points and integrate specialist outputs. |
| 03 Specialist outputs | Produce the art, animation, sound, or UI this iteration needs, with specifications and source information. |
| 04 Verification and delivery | Check experience paths, regression risks, and actual deliverables; record evidence and limitations. |

These are responsibilities, not a requirement for four windows; the current task can handle a small change.
Reuse existing tasks belonging to this project; create missing user-visible tasks only when the user explicitly requests them.
Available subagents may handle bounded internal work, with clear file ownership, input baselines, and acceptance conditions.
Preserve the existing directory structure; assign separate files to asset authors and integrators, avoiding concurrent edits to shared scenes or import settings.

## Agree on interfaces before producing final assets

Fill in relevant fields for 2D, 3D, and the asset type; omit inapplicable fields and notify integrators of changes.

| Field | Agreement needed |
| --- | --- |
| Location and version | Source and runtime files within existing directories, naming, and the applicable interface revision. |
| Coordinates and units | World axes, character facing, and the relationship between pixels, world units, or physical dimensions. |
| Dimensions and origin | Visible bounds, scale, pivots or anchors; distinguish canvas padding from actual character bounds. |
| Collision ownership | Who defines colliders, trigger volumes, and hit regions, and whether code or scenes maintain them. |
| Animation and states | State names, looping, transition conditions, and necessary events; avoid relying on unspecified frame order. |
| Format and import | File format, alpha, filtering and compression needs, and ownership of import settings. |
| Audio and UI | Trigger timing, loop or interruption rules, layout constraints, and required platform adaptation. |
| Origin and use | Original, generated, or third-party sources, with applicable licenses and usage restrictions recorded. |

After asset replacement, check scale, orientation, occlusion, collision, and prompt placement; opening the file alone is insufficient.
Serialize operations when a shared import cache or editor session creates a real conflict; independent work can continue.

## Verify actual deliverables in separate layers

- Source project: check loading, asset references, runtime errors, and key behavior affected by the change.
- Playable experience: complete the agreed loop and check input, camera, prompts, feedback, and necessary retry or exit paths.
- Exported artifact: when export is in scope, run the actual package and check startup, assets, input, and target environment behavior.
- Delivery notes: provide the real entry point, controls, version or baseline, verified scope, and remaining limitations.

A working source project does not establish that its export works; headless checks cannot replace game feel or audiovisual checks.
Mark only checks actually performed as verified, and explicitly identify environments that could not be tested.
Hold candidate inputs stable during acceptance; after changes or failures, recheck the affected scope and related risks.
Respect existing publishing authorization and report local completion, export completion, and external publication separately.

## Copyable request examples

Starting a new project (fill in placeholders; this request explicitly authorizes creating missing tasks):

> Use $multi-thread-delivery to start a finite playable [game type] demo with [core loop], using [user-selected engine] in [project location]. Inspect the project and its current tasks first. Reuse relevant existing tasks and create missing independent tasks for work that can proceed independently and has no owner. Assign coordination, implementation, specialist outputs, and verification/delivery responsibilities, combining them where appropriate. Start with a greybox, then integrate assets against agreed interfaces; preserve the directory structure. Deliver [source project or export target] and finish at [observable completion conditions]. Keep installation, replacement, and external publication within my existing authorization.

Iterating on an existing demo:

> Use $multi-thread-delivery to continue the current demo and complete only [this iteration's change]. Reuse existing tasks without creating new task windows. Preserve gameplay outside this change and the existing directories. Check the current baseline and asset interfaces, verify affected playable paths, and deliver the result with its limitations.

Design only:

> Use $multi-thread-delivery to design a finite demo loop, greybox scope, responsibility split, and asset interfaces for [gameplay idea]. Deliver design advice only. Do not create tasks, edit the project, install software, or begin development.
