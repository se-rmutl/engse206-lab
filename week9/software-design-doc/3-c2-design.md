# Agent Wallboard System - C2 Container Diagram
## Software Architecture - C4 Model Level 2

**Document ID:** C2-AWS-001  
**Version:** 1.0  
**วันที่:** กันยายน 2025  
**จัดทำโดย:** อาจารย์ ENGSE206 - RMUTL  

---

## 📦 1. C2 Container Diagram

### 1.1 Container Architecture Overview 

```mermaid
graph TB
    %% External Users
    Agent["👤 Agent<br/>Call Center Staff"]
    Supervisor["👥 Supervisor<br/>Team Manager"]
    Manager["🏢 Operations Manager<br/>Department Head"]
    Admin["⚙️ System Admin<br/>IT Personnel"]
    
    %% External Systems (เฉพาะที่จำเป็น)
    FileShare["📁 File Share"]
    
    subgraph "Agent Wallboard System"
        %% Frontend Containers
        DesktopApp["🖥️ Agent Desktop App<br/>---<br/>Technology: Electron + React<br/>Responsibilities:<br/>- Agent status management<br/>- Message receiving<br/>- Desktop notifications<br/>- Simple UI for agents"]
        
        WebApp["🌐 Web Dashboard<br/>---<br/>Technology: React + Material-UI<br/>Responsibilities:<br/>- Team monitoring dashboard<br/>- Message sending interface<br/>- Performance analytics<br/>- Report generation"]
        
        AdminPanel["⚙️ Admin Panel<br/>---<br/>Technology: React + Simple Admin UI<br/>Responsibilities:<br/>- User management (CRUD)<br/>- System configuration<br/>- Basic system monitoring<br/>- Simple admin tools"]
        
        %% Backend Containers
        APIServer["🔧 API Server<br/>---<br/>Technology: Node.js + Express<br/>Responsibilities:<br/>- REST API endpoints<br/>- Business logic<br/>- Simple authentication (JWT)<br/>- Data validation"]
        
        WebSocketServer["⚡ WebSocket Server<br/>---<br/>Technology: Socket.io<br/>Responsibilities:<br/>- Real-time status updates<br/>- Message broadcasting<br/>- Live notifications<br/>- Connection management"]
        
        %% Database Containers (เฉพาะที่จำเป็น)
        SQLServer["🗄️ SQL Server Database<br/>---<br/>Technology: Microsoft SQL Server<br/>Responsibilities:<br/>- User accounts & teams<br/>- System configuration<br/>- Audit logs<br/>- Master data"]
        
        MongoDB["🍃 MongoDB Database<br/>---<br/>Technology: MongoDB<br/>Responsibilities:<br/>- Agent status & history<br/>- Messages & conversations<br/>- Performance metrics<br/>- Real-time data"]
    end
    
    %% User to Frontend Connections
    Agent -->|Desktop Application<br/>HTTP/WebSocket| DesktopApp
    Supervisor -->|Web Browser<br/>HTTPS/WebSocket| WebApp
    Manager -->|Web Browser<br/>HTTPS| WebApp
    Admin -->|Web Browser<br/>HTTPS| AdminPanel
    
    %% Frontend to Backend Connections
    DesktopApp -->|REST API<br/>HTTP/JSON| APIServer
    DesktopApp -->|Real-time Updates<br/>WebSocket| WebSocketServer
    
    WebApp -->|REST API<br/>HTTP/JSON| APIServer
    WebApp -->|Real-time Updates<br/>WebSocket| WebSocketServer
    
    AdminPanel -->|REST API<br/>HTTP/JSON| APIServer
    
    %% Backend Interconnections
    APIServer -->|SQL Queries<br/>Connection Pool| SQLServer
    APIServer -->|Document Operations<br/>MongoDB Driver| MongoDB
    
    WebSocketServer -->|Real-time Data<br/>MongoDB Driver| MongoDB
    
    %% External System Connections 
    APIServer -->|File Export<br/>Simple File Copy| FileShare
    
    %% Styling
    classDef person fill:#08427b,color:#ffffff,stroke:#052e56
    classDef frontend fill:#1168bd,color:#ffffff,stroke:#0b4884
    classDef backend fill:#3c9f3c,color:#ffffff,stroke:#2d7a2d
    classDef database fill:#8b4513,color:#ffffff,stroke:#654321
    classDef external fill:#999999,color:#ffffff,stroke:#6b6b6b
    
    class Agent,Supervisor,Manager,Admin person
    class DesktopApp,WebApp,AdminPanel frontend
    class APIServer,WebSocketServer backend
    class SQLServer,MongoDB database
    class FileShare external
```

