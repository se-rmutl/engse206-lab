# สัปดาห์ที่ 5: Draw.io Architecture Diagrams - Agent Wallboard System

## 🎯 วัตถุประสงค์การเรียนรู้
นักศึกษาสามารถสร้าง Architecture Diagrams ด้วย Draw.io เพื่ออธิบายสถาปัตยกรรมระดับสูง (High-Level Architecture) ของระบบ Agent Wallboard พร้อมใช้หลักการ C4 Model สำหรับระบบ Call Center Real-time Communication System

---

## 📊 Architecture Diagrams แบบต่างๆ

### 1. C1 - System Context Diagram
**จุดประสงค์:** แสดงภาพรวมของระบบ Agent Wallboard และผู้ใช้งานหลัก

```
[Draw.io Code - System Context]
รายละเอียดที่ต้องรวม:
- Agent Wallboard System (ระบบกลาง)
- Call Center Agents (ผู้ใช้หลัก - Desktop Application)
- Team Leaders/Supervisors (ผู้จัดการ - Web Dashboard)
- Operations Managers (ผู้บริหาร - Management Reports)
- System Administrator (ผู้ดูแลระบบ - Configuration)

ไม่มี External Systems เนื่องจาก Agent Wallboard เป็น Standalone System
```

**ขั้นตอนการสร้างใน Draw.io:**
1. เปิด Draw.io → เลือก Template "Business Process"
2. ลาก Shape "Actor" สำหรับผู้ใช้แต่ละประเภท:
   - Call Center Agents
   - Supervisors/Team Leaders
   - Operations Managers
   - System Administrator
3. ใช้ "System" shape (สี่เหลี่ยมใหญ่) สำหรับ Agent Wallboard System
4. เชื่อม Arrow พร้อมใส่ label อธิบายการทำงาน:
   - "Uses Desktop App for Status Management"
   - "Monitors Real-time Agent Status"
   - "Views Management Reports"
   - "Configures System Settings"
5. ใช้สีแยกประเภท: ฟ้าสำหรับ Users, เขียวสำหรับ Main System

### 2. C2 - Container Diagram
**จุดประสงค์:** แสดงส่วนประกอบหลักของระบบและเทคโนโลยีที่ใช้ตามมาตรฐาน Agent Wallboard System

```
[Draw.io Code - Container Architecture]
Frontend Containers:
- Desktop Application (Electron.js)
  * Agent Status Management Interface
  * Real-time Notification System
  * Message Communication Panel
  * Cross-platform (Windows/Mac/Linux)
  
- Web Dashboard (React.js in Browser)
  * Supervisor Monitoring Dashboard
  * Real-time Agent Status Display
  * Message Broadcasting Interface
  * Management Reports Portal

Backend Containers:
- API Server (Node.js + Express.js)
  * RESTful API Endpoints
  * Authentication & Authorization
  * Business Logic Processing
  * Request/Response Handling
  
- WebSocket Server (Socket.io + Node.js)
  * Real-time Communication Hub
  * Live Status Broadcasting
  * Message Routing Service
  * Connection Management
  
- Background Services (Node.js Workers)
  * Data Aggregation Jobs
  * Status Log Processing
  * Report Generation
  * System Maintenance Tasks

Data Containers:
- MSSQL Database
  * Agent Master Data (OnlineAgents table)
  * User Accounts & Authentication
  * System Configuration
  * Structured Transactional Data
  
- MongoDB Database
  * Real-time Status Logs
  * Message History
  * Session Data
  * Time-series Performance Data
```

**ขั้นตอนการสร้างใน Draw.io:**
1. เลือก Shape "Container" หรือ "Rectangle" สำหรับแต่ละ container
2. จัดกลุ่มตามหน้าที่: Frontend, Backend, Data
3. ใช้สีแยกประเภท: 
   - ส้มสำหรับ Frontend (Electron.js, React.js)
   - น้ำเงินสำหรับ Backend (Node.js services)
   - เขียวสำหรับ Data (MSSQL, MongoDB)
4. เชื่อม Arrow พร้อมระบุ Protocol:
   - HTTP/HTTPS REST API
   - WebSocket Protocol
   - Database Connections (TCP/IP)
5. เพิ่ม Technology label ในแต่ละ container พร้อม Port หรือ Endpoint สำคัญ

### 3. Deployment Diagram
**จุดประสงค์:** แสดงวิธีการ deploy และโครงสร้าง infrastructure สำหรับ Agent Wallboard System

