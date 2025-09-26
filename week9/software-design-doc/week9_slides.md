# สัปดาห์ที่ 9: การออกแบบสถาปัตยกรรม - ขั้นสูง
## Low-Level Design & API Specifications

### หลักสูตร: ENGSE206 Software Requirements Specification and Design
### มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา (ดอยสะเก็ด)

---

## Slide 1: 🎯 ภาพรวมสัปดาห์ที่ 9
### การออกแบบสถาปัตยกรรม - ขั้นสูง

**🔥 จุดเด่นของสัปดาห์นี้:**
- **C4 Model Level 4 (Code)**: เข้าสู่รายละเอียดระดับโค้ด
- **UML Class & Sequence Diagrams**: แสดงโครงสร้างและการทำงาน
- **REST API Specifications**: เขียน OpenAPI/Swagger documentation
- **WebSocket Protocols**: ออกแบบ real-time communication
- **Database Schema Design**: ER Diagrams และ optimization

**🎯 เป้าหมายการเรียนรู้:**
```
Week 5: C1-C2 (System Context + Container) ✅
Week 6: Design Patterns ✅  
Week 7: C3 (Component Architecture) ✅
Week 9: C4 (Code Level) + Implementation Details ← เรียนที่นี่!
```

**📊 ความต่อเนื่องจากสัปดาห์ที่ผ่านมา:**
- สร้าง C1-C2 Architecture ✅
- เรียนรู้ Design Patterns ✅
- สร้าง C3 Component Design ✅
- เขียน API Phase 1-2 ✅

---

## Slide 2: 🎯 Learning Objectives
### วัตถุประสงค์การเรียนรู้

**หลังเรียนจบสัปดาห์นี้ นักศึกษาสามารถ:**

**🎯 Technical Skills:**
1. **ออกแบบ Class Diagrams** ที่แสดง relationships และ methods
2. **เขียน API Specifications** แบบมืออาชีพด้วย OpenAPI/Swagger
3. **ออกแบบ Database Schema** ที่รองรับ performance requirements
4. **สร้าง UI Mockups** สำหรับ Desktop และ Web Applications
5. **ออกแบบ WebSocket Protocols** สำหรับ real-time communication

**🛠️ Practical Skills:**
- เชื่อมต่อ Architecture Design กับ Implementation
- สร้าง Technical Documentation ที่ Developer ใช้งานได้จริง
- วิเคราะห์ Performance และ Scalability requirements
- ออกแบบ Error Handling และ Exception Management

**💼 Professional Skills:**
- สื่อสาร Technical Design กับทีม Development
- ทำ Code Review และ Architecture Review
- วางแผน Implementation Strategy

---

## Slide 3: 📋 สัปดาห์ที่ 9 Agenda
### แผนการเรียน 3 ชั่วโมง

**⏰ Hour 1 (50 นาที): C4 Code Level Design**
- ทบทวน C1-C3 Architecture
- C4 Model: Code Level Details
- UML Class Diagrams for Agent Wallboard
- Design Patterns Implementation

**⏰ Hour 2 (50 นาที): API & WebSocket Design** 
- REST API Specifications (OpenAPI/Swagger)
- WebSocket Protocol Design
- Error Handling Strategies
- Security Considerations

**⏰ Hour 3 (50 นาที): Database & UI Design**
- Database Schema Design (MSSQL + MongoDB)
- ER Diagrams และ Relationships
- UI Mockups (Desktop & Web)
- Performance & Scalability

**🎯 Workshop Activities:**
- สร้าง Complete Technical Specifications
- ออกแบบ Implementation-ready Documentation
- Team Review และ Feedback

---

## Slide 4: 🔄 บทสรุปสัปดาห์ที่ผ่านมา
### จุดเชื่อมต่อ Week 5-7 → Week 9

**📊 Week 5-7 Achievements:**

**✅ Week 5: High-Level Architecture**
```
Agent Wallboard System Overview:
- C1 System Context: Users + External Systems
- C2 Container Diagram: Desktop App, Web Dashboard, API Server
- 3-Tier Architecture: Presentation → Application → Data
```

**✅ Week 6: Design Patterns**
```
Key Patterns for Agent Wallboard:
- Publisher-Subscriber: Real-time status updates
- Observer Pattern: Event handling
- Factory Pattern: Component creation
- Singleton: WebSocket connection management
```

**✅ Week 7: Component Architecture**
```
C3 Component Design:
- Authentication Components
- Status Management Components
- Message Communication Components
- Dashboard Components
```

**🎯 Week 9 Goal:**
**จาก High-level Design สู่ Implementation-ready Specifications**

---

## Slide 5: 🏗️ C4 Model Review: Lower View Architecture
### From Abstract to Concrete

**🎯 C4 Model Progression:**

```
C1: System Context     (WHO uses the system?)
    ↓
C2: Container Diagram  (WHAT applications exist?)
    ↓  
C3: Component Diagram  (HOW are containers structured?)
    ↓
C4: Code Diagram      (DETAILS of implementation)
```

**📊 Agent Wallboard System Architecture Journey:**

```
Week 5: [C1] Agent System ↔ Users, MSSQL, External APIs
        [C2] Desktop App ↔ API Server ↔ Database
        
Week 7: [C3] API Server = Auth + Status + WebSocket + Message Components
        
Week 9: [C4] AuthService.authenticate(credentials) → JWT Token
             StatusService.updateAgentStatus(agentId, status) → Events
             WebSocketManager.broadcast(event) → Connected Clients
```

**🔍 สิ่งที่เพิ่มขึ้นใน Week 9:**
- Method signatures และ parameters
- Data structures และ interfaces
- Error handling mechanisms
- Performance considerations

---

## Slide 6: 📊 C4 Code Level: Class Diagrams 
### UML Class Diagrams สำหรับ Agent Wallboard System

**🎯 วัตถุประสงค์ของ Class Diagrams:**
- แสดง **โครงสร้าง classes** และ **relationships**
- ระบุ **methods, properties, และ data types**
- เป็น **blueprint สำหรับ developers**

### **Example: Authentication Component Class Design**

```typescript
┌─────────────────────────────┐
│        AuthService          │
├─────────────────────────────┤
│ - jwtSecret: string         │
│ - tokenExpiry: number       │
│ - activeUsers: Map<string>  │
├─────────────────────────────┤
│ + authenticate(credentials) │
│ + generateToken(user)       │
│ + validateToken(token)      │
│ + logout(userId)            │
│ + refreshToken(token)       │
└─────────────────────────────┘
             │
             ├──implements──► IAuthService
             │
             ▼
┌─────────────────────────────┐
│          User               │
├─────────────────────────────┤
│ + id: string                │
│ + username: string          │
│ + email: string             │
│ + department: string        │
│ + role: UserRole            │
│ + isActive: boolean         │
├─────────────────────────────┤
│ + validatePassword()        │
│ + updateLastLogin()         │
└─────────────────────────────┘
```

**🔗 Key Relationships:**
- **Composition**: AuthService *owns* User objects
- **Implementation**: AuthService implements IAuthService interface
- **Association**: AuthService *uses* DatabaseConnection

---

## Slide 7: 🎯 Core Class Diagrams: Agent Management
### ออกแบบ Classes สำหรับ Agent Management Component

**📋 Agent Management System Classes:**

```typescript
┌─────────────────────────────┐      ┌─────────────────────────────┐
│     AgentStatusService      │      │          Agent              │
├─────────────────────────────┤      ├─────────────────────────────┤
│ - agents: Map<string,Agent> │◄────►│ + id: string                │
│ - statusHistory: Status[]   │      │ + agentCode: string         │
│ - eventBus: EventBus        │      │ + name: string              │
├─────────────────────────────┤      │ + email: string             │
│ + updateStatus(id, status)  │      │ + department: Department    │
│ + getAgentStatus(id)        │      │ + skills: string[]          │
│ + getAgentsByStatus(status) │      │ + status: AgentStatus       │
│ + getStatusHistory(id)      │      │ + isOnline: boolean         │
│ + broadcastStatusChange()   │      │ + lastStatusChange: Date    │
└─────────────────────────────┘      ├─────────────────────────────┤
             │                       │ + changeStatus(newStatus)   │
             │                       │ + validate()                │
             │                       │ + toJSON()                  │
             ▼                       └─────────────────────────────┘
┌─────────────────────────────┐                    │
│       AgentStatus           │                    │
├─────────────────────────────┤                    │
│ + AVAILABLE = "Available"   │◄───────────────────┘
│ + BUSY = "Busy"             │
│ + WRAP = "Wrap"             │      ┌─────────────────────────────┐
│ + BREAK = "Break"           │      │       StatusHistory         │
│ + NOT_READY = "Not Ready"   │      ├─────────────────────────────┤
│ + OFFLINE = "Offline"       │      │ + id: string                │
└─────────────────────────────┘      │ + agentId: string           │
                                     │ + previousStatus: string    │
                                     │ + newStatus: string         │
                                     │ + timestamp: Date           │
                                     │ + reason?: string           │
                                     │ + duration?: number         │
                                     └─────────────────────────────┘
```

**🎯 Design Principles ที่ใช้:**
1. **Single Responsibility**: แต่ละ class มีหน้าที่เฉพาะ
2. **Open/Closed**: เพิ่ม AgentStatus ใหม่ได้ง่าย  
3. **Interface Segregation**: แยก interfaces ตามการใช้งาน
4. **Dependency Injection**: EventBus injected เข้า Service

---

## Slide 8: 🔄 UML Sequence Diagrams
### แสดงการทำงานของระบบ Real-time

**🎯 Sequence Diagram: Agent Status Update Flow**

```
Desktop App    API Server     WebSocket     Database     Other Clients
     │              │             │            │              │
     │─────[1]─────►│             │            │              │
     │  PATCH /agents │             │            │              │
     │  /123/status   │             │            │              │
     │              │             │            │              │
     │              │─────[2]─────►│            │              │
     │              │  Validate    │            │              │
     │              │  Request     │            │              │
     │              │             │            │              │
     │              │──────────[3]──────────►│              │
     │              │     UPDATE agents      │              │
     │              │     SET status=Busy    │              │
     │              │             │            │              │
     │              │◄─────────[4]───────────│              │
     │              │     Success            │            │
     │              │             │            │              │
     │◄────[5]──────│             │            │              │
     │  200 OK      │             │            │              │
     │  Updated     │             │            │              │
     │              │             │            │              │
     │              │─────[6]─────►│            │              │
     │              │  Broadcast   │            │              │
     │              │  Event       │            │              │
     │              │             │            │              │
     │              │             │─────[7]────────────────►│
     │              │             │  agentStatusChanged    │
     │              │             │  { agentId, status }   │
```

**📊 Key Points:**
1. **Synchronous**: HTTP Request-Response (steps 1-5)
2. **Asynchronous**: WebSocket broadcast (steps 6-7)  
3. **Error Handling**: วิธีจัดการเมื่อ database update ล้มเหลว
4. **Real-time**: Supervisor dashboard อัปเดตทันที

---

## Slide 9: 🌐 REST API Specifications
### OpenAPI/Swagger Documentation

**🎯 Professional API Documentation:**

```yaml
openapi: 3.0.3
info:
  title: Agent Wallboard API
  description: Professional API for Call Center Agent Management
  version: 2.0.0
  contact:
    name: Development Team
    email: dev@company.com

servers:
  - url: http://localhost:3001/api
    description: Development Server
  - url: https://api-prod.wallboard.com/api  
    description: Production Server

paths:
  /agents:
    get:
      summary: List all agents
      description: Retrieve paginated list of agents with filtering
      parameters:
        - name: status
          in: query
          description: Filter by agent status
          schema:
            type: string
            enum: [Available, Busy, Wrap, Break, Not Ready, Offline]
        - name: department
          in: query
          description: Filter by department
          schema:
            type: string
            enum: [Sales, Support, Technical, General]
        - name: page
          in: query
          description: Page number for pagination
          schema:
            type: integer
            minimum: 1
            default: 1
        - name: limit
          in: query
          description: Items per page
          schema:
            type: integer
            minimum: 1
            maximum: 100
            default: 20
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                type: object
                properties:
                  success:
                    type: boolean
                  message:
                    type: string
                  count:
                    type: integer
                  totalPages:
                    type: integer
                  currentPage:
                    type: integer
                  data:
                    type: array
                    items:
                      $ref: '#/components/schemas/Agent'
```