---

## 🏗️ 2. Container Details 

### 2.1 Frontend Containers

#### 🖥️ **Agent Desktop App**
**Technology Stack:** Electron + React (simple stack)  
**Target Platform:** Windows, macOS, Linux  
**Primary Users:** Agent (100-200 คน)

**Key Features:**
- **Simple Status Management:** dropdown สำหรับเปลี่ยนสถานะ
- **Message Inbox:** รับและอ่านข้อความจาก Supervisor
- **Desktop Notifications:** แจ้งเตือนแบบ native OS
- **Real-time Updates:** อัปเดตสถานะทันทีผ่าน WebSocket

**Technical Specifications:**
- **Simple Packaging:** Electron Builder สำหรับ easy distribution
- **State Management:** React useState + useContext (no complex state management)
- **UI Framework:** Material-UI สำหรับ consistent design
- **Real-time:** Socket.io client สำหรับ WebSocket connection

#### 🌐 **Web Dashboard**
**Technology Stack:** React + Material-UI (standard web stack)  
**Target Platform:** Modern Web Browsers  
**Primary Users:** Supervisor (10-30 คน), Operations Manager (5-10 คน)

**Key Features:**
- **Team Dashboard:** grid แสดงสถานะ Agent แบบ simple
- **Message Center:** ส่งข้อความ direct และ broadcast
- **Basic Analytics:** simple charts แสดงประสิทธิภาพทีม
- **Report Export:** export เป็น Excel/PDF

**Technical Specifications:**
- **Simple Build:** Create React App (no complex bundling)
- **Charts:** Chart.js สำหรับ basic data visualization
- **State Management:** React Query สำหรับ server state
- **Responsive Design:** รองรับ desktop และ tablet

#### ⚙️ **Admin Panel**
**Technology Stack:** React + Simple Admin Framework  
**Target Platform:** Web Browsers  
**Primary Users:** System Admin (2-5 คน)

**Key Features:**
- **User Management:** simple CRUD สำหรับ user accounts
- **System Configuration:** basic settings และ parameters
- **Activity Logs:** ดู system logs และ user activities
- **Basic Monitoring:** แสดง system health อย่างง่าย

**Technical Specifications:**
- **Simple Framework:** React Admin หรือ custom simple forms
- **Data Tables:** basic tables with pagination
- **Form Validation:** simple client-side validation
- **Access Control:** basic role-based components

### 2.2 Backend Containers

#### 🔧 **API Server**
**Technology Stack:** Node.js + Express (standard backend)  
**Architecture Pattern:** Simple REST API + basic MVC  
**Responsibilities:** Business logic และ data processing

**Key Features:**
- **Simple Authentication:** JWT tokens (no complex auth)
- **Basic Authorization:** role-based access (Agent/Supervisor/Admin)
- **CRUD Operations:** standard Create, Read, Update, Delete
- **Data Validation:** basic input validation และ sanitization

**API Endpoints :**
```javascript
// Authentication
POST /api/auth/login
POST /api/auth/logout

// Agent Management  
GET  /api/agents
PUT  /api/agents/:id/status
GET  /api/agents/:id/history

// Messaging
POST /api/messages/send
GET  /api/messages/inbox/:userId
PUT  /api/messages/:id/read

// Admin Operations
GET  /api/admin/users
POST /api/admin/users
PUT  /api/admin/config
```

**Technical Specifications:**
- **Framework:** Express.js with basic middleware
- **Validation:** express-validator สำหรับ input validation
- **Error Handling:** simple try-catch และ error responses
- **Logging:** basic console.log และ file logging

