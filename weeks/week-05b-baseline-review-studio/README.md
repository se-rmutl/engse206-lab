# Week 05b: Requirement Baseline Review & Readiness Gate (Self-Directed Studio)
> **Repository workflow:** อ่านโจทย์จาก Course Repo แต่ทำและส่งงานใน Team Repo ของกลุ่ม
> **รูปแบบพิเศษ:** กิจกรรมนี้ทีมดำเนินการเอง 100% (อาจารย์ไม่อยู่ในคาบ) — เอกสารพาทีมเดินเองได้ตั้งแต่ต้นจนจบ
> [เอกสารกิจกรรม (PDF)](ENGSE206_Requirement_Baseline_Review_Studio_TH.pdf) | [ตัวอย่างเดินทีละขั้น (Case X)](EXAMPLE-baseline-review-walkthrough-casex.md) | [คู่มือ 2 Repository](../../docs/two-repository-workflow.md)

## ข้อมูลกิจกรรม (Assignment Contract)

| Field | Value |
|---|---|
| Assignment ID | `W05-RBR-v1.0` |
| Topic | Requirement Baseline Review & Readiness Gate |
| ประเภท | Consolidation Studio — ทบทวน/ตรวจสอบงาน W1–W5 (ไม่ใช่บทเรียนใหม่) |
| เวลา | 4 ชั่วโมง (ยืดหยุ่น 3–5 ชม.) ทำจบภายในคาบเดียว |
| CLO | CLO2, CLO3 |
| Milestone | **Requirement Baseline v1.0** (commit + `git tag baseline-v1.0`) |
| Student output paths | `docs/05-requirement-backlog.md`, `docs/08-validation-traceability.md`, `evidence/week-05/baseline-review/`, `submissions/baseline-review-submission.md` |
| Submission commit | `submit(w05): lock requirement baseline v1.0` |
| ส่งลิงก์ที่ | Google Sheet คอลัมน์ "Requirement Baseline Review & Readiness Gate" แถว Case ของกลุ่ม |

## เป้าหมายการเรียนรู้

ทีม "หยุดตรวจงานตัวเอง" เพื่อยืนยันว่าสิ่งที่ทำมาใน W1–W5 เข้าใจตรงกัน มีคุณภาพ มีที่มา และเชื่อมโยง (traceable) จริง ก่อนต่อยอดเป็น Requirement Model ใน Week 06

เมื่อจบกิจกรรม ทีมต้องได้ **Baseline v1.0** ที่ตรวจแล้ว มีสาย traceability ครบ และมีรายการ Gap/Open Questions ที่ยกไปทำต่อใน Week 06 — โดยทำเองได้ทั้งหมดโดยไม่ต้องมีอาจารย์คอยบอกทีละขั้น

## ไฟล์หลักของ Week05b

| Artifact | File |
|---|---|
| เอกสารกิจกรรม (ฉบับเต็ม) | [ENGSE206_Requirement_Baseline_Review_Studio_TH.pdf](ENGSE206_Requirement_Baseline_Review_Studio_TH.pdf) / [DOCX](ENGSE206_Requirement_Baseline_Review_Studio_TH.docx) |
| ตัวอย่างเดินทีละขั้น (Case X) | [EXAMPLE-baseline-review-walkthrough-casex.md](EXAMPLE-baseline-review-walkthrough-casex.md) |
| แม่แบบไฟล์ส่งงาน (กรอกในรีโปกลุ่ม) | [`submissions/baseline-review-submission.md`](https://github.com/se-rmutl/engse206-project-template/blob/main/submissions/baseline-review-submission.md) (ใน Team Repo template) |
| Rubric | _(เพิ่มภายหลังถ้ามีเวอร์ชันให้คะแนน)_ |

## การเตรียมก่อนทำกิจกรรม

- เปิด repository ของกลุ่มให้พร้อม และ `git pull origin main` ให้เป็นเวอร์ชันล่าสุด
- เปิดเอกสาร W1–W5 ที่ทำมาแล้ว: `docs/01`–`docs/05`, `evidence/week-01`…`week-05`
- เชิญอาจารย์เป็น **collaborator** ถ้า repo เป็น Private (ไม่งั้นลิงก์ที่ส่งจะเปิดไม่ได้)
- ตรวจว่ามีไฟล์ `submissions/baseline-review-submission.md` ในรีโปหรือยัง — ถ้าไม่มี ดูวิธีสร้างในตัวอย่างเดินทีละขั้น ขั้นที่ 1

## ลำดับการทำงาน 7 ช่วง (สรุป)

| ช่วง | สิ่งที่ทำ | เวลา |
|---|---|---|
| 0 | Setup — เปิด repo/เอกสาร W1–W5 + แบ่งบทบาท | 15' |
| 1 | Artefact Health Check — เช็ก docs/01–05 ครบ/อัปเดต | 40' |
| 2 | Traceability Audit — ไล่ Problem→Evidence→Need→FR/NFR→Priority | 55' |
| 3 | Quality & MoSCoW Check — วัดได้ ไม่กำกวม scope ไม่บวม | 40' |
| 4 | Peer Cross-Review — แลกตรวจกับอีกทีม | 35' |
| 5 | Fix & Lock — แก้ 3 อันดับแรก + commit + tag baseline-v1.0 | 30' |
| 6 | Readiness Gate + Reflection — ผ่านด่าน 5 ข้อ + preview W6 | 25' |

> รายละเอียดแต่ละช่วง กล่อง Self-check และตัวอย่าง Case X อยู่ในเอกสารกิจกรรมฉบับเต็ม (PDF)

## การส่งงาน (สำคัญ: ตรวจง่ายด้วยลิงก์ที่ pin กับ tag)

1. กรอก `submissions/baseline-review-submission.md` ให้ครบ (แนบลิงก์ทุกชิ้นงาน)
2. `git add -A && git commit -m "submit(w05): lock requirement baseline v1.0"`
3. `git tag baseline-v1.0` → `git push` → `git push origin baseline-v1.0`
4. วางลิงก์ไฟล์ส่งงานในเซลล์ Google Sheet คอลัมน์ RBR:
   `<REPO>/blob/baseline-v1.0/submissions/baseline-review-submission.md`

> ทุกลิงก์ต้องชี้ที่ `baseline-v1.0` (ไม่ใช่ `main`) เพื่อให้เป็นสแนปช็อตแช่แข็ง ณ ตอนส่ง
> ขั้นตอนแบบละเอียดพร้อมตัวอย่างจริง ดูที่ [EXAMPLE-baseline-review-walkthrough-casex.md](EXAMPLE-baseline-review-walkthrough-casex.md)

## หมายเหตุสำหรับกลุ่มที่สร้างรีโปไปแล้ว

ถ้ากลุ่มสร้าง Team Repo จาก template **ก่อน** ไฟล์ `baseline-review-submission.md` ถูกเพิ่มเข้า template รีโปของกลุ่มจะยังไม่มีไฟล์นี้ ให้ดาวน์โหลดแม่แบบเข้ารีโปตัวเอง:

```bash
curl -L -o submissions/baseline-review-submission.md \
  https://raw.githubusercontent.com/se-rmutl/engse206-project-template/main/submissions/baseline-review-submission.md
```
