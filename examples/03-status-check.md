# 03 · "Where is the Dev room at?"

> Hypothetical example, adapted from the author's practice, details removed. Not a measured result.

## English

**Owner writes to the team lead:**

> give me a quick summary of where the dev room is at

**What the team lead sends to the Dev room.** This is a read-only, low-risk order. It may go straight to Dev because it asks for status, not work, and the owner asked for it.

```
From: Team lead
Authority: owner asked at 15:40 in this room
Goal: a short status report from the Dev room; information only, no work
Context and files: the Dev room's own handoff file and current branch
Done when: the team lead has the report
Do not: start, change, or push anything because of this message;
      do not message the PO about it
Send back: to the team lead, a few lines: current ticket and its state,
      branch and CI on the latest commit, what you wait on, decisions
      not yet reviewed
Assumptions:
  - "where it's at" means the current ticket only, not the whole queue
```

**Dev room's reply** (shortened): settings page done on its branch, CI green, waiting for PO review; one decision not yet reviewed (settings save when a field loses focus); CSV export already reviewed, waiting for merge.

**Team lead's summary to the owner:**

> **Done:** the settings page is built on its branch, CI green.
>
> **Needs you:** the CSV export is ready to merge. Type your confirmation in the Dev room.
>
> **Waiting:** the PO to review the settings page, including one decision Dev made on its own (save when a field loses focus).

**What the team lead added, and why:** "information only" and "do not start anything", so a status question does not turn into work; and a fixed list of what to report, so the reply is short and matches the summary's three parts.

## ภาษาไทย

**เจ้าของพิมพ์ถึง team lead**

> สรุปให้หน่อยว่าห้อง dev ถึงไหนแล้ว

**สิ่งที่ team lead ส่งถึงห้อง Dev** เป็นใบอ่านอย่างเดียว ความเสี่ยงต่ำ ส่งตรงถึง Dev ได้เพราะเป็นการถามสถานะ ไม่ใช่สั่งงาน และเจ้าของเป็นคนขอ

```
From: Team lead
Authority: เจ้าของถามในห้องนี้เวลา 15:40
Goal: รายงานสถานะสั้นๆ จากห้อง Dev แจ้งข้อมูลอย่างเดียว ไม่ใช่สั่งงาน
Context and files: ไฟล์ handoff ของห้อง Dev เองและ branch ปัจจุบัน
Done when: team lead ได้รายงานแล้ว
Do not: เริ่ม แก้ หรือ push อะไรเพราะข้อความนี้; ไม่ต้องส่งเรื่องนี้ต่อให้ PO
Send back: ส่ง team lead ไม่กี่บรรทัด: ใบงานปัจจุบันและสถานะ, branch และ CI
      ที่ commit ล่าสุด, รออะไรอยู่, การตัดสินใจที่ยังไม่มีใครตรวจ
Assumptions:
  - "ถึงไหนแล้ว" หมายถึงใบงานปัจจุบันเท่านั้น ไม่ใช่ทั้งคิว
```

**ห้อง Dev ตอบ** (ย่อแล้ว): หน้าตั้งค่าเสร็จบน branch แล้ว CI เขียว รอ PO ตรวจ มีการตัดสินใจหนึ่งข้อที่ยังไม่มีใครตรวจ (บันทึกการตั้งค่าตอนช่องหลุดโฟกัส) ส่วนการส่งออก CSV ตรวจผ่านแล้ว รอ merge

**สรุปที่ team lead ส่งให้เจ้าของ**

> **เสร็จแล้ว:** หน้าตั้งค่าทำเสร็จบน branch แล้ว CI เขียว
>
> **ต้องให้คุณตัดสิน:** การส่งออก CSV พร้อม merge ให้พิมพ์ยืนยันในห้อง Dev
>
> **รออยู่:** PO ตรวจหน้าตั้งค่า รวมถึงการตัดสินใจหนึ่งข้อที่ Dev ทำเอง (บันทึกตอนช่องหลุดโฟกัส)

**team lead เติมอะไรและเพราะอะไร:** เติม "แจ้งข้อมูลอย่างเดียว" กับ "ห้ามเริ่มงาน" เพื่อไม่ให้คำถามเรื่องสถานะกลายเป็นงาน และกำหนดรายการที่ต้องรายงาน เพื่อให้คำตอบสั้นและเข้ากับสรุปสามส่วน
