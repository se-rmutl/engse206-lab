# Week 04 — Workshop 3: AI Stakeholder Panel, Evidence Logging and Negotiation

> **READ** instruction/role packs from Course Repository → **WORK & SUBMIT** all evidence in Team Repository.  
> [Assignment Contract](assignment-contract.md) · [Prompt Pack](prompt-pack.md) · [Role Packs](role-packs/README.md) · [Rubric](rubric.md)

## 1. ข้อมูลสัปดาห์

| รายการ | รายละเอียด |
|---|---|
| บทเรียน | 2.2 Facilitation, Observation, Workshop และ Negotiation |
| CLO | CLO2, CLO6 |
| เวลา | ทฤษฎี 2 ชั่วโมง + Workshop 3 ชั่วโมง |
| Inputs | Week 3 Elicitation Plan + revised Interview Guide |
| Outputs | Simulation Log + Evidence Log + Conflict/Negotiation + Requirement Candidates |
| คะแนน | A3 = 4 คะแนน |

## 2. เป้าหมาย

ดำเนินการ stakeholder simulation หลายบทบาท เก็บ evidence โดยไม่ตีความเกินข้อมูล ระบุความขัดแย้ง วิเคราะห์ position/interest/constraint/options และสร้าง requirement candidates ที่อ้าง E-ID พร้อม status/confidence/follow-up

## 3. Theory Brief — 2 ชั่วโมง

- Facilitation roles, active listening and power balance
- Observation/minutes/evidence logging
- Fact, simulated need, constraint, opinion, assumption and proposed solution
- Conflict: position vs interest; authority and decision rights
- Negotiation options, criteria, rationale and unresolved status
- Responsible AI: role isolation, no PII and simulation label

## 4. Workshop — 180 นาที

| เวลา | ขั้นตอน | Output |
|---|---|---|
| 00–15 | แบ่งบทบาท เปิด Plan/Guide และเลือก stakeholder 3–4 roles | role assignment |
| 15–50 | Interview Round 1: Primary User + Operational Staff | notes/E-ID candidates |
| 50–70 | Evidence Review: CF/SN/CT/OP/AS/PS/OQ | evidence table + follow-ups |
| 70–105 | Panel Round 2: Policy/Manager + Technical/Privacy/Safety | authority/constraint evidence |
| 105–135 | Negotiation Clinic: conflict, interests, options, criteria, status | negotiation record |
| 135–155 | Requirement Candidates 5–8 ข้ออ้าง E-ID | RC list |
| 155–175 | Tabletop presentation 4–5 นาที | evidence/conflict/decision summary |
| 175–180 | commit/push | submission checkpoint |

## 5. Evidence Tags

| Tag | Meaning |
|---|---|
| `CF` | Case Fact from authorized case/document |
| `SN` | Simulated Need stated by an AI role; requires verification |
| `CT` | Constraint/rule; record authority/source |
| `OP` | Opinion/preference; not automatically a requirement |
| `AS` | Assumption; create follow-up/open question |
| `PS` | Proposed solution; search for underlying need |
| `OQ` | Open question/unresolved information |

## 6. Exact Output Paths ใน Team Repo

- `evidence/week-04/ai-stakeholder-simulation-log.md`
- `docs/04-evidence-log.md`
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
5. A simulated panel may produce **Candidate/Provisional/Unresolved**, not real-world Approved requirements.
6. Record contradictions instead of silently merging them.

## 8. Tabletop Presentation — 4–5 นาที

1. Stakeholder roles interviewed
2. Important evidence with source/tag/confidence
3. One conflict: positions, interests, authority and constraints
4. Options and decision/status/rationale
5. One or two evidence-linked requirement candidates
6. Unresolved issue and verification plan for Week 5

## 9. Commit

```text
checkpoint(w04): stakeholder evidence and conflict analysis
submit(w04): stakeholder evidence negotiation and candidates
```

## 10. Definition of Done

- [ ] ≥ 3 stakeholder roles, separate sessions
- [ ] Evidence has E-ID, source, tag, context, confidence and follow-up
- [ ] ≥ 1 conflict with ≥ 2 options and explicit status/rationale
- [ ] 5–8 RCs link to E-IDs and do not overclaim approval
- [ ] no PII/confidential data; AI use is disclosed
- [ ] repository links, logs, contribution and commit history are complete