#### ⚡ **WebSocket Server**
**Technology Stack:** Socket.io + Node.js (simple real-time)  
**Architecture Pattern:** Event-driven communication  
**Responsibilities:** Real-time data broadcasting

**Key Features:**
- **Status Broadcasting:** ส่งการเปลี่ยนสถานะ Agent
- **Message Delivery:** ส่งข้อความแบบ real-time
- **Connection Management:** handle connect/disconnect
- **Simple Rooms:** organize users by teams

**Socket Events :**
```javascript
// Agent Events
'agent:status-change'     // Agent เปลี่ยนสถานะ
'agent:online'            // Agent เข้าระบบ
'agent:offline'           // Agent ออกระบบ

// Supervisor Events  
'supervisor:join-team'    // เข้าร่วม team room
'supervisor:send-message' // ส่งข้อความ

// System Events
'system:notification'     // แจ้งเตือนทั่วไป
```

**Technical Specifications:**
- **Simple Scaling:** no Redis adapter (single server instance)
- **Basic Authentication:** JWT verification for connections
- **Error Handling:** basic connection retry
- **Performance:** simple connection limits

### 2.3 Database Containers

#### 🗄️ **SQL Server Database**
**Technology:** Microsoft SQL Server 2019+ (หรือ SQL Server Express)  
**Purpose:** Master data และ structured information  
**Data Types:** User accounts, configuration, audit logs

**Key Tables :**
```sql
-- Core Tables เท่านั้น
Users (UserID, AgentCode, FullName, Role, TeamID)
Teams (TeamID, TeamName, SupervisorID)
SystemConfig (ConfigKey, ConfigValue, Description)
AuditLogs (LogID, UserID, Action, Timestamp, Details)

-- Simple Indexes
CREATE INDEX IX_Users_AgentCode ON Users(AgentCode)
CREATE INDEX IX_AuditLogs_Timestamp ON AuditLogs(Timestamp)
```

**Technical Specifications:**
- **Simple Connection:** basic connection pooling (5-10 connections)
- **Basic Backup:** daily full backup script
- **Performance:** basic indexes สำหรับ common queries
- **Security:** basic SQL authentication

#### 🍃 **MongoDB Database**
**Technology:** MongoDB 5.0+ (หรือ Community Edition)  
**Purpose:** Real-time data และ flexible documents  
**Data Types:** Agent status, messages, performance data

**Key Collections :**
```javascript
// Agent Status Collection
{
  _id: ObjectId,
  agentId: "AG001",
  status: "Available",
  timestamp: ISODate(),
  duration: 3600
}

// Messages Collection
{
  _id: ObjectId,
  senderId: "SP001",
  recipientId: "AG001", // null for broadcast
  type: "direct",       // or "broadcast"
  content: "Please check the queue",
  priority: "normal",
  sentAt: ISODate(),
  readAt: ISODate()
}

// Performance Metrics Collection
{
  _id: ObjectId,
  teamId: 1,
  date: ISODate(),
  metrics: {
    totalAgents: 15,
    utilization: 87.5,
    statusCounts: { available: 8, busy: 4, break: 2, offline: 1 }
  }
}
```

**Technical Specifications:**
- **Simple Setup:** single instance (no replica set initially)
- **Basic Indexes:** simple indexes สำหรับ query performance
- **Simple Aggregation:** basic pipelines สำหรับ analytics
- **No Complex Features:** no sharding, no advanced security

---

## 🔗 3. Communication Protocols 

### 3.1 Frontend-Backend Communication

#### **HTTP REST API (Standard)**
```
Protocol: HTTPS (basic TLS)
Format: JSON
Authentication: Bearer Token (JWT)
Rate Limiting: basic limits (100 req/min per user)

Example Request:
PUT /api/agents/AG001/status
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
Content-Type: application/json

{
  "status": "Break",
  "reason": "Lunch break"
}
```

#### **WebSocket (Simple Real-time)**
```
Protocol: WSS (WebSocket Secure)
Format: JSON Events
Authentication: JWT in connection handshake
Heartbeat: simple ping/pong every 60 seconds

Example Event:
{
  "event": "agent:status-change",
  "data": {
    "agentId": "AG001",
    "newStatus": "Break", 
    "timestamp": "2025-09-21T10:30:00Z"
  }
}
```

