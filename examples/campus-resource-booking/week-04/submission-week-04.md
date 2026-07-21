# Submission Summary — Week 04

> **Assignment:** `W04-v2.0`  
> **Case:** Campus Resource Booking  
> **Status:** Evidence checkpoint complete; ready for Week 05 analysis

## 1. Submitted artefacts

| Artefact | Path | Key content | Status |
|---|---|---|---|
| Evidence Log | [`04-evidence-log.md`](04-evidence-log.md) | 14 E-IDs, source/tag/confidence/follow-up | Complete |
| Negotiation Record | [`04-negotiation-record.md`](04-negotiation-record.md) | 3 conflicts, options, criteria, status/rationale | Complete |
| Requirement Candidates | [`04-requirement-candidates.md`](04-requirement-candidates.md) | 8 evidence-linked RCs + coverage matrix | Complete |
| Stakeholder panel figure | [`images/w04-stakeholder-panel.svg`](images/w04-stakeholder-panel.svg) | separated roles/sessions | Complete |
| Evidence tagging figure | [`images/w04-evidence-tagging.svg`](images/w04-evidence-tagging.svg) | statement → tag → confidence → follow-up | Complete |
| Negotiation figure | [`images/w04-conflict-negotiation.svg`](images/w04-conflict-negotiation.svg) | position → interest → option → status | Complete |
| Requirement trace figure | [`images/w04-requirement-trace.svg`](images/w04-requirement-trace.svg) | OQ/EO/Q → E/N → RC → Week 05 | Complete |

## 2. Outcome summary

- Stakeholder roles simulated separately: ST-01, ST-02, ST-03, ST-04
- Evidence: `E-01..E-14`
- Conflicts: `N-01` Provisional, `N-02` Provisional, `N-03` Unresolved
- Requirement Candidates: `RC-01..RC-08`
- Major unresolved issues: exact booking limits/no-show policy, authority matrix, schedule integration, notification timing/channel

## 3. Responsible-AI declaration

- AI ถูกใช้เป็น stakeholder proxy ภายใต้ role pack และแยก session รายบทบาท
- ไม่มีข้อมูลบุคคลจริงหรือ policy/statistic ที่แต่งขึ้น
- ทุกคำตอบ AI ติด `SN/OP/AS/PS/OQ` ตามลักษณะและไม่เกิน Medium confidence
- ทีมเป็นผู้ทบทวน แยก statement/interpretation เปิด conflict และตัดสินสถานะ candidate

## 4. Definition of Done

- [x] มีอย่างน้อย 3 stakeholder roles และแยก source/session
- [x] Evidence มี E-ID, source, tag, context, confidence และ follow-up
- [x] มี conflict อย่างน้อย 1 เรื่อง พร้อม 2+ options และ rationale/status
- [x] มี RC 5–8 ข้อที่อ้าง E-ID และไม่ overclaim approval
- [x] unresolved issue มี owner/verification plan
- [x] Markdown links ไปยัง SVG ถูกต้อง
- [x] พร้อมส่ง RC และ issues เข้า Week 05 backlog analysis

## 5. Example commits

```text
checkpoint(w04): stakeholder evidence and conflict analysis
submit(w04): stakeholder evidence negotiation and candidates
```

> ใน Team Repo จริงต้องเพิ่ม simulation log, risk/issue log, decision log, team/AI-use log และ final commit hash ตาม Assignment Contract
