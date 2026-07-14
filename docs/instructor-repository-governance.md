# คู่มือผู้สอน: การดูแล Course Repo และตรวจ Team Repos

## Course Repo เป็น Source of Truth

ผู้สอนควร publish รายสัปดาห์ด้วยโครงเหมือนกันทุก Week:

1. Learning objectives
2. Required reading
3. Case-specific input / prompt pack
4. Workshop steps และเวลา
5. Expected outputs และ exact paths ใน Team Repo
6. Rubric / checklist
7. Submission deadline และ commit convention
8. Assignment version/date

## ก่อนเปิดสัปดาห์ใหม่

- ตรวจ link ภายใน repo
- ระบุว่าไฟล์ใดเป็น required / optional
- ตรวจว่า template repo มี path รองรับแล้ว
- ประกาศ assignment version เช่น `W04-v1.0`
- ไม่เปลี่ยนโจทย์ย้อนหลังโดยไม่บันทึก changelog

## วิธีตรวจงาน

1. เปิด `submissions/submission-register.md`
2. เปิด submission file ของสัปดาห์
3. ใช้ commit hash ที่นักศึกษาระบุเป็น snapshot สำหรับตรวจ
4. ตรวจ artefact, evidence, worklog และ feedback
5. เขียน feedback เป็น Issue/PR comment หรือ feedback file ตามกติกา
6. นักศึกษาแก้ด้วย commit ใหม่ ไม่ rewrite history

## การควบคุม 10 Cases

- ใช้ Case ID 01–10 เป็นรหัสกลาง
- เก็บ assignment sheet ใน `cases/case-assignment-sheet.*`
- Week 3–4 ควรมี AI role/prompt pack แยกตาม Case ID
- rubric และ output path เหมือนกันทุกกลุ่ม แต่เนื้อหาแตกต่างตาม case

## การตรวจความเท่าเทียม

เกณฑ์ต้องวัดคุณภาพกระบวนการและหลักฐาน ไม่วัดว่า case ใดดูซับซ้อนกว่า เช่น:

- ความชัดเจนของ reasoning
- traceability ไปยัง evidence
- stakeholder coverage
- requirement quality
- quality of design rationale
- collaboration evidence
