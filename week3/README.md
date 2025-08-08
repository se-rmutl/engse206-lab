# ENGSE206: การกำหนดความต้องการและการออกแบบทางซอฟต์แวร์
## สัปดาห์ที่ 3: การเขียนเอกสารและการตรวจสอบความต้องการ
*Software Requirements Specification and Design*

---

## Slide 1: Course Overview & Today's Learning Objectives

### สัปดาห์ที่ผ่านมา
- **สัปดาห์ที่ 1:** บทนำและการเก็บรวบรวมความต้องการ
- **สัปดาห์ที่ 2:** การวิเคราะห์และการจัดลำดับความสำคัญ

### วันนี้เราจะเรียนรู้
🎯 **Learning Objectives:**
1. **เขียนเอกสาร SRS** ตามมาตรฐาน IEEE 830
2. **สร้าง Use Cases และ User Stories** ที่มีคุณภาพ
3. **ใช้ SMART Criteria** ในการเขียนความต้องการ
4. **ตรวจสอบและ Validate** ความต้องการอย่างเป็นระบบ

### สิ่งที่จะได้รับ
- ทักษะการเขียนเอกสารระดับมืออาชีพ
- เครื่องมือสำหรับการสื่อสารกับ stakeholders
- วิธีการตรวจสอบความถูกต้องของความต้องการ

---

## Slide 2: Real-World Problem - "The Million Dollar Mistake"

### 🚨 Case Study: Ariane 5 Rocket Explosion (1996)
- **วันที่:** 4 มิถุนายน 1996
- **ผลลัพธ์:** จรวดระเบิดหลังยิง 37 วินาที
- **ความเสียหาย:** $500 ล้านดอลลาร์

### สาเหตุหลัก
> **"Inertial reference system tried to convert a 64-bit floating point number to a 16-bit signed integer"**

### แต่สาเหตุที่แท้จริงคือ...
❌ **ปัญหาในเอกสาร Requirements:**
- ไม่ระบุข้อจำกัดของระบบอย่างชัดเจน
- ไม่มีการ validate requirements ข้าม subsystems
- เอกสารไม่ครอบคลุม edge cases

### 💡 Active Learning Question
**Q: หากคุณเป็น Requirements Engineer ใน project นี้ คุณจะเขียน requirement ยังไงให้ป้องกันปัญหานี้?**

*ให้นักศึกษาคิด 2 นาที แล้วแบ่งปันความคิดเห็น*

---

## Slide 3: Software Requirements Specification (SRS) - บทนำ

### 📋 SRS คืออะไร?
> **Software Requirements Specification (SRS)** คือเอกสารที่อธิบายอย่างละเอียดว่าระบบซอฟต์แวร์ควรทำอะไร และทำงานภายใต้เงื่อนไขอย่างไร

### 🎯 จุดประสงค์ของ SRS
1. **สื่อสาร** ระหว่าง stakeholders ทุกฝ่าย
2. **กำหนดขอบเขต** ของโครงการอย่างชัดเจน
3. **เป็นพื้นฐาน** สำหรับการออกแบบและการทดสอบ
4. **จัดการการเปลี่ยนแปลง** อย่างเป็นระบบ

### 📊 Statistics from IEEE Studies
- โครงการที่มี SRS ที่ดี: **มีโอกาสสำเร็จ 70% มากกว่า**
- การมี SRS ลดต้นทุนการแก้ไข: **ถึง 200 เท่า** เมื่อเทียบกับการแก้ไขหลัง deployment

### 🤔 Quick Poll
**ใครเคยเขียนเอกสาร requirements บ้าง? ปัญหาที่เจอคืออะไร?**
- A) ไม่รู้จะเขียนยังไง
- B) ผู้อ่านไม่เข้าใจ
- C) เขียนแล้วแต่ไม่ได้ใช้
- D) อื่นๆ

---

## Slide 4: มาตรฐาน IEEE 830 - The Gold Standard

### 📖 IEEE 830 Standard Overview
**IEEE Std 830-1998:** "Recommended Practice for Software Requirements Specifications"

### 🏗️ โครงสร้างหลัก
```
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
   3.3 Design Constraints
```

### ⭐ หลักการสำคัญของ IEEE 830
1. **Correct** - ความต้องการทุกข้อต้องถูกต้อง
2. **Unambiguous** - ไม่คลุมเครือ มีความหมายเดียว
3. **Complete** - ครอบคลุมทุกสิ่งที่จำเป็น
4. **Consistent** - ไม่ขัดแย้งกัน
5. **Ranked** - จัดลำดับความสำคัญ
6. **Verifiable** - สามารถตรวจสอบได้
7. **Modifiable** - แก้ไขได้ง่าย
8. **Traceable** - ติดตามได้

---

## Slide 5: Hands-on Exercise - SRS Quality Check

### 🔍 ตัวอย่าง Requirements ที่มีปัญหา

#### Requirement A
> "The system shall be user-friendly and provide good performance."

