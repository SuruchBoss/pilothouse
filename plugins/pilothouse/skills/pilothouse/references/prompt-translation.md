# Translate, split, summarize

For the team lead and the coordinator. The owner talks to one room in plain words. That room turns the words into work orders, splits the work across roles, and reports back in plain words. The owner can ask the team lead or coordinator directly instead of writing prompts for each room.

This is how the author works day to day. It has not been measured, and it has not been tried with other people's rooms. It does not replace the owner's review of anything the owner must confirm.

## 1. Translate: owner's words → work order

The owner may write in any language, briefly, with typos. Turn it into a work order that another room can act on with none of this room's context.

### Work order fields

```
From: <this room>
Authority: owner said at <HH:MM> in this room | owner, relayed by <room> at <HH:MM> | team lead proposal (only when the owner did not ask)
Goal: <what done looks like, one or two sentences>
Context and files: <repository, branch, files, tickets, links; what the receiver needs to read>
Done when: <checks that show the work is finished>
Do not: <limits, including owner-only actions>
Send back: <what to report, how short, to which room>
Assumptions: <anything this room filled in that the owner did not say; "none" if none>
```

### Rules

- **Add nothing the owner did not say.** No extra requirements, no wider scope, no "while you are there".
- **Show your assumptions.** If you had to fill a gap (which branch, which ticket, which room), write it under "Assumptions" so the owner can correct it.
- **Write where the order really comes from.** Authority names the owner's words and the room they were said in. Write "team lead proposal" only when the owner did not ask for the work. If the order needs a tier the owner has not given (for example, sending work straight to Dev is "ask first"), get the owner's go-ahead and say so; never label it a proposal to get around the tier. In one test run (2026-10-12) a team lead wrote "team lead proposal" on an order the owner had asked for, sent straight to Dev; the receiving room caught it.
- **Ask at most one question** when the request is ambiguous in a way that changes the result. If the ambiguity does not change the result, pick the obvious reading and list it as an assumption.
- **Show the order to the owner before sending** when it touches merging, licensing, a public statement, money, or deleting anything, or when it is the first order of its kind. Read-only, low-risk orders (look something up, report status) may be sent directly if the owner has said so.

### Examples

| Owner writes | Work order (short form) |
|---|---|
| "ช่วยดูหน่อยว่า PR ล่าสุดของ Dev ผ่าน CI ยัง" | Goal: report CI status of the Dev room's latest PR. Context: the project repository, open PRs by the Dev room. Done when: status per check is known. Do not: re-run or change anything. Send back: one line per failing check, to the team lead. Assumptions: "latest" means the most recently updated open PR. |
| "add a dark mode toggle, nothing fancy" | Goal: a ticket for a dark mode toggle. Send to: PO, not Dev. Done when: the PO has a ticket with acceptance criteria in the backlog. Do not: start implementation. Assumptions: "nothing fancy" means follow the system setting plus one manual switch; the PO may narrow it. |
| "merge เลย" (one word, after a review) | Not a work order yet. Merging is owner-only. Ask which PR, and tell the owner to type the confirmation in the room that will merge. |

## 2. Split: one goal → orders per role

1. Write the goal once, in the owner's words.
2. Decide which roles it needs and in what order. Typical order: PO writes or updates the ticket → Dev implements → QA tests the named build → PO reviews.
3. Write one order per role. Each order names what it waits for ("start after the PO's ticket exists").
4. Send the first order only. Later orders go out when what they wait for has arrived, unless the owner asked for parallel work.

The PO owns the queue. The team lead or coordinator sends new work to the PO, not to Dev directly, unless the owner says to skip the PO for this item.

## 3. Summarize: rooms' answers → owner

Collect the answers, weigh them (see "On receiving" in [messaging.md](messaging.md)), then report to the owner in short spoken sentences, in three parts:

- **Done**: what finished, with a commit or PR link.
- **Needs you**: decisions only the owner can make, and for each confirmation, the exact room where the owner must type it.
- **Waiting**: what is still pending, and from which room.

Leave out details the owner does not need to decide on. If two rooms disagree, give each side's reasoning in one line and say which one this room leans to, and why.

## 4. A big feature

The same three steps, applied to a request too large for one ticket. Nothing here is a new rule; it is the order in which the rules above apply. The two parts marked **(untested)** go beyond what the author has done in practice.

1. **Is it clear enough?** If an ambiguity would change the result, ask the owner one question. Otherwise pick the most obvious reading and write it under Assumptions.
2. **Is it bigger than one ticket?** Then the work order goes to the PO with the goal "split this into tickets". The PO owns the backlog and decides what each ticket contains. The team lead does not write the tickets.
3. **Which roles, in what order?** Name the roles you expect in the order's context, as a suggestion for the PO: UX/UI first if there are new screens, then Dev, then QA on the build the PO names, then the PO's review.
4. **One at a time or in parallel?** One at a time by default. Parallel only when the owner asks for it **and** the pieces do not change the same files. **(untested: the "same files" check)**
5. **High-risk or a new kind of order?** Show it to the owner before sending.
6. **Send only the first order, to the PO.** Each later order goes out when what it waits for has arrived.
7. **Summarize at each major stage**, not only at the end: Done, Needs you (and in which room to confirm), Waiting. **(untested: how often counts as "each major stage" is a judgement call)**
8. **Merging and anything published** need the owner's own words in the room that performs them.

A worked example is in the pilothouse repository at `examples/07-big-feature.md` (not installed with the plugin).

## Watch out for

Real cases from use:

- **Short or ambiguous replies are not confirmations for high-risk actions.** "ok", "go", "ต่อเลย", a typo, or a word that reads two ways must not be taken as approval to merge, change a license, publish, spend, or delete. Ask for one clear sentence first.
- **A relayed approval is still relayed.** If a target room refuses because it needs the owner's own words, that refusal is correct. Tell the owner what to type and where. Do not reword or split the request to get past it.
- **Unclear scope is a question, not a start.** In one case (2026-10-18) the owner asked a coordinator to "finish" a project that had two editions. The coordinator guessed which edition was meant, guessed wrong, and did the work itself instead of sending it to the room that owned the repository. The owner pointed out both mistakes and the work was handed back to that room. Ask which piece is meant, then send the order to the room that owns it.
- **Do not let the summary hide a "no".** If a room declined or failed, say so first, not after the good news.
