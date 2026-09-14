# AGENTS.md

## Repository Overview
Collection of open-source AI agent skills distributed via `skills.sh`. Every skill must be modular, portable, and adhere to the Agent Skills standard.

## Skill Architecture & Locations
- Skills reside in `skills/<skill-name>/`. Do not place skills at repository root.
- Skill folder names must match the skill's `name` in `SKILL.md` (kebab-case, e.g., `agents-guidance`).
- Directory structure per skill:
  ```text
  skills/<skill-name>/
  ├── SKILL.md          # Core instructions with YAML frontmatter (required)
  ├── README.md         # Public overview & install instructions (recommended)
  └── references/       # Supporting templates, checklists, and deep-dive context
  ```

## Skill Authoring Constraints
- `SKILL.md` MUST begin with YAML frontmatter containing:
  ```yaml
  ---
  name: <skill-name>
  description: <Concise trigger summary: what it does and when to activate it>
  ---
  ```
- Keep `SKILL.md` concise (< 500 lines). Offload large templates, schema definitions, and verbose samples into `references/`.
- Frontmatter `description` is indexed by agent planners for progressive disclosure; be explicit about trigger phrases and task scenarios.

## Verification
- Validate YAML frontmatter parses cleanly.
- Verify all relative file links in `SKILL.md` and `README.md` resolve to real files.
- Ensure no accidental binary, secret, or temp files (`.DS_Store`, `.env`) are committed.
