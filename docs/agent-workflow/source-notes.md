# Source notes and adaptation boundaries

## Source used

The source is the user-provided `script.txt` YouTube talk transcript supplied with this task. It is an unstructured transcript with transcription errors and inconsistent product names. The video title, URL, date, timestamps, original slides, and original repository files were not supplied. This kit therefore attributes ideas to the supplied talk without claiming exact filenames or implementation details beyond those explicitly mentioned.

The previous chat summary helped identify the requested scope, but the transcript was read directly to ground the adaptation. The transcript is not redistributed in this kit. This is an original practical synthesis, not an official Lauren Tan document or a copy of PStack.

## Talk-to-kit mapping

| Idea in the supplied talk | Treatment in this kit |
|---|---|
| Verification is foundational; the agent should run the actual software | Verification contract, exercised journeys, setup/control/reset recipes |
| `control-glass` gave agents application control | Generic control runbook plus runtime-specific capability adapter |
| A feature map taught agents product navigation and context | Feature-map template linking user language, interface, code, fixtures, and expected behavior |
| PStack grew from observed failures and corrections | Incremental skills and correction-to-enforcement workflow |
| Create and maintain verification skills | Portable procedure definitions and same-change maintenance rules |
| Skills are evaluated with isolated workers, rubrics, and judges | Eval cases, reports, roles, and independent checking |
| Evaluation across models and iterative improvement | Optional comparative matrix, held-out cases, bounded improvement loops |
| Cloud agents reused verification and investigated incoming reports | Event-to-PR contract with the same canonical local/hosted procedures |
| A report could reproduce on a released version but be fixed on main | Explicit revision comparison and no-change triage outcome |
| Dune made conventional feature development easier and colocated code | Feature-oriented discovery and explicit extension points; no Electron-specific framework requirement |
| Architecture, static analysis, and CI provide harder constraints than Markdown/review | Invariant register with positive/negative cases and honest enforcement status |
| Runtime/process separation and dependency checks prevented mistakes | General boundary enforcement for whichever runtimes the project uses |
| Project-specific CI bans included `useEffect` and comments | Examples of tailored constraints, not universal rules |
| Automated AI review was an additional layer | Evidence-based reviewer protocol, with fallibility and required executable gates |
| Cohesive PRs improved rollback and Git context | Atomic changes with clear dependencies and no arbitrary line cap |
| Trust developed from close supervision toward auto-merge | Scoped autonomy stages and promotion evidence |
| Token cost and setup investment mattered | Bounded iterations, proportional adoption, and outcome/cost measurements |

## Additions made for a reusable system

The talk explains principles and examples rather than a complete cross-platform installation protocol. This kit adds explicit bootstrap sequencing, copy destinations, revision-bound evidence, check status semantics, authority records, deduplication/claims, timeout and budget controls, held-out evaluations, policy-change separation, missing/skipped-check treatment, recovery rehearsals, and migration guidance. These are engineering recommendations introduced here, not claims about Lauren's exact implementation.

All filenames apart from names explicitly mentioned in the transcript are this kit's design. The templates are intentionally unpopulated. Any tool commands, paths, selectors, protections, or thresholds must be established against the future project's actual environment.

## Limits

Documents alone do not provide browser control, event subscriptions, cloud workers, CI, branch protections, or automatic merge. Those capabilities must be installed, authorized, tested, and recorded per project. Compiler success and passing tests offer evidence for the properties they check; they do not prove absence of all defects. Independent agent review can still miss problems.

No specific model, vendor skill system, editor, framework, or deployment host is required. A tool that cannot automatically read repository instructions can still use this system when given an explicit instruction to read the entry point and linked records. An agent that lacks execution capabilities needs a real executor or an honestly reported verification gap.
