# สัปดาห์ที่ 7: การออกแบบสถาปัตยกรรมซอฟต์แวร์ - พื้นฐาน (Part 1/4)
## Agent Wallboard System - ENGSE206 มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา (ดอยสะเก็ด)

---

## Slide 1: 🎯 วัตถุประสงค์และเป้าหมายการเรียนรู้

### 📚 วัตถุประสงค์
- **สร้าง C3 (Component) Diagram** แสดง Internal Architecture ของ Agent Wallboard System
- **ออกแบบ Component Interface** และ Dependencies ระหว่าง Components
- **เข้าใจ Component Design Principles** สำหรับระบบ Real-time

### 🎯 เป้าหมายการเรียนรู้
- **วิเคราะห์และแบ่ง Components** ในระบบ 3-Tier Architecture
- **ออกแบบ Interface** ที่มีประสิทธิภาพระหว่าง Components
- **ประยุกต์ใช้ Design Patterns** ที่เรียนมาในการออกแบบ Components

### 📊 ผลที่คาดหวัง
- **สร้าง C3 Component Diagram** ที่สมบูรณ์สำหรับ Agent Wallboard System
- **ออกแบบ Component Interface Specifications** ที่ชัดเจน
- **เตรียมความพร้อม** สำหรับการ Implementation ในสัปดาห์ที่ 8

---

## Slide 2: 📚 ทบทวนและต่อเนื่องจากสัปดาห์ที่แล้ว

### ความเชื่อมโยงของการเรียน

**สัปดาห์ที่ 5: High-Level Architecture**
- หลักการ SOLID, DRY, KISS, YAGNI
- 3-Tier Architecture (Presentation → Application → Data)
- C4 Model Level 1-2 (Context & Container)

**สัปดาห์ที่ 6: Design Patterns**
- **Creational:** Singleton, Factory
- **Structural:** Adapter, Facade
- **Behavioral:** Observer, Strategy, Command
- **Real-time:** Publisher-Subscriber, Circuit Breaker

**สัปดาห์นี้ (ที่ 7): Component Architecture**
- **C4 Level 3:** แบ่ง Components ภายใน Containers
- **Component Design Principles:** High Cohesion, Loose Coupling
- **Component Communication:** Interface Design, Dependencies

**ต่อไปสัปดาห์ที่ 8: Implementation Ready**
- **C4 Level 4:** Code Level Design
- **UML Diagrams:** Class, Sequence, Activity
- **API Specifications:** REST + WebSocket

---

## Slide 3: 🧩 Component คืออะไร?

### ความหมายและลักษณะของ Component

**💡 Component = หน่วยย่อยที่ทำงานได้อิสระและมีหน้าที่เฉพาะ**

**🏠 เปรียบเทียบกับบ้าน:**
- **บ้าน** = ระบบ (Agent Wallboard System)
- **ห้องต่างๆ** = Components (ห้องครัว, ห้องนอน, ห้องน้ำ)
- **แต่ละห้องมีหน้าที่เฉพาะ** แต่ทำงานร่วมกันเป็นบ้าน

**📦 ลักษณะของ Component ที่ดี:**

**1. High Cohesion (ความสอดคล้องภายใน)**
- ส่วนต่างๆ ภายใน component ทำงานร่วมกันดี
- มีเป้าหมายเดียวกัน

**2. Loose Coupling (การพึ่งพาน้อย)**
- พึ่งพา components อื่นน้อย
- เปลี่ยนแปลงได้โดยไม่กระทบส่วนอื่นมาก

**3. Clear Interface (ขอบเขตชัดเจน)**
- มี interface ที่ชัดเจนในการสื่อสารกับ components อื่น
- ซ่อนรายละเอียดภายใน (Encapsulation)

**4. Reusability (ใช้ใหม่ได้)**
- สามารถนำไปใช้ในบริบทอื่นได้
- ไม่ผูกติดกับ implementation เฉพาะ

---

## Slide 4: 🔄 จาก Design Patterns สู่ Components

### การนำ Patterns มาใช้ในการออกแบบ Components

**💼 จากสัปดาห์ที่แล้ว เรามี Patterns:**

**🏭 Creational Patterns:**
- **Singleton** → WebSocket Connection Manager Component
- **Factory** → Message Factory Component

**🏗️ Structural Patterns:**
- **Adapter** → Database Adapter Component  
- **Facade** → API Facade Component

**🎭 Behavioral Patterns:**
- **Observer** → Event Broadcasting Component
- **Strategy** → Authentication Strategy Component

**⚡ Real-time Patterns:**
- **Publisher-Subscriber** → Event Bus Component
- **Circuit Breaker** → Resilience Component

**🎯 การต่อยอด:**
- **Pattern** = วิธีการแก้ปัญหาเฉพาะ
- **Component** = หน่วยการทำงานที่ใช้ Patterns
- **Architecture** = การจัดเรียง Components ให้ทำงานร่วมกัน

**ตัวอย่าง:**
- **Observer Pattern** → **Status Broadcasting Component**
- **Facade Pattern** → **Dashboard API Component**
- **Singleton Pattern** → **WebSocket Manager Component**

