# 02 · "Pass it to the PO"

> Hypothetical example, adapted from the author's practice, details removed. Not a measured result.

## English

**Context:** the Dev room reported to the owner that the "export report as CSV" ticket is done. The owner tells the team lead:

> pass it to the PO

**What the team lead sends to the PO room.** The PO has none of the Dev room's context, so the order carries what the PO needs:

```
From: Team lead
Authority: owner said "pass it to the PO" at 16:20 in this room
Goal: the PO reviews the Dev result for "export report as CSV" against
      the ticket's acceptance criteria, and decides two open points
Context and files: branch feature/csv-export, pushed, CI green on the
      latest commit; new tests for the export, existing tests unchanged.
      Decisions Dev made that the ticket did not cover:
        1. dates are written as YYYY-MM-DD
        2. empty cells are left empty, not written as 0
Done when: the PO has sent its review result to the Dev room and has
      accepted or changed both decisions
Do not: merge; reorder the queue; start the next ticket in Dev before
      the review is done
Send back: review result to the Dev room; to the team lead only what
      needs the owner
Assumptions:
  - "pass it to the PO" means for review, not for merging
  - the owner has not decided the two open points; the PO may decide
    them or send them back to the owner
```

**What the team lead added, and why:** the branch, CI state, and Dev's two unreviewed decisions, because the PO cannot see the Dev room; and "do not merge", because merging needs the owner's own words in the room that merges.

## ภาษาไทย

**บริบท:** ห้อง Dev รายงานเจ้าของว่าใบงาน "ส่งออกรายงานเป็น CSV" เสร็จแล้ว เจ้าของบอก team lead ว่า

> ส่งต่อให้ PO ได้เลย

**สิ่งที่ team lead ส่งถึงห้อง PO** ห้อง PO ไม่มี context ของห้อง Dev ใบสั่งงานจึงต้องมีสิ่งที่ PO ต้องใช้ครบ

```
From: Team lead
Authority: เจ้าของพิมพ์ "ส่งต่อให้ PO ได้เลย" ในห้องนี้เวลา 16:20
Goal: PO ตรวจผลของ Dev สำหรับ "ส่งออกรายงานเป็น CSV" เทียบกับเกณฑ์ยอมรับ
      ของใบงาน และตัดสินสองเรื่องที่ค้าง
Context and files: branch feature/csv-export push แล้ว CI เขียวที่ commit
      ล่าสุด มีเทสต์ใหม่ของการส่งออก เทสต์เดิมไม่ได้แก้
      สิ่งที่ Dev ตัดสินเองซึ่งใบงานไม่ได้ระบุ:
        1. วันที่เขียนเป็น YYYY-MM-DD
        2. ช่องว่างปล่อยว่าง ไม่เขียนเป็น 0
Done when: PO ส่งผลตรวจให้ห้อง Dev แล้ว และรับหรือเปลี่ยน
      การตัดสินใจทั้งสองข้อแล้ว
Do not: merge; เปลี่ยนลำดับคิว; ให้ Dev เริ่มใบถัดไปก่อนตรวจเสร็จ
Send back: ผลตรวจส่งห้อง Dev; ส่ง team lead เฉพาะเรื่องที่ต้องให้เจ้าของตัดสิน
Assumptions:
  - "ส่งต่อให้ PO" หมายถึงส่งให้ตรวจ ไม่ใช่ให้ merge
  - เจ้าของยังไม่ได้ตัดสินสองเรื่องที่ค้าง PO ตัดสินเองได้
    หรือส่งกลับมาให้เจ้าของ
```

**team lead เติมอะไรและเพราะอะไร:** เติม branch สถานะ CI และการตัดสินใจสองข้อของ Dev ที่ยังไม่มีใครตรวจ เพราะ PO มองไม่เห็นห้อง Dev และเติม "ห้าม merge" เพราะการ merge ต้องให้เจ้าของพิมพ์เองในห้องที่ merge