### 3.2 Backend-Database Communication

#### **SQL Server (Basic Queries)**
```javascript
// Simple Connection Pool
const sql = require('mssql');
const pool = new sql.ConnectionPool({
  server: 'localhost',
  database: 'AgentWallboard',
  user: 'app_user',
  password: 'password',
  pool: {
    max: 10,
    min: 2,
    idleTimeoutMillis: 30000
  }
});
```

#### **MongoDB (Simple Operations)**
```javascript
// Basic MongoDB Connection
const mongoose = require('mongoose');
mongoose.connect('mongodb://localhost:27017/wallboard', {
  useNewUrlParser: true,
  useUnifiedTopology: true
});
```

---

## 🛡️ 4. Security 

### 4.1 Simple Authentication Flow

```mermaid
sequenceDiagram
    participant U as User
    participant FE as Frontend App
    participant API as API Server
    participant DB as SQL Server
    
    U->>FE: Login (username/password)
    FE->>API: POST /api/auth/login
    API->>DB: Check user credentials
    DB-->>API: User data + role
    API-->>FE: JWT Token + User info
    FE-->>U: Login successful
    
    Note over API,DB: Simple password hash check
    Note over FE,API: JWT expires in 8 hours
```

### 4.2 Authorization Matrix 

| User Role | Desktop App | Web Dashboard | Admin Panel | API Access |
|-----------|-------------|---------------|-------------|-------------|
| **Agent** | ✅ Full Access | ❌ No Access | ❌ No Access | ✅ Agent APIs only |
| **Supervisor** | ❌ No Access | ✅ Team Access | ❌ No Access | ✅ Team APIs only |
| **Manager** | ❌ No Access | ✅ Read Only | ❌ No Access | ✅ Reports only |
| **Admin** | ❌ No Access | ✅ Limited | ✅ Full Access | ✅ Admin APIs |

### 4.3 Basic Security Measures

#### **Simple Data Protection:**
- **Basic Encryption:** HTTPS สำหรับ web traffic
- **Password Security:** bcrypt hashing (simple implementation)
- **JWT Tokens:** HS256 signing (basic JWT)
- **Input Validation:** basic sanitization และ validation

#### **Network Security (เบื้องต้น):**
- **Firewall:** open only necessary ports (3000, 3001, 1433, 27017)
- **Local Network:** ระบบรันบน LAN เท่านั้น
- **Basic Access Control:** simple IP restrictions ถ้าจำเป็น

---

## 📊 5. Performance & Scalability (เหมาะสำหรับนักศึกษา)

### 5.1 Performance Targets (realistic for students)

| Component | Response Time | Throughput | Notes |
|-----------|---------------|------------|-------|
| **API Server** | < 500ms | 100 req/sec | Basic performance |
| **WebSocket** | < 2 seconds | 100 connections | Simple real-time |
| **SQL Server** | < 100ms | 50 queries/sec | Basic queries |
| **MongoDB** | < 50ms | 100 ops/sec | Simple operations |

### 5.2 Simple Scaling Strategy

#### **Initial Setup (for students):**
- **Single Server:** รัน API + WebSocket บน server เดียว
- **Local Database:** SQL Server + MongoDB บน server เดียว
- **Basic Load Handling:** รองรับ 50-100 concurrent users

#### **Future Scaling (if needed):**
- **Separate Servers:** แยก API server และ database server
- **Load Balancer:** simple nginx load balancer
- **Database Optimization:** indexes และ query optimization

---

## ✅ 6. Implementation Roadmap (12 สัปดาห์)

### 6.1 Development Phases (เหมาะสำหรับนักศึกษา)

#### **Phase 1: Basic Setup (Weeks 1-3)**
- ✅ Database setup (SQL Server + MongoDB)
- ✅ Basic API server (Node.js + Express)
- ✅ Simple authentication (JWT)
- ✅ Basic CRUD operations

#### **Phase 2: Core Features (Weeks 4-6)**
- ✅ Agent Desktop App (Electron + React)
- ✅ WebSocket implementation (Socket.io)
- ✅ Real-time status updates
- ✅ Basic messaging system

