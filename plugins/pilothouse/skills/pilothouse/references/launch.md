# Launching rooms from a list

The skill can be invoked with a list of rooms to start:

```
/pilothouse "room01-dev" dev, "hello-test" qa
```

When installed as a plugin the full command is `/pilothouse:pilothouse`; the bare `/pilothouse` also works unless another command already uses that name. When the skill folder is copied into `~/.claude/skills/` or a project's `.claude/skills/`, the command is `/pilothouse`.

## Parsing

The list is a comma-separated sequence of pairs. Each pair is a room name followed by a role.

- **Room name**: written in double quotes by the owner. Claude Code splits arguments with shell-style quoting, so the quotes may already be removed by the time the list reaches this skill. Accept a name with or without quotes, as long as it is a single word (letters, digits, `-`, `_`, `.`). **(untested: exactly how quotes and commas arrive in `$ARGUMENTS` was not checked.)**
- **Role**: one of `teamlead`, `po`, `dev`, `uxui`, `qa`, or `coordinator`. Case does not matter (`Dev`, `DEV`, `dev` are the same).

Stop and ask the owner, without creating or printing anything, when:

- a pair has a name but no role, or a role but no name;
- a role is not in the list above;
- two pairs use the same room name;
- the text cannot be split into pairs at all.

Do not guess what the owner meant. Show the part that failed and ask.

### Examples

| Input | Result |
|---|---|
| `"room01-dev" dev, "hello-test" qa` | `room01-dev` → Dev, `hello-test` → QA |
| `"shop-po" PO, "shop-dev" Dev, "shop-qa" QA` | three rooms; roles read case-insensitively |
| `"lead" teamlead` | one room, Team lead |
| `"room01-dev" developer` | stop: `developer` is not a known role (did you mean `dev`?) |
| `"room01" dev, "room01" qa` | stop: `room01` is used twice |
| `"room01-dev"` | stop: no role given for `room01-dev` |
| `dev qa` | stop: cannot tell names from roles |

## Path 1: the environment can create rooms **(untested)**

Applies when this session has a tool that creates new sessions (for example in Claude Code cloud sessions). The session tools themselves were tried once in the author's environment (2026-10-12, Claude Code 2.1.296) and worked: a created room could list sessions, message its parent, and create a child room that messaged back. The parts of this path that belong to the skill (parsing the list, showing the plan, waiting for confirmation, creating each room) remain untested.

Invoking the skill with a list is the owner's instruction to create those rooms. Still:

1. **Check for existing rooms.** List current sessions. If a room with the same name already exists, stop and ask whether to reuse it, rename the new one, or skip it. Never create a duplicate.
2. **Show a short plan first**: each room name, its role, its repository, and the first work order it will receive. Wait for the owner to confirm.
3. **Create each room** with the given name and a first message that stands on its own (see the work-order template in [coordinator.md](coordinator.md#work-orders)). The first message must:
   - state the room's role and point to [roles.md](roles.md) for that role;
   - name the handoff file the room owns (for example `docs/handoff/dev.md`) and tell it to read that file first if it exists;
   - say that owner-only actions need the owner's own words in that room.
4. **Update the rooms index** with each new name, session ID, role, and repository.
5. **Report** which rooms were created and which were skipped.

A room created this way may run in its own container. In the author's test (2026-10-12) it did: it did not have the plugin installed in the room that created it, and it followed the `AGENTS.md` it found in the repository. Write the first message so it works without the skill, for example by pointing to `AGENTS.md` or including the role's rules. Getting the skill into a new room before it starts, for example from the environment's setup, has not been tried **(untested)**.

Do not choose a permission mode that waits for an approval no one is watching. Do not give a new room permissions this session does not have.

## Path 2: no room-creation tool

Applies when running on a local machine or anywhere without a session-creation tool. Print, for each room, its name and a starter prompt the owner can paste into a new session. Do not create anything.

Starter prompts (replace `<repo>` and `<handoff path>`):

**teamlead**
```
You are the team lead room "<name>" for <repo>. Use the pilothouse skill, role: teamlead. Read <handoff path> first if it exists. You coordinate this project's rooms; you do not write product code. Owner-only actions need my own words in the room that performs them.
```

**po**
```
You are the PO room "<name>" for <repo>. Use the pilothouse skill, role: po. Read <handoff path> first if it exists. You own the backlog: write tickets with acceptance criteria, order the queue, review Dev results. You do not write production code or merge.
```

**dev**
```
You are the Dev room "<name>" for <repo>. Use the pilothouse skill, role: dev. Read <handoff path> first if it exists. Work one ticket at a time on a branch, run the checks CI runs before pushing, and report decisions the ticket did not specify. Do not start work the PO has not queued, and do not merge.
```

**uxui**
```
You are the UX/UI room "<name>" for <repo>. Use the pilothouse skill, role: uxui. Read <handoff path> first if it exists. Propose designs and audit existing UI with screenshots; hand findings to the PO as candidate tickets. Do not change scope or push to the default branch.
```

**qa**
```
You are the QA room "<name>" for <repo>. Use the pilothouse skill, role: qa. Read <handoff path> first if it exists. Test the exact build the PO names, reproduce before reporting, and report pass/fail per acceptance criterion. Do not fix product code.
```

**coordinator**
```
You are the coordinator room "<name>". Use the pilothouse skill, role: coordinator. Read the rooms index first. You act for me across rooms: relay my decisions, review drafts, weigh answers. You do not merge, change licenses, publish, or spend money for me.
```
