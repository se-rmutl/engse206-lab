# Workshop สัปดาห์ที่ 3: การสร้างเอกสาร SRS แบบกลุ่ม
## "From Requirements to Reality" - Complete SRS Development Workshop

---

## 🎯 Overview และ Learning Objectives

### จุดประสงค์ของ Workshop
พัฒนาทักษะการเขียนเอกสาร Software Requirements Specification (SRS) ที่มีคุณภาพระดับมืออาชีพผ่านการทำงานร่วมกันเป็นทีม

### Learning Outcomes
หลังจากเสร็จสิ้น workshop นักศึกษาจะสามารถ:
1. **ประยุกต์ใช้มาตรฐาน IEEE 830** ในการเขียน SRS
2. **เขียน requirements ที่เป็น SMART** และตรวจสอบได้
3. **สร้าง Use Cases และ User Stories** ที่สมบูรณ์
4. **ทำงานเป็นทีม** และแบ่งหน้าที่รับผิดชอบอย่างมีประสิทธิภาพ
5. **ตรวจสอบและ validate requirements** ด้วยเทคนิคต่างๆ

### เวลาที่ใช้: 90 นาที
- **Planning & Team Formation:** 15 นาที
- **SRS Development:** 60 นาที
- **Presentation & Peer Review:** 15 นาที

---

## 📱 Project Scenarios (เลือก 1 จาก 4)

### Scenario 1: "SmartCampus" - University Management System
**Context:** มหาวิทยาลัยต้องการระบบจัดการแบบครบวงจรสำหรับนักศึกษา อาจารย์ และเจ้าหน้าที่

**Key Features:**
- ระบบลงทะเบียนเรียนออนไลน์
- การจัดการตารางเรียน/สอน
- ระบบแจ้งข่าวสารและประกาศ
- การจองห้องเรียน/ห้องประชุม
- ระบบประเมินการเรียนการสอน
- Mobile app สำหรับการเข้าถึงข้อมูล

**Stakeholders:**
- นักศึกษา (12,000 คน)
- อาจารย์ (800 คน)
- เจ้าหน้าที่สำนักงาน (300 คน)
- ผู้บริหารมหาวิทยาลัย
- ผู้ปกครอง

### Scenario 2: "HealthTrack" - Personal Health Management App
**Context:** แอปพลิเคชันจัดการสุขภาพส่วนบุคคลสำหรับคนไทยทุกวัย

**Key Features:**
- บันทึกข้อมูลสุขภาพประจำวัน
- ติดตามการออกกำลังกายและโภชนาการ
- แจ้งเตือนการทานยาและนัดหมายแพทย์
- เชื่อมต่อกับอุปกรณ์วัดสุขภาพ (smart watch, blood pressure monitor)
- ระบบให้คำปรึกษาจากแพทย์ออนไลน์
- รายงานสุขภาพและแนวโน้ม

**Stakeholders:**
- ผู้ใช้ทั่วไป (วัย 25-65 ปี)
- ผู้สูงอายุ (65+ ปี)
- แพทย์และพยาบาล
- โรงพยาบาลและคลินิก
- บริษัทประกันสุขภาพ

### Scenario 3: "EcoMart" - Sustainable E-commerce Platform
**Context:** แพลตฟอร์มออนไลน์สำหรับซื้อขายสินค้าที่เป็นมิตรกับสิ่งแวดล้อม

**Key Features:**
- ตลาดออนไลน์สำหรับสินค้า eco-friendly
- ระบบ carbon footprint tracking
- โปรแกรมแลกเปลี่ยนและรีไซเคิล
- ระบบจัดส่งแบบ carbon neutral
- Community platform สำหรับแบ่งปันเทคนิค sustainable living
- ระบบให้คะแนนและรีวิว sustainability

**Stakeholders:**
- ผู้บริโภคที่ใส่ใจสิ่งแวดล้อม
- ผู้ขายสินค้า eco-friendly
- บริษัทจัดส่ง
- องค์กรด้านสิ่งแวดล้อม
- หน่วยงานรัฐ

