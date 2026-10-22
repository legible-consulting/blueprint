# Tiers

| Tier | Renders | Notes |
|---|---|---|
| `site` | a static site: `CLAUDE.md`, `README.md`, `.gitignore`, the ticket convention (`.icm/intake/` with `CONTEXT.md`, `README.md` and the empty `_done/` folders, and the two scripts in `.icm/scripts/`), `.github/pull_request_template.md` (the gates at the top), `.github/workflows/ci.yml` calling `.github`'s `check-client`, `.claude/` (the three guards and the settings that register them) | public by default |
| `app` | the same files as `site`. `ci.yml` adds the `release` job, which calls `.github`'s `release.yml` (release-please) on each push to `main` | private by default, deploys from Vercel |
| `platform` | the same files as `site` for a monorepo: `ci.yml` calls `check-client` with tier `platform` and ships no release job, because a platform keeps its own release workflow and names it in `CLAUDE.md`. `.gitignore` adds the monorepo caches | private |
| `workspace` | a client's own ICM workspace for coaching | rendered into the client's account, unwritten |

Each tier folder is a complete template root for copier (`_subdirectory` points here).

## Written once

`copier update` never overwrites a file that exists and that `_skip_if_exists` in `copier.yml`
names: every tier's `README.md` and `.icm/intake/README.md` (the repo's own page about its
backlog), and the `app` and `platform` tiers' `CLAUDE.md` and `.gitignore`. Every other
rendered file is the blueprint's: `copier update` merges a new tag
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
