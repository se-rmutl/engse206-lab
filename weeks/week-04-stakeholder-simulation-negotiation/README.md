# Week 04 — AI Evidence Rehearsal: From Conversation to Requirement Candidates

> **READ** instruction/role packs from Course Repository → **WORK & SUBMIT** all evidence in Team Repository.  
> [Student Workshop Guide](student-workshop-guide.md) · [Assignment Contract](assignment-contract.md) · [Prompt Pack](prompt-pack.md) · [Role Packs](role-packs/README.md) · [Rubric](rubric.md)

## 1. ข้อมูลสัปดาห์

| รายการ | รายละเอียด |
|---|---|
| บทเรียน | From Conversation to Evidence, Need and Requirement Candidate |
| CLO | CLO2, CLO6 |
| เวลา | ทฤษฎี 2 ชั่วโมง + Workshop 3 ชั่วโมง |
| Inputs | Week 3 Elicitation Plan + revised Interview Guide |
| Outputs | AI Conversation Excerpt + Evidence Log + Need List + Requirement Candidates |
| คะแนน | A3 = 4 คะแนน |

## 2. เป้าหมาย

ฝึกใช้ AI เป็น stakeholder จำลอง แล้วแยกข้อมูลจากบทสนทนาออกเป็น 4 ชั้น ได้แก่ **Evidence → Need → Requirement Candidate → Follow-up** โดยไม่เขียนเกินหลักฐานที่มี และไม่ถือว่าข้อความจาก AI เป็นข้อเท็จจริงจริงของมหาวิทยาลัย

## 3. Theory Brief — 2 ชั่วโมง

- Evidence คือข้อความ/เหตุการณ์/ข้อจำกัดที่อ้างอิงได้
- Need คือปัญหาหรือเป้าหมายของ stakeholder ที่ตีความจาก evidence
- Requirement Candidate คือข้อกำหนดร่างที่ยังต้องตรวจสอบ
- Tag พื้นฐาน: `FACT`, `NEED`, `CONSTRAINT`, `UNKNOWN`, `ASSUMPTION`
- Responsible AI: ใช้ข้อมูลจำลอง, ไม่ใส่ข้อมูลส่วนบุคคล, ต้องตรวจทานเอง

## 4. Workshop — 180 นาที

| เวลา | ขั้นตอน | Output |
|---|---|---|
| 00–15 | เปิด case card, Week03 interview guide และ role pack | พร้อมถาม AI |
| 15–45 | คุยกับ AI 1 role หลัก | conversation excerpt |
| 45–70 | คัด evidence 5–8 ชิ้นจากบทสนทนา | E-ID + tag |
| 70–95 | แปลง evidence เป็น need | Need list |
| 95–125 | เขียน requirement candidates 4–6 ข้อ | RC list |
| 125–145 | หา unknown/conflict/follow-up | follow-up list |
| 145–165 | peer trace check: RC อ้าง E-ID ได้หรือไม่ | revision notes |
| 165–180 | commit/push และกรอก submission | submission checkpoint |

## 5. Evidence Tags

| Tag | Meaning |
|---|---|
| `FACT` | ข้อเท็จจริงจาก case card หรือสิ่งที่ stakeholder ระบุชัด |
| `NEED` | ความต้องการ/ปัญหาที่ stakeholder กล่าวหรือทีมตีความจาก evidence |
| `CONSTRAINT` | กฎ ขอบเขต เงื่อนไข หรือข้อจำกัด |
| `UNKNOWN` | ข้อมูลที่ยังไม่รู้ ต้องถามต่อ |
| `ASSUMPTION` | ข้อสมมติของทีม ต้องตรวจสอบก่อนใช้เป็น requirement |

## 6. Exact Output Paths ใน Team Repo

- `evidence/week-04/ai-stakeholder-simulation-log.md`
- `evidence/week-04/ai-conversation-excerpt.md`
- `docs/04-evidence-log.md`
- `docs/04-requirement-candidates.md`
- `project-management/risk-and-issue-log.md`
- `project-management/decision-log.md`
- `project-management/team-worklog.md`
- `project-management/ai-use-log.md`
- `submissions/week-04-submission.md`

## 7. Controlled Simulation Rules

1. One stakeholder role per chat/session.
2. AI Operator may read the role pack; interviewers should discover details through questions.
3. Never invent real names, personal data, university policy or statistics.
4. AI statements must be labelled simulation and assigned source/tag/confidence.
5. AI output may produce **Candidate/Needs Validation/Unresolved**, not approved requirements.
6. Record unknowns and contradictions instead of silently merging them.

## 8. Tabletop Presentation — 4–5 นาที

1. Case และ stakeholder role ที่ถาม
2. Evidence สำคัญ 2–3 ชิ้น พร้อม E-ID
3. Need ที่ได้จาก evidence
4. Requirement candidate 1–2 ข้อที่อ้าง E-ID
5. Unknown/follow-up ที่ต้องตรวจสอบใน Week05

## 9. Commit

```text
checkpoint(w04): extract evidence from ai conversation
submit(w04): evidence and requirement candidates
```

## 10. Definition of Done

- [ ] ≥ 1 stakeholder role; ถ้าทันให้เพิ่ม role ที่ 2
- [ ] Evidence has E-ID, source, tag, quote/summary, need and follow-up
- [ ] Unknown/conflict/assumption ถูกบันทึกแยกจาก requirement
- [ ] 4–6 RCs link to E-IDs and do not overclaim approval
- [ ] no PII/confidential data; AI use is disclosed
- [ ] repository links, logs, contribution and commit history are complete
