# สัปดาห์ที่ 7: การออกแบบสถาปัตยกรรมซอฟต์แวร์ - พื้นฐาน (Part 3/4)
## Component Communication และ Architecture Patterns

---

## Slide 21: 🎨 สร้าง C3 Component Diagram - แผนภาพองค์ประกอบ

### วิธีการสร้างแผนภาพ Components สำหรับ Agent Wallboard System

**🎯 ขั้นตอนการสร้าง C3 Diagram:**

**Step 1: ระบุ Components ใน แต่ละ Container**
```
Desktop App Container:
├── Authentication Component
├── Status Management Component  
├── Notification Component
├── Profile Component
└── WebSocket Client Component

API Server Container:
├── Authentication Service
├── Agent Status Service
├── Message Routing Service
├── WebSocket Manager
├── Database Access Layer
└── Event Bus Component

Database Container:
├── MSSQL Component
├── MongoDB Component
└── Connection Pool Manager
```

**Step 2: กำหนด Interface ระหว่าง Components**
```
Authentication Component → Authentication Service
  Interface: POST /api/auth/login, GET /api/auth/validate

Status Management → Agent Status Service  
  Interface: PUT /api/agents/{id}/status, GET /api/agents/{id}/status

WebSocket Client ↔ WebSocket Manager
  Interface: agent_status_update, message_received, system_alert

Database Access Layer → MSSQL/MongoDB
  Interface: SQL queries, MongoDB operations
```

**Step 3: แสดง Dependencies และ Data Flow**
```
User Input (Status Change)
    ↓
Status Management Component
    ↓ HTTP Request
Agent Status Service  
    ↓ Database Query
Database Access Layer
    ↓ SQL/NoSQL
MSSQL/MongoDB
    ↑ Response
Database Access Layer
    ↑ Service Response  
Agent Status Service
    ↓ WebSocket Event
WebSocket Manager
    ↓ Real-time Update
All Connected Clients
```

**Step 4: ใส่ Technology Details**
- **Communication Protocols:** HTTP/HTTPS, WebSocket, TCP/IP
- **Data Formats:** JSON, SQL Results, MongoDB Documents
- **Authentication:** JWT Tokens, Session Management
- **Error Handling:** Circuit Breaker, Retry Logic

---

## Slide 22: 📊 C3 Diagram - Desktop App Components

### รายละเอียด Components ใน Desktop Application

**🖥️ Agent Desktop App (Electron.js Container):**

```
┌─────────────────────────────────────────────────┐
│               Desktop Application               │
│                 (Electron.js)                   │
│                                                 │
│ ┌─────────────────┐    ┌───────────────────────┐│
│ │  Authentication │    │   Status Management   ││
│ │   Component     │◄──►│     Component         ││  
│ │                 │    │                       ││
│ │• login()        │    │• changeStatus()       ││
│ │• logout()       │    │• getCurrentStatus()   ││
│ │• validateToken()│    │• getHistory()         ││
│ └─────────────────┘    └───────────────────────┘│
│           │                        │            │
│           │            ┌───────────────────────┐│
│           │            │     Notification      ││
│           └───────────►│      Component        ││
│                        │                       ││
│ ┌─────────────────┐    │• showAlert()          ││
│ │   WebSocket     │◄──►│• displayMessage()     ││
│ │ Client Component│    │• updateStatus()       ││
│ │                 │    └───────────────────────┘│
│ │• connect()      │               │             │
│ │• subscribe()    │    ┌───────────────────────┐│
│ │• emit()         │    │   Profile Component   ││
│ │• disconnect()   │◄──►│                       ││
│ └─────────────────┘    │• getProfile()         ││
│           │            │• updatePreferences()  ││
│           │            │• saveSettings()       ││
│           │            └───────────────────────┘│
│           │                                     │
│           ▼ WebSocket Connection                │
└─────────────────────────────────────────────────┘
           │
           ▼ HTTPS/WebSocket  
┌─────────────────────────────────────────────────┐
│                API Server                       │
└─────────────────────────────────────────────────┘
```

