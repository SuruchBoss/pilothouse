# 08 · A decision that outlasts the room

> Hypothetical example, adapted from the author's practice, details removed. Not a measured result.

## English

**Context:** in the PO room, the owner answers a question that has been waiting:

> empty cells in the export should stay blank, not 0. that's for every export, not just this one

**1. The PO room writes its own file.** It adds one row to `memory/po.md` and nothing else:

```markdown
| 2026-01-16 | Empty export cells stay blank, not 0 | Owner, PO room | owner decided |
```

It removes the matching row from "Waiting on the owner" in the same file, commits, pushes, and checks the remote:

```bash
git fetch origin main
git log origin/main..HEAD --oneline   # prints nothing, so the push landed
```

Only then does it reply "noted". It also tells the team lead: "New owner decision in `memory/po.md` that every room needs: empty cells stay blank in all exports."

**2. The team lead distills it into the index.** It copies the row into "Owner decisions in force" in `memory/index.md`, and removes the open question from "Waiting on the owner" there. The PO room does not edit the index itself.

**3. A month later, a new Dev room starts.** It reads `docs/handoff/dev.md`, then `memory/index.md`, sees the rule, and writes the new report export with blank cells without asking again. It does not open `memory/po.md` or the archive, because the index already says what it needs.

**What did not go into memory:** the ticket number, the pull request, and the test count for the export. Those are in the backlog and the pull request already.

## ภาษาไทย

**บริบท:** ในห้อง PO เจ้าของตอบคำถามที่ค้างอยู่

> ช่องว่างในไฟล์ส่งออกให้ปล่อยว่าง ไม่ต้องใส่ 0 ใช้กับทุกไฟล์ส่งออก ไม่ใช่แค่อันนี้

**1. ห้อง PO เขียนไฟล์ของตัวเอง** เพิ่มหนึ่งแถวใน `memory/po.md` ไม่แตะไฟล์อื่น

```markdown
| 2026-01-16 | ช่องว่างในไฟล์ส่งออกปล่อยว่าง ไม่เขียน 0 | เจ้าของ ห้อง PO | owner decided |
```

ลบแถวที่ตรงกันออกจาก "Waiting on the owner" ในไฟล์เดียวกัน commit push แล้วเช็กว่า remote มีจริง

```bash
git fetch origin main
git log origin/main..HEAD --oneline   # ไม่มีอะไรพิมพ์ออกมา แปลว่า push ขึ้นแล้ว
```

แล้วค่อยตอบว่า "จดแล้ว" จากนั้นบอก team lead ว่า "มีการตัดสินใหม่ของเจ้าของใน `memory/po.md` ที่ทุกห้องต้องรู้: ช่องว่างในไฟล์ส่งออกทุกไฟล์ปล่อยว่าง"

**2. team lead สรุปขึ้น index** คัดแถวนั้นไปไว้ใน "Owner decisions in force" ของ `memory/index.md` และลบคำถามที่ค้างออกจาก "Waiting on the owner" ในนั้น ห้อง PO ไม่แก้ index เอง

**3. หนึ่งเดือนต่อมา ห้อง Dev ห้องใหม่เริ่มงาน** อ่าน `docs/handoff/dev.md` แล้วอ่าน `memory/index.md` เห็นกติกานี้ จึงทำไฟล์ส่งออกรายงานใหม่ให้ช่องว่างปล่อยว่างโดยไม่ต้องถามซ้ำ ไม่ต้องเปิด `memory/po.md` หรือ archive เพราะ index บอกสิ่งที่ต้องรู้แล้ว

**สิ่งที่ไม่ได้จดลงความจำ:** เลขใบงาน pull request และจำนวนเทสต์ของงานส่งออก เพราะอยู่ใน backlog และ pull request อยู่แล้ว
