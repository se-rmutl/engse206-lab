# ENGSE206 Week05 เอกสารประกอบการสอน

> **หัวข้อ:** Requirement Analysis, Classification and Prioritization  
> **คำถามหลัก:** Requirement ใดสำคัญ อยู่ประเภทใด และควรทำก่อน-หลังอย่างไร  
> **Phase:** Define/Specify  
> **Input:** Week04 `Evidence -> Need -> Requirement Candidate`  
> **Output:** Week05 `Requirement Backlog v0.1`

## 1. บทนำ

Week05 เป็นสัปดาห์แรกที่นักศึกษาเริ่มเปลี่ยนข้อมูลจากระยะ Discover ให้กลายเป็น requirement ที่จัดระเบียบได้ แต่ยังไม่ใช่การเขียน SRS เต็มฉบับและยังไม่ใช่การออกแบบระบบ

แกนของสัปดาห์นี้คือ:

```text
Requirement Candidate
-> Functional / NFR / Business Rule / Constraint / Issue
-> Priority
-> Requirement Backlog v0.1
```

จุดที่ต้องย้ำกับนักศึกษาคือ Requirement Backlog ไม่ใช่รายการสิ่งที่ทีมอยากทำ แต่เป็นรายการที่มีหลักฐาน มีเหตุผล และรู้ว่าสิ่งใดยังไม่ควรยืนยัน

## 2. เป้าหมายการเรียนรู้

เมื่อจบ Week05 นักศึกษาควรทำได้:

1. ตรวจ Requirement Candidate โดยอ้าง Evidence/Need จาก Week04 ได้
2. แยกประเภท requirement ได้อย่างมีเหตุผล
3. จัดลำดับความสำคัญด้วย value, risk, urgency และ dependency
4. แยก requirement ที่พร้อมใช้ต่อออกจาก issue/unknown/policy gap
5. สร้าง `docs/05-requirement-backlog.md` ที่ส่งต่อ Week06 ได้

## 3. แนวคิดหลักที่ 1: Requirement Type

Requirement แต่ละข้อควรบอกได้ว่ามันเป็นอะไร เพราะ type จะกำหนดวิธีตรวจสอบและวิธีนำไป model ใน Week06

| Type | ความหมาย | ตัวอย่างคำถาม |
|---|---|---|
| Functional Requirement | ระบบต้องทำ behavior หรือ action | ระบบต้องทำอะไรให้ใคร |
| Non-functional Requirement | คุณภาพหรือเงื่อนไขคุณภาพของระบบ | ต้องเร็ว ปลอดภัย ใช้ง่าย หรือเชื่อถือได้แค่ไหน |
| Business Rule | กฎการทำงานของ domain | เมื่อใดจึงอนุมัติ ยกเลิก หรือเปลี่ยนสถานะ |
| Constraint | ข้อจำกัดภายนอกที่ระบบต้องเคารพ | ต้องใช้ platform, policy, data หรือระบบใด |
| Issue / Unknown | เรื่องที่ยังไม่รู้หรือยังไม่มีหลักฐาน | ต้องถามใคร ต้องใช้หลักฐานอะไร |

### ตัวอย่าง

| Candidate | Type ที่เหมาะ | เหตุผล |
|---|---|---|
| ระบบต้องให้ผู้ใช้ค้นหาห้องว่างตามช่วงเวลา | Functional | เป็น behavior ที่ระบบต้องทำ |
| ระบบต้องใช้ข้อมูลผู้ใช้เท่าที่จำเป็น | NFR / Constraint | เป็นคุณภาพ/ข้อจำกัดด้าน privacy |
| คำขอต้องมีข้อมูลขั้นต่ำก่อนส่งพิจารณา | Business Rule | เป็นกฎของ workflow |
| ต้องลงโทษ no-show ทุกกรณี | Issue / Hold | ยังไม่มี policy source |

## 4. แนวคิดหลักที่ 2: Priority

Priority คือการตัดสินใจอย่างมีเหตุผลว่า requirement ใดควรมาก่อน ไม่ใช่การเลือกจากความชอบของทีม

ใช้ MoSCoW:

| Priority | ใช้เมื่อ |
|---|---|
| Must | ขาดไม่ได้ต่อ workflow รุ่นแรก กฎ ความปลอดภัย หรือเป้าหมายหลัก |
| Should | สำคัญมาก แต่ยังมี workaround |
| Could | มีคุณค่า แต่เลื่อนได้ |
| Won't yet | ยังไม่ทำใน scope นี้ หรือหลักฐานยังไม่พอ |

ให้ถาม 4 มิติทุกครั้ง:

| Dimension | คำถาม |
|---|---|
| Value | stakeholder หลักได้ประโยชน์อะไร |
| Risk | ถ้าไม่ทำจะเกิดปัญหาใด |
| Urgency | ต้องใช้ใน workflow แรกหรือยังรอได้ |
| Dependency | ต้องรอ policy, authority, IT integration หรือข้อมูลเพิ่มหรือไม่ |

## 5. แนวคิดหลักที่ 3: Backlog v0.1

Backlog v0.1 คือรายการ requirement ที่ยังเป็น working version แต่มีโครงสร้างพอให้ตรวจและส่งต่อได้

แต่ละแถวควรมี:

