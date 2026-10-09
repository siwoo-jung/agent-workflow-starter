# Agent operating instructions

These instructions apply to this repository and to future projects that adopt this starter. They are model-independent. Runtime and platform requirements take precedence over repository guidance; explicit task authorization and project-specific policy govern what actions are permitted.

## Start every task

1. Read this file. Read applicable nested `AGENTS.md` files along the paths you will change; discover their scope explicitly if your tool does not do so automatically. Nested guidance specializes its directory and must not silently bypass project-wide invariants. Surface an unresolved policy conflict before a dependent action.
2. If `docs/project/context.md` or `docs/project/verification.md` is absent or unusable, follow [Bootstrap](docs/agent-workflow/01-bootstrap.md). Bootstrap records are created from [templates](templates/agent-workflow/README.md); they are not assumed to exist.
3. Otherwise read `docs/project/context.md`, `docs/project/verification.md`, `docs/project/invariants.md`, and `docs/project/automation-policy.md`. Read `docs/project/feature-map.md` entries for the affected behavior and the relevant architecture decisions. Load only the procedures and code needed for this task.
4. Inspect the working tree, current revision, relevant implementation, and existing tests. Preserve unrelated work. Establish scope, acceptance criteria, and verification before implementation; a short task note is enough for a small change.
5. Check available capabilities against `docs/project/capabilities.md` if present. Use a supported equivalent when a preferred tool is unavailable; never invent successful execution.

## Work from evidence

- Read the relevant code before diagnosing it. Label hypotheses as hypotheses. Reproduce a bug through the actual supported interface where feasible, then connect observations to implementation.
- For features, define observable acceptance criteria and a real path to test them. Build the smallest cohesive change that satisfies the request.
- Prefer existing project patterns and suitable maintained, permissively licensed components before creating equivalents. Check whether the library already provides the complete control or behavior; using its primitives to assemble a duplicate does not establish a need for custom code. Document a concrete gap when custom implementation is justified.
- Respect feature and runtime boundaries. Keep related behavior together where the framework permits it. Enforce repeatable invariants through architecture, compiler, static analysis, tests, or CI, not instructions alone.
- Do not weaken a check, delete a meaningful assertion, suppress a failure, or alter acceptance criteria merely to make the change pass. A necessary policy or test correction needs its own rationale and the review required by project policy.

## Close the verification loop

- Run the affected behavior, inspect results, fix failures, and repeat within the task's budget. Use real application execution for user-facing behavior; a successful build alone is insufficient evidence.
- Run the verification contract's required checks for this change class. Add meaningful regression coverage for bugs and substantial behavior; avoid tests that simply restate the implementation.
- Verify the verifier when creating or modifying a gate: a deliberately invalid case must fail and a valid case must pass. Remove the temporary fault afterward.
- Record the tested revision or content identity, commands, environment, fixtures, expected and actual results, and evidence locations. Mark every omitted or blocked check. Reverify affected evidence after changes; prior-revision results are not final-revision results.
- Never claim completion, approval, or a passing check without supporting evidence. If runtime verification is blocked, complete independent work and clearly state the remaining gap.

## Review and integrate

- Follow [Execution](docs/agent-workflow/02-execution.md). Keep commits and PRs cohesive so they explain one behavior and can be reverted. Split by conceptual independence, not arbitrary line counts.
- Request or perform review within the authorized workflow. Evaluate concrete findings; inspect and verify them before changing code. An AI review is a fallible signal, not a substitute for required executable checks.
- Merge, deployment, destructive operations, and external communications require applicable authorization. Honor authorization already provided; do not repeatedly ask for it. Missing policy limits external actions, not routine reversible local implementation.
- Automatic merging is available only under a completed project policy and enforced repository gates. Instructions cannot grant bypass authority. Do not change credentials, branch protections, or merge policy to get your own change through.

## Maintain the environment

- Update feature maps, verification recipes, project facts, and decisions in the same change when behavior or commands change. Record durable facts and rationale, not conversation history.
- Convert repeated corrections into the smallest useful skill or mechanical constraint and evaluate it. Do not generalize a one-off review comment into a global ban without evidence.
- Share a concise outcome: behavior changed, evidence, unresolved limitations, integration state, and any concrete owner decision still required.

Read the [playbook index](README.md) for detailed procedures. If this repository only contains the starter, validate documentation and templates; do not pretend an application or project CI exists.
