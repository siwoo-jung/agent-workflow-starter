# Agent Workflow Starter

**A reusable starting point for projects developed with AI agents.**

This kit turns the principles from a recording of Lauren Tan's approximately one-hour Zoom workshop into a project-independent operating system for development: agents can understand the product, exercise it, verify their changes, work within enforced boundaries, and earn progressively wider autonomy. It works with one agent or a team, locally or in a hosted environment, without requiring a particular model, editor, agent framework, or programming language.

The core loop is **inspect → reproduce or specify → implement → verify → review → integrate → learn**. Documents provide context; executable checks and repository controls enforce the important constraints. Installing these documents alone does not install tooling or make a project ready for unattended merging.

## Start a future project

1. Copy `AGENTS.md`, `docs/agent-workflow/`, and `templates/agent-workflow/` into the project. If it already has agent instructions, reconcile them instead of overwriting them.
2. Give the first agent the bootstrap prompt below. Agents that do not automatically discover `AGENTS.md` must be instructed to read it explicitly.
3. The agent follows [Bootstrap](docs/agent-workflow/01-bootstrap.md), creates the project-specific records, and proves one end-to-end verification path.
4. Build the first small feature with a reviewer. Expand automation only after measured evidence supports it.

The initial owner supplies the intended product and any real constraints. The agent discovers the rest where possible, records assumptions, and asks only about decisions that affect correctness, scope, or authorization. Routine local work should not require repeated permission.

```text
Read AGENTS.md and docs/agent-workflow/01-bootstrap.md before changing code.
Bootstrap this project using the starter kit. Inspect existing files and preserve
working conventions. Populate docs/project/ from the provided templates with
observed facts, executable commands, and explicitly marked unknowns. Establish
one real verification loop and the first enforced architectural invariant.
Use the project goal and constraints I provide; choose reversible details yourself.
Do not claim that checks, controls, or automation exist until you have verified them.
Then report what is ready, what remains blocked, and the next smallest feature.

Project goal: [describe the product and its users]
Constraints: [known stack, environment, integrations, time, budget, data constraints]
Authorized external actions: [for example: create branches and PRs in this repo]
```

## Where to read

| Document | Use it for |
|---|---|
| [AGENTS.md](AGENTS.md) | Entry point and durable operating rules for every agent |
| [01 — Bootstrap](docs/agent-workflow/01-bootstrap.md) | Starting a new project or adopting an existing one |
| [02 — Execution](docs/agent-workflow/02-execution.md) | Features, bugs, task handoffs, review, and completion |
| [03 — Verification](docs/agent-workflow/03-verification.md) | Application control, feature maps, evidence, and verifier reliability |
| [04 — Architecture and enforcement](docs/agent-workflow/04-architecture.md) | Conventions, dependencies, static checks, and CI gates |
| [05 — Skills and evaluations](docs/agent-workflow/05-skills-and-evals.md) | Improving reusable procedures and testing agent behavior |
| [06 — Automation](docs/agent-workflow/06-automation.md) | Hosted workers, event intake, review, merge eligibility, and recovery |
| [07 — Maintenance](docs/agent-workflow/07-maintenance.md) | Keeping context current and converting failures into improvements |
| [Source notes](docs/agent-workflow/source-notes.md) | What comes from the workshop and what this kit adds |
| [Template index](templates/agent-workflow/README.md) | Copy destinations and fillable project records |

## The layers

| Layer | Responsibility | Example |
|---|---|---|
| Architecture | Make the easiest implementation path a sound one | Feature-local code and explicit runtime boundaries |
| Mechanical verification | Reject detectable violations | Compiler, dependency analysis, lint, behavioral tests |
| Product context | Explain what the software does and how to exercise it | Feature map, fixtures, acceptance criteria |
| Procedures | Explain how agents investigate, implement, and verify | Markdown skills and runbooks |
| Evaluation | Test whether procedures improve actual agent behavior | Seeded failures, held-out cases, independent scoring |
| Review and integration | Decide what may land and under which evidence | Required checks, review findings, explicit merge policy |
| Operations | Detect and recover from failures after integration | Smoke checks, telemetry, rollback, automation kill switch |

## Adoption size

For a small project, start with one context record, one verification contract, a feature map for the first journey, a short invariant register, and the baseline automation policy. Keep one task record per meaningful change. Add skills, evaluations, hosted workers, and larger automation only where they solve observed problems. Do not create a large process before the project needs it.

All project templates deliberately contain `UNSET` values. They are prompts for discovery, not working settings. An unset command is unavailable; an unset merge policy grants no merge authority. The project owner can authorize wider scope in the current task or in a completed policy record.

## Updating this kit

Keep the universal playbook separate from `docs/project/`, where the project's facts and decisions live. Review starter updates as normal changes; preserve local policy and adapt consciously. The kit has no vendor-native configuration files. A thin tool-specific adapter may point to these canonical documents without duplicating their rules.

## Provenance

This is an original synthesis based on a recording of an approximately one-hour Zoom workshop led by Lauren Tan, not Lauren Tan's actual PStack files, Dune implementation, or an official distribution. The workshop video itself is not bundled, and its title, URL, and date are not included in this repository. See [Source notes](docs/agent-workflow/source-notes.md) for attribution and limits.
