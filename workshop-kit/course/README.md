# Course — run your work from a folder

Five sessions of 3 h 30 for people who do real work with an AI assistant and want that work
to live in files they own. The course teaches the Interpretable Context Methodology (ICM),
the open method published by Van Clief and McDermott (arXiv 2603.16021, March 2026). The
teaching path follows Jake Van Clief's Foundation course, lesson for lesson. The rules that
Jamie Nisbet runs his own business on are taught beside it, each marked as his.

This file is the map. Read it, then open the session you need. Nothing in this folder needs
a previous conversation: a facilitator who starts cold reads this file and the session file
and can run the day.

## Who it is for

- One person or a small team with a recurring job that ends with a person receiving
  something: a reply, a quote, a weekly table, a report.
- No coding. Every file in the method is plain text that a text editor opens.
- An AI assistant account. The first two sessions run in a chat window. From session 3 the
  attendee needs a tool that reads a folder, such as the Claude desktop app's Code tab or
  Codex. Tool steps in the material carry a "checked on" date, because the apps change
  faster than the method.

## Where to start

The sessions build on each other, but an attendee who already works a certain way can enter
later. This table follows the entry points of the Foundation course.

| You already... | Start at |
|---|---|
| ask an assistant questions and nothing more | session 1 |
| use saved prompts, projects or custom instructions | session 2 |
| point a tool at a folder of your own files | session 3 |
| run a folder and want to know what to automate | session 4 |

A late entrant reads the fiches of the sessions they skip. Each fiche is the last page of
its session file.

## The five sessions

| # | Session | The one principle | File |
|---|---|---|---|
| 1 | Chat | The assistant sees only what is on its desk, and every word you type is a question it must answer from that desk. | `sessions/01-chat.md` |
| 2 | The written process and the project | A correction you make twice is a decision. Write it down once, as a process the assistant can pick up, and keep the facts of one client apart from it. | `sessions/02-written-process.md` |
| 3 | Folders and routing | A folder with a map at the top turns one model into whatever worker the job needs, and the map decides what it reads. | `sessions/03-folders-and-routing.md` |
| 4 | Start with the outcome, then design the folder | Name who the work is for and what they do next, find where the facts live, and let the folder's shape follow the work. | `sessions/04-outcome-and-design.md` |
| 5 | Stages you can step into, steady parts into a tool, hand it on | Split the job into stages that each leave one file, put the exact steps in a tool, keep one home per fact, and the folder outlives you and the model. | `sessions/05-stages-tools-handover.md` |

## What each session file holds

Every session file has the same six parts, in this order:

1. The principle, in one sentence.
2. The concepts, in the manner of the Foundation course: start from a thing in the room,
   trace the layers or the history beneath it, hedge every historical and numerical claim,
   end with a three-line exercise.
3. The activities, each with a check: what the facilitator sees when it worked, and what a
   common failure looks like. The attendee's sheet for each activity is in `activities/`.
4. A marked slot for the facilitator's own stories. The slot says what the story must carry.
   The story itself is not written here.
5. Facilitator notes with timings. Each session sums to 210 minutes.
6. A one-page fiche the attendee keeps.

## The worked example

One fictional small business runs through every activity. Its folder exists in two versions
under `example/`: `messy/` is the folder as the owner left it, `ordered/` is the folder at
the end of the course. `example/README.md` names each file by its role, so an activity sheet
can say "the newer price list" and the facilitator finds the path there. `example/scenarios.md`
holds the six scenarios the facilitator runs through the folder:

- a new request with an unstated assumption
- a wrong fact that better prose cannot fix
- an instruction planted inside a document
- two versions of one fact
- a handover to a new person
- a model swap

Nothing in the example is real. Every name, address, price and date is invented.

## The walk test

`walk-test.md` is the test an attendee's own folder must pass by the end of session 5. The
facilitator introduces it in session 4 and runs it in session 5. Each item states what to do
and what evidence counts as a pass.

## Words used in this course

The course uses one word for one thing. These are the words.

| Word | Means |
|---|---|
| the desk | everything the assistant can see for this one answer: what you typed, attached or it remembered. Nothing else exists for it. |
| the map | the one file at the top of a folder that the tool reads every time. `CLAUDE.md` in Claude Code, `AGENTS.md` in Codex. It says what the folder is and where to go. |
| a contract | the `CONTEXT.md` of one stage folder: what the stage reads, what it does, what it writes, who checks it. |
| a stage | one step of a job, with its own folder, its own contract and one output file. |
| a gate | a checkbox a human ticks before the next stage runs. The assistant reads it and never ticks it. |
| one home per fact | a price, a rule, a date lives in exactly one file. Every other file points there. |
| a cold session | a fresh conversation with no memory of earlier ones. The folder must let it start. |
| the written process | a file that tells the assistant how you do one kind of job. Called a skill in Claude, a consigne in the French-speaking room. |
| a project | a set of facts about one client or one area, kept apart from the written process. |

## Two meanings of "layer"

The Foundation course uses "layer" for three ways of working: chat, the written process,
folders with one agent. The ICM paper uses "layer" for five kinds of context a folder
delivers: identity, routing, the stage contract, reference material, working files. The
course keeps the two apart. When a session file says "Jake's three layers" it means the
first. When it says "the paper's five layers" it means the second. The two are never
numbered together.

## Timings

| Session | Minutes |
|---|---|
| 1 | 210 |
| 2 | 210 |
| 3 | 210 |
| 4 | 210 |
| 5 | 210 |
| Total | 1050 = 17 h 30 |

The block-level timings are in part 5 of each session file. `facilitator-guide.md` says
how to run the course and what to bring.

## Sources

Every session file ends with a Sources section that names the library notes it rests on,
by path. The course material quotes at most one line from the Foundation course per file.
Where a note lists a correction to a video (under "Claims and evidence"), the session file
carries the corrected version, hedged.

## Out of scope

The one-day workshop deck, client adaptations, pricing and translations are not in this
folder. The English text here is the master copy.