### Scenario 4: "SkillBridge" - Online Learning & Career Platform
**Context:** แพลตฟอร์มเรียนรู้ออนไลน์ที่เชื่อมโยงกับโอกาสในการทำงาน

**Key Features:**
- หลักสูตรออนไลน์ที่หลากหลาย
- ระบบประเมินและออกใบรับรอง
- Career matching และ job placement
- Mentorship program
- Virtual networking events
- Progress tracking และ portfolio building

**Stakeholders:**
- ผู้เรียน (นักศึกษา, คนทำงาน, ผู้ว่างงาน)
- ผู้สอน/วิทยากร
- นายจ้างและ HR
- บริษัทที่เป็นพาร์ทเนอร์
- หน่วยงานรัฐด้านแรงงาน

---

## 👥 Team Formation & Role Assignment (15 นาที)

### การแบ่งกลุ่ม
- **จำนวน:** 5-6 คนต่อกลุ่ม
- **การเลือก Scenario:** แต่ละกลุ่มเลือก 1 จาก 4 scenarios
- **หลักการ:** ความสนใจ, ความเชี่ยวชาญ, ความหลากหลายของทีม

### บทบาทในทีม

#### 1. Project Manager / SRS Coordinator
**หน้าที่:**
- ควบคุมการทำงานให้เป็นไปตามกำหนดเวลา
- ประสานงานระหว่างสมาชิกในทีม
- รับผิดชอบ Section 1 (Introduction) และ Section 2.1-2.2 (Overall Description)
- ตรวจสอบความสอดคล้องของเอกสารทั้งหมด

**Skills Required:** Leadership, Communication, Organization

#### 2. Business Analyst / Requirements Specialist
**หน้าที่:**
- วิเคราะห์ความต้องการทางธุรกิจ
- รับผิดชอบ Section 3.1 (Functional Requirements) - ส่วนที่ 1
- สร้าง Business Rules และ Constraints
- ทำ Stakeholder Analysis

**Skills Required:** Business Understanding, Analytical Thinking

#### 3. System Architect / Technical Lead
**หน้าที่:**
- กำหนด Technical Architecture
- รับผิดชอบ Section 3.1 (Functional Requirements) - ส่วนที่ 2
- รับผิดชอบ Section 3.2 (Non-functional Requirements)
- ตรวจสอบ Technical Feasibility

**Skills Required:** Technical Knowledge, Systems Thinking

#### 4. UX/UI Designer / User Experience Specialist
**หน้าที่:**
- ออกแบบและวิเคราะห์ User Experience
- รับผิดชอบ Use Case Diagrams และ User Stories
- สร้าง User Personas และ User Journey
- รับผิดชอบ Interface Requirements

**Skills Required:** Design Thinking, User Empathy

#### 5. Quality Assurance / Validation Specialist
**หน้าที่:**
- ตรวจสอบคุณภาพของ Requirements
- สร้าง Acceptance Criteria สำหรับ User Stories
- รับผิดชอบ Validation Scenarios
- ทำ Requirements Traceability Matrix

**Skills Required:** Attention to Detail, Testing Mindset

#### 6. Documentation & Communication Specialist
**หน้าที่:**
- จัดทำเอกสารให้เป็นไปตามมาตรฐาน IEEE 830
- รับผิดชอบ Appendices (Glossary, References)
- เตรียมการนำเสนอ
- ตรวจสอบ Grammar และ Consistency

**Skills Required:** Writing, Presentation, Organization

### Team Charter Template
```
Team Name: _________________
Chosen Scenario: _________________
Project Vision: _________________

Team Members & Roles:
1. _________________ - Project Manager
2. _________________ - Business Analyst  
3. _________________ - System Architect
4. _________________ - UX/UI Designer
5. _________________ - QA Specialist
6. _________________ - Documentation Specialist

Communication Plan:
- Primary Tool: _________________
- Meeting Schedule: _________________
- Decision Making Process: _________________
```

---

## 📋 SRS Development Process (60 นาที)

### Phase 1: Planning & Research (10 นาที)

#### Stakeholder Analysis Workshop
**Activity:** แต่ละคนใน 2 นาที brainstorm stakeholders สำหรับ scenario ที่เลือก

