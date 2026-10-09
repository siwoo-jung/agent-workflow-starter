# 03 — Build a verification loop agents can use

## The verification contract

Maintain `docs/project/verification.md` using the [template](../../templates/agent-workflow/verification-contract.md). It defines how to set up, start, exercise, observe, reset, and clean up the product, plus which checks apply to each change class. Every command needs its working directory, dependencies, expected result, and failure interpretation.

An agent must be able to run the actual product and inspect the outcome. Source inspection, compiler success, and test success provide different evidence; none alone proves all user behavior. Use a proportional combination rather than a universal enormous test suite.

## Control capability and product knowledge

Lauren's verification approach combines application control with a feature map. Preserve this distinction:

| Artifact | Question it answers |
|---|---|
| Control runbook and tooling | How can an agent start, operate, observe, and reset this application? |
| Feature map | What do users call this feature, where is it, and how should it behave? |
| Verification recipe | Which actions and observations prove this particular acceptance criterion? |

Control tooling can use whatever supported interfaces the project exposes. Keep the procedure readable without a proprietary skill loader. If a loader is used, its skill points to the canonical recipe and verified tool mapping.

| Product surface | Possible control and observations |
|---|---|
| Web UI | Browser automation, accessible selectors, screenshots, console/network logs, trace capture |
| API/service | Requests with test identities, response/status checks, state readback, logs/metrics |
| CLI | Inputs/arguments, exit codes, stdout/stderr, output files, subprocess lifecycle |
| Desktop/mobile | Automation API or simulator, navigation, screenshots, crash logs, process/CPU traces |
| Worker/data pipeline | Synthetic input, job state, resulting records, retries, throughput, idempotency |
| Library | Representative consumer call, documented API behavior, exceptions, compatibility fixtures |
| Hardware-dependent system | Approved simulator or bench test, declared limits, captured signals and configuration |

These are capability examples, not required vendor choices. Mark inaccessible surfaces blocked or use a documented equivalent with its limits stated. A simulation must not be reported as real-device validation.

## Feature map construction

Start with the first journey, then add entries as work touches features. Use stable IDs and user vocabulary. Each entry contains an interface path, prerequisites, test identity and fixture, relevant code, actions, expected observations, negative or boundary cases, and a recipe/evidence reference. Prefer stable accessible names or deliberate test hooks to fragile positional selectors.

Verify entries by actually navigating or invoking the interface. Distinguish inspected-only entries from exercised entries. Include keyboard shortcuts only when they exist; for APIs or pipelines use endpoint/job/command names instead of UI terminology. Link to implementation so a vague report can be traced to candidate code without guessing.

Do not map every function. The purpose is to connect product behavior to a repeatable verification path. Update an affected entry in the same change when navigation, behavior, fixture, selectors, or ownership changes.

## Design evidence before implementation

Translate acceptance criteria into independent observations. A saved-setting popup appearing is weaker evidence than a saved value surviving a reload. An API returning 200 is weaker than confirming the expected state transition and failure response. A pipeline job reporting success is weaker than checking the produced data and count.

Define fixtures and expected results before changing code where possible. Separate the expected outcome from implementation details so the test does not merely agree with the code it tests. For a defect, capture the failing observation before the fix. Include negative cases that distinguish a real fix from a superficially successful path.

## Check selection

The project contract supplies exact commands and triggers. This table describes typical coverage, not a mandatory stack:

| Change class | Evidence usually needed |
|---|---|
| Documentation only | Link/path checks and accuracy against current commands/code |
| Local behavior | Targeted unit/contract checks plus real invocation where applicable |
| User journey | Integration/UI verification of acceptance criteria and failure behavior |
| Cross-feature/public contract | Consumer compatibility and affected integration journeys |
| Runtime/dependency boundary | Dependency analysis and positive/negative enforcement cases |
| Performance | Representative workload, before/after measurements, environment and variance |
| Data/schema migration | Disposable data rehearsal, compatibility, interruption/retry behavior, recovery |
| Verification or CI changes | Valid case passes; controlled violation fails; checks genuinely gate integration |

Run required checks once against the final change; repeat after new changes or unresolved failures. Avoid unrelated test expansion for low-impact edits. Record pre-existing failures distinctly and assess whether they obscure relevant evidence.

## Validate the verifier

Whenever a new verifier is introduced, and after material changes to it:

1. Select a known valid baseline and an intentionally invalid case matching the target failure.
2. Run in an isolated checkout or disposable environment.
3. Confirm the valid case passes and the invalid case fails for the expected reason.
4. Confirm the runner propagates exit codes, discovers the intended tests, checks assertions, and does not swallow errors.
5. Restore the baseline, rerun it, and save the results.

Check false positives as well as missed defects. A permanent flaky check trains agents to ignore failures. Fix unreliable fixtures or timing and give every gate an owner. Any temporary quarantine needs an expiration, alternate evidence, and policy treatment; a quarantined gate is not a passing gate.

## Evidence and revision identity

Use the [verification report](../../templates/agent-workflow/verification-report.md). Record revision/content identity, base, changed files, environment, check commands, inputs, expected/actual results, timestamps, and artifact references. For uncommitted code, capture a diff digest or equivalent identity and validate the resulting committed revision before merge.

Keep screenshots, logs, traces, and test reports at durable references according to project retention policy. Redact secrets and sensitive fixture data. Logs do not need to be pasted into every Markdown record; a concise result and artifact reference suffice.

After another commit, dependency update, conflict resolution, or base movement, determine which evidence remains valid and rerun affected checks. Automatic integration requires server-side checks for the actual candidate revision, with combined-state validation as defined by the merge policy. Evidence for an earlier head is not merge evidence for a new head.

## Performance and cleanup

For a performance issue, record workload, data size, machine/environment, warmup/cache conditions, repetitions, metric and accepted tolerance. Compare equivalent conditions; report uncertainty rather than unsupported precision. The project's own budgets determine failure, not a universal FPS or latency figure.

Reset deterministic fixtures and clean up only resources created by the verification run. Use bounded readiness waits and process timeouts. Record who owns persistent resources and avoid leaving hosted workers or services consuming budget without a declared lifecycle.
