# Week 10: Design Strategy Studio
> **Repository workflow:** อ่านโจทย์จาก Course Repo แต่ทำและส่งงานใน Team Repo ของกลุ่ม  
> [เปิด Assignment Contract](assignment-contract.md) | [คู่มือ 2 Repository](../../docs/two-repository-workflow.md)

## ข้อมูลสัปดาห์

| รายการ | รายละเอียด |
|---|---|
| บทเรียน | 5.1 Design Strategy และ Design Rationale |
| CLO | CLO5 |
| เวลา | ทฤษฎี 2 ชั่วโมง + ปฏิบัติ 3 ชั่วโมง |
| คำถามของสัปดาห์ | รุ่นแรกจะสร้างอะไร และอะไรห้ามพลาด? |
| ผลงานที่ต้องส่ง | Design Strategy (scope 4 ระดับ · design drivers 3 ข้อ · open decisions) + Design Spine v0.1 |

## สื่อบนเว็บรายวิชา

| หน้า | ใช้เมื่อไร |
|---|---|
| [ตัวอย่าง CRBS ที่ทำเสร็จแล้ว](https://se-rmutl.github.io/engse206/week10/index.html) | ก่อนคาบและระหว่าง Lab — เดินทีละขั้นว่า CRBS คิดอย่างไร |
| [คู่มือ Lab + บอร์ด Miro](https://se-rmutl.github.io/engse206/week10/lab.html) | ในคาบปฏิบัติ — Activity A–D · checkpoint · การบ้าน · กติกา review บน Miro |

## ไฟล์ในโฟลเดอร์นี้

| โฟลเดอร์ | มีอะไร |
|---|---|
| [`reference/`](reference/) | ตัวอย่าง CRBS ที่ทำเสร็จแล้ว — [อ่านบน GitHub](reference/CRBS_W10_Design_Strategy_Completed_Example_TH.md) หรือดาวน์โหลด .docx |
| [`lab/`](lab/) | [คู่มือ Lab](lab/ENGSE206_Week10_Student_Lab_Guide_TH.md) · [Done Checklist](lab/W10_DONE_CHECKLIST_TH.md) · `worksheets/` W10-A ถึง W10-D · `miro/` [คู่มือบอร์ด Miro](lab/miro/ENGSE206_Week10_Miro_Board_Guide_TH.md) พร้อมภาพ (ทุกไฟล์มีทั้ง .md และ .docx) |
| [`assets/`](assets/) | ภาพในตัวอย่าง CRBS — Design Spine · scope ladder · W10 อยู่ตรงไหนในเส้นทาง (.drawio + PNG) |

แม่แบบสำหรับ Team Repo: [`templates/10-design-strategy.md`](../../templates/10-design-strategy.md) · [`templates/00-design-spine.md`](../../templates/00-design-spine.md)

## Lab 180 นาที

| ช่วง | นาที | ทำอะไร | Worksheet |
|---|---:|---|---|
| Step 0 | 10 | เปิด backlog W05 · model W06 · SRS W07 · finding/OI W08 · คัดลอกแม่แบบ W10 | — |
| A Journey walk | 35 | เขียนเส้นทาง "งานหลักหนึ่งชิ้น" ของ case 5–8 ขั้น หา UC/AC จาก W06 → Design Spine | W10-A |
| B Scope sort | 35 | การ์ด FR/UC เรียง 4 กอง Build now / Overview / Later / ไม่ทำ พร้อมเหตุผล 1 บรรทัด | W10-B |
| Checkpoint 1 | 10 | Gallery walk: ทีมข้าง ๆ ถาม "ทำไมข้อนี้อยู่กองนี้" | — |
| C Drivers | 35 | "ถ้าออกแบบพลาดตรงนี้ ระบบพัง" อ้าง BR/NFR/FR → เหลือ 3 ข้อ พร้อมผลต่อ W11/W12/W13 | W10-C |
| D Open decisions | 30 | จาก OI ของ SRS + สิ่งที่ยังไม่รู้ → DD ไม่เกิน 5 ข้อ มีเจ้าของ/ผลกระทบ/ระหว่างรอทำอย่างไร · ห้ามแต่งตัวเลข | W10-D |
| Checkpoint 2 | 10 | Done checklist 6 ข้อ | Done checklist |
| ปิด | 15 | commit ร่าง · แบ่งงานการบ้าน | — |

หลังคาบ ทีมนำงานขึ้นบอร์ด Miro "Design Strategy Gallery" ให้คู่ review — ดู[คู่มือบอร์ด Miro](lab/miro/ENGSE206_Week10_Miro_Board_Guide_TH.md)

## สิ่งที่ต้องส่ง (ก่อนคาบ W11)

1. `design/10-design-strategy.md` — scope 4 ระดับ · drivers 3 ข้อ · open decisions ≤ 5
2. `design/00-design-spine.md` — Design Spine v0.1 คอลัมน์ "W10 ระดับ" (W11–W13 เติมคอลัมน์ต่อในไฟล์เดียวกัน)
3. `submissions/week-10-submission.md` แล้ว commit `submit(w10): design strategy and rationale`

> [Assignment Contract](assignment-contract.md) (`W10-v1.0`) กำหนด path ข้อ 1 และ 3 · Design Spine เริ่มใน W10 ตามคู่มือ Lab และ [contract W11](../week-11-conceptual-architecture/assignment-contract.md) ใช้ต่อ

## Done checklist W10

- [ ] scope table แบ่ง 4 ระดับ (Build now / Overview / Later / ไม่ทำ) โดยไม่ลบ FR ใดออกจาก SRS
- [ ] ทุกแถวใน scope table มี requirement ID อย่างน้อย 1 ตัว
- [ ] drivers 3 ข้อ แต่ละข้ออ้าง ID และบอกผลต่อการออกแบบใน W11/W12/W13
- [ ] Spine 5–8 แถว มี actor + UC ทุกแถว เรียงตามผู้ใช้ทำจริง
- [ ] open decisions ≤ 5 มีเจ้าของ + ผลกระทบ + "ระหว่างรอทำอย่างไร" และไม่มีค่าที่แต่งขึ้น
- [ ] ระบุสถานะ SRS ตามจริง (Draft / Needs Revision / Baseline Candidate) — ไม่อ้างว่า Approved

## ขอบเขตของสัปดาห์นี้

ยังไม่เลือก architecture · เทคโนโลยี · ฐานข้อมูล · framework · ยังไม่ออกแบบหน้าจอ — เก็บไว้ W11–W13 · เรื่องที่ SRS ยังไม่ตอบให้บันทึกเป็น open decision ห้ามแต่งตัวเลข นโยบาย หรือ protocol

ดู [แผนประเมินผล](../../docs/assessment-rubrics.md) และ [Artefact Roadmap](../../docs/artefact-roadmap.md)