**Template:**
```
Primary Stakeholders (ใช้งานโดยตรง):
- _________________
- _________________

Secondary Stakeholders (ได้รับผลกระทบ):
- _________________
- _________________

Key Stakeholders (มีอำนาจตัดสินใจ):
- _________________
- _________________
```

#### Project Scope Definition
**Activity:** กำหนดขอบเขตโครงการ

**Template:**
```
In Scope (ทำ):
- _________________
- _________________

Out of Scope (ไม่ทำ):
- _________________
- _________________

Future Scope (ทำในเฟสต่อไป):
- _________________
- _________________
```

### Phase 2: Requirements Gathering (15 นาที)

#### User Story Mapping Session
**Process:**
1. **Identify User Personas (3 นาที)**
   - แต่ละคนเขียน 1 persona บน sticky note
   - รวมและจัดกลุ่ม personas ที่คล้ายกัน

2. **User Journey Mapping (5 นาที)**
   - วาง user journey หลักของแต่ละ persona
   - ระบุ touchpoints สำคัญ

3. **User Story Generation (7 นาที)**
   - เขียน user stories สำหรับแต่ละ step ใน journey
   - ใช้ template: "As a [user], I want [goal] so that [benefit]"

**User Story Template:**
```
Story ID: US-001
As a [type of user],
I want [to perform some task]
So that [I can achieve some goal/benefit]

Priority: High/Medium/Low
Estimate: Small/Medium/Large

Acceptance Criteria:
Given [precondition]
When [action]
Then [expected result]
And [additional criteria]
```

### Phase 3: SRS Document Creation (25 นาที)

#### Parallel Development Strategy
แต่ละคนทำงานใน section ที่รับผิดชอบพร้อมกัน:

**Section 1: Introduction (Project Manager - 5 นาที)**
```
1.1 Purpose
- วัตถุประสงค์ของเอกสาร SRS
- ผู้อ่านเป้าหมาย

1.2 Scope  
- ชื่อผลิตภัณฑ์
- สิ่งที่ระบบจะทำและไม่ทำ
- ประโยชน์และเป้าหมาย

1.3 Definitions, Acronyms, and Abbreviations
- คำศัพท์เฉพาะที่ใช้ในเอกสาร

1.4 References
- เอกสารอ้างอิง

1.5 Overview
- โครงสร้างของเอกสารที่เหลือ
```

**Section 2: Overall Description (Project Manager - 5 นาที)**
```
2.1 Product Perspective
- ระบบใหม่หรือส่วนหนึ่งของระบบใหญ่
- System interfaces, User interfaces, Hardware interfaces

2.2 Product Functions  
- สรุปฟังก์ชันหลักๆ ของระบบ

2.3 User Characteristics
- ลักษณะของผู้ใช้แต่ละประเภท

2.4 Constraints
- ข้อจำกัดด้านเทคโนโลยี, นโยบาย, ฮาร์ดแวร์

2.5 Assumptions and Dependencies
- สมมติฐานและสิ่งที่ระบบต้องพึ่งพา
```

**Section 3.1: Functional Requirements Part 1 (Business Analyst - 8 นาที)**
```
REQ-F001: [Requirement Name]
Description: [รายละเอียดของความต้องการ]
Priority: High/Medium/Low
Source: [ที่มาของความต้องการ]
Rationale: [เหตุผลที่ต้องมี requirement นี้]

Acceptance Criteria:
- [เกณฑ์การยอมรับข้อที่ 1]
- [เกณฑ์การยอมรับข้อที่ 2]

Dependencies: [Requirements อื่นที่เกี่ยวข้อง]

(ทำอย่างน้อย 5-7 requirements)
```

**Section 3.1: Functional Requirements Part 2 (System Architect - 8 นาที)**
```
REQ-F008: [System Integration Requirements]
REQ-F009: [Data Management Requirements]  
REQ-F010: [Security Requirements]
REQ-F011: [Performance Requirements]
REQ-F012: [Backup and Recovery Requirements]

(ทำอย่างน้อย 5 requirements ที่เน้นด้านเทคนิค)
```

