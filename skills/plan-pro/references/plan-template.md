# Implementation Plan Template

Use this format when generating or updating plans saved in `.agents/agent-plans/<slug>.md`.

---

```markdown
# Plan: {Title (2-10 words)}

## Summary
{TL;DR: concise explanation of what is changing, why, and the recommended technical strategy.}

## Scope
- **In-Scope**: {List of features, services, or boundaries addressed by this plan}
- **Out-of-Scope**: {Explicit non-goals or deferred functionality}

## Implementation Steps

### Phase 1: {Phase Name (if 5+ steps total)}
1. {Step description}
   - *Details*: {Specific patterns, functions, and interfaces}
   - *Dependencies*: None / Depends on Step X
2. {Step description}
   - *Dependencies*: Parallel with Step 1

### Phase 2: {Phase Name}
3. {Step description}
   - *Dependencies*: Depends on Phase 1

## Relevant Files & Symbols
- `{full/path/to/file.ext}`: {What to modify or add; reference specific types or methods}
- `{full/path/to/existing.ext}`: {Reference for patterns or fixtures to reuse}

## Verification Plan
1. **Automated Tests**:
   - `{exact command to run single test suite}`
   - `{exact command to run lint and typecheck}`
2. **Manual Verification**:
   - {Specific user flows or verification checks}

## Key Decisions & Trade-offs
- **{Decision Topic}**: {Chosen option and reasoning}
```

---

## Formatting Guidelines
- **Avoid pasting large code blocks in the plan**: Reference symbols, files, and signatures instead.
- **No unresolved blocking questions in the plan file**: Resolve blockers interactively in chat before finalizing.
- Keep file paths absolute or repository-relative for easy navigation.
