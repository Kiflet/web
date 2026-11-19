# AGENTS.md

## Project

Kiflet web: the Next.js app for Kiflet, offline-first shipment tracking and
proof of delivery for Ethiopian trucking companies. It serves the company
dashboard (`/app`), the operator's pages (`/platform`) and the public pages
(tracking, confirmation, sign-in, sign-up).

- `docs/architecture.md`: how this app is built
- `docs/migration.md`: the plan for moving each page here from the Go app
- `CHANGELOG.md`: what changed in each release
- The rest of the system is in [Kiflet/backend](https://github.com/Kiflet/backend):
  its `docs/architecture.md` (the whole platform), `docs/migration.md` (all
  phases), `docs/E2E_TEST_GUIDE.md` (every flow, the parity checklist) and
  `docs/functional_requirements.md` (FR numbers referenced in code).

## State

No app code yet. Until a page has moved here (`docs/migration.md`, the
page inventory), the Go app in Kiflet/backend is what users see, and it is
the reference for how the page must behave.

## Rules

- **No business rules here.** Roles, statuses and their transitions, plan
  limits and alert conditions live in the backend. Show the buttons the
  API's `actions` allow; never work them out in TypeScript.
- **The API contract is `@kiflet/api`**, generated from Kiflet/backend's
  `api/openapi/web.yaml`. Don't hand-write types for API data. A missing
  field is a change in the backend first.
- **Server components by default;** client components only for the map,
  live updates, interactive tables, dialogs and menus.
- **Same origin.** The browser calls `/api/*` and `/ws` on this app's host;
  Caddy routes them to the backend. The session is the backend's
  `HttpOnly` cookie; never put a token in JavaScript.
- **CSP with nonces,** no inline scripts without one, no
  `dangerouslySetInnerHTML`.
- **What a customer reads is in English and Amharic** (`messages/en.json`,
  `messages/am.json`, same keys; a test checks). The dashboard is English
  until the Amharic has been reviewed (the backend's ROADMAP, W1).
- **The look is Desk (light) and Night (dark):** tokens in
  `app/globals.css`, copied from the backend's `static/app.css`; lucide
  icons; Geist fonts, self-hosted.
- **Metrics and traces** never carry a company, user or shipment ID as a
  label.
- Commits and pull requests carry no AI co-author or "Generated with"
  lines.
- Every change gets a line in `CHANGELOG.md`.
