# 1. MeetingRoom Project Guide Document

### Simplified (สำหรับนักศึกษา)

    ใช้ "All-in-one document" 
    เรียกว่า "Project Guide" แทน SRS
    อธิบายว่าเป็นการผสม SRS + Design + Implementation

### เหตุผลที่ใส่ Technical Details ในเอกสาร:
**🎓 Context การศึกษา**

    นักศึกษาปี 2 ยังไม่คุ้นเคยกับการแยก documents
    ต้องการ "One-stop document" ที่มีทุกอย่าง
    ลดความสับสนจากการมีหลายเอกสาร

**⏰ ข้อจำกัดเวลา 1 เดือน**

    ไม่มีเวลาทำหลายเอกสาร
    ต้องการให้เริ่ม coding ได้เร็ว
    ลด overhead ของ documentation

**🔧 Practical Approach**

    นักศึกษาต้องการตัวอย่างที่ชัดเจน
    ช่วยให้เห็นภาพรวมตั้งแต่ requirement ถึง implementation
    เรียนรู้ได้เร็วขึ้นเมื่อเห็น end-to-end

---

# 2. MeetingRoom Lite IEEE 830 Standard Document

### Standard (ฝึกทำตามมาตรฐาน)

    แยกเป็น 2-3 เอกสาร
    Phase 1: ทำ SRS (requirements only)
    Phase 2: ทำ Design Document
    Phase 3: Implementation

### SRS - MeetingRoom System (Standard Version) ตามมาตรฐาน IEEE 830

```
SRS (ควรมี)
├── Requirements (WHAT)
│   ├── Functional Requirements
│   ├── Non-functional Requirements
│   ├── Use Cases
│   └── User Stories
│
└── ไม่ควรมี (HOW)
    ├── ❌ Database Design
    ├── ❌ API Design
    ├── ❌ Code Examples
    └── ❌ Technical Architecture
```

### 📚 เอกสารที่ควรแยกตามมาตรฐาน:
**1. SRS (Software Requirements Specification)**
```
✅ ควรมี:
- Business requirements
- Functional requirements  
- Non-functional requirements
- Use cases & scenarios
- Constraints & assumptions

❌ ไม่ควรมี:
- Database schema
- API endpoints
- Code samples
- UI mockups (อ้างอิงเท่านั้น)
```
**2. SDD (Software Design Document)**
```
✅ ควรมี:
- System architecture
- Database design
- API specification
- Component design
- Security design
```
**3. Technical Specification**
```
✅ ควรมี:
- Technology stack
- Development environment
- Coding standards
- Deployment architecture
```

**🔄 แยกเอกสารให้ถูกต้องตามมาตรฐาน:**
```
Project Documents/
├── 1. SRS Document
│   ├── Requirements only
│   ├── Use cases
│   └── Acceptance criteria
│
├── 2. Design Documents  
│   ├── Architecture Design
│   ├── Database Design
│   └── API Design
│
├── 3. Implementation Guide
│   ├── Setup instructions
│   ├── Code examples
│   └── Best practices
│
└── 4. Test Documents
    ├── Test plan
    ├── Test cases
    └── Test results
```

**🔄 ตัวอย่าง Functional Requirements ตามมาตรฐาน:**
```
## 3. Functional Requirements

### FR-01: User Registration
The system shall allow users to register with email and password.

**Rationale:** To control access to the system
**Priority:** High
**Dependencies:** None

**Acceptance Criteria:**
- Given a new user visits registration page
- When they enter valid email and password
- Then account is created and user can login

[ไม่มี code, ไม่มี API design, ไม่มี database schema]
```


