# ตัวอย่างการส่งงาน Baseline Review — เดินทีละขั้น (Case X)

> **นี่คือ "ตัวอย่างกลาง" (Case X = SE Career Talk)** ทำให้ดูเป็นตัวอย่างเท่านั้น — ไม่ใช่คำตอบของกลุ่มใด
> ให้แต่ละกลุ่มทำ **ขั้นตอนเดียวกัน** กับ Case ของตัวเอง โดยเปลี่ยนชื่อ repo / ID / เนื้อหาให้เป็นของกลุ่ม
>
> สมมติกลุ่มตัวอย่างใช้ repo:
> `https://github.com/se-rmutl/ENGSE206-GroupX-CareerTalk`
> ต่อไปนี้จะเขียนย่อว่า **`<REPO>`**

---

## ภาพรวม 6 ขั้น (ทำจากบนลงล่าง)

```
[1] กรอกไฟล์ส่งงาน   →  [2] commit  →  [3] tag baseline-v1.0
        →  [4] push ทั้ง code และ tag  →  [5] เช็กลิงก์เปิดได้
        →  [6] วางลิงก์ในเซลล์ Google Sheet (คอลัมน์ RBR)
```

**กฎเหล็กข้อเดียว:** ทุกลิงก์หลักฐานต้องชี้ที่ `baseline-v1.0` (ไม่ใช่ `main`)
เพราะ `main` จะขยับเมื่อแก้ไฟล์ทีหลัง แต่ `baseline-v1.0` คือสแนปช็อตแช่แข็ง ณ ตอนส่ง

---

## ขั้นที่ 1 — กรอกไฟล์ส่งงานให้ครบก่อน

เปิดไฟล์ `submissions/baseline-review-submission.md` แล้วกรอกให้ครบ
**เคล็ดลับ:** พิมพ์ URL แบบ `<REPO>/blob/baseline-v1.0/...` ได้เลย ไม่ต้องรอสร้าง tag ก่อน
เพราะรูปแบบ URL คาดเดาได้ (เดี๋ยวขั้นที่ 3–4 เราจะสร้าง tag นี้จริง)

ตัวอย่างไฟล์ที่กรอกเสร็จแล้วของ Case X (ดูเป็นแนวทาง):

```markdown
# Baseline Review Submission — Case X (SE Career Talk)

## 1. Assignment Source
| Field | Value |
|---|---|
| Case ID | Case X · SE Career Talk (Multi-Resource Event Booking) |
| Baseline tag | baseline-v1.0 |
| Tag URL | https://github.com/se-rmutl/ENGSE206-GroupX-CareerTalk/releases/tag/baseline-v1.0 |
| Submitted at | 2026-08-20 15:30 |

## 2. Deliverables (ลิงก์ pin ที่ baseline-v1.0)
| # | ชิ้นงาน | ลิงก์ | ✔ |
|---:|---|---|:--:|
| 1 | Backlog | .../blob/baseline-v1.0/docs/05-requirement-backlog.md | ✅ |
| 2 | Traceability + Gap | .../blob/baseline-v1.0/docs/08-validation-traceability.md | ✅ |
| 3 | Health Check + Cross-Review | .../tree/baseline-v1.0/evidence/week-05/baseline-review/ | ✅ |
| 4 | Decision log | .../blob/baseline-v1.0/project-management/decision-log.md | ✅ |
| 5 | Team worklog | .../blob/baseline-v1.0/project-management/team-worklog.md | ✅ |
| 6 | Reflection รายคน | .../blob/baseline-v1.0/feedback/15-individual-reflection.md | ✅ |

## 3. Traceability Highlights — 3 Must (ลิงก์เจาะจงบรรทัด)
| Req ID | ลิงก์ (line anchor) | Evidence | Priority |
|---|---|---|---|
| FR-05 | .../blob/baseline-v1.0/docs/05-requirement-backlog.md#L44-L52 | E-07 | Must |
| FR-08 | .../blob/baseline-v1.0/docs/05-requirement-backlog.md#L54-L61 | E-07 | Must |
| FR-01 | .../blob/baseline-v1.0/docs/05-requirement-backlog.md#L20-L28 | E-02 | Must |

## 4. Readiness Gate (5 ข้อ)
| # | เกณฑ์ | ผ่าน? |
|---:|---|:--:|
| 1 | docs/01–05 ครบและอัปเดตล่าสุด | ✅ |
| 2 | ทุก Must ลากถึง Evidence + Stakeholder | ✅ |
| 3 | FR/NFR ทุกข้อวัด/ทดสอบได้ ไม่กำกวม | ✅ |
| 4 | ผ่าน Peer Cross-Review 1 รอบ | ✅ |
| 5 | commit + tag baseline-v1.0 แล้ว | ✅ |

## 5. Gap / Open Questions (ยกไป Week 6)
- [ ] OQ-01: ต้องรองรับการจองซ้อนที่ "อนุญาตให้ทับได้บางกรณี" ไหม? (รอถามเจ้าของงาน)

## 7. Final Submission Snapshot
| Field | Value |
|---|---|
| Commit message | submit(w05): lock requirement baseline v1.0 |
| Commit hash | a1b2c3d |
| Tag pushed? | ✅ |
```

