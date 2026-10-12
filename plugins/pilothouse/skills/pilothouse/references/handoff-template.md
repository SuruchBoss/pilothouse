# Handoff file

One file per role, for example `docs/handoff/po.md`, `docs/handoff/dev.md`, `docs/handoff/qa.md`. If the repository already has a short status file for that role, use it instead of creating a new one. A long backlog or decision log is **not** a handoff file.

Rules:

- **Overwrite, do not append.** The file describes now, not history. History belongs in git, tickets, and decision records.
- Keep it under about 60 lines.
- Update it before ending a unit of work and before the room is rotated.
- A new room for this role reads this file first, before anything else in the repository.
- If the repository is public, the file is public. No secrets, tokens, personal data, or customer names.

## Template

```markdown
# <Role> handoff

Updated: <YYYY-MM-DD HH:MM, timezone> by <room name>

## Current work
- <ticket or task>: <state in one line> (branch `<name>`, last commit `<sha>`)

## Waiting on
- <who or what>: <what is needed>, <how this room will know it arrived>

## Next
1. <next step>
2. <next step>

## Decisions made in this role, not yet reviewed
- <decision>: <reason>

## Do not
- <anything the next room must avoid, with the reason>

## How to verify the current state
- <command or check that proves the state above, e.g. "CI on main is green at <sha>">
```
