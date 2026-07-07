# Initial Requirement Candidates — Campus Resource Booking

> **สถานะ:** Initial candidates from Week 03 planning/rehearsal.  
> **ยังไม่ใช่ SRS และยังไม่ใช่ requirement ที่อนุมัติแล้ว**  
> Week 04 จะเก็บ evidence และ Week 05 จะวิเคราะห์/จัดหมวด/ปรับถ้อยคำให้ตรวจสอบได้

| ID | Candidate Type | Initial Candidate | Source / Planned Evidence | Confidence | Open Validation |
|---|---|---|---|---|---|
| RC-F-01 | Functional | ระบบควรให้ผู้ใช้ค้นหาห้องและอุปกรณ์ตามวันที่ ช่วงเวลา ประเภท และความจุ/คุณลักษณะที่เกี่ยวข้อง | Student interview + inventory source | Medium | ข้อมูลใดจำเป็นต่อการตัดสินใจจริง? |
| RC-F-02 | Functional | ระบบควรให้ผู้ใช้ส่งคำขอจอง ยกเลิก และดูสถานะของคำขอตนเองได้ | Student + staff workflow | Medium | เงื่อนไขยกเลิกและช่วงเวลายังไม่ยืนยัน |
| RC-F-03 | Functional | ระบบควรตรวจสอบความขัดแย้งของเวลาและสถานะทรัพยากรก่อนรับคำขอ | Staff workflow + inventory data | Medium | ตรวจระดับห้อง/อุปกรณ์/ผู้ใช้พร้อมกันอย่างไร? |
| RC-F-04 | Functional | ระบบควรรองรับการอนุมัติหรืออนุมัติอัตโนมัติตามประเภททรัพยากรและกฎที่กำหนด | Staff + manager interview | Low | ต้องยืนยัน approval matrix |
| RC-F-05 | Functional | เจ้าหน้าที่ควรเห็นรายการคำขอ งานค้าง และสามารถบันทึกผลอนุมัติ/ปฏิเสธพร้อมเหตุผลได้ | Staff workflow | Medium | รูปแบบรายการค้างและเหตุผลยังไม่ยืนยัน |
| RC-F-06 | Functional | ระบบควรบันทึกการส่งมอบและรับคืนในระดับที่เหมาะกับประเภทอุปกรณ์ | Staff interview | Low | ต้องยืนยันข้อมูล/หลักฐานที่ต้องเก็บ |
| RC-F-07 | Functional | ระบบควรแจ้งผู้ใช้เมื่อคำขอถูกส่ง เปลี่ยนสถานะ อนุมัติ ปฏิเสธ หรือใกล้ถึงเวลาใช้งาน | Student + staff interview | Low | ช่องทาง/เวลาแจ้งยังไม่ยืนยัน |
| RC-F-08 | Functional | ผู้จัดการพื้นที่ควรดูรายงานพื้นฐานเกี่ยวกับการจอง การยกเลิก และ no-show ได้ | Manager interview | Medium | ตัวชี้วัด/ช่วงเวลารายงานยังไม่ยืนยัน |
| RC-NF-01 | Non-functional | ระบบควรใช้บัญชีสถาบันเพื่อยืนยันตัวตนและกำหนดสิทธิ์ตามบทบาท | IT proxy + identity constraints | Medium | รายละเอียด role mapping ยังไม่ยืนยัน |
| RC-NF-02 | Non-functional | ผู้ใช้ควรเห็นเฉพาะข้อมูลคำขอของตน ส่วนเจ้าหน้าที่และผู้จัดการเห็นข้อมูลตามหน้าที่ | Privacy/access analysis + IT | Medium | ต้องตรวจ role-based access matrix |
| RC-NF-03 | Non-functional | สถานะทรัพยากรที่แสดงต้องมีเวลาอัปเดต/แหล่งข้อมูลชัดเจน เพื่อไม่ให้ผู้ใช้ตัดสินใจจากข้อมูลเก่า | Student pain point + inventory source | Low | กำหนด freshness rule กับเจ้าหน้าที่/IT |

## Rule for Week 04–05

เมื่อได้ evidence ใหม่ ให้เพิ่ม `Evidence ID` และปรับ confidence จาก Low/Medium/High พร้อมบันทึกเหตุผล ถ้า evidence ขัดแย้งกันให้บันทึกเป็น issue ไม่ควรเลือกคำตอบตามความเห็นของทีมเพียงฝ่ายเดียว
