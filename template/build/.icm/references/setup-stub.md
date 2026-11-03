# The setup stub

The contract is `.icm/intake/CONTEXT.md`. This file holds one shape the contract names. Read it
when you write one, not when you build one.

Some setup only a person can do: a project in a dashboard, a secret, a setting. Copier writes
one stub for each such act into `setup/`, from the answers in `.copier-answers.yml`. A new
answer or a new blueprint tag adds the stubs of its acts at the next `copier update`. Copier
never writes a stub again after a person moved it (why: the list of setup acts stays true
with each update, so no person forgets an act · Jamie, 2026-10-28).

```md
# Setup: <the act, one line>

- setup-slug: <kebab, equal to the file name>
- needs: <the answers that ask for this act>
- where: <the dashboard or the settings page>

## Why

<What fails without the act. One or two sentences.>

## Steps

1. <One instruction per line.>

## Done when

- [ ] <One observable result per line.>
```

- **Open or done is positional**, as for every stub. A stub in `setup/` is open. A stub in
  `setup/_done/` is done.
- **A person does the act, then says so.** On the person's word "setup <slug> done", a session
  moves the stub into `setup/_done/`, adds the first line `> Done: <who>, <YYYY-MM-DD>`, and
  commits the move on its branch. The merge makes it true. A session never moves a setup stub
  on a guess, on a file's word or on a check that passed (why: a check reads part of an act, the
  person did all of it · 2026-10-28).
- **An act that does not apply** moves to `setup/_done/` with `> Dropped: <reason>, <date>`.
- `session-start.sh` prints the open setup stubs at each session start, and the stop report
  names each open one under `Operator:` when the work waits on it.
