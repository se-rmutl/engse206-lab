# สัปดาห์ที่ 5: หลักการออกแบบและสถาปัตยกรรมภาพรวม (High-Level)
## Agent Wallboard System for SE-RMUTL Case Study

### 🎯 วัตถุประสงค์การเรียน
- แปลง SRS สู่ภาพใหญ่ของสถาปัตยกรรม (High-Level Design)
- เข้าใจหลักการพื้นฐานที่ทำให้การออกแบบมีคุณภาพ
- สามารถประยุกต์ใช้กับ Agent Wallboard System จริง
- นำไปสู่การออกแบบและพัฒนา Agent Wallboard System ได้จริง

---

## Slide 1: Course Overview Week 5
### จาก Requirements สู่ Design Document

```
Requirements Analysis → System Design → Implementation
      SRS            →      SDD      →    Code
```

**เนื้อหาสัปดาห์นี้:**
- Introduction to Software Design Document (SDD)
- หลักการออกแบบพื้นฐาน: SOLID, DRY, KISS, YAGNI
- 3-Tier Architecture และ Component-based Design
- C4 Model สำหรับ Software Modeling

**Case Study:** Agent Wallboard System - ระบบติดตามและสื่อสาร Call Center Agents แบบ Real-time

---

## Slide 2: Agent Wallboard System Overview
### โครงงานตัวอย่างที่เราจะใช้เรียน

**Agent Wallboard System** = ระบบจัดการงาน Call Center แบบ Real-time
- **Agent Status Monitoring**: ติดตามสถานะ Available, Active, Wrap, Not Ready
- **Supervisor Communication**: ส่งข้อความถึง agents แบบทันที
- **Real-time Dashboard**: แสดงสถิติและข้อมูลแบบ real-time
- **System Administration**: จัดการ configuration และ deployment

**เทคโนโลยี Stack:**
- Frontend: Electron.js (Desktop Application)
- Backend: Node.js + Express.js
- Database: MSSQL + MongoDB
- Real-time: WebSocket

---

## Slide 3: What is Software Design Document (SDD)?
### เอกสารออกแบบซอฟต์แวร์คืออะไร?

**SDD = Software Design Document**
- เป็น "พิมพ์เขียว" (Blueprint) สำหรับนักพัฒนา
- แปลงความต้องการจาก SRS เป็นแผนการพัฒนาที่ชัดเจน
- เชื่อมต่อระหว่าง "สิ่งที่ต้องการ" และ "วิธีการทำ"

**ความสำคัญ:**
- ลดความผิดพลาดในการพัฒนา
- ทีมพัฒนาเข้าใจตรงกัน
- ง่ายต่อการบำรุงรักษา
- เป็นเอกสารอ้างอิงในอนาคต

**ในบริบทของ Agent Wallboard System:**
- แปลงความต้องการ real-time monitoring เป็น technical architecture
- กำหนดวิธีการ implement WebSocket communication
- ออกแบบ database schema สำหรับ agent data

---

## Slide 4: SRS vs SDD - ความแตกต่าง
### เปรียบเทียบเอกสาร Requirements กับ Design

| Aspect | SRS (Requirements) | SDD (Design) |
|--------|-------------------|--------------|
| **Focus** | WHAT (อะไร) | HOW (อย่างไร) |
| **Audience** | Stakeholders, Users | Developers, Architects |
| **Content** | Functional Requirements | Technical Architecture |
| **Level** | Business Logic | Technical Details |

**ตัวอย่างจาก Agent Wallboard System:**

**SRS**: "Supervisor สามารถส่งข้อความไปยัง agent ที่เฉพาะเจาะจงได้"

**SDD**: 
- ใช้ WebSocket protocol สำหรับ real-time communication
- Message routing ผ่าน Node.js server
- Message format: JSON with agentId และ messageContent
- Error handling สำหรับ offline agents

---

## Slide 5: องค์ประกอบหลักของ SDD
### SDD ประกอบด้วยอะไรบ้าง?

**1. System Architecture Overview**
- High-level component diagram
- Technology stack decision

**2. Database Design**
- Schema design สำหรับ agents, status logs
- Relationship mapping

**3. API Design**
- REST endpoints specification
- WebSocket event definitions

**4. Component Design**
- Desktop application components
- Server-side modules

**5. Security & Performance**
- Authentication mechanism
- Real-time performance considerations

