# Week 06: Workshop 4: Requirement Modeling and Negotiation Board
> **Repository workflow:** อ่านโจทย์จาก Course Repo แต่ทำและส่งงานใน Team Repo ของกลุ่ม  
> [เปิด Assignment Contract](assignment-contract.md) | [คู่มือ 2 Repository](../../docs/two-repository-workflow.md)

## ข้อมูลสัปดาห์

| รายการ | รายละเอียด |
|---|---|
| บทเรียน | 3.2 User Story, Use Case, Acceptance Criteria และ Requirement Model |
| CLO | CLO3 |
| เวลา | ทฤษฎี 2 ชั่วโมง + ปฏิบัติ/กิจกรรม 3 ชั่วโมง |
| รูปแบบ | Modeling Studio + Negotiation Board |
| ผลงานที่ต้องส่ง | User Stories/Use Cases + Acceptance Criteria + Model |

## เป้าหมายการเรียนรู้

เขียน requirement ที่ตรวจสอบได้ผ่าน user story/use case/acceptance criteria และต่อรอง scope ภายใต้ข้อจำกัด

เมื่อจบสัปดาห์ นักศึกษาต้องสร้างหลักฐานการเรียนรู้ที่เชื่อมโยงกับ Case Project ของตน ไม่ใช่เพียงทำกิจกรรมตามตัวอย่าง

## การเตรียมก่อนเรียน

- อ่าน artefact ของสัปดาห์ก่อนและเปิด repository ของกลุ่มให้พร้อม
- เตรียมแม่แบบที่เกี่ยวข้องจาก [`templates/`](../../templates/README.md)
- ผู้สอนเตรียม worked example, checklist/rubric และเวลา feedback ระหว่าง workshop

## แผนสอนทฤษฎี 2 ชั่วโมง

### 1) Activate prior knowledge — 15 นาที
- ทบทวนงานสัปดาห์ก่อนด้วยคำถามสั้นหรือ artefact ที่มีข้อผิดพลาด
- เชื่อมสิ่งที่จะเรียนกับ Requirement-to-Design Package ของกลุ่ม

### 2) Mini lecture + worked example — 55 นาที
- User story/use case/acceptance criteria
- System context/user flow/domain model
- Ambiguity, conflict และ requirement gap

ผู้สอนควรใช้ Case เดียวตัวอย่าง 1 เรื่อง และแสดงทั้งตัวอย่างที่ดี/ไม่ดีเพื่อให้เห็นเกณฑ์คุณภาพชัดเจน

### 3) Guided analysis — 35 นาที
- ให้กลุ่มวิเคราะห์สถานการณ์สั้น
- ใช้ think-pair-share หรือถามตอบเพื่อทดลองตัดสินใจ
- สรุป misconception สำคัญก่อนปฏิบัติ

### 4) Briefing งานปฏิบัติ — 15 นาที
- อธิบาย output, rubric, commit/submission rule และเวลาส่ง
- ย้ำความต่างระหว่าง **facts**, **assumptions**, **requirements** และ **design choices** ตามหัวข้อของสัปดาห์

## แผน Workshop/LAB 3 ชั่วโมง

1. เขียน user story หรือ use case
2. สร้าง acceptance criteria
3. เขียน user flow/domain/context model
4. จำลอง negotiation ภายใต้ข้อจำกัด
5. ล็อก scope ที่จะเข้ารอบ SRS v1

### Checkpoints
- นาทีที่ 45: แสดง output ขั้นต้นให้เพื่อนหรือผู้สอนตรวจ
- นาทีที่ 100: ต้องมี artefact ที่มีโครงสร้างครบ แม้รายละเอียดไม่สมบูรณ์
- นาทีที่ 155: ตรวจ checklist และอธิบายสิ่งที่เปลี่ยนหลังได้รับ feedback
- ก่อนจบ: commit/push หรือส่งลิงก์ตามช่องทางอาจารย์กำหนด

## สิ่งที่ต้องส่ง

1. อัปเดตไฟล์ใน repository ของกลุ่ม
2. เก็บภาพ/บันทึก/หลักฐานใน `evidence/` เมื่อมีสัมภาษณ์ role-play หรือ test
3. เขียน Team Worklog ระบุผู้รับผิดชอบและงานที่ทำ
4. ใช้ commit message ที่บอกเนื้อหาการเปลี่ยนแปลง

## เกณฑ์ตรวจแบบเร็ว

- [ ] โครงสร้างเอกสารถูกต้องและครบหัวข้อ
- [ ] เนื้อหาสอดคล้องกับ Case Card/หลักฐาน ไม่คิด solution ลอย ๆ
- [ ] ขอบเขตไม่ใหญ่เกินข้อกำหนดรายวิชา
- [ ] มีเหตุผลหรือหลักฐานรองรับ requirement/design decision
- [ ] ทุกคนมีส่วนร่วมที่ตรวจสอบได้
- [ ] ส่งงานครบและตรงเวลา

## การให้ feedback

ใช้คำถามชี้นำ เช่น
- หลักฐานใดสนับสนุนข้อสรุปนี้
- stakeholder คนใดยังไม่ได้พิจารณา
- requirement นี้ตรวจสอบความสำเร็จได้อย่างไร
- design decision นี้ตอบ requirement ข้อใด

ดู [แผนประเมินผล](../../docs/assessment-rubrics.md) และ [Artefact Roadmap](../../docs/artefact-roadmap.md)
