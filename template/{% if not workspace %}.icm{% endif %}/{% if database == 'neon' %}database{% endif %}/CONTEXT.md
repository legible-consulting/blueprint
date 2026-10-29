# Database — the Neon projects, a branch for each preview, and the migration at build

This build answered `neon` to `database` in `copier.yml`. This file is the database rule for
every environment. Three rules make it: isolation by Neon project, a Neon branch for each
preview, and a migration at build that holds a lock.

## Inputs

| Shape | Neon projects | Preview reads | UAT reads | Production reads | Production migrates |
|---|---|---|---|---|---|
| With UAT | `<slug>` and `uat-<slug>` | its own branch of `uat-<slug>` | the default branch of `uat-<slug>` | the default branch of `<slug>` | in `promote.yml`, on `promote.sh run` |
| Without UAT | `<slug>` | its own branch of `<slug>` | — | the default branch of `<slug>` | at the build of `main` |

- **Isolation is by Neon project.** With UAT, only Vercel Production and `promote.yml` reach
  `<slug>`. Each other deployment reads `uat-<slug>` (why: a separate project is the strongest
  wall between the client's production data and a preview · Jamie, 2026-10-28).
- **Neon makes each preview's database.** The Neon integration on Vercel cuts the branch
  `preview/<git branch>` from the default branch, with its data, when the first deployment of a
  git branch starts. It gives the branch's `DATABASE_URL` and `DATABASE_URL_UNPOOLED` to each
  deployment of that git branch, not to the Vercel project. It deletes the branch when the git
  branch is deleted. No script and no workflow of this build makes or deletes a branch (why: the
  integration makes the branch before the build, so no build runs without its database · Jamie,
  2026-10-28).
- **One pull request has one Neon branch.** The name comes from the git branch, so all the apps
  of a monorepo's pull request read one branch (why: a test with two apps · 2026-10-29).
- **No `DATABASE_URL` on Preview for all branches.** A preview without its branch fails its
  build, and never reads or writes the UAT database (why: a shared preview database mixed the
  test rows of each pull request into the client's UAT data · Jamie, 2026-10-28).
- Without UAT, a preview branch copies production's data. A build with personal data in
  production answers yes to `uat`.

## Process

**The migration rule.** `package.json` names `db:migrate` and `db:verify`. Its `vercel-build`
line calls the blueprint's script, and the line never changes (why: the rule lives in a file
that `copier update` changes, so a new tag reaches every build · Jamie, 2026-10-28):

```json
"vercel-build": "bash .icm/scripts/vercel-build.sh next build"
```

- `.icm/scripts/vercel-build.sh` runs `db:migrate`, then `db:verify`, then the build command.
  With UAT it skips the migration when `VERCEL_TARGET_ENV` is `production`, because
  production's build runs at the merge to `main`, before the sign-off. `promote.yml` migrates
  production. Without UAT, every build migrates, production too.
- Vercel sets `VERCEL_TARGET_ENV` at build, and no person sets it. Without it, the script stops.
- The script gives `db:migrate` and `db:verify` `DATABASE_URL_UNPOOLED` as `DATABASE_URL` when
  it has a value: a migration needs a direct connection.
- **`db:migrate` holds a Postgres advisory lock** for the whole run, and releases it at the
  end. Two builds can migrate one database at the same time: two apps of a monorepo on `uat`,
  or two pushes to one branch. The lock makes the second run wait, then find nothing to apply
  (why: the migration tool does not lock by itself · Jamie, 2026-10-28).
- **A monorepo calls the script from each app's `vercel.json`.** Vercel runs `turbo run build`
  there, not `vercel-build`. Each app that reads the database names `db:migrate` and
  `db:verify` in its own `package.json`, and its `vercel.json` has the line
  `"buildCommand": "bash ../../.icm/scripts/vercel-build.sh turbo run build"`. The script migrates
  before turbo starts, so `turbo.json` names no variable for the migration (why: turbo's strict
  mode removes `DATABASE_URL` from a task that `turbo.json` does not name, and a cache hit skips
  the task · 2026-10-28). A build that reads the database names both in its task's `env`. A
  package one level below the root calls `../.icm/scripts/`.
- A migration at build runs while the previous deployment still serves. So a migration must be
  forward-compatible with the code it replaces.

## Outputs

- A Neon branch `preview/<git branch>` for each git branch with a preview, while it exists.
- A migrated database for each deployment, before its build. Production with UAT: after the
  sign-off, in `promote.yml`.

## Setup, once

Each person act is a setup stub in `.icm/intake/setup/` (`.icm/intake/CONTEXT.md` § The setup stub):

1. `neon-projects`: the Neon project `<slug>`, and with UAT `uat-<slug>`.
2. `neon-vercel-integration`: the integration on each Vercel project of the build that reads
   the database, each one connected to the same Neon projects. Preview from `uat-<slug>` with
   UAT, or `<slug>` without, with a branch for each preview. Production from `<slug>`.
3. `uat-database` (with UAT): `DATABASE_URL` and `DATABASE_URL_UNPOOLED` of `uat-<slug>` on
   the `uat` environment of each UAT project.
4. `github-delete-head-branches`: GitHub deletes the head branch after a merge, so the
   integration deletes its Neon branch.

The session's own setup: `db:migrate` with the lock, `db:verify`, and the build lines above.

| Name | Holds | Where |
|---|---|---|
| `DATABASE_URL` | the pooled connection string of the deployment's database | Vercel: Production and `uat` by the setup, each preview deployment by the integration |
| `DATABASE_URL_UNPOOLED` | the direct connection string of the same database | as `DATABASE_URL` |
| `VERCEL_TARGET_ENV` | the deployment's environment, set by Vercel at build and at runtime | Vercel, a system variable |