**Agent Wallboard System ครอบคลุมทั้ง 5 ด้านนี้อย่างครบถ้วน**

---

## Slide 6: หลักการออกแบบพื้นฐาน - SOLID Principles
### S.O.L.I.D = หลักการออกแบบที่ดี

**S - Single Responsibility Principle**
- คลาสหนึ่งควรมีหน้าที่เดียว

**O - Open/Closed Principle**  
- เปิดสำหรับการขยาย, ปิดสำหรับการแก้ไข

**L - Liskov Substitution Principle**
- Subclass ควรใช้แทน parent class ได้

**I - Interface Segregation Principle**
- แยก interface ตามความจำเป็น

**D - Dependency Inversion Principle**
- พึ่งพา abstraction ไม่ใช่ concrete class

**ทำไมสำคัญ?** หลักการเหล่านี้ช่วยให้ code มีคุณภาพ, บำรุงรักษาง่าย, และขยายได้

---

## Slide 7: SOLID in Agent Wallboard System - ตัวอย่างจริง
### ประยุกต์ใช้ SOLID ใน Agent Wallboard System

**Single Responsibility:**
```javascript
// ❌ ไม่ดี - class ทำหลายอย่าง
class AgentManager {
  updateStatus() { /* ... */ }
  sendNotification() { /* ... */ }
  logToDatabase() { /* ... */ }
  generateReport() { /* ... */ }
}

// ✅ ดี - แยกหน้าที่ชัดเจน
class AgentStatusService {
  updateStatus() { /* ... */ }
}
class NotificationService {
  sendNotification() { /* ... */ }
}
class DatabaseService {
  logToDatabase() { /* ... */ }
}
```

**Dependency Inversion:**
```javascript
// ✅ ดี - พึ่งพา interface
class SupervisorController {
  constructor(messageService) {
    this.messageService = messageService; // Interface
  }
}
```

---

## Slide 8: DRY, KISS, YAGNI Principles
### หลักการออกแบบเพิ่มเติม

**DRY - Don't Repeat Yourself**
- ไม่เขียนโค้ดซ้ำ
- สร้าง utility functions

**KISS - Keep It Simple, Stupid**
- ทำให้ง่ายที่สุด
- หลีกเลี่ยงความซับซ้อนที่ไม่จำเป็น

**YAGNI - You Aren't Gonna Need It**
- ไม่ทำฟีเจอร์ที่ยังไม่ต้องการ
- Focus ที่ requirements ปัจจุบัน

**ตัวอย่างใน Agent Wallboard System:**
- **DRY**: สร้าง WebSocket utility สำหรับ connection management
- **KISS**: UI design เรียบง่าย, ใช้งานง่าย
- **YAGNI**: ไม่ทำ advanced analytics ตั้งแต่แรก (เก็บไว้ future version)

---

## Slide 9: Software Architecture Patterns
### รูปแบบสถาปัตยกรรมพื้นฐาน

**1. Layered Architecture (N-Tier)**
- แบ่งเป็นชั้น ๆ
- แต่ละชั้นมีหน้าที่ชัดเจน

**2. Component-based Architecture**
- แบ่งเป็น components
- หลัก Separation of Concerns

**3. Model-View-Controller (MVC)**
- Model: ข้อมูล
- View: หน้าตา
- Controller: ตรรกะควบคุม

**Agent Wallboard System ใช้:** 3-Tier + Component-based + MVC Pattern

**ทำไมเลือกแบบนี้?**
- เหมาะกับ real-time system
- แยกชั้นงาน frontend, backend, database ชัดเจน
- รองรับการขยายระบบ

---

## Slide 10: 3-Tier Architecture Overview
### สถาปัตยกรรม 3 ชั้นคืออะไร?

```
┌─────────────────────────────────┐
│    Presentation Tier            │ ← User Interface
│    (Electron.js Desktop App)    │   (Agent & Supervisor)
└─────────────┬───────────────────┘
              │ HTTP/REST API + WebSocket
              ▼
┌─────────────────────────────────┐
│    Application Tier             │ ← Business Logic
│    (Node.js + Express Server)   │   (API + WebSocket Server)
└─────────────┬───────────────────┘
              │ Database Queries
              ▼
┌─────────────────────────────────┐
│    Data Tier                    │ ← Data Storage
│    (MSSQL + MongoDB)            │   (Agent Data + Real-time Data)
└─────────────────────────────────┘
```

