# 06 · Handoff before rotating a room

> Hypothetical example, adapted from the author's practice, details removed. Not a measured result.

## English

**Owner tells the Dev room:**

> this room is getting big, let's move to a new one

The Dev room parks its work, writes `docs/handoff/dev.md` (overwriting the old one), pushes it, checks the remote has it, then gives the owner one line to start the new room. It does not clear or replace itself.

```markdown
# Dev handoff

Updated: 2026-01-15 17:40 UTC+7 by Dev room

## Current work
- Settings page ticket: implemented, waiting for PO review
  (branch `feature/settings-page`, last commit `<sha>`)

## Waiting on
- PO room: review of the settings page; the PO will message the Dev room
- PO room: next ticket to be queued

## Next
1. Address the PO's review of the settings page, if any
2. Take the next ticket the PO queues

## Decisions made in this role, not yet reviewed
- Settings are saved when the field loses focus, not on every keystroke:
  avoids a save per character

## Do not
- Do not merge `feature/settings-page`: needs the owner's own words in this room
- Do not change the CSV export: it passed review and waits for merge

## How to verify the current state
- `git log -1 origin/feature/settings-page` shows `<sha>`
- CI on that commit is green
```

**Line for the owner to start the new room:**

```
You are the Dev room for <repo>. Read docs/handoff/dev.md first,
check it against the repository, and report any mismatch before
doing anything else.
```

## ภาษาไทย

**เจ้าของบอกห้อง Dev**

> ห้องนี้ใหญ่แล้ว ย้ายไปห้องใหม่กันเถอะ

ห้อง Dev พักงานไว้ เขียน `docs/handoff/dev.md` ทับไฟล์เดิม push แล้วเช็กว่า remote มีไฟล์นั้นจริง จากนั้นให้เจ้าของหนึ่งบรรทัดสำหรับเปิดห้องใหม่ ห้องไม่ล้างหรือแทนที่ตัวเองเอง

```markdown
# Dev handoff

Updated: 2026-01-15 17:40 UTC+7 by Dev room

## Current work
- ใบงานหน้าตั้งค่า: ทำเสร็จแล้ว รอ PO ตรวจ
  (branch `feature/settings-page`, commit ล่าสุด `<sha>`)

## Waiting on
- ห้อง PO: ตรวจหน้าตั้งค่า PO จะส่งข้อความมาที่ห้อง Dev
- ห้อง PO: เข้าคิวใบงานถัดไป

## Next
1. แก้ตามผลตรวจหน้าตั้งค่าของ PO ถ้ามี
2. หยิบใบงานถัดไปที่ PO เข้าคิว

## Decisions made in this role, not yet reviewed
- บันทึกการตั้งค่าตอนช่องหลุดโฟกัส ไม่บันทึกทุกครั้งที่พิมพ์
  เพื่อไม่ให้บันทึกทุกตัวอักษร

## Do not
- ห้าม merge `feature/settings-page` ต้องให้เจ้าของพิมพ์เองในห้องนี้
- ห้ามแก้การส่งออก CSV เพราะตรวจผ่านแล้วและรอ merge

## How to verify the current state
- `git log -1 origin/feature/settings-page` แสดง `<sha>`
- CI บน commit นั้นเขียว
```

**บรรทัดที่เจ้าของใช้เปิดห้องใหม่**

```
You are the Dev room for <repo>. Read docs/handoff/dev.md first,
check it against the repository, and report any mismatch before
doing anything else.
```
