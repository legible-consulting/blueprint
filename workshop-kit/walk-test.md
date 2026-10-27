# The walk test

The test an attendee's workspace must pass at the end of the day (exercise 7 in
`exercises.md`). A coaching hour runs the same test again on the client's own workspace. Each
check passes or fails. A workspace passes when every check passes. A colleague who did not
build the workspace runs checks 8 and 9.

Sources, in `legible-consulting/library` (read only), under
`course/jake-van-clief/01_the-foundation/`:

- `01_the-three-layers/03_folders-agent.md`: the map, the routing table, the read test.
- `02_build-it-around-your-work/02_design-your-folder.md`: method apart from facts,
  instruction or state, the short map.
- `03_automate-it-keep-your-judgment/01_stages-you-can-step-into.md`: one stage one file, the
  stage contract, the named checker.
- `03_automate-it-keep-your-judgment/03_keep-it-useful-hand-it-on.md`: the fresh-session test,
  one home per fact, the archive, the map as onboarding.

## The folder

1. **The map fits on one screen.** It says what the folder holds, how to name files, and
   has one routing row per stage. It does not list every file.
2. **Each stage has a contract.** Each stage folder has a `CONTEXT.md` with the three
   sections `## Inputs`, `## Process` and `## Outputs`. A workspace rendered from the
   blueprint gets this check from CI: its `ci.yml` asks `check-client` with
   `workspace: true`.
3. **Inputs name files.** Each Inputs line names a file or a file name pattern, not "the
   folder" or "everything".
4. **One stage, one file.** Each stage writes one file that a person can open and read.
5. **Method apart from facts.** No contract names a client, an order or a price. The facts
   of one case are in that case's files.
6. **One home per fact.** A price, a rule or a template exists in one file only. Old work is
   in an archive that the map says never to read, or you delete it.

## The gate

7. **A person checks.** At least one gate exists: a checkbox, the role of the person who
   ticks it, and the stage that waits for the tick. A tool, not the model, does each step
   that must give the same output every time.

## The readers

8. **The fresh-session test.** Open a new session on the workspace. Ask: "What is this
   folder, where does the work stand, and what comes next?" The answer is correct, and the
   session opened only the map and the files the map routes to.
9. **The colleague test.** A colleague from another team opens the folder without the
   model. In five minutes they say what it is, where the work stands, and what comes next.

## Sign-off

- [ ] All nine checks pass. — checked by: ____________________, date: __________
