# แผนการสอน 17 สัปดาห์ - การกำหนดความต้องการและการออกแบบทางซอฟต์แวร์
## หลักสูตร ENGSE206 - มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา (ดอยสะเก็ด)

**Case Study:** Agent Wallboard System - ระบบ Real-time Agent Status Monitoring และ Communication สำหรับ Call Center

---

# **ส่วนที่ 1: การกำหนดความต้องการซอฟต์แวร์ (Requirements Engineering) - 4 สัปดาห์**
**เป้าหมาย:** สร้างเอกสาร Software Requirements Specification (SRS) ที่สมบูรณ์สำหรับ Agent Wallboard System

---

## **สัปดาห์ที่ 1: บทนำและการเก็บรวบรวมความต้องการ**

### 🎯 วัตถุประสงค์
- เข้าใจความสำคัญของ Requirements Engineering และ SDLC
- สามารถเลือกใช้เทคนิคการเก็บรวบรวมความต้องการตามบริบท
- ประยุกต์ใช้ Agile Requirements เบื้องต้น

### 📚 เนื้อหาหลัก

#### 1. ความสำคัญของ Requirements Engineering
- สถิติความล้มเหลวของโครงการจาก Poor Requirements
- บทบาทของ Business Analyst และ Requirements Engineer
- ความเชื่อมโยงระหว่าง Requirements กับ SDLC phases

#### 2. ประเภทของความต้องการ
- **Functional Requirements**: สิ่งที่ระบบต้องทำ
- **Non-functional Requirements**: คุณภาพของระบบ
- **Domain Requirements**: ข้อกำหนดเฉพาะธุรกิจ

#### 3. เทคนิคการเก็บรวบรวมความต้องการ
- **Interviews**: การสัมภาษณ์ stakeholders
- **Surveys**: แบบสอบถามสำหรับกลุ่มใหญ่
- **Observation**: สังเกตการทำงานจริง
- **Document Analysis**: วิเคราะห์เอกสารที่มีอยู่

#### 4. Agile Requirements
- **User Stories**: As a [role], I want [feature], So that [benefit]
- **Epic**: กลุ่มของ User Stories ที่เกี่ยวข้องกัน
- **Story Mapping**: จัดลำดับ User Stories ตาม User Journey

### 👨‍💻 กิจกรรม Workshop
**ปฏิบัติการ:** Agent Wallboard System Requirements Gathering
- จำลองการสัมภาษณ์ Call Center Manager
- สร้าง User Story Map สำหรับ Agent และ Supervisor workflows
- ระบุ Stakeholders และสร้าง Stakeholder Matrix

### 🛠️ เครื่องมือที่ใช้
- Miro/StoriesOnBoard (Story Mapping)
- Google Forms (Surveys)
- JIRA/Azure DevOps (Requirements Management)

### 📊 การประเมินผล (15%)
**Assignment 1:** Agent Wallboard System - Initial Requirements Collection
- User Story Map (10 User Stories)
- Stakeholder Analysis Report
- Requirements Gathering Plan

---

## **สัปดาห์ที่ 2: การวิเคราะห์และการจัดลำดับความสำคัญ**

### 🎯 วัตถุประสงค์
- สามารถวิเคราะห์ความต้องการที่รวบรวมมาได้อย่างเป็นระบบ
- จัดลำดับความสำคัญด้วยเทคนิคที่หลากหลาย
- จัดการความขัดแย้งของ Requirements

### 📚 เนื้อหาหลัก

#### 1. เทคนิคการวิเคราะห์ความต้องการ
- **Root Cause Analysis**: หาต้นเหตุของปัญหา
- **5 Whys Technique**: ขุดลึกหาสาเหตุ
- **Gap Analysis**: เปรียบเทียบ Current State vs Future State

#### 2. การจัดลำดับความสำคัญ
- **MoSCoW Method**: Must have, Should have, Could have, Won't have
- **Kano Model**: Basic, Performance, Excitement features
- **Value vs Effort Matrix**: คุณค่าเปรียบเทียบกับความพยายาม
- **RICE Framework**: Reach, Impact, Confidence, Effort

#### 3. การวิเคราะห์ผู้มีส่วนได้ส่วนเสีย (Stakeholder Analysis)
- **Stakeholder Matrix**: Interest vs Influence
- **Power-Interest Grid**: จัดกลุ่ม stakeholders
- **Communication Strategy**: วางแผนการสื่อสาร