---

## Slide 10: 📱 API Design: CRUD Operations
### Complete Agent Management APIs

**🔧 Agent Management Endpoints:**

```yaml
# POST /api/agents - Create Agent
requestBody:
  required: true
  content:
    application/json:
      schema:
        type: object
        required: [agentCode, name, email, department]
        properties:
          agentCode:
            type: string
            pattern: '^A[0-9]{3}$'
            example: 'A001'
          name:
            type: string
            minLength: 2
            maxLength: 100
            example: 'John Doe'
          email:
            type: string
            format: email
            example: 'john.doe@company.com'
          department:
            type: string
            enum: [Sales, Support, Technical, General]
          skills:
            type: array
            items:
              type: string
            example: ['Thai', 'English', 'Sales']

responses:
  '201':
    description: Agent created successfully
    content:
      application/json:
        schema:
          type: object
          properties:
            success:
              type: boolean
              example: true
            message:
              type: string
              example: 'Agent created successfully'
            data:
              $ref: '#/components/schemas/Agent'
  '400':
    description: Validation error
    content:
      application/json:
        schema:
          $ref: '#/components/schemas/ValidationError'
  '409':
    description: Agent code already exists
    content:
      application/json:
        schema:
          $ref: '#/components/schemas/ConflictError'
```

---

## Slide 11: ⚡ WebSocket Protocol Design
### Real-time Communication Specifications

**🔌 WebSocket Events Architecture:**

```typescript
// Client → Server Events
interface ClientEvents {
  // Agent Desktop App Events
  'agent-login': {
    agentId: string;
    agentCode: string;
    timestamp: Date;
  };
  
  'agent-logout': {
    agentId: string;
    reason?: string;
  };
  
  'status-change-request': {
    agentId: string;
    newStatus: AgentStatus;
    reason?: string;
  };
  
  // Supervisor Dashboard Events
  'join-dashboard': {
    supervisorId: string;
    department?: string;
  };
  
  'broadcast-message': {
    from: string;
    to: string | string[]; // Single agent or multiple
    message: string;
    type: 'message' | 'alert' | 'notification';
    priority: 'low' | 'normal' | 'high' | 'urgent';
  };
}

// Server → Client Events  
interface ServerEvents {
  'connection-established': {
    clientId: string;
    serverTime: Date;
    supportedFeatures: string[];
  };
  
  'agent-status-changed': {
    agentId: string;
    agentCode: string;
    previousStatus: AgentStatus;
    newStatus: AgentStatus;
    timestamp: Date;
    reason?: string;
  };
  
  'new-message': {
    messageId: string;
    from: string;
    to: string;
    message: string;
    type: string;
    priority: string;
    timestamp: Date;
  };
  
  'dashboard-update': {
    totalAgents: number;
    statusSummary: Record<AgentStatus, number>;
    departmentSummary: Record<string, number>;
    timestamp: Date;
  };
  
  'agent-online': {
    agentId: string;
    agentCode: string;
    name: string;
    timestamp: Date;
  };
  
  'agent-offline': {
    agentId: string;
    agentCode: string;
    lastSeen: Date;
  };
}
```

---

## Slide 12: 🔒 Security & Error Handling
### Production-Ready API Security

**🛡️ Security Considerations:**

```typescript
// Authentication & Authorization
interface SecurityMiddleware {
  // JWT Token Validation
  authenticateToken(req: Request, res: Response, next: NextFunction): void;
  
  // Role-based Access Control
  authorizeRole(roles: UserRole[]): MiddlewareFunction;
  
  // Rate Limiting
  rateLimiter: {
    windowMs: number;
    maxRequests: number;
    skipSuccessfulRequests: boolean;
  };
  
  // Input Validation & Sanitization
  validateInput(schema: JoiSchema): MiddlewareFunction;
  sanitizeInput(): MiddlewareFunction;
  
  // CORS Configuration
  corsOptions: {
    origin: string | string[];
    credentials: boolean;
    optionsSuccessStatus: number;
  };
}

// Error Handling Strategy
class APIError extends Error {
  constructor(
    public statusCode: number,
    public message: string,
    public code?: string,
    public details?: any
  ) {
    super(message);
    this.name = 'APIError';
  }
}

// Standardized Error Responses
interface ErrorResponse {
  success: false;
  error: {
    code: string;
    message: string;
    details?: any;
    timestamp: Date;
    path: string;
    requestId?: string;
  };
}

// Example Error Responses
const errorExamples = {
  validation: {
    statusCode: 400,
    body: {
      success: false,
      error: {
        code: 'VALIDATION_FAILED',
        message: 'Request validation failed',
        details: [
          {
            field: 'agentCode',
            message: 'Agent code must follow format A001'
          }
        ],
        timestamp: '2025-01-15T10:30:00Z',
        path: '/api/agents'
      }
    }
  },
  
  authorization: {
    statusCode: 403,
    body: {
      success: false,
      error: {
        code: 'INSUFFICIENT_PERMISSIONS',
        message: 'User does not have permission to perform this action',
        timestamp: '2025-01-15T10:30:00Z',
        path: '/api/agents/123/status'
      }
    }
  }
};
```

---

## Slide 13: 🗄️ Database Schema Design
### MSSQL + MongoDB Hybrid Architecture

**🎯 Database Strategy:**
- **MSSQL**: Master data, relationships, consistency
- **MongoDB**: Event logs, real-time data, flexibility

### **MSSQL Schema (Master Data):**

```sql
-- Agents Table (Master Data)
CREATE TABLE Agents (
    ID UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(),
    AgentCode NVARCHAR(10) NOT NULL UNIQUE,
    Name NVARCHAR(100) NOT NULL,
    Email NVARCHAR(100) NOT NULL UNIQUE,
    Department NVARCHAR(50) NOT NULL,
    IsActive BIT NOT NULL DEFAULT 1,
    CreatedDate DATETIME2 NOT NULL DEFAULT GETUTCDATE(),
    ModifiedDate DATETIME2 NOT NULL DEFAULT GETUTCDATE(),
    
    INDEX IX_Agents_AgentCode (AgentCode),
    INDEX IX_Agents_Department (Department),
    INDEX IX_Agents_IsActive (IsActive)
);

-- Agent Skills (Many-to-Many)
CREATE TABLE AgentSkills (
    ID UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(),
    AgentID UNIQUEIDENTIFIER NOT NULL,
    Skill NVARCHAR(50) NOT NULL,
    ProficiencyLevel TINYINT DEFAULT 1, -- 1-5 scale
    
    FOREIGN KEY (AgentID) REFERENCES Agents(ID) ON DELETE CASCADE,
    UNIQUE (AgentID, Skill)
);

-- User Authentication
CREATE TABLE Users (
    ID UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(),
    Username NVARCHAR(50) NOT NULL UNIQUE,
    PasswordHash NVARCHAR(255) NOT NULL,
    Role NVARCHAR(20) NOT NULL DEFAULT 'Agent',
    AgentID UNIQUEIDENTIFIER NULL,
    LastLoginDate DATETIME2 NULL,
    IsActive BIT NOT NULL DEFAULT 1,
    
    FOREIGN KEY (AgentID) REFERENCES Agents(ID),
    INDEX IX_Users_Username (Username),
    INDEX IX_Users_Role (Role)
);

-- Departments Reference
CREATE TABLE Departments (
    ID UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(),
    Name NVARCHAR(50) NOT NULL UNIQUE,
    Description NVARCHAR(200),
    ManagerID UNIQUEIDENTIFIER NULL,
    IsActive BIT NOT NULL DEFAULT 1,
    
    FOREIGN KEY (ManagerID) REFERENCES Users(ID)
);
```

---

## Slide 14: 📊 MongoDB Schema Design
### Event-Driven Data Storage

```javascript
// MongoDB Collections for Real-time Data

// 1. Agent Status History (Time-series data)
const agentStatusHistorySchema = {
  _id: ObjectId,
  agentId: String,        // Reference to MSSQL Agents.ID
  agentCode: String,      // For quick lookups
  previousStatus: String,
  newStatus: String,
  timestamp: Date,
  reason: String,         // Optional reason for status change
  duration: Number,       // Duration in previous status (seconds)
  sessionId: String,      // Desktop app session ID
  metadata: {
    ipAddress: String,
    userAgent: String,
    location: String
  }
};

// Indexes for performance
db.agentStatusHistory.createIndex({ agentId: 1, timestamp: -1 });
db.agentStatusHistory.createIndex({ timestamp: -1 });
db.agentStatusHistory.createIndex({ agentCode: 1 });

// 2. Messages Collection
const messagesSchema = {
  _id: ObjectId,
  from: String,           // Sender (agentCode or supervisorId)
  to: [String],          // Recipients (array for broadcast)
  message: String,
  type: String,          // 'message', 'alert', 'notification'
  priority: String,      // 'low', 'normal', 'high', 'urgent'
  timestamp: Date,
  readBy: [{
    agentId: String,
    readTimestamp: Date
  }],
  status: String,        // 'sent', 'delivered', 'read'
  metadata: {
    department: String,
    category: String,
    attachments: []
  }
};

// 3. WebSocket Sessions (Active connections)
const webSocketSessionsSchema = {
  _id: ObjectId,
  sessionId: String,     // Unique session identifier
  userId: String,        // agentId or supervisorId
  userType: String,      // 'agent' or 'supervisor'
  connectedAt: Date,
  lastActivity: Date,
  ipAddress: String,
  status: String,        // 'connected', 'idle', 'disconnected'
  metadata: {
    browser: String,
    version: String,
    features: [String]
  }
};

// 4. System Events Log
const systemEventsSchema = {
  _id: ObjectId,
  eventType: String,     // 'login', 'logout', 'statusChange', 'message'
  entityType: String,    // 'agent', 'supervisor', 'system'
  entityId: String,
  timestamp: Date,
  details: Object,       // Flexible event details
  severity: String,      // 'info', 'warning', 'error', 'critical'
  processed: Boolean,    // For event processing workflows
  retryCount: Number
};
```

---

## Slide 15: 🎨 UI Mockups: Desktop Application
### Electron.js Agent Desktop Interface

**🖥️ Agent Desktop Application Design:**

```
┌─────────────────────────────────────────────────────────────┐
│ Agent Wallboard - A001 - John Doe                    [- □ ×]│
├─────────────────────────────────────────────────────────────┤
│ File  View  Tools  Help                          🔌 Online   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌─ Agent Status ──────────────────────────────────────────┐│
│  │                                                         ││
│  │   Current Status: [🟢 Available    ▼] [Change Status]   ││
│  │                                                         ││
│  │   ⏱️  Duration: 00:15:32                                ││
│  │   📊  Today: Available(4h) | Busy(2h) | Break(45m)     ││
│  │                                                         ││
│  └─────────────────────────────────────────────────────────────┘
```

**🎯 Key UI Features:**
- **Real-time Status Display**: แสดงสถานะปัจจุบันและระยะเวลา
- **Message Center**: รับ-ส่งข้อความแบบ real-time
- **Quick Actions**: เปลี่ยนสถานะด้วยปุ่มเดียว
- **Statistics**: สรุปสถิติการทำงานรายวัน
- **Connection Status**: แสดงสถานะการเชื่อมต่อแบบ real-time

---

## Slide 16: 🌐 UI Mockups: Web Dashboard
### React.js Supervisor Dashboard

**💻 Supervisor/Manager Web Dashboard:**

