# Assignment Contract — Week 11

> **ข้อเสนอ (ยังไม่แทนที่ไฟล์ใน repo)** — ปรับให้ส่งงานหลักเป็น Word ตาม Blueprint v0.5 (DF-15) และให้ไฟล์ `.md` เป็นทางเลือก
> ผู้สอนตรวจแล้วค่อยคัดลอกไปแทน `weeks/week-11-conceptual-architecture/assignment-contract.md` · ส่วนที่เปลี่ยนจากเดิมสรุปไว้ท้ายไฟล์

| Field | Value |
|---|---|
| Assignment ID | `W11-v1.1` |
| Topic | Conceptual Architecture — C4 ระดับ 1 (Context) และระดับ 2 (Container) |
| Course instruction | [เปิดคำสั่งงาน](https://github.com/se-rmutl/engse206-lab-v2/blob/main/weeks/week-11-conceptual-architecture/README.md) |
| Source of case | [`cases/`](https://github.com/se-rmutl/engse206-lab-v2/tree/main/cases) |
| Milestone | Architecture View + Rationale |
| Reference | Template และ Completed Sample (CRBS) v0.3 ใน `reference/` · Lab Worksheets A–D ใน `lab/` |
| Student output — เอกสารหลัก | `design/11-conceptual-architecture-v0.1.docx` (ทำจาก Template W11, 11 หัวข้อ) |
| Student output — ภาพ | `diagrams/architecture/` — Context และ Container เป็น `.drawio` + `.png` (ชื่อแนะนำ `11-context`, `11-container`) |
| Student output — Spine | `design/00-design-spine.md` — เติมคอลัมน์ "W11 กล่องที่รับผิดชอบ" (= "W11 เดินผ่าน container" ในหัวข้อ 7 ของไฟล์ Word) |
| Student output — ใบส่งงาน | `submissions/week-11-submission.md` |
| Student output — ไม่บังคับ | `design/11-conceptual-architecture.md` (สรุปสั้น + ลิงก์ไปไฟล์ Word และภาพ) |
| Evidence | `evidence/week-11/` — ภาพ frame Miro ก่อน/หลังแก้ (บังคับ) · ภาพ worksheet (ไม่บังคับ) |
| Submission commit | `submit(w11): conceptual architecture` |

## ขั้นตอน

1. อ่าน README ของสัปดาห์ และเปิด Completed Sample (CRBS) คู่กับ Template
2. บันทึก Assignment ID และ URL ใน Team Repo
3. คัดลอก Template ไปเป็น `design/11-conceptual-architecture-v0.1.docx` แล้วทำ case ของทีมตามหัวข้อ 1–11
4. วาดภาพใน draw.io เก็บ `.drawio` + `.png` ที่ `diagrams/architecture/` แล้ววาง PNG ในกรอบภาพของไฟล์ Word
5. เติมคอลัมน์ W11 ใน `design/00-design-spine.md` ให้ตรงกับหัวข้อ 7 ของไฟล์ Word
6. เก็บภาพ frame Miro ก่อน/หลังแก้ไว้ที่ `evidence/week-11/` และเขียน worklog / AI use log
7. ตรวจ Done checklist (หัวข้อ 10 ของไฟล์ Word)
8. กรอก `submissions/week-11-submission.md`
9. commit และ push ด้วยข้อความ `submit(w11): conceptual architecture`

## ไฟล์ Word ต้องมีครบ 11 หัวข้อ

1 สิ่งที่รับจาก W10 · 2 Context (C4 ระดับ 1) · 3 Container (C4 ระดับ 2) · 4 ชนิดและสภาพแวดล้อมของ container · 5 NFR กระทบ container ไหน · 6 Decision cards (สถานะ Proposed) · 7 เดิน Spine บน container diagram · 8 Open decisions · 9 ส่งต่อ W12/W13 · 10 Done checklist · 11 AI use + worklog

## ขอบเขตของสัปดาห์นี้

- วาดถึง C4 ระดับ 2 เท่านั้น — component ภายใน API ทำใน W13
- ใช้ stack อ้างอิง React · Node.js + Express · PostgreSQL · ถ้าจะใช้อย่างอื่นต้องมี decision card อ้าง NFR หรือข้อจำกัดของทีม
- สถานะ SRS ระบุตามจริง · decision card ทุกใบเป็น Proposed จนกว่า Dev ยืนยัน
- ห้ามแต่งตัวเลขหรือนโยบายที่ SRS ไม่มี — ให้บันทึกเป็น open decision

> Course Repo เป็นแหล่งคำสั่งงาน ส่วน Team Repo ของกลุ่มเป็นพื้นที่ทำงานและส่งงาน

---

## สิ่งที่เปลี่ยนจาก `W11-v1.0` (สำหรับผู้สอน)

| เรื่อง | เดิม (`W11-v1.0`) | เสนอ (`W11-v1.1`) |
|---|---|---|
| เอกสารหลัก | `design/11-conceptual-architecture.md` | `design/11-conceptual-architecture-v0.1.docx` · ไฟล์ `.md` เป็นทางเลือก |
| ภาพ | `diagrams/architecture/` | เหมือนเดิม และระบุว่าต้องมีทั้ง `.drawio` + `.png` |
| Spine | ไม่ได้ระบุ | `design/00-design-spine.md` คอลัมน์ W11 (ต่อจาก W10) |
| Evidence | ไม่ได้ระบุ path | `evidence/week-11/` |
| ขั้นตอน | 7 ขั้น | 9 ขั้น (เพิ่มคัดลอก Template และเติม Spine) |
| ขอบเขต | ไม่ได้ระบุระดับ C4 | C4 ระดับ 1–2 · component ไป W13 · stack อ้างอิง |

ถ้าผู้สอนต้องการคง `W11-v1.0` ไว้ ให้ใช้เฉพาะแถว "ไม่บังคับ" และ "Evidence" เพิ่มลงไฟล์เดิม แล้วประกาศในห้องว่าให้ส่ง Word แทน `.md`
