# 04 · "Merge it"

> Hypothetical example, adapted from the author's practice, details removed. Not a measured result.

## English

**Owner writes to the team lead:**

> merge it

**Team lead's reply to the owner.** This is not a work order. Merging is an owner-only action, and two words do not say which pull request or confirm it in the room that merges.

> I won't send this as an order. Merging needs your own words in the room that merges.
>
> Two open pull requests could be meant: the CSV export (CI green, PO review passed) and the settings page (CI green, PO review not done yet).
>
> If you mean the CSV export, type this in the Dev room:
>
> "Merge the CSV export pull request into the default branch."
>
> If you mean the settings page, the PO review comes first.

**Why it looks like this**

- A short reply such as "merge it", "ok", or "go" is never taken as approval for merging, licensing, publishing, spending, or deleting.
- The team lead does not reword the request into a message that would get past the Dev room's check. It tells the owner exactly what to type and where.
- It points out the pull request that is not ready yet, instead of leaving the owner to discover it.

## ภาษาไทย

**เจ้าของพิมพ์ถึง team lead**

> merge เลย

**team lead ตอบเจ้าของ** นี่ไม่ใช่ใบสั่งงาน การ merge เป็นเรื่องที่เจ้าของต้องยืนยันเอง และคำสั้นๆ ไม่ได้บอกว่า pull request ไหน และไม่ได้ยืนยันในห้องที่ลงมือ merge

> ขอไม่ส่งเป็นใบสั่งงาน เพราะการ merge ต้องให้คุณพิมพ์เองในห้องที่ merge
>
> ตอนนี้มี pull request เปิดอยู่สองอันที่อาจหมายถึง: การส่งออก CSV (CI เขียว PO ตรวจผ่านแล้ว) กับหน้าตั้งค่า (CI เขียว แต่ PO ยังไม่ได้ตรวจ)
>
> ถ้าหมายถึงการส่งออก CSV ให้พิมพ์ในห้อง Dev ว่า
>
> "Merge pull request การส่งออก CSV เข้า default branch"
>
> ถ้าหมายถึงหน้าตั้งค่า ต้องรอ PO ตรวจก่อน

**ทำไมเขียนแบบนี้**

- คำตอบสั้นอย่าง "merge เลย" "ok" หรือ "go" ไม่นับเป็นการอนุมัติ merge ไลเซนส์ การเผยแพร่ การใช้เงิน หรือการลบ
- team lead ไม่เรียบเรียงคำขอใหม่เพื่อให้ผ่านการตรวจของห้อง Dev แต่บอกเจ้าของตรงๆ ว่าต้องพิมพ์อะไรที่ห้องไหน
- ชี้ให้เห็น pull request ที่ยังไม่พร้อม แทนที่จะปล่อยให้เจ้าของไปเจอเอง