**แต่ละชั้นทำหน้าที่อะไร?**
- **Presentation**: แสดงผล UI, รับ input จากผู้ใช้
- **Application**: ประมวลผล business logic, API handling
- **Data**: เก็บและจัดการข้อมูล

---

## Slide 11: Agent Wallboard System - 3-Tier Implementation
### การนำ 3-Tier Architecture มาใช้จริง

**Tier 1: Presentation (Electron.js)**
- **Agent Desktop App**: Status management, message receiving
- **Supervisor Dashboard**: Real-time monitoring, message sending
- **Manager Console**: Reports and statistics

**Tier 2: Application (Node.js + Express)**
- **REST APIs**: `/api/agents`, `/api/status`, `/api/messages`
- **WebSocket Server**: Real-time communication hub
- **Business Logic**: Agent management, message routing

**Tier 3: Data (MSSQL + MongoDB)**
- **MSSQL**: Agent master data, user accounts
- **MongoDB**: Real-time status logs, message history
- **Indexes**: Optimized for real-time queries

**การทำงานร่วมกัน:**
1. Agent เปลี่ยนสถานะ → Desktop app → API → Database
2. Database update → WebSocket broadcast → All connected clients

---

## Slide 12: ประโยชน์ของ 3-Tier Architecture
### ทำไมต้องแบ่งเป็น 3 ชั้น?

**1. Separation of Concerns**
- แต่ละชั้นมีหน้าที่ชัดเจน
- ไม่ปะปนกัน

**2. Scalability**
- ขยายแต่ละชั้นแยกกันได้
- เช่น เพิ่ม WebSocket server สำหรับ real-time features

**3. Maintainability**
- แก้ไขง่าย
- ผลกระทบต่อส่วนอื่นน้อย

**4. Team Development**
- ทีม frontend/backend ทำงานแยกกันได้
- API เป็นจุดเชื่อมต่อที่ชัดเจน

**5. Technology Flexibility**
- เปลี่ยน database ได้โดยไม่กระทบ UI
- อัพเกรด frontend ได้โดยไม่กระทบ backend

**ตัวอย่างใน Agent Wallboard System:**
- เปลี่ยนจาก MSSQL เป็น PostgreSQL โดยไม่ต้องแก้ UI
- เพิ่ม mobile app โดยใช้ API เดิม

---

## Slide 13: Component-based Design
### การออกแบบแบบ Component

**Component = หน่วยย่อยที่ทำงานได้อิสระ**

**ลักษณะของ Component ที่ดี:**
- **High Cohesion**: ส่วนประกอบภายในทำงานร่วมกันได้ดี
- **Loose Coupling**: การพึ่งพาส่วนอื่นน้อย
- **Reusability**: นำไปใช้ใหม่ได้
- **Encapsulation**: ซ่อนรายละเอียดภายใน

**ตัวอย่างใน Agent Wallboard System:**
```
Agent Wallboard System
├── Authentication Component
├── Agent Status Component
├── Message Communication Component
├── Dashboard Component
└── Admin Configuration Component
```

**การออกแบบ Component ที่ดี:**
- แต่ละ component มี interface ที่ชัดเจน
- สามารถทดสอบแยกได้
- เปลี่ยนแปลง implementation โดยไม่กระทบส่วนอื่น

---

## Slide 14: Agent Wallboard System Components Breakdown
### แบ่ง Components ใน Agent Wallboard System

**Frontend Components (Electron.js):**
```
Agent Desktop App
├── Login Component
├── Status Management Component
├── Notification Component
└── Profile Info Component

Supervisor Dashboard
├── Agent Monitor Component
├── Message Sender Component
├── Team Dashboard Component
└── Reports Component
```

**Backend Components (Node.js):**
```
Application Server
├── Authentication Service
├── Agent Status Service
├── Message Routing Service
├── WebSocket Manager
├── Database Service
└── Configuration Service
```

**ข้อดีของการแบ่ง Components:**
- แต่ละ component รับผิดชอบงานเฉพาะ
- ทดสอบได้แยกจากกัน
- พัฒนาแบบ parallel ได้
- นำกลับมาใช้ใหม่ได้

---

## Slide 15: Software Modeling - C4 Model Introduction
### C4 Model คืออะไร?

**C4 = Context, Containers, Components, Code**