#### **Phase 3: Dashboard & Admin (Weeks 7-9)**
- ✅ Supervisor Web Dashboard (React)
- ✅ Basic analytics และ charts
- ✅ Admin Panel (simple CRUD)
- ✅ Report export functionality

#### **Phase 4: Testing & Polish (Weeks 10-12)**
- ✅ Integration testing
- ✅ Basic performance optimization
- ✅ Simple deployment setup
- ✅ Documentation และ user guides

### 6.2 Technology Rationale (สำหรับนักศึกษา)

#### **Why Node.js + Express?**
- **เรียนรู้ง่าย:** JavaScript ที่คุ้นเคย
- **Community Support:** มี tutorial และ examples เยอะ
- **Real-time Ready:** ดีสำหรับ WebSocket applications
- **Rapid Development:** สร้าง prototype ได้เร็ว

#### **Why React?**
- **Popular Framework:** ใช้กันแพร่หลายในอุตสาหกรรม
- **Component-based:** เรียนรู้ concept ที่สำคัญ
- **Good Documentation:** มี resources สำหรับการเรียนรู้
- **Cross-platform:** ใช้ได้ทั้ง web และ desktop (Electron)

#### **Why SQL Server + MongoDB?**
- **Best Practice:** เรียนรู้ทั้ง relational และ NoSQL
- **Practical Experience:** ใช้จริงในอุตสาหกรรม
- **Clear Separation:** structured data vs flexible data
- **Performance Learning:** เข้าใจ when to use what

---

## 🚀 7. Summary และ Next Steps

### 7.1 Container Architecture Summary

**Agent Wallboard System** ประกอบด้วย **7 containers หลัก:**

#### **Frontend Tier (3 containers):**
🖥️ **Agent Desktop App** (Electron + React)  
🌐 **Web Dashboard** (React + Material-UI)  
⚙️ **Admin Panel** (React + Simple Admin Framework)  

#### **Backend Tier (2 containers):**
🔧 **API Server** (Node.js + Express)  
⚡ **WebSocket Server** (Socket.io)  

#### **Data Tier (2 containers):**
🗄️ **SQL Server** (Master data)  
🍃 **MongoDB** (Real-time data)  

### 7.2 Key Architecture Decisions (เหมาะสำหรับนักศึกษา)

✅ **Simplicity First:** เลือก technologies ที่เรียนรู้ง่าย  
✅ **Standard Stack:** JavaScript ecosystem ทั้งหมด  
✅ **Clear Separation:** แยก concerns ระหว่าง containers ชัดเจน  
✅ **Scalable Foundation:** สามารถขยายได้ในอนาคต  
✅ **Student-friendly:** 12 สัปดาห์พัฒนาได้จริง  

### 7.3 No Complex Dependencies

❌ **ไม่ใช้สิ่งที่ซับซ้อน:**
- ไม่มี Redis (ใช้ in-memory แทน)
- ไม่มี LDAP/Active Directory
- ไม่มี Email system integration
- ไม่มี Complex microservices
- ไม่มี Advanced monitoring tools

### 7.4 Next Steps: C3 Component Diagram

การออกแบบ **C3 Component Diagram** ในขั้นต่อไปจะแสดง:

🧩 **Internal Components:** Controllers, Services, Models ภายในแต่ละ container  
🔧 **Simple Patterns:** MVC pattern, Service layer  
📡 **Component Interactions:** ง่ายและเข้าใจได้  
🗃️ **Data Access:** ORMs, Database connections  

**C2 Container Diagram นี้เรียบง่าย เหมาะสำหรับนักศึกษา และพัฒนาได้จริงใน 12 สัปดาห์!** 🚀 Specifications:**
- **Scalability:** Redis Adapter สำหรับ horizontal scaling
- **Authentication:** JWT verification สำหรับ WebSocket connections
- **Error Handling:** Graceful connection recovery
- **Performance:** Connection pooling และ rate limiting

### 2.3 Database Containers

#### 🗄️ **SQL Server Database**
**Technology:** Microsoft SQL Server 2019+  
**Purpose:** Structured data และ ACID transactions  
**Data Types:** User management, configuration, audit logs

