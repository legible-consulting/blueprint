---
marp: true
title: ICM in one day
paginate: true
---

<!--
The one-day ICM workshop. The method in the morning, the walk in the afternoon.
Show with Marp: `marp workshop-kit/slides.md` or the Marp extension for VS Code.
Each section cites the library path it rests on, under
legible-consulting/library course/jake-van-clief/01_the-foundation/ (private, read only).
The exercises are in exercises.md. The test of the afternoon is in walk-test.md.
-->

# ICM in one day

The folder is the system.

Morning: the method. Afternoon: you build your own workspace and test it.

---

## The day

| Hour | Part | Exercise |
|---|---|---|
| 1 | The desk | 1. Sort your week, correct one real job |
| 2 | The written process | 2. Turn the corrections into a contract |
| 3 | The folder and the map | 3. Map one job: reads, makes, stages |
| — | Lunch | |
| 4 | Your workspace | 4. Set up the three stages |
| 5 | Contracts and the gate | 5. Write the contracts, name the gate |
| 6 | Run it once | 6. One real run, step in at the gate |
| 7 | The walk test | 7. A fresh session and a colleague read it |

---

## Five words for the day

- **The desk**: what the model sees in one conversation. Nothing else.
- **The stage**: one piece of work. It reads files and writes one file.
- **The contract**: the short file that tells a stage what it reads, what it does, what it writes.
- **The map**: the file at the top of the folder. It says what the folder holds and where each job goes.
- **The gate**: a person reads the file of a stage before the next stage starts.

<!-- source: 00_start-here.md (the three layers as a way to organise work, not a ladder of skill) -->

---

## Three layers, one idea

1. **Chat.** You type, you correct, you answer every question again next time.
2. **A written process.** Your corrections become a file the model reads.
3. **A folder.** A map, one folder per stage, one contract per stage. One short request starts real work, and every step is a file you can open.

Simple, then complex underneath, then simple again on top.

<!-- source: 00_start-here.md -->

---

<!-- _class: lead -->

# Hour 1 — The desk

<!-- source: 01_the-three-layers/01_chat.md, 05_history-and-concepts/04_the-ladder-that-explains-every-ai-failure.md (the task triage) -->

---

## Sort your week first

Every task goes in one of three columns:

| The model | A normal tool | A person |
|---|---|---|
| reads a situation and writes a draft | a total, a date, a stock level: the same answer each time | the decision, the relationship, the signature |

Most of the work is not the model. Start from the work, not from the tool.

---

## The model sees only its desk

- What you typed, what you attached, what the tool remembers. Nothing else.
- **Missing** on the desk: the model guesses.
- **Too much** on the desk: the model guesses which item you meant.
- So: **one conversation per job.** An old conversation carries old work onto the desk.

---

## Every word of a request is an open question

"Reply to this client" leaves open: the tone, the reader, what we promise, what we know.

In chat, you answer these questions again every time.

The rest of the day ends them: a file answers each one, once.

---

## Corrections are decisions

Each correction says something about:

- your **voice** (how we write),
- what is **true** (what we know, what we promise),
- the **relationship** (who this reader is to us).

A wrong promise costs more than a stiff sentence.

**Write every correction down.** The list is the material of hour 2.

→ Exercise 1

---

<!-- _class: lead -->

# Hour 2 — The written process

<!-- source: 01_the-three-layers/02_skills.md -->

---

## From corrections to a contract

1. Give the model your list of corrections.
2. Let it ask you questions: the purpose, when to use it, one good example.
3. It writes a short file: a name, when to use it, the steps.
4. **You read it.** A model sometimes adds a rule you never said, or makes one example into a law. You correct it.
5. Test it in a **new** conversation, with a one-line request.

---

## Method apart from facts

| Method | Facts |
|---|---|
| how we do this kind of job | this client, this order, this price |
| travels to the next case | stays with its case |
| the contract | the files of the case |

Mix them, and the details of one client leak into every reply.

---

## Where the contract lives

The tool does not matter. The file does.

- A chat tool with projects: the project's instructions and files.
- An agent in a folder (Claude Code, Codex): the folder's files.

The contract is plain text. It moves to the next tool with you.

<!-- source: 01_the-three-layers/04_pick-your-setup.md (four pieces: model, harness, interface, where it runs) -->

→ Exercise 2

---

<!-- _class: lead -->

# Hour 3 — The folder and the map

<!-- source: 01_the-three-layers/03_folders-agent.md, 02_build-it-around-your-work/01_start-with-outcome.md, 02_build-it-around-your-work/02_design-your-folder.md, 02_build-it-around-your-work/03_one-model-different-jobs.md -->

---

## Start from the outcome

Four questions before any tool:

1. Who is this work for?
2. What must that person do next?
3. Where does the information come from today?
4. What breaks, and who feels it?

The output helps someone decide. Measure it by how fast and how well they decide.

