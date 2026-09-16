# Recommended Global Skills

A curated list of high-impact, battle-tested AI agent skills recommended for every coding workspace.

These skills extend agent capabilities with structured planning, repo guidance, design expertise, PDF tooling, and conventional git workflows across supported agents (OpenCode, Claude Code, Cursor, Copilot, Antigravity, etc.).

---

## Quick Install (All Recommended Skills)

Install the full recommended suite globally in your environment:

```bash
# AD-RIAN Studio Skills
npx skills add AD-RIAN-Studio/AgentSkills -g

# Community & Production Skills
npx skills add anthropics/skills --skill frontend-design -g
npx skills add anthropics/skills --skill pdf -g
npx skills add mattpocock/skills --skill grill-me -g
npx skills add vercel-labs/skills --skill find-skills -g
```

---

## Skills Catalog

| Skill | Source / Repo Slug | Category | Description |
| :--- | :--- | :--- | :--- |
| **`agents-guidance`** | `AD-RIAN-Studio/AgentSkills` | Architecture / Standards | Guidelines for auditing, writing, and maintaining compact `AGENTS.md` repo instructions. |
| **`plan-pro`** | `AD-RIAN-Studio/AgentSkills` | Planning / Research | Discovers context with subagents, aligns with user, and creates durable plans in `.agents/agent-plans/`. |
| **`git-commit-message`** | `AD-RIAN-Studio/AgentSkills` | Git / Workflow | Inspects git diffs to generate conventional commits and prompts safe confirmation before committing/pushing. |
| **`frontend-design`** | `anthropics/skills` | UI / Frontend | Deliberate, intentional visual design guidance for distinctive UI, typography, and styling without cliché defaults. |
| **`pdf`** | `anthropics/skills` | Document Processing | Comprehensive toolkit for reading, extracting, combining, rotating, OCR-ing, and generating PDF documents. |
| **`grill-me`** | `mattpocock/skills` | Architecture / Review | Interactive, relentless interview session to stress-test and sharpen an implementation plan or design. |
| **`find-skills`** | `vercel-labs/skills` | Discovery | Helps agents and users search and discover new skills from the open `skills.sh` registry. |

---

## Detailed Overview & Triggers

### 1. `agents-guidance`
- **Slug**: `AD-RIAN-Studio/AgentSkills --skill agents-guidance`
- **When to Use**: When creating or auditing an `AGENTS.md` file, establishing repository rules, or ramping up AI agents on a new codebase.
- **Why it's Essential**: Enforces the *"Would an agent miss this without help?"* litmus test to eliminate prompt bloat while capturing hard-earned command ordering and quirks.

```bash
npx skills add AD-RIAN-Studio/AgentSkills --skill agents-guidance -g
```

---

### 2. `plan-pro`
- **Slug**: `AD-RIAN-Studio/AgentSkills --skill plan-pro`
- **When to Use**: When asked to "plan", "design", "research", or "architect" a feature, refactor, or complex task before touching code.
- **Why it's Essential**: Uses parallel subagents for discovery, aligns interactively on trade-offs, and writes a reviewable markdown plan file to `.agents/agent-plans/<slug>.md`.

```bash
npx skills add AD-RIAN-Studio/AgentSkills --skill plan-pro -g
```

---

### 3. `git-commit-message`
- **Slug**: `AD-RIAN-Studio/AgentSkills --skill git-commit-message`
- **When to Use**: When ready to commit changes ("commit this", "draft commit").
- **Why it's Essential**: Analyzes staged/unstaged diffs, suggests precise conventional commit messages (`feat(...)`, `fix(...)`), and enforces explicit user confirmation before executing `git commit` or `git push`.

```bash
npx skills add AD-RIAN-Studio/AgentSkills --skill git-commit-message -g
```

---

### 4. `frontend-design`
- **Slug**: `anthropics/skills --skill frontend-design`
- **When to Use**: Whenever building new UI components, styling web pages, or redesigning an application.
- **Why it's Essential**: Prevents generic, templated AI frontend designs by making bold, opinionated choices around color palettes, typography, spacing, and micro-interactions.

```bash
npx skills add anthropics/skills --skill frontend-design -g
```

---

### 5. `pdf`
- **Slug**: `anthropics/skills --skill pdf`
- **When to Use**: When reading, summarizing, parsing tables, splitting, merging, or generating PDF files.
- **Why it's Essential**: Equips agents with practical command recipes and python scripts to manipulate and extract high-fidelity text and structure from PDFs.

```bash
npx skills add anthropics/skills --skill pdf -g
```

---

### 6. `grill-me`
- **Slug**: `mattpocock/skills --skill grill-me`
- **When to Use**: Before starting a major refactor or new architectural feature.
- **Why it's Essential**: The agent conducts an in-depth, interview-style grilling session with you to uncover edge cases, technical trade-offs, and unstated assumptions before coding begins.

```bash
npx skills add mattpocock/skills --skill grill-me -g
```

---

### 7. `find-skills`
- **Slug**: `vercel-labs/skills --skill find-skills`
- **When to Use**: When you ask "is there a skill for X?", "how do I do Y?", or want to search the `skills.sh` registry.
- **Why it's Essential**: Allows the agent to query the global directory of skills and recommend additions directly in chat.

```bash
npx skills add vercel-labs/skills --skill find-skills -g
```

---

## Keeping Skills Updated

Update all installed global skills from their upstream GitHub repositories at any time:

```bash
npx skills update -g
```
