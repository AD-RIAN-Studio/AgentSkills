# AGENTS.md Templates

Use these reference templates when creating or updating `AGENTS.md` files. Choose the template that matches the project's scale.

---

## 1. Minimal Template (Single library / small CLI / flat app)

```markdown
# AGENTS.md

## Project Overview
[1-2 sentences on what this project builds and the main entrypoint]

## Commands
- Build: `npm run build`
- Lint & Format: `npm run lint`
- Typecheck: `npm run typecheck`
- All Tests: `npm test`
- Single Test: `npm test -- path/to/file.test.ts -t "test name pattern"`

## Key Conventions & Quirks
- [Quirk 1: e.g. Do not edit src/generated/*.ts directly; run `npm run codegen`]
- [Quirk 2: e.g. Requires local .env with TEST_DATABASE_URL to run integration tests]
```

---

## 2. Standard Template (Full-Stack / Multi-Service Application)

```markdown
# AGENTS.md

## Overview & Architecture
- Core stack: [Language / Framework / Database / Transport]
- Entrypoints:
  - API / Backend: `src/server.ts`
  - Client / UI: `src/client/main.tsx`
- Routing & Data Flow: [State mental model or request lifecycle quirks]

## Verification Commands
- Dev Server: `pnpm dev`
- Typecheck: `pnpm typecheck`
- Lint: `pnpm lint`
- Unit Tests (all): `pnpm test:unit`
- Unit Test (single): `pnpm vitest run path/to/spec.ts`
- E2E Tests: `pnpm test:e2e` (requires `docker compose up -d db`)

## Execution Order
When verifying changes, run in this sequence:
`pnpm lint -> pnpm typecheck -> pnpm test:unit`

## Toolchain & Codegen Quirks
- Database migrations: `pnpm db:migrate` (do not run `db:push` in production scripts).
- Codegen: After modifying GraphQL schemas or Prisma files, run `pnpm codegen`.
- Generated files: Files under `src/generated/` and `*.generated.ts` are auto-generated.

## Strict Conventions
- Error handling: Use domain-specific error classes from `src/errors/`.
- Styling: Use Tailwind utility classes; avoid inline CSS or custom CSS modules.
- Commits: Follow Conventional Commits (`feat: ...`, `fix: ...`, `chore: ...`).
```

---

## 3. Monorepo Template (Turborepo / Nx / pnpm Workspaces)

```markdown
# AGENTS.md

## Monorepo Architecture
- Package Manager: `pnpm` (configured via `pnpm-workspace.yaml`)
- Core packages:
  - `apps/web`: Frontend application (Next.js)
  - `apps/api`: Backend service (Fastify)
  - `packages/ui`: Shared React components
  - `packages/config`: Shared tsconfig, eslint, and tailwind presets
- Package boundaries: Apps may import packages; packages must never import apps.

## Focused Commands
- Filtered build: `pnpm --filter @repo/web build`
- Filtered test: `pnpm --filter @repo/api test`
- Single test in package: `pnpm --filter @repo/api test -- src/user.service.spec.ts`
- Global verification: `pnpm turbo run lint typecheck test`

## Environment & Prerequisites
- Node version: Managed via `.nvmrc` (v20+)
- Local services: Run `docker compose -f docker-compose.dev.yml up -d` for Postgres and Redis.
- Environment variables: Copy `.env.example` to root and `apps/*/.env.local`.

## Quirks & Rules
- Shared dependency additions: Use `pnpm --filter <pkg> add <dep>` (avoid root `pnpm add` unless tooling).
- Build graph caching: Turbo cache keys depend on environment variables listed in `turbo.json`.
```
