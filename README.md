# blueprint

Legible Consulting's method, public: one copier template that renders a client build from its
answers, the conventions every rendered repo follows, and the workshop kit. The questions are
the bank in `copier.yml`: the slug, the client's name, the language, then `monorepo`, `release`
and `uat`.

```bash
copier copy gh:legible-consulting/blueprint ~/Desktop/legible-consulting/projects/<slug>
copier update   # inside a rendered repo, after a new tag here
```

Tags are the versions `copier update` compares (PEP 440: `v0.1.0`, `v0.2.0`, …). Nothing
client-specific is ever committed here.

| Folder | Holds |
|---|---|
| `template/` | the one template root: the files a build renders. `{{ _copier_conf.answers_file }}.jinja` records the answers |
| `conventions/` | what a rendered repo must keep: `CLAUDE.md` shape, tickets, pull requests and gates, commits, writing, CI, guards, secrets, UAT |
| `workshop-kit/` | the one-day workshop (Marp) and course material |

`check.yml` renders three proof answer sets on each push (the defaults, every yes, and `release`
no), lints the rendered workflows, hooks and scripts, and checks that every functionality
question has a default and a help line.

## The template

Every render carries `CLAUDE.md`, `README.md`, `.gitignore`, `.copier-answers.yml`, the ticket
convention (`.icm/intake/` with `CONTEXT.md`, `README.md` and the empty `_done/` folders),
`.icm/scripts/new-run.sh` and `close-out.sh`, `.github/pull_request_template.md` (the gates at
the top), `.github/workflows/ci.yml` calling `.github`'s `check-client`, and `.claude/` (the
three guards and the settings that register them).

| Question | Yes renders or changes |
|---|---|
| `monorepo` | `.gitignore` gains the monorepo caches. `CLAUDE.md` gains an Apps and packages table and says previews, plural |
| `release` | `ci.yml` gains the `release` job: `.github`'s `release.yml` (release-please) on each push to `main`. `CLAUDE.md` says the release is Jamie's merge of the release pull request. No: production follows `main`, and the merge is the release |
| `uat` (asked when `release` is yes) | the UAT shape below |

### Written once

`copier update` never overwrites a file that exists and that `_skip_if_exists` in `copier.yml`
names: `README.md`, `.icm/intake/README.md` (the repo's own page about its backlog),
`CLAUDE.md`, `.gitignore`, and a UAT build's `.env.example`. Every other rendered file is the
blueprint's: `copier update` merges a new tag into it three ways and marks a conflict inline.
The tickets themselves (`.icm/intake/<epic>/`, `triage/`) are never in the template, so an
update never touches them.

### One ticket convention

The contract, `.icm/intake/CONTEXT.md`, is the blueprint's and stands alone: the stub, the
breakdown, the triage stub, the writing rules and the loop from stub to merge. There is no
`BUILD.md`.

### UAT

| File | Does |
|---|---|
| `.icm/uat/CONTEXT.md` | the whole UAT contract: the three environments, the database, the batch, the sign-off, the promotion, the rollback, the setup acts and the names |
| `.icm/scripts/promote.sh` | `status` reads the batch, the release pull request, `ci`, the UAT deployment, the staged production build, and prints the dispatch command when a release waits. `approve --by "<who>"` records the client's word on the release pull request |
| `.icm/scripts/uat-db.sh` | with one Neon project: `status`, `create`, `reset --yes`, `delete --yes`: the Neon branch `uat` (schema only, no rows) and its connection string on the Vercel custom environment. A build with a second Neon project for UAT does not use it |
| `.icm/scripts/rollback.sh` | names the previous production deployment and prints the rollback command. Runs nothing |
| `.icm/scripts/lib/vercel.sh`, `lib/neon.sh` | the two transports. A token never reaches a command line |
| `.github/workflows/promote.yml` | on Jamie's dispatch with a release tag: migrate production → promote the staged build → read production once. No push, merge or tag starts it |
| `.github/workflows/neon-cleanup.yml` | a pull request closes → its `preview/<branch>` Neon branch is deleted |
| `.env.example` | the names, with the environments each one reaches. Written once |

The shape in four sentences. Every merge to `main` deploys the Vercel custom environment `uat`
and builds a staged production deployment. The client tests the batch at the UAT address. Jamie
records the sign-off, merges the release pull request, and dispatches `promote.yml` with its tag.
That run migrates production and promotes the staged build. No means the pull request preview is
the UAT and production follows `main`.

### How a file renders only on yes

A file or folder named `{% if uat %}name{% endif %}` renders to an empty name on no, and copier
skips it. The content of such a file is copied as is unless its name ends in `.jinja`, so a
workflow's `${{ }}` expressions stay untouched.