---

## Slide 5: 🏢 C4 Model Level 3 - Component Diagram

### จาก Container สู่ Component

**📊 C4 Model Recap:**
- **C1 (Context):** Agent Wallboard System ในบริบทใหญ่
- **C2 (Container):** Desktop App + API Server + Database
- **C3 (Component):** ส่วนประกอบภายใน Container ← **เรียนวันนี้**
- **C4 (Code):** Classes และ Functions ← สัปดาห์หน้า

**🎯 C3 Component Diagram แสดง:**
- Components ภายในแต่ละ Container
- Interface การสื่อสารระหว่าง Components
- Dependencies และ Data Flow
- การใช้งาน Design Patterns

**📈 ความสำคัญ:**
- **สำหรับ Developers:** แผนที่การพัฒนา, Task breakdown
- **สำหรับ Architects:** ตรวจสอบ design, Dependencies analysis  
- **สำหรับ Team Leads:** วางแผนการทำงาน, Resource allocation
- **สำหรับ QA:** Test planning, Integration testing

**🔄 Process:**
```
Container Diagram → Component Breakdown → Interface Design → Implementation Plan
```

---

## Slide 6: 🖥️ Frontend Components - Agent Desktop App

### Components ภายใน Desktop Application (Electron.js)

**📱 Agent Desktop App Container แบ่งเป็น Components:**

**🔐 Authentication Component**
- **หน้าที่:** จัดการการ Login/Logout
- **Interface:** login(credentials), logout(), getCurrentUser()
- **Pattern ที่ใช้:** Strategy Pattern (Local/SSO Authentication)
- **Dependencies:** Auth API, Session Manager

**📊 Status Management Component**
- **หน้าที่:** จัดการสถานะของ Agent (Available, Busy, Break, etc.)
- **Interface:** changeStatus(newStatus), getCurrentStatus(), getStatusHistory()
- **Pattern ที่ใช้:** Observer Pattern (แจ้ง status changes)
- **Dependencies:** Agent API, WebSocket Component

**🔔 Real-time Notification Component**
- **หน้าที่:** รับและแสดง notifications แบบ real-time
- **Interface:** showNotification(message), subscribeToEvents(), unsubscribe()
- **Pattern ที่ใช้:** Observer Pattern (รับ events), Pub-Sub Pattern
- **Dependencies:** WebSocket Component, UI Framework

**👤 Profile Management Component**
- **หน้าที่:** จัดการข้อมูลส่วนตัวของ Agent
- **Interface:** getProfile(), updateProfile(data), getPreferences()
- **Dependencies:** Agent API, Local Storage

**💬 Message Display Component**
- **หน้าที่:** แสดงข้อความจาก Supervisor
- **Interface:** displayMessage(message), markAsRead(), getMessageHistory()
- **Dependencies:** Message API, WebSocket Component

---

## Slide 7: 🖥️ Frontend Components - Supervisor Dashboard

### Components ภายใน Supervisor Web Dashboard

**📊 Dashboard Visualization Component**
- **หน้าที่:** แสดงภาพรวมสถานะ Agents แบบ real-time
- **Interface:** refreshDashboard(), filterAgents(), exportReport()
- **Pattern ที่ใช้:** Observer Pattern (auto-refresh), Facade Pattern (รวมข้อมูล)
- **Dependencies:** Dashboard API, Chart Libraries, WebSocket

**👥 Agent Monitor Component**
- **หน้าที่:** ติดตามสถานะ Agent รายบุคคล
- **Interface:** getAgentStatus(agentId), getAgentHistory(), sendMessage()
- **Pattern ที่ใช้:** Observer Pattern (real-time updates)
- **Dependencies:** Agent API, WebSocket Component

**📨 Message Management Component**
- **หน้าที่:** ส่งข้อความถึง Agents (บุคคลหรือกลุ่ม)
- **Interface:** sendMessage(recipients, message), getBroadcastHistory()
- **Pattern ที่ใช้:** Command Pattern (message commands), Factory Pattern (message types)
- **Dependencies:** Message API, Agent List Component

**📈 Reports Component**
- **หน้าที่:** สร้างและแสดงรายงาน performance
- **Interface:** generateReport(criteria), exportToPDF(), scheduleReport()
- **Pattern ที่ใช้:** Strategy Pattern (report types), Factory Pattern (export formats)
- **Dependencies:** Reporting API, Chart Libraries

**🎛️ Control Panel Component**
- **หน้าที่:** ควบคุมการตั้งค่าทีม และระบบ
- **Interface:** updateTeamSettings(), manageAgents(), systemConfig()
- **Dependencies:** Admin API, Settings Component

---

## Slide 8: ⚙️ Backend Components - API Server

### Components ภายใน Node.js API Server

**🔐 Authentication Service Component**
- **หน้าที่:** ตรวจสอบ credentials และสร้าง sessions
- **Interface:** authenticate(credentials), validateToken(token), refreshSession()
- **Pattern ที่ใช้:** Strategy Pattern (auth methods), Singleton Pattern (session store)
- **Dependencies:** Database Adapter, JWT Library, Password Hash

