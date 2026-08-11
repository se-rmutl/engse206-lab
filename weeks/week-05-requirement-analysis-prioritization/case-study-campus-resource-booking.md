# Case Study Guide — Campus Resource Booking for Week05

> ใช้สาธิตในชั้นเรียนเพื่อแสดงการแปลง Week04 RC เป็น Week05 Backlog v0.1

## 1. Starting Point from Week04

Week04 ให้ผลลัพธ์เป็น:

```text
Evidence E-01..E-14
-> Need / Conflict N-AVAIL..N-MIN-DATA
-> Requirement Candidate RC-01..RC-08
```

Week05 ไม่คัดลอก RC ตรง ๆ แต่ต้องตรวจ 3 อย่าง:

1. RC มีหลักฐานจริงหรือไม่
2. RC เป็น requirement type ใด
3. RC ควร priority เท่าไรและพร้อมใช้ต่อหรือไม่

## 2. Worked Transformation

| Week04 RC | วิเคราะห์ใน Week05 | ผลลัพธ์ |
|---|---|---|
| RC-01 ค้นหาและดูสถานะทรัพยากร | มี fact เรื่องทรัพยากรจำกัดและการจองหลายช่องทาง | `FR-SCRB-01`, Must, Ready |
| RC-03 ตรวจข้อมูลขั้นต่ำ | เป็น business rule ไม่ใช่ function ล้วน | `BR-SCRB-01`, Must, Needs Follow-up |
| RC-04 exception request | เป็น functional capability แต่ authority ยังไม่ชัด | `FR-SCRB-03`, Should, Needs Follow-up |
| RC-05 cancellation/no-show | event record ใช้ได้ แต่ penalty ยังไม่มี policy | `FR-SCRB-04`, Could/Hold |
| RC-08 ใช้ identity/role เท่าที่จำเป็น | เป็น NFR/Constraint ด้าน privacy/security | `NFR-SCRB-01`, Must, Needs IT/Policy Review |

## 3. Instructor Demonstration Script

1. เปิด Week04 Completed Example และชี้ RC-01
2. ถามนักศึกษา: “RC-01 มี evidence ใดรองรับ”
3. แยก type เป็น Functional
4. ให้ priority เป็น Must เพราะเป็น capability หลัก
5. เขียน requirement statement ใหม่ให้ชัดขึ้น แต่ไม่ออกแบบ UI
6. ทำแบบเดียวกันกับ RC-03 เพื่อให้เห็น Business Rule
7. ทำ RC-05 เพื่อให้เห็นว่าเรื่องสำคัญบางเรื่องต้อง Hold หากไม่มี policy

## 4. Student Transfer Question

หลังดูตัวอย่าง ให้นักศึกษาตอบ:

- ใน case ของทีม มี RC ใดเทียบได้กับ capability หลักแบบ RC-01
- มี RC ใดที่เป็น business rule ไม่ใช่ function
- มี policy/unknown ใดที่ควร Hold
- Requirement ใดพร้อมใช้ทำ User Story หรือ Use Case ใน Week06

## 5. Link to Completed Example

ดูตัวอย่างเต็มได้ที่:

- `examples/campus-resource-booking/week-05/05-requirement-backlog.md`
- `examples/campus-resource-booking/week-05/05-prioritization-rationale.md`
- `examples/campus-resource-booking/week-05/05-open-questions-and-issues.md`

