# 04 — Requirement Candidates: Campus Resource Booking

## 1. How We Turned Evidence into Requirement Candidates

หลักคิดของทีม:

1. เริ่มจาก evidence ที่มี E-ID
2. เขียน need เป็นปัญหา/เป้าหมายของ stakeholder
3. เขียน RC เป็น capability ของระบบ
4. ใส่ status เป็น `Candidate` หรือ `Needs Validation`
5. ระบุ follow-up ถ้ายังมี unknown

```mermaid
flowchart LR
    E["E-01: ไม่รู้ว่าว่างจริงไหม"] --> N["N-01: ต้องเห็นสถานะก่อนจอง"]
    N --> R["RC-01: แสดงสถานะว่าง/ไม่ว่าง"]
```

## 2. Requirement Candidate Table

| RC-ID | Requirement Candidate | Stakeholder / Need | Evidence E-ID(s) | Status | Follow-up |
|---|---|---|---|---|---|
| RC-01 | The system should show availability status for rooms and learning equipment before a user submits a booking request. | Student Requester / N-01 | E-01 | Candidate | Verify source of availability status |
| RC-02 | The system should allow users to search and filter resources by resource type and availability so that they can choose a suitable resource before requesting it. | Student Requester / N-02 | E-02 | Candidate | Confirm search/filter fields |
| RC-03 | The system should display expected return date/time for borrowed equipment to both requester and resource officer. | Student Requester, Resource Officer / N-03 | E-03 | Candidate | Confirm due-date rule |
| RC-04 | The system should require minimum booking information before a request can be submitted for review. | Resource Officer / N-04 | E-04 | Candidate | Confirm required fields |
| RC-05 | The system should mark urgent or schedule-conflicting requests as needing manager/instructor validation before approval. | Resource Officer / N-05 | E-05 | Needs Validation | Confirm approval authority |

## 3. Why These Are Candidates, Not Final Requirements

| RC | เหตุผลที่ยังไม่ final |
|---|---|
| RC-01 | ยังไม่รู้ว่า availability จะ sync จากแหล่งข้อมูลใด |
| RC-03 | ยังไม่รู้กฎวันคืนและวิธีแจ้งเตือน |
| RC-05 | ยังไม่รู้ authority ที่อนุมัติ exception จริง |

## 4. Candidate to Week05 Backlog Handoff

| Week04 RC | Move to Week05? | Reason |
|---|---|---|
| RC-01 | Yes | Evidence ชัดและเป็น core flow |
| RC-02 | Yes | ช่วยลดการถามเจ้าหน้าที่ซ้ำ |
| RC-03 | Yes, revise after validation | ต้องยืนยัน rule วันคืน |
| RC-04 | Yes | เป็น constraint จากเจ้าหน้าที่ |
| RC-05 | Revise | ต้องถามผู้มีอำนาจก่อนเขียนให้ชัด |

## 5. Student Takeaway

ตัวอย่างนี้แสดงว่า RC ที่ดีควรตอบได้ว่า:

- อ้าง evidence ไหน
- แก้ need อะไร
- ยังไม่รู้อะไร
- จะตรวจต่อใน Week05 อย่างไร
