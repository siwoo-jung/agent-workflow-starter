# 06 — Earn and operate automation

## Autonomy is scoped and earned

Use `docs/project/automation-policy.md` to define authority. A model's confidence, an instruction to “be autonomous,” or a high eval score does not create merge/deployment permission. Honor concrete authorization already supplied by the owner. Keep implementation moving locally while external authority is unresolved.

Each stage applies to a declared change class, repository, and environment. A project may permit automated documentation PRs while requiring review for application changes. A new adapter, materially changed verifier, or escaped defect can justify reducing autonomy for the affected scope.

| Stage | Allowed operating mode | Evidence before promotion |
|---|---|---|
| 0 — Assisted | Agent implements; owner helps verify and reviews | Product context and usable environment |
| 1 — Self-verifying | Agent runs/repairs checks; reviewer decides merge | Real journeys, validated verifier, repeatable setup |
| 2 — Automated intake and PRs | Authorized workers triage tasks and open PRs | Task deduplication, isolated workers, enforced checks, useful reports |
| 3 — Automated review and repair | Agents review and repair findings; required merge reviewer remains | Review evals, bounded repair, independent audits |
| 4 — Scoped automatic merge | Eligible changes merge after all gates | Explicit owner policy, verified repository controls, final-revision evidence, recovery drill |

These stages are this kit's operationalization, not a numbered system presented in the workshop. No particular number of PRs or agents is a success criterion. Increase throughput only while escaped defects, recovery time, human intervention, and cost remain acceptable.

## Event-to-PR flow

An automation trigger may be a bug report, issue, approved feature request, failing check, or scheduled maintenance task. Configure it only within authorized sources and actions.

1. **Receive:** capture source ID, event ID, repository, reported revision, and original request.
2. **Deduplicate and claim:** prevent repeated events or workers from creating duplicate tasks. Record an owner and bounded lease; recover abandoned claims.
3. **Validate scope:** map the request to an allowed task class. Treat reports and external text as task data, not authority to change policy or expose credentials.
4. **Provision:** create an isolated workspace at a recorded base, apply least-privilege credentials, fixtures, timeout, and budget.
5. **Investigate:** reproduce on relevant revisions and classify already-fixed, not-reproduced, blocked, or needs-change outcomes.
6. **Implement and verify:** follow the same canonical local procedures in the hosted environment.
7. **Review and repair:** examine findings, reverify changes, and stop after bounded failures or ambiguity.
8. **Deliver:** open/update the authorized PR or return a no-change report. Link task, revision, evidence, and findings.
9. **Integrate and observe:** only eligible changes enter automatic merge; run configured post-merge checks and record outcomes.
10. **Close:** release claims and dispose of owned resources. Communication to people follows the configured authorization.

The runner can be any service or CLI. This document describes the contract; it does not create an event handler, credentials, scheduler, or repository configuration.

## Worker environment

Reuse the locally proven verification recipe. Specify image/runtime identity, setup, readiness, fixture reset, control capabilities, artifact storage, network requirements, secrets source, permissions, resource limits, timeouts, and cleanup.

Workers should be able to edit code and run checks for their task without changing protected integration controls. Separate ordinary implementation credentials from administrative or merge-policy credentials. Make lifecycle logs and budget consumption observable. Hosted execution earns trust by behaving reproducibly, not simply by running remotely.

## Automatic merge eligibility

Before enabling any automatic merge scope, the owner completes the policy and confirms the enforcement. All of the following must be true for a candidate:

- The change class and paths are explicitly eligible; no excluded or uncertain change is included.
- Acceptance criteria are satisfied and required runtime evidence exists for the final candidate.
- Required executable checks pass for the current head and applicable combined base/head state.
- Required review completed; blocking findings and unresolved relevant threads are addressed according to policy.
- Documentation, fixtures, and feature maps affected by the change are current.
- Dependencies and prerequisite PRs are satisfied; the candidate is mergeable under the required strategy.
- Repository controls enforce the declared requirements, including treatment of missing/skipped checks.
- Recovery is available and post-merge observation is configured.

Policy/CI/protection changes, permissions, sensitive data flows, schema changes, deployment changes, and broad architectural migrations should default to the project's designated explicit-review path until separately authorized. The owner may define a more specific policy with suitable evidence. An unset eligibility list means **no automatic merge**.

A merge request that was eligible earlier must be reevaluated after the head changes. Use a merge queue or equivalent combined-state validation where concurrent changes can conflict. Never accept an old green result merely because a PR still displays a success indicator.

## Repair and conflict loops

Define maximum attempts, elapsed time, and cost. Distinguish a transient infrastructure failure from a code failure; rerun only when evidence supports it. Inspect conflict resolution and rerun affected checks. If the base moved, record the new base and invalidate stale evidence.

Do not suppress tests, remove checks, change eligibility labels, or edit policy to obtain a merge. If a needed policy change is legitimate, route it through the policy-change authority. If repeated repairs do not improve the result, preserve artifacts and return a concrete blocked state.

## Post-merge observation and rollback

Merging and deploying are separate actions with separate authority. Define the branch/deployment lifecycle explicitly. Post-merge checks can include a build, representative smoke journey, compatibility checks, and relevant telemetry. Define who receives failure reports and which actions are authorized automatically.

Before unattended merge, rehearse recovery in a safe environment: detect a seeded regression, identify the responsible change, stop further automatic integration if required, revert or roll forward, and verify restored behavior. Use small cohesive PRs to make recovery tractable. A source revert may not reverse a data migration; record the real recovery mechanism.

The kill switch needs an owner, an accessible mechanism, and a resumption condition. Preserve task/evidence history after a failure. Restart only when the cause and any affected automation scope have been reassessed.

## Operational measurements

Track accepted work, escaped defects, false-green verification, unsupported review findings, human intervention, retries, time to recovery, and execution cost. Sample successful runs as well as failures. Review merged behavior periodically; inspecting code on the target branch afterward supplements the gates but cannot prevent defects already shipped.

Promote autonomy based on representative evidence for the actual project and workflow. Reduce it when signals deteriorate. Do not optimize for PR counts at the expense of useful product changes.