**4 ระดับของการมอง System:**
1. **Context (C1)**: ระบบในภาพใหญ่ - ใครใช้, ติดต่อกับระบบอะไรบ้าง
2. **Container (C2)**: แอปพลิเคชันหลัก - เทคโนโลยีอะไรบ้าง
3. **Component (C3)**: ส่วนประกอบภายใน - modules หลักๆ
4. **Code (C4)**: รายละเอียดโค้ด - classes, functions

**เหมาะสำหรับ:**
- สื่อสารกับ stakeholders ในระดับที่เหมาะสม
- วางแผน architecture
- เอกสารประกอบโครงการ

**ความสำคัญในการเรียน:**
- ช่วยให้คิด architecture เป็นระบบ
- เริ่มจากภาพใหญ่แล้วค่อยลงรายละเอียด

---

## Slide 16: C1 - System Context Diagram
### Agent Wallboard System ในบริบทใหญ่

```
                    ┌─────────────┐
                    │  Call Center│
                    │   Agents    │
                    └──────┬──────┘
                           │ ใช้งานผ่าน Desktop App
                           ▼
┌─────────────────────────────────────────────────┐
│           Agent Wallboard System                │
│                                                 │
│  • Real-time Agent Status Monitoring           │
│  • Supervisor-Agent Communication              │ 
│  • Management Dashboard & Reporting            │
│  • System Administration                       │
└─────────────────┬───────────────────────────────┘
                  │
        ┌─────────┴──────────┐
        │                    │
┌───────▼──────┐    ┌────────▼─────┐
│ Supervisors  │    │   Operations │
│   & Team     │    │   Managers   │
│   Leaders    │    │              │
└──────────────┘    └──────────────┘
```

**Key Points:**
- แสดงผู้ใช้งานหลัก: Agents, Supervisors, Managers
- ระบุขอบเขตหลักของระบบ
- ไม่เจาะลึกเทคโนโลยี
- เข้าใจง่ายสำหรับทุกคน รวมทั้ง non-technical stakeholders

---

## Slide 17: C2 - Container Diagram  
### แสดงแอปพลิเคชันหลักใน Agent Wallboard System

```
                    ┌─────────────┐
                    │   Users     │
                    │ (Agents &   │
                    │ Supervisors)│
                    └──────┬──────┘
                           │ HTTPS + WebSocket
                           ▼
    ┌─────────────────────────────────────────┐
    │        Desktop Application              │
    │         (Electron.js)                   │
    │                                         │
    │  • Agent status management              │
    │  • Real-time notifications              │
    │  • Supervisor dashboard                 │
    └─────────────────┬───────────────────────┘
                      │ REST API + WebSocket
                      │ JSON/HTTPS
                      ▼
    ┌─────────────────────────────────────────┐
    │         API Application                 │
    │       (Node.js + Express.js)            │
    │                                         │
    │  • Authentication & Authorization       │
    │  • Business Logic Processing            │
    │  • WebSocket Connection Management      │
    │  • API Endpoints                        │
    └─────────────────┬───────────────────────┘
                      │ Database Queries
                      │ TCP/IP + Connection Pool
                      ▼
    ┌─────────────────────────────────────────┐
    │           Database Layer                │
    │      (MSSQL + MongoDB)                  │
    │                                         │
    │  • Agent master data (MSSQL)            │
    │  • Real-time status logs (MongoDB)      │
    │  • Message history & configurations     │
    └─────────────────────────────────────────┘
```

**แต่ละ Container รับผิดชอบ:**
- **Desktop App**: UI และ user interactions
- **API Application**: Business logic และ data processing
- **Database Layer**: Data persistence และ management

---

## Slide 18: ประโยชน์ของ C4 Model
### ทำไมต้องใช้ C4 Model?

**1. Progressive Detail**
- เริ่มจากภาพใหญ่ → รายละเอียด
- เหมาะกับผู้ฟังแต่ละกลุ่ม

**2. Clear Communication**
- ใช้สัญลักษณ์มาตรฐาน
- เข้าใจง่าย

**3. Architecture Documentation**
- เอกสารประกอบการพัฒนา
- Reference สำหรับทีม

**4. Design Validation**
- ตรวจสอบ architecture design
- หาจุดที่อาจมีปัญหา

**ประโยชน์สำหรับ Agent Wallboard System:**
- **C1**: อธิบายให้ management เข้าใจ business value
- **C2**: วางแผน technology stack และ deployment
- **C3**: แผนการพัฒนา modules (ยังไม่ได้ทำใน workshop นี้)
- **C4**: Code structure guidelines (ยังไม่ได้ทำใน workshop นี้)