#### 4. การจัดการความขัดแย้ง
- **Conflict Identification**: ระบุจุดขัดแย้ง
- **Negotiation Techniques**: เทคนิคการเจรจาต่อรอง
- **Trade-off Analysis**: การวิเคราะห์ข้อแลกเปลี่ยน

### 👨‍💻 กิจกรรม Workshop
**ปฏิบัติการ:** Agent Wallboard System - Requirements Analysis
- วิเคราะห์ User Stories จากสัปดาห์ที่ 1
- ทำ MoSCoW Prioritization สำหรับ Agent Wallboard features
- สร้าง Value vs Effort Matrix
- จำลองสถานการณ์ Conflict Resolution

### 🛠️ เครื่องมือที่ใช้
- Excel/Google Sheets (Prioritization Matrix)
- Aha!/ProductPlan (Prioritization Tools)
- Stakeholder Analysis Canvas

### 📊 การประเมินผล (20%)
**Assignment 2:** Agent Wallboard System - Requirements Analysis Report
- Prioritized Requirements List (MoSCoW + Value/Effort)
- Stakeholder Analysis Matrix
- Conflict Resolution Strategy

---

## **สัปดาห์ที่ 3: การเขียนเอกสารความต้องการ (SRS) และ UML Modeling**

### 🎯 วัตถุประสงค์
- เขียนเอกสาร SRS ตามมาตรฐาน IEEE 830
- สร้างแบบจำลอง UML เพื่อออกแบบและสื่อสาร
- กำหนด Acceptance Criteria ที่ชัดเจน

### 📚 เนื้อหาหลัก

#### 1. Software Requirements Specification (SRS)
- **IEEE 830 Structure**: มาตรฐานการเขียน SRS
- **SMART Criteria**: Specific, Measurable, Achievable, Relevant, Time-bound
- **Writing Best Practices**: ภาษาที่ชัดเจน, หลีกเลี่ยงคำคลุมเครือ

#### 2. UML Modeling สำหรับ Requirements
- **Use Case Diagram**: แสดงปฏิสัมพันธ์ระหว่าง Actor และ System
  - Use Case Relationships: Include, Extend, Generalization
  - Actor Identification และ Use Case Definition
- **Activity Diagram**: แสดง Workflow และ Business Process
  - Decision Points, Parallel Activities, Swimlanes

#### 3. User Stories และ Acceptance Criteria
- **User Story Format**: As a [role], I want [feature], So that [benefit]
- **Given-When-Then Format**: Behavior-Driven Development
- **Definition of Done**: เกณฑ์การยอมรับงานเสร็จ

#### 4. Requirements Quality Assurance
- **Verification Techniques**: Reviews, Inspections, Walkthroughs
- **Validation Techniques**: Prototyping, User Testing

### 👨‍💻 กิจกรรม Workshop
**ปฏิบัติการ:** Agent Wallboard System - SRS และ Use Case Development
- เขียน SRS บางส่วนตาม IEEE 830 structure
- สร้าง Use Case Diagram สำหรับ Agent Wallboard System (8+ Use Cases)
- เขียน Detailed Use Case Specifications
- กำหนด Acceptance Criteria สำหรับ Priority User Stories

### 🛠️ เครื่องมือที่ใช้
- Lucidchart/Draw.io (UML Diagrams)
- Confluence/Notion (Documentation)
- PlantUML (Text-based UML)

### 📊 การประเมินผล (25%)
**Assignment 3:** Agent Wallboard System - SRS Document (Draft)
- Complete SRS sections 1-2 (IEEE 830)
- Use Case Diagram (8+ Use Cases)
- Detailed Use Case Specifications (3 Use Cases)
- Traceability Matrix (Requirements ↔ Use Cases)

---

## **สัปดาห์ที่ 4: การบริหารจัดการและการต่อรองความต้องการ**

### 🎯 วัตถุประสงค์
- เข้าใจกระบวนการ Change Management สำหรับ Requirements
- สามารถสร้าง Prototype เพื่อ Validate Requirements
- จัดการ Requirements Traceability และ Impact Analysis

### 📚 เนื้อหาหลัก

#### 1. Requirements Change Management
- **Change Control Process**: การควบคุมการเปลี่ยนแปลง
  - Change Request → Impact Analysis → Approval → Implementation
- **Version Control**: การจัดการเวอร์ชันของเอกสาร
- **Baseline Management**: การกำหนด Requirements Baseline

