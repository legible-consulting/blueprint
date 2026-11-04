# The epics

The contract is `.icm/intake/CONTEXT.md`. This file holds the rules of the epics: their order,
the decisions that bind them, and the path from a user story to one epic. Read it when you cut
or order an epic, not when you build a stub.

## The order of the epics

The build order says which stub of an epic goes first. It does not say which epic goes first.
When two or more epics are open, `.icm/intake/README.md` holds that order under `## Order`. A session
never sets the order on a guess (why: epics cut at the same time compete for the same weeks.
The order is Jamie's call · 2026-10-25).

```md
## Order

Set by Jamie on <YYYY-MM-DD>.

1. triage
2. <epic-slug>
3. <epic-slug>
```

- **One line per open epic**, and one line for `triage` while it holds an open stub. The
  pull request whose close-out moves an epic into `_done/` also removes the epic's line.
- **Classify, then ask.** A session that cuts an epic while another epic is open asks for the
  order. A session that cuts two or more epics at once also asks. First it classifies every
  open epic and `triage` in one table, one row each:

  | Column | What it says |
  |---|---|
  | Open | The count of open stubs. |
  | P0 | The count of open `P0` stubs. |
  | Serves | The deadline, the deal, the milestone, or the break a user sees today. |
  | Links | Each `depends-on` or `blocked:` line that names a stub of another epic, in both directions. |
  | Files | The shared files the epic touches: the schema, the lockfile, the layouts, a route. |

  Then it asks one question, the order, with a default from the rules below. It writes
  Jamie's answer under `## Order` with the date, and stops (why: the table shows the
  conflicts, and Jamie decides in one reply · 2026-10-25).
- **The default order**, for the question's default only:
  1. `triage` first (why: Jamie clears the small chores before an epic starts · 2026-10-25).
  2. Two epics that touch the same files run one after the other. The epic that adds a route,
     a card or a column goes first. The epic that restyles them goes after it (why: a restyle
     before the structure changes costs a second restyle · 2026-10-25).
  3. Then the epic that fixes a break a user sees today. Then the epic with the earliest
     deadline. Then the epic with more `P0` stubs.
- **A link across epics moves one stub, not its epic.** An epic can wait on one stub of an
  epic later in the order. Then that one stub runs before the waiting epic. The rest of its
  epic keeps its place (why: one stub lifts the block. A move of the whole epic overrides
  Jamie's order · 2026-10-25).
- **A new epic gets a place.** A session that cuts an epic while `## Order` exists asks where
  the new line goes, with the table, and writes the answer.

## Decisions

A rule that binds every epic of this repo lives in `.icm/intake/README.md`, under
`## Decisions`. A rule of one epic stays in its `breakdown.md`. A rule of one ticket stays in
its stub.

```md
## Decisions

- <the rule, one sentence> (why: <the reason> · <who>, <YYYY-MM-DD>).
```

- **One line per rule.** No ID, no number. A changed rule is edited in place. Git keeps the
  old line (why: the history of a rule is the history of its line · Jamie, 2026-10-30).
- **The session that writes the rule writes the line, on Jamie's word.** A session never adds
  a line on a guess.
- **Give each rule its why**, in the file's own style: `(why: <the reason> · <who>,
  <YYYY-MM-DD>)`.

## A user story

A client's document that asks for work, a user story most often, follows one path from the
client's words to the stubs:

- **The story is the client's.** It lives in the client's Drive folder. It is never committed
  to the repo (why: the repo holds the work, the client holds their words, and a copy drifts
  · 2026-10-23).
- **One story becomes one epic.** The breakdown's `source:` line names the story: its number,
  its title in the client's language, its author, its date and its link. A `story:` line
  after `epic-slug:` carries the number (why: the client's list and the backlog read the
  same. A reader goes from a stub to the story in one step · 2026-10-23).
- **`## What I understood` restates the story** in the session's words. Then it names what
  exists in the repo that the story replaces or reuses. Then it lists the questions, numbered,
  each with a default, under `### Questions for <the client>` and `### Questions for Jamie`
  (why: the answers catch a misread before any cut. The client answers in one reply ·
  2026-10-23).
- **A table `## Criteria → stubs` lists every acceptance criterion of the story**, once, in
  the story's order. Each row names the stub that carries it, or `rule: README` for a rule that binds the
  whole product, or `not built: <reason>`. Nothing the client wrote is lost silently (why: the
  client checks their own list against the table in one read · 2026-10-23).
- **Every stub of the epic carries `- story: <n>`** after `- epic:`. With no story, the line is
  absent (why: the pull request, the stub and the story stay linked without a
  ticket number · 2026-10-23).
- **A story that only states rules for the whole product** becomes a line in
  `.icm/intake/README.md` § Decisions, not an epic. The breakdowns name the decisions they rest
  on (why: a rule that binds every epic has one home. An epic for it would never close ·
  2026-10-23).
- **`.icm/intake/README.md` lists the stories in order** with their epic slug and state. The client's
  list and the backlog then read the same (why: the client asks "where is my story 12?" and the
  answer is one row · 2026-10-23).