**🔗 Component Interactions:**

**Authentication Component:**
- **Interface:** IAuthentication
- **Dependencies:** API Client, Session Storage
- **Responsibilities:** User login/logout, token management

**Status Management Component:**
- **Interface:** IStatusManager  
- **Dependencies:** Authentication, API Client, WebSocket Client
- **Responsibilities:** Agent status changes, status history

**WebSocket Client Component:**
- **Interface:** IWebSocketClient
- **Dependencies:** Authentication (for connection auth)
- **Responsibilities:** Real-time communication, event handling

**Notification Component:**
- **Interface:** INotificationDisplay
- **Dependencies:** WebSocket Client
- **Responsibilities:** Show alerts, messages, status updates

**Profile Component:**
- **Interface:** IProfile
- **Dependencies:** Authentication, API Client
- **Responsibilities:** User preferences, settings management

---

## Slide 23: 🖥️ C3 Diagram - Supervisor Dashboard Components

### รายละเอียด Components ใน Web Dashboard

**🌐 Supervisor Dashboard (Web Container):**

```
┌─────────────────────────────────────────────────┐
│            Supervisor Dashboard                 │
│               (React.js Web)                    │
│                                                 │
│ ┌─────────────────┐    ┌───────────────────────┐│
│ │   Dashboard     │◄──►│   Agent Monitor       ││
│ │ Visualization   │    │    Component          ││
│ │   Component     │    │                       ││
│ │                 │    │• getTeamStatus()      ││
│ │• renderCharts() │    │• monitorAgent()       ││
│ │• updateMetrics()│    │• viewHistory()        ││
│ │• exportReport() │    │• sendMessage()        ││
│ └─────────────────┘    └───────────────────────┘│
│           │                        │            │
│           │            ┌───────────────────────┐│
│           │            │    Message            ││
│           └───────────►│   Management          ││
│                        │    Component          ││
│ ┌─────────────────┐    │                       ││
│ │    Reports      │◄──►│• sendIndividual()     ││
│ │   Component     │    │• broadcast()          ││
│ │                 │    │• messageHistory()     ││
│ │• generateKPI()  │    └───────────────────────┘│
│ │• scheduleReport()│               │            │
│ │• exportPDF()    │    ┌───────────────────────┐│
│ └─────────────────┘    │   Control Panel       ││
│           │            │    Component          ││
│           │◄──────────►│                       ││
│           │            │• teamSettings()       ││
│ ┌─────────────────┐    │• manageAgents()       ││
│ │   WebSocket     │    │• systemConfig()       ││
│ │ Client Component│◄───┘• auditLogs()         ││
│ │                 │    └───────────────────────┘│
│ │• subscribeTeam()│                             │
│ │• handleUpdates()│                             │
│ │• broadcastMsg() │                             │
│ └─────────────────┘                             │
│           │                                     │
│           ▼ WebSocket/HTTPS                     │
└─────────────────────────────────────────────────┘
           │
           ▼ API Calls
┌─────────────────────────────────────────────────┐
│                API Server                       │
└─────────────────────────────────────────────────┘
```

**🔗 Supervisor Dashboard Component Details:**

**Dashboard Visualization Component:**
- **Renders:** Real-time charts, KPI metrics, team overview
- **Updates:** Every 5 seconds via WebSocket
- **Libraries:** Chart.js, D3.js สำหรับ data visualization

**Agent Monitor Component:**  
- **Displays:** Individual agent status, performance metrics
- **Features:** Filter, search, drill-down capabilities
- **Real-time:** Live status updates, activity tracking

**Message Management Component:**
- **Functions:** Send messages to agents, broadcast announcements
- **Message Types:** Individual chat, team broadcast, urgent alerts
- **History:** Message tracking, delivery confirmation

