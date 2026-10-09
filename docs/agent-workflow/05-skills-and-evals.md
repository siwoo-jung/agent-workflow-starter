# 05 — Build skills incrementally and evaluate them

## What a skill means here

A skill is a versioned, reusable procedure: when to use it, what inputs it needs, what actions to take, how to verify them, and what result to return. Plain Markdown is sufficient. No specific model, plugin loader, slash command, or orchestration framework is required. Tool-specific wrappers point to the canonical procedure and capability mapping.

Start with observed failures. Inspect tool actions, commands, diffs, outputs, and outcome evidence; do not depend on access to a model's hidden reasoning. A repeated unsupported diagnosis might need an investigation skill. Repeated trouble exercising the product might need better control tooling or feature context. Choose the intervention that addresses the cause.

## Skill creation loop

1. Record a concrete failure with expected and observed behavior.
2. Decide whether the remedy belongs in context, a reusable procedure, tooling, a test, or architecture. Avoid creating a skill for a problem a compiler can eliminate.
3. Write a short procedure using the [skill template](../../templates/agent-workflow/skill.md). Specify inputs, capabilities, action sequence, evidence, stopping conditions, and output.
4. Run it locally while observing execution. Fix missing prerequisites and ambiguous instructions.
5. Evaluate it against known cases and unfamiliar cases.
6. Adopt it if it improves actual outcomes without unacceptable cost or regressions.
7. Update or retire it when product/tooling changes make it inaccurate or unnecessary.

Useful initial procedures often include investigation, create verification, maintain verification, and review. Add them only when they provide value; the playbook already defines the core workflows. Keep facts in project records and procedures in skills to avoid drift from duplicated information.

## Create and maintain verification as procedures

**Create verification:** inspect entry points and user journeys; discover a supported control mechanism; build deterministic fixtures; populate the feature map; implement a real acceptance check; prove positive and negative results; record commands and evidence.

**Maintain verification:** identify changed features/interfaces; exercise affected recipes; update selectors, fixtures, commands, and code links; reevaluate the verifier for material changes; mark remaining gaps. Update alongside the implementation rather than waiting for a large documentation cleanup.

These preserve the purpose of Lauren's create/maintain verification skills without assuming her private implementation or plugin format.

## An evaluation is a test of agent behavior

A normal test checks software output. An agent eval checks whether an agent follows a procedure and produces a correct, supported result under representative conditions. A green implementation test does not establish that the investigation or reporting skill works.

Use the [eval case](../../templates/agent-workflow/eval-case.md) and [eval report](../../templates/agent-workflow/eval-report.md) templates. A case includes a fixed repository/fixture state, ordinary task wording, expected outcomes, prohibited behaviors, ground-truth references, and a predeclared rubric. Run in isolated workspaces with resettable state. Keep expected answers and judge material inaccessible to the worker.

Give workspaces neutral names and normal tasks so the worker is not prompted to behave specially for a scored benchmark. Keep evaluation activity within authorized test environments. Avoid including the desired answer in the task. Do not hide information the real procedure would need merely to manufacture difficulty.

## Minimum useful case set

| Case | What it measures |
|---|---|
| Normal feature or bug | Correct result and required verification |
| Misleading symptom | Reads implementation and tests hypotheses instead of guessing |
| Already fixed on target branch | Avoids unnecessary changes and reports revision evidence |
| Stale feature-map entry | Detects mismatch and repairs or reports it |
| Unavailable tool or environment | Uses a valid fallback or reports a block honestly |
| Seeded architectural violation | Detects or rejects the forbidden pattern |
| Verifier with a broken assertion/exit path | Does not trust an always-green check |
| Review disagreement | Resolves findings with evidence rather than approval chasing |

Choose a small relevant subset initially. For high-value procedures use held-out cases the skill author does not optimize against. Add new cases from escaped defects and recurring corrections.

## Roles and scoring

Roles can be separate agents or sequential sessions:

- **Coordinator:** fixes cases, rubric, budgets, and environment before the run.
- **Worker:** receives the procedure and normal task, performs the work, and records observable actions/results.
- **Judge:** compares artifacts with ground truth and rubrics; uses deterministic checks whenever possible.
- **Independent checker:** audits disputed or consequential scores; a different model can help but is not required.

Freeze the rubric for a comparison. Score correctness, evidence quality, instruction adherence, context maintenance, boundary handling, and efficiency. Define concrete anchors for each dimension. Critical failures—fabricated results, unauthorized actions, bypassed gates, or an uncorrected known defect—fail the run regardless of average score.

Record model/tool versions as experimental metadata, not as normative requirements. A procedure should work across the agents the project actually uses. Run comparable cases across more than one model/tool family when feasible; if only one was tested, do not claim universal reliability.

## Controlled improvement

Run baseline and proposed skill versions on the same cases and environment. Repeat cases where nondeterminism materially affects conclusions. Compare successes, failures, variance, elapsed time, tool/token cost where available, and regression outcomes. Keep held-out results separate.

An improvement loop may revise the procedure and rerun evaluations, but it needs a maximum iteration count, budget, stop conditions, and preserved result history. Do not alter ground truth or lower thresholds to raise the score. A perfect score on a small tuned set is not proof of general reliability. Re-run after changing the runtime adapter, important tool versions, or procedure behavior.

## Acceptance and cost

The project owner chooses thresholds appropriate to the workflow and consequence. No universal numerical score establishes merge safety. Require no critical failures in the chosen acceptance set, useful evidence, and no unacceptable regression. For consequential automation, audit representative runs independently before promotion.

Use cheap deterministic checks before expensive agent judging. Evaluate high-leverage procedures and recent changes rather than rerunning a large matrix for every small edit. Record whether reduced human intervention offsets setup, maintenance, and execution cost.