```
┌─────────────────────────────────────────────────────────────────────┐
│ 🏢 Agent Wallboard Dashboard                        👤 Manager1 ▼   │
├─────────────────────────────────────────────────────────────────────┤
│ 📊 Dashboard | 👥 Agents | 💬 Messages | 📈 Reports | ⚙️ Settings    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│ ┌─ Real-time Status Overview ─────────────────────────────────────┐ │
│ │                                                                 │ │
│ │  🟢 Available: 12    🔴 Busy: 8      🟡 Wrap: 3               │ │
│ │  🟠 Break: 2         ⚫ Offline: 5   📊 Total: 30             │ │
│ │                                                                 │ │
│ │  📈 Real-time Chart: [████▆▅▇██▆▅] (Last 60 minutes)          │ │
│ │                                                                 │ │
│ └─────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│ ┌─ Agent Status Grid ─────────────────────────────────────────────┐ │
│ │                                                                 │ │
│ │ Filter: [All Departments ▼] [All Status ▼] [🔍 Search...]     │ │
│ │                                                                 │ │
│ │ Agent    Name          Dept     Status      Duration   Actions │ │
│ │ ──────────────────────────────────────────────────────────────  │ │
│ │ A001 🟢  John Doe      Sales    Available   00:15:32   [💬][📊] │ │
│ │ A002 🔴  Jane Smith    Support  Busy        01:23:45   [💬][📊] │ │
│ │ A003 🟡  Mike Johnson  Tech     Wrap        00:03:12   [💬][📊] │ │
│ │ A004 🟠  Lisa Brown    Sales    Break       00:08:30   [💬][📊] │ │
│ │ A005 🟢  Tom Wilson    Support  Available   00:45:22   [💬][📊] │ │
│ │                                                                 │ │
│ │ ⏮️ Previous  1 2 3 4 5 Next ⏭️                      (30 total) │ │
│ │                                                                 │ │
│ └─────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│ ┌─ Broadcast Message ─────────────────────────────────────────────┐ │
│ │                                                                 │ │
│ │ Send To: [🎯 Select Agents ▼]  Priority: [Normal ▼]           │ │
│ │                                                                 │ │
│ │ ┌─ Message ───────────────────────────────────────────────────┐ │ │
│ │ │ Please check your queue for priority tickets...             │ │ │
│ │ │                                                             │ │ │
│ │ │                                                             │ │ │
│ │ └─────────────────────────────────────────────────────────────┘ │ │
│ │                                                                 │ │
│ │                          [📤 Send Message] [📋 Save Template]   │ │
│ │                                                                 │ │
│ └─────────────────────────────────────────────────────────────────┘ │
│                                                                     │
├─────────────────────────────────────────────────────────────────────┤
│ 🔌 Real-time • 30 agents connected • Last update: 10:45:24 AM      │
└─────────────────────────────────────────────────────────────────────┘
```

**🎯 Dashboard Key Features:**
- **Real-time Status Overview**: แสดงสถิติแบบ real-time
- **Agent Grid**: ตารางข้อมูล agent ที่อัปเดตแบบ live
- **Filtering & Search**: กรองข้อมูลตามแผนก/สถานะ
- **Broadcast Messaging**: ส่งข้อความหาหลายคนพร้อมกัน
- **Individual Actions**: ส่งข้อความส่วนตัวหรือดูสถิติ

---

## Slide 17: 🔧 Component Integration Pattern
### การเชื่อมต่อ Components แบบมืออาชีพ

**🎯 Integration Architecture Pattern:**

```typescript
// 1. Service Layer Pattern (Business Logic)
interface IAgentService {
  getAgents(filter?: AgentFilter): Promise<Agent[]>;
  updateAgentStatus(id: string, status: AgentStatus): Promise<Agent>;
  getAgentHistory(id: string): Promise<StatusHistory[]>;
}

class AgentService implements IAgentService {
  constructor(
    private database: IDatabase,
    private websocket: IWebSocketService,
    private eventBus: IEventBus
  ) {}
  
  async updateAgentStatus(id: string, status: AgentStatus): Promise<Agent> {
    // 1. Validate business rules
    const agent = await this.database.findAgent(id);
    if (!this.canTransitionTo(agent.status, status)) {
      throw new BusinessLogicError('Invalid status transition');
    }
    
    // 2. Update database
    const updatedAgent = await this.database.updateAgentStatus(id, status);
    
    // 3. Log to history (MongoDB)
    await this.database.logStatusChange({
      agentId: id,
      previousStatus: agent.status,
      newStatus: status,
      timestamp: new Date()
    });
    
    // 4. Broadcast event
    this.websocket.broadcast('agent-status-changed', {
      agentId: id,
      agentCode: updatedAgent.agentCode,
      previousStatus: agent.status,
      newStatus: status,
      timestamp: new Date()
    });
    
    // 5. Emit business event
    this.eventBus.emit('agent.status.updated', updatedAgent);
    
    return updatedAgent;
  }
}

// 2. Repository Pattern (Data Access)
interface IAgentRepository {
  findById(id: string): Promise<Agent>;
  findByStatus(status: AgentStatus): Promise<Agent[]>;
  update(id: string, data: Partial<Agent>): Promise<Agent>;
  create(agent: CreateAgentRequest): Promise<Agent>;
}

class AgentRepository implements IAgentRepository {
  constructor(private db: IDatabase) {}
  
  async findById(id: string): Promise<Agent> {
    const result = await this.db.query(
      'SELECT * FROM Agents WHERE ID = ?', [id]
    );
    return this.mapToAgent(result[0]);
  }
}

// 3. Event-Driven Architecture
class EventBus implements IEventBus {
  private handlers: Map<string, Function[]> = new Map();
  
  emit(event: string, data: any): void {
    const handlers = this.handlers.get(event) || [];
    handlers.forEach(handler => handler(data));
  }
  
  on(event: string, handler: Function): void {
    const handlers = this.handlers.get(event) || [];
    handlers.push(handler);
    this.handlers.set(event, handlers);
  }
}

// 4. Dependency Injection Container
class DIContainer {
  private services: Map<string, any> = new Map();
  
  register<T>(name: string, implementation: T): void {
    this.services.set(name, implementation);
  }
  
  resolve<T>(name: string): T {
    return this.services.get(name);
  }
}
```

---

## Slide 18: 🚀 Performance Optimization Strategy
### การออกแบบสำหรับ High Performance

**🎯 Performance Considerations:**

```typescript
// 1. Database Optimization
class DatabaseOptimization {
  // Connection Pooling
  private connectionPool = {
    min: 5,
    max: 20,
    acquireTimeoutMillis: 30000,
    idleTimeoutMillis: 600000
  };
  
  // Query Optimization
  async getAgentsByDepartment(department: string): Promise<Agent[]> {
    // Use indexed query
    return this.db.query(`
      SELECT a.*, COUNT(sh.ID) as status_changes_today
      FROM Agents a
      LEFT JOIN StatusHistory sh ON a.ID = sh.AgentID 
        AND sh.Timestamp >= CONVERT(date, GETUTCDATE())
      WHERE a.Department = @department AND a.IsActive = 1
      GROUP BY a.ID, a.AgentCode, a.Name, a.Email, a.Department
      ORDER BY a.AgentCode
    `, { department });
  }
  
  // Caching Strategy
  @Cache(300) // Cache for 5 minutes
  async getAgentStatusSummary(): Promise<StatusSummary> {
    return this.db.query(`
      SELECT Status, COUNT(*) as Count
      FROM Agents a
      JOIN CurrentStatus cs ON a.ID = cs.AgentID
      WHERE a.IsActive = 1
      GROUP BY Status
    `);
  }
}

// 2. WebSocket Optimization
class WebSocketOptimization {
  private rooms: Map<string, Set<string>> = new Map();
  
  // Room-based broadcasting (reduce unnecessary traffic)
  broadcastToDepartment(department: string, event: string, data: any): void {
    const room = this.rooms.get(`department:${department}`);
    if (room) {
      room.forEach(socketId => {
        this.io.to(socketId).emit(event, data);
      });
    }
  }
  
  // Rate limiting for messages
  @RateLimit(100, 60000) // 100 messages per minute
  async sendMessage(from: string, to: string, message: string): Promise<void> {
    // Implementation
  }
  
  // Message compression
  setupCompression(): void {
    this.io.engine.generateId = () => {
      return uuid().substring(0, 8); // Shorter IDs
    };
    
    this.io.compression(true);
  }
}

// 3. Frontend Optimization
class FrontendOptimization {
  // Virtual scrolling for large agent lists
  private virtualScrollConfig = {
    itemHeight: 60,
    containerHeight: 400,
    bufferSize: 10
  };
  
  // Debounced search
  @Debounce(300)
  searchAgents(query: string): void {
    this.agentService.search(query);
  }
  
  // Memory management
  componentWillUnmount(): void {
    this.websocket.disconnect();
    this.subscriptions.forEach(sub => sub.unsubscribe());
  }
}

// 4. Monitoring & Metrics
class PerformanceMonitoring {
  @Metric('api.response.time')
  async handleRequest(req: Request, res: Response): Promise<void> {
    const start = Date.now();
    
    try {
      // Process request
      await this.processRequest(req, res);
    } finally {
      const duration = Date.now() - start;
      this.metrics.record('api.response.time', duration);
      
      if (duration > 1000) {
        this.logger.warn(`Slow request: ${req.path} took ${duration}ms`);
      }
    }
  }
}
```

---

## Slide 19: 🔍 Testing Strategy
### การทดสอบแบบครอบคลุม

**🧪 Comprehensive Testing Approach:**

```typescript
// 1. Unit Testing (Jest + TypeScript)
describe('AgentService', () => {
  let service: AgentService;
  let mockDatabase: jest.Mocked<IDatabase>;
  let mockWebSocket: jest.Mocked<IWebSocketService>;
  
  beforeEach(() => {
    mockDatabase = {
      findAgent: jest.fn(),
      updateAgentStatus: jest.fn(),
      logStatusChange: jest.fn()
    } as any;
    
    mockWebSocket = {
      broadcast: jest.fn()
    } as any;
    
    service = new AgentService(mockDatabase, mockWebSocket, mockEventBus);
  });
  
  describe('updateAgentStatus', () => {
    it('should update agent status successfully', async () => {
      // Arrange
      const agentId = 'test-id';
      const newStatus = AgentStatus.BUSY;
      const existingAgent = { id: agentId, status: AgentStatus.AVAILABLE };
      
      mockDatabase.findAgent.mockResolvedValue(existingAgent);
      mockDatabase.updateAgentStatus.mockResolvedValue({
        ...existingAgent,
        status: newStatus
      });
      
      // Act
      const result = await service.updateAgentStatus(agentId, newStatus);
      
      // Assert
      expect(result.status).toBe(newStatus);
      expect(mockDatabase.updateAgentStatus).toHaveBeenCalledWith(
        agentId, 
        newStatus
      );
      expect(mockWebSocket.broadcast).toHaveBeenCalledWith(
        'agent-status-changed',
        expect.objectContaining({
          agentId,
          newStatus
        })
      );
    });
    
    it('should throw error for invalid status transition', async () => {
      // Arrange
      const agent = { id: 'test-id', status: AgentStatus.OFFLINE };
      mockDatabase.findAgent.mockResolvedValue(agent);
      
      // Act & Assert
      await expect(
        service.updateAgentStatus('test-id', AgentStatus.WRAP)
      ).rejects.toThrow('Invalid status transition');
    });
  });
});

// 2. Integration Testing
describe('API Integration Tests', () => {
  let app: Express;
  let testDb: TestDatabase;
  
  beforeAll(async () => {
    testDb = await setupTestDatabase();
    app = createTestApp(testDb);
  });
  
  afterAll(async () => {
    await testDb.cleanup();
  });
  
  describe('GET /api/agents', () => {
    it('should return all agents with pagination', async () => {
      // Arrange
      await testDb.seed('agents', agentTestData);
      
      // Act
      const response = await request(app)
        .get('/api/agents?page=1&limit=10')
        .expect(200);
      
      // Assert
      expect(response.body.success).toBe(true);
      expect(response.body.data).toHaveLength(10);
      expect(response.body.totalPages).toBeGreaterThan(0);
    });
  });
  
  describe('WebSocket Events', () => {
    it('should broadcast status change events', (done) => {
      const client = io('http://localhost:3001');
      
      client.on('agent-status-changed', (data) => {
        expect(data.agentId).toBeDefined();
        expect(data.newStatus).toBe('Busy');
        client.disconnect();
        done();
      });
      
      // Trigger status change via API
      request(app)
        .patch('/api/agents/test-id/status')
        .send({ status: 'Busy' })
        .expect(200);
    });
  });
});

// 3. End-to-End Testing (Playwright)
import { test, expect } from '@playwright/test';

test.describe('Agent Desktop Application', () => {
  test('agent can change status and see real-time updates', async ({ page }) => {
    // Navigate to desktop app
    await page.goto('http://localhost:3000');
    
    // Login as agent
    await page.fill('[data-testid="agent-code"]', 'A001');
    await page.fill('[data-testid="password"]', 'password');
    await page.click('[data-testid="login-button"]');
    
    // Verify dashboard is loaded
    await expect(page.locator('[data-testid="agent-dashboard"]')).toBeVisible();
    
    // Change status
    await page.selectOption('[data-testid="status-dropdown"]', 'Busy');
    await page.click('[data-testid="change-status-button"]');
    
    // Verify status updated
    await expect(page.locator('[data-testid="current-status"]')).toContainText('Busy');
    
    // Verify message appears in supervisor dashboard (second browser context)
    const supervisorPage = await page.context().newPage();
    await supervisorPage.goto('http://localhost:3001/dashboard');
    
    await expect(supervisorPage.locator('[data-testid="agent-A001-status"]')).toContainText('Busy');
  });
});

// 4. Performance Testing
describe('Performance Tests', () => {
  test('API should handle concurrent requests', async () => {
    const concurrentRequests = 100;
    const promises = Array.from({ length: concurrentRequests }, () => 
      request(app).get('/api/agents').expect(200)
    );
    
    const start = Date.now();
    await Promise.all(promises);
    const duration = Date.now() - start;
    
    expect(duration).toBeLessThan(5000); // Should complete within 5 seconds
  });
  
  test('WebSocket should handle many concurrent connections', async () => {
    const connections = Array.from({ length: 50 }, () => 
      io('http://localhost:3001')
    );
    
    // All should connect successfully
    await Promise.all(connections.map(client => 
      new Promise(resolve => client.on('connect', resolve))
    ));
    
    connections.forEach(client => client.disconnect());
  });
});
```

