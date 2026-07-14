# ENGSE206 Two-Repository Operating Model
## รูปแบบการทำงานระหว่าง Course/Lab Repository และ Student Team Repository

รายวิชา ENGSE206 ใช้ repository สองประเภทที่มีหน้าที่ต่างกันอย่างชัดเจน

| Repository | เจ้าของ/ผู้ดูแล | ใช้ทำอะไร | นักศึกษาแก้ไขหรือไม่ |
|---|---|---|---|
| [`engse206-lab-v2`](https://github.com/se-rmutl/engse206-lab-v2) | อาจารย์ผู้สอน | แหล่งโจทย์ 10 cases, คำสั่งงานรายสัปดาห์, workshop, rubric, prompt pack และตัวอย่าง | **อ่านอย่างเดียว** |
| Repository ของแต่ละกลุ่มที่สร้างจาก [`engse206-project-template`](https://github.com/se-rmutl/engse206-project-template) | นักศึกษาแต่ละกลุ่ม | พื้นที่สร้างชิ้นงาน เก็บหลักฐาน บันทึกการมีส่วนร่วม และส่งงานต่อเนื่อง | **แก้ไขและส่งงานที่นี่** |

> กฎจำง่าย: **READ from Course Repo → WORK and SUBMIT in Team Repo**

## สิ่งที่ห้ามสับสน

1. นักศึกษาไม่ส่งงานโดย fork หรือแก้ไฟล์ใน Course Repo
2. ไม่คัดลอก Course Repo ทั้งชุดเข้า Team Repo
3. คัดลอกเฉพาะโจทย์/ข้อมูล case ที่ได้รับลง `CASE_CARD.md` และกรอกลิงก์ต้นทางไว้
4. คำสั่งงานล่าสุดใน Course Repo เป็น source of truth
5. ชิ้นงานใน Team Repo เป็น source of evidence สำหรับการตรวจคะแนน

## วงจรการทำงานประจำสัปดาห์

1. **READ** — เปิด `weeks/week-XX-.../README.md` ใน Course Repo
2. **CONFIRM** — ตรวจ Case ID, expected output, rubric, deadline และ assignment version
3. **PLAN** — สร้าง/อัปเดต Issue หรือ GitHub Project item และแบ่ง owner
4. **WORK** — แก้ไฟล์หลักใน `docs/`, `design/`, `diagrams/` หรือ `final/`
5. **EVIDENCE** — เก็บหลักฐานที่ `evidence/week-XX/` และบันทึก AI ใน `project-management/ai-use-log.md`
6. **REVIEW** — peer review / Tabletop Studio / instructor feedback
7. **SUBMIT** — กรอก `submissions/week-XX-submission.md`, commit และ push
8. **TRACK** — อัปเดต `submissions/submission-register.md`, `PROJECT_STATUS.md` และ worklog

## การเชื่อมโยง Case ตลอดภาคเรียน

- Case ID ถูกกำหนดใน Week 1 และใช้ต่อเนื่องถึง Week 16
- นักศึกษาคัดลอกข้อมูลตั้งต้นจาก Course Repo ลง `CASE_CARD.md`
- การตีความ ข้อค้นพบ requirement และ design ทั้งหมดเกิดใน Team Repo
- หากโจทย์หรือ scope เปลี่ยน ต้องบันทึกใน change/decision log และได้รับอนุมัติตามกติกา

## การอ้างอิงคำสั่งงานในไฟล์ส่ง

ทุก `submissions/week-XX-submission.md` ต้องมี

- Course assignment URL
- Case ID และ Case URL
- วันที่/commit ของ Course Repo ที่อ่าน
- path ของชิ้นงานใน Team Repo
- commit hash ฉบับส่ง
- สมาชิกและบทบาท
- รายการ feedback และสิ่งที่แก้ไข

## AI-Assisted Activities ใน Week 3–4

- Course Repo ให้ **prompt pack, role rules และสถานการณ์ควบคุม** ตามแต่ละ case
- Team Repo เก็บ **prompt ที่ใช้, transcript/summary, fact-opinion-assumption analysis และ human verification**
- AI เป็น stakeholder จำลอง ไม่ใช่แหล่งความจริงสูงสุด
- ห้ามใช้ AI สร้าง requirement ทั้งชุดโดยไม่มี evidence และการวิเคราะห์ของทีม
