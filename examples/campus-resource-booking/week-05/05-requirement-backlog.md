# 05 — Requirement Backlog v0.1: Campus Resource Booking

> **Case:** Campus Resource Booking System (CRBS)  
> **Source:** Week04 Completed Example: `E-01..E-14`, `N-AVAIL..N-MIN-DATA`, `RC-01..RC-08`  
> **Status:** Completed teaching example for Week05  
> **Goal:** จัดประเภท จัดลำดับ และแยกสิ่งที่พร้อมใช้ต่อ Week06 ออกจากสิ่งที่ยังต้องถามต่อ

## 1. Project Metadata

| Field | Value |
|---|---|
| Course / Week | ENGSE206 / Week05 |
| Team | Example Team |
| Case | Campus Resource Booking |
| Source Week04 file | `examples/campus-resource-booking/week-04/ENGSE206_Week04_Campus_Resource_Booking_Completed_Example.md` |
| Backlog version | `v0.1` |
| Date | 2026-08-11 |

## 2. Prioritization Method

ใช้ MoSCoW โดยไม่ใช้ความรู้สึกของทีมเป็นหลัก แต่ดูจาก 4 มิติ

| Dimension | วิธีใช้ในตัวอย่างนี้ |
|---|---|
| Value | ช่วยผู้ขอใช้และเจ้าหน้าที่ทำงานหลักได้หรือไม่ |
| Risk | ถ้าขาด requirement นี้จะเกิดการจองซ้ำ งานล่าช้า หรือข้อมูลไม่ครบหรือไม่ |
| Urgency | จำเป็นต่อ workflow รุ่นแรกหรือเป็นเรื่องปรับปรุงภายหลัง |
| Dependency | ต้องรอ policy, IT integration, authority matrix หรือข้อมูลตัวเลขก่อนหรือไม่ |

## 3. Requirement Backlog v0.1

| Req ID | Source RC | Evidence / Need Trace | Requirement Statement | Type | Priority | Rationale | Status | Open Question | Week06 Use |
|---|---|---|---|---|---|---|---|---|---|
| FR-SCRB-01 | RC-01 | E-01, E-02, E-03 -> N-AVAIL | ระบบต้องให้ผู้ขอใช้ค้นหาและดูสถานะห้อง/อุปกรณ์ตามช่วงเวลา พร้อมข้อมูลที่จำเป็นต่อการตัดสินใจก่อนยื่นคำขอ | Functional | Must | เป็น capability หลักของระบบและลดปัญหาจองซ้ำ | Ready for Week06 | ข้อมูลขั้นต่ำที่ต้องแสดงมีอะไรบ้าง | Use Case + User Story |
| FR-SCRB-02 | RC-02 | E-04, E-12 -> N-COMPLETE, N-01 | ระบบต้องให้ผู้ขอใช้บันทึกคำขอเป็น Draft/Incomplete โดยยังไม่ถือว่าเป็นการจองหรือกันทรัพยากร | Functional | Should | ช่วยลดการกรอกซ้ำและลดงานถามกลับ แต่ยังต้องกำหนด rule ของ draft | Needs Follow-up | Draft อยู่ได้นานเท่าไร ใครเห็น draft ได้บ้าง | User Story + State Rule |
| BR-SCRB-01 | RC-03 | E-04, E-12 -> N-COMPLETE | ระบบต้องตรวจข้อมูลขั้นต่ำก่อนส่งคำขอเข้าสู่การพิจารณา | Business Rule | Must | ถ้าข้อมูลไม่ครบ เจ้าหน้าที่ทำงานต่อไม่ได้และเกิด delay | Needs Follow-up | required fields ต้องยืนยันจากเจ้าหน้าที่ | Use Case Rule + AC |
| FR-SCRB-03 | RC-04 | E-05, E-07, E-11 -> N-EXCEPTION, N-02 | ระบบต้องรองรับการส่งคำขอ exception พร้อมเหตุผล ผู้มีอำนาจ และผู้ได้รับผลกระทบ | Functional | Should | รองรับกรณีพิเศษโดยไม่ทำ auto override ที่ไม่มีหลักฐาน | Needs Follow-up | authority matrix และเงื่อนไข exception คืออะไร | Use Case Extension |
| FR-SCRB-04 | RC-05 | E-08, E-12, E-13 -> N-FAIR, N-03 | ระบบต้องบันทึกเหตุการณ์ยกเลิก/no-show และแจ้งผู้เกี่ยวข้องตาม policy ที่ได้รับอนุมัติ | Functional + Policy Dependency | Could | event record มีประโยชน์ แต่ penalty/duration ยังไม่มี policy source | Hold | no-show definition, booking duration, penalty owner | Follow-up only |
| FR-SCRB-05 | RC-06 | F-04, E-09, E-14 -> N-ACCOUNT | เจ้าหน้าที่ต้องบันทึกการส่งมอบ/รับคืนด้วยผู้รับผิดชอบ เวลา และสภาพโดยสรุปตามข้อมูลขั้นต่ำที่อนุมัติ | Functional | Should | มี fact เรื่องผู้รับผิดชอบและวันคืน แต่ยังไม่ควรกำหนดรูปถ่ายเป็น rule | Ready for Week06 | สภาพโดยสรุปควรมีตัวเลือกใด | Use Case + AC |
| FR-SCRB-06 | RC-07 | E-06 -> N-AVAIL, N-FAIR | ระบบต้องแจ้งผู้เกี่ยวข้องเมื่อคำขอถูกตัดสิน เปลี่ยนแปลง หรือใกล้เหตุการณ์สำคัญ โดยใช้ recipient/timing ที่ยืนยันแล้ว | Functional | Should | ลดความไม่แน่นอนใน workflow แต่ channel/timing ต้องยืนยัน | Needs Follow-up | แจ้งผ่านช่องทางใด และแจ้งก่อนกี่ชั่วโมง | User Story + Event List |
| NFR-SCRB-01 | RC-08 | CT-02, E-10 -> N-MIN-DATA | ระบบต้องใช้ข้อมูล identity/role เท่าที่จำเป็นต่อการยืนยันตัวตนและสิทธิ์ และไม่เก็บข้อมูลสถาบันซ้ำโดยไม่มีวัตถุประสงค์ที่ยืนยันได้ | NFR / Constraint | Must | เป็นหลัก data minimization และลดความเสี่ยงเรื่อง privacy | Needs IT/Policy Review | data owner, retention, access control, integration boundary | Quality Scenario + Constraint |
| ISSUE-SCRB-01 | E-08 | E-08, E-13 -> N-FAIR | ยังไม่มีหลักฐานยืนยัน quota, booking duration, no-show definition และ penalty | Issue | Won't yet | ห้ามสร้าง policy เองจากความรู้สึกหรือจากตัวอย่างทั่วไป | Hold | ใครเป็นผู้อนุมัติ policy และต้องใช้ข้อมูลย้อนหลังอะไร | Follow-up only |
| ISSUE-SCRB-02 | E-11 | E-11 -> N-EXCEPTION | ยังไม่ยืนยันการอ่านตารางเรียนแบบ real-time หรือ integration กับระบบกลาง | Issue / Technical Dependency | Won't yet | ถ้าสมมติ integration เองจะทำให้ scope และ design ผิดทิศ | Hold | มี API/ระบบกลางหรือไม่ และใช้ได้ใน scope วิชาหรือไม่ | Follow-up only |

