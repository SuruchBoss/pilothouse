# ติดตั้ง pilothouse

[English](INSTALL.md)

pilothouse เป็น skill ของ **Claude Code** ขั้นตอนข้างล่างรันจริงกับ Claude Code **2.1.296** บน Linux เวอร์ชันอื่นและระบบปฏิบัติการอื่นยังไม่ได้ตรวจ ไม่ได้อ้างว่าใช้กับเอเจนต์หรือเครื่องมืออื่นได้ สำหรับเอเจนต์ที่อ่านแค่ไฟล์กฎ มี [AGENTS.md](AGENTS.md) เป็นฉบับข้อความสั้นที่ไม่มีคำสั่งของ skill **(ยังไม่ได้ทดสอบกับเอเจนต์ใด)**

## ทางที่ 1: ติดตั้งจาก marketplace (แนะนำ)

```bash
claude plugin marketplace add SuruchBoss/pilothouse
claude plugin install pilothouse@pilothouse
```

เช็กว่าติดตั้งสำเร็จ

```bash
claude plugin list
claude plugin details pilothouse@pilothouse
```

`list` จะแสดง `pilothouse@pilothouse` สถานะ enabled ส่วน `details` จะแสดง skill หนึ่งตัวชื่อ `pilothouse` ไม่มี hook, agent หรือ MCP server

เปิด session ใหม่เพื่อให้ skill โหลด skill ที่ติดตั้งระหว่าง session ใช้ใน session เดิมไม่ได้ ในการทดสอบครั้งหนึ่ง (12 ต.ค. 2026) เรียกใน session เดิมแล้วได้ "Unknown skill" ใน session ใหม่ คำสั่งคือ `/pilothouse:pilothouse` พิมพ์ `/pilothouse` เฉยๆ ก็ได้ถ้าไม่มีคำสั่งอื่นใช้ชื่อนี้ การเห็นคำสั่งในเมนูภายใน session **ยังไม่ได้ตรวจ (untested)**

อัปเดตภายหลัง

```bash
claude plugin marketplace update pilothouse
claude plugin update pilothouse@pilothouse
```

## ทางที่ 2: คัดลอกโฟลเดอร์ skill เอง

คัดลอก `plugins/pilothouse/skills/pilothouse/` ไปไว้ที่ใดที่หนึ่ง

- `~/.claude/skills/pilothouse/` ใช้กับทุกโปรเจกต์ของคุณ หรือ
- `<repository ของคุณ>/.claude/skills/pilothouse/` ใช้กับโปรเจกต์เดียว (และทุกคนที่ clone ไป)

เช็กว่าโฟลเดอร์ถูกรูปแบบ

```bash
claude plugin validate ~/.claude/skills
```

skill ที่คัดลอกเองจะไม่ขึ้นใน `claude plugin list` เพราะไม่ใช่ plugin คำสั่งคือ `/pilothouse` การโหลดใน session **ยังไม่ได้ตรวจ (untested)**

## session บนคลาวด์ กับ session ในเครื่อง

| | session ในเครื่อง | session บนคลาวด์ |
|---|---|---|
| บทบาท ไฟล์ handoff การหมุนห้อง | ใช้ได้เหมือนกัน | ใช้ได้เหมือนกัน |
| `/pilothouse:pilothouse "name" role, ...` | พิมพ์ prompt เริ่มต้นของแต่ละห้องให้คัดลอกไปเปิด session ใหม่เอง | ถ้า session มีเครื่องมือสร้าง session skill จะสร้างห้องให้หลังเจ้าของยืนยันแผน **(ยังไม่ได้ทดสอบ)** ถ้าไม่มีจะพิมพ์ prompt เริ่มต้นแทน |
| ข้อความข้ามห้อง | ขึ้นกับเครื่องมือที่ระบบของคุณมี | ใน session บนคลาวด์ของผู้เขียน ห้องที่มีอยู่แล้วส่งข้อความหากันได้ ชื่อเครื่องมือของคุณอาจต่างไป |
| การติดตั้ง | ทางที่ 1 หรือ 2 | ทางที่ 2 ใน repository (`.claude/skills/`) ติดไปกับการ clone แต่จะโหลดหรือไม่ **ยังไม่ได้ตรวจ (untested)** ทางที่ 1 จาก clone ในเครื่อง (`claude plugin marketplace add <path>` แล้ว `claude plugin install pilothouse@pilothouse`) ทำได้หนึ่งครั้งใน session บนคลาวด์ (12 ต.ค. 2026) ส่วนการเพิ่มด้วยชื่อบน GitHub (`claude plugin marketplace add SuruchBoss/pilothouse`) ทำได้หนึ่งครั้งใน session บนคลาวด์ที่ไม่ได้ผูก repository และไม่ใช้ token (12 ต.ค. 2026) |
| ห้องที่อีกห้องสร้างให้ | ไม่เกี่ยว | ในการทดสอบครั้งหนึ่ง ห้องใหม่อยู่คนละ container และไม่มี plugin ที่ติดตั้งในห้องที่สร้างมัน ห้องนั้นทำตาม `AGENTS.md` ใน repository ถ้าอยากให้มี skill ต้องมี skill อยู่ก่อนห้องเริ่ม การทำผ่าน setup ของสภาพแวดล้อมยังไม่ได้ลอง **(untested)** |