**Key Tables:**
```sql
-- Core Tables
Users (UserID, AgentCode, FullName, Role, TeamID)
Teams (TeamID, TeamName, SupervisorID)
SystemConfig (ConfigKey, ConfigValue, Description)
AuditLogs (LogID, UserID, Action, Timestamp, Details)

-- Indexes for Performance
CREATE INDEX IX_Users_AgentCode ON Users(AgentCode)
CREATE INDEX IX_AuditLogs_Timestamp ON AuditLogs(Timestamp DESC)
CREATE INDEX IX_Users_TeamID ON Users(TeamID)
```

**Technical Specifications:**
- **Connection Pooling:** SQL Server connection pool (10-50 connections)
- **Backup Strategy:** Full backup daily, transaction log backup hourly
- **Performance:** Optimized indexes สำหรับ common queries
- **Security:** Encrypted connections, least privilege access

#### 🍃 **MongoDB Database**
**Technology:** MongoDB 5.0+  
**Purpose:** Flexible documents และ real-time data  
**Data Types:** Agent status, messages, performance metrics

**Key Collections:**
```javascript
// Agent Status Collection
{
  _id: ObjectId,
  agentId: "AG001",
  status: "Available",
  timestamp: ISODate(),
  duration: 3600,
  metadata: { location: "Floor1", shift: "Morning" }
}

// Messages Collection
{
  _id: ObjectId,
  senderId: "SP001",
  recipientId: "AG001", // null for broadcast
  type: "direct",       // or "broadcast"
  content: "Please check the new procedure",
  priority: "normal",   // "normal", "urgent", "critical"
  sentAt: ISODate(),
  readAt: ISODate()
}

// Performance Metrics Collection
{
  _id: ObjectId,
  teamId: 1,
  date: ISODate(),
  metrics: {
    totalAgents: 15,
    utilization: 87.5,
    statusBreakdown: {
      available: 8, busy: 4, break: 2, offline: 1
    }
  }
}
```

**Technical Specifications:**
- **Replica Set:** 3-node replica set สำหรับ high availability
- **Indexes:** Compound indexes สำหรับ query optimization
- **Aggregation:** Pipeline สำหรับ real-time analytics
- **Change Streams:** Real-time data synchronization

#### 🔴 **Redis Cache**
**Technology:** Redis 6.0+  
**Purpose:** In-memory cache และ session storage  
**Data Types:** Sessions, cache, rate limiting

**Key Data Structures:**
```javascript
// Session Storage
"session:jwt_token_hash" = {
  userId: "AG001",
  role: "agent", 
  teamId: 1,
  loginTime: timestamp,
  lastActivity: timestamp
}

// Agent Status Cache (for quick lookup)
"agent:AG001:status" = {
  status: "Available",
  lastUpdate: timestamp,
  onlineStatus: "online"
}

// Rate Limiting
"rate_limit:192.168.1.100" = {
  count: 45,
  windowStart: timestamp
}
```

**Technical Specifications:**
- **Persistence:** RDB snapshots + AOF logging
- **Memory Management:** LRU eviction policy
- **Clustering:** Redis Cluster สำหรับ scalability
- **Monitoring:** Redis metrics และ slow query logging

---

## 🔗 3. Communication Protocols

### 3.1 Frontend-Backend Communication

#### **HTTP REST API (Synchronous)**
```
Protocol: HTTPS (TLS 1.3)
Format: JSON
Authentication: Bearer Token (JWT)
Rate Limiting: 100 requests/minute per user

Example Request:
PUT /api/agents/AG001/status
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
Content-Type: application/json

{
  "status": "Break",
  "reason": "Lunch break",
  "estimatedDuration": 3600
}
```

#### **WebSocket (Real-time)**
```
Protocol: WSS (WebSocket Secure)
Format: JSON Events
Authentication: JWT in connection handshake
Heartbeat: 30-second ping/pong

Example Event:
{
  "event": "agent:status-change",
  "data": {
    "agentId": "AG001",
    "newStatus": "Break", 
    "timestamp": "2025-09-21T10:30:00Z",
    "teamId": 1
  }
}
```

### 3.2 Backend-Database Communication

