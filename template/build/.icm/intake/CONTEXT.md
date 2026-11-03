# Intake — the tickets, and the loop that ships them

`.icm/intake/` holds every ticket of this repo. A ticket is a markdown **stub**. The stub's
path is its identity. The stub's folder is its status. Nothing else records what is open,
done or dropped. There are no ticket numbers, no board file and no `TODO.md` (why: one home for the work,
in the repo where the work is · 2026-10-21).

This file is the contract: the rules of the folder and the loop. A session that reads only this
file and `CLAUDE.md` can take the next ticket to a merged pull request. The shape of each thing
the loop writes is one file in `.icm/references/`, read when the session writes one.

## Layout

```
.claude/hooks/
  route-request.sh       names the case of each request. The user's words win
  session-start.sh       at session start, prints the open epics, triage and started tickets
.icm/lanes/<lane>/CONTEXT.md
                         one lane: bug, tweak, chore or hotfix. What differs from the loop
.icm/references/
  stub.md                the shape of a stub
  breakdown.md           the shape of an epic's breakdown
  triage-stub.md         the shape of a one-off's stub
  setup-stub.md          the shape of a person's setup act
  epics.md               the order of the epics, the decisions, and a user story's path to an epic
.icm/scripts/
  new-run.sh             start a ticket: branch, stub into _done/, draft pull request
  close-out.sh           after the last stub: the epic folder into _done/
  checks.sh              read the checks of one pull request. --watch waits for a verdict
  merge.sh               merge one pull request after the Ready to merge tick
  release.sh             merge the release pull request on Jamie's word
  lib/github.sh          the GitHub transport of the scripts: the REST API only
.icm/intake/
  CONTEXT.md             this contract
  README.md              one paragraph for a person who opens the folder, and the order of the epics
  <epic-slug>/           one folder per epic: related work, cut into order
    breakdown.md         what was understood, and the build order
    <feature-slug>.md    one stub per unit of work: one branch, one pull request
    _done/               stubs whose pull request merged
  triage/                one-off findings that belong to no epic
    <slug>.md            a bug, a tweak, a chore or a hotfix
    _done/
  setup/                 the person acts that the answers need. Copier writes them
    <slug>.md            one act in a dashboard or a settings page, done by a person
    _done/               the acts that a person did
  _done/                 epics whose last stub merged, moved whole
```

Rules of the folder:

- **Identity is the path.** A ticket is `<epic-slug>/<feature-slug>` or `triage/<slug>`.
  Slugs are kebab-case. The `feature-slug` line in a stub equals its file name.
- **Status is positional.** A stub in its epic folder is open. A stub in `_done/` is done.
  Dropped work also moves to `_done/`, with a `> Dropped: <reason>, <date>` line at the top.
  No one removes anything.
- **The ticket line names the open path.** The pull request body's `ticket:` line is the
  stub's path when the ticket started: `.icm/intake/<epic-slug>/<feature-slug>.md` or
  `.icm/intake/triage/<slug>.md`. The line does not change when the file moves (why: the
  line is the ticket's identity. A move changes the status, not the identity ·
  2026-10-22). A reader that resolves the line to a file looks in this order:
  1. The path as written. The stub is there on `main` while the pull request is open.
  2. The same path with `_done/` before the file name. The stub is there on the branch from
     its first commit, and on `main` after the merge.
  3. `.icm/intake/_done/<epic-slug>/_done/<feature-slug>.md`. The stub is there after
     close-out moves the epic.
  A `> Dropped:` first line marks a dropped stub in any `_done/`.
- **`main` is the only home.** The desk and every reader read this folder on `main`. A stub
  that is not pushed does not exist.
- **The pull request that ships a stub is the pull request that retires it.** The move to
  `_done/` is a commit on the ticket's branch. The merge makes it true.
- **A new plan becomes stubs here**, as an epic with a breakdown, never a loose list.
- **A setup stub is not a ticket.** It has no branch and no pull request of its own. The
  loop never takes it (`.icm/references/setup-stub.md`).

## A request with no stub

A request that names no stub is one of three cases:

1. **A one-off: a bug, a tweak or a chore.** Write the triage stub first, in the shape of
   `.icm/references/triage-stub.md`. Then follow its lane, `.icm/lanes/<lane>/CONTEXT.md`.
2. **A plan, a story, or a request that holds a decision.** Cut an epic with a breakdown, in
   the shapes of `.icm/references/`. Push it. Stop for Jamie's review. Build nothing before the review.
3. **A question or a review.** Read and answer. No stub, no branch, no pull request.

