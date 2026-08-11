# 05 — Prioritization Rationale: Campus Resource Booking

> ไฟล์นี้อธิบาย “ทำไม” requirement แต่ละข้อจึงได้ priority ตามที่กำหนด เพื่อให้นักศึกษาเห็นว่าการจัดลำดับไม่ใช่การเดาหรือเลือกตามความชอบ

## 1. หลักคิด

ทีมใช้ 4 คำถามกับทุก requirement:

1. **Value:** ใครได้ประโยชน์โดยตรง และประโยชน์นั้นเกี่ยวกับปัญหาหลักหรือไม่
2. **Risk:** ถ้าไม่ทำ จะเกิด conflict, delay, wrong decision หรือ privacy risk หรือไม่
3. **Urgency:** ต้องใช้ใน workflow รุ่นแรกหรือยังรอได้
4. **Dependency:** ต้องรอ policy, authority, IT integration หรือข้อมูลเพิ่มหรือไม่

## 2. เหตุผลราย requirement

| Req ID | Priority | เหตุผลหลัก | Trade-off / Dependency |
|---|---|---|---|
| FR-SCRB-01 | Must | ถ้าไม่มีการค้นหาและดูสถานะก่อนยื่นคำขอ ระบบจะไม่แก้ปัญหาจองซ้ำและตรวจสถานะยาก | ต้องระบุข้อมูลขั้นต่ำที่ต้องแสดง แต่ไม่ต้องออกแบบ UI ใน Week05 |
| FR-SCRB-02 | Should | Draft ช่วยลดงานกรอกซ้ำและลดการถามกลับ | ต้องกำหนด lifetime/visibility ของ draft ก่อนเป็น rule สมบูรณ์ |
| BR-SCRB-01 | Must | ข้อมูลขั้นต่ำเป็น gate สำคัญก่อนเจ้าหน้าที่พิจารณา | ยังต้องถามเจ้าหน้าที่ว่าข้อมูลใด “ขั้นต่ำจริง” |
| FR-SCRB-03 | Should | Exception สำคัญต่อกรณีเรียน/กิจกรรมพิเศษ แต่ห้าม auto override โดยไม่มี authority | ต้องมี authority matrix และ communication rule |
| FR-SCRB-04 | Could | event record เรื่อง cancel/no-show มีคุณค่า แต่ policy ยังไม่ชัด | penalty, quota, duration ต้อง hold |
| FR-SCRB-05 | Should | การส่งมอบ/รับคืนมี fact รองรับและช่วย accountability | รูปถ่ายทุกครั้งยังไม่ควรถูกบังคับ เพราะเป็น proposed solution และมี privacy concern |
| FR-SCRB-06 | Should | การแจ้งเตือนลดความไม่แน่นอน แต่ channel/timing ยังไม่ยืนยัน | ต้องแยก event ที่ต้องแจ้งจากช่องทางแจ้ง |
| NFR-SCRB-01 | Must | data minimization เป็นข้อจำกัดคุณภาพ/ความปลอดภัยที่ครอบ requirement หลายข้อ | ต้องให้ IT/policy owner ยืนยัน boundary |
| ISSUE-SCRB-01 | Won't yet | ไม่มีหลักฐานตัวเลขและ policy | ใช้เป็น follow-up ไม่ใช่ requirement |
| ISSUE-SCRB-02 | Won't yet | integration ยังเป็น assumption | ต้องออกแบบ backlog ที่ไม่พึ่ง real-time integration ก่อน |

## 3. สิ่งที่ไม่ได้เลือกเป็น requirement ทันที

| สิ่งที่พบใน Week04 | เหตุผลที่ยังไม่กำหนดเป็น requirement |
|---|---|
| ใช้ LINE/email/QR เป็นช่องทางหลัก | เป็น channel preference ไม่ใช่ need ที่ยืนยันแล้ว |
| ถ่ายรูปทุกครั้งตอนรับคืน | เป็น proposed solution และอาจกระทบ privacy |
| กำหนด penalty no-show | ยังไม่มี policy source |
| อ่านตารางเรียน real-time | ยังไม่มีหลักฐานว่า integration ทำได้ |
| auto override คำขอเดิม | อาจกระทบ fairness และ authority; ต้องมี policy ก่อน |

## 4. บทเรียนสำหรับนักศึกษา

- Priority สูงไม่ได้แปลว่ารายละเอียดครบแล้วเสมอไป
- Requirement ที่สำคัญแต่ยังขาด policy อาจเป็น `Needs Follow-up`
- Issue ที่สำคัญมากอาจต้องเป็น `Hold` หากยังไม่มี evidence
- Backlog ที่ดีช่วยบอกว่า “ทำอะไรต่อได้” และ “อะไรยังไม่ควรเดา”

