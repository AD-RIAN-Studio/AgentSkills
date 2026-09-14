# AGENTS.md Audit Checklist

Before finalizing or committing an `AGENTS.md` file, run through this checklist to ensure maximum signal-to-noise ratio.

---

## 1. High-Signal Filter
- [ ] **Litmus Test Passed**: Does every single bullet or line tell an agent something it would likely miss or get wrong otherwise?
- [ ] **Zero Fluff**: Are generic tips removed? (e.g., "Write testable code", "Keep functions small", "Be polite").
- [ ] **No Default Idioms**: Are standard language norms (e.g. Go formatting, Rust clippy defaults, PEP 8) omitted unless the repo deviates from them?
- [ ] **No Redundant Trees**: Is the full repository file tree omitted in favor of targeted entrypoints and boundaries?

## 2. Command Accuracy & Verification
- [ ] **Executable Verification**: Did you verify commands against `package.json`, `Makefile`, or CI files rather than prose docs?
- [ ] **Single Test Command**: Is there an explicit command for running a single test file or targeted suite?
- [ ] **Command Ordering**: If lint, typecheck, codegen, or tests depend on a specific sequence, is the sequence explicitly stated?
- [ ] **Monorepo Filtering**: For workspaces/monorepos, are filtered commands documented (e.g., `pnpm --filter <app> test`)?

## 3. Toolchain & Operational Gotchas
- [ ] **Codegen Documented**: Are code generators (Prisma, GraphQL, Protobuf, OpenAPI) and their generated target paths listed?
- [ ] **Generated Files Marked Do-Not-Edit**: Are generated directories explicitly noted so agents don't edit them directly?
- [ ] **Prerequisites Explicit**: Are external dependencies (Docker, Redis, local ports, required env vars) documented?

## 4. Brevity & Maintainability
- [ ] **Line Count**: Is the file concise (< 150 lines for standard projects, < 250 for large monorepos)?
- [ ] **Scannable**: Uses bulleted lists, bold prefixes, and backticked commands for immediate agent consumption.
- [ ] **In-place Reconciliation**: If updating an existing `AGENTS.md`, were historical verified facts retained and only stale parts removed?
