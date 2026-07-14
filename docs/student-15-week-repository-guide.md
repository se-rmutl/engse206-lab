# คู่มือนักศึกษา: อ่านจาก Course Repo และส่งใน Team Repo ตลอด 15 สัปดาห์

## 1. Repository ที่ต้องเปิดสองแท็บ

- Course/Lab Repo: https://github.com/se-rmutl/engse206-lab-v2
- Team Repo: repository ของกลุ่มที่สร้างจาก https://github.com/se-rmutl/engse206-project-template

## 2. ก่อนเริ่ม Week 1

1. กด **Use this template** เพื่อสร้าง Team Repo
2. ตั้งชื่อ `ENGSE206-GroupXX-ProjectName`
3. เพิ่มสมาชิกทุกคนและอาจารย์ตามที่กำหนด
4. กรอก `TEAM.md`, `CASE_CARD.md`, `COURSE_REPOSITORY.md`
5. กรอก Case ID และลิงก์ Case Card จาก Course Repo
6. เปิด `submissions/submission-register.md`

## 3. ขั้นตอนประจำสัปดาห์

### A. อ่านโจทย์
เปิด Week ที่กำลังเรียนใน Course Repo และอ่านให้ครบ: objective, steps, expected output, rubric และ deadline

### B. วางแผนงาน
สร้าง Issue/Project item ระบุ Week, Owner, Status และ Evidence Path

### C. ทำงานใน Team Repo
แก้ไฟล์ตาม path ที่ระบุ ห้ามสร้างเอกสารซ้ำโดยไม่จำเป็น

### D. เก็บหลักฐาน
- ภาพ/บันทึก/diagram export → `evidence/week-XX/`
- การใช้ AI → `project-management/ai-use-log.md`
- การประชุม/การตัดสินใจ → `project-management/meeting-minutes/` และ `decision-log.md`

### E. ตรวจและส่ง
กรอก `submissions/week-XX-submission.md`, commit ด้วยข้อความมาตรฐาน และ push ขึ้น GitHub

## 4. Definition of Done

- [ ] อ่านคำสั่งงานฉบับล่าสุดและบันทึก URL/วันที่แล้ว
- [ ] ไฟล์หลักอยู่ใน path ที่กำหนด
- [ ] diagram มี source `.drawio` และ export `.png`/`.pdf`
- [ ] มี evidence และลิงก์ย้อนกลับจากเอกสาร
- [ ] สมาชิกทุกคนมี worklog/commit หรือบทบาทที่ตรวจสอบได้
- [ ] มี peer/instructor feedback และระบุสิ่งที่แก้
- [ ] submission file ระบุ commit hash ฉบับส่ง
- [ ] push ขึ้น remote แล้วและลิงก์เปิดได้

## 5. การแก้ไขหลังส่ง

ห้ามแก้ commit เดิม ให้สร้าง commit ใหม่ เช่น

```text
fix(w04): revise conflict record after instructor feedback
```

จากนั้นบันทึกใน submission file ว่าแก้อะไร เพราะอะไร และ commit ใหม่คืออะไร
