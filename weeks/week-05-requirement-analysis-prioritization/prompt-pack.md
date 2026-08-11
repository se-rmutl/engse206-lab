# ENGSE206 Week05 Prompt Pack

> ใช้ AI เป็นผู้ช่วยตรวจ ไม่ใช่ผู้ตัดสิน requirement แทนทีม  
> ห้ามให้ AI เพิ่ม fact, policy, ตัวเลข หรือ stakeholder ใหม่ที่ไม่มีในหลักฐานของทีม

## Prompt 1 — Trace Check

```text
คุณเป็นผู้ช่วยตรวจ Requirement Candidate สำหรับวิชา ENGSE206
ฉันจะให้ตาราง RC, Evidence และ Need
โปรดตรวจว่าแต่ละ RC:
1) มี evidence สนับสนุนจริงหรือไม่
2) เขียนเกินหลักฐานหรือไม่
3) ควรใช้ต่อ ปรับแก้ หรือ Hold

ห้ามเพิ่ม fact หรือ policy ใหม่ที่ไม่มีในข้อมูลที่ให้
ตอบเป็นตาราง RC-ID, verdict, reason, follow-up question
```

## Prompt 2 — Classification Review

```text
โปรดช่วยตรวจการจัดประเภท requirement ต่อไปนี้
ประเภทที่ใช้ได้คือ Functional, NFR, Business Rule, Constraint, Issue
สำหรับแต่ละแถวให้บอก:
1) Type เหมาะสมหรือไม่
2) ถ้าไม่เหมาะ ควรเปลี่ยนเป็นอะไร
3) ควร split requirement หรือไม่
4) เหตุผลสั้น ๆ

ห้ามคิด requirement ใหม่หรือเพิ่ม policy ใหม่
```

## Prompt 3 — Priority Rationale Review

```text
โปรดตรวจ priority ของ Requirement Backlog นี้
ใช้เกณฑ์ value, risk, urgency, dependency และ MoSCoW
สำหรับแต่ละแถวให้บอกว่า priority มีเหตุผลหรือเป็นความรู้สึก
ถ้ามี dependency หรือ policy gap ให้แนะนำ status เป็น Needs Follow-up หรือ Hold

ห้ามเพิ่มข้อมูลนอกเหนือจาก evidence ที่ให้
```

## Prompt 4 — Week06 Readiness Gate

```text
โปรดตรวจว่า requirement ใดพร้อมส่งต่อ Week06
เงื่อนไข Ready for Week06:
- มี Source RC และ Evidence/Need Trace
- Type ชัด
- Priority มี rationale
- ไม่มี policy/unknown สำคัญค้างอยู่

ให้ตอบเป็นตาราง Req ID, Ready/Not Ready, reason, suggested Week06 use
```

## AI Use Log

เมื่อนำ AI มาใช้ ให้บันทึกใน `submissions/week-05-submission.md` หรือ `project-management/ai-use-log.md`

| ใช้ AI ช่วยเรื่องใด | Prompt ที่ใช้ | ทีมตรวจสอบอย่างไร |
|---|---|---|
| [กรอก] | [สรุป] | [เทียบกับ E-ID/N-ID] |

