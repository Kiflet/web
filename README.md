# Kiflet web

**The browser side of Kiflet**: shipment tracking and proof of delivery for
Ethiopian trucking companies. This repository will hold the Next.js app
for the company dashboard, the operator's pages and the public pages
(tracking, delivery confirmation, sign-in and sign-up).

Kiflet is three repositories:

| Repository | What |
|---|---|
| [Kiflet/backend](https://github.com/Kiflet/backend) | The Go backend, its APIs, workers and infrastructure. Today it also renders the dashboard this repository will replace. |
| **Kiflet/web** (this one) | The Next.js web app |
| [Kiflet/mobile](https://github.com/Kiflet/mobile) | The driver app (React Native with Expo) |

## Status

Planning. There is no app code yet: the pages are still served by
Kiflet/backend's Go app, and move here one at a time.

- [`docs/architecture.md`](docs/architecture.md): what this app is built
  from and how it works.
- [`docs/migration.md`](docs/migration.md): the plan, wave by wave, with
  every page and the API it needs.
- The whole system: [Kiflet/backend `docs/architecture.md`](https://github.com/Kiflet/backend/blob/main/docs/architecture.md)
  and [`docs/migration.md`](https://github.com/Kiflet/backend/blob/main/docs/migration.md).

## Running it

Not yet. Step 1 of `docs/migration.md` adds the app, and this section
with it: `pnpm install`, a backend from Kiflet/backend (`make deps seed
run`), then `pnpm dev`.
