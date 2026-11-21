# What has been tested

[ภาษาไทย](TESTED.th.md) · [Back to README](../README.md)

pilothouse is written for and tried only with Claude Code. Everything below was done by the author, one person. Nothing about time, cost, or quality was measured.

## Summary

- **One real team, about a month.** Since around 2026-10-20 the author has run one project with pilothouse: a team of rooms with PO, Dev, UX/UI, QA, team lead, and a writer room (a role the skill does not define). Roles, work orders, cross-room messages, handoff files, and room rotation were used day to day. One person, one project; no other users so far, and nothing was measured. The three checks added in 0.4.0 come from failures seen in the author's rooms: the merge check from this team, the other two from short setups on the author's other projects.

The rest were tried by the author once or twice each, mostly on toy repositories:

- A team lead turned a plain request into a work order, asked the owner one question, and the receiving room replied within tens of seconds.
- Told "merge it" by another room, a team lead refused and said the owner must confirm in the room that merges.
- Before printing starter prompts, the launch step looked at the repository, noticed an existing team, and asked whether to replace it or work beside it.
- A QA room asked to mark an untested build as passed objected once, with reasons, and offered a smaller test run instead. It did not write the disagreement into its handoff file: that run had no permission to write files.

Not tried yet: anyone else's team, a room writing a disagreement into its handoff file, a room creating other rooms through the skill, and the three checks from 0.4.0 as written. The ownership rules were in the skill during the month of real use, but how often rooms used them was not recorded.

## Starter prompts and launch

In one local run (2026-10-14, Windows, Claude app, five rooms), the skill looked at the repository before writing the prompts. It gave the new handoff files a prefix so they would not overwrite handoff files already there. It noticed that another team of rooms was already working in the repository, advised having those rooms write handoffs before any new room replaced them, and said that the run only printed prompts and changed no files or sessions. One run. Since 0.2.0 these steps are written into `references/launch.md` as instructions ("Before either path: look at the repository"), so the skill does them on purpose rather than by chance. The written form was run twice on toy repositories (2026-10-18) and did each step.

