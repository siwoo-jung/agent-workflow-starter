# 02 — Execute, review, and finish a task

## The task contract

Start with the owner's requested behavior. Capture observable acceptance criteria, relevant features, scope, constraints, authorized external actions, and verification. Use the [task template](../../templates/agent-workflow/task.md) for substantial work; a brief equivalent note suffices for small edits.

Resolve only ambiguities that materially affect the result. Discover facts from code and the running product where possible. Make reversible implementation choices within the established conventions. Do useful independent work while a required decision is outstanding.

## Feature workflow

1. **Inspect:** read the feature map, implementation, public contracts, existing tests, applicable invariants, and relevant prior decisions.
2. **Specify:** translate the request into observable examples, including failure or boundary behavior. Decide the smallest coherent slice and how to verify it.
3. **Implement:** use the established extension point or suitable existing component. Keep unrelated cleanup out. Update contracts and fixtures where behavior genuinely changes.
4. **Exercise:** start the product, drive the supported interface, and inspect actual outputs. Use the same path documented for another agent.
5. **Verify:** run required checks, inspect failures, repair the cause, and rerun affected checks. Capture final-change evidence.
6. **Review:** inspect the diff and request the required independent review. Fix substantiated findings and reverify impacted evidence.
7. **Integrate:** commit, open a PR, or merge only within current authority and project policy. Record the integration state accurately.
8. **Maintain:** update navigation, commands, constraints, and reusable procedures affected by the change.

## Bug workflow

Reproduce before diagnosing whenever feasible. For a vague report, use the feature map to identify candidate behavior; use screenshot details and logs as clues, not as proof. Inspect the code along the exercised path. Write down observed facts, plausible hypotheses, and the next experiment that distinguishes them.

Compare the reported revision with the target branch when the report may concern an older release. Use matching fixtures and conditions. Classify the result:

| Observation | Outcome |
|---|---|
| Fails on reported revision and target branch | Fix or further investigation needed |
| Fails on reported revision; passes on target branch | Likely already fixed; identify the responsible change if possible and suggest the appropriate release action |
| Fails only under specific data or environment | Capture the conditions and test the relevant boundary |
| Does not reproduce in tested conditions | State exactly what was tested and what remains unknown |
| Required environment or inputs unavailable | Mark reproduction blocked; finish code inspection and other independent checks |

Do not change code for an already fixed issue merely to produce a PR. Do not claim a bug impossible because one attempt passed. A release recommendation does not itself authorize release.

For a reproducible defect, add a regression test that fails for the original behavior and passes for the fix when feasible. Match coverage to the failure mechanism; avoid a brittle assertion that merely repeats the chosen implementation. For performance problems, compare measured traces or workloads rather than claiming improvement from code shape.

## Review protocol

The reviewer receives the task criteria, diff, affected contracts, invariants, and verification evidence. Prefer a fresh reviewer session or separate reviewer where available; a separate model is optional. If only self-review is possible, say so and do not label it independent.

Review correctness, boundary conditions, authorization/data handling where relevant, architecture, maintainability, verification quality, and affected performance. Tie findings to concrete code and a plausible failing scenario. Classify a finding as blocking defect, nonblocking improvement, question, or unsupported hypothesis. A score or approval word without evidence is insufficient.

The implementing agent investigates each finding, records whether it was confirmed, fixes confirmed blocking defects, and reruns the checks they affect. Reviewer disagreement is resolved with implementation evidence, tests, or an owner decision, not repeated voting until approval appears. Keep unresolved blocking findings visible. Do not auto-resolve a thread merely because the code changed.

## Commits and PRs

Each PR should describe one coherent behavior or prerequisite and have a clear verification story. There is no universal line limit. Split independent changes and broad migrations into separately verifiable pieces; do not split so tightly that every PR is broken alone.

Declare dependent PR bases and merge order. Validate after prerequisite changes land; stale checks on a different dependency state do not prove integration. Preserve history useful for investigation: explain the problem, resulting behavior, evidence, and material limitations. Avoid chat history and abandoned plans unless they explain a real tradeoff.

## Parallel work, when supported and authorized

Parallelism is optional. Begin with one reliable agent. If using several, assign one owner per task, isolate edits with branches/worktrees or equivalent workspaces, define interfaces before dependent changes, and record each task's base revision. Share durable artifacts, not private session assumptions.

An integrator owns conflict resolution and final validation. Two agents passing separate tests do not establish that their combined change works. Duplicate task intake needs a claim or deduplication mechanism. If a tool lacks workers, execute the same roles sequentially; correctness must not depend on multi-agent support.

## Blockers and stop conditions

Record a blocker with the failing command or missing decision, its effect, the work completed, and the smallest next action. Continue independent authorized work. Stop the dependent path when a required check cannot run, scope or authorization is unresolved, an invariant would need bypassing, repeated attempts make no progress, or the declared budget is exhausted. Do not keep making speculative changes indefinitely.

## Definition of done

A task is complete when its acceptance criteria are met; the required final-change checks pass; relevant runtime behavior has evidence; required review findings are addressed; project records are updated; and integration is at the stage authorized by the owner. Report a partial result honestly if any condition remains unmet.

A good closing report states: **what changed, why, what ran and passed, what did not run, what review occurred, and whether the result is local, committed, in a PR, merged, or deployed**. It must not require reading the original chat to understand the delivered state.
