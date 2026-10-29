# blueprint

Legible Consulting's method, public, in three parts: one copier template, the conventions every
rendered repo follows, and the workshop kit. The template renders a client build, or a client's
ICM workspace, from its answers. The questions are the bank in `copier.yml`: the slug, the client's name, the
language, `workspace`, then for a build `monorepo`, `release`, `uat` and `database`.

```bash
copier copy gh:legible-consulting/blueprint ~/Desktop/legible-consulting/projects/<slug>
copier update   # inside a rendered repo, after a new tag here
```

Tags are the versions `copier update` compares (PEP 440: `v0.1.0`, `v0.2.0`, …). Nothing
client-specific is ever committed here.

The blueprint is MIT licensed: see `LICENSE`.

| Folder | Holds |
|---|---|
| `template/` | the one template root: the files a build renders. `{{ _copier_conf.answers_file }}.jinja` records the answers |
| `conventions/` | what a rendered repo must keep: `CLAUDE.md` shape, tickets, pull requests and gates, commits, writing, CI, guards, secrets, UAT |
| `workshop-kit/` | the one-day workshop: the slides (Marp), the exercises and the walk test |

`check.yml` renders six proof answer sets on each push (the defaults, every yes with `neon`,
`release` no, a workspace, `neon` without UAT, and `mongodb` with UAT). It lints the rendered
workflows, hooks and scripts. In each build it runs the router's fixture test, the board's
fixture, a dry run of `new-run.sh` and the refusals of `merge.sh` with a fake `gh`. It proves `copier update` from an older tag to `HEAD`.
It checks that every functionality question has a default and a help line.

## The template

Every build carries these files, whatever its answers:

| File | Is |
|---|---|
| `CLAUDE.md`, `README.md`, `.gitignore` | the routing table and the rules, the build's own page, the ignore list. Written once |
| `.copier-answers.yml` | the answers and the blueprint tag |
| `.icm/environments.md` | where the build runs: one table of the environments, with the address, the Vercel project, the database and what moves each one. Rendered from the answers. The blueprint's, so `copier update` merges a new tag into it and a filled cell stays filled |
| `.icm/intake/` | the ticket convention: `CONTEXT.md` (the contract and the loop), `README.md`, the empty `_done/` folders |
| `.icm/lanes/<lane>/CONTEXT.md` | the four lanes for a one-off: `bug`, `tweak`, `chore`, `hotfix` |
| `.icm/scripts/` | `new-run.sh` (with `--ready` and `--dry-run`), `close-out.sh`, `checks.sh`, `merge.sh`, `release.sh`, and `lib/github.sh`. Each GitHub call is REST, through `gh api`, because a Claude Code cloud session gets HTTP 403 on GraphQL |
| `.github/pull_request_template.md` | the pull request body, the two gates at the top |
| `.github/workflows/ci.yml` | calls `.github`'s `check-client` |
| `.claude/settings.json` | the allow list for `merge.sh` and `release.sh` (build only), the deny list, and the registration of the hooks |
| `.claude/hooks/` | the three guards, the router `route-request.sh` and its test, the board `session-start.sh` |
| `.claude/skills/` | the three skills below |

| Question | Yes renders or changes |
|---|---|
| `workspace` | a client's ICM workspace instead of a build: see The workspace below. copier asks `monorepo`, `release`, `uat` and `database` only on no |
| `monorepo` | `.gitignore` gains the monorepo caches. `CLAUDE.md` gains an Apps and packages table and says previews, plural |
| `release` | `ci.yml` gains the `release` job: `.github`'s `release.yml` (release-please) on each push to `main`. `CLAUDE.md` says the release is Jamie's word `release`, and the session runs `release.sh`. No: production follows `main`, and the merge is the release |
| `uat` (asked when `release` is yes) | the UAT shape below |
| `database` (`none`, `neon`, `mongodb`, `other`) | `neon` renders the database shape below. Any other answer renders no database file, and `.copier-answers.yml` keeps the answer |

### Written once