#### Requirement B  
> "When user clicks login button, system should validate credentials and if valid, redirect to dashboard, otherwise show error message, unless server is down then show maintenance page."

#### Requirement C
> "The system must process transactions quickly."

### 📝 Group Activity (5 นาที)
**แบ่งกลุ่ม 3-4 คน วิเคราะห์ requirements ข้างต้น:**

1. ข้อไหนผิดหลักการ IEEE 830 อย่างไร?
2. จะแก้ไขยังไงให้ดีขึ้น?

### ✅ ตัวอย่างคำตอบ
**Requirement A Issues:**
- ❌ **Ambiguous:** "user-friendly", "good performance" คืออะไร?
- ❌ **Not Verifiable:** วัดยังไง?

**Fixed Version:**
> "The system shall respond to user requests within 2 seconds under normal load (≤100 concurrent users) and maintain 99.9% uptime."

---

## Slide 6: SMART Criteria - เขียน Requirements ให้ชัดเจน

### 🎯 SMART Framework
**S**pecific - เฉพาะเจาะจง  
**M**easurable - วัดผลได้  
**A**chievable - ทำได้จริง  
**R**elevant - เกี่ยวข้อง  
**T**ime-bound - มีกรอบเวลา  

### 📊 ตัวอย่างการปรับปรุง Requirements

| ❌ ไม่ SMART | ✅ SMART |
|-------------|---------|
| "System should be fast" | "System shall respond to search queries within 3 seconds for 95% of requests under normal load" |
| "Easy to use interface" | "New users shall complete account registration within 5 minutes without external help in 90% of cases" |
| "Secure system" | "System shall encrypt all user data using AES-256 and require multi-factor authentication for admin access" |

### 🔧 SMART Template
```
The [system/component] shall [specific action] 
[measurable criteria] within [time constraint] 
under [specified conditions].
```

### 💡 Practice Exercise
**เขียน SMART requirement สำหรับ:**
> "ระบบห้องสมุดควรให้ผู้ใช้ค้นหาหนังสือได้ง่าย"

*ให้เวลา 3 นาที เขียนใน chat หรือกระดาษ*

---

## Slide 7: Use Case Modeling - เล่าเรื่องของระบบ

### 🎭 Use Case คืออะไร?
> **Use Case** คือการอธิบายปฏิสัมพันธ์ระหว่าง actor (ผู้ใช้) กับระบบ เพื่อให้บรรลุเป้าหมายที่เฉพาะเจาะจง

### 🧩 องค์ประกอบของ Use Case
1. **Actor** - ผู้ที่มีปฏิสัมพันธ์กับระบบ
2. **Use Case** - ฟังก์ชันหรือบริการของระบบ
3. **System Boundary** - ขอบเขตของระบบ
4. **Relationships** - ความสัมพันธ์ระหว่าง elements

### 📋 Use Case Specification Format
```
Use Case Name: [ชื่อ Use Case]
Actor: [Primary Actor]
Precondition: [เงื่อนไขก่อนเริ่ม]
Postcondition: [ผลลัพธ์หลังสำเร็จ]
Main Flow:
  1. [Actor action]
  2. [System response]
  3. [...]
Alternative Flows:
  - [Exception scenarios]
```

### 🏥 ตัวอย่าง: ระบบโรงพยาบาล

#### Use Case: "จองนัดหมายแพทย์"
- **Actor:** ผู้ป่วย
- **Precondition:** ผู้ป่วยมี account ในระบบ
- **Main Flow:**
  1. ผู้ป่วยล็อกอินเข้าระบบ
  2. ระบบแสดงหน้าจองนัดหมาย
  3. ผู้ป่วยเลือกแผนกและแพทย์
  4. ระบบแสดงช่วงเวลาว่าง
  5. ผู้ป่วยเลือกวันและเวลา
  6. ระบบยืนยันการจองและส่ง SMS

---

## Slide 8: Use Case Diagram - Visual Storytelling

### 🎨 Use Case Diagram Elements

```
🤵 Actor (Stick Figure)
⭕ Use Case (Oval)
📦 System Boundary (Rectangle)
➡️ Association (Line)
⬅️ Include (Dashed arrow with <<include>>)
↗️ Extend (Dashed arrow with <<extend>>)
🔺 Generalization (Solid line with triangle)
```

### 📚 ตัวอย่าง: ระบบห้องสมุดดิจิทัล (EduLib Connect)

```
                Library Management System
    ┌─────────────────────────────────────────────┐
    │  📚 Search Books        📖 Borrow Books     │
    │      ⭕                      ⭕             │
    │       │                      │             │
🤵 Student ──┼──────────────────────┼─────────────│
    │       │                      │             │  
    │  📝 Reserve Books       📱 Renew Books      │
    │      ⭕                      ⭕             │
    │                                             │
    │  📊 Generate Reports    🔧 Manage System    │
    │      ⭕                      ⭕             │
    │       │                      │             │
👩‍💼 Librarian ┼──────────────────────┼─────────────│
    │       │                      │             │
    │  📈 View Statistics     ⚙️ Backup Data     │
    │      ⭕                      ⭕             │
    └─────────────────────────────────────────────┘
```