#### **SQL Server (Structured Queries)**
```javascript
// Connection Pool Configuration
const pool = new sql.ConnectionPool({
  server: 'sql-server.internal',
  database: 'AgentWallboard',
  user: 'app_user',
  password: 'secure_password',
  pool: {
    max: 20,
    min: 5,
    idleTimeoutMillis: 30000
  },
  options: {
    encrypt: true,
    trustServerCertificate: false
  }
});
```

#### **MongoDB (Document Operations)**
```javascript
// MongoDB Connection
const mongoose = require('mongoose');
mongoose.connect('mongodb://mongo-cluster:27017/wallboard', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
  maxPoolSize: 10,
  serverSelectionTimeoutMS: 5000,
  socketTimeoutMS: 45000
});
```

#### **Redis (Key-Value Operations)**
```javascript
// Redis Connection
const redis = require('redis');
const client = redis.createClient({
  host: 'redis-cluster',
  port: 6379,
  password: 'redis_password',
  db: 0,
  retry_strategy: (options) => {
    return Math.min(options.attempt * 100, 3000);
  }
});
```

---

## 🛡️ 4. Security Boundaries

### 4.1 Authentication Flow

```mermaid
sequenceDiagram
    participant U as User
    participant FE as Frontend App
    participant API as API Server
    participant AD as Active Directory
    participant Redis as Redis Cache
    
    U->>FE: Login (username/password)
    FE->>API: POST /api/auth/login
    API->>AD: LDAP Authentication
    AD-->>API: User credentials + groups
    API->>Redis: Store session data
    API-->>FE: JWT Token + User info
    FE-->>U: Login successful
    
    Note over API,Redis: JWT expires in 8 hours
    Note over FE,API: All subsequent requests include JWT
```

### 4.2 Authorization Matrix

| User Role | Desktop App | Web Dashboard | Admin Panel | API Access | WebSocket |
|-----------|-------------|---------------|-------------|-------------|-----------|
| **Agent** | ✅ Full Access | ❌ No Access | ❌ No Access | ✅ Limited | ✅ Agent Events |
| **Supervisor** | ❌ No Access | ✅ Full Access | ❌ No Access | ✅ Team Data | ✅ Team Events |
| **Manager** | ❌ No Access | ✅ Read Only | ❌ No Access | ✅ Reports | ✅ Metrics |
| **Admin** | ❌ No Access | ✅ Limited | ✅ Full Access | ✅ Admin APIs | ✅ System Events |

### 4.3 Data Protection

#### **Encryption Standards:**
- **In Transit:** TLS 1.3 สำหรับ HTTPS/WSS
- **At Rest:** AES-256 สำหรับ database encryption
- **JWT Tokens:** HS256 signing algorithm
- **Passwords:** bcrypt hashing (12 rounds)

#### **Network Security:**
- **Firewall Rules:** Allow only necessary ports (443, 27017, 6379, 1433)
- **VPN Access:** Admin operations require VPN connection
- **IP Whitelisting:** Production access limited to corporate IPs
- **Rate Limiting:** API และ WebSocket connection limits

---

## 📊 5. Scalability และ Performance

### 5.1 Horizontal Scaling Strategy

#### **Frontend Scaling:**
- **Web Apps:** CDN distribution + multiple instances
- **Desktop Apps:** Auto-update mechanism + client-side caching

#### **Backend Scaling:**
- **API Server:** Load balancer + multiple Node.js instances
- **WebSocket Server:** Redis Adapter สำหรับ multi-instance communication

#### **Database Scaling:**
- **SQL Server:** Read replicas สำหรับ reporting queries
- **MongoDB:** Sharded cluster สำหรับ large datasets
- **Redis:** Cluster mode สำหรับ high availability

### 5.2 Performance Targets

| Component | Response Time | Throughput | Availability |
|-----------|---------------|------------|--------------|
| **API Server** | < 200ms (95th percentile) | 1,000 req/sec | 99.9% |
| **WebSocket** | < 100ms latency | 500 concurrent connections | 99.9% |
| **SQL Server** | < 50ms (avg query) | 100 queries/sec | 99.95% |
| **MongoDB** | < 30ms (avg read) | 500 operations/sec | 99.9% |
| **Redis** | < 1ms (cache hit) | 10,000 operations/sec | 99.9% |

