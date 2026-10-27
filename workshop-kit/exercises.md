# Exercises

One exercise per hour of the day in `slides.md`. Attendees work in pairs, on their own real
work. Each exercise has a goal, the steps, what the attendee leaves with, and a check. A second
person does the check in two minutes. An exercise ends when its check passes, not when the
hour ends.

Last check of the tool steps: 2026-10-26. They work in a chat tool with projects, where the
contract goes in the project's instructions. They also work in an agent that works in a
folder, such as Claude Code or Codex, where the contract is a file. When a tool changes, the step changes and the method
stays.

Sources, in `legible-consulting/library` (read only), under
`course/jake-van-clief/01_the-foundation/`: `00_start-here.md`, `01_the-three-layers/`,
`02_build-it-around-your-work/`, `03_automate-it-keep-your-judgment/`,
`05_history-and-concepts/04_the-ladder-that-explains-every-ai-failure.md`. The training goal:
`research/design-trail/01-goals.md`.

## 1. Sort your week, correct one real job

Hour 1, the desk. Source: `01_the-three-layers/01_chat.md`,
`05_history-and-concepts/04_the-ladder-that-explains-every-ai-failure.md` (the task triage).

**Goal.** See where the model has a place in your week, and collect the corrections that one
real job needs.

**Steps.**

1. List the tasks of your normal week. Ten lines are enough.
2. Put each task in one column: the model, a normal tool (spreadsheet, ERP, calendar), a
   person.
3. Choose one task from the model column that you do every week. This is your job for the
   day.
4. Open a new conversation. Give it one real input of that job and a short request.
5. Correct the output in plain words until you could send it.
6. Write each correction on its own line: what you changed and why.

**You leave with.** Your sorted week. Your job for the day. A list of corrections.

**Check.** Your partner reads the list. Each line says what changed and why. At least three
lines. The job is one that recurs.

## 2. Turn the corrections into a contract

Hour 2, the written process. Source: `01_the-three-layers/02_skills.md`,
`01_the-three-layers/04_pick-your-setup.md`.

**Goal.** Write the job's method down once, so that you stop answering the same questions.

**Steps.**

1. In a new conversation, give the model your list of corrections. Ask it to interview you
   and then write a short process: a name, when to use it, the steps.
2. Answer its questions: the purpose, when to use it, one good example.
3. Read the result line by line. Delete each rule you never said. Delete each example that
   became a law.
4. Split the file: the method stays, the facts of one case go out.
5. Put the method where your tool reads it: a project's instructions, or a file in a folder.
6. Test it in a new conversation with a one-line request and a new input.

**You leave with.** The first contract of your job, in your own words.

**Check.** Your partner gives the one-line request in a new conversation. The output needs
fewer corrections than in exercise 1. The contract names no client, order or price.

## 3. Map one job: reads, makes, stages

Hour 3, the folder and the map. Source: `02_build-it-around-your-work/01_start-with-outcome.md`,
`02_build-it-around-your-work/02_design-your-folder.md`,
`01_the-three-layers/03_folders-agent.md`.

**Goal.** Cut the job into stages, each of which reads files and writes one file.

**Steps.**

1. Answer the four questions on paper. Who is the work for? What do they do next? Where does
   the information come from today? What breaks, and who feels it?
2. Write the steps of the job. For each step: what it reads, what it makes.
3. Group the steps into three stages: collect, draft, deliver.
4. Sort the job's files into four piles: method, facts, work in progress, outputs.
5. Mark each file as instruction or state. Strike out each file that is neither.
6. Draw the folder: the map at the top, one folder per stage.

**You leave with.** The map of your job on one page: stages, reads, makes.

**Check.** Your partner points at any stage and asks "what does it read, what does it write?".
You answer from the page, with file names.

## 4. Set up the three stages

Hour 4, your workspace. Source: `02_build-it-around-your-work/02_design-your-folder.md`.

**Goal.** Have a real folder on your machine or your shared drive, with the shape of the
map from exercise 3.

**Steps.**

1. Make the workspace. Render it from the blueprint
   (`copier copy gh:legible-consulting/blueprint <folder> --data workspace=true`), or make the
   folders by hand: a map file, `01-collect/`, `02-draft/`, `03-deliver/`, each with a
   `CONTEXT.md`.
2. Write the map: what the folder holds, one routing row per stage, how to name files.
3. Keep the map on one screen.
4. Put the contract from exercise 2 where the draft stage reads it.
5. Put one real input in `01-collect/`.

**You leave with.** Your workspace, with a map and one real input.

**Check.** Your partner opens the map and, without your help, says which folder the next
input goes into and which stage writes the draft.

## 5. Write the contracts, name the gate

Hour 5, contracts and the gate. Source: `03_automate-it-keep-your-judgment/01_stages-you-can-step-into.md`,
`03_automate-it-keep-your-judgment/02_steady-parts-into-code.md`.

**Goal.** Each stage knows what it reads, what it does and what it writes. A person checks the
draft before it goes further.

**Steps.**

1. In each `CONTEXT.md`, write three sections: `## Inputs`, `## Process`, `## Outputs`. One
   instruction per line.
2. Inputs name files, not folders.
3. In the draft stage, write the gate. It has one checkbox, the role of the person who ticks it, and
   the rule that the deliver stage starts only after the tick.
4. Find each step that must give the same output every time: a total, a date, a reference.
   Give it to a tool (the spreadsheet, the ERP, a script). Write which tool in the Process.
5. Mark the one or two stages where your judgment changes the result.

**You leave with.** Three contracts and one gate.

**Check.** Your partner reads each contract and finds Inputs, Process and Outputs. The gate
names a role. The model does no step that must be exact.

## 6. One real run, step in at the gate

Hour 6, run it once.

**Goal.** One useful result from the workspace, with your judgment at the gate.

**Steps.**

1. Start a new session on the workspace.
2. Ask for each stage with one short request.
3. Watch which files the model opens. When it opens a wrong file, correct the map row or the
   Inputs line, and run the stage again.
4. Read the draft. Step in: add, shorten, delete. Tick the gate.
5. Run the deliver stage. You send the output, not the model.
6. Write down each correction you made at the gate. Each one that recurs becomes a line in
   the draft's contract.

**You leave with.** One finished output, and the corrections that improve the contract.

**Check.** Your partner opens the folder and finds one file per stage for this run, and a
ticked gate.

## 7. A fresh session and a colleague read it

Hour 7, the walk test. Source: `03_automate-it-keep-your-judgment/03_keep-it-useful-hand-it-on.md`,
`05_history-and-concepts/04_the-ladder-that-explains-every-ai-failure.md`.

**Goal.** Your workspace passes the walk test, and you know what you do with it next week.

**Steps.**

1. Run the checks in `walk-test.md`, in order.
2. When a check fails, correct the workspace. Run the check again.
3. Look at your sorted week from exercise 1 again. Choose the next job for a workspace, and
   one job you leave alone.
4. Ask: will the next version of my tool give this for free? If yes, make it smaller.
5. Choose how you hand it on: a copy, or one shared place where you agree who changes what.

**You leave with.** A workspace that passes the walk test. Your next job.

**Check.** The walk test passes. Your partner signs the line at the end of `walk-test.md`.
