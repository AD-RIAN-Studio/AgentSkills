# Agent Skills

An open-source collection of specialized AI agent skills designed for coding agents, compatible with [`skills.sh`](https://skills.sh) and the Agent Skills standard (`npx skills`).

These skills use **progressive disclosure**—delivering targeted procedural knowledge, reference templates, and guidelines only when activated by an agent.

## Available Skills

| Skill | Description | Direct Install |
| :--- | :--- | :--- |
| [`agents-guidance`](./skills/agents-guidance/) | High-signal methodology for creating, auditing, and maintaining `AGENTS.md` and repository-level instructions. | `npx skills add <user>/AgentSkills --skill agents-guidance` |

## Installation & Usage

### Using `skills.sh` CLI
Install any skill directly into your project's local agent configuration:

```bash
# Install a specific skill
npx skills add <github-username>/AgentSkills --skill agents-guidance

# Or install from local path (if cloned)
npx skills add ./skills/agents-guidance
```

### Manual Installation
Copy the target folder under `skills/<skill-name>/` to your local agent skills directory (e.g. `.skills/<skill-name>` or `.agent-skills/<skill-name>`).

## Skill Directory Structure

Every skill in this repository follows the Agent Skills specification:

```text
skills/<skill-name>/
├── SKILL.md            # Required: YAML frontmatter + procedural guidance
├── README.md           # Documentation for human developers
└── references/         # Extended templates, checklists, and reference guides
```

## Contributing

1. Create a directory: `skills/<your-skill-name>/`
2. Add `SKILL.md` with required YAML frontmatter (`name` and `description`).
3. Place detailed templates or heavy reference material in `references/` to keep `SKILL.md` concise (< 500 lines).
4. Submit a Pull Request!

## License

[MIT](LICENSE)
