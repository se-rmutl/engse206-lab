# สัปดาห์ที่ 5: Draw.io Architecture Diagrams - Agent Wallboard System

## 🎯 วัตถุประสงค์การเรียนรู้
นักศึกษาสามารถสร้าง Architecture Diagrams ด้วย Draw.io เพื่ออธิบายสถาปัตยกรรมระดับสูง (High-Level Architecture) ของระบบ Agent Wallboard พร้อมใช้หลักการ C4 Model

---

## 📊 Architecture Diagrams แบบต่างๆ

### 1. C1 - System Context Diagram
**จุดประสงค์:** แสดงภาพรวมของระบบ Agent Wallboard และผู้ใช้งานหลัก

```
[Draw.io Code - System Context]
รายละเอียดที่ต้องรวม:
- Agent Wallboard System (ระบบกลาง)
- Call Center Agents (ผู้ใช้หลัก)
- Team Leaders/Supervisors (ผู้จัดการ)
- System Administrator (ผู้ดูแลระบบ)
- External Systems:
  * Phone System (PBX/VoIP)
  * CRM System
  * Reporting Database
  * Real-time Analytics Engine
```

**ขั้นตอนการสร้างใน Draw.io:**
1. เปิด Draw.io → เลือก Template "Business Process"
2. ลาก Shape "Actor" สำหรับผู้ใช้แต่ละประเภท
3. ใช้ "System" shape (สี่เหลี่ยมใหญ่) สำหรับ Agent Wallboard System
4. เชื่อม Arrow พร้อมใส่ label อธิบายการทำงาน
5. ใช้สีแยกประเภท: ฟ้าสำหรับ Users, เขียวสำหรับ Main System, เทาสำหรับ External

### 2. C2 - Container Diagram
**จุดประสงค์:** แสดงส่วนประกอบหลักของระบบและเทคโนโลยีที่ใช้

```
[Draw.io Code - Container Architecture]
Frontend Containers:
- Web Application (React.js)
  * Real-time Dashboard
  * Agent Status Panel
  * Performance Charts
- Mobile App (React Native)
  * Quick Status Updates
  * Emergency Notifications

Backend Containers:
- API Gateway (Node.js + Express)
  * Authentication & Authorization
  * Rate Limiting
  * Request Routing
- Real-time Service (Socket.io)
  * Live Status Updates
  * Event Broadcasting
- Business Logic Service (Node.js)
  * Agent Management
  * Performance Calculation
  * Report Generation
- Background Jobs (Bull Queue)
  * Data Aggregation
  * Scheduled Reports
  * System Maintenance

Data Containers:
- Primary Database (PostgreSQL)
  * Agent Information
  * Historical Data
  * Configuration Settings
- Cache Layer (Redis)
  * Session Storage
  * Real-time Metrics
  * Temporary Data
- Time-series Database (InfluxDB)
  * Performance Metrics
  * Call Statistics
  * Response Time Data
```

**ขั้นตอนการสร้างใน Draw.io:**
1. เลือก Shape "Container" หรือ "Rectangle" สำหรับแต่ละ container
2. จัดกลุ่มตามหน้าที่: Frontend, Backend, Data
3. ใช้สีแยกประเภท: ส้มสำหรับ Frontend, น้ำเงินสำหรับ Backend, เขียวสำหรับ Data
4. เชื่อม Arrow พร้อมระบุ Protocol (HTTP, WebSocket, TCP)
5. เพิ่ม Technology label ในแต่ละ container

### 3. Deployment Diagram
**จุดประสงค์:** แสดงวิธีการ deploy และโครงสร้าง infrastructure