#### 2. Requirements Traceability
- **Traceability Matrix**: เชื่อมโยง Requirements กับ Design/Test/Code
- **Forward Traceability**: Requirements → Design → Code → Test
- **Backward Traceability**: Test/Code → Design → Requirements
- **Impact Analysis**: วิเคราะห์ผลกระทบของการเปลี่ยนแปลง

#### 3. Requirements Validation
- **Prototyping**: สร้างต้นแบบเพื่อทดสอบ Requirements
  - Paper Prototypes, Digital Mockups, Interactive Prototypes
- **User Acceptance Testing (UAT)**: การทดสอบโดยผู้ใช้จริง
- **Requirements Reviews**: การตรวจสอบโดย Stakeholders

#### 4. Negotiation และ Communication
- **Win-Win Negotiation**: การเจรจาที่ทุกฝ่ายได้ประโยชน์
- **Communication Plans**: วางแผนการสื่อสาร
- **Stakeholder Buy-in**: การทำให้ Stakeholders เห็นด้วย

### 👨‍💻 กิจกรรม Workshop
**ปฏิบัติการ:** Agent Wallboard System - Change Management และ Prototyping
- จำลอง Change Request Scenario
- สร้าง Requirements Traceability Matrix
- Rapid Prototyping สำหรับ Agent Desktop Interface
- การทำ Requirements Review Session

### 🛠️ เครื่องมือที่ใช้
- Figma/Adobe XD (Prototyping)
- Balsamiq (Wireframing)
- IBM DOORS/Jama Connect (Requirements Management)
- Git (Version Control)

### 📊 การประเมินผล (20%)
**Assignment 4:** Agent Wallboard System - Final Requirements Package
- Complete SRS Document (IEEE 830)
- Requirements Traceability Matrix
- Change Management Plan
- Low-fidelity Prototype

---

# **ส่วนที่ 2: การออกแบบซอฟต์แวร์ (Software Design) - 12 สัปดาห์**
**เป้าหมาย:** สร้างเอกสาร Software Design Document (SDD) ที่สมบูรณ์สำหรับ Agent Wallboard System

---

## **สัปดาห์ที่ 5: หลักการออกแบบและสถาปัตยกรรมภาพรวม (High-Level)**

### 🎯 วัตถุประสงค์
- แปลง SRS สู่ Software Design Document (SDD) ที่มีคุณภาพ
- ประยุกต์ใช้หลักการออกแบบพื้นฐานใน Real-time System  
- สร้าง C1 (System Context) และ C2 (Container) Diagram

### 📚 เนื้อหาหลัก

#### 1. Introduction to Software Design Document (SDD)
- การเชื่อมต่อ SRS → SDD → Implementation
- องค์ประกอบหลัก: Architecture, Database, API, UI/UX, Security, Performance

#### 2. Design Principles for Real-time Systems
- **SOLID Principles** สำหรับ JavaScript/Node.js
  - Single Responsibility, Open/Closed, Liskov Substitution
  - Interface Segregation, Dependency Inversion
- **DRY, KISS, YAGNI** ในบริบท Agent Wallboard System
- **Separation of Concerns** สำหรับ WebSocket และ REST API

#### 3. 3-Tier Architecture for Agent Wallboard
- **Presentation**: Electron.js Desktop + Web Dashboard
- **Application**: Node.js API + WebSocket Manager  
- **Data**: MSSQL (Master Data) + MongoDB (Real-time Logs)

#### 4. C4 Model - Level 1 & 2
- **C1 (System Context)**: Agent Wallboard ในภาพใหญ่ Call Center Operation
- **C2 (Container)**: Technology Stack และ Communication Protocols

### 🛠️ Workshop
สร้าง C1 และ C2 Diagram สำหรับ Agent Wallboard System โดยใช้ Draw.io

### 📊 การประเมินผล (15%)
Architecture Design Document (C1 + C2) พร้อมคำอธิบาย Technology Decisions

---

## **สัปดาห์ที่ 6: Design Patterns และ Architectural Patterns**

### 🎯 วัตถุประสงค์
- เลือกใช้ Design Patterns ที่เหมาะกับ Real-time Communication System
- ออกแบบ Component Architecture ด้วย Patterns

### 📚 เนื้อหาหลัก

#### 1. Creational Patterns
- **Singleton**: WebSocket Connection Manager, Database Connection Pool
- **Factory**: Message Factory สำหรับ different message types

