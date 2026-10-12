# 01 · Plain words → work order

> Hypothetical example, adapted from the author's practice, details removed. Not a measured result.

## English

**Owner writes to the team lead:**

> go through the code and merge the parts that repeat, and stay out of security and data validation

**Team lead's work order, sent to the PO** (not to Dev: the PO owns the queue):

```
From: Team lead
Authority: owner said at 14:05 in this room
Goal: a ticket to find duplicated code and consolidate it into shared
      functions, without changing behavior
Context and files: the project repository, default branch; existing
      tests; the security and input-validation modules (to exclude)
Done when: the PO has a ticket in the backlog whose acceptance criteria
      include: no behavior change; all existing tests pass; no file in
      the security or input-validation modules is changed; each
      consolidation is listed with before/after locations
Do not: start implementation; reorder the queue; touch security or
      input-validation code
Send back: ticket link and its place in the queue, to the team lead
Assumptions:
  - "data validation" means input validation (checking what users or
    other systems send in), not data checks inside reports
  - "the code" means application code, not tests or generated files
  - "merge the parts that repeat" means consolidate duplicates into
    shared code, not merge branches
  - one ticket; the PO may split it if it is large
```

**Why it looks like this**

- Nothing the owner did not say was added. "No behavior change" and "tests pass" follow from "merge the parts that repeat" without adding scope.
- Each place the team lead had to guess is under Assumptions, so the owner can correct it in one line.
- Only one question would have been allowed. None was needed: every ambiguity had an obvious reading that the owner can see and fix.

## ภาษาไทย

**เจ้าของพิมพ์ถึง team lead**

> ช่วยไล่ตรวจโค้ดแล้วยุบส่วนที่ซ้ำกันให้หน่อย อย่าไปยุ่งเรื่องความปลอดภัยกับการตรวจข้อมูล

**ใบสั่งงานที่ team lead ส่งให้ PO** (ไม่ส่งตรงถึง Dev เพราะ PO เป็นเจ้าของคิว)

```
From: Team lead
Authority: เจ้าของพิมพ์ในห้องนี้เวลา 14:05
Goal: ใบงานสำหรับหาโค้ดที่ซ้ำกันแล้วยุบรวมเป็นฟังก์ชันที่ใช้ร่วมกัน
      โดยพฤติกรรมของโปรแกรมไม่เปลี่ยน
Context and files: repository ของโปรเจกต์ บน default branch; เทสต์ที่มีอยู่;
      โมดูลความปลอดภัยและโมดูลตรวจข้อมูลขาเข้า (ไว้ยกเว้น)
Done when: PO มีใบงานใน backlog ที่เกณฑ์ยอมรับมี: พฤติกรรมไม่เปลี่ยน;
      เทสต์เดิมผ่านทั้งหมด; ไม่มีไฟล์ในโมดูลความปลอดภัยหรือตรวจข้อมูลขาเข้า
      ถูกแก้; ทุกจุดที่ยุบรวมมีรายการตำแหน่งก่อนและหลัง
Do not: เริ่มลงมือเขียนโค้ด; เปลี่ยนลำดับคิว; แตะโค้ดความปลอดภัยหรือ
      การตรวจข้อมูลขาเข้า
Send back: ลิงก์ใบงานและลำดับในคิว ส่งกลับ team lead
Assumptions:
  - "การตรวจข้อมูล" หมายถึงการตรวจข้อมูลขาเข้า (สิ่งที่ผู้ใช้หรือระบบอื่น
    ส่งเข้ามา) ไม่ใช่การตรวจข้อมูลในรายงาน
  - "โค้ด" หมายถึงโค้ดของแอป ไม่รวมเทสต์หรือไฟล์ที่สร้างอัตโนมัติ
  - "ยุบส่วนที่ซ้ำ" หมายถึงรวมโค้ดซ้ำเป็นโค้ดที่ใช้ร่วมกัน ไม่ใช่ merge branch
  - ใบงานเดียว PO แตกเป็นหลายใบได้ถ้างานใหญ่
```

**ทำไมเขียนแบบนี้**

- ไม่เพิ่มสิ่งที่เจ้าของไม่ได้พูด "พฤติกรรมไม่เปลี่ยน" กับ "เทสต์ผ่าน" ตามมาจากคำว่า "ยุบส่วนที่ซ้ำกัน" เอง ไม่ได้ขยายขอบเขต
- ทุกจุดที่ team lead ต้องเดาอยู่ใน Assumptions เจ้าของแก้ได้ในบรรทัดเดียว
- ถามได้ไม่เกินหนึ่งคำถาม รอบนี้ไม่ต้องถาม เพราะทุกจุดกำกวมมีความหมายที่ชัดพอและเจ้าของเห็นแล้วแก้ได้
