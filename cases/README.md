# Case Project ทั้ง 10 เรื่อง

Case Cards ชุดนี้เป็นโจทย์มาตรฐานสำหรับแจกกลุ่มละ 1 เรื่องตั้งแต่ Week 1 และใช้ต่อยอดตลอดภาคเรียน

## วิธีแจกโจทย์

- อาจารย์สุ่มหรือกำหนดให้กลุ่มละ 1 Case
- หากมีน้อยกว่า 10 กลุ่ม ให้เลือกใช้เฉพาะ Case ที่เหมาะกับขนาดชั้นเรียน
- หากมีมากกว่า 10 กลุ่ม อาจใช้ Case เดิมซ้ำได้เฉพาะเมื่อกำหนด constraint/บทบาท stakeholder ต่างกันชัดเจน
- นักศึกษาห้ามเปลี่ยนโจทย์หลัง Week 2 เว้นแต่ได้รับอนุมัติจากอาจารย์

| Case | โจทย์ | ลิงก์ |
|---:|---|---|
| 01 | ระบบจองพื้นที่ทำงานกลุ่มและอุปกรณ์การเรียนรู้ | [เปิด Case Card](01-group-space-and-learning-equipment-booking.md) |
| 02 | ระบบแจ้งซ่อมอุปกรณ์ในห้องเรียนและห้องปฏิบัติการ | [เปิด Case Card](02-classroom-and-lab-maintenance-reporting.md) |
| 03 | ระบบจองคิวและติดตามสถานะเครื่องซักผ้าหอพัก | [เปิด Case Card](03-dorm-laundry-queue-and-status.md) |
| 04 | ระบบจัดการคิวร้านอาหารหรือร้านเครื่องดื่มในมหาวิทยาลัย | [เปิด Case Card](04-campus-food-queue-and-preorder.md) |
| 05 | ระบบแจ้งของหาย–พบของในมหาวิทยาลัย | [เปิด Case Card](05-campus-lost-and-found.md) |
| 06 | ระบบลงทะเบียนและเช็กอินกิจกรรมของหลักสูตร | [เปิด Case Card](06-program-event-registration-checkin.md) |
| 07 | ระบบติดตามงานกลุ่มและการแบ่งบทบาทสมาชิก | [เปิด Case Card](07-student-teamwork-task-tracking.md) |
| 08 | ระบบยืม–คืนอุปกรณ์กีฬาและกิจกรรม | [เปิด Case Card](08-sports-equipment-borrowing.md) |
| 09 | ระบบนัดหมายเข้าพบอาจารย์ที่ปรึกษา | [เปิด Case Card](09-advisor-appointment.md) |
| 10 | ระบบแจ้งปัญหาพื้นที่ส่วนกลางและติดตามการแก้ไข | [เปิด Case Card](10-common-area-issue-reporting.md) |

## เอกสารประกอบ

- [ใบจัดสรร Case ให้แต่ละกลุ่ม](case-assignment-sheet.md)
- [CSV สำหรับกรอกการจัดสรร](case-assignment-sheet.csv)
- [วิธีใช้ Semester Project Case](../docs/semester-project-method.md)

## ใช้ Case ใน Week 04

- เปิด Case Card ของกลุ่มควบคู่กับ Role Pack ที่ตรงกันใน `weeks/week-04-stakeholder-simulation-negotiation/role-packs/`
- ใช้ AI เป็น stakeholder จำลองตาม Role Pack แล้วคัดเฉพาะบทสนทนาที่เป็นประโยชน์ลงใน AI Conversation Excerpt
- แยกข้อความเป็น Evidence ก่อนสรุปเป็น Need และ Requirement Candidate; ไม่ข้ามจากคำตอบของ AI ไปเป็น requirement ทันที
- ผลลัพธ์ Week 04 คือ Evidence Log และ Requirement Candidates ซึ่งยังไม่ใช่ requirement final
- ดูตัวอย่างทำครบกระบวนการได้ที่ [`campus_resource_booking_case/week04-campus-resource-booking-example/`](../campus_resource_booking_case/week04-campus-resource-booking-example/)