---

## Slide 20: 📋 Implementation Checklist
### การเตรียมพร้อมสำหรับ Development

**✅ Development Readiness Checklist:**

### **🎯 Architecture & Design (Week 9 Deliverables):**
```
□ C4 Code Level Diagrams completed
□ UML Class Diagrams with relationships
□ UML Sequence Diagrams for key workflows  
□ REST API OpenAPI/Swagger specification
□ WebSocket event protocols defined
□ Database schema (MSSQL + MongoDB)
□ UI Mockups (Desktop + Web Dashboard)
□ Error handling strategy documented
□ Security requirements specified
□ Performance benchmarks defined
```

### **🛠️ Technical Infrastructure:**
```
□ Development environment setup
□ Git repository with branching strategy
□ CI/CD pipeline configuration
□ Database migration scripts
□ API testing suite (Postman/Newman)
□ Code quality tools (ESLint, Prettier)
□ Documentation generation setup
□ Monitoring & logging configuration
□ Deployment scripts & Docker configuration
□ Security scanning tools
```

### **👥 Team Coordination:**
```
□ Development team roles assigned
□ Code review process established
□ Sprint planning completed
□ Definition of Done criteria
□ Communication channels setup
□ Issue tracking system configured
□ Knowledge sharing sessions scheduled
□ Quality assurance processes
□ User acceptance testing plan
□ Go-live checklist prepared
```

### **📊 Quality Assurance:**
```
□ Unit testing framework setup
□ Integration testing environment
□ End-to-end testing scripts
□ Performance testing tools
□ Security testing procedures
□ User acceptance testing plan
□ Bug tracking and resolution process
□ Code coverage targets defined
□ Load testing scenarios
□ Disaster recovery procedures
```

---

## Slide 21: 🎪 Workshop Activity: Complete Implementation Design
### การออกแบบ Implementation ที่สมบูรณ์

**🚀 Workshop Goal:**
สร้าง **Complete Implementation-Ready Design** สำหรับ Agent Wallboard System

### **⏰ Activity Timeline (150 นาที):**

**Part 1: Class Design Workshop (50 นาที)**
```
🎯 Individual Work (20 นาที):
- เลือก 1 Component จาก C3 Architecture
- วาด UML Class Diagram พร้อม methods และ attributes
- ระบุ relationships และ dependencies

🤝 Team Review (20 นาที):  
- รวม Class Diagrams จากสมาชิกทีม
- ตรวจสอบ consistency และ naming conventions
- แก้ไข conflicts และ overlapping responsibilities

📋 Presentation Prep (10 นาที):
- เตรียม 3-minute presentation
- สรุป key design decisions
```

**Part 2: API Design Workshop (50 นาที)**
```
🎯 Team Work (30 นาที):
- เลือก 2-3 API endpoints สำคัญ
- เขียน OpenAPI specification (YAML format)
- ระบุ request/response schemas
- ออกแบบ error handling

🔍 Cross-team Review (15 นาที):
- แลกเปลี่ยนกับทีมอื่น
- ตรวจสอบ API consistency
- ให้ feedback และรับ feedback

📝 Documentation (5 นาที):
- Complete API documentation
- Add examples และ use cases
```

**Part 3: Integration Design (50 นาที)**
```
🎯 Complete System Design (40 นาที):
- รวม Class Diagrams + API Specs + Database Schema
- สร้าง Sequence Diagram สำหรับ 1 key scenario
- ตรวจสอบ end-to-end flow

🏆 Final Presentation (10 นาที):
- Each team: 3-minute presentation
- แสดง complete design package
- รับ feedback จากอาจารย์และเพื่อน
```

### **📊 Workshop Deliverables:**
1. **UML Class Diagram** (exported from Draw.io/Lucidchart)
2. **API Specification** (OpenAPI YAML file)
3. **Sequence Diagram** (1 key workflow)
4. **Integration Summary** (1-page document)

---

## Slide 22: 🎯 Workshop Teams & Assignments
### การแบ่งทีมและหน้าที่

**👥 Team Formation (4-5 คนต่อทีม):**

### **Team A: Frontend Components**
```
🎯 Focus Areas:
- Desktop Application (Electron.js) Classes
- Agent Status Management Components
- Message/Notification Components
- Real-time WebSocket Client

📋 Deliverables:
- Frontend Component Class Diagrams
- WebSocket Client API specifications
- Agent Status Update Sequence Diagram
- UI State Management Strategy
```

### **Team B: Backend Services**
```
🎯 Focus Areas:
- API Server Components (Authentication, Agent Management)
- WebSocket Server Components
- Business Logic Services
- Database Integration Layer

📋 Deliverables:
- Backend Service Class Diagrams  
- REST API OpenAPI Specification
- Message Broadcasting Sequence Diagram
- Error Handling Strategy
```

### **Team C: Data & Integration**
```
🎯 Focus Areas:
- Database Schema Design (MSSQL + MongoDB)
- Data Access Layer Components
- Event Logging Components
- System Integration Patterns

📋 Deliverables:
- Database Schema ER Diagrams
- Data Access Layer Class Diagrams
- Data Synchronization Sequence Diagram
- Performance Optimization Strategy
```

### **Team D: Supervisor Dashboard**
```
🎯 Focus Areas:
- Web Dashboard Components (React.js)
- Real-time Dashboard Updates
- Management Functions (Broadcasting, Reports)
- Dashboard WebSocket Integration

📋 Deliverables:
- Dashboard Component Class Diagrams
- Management API Specifications
- Dashboard Update Sequence Diagram
- UI/UX Integration Strategy
```

---

## Slide 23: 📊 Workshop Evaluation Criteria
### เกณฑ์การประเมิน Workshop

**🏆 Grading Rubric (Total: 100 points)**

### **Technical Accuracy (40 points)**
```
Excellent (36-40): 
- UML diagrams สมบูรณ์และถูกต้องทางเทคนิค
- API specifications ใช้งานได้จริง
- Database design optimized และ normalized

Good (28-35):
- Design ถูกต้องแต่อาจขาดรายละเอียดบางส่วน
- Minor technical issues ที่แก้ได้ง่าย

Satisfactory (20-27):
- Design พื้นฐานถูกต้องแต่ไม่สมบูรณ์
- ต้องปรับปรุงก่อนใช้งานจริง

Needs Improvement (0-19):
- Major technical flaws
- ไม่สามารถใช้เป็น implementation guide ได้
```

### **Completeness & Integration (25 points)**
```
Excellent (23-25):
- ครอบคลุมทุก requirements จาก C3 architecture
- Components integrate seamlessly
- End-to-end flow ชัดเจน

Good (18-22):
- ครอบคลุม core requirements
- Minor integration gaps

Satisfactory (13-17):
- Basic requirements covered
- Some integration issues need resolution

Needs Improvement (0-12):
- Incomplete coverage
- Major integration problems
```

### **Professional Quality (20 points)**
```
Excellent (18-20):
- Documentation มืออาชีพ
- Consistent naming conventions
- Ready for development team

Good (14-17):
- Good quality มี minor issues
- Professional presentation

Satisfactory (10-13):
- Acceptable quality แต่ต้อง polish
- Basic professional standards

Needs Improvement (0-9):
- Poor documentation quality
- Inconsistent or unclear
```

### **Innovation & Problem Solving (15 points)**
```
Excellent (14-15):
- Creative solutions to complex problems
- Advanced patterns และ techniques
- Consideration of non-functional requirements

Good (11-13):
- Some innovative approaches
- Good problem-solving skills

Satisfactory (8-10):
- Standard solutions
- Basic problem-solving

Needs Improvement (0-7):
- Lack of creative thinking
- Problems not properly addressed
```

---

## Slide 24: 🔍 Code Review Workshop
### การทำ Architecture Review

**🎯 Peer Review Process:**

### **Architecture Review Checklist:**

**🏗️ Design Principles Review:**
```
□ Single Responsibility: แต่ละ class มีหน้าที่ชัดเจน
□ Open/Closed: สามารถขยายฟีเจอร์ใหม่ได้ง่าย
□ Dependency Inversion: Components ไม่ depend on concrete implementations
□ Interface Segregation: Interfaces เฉพาะเจาะจง ไม่รวมทุกอย่าง
□ DRY: ไม่มีการทำซ้ำ logic
□ KISS: Design ไม่ซับซอนเกินจำเป็น
```

**🔗 Integration Review:**
```
□ API Contracts: Request/Response schemas สอดคล้องกัน
□ Data Flow: ข้อมูลไหลผ่านระบบอย่างสมเหตุสมผล
□ Error Propagation: Error handling ครอบคลุมและสอดคล้อง
□ Security: Authentication/Authorization ปลอดภัย
□ Performance: ไม่มี obvious bottlenecks
□ Scalability: รองรับการขยายตัว
```

**📊 Documentation Review:**
```
□ Clarity: เข้าใจง่าย สำหรับ developers ใหม่
□ Completeness: ข้อมูลครบถ้วน สำหรับ implementation
□ Consistency: Naming conventions และ styles เหมือนกัน
□ Maintainability: สามารถอัปเดตและดูแลรักษาได้
□ Testability: ออกแบบให้ test ได้ง่าย
```

### **Review Process Steps:**

**Step 1: Self Review (10 นาที)**
```
- ตรวจสอบงานของตัวเองก่อนให้คนอื่น review
- ใช้ checklist ข้างบน
- แก้ไข obvious issues
```

**Step 2: Peer Review (20 นาที)**
```
- แลกเปลี่ยนงานกับทีมอื่น
- ให้ constructive feedback
- เสนอแนะ improvements
```

**Step 3: Instructor Review (10 นาที)**
```
- อาจารย์ให้ feedback หลัก
- แนวทางปรับปรุง
- Best practices sharing
```

---

## Slide 25: 📈 Performance & Scalability Analysis
### การวิเคราะห์ Performance และ Scalability

**🚀 Performance Considerations:**

