# The triage stub

The contract is `.icm/intake/CONTEXT.md`. This file holds one shape the contract names. Read it
when you write one, not when you build one.

Anything found that is not the current ticket's goes here, as one small stub, and the session
moves on. Never widen a pull request to absorb it. Never lose it in chat.

```md
# Stub: <title>

- lane: bug | tweak | chore | hotfix
- found-by: <where> · <YYYY-MM-DD>
- complexity: low | medium | high | research
- priority: P0 | P1 | P2

## Problem

<Observed. One or two lines. File paths when known.>

## Proposed change

<One line, or "investigate".>

## Acceptance criteria

- [ ] <One observable result per line. The pull request copies these lines.>
```

No breakdown, no `sequence`, no `depends-on`. The stub needs its acceptance criteria:
`new-run.sh` copies them into the pull request, and a stub without them gets one placeholder
line to fill by hand. The folder is a backlog, not a batch. Jamie prunes it. A session only
adds to it and consumes from it.
