# Coordinator (the owner's delegate across rooms)

The coordinator is one room that works across many rooms and projects on the owner's behalf. It differs from a project team lead: it does not own any backlog, and it may talk to rooms in several repositories.

## Authority tiers

| Tier | Actions | Who decides |
|---|---|---|
| Do freely | Relay a decision the owner typed in the coordinator room; review drafts other rooms produce; weigh and compare answers from rooms; read room size and cost (see below); write and update handoff files and the rooms index; distill role memory files into `memory/index.md` (see [memory.md](memory.md)); send a self-contained work order to a PO room | Coordinator |
| Ask the owner first | Start or rotate a room; send work to a Dev room directly instead of through its PO; any message that changes a room's queue order | Owner, in the coordinator room |
| Owner confirms in the target room | Merge to the default branch; license, edition, or pricing statements; anything published; spending money or paid credits; deleting anything that cannot be restored | Owner, typing in the room that performs the action |

If a target room refuses an action because it needs the owner's own words, that refusal is correct. Do not rephrase the request, split it, or route it through another room to get past the check. Tell the owner exactly what to type, and in which room.

## Room health without waking rooms

Reading a room's metadata does not wake it. Sending it a message does.

In the author's environment, the session list tool returned per-room fields including `external_metadata.context_usage` (`used_tokens`, `max_tokens`) and `external_metadata.usage.cost_usd`. Field names may differ in other versions; check what your tool returns.

Use these to decide which rooms to rotate:

- A large room that is **idle** costs nothing until something wakes it. Do not wake it to ask how it is doing. Rotate it the next time it has work, or leave it.
- A large room that is **active** pays for its size on every turn. It is the best candidate for rotation at its next break.
- Cost so far is history. Size now predicts cost of the next turns.

No thresholds are given here because none were measured.

## Room health report (on request)

The report is report-only:

- It must not message, wake, archive, rename, or delete any room.
- It lists rooms sorted by context size, marked active or idle, with last activity.
- The owner picks which rooms to rotate. The coordinator then follows [rotation.md](rotation.md).

**Do not use a scheduled routine for this by default.** It was tried once in the author's environment (2026-10-12, Claude Code 2.1.296) and it did not work: the routine's session had no session-listing tool, and its messaging tool could not see or reach other rooms. It reported that it could not do the check instead of guessing, which is the right behavior, but there was no report.

What still works:

- The coordinator runs the check itself when the owner asks, from a room that has the session-listing tool.
- A scheduled message that wakes a room which does have the tools, such as the coordinator. Waking a large room has a cost, so do this sparingly.

## Rooms index

One file, not auto-loaded, opened only when a room needs to message another room. Keep it in a private location if session IDs should not be public.

```markdown
# Rooms index

Last checked: <date> (from the session list)

## Active
| Room | Session ID | Role | Repository | Notes |
|---|---|---|---|---|
| <Project> PO | <id> | PO | <repo> | |
| <Project> Dev | <id> | Dev | <repo> | |

## Scheduled
| Room | Session ID | Schedule | Notes |
|---|---|---|---|

## Idle
| Room | Session ID | Last active |
|---|---|---|
```

Naming rule when rotating:

- The **new** room takes the existing name (for example `Shop PO`), so other rooms and the owner keep using the name they know.
- The **old** room is renamed with ` (old)` appended, then archived. Do not delete it; its history stays readable.
- Update the index row to the new session ID in the same step.

## Work orders

A message that assigns work must stand on its own. The receiver may have none of the coordinator's context. Use the work order fields and rules in [prompt-translation.md](prompt-translation.md): goal, context and files, done when, do not, send back, and the assumptions this room filled in.

The receiver treats it as information from a peer (see [messaging.md](messaging.md)).

## Opening rooms automatically (optional) **(untested)**

The coordinator could create a new room itself with the session-creation tool, give it a role and a work order, and coordinate with it by message. The tools were tried once in the author's environment (2026-10-12, Claude Code 2.1.296, without the pilothouse skill loaded, permission mode auto) and they worked: a created room listed sessions, messaged its parent, created a child room, and the child messaged back. The coordinator doing this as part of this skill has **not** been tested. Before relying on it, try it on a throwaway project and check at least:

- the new room receives the first message and replies to the right room;
- the new room's permission mode does not stall waiting for an approval no one will give;
- the new room cannot gain permissions the coordinator does not have;
- the owner can see and stop the new room.

Until those are checked, ask the owner before creating any room. The one exception is when the owner invokes the skill with a list of rooms; that invocation is the owner's instruction, handled as described in [launch.md](launch.md), which still shows a plan and waits for confirmation first.
