# 07 · A big feature: in-app notifications

> Hypothetical example, adapted from the author's practice, details removed. Not a measured result.

## English

**Owner writes to the team lead:**

> I want notifications in the app, a bell in the top right, tap it and you see the list

**Step 1, clear enough?** One ambiguity changes the result a lot: inside the app only, or also pushed to phones? Push needs outside services and setup. The team lead asks one question:

> Inside the app only, or also as push notifications on phones?

> inside the app only for now

Other gaps (which events create a notification, read/unread) do not need a question. They go under Assumptions.

**Step 2, bigger than one ticket?** Yes: a design, data and API, and the screen. So the order goes to the PO to split; the team lead does not write the tickets.

**Step 5, new kind of order?** It is the first big-feature order for this project, so the team lead shows it to the owner first. The owner replies "ok, send it". That is enough here: sending a work order is not a merge, license, publish, spend, or delete.

**What the team lead sends to the PO:**

```
From: Team lead
Authority: owner asked at 10:15 and approved this order at 10:22,
      in this room
Goal: split "in-app notifications" into tickets and queue them:
      a bell in the top right, tapping it shows a list
Context and files: the project repository; current header and
      navigation screens. Suggested roles, in order: UX/UI (bell,
      list, empty state) → Dev → QA on the build you name → your
      review. The split and ticket contents are yours to decide.
Done when: the tickets are in the backlog with acceptance criteria,
      in order, each saying what it waits for
Do not: start implementation; put these ahead of work already queued
      without telling the team lead why
Send back: the ticket list and order, to the team lead
Assumptions:
  - inside the app only; no push to phones (owner confirmed)
  - which events create a notification: the PO proposes, the owner
    can correct
  - notifications have read and unread states
  - one ticket at a time; the owner did not ask for parallel work
```

**What the PO sends back** (shortened):

| Ticket | Room | Waits for |
|---|---|---|
| 1. Bell, list, and empty state design | UX/UI | nothing |
| 2. Store notifications, mark read/unread, list API | Dev | PO accepts the design in ticket 1 |
| 3. Bell and list on screen, using ticket 1's design and ticket 2's API | Dev | ticket 2 reviewed by the PO |
| then QA on the build the PO names, then PO review | QA, PO | ticket 3 |

The PO also proposes three events that create a notification and asks the owner to confirm them.

**Team lead's summary to the owner, after the split:**

> **Done:** the PO split the feature into three tickets: design, then data and API, then the screen. They run one at a time.
>
> **Needs you:** the PO proposes three events that create a notification. Confirm or change them in the PO room or here.
>
> **Waiting:** UX/UI starts the design. Nothing else starts until the PO accepts it.

**Later summaries** follow the same three parts at each major stage: design accepted, data and API reviewed, screen built and QA done. At the end the "Needs you" part says which pull requests are ready and that merging needs the owner's own words in the Dev room.

## ภาษาไทย

**เจ้าของพิมพ์ถึง team lead**

> อยากได้ระบบแจ้งเตือนในแอป มีกระดิ่งมุมขวาบน กดแล้วเห็นรายการ

**ขั้นที่ 1 ชัดพอไหม** มีจุดกำกวมหนึ่งจุดที่เปลี่ยนผลมาก คือแจ้งเตือนเฉพาะในแอป หรือส่งขึ้นมือถือด้วย การส่งขึ้นมือถือต้องใช้บริการภายนอกและต้องตั้งค่า team lead จึงถามหนึ่งคำถาม

> แจ้งเตือนเฉพาะในแอป หรือส่งขึ้นมือถือด้วย

> ในแอปอย่างเดียวก่อน

ช่องว่างอื่น (เหตุการณ์ไหนสร้างแจ้งเตือน, อ่านแล้ว/ยังไม่อ่าน) ไม่ต้องถาม ใส่ไว้ใน Assumptions

**ขั้นที่ 2 ใหญ่เกินใบเดียวไหม** ใช่ มีทั้งงานออกแบบ ข้อมูลกับ API และหน้าจอ ใบสั่งงานจึงส่งให้ PO แตกเอง team lead ไม่เขียนใบงานเอง

