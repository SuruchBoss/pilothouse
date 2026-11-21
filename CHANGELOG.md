# Changelog

## 0.4.0 (unreleased)

Three rules from about a month of use with one project's team of rooms. Each comes from a failure seen there. The rules as written are untested.

- **Plan before others build.** A room that hands out work does not tell other rooms to start building until the owner has confirmed the plan in their own words; connected rooms are not a confirmed plan. If the owner asked for a design or a decision first, only that is sent.
- **"Ready" means someone outside tried it.** No room calls work that outsiders will see ready until someone who has not seen the code or the plan has gone through the main path on the kind of device real users use. Passing end-to-end tests are not enough.
- **Check the pull request at merge time.** Whoever merges fetches, checks the base branch and the reviewed head commit, and after merging checks the branch for commits that arrived later.
- Where: the core of each rule in `SKILL.md` (so a room that cannot read the reference files still has it); details and the real cases in a new section of `roles.md`, "Three checks from real use"; role lines in `roles.md`; `coordinator.md`; `prompt-translation.md` (split step and "Watch out for"); starter prompts in `launch.md`; `AGENTS.md`.
- README and README.th: the evidence now describes the month of use with one team (one person, one project, nothing measured) instead of only toy repositories, and says what is still untested. README, README.th, INSTALL, INSTALL.th: say that the skill is written for and tried only with Claude Code, and that a room is one Claude Code session. A FAQ entry on other tools.

Nothing was removed from 0.3.0.

## 0.3.0 (2026-10-18)

- `roles.md`: a new section, "Owning the work and pushing back". Each room owns the professional quality of its own output, and each role has an **Owns** line with the questions it asks (PO: value, scope, acceptance criteria; Dev: correct, proven, readable; UX/UI: a real user can finish the task; QA: coverage and readiness for production).
- Pushing back: disagree once with reasons, record it in the handoff file, then follow the decision. Refuse only a step that cannot be undone or puts security at risk, until the owner confirms in their own words. The core is in `SKILL.md` as well, so a room that cannot read the reference files still has it.
- `handoff-template.md`: a "Disagreements recorded" section.
- `AGENTS.md`: the same rules for agents without the skill.
- README and README.th: a short note under the roles table and a row in the limits table. These rules have not been run with a team; one headless run of a QA room (2026-10-18) used the `SKILL.md` core rule as written, except that it could not write its handoff file.

Nothing was removed from 0.2.0.

## 0.2.0 (2026-10-18)

- `launch.md`: a new step, "Before either path: look at the repository". Before printing prompts or creating rooms, the skill looks for existing handoff files, picks handoff paths that do not overwrite them, points out a team already working in the repository, and says what the run changed. These behaviours were seen once without instructions (2026-10-14, Windows); the written version was run twice on toy repositories (2026-10-18, headless) and did each step.
- `launch.md`: two spellings of what looks like one room name are pointed out and used as typed; the note on how quotes arrive records the 2026-10-14 run.
- Starter prompts point to the repository's rules file when it has one.
- `AGENTS.md`: the same rule for agents without the skill, in four sentences.
- Every role: when it is unclear which piece of work or which room an instruction means, ask one question before starting, and send work to the room that owns it instead of doing it yourself (`SKILL.md`, `prompt-translation.md`, `coordinator.md`, `roles.md`, `AGENTS.md`). From a real case on 2026-10-18.
- README and README.th: the 2026-10-14 findings and the new step.
- README, INSTALL: in headless runs (`claude -p`) with default permissions the skill could not read its own reference files; the workaround and what is still untested are written down.

- Problems can be reported as GitHub issues; a short issue template asks for version, OS, install method, and session type.
- README: a link to Quick start near the top; checked again with Claude Code 2.1.302.

Nothing was removed from 0.1.0.

## 0.1.0 (2026-10-12)

First public release.