### **Database Performance Analysis:**
```typescript
// Performance Bottlenecks ที่ต้องระวัง

// 1. N+1 Query Problem (หลีกเลี่ยง)
❌ Bad Approach:
const agents = await Agent.findAll();
for (const agent of agents) {
  agent.statusHistory = await StatusHistory.findByAgentId(agent.id);
}
// Result: 1 + N queries

✅ Good Approach:
const agents = await Agent.findAll({
  include: [{
    model: StatusHistory,
    limit: 10,
    order: [['timestamp', 'DESC']]
  }]
});
// Result: 1 query with JOIN

// 2. Database Index Strategy
const requiredIndexes = {
  agents: [
    'CREATE INDEX IX_Agents_Status ON Agents(Status, IsActive)',
    'CREATE INDEX IX_Agents_Department ON Agents(Department)',
    'CREATE INDEX IX_Agents_AgentCode ON Agents(AgentCode)'
  ],
  statusHistory: [
    'CREATE INDEX IX_StatusHistory_AgentId_Timestamp ON StatusHistory(AgentId, Timestamp DESC)',
    'CREATE INDEX IX_StatusHistory_Timestamp ON StatusHistory(Timestamp DESC)'
  ]
};

// 3. Query Optimization Examples
// ❌ Unoptimized query
const slowQuery = `
  SELECT * FROM Agents a
  WHERE a.Department = 'Sales'
  AND a.ID IN (
    SELECT AgentId FROM StatusHistory 
    WHERE Timestamp > DATEADD(day, -1, GETUTCDATE())
  )
`;

// ✅ Optimized query
const fastQuery = `
  SELECT DISTINCT a.ID, a.AgentCode, a.Name, a.Status
  FROM Agents a
  INNER JOIN StatusHistory sh ON a.ID = sh.AgentId
  WHERE a.Department = 'Sales' 
    AND a.IsActive = 1
    AND sh.Timestamp > DATEADD(day, -1, GETUTCDATE())
`;
```

### **WebSocket Scalability Strategy:**
```typescript
// Horizontal Scaling with Redis
class WebSocketScaling {
  constructor(
    private redisAdapter: RedisAdapter,
    private loadBalancer: LoadBalancer
  ) {}
  
  // Room-based message distribution
  async broadcastToRoom(room: string, event: string, data: any): Promise<void> {
    // Use Redis to coordinate across multiple server instances
    await this.redisAdapter.publish(`room:${room}`, {
      event,
      data,
      timestamp: Date.now()
    });
  }
  
  // Connection management across instances
  async trackConnection(socketId: string, userId: string): Promise<void> {
    const serverId = process.env.SERVER_ID || 'server-1';
    
    await this.redisAdapter.setEx(
      `connection:${socketId}`,
      3600, // 1 hour TTL
      JSON.stringify({
        userId,
        serverId,
        connectedAt: Date.now()
      })
    );
  }
  
  // Load balancing strategy
  getOptimalServer(): string {
    return this.loadBalancer.getLeastConnectedServer();
  }
}

// Caching Strategy
class CachingStrategy {
  // Multi-level caching
  async getAgentStatus(agentId: string): Promise<AgentStatus> {
    // Level 1: In-memory cache (fastest)
    let status = this.memoryCache.get(`agent:${agentId}:status`);
    if (status) return status;
    
    // Level 2: Redis cache (fast)
    status = await this.redisCache.get(`agent:${agentId}:status`);
    if (status) {
      this.memoryCache.set(`agent:${agentId}:status`, status, 60); // 1 min
      return status;
    }
    
    // Level 3: Database (slowest)
    const agent = await this.database.findAgent(agentId);
    status = agent.status;
    
    // Cache at all levels
    await this.redisCache.setEx(`agent:${agentId}:status`, 300, status); // 5 min
    this.memoryCache.set(`agent:${agentId}:status`, status, 60); // 1 min
    
    return status;
  }
}
```

### **Frontend Performance:**
```typescript
// React.js Optimization Techniques
const DashboardOptimization = {
  // 1. Virtual Scrolling for large datasets
  VirtualizedAgentList: React.memo(({ agents }) => {
    const FixedSizeList = require('react-window').FixedSizeList;
    
    return (
      <FixedSizeList
        height={600}
        itemCount={agents.length}
        itemSize={80}
        itemData={agents}
      >
        {AgentListItem}
      </FixedSizeList>
    );
  }),
  
  // 2. Debounced search
  useDebounce: (value: string, delay: number) => {
    const [debouncedValue, setDebouncedValue] = useState(value);
    
    useEffect(() => {
      const handler = setTimeout(() => {
        setDebouncedValue(value);
      }, delay);
      
      return () => clearTimeout(handler);
    }, [value, delay]);
    
    return debouncedValue;
  },
  
  // 3. Memoized calculations
  StatusSummary: React.memo(({ agents }) => {
    const summary = useMemo(() => {
      return agents.reduce((acc, agent) => {
        acc[agent.status] = (acc[agent.status] || 0) + 1;
        return acc;
      }, {} as Record<string, number>);
    }, [agents]);
    
    return <StatusChart data={summary} />;
  })
};
```

---

## Slide 26: 🛡️ Security Architecture
### การออกแบบความปลอดภัย

**🔒 Security Implementation Strategy:**

```typescript
// 1. Authentication & Authorization Architecture
class SecurityArchitecture {
  // JWT Token Management
  private jwtConfig = {
    secret: process.env.JWT_SECRET,
    accessTokenExpiry: '15m',
    refreshTokenExpiry: '7d',
    algorithm: 'HS256'
  };
  
  // Multi-factor Authentication
  async authenticateWithMFA(
    username: string, 
    password: string, 
    mfaToken?: string
  ): Promise<AuthResult> {
    // Step 1: Verify username/password
    const user = await this.userRepository.findByUsername(username);
    if (!user || !await bcrypt.compare(password, user.passwordHash)) {
      throw new UnauthorizedError('Invalid credentials');
    }
    
    // Step 2: Check if MFA required
    if (user.mfaEnabled && !mfaToken) {
      return {
        requiresMFA: true,
        message: 'MFA token required'
      };
    }
    
    // Step 3: Verify MFA token if provided
    if (user.mfaEnabled && mfaToken) {
      const isValidMFA = await this.verifyMFAToken(user.id, mfaToken);
      if (!isValidMFA) {
        throw new UnauthorizedError('Invalid MFA token');
      }
    }
    
    // Step 4: Generate tokens
    const tokens = await this.generateTokenPair(user);
    
    return {
      user: this.sanitizeUser(user),
      accessToken: tokens.accessToken,
      refreshToken: tokens.refreshToken
    };
  }
  
  // Role-based Access Control (RBAC)
  authorizeAction(user: User, resource: string, action: string): boolean {
    const userPermissions = this.rolePermissions[user.role] || [];
    const requiredPermission = `${resource}:${action}`;
    
    return userPermissions.includes(requiredPermission) || 
           userPermissions.includes(`${resource}:*`) ||
           userPermissions.includes('*:*');
  }
}

// 2. Input Validation & Sanitization
class InputValidation {
  // XSS Protection
  sanitizeInput(input: string): string {
    return DOMPurify.sanitize(input, {
      ALLOWED_TAGS: [], // No HTML tags allowed
      ALLOWED_ATTR: []
    });
  }
  
  // SQL Injection Prevention (using parameterized queries)
  async safeDatabaseQuery(query: string, params: any[]): Promise<any[]> {
    // Always use parameterized queries
    return this.database.execute(query, params);
  }
  
  // API Input Validation Schema
  agentValidationSchema = Joi.object({
    agentCode: Joi.string().pattern(/^A[0-9]{3}$/).required(),
    name: Joi.string().min(2).max(100).required(),
    email: Joi.string().email().required(),
    department: Joi.string().valid('Sales', 'Support', 'Technical', 'General').required(),
    skills: Joi.array().items(Joi.string().max(50)).max(10)
  });
}

// 3. WebSocket Security
class WebSocketSecurity {
  // Connection Authentication
  authenticateWebSocketConnection(socket: Socket, next: Function): void {
    const token = socket.handshake.auth.token;
    
    try {
      const decoded = jwt.verify(token, process.env.JWT_SECRET);
      socket.userId = decoded.sub;
      socket.userRole = decoded.role;
      next();
    } catch (error) {
      next(new Error('Authentication failed'));
    }
  }
  
  // Rate Limiting for WebSocket Events
  @RateLimit(100, 60000) // 100 events per minute
  async handleWebSocketEvent(socket: Socket, event: string, data: any): Promise<void> {
    // Validate event data
    const validationResult = this.validateEventData(event, data);
    if (!validationResult.isValid) {
      socket.emit('error', { message: 'Invalid event data' });
      return;
    }
    
    // Check permissions
    if (!this.hasPermission(socket.userRole, event)) {
      socket.emit('error', { message: 'Insufficient permissions' });
      return;
    }
    
    // Process event
    await this.processEvent(socket, event, data);
  }
  
  // Message Encryption for sensitive data
  encryptSensitiveMessage(message: string): string {
    const cipher = crypto.createCipher('aes-256-cbc', process.env.ENCRYPTION_KEY);
    let encrypted = cipher.update(message, 'utf8', 'hex');
    encrypted += cipher.final('hex');
    return encrypted;
  }
}

// 4. Security Monitoring & Logging
class SecurityMonitoring {
  // Audit Log
  async logSecurityEvent(event: SecurityEvent): Promise<void> {
    const auditLog = {
      eventType: event.type,
      userId: event.userId,
      ipAddress: event.ipAddress,
      userAgent: event.userAgent,
      timestamp: new Date(),
      success: event.success,
      details: event.details,
      riskLevel: this.calculateRiskLevel(event)
    };
    
    await this.auditRepository.create(auditLog);
    
    // Alert on high-risk events
    if (auditLog.riskLevel === 'HIGH') {
      await this.alertService.sendSecurityAlert(auditLog);
    }
  }
  
  // Intrusion Detection
  detectSuspiciousActivity(userId: string, ipAddress: string): boolean {
    // Check for multiple failed login attempts
    const recentFailures = this.getRecentFailedLogins(userId, ipAddress);
    if (recentFailures > 5) {
      return true;
    }
    
    // Check for unusual access patterns
    const accessPattern = this.analyzeAccessPattern(userId);
    if (accessPattern.isAnomalous) {
      return true;
    }
    
    return false;
  }
}
```

---

## Slide 27: 📋 Assignment: Complete Technical Specifications
### งานที่มอบหมาย - การสร้าง Technical Specifications ที่สมบูรณ์

**🎯 Assignment Overview:**
**"สร้าง Complete Implementation-Ready Technical Specifications สำหรับ Agent Wallboard System"**

### **📊 Assignment Requirements (100 คะแนน):**

**Part 1: Detailed Class Design (30 คะแนน)**
```
สร้าง UML Class Diagrams สำหรับ:

1. Core Business Components (15 คะแนน):
   - Agent Management Component
   - Authentication Component  
   - Message Communication Component
   - WebSocket Management Component

2. Data Access Components (10 คะแนน):
   - Database Repository Classes
   - Data Transfer Objects (DTOs)
   - Database Connection Management

3. Integration Components (5 คะแนน):
   - API Controllers
   - Event Bus Components
   - Error Handling Classes

Requirements:
- ใช้ proper UML notation
- แสดง relationships (composition, inheritance, association)
- ระบุ method signatures และ parameters
- Include access modifiers (+, -, #, ~)
```

**Part 2: API Documentation (25 คะแนน)**
```
สร้าง OpenAPI/Swagger Specification สำหรับ:

1. Agent Management APIs (15 คะแนน):
   - CRUD operations สำหรับ agents
   - Status management endpoints
   - Agent history และ statistics

2. Authentication & Security APIs (5 คะแนน):
   - Login/logout endpoints
   - Token refresh mechanism
   - Password change/reset

3. Real-time Communication APIs (5 คะแนน):
   - WebSocket event specifications
   - Message broadcasting endpoints
   - Dashboard update mechanisms

Requirements:
- Complete request/response schemas
- Error response documentation
- Security definitions (JWT)
- Example requests and responses
```

**Part 3: Database Design (20 คะแนน)**
```
สร้าง Complete Database Schema:

1. MSSQL Schema Design (12 คะแนน):
   - Table definitions with proper data types
   - Primary keys, foreign keys, constraints
   - Indexes for performance optimization
   - Stored procedures (optional)

2. MongoDB Schema Design (8 คะแนน):
   - Collection schemas with validation rules
   - Index definitions for performance
   - Data retention policies
   - Aggregation pipeline examples

Requirements:
- ER Diagram สำหรับ MSSQL
- Document structure examples สำหรับ MongoDB
- Data migration strategy
- Performance considerations
```