**Section 3.2: Non-functional Requirements (System Architect - 7 นาที)**
```
Performance Requirements:
- Response time: [เวลาตอบสนอง]
- Throughput: [จำนวน transactions ต่อหน่วยเวลา]
- Capacity: [จำนวน concurrent users]

Security Requirements:
- Authentication: [วิธีการพิสูจน์ตัวตน]
- Authorization: [การควบคุมสิทธิการเข้าถึง]
- Data Encryption: [การเข้ารหัสข้อมูล]

Usability Requirements:
- Ease of use: [ความง่ายในการใช้งาน]
- Accessibility: [การเข้าถึงสำหรับผู้พิการ]
- User satisfaction: [ความพึงพอใจของผู้ใช้]

Reliability Requirements:
- Availability: [เปอร์เซ็นต์เวลาที่ระบบพร้อมใช้งาน]
- Fault tolerance: [ความสามารถในการทำงานต่อเมื่อมีข้อผิดพลาด]
- Recovery time: [เวลาในการกู้คืนระบบ]
```

**Use Cases & User Stories (UX/UI Designer - 8 นาที)**
```
Use Case Diagram: 
- สร้างแผนภาพ Use Case สำหรับฟังก์ชันหลัก
- ระบุ Actors และ Use Cases
- แสดง relationships (include, extend, generalization)

Detailed Use Cases (เลือก 3 use cases สำคัญ):
Use Case: [ชื่อ]
Actor: [Primary Actor]  
Precondition: [เงื่อนไขก่อนเริ่ม]
Postcondition: [ผลลัพธ์หลังเสร็จสิ้น]
Main Flow:
1. [ขั้นตอนที่ 1]
2. [ขั้นตอนที่ 2]
...
Alternative Flows:
- [สถานการณ์พิเศษ]
```

**Quality Assurance & Validation (QA Specialist - 8 นาที)**
```
Acceptance Criteria สำหรับ User Stories:
- ตรวจสอบทุก User Story ว่ามี Acceptance Criteria
- ใช้ Given-When-Then format
- ระบุ success และ failure scenarios

Validation Scenarios:
Scenario 1: [ชื่อสถานการณ์]
Given: [บริบท]
When: [การกระทำ]  
Then: [ผลลัพธ์ที่คาดหวัง]
Success Criteria: [วิธีการวัดความสำเร็จ]

Requirements Traceability Matrix:
| Req ID | User Story | Use Case | Test Case | Priority |
|--------|------------|----------|-----------|----------|
| REQ-F001 | US-001 | UC-001 | TC-001 | High |
```

### Phase 4: Integration & Review (10 นาที)

#### Document Integration (5 นาที)
- **Documentation Specialist** รวบรวมทุก section
- ตรวจสอบ formatting และ consistency
- สร้าง Table of Contents
- เพิ่ม Glossary และ References

#### Internal Review (5 นาที)
**Review Checklist:**
```
Content Quality:
□ ครอบคลุมทุก stakeholder needs
□ Requirements ชัดเจนและ measurable
□ มี acceptance criteria ครบถ้วน
□ ไม่มี requirements ที่ขัดแย้งกัน

IEEE 830 Compliance:
□ มีโครงสร้างตามมาตรฐาน
□ Requirements เป็น SMART
□ มี unique identifiers
□ มี priority levels

Writing Quality:
□ ใช้ active voice
□ หลีกเลี่ยงคำที่คลุมเครือ
□ terminology สอดคล้องกัน
□ grammar ถูกต้อง
```

---

## 🎯 SRS Quality Standards & Evaluation Criteria

### IEEE 830 Compliance Checklist

#### ⭐ Excellent (90-100%)
```
Structure & Organization:
✅ สมบูรณ์ทุก section ตาม IEEE 830
✅ Table of contents และ appendices ครบถ้วน
✅ Cross-references ถูกต้อง

Requirements Quality:
✅ ทุก requirement เป็น SMART
✅ มี acceptance criteria ที่ชัดเจน
✅ ไม่มี ambiguous terms
✅ มี unique IDs และ priority levels

Technical Content:
✅ ครอบคลุมทั้ง functional และ non-functional
✅ Use cases สมบูรณ์และถูกต้อง
✅ มี traceability matrix
✅ Validation scenarios มีคุณภาพ
```