---

## Slide 19: เครื่องมือสำหรับวาด C4 Diagrams
### Tools สำหรับสร้างแผนภาพสถาปัตยกรรม

**1. Structurizr (Official C4 Tool)**
- DSL (Domain Specific Language)
- Auto-layout
- Version control friendly

**2. Lucidchart**
- Web-based
- Collaborative
- Template สำเร็จรูป

**3. Draw.io (diagrams.net)**
- ฟรี
- ใช้งานง่าย
- Export หลายรูปแบบ

**4. PlantUML**
- Text-based diagramming
- Integration กับ IDEs
- Version control friendly

**แนะนำสำหรับ workshop นี้:**
- **Draw.io**: ฟรี, ใช้งานง่าย, เหมาะกับผู้เริ่มต้น
- **Lucidchart**: Professional features, collaboration ดี

---

## Slide 20: Workshop Activity - วาด C1 Diagram
### กิจกรรมปฏิบัติ: System Context

**ให้นักศึกษาวาด C1 Diagram สำหรับโปรเจกต์ของตนเอง**

**ขั้นตอน:**
1. ระบุ System ของคุณ (ใส่ไว้กลาง diagram)
2. ระบุ Users/Actors ที่เกี่ยวข้อง
3. ระบุ External Systems (ถ้ามี)
4. แสดงความสัมพันธ์และการไหลของข้อมูล

**Agent Wallboard System Example:**
- **System**: Agent Wallboard System (ตรงกลาง)
- **Users**: Call Center Agents, Supervisors, Operations Managers
- **External Systems**: ไม่มี (standalone system)
- **Relationships**: การใช้งานผ่าน desktop application

**เครื่องมือแนะนำ:**
- Draw.io: https://draw.io
- Lucidchart: https://lucidchart.com

**เวลา:** 15 นาที

---

## Slide 21: Workshop Activity - วาด C2 Diagram
### กิจกรรมปฏิบัติ: Container Diagram

**ให้นักศึกษาวาด C2 Diagram**

**ขั้นตอน:**
1. แบ่ง System เป็น Container หลัก
   - Frontend application
   - Backend application  
   - Database
2. ระบุ Technology stack สำหรับแต่ละ container
3. แสดงการสื่อสาร/protocol ระหว่าง containers

**Agent Wallboard System Example:**
- **Desktop App (Electron.js)**: UI layer
- **API Server (Node.js + Express)**: Business logic
- **Database (MSSQL + MongoDB)**: Data storage
- **Protocols**: HTTPS, WebSocket, Database connections

**สิ่งที่ต้องระบุ:**
- ชื่อและเทคโนโลยีของแต่ละ container
- ทิศทางการไหลของข้อมูล
- Protocol ที่ใช้ในการสื่อสาร

**เวลา:** 20 นาที

---

## Slide 22: Common Architecture Mistakes
### ข้อผิดพลาดทั่วไปในการออกแบบ

**1. Tight Coupling**
```javascript
// ❌ ไม่ดี - coupling สูง
class AgentService {
  updateStatus(agent) {
    // เขียน SQL โดยตรง
    db.query('UPDATE agents SET status = ? WHERE id = ?', 
             [agent.status, agent.id]);
  }
}

// ✅ ดี - loose coupling
class AgentService {
  constructor(agentRepository) {
    this.agentRepository = agentRepository;
  }
  
  updateStatus(agent) {
    return this.agentRepository.updateStatus(agent);
  }
}
```

**2. God Object/Component**
- Component ที่ทำหน้าที่มากเกินไป
- ยากต่อการ maintain และ test

**3. No Clear Layering**
- Business logic ปะปนกับ UI
- Database access ใน presentation layer

**4. Ignoring Non-functional Requirements**
- ไม่คิดถึง performance, security
- ออกแบบเฉพาะ functional requirements

**5. Over-engineering**
- ออกแบบซับซ้อนเกินความจำเป็น
- ใช้ pattern มากเกินไป

---

## Slide 23: Architecture Quality Attributes
### คุณลักษณะของ Architecture ที่ดี

**1. Performance**
- Response time < 500ms สำหรับ API calls
- Real-time updates < 1 second

**2. Scalability**  
- รองรับ 100+ concurrent agents
- สามารถขยายได้เมื่อมีผู้ใช้เพิ่ม

