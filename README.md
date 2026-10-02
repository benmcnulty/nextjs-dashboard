# Next.js App Router Course dashboard

A historical learning implementation based on the
[Next.js App Router course](https://nextjs.org/learn). The checkout includes
dashboard/customer/invoice routes, server data access and mutations, form
validation and credential authentication. It is course-derived work, not an
original invoicing product or a verified production service.

## Source map

- [`app/dashboard`](app/dashboard) contains dashboard and invoice pages.
- [`app/lib/data.ts`](app/lib/data.ts) reads PostgreSQL;
  [`app/lib/actions.ts`](app/lib/actions.ts) implements mutations.
- [`auth.ts`](auth.ts), [`auth.config.ts`](auth.config.ts) and
  [`middleware.ts`](middleware.ts) implement the course authentication flow.
- [`scripts/seed.js`](scripts/seed.js) creates/populates course sample tables.

## Local setup

The committed stack is Next.js 14, React 18, NextAuth 5 beta and `@vercel/postgres`.
The original `.nvmrc` specifies Node 18, and `package.json` declares Node >=18.
That records the historical setup; this review did not certify the lockfile,
native bcrypt installation or app against a current supported runtime.

```sh
npm ci
npm run dev
```

Open `http://localhost:3000`. Dashboard/login journeys require a compatible
PostgreSQL connection and NextAuth configuration; installing packages alone does
not provide the database. Configure an existing disposable development database
and server-only `POSTGRES_URL` and `AUTH_SECRET` values locally, following the
[upstream environment reference](https://github.com/vercel/next-learn/blob/main/dashboard/starter-example/.env.example).
That upstream reference evolves separately from this old checkout. Keep actual
connection strings and secrets outside tracked files; no hosted service or new
account is required by this documentation change.

Next.js loads local environment files for the application. The seed command uses
`dotenv/config`, which defaults to `.env`; a different file can be selected with
`DOTENV_CONFIG_PATH`. Review the seed script and target database before using
`npm run seed`: it writes users, customers, invoices and revenue. It was not run
against any database in this review. Course fixture credentials are demonstration
data and must not become production login credentials.

## Verification and provenance

`npm run lint` runs Next.js lint; `npm run build` builds the application and
`npm start` serves a completed build. No automated test script or CI workflow is
committed. Database/authentication, build and browser behavior remain unverified
in this documentation-only review.

Preserve the Next.js/Vercel course attribution and bundled sample assets. No
standalone source license is committed in this checkout; do not infer original
authorship or a new redistribution grant from the repository being public.