**Reports Component:**
- **Generates:** Daily/weekly/monthly reports
- **Formats:** PDF, Excel, CSV export
- **Scheduling:** Automated report generation

**Control Panel Component:**
- **Administration:** Team settings, user management
- **Configuration:** System settings, alert thresholds
- **Audit:** Activity logs, security monitoring

---

## Slide 24: ⚙️ C3 Diagram - API Server Components

### รายละเอียด Components ใน Backend API Server

**🔧 API Server (Node.js Container):**

```
┌─────────────────────────────────────────────────┐
│                API Server                       │
│               (Node.js + Express)               │
│                                                 │
│ ┌─────────────────┐    ┌───────────────────────┐│
│ │ Authentication  │◄──►│   Agent Status        ││
│ │    Service      │    │     Service           ││
│ │                 │    │                       ││
│ │• authenticate() │    │• updateStatus()       ││
│ │• validateToken()│    │• getStatusHistory()   ││
│ │• createSession()│    │• validateTransition() ││
│ └─────────────────┘    └───────────────────────┘│
│           │                        │            │
│           │ ┌─────────────────────────────────┐ │
│           │ │          Event Bus              │ │
│           │ │         Component               │ │
│           │ │                                 │ │
│           │ │• publish(event, data)          │ │
│           │ │• subscribe(event, handler)     │ │
│           │ │• unsubscribe(event, handler)   │ │
│           │ └─────────────────────────────────┘ │
│           │                   │                 │
│ ┌─────────────────┐          │  ┌──────────────┐│
│ │   WebSocket     │◄─────────┼─►│   Message    ││
│ │    Manager      │          │  │   Routing    ││
│ │                 │          │  │   Service    ││
│ │• handleConn()   │          │  │              ││
│ │• broadcast()    │          │  │• routeMsg()  ││
│ │• manageRooms()  │          │  │• validate()  ││
│ └─────────────────┘          │  │• persist()   ││
│           │                  │  └──────────────┘│
│           │                  │                  │
│ ┌─────────────────────────────────────────────┐ │
│ │        Database Access Layer                │ │
│ │                                             │ │
│ │• executeQuery(sql)                          │ │
│ │• insertDocument(collection, doc)            │ │
│ │• transaction(operations)                    │ │
│ │• getConnection(type)                        │ │
│ └─────────────────────────────────────────────┘ │
│                           │                     │
│                           ▼ Database Queries   │
└─────────────────────────────────────────────────┘
                           │
                           ▼ SQL/NoSQL
┌─────────────────────────────────────────────────┐
│              Database Layer                     │
│        (MSSQL + MongoDB)                        │
└─────────────────────────────────────────────────┘
```

**⚙️ API Server Component Details:**

**Authentication Service:**
- **Strategies:** Local, SSO, LDAP (Strategy Pattern)
- **Token Management:** JWT creation, validation, refresh
- **Session Handling:** Create, validate, destroy sessions

**Agent Status Service:**
- **Business Logic:** Status transition validation
- **Data Operations:** CRUD operations for agent status
- **Event Publishing:** Broadcast status changes via Event Bus

**Message Routing Service:**
- **Routing Logic:** Individual messages, team broadcasts
- **Message Types:** Chat, alerts, announcements (Factory Pattern)
- **Persistence:** Store message history, delivery tracking

**WebSocket Manager:**
- **Connection Management:** Handle connections, disconnections
- **Room Management:** Group users by teams, roles
- **Broadcasting:** Send real-time updates to relevant clients

**Event Bus Component:**
- **Pub-Sub Pattern:** Decouple components via events
- **Event Types:** status_changed, message_sent, user_login
- **Reliability:** Ensure event delivery, handle failures

**Database Access Layer:**
- **Abstraction:** Hide database specifics from services
- **Connection Pooling:** Efficient database connection management
- **Transaction Management:** ACID transactions for critical operations

