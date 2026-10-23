# Tiers

| Tier | Renders | Notes |
|---|---|---|
| `site` | a static site: `CLAUDE.md`, `README.md`, `.gitignore`, the ticket convention (`.icm/intake/` with `CONTEXT.md`, `README.md` and the empty `_done/` folders, and the two scripts in `.icm/scripts/`), `.github/pull_request_template.md` (the gates at the top), `.github/workflows/ci.yml` calling `.github`'s `check-client`, `.claude/` (the three guards and the settings that register them) | public by default |
| `app` | the same files as `site`. `ci.yml` adds the `release` job, which calls `.github`'s `release.yml` (release-please) on each push to `main`. With `uat` answered yes: `.icm/uat/CONTEXT.md`, `.icm/scripts/promote.sh`, `uat-db.sh`, `rollback.sh` and `lib/`, `.github/workflows/promote.yml` and `neon-cleanup.yml`, `.env.example` (see UAT below) | private by default, deploys from Vercel |
| `platform` | the same files as `site` for a monorepo: `ci.yml` calls `check-client` with tier `platform` and ships no release job, because a platform keeps its own release workflow and names it in `CLAUDE.md`. `.gitignore` adds the monorepo caches | private |
| `workspace` | a client's own ICM workspace for coaching | rendered into the client's account, unwritten |

Each tier folder is a complete template root for copier (`_subdirectory` points here).

## Written once

`copier update` never overwrites a file that exists and that `_skip_if_exists` in `copier.yml`
names: every tier's `README.md` and `.icm/intake/README.md` (the repo's own page about its
backlog), the `app` and `platform` tiers' `CLAUDE.md` and `.gitignore`, and a UAT build's
`.env.example`. Every other rendered file is the blueprint's: `copier update` merges a new tag
into it three ways and marks a conflict inline. The tickets themselves (`.icm/intake/<epic>/`,
`triage/`) are never in the template, so an update never touches them.

## One ticket convention

Every tier keeps its tickets in `.icm/intake/`. The contract, `.icm/intake/CONTEXT.md`, is the
blueprint's and stands alone: the stub, the breakdown, the triage stub, the writing rules and
the loop from stub to merge. There is no `BUILD.md` in any tier.

## One set of shared files

The `site` tier is the source of every file the tiers share: the ticket contract, the two
scripts, the pull request template, `.claude/settings.json` and the three hooks. The `app` and
`platform` copies are byte-identical, and the blueprint's `check.yml` fails when one drifts.
Change a shared file in `templates/site/`, then copy it to the other tiers.

## UAT

The `uat` question is asked for the `app` tier only. Yes renders, beside the shared files:

| File | Does |
|---|---|
| `.icm/uat/CONTEXT.md` | the whole UAT contract: the three environments, the database, the batch, the sign-off, the promotion, the rollback, the setup acts and the names |
| `.icm/scripts/promote.sh` | `status` reads the batch, the release pull request, `ci`, the UAT deployment and the staged production build. `approve --by "<who>"` records the client's word on the release pull request |
| `.icm/scripts/uat-db.sh` | `status`, `create`, `reset --yes`, `delete --yes`: the Neon branch `uat` (schema only, no rows) and its connection string on the Vercel custom environment |
| `.icm/scripts/rollback.sh` | names the previous production deployment and prints the rollback command. Runs nothing |
| `.icm/scripts/lib/vercel.sh`, `lib/neon.sh` | the two transports. A token never reaches a command line |
| `.github/workflows/promote.yml` | after `ci` on `main`: a `v*` tag at the head → migrate production → promote the staged build → read production once |
| `.github/workflows/neon-cleanup.yml` | a pull request closes → its `preview/<branch>` Neon branch is deleted |
| `.env.example` | the names, with the environments each one reaches. Written once |

The shape in four sentences. Every merge to `main` deploys the Vercel custom environment `uat`
and builds a staged production deployment. The client tests the batch at the UAT address. Jamie
records the sign-off and merges the release pull request. That merge migrates production and
promotes the staged build. No means the pull request preview is the UAT and production follows
`main`.

The UAT files have no copy in another tier. A `platform` names its own release model, so it
names its own UAT too.
