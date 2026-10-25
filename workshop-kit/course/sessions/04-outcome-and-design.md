# Session 4 — Start with the outcome, then design the folder

Jake's module two. The attendee names who their job is for and what that person does next,
finds where the facts live, and designs the folder for their own job: a map, the four piles,
one contract. The walk test is introduced.

## 1. The principle

Name who the work is for and what they do next, find where the facts live, and let the
folder's shape follow the work.

## 2. Concepts

### Start from the diary on the wall

Most small businesses have one: a paper diary, a wall calendar, a spreadsheet that someone
exports on Monday. It is the least impressive object in the room and the most important one.
When a customer asks for Saturday, the answer is in there, and nowhere else.

Session 1 showed the reply that promised the room. No rewrite fixes that reply, because the
fact that makes it right or wrong lives in the diary. Jake's lesson calls this facts beat
prose. Before you design anything, find the diary. For your job it may be a price list, a
stock sheet, a rota, a ledger. Whatever it is, it is where the work begins.

### Four questions before any tool

Jake opens module two with four questions. Answer them for the job you brought, before you
open a folder:

1. Who is this for?
2. What must they do next, once they have it?
3. Where does the information come from now?
4. What breaks when it goes wrong, and who feels it?

The second question is the one people skip. Output exists so that someone can decide
something. Jake measures the quality of the output by how fast that person decides, what the
decision costs, and how they interact with the result. A weekly table that the owner reads in
one minute beats a report nobody opens.

Gerald Weinberg observed in 1971 that the way you name a problem shapes the thing you build.
Name the job as "answer date questions clearly" and you may fix the diary first and never build
an email writer at all.

### A rough split, kept rough

Jake offers a rule of thumb for where the effort goes: most of it in knowing the data and the
problem, a middle share in tools that already exist, and a small slice in the assistant
itself. He gives the shares as sixty, thirty and ten, and says in the same breath that the
numbers are deliberately rough. His written pages call it a design heuristic and never a
measured share of any system. The course keeps that hedge. Use the split to notice when you
have started at the ten. Do not use it to size anything.

His worked example: a Monday export of bookings becomes a table for the owner. The sixty is
knowing that pending bookings are what matter. The thirty is the export and a spreadsheet.
The ten is a short note from the assistant on what changed.

### Half the requests aim at the wrong problem

A practitioner Jake interviewed, who has run a machine-learning consultancy for years,
estimates that about half of the requests she receives aim a model at the wrong problem. Her
own number, from her own desk. Her screen before any build: can the requester name higher
revenue, lower cost or lower risk? If not, do not build. Then sort the problem: fixed steps
with no decision are plain software, predicting an outcome is machine learning, and an agent
earns a place only where its unpredictability is affordable.

Jake's webinar on why company pilots stall names five ways they fail: a demonstration that
never leaves the pilot, generated material nobody can find, cost with no outcome, one expert
who built it and cannot hand it on, and teams that rebuild from scratch. The statistics he
shows beside them come from third-party slides the library has not verified. The five failure
modes stand on their own as a checklist for your own job. Which one would yours fall into?

### Jobs to be done

A story usually credited to Theodore Levitt, and made popular by Clayton Christensen, says
that nobody wants a drill. They want a hole. Push once more and they want the picture on the
wall, and a strip of adhesive might do. Before you improve the drill, ask why the hole is
needed. Jake runs this live: for each workflow an attendee would hand to an assistant, he asks
who it is for and why it matters, and about one in three turns out to need a process change
and no assistant.

### Three shapes, one method

Jake compares three real folders that all came from the same method. A folder of stages, for
work that flows from one step to the next. A folder of records, one per client, for work that
repeats per relationship. A wiki, where raw sources sit apart from pages the assistant wrote
and linked, an idea he credits to Andrej Karpathy. Your folder will not look like his.
The method is the way of thinking that produces the shape. Shape follows work.

### Four piles, then a label

Session 2 sorted the example's files into four piles: method, facts, work, outputs. Today you
sort your own. Method carries across clients. Facts stay with one. Work is what is in
progress. Outputs are what leaves.

Then one label per file, from a lens Jake borrows from programming. A program has three
parts: instructions, something that runs them, and state that is read and changed. In a
folder, the model is the runner. Everything else you write is instructions or state. A file
that is neither is the first suspect, and usually a summary of a summary. David Parnas argued
in 1972 that a system should be split by what each part hides from the rest. In a folder, that
is why the voice file does not hold prices, and why the diary does not hold the voice.

### The paper's five layers, as a design aid

The paper behind the course gives the folder five kinds of context, top down:

| Layer | Answers | In your folder |
|---|---|---|
| 0, identity | where am I | the map's first lines |
| 1, routing | where do I go | the map's routing table |
| 2, the stage contract | what do I do | one `CONTEXT.md` per stage: reads, does, writes, who checks |
| 3, reference | what rules apply | the voice file, the conventions, the facts that do not change per run |
| 4, working | what am I working with | this week's inbox, this run's draft |

Layer 3 is the factory, configured once. Layer 4 is the product, new every run. The paper's
line for this: configure the factory, not the product. Keep the two apart in the folder and
the assistant receives them already sorted.

For a large source of facts, Jake's advice from the webinar is to describe it, not move it: a
short file that says where each kind of record lives and how to read it, rather than copying a
database into the folder.

### Short map, smallest version first

Write the map last, and keep it to one screen. Then test with a real request in a new
session. If the assistant reads everything, one routing row is vague. Tighten that row. Add
rooms only when the work asks for them. Jake's lesson mentions that a free written process,
ICM Architect, can draft a structure from a messy folder. Use it, if at all, as a second
opinion against your own sort.

### The rules I run on

Two of mine, because today you write your first map and your first contract.

A folder must let a cold session start. The map and the contracts carry everything the job
needs. The test is item 1 of the walk test: a fresh session answers what this folder is, what
is in progress and what is next, from the map and at most two files (why: a job that needs
the memory of an earlier conversation breaks the day a fresh session opens it · 2026-10-14).

A rule carries its own why and its own date. A rule without a why is deleted. You will see
the form all over this course: a rule, then "why:", then the date it was set. When you cannot
say why a rule exists, you cannot say when it is safe to change, and the next person cannot
either (why: a rule nobody can explain is never safely changed · 2026-10-14).

### Three-line exercise

Write three lines about your folder:

1. The decision your output helps someone make.
2. The one file that holds the fact most likely to be wrong.
3. The first routing row of your map.

## 3. Activities

The attendee's sheets are in `../activities/`.

### A4.1 The four questions (20 min) — sheet `s4-a1-four-questions.md`

Alone, then pairs. Each attendee answers the four questions for the job they brought, and
reads the answers to their pair.

- **Worked:** question 2 names a decision, not a document. Question 3 names a place for each
  fact. The pair can repeat the decision back.
- **Common failure:** question 1 is "me" and question 2 is "read it". Ask: "What do you do
  differently on Monday because of it?"

### A4.2 The split and the fact (20 min) — sheet `s4-a2-the-split-and-the-fact.md`

Pairs. Each attendee marks the sixty, thirty and ten of their job in rough words, then names
the fact from session 1's third activity that prose could not fix, and where it lives in
their own job.

- **Worked:** the ten is small and named. The fact has a file, a sheet or a system as its
  home. The attendee can say whether that home is a place the assistant can read.
- **Common failure:** the ten is everything. Ask: "Which parts would still be work if the
  assistant did not exist?" That is the sixty and the thirty.

### A4.3 Jobs, reads and makes, four piles, one label (25 min) — sheet `s4-a3-jobs-reads-makes.md`

Alone, on the copy of their real folder. List the jobs toward the outcome. For each, what it
reads and what it makes. Sort every file into the four piles. Label each file instructions,
state or both. Circle any file that is neither.

- **Worked:** every file has a pile and a label. At least one file is circled, and the
  attendee says what to do with it: delete, merge or archive.
- **Common failure:** no file is circled. Ask: "Which file is a summary of another file?"
  Circle it.

### A4.4 Design your folder (35 min) — sheet `s4-a4-design-your-folder.md`

Alone, then pairs. The attendee writes the map on one screen and one stage contract with four
parts: reads, does, writes, who checks. Then runs walk test items 1 and 2 with their pair
watching the file list.

- **Worked:** the map fits on one screen and every rule in it has a why and a date. The
  contract names its inputs by file. Item 1 passes: the fresh session answers from the map
  and at most two files. Item 2 passes: the request opens three files or fewer.
- **Common failure:** item 2 fails because the routing row says "the relevant files". Ask:
  "Name them." Then the row names them.

### A4.5 A new request with an unstated assumption (10 min) — sheet `s4-a5-unstated-assumption.md`

Facilitator demonstration on `example/ordered/`, then one run per pair. The first scenario
again, now through the ordered folder.

- **Worked:** the draft names the assumption or asks the owner the one question, instead of
  guessing. The pair finds the line in the map or the contract that made it do so.
- **Common failure:** the draft still guesses. Ask: "Which file should have carried the fact,
  and does the routing row open it?"

## 4. Story slot

