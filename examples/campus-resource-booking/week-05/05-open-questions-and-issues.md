# 05 — Open Questions and Issues: Campus Resource Booking

> ไฟล์นี้แยกเรื่องที่ยังไม่รู้หรือยังไม่มี policy ออกจาก Requirement Backlog เพื่อไม่ให้นักศึกษาสร้าง requirement เกินหลักฐาน

## 1. Open Questions

| OQ-ID | คำถาม | Related Evidence / Req | Owner ที่ควรถาม | ผลต่อ Week06 |
|---|---|---|---|---|
| OQ-W05-01 | ข้อมูลขั้นต่ำของคำขอจองมีอะไรบ้าง | E-04, BR-SCRB-01 | Resource Officer | ต้องใช้เขียน Acceptance Criteria |
| OQ-W05-02 | Draft request ควรเก็บได้นานเท่าไร และใครเห็นได้บ้าง | FR-SCRB-02 | Resource Officer / IT | ต้องใช้ทำ state rule |
| OQ-W05-03 | exception request ใครมีอำนาจอนุมัติในแต่ละกรณี | FR-SCRB-03 | Course/Department authority | ต้องใช้ทำ alternate flow |
| OQ-W05-04 | ต้องแจ้งเตือน event ใด ผ่านช่องทางใด และก่อนกี่ชั่วโมง | FR-SCRB-06 | Student requester / Officer | ต้องใช้ทำ notification AC |
| OQ-W05-05 | identity/role data ใดมาจากระบบกลางและเก็บซ้ำได้หรือไม่ | NFR-SCRB-01 | IT / Policy owner | ต้องใช้ทำ quality scenario |

## 2. Issues / Holds

| Issue ID | เรื่องที่ต้อง Hold | เหตุผล | สิ่งที่ต้องเก็บเพิ่ม |
|---|---|---|---|
| ISSUE-SCRB-01 | quota, booking duration, no-show definition, penalty | ไม่มี policy source และ E-08 ระบุว่ายังไม่มีตัวเลขยืนยัน | policy document หรือ decision จากผู้มีอำนาจ |
| ISSUE-SCRB-02 | real-time schedule integration | E-11 ยังเป็น assumption/OQ | ข้อมูลระบบกลาง/API/ความเป็นไปได้ |
| ISSUE-SCRB-03 | mandatory photo for every handover/return | E-14 เป็น proposed solution และมี privacy concern | เหตุผลทาง accountability และ privacy review |
| ISSUE-SCRB-04 | automatic override สำหรับกิจกรรมเรียน | เสี่ยงกระทบ fairness และ authority | authority matrix + escalation policy |

## 3. Follow-up Plan

| Action | Output ที่ต้องได้ | ใช้ต่อใน Week06 อย่างไร |
|---|---|---|
| สัมภาษณ์ Resource Officer เพิ่ม 10 นาที | required fields + draft rule | AC และ use case precondition |
| ขอ policy/decision เรื่อง exception | authority matrix | alternate flow / extension |
| ถาม IT เรื่อง identity/role | data boundary | quality scenario และ constraint |
| เก็บข้อมูล no-show/cancel ถ้ามี | policy evidence | ยังไม่ใช้จนกว่าจะมี owner ยืนยัน |

