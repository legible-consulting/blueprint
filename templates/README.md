# Tiers

| Tier | Renders | Notes |
|---|---|---|
| `site` | a static site: `CLAUDE.md`, `README.md`, `.gitignore`, `.icm/intake/` (the ticket convention: the contract copy, `README.md` and `CONTEXT.md`, and the empty `_done/` folders), `.github/workflows/ci.yml` calling `.github`'s `check-client`, `.claude/` (the `block-local-checks`, `confirm-git-writes` and `guard-plaintext-secrets` guards, so cloud sessions are guarded too) | public by default |
| `app` | the same files as `site`, written from what the three adopted app repos share; `ci.yml` adds the `release` job, which calls `.github`'s `release.yml` (release-please) on each push to `main` | private by default; deploys from Vercel |
| `platform` | the app tier plus the heavier pipeline | private |
| `workspace` | a client's own ICM workspace for coaching | rendered into the client's account |

Each tier folder is a complete template root for copier (`_subdirectory` points here).
`platform` and `workspace` render only the answers file and a README yet; their contents are
Wave 1 (D2) work.

## Written once

`copier update` never overwrites a file that exists and that `_skip_if_exists` in `copier.yml`
names: every tier's `README.md` and its copy of the ticket contract (`.icm/intake/README.md`
and `.icm/intake/CONTEXT.md`, which the ICM pipeline syncs from icm-board), and the `app`
tier's `CLAUDE.md` and `.gitignore`. Every other rendered file is the blueprint's:
`copier update` merges a new tag into it three ways and marks a conflict inline. The tickets
themselves (`.icm/intake/<epic>/`, `triage/`) are never in the template, so an update never
touches them.

## One ticket convention

There is no `BUILD.md` in any tier. Every build keeps its tickets in `.icm/intake/`: a ticket
is a stub, its path is its identity (`<epic-slug>/<feature-slug>`, no numbers) and its folder
is its status (`git mv` into `_done/` is done; nothing is deleted). The two tiers seed the
same contract copy, taken from the adopted repos, and nothing else of `.icm/` yet.

## One set of guards

`templates/site/.claude/` and `templates/app/.claude/` hold the same `settings.json` and the
same three hooks, byte for byte. The `site` copies are the source: the house's `check.yml`
compares the house hooks against `templates/site/.claude/hooks/` only, and nothing compares
the `app` copies. Change a guard in `templates/site/`, then copy it to `templates/app/`.