---

## Slide 25: 🗄️ C3 Diagram - Database Layer Components

### รายละเอียด Components ใน Database Layer

**💾 Database Layer Components:**

```
┌─────────────────────────────────────────────────┐
│                Database Layer                   │
│                                                 │
│ ┌─────────────────┐    ┌───────────────────────┐│
│ │     MSSQL       │◄──►│    Data Sync          ││
│ │   Component     │    │   Component           ││
│ │                 │    │                       ││
│ │• Agent Master   │    │• syncAgentData()      ││
│ │• User Accounts  │    │• reconcileStatus()    ││
│ │• Team Structure │    │• handleConflicts()    ││
│ │• System Config  │    │• auditChanges()       ││
│ └─────────────────┘    └───────────────────────┘│
│           │                        │            │
│           │            ┌───────────────────────┐│
│           │            │     MongoDB           ││
│           └───────────►│    Component          ││
│                        │                       ││
│ ┌─────────────────┐    │• Status Logs          ││
│ │ Connection Pool │◄──►│• Message History      ││
│ │    Manager      │    │• Performance Data     ││
│ │                 │    │• Real-time Analytics  ││
│ │• MSSQL Pool     │    └───────────────────────┘│
│ │• MongoDB Pool   │               │             │
│ │• Health Check   │    ┌───────────────────────┐│
│ │• Load Balance   │    │   Data Security       ││
│ └─────────────────┘◄──►│    Component          ││
│           │            │                       ││
│           │            │• encrypt()            ││
│           │            │• decrypt()            ││
│           │            │• auditLog()           ││
│           │            │• accessControl()      ││
│           │            └───────────────────────┘│
└─────────────────────────────────────────────────┘
```

**🔐 Database Component Responsibilities:**

**MSSQL Component:**
- **Master Data:** Agent profiles, team structures, user accounts
- **Configuration:** System settings, business rules
- **Referential Integrity:** Foreign key constraints, data consistency
- **ACID Transactions:** Critical business operations

**MongoDB Component:**  
- **Real-time Data:** Agent status logs, live activity tracking
- **Message Storage:** Chat history, broadcast messages
- **Analytics Data:** Performance metrics, usage statistics
- **Flexible Schema:** Adaptable document structure

**Data Synchronization Component:**
- **Two-way Sync:** Keep MSSQL and MongoDB consistent  
- **Conflict Resolution:** Handle simultaneous updates
- **Change Detection:** Track data modifications
- **Audit Trail:** Log all synchronization activities

**Connection Pool Manager:**
- **Resource Management:** Optimize database connections
- **Load Balancing:** Distribute queries across instances
- **Health Monitoring:** Track connection status
- **Failover:** Handle database unavailability

**Data Security Component:**
- **Encryption:** Protect sensitive data at rest
- **Access Control:** Role-based database permissions  
- **Audit Logging:** Track all data access
- **Compliance:** Meet security standards

---

## Slide 26: 🔄 Component Interaction Flow

### การไหลของข้อมูลระหว่าง Components

**📊 Complete Interaction Flow - Agent Status Change:**

```
1. User Input (Agent Desktop)
   │
   ▼
2. Status Management Component
   │ validateInput()
   │ showLoading()
   ▼
3. HTTP API Call to Backend
   │ PUT /api/agents/{id}/status
   │ Authorization: Bearer <token>
   ▼
4. Authentication Service
   │ validateToken()
   │ checkPermissions()
   ▼
5. Agent Status Service  
   │ validateStatusTransition()
   │ checkBusinessRules()
   ▼
6. Database Access Layer
   │ beginTransaction()
   │ updateAgentStatus()
   │ logStatusHistory()
   │ commitTransaction()
   ▼
7. Event Bus Publishing
   │ publish('agent_status_changed', data)
   ▼
8. Multiple Subscribers:
   ├── WebSocket Manager
   │   │ broadcastToSupervisors()
   │   │ broadcastToTeam()
   │   ▼
   │   Supervisor Dashboard
   │   │ updateUI()
   │   │ playNotificationSound()
   │
   ├── Analytics Service
   │   │ recordMetric()
   │   │ updatePerformanceData()
   │
   └── Notification Service
       │ sendEmailAlert() (if configured)
       │ sendSMSAlert() (if critical)
```