### 🎯 Group Exercise (8 นาที)
**วาด Use Case Diagram สำหรับ "MoneyWise App"**
- **Actors:** นักศึกษา, คนทำงาน, แม่บ้าน
- **Main Functions:** บันทึกรายจ่าย, ตั้งเป้าหมายการออม, ดูรายงาน, แจ้งเตือน

*แบ่งกลุ่ม 4-5 คน วาดบนกระดาษ A4 หรือ whiteboard*

---

## Slide 9: User Stories - Agile Approach

### 📖 User Story vs Use Case

| Use Case | User Story |
|----------|------------|
| 📄 เอกสารยาว รายละเอียดมาก | 📝 สั้น กระชับ |
| 🎯 เน้นขั้นตอนการทำงาน | 💝 เน้นคุณค่าที่ผู้ใช้ได้รับ |
| 🏗️ แบบ Waterfall | 🔄 แบบ Agile |
| 🧠 Technical perspective | ❤️ User perspective |

### 📝 User Story Template
```
As a [type of user],
I want [to perform some task]
So that [I can achieve some goal/benefit]
```

### 🎯 ตัวอย่าง User Stories - MoneyWise App

#### Story 1: การบันทึกรายจ่าย
```
As a busy working professional,
I want to quickly add expenses by taking photos of receipts
So that I can track my spending without manual data entry
```

#### Story 2: การแจ้งเตือน
```
As a forgetful student,
I want to receive notifications when I'm approaching my monthly budget limit
So that I can avoid overspending and stay within my financial goals
```

#### Story 3: การวิเคราะห์
```
As a family breadwinner,
I want to see visual charts of my family's spending patterns
So that I can identify areas where we can save money
```

### ✍️ Quick Exercise
**เขียน User Story สำหรับ:**
"ฟีเจอร์แบ่งปันค่าใช้จ่ายกับเพื่อน"
*2 นาที*

---

## Slide 10: Acceptance Criteria - Definition of Done

### ✅ Acceptance Criteria คืออะไร?
> **Acceptance Criteria** คือเงื่อนไขที่ระบุอย่างชัดเจนว่า User Story จะถือว่าสำเร็จเมื่อไหร่

### 🎯 จุดประสงค์
1. **กำหนดขอบเขต** ของ User Story
2. **ป้องกันความเข้าใจผิด** ระหว่าง team
3. **เป็นพื้นฐาน** สำหรับการเขียน test cases
4. **เกณฑ์การยอมรับ** สำหรับ Product Owner

### 📋 รูปแบบการเขียน

#### Given-When-Then Format
```
Given [precondition/context]
When [action/event]  
Then [expected outcome]
And [additional outcome]
```

#### Rule-oriented Format
```
- User can [action] when [condition]
- System shall [behavior] if [scenario]
- [Field] must [validation rule]
```

### 🏦 ตัวอย่าง: MoneyWise Expense Tracking

#### User Story
```
As a user,
I want to categorize my expenses
So that I can understand my spending patterns
```

#### Acceptance Criteria
```
Given I am adding a new expense
When I select a category from the dropdown
Then the expense should be saved with the selected category
And the category should appear in my expense reports

Given I am viewing my expense list
When I filter by category
Then I should see only expenses from that category
And the total amount for that category should be displayed

Given I try to save an expense without selecting a category
When I submit the form
Then I should see an error message "Please select a category"
And the expense should not be saved
```

---

## Slide 11: Workshop Activity - Writing User Stories & Acceptance Criteria

### 🎮 Scenario: "Smart Classroom System"
มหาวิทยาลัยต้องการระบบจัดการห้องเรียนอัจฉริยะ

#### Background
- ห้องเรียน 50 ห้อง
- อุปกรณ์: โปรเจ็กเตอร์, เครื่องเสียง, แอร์, ไฟ, กล้อง
- ผู้ใช้: อาจารย์, นักศึกษา, เจ้าหน้าที่ IT

### 📋 Team Exercise (15 นาที)

#### Round 1: Brainstorm Personas (5 นาที)
แต่ละทีมเลือก 1 persona และนึกถึง pain points

**Personas:**
- 👨‍🏫 อาจารย์อายุ 45 ปี (ไม่ค่อยเก่งเทคโนโลジี)
- 👨‍🎓 นักศึกษาปี 1 (เก่งเทคโนโลจี)
- 🔧 เจ้าหน้าที่ IT (ต้องแก้ปัญหาระบบ)

#### Round 2: Write User Stories (7 นาที)
เขียน 3 User Stories สำหรับ persona ที่เลือก

#### Round 3: Add Acceptance Criteria (3 นาที)
เลือก 1 story ที่ดีที่สุด เขียน Acceptance Criteria

