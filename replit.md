# Connecting Neighbors

## Overview

A hyperlocal community app for residential colonies where neighbors connect, share resources, post announcements, buy/sell locally, coordinate rides, report safety alerts, and build a stronger community together.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **Frontend**: React + Vite (wouter routing, TanStack Query, shadcn/ui, framer-motion)
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod, drizzle-zod
- **Auth**: Replit Auth (OpenID Connect with PKCE)
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)

## Architecture

- `artifacts/connecting-neighbors/` — React + Vite frontend (served at `/`)
- `artifacts/api-server/` — Express API server (served at `/api`)
- `lib/api-spec/openapi.yaml` — OpenAPI spec (single source of truth)
- `lib/api-client-react/` — Generated React Query hooks
- `lib/api-zod/` — Generated Zod validation schemas
- `lib/db/` — Drizzle ORM schema and DB connection
- `lib/replit-auth-web/` — Browser auth hook (`useAuth`)

## Key Features

- Community feed with categories (general, announcement, helpNeeded, lostFound, recommendation, safety)
- Local marketplace (buy, sell, free, rent items)
- Community events with RSVP
- Safety alerts with severity levels
- Resource sharing (rides, items, services, childcare)
- Member directory
- User profiles with apartment info
- Dashboard with community stats and activity feed

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)

## Database Tables

- `users` — Replit auth users
- `sessions` — Auth sessions
- `neighborhood_users` — App user profiles with apartment/bio info
- `posts` — Community feed posts
- `post_likes` — Post likes junction table
- `listings` — Marketplace listings
- `events` — Community events
- `event_rsvps` — Event RSVPs junction table
- `alerts` — Safety alerts
- `resources` — Shared resources

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.