ถ้าไม่แน่ใจว่า session ของคุณทำอะไรได้บ้าง ให้ใช้ prompt เริ่มต้นที่ skill พิมพ์ให้ ทางนี้ไม่ต้องใช้เครื่องมือพิเศษ

## ถอนการติดตั้ง

ติดตั้งจาก marketplace

```bash
claude plugin uninstall pilothouse@pilothouse
claude plugin marketplace remove pilothouse
```

คัดลอกโฟลเดอร์เอง: ลบโฟลเดอร์ `pilothouse` ที่คัดลอกไว้

## ปัญหาที่อาจเจอ

| อาการ | สาเหตุที่น่าจะเป็น | ลองทำ |
|---|---|---|
| `/pilothouse` ไปเรียกคำสั่งอื่น | มีคำสั่งอื่นใช้ชื่อนี้อยู่แล้ว | ใช้ `/pilothouse:pilothouse` |
| ได้ `Unknown skill` หรือ skill ไม่โหลดหลังติดตั้ง | skill โหลดตอนเริ่ม session และ session นี้เปิดก่อนติดตั้ง | เปิด session ใหม่ |
| ห้องที่อีกห้องสร้างให้ใช้ `/pilothouse:pilothouse` ไม่ได้ | ห้องนั้นเริ่มโดยไม่มี plugin และอยู่คนละ container | ใช้ `AGENTS.md` ใน repository หรือติดตั้ง skill ก่อนห้องเริ่ม **(untested)** |
| hook commit หรือ push ไฟล์ที่สร้างไว้ตอนทดสอบ | บางระบบมี hook ที่ commit ไฟล์ untracked ตอนห้องหยุด | ใส่ไฟล์เหล่านั้นใน `.git/info/exclude` git จะไม่สนใจไฟล์โดยไม่ต้องแก้ repository |
| `/pilothouse:pilothouse "a" dev, "b" qa` หยุดถาม | สะกดบทบาทผิด ชื่อห้องซ้ำ หรือไม่ได้ใส่บทบาท | แก้รายการ บทบาทคือ `teamlead`, `po`, `dev`, `uxui`, `qa`, `coordinator` |
| ห้องไม่ยอม merge หรือแก้ไลเซนส์ตามข้อความจากห้องอื่น | ต้องการคำพูดของเจ้าของเองในห้องนั้น ตั้งใจออกแบบไว้แบบนี้ | พิมพ์ยืนยันในห้องนั้นเอง |
| ห้องไม่ตื่นเมื่อ CI เสร็จหรือห้องอื่นตอบ | event จากภายนอกส่วนใหญ่ไม่ปลุกห้องเอง | ให้ห้อง subscribe หรือตั้งเวลากลับมาเช็ก หรือบอกห้องเอง **(ยังไม่ได้ทดสอบในภาพรวม)** |
| `claude plugin marketplace add` ล้มเหลว | เครื่องเข้า network หรือ GitHub ไม่ได้ | clone repository มาแล้วรัน `claude plugin marketplace add <path ของ clone>` |

## ลบสิ่งที่ skill สร้างไว้

ตอนติดตั้ง skill ไม่เขียนไฟล์อะไร แต่ห้องที่ใช้ skill อาจสร้างไฟล์ handoff (เช่น `docs/handoff/dev.md`) และดัชนีห้องใน repository ของคุณ ไฟล์เหล่านี้เป็นไฟล์ธรรมดา ลบได้ถ้าเลิกใช้ skill
