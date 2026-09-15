# Plan Pro Skill

A specialized AI agent skill that pairs with the user to thoroughly research, align on, and architect multi-step technical implementation plans before writing any code.

Plans are persisted to `.agents/agent-plans/<slug>.md` so developers can inspect, edit, and collaborate on the design before implementation starts.

## Installation

### Via `skills.sh` CLI
```bash
npx skills add AD-RIAN-Studio/AgentSkills --skill plan-pro
```

### Manual Installation
Copy the `plan-pro` directory into your agent skills directory:
```bash
cp -r skills/plan-pro ~/.agent-skills/
# or in a specific project:
cp -r skills/plan-pro .skills/
```

## When to Activate

Trigger this skill when:
- Designing a new feature, architecture refactoring, or complex bugfix.
- The user requests a plan or outline before code changes begin.
- Researching across multiple subsystems or services with parallel subagents.
- Requiring an interactive alignment phase with explicit scope boundaries and verification steps.

## Workflow

```text
Discovery ──► Alignment ──► Design ──► Refinement ──► Handoff
 (Research)    (Clarify)    (Draft)    (User Edits)    (Ready)
```

## What's Included

- [`SKILL.md`](./SKILL.md): Core planning rules, subagent parallel discovery, alignment workflows, and handoff protocols.
- [`references/plan-template.md`](./references/plan-template.md): Standardized markdown plan format for `.agents/agent-plans/`.
