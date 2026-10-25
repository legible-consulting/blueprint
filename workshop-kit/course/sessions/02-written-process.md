# Session 2 — The written process and the project

Jake's layer two. The attendee turns yesterday's corrections into a written process the
assistant picks up on its own, tests it in a fresh chat, and learns to keep the facts of one
client apart from the method.

## 1. The principle

A correction you make twice is a decision. Write it down once, as a process the assistant can
pick up, and keep the facts of one client apart from it.

## 2. Concepts

### Start from a recipe card

Bring a recipe card into the room, or a checklist from a kitchen, a cockpit or a workshop.
Read it aloud. It has a title that says what it is for. It has a line that says when to use it.
It has steps in plain words. It leaves out what every cook knows. It names the one thing that
goes wrong if you skip it.

The written process the assistant reads is the same card. Jake calls it a skill. A
French-speaking room calls it a consigne. This course calls it the written process, so that no
tool's word owns it. Whatever the name, it is a folder that holds a text file with three
parts: a name, a line that says when it applies, and the steps.

Checklists have a history worth one sentence, hedged. The story usually told is that a 1935
test flight of a new bomber ended in a crash because the aircraft had become too much for one
pilot's memory, and the crews answered with a card. The details vary by teller. The point does
not: a process written down is a process that a second person, or a second session, can run.

### Plain text, and why it was chosen

The card is written in markdown: plain text with a few marks for headings, lists and emphasis.
John Gruber published the format in 2004. It was chosen for the assistant for a plainer reason
than taste: the model already writes in it, every text editor opens it, and it survives every
app change. The method you learn this week rests on files like this and nothing more.

### A frozen conversation

Yesterday you had a conversation that ended with a usable reply. The written process is that
conversation, frozen. Jake's phrase in one of his recorded sessions is that a skill is
technically a frozen conversation. The corrections you logged are the parts worth freezing.

What goes on the desk when you have many such cards? Not all of them. The tool puts only each
card's name and its when-to-use line on the desk. When a request matches one, the full steps
load. This keeps the desk clean with ten cards or a hundred. It also means the when-to-use
line does the routing. A vague one never fires. A greedy one fires for everything.

### A generated card needs reading

You will not write the card by hand. You will ask the assistant for one and answer its
questions: what the job is for, what triggers it, one good example. Then you read what it
wrote, and you read it as an editor, because two things happen often. The assistant invents a
rule you never stated. The assistant takes one example and promotes it to a law. Strike both.
Then ask it to rewrite from your edits. The human writes the rules. The model writes them up.

Jake's lesson quotes a team that mapped dozens of workflows in days and cut a multi-day
estimate to hours. The library note marks it as an anecdote told in the video and nowhere
verified. Treat it as a direction, not a number.

### Method travels, facts stay

Now the split that the rest of the course depends on. The way you reply to customers is
method. It travels to the next customer, the next client, the next year. The hours of this
one business, the price of this one service, the name of this one contact, are facts. They
stay with that client.

The assistant's tools give the two different homes. The written process holds method. A
project holds facts: the files and the short instruction that are true for one client or one
area. Mix them and one client's details leak into every reply. Keep them apart and you can
hand the method to someone else without handing them a client.

One more box: the instructions field that applies to every chat. It holds only what is true
in every conversation, such as your name and your language. Nothing about a client goes there.

### Four constants

A recorded talk of Jake's names four things every working prompt has, whether it lives in a
chat, a file or a framework: who the assistant is acting as, what shape the output must take,
how the output is checked, and what happens on failure. In a chat you do the last two by hand.
In a written process the first two are written, and the third is you reading the result. The
fourth, in this course, is always the same: hand it back to a person. There is no automatic
retry.

Use the four as a reading check on your card. A card with no output shape makes a different
reply each time. A card with no check is a card nobody reads.

### Raise the bar, do not detect

Jake's older recordings on teaching make one point that applies here. When a tool can pass
your review, the review was the weak part. The answer is not to detect the tool. The answer
is to say what good looks like before the draft exists, then judge against it. Today's last
activity does that with three drafts.

### The rule I run on

One home per fact. A price, a rule, a date lives in exactly one file, and every other file
points there. The method-versus-facts split is the first place the rule shows. Voice is
method, written once. The hours of one business are a fact, written once in that business's
folder. When two files carry the same fact, the two will drift, and the assistant will pick
one (why: two homes drift, and nobody notices which one the draft used · 2026-10-14).

### Three-line exercise

Write three lines about the card you will make today:

1. The job it is for, in the words you would use to a colleague.
2. The line that says when it applies.
3. The one correction from your log that must never be lost.

## 3. Activities

The attendee's sheets are in `../activities/`.

### A2.1 From corrections to a written process (35 min) — sheet `s2-a1-from-corrections-to-process.md`

Alone, then in pairs. The attendee asks the assistant for a written process for their job,
pastes the corrections log, answers the interview, saves the file, and reads it as an editor.

- **Worked:** the file has a name, a when-to-use line and steps. The attendee has struck at
  least one line the assistant invented or over-generalised, and can point to the correction
  each remaining step came from.
- **Common failure:** the attendee accepts the first draft whole. Ask: "Which line here did
  you never say?" There is always one.

### A2.2 The fresh-chat test (15 min) — sheet `s2-a2-fresh-chat-test.md`