### 📊 Sharing & Feedback
แต่ละทีมนำเสนอ 1 User Story พร้อม Acceptance Criteria (1 นาทีต่อทีม)

### 🏆 Voting
โหวต User Story ที่ดีที่สุดตามเกณฑ์:
- ความชัดเจน
- ความเป็นไปได้
- คุณค่าที่ได้รับ

---

## Slide 12: Requirements Verification vs Validation

### 🔍 ความแตกต่างพื้นฐาน

| Verification | Validation |
|-------------|-----------|
| **"Are we building the product right?"** | **"Are we building the right product?"** |
| ตรวจสอบว่าทำตาม specification ถูกต้องหรือไม่ | ตรวจสอบว่าผลิตภัณฆ์ตอบโจทย์ user ได้หรือไม่ |
| 🔧 Process-oriented | 👥 User-oriented |
| 📋 Document reviews, inspections | 🧪 Prototyping, user testing |

### 🎯 เป้าหมายของแต่ละกิจกรรม

#### Verification Goals
- ✅ Requirements ไม่ขัดแย้งกัน
- ✅ ครอบคลุมทุก functional areas
- ✅ ปฏิบัติตามได้จริง
- ✅ มีความสอดคล้องกับ business rules

#### Validation Goals  
- ✅ ตอบโจทย์ real user needs
- ✅ ใช้งานได้จริงในสภาพแวดล้อมจริง
- ✅ สร้างคุณค่าให้กับธุรกิจ
- ✅ ผู้ใช้พึงพอใจกับผลลัพธ์

### 💡 Remember Barry Boehm's Quote
> "Verification and validation are independent procedures that are used together for checking that a product, service, or system meets requirements and specifications and that it fulfills its intended purpose."

---

## Slide 13: Verification Techniques - ตรวจสอบความถูกต้อง

### 📋 1. Requirements Reviews & Inspections

#### Formal Inspection Process (Fagan Inspection)
```
1. Planning → 2. Overview → 3. Preparation → 4. Inspection → 5. Rework → 6. Follow-up
```

**Roles:**
- **Moderator:** คุมประชุม, จัดการกระบวนการ
- **Author:** คนเขียน requirements
- **Reviewer:** ผู้เชี่ยวชาญด้านต่างๆ
- **Scribe:** บันทึกข้อบกพร่อง

#### 🔍 Inspection Checklist
```
□ ครบถ้วน (Complete) - ไม่มี missing requirements
□ ถูกต้อง (Correct) - สอดคล้องกับ business needs  
□ ชัดเจน (Clear) - ไม่คลุมเครือ
□ สอดคล้อง (Consistent) - ไม่ขัดแย้งกัน
□ ปฏิบัติได้ (Feasible) - ทำได้จริงด้วยเทคโนโลยีที่มี
□ ทดสอบได้ (Testable) - วัดผลได้
□ จำเป็น (Necessary) - ต้องมีจริงๆ
```

### 🤖 2. Automated Analysis Tools

#### Static Analysis Tools
- **Requirement quality metrics**
- **Consistency checking**  
- **Completeness analysis**
- **Traceability verification**

#### Popular Tools
- IBM DOORS
- Jama Connect  
- ReqSuite
- Modern Requirements

### 📊 3. Metrics-Based Verification

#### Quality Metrics
```
Completeness = (Requirements Implemented / Total Requirements) × 100%
Consistency = 1 - (Conflicts Found / Total Requirements)
Clarity = 1 - (Ambiguous Requirements / Total Requirements)
```

---

## Slide 14: Validation Techniques - ตรวจสอบความเหมาะสม

### 🧪 1. Prototyping

#### Types of Prototypes
- **Paper Prototypes:** ร่างออกแบบบนกระดาษ
- **Digital Mockups:** ใช้เครื่องมือ UI design
- **Interactive Prototypes:** คลิกได้ นำทางได้
- **Functional Prototypes:** มีฟังก์ชันพื้นฐาน

#### 📱 ตัวอย่าง: MoneyWise App Validation
```
Week 1: Paper sketches → User interviews (5 users)
Week 2: Figma mockups → Online survey (50 users)  
Week 3: Interactive prototype → Usability testing (10 users)
Week 4: Beta version → Field testing (100 users)
```

### 👥 2. User Acceptance Testing (UAT)

#### UAT Process
```
1. Define acceptance criteria
2. Create test scenarios
3. Select representative users
4. Execute tests in real environment
5. Collect feedback
6. Prioritize changes
```

#### 🎯 UAT Success Criteria
- **Task completion rate** ≥ 90%
- **User satisfaction score** ≥ 4/5
- **Error rate** ≤ 5%
- **Time to complete tasks** within expected range

### 🔄 3. Stakeholder Reviews

#### Regular Checkpoint Reviews
- **Sprint Reviews** (Agile teams)
- **Milestone Reviews** (Traditional projects)
- **Executive Steering Committee** (Strategic decisions)

