# Agents Guidance Skill

A high-signal skill for auditing, creating, and updating repository-level instruction files (`AGENTS.md`, `CLAUDE.md`, `.cursorrules`).

This skill trains AI agents to systematically inspect a codebase, identify hard-earned context, extract non-obvious commands and quirks, and write compact, actionable guidance while eliminating prompt bloat.

## Installation

### Via `skills.sh` CLI
```bash
npx skills add <github-username>/AgentSkills --skill agents-guidance
```

### Manual Installation
Copy the `agents-guidance` directory to your local skills directory:
```bash
cp -r skills/agents-guidance ~/.agent-skills/
# or into your project:
cp -r skills/agents-guidance .skills/
```

## When to Activate

Trigger this skill when:
- Creating a new `AGENTS.md` or updating an existing one.
- Setting up agent onboarding instructions for a new codebase or monorepo.
- Auditing existing prompt files for bloat, obsolete instructions, or missing commands.
- Configuring coding agents (OpenCode, Claude Code, Cursor, Codex, Antigravity) to operate effectively in your repository.

## What's Included

- [`SKILL.md`](./SKILL.md): Core procedural instructions and the "Would an agent miss this?" litmus test.
- [`references/agents-md-template.md`](./references/agents-md-template.md): Production-tested templates for minimal libraries, full-stack apps, and monorepos.
- [`references/agent-rules-checklist.md`](./references/agent-rules-checklist.md): Quality checklist to audit `AGENTS.md` before committing.
