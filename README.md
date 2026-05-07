# Meetup Realtime Social App

This repository contains the implementation plan and starter architecture for a mobile-first, realtime, venue-based social product with strong trust & safety requirements.

## Core Stack

- Frontend: Next.js 15 (App Router, TypeScript)
- Backend: NestJS (modular architecture + WebSocket gateways)
- Database: PostgreSQL + Prisma
- Realtime: Socket.IO + Redis adapter
- Cache / Queues: Redis
- Storage: Cloudflare R2
- Monitoring: Sentry + PostHog

## Delivery Phases

1. Product + Design foundation
2. Frontend scaffolding and UX flows
3. Backend modules and realtime infrastructure
4. Production hardening (abuse prevention, analytics, observability, CI/CD)

Detailed implementation guidance is in [`docs/implementation-plan.md`](docs/implementation-plan.md).

## Git Workflow

Follow the branch workflow in [`docs/branching-workflow.md`](docs/branching-workflow.md):

- Create one branch per focused task.
- Open PRs to merge task branches into `work` (or `main` after release).
- Run checks before merge.
- Squash merge cleanly.

## Next Step

Start with **Phase 0: Repository bootstrap** from the implementation plan and create the first feature branch.
