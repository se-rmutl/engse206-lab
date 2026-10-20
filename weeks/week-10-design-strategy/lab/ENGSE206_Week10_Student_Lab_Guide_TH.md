# ENGSE206 Week 10 — Student Lab Guide (Design Strategy)

> **หัวข้อ:** 5.1 Design Strategy — "รุ่นแรกจะสร้างอะไร และอะไรห้ามพลาด?"
> **เวลาปฏิบัติ:** 180 นาที (เริ่มในห้อง ทำต่อที่บ้าน ส่งก่อนคาบ W11)
> **Assignment:** `W10-v1.0` · **CLO:** CLO5
> **ผลงานที่ต้องส่ง:** `design/10-design-strategy.md` + `design/00-design-spine.md` + `submissions/week-10-submission.md`
> **Repository workflow:** อ่านคำสั่งจาก Course Repo แต่ทำงานและส่งงานใน Team Repo ของกลุ่ม

---

## 0. Lab นี้ทำอะไร (อ่านก่อนเริ่ม)

> **ก่อนเริ่ม** เปิด [ตัวอย่าง CRBS](../reference/CRBS_W10_Design_Strategy_Completed_Example_TH.md) ดู CRBS เป็นตัวอย่าง — สังเกตกล่อง 🟦 "มาลองทำไปด้วยกัน" ที่เล่าว่าอาจารย์คิดยังไงในแต่ละขั้น เราจะทำแบบเดียวกันกับ case ของเรา

วันนี้ทีมจะตอบ 4 คำถามให้ **case ของตัวเอง** (ไม่ใช่ CRBS — CRBS คือตัวอย่างที่อาจารย์ทำให้ดู):

1. **เส้นทางงานหลักหนึ่งชิ้น** ของระบบคืออะไร → ได้ **Design Spine**
2. รุ่นแรกจะสร้างอะไรก่อน อะไรทีหลัง → ได้ **scope table** (Build now / Overview / Later / ไม่ทำ)
3. **3 เรื่องที่ถ้าออกแบบพลาด ระบบพัง** คืออะไร → ได้ **design drivers**
4. เรื่องที่ยังไม่รู้คำตอบ จะทำอย่างไรระหว่างรอ → ได้ **open decisions**

> **สิ่งที่ยังไม่ต้องทำวันนี้:** เลือก architecture, เลือกเทคโนโลยี/ฐานข้อมูล/framework, ทำ decision matrix ยาว, ออกแบบหน้าจอ — เก็บไว้ W11–W13

**ศัพท์ที่จะใช้** (คงคำอังกฤษ แต่แปลกำกับครั้งแรก): **increment** = รุ่นแรก · **design driver** = เรื่องที่ถ้าพลาดแล้วพัง · **design spine** = แกนกลางเส้นทางงานหลัก · **open decision** = เรื่องที่ยังไม่มีคำตอบแต่ออกแบบต่อได้ · **TBD** = ยังไม่กำหนด

---

## 1. สิ่งที่ต้องเปิดก่อนเริ่ม (Step 0 — 10 นาที)

ใน Team Repo ของกลุ่ม เปิดไฟล์เหล่านี้ค้างไว้ทั้งคาบ:

- `docs/05-requirement-backlog.md` (FR/BR/NFR/DR ของทีม)
- `docs/06-requirement-models.md` (US/UC/AC และ state จาก W06)
- `docs/07-srs-v1.md` (SRS ของทีม — ดูสถานะและ Open Issues)
- `docs/08-validation-traceability.md` (finding/OI จาก W08 ถ้ามี)
- คัดลอกแม่แบบจาก [`templates/`](../../../templates/README.md) (`10-design-strategy.md` · `00-design-spine.md`) หรือจาก Team Repo template มาไว้ที่ `design/10-design-strategy.md`, `design/00-design-spine.md`, `submissions/week-10-submission.md`

> **ถ้า input ทีมไม่พร้อม** (เช่น W06 มี UC ไม่ครบ): ให้ Spine ใช้ UC ที่มี แล้วเขียนแถวที่ยังไม่มี UC เป็น "ต้องเติม model" ไว้ใน open decision — **ไม่ต้องกลับไปทำ W06 ใหม่ในคาบนี้**