#### 2. Structural Patterns  
- **Adapter**: Database Adapter (MSSQL ↔ MongoDB)
- **Facade**: API Facade สำหรับ Complex Dashboard Operations

#### 3. Behavioral Patterns
- **Observer**: Real-time Status Broadcasting System
- **Strategy**: Authentication Strategies (Local, SSO)
- **Command**: User Action Commands (Status Change, Send Message)

#### 4. Real-time Systems Patterns
- **Publisher-Subscriber**: WebSocket Event Broadcasting
- **Circuit Breaker**: Database Connection Resilience

### 🛠️ Workshop
ออกแบบ Pattern Implementation Plan สำหรับ Agent Wallboard System

### 📊 การประเมินผล (10%)
Design Patterns Implementation Strategy

---

## **สัปดาห์ที่ 7: การออกแบบสถาปัตยกรรมซอฟต์แวร์ - พื้นฐาน**

### 🎯 วัตถุประสงค์  
- สร้าง C3 (Component) Diagram แสดง Internal Architecture
- ออกแบบ Component Interface และ Dependencies

### 📚 เนื้อหาหลัก

#### 1. C4 Model - Level 3 (Components)
**Frontend Components:**
- Authentication Component, Status Management Component
- Real-time Notification Component, Dashboard Visualization Component

**Backend Components:**
- Authentication Service, Agent Status Service, Message Routing Service
- WebSocket Connection Manager, Database Access Layer

#### 2. Component Design Principles
- **High Cohesion, Loose Coupling**
- **Interface Segregation** for Component Communication
- **Dependency Injection** patterns

#### 3. Component Communication Patterns
- **Event-Driven Architecture** for Real-time Updates
- **API Gateway Pattern** for External Communications
- **CQRS Pattern** for Read/Write Separation

### 🛠️ Workshop
สร้าง C3 Component Diagram และ Component Interface Specifications

### 📊 การประเมินผล (10%)
Complete Component Architecture Design

---

## **สัปดาห์ที่ 8: สอบกลางภาค**

### 📝 สอบกลางภาค (30% ของคะแนนรวม)
**เนื้อหาที่สอบ:**
- Requirements Engineering (สัปดาห์ 1-4)
- High-Level Software Design (สัปดาห์ 5-7)
- Agent Wallboard System Case Study Analysis

**รูปแบบการสอบ:**
- ข้อเขียน (60%): ทฤษฎี Requirements และ Design Principles
- ปฏิบัติ (40%): วาด Use Case Diagram, C1-C2 Architecture Diagram

---

## **สัปดาห์ที่ 9: การออกแบบสถาปัตยกรรมซอฟต์แวร์ - ขั้นสูง**

### 🎯 วัตถุประสงค์
- สร้าง C4 (Code) Level Design และ UML Class/Sequence Diagrams
- ออกแบบ API Specifications ที่สมบูรณ์

### 📚 เนื้อหาหลัก

#### 1. C4 Model - Level 4 (Code)
```javascript
class AgentStatusManager {
  updateStatus(agentId, status, timestamp)
  getStatusHistory(agentId, timeRange)
  broadcastStatusChange(statusData)
}

class WebSocketManager {
  handleConnection(socket)
  broadcastToClients(event, data)
  manageClientSubscriptions()
}
```

#### 2. UML Diagrams
- **Class Diagram**: Core Classes และ Relationships
- **Sequence Diagram**: Status Update Flow, Message Routing Flow
- **Activity Diagram**: Agent Login Process, Dashboard Data Loading

#### 3. API Design Specifications
**REST Endpoints:**
- `POST /api/auth/login`, `PUT /api/agents/{id}/status`  
- `GET /api/dashboard/agents`, `POST /api/messages`

**WebSocket Events:**
- `agent_status_update`, `new_message_received`, `connection_status_change`

### 🛠️ Workshop
สร้าง Complete Technical Specification (C4 + UML + API Docs)

### 📊 การประเมินผล (15%)
Low-Level Design Document (C4 + UML + API)

---

## **สัปดาห์ที่ 10: การออกแบบฐานข้อมูลและการจัดการข้อมูล**

### 🎯 วัตถุประสงค์
- ออกแบบ Database Schema ที่รองรับ Real-time Operations
- เข้าใจการเลือก SQL vs NoSQL ตาม Data Characteristics