#### ⭐ Good (80-89%)
```
Structure & Organization:
✅ มีโครงสร้างหลักตาม IEEE 830
✅ บาง section อาจไม่สมบูรณ์
⚠️ Cross-references บางส่วนไม่ถูกต้อง

Requirements Quality:  
✅ Requirements ส่วนใหญ่เป็น SMART
⚠️ Acceptance criteria บางข้อไม่ชัดเจน
⚠️ มี ambiguous terms บางคำ
✅ มี IDs และ priorities

Technical Content:
✅ ครอบคลุมเนื้อหาหลัก
⚠️ Use cases อาจไม่สมบูรณ์
⚠️ Traceability ไม่ครบถ้วน
✅ มี validation scenarios พื้นฐาน
```

#### ⭐ Satisfactory (70-79%)
```
Structure & Organization:
✅ มีโครงสร้างพื้นฐาน
❌ ขาด section สำคัญบางส่วน
❌ ไม่มี cross-references

Requirements Quality:
⚠️ Requirements บางข้อไม่เป็น SMART  
❌ Acceptance criteria ไม่ครบ
❌ มี ambiguous terms หลายคำ
✅ มี basic IDs

Technical Content:
⚠️ ครอบคลุมเนื้อหาพื้นฐาน
❌ Use cases ไม่สมบูรณ์
❌ ไม่มี traceability
❌ Validation scenarios ไม่เพียงพอ
```

### Peer Review Evaluation Form

```
Team Name: _________________
Reviewer Team: _________________

Section 1: Document Structure (20 points)
□ IEEE 830 compliance (10 pts)
□ Organization & readability (5 pts)  
□ Completeness (5 pts)

Section 2: Requirements Quality (30 points)
□ SMART criteria compliance (15 pts)
□ Clarity & specificity (10 pts)
□ Acceptance criteria quality (5 pts)

Section 3: Technical Content (30 points)
□ Functional requirements coverage (15 pts)
□ Non-functional requirements (10 pts)
□ Use cases & user stories (5 pts)

Section 4: Professional Presentation (20 points)
□ Writing quality & grammar (10 pts)
□ Visual elements & formatting (5 pts)
□ Team collaboration evidence (5 pts)

Total Score: ___/100

Strengths:
1. _________________
2. _________________

Areas for Improvement:
1. _________________  
2. _________________

Specific Suggestions:
_________________
```

---

## 🎤 Presentation & Peer Review (15 นาที)

### Presentation Format (8 นาที)
แต่ละทีมมีเวลา 2 นาที presentation + 30 วินาที Q&A

#### Presentation Structure (2 นาที):
```
Slide 1: Project Overview (30 วินาที)
- Scenario ที่เลือก
- Key stakeholders
- Project vision/goals

Slide 2: Requirements Highlights (45 วินาที)  
- จำนวน functional/non-functional requirements
- ตัวอย่าง 2-3 requirements ที่สำคัญ
- Use cases หลัก

Slide 3: Quality & Validation (30 วินาที)
- Validation approach
- Acceptance criteria examples
- Traceability matrix overview  

Slide 4: Team Process & Lessons Learned (15 วินาที)
- การแบ่งหน้าที่
- Challenges และ solutions
- Key takeaways
```

### Peer Review Process (7 นาที)

#### Round Robin Review:
- แต่ละทีมแลกเปลี่ยนเอกสาร SRS กับทีมอื่น
- ใช้เวลา 5 นาที review และให้ feedback
- ใช้ Evaluation Form ข้างต้น

