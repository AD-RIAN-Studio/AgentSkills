# Git Commit Message Skill

An AI agent skill for generating clean, conventional commit messages and safely executing git commits and pushes after explicit user confirmation.

## Installation

### Via `skills.sh` CLI
```bash
npx skills add <github-username>/AgentSkills --skill git-commit-message
```

### Manual Installation
Copy the `git-commit-message` directory to your local skills folder:
```bash
cp -r skills/git-commit-message ~/.agent-skills/
# or in a project repository:
cp -r skills/git-commit-message .skills/
```

## When to Activate

Trigger this skill when:
- Asking the agent to commit changes ("commit this", "create a commit").
- Generating a conventional commit message from git diff.
- Reviewing unstaged changes and deciding how to group files into commits.
- Safely staging, committing, and pushing with interactive confirmation.

## What's Included

- [`SKILL.md`](./SKILL.md): Complete instructions, confirmation protocol, and execution steps.
- [`references/conventional-commits.md`](./references/conventional-commits.md): Type reference, breaking change syntax, and good commit message examples.