### 📚 เนื้อหาหลัก

#### 1. Entity-Relationship Design สำหรับ Agent Wallboard
**MSSQL Entities (Master Data):**
- Agent (ID, Name, Department, Skills, CreatedDate)
- Team (ID, Name, SupervisorID, Department)  
- Configuration (Key, Value, Environment, Description)

**MongoDB Collections (Real-time Data):**
- StatusLogs (AgentID, Status, Timestamp, Duration, SessionID)
- Messages (ID, FromID, ToID, Content, Timestamp, Type, IsRead)
- ConnectionLogs (AgentID, ConnectedAt, DisconnectedAt, IPAddress)

#### 2. Database Selection Strategy
- **MSSQL**: Referential Integrity, ACID, Reporting
- **MongoDB**: High Write Volume, Flexible Schema, Fast Read

#### 3. Performance Optimization
- **Indexing Strategy** for Real-time Queries
- **Connection Pooling** for Concurrent Users
- **Data Archiving** Strategy for Status Logs

### 🛠️ Workshop
สร้าง Complete Database Design (ER + Schema + Optimization Plan)

### 📊 การประเมินผล (15%)
Database Design Document with Performance Considerations

---

## **สัปดาห์ที่ 11: การออกแบบ User Experience (UX) และ User Interface (UI)**

### 🎯 วัตถุประสงค์  
- ออกแบบ User Experience สำหรับ Real-time Monitoring System
- สร้าง UI Design ที่เหมาะกับ different user roles

### 📚 เนื้อหาหลัก

#### 1. User-Centered Design for Agent Wallboard
- **Agent Persona**: ต้องการ simple, fast, non-intrusive interface
- **Supervisor Persona**: ต้องการ comprehensive overview, quick action capabilities  
- **Manager Persona**: ต้องการ analytics, reporting, high-level insights

#### 2. UX Design for Real-time Systems
- **Information Architecture**: จัดกลุ่มข้อมูลตาม priority และ frequency of use
- **User Journey Mapping**: Agent login → Status management → Receive messages
- **Real-time Feedback Design**: Status indicators, notifications, alerts

#### 3. UI Design Principles
- **Desktop App UI**: Clean, minimal, always-visible status
- **Dashboard UI**: Data-dense, customizable, role-based access
- **Notification Design**: Non-disruptive, categorized by urgency

### 🛠️ Workshop
สร้าง User Journey Map, Wireframes และ Interactive Prototype

### 📊 การประเมินผล (10%)
UX Research Report และ UI Prototype

---

## **สัปดาห์ที่ 12: Mobile และ Responsive Design**

### 🎯 วัตถุประสงค์
- ออกแบบ Responsive Interface สำหรับ different screen sizes  
- เข้าใจ Mobile-first approach สำหรับ Supervisor Dashboard

### 📚 เนื้อหาหลัก (Overview)

#### 1. Responsive Design for Agent Wallboard
- **Desktop Priority**: Agent Desktop App (primary use case)
- **Mobile Dashboard**: Supervisor mobile access for monitoring
- **Tablet Interface**: Management reporting interface

#### 2. Touch Interface Considerations  
- **Mobile Dashboard**: Swipe gestures, touch-friendly controls
- **Notification Handling**: Mobile push notifications
- **Offline Capabilities**: Basic status viewing when disconnected

### 🛠️ Workshop (Simplified)
ปรับ Desktop UI Design ให้เป็น Responsive Design

### 📊 การประเมินผล (5%)
Responsive Design Mockups

---

## **สัปดาห์ที่ 13: การทบทวนและปรับปรุงเอกสารออกแบบ (Design Review & Refinement)**

### 🎯 วัตถุประสงค์
- Review และ Integrate ทุก Design Components เข้าด้วยกัน
- Peer Review และ Design Quality Assurance

### 📚 เนื้อหาหลัก

#### 1. Design Integration
- รวม Architecture + Database + UI + Patterns เป็น Complete SDD
- ตรวจสอบ Consistency ระหว่าง different design levels
- Validate Design กับ Original Requirements (SRS)

#### 2. Design Review Process
- **Technical Review**: Architecture scalability, performance implications
- **Usability Review**: UI/UX consistency, user flow validation  
- **Implementation Review**: Technical feasibility, development complexity

### 🛠️ Workshop
Design Review Session + SDD Integration Workshop

### 📊 การประเมินผล (5%)
Peer Review Participation + Integrated SDD