**Part 4: Implementation Strategy (15 คะแนน)**
```
สร้าง Implementation Plan:

1. Development Phases (8 คะแนน):
   - Phase breakdown with timelines
   - Dependency management
   - Risk assessment และ mitigation

2. Testing Strategy (7 คะแนน):
   - Unit testing approach
   - Integration testing plan
   - Performance testing scenarios
   - Security testing requirements

Requirements:
- Detailed timeline with milestones
- Resource allocation plan
- Quality assurance procedures
- Deployment strategy
```

**Part 5: Architecture Analysis (10 คะแนน)**
```
Technical Analysis Report:

1. Performance Analysis (5 คะแนน):
   - Bottleneck identification
   - Scalability assessment
   - Optimization recommendations

2. Security Analysis (5 คะแนน):
   - Threat model assessment
   - Security controls implementation
   - Compliance requirements

Requirements:
- Professional analysis document
- Supporting diagrams and charts
- Actionable recommendations
- Industry best practices references
```

---

## Slide 28: 📅 Assignment Timeline & Submission
### กำหนดเวลาและการส่งงาน

**⏰ Assignment Timeline:**

### **Week 9 (Today) - Assignment Release:**
```
🎯 In-Class Activities:
- Workshop completion
- Team formation และ role assignment
- Initial design discussions
- Template และ resource sharing

📋 By End of Class:
- Team assignments confirmed
- Project scope clarified
- Resource access verified
- Questions resolved with instructor
```

### **Week 10 - Development Week:**
```
🛠️ Development Activities:
- Create detailed class diagrams
- Write API specifications
- Design database schemas
- Develop implementation plans

📞 Support Available:
- Office Hours: Monday/Wednesday 2:00-4:00 PM
- Online Q&A sessions: Tuesday/Thursday 7:00-8:00 PM  
- Peer review sessions: Friday 1:00-3:00 PM
- Email support: continuous response within 24 hours
```

### **Week 11 - Final Preparation:**
```
🔍 Quality Assurance:
- Complete all documentation
- Peer review sessions
- Final testing และ validation
- Presentation preparation

📊 Submission Preparation:
- Document formatting และ organization
- File naming conventions verification
- Submission checklist completion
- Backup preparation
```

### **📝 Submission Requirements:**

**🗂️ Submission Format:**
```
AgentWallboard_TechnicalSpecs_TeamX.zip
├── 01_ClassDiagrams/
│   ├── AgentManagement_ClassDiagram.png
│   ├── Authentication_ClassDiagram.png
│   ├── WebSocket_ClassDiagram.png
│   └── DataAccess_ClassDiagram.png
├── 02_APIDocumentation/
│   ├── AgentWallboard_OpenAPI.yaml
│   ├── WebSocket_Events.md
│   └── API_Examples.md
├── 03_DatabaseDesign/
│   ├── MSSQL_Schema.sql
│   ├── MongoDB_Schema.js
│   └── ER_Diagram.png
├── 04_ImplementationPlan/
│   ├── Development_Timeline.md
│   ├── Testing_Strategy.md
│   └── Risk_Assessment.md
├── 05_Analysis/
│   ├── Performance_Analysis.md
│   ├── Security_Analysis.md
│   └── Architecture_Review.md
└── README.md (Project overview และ team members)
```

**⏳ Submission Deadline:**
- **Due Date**: สัปดาห์ที่ 11, วันศุกร์ เวลา 23:59
- **Late Submission**: -10% per day (maximum 3 days)
- **Submission Method**: LMS Upload + Email confirmation
- **File Size Limit**: 50 MB per submission

---

## Slide 29: 🏆 Grading Rubric & Success Criteria
### เกณฑ์การประเมินและความสำเร็จ

**📊 Detailed Grading Rubric:**

### **Technical Excellence (40 คะแนน)**
```
Outstanding (36-40):
✅ All UML diagrams technically accurate และ complete
✅ API specifications implementable without modification
✅ Database design optimized และ normalized
✅ Code examples syntactically correct
✅ Industry best practices consistently applied

Proficient (28-35):
✅ Minor technical issues ที่แก้ไขได้ง่าย
✅ Good understanding of concepts
✅ Most specifications complete และ accurate

Developing (20-27):
⚠️ Some technical errors requiring correction
⚠️ Basic understanding demonstrated
⚠️ Specifications need refinement for implementation

Beginning (0-19):
❌ Major technical flaws
❌ Specifications unusable for implementation
❌ Fundamental misunderstanding of concepts
```

### **Completeness & Coverage (25 คะแนน)**
```
Outstanding (23-25):
✅ All required components thoroughly covered
✅ Comprehensive integration between components
✅ Additional valuable components beyond requirements

Proficient (18-22):
✅ All major requirements addressed
✅ Good integration coverage
✅ Minor gaps in some areas

Developing (13-17):
⚠️ Most requirements covered
⚠️ Some integration gaps
⚠️ Missing some important components

Beginning (0-12):
❌ Significant gaps in coverage
❌ Major components missing
❌ Poor integration planning
```

### **Professional Quality (20 คะแนน)**
```
Outstanding (18-20):
✅ Documentation publication-ready
✅ Consistent professional formatting
✅ Clear, concise technical writing
✅ Comprehensive examples และ explanations

Proficient (14-17):
✅ Good professional presentation
✅ Generally consistent formatting
✅ Clear technical communication

Developing (10-13):
⚠️ Acceptable quality needing minor improvements
⚠️ Some formatting inconsistencies
⚠️ Generally clear communication

Beginning (0-9):
❌ Poor presentation quality
❌ Inconsistent formatting
❌ Unclear technical communication
```

### **Innovation & Problem Solving (15 คะแนน)**
```
Outstanding (14-15):
✅ Creative solutions to complex problems
✅ Advanced design patterns และ techniques
✅ Consideration of edge cases และ non-functional requirements
✅ Future-proofing และ extensibility

Proficient (11-13):
✅ Good problem-solving approaches
✅ Some creative elements
✅ Basic consideration of non-functional requirements

Developing (8-10):
⚠️ Standard solutions applied correctly
⚠️ Limited creative thinking
⚠️ Basic problem-solving skills

Beginning (0-7):
❌ Poor problem-solving approach
❌ Lack of creative thinking
❌ Problems not properly addressed
```

### **🎯 Success Indicators:**
- **A Grade (90-100)**: Ready for immediate implementation
- **B Grade (80-89)**: Minor revisions needed before implementation  
- **C Grade (70-79)**: Significant revisions required
- **Below C**: Major rework necessary

---

## Slide 30: 🌟 Best Practices & Tips for Success
### แนวทางปฏิบัติที่ดีและเคล็ดลับความสำเร็จ

**💡 Professional Development Tips:**

### **🎯 Technical Design Excellence:**
```
✅ DO:
- Start with simple designs และ add complexity gradually
- Use established design patterns appropriately
- Consider performance implications early
- Design for testability และ maintainability
- Document design decisions และ trade-offs
- Validate designs with potential users/stakeholders

❌ DON'T:
- Over-engineer solutions for simple problems
- Use design patterns just because you know them
- Ignore non-functional requirements
- Create tightly coupled components
- Skip validation with stakeholders
- Design without considering future changes
```

### **📚 Documentation Best Practices:**
```
✅ DO:
- Write for your audience (developers, managers, users)
- Use consistent terminology throughout
- Include concrete examples และ use cases
- Provide both high-level overview และ detailed specs
- Update documentation when design changes
- Use visual aids (diagrams, charts) effectively

❌ DON'T:
- Write documentation that only you can understand
- Use inconsistent naming conventions
- Provide only abstract descriptions
- Skip examples และ practical guidance
- Let documentation become outdated
- Rely solely on text without visual support
```

### **🤝 Team Collaboration Strategies:**
```
✅ Effective Collaboration:
- Establish clear roles และ responsibilities
- Use version control for all artifacts
- Schedule regular team check-ins
- Share knowledge และ expertise freely
- Resolve conflicts through discussion
- Celebrate team achievements

✅ Communication Tips:
- Ask questions when uncertain
- Provide constructive feedback
- Be open to receiving criticism
- Document important decisions
- Keep all team members informed
- Use collaborative tools effectively
```

### **⏰ Time Management & Planning:**
```
Week-by-Week Strategy:

Week 9 (Today):
🎯 Complete workshop activities
📋 Assign team roles และ responsibilities  
🛠️ Set up development environment และ tools
📝 Create project timeline และ milestones

Week 10:
🏗️ Focus on core components (Mon-Wed)
🔍 Peer review และ feedback (Thu-Fri)
📊 Integration testing และ validation
🔧 Refinement based on feedback

Week 11:
✨ Final polish และ quality assurance
📖 Complete documentation review
🎤 Presentation preparation
📤 Submission และ backup
```

### **🚀 Advanced Success Strategies:**
```
Go Beyond Requirements:
- Research industry standards และ practices
- Include security considerations proactively
- Consider accessibility requirements
- Plan for scalability และ performance
- Think about maintenance และ operations
- Prepare for change management

Quality Assurance:
- Test designs with realistic scenarios
- Get feedback from multiple perspectives
- Validate against original requirements
- Check for consistency across all artifacts
- Proofread all documentation
- Prepare presentation materials early
```

---

## Slide 31: 📚 Resources & Learning Materials
### แหล่งเรียนรู้และเอกสารอ้างอิง

**📖 Essential Reading Materials:**

### **🏗️ Architecture & Design:**
```
Books:
📚 "Clean Architecture" - Robert C. Martin
📚 "Software Architecture in Practice" - Bass, Clements, Kazman
📚 "Designing Data-Intensive Applications" - Martin Kleppmann
📚 "Building Microservices" - Sam Newman
📚 "Domain-Driven Design" - Eric Evans

Online Resources:
🌐 C4 Model Official Website: https://c4model.com/
🌐 Microsoft Architecture Center
🌐 AWS Well-Architected Framework
🌐 Google Cloud Architecture Center
🌐 Martin Fowler's Architecture Articles
```

### **🛠️ Technical Implementation:**
```
API Design:
📖 OpenAPI Specification: https://swagger.io/specification/
📖 REST API Design Guidelines - Microsoft
📖 "RESTful Web Services" - Leonard Richardson

WebSocket & Real-time:
📖 Socket.io Documentation: https://socket.io/docs/
📖 "Real-Time Web Application Development" - Rami Sayar
📖 WebSocket RFC 6455 specification

Database Design:
📖 "Database Design for Mere Mortals" - Michael J. Hernandez
📖 MongoDB Manual: https://docs.mongodb.com/
📖 SQL Server Documentation: https://docs.microsoft.com/sql/
```

### **🎨 Tools & Software:**
```
Diagramming Tools:
🛠️ Draw.io (Free): https://app.diagrams.net/
🛠️ Lucidchart (Student License): https://lucidchart.com/
🛠️ Microsoft Visio (University License)
🛠️ PlantUML (Free, Text-based): https://plantuml.com/

Development Tools:
🛠️ Visual Studio Code (Free)
🛠️ Postman (API Testing): https://postman.com/
🛠️ MongoDB Compass (Free)
🛠️ SQL Server Management Studio (Free)
🛠️ Git + GitHub (Version Control)

API Documentation:
🛠️ Swagger Editor: https://editor.swagger.io/
🛠️ Insomnia (REST Client): https://insomnia.rest/
🛠️ Redoc (Documentation): https://redoc.ly/
```

### **📺 Video Learning Resources:**
```
YouTube Channels:
📹 "Clean Code" - Uncle Bob Martin
📹 "Architecture Weekly" - Oskar Dudycz  
📹 "Software Architecture Monday" - Mark Richards
📹 "The Dev Show" - Microsoft Developers

Online Courses:
💻 "Software Architecture & Design" - Coursera/University of Alberta
💻 "Microservices Architecture" - Pluralsight
💻 "API Design Best Practices" - Udemy
💻 "Database Design Fundamentals" - edX/Microsoft
```