`copier update` never overwrites a file that exists and that `_skip_if_exists` in `copier.yml`
names: `README.md`, `.icm/intake/README.md` (the repo's own page about its backlog),
`CLAUDE.md`, `.gitignore`, and a UAT build's `.env.example`. Every other rendered file is the
blueprint's: `copier update` merges a new tag into it three ways and marks a conflict inline.
The tickets themselves (`.icm/intake/<epic>/`, `triage/`) are never in the template, so an
update never touches them.

### One ticket convention

The contract, `.icm/intake/CONTEXT.md`, is the blueprint's and stands alone. It holds the stub,
the breakdown, the triage stub, the writing rules and the loop from stub to merge. There is no
`BUILD.md`.

### The skills

A build carries three skills in `.claude/skills/`. Claude Code loads each one from its
`SKILL.md`. A workspace carries none. The contract holds every shape. A skill adds no shape.

| Skill | Adds |
|---|---|
| `pr-conventions` | the git and GitHub mechanics: the branch, the commit, the CI read, the edit of a pull request body |
| `ticket-craft` | the judgement behind a stub, a cut, a triage stub and a dropped stub |
| `asd-ste100` | the writing reference for every stub, breakdown and pull request body |

`asd-ste100` is a copy of [danyuchn/asd-ste100-skill](https://github.com/danyuchn/asd-ste100-skill)
at commit `3944283c183eea13fe5bd902b572da3b4de8bf44`, the commit that `check.yml` pins. The
licence is MIT, and the copy keeps its `LICENSE`. The blueprint edits no file in the copy.

### UAT

| File | Does |
|---|---|
| `.icm/uat/CONTEXT.md` | the whole UAT contract: the three environments, the database, the batch, the sign-off, the promotion, the rollback, the setup acts and the names |
| `.icm/scripts/promote.sh` | `status` reads the batch, the release pull request, `ci`, the UAT deployment, the staged production build, and prints the dispatch command when a release waits. `approve --by "<who>"` records the client's word on the release pull request. `run --tag <tag>` dispatches `promote.yml`, on Jamie's word |
| `.icm/scripts/rollback.sh` | names the previous production deployment and prints the rollback command. Runs nothing |
| `.icm/scripts/lib/vercel.sh` | the Vercel transport of the UAT scripts and `promote.yml`. A token never reaches a command line |
| `.github/workflows/promote.yml` | dispatched by `promote.sh run` with a release tag: migrate production → promote the staged build → read production once. No push, merge or tag starts it |
| `.env.example` | the names, with the environments each one reaches. Written once. Also on `neon` |

The shape in four sentences. Every merge to `main` deploys the Vercel custom environment `uat`
and builds a staged production deployment. The client tests the batch at the UAT address. On
Jamie's word, the session records the sign-off, merges the release pull request with
`release.sh`, and runs `promote.sh run` with its tag. That run migrates production and promotes
the staged build. No means the pull request preview is
the UAT and production follows `main`.

### The database

A build that answered `neon` carries the database shape. Any other answer renders none of it.

| File | Does |
|---|---|
| `.icm/database/CONTEXT.md` | the database contract: the Neon projects, a branch for each preview, the migration at build, the setup acts and the names |
| `.icm/scripts/vercel-build.sh` | the `vercel-build` of `package.json`: migrate, verify, then build. With UAT, production only builds. `package.json` calls it with one line that never changes. In a monorepo, each app's `vercel.json` `buildCommand` calls it before `turbo run build` |

The shape in four sentences. Isolation is by Neon project: with UAT, only production reads
`<slug>`, and each other deployment reads `uat-<slug>`. The Neon integration makes a branch for
each preview, before its build, and deletes it with the git branch. Every build migrates its own
database, except production with UAT, which `promote.yml` migrates after the sign-off.
`db:migrate` holds a Postgres advisory lock, so two builds never migrate one database at once.

### Setup acts

A UAT or Neon build carries `.icm/intake/setup/`: one stub for each act that only a person can
do, written by copier from the answers. A new answer or a new tag adds its acts at the next
`copier update`. A stub that a person moved to `setup/_done/` is not written again.
`session-start.sh` prints the open acts at each session start.

### The workspace

A coaching client leaves with a workspace for their own job, rendered with `workspace` yes.
It has no code, no tickets and no releases.

| File | Is |
|---|---|
| `CLAUDE.md` | the map: what the folder holds, one routing row per stage, the rules. Written once |
| `01-collect/CONTEXT.md`, `02-draft/CONTEXT.md`, `03-deliver/CONTEXT.md` | the stage contracts: `status: stub`, `## Inputs`, `## Process`, `## Outputs` with lines in angle brackets that the first coaching hour fills. Written once |
| `02-draft/CONTEXT.md` § Gate | the example gate: a checkbox, the role of the person who ticks it, and the stage that waits |
| `.github/workflows/ci.yml` | `.github`'s `check-client` with `workspace: true`: every `CONTEXT.md` keeps the three sections |
| `README.md`, `.gitignore`, `.copier-answers.yml`, `.claude/` | as in a build |

No `.icm/`, no pull request template, no release job. The stage folders keep their names: a
renamed folder comes back on the next `copier update`. The job's own words go in the contract
title and the routing row. The walk test in `workshop-kit/walk-test.md` is the test the
workspace must pass.

### How a file renders only on yes

A file or folder named `{% if uat %}name{% endif %}` renders to an empty name on no, and copier
skips it. The build's own paths (`.icm/`, the pull request template) carry
`{% if not workspace %}` in the same way. Copier copies the content of such a file as is unless its name ends in `.jinja`, so a
workflow's `${{ }}` expressions stay untouched.
