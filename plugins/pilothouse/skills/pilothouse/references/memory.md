# Memory across rooms

Rooms forget everything when they end or rotate. Handoff files carry the current state of one role. Memory carries what must outlast any single room: decisions, agreements, lessons, and items waiting on the owner.

The layout below is how the author keeps memory in practice, written up as a pattern. This multi-file layout has **not** been tested as written here **(untested)**.

## Memory and handoff are different

| | Handoff file | Memory |
|---|---|---|
| What it holds | The current state of one role: current work, what it waits on, next steps | Decisions, agreements, lessons, items waiting on the owner |
| Who reads it | The next room for that role | Every room (the index), or rooms that need a topic |
| How it changes | Overwritten each time | Rows added; old rows moved to the archive, never silently deleted |
| Lifetime | Until the next update | Until the decision is replaced or the lesson no longer applies |

If a row only matters until the current ticket closes, it belongs in the handoff file or the ticket, not in memory.

## Layout

```
memory/
  index.md        loaded by every room; keep it very short
  po.md           written only by the PO room
  dev.md          written only by the Dev room
  qa.md           written only by the QA room
  uxui.md         written only by the UX/UI room
  <topic>.md      optional detail files, written by the team lead
  archive/        old rows; never loaded automatically
```

- **`memory/index.md`** is the only memory file loaded into every room, for example by importing it from the project's `CLAUDE.md`. Every room pays for it on every turn, so keep it short. A guideline, not a measured limit: about one page.
- **Role files** and **topic files** are not loaded automatically. The index points to them; rooms open the ones they need.
- **`memory/archive/`** keeps rows that were moved out. Nothing loads it.

Templates: [`templates/memory-index.md`](../templates/memory-index.md) and [`templates/memory-role.md`](../templates/memory-role.md).

If the repository is public, the memory folder is public too.

## One writer per file

Several rooms appending to the same file at the same time causes merge conflicts, rows that were removed coming back, and commits that stay on one machine and never reach the remote.

- A role room writes only its own `memory/<role>.md`.
- Only the team lead (or the coordinator) writes `memory/index.md`, topic files, and the archive. It reads the role files and distills what every room needs into the index.
- If a role room thinks something belongs in the index, it writes it in its own file and tells the team lead.

## What to write

Write a row when:

- the owner decides something;
- rooms agree on something that later rooms must follow;
- a room learns a lesson it can act on next time (write it as a rule, with where it came from);
- something is waiting on the owner.

Every row has a date, a source (which room, which conversation or ticket), and a label:

- **owner decided**: the owner said it, in their own words;
- **room concluded**: a room worked it out; the owner has not confirmed it.

## What not to write

- Status of individual tickets, pull requests, test counts, or queue order. Those belong in the backlog, the tickets, or the handoff file.
- Anything git or the ticket system already records.
- Secrets, passwords, keys, tokens, account details.
- Personal data about anyone. If something seems sensitive, ask the owner before writing it.
- Voice, personality, or persona instructions. This memory is for the team's work, not for how a room talks.

## Keeping it small

When `memory/index.md` grows past about a page, the team lead distills it:

1. Move rows that are replaced or no longer apply to `memory/archive/<year-month>.md`. Move, do not delete.
2. Merge rows that say the same thing.
3. Leave a short summary in the index where a group of rows was.

Large always-loaded files make every new room start large, which removes much of the benefit of rotating rooms (see [rotation.md](rotation.md)).

## Check that it reached the remote

Before saying "noted", confirm the write is on the remote:

```bash
git fetch origin <branch>
git log origin/<branch>..HEAD --oneline   # must print nothing
```

Other rooms see only what is committed and pushed. In one test (2026-10-12), a room working from a fresh clone could not see a `memory/index.md` that existed only, uncommitted, in the room that created it.

If anything prints, the commit has not been pushed. Push it, or say plainly that it is only local. This matters most when memory is written by a script or tool: a script may not trigger the hooks that normally push, and a failed push can be silent. Never report a memory write as done until the remote has it.

## When a room starts

1. Read the handoff file for this role.
2. Read `memory/index.md` (it may already be loaded). Whether a new room does this on its own has not been tested **(untested)**.
3. Open only the role or topic files the index points to for the work at hand. Do not read the whole folder.