**⏱️ Timing and Performance:**

**Synchronous Operations (< 200ms):**
- Input validation
- Token authentication
- Business rule checking
- Database updates

**Asynchronous Operations (background):**
- Event broadcasting
- Analytics recording  
- Email/SMS notifications
- Report generation

**Real-time Updates (< 1 second):**
- WebSocket broadcasts
- UI updates
- Dashboard refreshes

---

## Slide 27: 📋 Component Dependencies Matrix

### การวิเคราะห์ Dependencies ระหว่าง Components

**📊 Dependency Matrix for Agent Wallboard System:**

| Component | Auth Service | Agent Status Service | Message Service | WebSocket Manager | Database Layer | Event Bus |
|-----------|:------------:|:-------------------:|:--------------:|:----------------:|:-------------:|:---------:|
| **Authentication Component** | ✅ Direct | ❌ | ❌ | ❌ | ❌ | ❌ |
| **Status Management Component** | ✅ Indirect | ✅ Direct | ❌ | ✅ Direct | ❌ | ❌ |
| **Notification Component** | ❌ | ❌ | ❌ | ✅ Direct | ❌ | ❌ |
| **Dashboard Component** | ✅ Indirect | ✅ Direct | ✅ Direct | ✅ Direct | ❌ | ❌ |
| **Auth Service** | ❌ | ❌ | ❌ | ❌ | ✅ Direct | ✅ Direct |
| **Agent Status Service** | ✅ Direct | ❌ | ❌ | ❌ | ✅ Direct | ✅ Direct |
| **Message Service** | ✅ Direct | ❌ | ❌ | ✅ Direct | ✅ Direct | ✅ Direct |
| **WebSocket Manager** | ✅ Direct | ❌ | ❌ | ❌ | ❌ | ✅ Direct |

**🔍 Dependency Analysis:**

**✅ Good Dependencies (Following Architecture Rules):**
- Frontend components depend on Backend services ✓
- Services depend on Database layer ✓  
- All services use Event Bus for decoupling ✓
- Authentication is used by components that need it ✓

**⚠️ Potential Issues:**
- **WebSocket Manager** has many incoming dependencies
- **Event Bus** is a central point of failure
- **Database Layer** is heavily used (potential bottleneck)

**🛠️ Mitigation Strategies:**

**For WebSocket Manager:**
```javascript
// Use connection pooling and load balancing
class WebSocketManager {
  constructor() {
    this.connectionPools = new Map();
    this.loadBalancer = new RoundRobinLoadBalancer();
  }
  
  broadcast(event, data) {
    const pool = this.loadBalancer.getNextPool();
    return pool.broadcast(event, data);
  }
}
```

**For Event Bus Reliability:**
```javascript
// Implement circuit breaker and fallback
class ResilientEventBus {
  constructor() {
    this.circuitBreaker = new CircuitBreaker();
    this.fallbackQueue = new InMemoryQueue();
  }
  
  async publish(event, data) {
    try {
      await this.circuitBreaker.execute(() => 
        this.eventBus.publish(event, data)
      );
    } catch (error) {
      // Fallback to in-memory queue
      this.fallbackQueue.enqueue({event, data});
    }
  }
}
```

