# Week 4 — Requirement Candidates

**Case:** Campus Resource Booking  
**Status:** Candidate / Provisional only — not approved requirements  
**Inputs:** Evidence Log + Negotiation Record  
**Version:** 1.0

> Requirement Candidate (RC) ต้องอ้างหลักฐานและแสดงสิ่งที่ยังต้องยืนยัน ไม่ควรเขียนให้ดูแน่นอนเกิน evidence

## 1. Candidate register

| RC-ID | Candidate requirement | Type | Evidence | Status | Confidence | Verification needed |
|---|---|---|---|---|---|---|
| RC-001 | ระบบควรให้ผู้ใช้ที่ยืนยันตัวตนแล้วค้นหาทรัพยากรตามวันที่ ช่วงเวลา ประเภท และความจุ พร้อมแสดงเวลาซิงก์ข้อมูลล่าสุด | Functional | E-001, E-002, E-005, E-014 | Candidate | Medium | ยืนยัน data source/API และ search fields |
| RC-002 | ก่อนส่งคำขอ ระบบควรตรวจความครบถ้วนของวัตถุประสงค์ จำนวนผู้ใช้ ผู้รับผิดชอบ วันเวลา และข้อมูลที่ resource type กำหนด | Functional | E-007, E-010 | Candidate | Medium | ตรวจแบบฟอร์มและ field-by-resource |
| RC-003 | ระบบควรแสดงสถานะคำขอและสิ่งที่ผู้ใช้ต้องดำเนินการถัดไป เช่น รอตรวจสอบ ต้องแก้ไข อนุมัติ หรือปฏิเสธ | Functional | E-002, E-004, E-016 | Candidate | Medium | Validate status model and wording |
| RC-004 | เมื่อคำขอถูกส่งกลับ ระบบควรระบุข้อมูลที่ต้องแก้และเหตุผลโดยไม่เปิดเผยข้อมูลของคำขออื่น | Functional / Privacy | E-004, E-013 | Candidate | Medium | privacy/UX review |
| RC-005 | ระบบควรแจ้งเหตุการณ์สำคัญ ได้แก่ ส่งคำขอ ส่งกลับ อนุมัติ ปฏิเสธ ยกเลิก และเปลี่ยนเวลา ผ่านช่องทางที่องค์กรอนุญาต | Functional | E-003, E-004, E-016 | Candidate | Low–Medium | ยืนยัน mandatory events และ approved channels |
| RC-006 | เมื่อพบคำขอชนกัน ระบบควรใช้ priority rule ที่ได้รับอนุมัติ และหากกฎไม่ครอบคลุมให้ส่งผู้มีอำนาจพิจารณา | Functional / Business Rule | E-008, E-011, E-012, N-01 | Provisional | Low | policy sign-off and authority matrix |
| RC-007 | การ override ลำดับคำขอต้องบันทึก approver role, reason code, rationale และ timestamp ใน audit trail | Functional / Audit | E-012, N-01 | Provisional | Medium | governance and retention review |
| RC-008 | ผู้ใช้ทั่วไปไม่ควรเห็นชื่อเต็ม เหตุผลละเอียด หรือข้อมูลส่วนบุคคลของผู้จองรายอื่น เว้นแต่ได้รับสิทธิ์ตามบทบาท | Non-functional / Privacy | E-013, E-015 | Candidate | Medium | data visibility matrix approval |
| RC-009 | ระบบต้องใช้ University SSO และไม่จัดเก็บรหัสผ่านของผู้ใช้ภายใน CRBS | Non-functional / Security | E-015 | Candidate | Medium | verify security architecture |
| RC-010 | หากระบบตารางเรียนหรือ availability source ไม่พร้อมใช้งาน ระบบควรแสดงสถานะข้อมูลไม่พร้อม/ล้าสมัยและไม่ยืนยันว่าทรัพยากรว่างโดยไม่มีหลักฐาน | Functional / Reliability | E-005, E-014 | Candidate | Low–Medium | integration/fallback validation |
| RC-011 | ระบบควรเก็บประวัติการเปลี่ยนสถานะและผู้ดำเนินการเพื่อให้ตรวจสอบย้อนหลังได้ตามสิทธิ์ | Non-functional / Auditability | E-012, E-016 | Candidate | Medium | retention period and access review |
| RC-012 | ระบบควรอนุญาตให้ผู้ดูแลกำหนด booking window, maximum duration และ approval rule แยกตาม resource type | Functional / Configurability | E-006, E-017, E-018 | Provisional | Low | verify variation and rule owner |

## 2. Candidate quality review

### 2.1 What is good

- แต่ละ RC อ้าง E-ID หรือ negotiation record
- ใช้คำว่า “ควร” และ status เพื่อไม่ overclaim approval
- แยก need/rule ออกจาก design choice เช่น ไม่กำหนด LINE เป็นช่องทางทันที
- ระบุ verification action สำหรับ confidence ต่ำ

### 2.2 What still needs work in Week 5

- จัด classification อย่างเป็นทางการ: functional, data, interface, constraint, quality attribute
- แยก compound requirement บางข้อ
- กำหนด priority ด้วยวิธีที่มีเหตุผล
- ระบุ acceptance criteria / fit criterion
- resolve authority และ policy gaps
- ตัด proposed solution ที่ยังไม่จำเป็น

## 3. Traceability snapshot

| Source | Leads to | Notes |
|---|---|---|
| OQ-01 → EO-01 | E-010, E-012, E-018 → RC-006, RC-007, RC-012 | authority ยัง unresolved |
| OQ-02 → EO-02 | E-006, E-007, E-017 → RC-002, RC-012 | booking rule ต้องแยกตาม resource |
| OQ-03 → EO-03 | E-013, E-015 → RC-008, RC-009 | ต้องทำ visibility matrix |
| OQ-04 → EO-04 | E-008, E-011, E-012 → N-01 → RC-006, RC-007 | provisional negotiation |
| OQ-05 → EO-05 | E-002, E-003, E-004, E-016 → RC-003, RC-004, RC-005 | channel ยังไม่เลือก |
| C-02 → EO-06 | E-005, E-014 → RC-001, RC-010 | API assumption unresolved |

## 4. Candidate-to-acceptance direction

| RC-ID | Early acceptance direction (not final) |
|---|---|
| RC-001 | Given valid search criteria, results show matching resources and last-sync time |
| RC-003 | Every request state maps to a visible status and next action |
| RC-006 | Conflict test scenarios produce rule-based or human-review outcome with rationale |
| RC-008 | Role tests confirm unauthorized users cannot access protected fields |
| RC-010 | When source unavailable, system displays stale/unavailable warning and blocks false confirmation |

## 5. Week 5 handoff checklist

- [x] มี 5–8 ข้อขึ้นไป (ตัวอย่างนี้มี 12 เพื่อใช้สอน classification)
- [x] ทุกข้อมี evidence link
- [x] แสดง status/confidence/follow-up
- [x] ไม่มีข้อใดอ้างว่าได้รับอนุมัติจริง
- [x] conflict ที่สำคัญเชื่อม negotiation record
- [x] unresolved issues พร้อมเข้าสู่ analysis/prioritization
