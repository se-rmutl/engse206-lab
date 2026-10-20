# Week 11: LAB 3: Conceptual Architecture Studio
> **Repository workflow:** อ่านโจทย์จาก Course Repo แต่ทำและส่งงานใน Team Repo ของกลุ่ม  
> [เปิด Assignment Contract](assignment-contract.md) | [คู่มือ 2 Repository](../../docs/two-repository-workflow.md)

## ข้อมูลสัปดาห์

| รายการ | รายละเอียด |
|---|---|
| บทเรียน | 5.1 Conceptual Architecture — C4 ระดับ 1 (Context) และระดับ 2 (Container) |
| CLO | CLO5 |
| เวลา | ทฤษฎี 2 ชั่วโมง + ปฏิบัติ 3 ชั่วโมง |
| คำถามของสัปดาห์ | ระบบแบ่งเป็นกี่ชิ้นที่ต้องรัน แต่ละชิ้นใช้เทคโนโลยีชนิดไหน และกติกาสำคัญอยู่ชิ้นไหน? |
| ผลงานที่ต้องส่ง | Conceptual Architecture (Word ตาม Template) + ภาพ .drawio/PNG + Design Spine คอลัมน์ W11 |
| stack อ้างอิง | React · Node.js + Express · PostgreSQL (เปลี่ยนได้เมื่อมี decision card อ้าง NFR หรือข้อจำกัดของทีม) |

## สื่อบนเว็บรายวิชา

| หน้า | ใช้เมื่อไร |
|---|---|
| [อ่านก่อนเรียน](https://se-rmutl.github.io/engse206/week11/intro.html) | ก่อนคาบ — W10 ให้อะไร ทำไมต้องมี W11 และ C4 คืออะไร |
| [สไลด์ทฤษฎี](https://se-rmutl.github.io/engse206/week11/slides.html) | ในคาบทฤษฎี |
| [ตัวอย่าง CRBS ที่ทำเสร็จแล้ว](https://se-rmutl.github.io/engse206/week11/index.html) | เปิดคู่กับ Template ตลอด Lab |
| [คู่มือ Lab 180 นาที](https://se-rmutl.github.io/engse206/week11/lab.html) | ในคาบปฏิบัติ — ลำดับงาน ข้อสังเกต เกณฑ์ผ่าน Miro และการส่งงาน |

## ไฟล์ในโฟลเดอร์นี้

| โฟลเดอร์ | มีอะไร |
|---|---|
| `reference/` | Template (แบบฟอร์มงานกลุ่ม) · Completed Sample ของ CRBS (.docx + .pdf) |
| `lab/` | Lab Worksheets A–D (.docx + .pdf) · `figures/` รูปของคู่มือ Lab และบอร์ด Miro W11 (.drawio + PNG) |
| `assets/` | ภาพใน Completed Sample (.drawio + PNG) — เปิดใน draw.io เพื่อดูวิธีวาด |

## Lab 180 นาที

| ช่วง | นาที | ทำอะไร | Worksheet → Template |
|---|---:|---|---|
| Step 0 | 10 | เปิด SRS + W10 ของทีม แบ่งบทบาท คัดลอก Template | หัวข้อ 1 |
| A Context | 25 | ระบบ 1 กล่อง + actor + ระบบภายนอก (Core / Extension / TBD) | W11-A → หัวข้อ 2 |
| B Container | 45 | การ์ด 3 แบบ → เมนูชนิด → container diagram + ตาราง (รันที่ไหน ใครควบคุม) | W11-B → หัวข้อ 3–4 |
| Checkpoint 1 | 10 | Miro: โพสต์ Context + Container ให้คู่ถาม "driver ที่ห้ามพลาดของทีม อยู่ container ไหน" | — |
| C NFR + decision | 40 | NFR ทุกข้อ → container ที่กระทบ หรือ TBD · decision card ≤ 3 ใบ | W11-C → หัวข้อ 5–6 |
| D Spine + DD | 25 | เดิน Spine บน container diagram · อัปเดต open decisions | W11-D → หัวข้อ 7–8 |
| Checkpoint 2 | 10 | Done checklist 6 ข้อ + คู่อ่านช่อง 3–4 บน Miro | หัวข้อ 10 |
| ปิด | 15 | export PNG วางใน Template · commit ร่าง · แบ่งการบ้าน | — |

คู่ตรวจบน Miro W11: กลุ่ม 1 กับ 2 · 3 กับ 4 · 5 กับ 6 · 7 กับ 8 · 9 กับ 10

## สิ่งที่ต้องส่ง (ก่อนคาบ W12)

ดู path ทั้งหมดใน [Assignment Contract](assignment-contract.md) — สรุป:

1. `design/11-conceptual-architecture-v0.1.docx` — Template W11 ครบ 11 หัวข้อ
2. `diagrams/architecture/` — Context และ Container เป็น .drawio + .png
3. `design/00-design-spine.md` — เติมคอลัมน์ "W11 กล่องที่รับผิดชอบ"
4. `evidence/week-11/` — ภาพ frame Miro ก่อน/หลังแก้
5. `submissions/week-11-submission.md` และ commit `submit(w11): conceptual architecture`

## Done checklist W11

- [ ] Context diagram: ระบบ 1 กล่อง + actor ครบ + ระบบภายนอกพร้อมป้าย Core / Extension / TBD
- [ ] Container diagram: ทุก container มีชื่อ + [ชนิด · เทคโนโลยี] + หน้าที่; ลูกศรทุกเส้นบอกว่าส่งอะไร
- [ ] ตาราง container บอกสภาพแวดล้อม (รันที่ไหน ใครควบคุม) และข้อมูลที่เก็บ
- [ ] NFR ทุกข้อชี้ได้ว่ากระทบ container ไหน หรือเป็น TBD; decision card ≤ 3 ใบอ้าง NFR/driver
- [ ] ทุกขั้น Build now/Overview ใน Spine เดินผ่าน container ได้ และกติกา D1–D3 อยู่ฝั่ง server
- [ ] ใช้ stack อ้างอิง หรือมี decision card เมื่อเปลี่ยน; ไม่มีเทคโนโลยีเกินจำเป็น; ทุกภาพมี .drawio + PNG

## ขอบเขตของสัปดาห์นี้

วาดถึง C4 ระดับ 2 เท่านั้น — component ข้างใน API ทำใน W13 · เรื่องที่ SRS ยังไม่ตอบให้เขียน TBD และบันทึกเป็น open decision ห้ามแต่งตัวเลข นโยบาย หรือ protocol

ดู [แผนประเมินผล](../../docs/assessment-rubrics.md) และ [Artefact Roadmap](../../docs/artefact-roadmap.md)
