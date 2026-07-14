# Team Worklog — Week 1 (Example Completed Work)

> บันทึกนี้แสดงหลักฐานการมีส่วนร่วมของสมาชิกและการตัดสินใจสำคัญ ไม่ใช้เพื่อจับเวลาทุกนาที

## ข้อตกลงทีม

- ช่องทางสื่อสาร: Microsoft Teams + Issue ใน Team Repo
- เวลานัดหมาย: วันจันทร์ 16:30–17:15 และหลังคาบ 20 นาที
- วิธีตัดสินใจเมื่อเห็นไม่ตรงกัน: อ้างอิง Case Card/หลักฐานก่อน หากยังไม่มีหลักฐานให้บันทึกเป็น Open Question
- วิธีตรวจงานก่อนส่ง: สมาชิกอย่างน้อย 2 คน review pull request ก่อน merge
- Naming convention: `F-xx`, `P-xx`, `A-xx`, `UR-xx`, `OQ-xx`

## Worklog

| วันที่/เวลา | สมาชิก | งานที่ทำ | หลักฐาน/ลิงก์ | เวลาประมาณ | หมายเหตุ |
|---|---|---|---|---:|---|
| 2569-06-22 13:10 | วรินทร์ | ตั้ง repo, issue และโครง Problem Brief | Issue #1, commit `chore: initialize week01 artefacts` | 25 นาที | ใช้ template จาก Course Repo |
| 2569-06-22 13:35 | ณัฐพล | สกัด stakeholder จาก Case Card | Issue #2, section 4 | 30 นาที | เพิ่มผู้บริหารเป็น stakeholder ที่ต้องตรวจสอบ |
| 2569-06-22 14:05 | ชลิตา | แยก facts/pain points/assumptions | board note + image | 40 นาที | ย้าย “ผู้ใช้ต้องการ mobile app” ไปเป็น assumption/solution idea |
| 2569-06-22 14:45 | ปวีณา | ร่าง goals, starter requirements และ NFR concerns | commit `docs: add goals and starter requirements` | 45 นาที | ยังไม่กำหนดค่าตัวเลขที่ไม่มีหลักฐาน |
| 2569-06-22 15:30 | ทีม | Scope review และ peer check | PR #3 | 30 นาที | ตัด payment, procurement, IoT ออกจาก scope |
| 2569-06-22 16:00 | วรินทร์ + ชลิตา | ตรวจ trace จาก pain point ไป starter requirement | review comment | 20 นาที | เพิ่ม evidence/reason column |
| 2569-06-22 16:25 | ทีม | สรุป open questions และ AI disclosure | commit `docs: complete problem brief v0.1` | 25 นาที | เตรียมใช้ OQ-ID ต่อใน Week 3 |

## Decision Log ย่อ

| Decision ID | การตัดสินใจ | เหตุผล | หลักฐาน | ผู้ร่วมตัดสินใจ |
|---|---|---|---|---|
| D-01 | จำกัด pilot ที่ 1 อาคาร/หน่วยงาน | สอดคล้อง constraint และลด scope | Case Card C-01 | ทั้งทีม |
| D-02 | ไม่ระบุ “ต้องเป็น mobile app” | ยังเป็น solution ไม่ใช่ verified need | review discussion | ทั้งทีม |
| D-03 | Starter requirements ทุกข้อมี evidence/reason | ป้องกันการเขียนจากการคาดเดา | Week 1 rubric | ทั้งทีม |
| D-04 | ยังไม่กำหนดเวลา response เป็นวินาที | ไม่มีข้อมูล workload/expectation | Open Question | ปวีณา, ชลิตา |

## Reflection รายบุคคล (ตัวอย่าง)

- **วรินทร์:** พบว่าการจำกัด scope ทำให้ทีมเขียนเป้าหมายได้ชัดขึ้น
- **ณัฐพล:** Stakeholder ไม่ได้มีเฉพาะผู้ใช้ปลายทาง ผู้กำหนดนโยบายมีผลต่อ requirement มาก
- **ชลิตา:** Facts และ assumptions ต้องติดป้ายต่างกัน ไม่เช่นนั้นทีมจะเชื่อสิ่งที่ตนเองคิดว่าเป็นข้อมูลจริง
- **ปวีณา:** Requirement ที่ดีใน Week 1 ยังเป็น draft ได้ แต่ต้องมีเหตุผลและคำถามสำหรับตรวจสอบต่อ