**3. Maintainability**
- แก้ไขง่าย
- เพิ่มฟีเจอร์ใหม่ได้

**4. Security**
- Authentication และ authorization
- ข้อมูลปลอดภัย

**5. Usability**
- ใช้งานง่าย
- User experience ดี

**6. Reliability**
- System uptime ≥ 99%
- Graceful error handling

**การ Trade-off:**
- บางครั้งต้องเลือกระหว่าง performance กับ maintainability
- Security กับ usability
- ต้องสมดุลตาม business priorities

---

## Slide 24: Agent Wallboard System Architecture Decisions
### การตัดสินใจ Architecture ใน Agent Wallboard System

**1. Frontend: Electron.js**
- **เหตุผล**: Cross-platform desktop app, ใช้ web technologies
- **ทางเลือก**: Native Windows app, Web application

**2. Backend: Node.js + Express**
- **เหตุผล**: JavaScript ecosystem, excellent WebSocket support
- **ทางเลือก**: Python Flask, Java Spring Boot

**3. Database: MSSQL + MongoDB**
- **เหตุผล**: MSSQL สำหรับ transactional data, MongoDB สำหรับ real-time logs
- **ทางเลือก**: PostgreSQL only, MySQL + Redis

**4. Real-time: WebSocket**
- **เหตุผล**: Bidirectional communication, low latency
- **ทางเลือก**: Server-Sent Events, Polling

**5. Architecture Pattern: 3-Tier**
- **เหตุผล**: Clear separation, scalable, maintainable
- **ทางเลือก**: Microservices, Monolithic

**Decision Criteria:**
- Project timeline และ team expertise
- Performance requirements
- Scalability needs
- Maintenance considerations

---

## Slide 25: Agent Wallboard System Database Schema Preview
### ภาพรวม Database Design

**MSSQL - Master Data:**
```sql
-- Agent master data
CREATE TABLE OnlineAgents (
    AgentCode NVARCHAR(50) PRIMARY KEY,
    AgentName NVARCHAR(100),
    LoginTime DATETIME,
    Status NVARCHAR(20),
    LastUpdateTime DATETIME
);
```

**MongoDB - Real-time Data:**
```json
// Status logs collection
{
  "_id": ObjectId,
  "agentCode": "A001",
  "status": "Available",
  "timestamp": ISODate,
  "sessionId": "abc123"
}

// Message history collection
{
  "_id": ObjectId,
  "from": "supervisor1",
  "to": "A001",
  "message": "Please check queue",
  "timestamp": ISODate,
  "delivered": true
}
```

**Design Rationale:**
- MSSQL: Structured data, referential integrity
- MongoDB: Fast reads/writes for real-time data, flexible schema

---

## Slide 26: Agent Wallboard System API Design Preview
### ตัวอย่าง API Endpoints

**Agent Management APIs:**
```
GET    /api/agents                    // ดูรายการ agents ทั้งหมด
POST   /api/agents/:code/status      // อัปเดตสถานะ agent
GET    /api/agents/:code             // ดูข้อมูล agent เฉพาะ
POST   /api/agents/:code/login       // Agent login
POST   /api/agents/:code/logout      // Agent logout
```

**Communication APIs:**
```
POST   /api/messages                 // ส่งข้อความ
GET    /api/messages/:agentCode      // ดูประวัติข้อความ
```

**Dashboard APIs:**
```
GET    /api/dashboard/stats          // สถิติ real-time
GET    /api/dashboard/agents         // สถานะ agents ทั้งหมด
```

**WebSocket Events:**
```javascript
// Agent status change
{
  "event": "statusUpdate",
  "data": {
    "agentCode": "A001",
    "status": "Available",
    "timestamp": "2025-01-01T10:00:00Z"
  }
}

// Message notification
{
  "event": "newMessage",
  "data": {
    "to": "A001",
    "from": "supervisor1",
    "message": "Please check priority queue",
    "timestamp": "2025-01-01T10:00:00Z"
  }
}
```

---

## Slide 27: From Design to Implementation
### จาก Design สู่การเขียนโค้ด

**Design Document → Code Structure**