---

## 2. ตารางเวลา Lab 180 นาที (ทำเป็นกลุ่ม)

| ช่วง | นาที | กิจกรรม | Worksheet |
|---|---:|---|---|
| Step 0 เปิดของเดิม | 10 | เปิด backlog W05, model W06, SRS W07, OI/finding W08; เปิด template W10 | — |
| **A Journey walk** | 35 | บนกระดาน/sticky: เขียนเส้นทาง "งานหลักหนึ่งชิ้น" ของ case 5–8 ขั้น เรียงตามผู้ใช้ทำจริง; แต่ละคนรับ 1–2 ขั้น ไปหา UC/AC ที่ตรงจาก W06 → พิมพ์ลง Spine | W10-A |
| **B Scope sort** | 35 | การ์ด FR/UC ของทีม เรียงเป็น 4 กอง Build now / Overview / Later / ไม่ทำ; ทุกการ์ดมีเหตุผล 1 บรรทัด; Build now ต้องเป็นวงจรที่ "จบงานได้" 1 รอบ | W10-B |
| **Checkpoint 1** (นาที 80) | 10 | **Gallery walk 2 นาที**: ทีมข้าง ๆ ดู Spine + กอง ถาม 1 คำถาม "ทำไมข้อนี้อยู่กองนี้" (ไม่บันทึกเป็น peer review) | — |
| **C Drivers** | 35 | แต่ละคนเขียน 1 ข้อ "ถ้าออกแบบพลาดตรงนี้ ระบบพัง" อ้าง BR/NFR/FR; โหวตเหลือ 3; เขียนผลต่อ W11/12/13 | W10-C |
| **D Open decisions** | 30 | จาก OI ของ SRS ทีม + สิ่งที่ยังไม่รู้ตอน sort: เขียน DD ≤ 5 พร้อมเจ้าของ/ผลกระทบ/ระหว่างรอทำอย่างไร; **ห้ามแต่งตัวเลข** | W10-D |
| **Checkpoint 2** (นาที 160) | 10 | Done checklist 6 ข้อ; ผู้สอนเดินดู | Done checklist |
| ปิด | 15 | commit ร่าง; แบ่งงานการบ้าน; นัดส่ง | — |

---

## 3. คำอธิบายแต่ละกิจกรรม

### Activity A — Journey Walk (35 นาที) → `design/00-design-spine.md`

**เป้าหมาย:** ได้เส้นทาง "งานหลักหนึ่งชิ้น" ของระบบ 5–8 ขั้น เรียงตามที่ **ผู้ใช้ทำจริง** (ไม่ใช่เรียงตามหน้าจอ หรือตามตารางข้อมูล)

1. บนกระดาน/กระดาษ เขียนชื่อ "งานหลักหนึ่งชิ้น" ของ case เช่น *ยืมอุปกรณ์กีฬา 1 ครั้ง* หรือ *นัดพบอาจารย์ 1 ครั้ง* (เลือกงานที่วิ่งจากต้นจนจบ)
2. ช่วยกันเขียนขั้นที่ผู้ใช้/ระบบทำ เรียงจากต้น → จบ (ค้นหา/เริ่ม → กรอก/ส่ง → ตรวจ/ตัดสิน → ดูสถานะ → จบงาน)
3. **แบ่งงาน (role rotation):** แต่ละคนรับ 1–2 ขั้น ไปเปิด `docs/06-requirement-models.md` หา **UC** และ **AC** ที่ตรงกับขั้นนั้น
4. พิมพ์ลงตารางใน `design/00-design-spine.md` คอลัมน์: #, ขั้นในเส้นทาง, Actor, UC, AC หลัก, W10 ระดับ (เว้น W11–13 ว่างไว้)

