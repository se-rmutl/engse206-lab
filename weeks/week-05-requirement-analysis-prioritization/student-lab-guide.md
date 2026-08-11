# ENGSE206 Week05 Student Lab Guide

> **หัวข้อ:** Requirement Analysis, Classification and Prioritization  
> **เวลาปฏิบัติ:** 3 ชั่วโมง  
> **เป้าหมาย:** สร้าง `docs/05-requirement-backlog.md` จาก Requirement Candidate ของทีม  
> **Repository workflow:** อ่านคำสั่งจาก Course Repo แต่ทำงานและส่งงานใน Team Repo

## 1. สิ่งที่ต้องเปิดก่อนเริ่ม

ใน Team Repo ของกลุ่ม เปิดไฟล์เหล่านี้:

- `docs/04-evidence-log.md`
- `docs/04-requirement-candidates.md`
- `docs/05-requirement-backlog.md`
- `project-management/team-worklog.md`
- `submissions/week-05-submission.md`

ถ้าทีมยังไม่มีไฟล์ Week04 ที่ครบ ให้เริ่มจาก candidate 3-5 ข้อที่มี evidence ชัดที่สุดก่อน

## 2. ผลงานที่ต้องส่ง

| Path | สิ่งที่ต้องมี |
|---|---|
| `docs/05-requirement-backlog.md` | Backlog v0.1 มี Req ID, Source RC, Trace, Type, Priority, Rationale, Status, Week06 Use |
| `project-management/team-worklog.md` | ใครทำอะไร ตรวจอะไร และแก้อะไร |
| `project-management/risk-and-issue-log.md` | policy/unknown/dependency ที่ยังไม่ควรเดา |
| `submissions/week-05-submission.md` | checklist และ reflection ก่อนส่ง |

## 3. Lab Flow

### Step 1 — Select Candidate

เลือก Requirement Candidate จาก Week04 อย่างน้อย 3-5 ข้อ

| RC-ID | Candidate | Evidence / Need | ใช้ต่อหรือไม่ | เหตุผล |
|---|---|---|---|---|
| RC-xx | [คัดลอกแบบย่อ] | E-xx -> N-xx | Yes/No/Hold | [เหตุผล] |

### Step 2 — Trace Check

ตอบคำถามกับทุก RC:

1. หลักฐานใดสนับสนุน RC นี้?
2. หลักฐานเป็น fact, simulated need, constraint, unknown หรือ proposed solution?
3. ประโยค RC เขียนเกินหลักฐานหรือไม่?
4. ต้องถามต่อเรื่องใดก่อนยืนยัน?

ถ้าไม่มี evidence ให้ใส่เป็น `Issue` หรือ `Hold` ก่อน

### Step 3 — Classification

แยกแต่ละรายการเป็น type ที่เหมาะสม

| Type | ใช้เมื่อ | ตัวอย่าง |
|---|---|---|
| Functional | ระบบต้องทำพฤติกรรมหรือ action | ระบบต้องให้ผู้ใช้ค้นหาห้องว่าง |
| NFR | คุณภาพของระบบหรือบริการ | ระบบต้องปกป้องข้อมูลผู้ใช้เท่าที่จำเป็น |
| Business Rule | กฎการทำงานของ domain | คำขอต้องมีข้อมูลขั้นต่ำก่อนส่งพิจารณา |
| Constraint | ข้อจำกัดภายนอกที่ต้องเคารพ | ต้องใช้บัญชีมหาวิทยาลัย |
| Issue | ยังไม่รู้หรือยังยืนยันไม่ได้ | ยังไม่มี policy เรื่อง no-show |

### Step 4 — Prioritize

ใช้ MoSCoW:

- `Must`: ขาดไม่ได้ต่อ workflow รุ่นแรก กฎ หรือความเสี่ยงหลัก
- `Should`: สำคัญมาก แต่ยังมี workaround
- `Could`: มีคุณค่า แต่เลื่อนได้
- `Won't yet`: ยังไม่ทำใน scope นี้ เพราะยังไม่มีหลักฐานหรือยังไม่จำเป็น

ให้เขียน rationale จากอย่างน้อย 2 มิติ: value, risk, urgency, dependency

### Step 5 — Build Backlog v0.1

กรอกตารางหลักใน `docs/05-requirement-backlog.md`

| Req ID | Source RC | Evidence / Need Trace | Requirement Statement | Type | Priority | Rationale | Status | Open Question | Week06 Use |
|---|---|---|---|---|---|---|---|---|---|
| FR-01 | RC-01 | E-01 -> N-01 | ระบบต้อง... | Functional | Must | [เหตุผล] | Ready for Week06 | [ถ้ามี] | Use Case |

### Step 6 — Peer Review

แลกไฟล์กับอีกทีม/อีกคู่ แล้วตรวจ 4 เรื่อง:

- Trace มีจริงหรือไม่
- Type เหมาะสมหรือไม่
- Priority มีเหตุผลหรือไม่
- Issue ถูก hold ไว้หรือถูกเดาเป็น requirement

### Step 7 — Submit

ก่อนส่ง ให้ทำงานใน Team Repo:

```text
git add docs/05-requirement-backlog.md submissions/week-05-submission.md project-management/
git commit -m "submit(w05): prioritized requirement backlog"
git push
```

ถ้ายังไม่ได้ใช้ git ในห้อง ให้ส่ง PDF/ลิงก์ตามที่อาจารย์กำหนด และเก็บไฟล์ใน path เดิมไว้

## 4. Definition of Done

- [ ] Backlog มี requirement อย่างน้อย 3-5 ข้อที่มี trace
- [ ] มี Issue/Hold อย่างน้อย 1 รายการ ถ้ามีสิ่งที่ยังไม่รู้
- [ ] ทุก requirement มี Type และ Priority
- [ ] ทุก Priority มี rationale
- [ ] มีรายการ Ready for Week06
- [ ] ส่ง `submissions/week-05-submission.md`