---

## **สัปดาห์ที่ 14: ข้อควรพิจารณาด้าน Security และ Performance**

### 🎯 วัตถุประสงค์
- เข้าใจ Security และ Performance implications ของ Design decisions
- สร้าง Security และ Performance Architecture (Overview)

### 📚 เนื้อหาหลัก (Overview)

#### 1. Security Design for Agent Wallboard
- **Authentication**: JWT tokens, session management
- **Authorization**: Role-based access (Agent, Supervisor, Admin)
- **Communication Security**: HTTPS, WSS (WebSocket Secure)
- **Data Protection**: Encryption at rest, PII handling

#### 2. Performance Architecture
- **Real-time Performance**: WebSocket connection optimization
- **Database Performance**: Query optimization, connection pooling
- **Scalability**: Load balancing, horizontal scaling considerations

### 🛠️ Workshop (Simplified)
Security Checklist และ Performance Planning สำหรับ Agent Wallboard System

### 📊 การประเมินผล (5%)  
Security และ Performance Considerations Document

---

## **สัปดาห์ที่ 15: ข้อควรพิจารณาด้าน DevOps และ Deployment**

### 🎯 วัตถุประสงค์
- เข้าใจ Deployment Architecture และ DevOps considerations (Overview)
- เตรียม SDD สำหรับ Hand-off ไปยัง Implementation Team

### 📚 เนื้อหาหลัก (Overview)

#### 1. Deployment Architecture for Agent Wallboard
- **Desktop App Distribution**: Electron app packaging, auto-update
- **Server Deployment**: Node.js application, database setup
- **Environment Management**: Development, Staging, Production

#### 2. DevOps Considerations
- **CI/CD Pipeline**: Automated testing, deployment pipeline
- **Monitoring**: Application logs, performance monitoring
- **Backup Strategy**: Database backup, configuration backup

### 🛠️ Workshop (Simplified)
สร้าง Deployment Plan และ Hand-off Documentation

### 📊 การประเมินผล (5%)
Deployment Architecture และ Implementation Readiness Document

---

## **สัปดาห์ที่ 16: โครงงานปฏิบัติการและการนำเสนอ**

### 🎯 วัตถุประสงค์
- นำเสนอ Complete Software Design Document
- Demonstrate การเชื่อมโยง Requirements → Design → Implementation Readiness

### 📚 เนื้อหาหลัก

#### 1. การรวม Complete SDD
- Architecture Design (C1-C4), Database Design, API Specifications
- UI/UX Design, Security และ Performance Considerations, Deployment Plan

#### 2. Professional Presentation
- Executive Summary สำหรับ Management
- Technical Deep-dive สำหรับ Development Team
- Implementation Roadmap

### 🛠️ Final Project
**Complete Agent Wallboard System Design Document** พร้อมการนำเสนอ

### 📊 การประเมินผล (15%)
- Complete SDD Quality (10%)
- Presentation และ Communication (5%)

---

## **สัปดาห์ที่ 17: สอบปลายภาค**

### 📝 สอบปลายภาค (30% ของคะแนนรวม)
**เนื้อหาที่สอบ:**
- Software Design (สัปดาห์ 5-16)
- การประยุกต์ใช้ Design Patterns และ Architecture Patterns
- UX/UI Design และ Modern Development Practices
- การแก้ปัญหาการออกแบบในสถานการณ์จริง

**รูปแบบการสอบ:**
- ข้อเขียน (50%): ทฤษฎี Design Principles, Patterns, Architecture
- ปฏิบัติ (50%): ออกแบบ System Architecture, Database Design, API Design

---

# 🎯 **การเชื่อมโยงทั้ง 17 สัปดาห์**

## Progressive Learning Journey:
### **Phase 1**: Requirements Foundation (Week 1-4)
- Stakeholder Analysis → Requirements Gathering → Analysis & Prioritization → SRS Documentation

### **Phase 2**: High-Level Design (Week 5-8)  
- Design Principles → Architecture Patterns → System Design → **Midterm Exam**

### **Phase 3**: Detailed Design (Week 9-12)
- Low-Level Design → Database Design → UI/UX Design → Mobile/Responsive

### **Phase 4**: Integration & Quality (Week 13-16)
- Design Review → Security/Performance → DevOps → **Final Project**

### **Phase 5**: Assessment (Week 17)
- **Final Exam** → Course Completion