```
[Draw.io Code - Deployment Architecture]
Production Environment:
┌─────────────────────────────────────────┐
│         Load Balancer (NGINX)           │
│        - SSL/TLS Termination            │
│        - Request Distribution           │
└──────────────┬─────────────┬────────────┘
               │             │
    ┌──────────▼────────┐   ┌▼────────────────┐
    │   Application     │   │   Application   │
    │   Server 1        │   │   Server 2      │
    │  - Node.js API    │   │  - Node.js API  │
    │  - WebSocket      │   │  - WebSocket    │
    │  - Electron Apps  │   │  - Electron Apps│
    └──────────┬────────┘   └┬────────────────┘
               │             │
    ┌──────────▼─────────────▼────────────────┐
    │         Database Layer                  │
    │                                         │
    │  ┌─────────────────┐ ┌─────────────────┐│
    │  │   MSSQL Server  │ │   MongoDB       ││
    │  │   (Master Data) │ │   (Real-time)   ││
    │  │   - OnlineAgents│ │   - StatusLogs  ││
    │  │   - UserAccounts│ │   - MessageHist ││
    │  └─────────────────┘ └─────────────────┘│
    │                                         │
    │  ┌─────────────────┐ ┌─────────────────┐│
    │  │   Backup        │ │   Monitoring    ││
    │  │   Services      │ │   Services      ││
    │  └─────────────────┘ └─────────────────┘│
    └─────────────────────────────────────────┘

Development Environment:
┌─────────────────────────────────────────┐
│          Development Server             │
│                                         │
│  ┌─────────────────────────────────────┐│
│  │        Docker Containers            ││
│  │                                     ││
│  │  [Electron] [Node.js] [MSSQL] [Mongo]│
│  │    :3000     :8000     :1433  :27017││
│  │                                     ││
│  │  [NGINX]    [Redis]   [Monitoring]  ││
│  │   :80       :6379      :9090        ││
│  └─────────────────────────────────────┘│
└─────────────────────────────────────────┘
```

### 4. Data Flow Diagram
**จุดประสงค์:** แสดงการไหลของข้อมูลในระบบ Agent Wallboard System

```
[Draw.io Code - Data Flow]
Real-time Status Update Flow:
Agent Desktop App → WebSocket Connection → Node.js API → 
MSSQL Update → MongoDB Log → WebSocket Broadcast → All Connected Clients

Message Communication Flow:
Supervisor Dashboard → REST API → Message Router → 
WebSocket Delivery → Target Agent Desktop App → Delivery Confirmation

Authentication Flow:
Login Request → Node.js API → MSSQL User Validation → 
JWT Token Generation → Client Authentication → Session Management

Reporting Data Flow:
Scheduled Job → MongoDB Aggregation → Data Processing → 
Report Generation → MSSQL Storage → Management Dashboard Display
```

---

## 🛠️ การใช้ Draw.io อย่างมีประสิทธิภาพ

### เทคนิคการออกแบบ Diagram สำหรับ Agent Wallboard System

#### 1. การใช้สี (Color Coding) ตาม Technology Stack
```
🔵 น้ำเงิน: Node.js Backend Services
🟢 เขียว: Database Systems (MSSQL + MongoDB)
🟠 ส้ม: Frontend Applications (Electron.js + React.js)
🔴 แดง: External/Network Components
🟡 เหลือง: Security & Authentication Components
🟣 ม่วง: Infrastructure & DevOps Tools
```

#### 2. การใช้ Icons และ Shapes ตาม Agent Wallboard Components
```
🖥️ Desktop App: Computer/Monitor icon สำหรับ Electron.js
🌐 Web Dashboard: Browser icon สำหรับ React.js Dashboard
🗄️ MSSQL Database: Cylinder shape with "SQL" label
📄 MongoDB: Document/Collection icon
⚡ WebSocket: Lightning/Network icon สำหรับ Real-time Communication
🔐 Authentication: Shield icon สำหรับ Security Components
```

#### 3. การจัด Layout ตาม 3-Tier Architecture
```
แนวตั้ง (Vertical 3-Tier):
Presentation Tier (Top)
  ↓ HTTP/WebSocket
Business Logic Tier (Middle)  
  ↓ Database Connections
Data Tier (Bottom)

แนวนอน (Horizontal Flow):
Users → Frontend Apps → API Services → Databases

แบบ Layer (Layered Architecture):
User Interface Layer
API Gateway Layer
Business Logic Layer
Data Access Layer
Infrastructure Layer
```

---

## 📋 Workshop Activity: สร้าง Agent Wallboard Diagrams

### กิจกรรมที่ 1: System Context Diagram (15 นาที)
**เป้าหมาย:** สร้างแผนภาพแสดงภาพรวมของระบบ Agent Wallboard System

**ขั้นตอน:**
1. เปิด Draw.io และเลือก Blank Diagram
2. สร้าง Actor สำหรับผู้ใช้ 4 ประเภท:
   - Call Center Agents (หลัก - Desktop Application)
   - Team Leaders/Supervisors (Dashboard Monitoring)
   - Operations Managers (Reports & Analytics)
   - System Administrators (Configuration)
