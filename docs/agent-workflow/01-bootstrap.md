# 01 — Bootstrap a project

## Outcome

The first agent leaves a project that another agent can understand, start, exercise, and validate without relying on the original chat. Bootstrap is complete when the project facts are recorded, a representative real journey works, its verification detects an intentional failure, and at least one important invariant has executable enforcement. Repository-side gates may remain an explicitly tracked owner action if the agent lacks administrative capability.

## 1. Discover before designing

Inspect the repository, working tree, manifests, lockfiles, entry points, framework conventions, tests, CI, existing documentation, deployment configuration, and instruction files. Determine whether this is a new product, an existing product, or a prototype needing structure. Read existing rules before installing new ones. Record which current behavior is known to work and which baseline checks fail.

For a new project, get the product goal, intended users, first user journey, and material constraints from the owner. Choose a supported stack with useful correctness checks, accessible verification tools, and a sustainable deployment path. Respect an existing stack unless a change has a concrete justification. This kit does not prescribe a language or platform.

For an existing project, preserve working architecture and characterize behavior before changing it. A rewrite is a decision with costs and evidence, not a bootstrap prerequisite. Introduce boundaries incrementally around a feature or seam; use [Architecture](04-architecture.md) for migration planning.

## 2. Create the project records

Copy the templates listed in [Template index](../../templates/agent-workflow/README.md) to `docs/project/`. Populate these first:

| Record | Minimum useful contents |
|---|---|
| `context.md` | Product goal, constraints, code layout, dependencies, environment, exact setup/start/check commands |
| `feature-map.md` | First journey, user vocabulary, navigation/interface, relevant code, fixture, expected behavior |
| `verification.md` | Setup, control method, reset, check commands, evidence recipe, failure conditions |
| `invariants.md` | One or more important rules, rationale, enforcement location, positive and negative cases |
| `automation-policy.md` | Currently authorized actions, permitted worker scope, required checks, merge mode, escalation boundaries |
| `capabilities.md` | Actual agent capabilities, tool equivalents, unavailable capabilities, tested adapter mappings |

For every nontrivial fact, include an implementation/configuration reference or an observation. Record `UNSET` for a needed value that cannot yet be established, and `NOT_APPLICABLE` with a reason where a field does not apply. Never fabricate commands or infer successful setup from configuration alone. Distinguish configured, executed locally, and enforced remotely.

Use a small decision record for important choices. The context file is a concise index of current facts; detailed runbooks belong in the verification contract and feature map.

## 3. Establish a reproducible environment

Document the required runtime and dependency versions, install method, external services, configuration names, fixture preparation, and cleanup. Keep credentials outside the repository; name the secret source and required permission without copying secret values. Use test identities and isolated data.

Run the setup from a clean checkout or record exactly why that check is blocked. Verify the actual documented working directory and commands. If a container or hosted worker is used, test its lifecycle and dependency availability rather than assuming it matches the developer laptop. A lockfile or declared image version improves repeatability but is not proof that startup works.

## 4. Prove one end-to-end control path

Choose the first meaningful product journey. Start the application using the recorded command, establish readiness, exercise the journey through its supported interface, check an observable outcome, capture evidence, reset fixtures, and stop resources owned by the run.

The interface may be browser, API, CLI, simulator, desktop, background worker, batch job, or library call. The same requirement applies: the agent needs a repeatable way to act and observe. Document any control adapter as a normal procedure plus executable tooling, not a model-specific incantation.

Demonstrate that the verifier can detect failure. Introduce a temporary controlled fault in a disposable checkout or fixture, observe a failing check, restore the baseline, and observe a pass. Save the fault description and results, not a permanent broken change. A verifier that always reports success is not a trust foundation.

## 5. Establish the first enforced invariant

Choose a high-value risk, such as a forbidden dependency direction, missing authorization on a sensitive endpoint, or accidental use of production configuration in tests. Define the rule precisely. Use an existing compiler, analyzer, framework facility, test, or linter where suitable.

Create a valid example and an intentionally invalid example. Check that the rule distinguishes them. Add its executable check to the local verification contract and the project's CI when authorized. Record the status in the invariant register. A written intention remains advisory until enforcement exists.

## 6. Set a conservative initial integration mode

Until the owner authorizes otherwise, agents can implement and verify locally within the task's scope; repository writes follow the authorization supplied for the task. Record whether agents may create branches, open PRs, respond to findings, merge, or deploy. Begin with a reviewer before merge. Set automatic merge eligibility to none during bootstrap.

After the checks exist, configure repository gates through an authorized administrator or supported mechanism. Describe the actual required check names and review rules; do not mark protections active without inspecting or testing them. Never silently weaken existing protections to accommodate this kit.

## 7. Run the first small task

Choose a bounded feature or real bug. Follow [Execution](02-execution.md). Confirm another agent or a fresh session can read the project records, locate the feature, run verification, and produce a useful report. If it needs missing chat context, put the durable information in the relevant record.

## Completion checklist

- [ ] Existing behavior and baseline failures recorded; unrelated work preserved.
- [ ] Project records populated with observations; remaining unknowns and their impact listed.
- [ ] Setup, readiness, one real journey, reset, and cleanup executed.
- [ ] Feature map matches the tested journey and implementation.
- [ ] Verification passes valid behavior and detects a controlled failure.
- [ ] At least one invariant enforced and tested with positive/negative cases.
- [ ] Required CI and repository controls have an honest status: planned, configured, or confirmed.
- [ ] Action authority and initial review/merge mode recorded.
- [ ] Fresh-session handoff succeeds, or the exact missing capability is recorded.

Report bootstrap as **ready for supervised implementation**, **partially ready with named blockers**, or **not ready**. Being ready for supervised work does not imply readiness for unattended merge or deployment. If permissions or tooling are missing, deliver the concrete local setup and exact remaining action instead of stopping all progress.