**For Database Layer:**
```javascript  
// Implement connection pooling and caching
class DatabaseAccessLayer {
  constructor() {
    this.connectionPool = new ConnectionPool();
    this.cache = new RedisCache();
  }
  
  async query(sql, params) {
    // Check cache first
    const cacheKey = this.generateCacheKey(sql, params);
    let result = await this.cache.get(cacheKey);
    
    if (!result) {
      const connection = await this.connectionPool.getConnection();
      result = await connection.query(sql, params);
      await this.cache.set(cacheKey, result, 300); // 5 min TTL
    }
    
    return result;
  }
}
```

---

## Slide 28: 🚨 Common Anti-Patterns และ Solutions

### ปัญหาที่พบบ่อยในการออกแบบ Components

**❌ Common Anti-Patterns:**

**1. God Component (Component ที่ทำหน้าที่มากเกินไป)**
```javascript
// ❌ Anti-pattern: ทำทุกอย่าง
class SuperManagerComponent {
  // Authentication
  login() { }
  logout() { }
  
  // Agent Management  
  updateAgentStatus() { }
  getAgentList() { }
  
  // Messaging
  sendMessage() { }
  broadcastAnnouncement() { }
  
  // Reporting
  generateReport() { }
  exportToPDF() { }
  
  // Database
  connectToDatabase() { }
  executeQuery() { }
  
  // UI Management
  renderDashboard() { }
  updateCharts() { }
}
```

**✅ Solution: แยก Components ตาม Single Responsibility**
```javascript
// ✅ Separate responsibilities
class AuthenticationComponent {
  login() { }
  logout() { }
  validateSession() { }
}

class AgentManagementComponent {
  updateAgentStatus() { }
  getAgentList() { }
  monitorAgents() { }
}

class MessagingComponent {
  sendMessage() { }
  broadcastAnnouncement() { }
  getMessageHistory() { }
}
```

**2. Circular Dependencies (การพึ่งพาแบบวงกลม)**
```javascript
// ❌ Anti-pattern: A depends on B, B depends on A
class ComponentA {
  constructor(componentB) {
    this.b = componentB;
  }
  
  doSomething() {
    this.b.helpMe(); // A uses B
  }
}

class ComponentB {
  constructor(componentA) {
    this.a = componentA;
  }
  
  helpMe() {
    this.a.doSomethingElse(); // B uses A - CIRCULAR!
  }
}
```

**✅ Solution: ใช้ Event Bus หรือ Mediator Pattern**
```javascript
// ✅ Break circular dependency with Event Bus
class ComponentA {
  constructor(eventBus) {
    this.eventBus = eventBus;
  }
  
  doSomething() {
    this.eventBus.publish('need_help', { from: 'A', data: '...' });
  }
}

class ComponentB {
  constructor(eventBus) {
    this.eventBus = eventBus;
    this.eventBus.subscribe('need_help', (event) => {
      if (event.from === 'A') {
        this.provideHelp(event.data);
      }
    });
  }
  
  provideHelp(data) {
    // Help without direct dependency on A
    this.eventBus.publish('help_provided', { to: 'A', result: '...' });
  }
}
```

**3. Hidden Dependencies (การพึ่งพาที่ซ่อนอยู่)**
```javascript
// ❌ Anti-pattern: Hidden global dependencies
class UserService {
  getUser(id) {
    // Hidden dependency on global database connection
    return window.database.query(`SELECT * FROM users WHERE id = ${id}`);
  }
  
  sendEmail(user, message) {
    // Hidden dependency on global email service
    return window.emailService.send(user.email, message);
  }
}
```

**✅ Solution: Explicit Dependency Injection**
```javascript
// ✅ Make dependencies explicit
class UserService {
  constructor(database, emailService) {
    this.database = database;
    this.emailService = emailService;
  }
  
  async getUser(id) {
    return await this.database.query('users').find({ id });
  }
  
  async sendEmail(user, message) {
    return await this.emailService.send({
      to: user.email,
      subject: message.subject,
      body: message.body
    });
  }
}

// Clear instantiation with dependencies
const userService = new UserService(
  new DatabaseConnection(),
  new EmailService()
);
```

