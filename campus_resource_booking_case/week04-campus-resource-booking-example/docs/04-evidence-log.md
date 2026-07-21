# 04 — Evidence Log: Campus Resource Booking

## 1. Source Summary

| Field | Value |
|---|---|
| Case | Campus Resource Booking |
| AI role(s) used | Student Requester, Resource Officer |
| Source files | Case card, Week04 role pack, Week03 interview guide |
| Conversation excerpt | [`../evidence/week-04/ai-conversation-excerpt.md`](../evidence/week-04/ai-conversation-excerpt.md) |

## 2. Evidence Log

| E-ID | Source / Role | Evidence quote or summary | Tag | Interpreted Need | Related RC | Follow-up / Unknown |
|---|---|---|---|---|---|---|
| E-01 | AI: Student Requester | นักศึกษาไม่รู้ว่าห้องหรืออุปกรณ์ว่างจริงไหม ต้องถามเจ้าหน้าที่ก่อน และบางครั้งมีคำขอชนช่วงเดียวกัน | NEED | ผู้ใช้ต้องเห็นสถานะทรัพยากรก่อนส่งคำขอจอง | RC-01 | ต้องยืนยันว่า status มาจากแหล่งข้อมูลใด |
| E-02 | AI: Student Requester | อยากเห็นรายการทรัพยากรที่ค้นหาได้ พร้อมสถานะว่าจองได้หรือไม่ | NEED | ผู้ใช้ต้องค้นหาและกรองทรัพยากรได้ก่อนจอง | RC-02 | ต้องระบุ field ค้นหาที่จำเป็น |
| E-03 | AI: Student Requester | บางครั้งยืม adapter หรือ webcam แล้วคืนช้า เจ้าหน้าที่ต้องตามเอง และนักศึกษาไม่แน่ใจวันคืน | NEED | ผู้ยืมและเจ้าหน้าที่ต้องเห็นกำหนดคืนที่ชัดเจน | RC-03 | ต้องตรวจวิธีแจ้งเตือนที่เหมาะสม |
| E-04 | AI: Resource Officer | ต้องรู้ผู้รับผิดชอบ ทรัพยากร ช่วงเวลา และวันคืน ถ้าข้อมูลไม่ครบต้องถามกลับ | CONSTRAINT | คำขอจองต้องมีข้อมูลขั้นต่ำก่อนส่งให้ตรวจ | RC-04 | ต้องยืนยันว่าข้อมูลขั้นต่ำมีอะไรบ้าง |
| E-05 | AI: Resource Officer | คำขอเร่งด่วนหรือชนตารางเรียนต้องให้ผู้ดูแล/อาจารย์ยืนยัน เจ้าหน้าที่ไม่ควรอนุมัติเองทุกกรณี | CONSTRAINT | ระบบต้องแยกคำขอปกติกับคำขอที่ต้องส่งต่อ | RC-05 | ต้องระบุ authority/approval rule |
| E-06 | AI: Resource Officer | ระยะเวลาจองล่วงหน้าและจำนวนครั้งที่จองได้ต่อคนต้องให้ผู้ดูแลพื้นที่กำหนด | UNKNOWN | ยังไม่ควรเขียนกฎโควตาหรือระยะเวลาจองเป็น final | - | ถาม Area Manager/Instructor ใน Week05 |

## 3. How the Team Derived Needs

| Evidence | ทำไมถือเป็น Need/Constraint | Need ที่ได้ |
|---|---|---|
| E-01 | stakeholder พูดถึงปัญหาก่อนส่งคำขอ ไม่ใช่เสนอหน้าจอเฉพาะ | N-01 ผู้ใช้ต้องเห็นสถานะทรัพยากรก่อนจอง |
| E-03 | มี pain point ทั้งฝั่งผู้ยืมและเจ้าหน้าที่ จึงควรแปลงเป็น need เรื่องกำหนดคืน | N-03 ผู้เกี่ยวข้องต้องเห็นวันคืนที่ชัดเจน |
| E-05 | มีขอบเขตอำนาจของเจ้าหน้าที่ จึงเป็น constraint ต่อ workflow | N-05 ระบบต้องช่วยแยกคำขอที่ต้องส่งต่อ |

## 4. Need Summary

| Need ID | Need statement | Based on E-ID(s) | Notes |
|---|---|---|---|
| N-01 | Student Requester needs to see actual availability before submitting a booking request | E-01 | ยังต้องตรวจแหล่งข้อมูลสถานะ |
| N-02 | Student Requester needs to search/filter resources before choosing what to book | E-02 | อาจเชื่อมกับประเภทห้อง/อุปกรณ์ |
| N-03 | Student Requester and Resource Officer need clear due-date information | E-03 | เกี่ยวกับ late return |
| N-04 | Resource Officer needs complete request information before review | E-04 | เป็นข้อมูลขั้นต่ำของแบบฟอร์ม |
| N-05 | Resource Officer needs risky/exception requests to be escalated | E-05 | ยังต้องยืนยัน authority |

## 5. Unknowns / Follow-up for Week 05

| OQ-ID | Question | Why it matters | Who/what can verify |
|---|---|---|---|
| OQ-01 | จองล่วงหน้าได้กี่วัน | กระทบ rule ใน requirement backlog | Area Manager/Instructor |
| OQ-02 | คนหนึ่งจองพร้อมกันได้กี่รายการ | กระทบ quota และ fairness | Area Manager/Instructor |
| OQ-03 | สถานะว่าง/ไม่ว่างมาจากแหล่งข้อมูลใด | กระทบความน่าเชื่อถือของ availability | Resource Officer / System Admin |
| OQ-04 | คำขอชนตารางเรียนต้องอนุมัติโดยใคร | กระทบ approval workflow | Area Manager/Instructor |