#### Best Practices for Peer Review:
```
DO:
✅ ให้ feedback ที่สร้างสรรค์
✅ ชี้ให้เห็นจุดเด่นก่อน
✅ แนะนำการปรับปรุงที่เฉพาะเจาะจง
✅ ใช้ IEEE 830 criteria เป็นมาตรฐาน

DON'T:
❌ วิจารณ์แบบไม่สร้างสรรค์
❌ เน้นแต่จุดด้อย
❌ ให้ feedback ที่คลุมเครือ
❌ เปรียบเทียบกับทีมอื่น
```

---

## 📊 Assessment Rubric

### การประเมินผลรวม (100 คแนน)

#### 1. SRS Document Quality (60 คะแนน)

**IEEE 830 Compliance (20 คะแนน)**
- Excellent (18-20): โครงสร้างสมบูรณ์ทุก section
- Good (15-17): โครงสร้างครบ บาง section ไม่สมบูรณ์  
- Satisfactory (12-14): โครงสร้างพื้นฐาน ขาดรายละเอียด
- Needs Improvement (0-11): โครงสร้างไม่เป็นไปตามมาตรฐาน

**Requirements Quality (25 คะแนน)**
- Excellent (23-25): ทุก requirement เป็น SMART, มี acceptance criteria ชัดเจน
- Good (20-22): Requirements ส่วนใหญ่มีคุณภาพ, criteria บางข้อไม่ชัดเจน
- Satisfactory (17-19): Requirements พื้นฐานถูกต้อง, ขาดรายละเอียด
- Needs Improvement (0-16): Requirements ไม่ชัดเจน, ไม่มี criteria

**Technical Content (15 คะแนน)**
- Excellent (14-15): Use cases สมบูรณ์, non-functional requirements ครอบคลุม
- Good (12-13): เนื้อหาเทคนิคดี, บางส่วนไม่สมบูรณ์
- Satisfactory (10-11): เนื้อหาพื้นฐาน, ขาดความลึก
- Needs Improvement (0-9): เนื้อหาเทคนิคไม่เพียงพอ

#### 2. Team Collaboration (20 คะแนน)

**Role Distribution (10 คะแนน)**
- การแบ่งหน้าที่ชัดเจน
- ทุกคนมีส่วนร่วม
- Specialization ตาม expertise

**Process Management (10 คะแนน)**  
- การจัดการเวลา
- การประสานงาน
- Problem-solving เป็นทีม

#### 3. Presentation & Communication (20 คะแนน)

**Content Presentation (10 คะแนน)**
- ความชัดเจนของการนำเสนอ
- Highlight ประเด็นสำคัญ
- การตอบคำถาม

**Professional Delivery (10 คะแนน)**
- การพูดและการนำเสนอ
- Visual aids
- Time management

---

## 🛠️ Tools & Templates

### Recommended Tools

#### For Document Creation:
- **Google Docs/Microsoft Word** - collaborative writing
- **Notion** - structured documentation
- **Confluence** - wiki-style documentation
- **GitBook** - technical documentation

#### For Diagramming:
- **Draw.io (diagrams.net)** - free UML diagrams
- **Lucidchart** - professional diagrams  
- **Miro** - collaborative brainstorming
- **Figma** - UI mockups and user journey

#### For Project Management:
- **Trello** - kanban boards
- **Google Sheets** - traceability matrix
- **Slack/Discord** - team communication

### Document Templates

#### SRS Document Template:
```
[Project Name] - Software Requirements Specification
Version 1.0
Date: [Date]
Team: [Team Name]

Table of Contents
1. Introduction
   1.1 Purpose
   1.2 Scope
   1.3 Definitions, Acronyms, Abbreviations  
   1.4 References
   1.5 Overview

2. Overall Description
   2.1 Product Perspective
   2.2 Product Functions
   2.3 User Characteristics
   2.4 Constraints
   2.5 Assumptions and Dependencies

3. Specific Requirements
   3.1 Functional Requirements
   3.2 Non-functional Requirements
   3.3 Interface Requirements

4. Use Cases and User Stories
   4.1 Use Case Diagrams
   4.2 Detailed Use Cases
   4.3 User Stories

5. Validation and Verification
   5.1 Acceptance Criteria
   5.2 Validation Scenarios
   5.3 Traceability Matrix

Appendices
A. Glossary
B. References  
C. Change Log
```