**4. Tight Coupling Through Concrete Classes**
```javascript
// ❌ Anti-pattern: Depend on concrete implementations
class OrderProcessor {
  constructor() {
    this.emailSender = new SMTPEmailSender(); // Hardcoded concrete class
    this.paymentGateway = new PayPalGateway(); // Hardcoded concrete class
  }
  
  processOrder(order) {
    const payment = this.paymentGateway.charge(order.total);
    this.emailSender.send(order.customerEmail, 'Order confirmed');
  }
}
```

**✅ Solution: Depend on Interfaces/Abstractions**
```javascript
// ✅ Depend on interfaces
class OrderProcessor {
  constructor(emailSender, paymentGateway) {
    this.emailSender = emailSender; // Interface: IEmailSender
    this.paymentGateway = paymentGateway; // Interface: IPaymentGateway
  }
  
  async processOrder(order) {
    const payment = await this.paymentGateway.charge(order.total);
    await this.emailSender.send(order.customerEmail, 'Order confirmed');
  }
}

// Different implementations can be injected
const orderProcessor = new OrderProcessor(
  new SMTPEmailSender(),    // or SendGridEmailSender, AWSEmailSender
  new PayPalGateway()       // or StripeGateway, SquareGateway
);
```

**🎯 Key Takeaways:**
- **Single Responsibility:** หนึ่ง component หนึ่งหน้าที่
- **Explicit Dependencies:** ไม่ซ่อน dependencies
- **Interface-based Design:** พึ่งพา abstractions ไม่ใช่ concrete classes
- **Event-driven Communication:** ลดการพึ่งพาโดยตรง

---

## Slide 29: ✅ Component Design Checklist

### รายการตรวจสอบการออกแบบ Components

**📋 Component Design Quality Checklist:**

**🎯 Single Responsibility Principle:**
- [ ] Component มีเป้าหมายหลักเดียวที่ชัดเจน
- [ ] ทุก method ใน component เกี่ยวข้องกับเป้าหมายเดียวกัน
- [ ] เมื่ออธิบาย component ไม่ต้องใช้คำว่า "และ" หรือ "หรือ"
- [ ] การเปลี่ยนแปลงใน業務 requirement มีผลกับ component เดียว

**🔗 Dependency Management:**
- [ ] Dependencies ถูก inject จากภายนอก (ไม่ new ภายใน)
- [ ] พึ่งพา interfaces/abstractions ไม่ใช่ concrete classes
- [ ] ไม่มี circular dependencies
- [ ] จำนวน dependencies ไม่เกิน 5 ตัวต่อ component

**🎭 Interface Design:**
- [ ] Interface ชื่อชัดเจน บอกหน้าที่ได้
- [ ] Method names เป็น verb ที่อธิบายการกระทำ
- [ ] Parameters และ return types มี strong typing
- [ ] Error handling มีความสอดคล้องกัน

**📦 Encapsulation:**
- [ ] ซ่อนรายละเอียด implementation จากผู้ใช้
- [ ] Public interface น้อยที่สุดเท่าที่จำเป็น
- [ ] Internal state ไม่สามารถเข้าถึงจากภายนอกได้โดยตรง
- [ ] Immutable objects เมื่อเป็นไปได้

**🧪 Testability:**
- [ ] Component สามารถ unit test ได้แยกจากส่วนอื่น
- [ ] Dependencies สามารถ mock ได้ง่าย
- [ ] ไม่ต้องพึ่งพา external resources ในการ test
- [ ] Test coverage อย่างน้อย 80%

**📊 Performance Considerations:**
- [ ] Component ไม่ทำงานที่ไม่จำเป็น
- [ ] มีการ cache ผลลัพธ์ที่เหมาะสม
- [ ] Lazy loading สำหรับ expensive operations
- [ ] Memory leaks ถูกป้องกัน (cleanup resources)