```
[Draw.io Code - Deployment Architecture]
Production Environment:
┌─────────────────────────────────────────┐
│            Load Balancer                │
│              (NGINX)                    │
└──────────────┬─────────────┬────────────┘
               │             │
    ┌──────────▼────────┐   ┌▼────────────────┐
    │   Web Server 1    │   │   Web Server 2  │
    │    (Node.js)      │   │    (Node.js)    │
    │  - API Services   │   │  - API Services │
    │  - Socket.io      │   │  - Socket.io    │
    └──────────┬────────┘   └┬────────────────┘
               │             │
    ┌──────────▼─────────────▼────────────────┐
    │         Database Cluster                │
    │                                         │
    │  ┌────────────┐  ┌─────────────────────┐│
    │  │PostgreSQL  │  │      Redis          ││
    │  │  (Master)  │  │     (Cache)         ││
    │  └──────┬─────┘  └─────────────────────┘│
    │         │                               │
    │  ┌──────▼─────┐  ┌─────────────────────┐│
    │  │PostgreSQL  │  │     InfluxDB        ││
    │  │  (Replica) │  │  (Time-series)      ││
    │  └────────────┘  └─────────────────────┘│
    └─────────────────────────────────────────┘

Development Environment:
┌─────────────────────────────────────────┐
│          Single Server                  │
│                                         │
│  ┌─────────────────────────────────────┐│
│  │        Docker Containers            ││
│  │                                     ││
│  │  [Frontend] [API] [DB] [Cache]      ││
│  │     :3000   :8000 :5432  :6379      ││
│  └─────────────────────────────────────┘│
└─────────────────────────────────────────┘
```

### 4. Data Flow Diagram
**จุดประสงค์:** แสดงการไหลของข้อมูลในระบบ

```
[Draw.io Code - Data Flow]
Real-time Data Flow:
Phone System → API Gateway → Real-time Service → WebSocket → Dashboard

Batch Data Flow:
Historical Data → Background Jobs → Data Processing → Database → Reports

User Action Flow:
Agent Input → Web App → API Gateway → Business Logic → Database → Response
```

---

## 🛠️ การใช้ Draw.io อย่างมีประสิทธิภาพ

### เทคนิคการออกแบบ Diagram

#### 1. การใช้สี (Color Coding)
```
🔵 น้ำเงิน: Backend Services
🟢 เขียว: Databases และ Data Storage
🟠 ส้ม: Frontend Applications
🔴 แดง: External Systems
🟡 เหลือง: Security Components
🟣 ม่วง: Infrastructure และ DevOps
```

#### 2. การใช้ Icons และ Shapes
```
📱 Mobile App: Mobile device icon
💻 Web App: Browser/Computer icon
🗄️ Database: Cylinder shape
🔄 API: Hexagon shape
⚡ Real-time: Lightning icon
🔐 Security: Shield icon
```

#### 3. การจัด Layout
```
แนวนอน (Horizontal):
User → Frontend → Backend → Database

แนวตั้ง (Vertical):
Frontend (Top)
↓
Backend (Middle)  
↓
Database (Bottom)

แบบ Layer (Layered):
Presentation Layer
Business Logic Layer
Data Access Layer
Infrastructure Layer
```

---

## 📋 Workshop Activity: สร้าง Agent Wallboard Diagrams

### กิจกรรมที่ 1: System Context Diagram (15 นาที)
**เป้าหมาย:** สร้างแผนภาพแสดงภาพรวมของระบบ

**ขั้นตอน:**
1. เปิด Draw.io และเลือก Blank Diagram
2. สร้าง Actor สำหรับผู้ใช้ 3 ประเภท:
   - Call Center Agent
   - Team Leader
   - System Administrator
3. วาด System Box สำหรับ "Agent Wallboard System"
4. เพิ่ม External Systems:
   - Phone System (PBX)
   - CRM Database
   - Reporting System
5. เชื่อมเส้นและใส่ Label อธิบายการทำงาน

**ผลลัพธ์ที่คาดหวัง:**
- แสดงความสัมพันธ์ระหว่าง Users และ System ได้ชัดเจน
- มี Label อธิบายการทำงานของแต่ละเส้นเชื่อม
- ใช้สีแยกประเภทได้เหมาะสม

### กิจกรรมที่ 2: Container Diagram (20 นาที)
**เป้าหมาย:** แบ่งระบบออกเป็น Container และแสดงเทคโนโลยี

**ขั้นตอน:**
1. แบ่ง System เป็น 3 กลุ่มใหญ่:
   - Frontend (React Dashboard, Mobile App)
   - Backend (API Server, Real-time Service, Background Jobs)
   - Data (Database, Cache, Analytics DB)
2. กำหนดเทคโนโลยีในแต่ละ Container:
   - React.js, Node.js, PostgreSQL, Redis
3. เชื่อมเส้นและระบุ Protocol:
   - HTTP REST API
   - WebSocket
   - SQL
