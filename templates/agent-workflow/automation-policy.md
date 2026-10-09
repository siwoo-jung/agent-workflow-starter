# Automation and action policy

Status: baseline — no unattended merge or deployment configured.
Policy owner/authorizing role: UNSET.
Approved revision/date and authorization reference: UNSET.
Current autonomy stage and scope: 0 — assisted, until assessed and authorized.

## Authority

Routine reversible local implementation and verification within an assigned task are permitted. External actions follow explicit authorization in the task or this completed policy. Record authorization already supplied; do not ask for the same permission repeatedly. `UNSET` is not a grant of external authority.

| Action | Authorized actor/role | Repository/environment/scope | Authorization reference | Limits |
|---|---|---|---|---|
| Create branch/commit remotely | UNSET | UNSET | UNSET | UNSET |
| Open/update PR | UNSET | UNSET | UNSET | UNSET |
| Review and repair | UNSET | UNSET | UNSET | UNSET |
| Merge after required review | UNSET | UNSET | UNSET | UNSET |
| Enable/use automatic merge | UNSET | UNSET | UNSET | disabled until completed policy and enforced gates |
| Deploy/release | UNSET | UNSET | UNSET | UNSET |
| Destructive/data operations | UNSET | UNSET | UNSET | UNSET |
| Send external/person-directed messages | UNSET | UNSET | UNSET | UNSET |
| Change CI, policy, protections, credentials | UNSET | UNSET | UNSET | separate policy-change review authority |

## Automatic merge — initially disabled

- Eligible change classes and allowed paths: none.
- Excluded change classes/paths: all until a scope is approved.
- Required acceptance/runtime evidence: UNSET.
- Exact required checks and missing/skipped-check rules: UNSET.
- Required independent review and blocking-finding policy: UNSET.
- Final head/base validation or merge-queue mechanism: UNSET.
- Merge strategy, prerequisite PR handling, conflict policy: UNSET.
- Confirmed repository enforcement and bypass restrictions: UNSET.
- Separate reviewer for CI/policy/verification changes: UNSET.
- Post-merge checks, failure signals, and owners: UNSET.
- Recovery mechanism and drill evidence: UNSET.

Change this section only with owner authorization and observed enforcement. A label or reviewer score alone cannot establish eligibility.

## Workers and intake

- Authorized trigger sources/task classes: UNSET.
- Event/task identity and deduplication/claim mechanism: UNSET.
- Workspace isolation and base revision capture: UNSET.
- Credential permission scope and secret source: UNSET.
- Environment/control adapter: UNSET.
- Evidence retention and redaction: UNSET.
- Attempt/time/cost limits and concurrency: UNSET.
- Cleanup and abandoned-task recovery: UNSET.

## Escalation and recovery

- Required owner decisions: material scope ambiguity; unapproved external action; policy/gate change; unresolved blocking review; incomplete required evidence.
- On blocked work: preserve artifacts, finish independent authorized work, report exact next action.
- Kill-switch mechanism, owner, and accessible location: UNSET.
- Authorized revert/roll-forward actions: UNSET.
- Failure notification destination and messaging authority: UNSET.
- Resumption criteria after escaped defect: UNSET.
- Next policy review triggers/cadence: UNSET.