## Agent Wallboard System - Complete Learning Journey:

### **Requirements Phase** (Week 1-4):
- ✅ Complete Stakeholder Analysis (4 user types: Agent/Supervisor/Manager/Admin)
- ✅ 14 User Stories mapped to business processes
- ✅ 13 Use Cases with detailed scenarios
- ✅ Complete SRS Document (IEEE 830 compliant)

### **Design Phase** (Week 5-16):
- ✅ Complete C4 Architecture (C1→C2→C3→C4)
- ✅ Multi-database design (MSSQL + MongoDB)
- ✅ Real-time communication architecture (WebSocket + REST)
- ✅ Role-based UI/UX for different user types
- ✅ Security & Performance considerations
- ✅ Deployment & DevOps planning

---

# 📈 **การประเมินผลรวม (100%)**

## Requirements Engineering (40%)
| สัปดาห์ | Assignment | คะแนน | Focus Area |
|---------|------------|-------|------------|
| 1 | Initial Requirements Collection | 15% | Stakeholder Analysis + User Stories |
| 2 | Requirements Analysis Report | 20% | Prioritization + Conflict Resolution |
| 3 | SRS Document (Draft) | 25% | IEEE 830 + Use Cases |
| 4 | Final Requirements Package | 20% | Complete SRS + Traceability |
| 8 | **สอบกลางภาค** | 20% | Requirements + High-level Design |

## Software Design (60%)
| สัปดาห์ | Assignment | คะแนน | Focus Area |
|---------|------------|-------|------------|
| 5 | Architecture Design (C1+C2) | 15% | System Context + Containers |
| 6 | Design Patterns Strategy | 10% | Pattern Implementation Plan |
| 7 | Component Design (C3) | 10% | Component Architecture |
| 9 | Technical Specification (C4+UML) | 15% | Low-level Design + API |
| 10 | Database Design | 15% | Multi-database Architecture |
| 11 | UX/UI Design | 10% | User Experience Design |
| 12-15 | Integration Components | 20% | Security/Performance/DevOps |
| 16 | Final Project Presentation | 15% | Complete SDD |
| 17 | **สอบปลายภาค** | 30% | Complete Software Design |

---

# 💡 **Key Success Metrics**

## นักศึกษาจะสำเร็จการเรียนด้วยความสามารถ:

### **Requirements Engineering Skills:**
1. **Requirements Gathering**: ใช้เทคนิคต่างๆ ในการเก็บรวบรวมความต้องการ
2. **Stakeholder Management**: วิเคราะห์และจัดการ stakeholders ได้อย่างมีประสิทธิภาพ
3. **Requirements Analysis**: จัดลำดับความสำคัญและแก้ไขความขัดแย้ง
4. **Documentation**: เขียนเอกสาร SRS ตามมาตรฐาน IEEE 830
5. **Change Management**: จัดการการเปลี่ยนแปลงความต้องการ

### **Software Design Skills:**
1. **Architecture Design**: สร้าง C4 Model ครบทั้ง 4 ระดับ
2. **Design Patterns**: เลือกและประยุกต์ใช้ patterns ที่เหมาะสม
3. **Database Design**: ออกแบบ multi-database architecture
4. **API Design**: สร้าง RESTful API และ WebSocket specifications
5. **UI/UX Design**: ออกแบบ user interface สำหรับหลายกลุ่มผู้ใช้
6. **System Integration**: รวม design components ทั้งหมดเป็น coherent system

### **Professional Skills:**
1. **Technical Communication**: นำเสนอ technical design ได้อย่างชัดเจน
2. **Documentation**: สร้างเอกสารตามมาตรฐานอุตสาหกรรม
3. **Problem Solving**: แก้ปัญหา design trade-offs
4. **Quality Assurance**: ตรวจสอบคุณภาพของ design
5. **Project Management**: จัดการ design project ตั้งแต่ต้นจนจบ

---

# 🎖️ **Final Deliverables**

## 1. Complete Requirements Package:
- ✅ **SRS Document** (IEEE 830 compliant) - 20-30 pages
- ✅ **Use Case Model** (13 Use Cases with detailed specifications)
- ✅ **User Story Map** (14 User Stories with acceptance criteria)
- ✅ **Requirements Traceability Matrix**
- ✅ **Change Management Plan**

