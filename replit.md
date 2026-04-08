# Workspace

## Overview

pnpm workspace monorepo using TypeScript. Each package manages its own dependencies.

This is **Replit2Api** — a self-hosted AI proxy gateway running on Replit that unifies OpenAI, Anthropic Claude, Google Gemini, and OpenRouter behind a single OpenAI-compatible API endpoint.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)

## Artifacts

- **api-server** (`/api`) — Backend proxy gateway. Routes AI requests to OpenAI, Anthropic, Gemini, OpenRouter. Supports streaming, tool calling, extended thinking.
- **api-portal** (`/`) — Frontend admin panel. 3-tab UI: Home / Stats & Nodes / API Docs. Includes SetupWizard and Fleet Manager for sub-node management.

## Key Libraries

- `lib/integrations-anthropic-ai` — Anthropic AI client integration helpers
- `lib/integrations-openai-ai-server` — OpenAI server-side integration helpers
- `lib/api-client-react` — Generated React Query hooks from OpenAPI spec
- `lib/api-spec` — OpenAPI spec + Orval codegen config
- `lib/api-zod` — Generated Zod schemas
- `lib/db` — Drizzle ORM schema + migrations

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally
- `pnpm --filter @workspace/api-portal run dev` — run admin portal locally

## Key Environment Variables (Secrets)

- `PROXY_API_KEY` — API key required for all proxy requests
- `OPENAI_API_KEY` — OpenAI API key
- `ANTHROPIC_API_KEY` — Anthropic/Claude API key
- `GEMINI_API_KEY` — Google Gemini API key
- `OPENROUTER_API_KEY` — OpenRouter API key
- `GITHUB_TOKEN` (optional) — for GitHub-based auto-update
- `DEFAULT_OBJECT_STORAGE_BUCKET_ID` (optional) — GCS bucket for cloud persistence

## Current Version

v1.1.7 — Per-model pricing calculation, per-model token stats, 47-model pricing table

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.
