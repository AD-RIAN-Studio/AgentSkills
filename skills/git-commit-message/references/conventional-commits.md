# Conventional Commits Reference

Standard specification for formatting git commit messages.

## Format

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

---

## Common Types

| Type | Description | Example |
| :--- | :--- | :--- |
| `feat` | Introduces a new feature to the codebase | `feat(auth): add OAuth2 provider support` |
| `fix` | Patches a bug | `fix(api): handle null payload gracefully` |
| `docs` | Documentation-only changes | `docs(readme): add troubleshooting section` |
| `style` | Formatting, white-space, missing semi-colons (no code logic change) | `style: format imports according to style guide` |
| `refactor` | Code change that neither fixes a bug nor adds a feature | `refactor(parser): extract token validation helper` |
| `perf` | Code change that improves performance | `perf(query): index user_id on accounts table` |
| `test` | Adding missing tests or correcting existing tests | `test(order): add unit tests for discount calculator` |
| `build` | Changes affecting build system or external dependencies | `build: upgrade typescript to v5.5` |
| `ci` | Changes to CI configuration files and scripts | `ci: add GitHub Actions matrix for Node 18/20` |
| `chore` | Routine maintenance, tooling changes | `chore: update .gitignore and clean up scripts` |

---

## Breaking Changes

Indicate breaking changes with a `!` after type/scope or a `BREAKING CHANGE:` footer:

```text
feat(api)!: remove deprecated v1 user endpoints

BREAKING CHANGE: The /api/v1/users endpoint has been decommissioned. Use /api/v2/users instead.
```

---

## Imperative Mood Guide

Use imperative mood in the short summary:
- ✅ `feat: add user authentication`
- ❌ `feat: added user authentication`
- ❌ `feat: adds user authentication`
- ❌ `feat: adding user authentication`