---

## Most of the work is not the model

- **The large share:** you know the data and the problem.
- **A middle share:** the tools you have already: the spreadsheet, the calendar, the mailbox.
- **A small share:** the model.

Facts beat prose: a better sentence does not correct a wrong date. The file that holds the date corrects it.

---

## The folder

```
CLAUDE.md          the map
01-collect/        the inputs, as they arrive
  CONTEXT.md       the contract of the stage
02-draft/          the draft
  CONTEXT.md       … and its gate
03-deliver/        the output, after the gate
  CONTEXT.md
```

Each stage: what it **reads**, what it **does**, what it **writes**.

---

## The map

- What the folder holds. Where each job goes. How to name files.
- A routing table: for each job, the files to open, the contract to apply, where the result goes.
- **Keep it short.** A map that lists every file puts the whole drawer back on the desk.

One model, many jobs: the role comes from what the model reads, not from a name.

---

## Instruction or state?

Each file is one of the two:

- **Instruction**: how to do the work. The contracts, the map, a template.
- **State**: what the work is now. The inputs, the drafts, the outputs.

A file that is neither is the first to delete.

→ Exercise 3

---

<!-- _class: lead -->

# Lunch

This afternoon: your own workspace, around your own job.

---

<!-- _class: lead -->

# Hour 4 — Your workspace

<!-- source: 02_build-it-around-your-work/02_design-your-folder.md (smallest version first) -->

---

## Smallest version first

- One job. Three stages. One gate.
- Add a stage only when the work asks for it.
- The starter: the three-stage workspace this blueprint renders, or the same three folders made by hand.

```bash
copier copy gh:legible-consulting/blueprint <folder> --data workspace=true
```

→ Exercise 4

---

<!-- _class: lead -->

# Hour 5 — Contracts and the gate

<!-- source: 03_automate-it-keep-your-judgment/01_stages-you-can-step-into.md, 03_automate-it-keep-your-judgment/02_steady-parts-into-code.md -->

---

## One stage, one file

- Each stage writes **one file** that a person can open.
- **Cheap early, expensive late.** An error in the draft costs one line. The same error in the sent document costs the client's trust.
- One request that goes from start to finish leaves only the most expensive point to step in.

---

## Where your judgment goes

- Do not check every stage. Check the one or two where taste changes the result.
- Stepping in is more than yes or no: add a line, shorten, and most often delete.
- The gate names **a person**. The next stage starts only after that person ticks.

---

## Steady parts go to a tool

If the same input must always give the same output, it is not the model's work:

- a total, a date, a reference, a layout → the spreadsheet, the ERP, a script.
- the reply, the choice, the tone → the model and you.

Check a tool once, properly, against a result made by hand.

→ Exercise 5

---

<!-- _class: lead -->

# Hour 6 — Run it once

---

## One real run

1. Put one real input in `01-collect/`.
2. Ask for each stage with one short request.
3. Watch what the model opens. A wrong file read means a vague row in the map.
4. Read the draft. Step in. Tick the gate yourself.
5. Deliver.

Finish one useful result, not the whole system.

→ Exercise 6

---

<!-- _class: lead -->

# Hour 7 — The walk test

<!-- source: 03_automate-it-keep-your-judgment/03_keep-it-useful-hand-it-on.md -->

---

## Keep it alive

- AI makes clutter cheap. Old drafts and versions mislead the next session.
- **An archive** that the map says never to read.
- **One home per fact.** A price, a rule, a contract: in one place.
- **The fresh-session test.** A new session says what the folder is, where the work stands, and what comes next. If it cannot, the map is out of date.

---

## The walk test

Your workspace passes when:

- a fresh session explains it correctly,
- a colleague from another team opens it and says the same,
- every check in `walk-test.md` passes.

Then you hand it on: a copy, or one shared place where you agree who changes what.

→ Exercise 7

---

## Before you leave

- Your sorted week: which job you automate next, which you leave alone.
- One question to keep: will the next version of the tool give this for free?
- Your workspace, your contracts, your gate.
- The attendance record for your files.

<!-- source: 05_history-and-concepts/04_the-ladder-that-explains-every-ai-failure.md (the triage revisited, the next-version question) -->

---

## Sources

The method of this day rests on, in `legible-consulting/library` (read only):

- `course/jake-van-clief/01_the-foundation/00_start-here.md`
- `…/01_the-three-layers/` (chat, skills, folders and one agent, pick your setup)
- `…/02_build-it-around-your-work/` (outcome, folder design, one model for different jobs)
- `…/03_automate-it-keep-your-judgment/` (stages, steady parts, keep it useful)
- `…/05_history-and-concepts/04_the-ladder-that-explains-every-ai-failure.md`
- `research/design-trail/01-goals.md` (the training goal)

ICM: the Interpretable Context Methodology. The course is Jake Van Clief's. These slides are ours.
