# ENGSE206 — การกำหนดความต้องการและการออกแบบทางซอฟต์แวร์
## Software Requirements Specification and Design

> ชุดเอกสาร Git Repository สำหรับรายวิชา ENGSE206 3(2-3-5)  
> หลักสูตร วศ.บ. วิศวกรรมซอฟต์แวร์ | ชั้นปีที่ 2 | แผน 15 สัปดาห์เรียน + สอบกลางภาค + สอบปลายภาค

เอกสารชุดนี้ออกแบบให้ใช้ **กรณีศึกษา 1 เรื่องต่อ 1 กลุ่มตลอดภาคเรียน** เพื่อฝึกสายธารงานจริงตั้งแต่  
**เข้าใจปัญหา → เก็บความต้องการ → เขียน SRS → ออกแบบ → ตรวจสอบและปรับปรุง → นำเสนอ**

รายวิชานี้ต่อยอดจากพื้นฐานการเขียนโปรแกรม กระบวนการซอฟต์แวร์ คุณภาพ และฐานข้อมูลที่ผู้เรียนได้รับจาก ENGCC304, ENGSE203, ENGSE204, ENGSE205 และ ENGSE219 แล้วเปลี่ยนความรู้เชิงเทคนิคให้เป็นชิ้นงานที่ตอบคำถามว่า **ระบบควรทำอะไร เพื่อใคร และควรออกแบบอย่างไร**

## เริ่มต้นใช้งาน

1. อาจารย์อ่าน [คู่มือเริ่มต้นสำหรับอาจารย์](docs/instructor-quick-start.md) และกำหนดกลุ่ม/กรณีศึกษา
2. นักศึกษาอ่าน [วิธีใช้ Git และการส่งงาน](docs/git-workflow-and-submission.md)
3. แต่ละกลุ่มเลือกหรือได้รับมอบหมาย 1 โจทย์จาก [Case Project ทั้ง 10 เรื่อง](cases/README.md)
4. ใช้ [Starter Repository สำหรับนักศึกษา](student-repo-starter/README.md) เป็นจุดเริ่มต้นของ repository กลุ่ม
5. เปิด [สัปดาห์ที่ 1](weeks/week-01-problem-brief/README.md) และดำเนินงานตามลำดับ

## แผนที่เอกสารสำคัญ

| สิ่งที่ต้องการ | เอกสาร |
|---|---|
| ภาพรวมรายวิชา ชั่วโมงเรียน และสายธารผลลัพธ์ | [Course Overview](docs/course-overview.md) |
| PLO / CLO / Bloom’s Taxonomy | [Learning Outcomes Mapping](docs/learning-outcomes-plo-clo.md) |
| การวัดผลและ rubric | [Assessment and Rubrics](docs/assessment-rubrics.md) |
| วิธีใช้ Semester Project Case | [Semester Project Method](docs/semester-project-method.md) |
| ลำดับชิ้นงานที่จะสะสมตลอดเทอม | [Artefact Roadmap](docs/artefact-roadmap.md) |
| วิธีใช้ Git, โครงสร้าง repo และการส่งงาน | [Git Workflow and Submission](docs/git-workflow-and-submission.md) |
| กำหนดการสอนทั้งรายวิชา | [Course Calendar](docs/course-calendar.md) |

## โครงสร้างโฟลเดอร์

```text
ENGSE206-Requirements-and-Design/
├── docs/                   # เอกสารภาพรวมรายวิชา อาจารย์ และนโยบายการส่งงาน
├── cases/                  # Case Cards 10 เรื่องสำหรับแจกแต่ละกลุ่ม
├── weeks/                  # เอกสารสอน/Workshop/LAB แยกตามสัปดาห์
├── templates/              # แม่แบบเอกสารที่ใช้ตลอดภาคเรียน
├── student-repo-starter/   # โครงตั้งต้นสำหรับ repository ของแต่ละกลุ่ม
└── references/             # ไฟล์ Word / ภาพประกอบที่ใช้กับ Week 1
```

## แผนรายสัปดาห์

| สัปดาห์ | หัวข้อ/กิจกรรมหลัก | เอกสาร |
|---:|---|---|
| 1 | Requirements & Design in SDLC; Problem Brief Kick-off | [Week 01](weeks/week-01-problem-brief/README.md) |
| 2 | Stakeholder, Context, Scope, Ethics | [Week 02](weeks/week-02-stakeholder-context-scope/README.md) |
| 3 | Elicitation Plan and Interview Design | [Week 03](weeks/week-03-elicitation-interview-design/README.md) |
| 4 | Stakeholder Simulation, Evidence Log, Negotiation | [Week 04](weeks/week-04-stakeholder-simulation-negotiation/README.md) |
| 5 | Requirement Analysis, Classification, Prioritization | [Week 05](weeks/week-05-requirement-analysis-prioritization/README.md) |
| 6 | User Story, Use Case, Acceptance Criteria, Negotiation Board | [Week 06](weeks/week-06-requirement-modeling-negotiation/README.md) |
| 7 | SRS Authoring Studio | [Week 07](weeks/week-07-srs-authoring/README.md) |
| 8 | SRS Quality Clinic, Traceability, Change Management | [Week 08](weeks/week-08-srs-validation-traceability/README.md) |
| 9 | สอบกลางภาค | [Week 09](weeks/week-09-midterm/README.md) |
| 10 | Design Strategy and Design Rationale | [Week 10](weeks/week-10-design-strategy/README.md) |
| 11 | Conceptual Architecture Studio | [Week 11](weeks/week-11-conceptual-architecture/README.md) |
| 12 | UX/UI Prototype and Accessibility | [Week 12](weeks/week-12-ux-ui-prototype/README.md) |
| 13 | Detailed Design Studio | [Week 13](weeks/week-13-detailed-design/README.md) |
| 14 | Design Review Simulation | [Week 14](weeks/week-14-design-review/README.md) |
| 15 | Usability / Peer Test and Iteration | [Week 15](weeks/week-15-usability-test-iteration/README.md) |
| 16 | Requirement-to-Design Showcase and Reflection | [Week 16](weeks/week-16-project-showcase/README.md) |
| 17 | สอบปลายภาค | [Week 17](weeks/week-17-final-exam/README.md) |

## หมายเหตุสำหรับผู้สอน

- แผนนี้ตั้งใจให้ **มี Workshop / Document Studio / Role-play / Peer Review** สลับกับ Computer LAB ไม่ใช่บังคับให้ใช้คอมพิวเตอร์ทุกสัปดาห์
- สัปดาห์ที่ 1 มีชุดเอกสารพร้อมใช้งานครบ: Case Cards 10 เรื่อง, คู่มืออาจารย์, ใบงานนักศึกษา, starter repo, rubric, ตัวอย่างงาน และภาพ infographic
- นักศึกษาส่งชิ้นงานผ่าน Git เพื่อให้เห็น revision history, หลักฐานการทำงาน และสามารถให้ feedback เป็นรอบได้