3. วาด System Box กลางสำหรับ "Agent Wallboard System"
4. เชื่อมเส้นและใส่ Label อธิบายการทำงาน:
   - "Manages status via Desktop App"
   - "Monitors team performance"
   - "Views operational reports"
   - "Configures system settings"
5. ใช้สีและ styling ที่เหมาะสม

**ผลลัพธ์ที่คาดหวัง:**
- แสดงความสัมพันธ์ระหว่าง Users และ System ได้ชัดเจน
- มี Label อธิบายการทำงานของแต่ละเส้นเชื่อม
- ใช้สีแยกประเภทได้เหมาะสม
- เป็น Standalone System ไม่มี External Dependencies

### กิจกรรมที่ 2: Container Diagram (25 นาที)
**เป้าหมาย:** แบ่งระบบออกเป็น Container และแสดงเทคโนโลยีตาม Agent Wallboard System

**ขั้นตอน:**
1. แบ่ง System เป็น 3 กลุ่มใหญ่ตาม 3-Tier Architecture:
   - **Frontend Tier**: 
     * Electron.js Desktop App (Agent Interface)
     * React.js Web Dashboard (Supervisor Interface)
   - **Backend Tier**: 
     * Node.js + Express API Server
     * WebSocket Server (Socket.io)
     * Background Services
   - **Data Tier**: 
     * MSSQL Database (Master Data)
     * MongoDB Database (Real-time Data)

2. กำหนดเทคโนโลยีในแต่ละ Container:
   - Electron.js, React.js, Node.js, Express.js, Socket.io
   - MSSQL Server, MongoDB, Redis (optional for caching)

3. เชื่อมเส้นและระบุ Protocol:
   - HTTP/HTTPS REST API
   - WebSocket Protocol
   - Database Connections (TCP/IP)
   - Authentication (JWT/Bearer Token)

4. เพิ่มรายละเอียด Port และ Endpoint สำคัญ:
   - :3000 (Electron App), :8000 (API Server)
   - :1433 (MSSQL), :27017 (MongoDB)

**ผลลัพธ์ที่คาดหวัง:**
- แสดงสถาปัตยกรรม 3-Tier ได้ชัดเจน
- ระบุเทคโนโลยีที่ใช้จริงใน Agent Wallboard System
- แสดง Communication Protocols ครบถ้วน
- จัด Layout ให้อ่านง่ายและเป็นระบบ

### กิจกรรมที่ 3: Deployment Diagram (15 นาที)
**เป้าหมาย:** แสดงการ Deploy ในสภาพแวดล้อมจริงสำหรับ Agent Wallboard System

**ขั้นตอน:**
1. สร้าง Production Environment Layout:
   - Load Balancer (NGINX)
   - Application Servers (Node.js instances)
   - Database Servers (MSSQL + MongoDB)

2. แสดงการกระจายโหลดและ High Availability:
   - Multiple API Server instances
   - Database clustering/replication
   - WebSocket connection pooling

3. เพิ่มรายละเอียด Infrastructure:
   - Network connections และ Security
   - Backup และ Monitoring systems
   - Development vs Production differences

4. ระบุข้อมูล Technical Specifications:
   - Server requirements และ capacity
   - Network protocols และ security measures
   - Scalability considerations

**ผลลัพธ์ที่คาดหวัง:**
- แสดงแผนการ deploy ที่สามารถนำไปใช้จริงได้
- ครอบคลุม Production และ Development environments
- แสดง Infrastructure requirements ชัดเจน
- พิจารณา Security และ Scalability aspects

---

## 🔧 Draw.io Tips & Tricks สำหรับ Agent Wallboard System

### Keyboard Shortcuts
```
Ctrl+D: Duplicate selected objects
Ctrl+G: Group selected objects
Ctrl+Shift+G: Ungroup
F2: Edit text
Ctrl+Shift+V: Paste without formatting
Ctrl+A: Select all
Delete: Remove selected items
Ctrl+Z: Undo
Ctrl+Y: Redo
```

### Advanced Features สำหรับ Technical Diagrams
```
1. Shape Libraries สำหรับ Tech Stack:
   - Software Architecture Icons
   - Database Icons (SQL/NoSQL)
   - Web Technology Icons
   - Network & Infrastructure Icons

2. Styling Options:
   - Technology-specific color schemes
   - Gradient fills สำหรับ layers
   - Shadow effects สำหรับ depth
   - Line styles (solid, dashed, dotted)

3. Layout Tools:
   - Auto-arrange สำหรับ complex diagrams
   - Align objects เป็นแถว/คอลัมน์
   - Distribute spacing อย่างสม่ำเสมอ
   - Grid และ guides สำหรับ precision
```

