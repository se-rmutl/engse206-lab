# Submission Summary — Week 03

> **Assignment:** `W03-v2.0`  
> **Case:** Campus Resource Booking  
> **Status:** Ready for Week 04 simulation (Teaching Example)

## 1. Submitted artefacts

| Artefact | Path | Evidence of completion |
|---|---|---|
| Elicitation Plan | [`03-elicitation-plan.md`](03-elicitation-plan.md) | EO/EP table, evidence schema, risk, exit criteria |
| Interview Guide | [`03-interview-guide.md`](03-interview-guide.md) | 12 questions, probes, bias check, rehearsal revisions |
| OQ → EO figure | [`images/w03-open-question-to-objective.svg`](images/w03-open-question-to-objective.svg) | แสดง transformation และ exit criteria |
| Plan flow | [`images/w03-elicitation-plan-flow.svg`](images/w03-elicitation-plan-flow.svg) | แสดง OQ → EO → stakeholder/method → evidence |
| Interview funnel | [`images/w03-interview-funnel.svg`](images/w03-interview-funnel.svg) | แสดงลำดับคำถามแบบไม่ชี้นำ |

## 2. Traceability spot check

| Week 02 | Week 03 objective | Plan | Questions | Week 04 expected output |
|---|---|---|---|---|
| OQ-01 / AS-03 | EO-01 | EP-01, EP-02 | Q-01–Q-03 | authority/rule/exception E-IDs |
| OQ-02 / AS-02 | EO-02 | EP-02, EP-04 | Q-04, Q-09, Q-11 | schedule/policy source + OQ |
| OQ-03 | EO-03 | EP-02, EP-03 | Q-05a, Q-05b | conflict/interests/negotiation |
| OQ-04 | EO-04 | EP-01 | Q-06 | minimum handover/return data |
| OQ-05 | EO-05 | EP-03 | Q-07, Q-08 | event/timing/recipient evidence |
| AS-01 | EO-06 | EP-04 | Q-10 | identity/data constraint |

## 3. Human review after AI rehearsal

- แยก Q-05 เป็น late cancellation และ no-show
- ตัดคำถามที่ชี้ไปยัง LINE/QR/photo
- เพิ่ม authority/document probe เพื่อป้องกัน simulation ถูกใช้เป็น policy
- เพิ่ม closing status: confirmed, corrected หรือ unresolved

## 4. Definition of Done

- [x] EO ทุกข้อเชื่อม OQ/AS และ decision
- [x] EP มี stakeholder, method, evidence, owner, time, risk และ exit criteria
- [x] Guide มี 10–12 ข้อพร้อม EO ID และ probe
- [x] มี before/after bias correction อย่างน้อย 2 ข้อ
- [x] AI rehearsal ติดป้าย Simulation และผ่าน human review
- [x] พร้อมสร้าง evidence โดยไม่ถือคำตอบจำลองเป็น approved requirement

## 5. Example commits

```text
checkpoint(w03): elicitation plan and interview rehearsal
submit(w03): elicitation plan interview guide and rehearsal
```

> Team Repo จริงต้องมี rehearsal notes, peer feedback, AI use log, team worklog และ final commit hash ของทีม