| Field | เหตุผลที่ต้องมี |
|---|---|
| Req ID | ใช้อ้างอิงต่อใน Week06 |
| Source RC | ตามรอยกลับไป Week04 |
| Evidence / Need Trace | ป้องกัน requirement ลอย |
| Requirement Statement | ทำให้เข้าใจสิ่งที่ระบบต้องทำ/ต้องเป็น |
| Type | กำหนดวิธีตรวจสอบและ model |
| Priority | บอกความสำคัญ |
| Rationale | อธิบายเหตุผล |
| Status | Ready / Needs Follow-up / Hold |
| Open Question | ไม่เดาสิ่งที่ยังไม่รู้ |
| Week06 Use | เตรียมนำไปทำ User Story / Use Case / AC |

## 6. Worked Example: Campus Resource Booking

จาก Week04 ได้ `RC-01` ว่า:

> ระบบต้องให้ผู้ขอใช้ค้นหาและดูสถานะห้อง/อุปกรณ์ตามช่วงเวลา พร้อมข้อมูลที่จำเป็นต่อการตัดสินใจก่อนยื่นคำขอ

เมื่อตรวจใน Week05:

| วิเคราะห์ | ผล |
|---|---|
| Evidence | E-01, E-02, E-03 |
| Need | N-AVAIL |
| Type | Functional |
| Priority | Must |
| Rationale | เป็น capability หลักที่ช่วยลดปัญหาจองซ้ำ |
| Status | Ready for Week06 |
| Week06 Use | Use Case + User Story |

ดังนั้นเขียนเป็น backlog ได้:

| Req ID | Statement | Type | Priority | Status |
|---|---|---|---|---|
| FR-SCRB-01 | ระบบต้องให้ผู้ขอใช้ค้นหาและดูสถานะห้อง/อุปกรณ์ตามช่วงเวลา | Functional | Must | Ready for Week06 |

แต่ `RC-05` เรื่อง no-show/cancellation ต้องระวัง เพราะมี need เรื่อง record แต่ยังไม่มี policy เรื่อง penalty จึงควรแยกเป็น:

- Functional ที่บันทึก event ได้
- Issue/Hold เรื่อง penalty, quota, duration

## 7. Activity Flow สำหรับห้องเรียน

| ช่วง | เวลา | กิจกรรม | Output |
|---|---:|---|---|
| Recall | 15 นาที | ทบทวน Week04 Evidence -> Need -> RC | เลือก RC 3-5 ข้อ |
| Mini Lecture | 35 นาที | อธิบาย type และ priority | นักศึกษาแยกตัวอย่างได้ |
| Worked Example | 30 นาที | Campus Resource Booking | เห็นวิธีแปลง RC -> Backlog |
| Trace Check | 30 นาที | ตรวจที่มาของ RC | ตาราง trace |
| Card Sorting | 40 นาที | แยก type | classification draft |
| Prioritization | 35 นาที | ให้ MoSCoW + rationale | priority draft |
| Build Backlog | 30 นาที | กรอก `docs/05-requirement-backlog.md` | Backlog v0.1 |
| Review/Submit | 25 นาที | peer review + submission | submission checklist |

## 8. Common Misconceptions

| ความเข้าใจผิด | วิธีแก้ |
|---|---|
| Requirement คือ solution ที่ทีมอยากทำ | ให้ถามว่า stakeholder need คืออะไรและหลักฐานอยู่ตรงไหน |
| NFR คืออะไรก็ได้ที่ไม่ใช่ function | ต้องผูกกับ quality attribute และ criterion |
| Priority คือสิ่งที่ทีมชอบก่อน | ต้องมี value/risk/urgency/dependency |
| Unknown แปลว่าคิดเองได้ | ให้ mark เป็น Issue/Hold |
| Business Rule กับ Constraint เหมือนกัน | Business Rule คือกฎ domain; Constraint คือข้อจำกัดภายนอก |

## 9. Responsible AI

ใช้ AI ได้เพื่อช่วยตรวจ แต่ทีมต้องตัดสินใจเอง

ใช้ AI ได้:

- ตรวจว่ามี trace หรือไม่
- ช่วยชี้ว่าประโยคกำกวมตรงไหน
- เสนอว่าควร split requirement หรือไม่
- ตรวจ consistency ของ backlog

ต้องตรวจเอง:

- Evidence จริงหรือไม่
- AI เพิ่ม fact ใหม่หรือไม่
- Type/Priority สอดคล้องกับหลักฐานหรือไม่
- Unknown ถูก hold ไว้หรือถูกเดาเป็น requirement

## 10. Definition of Done

งาน Week05 เสร็จเมื่อ:

- [ ] มี `docs/05-requirement-backlog.md`
- [ ] ทุก requirement มี Source RC และ Evidence/Need Trace
- [ ] มี type, priority, rationale, status และ Week06 Use
- [ ] issue/unknown/policy gap ไม่ถูกเขียนเป็น requirement โดยไม่มีหลักฐาน
- [ ] มี `submissions/week-05-submission.md`
- [ ] มีรายการ `Ready for Week06`

## 11. Handoff สู่ Week06

Week06 จะนำ Backlog v0.1 ไปสร้าง Requirement Model ชุดเล็ก:

| Input จาก Week05 | ใช้ทำอะไรใน Week06 |
|---|---|
| Functional Requirement | User Story / Use Case |
| Business Rule | Acceptance Criteria / Use Case Rule |
| NFR | Quality Scenario / Acceptance Criteria |
| Constraint | Constraint note ใน model |
| Issue/Hold | Follow-up list ยังไม่ทำ model |