---

## Slide 15: Hands-on Validation Exercise

### 🎯 Scenario: "University Food Delivery App"

#### Background
มหาวิทยาลัยต้องการ app สั่งอาหารส่งถึงหอพัก/ห้องเรียน

#### Requirements (Draft)
```
REQ-001: Students can browse food menus from campus restaurants
REQ-002: System shall process payments securely  
REQ-003: Delivery tracking should be available
REQ-004: App must work on iOS and Android
REQ-005: Order history should be accessible
```

### 🔍 Validation Exercise (10 นาที)

#### Step 1: Stakeholder Analysis (3 นาที)
**ใครคือ stakeholders?**
- Primary: นักศึกษา, ร้านอาหาร, คนส่ง
- Secondary: มหาวิทยาลัย, ผู้ปกครอง, ระบบการเงิน

#### Step 2: Create Validation Scenarios (4 นาที)
**เลือก 1 requirement เขียน validation scenario:**

Template:
```
Given [context]
When [user action]
Then [expected outcome]
Success criteria: [how to measure]
```

#### Step 3: Identify Validation Methods (3 นาที)
**วิธีการ validate แต่ละ requirement:**
- User interviews
- Prototype testing
- Survey
- Market research
- Technical feasibility study

### 💭 Discussion Questions
1. Requirement ไหนควร validate ก่อน? ทำไม?
2. วิธีไหนที่เหมาะสมที่สุดสำหรับแต่ละ requirement?
3. ความเสี่ยงอะไรบ้างถ้าไม่ validate?

---

## Slide 16: UML Use Case Diagrams - Deep Dive

### 🎨 Advanced UML Relationships

#### Include Relationship (<<include>>)
```
Primary Use Case ---- <<include>> ----> Secondary Use Case
```
**ใช้เมื่อ:** มี common behavior ที่หลาย use cases ต้องใช้

#### Extend Relationship (<<extend>>)
```
Extension Use Case ---- <<extend>> ----> Base Use Case
```
**ใช้เมื่อ:** มี optional behavior เพิ่มเติม

#### Generalization
```
Child Use Case ────────▷ Parent Use Case
```
**ใช้เมื่อ:** มี specialized versions ของ general use case

### 🏦 ตัวอย่าง: Banking System

```
                    Online Banking System
    ┌─────────────────────────────────────────────────┐
    │                                                 │
    │        Login                                    │
🤵 Customer ⭕ ←──<<include>>──⭕ Check Balance          │
    │        │                                        │
    │        │                 ⭕ Transfer Money       │  
    │        └──<<include>>──⭕ ←──<<extend>>──⭕       │
    │                        Pay Bills    Pay Bills   │
    │                                    Internationally│
    │                                                 │
    │        ⭕ Generate Report  ⭕ Manage Accounts     │
👩‍💼 Bank Admin ───┼─────────────────┼─────────────────│
    │        │                 │                     │
    │        └─────────────▷ Generate ◁───────────────┘
    │                      Monthly    Yearly
    │                      Report    Report
    └─────────────────────────────────────────────────┘
```

### 🎯 Practice: Draw Relationships
**ระบบ E-learning Platform**
- Base: "Take Quiz"  
- Extensions: "Take Timed Quiz", "Take Open Book Quiz"
- Include: "Authenticate User", "Save Progress"

---

## Slide 17: Documentation Best Practices

### 📝 Writing Style Guidelines

#### 1. Use Active Voice
```
❌ "Data will be encrypted by the system"
✅ "The system shall encrypt data"
```

#### 2. Avoid Weak Words
```
❌ Weak: "should", "might", "usually", "normally"
✅ Strong: "shall", "must", "will", "always"
```

#### 3. Be Specific with Numbers
```
❌ "System should handle many users"
✅ "System shall support 1000 concurrent users"
```

#### 4. Use Consistent Terminology
```
Create a glossary:
- User = registered person with account
- Customer = user who made purchase
- Admin = system administrator
- Session = login period
```

### 📚 Documentation Structure Tips

#### Section Organization
```
1. Executive Summary (1-2 pages)
   - Key requirements overview
   - Business justification
   
2. Functional Requirements (detailed)
   - Organized by feature/module
   - Priority levels marked
   
3. Non-functional Requirements
   - Performance, Security, Usability
   - Acceptance criteria for each
   
4. Appendices
   - Glossary, References, Change log
```

#### 🎯 Template for Each Requirement
```
REQ-ID: [Unique identifier]
Title: [Brief descriptive name]
Description: [Detailed specification]
Priority: [High/Medium/Low]
Source: [Who requested this]
Rationale: [Why needed]
Dependencies: [Related requirements]
Acceptance Criteria: [How to verify]
```

### 🔧 Tools for Documentation

#### Popular SRS Tools
- **Microsoft Word** + Templates
- **Confluence** - Wiki-based
- **GitBook** - Developer-friendly
- **Notion** - Modern collaborative
- **LaTeX** - Academic/formal documents