> **เกณฑ์ผ่าน:** 5–8 แถว, ทุกแถวมี actor + UC, เรียงตามผู้ใช้ทำจริง
> **ดูตัวอย่าง:** CRBS Spine 7 แถว ใน [ตัวอย่าง CRBS](../reference/CRBS_W10_Design_Strategy_Completed_Example_TH.md) (ค้นหา → Draft → Submit → ตัดสิน/Confirmed → ดูสถานะ → Check Out → Return)

### Activity B — Scope Sort (35 นาที) → `design/10-design-strategy.md` หัวข้อ 2

**เป้าหมาย:** จัด FR/UC ของทีมเป็น 4 กอง โดย **ไม่ลบอะไรออกจาก SRS**

1. เขียนการ์ด (sticky หรือพิมพ์) ใบละ 1 FR หรือ 1 UC ของทีม
2. วางเป็น 4 กอง:
   - **Build now** = Dev เริ่มเขียนได้หลัง W13 (ต้องรวมกันเป็น "วงจรที่จบงานได้ 1 รอบ")
   - **Overview** = อยู่ในภาพรวม/ข้อมูล/กติกา แต่ยังไม่ทำหน้าจอละเอียด
   - **Later** = increment ถัดไป หรือรอคำตอบ
   - **ไม่ทำในวิชานี้ / รอคำตอบ** = นอก Core หรือยังไม่มี owner/policy
3. **ทุกการ์ดเขียนเหตุผล 1 บรรทัด** ว่าทำไมอยู่กองนั้น
4. คัดลอกลงตาราง scope table 4 ระดับใน `design/10-design-strategy.md` พร้อม requirement ID ทุกแถว

> **กติกาที่ห้ามพลาด:** Build now ต้องเป็น **วงจรที่จบงานได้ 1 รอบ** (เช่น ค้นหา → ส่ง → ตัดสิน → เห็นผล) ถ้ากอง Build now ทำงานไม่จบวงจร แปลว่าจัดผิด
> **ระวัง:** "จัดลำดับพัฒนา" ไม่เท่ากับ "ลบทิ้ง" — ทุก FR ยังอยู่ใน SRS

### Checkpoint 1 — Gallery Walk (นาที 80, 10 นาที)

เดินไปดู Spine + กองการ์ดของทีมข้าง ๆ 2 นาที ถาม 1 คำถามว่า "ทำไมข้อนี้อยู่กองนี้" — เป็นการช่วยกันมองหาจุดที่จัดผิด **ไม่ใช่ peer review ที่ต้องบันทึก**

### Activity C — Design Drivers (35 นาที) → `design/10-design-strategy.md` หัวข้อ 3

**เป้าหมาย:** ได้ 3 เรื่องที่ "ถ้าออกแบบพลาด ระบบนี้พัง" จาก BR/NFR/FR ที่มีอยู่จริง

1. แต่ละคนเขียน 1 ข้อ "ถ้าออกแบบพลาดตรงนี้ ระบบพัง เพราะ..." ในกระดาษของตัวเอง
2. **ทุกข้อต้องอ้าง ID** (BR/NFR/FR/AC) — ถ้าอ้าง ID ไม่ได้ แปลว่ายังไม่ใช่ driver
3. เอามารวมกัน โหวตเหลือ **3 ข้อ**
4. แต่ละข้อเขียน "ผลต่อการออกแบบใน W11 / W12 / W13" 1 บรรทัด

> **driver ที่ดี vs ไม่ดี:**
> - ❌ ไม่ดี: "ระบบต้องใช้ง่าย", "ต้องเร็ว" (ไม่ได้ชี้ว่าพลาดตรงไหนแล้วพัง)
> - ✔ ดี: "ยืมได้เฉพาะของที่ว่างจริง (BR-xx) — ถ้าออกแบบให้ยืมของที่คนอื่นถืออยู่ ระบบพัง"
> **ดูตัวอย่าง:** CRBS D1 "Submit ≠ จอง (BR-02/06)", D2 "Confirmed ห้ามซ้อน (BR-07, NFR-04)", D3 "ตรวจย้อนได้+ทำตามสิทธิ์ (NFR-02/03)"

### Activity D — Open Decisions (30 นาที) → `design/10-design-strategy.md` หัวข้อ 6

