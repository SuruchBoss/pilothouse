# Changelog

## 0.2.0 (2026-10-18)

- `launch.md`: a new step, "Before either path: look at the repository". Before printing prompts or creating rooms, the skill looks for existing handoff files, picks handoff paths that do not overwrite them, points out a team already working in the repository, and says what the run changed. These behaviours were seen once without instructions (2026-10-14, Windows); the written version was run twice on toy repositories (2026-10-18, headless) and did each step.
- `launch.md`: two spellings of what looks like one room name are pointed out and used as typed; the note on how quotes arrive records the 2026-10-14 run.
- Starter prompts point to the repository's rules file when it has one.
- `AGENTS.md`: the same rule for agents without the skill, in four sentences.
- Every role: when it is unclear which piece of work or which room an instruction means, ask one question before starting, and send work to the room that owns it instead of doing it yourself (`SKILL.md`, `prompt-translation.md`, `coordinator.md`, `roles.md`, `AGENTS.md`). From a real case on 2026-10-18.
- README and README.th: the 2026-10-14 findings and the new step.
- README, INSTALL: in headless runs (`claude -p`) with default permissions the skill could not read its own reference files; the workaround and what is still untested are written down.

Nothing was removed from 0.1.0.

## 0.1.0 (2026-10-12)

First public release.