---

## Slide 18: Quality Assurance Checklist

### ✅ SRS Quality Checklist

#### Content Quality
```
□ All stakeholder needs addressed
□ Business rules clearly defined
□ Assumptions explicitly stated
□ Constraints identified
□ Success criteria measurable
□ Failure scenarios covered
□ Integration points specified
□ Data requirements complete
```

#### Writing Quality
```
□ No ambiguous words (e.g., "user-friendly")
□ Consistent terminology throughout
□ Active voice used
□ Requirements numbered/labeled
□ Cross-references accurate
□ Grammar and spelling correct
□ Appropriate level of detail
□ Logical organization
```

#### Technical Quality
```
□ Feasible with current technology
□ Performance targets realistic
□ Security requirements adequate
□ Scalability considered
□ Maintenance requirements clear
□ Testing approach defined
□ Deployment requirements specified
□ Backup/recovery procedures outlined
```

### 🎯 Review Process

#### 3-Stage Review
```
Stage 1: Self-Review (Author)
- Complete checklist above
- Fix obvious issues

Stage 2: Peer Review (Team)
- Technical accuracy
- Completeness check
- Consistency verification

Stage 3: Stakeholder Review
- Business alignment
- User acceptance
- Final approval
```

---

## Slide 19: Case Study - MoneyWise App SRS

### 📱 Complete SRS Example

#### 1. Introduction
```
1.1 Purpose
This SRS specifies requirements for MoneyWise, a personal 
finance management mobile application targeting Thai users 
aged 18-45.

1.2 Scope
MoneyWise helps users track expenses, set savings goals, 
and improve financial literacy through gamification and 
community features.

1.3 Definitions
- User: Registered application user
- Transaction: Financial income or expense entry
- Goal: User-defined savings or spending target
- Badge: Achievement reward for completing financial milestones
```

#### 2. Overall Description
```
2.1 Product Perspective
MoneyWise is a standalone mobile application that integrates 
with Thai banking APIs and provides offline functionality 
for expense tracking.

2.2 User Classes
- Primary: Young professionals (22-35 years)
- Secondary: University students (18-22 years)  
- Tertiary: Middle-aged adults (36-45 years)
```

#### 3. Specific Requirements

#### 3.1 Functional Requirements
```
REQ-F001: Expense Tracking
The system shall allow users to add expenses by:
- Manual entry with category selection
- Photo capture of receipts with OCR processing
- Bank transaction import via API

Acceptance Criteria:
- Manual entry completes in <30 seconds
- OCR accuracy ≥85% for printed receipts
- Bank import processes within 5 minutes
```

```
REQ-F002: Goal Setting
The system shall enable users to create SMART financial goals:
- Savings targets with deadlines
- Spending limits by category
- Progress tracking with visual indicators

Acceptance Criteria:
- Goal creation wizard completes in <2 minutes
- Progress updates in real-time
- Visual progress bar shows percentage completion
```

---

## Slide 20: Interactive Workshop - SRS Review

### 🔍 Group SRS Review Exercise (15 นาที)

#### Scenario Setup
คุณได้รับ SRS draft สำหรับ "Smart Library System" จากทีมพัฒนา

#### The Requirements (มีปัญหาเจตนา)
```
REQ-001: The system should be intuitive and easy to use
REQ-002: Books can be searched using various criteria  
REQ-003: System must handle concurrent users effectively
REQ-004: Overdue fines will be calculated automatically
REQ-005: The mobile app should work on smartphones
REQ-006: Backup occurs regularly to prevent data loss
REQ-007: Reports are generated for library management
```

#### Review Instructions
**แบ่งกลุ่ม 4-5 คน, ใช้เวลา 10 นาทีในการ:**

1. **Identify Problems (5 นาที)**
   - ใช้ IEEE 830 principles เป็นเกณฑ์
   - ใช้ SMART criteria ตรวจสอบ
   - บันทึกปัญหาที่พบ

2. **Rewrite Requirements (5 นาที)**
   - เลือก 2-3 requirements ที่มีปัญหามาก
   - เขียนใหม่ให้ถูกต้อง
   - เพิ่ม acceptance criteria

#### Review Framework
```
For each requirement ask:
- Is it specific enough?
- Can we measure success?
- Is it technically feasible?
- Why is this needed? (rationale)
- How will we test it?
```

### 📊 Share & Compare
แต่ละกลุ่มนำเสนอ:
- ปัญหาที่พบมากที่สุด (1 นาที)
- Requirements ที่เขียนใหม่ (2 นาที)

---

## Slide 21: Traceability Matrix - เชื่อมโยงความต้องการ

### 🔗 Requirements Traceability คืออะไร?
> **Traceability** คือความสามารถในการติดตาม และเชื่อมโยงความสัมพันธ์ระหว่าง requirements กับ artifacts อื่นๆ ตตลอด software lifecycle

### 📊 Traceability Matrix Structure