4. เพิ่มรายละเอียด Port หรือ Endpoint สำคัญ

**ผลลัพธ์ที่คาดหวัง:**
- แสดงสถาปัตยกรรม 3-Tier ได้ชัดเจน
- ระบุเทคโนโลยีและ Protocol ครบถ้วน
- จัด Layout ให้อ่านง่าย

### กิจกรรมที่ 3: Deployment Diagram (15 นาที)
**เป้าหมาย:** แสดงการ Deploy ในสภาพแวดล้อมจริง

**ขั้นตอน:**
1. สร้าง Server Nodes:
   - Load Balancer
   - Application Servers (2 nodes)
   - Database Server
2. แสดงการกระจายโหลดและ Failover
3. เพิ่มรายละเอียด Infrastructure:
   - Network connections
   - Backup systems
   - Monitoring tools
4. ระบุข้อมูล Technical:
   - Server specs
   - Network protocols
   - Security measures

---

## 🔧 Draw.io Tips & Tricks

### Keyboard Shortcuts
```
Ctrl+D: Duplicate selected objects
Ctrl+G: Group selected objects
Ctrl+Shift+G: Ungroup
F2: Edit text
Ctrl+Shift+V: Paste without formatting
Ctrl+A: Select all
Delete: Remove selected items
```

### Advanced Features
```
1. Shape Libraries:
   - AWS Architecture Icons
   - Google Cloud Icons
   - Kubernetes Icons
   - UML Shapes

2. Styling Options:
   - Custom color palettes
   - Gradient fills
   - Shadow effects
   - Line styles (dashed, dotted)

3. Layout Tools:
   - Auto-arrange
   - Align objects
   - Distribute spacing
   - Grid and guides
```

### Export Options
```
📄 PDF: สำหรับเอกสารทางการ
🖼️ PNG: สำหรับใส่ใน presentation
📐 SVG: สำหรับการแก้ไขต่อ
🔗 Link: สำหรับแชร์และ collaborate
```

---

## ✅ เกณฑ์การประเมิน Architecture Diagrams

### คะแนนเต็ม: 25 คะแนน

#### 1. ความถูกต้องทางเทคนิค (10 คะแนน)
- ✅ แสดงสถาปัตยกรรม 3-Tier ได้ชัดเจน (3 คะแนน)
- ✅ ระบุเทคโนโลยีที่ใช้ได้ถูกต้อง (3 คะแนน)
- ✅ แสดงการเชื่อมต่อระหว่าง Components (2 คะแนน)
- ✅ ใช้ C4 Model หลักการถูกต้อง (2 คะแนน)

#### 2. ความชัดเจนในการสื่อสาร (8 คะแนน)
- ✅ Layout จัดเรียงเข้าใจง่าย (3 คะแนน)
- ✅ Label และ Description ครบถ้วน (3 คะแนน)
- ✅ ใช้สีและ Icons เหมาะสม (2 คะแนน)

#### 3. ความสมบูรณ์ของเอกสาร (7 คะแนน)
- ✅ System Context Diagram (2 คะแนน)
- ✅ Container Diagram (3 คะแนน)
- ✅ Deployment Diagram (2 คะแนน)

---

## 📚 แหล่งข้อมูลเพิ่มเติม

### Template และ Examples
- [C4 Model Templates for Draw.io](https://github.com/plantuml-stdlib/C4-PlantUML)
- [System Architecture Examples](https://c4model.com/)
- [Draw.io Shape Libraries](https://app.diagrams.net/libs)

### Best Practices
- [Architecture Documentation Guidelines](https://arc42.org/)
- [Diagramming Standards](https://www.visual-paradigm.com/)
- [Color Theory for Technical Diagrams](https://uxdesign.cc/)

### สำหรับการทำงานจริง
- [Enterprise Architecture Tools Comparison](https://www.gartner.com/)
- [Cloud Architecture Best Practices](https://aws.amazon.com/architecture/)
- [Microservices Architecture Patterns](https://microservices.io/)

---

## 🎯 หัวข้อต่อไป: สัปดาห์ที่ 6
**การออกแบบข้อมูลและฐานข้อมูล (Database Design)**
- Entity-Relationship Diagrams
- Data Modeling สำหรับ Agent Wallboard
- การเลือกใช้ Database Technology
- Performance และ Scaling Considerations