**Agent Wallboard System Specific Checklist:**

**Real-time Components:**
- [ ] WebSocket connections มี reconnection logic
- [ ] Event handlers มี error boundaries
- [ ] Real-time updates ไม่ block UI thread
- [ ] มี fallback mechanism เมื่อ connection หลุด

**Authentication Components:**
- [ ] Tokens มี expiration handling
- [ ] Session timeout มีการแจ้งเตือน
- [ ] Sensitive data ไม่เก็บใน localStorage
- [ ] Multi-factor authentication support

**Status Management:**
- [ ] Status transitions มี validation
- [ ] Status history มี audit trail
- [ ] Concurrent status changes มีการจัดการ
- [ ] Status conflicts มีการ resolve

**Message Components:**
- [ ] Message delivery มี confirmation
- [ ] Message priority มีการจัดการ
- [ ] Message history มี pagination
- [ ] Offline messages มี queue mechanism

---

## Slide 30: 🎯 Component Architecture Summary

### สรุปหลักการออกแบบ Component Architecture

**🏆 Key Principles ที่ได้เรียนรู้:**

**1. 🧩 Component-Based Thinking**
- **แยกตามหน้าที่:** แต่ละ component รับผิดชอบสิ่งเดียว
- **Interface-driven:** ออกแบบ interface ก่อน implementation
- **Reusable:** Component สามารถใช้ซ้ำได้ในบริบทต่างๆ

**2. 🔗 Dependency Management**
- **Loose Coupling:** Components พึ่งพากันน้อยที่สุด
- **Dependency Injection:** ส่ง dependencies จากภายนอก
- **Interface Segregation:** แยก interface ให้เฉพาะเจาะจง

**3. 📡 Communication Patterns**
- **Event-Driven:** ใช้ events สำหรับ real-time communication
- **API Gateway:** จุดเข้าเดียวสำหรับ external clients
- **CQRS:** แยก read และ write operations เพื่อ performance

**4. 🏗️ Architecture Patterns**
- **Layered Architecture:** แยกชั้นตาม responsibilities
- **Component Composition:** รวม components เป็นระบบใหญ่
- **Pattern Integration:** ใช้ design patterns ร่วมกับ components

**📊 Agent Wallboard System Architecture Overview:**

```
Frontend Tier (Components):
├── Authentication Component
├── Status Management Component  
├── Dashboard Visualization Component
├── Message Management Component
└── Real-time Notification Component
                    ↓ HTTP/WebSocket
Backend Tier (Services):
├── Authentication Service
├── Agent Status Service
├── Message Routing Service
├── WebSocket Connection Manager
└── Event Bus Component
                    ↓ Database Queries
Data Tier (Components):
├── MSSQL Component (Master Data)
├── MongoDB Component (Real-time Data)
├── Connection Pool Manager
└── Data Synchronization Component
```

**🎯 Benefits ที่ได้รับ:**
- **Maintainability:** แก้ไข component เดียวไม่กระทบส่วนอื่น
- **Scalability:** Scale components แยกกันตาม load
- **Testability:** Test แต่ละ component แยกได้
- **Team Productivity:** ทีมทำงานแยก components ได้
- **Technology Flexibility:** เปลี่ยนเทคโนโลยีของ component ได้

**🚀 Next Steps สำหรับสัปดาห์หน้า:**
- **C4 Level 4 (Code):** Class diagrams, sequence diagrams
- **API Design:** REST endpoints, WebSocket events
- **Database Design:** Schema design, relationships
- **Implementation Planning:** Sprint planning, task breakdown

**🔧 Tools สำหรับการพัฒนา:**
- **Diagram Tools:** Draw.io, Lucidchart, PlantUML
- **Code Structure:** TypeScript interfaces, JSDoc
- **Testing:** Jest, Mocha, Postman
- **Documentation:** Swagger/OpenAPI, README files