| Requirement ID | Business Need | Design Element | Test Case | Status |
|---------------|---------------|----------------|-----------|---------|
| REQ-F001 | BN-001 | UC-Login, DB-User | TC-001, TC-002 | ✅ |
| REQ-F002 | BN-002 | UC-Search, API-Search | TC-003, TC-004 | 🔄 |
| REQ-NF001 | BN-001 | ARCH-Security | TC-005 | ❌ |

### 🎯 Types of Traceability

#### Forward Traceability
```
Business Needs → Requirements → Design → Code → Tests
```

#### Backward Traceability  
```
Code ← Design ← Requirements ← Business Needs
```

#### Bi-directional Traceability
```
Business Needs ↔ Requirements ↔ Design ↔ Tests
```

### 🛠️ Traceability Tools
- **JIRA** with requirement links
- **Azure DevOps** work item linking
- **IBM DOORS** advanced traceability
- **Jama Connect** requirements management
- **Excel/Google Sheets** for simple projects

### 💡 Benefits
- **Impact Analysis** - รู้ว่าการเปลี่ยนแปลงกระทบอะไรบ้าง
- **Coverage Analysis** - มั่นใจว่าทุก requirement ถูกทดสอบ
- **Change Management** - ติดตามการเปลี่ยนแปลง
- **Compliance** - พิสูจน์การปฏิบัติตามมาตรฐาน

---

## Slide 22: Change Management Process

### 🔄 Why Requirements Change?

#### Common Reasons
- **Business Environment Changes** (40%)
- **Better Understanding of Needs** (25%)
- **Technology Constraints Discovery** (15%)
- **Stakeholder Feedback** (10%)
- **Regulatory Changes** (10%)

### 📋 Change Control Process

#### 1. Change Request Submission
```
Change Request Form:
- Requester information
- Current requirement
- Proposed change
- Business justification
- Impact assessment
- Priority level
```

#### 2. Impact Analysis
```
Technical Impact:
□ Architecture changes needed?
□ Database schema changes?
□ API modifications required?
□ Third-party integrations affected?

Project Impact:
□ Schedule impact (days/weeks)
□ Budget implications
□ Resource requirements
□ Risk assessment
```

#### 3. Change Review Board
```
Members:
- Product Owner (business impact)
- Technical Lead (technical feasibility)
- Project Manager (schedule/budget)
- QA Lead (testing implications)
- Key Stakeholders (business alignment)
```

#### 4. Decision & Implementation
```
Possible Outcomes:
✅ Approved - implement immediately
🟡 Approved - implement in next release
⏸️ Deferred - evaluate later
❌ Rejected - document rationale
```

### 📈 Change Metrics
```
Change Request Volume = Total Changes / Total Requirements
Change Acceptance Rate = Approved Changes / Total Requests
Average Impact = Sum of Effort Days / Number of Changes
```

---

## Slide 23: Modern Documentation Approaches

### 🚀 Agile Documentation Principles

#### "Just Enough" Documentation
- **Working software over comprehensive documentation**
- **Collaborative documentation** over handoff documents
- **Living documents** over static specifications
- **Visual models** over text-heavy descriptions

### 📱 Documentation as Code

#### Benefits
```
✅ Version controlled with code
✅ Automated generation possible
✅ Developer-friendly workflow
✅ Always up-to-date
✅ Easy to maintain
```

#### Tools & Formats
```
- Markdown files in Git repositories
- API documentation with Swagger/OpenAPI
- Architecture diagrams with PlantUML
- Requirements in YAML/JSON format
- Automated publishing with GitBook/Docusaurus
```

### 🎨 Visual Documentation

#### Living Style Guides
- **Storybook** for UI components
- **Figma** for design systems
- **Miro/Mural** for collaborative diagrams
- **Draw.io** for technical diagrams

#### Example: API-First Documentation
```yaml
# requirements.yml
user_authentication:
  description: "User login functionality"
  priority: high
  acceptance_criteria:
    - username_validation: "Must be valid email format"
    - password_strength: "Minimum 8 characters with special chars"
    - session_duration: "24 hours maximum"
  test_cases:
    - valid_login
    - invalid_credentials
    - session_timeout
```

### 💡 Interactive Documentation
- **Executable specifications** with Cucumber/Gherkin
- **Live prototypes** with Figma/InVision
- **Interactive API docs** with Postman/Insomnia
- **Notebook-style docs** with Jupyter/Observable

---

## Slide 24: Workshop Capstone - Complete SRS Section

### 🎯 Final Challenge: Team SRS Creation

#### Project: "EcoTrack - Carbon Footprint Tracker"

#### Background
```
มหาวิทยาลัยต้องการแอปฯ ช่วยนักศึกษาและเจ้าหน้าที่
ติดตามการปล่อยก๊าซเรือนกระจก เพื่อเป้าหมาย
Carbon Neutral University 2030
```