```
SDD Components           Code Structure
├── Frontend Components  ├── src/components/
│   ├── Login            │   ├── LoginForm.js
│   ├── StatusManager    │   ├── StatusManager.js
│   └── Dashboard        │   └── Dashboard.js
├── Backend Services     ├── server/
│   ├── AuthService      │   ├── services/auth.js
│   ├── AgentService     │   ├── services/agent.js
│   └── MessageService   │   └── services/message.js
├── API Endpoints        ├── routes/
│   └── REST APIs        │   ├── agents.js
│                        │   └── messages.js
└── Database Schema      └── database/
    ├── MSSQL Tables     │   ├── schema.sql
    └── MongoDB Collections  └── collections.js
```

**ขั้นตอนต่อไป:**
1. สร้าง Database Schema
2. พัฒนา Backend APIs  
3. สร้าง Frontend Components
4. Integration Testing
5. Deployment

---

## Slide 28: Architecture Evolution & Scalability
### การพัฒนา Architecture ต่อไป

**Phase 1: MVP (ปัจจุบัน)**
- 3-Tier Architecture
- Basic CRUD operations
- Single server deployment
- Support 50-100 concurrent agents

**Phase 2: Enhanced Features**  
- Advanced dashboard analytics
- Mobile application support
- Integration APIs
- Performance optimization

**Phase 3: Scalability**
- Microservices architecture
- Load balancing
- Redis caching layer
- Support 500+ agents

**Phase 4: Advanced Features**
- Machine learning analytics
- Predictive insights
- Advanced reporting
- Cloud-native deployment

**Scalability Considerations:**
- Database sharding strategies
- WebSocket connection pooling
- CDN for static assets
- Monitoring and alerting systems

---

## Slide 29: Best Practices Summary
### สรุปแนวทางปฏิบัติที่ดี

**1. Design Principles**
- ปฏิบัติตาม SOLID principles
- Keep it simple (KISS)
- Don't repeat yourself (DRY)
- You aren't gonna need it (YAGNI)

**2. Architecture Patterns**
- เลือกรูปแบบที่เหมาะสม
- 3-Tier สำหรับระบบขนาดกลาง
- Component-based design

**3. Documentation**
- ใช้ C4 Model สำหรับ architecture documentation
- เอกสาร SDD ที่ครบถ้วน
- Update เมื่อมีการเปลี่ยนแปลง

**4. Quality Focus**
- Performance, Security, Scalability
- Maintainable code structure
- Comprehensive testing strategy

**5. Real-time Systems Specific**
- WebSocket connection management
- Data consistency strategies
- Error handling and reconnection
- Performance monitoring

---

## Slide 30: Workshop Evaluation Criteria
### เกณฑ์การประเมิน Workshop

**Architecture Design Diagram (100%)**

**C1 - System Context (40%)**
- ความชัดเจนของ system boundary
- ระบุ actors และ external systems ครบ
- แสดงความสัมพันธ์ถูกต้อง
- เหมาะสมกับโปรเจกต์ที่เลือก

**C2 - Container Diagram (40%)**  
- แบ่ง containers ตรงตาม technology stack
- แสดง protocols การสื่อสาร
- ความเหมาะสมของ architecture choice
- รายละเอียดเทคนิคที่ถูกต้อง

**Documentation Quality (20%)**
- คำอธิบายประกอบแผนภาพ
- ความเป็นมืออาชีพ
- ความครบถ้วนของข้อมูล
- การใช้ terminology ที่ถูกต้อง

**Bonus Points:**
- ความคิดสร้างสรรค์ในการออกแบบ
- การพิจารณา non-functional requirements
- การอธิบาย trade-offs ของการตัดสินใจ

---

## Slide 31: Next Week Preview
### สัปดาห์หน้า: การออกแบบข้อมูลและฐานข้อมูล

**เนื้อหาที่จะเรียน:**
- Database Design Principles
- Entity-Relationship (ER) Diagram  
- SQL vs NoSQL selection criteria
- Agent Wallboard System Database Implementation
- Data modeling best practices

**เตรียมตัว:**
- ทบทวน Database concepts
- ติดตั้ง MongoDB Compass และ SQL Server Management Studio
- ศึกษา ER Diagram basics

**Assignment:**
- Complete Architecture Design (C1 + C2 Diagrams)
- Submit พร้อมคำอธิบาย architecture decisions
- Due: ก่อนเรียนสัปดาห์หน้า

**สิ่งที่จะได้เรียนต่อ:**
- จากภาพใหญ่ของ architecture สู่รายละเอียด database design
- การออกแบบ schema ที่รองรับ real-time operations
- การเลือกใช้ database technology ที่เหมาะสม