If the session can create sessions (for example a Claude Code cloud session), the skill instead checks for rooms with the same name, shows you a plan, waits for your confirmation, and then creates the rooms. **(untested)** In one test, a room created this way did not have the plugin installed in the room that created it; see [INSTALL.md](../INSTALL.md#cloud-sessions-and-local-sessions).

## Big features

Two parts go beyond what the author has done in practice and are marked **(untested)** in `references/prompt-translation.md`: the "pieces do not overlap" check before parallel work, and how often counts as "each major stage".

## Every part, tried or not

The workflow has been used day to day by the author on real projects, and with one project's team of rooms for about a month (from around 2026-10-20; one person, one project, nothing measured). The table says which parts have been tried and which have not. Untested steps are marked **(untested)** in the reference files. Most test results are from 2026-10-12 with Claude Code 2.1.296 on Linux. Rows dated 2026-10-14 come from one local run on Windows with the Claude app (Claude Code installed with npm, version not recorded). Rows dated 2026-10-18 come from headless runs (`claude -p`) on toy repositories, Linux, Claude Code 2.1.302. Each was a single run. All but the install from GitHub were made before the project was renamed; only the name has changed since.

| Part | Status |
|---|---|
| Creating rooms from a list (`launch.md`, path 1) | Untested. Printing starter prompts (path 2) needs no special tools; it worked once (2026-10-14, local, Windows). |
| Looking at the repository before printing prompts (existing handoff files, prefixed names, an existing team) | Seen once without instructions (2026-10-14, Windows). Written into `launch.md` in 0.2.0 and run twice as written (2026-10-18, headless, toy repositories): with an existing team it asked replace-or-beside before printing anything and chose prefixed handoff paths; with an empty repository it used the default paths and pointed out two names one letter apart. |
| `/pilothouse:pilothouse` in a session that started with the plugin already installed | The command loaded the skill in four headless runs (2026-10-18); in two of them the skill could not read its reference files (next row). |
| The skill reading its own reference files in a headless run (`claude -p`) with default permissions | Refused, both when installed from a local folder and when installed from GitHub (2026-10-18). The skill stopped and asked instead of guessing. Adding the plugin folder with `--add-dir` fixed it for the local-folder install; for a GitHub install, not tried. Interactive sessions: not checked. |
| Owning the work and pushing back (`roles.md`, 0.3.0) | In the skill during the month with one team; how often rooms used it was not recorded. One headless run (2026-10-18, toy repository): a QA room asked by the team lead to mark an untested build as passed could not read the reference files, worked from the core rule in `SKILL.md`, objected once with reasons, named the owner as the one who decides, and offered a smaller test run instead. It did not write its handoff file (no write permission in that run). |
| One project's team of rooms over about a month (PO, Dev, UX/UI, QA, team lead, and a writer room the skill does not define) | Used day to day by the author from around 2026-10-20: roles, work orders, cross-room messages, handoff files, and room rotation. One person, one project, Claude Code cloud sessions. No other users, and no time, cost, or quality figures were measured. |
| The three checks (0.4.0): plan before others build, "ready" means someone outside tried it, check the pull request at merge time | Each written from a failure seen in the author's rooms: the merge check with that team, the other two in short setups on other projects (a PO starting other rooms before the plan was agreed; work reported ready on passing end-to-end tests and then confusing the owner; a merge into the wrong base branch, and commits pushed during review left out of a squash merge). The rules as written: untested. |
| How quotes and commas arrive in the skill's arguments | Tried once through the skill (2026-10-14, Windows, Claude app): a list of five rooms was split correctly, names and roles were checked, and a name spelled two different ways was pointed out and used as typed. Exactly how the quotes arrived was not recorded. |
| Installing from a local clone (`marketplace add <path>`, `install pilothouse@pilothouse`) | Worked once in a cloud session (2026-10-12, v0.1.0) |
| Installing from GitHub (`marketplace add SuruchBoss/pilothouse`, `install pilothouse@pilothouse`) | Worked once (2026-10-12, after the rename, repository public): a cloud session with no repository attached and no token installed v0.1.0 and it showed as enabled. One run. |
| Using the skill in the session where it was installed | Does not work: "Unknown skill". Start a new session. Whether `/reload-plugins` avoids that: untested. |
| The command in the in-session menu | Seen once (2026-10-14, Windows, Claude app): `pilothouse:pilothouse` with its description |
| `claude plugin list` after `marketplace add` only | Empty, as expected: `plugin install` is a separate step (2026-10-14) |
| A room created by another room having the skill | It did not: the new room ran in its own container without the plugin. It followed `AGENTS.md` from the repository. Installing the skill before the room starts: untested. |
| A team lead turning a plain request into a work order and sending it | Tried once, with the rules read from the reference files rather than loaded through `/pilothouse:pilothouse`: the order had every field, the team lead asked the owner one question, and the receiving room replied within tens of seconds. The Authority field said "team lead proposal" on an order the owner had asked for, sent straight to Dev; the receiving room caught it, and `prompt-translation.md` now says to write the real source. |
| A team lead receiving "merge เลย" ("merge it") | Tried once (2026-10-12), with the words relayed by another room, not typed by the owner: no work order, nothing sent, no merge. It asked which pull request (repository and number) and said the owner must confirm in the room that merges. One run; not proof that it can never slip. |
| A room creating another room, then both messaging with no human present | Tried once in the author's environment and it worked (list sessions, message the parent, create a child that messaged back). One run, without the pilothouse skill loaded, permission mode auto. |
| Being woken by CI or review events after subscribing to a pull request | Untested; the subscription itself was made |
| Whether an old room keeps receiving messages after rotation | Untested; depends on the environment |
| Weekly room-health report by a scheduled routine | Tried once in the author's environment and it did not work: the routine's session had no session-listing tool and could not message other rooms. Run the check from a room that has those tools instead. |
| The coordinator opening rooms by itself | Untested; the skill asks the owner first |
| Cross-room memory with the layout in `references/memory.md` | The author's working method, but this multi-file layout has not been tested as written. One finding: a room working from a fresh clone could not see a `memory/index.md` that was not committed. Whether a new room reads the index at start: untested. |
| Translate, split, summarize with anyone else's rooms | Untested; it is the author's working method and has not been measured |
| Existing rooms messaging each other and replying | Observed working in the author's cloud sessions |
| Local sessions on one machine messaging each other | Untested. If they cannot, the owner carries messages between rooms. |
| `send_later` scheduling a message to the same room | Observed working once |

Tool names (`list_sessions`, `send_message`, `create_session`, `send_later`, `subscribe_pr_activity`) are those in the author's environment. They may differ in yours.

No performance or cost figures are claimed. None were measured.
