# Branching Workflow

This project should be built using **small, testable branches**. Do not develop directly on `main`.

## Branch Model

- `main`: production-ready history only
- `work`: integration branch for validated features
- task branches: one branch per functionality

Examples:

- `feat/frontend-navigation-shell`
- `feat/qr-venue-checkin`
- `feat/chat-read-receipts`
- `fix/presence-race-condition`

## Branch Lifecycle

1. Sync base branch:
   - `git checkout work`
   - `git pull origin work`
2. Create task branch:
   - `git checkout -b feat/<task-name>`
3. Build only one coherent functionality.
4. Run local checks (lint/tests/build for touched packages).
5. Commit with clear message.
6. Push branch:
   - `git push -u origin feat/<task-name>`
7. Open PR into `work` with:
   - scope
   - testing evidence
   - rollout notes
8. After review and passing checks, squash merge into `work`.
9. Periodically merge `work` into `main` for stable releases.

## Merge Gate Checklist

Before merging any task branch:

- All tests for touched modules pass
- Lint passes
- No secrets in commits
- Database migrations reviewed
- Realtime contracts backward compatible
- Moderation-impacting changes include audit logging

## Commit Message Convention

- `feat: ...`
- `fix: ...`
- `chore: ...`
- `docs: ...`
- `refactor: ...`

Example:

- `feat(chat): add read-receipt event handling`

## PR Template (Recommended)

- What changed?
- Why now?
- How was it tested?
- Any migration or rollout risk?
- Screenshots / payload examples (if UI or API contract changed)
