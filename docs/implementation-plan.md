# Implementation Plan

## Product Goals

Build a mobile-first realtime social product around venue presence, QR entry, chat discovery, and safety-first controls.

## Architecture Principles

- Modular backend design (NestJS modules by domain)
- State-machine driven UX for critical flows
- Realtime-first event contracts
- Trust and safety as first-class system concerns
- Observability and analytics from day one

## Required Modules

### Backend (NestJS)

- `auth`
- `users`
- `venues`
- `discovery`
- `presence`
- `chat`
- `moderation`
- `analytics`
- `admin`

### Shared Backend Patterns

- Repository pattern per persistence aggregate
- Service layer abstractions for domain orchestration
- WebSocket gateway layer for realtime channels
- Centralized exception filters and validation pipes
- Event-driven components for async workflows

## Realtime Requirements

WebSocket updates must cover:

- active venue counts
- live presence changes
- typing indicators
- read receipts
- reveal request lifecycle
- panic exits
- moderation updates

Room segmentation:

- `venue:{id}`
- `chat:{id}`
- `admin:stream`

Horizontal scaling requirement:

- Socket.IO Redis adapter
- stateless API instances

## Safety and Anti-Abuse

Implement the following as dedicated services/policies:

- device fingerprinting hooks
- VPN/proxy risk checks
- suspicious velocity checks
- duplicate QR scan prevention
- impossible travel detection
- shadow restrictions
- spam scoring
- abuse reputation scoring

All moderation actions must be auditable.

## Analytics Baseline

Track events:

- qr_scanned
- venue_joined
- chat_started
- reveal_requested
- reveal_accepted
- panic_exit_triggered
- report_submitted
- session_duration
- venue_retention
- dau_wau_mau
- chat_conversion_funnel

## State Machines

Define explicit states and transitions for:

- venue presence lifecycle
- reveal request lifecycle
- websocket connection lifecycle
- onboarding completion
- moderation ticket lifecycle
- panic exit handling

Use optimistic UI updates where failure rollback is acceptable.

## Phase-by-Phase Build

### Phase 0 — Repository Bootstrap

- Setup monorepo structure (`apps/web`, `apps/api`, `packages/shared`)
- Setup TypeScript, linting, formatting, commit hooks
- Configure Docker Compose for Postgres + Redis
- Create CI skeleton (lint, test, build)

### Phase 1 — Product + Design

- Convert requirements into design system tokens
- Define app navigation and core user flows
- Build wireframes + high-fidelity prototypes

### Phase 2 — Frontend Core

- Next.js app shell
- Bottom tab navigation
- Venue map and venue detail screens
- Chat list and chat thread UI
- Notifications and profile
- Panic exit affordance

### Phase 3 — Backend Core

- NestJS module scaffolds
- Prisma schema + migrations
- Auth + session strategy
- WebSocket gateway contracts
- QR venue check-in flow

### Phase 4 — Realtime + Moderation

- Presence service and room fanout
- Chat delivery states (sent/delivered/read)
- Moderation dashboard APIs
- Audit logging and admin stream

### Phase 5 — Hardening

- Abuse detection pipeline
- Queues and retries
- SLOs + observability dashboards
- Load testing and websocket scaling tests

## Suggested Initial Task Branches

- `feat/bootstrap-monorepo`
- `feat/design-system-foundation`
- `feat/frontend-navigation-shell`
- `feat/backend-module-scaffold`
- `feat/realtime-gateway-contracts`
- `feat/moderation-audit-log`