> วิธีดูเลขบรรทัด (`#L44-L52`) แบบง่าย: เปิดไฟล์ `docs/05-requirement-backlog.md` ใน VS Code
> เลขบรรทัดอยู่ทางซ้ายมือ — จด "บรรทัดเริ่ม–บรรทัดจบ" ของ FR-05 มาใส่ได้เลย
> (ถ้ายังไม่ถนัด ข้ามส่วน `#L__-L__` ไปก่อน ใช้ลิงก์ทั้งไฟล์แล้วเขียนกำกับว่า "ดู FR-05" ก็ได้)

---

## ขั้นที่ 2 — commit งานทั้งหมด (รวมไฟล์ส่งงาน)

เปิด Terminal (macOS) หรือ Git Bash (Windows) ที่โฟลเดอร์ repo แล้วพิมพ์:

```bash
git add -A
git commit -m "submit(w05): lock requirement baseline v1.0"
```

ผลที่ควรเห็น (ประมาณนี้):

```text
[main a1b2c3d] submit(w05): lock requirement baseline v1.0
 6 files changed, 128 insertions(+), 12 deletions(-)
```

> **สำคัญ:** commit ไฟล์ส่งงาน *ก่อน* สร้าง tag — เพื่อให้ tag ครอบไฟล์ส่งงานไว้ด้วย
> ลิงก์เดียวในชีต (ที่ชี้ไฟล์ส่งงานที่ tag) จะเปิดเห็นงานทั้งชุดแบบแช่แข็ง

---

## ขั้นที่ 3 — สร้าง tag `baseline-v1.0`

```bash
git tag baseline-v1.0
```

เช็กว่า tag ถูกสร้างแล้ว:

```bash
git tag
```
```text
baseline-v1.0
```

---

## ขั้นที่ 4 — push ทั้ง code และ tag ขึ้น GitHub

```bash
git push
git push origin baseline-v1.0
```

ผลที่ควรเห็นบรรทัดท้าย ๆ (ประมาณนี้):

```text
 * [new tag]         baseline-v1.0 -> baseline-v1.0
```

ตอนนี้บน GitHub จะมี tag ให้เลือกแล้ว ทุกลิงก์ `.../blob/baseline-v1.0/...` เปิดได้จริง

---

## ขั้นที่ 5 — เช็กลิงก์ว่าเปิดได้ (ก่อนส่ง)

1. เปิดเบราว์เซอร์ กด `.../blob/baseline-v1.0/submissions/baseline-review-submission.md`
2. เปิดใน **หน้าต่าง Incognito** (ไม่ล็อกอิน) — ถ้าเปิดได้ = ลิงก์ใช้ได้จริง
3. ถ้า repo เป็น **Private** อาจารย์ต้องถูกเชิญเป็น **collaborator** ก่อน จึงจะเปิดลิงก์ได้
   (Settings → Collaborators → เพิ่มบัญชีอาจารย์)