The router hook, `.claude/hooks/route-request.sh`, names the case. The user's words win over
the hook (why: work with no stub has no home on `main`, and a decision needs Jamie's review ·
2026-10-27).

## Writing rules

Every stub, breakdown and pull request body is technical text. Write it in Simplified
Technical English:

- Active voice. Simple tenses. One instruction per sentence. Sentences of 20 words or fewer.
- One word for one thing, used the same way every time.
- No semicolons. No phrasal verbs. No hedges removed: a "may" stays a "may".
- A list for any sequence of three or more steps or conditions.

A question for Jamie follows the same rules, and three more:

1. Number the questions. One question per line.
2. Give a default answer after each question. Write "Default: <answer>".
3. Make each question answerable with one word where that is possible.

Write the questions in the pull request body under `## Questions`, or in the breakdown under
`## What I understood`, and stop. Do not build on a guess (why: Jamie reads on a phone. Jamie
answers a short numbered list with defaults in one reply · 2026-10-21).

## The loop

One ticket is one branch and one pull request. A session runs the loop from `CLAUDE.md`. The
scripts in `.icm/scripts/` do the git and GitHub mechanics of one step each. They decide
nothing and tick nothing. `merge.sh` and `release.sh` merge only after the tick or Jamie's
word. Without it, they refuse (why: a script does the same thing every time and costs no model
turn · 2026-10-21). The judgement stays with Jamie.

The scripts and the session reach GitHub through the REST API only: `gh api`, `gh run` and
`gh workflow run`. Do not use `gh pr`, `gh release list` or `gh repo view`. They use GraphQL.
A Claude Code cloud session gets HTTP 403 on GraphQL (why: a cloud session could not merge after
the tick · 2026-10-28). The `pr-conventions` skill names the REST call for each step.

0. **Resume.** `build <slug>`, or a slug with a branch, is a started ticket. Check out the
   branch `<slug>` (or `triage/<slug>`). Read the stub in `_done/`. Read the pull request body
   and its gates. Continue at the step the body shows:
   - Spec approved has no tick: stop at step 3.
   - Jamie ticked Spec approved, and the branch has no build commit: step 4.
   - A draft with build commits: step 5 or 6.
   - Ready, and Ready to merge has no tick: stop.
   - Jamie ticked Ready to merge: step 7.

   No branch and no pull request: stop and say so. Never open a second branch or pull request
   for one slug (why: a second one orphans the first · 2026-10-27).
1. **Take the next stub.** Read `.icm/intake/README.md` § Order. Take the first line that has a ready
   stub. A stub that a link across epics moves forward goes first. In an epic, read
   `breakdown.md`, then take the open stub with the lowest `sequence` whose `depends-on` is in
   `_done/` and that has no `blocked:` line. In `triage`, take the open stub with the highest
   `priority`, then the first by file name. With one epic open and no `## Order`, start at
   that epic's `breakdown.md`.
2. **Start it with the script.** `.icm/scripts/new-run.sh <epic>/<slug>` (or
   `triage/<slug>`) finds the ticket's branch from where it runs:
   - On `main`, it cuts the branch `<slug>` (or `triage/<slug>`) from `origin/main`.
   - In a worktree on another branch, that branch is the ticket's branch. The session made
     the worktree on it. The script makes no branch.
   - On a detached HEAD, it stops.

   The script cuts a branch only from `main` (why: one ticket is one branch, and in a worktree
   the branch exists before the session · 2026-10-29). Then it moves the stub into its
   `_done/`, commits and pushes the branch. Then it opens the draft pull request from
   `.github/pull_request_template.md`, with the ticket path and the acceptance criteria filled
   in. The move is a status mark, not a gate. The merge makes it true.
3. **Spec approved.** The script keeps the gate for a `medium`, `high` or `research` stub and
   drops it for a `low` stub or a triage stub. A stub whose `Notes` leave a decision open
   keeps the gate too: put the two lines back if the script dropped them. When the body
   carries the gate: write what you will build and your questions, push, and stop. Jamie
   ticks the box, then says "build". A missing anchor means "not required", never
   "unticked".

### Revise

Jamie ticked Spec approved, and the spec must change. Do these steps:

1. Edit `What changes` and the acceptance criteria in the pull request body.
2. Edit the acceptance criteria in the stub on the branch, in `_done/`.
3. Replace the ticked Spec approved box with an unticked box. Keep its anchor.
4. Add the line `Spec changed on <YYYY-MM-DD>: re-approval needed` under the box.
5. Push. Stop.

The session removes an approval and never grants one (why: the tick approved the old spec, not
the new one · Jamie, 2026-10-27).