**ขั้นที่ 5 เป็นใบชนิดใหม่ไหม** เป็นใบฟีเจอร์ใหญ่ใบแรกของโปรเจกต์นี้ team lead จึงให้เจ้าของดูก่อน เจ้าของตอบ "ok ส่งได้" ซึ่งพอสำหรับเรื่องนี้ เพราะการส่งใบสั่งงานไม่ใช่การ merge ไลเซนส์ การเผยแพร่ การใช้เงิน หรือการลบ

**สิ่งที่ team lead ส่งถึง PO**

```
From: Team lead
Authority: เจ้าของขอในห้องนี้เวลา 10:15 และอนุมัติใบนี้เวลา 10:22
Goal: แตก "ระบบแจ้งเตือนในแอป" เป็นใบงานแล้วเข้าคิว: กระดิ่งมุมขวาบน
      กดแล้วเห็นรายการ
Context and files: repository ของโปรเจกต์; หน้า header และการนำทางปัจจุบัน
      บทบาทที่น่าจะต้องใช้ตามลำดับ (เสนอเท่านั้น): UX/UI (กระดิ่ง รายการ
      หน้าว่าง) → Dev → QA บน build ที่ PO ระบุ → PO ตรวจ
      การแตกงานและเนื้อหาใบงานเป็นการตัดสินของ PO
Done when: ใบงานอยู่ใน backlog พร้อมเกณฑ์ยอมรับ เรียงลำดับแล้ว
      และแต่ละใบบอกว่ารออะไร
Do not: เริ่มเขียนโค้ด; แทรกหน้างานที่เข้าคิวอยู่แล้วโดยไม่บอกเหตุผล team lead
Send back: รายการใบงานและลำดับ ส่ง team lead
Assumptions:
  - แจ้งเตือนเฉพาะในแอป ไม่ส่งขึ้นมือถือ (เจ้าของยืนยันแล้ว)
  - เหตุการณ์ไหนสร้างแจ้งเตือน: PO เสนอ เจ้าของแก้ได้
  - แจ้งเตือนมีสถานะอ่านแล้ว/ยังไม่อ่าน
  - ทำทีละใบ เจ้าของไม่ได้ขอให้ทำขนานกัน
```

**สิ่งที่ PO ส่งกลับ** (ย่อแล้ว)

| ใบงาน | ห้อง | รออะไร |
|---|---|---|
| 1. ออกแบบกระดิ่ง รายการ และหน้าว่าง | UX/UI | ไม่ต้องรอ |
| 2. เก็บแจ้งเตือน ทำเครื่องหมายอ่านแล้ว/ยังไม่อ่าน และ API รายการ | Dev | PO รับแบบในใบที่ 1 |
| 3. กระดิ่งและรายการบนหน้าจอ ตามแบบใบที่ 1 และ API ใบที่ 2 | Dev | PO ตรวจใบที่ 2 แล้ว |
| จากนั้น QA ทดสอบ build ที่ PO ระบุ แล้ว PO ตรวจ | QA, PO | ใบที่ 3 |

PO เสนอสามเหตุการณ์ที่สร้างแจ้งเตือน และขอให้เจ้าของยืนยัน

**สรุปที่ team lead ส่งให้เจ้าของหลังแตกงาน**

> **เสร็จแล้ว:** PO แตกฟีเจอร์เป็นสามใบ: ออกแบบ แล้วข้อมูลกับ API แล้วหน้าจอ ทำทีละใบ
>
> **ต้องให้คุณตัดสิน:** PO เสนอสามเหตุการณ์ที่สร้างแจ้งเตือน ยืนยันหรือแก้ได้ที่ห้อง PO หรือที่นี่
>
> **รออยู่:** UX/UI เริ่มออกแบบ ใบอื่นยังไม่เริ่มจนกว่า PO จะรับแบบ

**สรุปรอบต่อๆ ไป** ใช้สามส่วนเดิมทุกครั้งที่จบขั้นสำคัญ: รับแบบแล้ว ตรวจข้อมูลกับ API แล้ว ทำหน้าจอและ QA เสร็จ รอบสุดท้ายส่วน "ต้องให้คุณตัดสิน" จะบอกว่า pull request ไหนพร้อม และการ merge ต้องให้เจ้าของพิมพ์เองในห้อง Dev
