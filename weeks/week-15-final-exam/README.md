# Week 15: สอบปลายภาค — Take-home 24 ชั่วโมง

> A6 · 15 คะแนน · ส่วน ก งานกลุ่ม 9 คะแนน + ส่วน ข รายบุคคล 6 คะแนน + oral spot-check หลังส่ง

## เวลา

| รายการ | ค่า |
|---|---|
| เริ่ม (T0) | 20 ตุลาคม 2569 · เวลา 9:00 |
| ส่งทั้งสองส่วน | ภายใน T0 + 24 ชั่วโมง |
| Oral spot-check | [ผู้สอนประกาศ] |
| ช่องทางถามระหว่างสอบ | [ผู้สอนกำหนด] |
| ส่งช้า | [ผู้สอนกำหนด] |

## อ่านก่อนวันสอบ

- [ประกาศรูปแบบสอบปลายภาค (Word)](./ENGSE206_Final_Announcement_v1.0.docx) · [PDF](./ENGSE206_Final_Announcement_v1.0.pdf)
- [ใบส่งงาน final-exam-submission.md](./templates/final-exam-submission.md) · [ai-use-log.md](./templates/ai-use-log.md)

## ข้อสอบ (เปิดที่ T0)

ไฟล์ในโฟลเดอร์ `exam/` จะขึ้นเมื่อถึงเวลา T0 — ก่อนหน้านั้นลิงก์จะยังเปิดไม่ได้

| ส่วน | ใครทำ | ไฟล์ |
|---|---|---|
| ส่วน ก Change-to-Design | ทั้งกลุ่ม | [Word](./exam/ENGSE206_Final_PartA_ChangeToDesign_v1.0.docx) · [PDF](./exam/ENGSE206_Final_PartA_ChangeToDesign_v1.0.pdf) |
| ส่วน ข ชุด A — ClubFund | เลขท้ายรหัส **คู่** (0 2 4 6 8) | [Word](./exam/ENGSE206_Final_PartB_SetA_ClubFund_v1.0.docx) · [PDF](./exam/ENGSE206_Final_PartB_SetA_ClubFund_v1.0.pdf) |
| ส่วน ข ชุด B — InternMatch | เลขท้ายรหัส **คี่** (1 3 5 7 9) | [Word](./exam/ENGSE206_Final_PartB_SetB_InternMatch_v1.0.docx) · [PDF](./exam/ENGSE206_Final_PartB_SetB_InternMatch_v1.0.pdf) |
| แบบฟอร์มคำตอบส่วน ก | ทั้งกลุ่ม | [Word](./exam/ENGSE206_Final_PartA_GroupAnswer_Template_v1.0.docx) — บันทึกเป็น `final-exam/final-exam-group-answer.docx` |

แนะนำให้ทุกคนทำ **ส่วน ข ให้เสร็จก่อน** แล้วจึงเริ่มงานกลุ่ม

## เนื้อหาที่ออกสอบ

| สัปดาห์ | เรื่อง | น้ำหนัก |
|---|---|---|
| W06 | User Story · Use Case · Acceptance Criteria (Given/When/Then) | รอง |
| W07 | SRS: FR / BR / NFR / DR · source · Open Issue | รอง |
| W08 | Review · Traceability · Baseline · Change Request และ impact | รอง |
| W10 | Scope 4 ระดับ · Design Driver · Design Spine · open decisions | **หลัก** |
| W11 | C4 ระดับ 1–2 · ชนิด container · NFR → container · stack อ้างอิง · decision card | **หลัก** |

ไม่ออกสอบ: W12 UX/UI Prototype และ W13 Detailed Design

## ส่งส่วน ก (งานกลุ่ม) ใน Team Repo

1. สร้าง branch `final-exam` จาก `main`
2. สร้างโฟลเดอร์ `final-exam/` แล้ววางไฟล์ตามตาราง
3. ทุกคน commit ส่วนของตัวเองด้วยบัญชีของตัวเอง — commit คือหลักฐานการมีส่วนร่วม
4. เปิด Pull Request เข้า `main` ชื่อ `submit(final): change-to-design take-home` ก่อน T0 + 24 ชั่วโมง

| ไฟล์ใน Team Repo | บังคับ |
|---|---|
| `final-exam/final-exam-group-answer.docx` (จากแบบฟอร์มคำตอบส่วน ก ที่ปล่อยใน `exam/`) | บังคับ |
| `final-exam/diagrams/context-after.drawio` + `.png` | บังคับ |
| `final-exam/diagrams/container-after.drawio` + `.png` | บังคับ |
| `final-exam/final-exam-submission.md` | บังคับ |
| `final-exam/ai-use-log.md` | บังคับ (ไม่ใช้ AI ก็เขียนว่าไม่ใช้) |

**อย่าแก้ไฟล์งานเดิมของแต่ละสัปดาห์** — ทำทุกอย่างใน `final-exam/`

## ส่งส่วน ข (รายบุคคล)

- พิมพ์คำตอบลงในไฟล์ Word ของชุดตัวเอง แล้วบันทึกชื่อ `final-exam-individual-<รหัส>.docx`
- ส่งที่ [ช่องทางที่ผู้สอนกำหนด] ภายใน T0 + 24 ชั่วโมง — **ไม่ส่งใน Team Repo**
- ทำคนเดียว ห้ามปรึกษาผู้อื่น รวมถึงเพื่อนในกลุ่ม · เปิดเอกสารรายวิชาได้ · ห้ามให้ AI ทำคำตอบแทน (ใช้ตรวจคำสะกดได้ ต้องระบุในช่องการใช้ AI ท้ายไฟล์)

## กติกาสำคัญ

- ห้ามแต่งตัวเลข นโยบาย หรือ protocol ที่ SRS ไม่มี — เขียน TBD แล้วบันทึกเป็น Open Issue หรือ open decision
- ห้ามอ้างว่า SRS หรือ Change Request ใด Approved แล้ว
- ใช้ stack อ้างอิง (React · Node.js + Express · PostgreSQL) และเมนูชนิด container ของ W11 — เปลี่ยนเมื่อมี decision card
- คะแนนส่วน ก ทุกคนได้เท่ากันเป็นฐาน แต่ผู้สอนปรับรายคนได้ถ้าหลักฐาน (commit · ตารางการมีส่วนร่วม · คำตอบเรื่องงานกลุ่มใน oral) ชี้ว่าแทบไม่มีส่วนร่วม

## Done checklist

- [ ] ส่วน ข ของตัวเอง: ทำครบ 6 ข้อ · เลือกโจทย์ย่อยตามเลขท้ายรหัส · ตั้งชื่อไฟล์ถูก · ส่งแล้ว
- [ ] ส่วน ก: CR-FX-01 ครบ G1–G4 · CR เสริม 1 ข้อใน G5 · G6 ครบ
- [ ] Context และ Container ฉบับใหม่มีทั้ง `.drawio` และ `.png` · ลูกศรทุกเส้นมีป้าย
- [ ] `final-exam-submission.md` มี commit hash สุดท้าย · `ai-use-log.md` ครบ
- [ ] เปิด PR ชื่อ `submit(final): change-to-design take-home` ก่อน T0 + 24 ชั่วโมง

สื่อทบทวน (สไลด์ · ตัวอย่าง CRBS · คู่มือ Lab) อยู่ที่เว็บรายวิชา <https://se-rmutl.github.io/engse206/>
