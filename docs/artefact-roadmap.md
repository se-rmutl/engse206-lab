# Artefact Roadmap: ชิ้นงานสะสมตลอดภาคเรียน

| Week | ชิ้นงาน | ที่เก็บแนะนำใน Git | สถานะ |
|---:|---|---|---|
| 1 | Problem Brief v0.1 + Team Worklog | `docs/01-problem-brief-v0.1.md` | Draft |
| 2 | Stakeholder Map + System Context + Scope | `docs/02-stakeholder-context-scope.md` | Draft |
| 3 | Elicitation Plan + Interview Guide | `docs/03-elicitation-plan.md` | Draft |
| 4 | Evidence Log + Minutes + Issue List | `evidence/week-04/` | Evidence |
| 5 | Requirement Backlog | `docs/05-requirement-backlog.md` | Draft |
| 6 | User Stories / Use Cases / Acceptance Criteria | `docs/06-requirement-models.md` | Draft |
| 7 | SRS Draft v1 | `docs/07-srs-v1.md` | Baseline Candidate |
| 8 | Review / Traceability / Change | `docs/08-validation-traceability.md` | Reviewed |
| 10 | Design Strategy | `design/10-design-strategy.md` | Draft |
| 11 | Conceptual Architecture | `design/11-conceptual-architecture.md` | Draft |
| 12 | Prototype + Usability Plan | `design/12-ux-ui-prototype.md` | Draft |
| 13 | Detailed Design | `design/13-detailed-design.md` | Draft |
| 14 | Design Review | `design/14-design-review.md` | Reviewed |
| 15 | Test Evidence + Revised Package | `evidence/week-15/` + `design/` | Revised |
| 16 | Final Package + Pitch + Reflection | `final/` | Final |

## Commit convention

- ใช้ชื่อไฟล์แบบ `lowercase-kebab-case` หรือเลขนำหน้า
- Commit สำคัญต้องสื่อสารความหมาย เช่น `docs: add FR-05 booking cancellation criteria`
- หลีกเลี่ยง `update`, `fix`, `งานใหม่`
- เมื่อเป็น baseline ให้ติด tag เช่น `srs-v1.0` หรือบันทึก release note ใน `CHANGELOG.md`
