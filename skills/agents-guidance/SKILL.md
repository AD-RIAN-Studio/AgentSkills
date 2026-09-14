---
name: agents-guidance
description: >-
  Expert guidelines for auditing, creating, and updating high-signal AGENTS.md files,
  repository instructions, and agent rules. Use when asked to generate or update AGENTS.md,
  audit repo instructions, establish durable project guidelines for AI coding agents,
  or configure repository guidance for OpenCode, Claude Code, Cursor, and Codex.
---

# AGENTS Guidance Skill

This skill provides a rigorous methodology for creating, auditing, and maintaining `AGENTS.md` and repository instruction files.

The primary objective of `AGENTS.md` is to serve as a **compact, durable instruction file** that helps AI coding sessions avoid mistakes and ramp up immediately without wasting context.

---

## Core Guiding Principle

> **The Litmus Test:**
> Every line must answer: *"Would an agent likely miss or guess this wrong without help?"*
> If the answer is no, **leave it out**.

Good `AGENTS.md` content is hard-earned context that typically requires reading multiple files to infer.

---

## 1. Investigation Protocol

Do not make assumptions or write speculative guidance. Follow this prioritized order of investigation:

### Step 1: Executable Sources of Truth (Highest Value)
1. **Root manifests & configs**: `package.json`, `Cargo.toml`, `pyproject.toml`, `go.mod`, `build.gradle`, etc.
2. **Workspace & lockfiles**: `pnpm-workspace.yaml`, `lerna.json`, `uv.lock`, `pnpm-lock.yaml`, etc.
3. **Build, test, lint, format, typecheck, & codegen configs**:
   - `tsconfig.json`, `eslint.config.*`, `.prettierrc`, `ruff.toml`, `Makefile`, `Justfile`, `CMakeLists.txt`
4. **CI workflows & Task Runners**:
   - `.github/workflows/`, `.gitlab-ci.yml`, pre-commit configs (`.pre-commit-config.yaml`).
5. **Existing instructions & agent configs**:
   - `AGENTS.md`, `CLAUDE.md`, `.cursor/rules/`, `.cursorrules`, `.github/copilot-instructions.md`, `opencode.json`.

### Step 2: Architecture & Entrypoint Inspection
If architecture remains unclear after reading configs:
- Inspect a small set of representative entrypoints (e.g. `main.*`, `index.*`, server bootstrap, router definitions).
- Trace real package boundaries and execution flow.
- Prefer files that explain system wiring over leaf implementation files.

### Step 3: Executable vs. Prose Conflicts
- **Always trust executable configs and scripts over prose documentation.**
- If `README.md` claims `npm test` works, but `package.json` specifies `pnpm test:unit` with specific flags, record the executable command. Only keep facts you can verify.

---

## 2. What to Extract (High-Signal Facts)

Focus strictly on facts that change how an agent operates:

1. **Exact Developer Commands**:
   - Non-obvious build, run, and dev commands.
   - Exact command to run a **single test**, a single package, or a focused verification step.
   - Required sequence if order matters (e.g., `codegen -> typecheck -> test:unit`).

2. **Monorepo & Package Boundaries**:
   - Workspace package ownership, internal dependency relationships, and boundary rules.
   - Core app vs. shared library entrypoints.

3. **Toolchain & Framework Quirks**:
   - Required codegen steps (`prisma generate`, `proto-gen`, `graphql-codegen`).
   - Database migrations or local seed flows.
   - Generated files that should never be edited directly.
   - Special environment loading requirements or mandatory runtime flags.

4. **Testing Quirks**:
   - Required local services (Docker, emulator, Redis).
   - Snapshot update commands and fixture conventions.
   - Suites that are flaky, slow, or require external credentials.

5. **Repo-Specific Conventions**:
   - Conventions that intentionally deviate from standard language or framework defaults.
   - Git branch/commit constraints (e.g., conventional commits, linear history).

---

## 3. What to Exclude (Strict Filtering)

To prevent prompt bloat and context contamination, **exclude**:

- ❌ **Generic software advice**: e.g., "Write clean code", "Handle errors gracefully", "Use descriptive names".
- ❌ **Long tutorials & file listings**: Avoid exhaustive file tree listings (agents have search tools).
- ❌ **Obvious language/framework defaults**: Standard Python PEP8 or standard Go idioms that tools already format.
- ❌ **Speculative or unverified claims**: Anything not substantiated by config, scripts, or user confirmation.
- ❌ **Redundant documentation**: Content that belongs in docs, unless an agent would actively fail without it.

*When in doubt, omit.*

---

## 4. Asking Questions

Only ask the user questions if the repository cannot answer something critical.
Keep questions to a single, concise batch.

**Legitimate questions:**
- Undocumented team conventions (e.g., "Do you require changeset files for PRs?").
- Deployment or release expectations not captured in CI.
- Missing environment setup or external service dependencies known only to the team.

**Do NOT ask** about anything verifiable from the codebase or config files.

---

## 5. Structuring & Updating `AGENTS.md`

### Updating an Existing File
- **Improve in-place**: Never blow away an existing `AGENTS.md` blindly.
- Preserve verified, useful context.
- Delete stale, inaccurate, or fluffy claims.
- Reconcile contradictory guidance with executable config.

### Standard Layout Recommendation
Keep it concise (< 150 lines for typical repos, < 250 lines for complex monorepos):

```markdown
# AGENTS.md

## Overview & Architecture
[2-4 bullets on core system boundaries, entrypoints, and mental models not obvious from file names]

## Essential Commands
[Exact, verified commands: dev, build, lint, typecheck]

## Testing & Verification
[How to run single test, test suites, integration prerequisites, snapshot commands]

## Toolchain Quirks & Codegen
[Generated files, build artifacts, required command ordering, migration workflows]

## Non-Standard Conventions
[Specific deviations from framework norms, commit patterns, or strict restrictions]
```

See [references/agents-md-template.md](references/agents-md-template.md) for tailored templates across minimal, standard, and monorepo codebases.
See [references/agent-rules-checklist.md](references/agent-rules-checklist.md) for the pre-commit review checklist.