---

## ✅ 6. Implementation Roadmap

### 6.1 Development Phases (12 สัปดาห์)

#### **Phase 1: Infrastructure Setup (Weeks 1-3)**
- ✅ Database setup (SQL Server + MongoDB + Redis)
- ✅ API Server basic structure
- ✅ Authentication implementation
- ✅ Basic CRUD operations

#### **Phase 2: Core Features (Weeks 4-6)**
- ✅ Agent Desktop App development
- ✅ WebSocket Server implementation
- ✅ Real-time status management
- ✅ Basic messaging system

#### **Phase 3: Advanced Features (Weeks 7-9)**
- ✅ Supervisor Web Dashboard
- ✅ Performance analytics
- ✅ Admin Panel development
- ✅ Report generation

#### **Phase 4: Testing & Deployment (Weeks 10-12)**
- ✅ Integration testing
- ✅ Performance optimization
- ✅ Security hardening
- ✅ Production deployment

### 6.2 Technology Rationale

#### **Why Node.js + Express?**
- **JavaScript Ecosystem:** ใช้ภาษาเดียวกันทั้ง frontend และ backend
- **Real-time Support:** ดีสำหรับ WebSocket และ event-driven applications
- **Rich Ecosystem:** NPM packages ครบครันสำหรับ rapid development
- **Student Friendly:** เรียนรู้ง่ายสำหรับนักศึกษา

#### **Why React?**
- **Component-based:** สร้าง reusable UI components
- **Large Community:** มี tutorial และ resources เยอะ
- **Industry Standard:** ใช้กันแพร่หลายในอุตสาหกรรม
- **Electron Compatible:** ใช้ได้ทั้ง web และ desktop

#### **Why SQL Server + MongoDB?**
- **Best of Both Worlds:** Structured data (SQL) + Flexible data (NoSQL)
- **Performance:** SQL สำหรับ ACID transactions, MongoDB สำหรับ real-time data
- **Scalability:** แต่ละ database optimized สำหรับ use case ที่แตกต่าง
- **Learning Opportunity:** นักศึกษาได้เรียนรู้ทั้ง SQL และ NoSQL

---

## 🚀 7. Summary และ Next Steps

### 7.1 Container Architecture Summary

**Agent Wallboard System** ประกอบด้วย **8 containers หลัก:**

#### **Frontend Tier (3 containers):**
🖥️ **Agent Desktop App** (Electron + React)  
🌐 **Supervisor Web App** (React + Material-UI)  
⚙️ **Admin Panel** (React + Admin Framework)  

#### **Backend Tier (2 containers):**
🔧 **API Server** (Node.js + Express)  
⚡ **WebSocket Server** (Socket.io)  

#### **Data Tier (3 containers):**
🗄️ **SQL Server** (Structured data)  
🍃 **MongoDB** (Real-time data)  
🔴 **Redis** (Cache + Sessions)  

### 7.2 Key Architecture Decisions

✅ **Separation of Concerns:** แยก UI, business logic, และ data layer ชัดเจน  
✅ **Technology Alignment:** ใช้ JavaScript ecosystem ทั้งหมดเพื่อความสอดคล้อง  
✅ **Scalability Ready:** ออกแบบให้รองรับการขยายระบบในอนาคต  
✅ **Student Implementable:** ใช้ technologies ที่นักศึกษาเรียนรู้ได้  
✅ **Production Ready:** มี security, monitoring, และ error handling  

### 7.3 Next Steps: C3 Component Diagram

การออกแบบ **C3 Component Diagram** ในขั้นต่อไปจะแสดง:

🧩 **Internal Components:** Controllers, Services, Repositories ภายในแต่ละ container  
🔧 **Design Patterns:** MVC, Repository Pattern, Service Layer  
📡 **Component Interactions:** Dependency injection, Event handling  
🗃️ **Data Access Layer:** ORMs, Database adapters, Caching strategies  

**C2 Container Diagram นี้เป็นพื้นฐานที่สมบูรณ์สำหรับการพัฒนาระบบจริง!** 🚀