> **Story slot (15 min).** One story from the facilitator's own practice. It must carry: a
> job that was named as a tool before it was named as an outcome, what got built, and what
> should have been built instead. The point to land: the diary was the fix, not the writer.

## 5. Facilitator notes and timings

| Block | Minutes |
|---|---|
| Arrival. Recap of fiche 3. Each attendee shows the folder copy they brought | 15 |
| Concepts: the diary, four questions, the rough split, the wrong problem, jobs to be done, three shapes, four piles and a label, the five layers, short map, the rules I run on, the three-line exercise | 40 |
| A4.1 The four questions | 20 |
| A4.2 The split and the fact | 20 |
| Break | 15 |
| A4.3 Jobs, reads and makes, four piles, one label | 25 |
| A4.4 Design your folder | 35 |
| A4.5 A new request with an unstated assumption | 10 |
| Story slot | 15 |
| Closing exercise: each attendee reads their first routing row, and the walk test is handed out | 10 |
| The fiche, and the homework line | 5 |
| **Total** | **210** |

Notes:

- Hand out `../walk-test.md` at the close. Say that session 5 runs all eleven items. Today
  only items 1 and 2 run, in A4.4.
- Keep the sixty, thirty, ten rough. When an attendee asks how to measure it, say that
  nobody has, including Jake, and that the number exists to catch a start at the ten.
- The five-layer table is the only place today where the paper's layers appear. Do not call
  them Jake's layers. Point to the board drawing from session 3.
- The real folders attendees bring are their own. The facilitator reads over shoulders and
  never types in them.
- An attendee with no real folder works on `example/messy/` and designs its ordered version.
  Compare with `example/ordered/` at the end, not before.
- Homework: finish the map and the one contract. Bring the folder to session 5.

## 6. Fiche — session 4, the attendee keeps this page

**The principle.** Name who the work is for and what they do next, find where the facts live,
and let the folder's shape follow the work.

**Four questions first.** Who is this for. What must they do next. Where does the information
come from now. What breaks, and who feels it.

**Facts beat prose.** The fact lives in the diary, the price list, the rota. No rewrite fixes
a reply that promised something the diary denies.

**A rough split, kept rough.** Most of the work is knowing the data and the problem. A
middle share is tools you already have. A small slice is the assistant. The numbers are a
heuristic, not a measure. Use them to notice when you started at the small slice.

**Before any build.** Does it raise revenue, cut cost or cut risk. Is the problem fixed steps,
a prediction, or a judgment. Would a process change do.

**Three shapes.** Stages for work that flows. Records for work per client. A wiki for sources
and linked pages. Shape follows work.

**Four piles, one label.** Method, facts, work, outputs. Then instructions, state or both. A
file that is neither is the first suspect.

**The paper's five layers.** Identity, routing, the stage contract, reference, working.
Configure the factory, not the product.

**Short map.** One screen. Test with a real request. If it reads everything, one row is vague.

**Two rules.** A folder must let a cold session start. A rule carries its why and its date.

**Bring to session 5:** your folder with its map and one contract, and the walk test.

## Sources

Library notes this session rests on, by path from the repository root:

- `library/course/jake-van-clief/01_the-foundation/02_build-it-around-your-work/01_start-with-outcome.md`
  — the four questions, the rough split and its hedge, facts beat prose, the decision
  framing, Weinberg, the bookings example.
- `library/course/jake-van-clief/01_the-foundation/02_build-it-around-your-work/02_design-your-folder.md`
  — three shapes, method and facts, the instructions-runner-state lens, the short map, the
  smallest version, ICM Architect.
- `library/course/jake-van-clief/01_the-foundation/05_history-and-concepts/01_choose-your-concept-series-guide.md`
  — the three-line exercise and the heuristic hedge on the split.
- `library/course/jake-van-clief/04_the-archive/03_ownership-in-the-ai-age/04_computational-orchestration.md`
  — rule, model or human per step, and the guide's note that the split is not a quota.
- `library/course/jake-van-clief/00_reference-material/youtube/03_systems-thinking-for-people-who-build-with.md`
  — the five failure modes, describe big data instead of moving it, jobs to be done, and the
  unverified statistics left out.
- `library/course/jake-van-clief/00_reference-material/youtube/05_a-pagani-a-toyota-and-why-best.md`
  — the practitioner's screen: revenue, cost or risk, then the three-way sort, and her
  estimate that about half of requests aim at the wrong problem.
- `library/course/jake-van-clief/00_reference-material/icm.pdf` — sections 3.1 and 3.2: the
  five layers, the factory and the product, the stage contract's inputs, process and outputs.