## 2. Complete Software Design Document (SDD):
- ✅ **Architecture Documentation** (C1-C4 Model)
- ✅ **Database Design** (ER Diagram + Schema + Optimization)
- ✅ **API Specifications** (REST + WebSocket + OpenAPI/Swagger)
- ✅ **UI/UX Design** (Wireframes + Prototypes + User Journey)
- ✅ **Design Patterns Implementation Guide**
- ✅ **Security & Performance Architecture**
- ✅ **Deployment & DevOps Plan**
- ✅ **Implementation Roadmap**

## 3. Supporting Artifacts:
- ✅ **Prototype** (Interactive UI/UX demonstrations)
- ✅ **Presentation Materials** (Executive summary + Technical deep-dive)
- ✅ **Quality Assurance Reports** (Design reviews + Validation results)

---

# 🌟 **Industry Readiness Features**

## Real-world Application:
- **Complete Case Study**: Agent Wallboard System เป็นระบบที่ใช้งานจริงใน Call Center
- **Modern Technology Stack**: Electron.js, Node.js, MongoDB, MSSQL, WebSocket
- **Scalable Architecture**: 3-tier + microservices patterns
- **Multi-user Support**: 4 distinct user roles with different requirements

## Professional Standards:
- **IEEE 830 Compliance**: SRS ตามมาตรฐานสากล
- **C4 Model**: Architecture documentation ที่เป็นมาตรฐานอุตสาหกรรม
- **RESTful API Design**: ตาม modern API design principles
- **Agile Practices**: User Stories, Sprint planning, Iterative development

## Career Preparation:
- **Business Analyst Skills**: Requirements gathering, Stakeholder management
- **Software Architect Skills**: System design, Technology selection
- **UI/UX Designer Skills**: User research, Wireframing, Prototyping
- **Project Manager Skills**: Planning, Risk assessment, Communication

---

# 📚 **Learning Resources**

## ตำรา/เอกสารหลัก:
1. **"Software Engineering"** - Ian Sommerville (Requirements Engineering)
2. **"Clean Architecture"** - Robert C. Martin (Design Principles)
3. **"Designing Data-Intensive Applications"** - Martin Kleppmann (Database Design)
4. **"RESTful Web APIs"** - Leonard Richardson (API Design)

## เครื่องมือที่ใช้ในคอร์ส:
- **Requirements**: JIRA, Confluence, Miro, StoriesOnBoard
- **Architecture**: Draw.io, Lucidchart, Structurizr
- **Database**: MySQL Workbench, MongoDB Compass
- **API**: Postman, Swagger Editor
- **UI/UX**: Figma, Adobe XD, Balsamiq
- **Development**: Git, Visual Studio Code, Node.js

## แหล่งเรียนรู้เพิ่มเติม:
- **C4 Model**: https://c4model.com/
- **API Design**: https://swagger.io/resources/articles/
- **UX Design**: https://www.interaction-design.org/
- **Real-time Systems**: https://socket.io/docs/

---

# 🚀 **Course Innovation Highlights**

## 1. **End-to-End Learning Journey**:
จากการเก็บ Requirements → Analysis → Design → Implementation Ready ในโครงการเดียวกัน

## 2. **Industry-Relevant Case Study**:
Agent Wallboard System ครอบคลุม Real-time, Multi-user, Multi-database, และ Cross-platform requirements

## 3. **Modern Methodology Integration**:
ผสม Traditional (IEEE 830) กับ Agile (User Stories) และ Modern Architecture (C4 Model)

## 4. **Practical Skill Development**:
เน้น hands-on workshops และ real-world tools มากกว่าแค่ทฤษฎี

## 5. **Quality-Focused Approach**:
Peer reviews, Design critiques, และ Professional presentation skills

## 6. **Career-Ready Portfolio**:
นักศึกษาได้ Complete project documentation ที่นำไปใช้ในการสมัครงานได้

---

# ✅ **Ready for Implementation**

แผนการสอนนี้พร้อมใช้งานทันที โดยมี:
- **Detailed Weekly Plans** สำหรับ 17 สัปดาห์
- **Complete Assessment Framework** (100% coverage)
- **Industry-Standard Tools and Methods**
- **Real Case Study** with complete documentation
- **Progressive Learning Path** จาก Beginner → Professional
- **Quality Assurance** at every stage

คุณครูสามารถเริ่มใช้งานได้เลย และปรับแต่งรายละเอียดตามบริบทของมหาวิทยาลัยและระยะเวลาเรียนได้ครับ!