The attendee opens a new chat, gives a one-line request, and watches whether the written
process announces itself.

- **Worked:** the assistant names the process it is using, and the reply follows the steps.
- **Common failure:** the process does not fire. Ask the attendee to read the when-to-use
  line aloud. It is either too vague to match or too specific to match this wording. Fix the
  line, not the request.

### A2.3 Method, facts, work, outputs (25 min) — sheet `s2-a3-method-facts-work-outputs.md`

Pairs, on the example's messy folder, printed as a file list. Each file goes in one of four
piles: method, facts, work in progress, outputs.

- **Worked:** the price lists are facts. The notes about how the owner writes to customers
  are method. The old flyer causes an argument, and the pair ends with it in outputs or in
  no pile. A file in no pile is written on the board as the first suspect.
- **Common failure:** everything goes in facts. Ask: "Would this file change if a new
  customer walked in?" If no, it is method.

### A2.4 Three drafts, stated criteria (30 min) — sheet `s2-a4-three-drafts.md`

Pairs. Before any draft, the pair writes three criteria for a good reply to the example's
second request. The assistant produces three drafts. The pair grades each against the
criteria and explains one correction per draft.

- **Worked:** the criteria were written before the drafts. Each draft has one explained
  correction. At least one correction is a fact, not a word.
- **Common failure:** the pair picks the best draft and stops. Ask: "What did the best one
  still get wrong against criterion two?" The exercise is the correction, not the pick.

## 4. Story slot

> **Story slot (15 min).** One story from the facilitator's own practice. It must carry: a
> process that lived in one person's head, the day that person was not there, and what the
> written version changed. The point to land: method that is not written is method that is
> not owned.

## 5. Facilitator notes and timings

| Block | Minutes |
|---|---|
| Arrival. Recap of fiche 1. Each attendee names one correction from their log | 15 |
| Concepts: the recipe card, plain text, the frozen conversation, reading a generated card, method and facts, four constants, raise the bar, the rule I run on, the three-line exercise | 40 |
| A2.1 From corrections to a written process | 35 |
| A2.2 The fresh-chat test | 15 |
| Break | 15 |
| A2.3 Method, facts, work, outputs | 25 |
| A2.4 Three drafts, stated criteria | 30 |
| Story slot | 15 |
| Closing exercise: each pair names the file that fits no pile and says why | 10 |
| The fiche, read together, and the homework line | 10 |
| **Total** | **210** |

Notes:

- Tool steps, checked on 2026-10-25: in the Claude app a written process is a skill,
  uploaded under Customize, and code execution must be on under Settings, Capabilities. In
  ChatGPT and Codex the format is near-identical, so a card travels. When the app has
  changed, the official help page wins and this line is fixed.
- A2.3 is the quiet centre of the course. The four piles return in session 4 as the shape of
  the folder. Keep the board drawing.
- An attendee whose corrections log is thin works from the example's inbox and the
  facilitator's own corrections to the first request. Say so without comment.
- Do not let A2.4 become a vote. Criteria first, then drafts, then one correction each.

## 6. Fiche — session 2, the attendee keeps this page

**The principle.** A correction you make twice is a decision. Write it down once, as a process
the assistant can pick up, and keep the facts of one client apart from it.

**The written process.** A folder with a text file: a name, a line that says when it applies,
the steps. Called a skill in Claude, a consigne in French. Plain text, any editor.

**It is your frozen conversation.** The corrections you logged are the steps worth keeping.

**Only the name and the when-to-use line sit on the desk.** The steps load when a request
matches. The when-to-use line does the routing: vague never fires, greedy always fires.

**Read a generated card as an editor.** Strike the rule you never said. Strike the example
promoted to a law. Then let it rewrite from your edits.

**Method travels, facts stay.** How you reply is method, in the written process. This client's
hours and prices are facts, in a project. Mix them and one client leaks into every reply.

**Four constants.** Who it acts as. What shape the output takes. How the output is checked.
What happens on failure. Here, failure always means a person takes over.

**Criteria before drafts.** Say what good looks like, then judge. Do not detect the tool.

**One home per fact.** A price, a rule, a date lives in exactly one file. Two homes drift.

**Bring to session 3:** your written process file, and a tool that reads a folder.

## Sources

Library notes this session rests on, by path from the repository root:

- `library/course/jake-van-clief/01_the-foundation/01_the-three-layers/02_skills.md` — the
  skill as a process written down, the interview, reading the result, skill versus project,
  the instructions box.
- `library/course/jake-van-clief/00_reference-material/youtube/10_your-second-brain-is-not-a-notes.md`
  — the frozen conversation line, derived over raw, structure decides the signal.
- `library/course/jake-van-clief/00_reference-material/youtube/08_why-i-stopped-building-ai-agents-and.md`
  — a voice file written by the model drifts toward the model, so the hard rules are your
  own, and one concern per file.
- `library/course/jake-van-clief/00_reference-material/youtube/09_ai-is-the-new-compiler-why-learning.md`
  — the four constants.
- `library/course/jake-van-clief/04_the-archive/02_old-but-gold/02_raise-the-bar.md` — the
  review assignment: criteria first, three drafts, one correction each.
- `library/course/jake-van-clief/01_the-foundation/02_build-it-around-your-work/02_design-your-folder.md`
  — method, facts, work, outputs, used here as a sorting exercise and in full in session 4.