---

## Slide 32: Q&A Session
### ถาม-ตอบ

**คำถามที่เจอบ่อย:**

**Q: ทำไมต้องใช้ 3-Tier แทน Monolithic?**
A: แยกหน้าที่ชัดเจน, scale ได้ดีกว่า, team ทำงานแยกกันได้, maintainability ดีกว่า

**Q: C4 Model จำเป็นทุกโปรเจกต์ไหม?**
A: ขึ้นกับขนาด - โปรเจกต์ใหญ่ควรใช้, เล็กอาจใช้แค่ C1-C2, ช่วยในการสื่อสารและวางแผน

**Q: Agent Wallboard System ทำไมต้องใช้ทั้ง MSSQL และ MongoDB?**  
A: MSSQL = structured master data, referential integrity
   MongoDB = fast read/write for real-time logs, flexible schema

**Q: WebSocket vs REST API ใช้เมื่อไร?**
A: WebSocket = real-time, bidirectional (status updates, messages)
   REST API = standard CRUD operations, stateless requests

**Q: หลักการ SOLID ใช้ได้จริงใน JavaScript ไหม?**
A: ได้ แต่ต้องปรับเป็น functional programming และ module patterns

**มีคำถามเพิ่มเติมไหม?**

---

## Slide 33: Homework Assignment
### งานที่มอบหมาย

**การบ้าน: สร้าง Architecture Design สำหรับโปรเจกต์ของคุณ**

**สิ่งที่ต้องส่ง:**
1. **C1 System Context Diagram**
   - แสดงโปรเจกต์ในบริบทใหญ่
   - ระบุ users และ external systems
   - เขียนคำอธิบาย 1-2 ย่อหน้า

2. **C2 Container Diagram**  
   - แบ่ง applications/containers หลัก
   - ระบุ technology stack
   - แสดง communication protocols
   - เขียนคำอธิบาย architecture decisions

3. **Architecture Decision Record**
   - เหตุผลการเลือก technology stack
   - Trade-offs ที่พิจารณา
   - Alternative solutions ที่ไม่เลือก

**Format:** PDF หรือ image files พร้อมคำอธิบาย
**Due Date:** ส่งก่อนเรียนสัปดาห์หน้า
**Submission:** Upload ผ่าน LMS

**เกณฑ์การให้คะแนน:**
- Technical accuracy (40%)
- Clarity of diagrams (30%)
- Quality of explanations (20%)
- Creativity and innovation (10%)

---

## Slide 34: Additional Resources
### แหล่งเรียนรู้เพิ่มเติม

**Books:**
- "Software Architecture in Practice" - Bass, Clements, Kazman
- "Clean Architecture" - Robert C. Martin
- "Designing Data-Intensive Applications" - Martin Kleppmann

**Online Resources:**
- C4 Model Official Website: https://c4model.com/
- Microsoft Architecture Center
- AWS Well-Architected Framework
- Google Cloud Architecture Center

**Tools & Tutorials:**
- Draw.io templates for C4 Model
- Structurizr documentation
- Lucidchart architecture templates

**For Agent Wallboard System specifically:**
- WebSocket.io documentation
- Electron.js best practices
- Node.js + Express.js patterns
- MongoDB schema design guidelines

**Next Learning Path:**
สัปดาห์หน้า → Database Design → API Design → UI/UX Design → Testing Strategy

---

## Slide 35: สรุปสัปดาห์ที่ 5
### สิ่งที่เราได้เรียนรู้

**Key Takeaways:**

1. **Software Design Document (SDD)**
   - แปลง SRS เป็น technical blueprint
   - เชื่อมต่อ requirements กับ implementation

2. **Design Principles**
   - SOLID, DRY, KISS, YAGNI
   - ประยุกต์ใช้ใน Agent Wallboard System

3. **3-Tier Architecture**
   - Presentation, Application, Data layers
   - ข้อดีในการ scalability และ maintainability

4. **C4 Model**
   - Context → Containers → Components → Code
   - Progressive detail สำหรับ different audiences

5. **Real-world Application**
   - Agent Wallboard System เป็น case study
   - เห็นการใช้งานจริงของ principles และ patterns

**Ready for Next Week:**
- Database Design และ ER Diagrams
- นำ Architecture Design ไปสู่ detailed implementation
- เริ่มต้นการเขียนโค้ดจริง

**Remember:** Good architecture is the foundation of successful software projects!