**เป้าหมาย:** เขียนเรื่องที่ยังไม่รู้คำตอบ ≤ 5 ข้อ ให้ออกแบบต่อได้

1. เปิด Open Issues (OI) ใน SRS ของทีม + จดสิ่งที่ยังไม่รู้ตอนทำ Activity B
2. แต่ละข้อเขียนให้ครบ 5 ช่อง: **คำถาม / เชื่อม OI ไหน / เจ้าของคำตอบ / ผลถ้าไม่ตอบ / รุ่นแรกทำอย่างไรระหว่างรอ**
3. **ห้ามแต่งตัวเลข/policy/เทคโนโลยี** มาเติมให้ตารางดูครบ — ถ้ายังไม่รู้ ให้เขียน "รอ [เจ้าของ]" และวิธีชั่วคราว

> **open decision (DD) ต่างจาก Open Issue (OI):** OI = คำถามระดับ requirement; DD = คำถามที่ design ต้องข้ามไปก่อนด้วยวิธีชั่วคราว
> **ดูตัวอย่าง:** CRBS DD-01 identity fixture, DD-02 กลไกกันซ้อน = Open for Dev, DD-04 ไม่กำหนดตัวเลข performance

### Checkpoint 2 — Done Checklist (นาที 160, 10 นาที)

ติ๊ก Done checklist 6 ข้อ (`W10_DONE_CHECKLIST_TH.md`) ด้วยตัวเอง ผู้สอนเดินดูเร็ว

---

## 4. การบ้าน (ทำต่อที่บ้าน ส่งก่อนคาบ W11)

1. เก็บ `design/10-design-strategy.md` + `design/00-design-spine.md` ให้เรียบร้อย (ครบทุกหัวข้อ ไม่มีช่องว่างที่ควรเติม)
2. กรอก `submissions/week-10-submission.md` (artefact links, done checklist, การมีส่วนร่วม)
3. อัปเดต `project-management/team-worklog.md` (ใครทำแถว/ข้อไหน)
4. ถ้าใช้ AI ช่วย: บันทึกใน `project-management/ai-use-log.md` พร้อมระบุว่าใครตรวจ (human verification)
5. commit และ push:

```text
git add design/10-design-strategy.md design/00-design-spine.md submissions/week-10-submission.md project-management/
git commit -m "submit(w10): design strategy and rationale"
git push
```

> ถ้ายังไม่ได้ใช้ git ในห้อง ให้ส่ง PDF/ลิงก์ตามที่อาจารย์กำหนด และเก็บไฟล์ใน path เดิมไว้

---

## 5. Definition of Done (ต้องครบก่อนส่ง)

- [ ] scope table แบ่ง 4 ระดับ (Build now / Overview / Later / ไม่ทำ) โดยไม่ลบ FR ใดออกจาก SRS
- [ ] ทุกแถวใน scope table มี requirement ID อย่างน้อย 1 ตัว
- [ ] drivers 3 ข้อ แต่ละข้ออ้าง ID และบอกผลต่อการออกแบบใน W11/12/13
- [ ] Spine 5–8 แถว มี actor + UC ทุกแถว เรียงตามผู้ใช้ทำจริง
- [ ] open decisions ≤ 5 มีเจ้าของ + ผลกระทบ + "ระหว่างรอทำอย่างไร" และ **ไม่มีค่าที่แต่งขึ้น**
- [ ] ระบุสถานะ SRS ตามจริง (Draft / Needs Revision / Baseline Candidate) — **ไม่อ้างว่า Approved**

---

## 6. คำถามชี้นำจากผู้สอน (ใช้ตอนติดขัด)

- หลักฐาน (requirement ID) ใดสนับสนุนการตัดสินใจนี้?
- stakeholder คนใดยังไม่ได้พิจารณา?
- decision นี้ตรวจสอบความสำเร็จได้อย่างไร?
- design decision นี้ตอบ requirement ข้อใด?

*Worksheets A–D อยู่ในโฟลเดอร์ `worksheets/` — ปริ้นต์หรือเปิดคู่กับกิจกรรม*