## 4. Priority Summary

| Priority | Count | Requirement IDs | เหตุผลรวม |
|---|---:|---|---|
| Must | 3 | FR-SCRB-01, BR-SCRB-01, NFR-SCRB-01 | เป็นแกน workflow, ลด conflict, และคุมข้อมูลส่วนบุคคล |
| Should | 4 | FR-SCRB-02, FR-SCRB-03, FR-SCRB-05, FR-SCRB-06 | มีคุณค่าสูง แต่บางข้อยังต้องยืนยัน rule/channel/authority |
| Could | 1 | FR-SCRB-04 | มีประโยชน์ แต่พึ่ง policy เรื่อง cancellation/no-show |
| Won't yet | 2 | ISSUE-SCRB-01, ISSUE-SCRB-02 | ยังไม่มีหลักฐานเพียงพอ ห้ามยกระดับเป็น requirement |

## 5. Ready / Follow-up / Hold

| Status | Requirement IDs | สิ่งที่ต้องทำต่อ |
|---|---|---|
| Ready for Week06 | FR-SCRB-01, FR-SCRB-05 | ทำ User Story / Use Case / Acceptance Criteria แบบเล็ก |
| Needs Follow-up | FR-SCRB-02, BR-SCRB-01, FR-SCRB-03, FR-SCRB-06, NFR-SCRB-01 | ถาม stakeholder/IT/policy owner เพิ่ม และเก็บ open question |
| Hold | FR-SCRB-04, ISSUE-SCRB-01, ISSUE-SCRB-02 | เก็บเป็น issue; ยังไม่เขียนเป็น final rule หรือ design |

## 6. Review Checklist

- [x] ทุก requirement มี Source RC หรือ Evidence source
- [x] ทุก requirement อ้าง Evidence / Need Trace
- [x] Type แยกเป็น Functional / NFR / Business Rule / Constraint / Issue
- [x] Priority มี rationale จาก value/risk/urgency/dependency
- [x] Unknown หรือ policy issue ไม่ถูกยกระดับเป็น requirement โดยไม่มีหลักฐาน
- [x] มี Week06 Use สำหรับรายการที่พร้อมทำ model

## 7. Week06 Handoff

Week06 ควรเริ่มจาก requirement ที่พร้อมก่อน:

| Week06 artefact | Input ที่เหมาะสม |
|---|---|
| User Story | FR-SCRB-01, FR-SCRB-05 |
| Use Case | FR-SCRB-01 เป็น main flow; FR-SCRB-05 เป็น operational flow |
| Acceptance Criteria | BR-SCRB-01 หลังยืนยัน required fields |
| Quality Scenario | NFR-SCRB-01 หลังยืนยัน data owner/access/retention |
| Extension / Alternate Flow | FR-SCRB-03 หลังยืนยัน authority matrix |

