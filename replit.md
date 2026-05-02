# Workspace

## Overview

pnpm workspace monorepo using TypeScript + Python. Each package manages its own dependencies.

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

### Clinic Price Scanner (`artifacts/clinic-scanner/`)
- **Type**: Python/Streamlit web app
- **Route**: `/` (root)
- **Port**: 5000
- **Stack**: Streamlit, requests, pandas, tenacity, beautifulsoup4
- **Purpose**: Find real posted price lists and fee schedules from clinics, occupational health centers, and hospitals. Strictly no aggregators (no ZocDoc, MDSave, FairHealth).
- **All 15 APIs integrated**: Serper, Exa, Tavily, LangSearch (search), Firecrawl, Jina, Scrapingdog, Browse AI, Browserbase, Olostep (scraping), Groq, OpenRouter, Minimax (LLM), Prospeo, Skrapp (enrichment)
- **Features**: Surgical search dorks, PDF/CSV prioritization, CMS price transparency, retry logic (tenacity), LLM price table extraction, batch extraction, CSV/JSON export
- **UI**: MacOS Tahoe glassmorphism — yellow/orange/purple palette

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.
