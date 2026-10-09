# Agent capability adapter

Owner/role: UNSET.
Agent runtime/tooling tested: UNSET.
Last validated revision/date: UNSET.

This maps required capabilities to actual tools. It does not duplicate policy or require a particular model. A thin vendor-native instruction file can say: “Read root AGENTS.md and linked project records before work.” Test that the runtime actually reads them.

| Capability | Actual tool/command/API | Tested usage | Equivalent fallback | Availability/limits |
|---|---|---|---|---|
| Read instructions and code | UNSET | UNSET | explicit document loading | UNSET |
| Edit files and inspect diff | UNSET | UNSET | UNSET | UNSET |
| Execute build/checks | UNSET | UNSET | external executor with evidence | UNSET |
| Start/stop application | UNSET | UNSET | UNSET | UNSET |
| Exercise product surface | UNSET | UNSET | documented equivalent | UNSET |
| Capture logs/traces/evidence | UNSET | UNSET | UNSET | UNSET |
| Branch/commit/PR operations | UNSET | UNSET | authorized host API/CLI | UNSET |
| Independent review session | UNSET | UNSET | sequential reviewer or declared self-review | UNSET |
| Isolated worker/eval sessions | UNSET | UNSET | sequential fresh sessions | UNSET |
| Hosted/event execution | UNSET | UNSET | manual intake and local execution | UNSET |

- Instruction discovery and scope test: UNSET.
- Permissions from automation policy: UNSET.
- Unavailable capabilities and affected workflow stages: UNSET.
- Installation/setup references (no secrets): UNSET.
- Adapter smoke journey and evidence: UNSET.
- Revalidation triggers: runtime/tool version, permissions, control surface, or environment changes.

If a fallback cannot provide equivalent evidence, report the gap. A model's ability to describe a tool is not evidence that the tool is available or executed.