#### Key Features (provided)
- การบันทึกการเดินทาง (รถยนต์, รถไฟฟ้า, เดิน)
- การติดตามการใช้พลังงาน (ไฟฟ้า, น้ำ)
- การจัดการขยะและรีไซเคิล
- ระบบแต้มและ gamification
- รายงานสรุปรายเดือน

### 📝 Assignment (20 นาที)

#### Team Formation
- กลุ่มละ 5-6 คน
- แต่ละคนรับผิดชอบ 1 ส่วน

#### Tasks Distribution
```
Person 1: Introduction & Scope (Section 1)
Person 2: Overall Description & User Classes (Section 2.1-2.2)
Person 3: Functional Requirements - Travel tracking (Section 3.1.1)
Person 4: Functional Requirements - Energy monitoring (Section 3.1.2)  
Person 5: Non-functional Requirements (Section 3.2)
Person 6: Use Cases & Acceptance Criteria (Section 4)
```

#### Deliverables
```
1. Complete SRS section (following IEEE 830)
2. At least 3 detailed requirements with acceptance criteria
3. 1 use case diagram with 5+ use cases
4. Traceability matrix (requirements to use cases)
```

#### Quality Criteria
```
✅ SMART requirements
✅ Clear acceptance criteria
✅ Consistent terminology
✅ Proper IEEE 830 structure
✅ Stakeholder needs addressed
```

### ⏰ Timeline
- **5 min:** Team formation & task assignment
- **12 min:** Individual section writing
- **3 min:** Team integration & review

### 🏆 Presentation (Next 15 minutes)
Each team presents 1 section + Q&A (2 min per team)

---

## Slide 25: Summary & Next Steps

### 🎯 Today's Key Takeaways

#### 1. SRS Documentation
```
✅ IEEE 830 provides gold standard structure
✅ SMART criteria ensure quality requirements
✅ Consistency and clarity are crucial
✅ Templates and checklists improve quality
```

#### 2. Use Cases & User Stories
```
✅ Use Cases detail system interactions
✅ User Stories focus on user value
✅ Both need clear acceptance criteria
✅ Visual diagrams aid understanding
```

#### 3. Verification & Validation
```
✅ Verification = "Building it right"
✅ Validation = "Building the right thing"
✅ Multiple techniques needed
✅ Early validation saves cost
```

#### 4. Quality Assurance
```
✅ Reviews catch 60-90% of defects
✅ Traceability enables impact analysis
✅ Change management prevents scope creep
✅ Modern tools improve efficiency
```

### 📚 Required Reading for Next Week
1. **Chapter 6:** "Software Design Fundamentals" 
2. **Article:** "SOLID Principles Explained with Examples"
3. **Case Study:** "Design Patterns in E-commerce Systems"

### 🎯 Assignment Due Next Week
**Individual Assignment:**
- Write complete SRS for your chosen project (from Week 1)
- Include 10+ functional requirements
- 5+ non-functional requirements  
- Use case diagram with 8+ use cases
- Acceptance criteria for all requirements

**Submission:**
- PDF format, 15-20 pages
- Upload to LMS by Sunday 11:59 PM
- Peer review assignments Monday

### 🔮 Next Week Preview: "Software Design Fundamentals"
- SOLID Principles in action
- Design Patterns introduction  
- Code quality metrics
- Hands-on refactoring workshop

### ❓ Q&A Session

**Common Questions:**

**Q: ความแตกต่างหลักระหว่าง Use Case และ User Story?**
A: Use Case เน้นขั้นตอนการทำงาน (how), User Story เน้นคุณค่าที่ได้รับ (why). ใช้ Use Case สำหรับระบบซับซ้อน, User Story สำหรับ Agile development.

**Q: จำเป็นต้องเขียน SRS แบบ IEEE 830 ทุกโครงการมั้ย?**
A: ไม่จำเป็น ขึ้นอยู่กับ context - โครงการใหญ่/critical systems ควรใช้ formal SRS, โครงการเล็ก/Agile อาจใช้ User Stories + Definition of Done

**Q: วิธีจัดการเมื่อ stakeholders ให้ requirements ที่ขัดแย้งกัน?**
A: 1) จัด workshop ให้พบกัน 2) ใช้ prioritization techniques 3) ระบุ trade-offs ชัดเจน 4) ให้ผู้มีอำนาจตัดสินใจสุดท้าย

**Q: ถ้า requirements เปลี่ยนบ่อยมาก ควรทำยังไง?**
A: 1) ตรวจสอบว่า stakeholders เข้าใจ scope ชัดเจนมั้ย 2) ใช้ agile approach กับ short iterations 3) ตั้ง change control process 4) educate stakeholders เรื่องต้นทุนของการเปลี่ยนแปลง

### 🙏 Thank You!
**Contact Information:**
- Email: instructor@university.ac.th
- Office Hours: Tuesdays & Thursdays 2-4 PM
- Course Forum: Available on LMS

**Remember:** Great software starts with great requirements! 🚀# engse206-lab