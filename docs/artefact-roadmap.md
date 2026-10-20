# Artefact Roadmap: ชิ้นงานสะสมตลอดภาคเรียน

| Week | ชิ้นงาน | ที่เก็บแนะนำใน Git | สถานะ |
|---:|---|---|---|
| 1 | Problem Brief v0.1 + Team Worklog | `docs/01-problem-brief-v0.1.md` | Draft |
| 2 | Stakeholder Map + System Context + Scope | `docs/02-stakeholder-context-scope.md` | Draft |
| 3 | Elicitation Plan + Interview Guide | `docs/03-elicitation-plan.md` | Draft |
| 4 | AI Conversation Excerpt + Evidence Log + Requirement Candidates | `evidence/week-04/ai-conversation-excerpt.md` · `docs/04-evidence-log.md` · `docs/04-requirement-candidates.md` | Evidence |
| 5 | Requirement Backlog | `docs/05-requirement-backlog.md` | Draft |
| 5b | Requirement Baseline v1.0 | `docs/08-validation-traceability.md` (ส่วน A) · `evidence/week-05/baseline-review/` · tag `baseline-v1.0` | Baseline |
| 6 | User Stories / Use Cases / Acceptance Criteria | `docs/06-requirement-models.md` | Draft |
| 7 | SRS Draft v1 | `docs/07-srs-v1.md` | Baseline Candidate |
| 8 | Review / Traceability / Change | `docs/08-validation-traceability.md` | Reviewed |
| 10 | Design Strategy + Design Spine v0.1 | `design/10-design-strategy.md` · `design/00-design-spine.md` | Design Draft |
| 11 | Conceptual Architecture (C4 ระดับ 1–2) | `design/11-conceptual-architecture-v0.1.docx` · `diagrams/architecture/` | Design Draft |
| 12 | Prototype + Usability Plan | `design/12-ux-ui-prototype.md` | Draft |
| 13 | Detailed Design | `design/13-detailed-design.md` | Draft |
| 14 | Developer Handoff v1.0 + การนำเสนอ (ประกาศในสัปดาห์ที่ 13) | ประกาศในสัปดาห์ที่ 13 | Provisional Handoff |
| 15 | สอบปลายภาค ส่วน ก (งานกลุ่ม) | branch `final-exam` · `final-exam/` | Exam |

## Commit convention

- ใช้ชื่อไฟล์แบบ `lowercase-kebab-case` หรือเลขนำหน้า
- Commit สำคัญต้องสื่อสารความหมาย เช่น `docs: add FR-05 booking cancellation criteria`
- หลีกเลี่ยง `update`, `fix`, `งานใหม่`
- เมื่อเป็น baseline ให้ติด tag เช่น `srs-v1.0` หรือบันทึก release note ใน `CHANGELOG.md`
