# Examples / ตัวอย่าง

> **Hypothetical examples, adapted from the author's practice, details removed.** Project names, company names, people, branch names, commit hashes, and session IDs are replaced or removed. These are illustrations, not measured results.
>
> **ตัวอย่างสมมติ ดัดแปลงจากการใช้งานจริงของผู้เขียน ตัดรายละเอียดออกแล้ว** ชื่อโปรเจกต์ บริษัท บุคคล ชื่อ branch เลข commit และ session ID ถูกแทนหรือลบออก เป็นตัวอย่างประกอบ ไม่ใช่ผลการวัด

Each file has an English section and a Thai section. / แต่ละไฟล์มีทั้งภาษาอังกฤษและภาษาไทย

| File | Owner says | What the team lead does |
|---|---|---|
| [01-translate-request.md](01-translate-request.md) | "go through the code and merge the parts that repeat, and stay out of security and data validation" | Writes a full work order for the PO, with assumptions |
| [02-relay-to-po.md](02-relay-to-po.md) | "pass it to the PO" (after Dev reports) | Writes a relay order that stands on its own |
| [03-status-check.md](03-status-check.md) | "give me a quick summary of where the dev room is at" | Sends a read-only status request to Dev, then summarizes |
| [04-merge-request.md](04-merge-request.md) | "merge it" | Does not send an order; asks which pull request and names the room to confirm in |
| [05-summary.md](05-summary.md) | (answers arrive from three rooms) | Summarizes as Done / Needs you / Waiting |
| [06-handoff-before-rotation.md](06-handoff-before-rotation.md) | "this room is getting big" | Writes the handoff file before rotating |
| [07-big-feature.md](07-big-feature.md) | "notifications in the app, a bell in the top right" | Asks one question, sends a split order to the PO, summarizes after the split |
| [08-memory.md](08-memory.md) | "empty cells stay blank in every export" | The PO writes its own memory file; the team lead copies it into the index; a later Dev room follows it |

Rules behind these examples: [`references/prompt-translation.md`](../plugins/pilothouse/skills/pilothouse/references/prompt-translation.md), [`references/messaging.md`](../plugins/pilothouse/skills/pilothouse/references/messaging.md), [`references/handoff-template.md`](../plugins/pilothouse/skills/pilothouse/references/handoff-template.md), [`references/rotation.md`](../plugins/pilothouse/skills/pilothouse/references/rotation.md).

The same examples, shortened, appear in the README sections "What you type → what the team lead sends" and "Big features".
