# Project template index

These are fillable templates, not active project facts. `UNSET` means the value must be discovered or decided. `NOT_APPLICABLE` requires a reason. Never run an example path/command as though it were verified configuration.

## Required bootstrap records

Create `docs/project/` and copy these templates to the indicated destinations. Preserve existing authoritative records instead of making competing copies. Replace values with observed facts and source references.

| Template | Canonical project destination |
|---|---|
| [project-context.md](project-context.md) | `docs/project/context.md` |
| [feature-map.md](feature-map.md) | `docs/project/feature-map.md` |
| [verification-contract.md](verification-contract.md) | `docs/project/verification.md` |
| [invariant-register.md](invariant-register.md) | `docs/project/invariants.md` |
| [automation-policy.md](automation-policy.md) | `docs/project/automation-policy.md` |
| [capability-adapter.md](capability-adapter.md) | `docs/project/capabilities.md` |

## Records created when needed

| Template | Suggested destination/use |
|---|---|
| [task.md](task.md) | `docs/project/tasks/TASK-ID.md`; brief notes suffice for small changes |
| [verification-report.md](verification-report.md) | `docs/project/evidence/TASK-ID.md` or a linked CI artifact |
| [pull-request.md](pull-request.md) | PR body; optionally adapt to the host's native PR template path |
| [decision.md](decision.md) | `docs/project/decisions/DEC-ID.md` |
| [correction-record.md](correction-record.md) | `docs/project/corrections/COR-ID.md` |
| [skill.md](skill.md) | `docs/project/skills/SKILL-ID.md`; optional tool wrapper links here |
| [eval-case.md](eval-case.md) | `docs/project/evals/cases/CASE-ID.md` |
| [eval-report.md](eval-report.md) | `docs/project/evals/runs/RUN-ID.md` |
| [scoped-AGENTS.md](scoped-AGENTS.md) | `AGENTS.md` inside a feature/runtime directory, after completing its scope |

These paths are defaults. If the project uses another durable location, update links in the root entry point and context. Do not keep a filled record and its template under the same name without identifying which is authoritative. Avoid placing unfilled scoped instructions in a directory where agents will treat them as active policy.
