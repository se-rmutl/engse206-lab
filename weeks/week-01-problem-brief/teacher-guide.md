# คู่มืออาจารย์: Week 1 — Problem Brief Kick-off

## จุดประสงค์
หลังจบ Week 1 นักศึกษาต้องเข้าใจว่า **โจทย์ปัญหาไม่ใช่รายการฟีเจอร์** และสามารถจัดทำ Problem Brief v0.1 ที่ประกอบด้วย facts, pain points, stakeholders, goals, scope, starter requirements, NFR concerns และ open questions ได้

## ก่อนเริ่มคาบ

1. แบ่งกลุ่ม 3–4 คน และบันทึกชื่อใน [Case Assignment Sheet](../../cases/case-assignment-sheet.md)
2. แจก Case Card กลุ่มละ 1 เรื่องจาก [Case Project ทั้ง 10 เรื่อง](../../cases/README.md)
3. สร้าง repo กลุ่มจาก [Student Starter Repository](../../student-repo-starter/README.md)
4. เปิดภาพ [Week 1 Workflow](assets/week01-workflow.png) และ [OS & Submission Guide](assets/week01-os-submission.png)
5. เปิด [ตัวอย่างงานที่ทำเสร็จแล้ว](sample-completed/README.md) เพื่อให้เห็นรูปแบบ แต่ย้ำว่าไม่ให้คัดลอกเนื้อหา

## Run Sheet ทฤษฎี 2 ชั่วโมง

| เวลา | กิจกรรม | จุดเน้น |
|---:|---|---|
| 0–15 | เปิดรายวิชาและผลลัพธ์ปลายภาค | Requirement-to-Design Package |
| 15–35 | เชื่อม ENGSE203/204/205 สู่ ENGSE206 | เขียนโปรแกรมเก่งไม่พอ ต้องเข้าใจสิ่งที่ต้องสร้าง |
| 35–65 | Mini lecture | problem, requirement, specification, design, implementation |
| 65–85 | Think-pair-share | ดึงผู้เรียนออกจากการพูดเป็นฟีเจอร์ทันที |
| 85–100 | สรุป artefact ตลอดเทอม | Problem Brief → SRS → Design → Review |
| 100–120 | อธิบาย Case Card/Git/เกณฑ์ | facts vs assumptions, scope, evidence |

## Run Sheet Workshop 3 ชั่วโมง

| เวลา | กิจกรรม | ผลลัพธ์/หลักฐาน |
|---:|---|---|
| 0–15 | อ่าน Case Card และตั้งชื่อโครงการ | Team profile |
| 15–40 | ระดม facts, observations, assumptions | Facts list |
| 40–65 | ระบุ stakeholder และ pain points | Stakeholder list + pain points |
| 65–90 | อธิบายเป้าหมายและ success indicator | Goals |
| 90–100 | พัก | - |
| 100–130 | กำหนด in scope / out of scope / constraints | Scope statement |
| 130–155 | ร่าง starter requirements 5 ข้อ + NFR 3 ข้อ | Requirement table |
| 155–170 | ระบุ open questions สำหรับ Week 3–4 | Open questions |
| 170–180 | Peer check, exit ticket, commit/push | Repo URL / commit |

## วิธี Facilitate

- เมื่อทีมพูดว่า “ระบบต้องมีหน้า login” ให้ถามว่า “ใครเป็นผู้ใช้ เหตุใดต้องยืนยันตัวตน และอะไรคือความเสี่ยงถ้าไม่ login”
- เมื่อทีมเสนอฟีเจอร์จำนวนมาก ให้ถามว่า “อะไรแก้ pain point หลักจริง และอะไรตัดออกได้ใน version แรก”
- เมื่อทีมบอกว่า “ผู้ใช้ต้องการ...” ให้ถามว่า “หลักฐานมาจาก Case Card, observation หรือข้อสมมติของเรา”
- เมื่อเกิดข้อโต้แย้ง ให้ใช้คำว่า “open question” แทนการรีบตัดสินว่าใครถูก

## Week 4 Simulation Preparation
ข้อมูลใน Case Card เพียงพอสำหรับ Week 1–3 ส่วน Week 4 ผู้สอนควรเพิ่มข้อมูล role-specific, conflict และสถานการณ์เปลี่ยนแปลง เพื่อให้ทีมฝึกสัมภาษณ์และต่อรองจริง

## การประเมิน Week 1

| ส่วน | คะแนน | วิธีตรวจ |
|---|---:|---|
| Problem Brief v0.1 ของกลุ่ม | 4 | ความครบ ความชัด เหตุผล ความพอดีของ scope |
| Individual Exit Ticket | 1 | แยก problem/requirement/design และระบุคำถามที่จะค้นต่อ |

## Exit Ticket ตัวอย่าง
1. ยกตัวอย่างจาก Case ของกลุ่มที่เป็น **problem** และ 1 ข้อที่เป็น **requirement**
2. สิ่งใดใน Problem Brief ยังเป็น assumption
3. หากเก็บข้อมูลเพิ่ม ทีมจะถาม stakeholder คนใดก่อน และเพราะเหตุใด

## Checklist ก่อนจบคาบ
- [ ] ทุกกลุ่มมี Case Card
- [ ] ทุกกลุ่มมี repository และสมาชิกเข้าถึงได้
- [ ] ทุกกลุ่มมี Problem Brief v0.1 อย่างน้อย 1 commit
- [ ] ทุกคนส่ง exit ticket
- [ ] อาจารย์บันทึก feedback 1–2 ข้อต่อกลุ่มสำหรับ Week 2