### **🔧 Practice Projects & Examples:**
```
GitHub Repositories:
📁 Microsoft Architecture Samples
📁 AWS Architecture Samples  
📁 Real-world API Examples
📁 Socket.io Example Applications
📁 MERN/MEAN Stack Examples

Online Sandboxes:
🏖️ CodeSandbox (Frontend): https://codesandbox.io/
🏖️ Repl.it (Full-stack): https://replit.com/
🏖️ Swagger Petstore (API Example)
🏖️ MongoDB Atlas (Free Database)
```

---

## Slide 32: ❓ Q&A Session
### ถาม-ตอบ และการแก้ปัญหา

**💬 คำถามที่ถามบ่อย (FAQ):**

### **🏗️ Architecture & Design Questions:**

**Q: ทำไมต้องใช้ทั้ง MSSQL และ MongoDB ในระบบเดียว?**
```
A: หลักการ Polyglot Persistence:
✅ MSSQL: Master data ที่ต้อง consistency (agents, users, departments)
✅ MongoDB: Event data ที่เขียน-อ่านบ่อย (status history, messages, logs)
✅ แต่ละ database เหมาะสำหรับ use case ต่างกัน
✅ Performance optimization: เลือกเครื่องมือที่เหมาะสำหรับงาน
```

**Q: WebSocket vs Server-Sent Events (SSE) ใช้อันไหนดีกว่า?**
```
A: สำหรับ Agent Wallboard System:
✅ WebSocket เหมาะกว่า เพราะ:
  - ต้องการ bidirectional communication
  - Agent ส่ง status updates, รับ messages
  - Real-time interaction สูง
  - Connection persistence ดีกว่า

❌ SSE เหมาะกับ:
  - One-way communication (server → client)
  - Simple notifications
  - ไม่ต้องการ complex interactions
```

**Q: การออกแบบ API จะเป็น RESTful หรือ GraphQL?**
```
A: สำหรับ Agent Wallboard:
✅ RESTful เหมาะกว่า เพราะ:
  - Simple CRUD operations
  - Straightforward caching
  - ทีมคุ้นเคยกับ REST patterns
  - Monitoring และ debugging ง่ายกว่า

💡 GraphQL เหมาะกับ:
  - Complex data relationships
  - Frontend ต้องการ flexible queries
  - Mobile apps ที่ต้อง minimize data transfer
```

### **🛠️ Implementation Questions:**

**Q: การจัดการ WebSocket connections เมื่อมี users เยอะ?**
```
A: Scaling Strategies:
🚀 Horizontal Scaling:
  - ใช้ Redis Adapter สำหรับ Socket.io
  - Load balancing กับ sticky sessions
  - Connection pooling และ management

⚡ Performance Optimization:
  - Room-based message broadcasting
  - Connection heartbeat monitoring
  - Graceful disconnection handling
  - Memory leak prevention
```

**Q: การจัดการ Database transactions ข้าม MSSQL และ MongoDB?**
```
A: Distributed Transaction Patterns:
🔄 Saga Pattern:
  - แบ่งเป็น steps ที่ compensate กันได้
  - Example: Create agent → Log creation event → Update cache

🎯 Event Sourcing:
  - Store events ใน MongoDB
  - Build current state จาก events
  - MSSQL เก็บ snapshot สำหรับ queries

⚠️ หลีกเลี่ยง 2-Phase Commit:
  - Complexity สูง
  - Performance overhead
  - ใช้เฉพาะเมื่อจำเป็นจริงๆ
```

### **📊 Assignment Questions:**

**Q: ทีมขนาดไหนเหมาะสมสำหรับ assignment นี้?**
```
A: ขนาดทีมที่แนะนำ:
✅ 4-5 คน: เหมาะสมที่สุด
  - แบ่งงานได้ชัดเจน (Frontend, Backend, Database, Documentation)
  - Communication overhead น้อย
  - ทุกคนมีส่วนร่วมมากพอ

⚠️ 3 คน: ได้แต่หนักหน่วง
❌ 6+ คน: Communication ยาก, คนเกินไป

📋 Role Distribution:
- Technical Lead (1 คน): Overall architecture
- Frontend Specialist (1 คน): UI/UX + Desktop app
- Backend Specialist (1 คน): API + WebSocket
- Database Specialist (1 คน): Schema + Performance
- Documentation Lead (1 คน): Integration + Testing
```

**Q: เวลาไม่พอทำให้ครบ จะ prioritize อย่างไร?**
```
A: Priority Ranking (High → Low):
🔥 Must Have (70% of grade):
  1. Core class diagrams (Agent, Auth, WebSocket)
  2. Essential API endpoints (CRUD agents, status update)
  3. Basic database schema (MSSQL core tables)
  4. Implementation timeline

🟡 Should Have (20% of grade):
  5. Advanced API documentation
  6. MongoDB schema details  
  7. Security specifications
  8. Performance analysis

🟢 Nice to Have (10% of grade):
  9. Advanced design patterns
  10. Comprehensive testing strategy
  11. Monitoring & logging design
  12. Extra features beyond requirements
```

**Q: จะรู้ได้อย่างไรว่า design ของเราดีพอ?**
```
A: Self-Assessment Checklist:
✅ Technical Validation:
  - สามารถ implement ตาม design ได้จริงไหม?
  - มี inconsistencies หรือ missing pieces ไหม?
  - Performance requirements สามารถทำได้ไหม?

✅ Professional Quality:
  - คนอื่นอ่านแล้วเข้าใจไหม?
  - Documentation ครบถ้วนไหม?
  - ตรงตาม requirements ไหม?

✅ Best Practices:
  - ใช้ design principles ถูกต้องไหม?
  - Security considerations ครบไหม?
  - Maintainability ดีไหม?
```

---

## Slide 33: 🔄 Integration with Previous Weeks
### การเชื่อมต่อกับสัปดาห์ที่ผ่านมา

**🔗 Learning Journey Connection:**

### **📊 Weeks 5-7 → Week 9 Integration:**

```
Week 5: High-Level Architecture
├── C1: System Context ✅
├── C2: Container Architecture ✅  
└── 3-Tier Architecture Pattern ✅
    ↓
Week 6: Design Patterns
├── Observer Pattern (WebSocket events) ✅
├── Publisher-Subscriber (Real-time updates) ✅
├── Factory Pattern (Component creation) ✅
└── Singleton Pattern (Connection management) ✅
    ↓
Week 7: Component Architecture  
├── C3: Component Breakdown ✅
├── Interface Definitions ✅
├── Component Communication ✅
└── Workshop: Team Design ✅
    ↓
Week 9: Implementation Details (TODAY!)
├── C4: Code Level Specifications
├── UML Class & Sequence Diagrams
├── API Documentation (OpenAPI/Swagger)
├── Database Schema Design
└── UI Mockups & Integration
```

### **🎯 How Each Week Builds Upon the Previous:**

**Week 5 Foundation → Week 9 Implementation:**
```
C1 System Context (Week 5):
Agent ↔ Desktop App ↔ API Server ↔ Database

↓ becomes ↓

Detailed Class Implementation (Week 9):
class DesktopApp {
  constructor(apiClient: IAPIClient, wsClient: IWebSocketClient) {}
  async authenticateAgent(credentials: LoginCredentials): Promise<AuthResult>
  async updateStatus(newStatus: AgentStatus): Promise<void>
}
```

**Design Patterns (Week 6) → Code Implementation (Week 9):**
```
Observer Pattern Concept (Week 6):
"WebSocket จะ notify ทุกคนเมื่อ agent เปลี่ยน status"

↓ becomes ↓

Actual Implementation (Week 9):
interface IStatusObserver {
  onStatusChanged(event: StatusChangeEvent): void;
}

class WebSocketManager {
  private observers: IStatusObserver[] = [];
  
  subscribe(observer: IStatusObserver): void {
    this.observers.push(observer);
  }
  
  notifyStatusChange(event: StatusChangeEvent): void {
    this.observers.forEach(observer => 
      observer.onStatusChanged(event)
    );
  }
}
```

**Component Architecture (Week 7) → Database Design (Week 9):**
```
C3 Component (Week 7):
"Agent Status Service จัดการ business logic"

↓ becomes ↓

Database Schema (Week 9):
CREATE TABLE Agents (
    ID UNIQUEIDENTIFIER PRIMARY KEY,
    AgentCode NVARCHAR(10) NOT NULL,
    CurrentStatus NVARCHAR(20) NOT NULL,
    LastStatusChange DATETIME2 NOT NULL
);

CREATE TABLE StatusHistory (
    ID UNIQUEIDENTIFIER PRIMARY KEY,
    AgentID UNIQUEIDENTIFIER NOT NULL,
    PreviousStatus NVARCHAR(20),
    NewStatus NVARCHAR(20) NOT NULL,
    Timestamp DATETIME2 NOT NULL,
    FOREIGN KEY (AgentID) REFERENCES Agents(ID)
);
```

---

## Slide 34: 🚀 Preparation for Implementation Phase
### การเตรียมพร้อมสู่การพัฒนาจริง

**🎯 From Design to Development:**

### **📋 Implementation Roadmap (สัปดาห์ที่ 10-15):**

**Week 10-11: Backend Development**
```
🏗️ Core Infrastructure:
- Setup Node.js project structure
- Configure TypeScript, ESLint, Prettier
- Setup database connections (MSSQL + MongoDB)
- Implement authentication middleware

🔧 API Development:
- Implement Agent CRUD endpoints
- Build WebSocket event handlers
- Create input validation middleware
- Setup error handling

📊 Database Implementation:
- Execute schema creation scripts
- Setup connection pooling
- Implement repository patterns
- Create migration scripts
```

**Week 12-13: Frontend Development**
```
🖥️ Desktop App (Electron.js):
- Setup Electron project structure
- Implement login screen
- Create agent dashboard UI
- Integrate with WebSocket client

🌐 Web Dashboard (React.js):
- Setup React application
- Implement supervisor dashboard
- Create real-time agent monitoring
- Build message broadcasting interface

🔗 Integration:
- Connect frontend to backend APIs
- Implement WebSocket client connections
- Handle real-time data updates
- Error handling and user feedback
```

**Week 14-15: Testing & Deployment**
```
🧪 Testing Implementation:
- Unit tests for business logic
- Integration tests for APIs
- End-to-end testing scenarios
- Performance testing

🚀 Deployment Preparation:
- Docker containerization
- Environment configuration
- CI/CD pipeline setup
- Production deployment
```

### **🛠️ Development Best Practices:**

**Code Organization:**
```
agent-wallboard/
├── backend/
│   ├── src/
│   │   ├── controllers/     # API endpoint handlers
│   │   ├── services/        # Business logic
│   │   ├── repositories/    # Data access layer
│   │   ├── models/          # Data models & DTOs
│   │   ├── middleware/      # Authentication, validation
│   │   ├── websocket/       # WebSocket event handlers
│   │   └── utils/           # Helper functions
│   ├── tests/               # Test files
│   └── database/            # Schema & migrations
├── frontend-desktop/        # Electron.js app
├── frontend-web/           # React.js dashboard
├── docs/                   # API documentation
└── deployment/            # Docker & deployment configs
```

**Development Workflow:**
```
🔄 Git Workflow:
- main branch: Production-ready code
- develop branch: Integration branch
- feature/* branches: Individual features
- Pull requests + code reviews

📋 Definition of Done:
✅ Code implements design specifications
✅ Unit tests written and passing
✅ Integration tests passing
✅ Documentation updated
✅ Code review completed
✅ Performance requirements met
```

---

## Slide 35: 📊 Course Progress & What's Next
### ความก้าวหน้าของหลักสูตรและสิ่งที่จะมาต่อไป

**🎓 Course Journey So Far:**

### **📈 Learning Progress Overview:**
```
✅ Weeks 1-4: Requirements Engineering
    - Software Requirements Specification (SRS)
    - Stakeholder analysis
    - Use case modeling
    - Requirements validation

✅ Week 5: High-Level Architecture Design
    - Software Design Document (SDD)
    - C1-C2 Architecture modeling
    - 3-Tier architecture patterns

✅ Week 6: Design Patterns & Solutions
    - Common design patterns
    - Problem-solving approaches
    - Pattern selection criteria

✅ Week 7: Component Architecture
    - C3 Component modeling
    - Interface design
    - Component communication

✅ Week 9: Implementation-Ready Design (TODAY!)
    - C4 Code level specifications
    - API documentation
    - Database design
    - UI mockups

📅 What's Coming Next (Weeks 10-15):
    - Actual software development
    - Testing & quality assurance
    - Deployment & operations
    - Project presentation & evaluation
```

