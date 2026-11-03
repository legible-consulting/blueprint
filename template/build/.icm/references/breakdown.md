# The breakdown

The contract is `.icm/intake/CONTEXT.md`. This file holds one shape the contract names. Read it
when you write one, not when you build one.

`<epic-slug>/breakdown.md` is the epic's one review surface. Jamie reads it before a session
builds any stub. Edit it and re-cut the stubs to steer.

```md
# Breakdown: <epic title>

- epic-slug: <slug>
- story: <n>                   # when the epic comes from a user story
- source: <where the work came from: the proposal's scope, a call, a review, a user
  story: its number, its title, its author, its date and its link>

## What I understood

<Three to six sentences. A misread is caught here, before any cut.>

## Criteria → stubs

<Only when the epic comes from a user story. One row per acceptance criterion of the story,
in the story's order.>

| # | The story's criterion | Carried by |
|---|---|---|
| 1 | <the criterion, in the story's words> | `<feature-slug>` |
| 2 | <the criterion> | rule: README |
| 3 | <the criterion> | not built: <reason> |

## Build order

1. <feature-slug> — <one line> — depends-on: none
2. <feature-slug> — <one line> — depends-on: <feature-slug>

## Out of scope

- <What no stub covers this round.>
```

The build order is strict: sequences run `1..m` with no gap, every `depends-on` names a stub
sequenced earlier, and the order agrees with each stub's `sequence` line. The stubs that touch
shared files (the lockfile, the schema, the layouts) go first (why: every later stub merges
over them).