**👤 Agent Status Service Component**  
- **หน้าที่:** จัดการสถานะ Agents และ status history
- **Interface:** updateStatus(agentId, status), getStatusHistory(), getCurrentTeamStatus()
- **Pattern ที่ใช้:** Observer Pattern (broadcast changes), Command Pattern (status commands)
- **Dependencies:** Database Adapter, WebSocket Manager, Event Bus

**📨 Message Routing Service Component**
- **หน้าที่:** จัดส่งข้อความระหว่าง Supervisors และ Agents
- **Interface:** sendMessage(from, to, message), broadcastMessage(), getMessageHistory()
- **Pattern ที่ใช้:** Factory Pattern (message types), Pub-Sub Pattern (routing)
- **Dependencies:** Database Adapter, WebSocket Manager, Message Queue

**🔌 WebSocket Connection Manager Component**
- **หน้าที่:** จัดการ WebSocket connections และ real-time communication
- **Interface:** handleConnection(socket), broadcastToClients(event, data), manageSubscriptions()
- **Pattern ที่ใช้:** Singleton Pattern (one manager), Observer Pattern (connection events)
- **Dependencies:** Socket.IO Library, Event Bus, Session Manager

**💾 Database Access Layer Component**
- **หน้าที่:** เชื่อมต่อและจัดการข้อมูล (MSSQL + MongoDB)
- **Interface:** query(sql), insertDocument(), updateRecord(), transaction()
- **Pattern ที่ใช้:** Adapter Pattern (database types), Factory Pattern (connection types)
- **Dependencies:** Database Drivers, Connection Pool, Circuit Breaker

---

## Slide 9: 🗄️ Data Tier Components

### Components ภายใน Database Layer

**🗃️ MSSQL Data Component**
- **หน้าที่:** จัดการ structured master data
- **ข้อมูลที่จัดการ:** Agents, Teams, Users, System Configuration
- **Interface:** executeStoredProcedure(), executeSQLQuery(), manageTransactions()
- **Pattern ที่ใช้:** Repository Pattern, Unit of Work Pattern
- **Features:** ACID properties, Referential integrity, Complex queries

**🍃 MongoDB Data Component**
- **หน้าที่:** จัดการ real-time และ log data
- **ข้อมูลที่จัดการ:** Status Logs, Message History, Performance Metrics
- **Interface:** insertDocument(), findDocuments(), updateDocument(), aggregatePipeline()
- **Pattern ที่ใช้:** Repository Pattern, Document Mapper
- **Features:** Fast writes, Flexible schema, Real-time analytics

**🔄 Data Synchronization Component**
- **หน้าที่:** ประสานข้อมูลระหว่าง MSSQL และ MongoDB
- **Interface:** syncAgentData(), syncStatusUpdates(), reconcileData()
- **Pattern ที่ใช้:** Adapter Pattern (data mapping), Observer Pattern (change detection)
- **Dependencies:** Both database components, Event Bus

**💾 Connection Pool Manager Component**
- **หน้าที่:** จัดการ database connections อย่างมีประสิทธิภาพ
- **Interface:** getConnection(dbType), releaseConnection(), monitorHealth()
- **Pattern ที่ใช้:** Singleton Pattern, Object Pool Pattern
- **Features:** Connection reuse, Health monitoring, Load balancing

**🛡️ Data Security Component**
- **หน้าที่:** เข้ารหัสและป้องกันข้อมูล
- **Interface:** encrypt(data), decrypt(data), hashPassword(), auditAccess()
- **Pattern ที่ใช้:** Strategy Pattern (encryption methods), Decorator Pattern (security layers)
- **Dependencies:** Crypto libraries, Audit logs

---

## Slide 10: 🔗 Component Dependencies และ Relationships

### การวิเคราะห์ Dependencies ระหว่าง Components

**📊 Dependency Analysis:**

**🔺 High-Level Dependencies (ขึ้นกับ):**
```
Frontend Components
    ↓ (HTTP/WebSocket)
Backend API Components  
    ↓ (Database queries)
Data Tier Components
```

**🔄 Cross-Component Dependencies:**

**Frontend → Backend:**
- Authentication Component → Authentication Service
- Status Management → Agent Status Service  
- Message Display → Message Routing Service
- Dashboard → Multiple backend services (via Facade)

**Backend Internal Dependencies:**
- WebSocket Manager ← All services (for real-time updates)
- Database Access Layer ← All services (for data operations)
- Authentication Service ← Other services (for authorization)

**Data Tier Dependencies:**
- MongoDB Component ← Real-time operations
- MSSQL Component ← Master data operations  
- Sync Component ← Both database components

**⚠️ Potential Issues:**
- **Circular Dependencies:** A depends on B, B depends on A
- **Too Many Dependencies:** One component depends on many others
- **Wrong Direction:** Lower layer depends on higher layer

**✅ Best Practices:**
- **Dependency Injection:** Don't hardcode dependencies
- **Interface Segregation:** Depend on interfaces, not concrete classes
- **Layered Dependencies:** Higher layers depend on lower layers only