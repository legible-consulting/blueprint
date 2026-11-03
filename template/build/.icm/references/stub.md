# The stub

The contract is `.icm/intake/CONTEXT.md`. This file holds one shape the contract names. Read it
when you write one, not when you build one.

```md
# Stub: <title, one line, what the user can do after this ships>

- feature-slug: <kebab, equal to the file name>
- epic: <epic-slug>
- story: <n>                   # when the epic comes from a user story
- sequence: <n> of <m>
- depends-on: <feature-slug, or none>
- complexity: low | medium | high | research
- priority: P0 | P1 | P2
- blocked: <reason>            # optional. Remove the line when the block lifts.

## Problem

<What is wrong or missing today. One to three sentences.>

## Proposed change

<What the build does, in the user's words. Not how.>

## Acceptance criteria

- [ ] <One observable result per line. The pull request copies these lines.>

## Out of scope

- <What this stub does not do.>

## Notes

<Decisions the build must keep. Files it will touch, when known. Optional.>
```

Required lines: the H1, `feature-slug`, `epic`, `sequence`, `depends-on`. The desk shows the
others when they are present. `complexity` decides the first gate (the contract's § The loop, step 3).
