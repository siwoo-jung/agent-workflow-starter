# 04 — Architecture and mechanical enforcement

## Make the conventional path the sound path

Agents copy nearby examples and favor short implementation paths. Provide one clear way to add a common feature, including its contracts, state, boundary adapters, tests, and verification entry. Put related behavior together where supported by the framework. Keep truly shared infrastructure small and purposeful.

Feature colocation is a principle, not a compulsory directory name. Route-based frameworks, embedded systems, data projects, and libraries may need different layouts. Follow the project's idioms while keeping discovery easy. Document code that must remain elsewhere and link it from the feature map.

Prefer explicit dependencies and small interfaces. Separate incompatible runtimes and trust boundaries structurally: client/server, UI/worker, domain/infrastructure, public/internal API, or tenant-owned/platform-owned data. Choose the boundaries the project actually needs; do not add layers with no observable purpose.

## The invariant register

Maintain `docs/project/invariants.md` using the [template](../../templates/agent-workflow/invariant-register.md). For every important rule record:

- A stable ID and precise prohibited or required behavior.
- The failure it prevents and the scope where it applies.
- The supported implementation path.
- The executable enforcement location and CI check name, if available.
- Positive and negative examples proving enforcement.
- Current status, owner, exceptions, and conditions for reevaluation.

A rule described in Markdown is advisory. A rule checked locally but not required remotely is not a merge gate. Mark status honestly: `advisory`, `local-check`, `ci-check`, or `required-gate`. Reserve `structural` for a boundary enforced by a checked architecture/compiler/runtime mechanism, not a directory naming convention alone.

## Move repeated corrections into enforcement

Use this progression when a failure recurs:

1. Record the concrete failure and its cost.
2. Clarify the correct pattern with a good example and focused instruction.
3. Reuse an existing analyzer, compiler facility, framework restriction, or linter if it can detect the rule.
4. Add a behavior or contract test where static enforcement is insufficient.
5. Redesign the extension point when the wrong path can be eliminated cheaply.
6. Verify positive/negative cases and make the check required at integration where appropriate.

AI review and skills are useful but fallible. Keep them for judgment, discovery, and context; use deterministic checks for mechanically decidable constraints. Not every engineering decision can or should become a lint rule.

| Recurring problem | Candidate enforcement | Remaining judgment |
|---|---|---|
| Wrong dependency direction | Import graph check or compiler/module boundary | Whether the chosen abstraction is useful |
| Custom duplicate of a library control | Component inventory and dependency checks where feasible | Whether a real functional or licensing gap exists |
| Invalid boundary input | Runtime validation and schema/contract tests | Whether the public contract meets user needs |
| Blocking work on a latency-sensitive path | Runtime separation plus representative performance test | Workload relevance and budget choice |
| Wrong tenant or authorization scope | Central policy interface and negative behavior tests | Completeness of the threat/permission model |
| Fragile navigation verification | Stable selectors and exercised feature-map recipes | Whether the journey covers real user behavior |
| Hallucinated diagnosis | Investigation procedure and evidence-based eval cases | Causal interpretation of incomplete evidence |

These are examples to adapt, not universal bans. In particular, this kit does not ban comments, hooks, unsafe language features, or any framework by name. A project-specific restriction needs a reason, a correct alternative, and tested enforcement.

## Reuse and dependency choices

Before implementing a common behavior, inspect the existing project library and maintained external options. Evaluate functional fit, license compatibility, maintenance, accessibility where relevant, runtime/bundle cost, security, and integration complexity. Use the library's full feature when it exists; assembling its primitives into a custom replacement still needs justification.

Record significant decisions, especially when choosing custom code. Pin or lock dependencies according to the ecosystem's supported method. Check authoritative current documentation when making version-sensitive decisions; do not use a remembered API or license as verified fact. External tooling is optional; keep the core procedure independent of a vendor.

## CI as an executable contract

Each required check has an exact name, command, scope, expected exit behavior, owner, and failure explanation. Local commands and CI should share definitions where practical. A gate should explain the violated rule and the valid alternative so agents can repair the cause.

Typical layers include formatting/lint, compiler/type analysis, dependency boundaries, unit/contract tests, integration checks, runtime journeys, relevant security checks, performance budgets, and documentation validation. Select layers by the project's actual risks. A fast project may use a few checks; a complex system needs more.

Verify test discovery and status propagation. If a path filter skips a job, define how the aggregate gate handles it; a skipped relevant check must not masquerade as success. Require checks for the candidate revision using the hosting system's controls. Test their effect rather than assuming a workflow file protects the branch.

For automated merging, ordinary implementation workers must not be able to bypass required gates or independently weaken CI, acceptance criteria, or protection settings. Give changes to those controls a separately authorized review path. Otherwise an agent can change the definition of success instead of satisfying it.

## Existing code and migrations

Characterize current behavior first. Isolate a seam, introduce the new conventional path, move one feature, verify equivalent behavior, then repeat. Use compatibility adapters where needed, with a removal plan. Keep each migration PR independently understandable and reversible where possible.

A rewrite proposal should compare incremental migration with replacement using concrete behavior coverage, delivery interruption, integration cost, runtime risk, and ongoing maintenance. Record an architecture decision and explicit scope authorization before broad replacement. Lauren's refactoring experience is evidence for investing in the environment; it is not a blanket instruction to rewrite projects.

## Exceptions

If a valid requirement conflicts with an invariant, record the affected rule, reason, scope, alternate evidence, owner, and expiration or review trigger. Apply the required policy review. Prefer a narrow explicit exception over a global disable. Exceptions to merge gates are governed by the owner and repository controls; an implementing agent cannot grant itself one.
