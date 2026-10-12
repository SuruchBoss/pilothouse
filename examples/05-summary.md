# 05 · Three rooms' answers → one summary

> Hypothetical example, adapted from the author's practice, details removed. Not a measured result.

## English

**What arrived at the team lead** (shortened):

- **PO:** CSV export reviewed against the ticket, passes. Accepted Dev's date format. Wants the owner to decide whether empty cells stay empty or show 0, because customers will see it.
- **Dev:** settings page pushed on its branch, CI green. Blocked on the next ticket until the PO queues it.
- **QA:** tested the CSV export on the commit the PO named. All four acceptance criteria pass. Could not test the settings page: no build named yet.

**Team lead's summary to the owner:**

> **Done:** CSV export passed PO review and QA (all four criteria), CI green. It is ready to merge.
>
> **Needs you:**
> 1. Empty cells in the CSV: leave them empty, or write 0? The PO asks because customers will see it.
> 2. Merging the CSV export. Type your confirmation in the Dev room.
>
> **Waiting:** the PO to review the settings page and name a build for QA. Dev waits for the PO to queue its next ticket.

**Why it looks like this**

- Three parts, in the order the owner acts on them. Details the owner does not decide on (which tests were added, the date format the PO already accepted) are left out.
- Each confirmation says where to type it.
- Nothing failed this round. If something had, it would come first, before the good news.

## ภาษาไทย

**สิ่งที่ team lead ได้รับ** (ย่อแล้ว)

- **PO:** ตรวจการส่งออก CSV เทียบใบงานแล้ว ผ่าน รับรูปแบบวันที่ที่ Dev เลือก อยากให้เจ้าของตัดสินว่าช่องว่างจะปล่อยว่างหรือแสดง 0 เพราะลูกค้าจะเห็น
- **Dev:** push หน้าตั้งค่าขึ้น branch แล้ว CI เขียว รอใบถัดไปจนกว่า PO จะเข้าคิว
- **QA:** ทดสอบการส่งออก CSV บน commit ที่ PO ระบุ ผ่านเกณฑ์ยอมรับทั้งสี่ข้อ ยังทดสอบหน้าตั้งค่าไม่ได้ เพราะยังไม่มีใครระบุ build

**สรุปที่ team lead ส่งให้เจ้าของ**

> **เสร็จแล้ว:** การส่งออก CSV ผ่านการตรวจของ PO และ QA (ครบทั้งสี่เกณฑ์) CI เขียว พร้อม merge
>
> **ต้องให้คุณตัดสิน:**
> 1. ช่องว่างใน CSV ปล่อยว่างหรือเขียน 0 PO ถามเพราะลูกค้าจะเห็น
> 2. merge การส่งออก CSV ให้พิมพ์ยืนยันในห้อง Dev
>
> **รออยู่:** PO ตรวจหน้าตั้งค่าและระบุ build ให้ QA ส่วน Dev รอ PO เข้าคิวใบถัดไป

**ทำไมเขียนแบบนี้**

- สามส่วน เรียงตามลำดับที่เจ้าของต้องทำ ตัดรายละเอียดที่เจ้าของไม่ต้องตัดสิน (เทสต์ที่เพิ่ม รูปแบบวันที่ที่ PO รับแล้ว)
- ทุกเรื่องที่ต้องยืนยันบอกว่าต้องพิมพ์ที่ห้องไหน
- รอบนี้ไม่มีอะไรล้ม ถ้ามี ให้บอกก่อนข่าวดี
