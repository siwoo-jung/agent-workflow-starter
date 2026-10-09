# 07 — Maintain context and remove recurring failure modes

## Keep records close to their source

Project records are living interfaces for future agents. Update them in the same change as affected behavior. Every record has an owner or owning role, source references, and a last-validated revision/date where useful. Avoid copying the same command or rule into several documents; use links and one canonical definition.

| Change | Update |
|---|---|
| Feature/navigation/API behavior | Feature map, acceptance recipe, relevant fixtures |
| Setup, command, runtime, dependency | Context, verification contract, capability adapter |
| New boundary or forbidden pattern | Invariant register, enforcement, architecture decision |
| Repeated agent failure | Correction record, skill/check, eval cases |
| Review/merge authority or gates | Automation policy and actual repository controls |
| Data recovery or deployment behavior | Recovery runbook and verification rehearsal |

For a small project, update on affected changes. For active automation, also review on escaped defects, tool changes, a new agent runtime, and a regular cadence chosen by the owner. A dated record is not automatically stale; verify when its source changes or observed behavior disagrees.

## Observe failures productively

When a human repeats a correction, capture the task, observed actions, expected behavior, consequence, and why current controls missed it. Use the [correction record](../../templates/agent-workflow/correction-record.md). Inspect observable tool calls, commands, artifacts, and results rather than speculating about hidden reasoning.

Find the smallest useful remedy:

- Missing product knowledge → update the feature map or context.
- Unsupported diagnosis → improve investigation and evaluate misleading cases.
- Repeated mechanical violation → use an analyzer/test/architecture constraint.
- Fragile verification → fix the fixture/control method and validate the verifier.
- Stale claims → improve revision/evidence tracking.
- Unbounded loops → tighten stop conditions and budget handling.

Distinguish a local correction from a durable project rule. Add a global restriction only when its scope and rationale are established. Preserve a justified exception rather than turning every failure into a ban.

## Change the environment safely

Treat procedure and policy changes as software changes. Version them, explain the failure they address, add or update relevant eval cases, and compare outcomes. Keep a record of regressions and cost. Changes that affect merge safety use the separately authorized policy-review path.

When adopting updates to the universal starter, review differences and preserve project-specific facts and authorizations. Record the adopted starter version in the context. Thin vendor adapters should continue to point at the same canonical documents.

## Audit the happy path

Sample successful tasks. Check that reported execution really occurred, evidence corresponds to the final revision, acceptance criteria were not weakened, and the resulting feature map can be used by a fresh session. Exercise a representative journey from a clean checkout periodically.

Audit checks themselves: are tests discovered, assertions meaningful, exit codes propagated, branch gates active, missing/skipped statuses handled, and failure evidence retained? A pipeline can stay green while its protection quietly deteriorates.

## Retire unnecessary rules

Remove duplicate guidance, inaccurate recipes, and checks whose original risk no longer exists. Confirm the removal does not reintroduce covered failures. Keep decisions and history discoverable but concise; current guidance should not require reading an archive of conversations.

## Handoff

For interrupted or long-running work, leave a task record with current revision, working tree state, completed work, evidence, remaining hypotheses, blockers, and next action. A new agent should resume from that record without redoing completed verification unless code or environment changed.

Share a brief owner report when useful: completed behavior, defects caught or escaped, notable recurring failures, improvements made, remaining limits, and any proposed expansion of autonomy. The purpose is a better environment and less repetitive intervention, not a larger documentation system.
