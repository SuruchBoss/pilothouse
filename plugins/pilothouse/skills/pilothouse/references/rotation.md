# Rotating a room

Every turn resends the room's whole conversation. A room that has grown large costs more on every later turn, even when the work is small. Rotating means ending the old room's role and continuing in a fresh room (a new session, or `/clear` in the same one) that starts from the handoff file.

## When to rotate

- A unit of work has ended and the next one is unrelated.
- The room's context has grown large. Pick a threshold that suits your plan and budget; this skill does not prescribe a number because none was measured.
- The room has started repeating itself, re-reading files it already read, or losing track of earlier decisions.

Do not rotate in the middle of a unit of work unless the owner asks.

**A new room does not start empty.** It starts with everything the environment loads into every session: rule files, memory files, and anything else configured to load at start. That can be large. In the author's tests, even a small test room started out large. Check a new room's size before counting on savings: rotating pays off when the old room is much larger than a new room's starting size. Keeping always-loaded memory short helps here (see [memory.md](memory.md#keeping-it-small)).

## Procedure

The old room proposes; the owner decides. A room must not clear or replace itself unprompted.

1. **Finish or park the current step.** Push work in progress to a branch, or note exactly where it stopped.
2. **Write the handoff file** using [handoff-template.md](handoff-template.md). Include the branch, last commit, what is waited on, and anything the next room must not do.
3. **Commit and push the handoff file**, then confirm the remote has it (for example, compare the local and remote commit).
4. **Tell the owner** that the room is ready to rotate, and give the one line the new room should be started with, for example:
   `You are the Dev room for <repo>. Read docs/handoff/dev.md first.`
5. **The owner starts the new room** (or runs `/clear`) with that line.
6. **The new room** reads the handoff file, then `memory/index.md` if the team keeps one (see [memory.md](memory.md)), checks the handoff against the repository (branch exists, commit matches, CI state), and reports any mismatch before doing anything else.
7. **Update the room index** (if the team keeps one) so other rooms message the new room, not the old one. The new room takes the old name; the old room gets ` (old)` appended and is archived, not deleted. See [coordinator.md](coordinator.md#rooms-index).
8. The old room stops taking work. Messages that still reach it should be answered with a pointer to the new room. **(untested: whether an old room keeps receiving messages after rotation depends on the environment.)**

## Scheduled or automated rooms

A room that runs on a schedule and reuses the same session grows every day. Prefer starting a fresh session for each run, with the full instructions in the scheduled prompt itself rather than in a file the run is told to read. **(untested in this skill; based on the author's observation that reused scheduled sessions kept growing.)**