### **🎯 Skills Acquired Throughout the Journey:**

**Technical Skills:**
```
🏗️ Architecture & Design:
✅ C4 Model mastery (Context → Code)
✅ UML diagram creation
✅ Design pattern application
✅ Component-based architecture

🛠️ Development Preparation:
✅ API design & documentation
✅ Database schema design
✅ WebSocket protocol design
✅ Security considerations

📊 Analysis & Problem Solving:
✅ Requirements analysis
✅ System decomposition
✅ Performance considerations
✅ Risk assessment
```

**Professional Skills:**
```
🤝 Collaboration:
✅ Team-based design workshops
✅ Peer review processes
✅ Professional presentation skills
✅ Technical communication

📋 Project Management:
✅ Timeline planning
✅ Resource allocation
✅ Quality assurance
✅ Documentation standards

🎯 Critical Thinking:
✅ Design trade-off analysis
✅ Alternative solution evaluation
✅ Best practice application
✅ Innovation & creativity
```

### **🏆 Final Project Vision:**
```
Agent Wallboard System - Complete Implementation

🖥️ What You'll Build:
- Professional Desktop Application (Electron.js)
- Real-time Web Dashboard (React.js)
- Scalable Backend API (Node.js + Express)
- Hybrid Database System (MSSQL + MongoDB)
- WebSocket Real-time Communication
- Professional Documentation Package

🎯 Industry-Ready Skills:
- Full-stack software development
- Real-time system architecture
- Database design & optimization
- API design & documentation
- Testing & quality assurance
- Professional project delivery
```

---

## Slide 36: 🎊 สรุปสัปดาห์ที่ 9
### Key Takeaways & Next Steps

**🌟 สิ่งที่เราได้เรียนรู้ในวันนี้:**

### **🎯 Major Achievements:**

**1. Complete Design Documentation:**
```
✅ C4 Code Level: From architecture to implementation
✅ UML Class Diagrams: Object-oriented design mastery
✅ UML Sequence Diagrams: Process flow visualization
✅ API Specifications: OpenAPI/Swagger proficiency
✅ Database Design: MSSQL + MongoDB hybrid approach
✅ UI Mockups: Professional interface design
```

**2. Implementation-Ready Specifications:**
```
✅ Technical documents that developers can use immediately
✅ Complete API specifications with examples
✅ Database schemas ready for deployment
✅ Security considerations implemented
✅ Performance optimization strategies planned
```

**3. Professional Development Skills:**
```
✅ Industry-standard design documentation
✅ Team collaboration in technical projects
✅ Architecture review and feedback processes
✅ Quality assurance methodologies
✅ Professional presentation of technical work
```

### **🔗 Connection to Real Industry Work:**
```
🏢 What You've Learned Matches Industry Needs:
- Software architects create exactly these documents
- Development teams use these specifications daily
- Quality assurance processes mirror industry standards
- Documentation skills are highly valued professionally

💼 Career Preparation:
- Portfolio-ready project documentation
- Demonstrable technical communication skills
- Understanding of complete software development lifecycle
- Experience with modern technology stacks
```

### **🚀 Immediate Next Steps:**

**This Week (Week 9):**
```
📋 Complete Assignment Preparation:
- Form teams and assign roles
- Set up development tools and environment
- Begin initial design work
- Schedule team meetings and collaboration sessions

🛠️ Resource Preparation:
- Access all provided templates and examples
- Set up accounts for required tools (Draw.io, GitHub, etc.)
- Review all reference materials
- Prepare questions for office hours
```

**Week 10 Focus:**
```
🎯 Core Development Activities:
- Intensive design work based on today's learning
- Implementation of backend API foundations
- Database setup and initial schema deployment
- Frontend project structure creation

📞 Support & Collaboration:
- Attend office hours for guidance
- Participate in peer review sessions
- Use online collaboration tools effectively
- Maintain regular team communication
```

### **🎉 Celebration & Motivation:**

**🏆 What You Should Be Proud Of:**
```
✨ You've mastered a complete software design methodology
✨ Your technical documentation skills rival industry professionals
✨ You can communicate complex technical concepts clearly
✨ You understand how to bridge requirements and implementation
✨ You're prepared to lead technical design discussions
```

**💪 Looking Forward:**
```
🎯 The exciting implementation phase begins!
🚀 Your designs will become working software
🏢 You're building genuinely useful, real-world applications
🎓 Every week brings you closer to professional readiness
🌟 The skills you're developing are immediately valuable in industry
```

**🔥 Final Encouragement:**
```
Remember: Great software starts with great design!

Today you've learned to CREATE that great design.
Next week you'll learn to IMPLEMENT that design.
By the end of this course, you'll have DELIVERED professional software.

The journey from requirements to running code is almost complete!
```

---

## Slide 37: 📞 Support & Office Hours
### การสนับสนุนและเวลาให้คำปรึกษา

**🤝 Available Support Channels:**

### **👨‍🏫 Instructor Support:**
```
📍 Office Hours:
- Monday & Wednesday: 2:00-4:00 PM
- Location: อาคารวิศวกรรมศาสตร์ ห้อง 301
- Online via Teams: https://teams.microsoft.com/l/meetup-join/...

📧 Email Communication:
- Response time: Within 24 hours (weekdays)
- Email: instructor@rmutl.ac.th
- Subject line: [ENGSE206] Your Topic Here

💬 Chat Support:
- Microsoft Teams: Available during business hours
- Discussion forum: Course LMS discussion board
- Quick questions: Teams chat anytime
```

### **👥 Peer Support Network:**
```
🤝 Study Groups:
- Weekly study sessions: Fridays 1:00-3:00 PM
- Location: ห้องปฏิบัติการคอมพิวเตอร์ 2
- Online collaboration: Discord server (link in LMS)

📋 Peer Review Sessions:
- Scheduled review meetings before major submissions
- Cross-team design reviews
- Collaborative problem-solving sessions

💡 Knowledge Sharing:
- Shared resource repository on GitHub
- Best practices documentation
- Common problem solutions wiki
```

### **🛠️ Technical Support:**
```
💻 Tool Support:
- Draw.io/Lucidchart tutorial sessions
- API documentation tools workshop
- Database design tool guidance
- Version control (Git) assistance

🔧 Development Environment:
- Setup assistance for development tools
- Troubleshooting common technical issues
- Performance optimization guidance
- Deployment preparation support

📚 Resource Access:
- Digital library access for reference materials
- Software licenses for professional tools
- Cloud platform credits for development
- Industry standard template access
```

### **📅 Special Support Sessions:**

**Week 9-10 Intensive Support:**
```
🎯 Extra Office Hours:
- Tuesday & Thursday: 7:00-8:00 PM (Online only)
- Saturday: 10:00 AM-12:00 PM (Walk-in basis)

🔍 Design Review Clinics:
- One-on-one design consultations
- Team architecture review sessions
- Quick feedback on work-in-progress

💬 Q&A Sessions:
- Live Q&A every Wednesday evening
- Recorded sessions available in LMS
- Anonymous question submission available
```

**Emergency Support:**
```
🚨 For Urgent Technical Issues:
- WhatsApp: +66-XXX-XXX-XXXX (Instructor)
- Response within 4 hours during weekdays
- Weekend support for critical assignment issues

📞 Team Conflict Resolution:
- Mediation services for team issues
- Alternative assignment arrangements if needed
- Individual consultation for special circumstances
```

---

## Slide 38: 🎯 Final Words & Motivation
### คำปิดท้ายและการสร้างแรงบันดาลใจ

**🌟 Congratulations on Your Journey So Far!**

### **💪 What You've Accomplished:**

```
🎓 Academic Excellence:
✅ Mastered complex software engineering concepts
✅ Developed professional-level technical documentation skills
✅ Learned industry-standard design methodologies
✅ Built strong foundation for software development career

🛠️ Technical Proficiency:
✅ Can create implementation-ready software designs
✅ Understand how to bridge business requirements with technical solutions  
✅ Proficient in modern software architecture patterns
✅ Ready to contribute to professional development teams

🤝 Professional Skills:
✅ Effective technical communication
✅ Collaborative design and development processes
✅ Critical thinking and problem-solving abilities
✅ Quality assurance and review methodologies
```

### **🚀 Looking Toward Your Future:**

**In the Software Industry:**
```
🏢 You're Now Prepared For:
- Software Architect roles (entry to mid-level)
- Full-stack developer positions
- Technical lead opportunities
- System analyst roles
- Product development team member

💰 Skills That Command High Salaries:
- API design and documentation
- Database architecture and optimization
- Real-time system development
- Professional technical communication
- End-to-end software development
```

**Continuing Your Learning Journey:**
```
🎯 Next Level Skills to Develop:
- Cloud architecture (AWS, Azure, Google Cloud)
- DevOps and CI/CD pipelines
- Advanced security implementations
- Machine learning integration
- Mobile application development

📈 Career Growth Path:
Junior Developer → Senior Developer → Technical Lead → Software Architect
                                  ↘ Product Manager
                                  ↘ Engineering Manager
```

### **🔥 Final Inspiration:**

**Remember Why You Started:**
```
💡 You chose software engineering because:
- You want to build solutions that matter
- Technology can solve real-world problems
- You enjoy creating something from nothing
- You want to be part of the digital transformation

✨ What You've Built Today:
- A complete system design for a real business problem
- Professional documentation that could be implemented tomorrow
- Skills that are immediately valuable to employers
- Confidence to tackle complex technical challenges
```

**The Agent Wallboard System You've Designed:**
```
🎯 Is Not Just an Academic Exercise:
- Call centers worldwide use exactly these systems
- Your design could improve productivity for thousands of workers
- The technical patterns you've learned apply to countless other applications
- You've solved a real business problem with elegant technical solutions

🏆 You Should Feel Proud Because:
- You've created something genuinely useful
- Your work demonstrates professional competency
- You've collaborated effectively with team members
- You've overcome complex technical challenges
```

### **🎊 As You Move Forward:**

**Keep This Mindset:**
```
🌟 Continuous Learning: Technology evolves rapidly, stay curious
🤝 Collaboration: Great software is built by great teams
🎯 Problem-Solving: Focus on solving real problems for real people
💪 Persistence: Challenging projects teach the most valuable lessons
✨ Innovation: Don't just follow patterns, create new solutions
```

**Your Next Mission:**
```
🚀 Implement the system you've designed
📈 Exceed your own expectations
🏢 Prepare for your professional software engineering career
🌍 Use your skills to make a positive impact on the world

Remember: Every expert was once a beginner.
Every professional system started with a design.
Every successful software engineer once sat where you're sitting today.

You have the skills. You have the knowledge. You have the potential.
Now go build something amazing! 🚀✨
```

**See you next week for the implementation phase! 💪**────────────────┘│
│                                                             │
│  ┌─ Messages & Notifications ──────────────────────────────┐│
│  │                                                         ││
│  │  📬 New Messages (3)              [Mark All Read]      ││
│  │                                                         ││
│  │  🔴 [URGENT] Supervisor: Please check queue            ││
│  │      From: Manager1 • 2 min ago                        ││
│  │                                                         ││
│  │  🟡 [INFO] System: Maintenance at 6 PM today           ││
│  │      From: System • 1 hour ago                         ││
│  │                                                         ││
│  │  💬 [MSG] Team: Coffee break anyone?                    ││
│  │      From: A005 • 15 min ago                           ││
│  │                                                         ││
│  └─────────────────────────────────────────────────────────┘│
│                                                             │
│  ┌─ Quick Actions ─────────────────────────────────────────┐│
│  │                                                         ││
│  │  [🏃 Break]  [🍕 Lunch]  [💻 Wrap Up]  [🏠 End Shift]  ││
│  │                                                         ││
│  │  📊 [View Statistics]    💬 [Send Message]             ││
│  │                                                         ││
│  └─────────────────────────────────────────────────────────┘│
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ 🔌 Connected • Last sync: 10:45:23 AM • Session: 2h 15m    │
└─────────────────────────────────────────