**อยากได้ลิงก์เจาะจงบรรทัดแบบเป๊ะ ๆ (ทางเลือก):**
เปิดไฟล์บน GitHub ที่ tag `baseline-v1.0` → คลิกเลขบรรทัดซ้ายมือ (กด `Shift` ค้างคลิกอีกบรรทัดเพื่อเลือกช่วง)
→ กดปุ่ม `...` → **Copy permalink** แล้วเอา URL นั้นไปแทน (จะได้ `#L44-L52` ให้อัตโนมัติ)

---

## ขั้นที่ 6 — วางลิงก์ในเซลล์ Google Sheet (คอลัมน์ RBR)

ในชีตรวมของรายวิชา ให้หาคอลัมน์ **"Requirement Baseline Review & Readiness Gate"**
แล้ววางลิงก์ในเซลล์ **แถวเดียวกับ Case ของกลุ่ม**

```
          | ... | Week05           | Requirement Baseline Review |
          |     | requirement &    | & Readiness Gate            |
          |     | Backlog          |  <-- คอลัมน์นี้              |
  --------+-----+------------------+-----------------------------
  Case X  | ... | ส่งงานที่นี่      |  [ ส่งงานที่นี่ ]  <-- ใส่ตรงนี้
```

ขั้นตอนใส่ลิงก์ (Google Sheets):

1. **คลิกเซลล์** ในคอลัมน์ RBR ตรงแถว Case ของกลุ่ม
2. เมนู **Insert → Link** (หรือกด `Ctrl+K` / `⌘+K` หรือคลิกไอคอนโซ่บนทูลบาร์)
3. ช่อง **Link:** วาง
   `https://github.com/se-rmutl/ENGSE206-GroupX-CareerTalk/blob/baseline-v1.0/submissions/baseline-review-submission.md`
4. ช่อง **Text:** พิมพ์ `ส่งงานที่นี่` (ให้เหมือนคอลัมน์อื่น)
5. กด **Apply**
6. **ทดสอบ:** คลิกลิงก์ในเซลล์ → ต้องเด้งไปหน้าไฟล์ส่งงานบน GitHub ได้

> วางลิงก์ **ไฟล์ส่งงาน** อันเดียวพอ — เพราะในไฟล์นั้นมีลิงก์ไปทุกชิ้นงานอยู่แล้ว
> อาจารย์เปิดเซลล์เดียว แล้วคลิกไล่ตรวจได้ครบ

---

## เช็กลิสต์ก่อนถือว่าเสร็จ

- [ ] กรอก `submissions/baseline-review-submission.md` ครบทุกช่อง
- [ ] `git commit` แล้ว (ไฟล์ส่งงานอยู่ใน commit นี้)
- [ ] `git tag baseline-v1.0` แล้ว
- [ ] `git push` และ `git push origin baseline-v1.0` แล้ว
- [ ] เปิดลิงก์ใน Incognito ได้ทุกอัน (repo Private = เชิญอาจารย์แล้ว)
- [ ] วางลิงก์ในเซลล์ Google Sheet คอลัมน์ RBR แถว Case ของกลุ่ม และคลิกเปิดได้

---

## ถ้าต้องแก้หลังส่ง (มี feedback)

อย่าแก้ commit เดิม ให้สร้าง commit ใหม่แล้วบันทึกไว้ในไฟล์ส่งงาน (หัวข้อ Revision after Feedback):

```bash
git add -A
git commit -m "fix(w05): revise FR-05 acceptance after peer feedback"
git tag baseline-v1.1
git push && git push origin baseline-v1.1
```

แล้วอัปเดตลิงก์ในชีตให้ชี้ `baseline-v1.1` (หรือแจ้งอาจารย์ว่ามีเวอร์ชันใหม่)
