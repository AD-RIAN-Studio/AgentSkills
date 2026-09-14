---
name: git-commit-message
description: >-
  Inspects unstaged and staged git changes to generate concise, conventional commit messages.
  Guides the user to review, confirm, and safely commit or push changes. Use whenever the user
  asks to commit changes, draft a commit message, generate a git commit, or review git diffs.
---

# Git Commit Message Skill

Use this skill when the user wants help creating a clean commit message or safely committing and pushing changes from current git modifications.

---

## Core Rules

1. **Explicit Confirmation Required**: Never create commits or push upstream unless the user explicitly confirms with a clear affirmative reply (`yes`, `ok`, `confirm`, or equivalent).
2. **Conventional Commit Style**: Prefer the format `type(scope): summary`.
3. **High Signal & Concise**: Keep messages short, imperative, and useful. Include a short body only when the diff needs non-obvious reasoning.
4. **Safe Defaults**: Inspect before staging; confirm before mutating git state; summarize affected paths before running commands.
5. **No-Pager Execution**: Run git commands with `--no-pager` and avoid interactive/editor-blocking flows.
6. **Zero-Diff Handling**: If nothing is changed or staged, notify the user instead of inventing a commit.
7. **Cohesive Changes**: If the working tree contains mixed, unrelated changes, recommend splitting them into targeted commits.

---

## Workflow

### 1. Inspect Git State
Gather the current status and diff statistics:
```bash
git --no-pager status
git --no-pager diff --stat
git --no-pager diff --cached --stat
git --no-pager log -n 5 --oneline  # Context on recent repo commit style
```

### 2. Determine Scope of Commit
- Prefer staging only files relevant to a coherent change.
- If the user explicitly instructed to commit all changes and the diff is cohesive, plan `git add -u` or explicit paths.
- If changes span multiple distinct concerns, recommend separate commits or staging a subset first.

### 3. Draft Proposed Commit Message
- **Format**: `type(scope): summary`
- **Common Types**: `feat`, `fix`, `refactor`, `chore`, `docs`, `test`, `perf`, `build`, `ci`, `style`. (See [references/conventional-commits.md](references/conventional-commits.md)).
- **Scope**: Derived from the affected module, package, or directory path.
- **Summary**: Imperative mood ("add", "fix", "update", not "added" or "fixing"), <= 72 characters.
- **Body** (optional): Explain *why* the change was made if non-obvious. Avoid AI meta-commentary (e.g. "as discussed").

### 4. Present Proposal to User
Display:
1. The proposed commit message.
2. The list of files to be included.
3. The proposed action (commit only vs. commit and push).
4. Confirmation prompt in this exact pattern:
   > "Reply `yes` to commit with this message, or `yes and push` to commit and push."

### 5. Execute Upon Confirmation
- **If user replies `yes`**:
  Stage the planned files and execute `git commit -m "<message>"`.
- **If user replies `yes and push`**:
  Stage the planned files, commit, and run `git push` to the current tracking branch.
- **If user requests edits**:
  Revise the commit message or file selection and re-prompt.

### 6. Report Execution
Report the resulting commit hash, active branch, and push status.

---

## Behavior When Diff is Unsuitable

If the working tree is dirty with unrelated changes or conflicting concerns:
- Identify the distinct logical groupings.
- Propose committing one subset first.
- Provide the exact files planned for the first commit, deferring the remainder.