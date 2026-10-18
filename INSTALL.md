# Installing pilothouse

[ภาษาไทย](INSTALL.th.md)

pilothouse is a skill for **Claude Code**. These steps were run with Claude Code **2.1.296** on Linux. One local run on Windows with the Claude app (2026-10-14, Claude Code installed with npm, version not recorded) is noted where it applies. Other versions and other operating systems were not checked. No claim is made that it works with other agents or tools; for agents that only read rule files, [AGENTS.md](AGENTS.md) is a short text version without the skill's commands **(untested with any agent)**.

## Option 1: from the marketplace (recommended)

```bash
claude plugin marketplace add SuruchBoss/pilothouse
claude plugin install pilothouse@pilothouse
```

Both commands are needed. `marketplace add` only adds the catalog; nothing is installed until `plugin install`. Until then `claude plugin list` does not show pilothouse, which can look like a failed install.

Check that it installed:

```bash
claude plugin list
claude plugin details pilothouse@pilothouse
```

`list` shows `pilothouse@pilothouse` as enabled. `details` lists one skill, `pilothouse`, and no hooks, agents, or MCP servers.

Start a new session for the skill to load. A skill installed during a session is not available in that same session: in one test (2026-10-12) calling it there gave "Unknown skill". In the new session, the command is `/pilothouse:pilothouse`; the bare `/pilothouse` also works unless another command uses that name. In the Windows run (2026-10-14) the in-session command menu showed `pilothouse:pilothouse` with its description.

Claude Code also has a `/reload-plugins` command, and its own messages suggest it for loading plugin changes into the current session. Whether it makes this skill usable without a new session was not checked **(untested)**.

To update later:

```bash
claude plugin marketplace update pilothouse
claude plugin update pilothouse@pilothouse
```

## Option 2: copy the skill folder

Copy `plugins/pilothouse/skills/pilothouse/` into one of:

- `~/.claude/skills/pilothouse/` for all your projects, or
- `<your repository>/.claude/skills/pilothouse/` for one project (and everyone who clones it).

Check the folder is well formed:

```bash
claude plugin validate ~/.claude/skills
```

A copied skill does not appear in `claude plugin list`, because it is not a plugin. The command is `/pilothouse`. Loading it in a session was **not** checked here **(untested)**.

## Cloud sessions and local sessions

| | Local session | Cloud session |
|---|---|---|
| Roles, handoff files, rotation | Work the same way | Work the same way |
| `/pilothouse:pilothouse "name" role, ...` | Prints a starter prompt per room for you to paste into new sessions. Tried once on Windows (2026-10-14): five rooms, one prompt each. | If the session has a tool that creates sessions, the skill can create the rooms after you confirm a plan **(untested)**. Otherwise it prints starter prompts. |
| Cross-room messages | Depend on the tools your setup provides. Whether local sessions on one machine can message each other was not checked **(untested)**. If yours cannot, you carry messages between rooms yourself: copy a message from one room and paste it into the other. | In the author's cloud sessions, existing rooms could message each other. Tool names may differ in yours. |
| Installing | Option 1 or 2. A plugin installed for your user (the default scope) is available to every new session on that machine, so the printed starter prompts need no slash command. That the new rooms loaded the skill was not checked **(untested)**. | Option 2 in the repository (`.claude/skills/`) travels with the clone; whether it loads there was **not** checked **(untested)**. Option 1 from a local clone (`claude plugin marketplace add <path>`, then `claude plugin install pilothouse@pilothouse`) worked once in a cloud session (2026-10-12); adding by GitHub name (`claude plugin marketplace add SuruchBoss/pilothouse`) worked once in a cloud session with no repository attached and no token (2026-10-12). |
| Rooms created by another room | Not applicable | In one test the new room ran in its own container and did not have the plugin installed in the room that created it. It followed `AGENTS.md` from the repository. For it to have the skill, the skill must be there before the room starts; doing that through the environment's setup was not tried **(untested)**. |

If you are not sure what your session can do, use the printed starter prompts. That path needs no special tools.

## Uninstall

Marketplace install:

```bash
claude plugin uninstall pilothouse@pilothouse
claude plugin marketplace remove pilothouse
```

Copied folder: delete the `pilothouse` folder you copied.

## Problems you may run into

| Symptom | Likely cause | What to try |
|---|---|---|
| `/pilothouse` runs a different command | Another command already uses the name | Use `/pilothouse:pilothouse` |
| `Unknown skill`, or the skill does not seem to load, right after installing | Skills load when a session starts; this one started before the install | Start a new session. `/reload-plugins` may also work **(untested)** |
| `claude plugin list` is empty after `marketplace add` | `marketplace add` only adds the catalog | Run `claude plugin install pilothouse@pilothouse` |
| In a headless run (`claude -p`) the skill says it cannot read `references/launch.md` or another of its own files | Default permissions refuse reads outside the working directory, including the plugin's own folder (seen 2026-10-18 with a local-folder install and with a GitHub install) | Add the plugin folder with `--add-dir`. That worked for a local-folder install; a GitHub install keeps the files under `~/.claude/plugins/cache/pilothouse/`, which was not tried **(untested)** |
| A room created by another room cannot use `/pilothouse:pilothouse` | It started without the plugin, in its own container | Rely on `AGENTS.md` in the repository, or install the skill before the room starts **(untested)** |
| A hook commits or pushes files you made while testing | Some setups run a hook that commits untracked files when a room stops | List those files in `.git/info/exclude`; git then ignores them without a change to the repository |
| `/pilothouse:pilothouse "a" dev, "b" qa` stops and asks | A role is misspelled, a name repeats, or a role is missing | Fix the list; roles are `teamlead`, `po`, `dev`, `uxui`, `qa`, `coordinator` |
| A room refuses to merge or change a license from a message | It needs the owner's own words in that room, as designed | Type the confirmation in that room yourself |
| Rooms do not wake when CI finishes or another room replies | Most outside events do not wake a room by themselves | Have the room subscribe or schedule a check-in, or tell it yourself **(untested in general)** |
| Cloud rooms ignore a rule the local rooms follow | The rule is in a file outside the repository, or not committed and pushed | Put standing rules in a committed file in the repository, and repeat them in each room's starter prompt |
| `claude plugin marketplace add` fails | Network or GitHub access from your machine | Clone the repository and run `claude plugin marketplace add <path to clone>` |

## Removing what the skill created

The skill writes nothing on install. Rooms using it may create handoff files (for example `docs/handoff/dev.md`) and a rooms index in your repository. Those are ordinary files; delete them if you stop using the skill.
