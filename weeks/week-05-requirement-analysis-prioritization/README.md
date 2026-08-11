# Week 05: Requirement Analysis and Backlog Prioritization
> **Repository workflow:** อ่านโจทย์จาก Course Repo แต่ทำและส่งงานใน Team Repo ของกลุ่ม  
> [Learning Blueprint TH](ENGSE206_Week05_Learning_Blueprint_TH.md) | [Teaching Notes TH](ENGSE206_Week05_เอกสารประกอบการสอน_TH.md) | [Student Lab Guide](student-lab-guide.md) | [Rubric](rubric.md) | [Prompt Pack](prompt-pack.md) | [เปิด Assignment Contract](assignment-contract.md) | [คู่มือ 2 Repository](../../docs/two-repository-workflow.md)

## ข้อมูลสัปดาห์

| รายการ | รายละเอียด |
|---|---|
| บทเรียน | 3.1 Requirement Analysis, Classification และ Prioritization |
| CLO | CLO2, CLO3 |
| เวลา | ทฤษฎี 2 ชั่วโมง + ปฏิบัติ/กิจกรรม 3 ชั่วโมง |
| รูปแบบ | Trace Check + Card Sorting + Prioritization + Backlog Build |
| ผลงานที่ต้องส่ง | Requirement Backlog v0.1 |

## เป้าหมายการเรียนรู้

แยก Functional Requirement, NFR, Business Rule, Constraint และ Issue จาก Requirement Candidate ของ Week04 จากนั้นจัดลำดับด้วยคุณค่า ความเสี่ยง ความเร่งด่วน และ dependency

เมื่อจบสัปดาห์ นักศึกษาต้องสร้างหลักฐานการเรียนรู้ที่เชื่อมโยงกับ Case Project ของตน ไม่ใช่เพียงทำกิจกรรมตามตัวอย่าง

## ไฟล์หลักของ Week05

| Artifact | File |
|---|---|
| Learning Blueprint | [ENGSE206_Week05_Learning_Blueprint_TH.md](ENGSE206_Week05_Learning_Blueprint_TH.md) |
| Teaching Notes | [ENGSE206_Week05_เอกสารประกอบการสอน_TH.md](ENGSE206_Week05_เอกสารประกอบการสอน_TH.md) / [DOCX](ENGSE206_Week05_เอกสารประกอบการสอน_TH.docx) |
| Teaching Slides | [slides/ENGSE206_Week05_Requirement_Backlog_Slides.pptx](slides/ENGSE206_Week05_Requirement_Backlog_Slides.pptx) |
| Student Lab | [student-lab-guide.md](student-lab-guide.md) |
| Activities | [Trace Check](activities/w05-trace-check.md), [Card Sorting](activities/w05-card-sorting.md), [Prioritization Matrix](activities/w05-prioritization-matrix.md) |
| Case Study | [case-study-campus-resource-booking.md](case-study-campus-resource-booking.md) |
| Prompt Pack | [prompt-pack.md](prompt-pack.md) |
| Rubric | [rubric.md](rubric.md) |

## การเตรียมก่อนเรียน

- อ่าน artefact ของสัปดาห์ก่อนและเปิด repository ของกลุ่มให้พร้อม
- เตรียมแม่แบบ [`templates/05-requirement-backlog.md`](../../templates/05-requirement-backlog.md)
- เปิดตัวอย่าง [Campus Resource Booking Week05](../../examples/campus-resource-booking/week-05/README.md)
- ผู้สอนเตรียม worked example, checklist/rubric และเวลา feedback ระหว่าง workshop

## แผนสอนทฤษฎี 2 ชั่วโมง

### 1) Activate prior knowledge — 15 นาที
- ทบทวนงานสัปดาห์ก่อนด้วยคำถามสั้นหรือ artefact ที่มีข้อผิดพลาด
- เชื่อมสิ่งที่จะเรียนกับ Requirement-to-Design Package ของกลุ่ม

### 2) Mini lecture + worked example — 55 นาที
- Functional/NFR/business rule/constraint
- Quality attributes
- Prioritization with value/risk/urgency/dependency

ผู้สอนควรใช้ Case เดียวตัวอย่าง 1 เรื่อง และแสดงทั้งตัวอย่างที่ดี/ไม่ดีเพื่อให้เห็นเกณฑ์คุณภาพชัดเจน

### 3) Guided analysis — 35 นาที
- ให้กลุ่มวิเคราะห์สถานการณ์สั้น
- ใช้ think-pair-share หรือถามตอบเพื่อทดลองตัดสินใจ
- สรุป misconception สำคัญก่อนปฏิบัติ

### 4) Briefing งานปฏิบัติ — 15 นาที
- อธิบาย output, rubric, commit/submission rule และเวลาส่ง
- ย้ำความต่างระหว่าง **facts**, **assumptions**, **requirements** และ **design choices** ตามหัวข้อของสัปดาห์

## แผน Workshop/LAB 3 ชั่วโมง

1. ตรวจ trace ของ RC จาก Week04
2. card sorting แยก Functional/NFR/Business Rule/Constraint/Issue
3. จัดลำดับ priority พร้อม rationale
4. แยก Ready / Needs Follow-up / Hold
5. ปรับ backlog และ commit

### Checkpoints
- นาทีที่ 45: แสดง output ขั้นต้นให้เพื่อนหรือผู้สอนตรวจ
- นาทีที่ 100: ต้องมี artefact ที่มีโครงสร้างครบ แม้รายละเอียดไม่สมบูรณ์
- นาทีที่ 155: ตรวจ checklist และอธิบายสิ่งที่เปลี่ยนหลังได้รับ feedback
- ก่อนจบ: commit/push หรือส่งลิงก์ตามช่องทางอาจารย์กำหนด

## สิ่งที่ต้องส่ง

1. `docs/05-requirement-backlog.md`
2. `submissions/week-05-submission.md`
3. `project-management/team-worklog.md`
4. `project-management/risk-and-issue-log.md` เมื่อมี unknown/policy/dependency
5. ใช้ commit message: `submit(w05): prioritized requirement backlog`

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
