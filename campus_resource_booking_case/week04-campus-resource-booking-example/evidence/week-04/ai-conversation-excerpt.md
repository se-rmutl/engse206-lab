# Week 04 — AI Conversation Excerpt

## Session Information

| Field | Value |
|---|---|
| Date | 21/07/2026 |
| Case | Campus Resource Booking |
| AI role | Student Requester และ Resource Officer |
| Team interviewer(s) | TeamXX |
| Source used | Case card + Week04 role pack + Week03 interview guide |

## Prompt Used

```text
Simulate Student Requester in Campus Resource Booking for a beginner requirements evidence rehearsal.
Use only the supplied case facts and role pack. Answer only from this role's knowledge.
Do not invent policy, numbers, personal data or confidential information.
If something is outside your authority, say that another role must confirm it.
```

## Conversation Excerpt A — Student Requester

| Turn | Question / Answer | Why this matters | Link to E-ID |
|---|---|---|---|
| Q1 | เวลาจะจองห้องทำงานกลุ่มหรืออุปกรณ์ จุดไหนที่สับสนที่สุด | เปิดให้ stakeholder เล่าปัญหาเอง | |
| A1 | นักศึกษามักไม่รู้ว่าห้องหรืออุปกรณ์ว่างจริงไหม ต้องถามเจ้าหน้าที่ก่อน และบางครั้งรู้ทีหลังว่ามีคนขอใช้ช่วงเดียวกัน | ใช้เป็น evidence เรื่องสถานะว่าง/ไม่ว่างและการจองซ้ำ | E-01 |
| Q2 | ถ้าระบบช่วยได้ สิ่งแรกที่อยากเห็นคืออะไร | หา need โดยไม่ชี้นำหน้าจอ | |
| A2 | อยากเห็นรายการทรัพยากรที่ค้นหาได้ พร้อมสถานะว่าจองได้หรือไม่ ก่อนส่งคำขอ | ใช้เป็น evidence เรื่องการค้นหาและสถานะก่อนจอง | E-02 |
| Q3 | มีเหตุการณ์อะไรที่ทำให้การคืนอุปกรณ์เป็นปัญหา | หาเหตุการณ์ตัวอย่าง | |
| A3 | บางครั้งยืม adapter หรือ webcam แล้วคืนช้า เจ้าหน้าที่ต้องตามเอง แต่นักศึกษาก็อาจไม่แน่ใจว่าต้องคืนวันไหน | ใช้เป็น evidence เรื่องวันคืนและการแจ้งเตือน | E-03 |

## Conversation Excerpt B — Resource Officer

```text
Simulate Resource Officer in Campus Resource Booking for a beginner requirements evidence rehearsal.
Use only the supplied case facts and role pack. Explain operational concerns and constraints.
Do not invent official policy or numbers. If policy needs approval, say it must be confirmed by manager/instructor.
```

| Turn | Question / Answer | Why this matters | Link to E-ID |
|---|---|---|---|
| Q4 | ก่อนอนุมัติคำขอ เจ้าหน้าที่ต้องรู้อะไรบ้าง | หา required information | |
| A4 | ต้องรู้ว่าใครรับผิดชอบ ใช้ทรัพยากรอะไร ใช้ช่วงเวลาไหน และจะคืนเมื่อใด ถ้าข้อมูลไม่ครบต้องถามกลับ | ใช้เป็น evidence เรื่องข้อมูลขั้นต่ำของคำขอ | E-04 |
| Q5 | คำขอแบบไหนเสี่ยงที่สุด | หา constraint/exception | |
| A5 | คำขอเร่งด่วนหรือคำขอที่ชนกับตารางเรียนต้องส่งให้ผู้ดูแลหรืออาจารย์ยืนยัน เจ้าหน้าที่ไม่ควรอนุมัติเองทุกกรณี | ใช้เป็น evidence เรื่องเงื่อนไขส่งต่อ/approval | E-05 |
| Q6 | เรื่องใดที่ยังไม่สามารถยืนยันได้จาก role นี้ | หา unknown | |
| A6 | ระยะเวลาจองล่วงหน้าและจำนวนครั้งที่จองได้ต่อคนต้องให้ผู้ดูแลพื้นที่กำหนด | ใช้เป็น unknown สำหรับ Week05 | E-06 |

## Team Notes

- Evidence ที่ใช้ได้ทันที: E-01 ถึง E-05
- Unknown สำคัญ: ระยะเวลาจองล่วงหน้า, โควตาการจอง, กฎกรณี no-show
- ข้อควรระวัง: ยังไม่มี policy จริง จึงห้ามเขียนว่า “ระบบต้องบังคับใช้กฎ X” แบบ final