### Export Options สำหรับการส่งงาน
```
📄 PDF: สำหรับเอกสารทางการและการส่งงาน
🖼️ PNG: สำหรับใส่ใน presentation หรือ documentation
📐 SVG: สำหรับการแก้ไขต่อและ high quality
🔗 Link: สำหรับแชร์และ collaborate แบบ real-time
💾 VSDX: สำหรับใช้ใน Microsoft Visio
```

---

## ✅ เกณฑ์การประเมิน Architecture Diagrams

### คะแนนเต็ม: 25 คะแนน

#### 1. ความถูกต้องทางเทคนิค (10 คะแนน)
- ✅ แสดงสถาปัตยกรรม 3-Tier ได้ชัดเจน (3 คะแนน)
- ✅ ระบุเทคโนโลยีตาม Agent Wallboard System (Electron.js, Node.js, MSSQL, MongoDB) (3 คะแนน)
- ✅ แสดงการเชื่อมต่อระหว่าง Components ถูกต้อง (2 คะแนน)
- ✅ ใช้ C4 Model หลักการถูกต้อง (2 คะแนน)

#### 2. ความชัดเจนในการสื่อสาร (8 คะแนน)
- ✅ Layout จัดเรียงตาม 3-Tier Architecture เข้าใจง่าย (3 คะแนน)
- ✅ Label และ Description ครบถ้วนสำหรับ Agent Wallboard components (3 คะแนน)
- ✅ ใช้สีและ Icons เหมาะสมกับ Technology Stack (2 คะแนน)

#### 3. ความสมบูรณ์ของเอกสาร (7 คะแนน)
- ✅ System Context Diagram แสดงผู้ใช้ Agent Wallboard System (2 คะแนน)
- ✅ Container Diagram แสดง Technology Stack ครบถ้วน (3 คะแนน)
- ✅ Deployment Diagram สำหรับ Production Environment (2 คะแนน)

### Bonus Points (เพิ่มเติม 5 คะแนน)
- 🌟 การใช้ Advanced Draw.io features อย่างสร้างสรรค์
- 🌟 การออกแบบที่พิจารณา Real-time Communication aspects
- 🌟 การอธิบาย Technology Decision Rationale
- 🌟 การแสดง Scalability และ Performance considerations

---

## 📚 แหล่งข้อมูลเพิ่มเติม

### Template และ Examples สำหรับ Agent Wallboard System
- [C4 Model Templates for Draw.io](https://github.com/plantuml-stdlib/C4-PlantUML)
- [Real-time System Architecture Examples](https://c4model.com/)
- [Node.js Architecture Patterns](https://nodejs.org/en/docs/guides/)
- [Electron.js Architecture Guidelines](https://www.electronjs.org/docs/latest/)

### Best Practices สำหรับ Real-time Systems
- [WebSocket Architecture Patterns](https://socket.io/docs/v4/)
- [Database Design for Real-time Applications](https://docs.mongodb.com/manual/)
- [3-Tier Architecture Best Practices](https://docs.microsoft.com/en-us/azure/architecture/)

### เทคโนโลยีเฉพาะสำหรับ Agent Wallboard System
- [MSSQL + MongoDB Integration Patterns](https://docs.microsoft.com/en-us/sql/)
- [Electron.js + Node.js Communication](https://www.electronjs.org/docs/latest/tutorial/ipc/)
- [Express.js + Socket.io Best Practices](https://expressjs.com/en/advanced/best-practice-performance.html)

### การออกแบบสำหรับ Call Center Systems
- [Call Center Technology Architecture](https://www.genesys.com/)
- [Real-time Monitoring System Design](https://grafana.com/docs/)
- [Agent Management System Patterns](https://www.twilio.com/docs/)

---

## 🎯 หัวข้อต่อไป: สัปดาห์ที่ 6
* **สัปดาห์ที่ 6: Design Patterns - เรียนรู้เทคนิคการก่อสร้าง** 🛠️ ****(เรียนครั้งนี้)**
    * เมื่อเรารู้แล้วว่าบ้านมี "ห้องครัว" และ "ห้องน้ำ" เราก็มาเรียนรู้ **"เทคนิค"** ที่ดีที่สุดในการแก้ปัญหาเฉพาะจุด เช่น:
        * เทคนิคการเดินท่อประปาที่ดีที่สุด (อาจเปรียบได้กับ **Observer Pattern** สำหรับการส่งข้อมูล)
        * เทคนิคการติดตั้งระบบไฟฟ้าให้ปลอดภัย (อาจเปรียบได้กับ **Circuit Breaker Pattern**)
    * **ผลลัพธ์:** นักศึกษาเรียนรู้ "เครื่องมือ" หรือ "สูตรสำเร็จ" โดยมีบริบทจากสัปดาห์ที่ 5 อยู่ในใจแล้วว่า จะนำไปใช้แก้ปัญหาในส่วนไหนของบ้าน