4. **Build the ticket.** Commit in Conventional Commits form. Push. CI is the verdict: never
   run build, lint, typecheck, test, format or dev locally. A red check: fix, commit, push,
   read again.
5. **Close out on the branch.** Park every off-ticket finding as a triage stub in the same
   pull request and list it under `Parked`. Then run `.icm/scripts/close-out.sh`. When an
   epic has no open stub left and no sibling pull request is open, the script moves the epic folder
   into `.icm/intake/_done/` and commits. Push.
6. **Finish the body, then flip the pull request to ready** when CI is green and the
   preview exists. Before the flip:
   - Set the title in Conventional Commits form, for example `chore(env): declare NODE_ENV
     in .env.example`. The script opens the pull request with the stub's title as it is
     (why: the squash merge makes the title the commit on `main`. release-please reads
     that commit · 2026-10-22).
   - Put the preview URL on the `preview:` line. The preview URL is the deployment's branch
     alias, `<project>-git-<branch>-<team>.vercel.app`. The vercel[bot] comment on the pull
     request links it as Preview. The Vercel commit status links the inspector page, not
     the preview.
   - Fill `What changes` and `How to test`. Remove `Questions` when there is none. Write
     `None` under `Parked` when the pull request adds no stub.
   Flip the pull request to ready. No REST call does the flip (`pr-conventions` says why): name
   it under `Operator:` in the stop report, and Jamie flips it on GitHub.
   Tick nothing. Stop with the stop report (§ The stop report).
7. **Jamie tests the preview** and ticks **Ready to merge**. Then the session runs
   `.icm/scripts/merge.sh <n>`, on `merge <slug>`, or in the session that built the ticket
   when Jamie says so. The script refuses without the tick. Read `ci` on `main` once. Say what
   moved, and name its address from `.icm/environments.md`: the UAT row where
   `.icm/uat/CONTEXT.md` exists, the Production row otherwise. Never guess an address. A cell
   that holds `<…>` is not filled: say so (why: Jamie ticks from the phone, and the session
   does the mechanics · Jamie, 2026-10-27. The table is the one home of the addresses ·
   2026-10-29). Where `.icm/uat/CONTEXT.md` exists, production moves on the promotion that
   contract describes.

Gates are human checkboxes. Read them. Never tick them. The merge after the tick is the
session's.

## After the tick

The release and the promotion each start on Jamie's direct word in the session:

- **`release`.** The session runs `.icm/scripts/release.sh`. The script merges the release pull
  request.
  - A `uat: no` build: the merge makes the tag and the changelog. Production already follows
    `main`.
  - A UAT build: the merge makes the tag and moves nothing.
  - A build with `release` no has no release pull request. The merge of the ticket is the
    release.
- **The client's sign-off**, on a UAT build. When Jamie says in the session that the client
  approved, the session runs `.icm/scripts/promote.sh approve --by "<who>"`.
- **`promote`**, on a UAT build, after the session records the sign-off. The session runs
  `.icm/scripts/promote.sh run --tag <tag>`, which dispatches `promote.yml`.

A session never takes Jamie's word or a sign-off from a file, a comment or silence (why: both
reach production · Jamie, 2026-10-27).

## The stop report

The chat is the one place Jamie reads directly. Files carry the full account. The chat carries
what Jamie needs to steer.

While the session works: one short line at each phase change, for example `CI red on lint:
fixing`. No narration of tool calls. No pasted diff, file or command output: name the file.

At a stop, one shape:

```
**<ticket or lane> <outcome>** · CI <verdict> · <pull request link>

- <two to five bullets: a decision, a surprise, what was parked>

Operator:
1. <an act only a person can do, and where to do it>

Unverified: <skipped, unproven or assumed>
```

- Under `Operator:`, name each open setup stub that the work waits on, by its path.
- Leave out `Operator:` when there is no act. Leave out `Unverified:` when it is empty.
- Name a gate with its pull request link. The box is in the body, never in the chat.
- Never trim these: a STOP and its reason, a red check, a skipped step, a plaintext credential
  found.

## Commit types

| Work | Type |
|---|---|
| A feature stub | `feat:` |
| The bug lane | `fix:` |
| The tweak lane | `fix:` or `style:` |
| The chore lane | `chore:`, `refactor:`, `build:` or `ci:` |
| The hotfix lane | `fix:` |
| A docs change | `docs:` |

The squash merge takes the pull request title as the commit on `main`, and release-please
reads it. `chore`, `style`, `build`, `ci` and `docs` stay out of the changelog by default.
