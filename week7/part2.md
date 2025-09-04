# สัปดาห์ที่ 7: การออกแบบสถาปัตยกรรมซอฟต์แวร์ - พื้นฐาน (Part 2/4)
## Component Design Principles

---

## Slide 11: 🏗️ Component Design Principles - High Cohesion

### หลักการ High Cohesion - ความเข้มแข็งภายใน

**💡 High Cohesion = ส่วนต่างๆ ภายใน Component ทำงานร่วมกันเพื่อเป้าหมายเดียว**

**🏠 เปรียบเทียบกับห้องครัว:**
- **ห้องครัวที่ดี:** เตา, อ่าง, ตู้เย็น, อุปกรณ์ทำครัว → ทุกอย่างเพื่อการทำอาหาร
- **ห้องครัวที่ไม่ดี:** เตา, อ่าง, โต๊ะทำงาน, เครื่องซักผ้า → วัตถุประสงค์ปะปน

**💻 ใน Agent Wallboard System:**

**✅ High Cohesion Example - Authentication Component:**
```javascript
class AuthenticationComponent {
  // ทุกอย่างเกี่ยวกับการ authenticate
  login(credentials)           // เข้าสู่ระบบ
  logout()                    // ออกจากระบบ  
  validateSession()           // ตรวจสอบ session
  refreshToken()              // ต่ออายุ token
  hashPassword(password)      // เข้ารหัส password
  getCurrentUser()            // ดึงข้อมูล user ปัจจุบัน
}
```
**เป้าหมายเดียว:** จัดการเรื่องการยืนยันตัวตน

**❌ Low Cohesion Example - Mixed Component:**
```javascript
class MixedComponent {
  login(credentials)           // Authentication
  sendMessage(message)         // Messaging  
  generateReport()            // Reporting
  updateAgentStatus()         // Status Management
  connectDatabase()           // Database
}
```
**ปัญหา:** ทำหลายอย่าง, แก้ไขยาก, ทดสอบยาก

**🎯 วิธีการวัด High Cohesion:**
- **LCOM (Lack of Cohesion of Methods):** Method ใน class ใช้ instance variables เดียวกันมากแค่ไหน
- **Single Responsibility:** Component ทำหน้าที่เดียว
- **Related Functionality:** Functions ที่เกี่ยวข้องกันอยู่ด้วยกัน

---

## Slide 12: 🔗 Component Design Principles - Loose Coupling

### หลักการ Loose Coupling - การพึ่งพาที่น้อย

**💡 Loose Coupling = Components พึ่งพากันน้อย, เปลี่ยนแปลงหนึ่งไม่กระทบอีกมาก**

**🏠 เปรียบเทียบกับสายไฟในบ้าน:**
- **Loose Coupling:** แต่ละห้องมีเบรกเกอร์แยก → ห้องหนึ่งไฟดับไม่กระทบห้องอื่น
- **Tight Coupling:** ไฟทั้งบ้านเบรกเกอร์เดียว → เบรกเกอร์หลักดับทุกห้องมืด

**💻 ใน Agent Wallboard System:**

**✅ Loose Coupling Example:**
```javascript
// Authentication Service ไม่รู้รายละเอียดของ Database
class AuthenticationService {
  constructor(databaseAdapter) {  // Dependency Injection
    this.db = databaseAdapter;
  }
  
  async authenticate(credentials) {
    // ใช้ interface ของ database ไม่สนว่าเป็น MSSQL หรือ MongoDB
    return await this.db.findUser(credentials.username);
  }
}

// Database Adapter ซ่อนรายละเอียด implementation
interface DatabaseAdapter {
  findUser(username): Promise<User>;
  saveUser(user): Promise<void>;
}
```

**❌ Tight Coupling Example:**
```javascript  
class AuthenticationService {
  async authenticate(credentials) {
    // Hardcoded dependency - ผูกติดกับ MSSQL
    const connection = new MSSQL.connect('server=...');
    const result = await connection.query(`
      SELECT * FROM Users WHERE username = '${credentials.username}'
    `);
    // ถ้าเปลี่ยนจาก MSSQL เป็น MongoDB ต้องแก้โค้ดทั้งหมด
  }
}
```

**🎯 เทคนิคสำหรับ Loose Coupling:**

**1. Dependency Injection**
- ส่ง dependencies ผ่าน constructor หรือ method parameters
- ไม่สร้าง dependencies ภายใน component

**2. Interface-based Programming**  
- พึ่งพา interfaces ไม่ใช่ concrete classes
- เปลี่ยน implementation ได้โดยไม่กระทบผู้ใช้

**3. Event-Driven Communication**
- ใช้ events แทนการเรียกฟังก์ชันตรงๆ
- Publisher ไม่รู้ว่ามี subscriber คนไหนบ้าง

---

## Slide 13: 🔌 Interface Segregation for Components

### หลักการ Interface Segregation - แบ่งแยก Interface

**💡 Interface Segregation = แบ่ง Interface ให้เฉพาะเจาะจง ไม่บังคับใช้สิ่งที่ไม่ต้องการ**

**🏠 เปรียบเทียบกับเครื่องใช้ไฟฟ้า:**
- **ดี:** รีโมททีวี (ปุ่มเฉพาะทีวี), รีโมทแอร์ (ปุ่มเฉพาะแอร์)
- **ไม่ดี:** รีโมทเดียวควบคุมทุกอย่าง (ทีวี+แอร์+เครื่องเสียง) → ใช้งานยาก

**💻 ใน Agent Wallboard System:**

**✅ Good Interface Segregation:**
```javascript
// แยก interface ตามหน้าที่
interface UserReader {
  getUser(id: string): Promise<User>;
  getUsersByTeam(teamId: string): Promise<User[]>;
}

interface UserWriter {
  createUser(user: User): Promise<void>;
  updateUser(id: string, updates: Partial<User>): Promise<void>;
  deleteUser(id: string): Promise<void>;
}

interface UserAuthenticator {
  authenticate(credentials: Credentials): Promise<AuthResult>;
  validateToken(token: string): Promise<boolean>;
}

// Component ใช้เฉพาะ interface ที่ต้องการ
class DashboardComponent implements UserReader {
  // ใช้เฉพาะการอ่านข้อมูล ไม่สามารถลบ/แก้ไขได้
}

class AdminComponent implements UserReader, UserWriter {
  // ใช้ทั้งอ่านและเขียน
}

class LoginComponent implements UserAuthenticator {
  // ใช้เฉพาะการ authenticate
}
```

**❌ Poor Interface Segregation:**
```javascript
// Interface ใหญ่เกินไป บังคับให้ implement ทุกอย่าง
interface UserManager {
  getUser(id: string): Promise<User>;
  createUser(user: User): Promise<void>;
  updateUser(id: string, updates: Partial<User>): Promise<void>;
  deleteUser(id: string): Promise<void>;
  authenticate(credentials: Credentials): Promise<AuthResult>;
  generateReport(): Promise<Report>;
  sendEmail(email: Email): Promise<void>;
  backupData(): Promise<void>;
}

// ทุก component ต้อง implement ทุกอย่าง แม้ไม่ต้องการ
class DashboardComponent implements UserManager {
  // ต้อง implement ทั้งหมด แม้ว่าจะใช้แค่ getUser
  createUser() { throw new Error("Not supported"); }
  deleteUser() { throw new Error("Not supported"); }
  // ... บังคับเขียนอีกเยอะ
}
```

---

## Slide 14: 💉 Dependency Injection Patterns

### การจัดการ Dependencies อย่างมีประสิทธิภาพ

**💡 Dependency Injection = ส่ง dependencies จากภายนอก ไม่สร้างภายใน component**

**🏠 เปรียบเทียบกับการทำอาหาร:**
- **DI:** แม่ครัวเตรียมส่วนประกอบให้ → เชฟนำมาทำอาหาร
- **ไม่ใช่ DI:** เชฟต้องออกไปซื้อวัตถุดิบเอง → ผูกติดกับร้านค้าเฉพาะ

**💻 ใน Agent Wallboard System:**

**1. Constructor Injection**
```javascript
class AgentStatusService {
  constructor(databaseAdapter, eventBus, logger) {
    this.db = databaseAdapter;        // Database access
    this.eventBus = eventBus;         // Event publishing
    this.logger = logger;             // Logging
  }
  
  async updateStatus(agentId, status) {
    await this.db.updateAgentStatus(agentId, status);
    this.eventBus.publish('status_changed', {agentId, status});
    this.logger.info(`Agent ${agentId} changed to ${status}`);
  }
}

// การใช้งาน
const service = new AgentStatusService(
  new DatabaseAdapter('MSSQL'),
  new EventBus(),
  new ConsoleLogger()
);
```

**2. Method Injection**
```javascript
class MessageService {
  sendMessage(message, messageSender) {
    // รับ dependency ผ่าน method parameter
    return messageSender.send(message);
  }
}

// การใช้งาน
messageService.sendMessage(message, new EmailSender());
messageService.sendMessage(message, new SMSSender());
```

**3. Interface Injection (Property Injection)**
```javascript
class DashboardComponent {
  // Properties ที่จะ inject
  dataService: DataService;
  chartLibrary: ChartLibrary;
  
  initialize() {
    // ใช้ dependencies ที่ inject มา
    const data = this.dataService.getDashboardData();
    this.chartLibrary.renderChart(data);
  }
}

// Container จะ inject dependencies
container.register('dashboardComponent', DashboardComponent);
container.register('dataService', DatabaseDataService);
container.register('chartLibrary', D3ChartLibrary);
```

**🎯 ประโยชน์ของ Dependency Injection:**
- **Testing:** Mock dependencies ได้ง่าย
- **Flexibility:** เปลี่ยน implementation ได้โดยไม่แก้โค้ด
- **Maintainability:** Component ไม่ผูกติดกับ concrete classes
- **Reusability:** Component ใช้กับ dependencies ต่างๆ ได้

---

## Slide 15: 🔄 Component Communication Patterns

### รูปแบบการสื่อสารระหว่าง Components

**💻 ใน Agent Wallboard System มีการสื่อสาร 4 รูปแบบหลัก:**

**1. 📞 Direct Method Calls (การเรียกใช้ตรง)**
```javascript
// Frontend Component เรียก Backend Service ผ่าน API
class StatusManagementComponent {
  async changeStatus(newStatus) {
    // เรียก API endpoint โดยตรง
    const result = await this.apiClient.post('/api/agents/status', {
      agentId: this.currentAgentId,
      status: newStatus
    });
    
    if (result.success) {
      this.updateUI(newStatus);
    }
  }
}
```
**ใช้เมื่อ:** การสื่อสารแบบ synchronous, ต้องการ response ทันที

**2. 🔔 Event-Driven Communication (การสื่อสารผ่าน Events)**
```javascript
// Publisher - Agent Status Service
class AgentStatusService {
  async updateStatus(agentId, status) {
    await this.db.updateStatus(agentId, status);
    
    // Publish event ไม่ต้องรู้ว่าใครจะรับ
    this.eventBus.publish('agent_status_changed', {
      agentId,
      status,
      timestamp: new Date()
    });
  }
}

// Subscribers - หลาย components สามารถ subscribe ได้
class DashboardComponent {
  constructor(eventBus) {
    eventBus.subscribe('agent_status_changed', (data) => {
      this.updateDashboard(data);
    });
  }
}

class NotificationComponent {
  constructor(eventBus) {
    eventBus.subscribe('agent_status_changed', (data) => {
      this.showNotification(`Agent ${data.agentId} is now ${data.status}`);
    });
  }
}
```
**ใช้เมื่อ:** Real-time updates, หลาย components ต้องรับข้อมูลเดียวกัน

**3. 📨 Message Passing (การส่ง Messages)**
```javascript
// Message Queue สำหรับ Async Processing
class MessageRoutingService {
  async sendMessage(message) {
    // เพิ่มใน message queue
    await this.messageQueue.enqueue({
      type: 'SEND_MESSAGE',
      from: message.senderId,
      to: message.recipientId,
      content: message.content,
      priority: message.priority
    });
  }
}

// Background Worker
class MessageProcessor {
  async processMessages() {
    const message = await this.messageQueue.dequeue();
    
    switch (message.type) {
      case 'SEND_MESSAGE':
        await this.deliverMessage(message);
        break;
      case 'BROADCAST_MESSAGE':
        await this.broadcastToTeam(message);
        break;
    }
  }
}
```
**ใช้เมื่อ:** Asynchronous processing, Background tasks, Load balancing

**4. 🌐 WebSocket Communication (Real-time Bidirectional)**
```javascript
// WebSocket Manager
class WebSocketManager {
  broadcastStatusUpdate(agentData) {
    // ส่งไปยัง clients ทั้งหมดที่ subscribe
    this.connectedClients.forEach(client => {
      if (client.subscriptions.includes('agent_status')) {
        client.socket.emit('agent_status_update', agentData);
      }
    });
  }
}

// Frontend WebSocket Client
class WebSocketClient {
  constructor() {
    this.socket = io.connect();
    
    this.socket.on('agent_status_update', (data) => {
      // อัพเดท UI แบบ real-time
      this.updateAgentDisplay(data);
    });
  }
}
```
**ใช้เมื่อ:** Real-time updates, Bidirectional communication, Live data

---

## Slide 16: 🏛️ Event-Driven Architecture สำหรับ Real-time Updates

### การออกแบบระบบ Event-Driven

**💡 Event-Driven Architecture = ระบบที่ใช้ Events เป็นหลักในการสื่อสาร**

**🎯 ส่วนประกอบหลัก:**

**1. Event Producers (ผู้ผลิต Events)**
- Agent Status Service → สร้าง `agent_status_changed` event
- Message Service → สร้าง `message_sent` event  
- System Monitor → สร้าง `system_alert` event

**2. Event Bus/Message Broker (ตัวกลางจัดส่ง)**
```javascript
class EventBus {
  constructor() {
    this.subscribers = new Map();
  }
  
  subscribe(eventType, handler) {
    if (!this.subscribers.has(eventType)) {
      this.subscribers.set(eventType, []);
    }
    this.subscribers.get(eventType).push(handler);
  }
  
  publish(eventType, eventData) {
    if (this.subscribers.has(eventType)) {
      this.subscribers.get(eventType).forEach(handler => {
        // Async execution ไม่ block publisher
        setImmediate(() => handler(eventData));
      });
    }
  }
  
  unsubscribe(eventType, handler) {
    if (this.subscribers.has(eventType)) {
      const handlers = this.subscribers.get(eventType);
      const index = handlers.indexOf(handler);
      if (index > -1) {
        handlers.splice(index, 1);
      }
    }
  }
}
```

**3. Event Consumers (ผู้รับ Events)**
- Dashboard Components → รับ `agent_status_changed` เพื่ออัพเดท UI
- Notification Service → รับ events เพื่อส่ง alerts
- Analytics Service → รับ events เพื่อ log และวิเคราะห์

**🔄 Event Flow ใน Agent Wallboard System:**
```
Agent เปลี่ยนสถานะ
    ↓
Agent Status Service receives request
    ↓  
Update database
    ↓
Publish 'agent_status_changed' event
    ↓
Event Bus distributes to subscribers:
    ├── Dashboard Component (อัพเดท UI)
    ├── Notification Service (ส่ง alert)
    ├── Analytics Service (บันทึก log)
    └── WebSocket Manager (broadcast ไปยัง clients)
```

**✅ ประโยชน์:**
- **Decoupling:** Components ไม่ต้องรู้จักกันโดยตรง
- **Scalability:** เพิ่ม event consumers ได้ง่าย
- **Flexibility:** เปลี่ยน business logic โดยไม่กระทบ producers
- **Real-time:** Events ถูกส่งทันทีเมื่อเกิดขึ้น

---

## Slide 17: 🚪 API Gateway Pattern สำหรับ External Communications

### การจัดการการสื่อสารภายนอกแบบรวมศูนย์

**💡 API Gateway = จุดเข้าเดียวสำหรับ external clients เชื่อมต่อกับ backend services**

**🏢 เปรียบเทียบกับแผนกต้อนรับ:**
- **ไม่มี Gateway:** ลูกค้าต้องรู้ว่าจะไปหาแผนกไหน เบอร์โทรอะไร
- **มี Gateway:** ลูกค้าโทรเบอร์เดียว แผนกต้อนรับจะต่อให้

**💻 ใน Agent Wallboard System:**

**API Gateway Component:**
```javascript
class APIGateway {
  constructor() {
    this.authService = new AuthenticationService();
    this.agentService = new AgentStatusService();
    this.messageService = new MessageRoutingService();
    this.dashboardService = new DashboardService();
  }
  
  // Single entry point สำหรับ external clients
  async handleRequest(request) {
    // 1. Authentication & Authorization
    const user = await this.authService.validateToken(request.token);
    if (!user) {
      return { status: 401, error: 'Unauthorized' };
    }
    
    // 2. Rate Limiting
    if (await this.isRateLimited(user.id)) {
      return { status: 429, error: 'Too many requests' };
    }
    
    // 3. Route to appropriate service
    switch (request.endpoint) {
      case '/api/agents/status':
        return await this.agentService.handleStatusRequest(request, user);
        
      case '/api/messages':
        return await this.messageService.handleMessageRequest(request, user);
        
      case '/api/dashboard':
        return await this.dashboardService.handleDashboardRequest(request, user);
        
      default:
        return { status: 404, error: 'Endpoint not found' };
    }
  }
  
  // 4. Response formatting
  formatResponse(data, format = 'json') {
    switch (format) {
      case 'json':
        return JSON.stringify(data);
      case 'xml':
        return this.convertToXML(data);
      default:
        return data;
    }
  }
}
```

**🎯 หน้าที่ของ API Gateway:**

**1. Authentication & Authorization**
- ตรวจสอบ JWT tokens
- Validate user permissions
- Session management

**2. Request Routing**
- นำ request ไปยัง backend service ที่ถูกต้อง
- Load balancing ระหว่าง service instances

**3. Protocol Translation**
- รับ HTTP requests จาก clients
- แปลงเป็น internal protocols (gRPC, message queues)

**4. Cross-cutting Concerns**
- Rate limiting (จำกัดจำนวน requests)
- Logging และ monitoring
- Error handling และ circuit breaking

**5. Response Aggregation**
```javascript
// รวมข้อมูลจากหลาย services
async getDashboardData(userId) {
  const [agents, messages, reports] = await Promise.all([
    this.agentService.getTeamAgents(userId),
    this.messageService.getRecentMessages(userId),
    this.reportService.getKPIData(userId)
  ]);
  
  return {
    agents,
    messages,
    reports,
    lastUpdated: new Date()
  };
}
```

**✅ ประโยชน์:**
- **Single Entry Point:** Clients รู้จัก endpoint เดียว
- **Security:** Centralized authentication/authorization
- **Monitoring:** รวม logs และ metrics
- **Flexibility:** เปลี่ยน backend services โดย clients ไม่รู้

---

## Slide 18: 📊 CQRS Pattern สำหรับ Read/Write Separation

### การแยก Command และ Query Operations

**💡 CQRS (Command Query Responsibility Segregation) = แยกการอ่าน (Query) และการเขียน (Command)**

**🏪 เปรียบเทียบกับร้านค้า:**
- **Command Side:** แคชเชียร์ (รับเงิน, ออกใบเสร็จ) → เน้นความถูกต้อง
- **Query Side:** พนักงานต้อนรับ (ตอบคำถาม, แนะนำสินค้า) → เน้นความเร็ว

**💻 ใน Agent Wallboard System:**

**Command Side (Write Operations):**
```javascript
class AgentStatusCommandHandler {
  constructor(database, eventBus) {
    this.db = database;  // MSSQL for ACID transactions
    this.eventBus = eventBus;
  }
  
  async handleChangeStatusCommand(command) {
    // 1. Validate command
    if (!this.isValidStatusTransition(command.oldStatus, command.newStatus)) {
      throw new Error('Invalid status transition');
    }
    
    // 2. Execute business logic
    await this.db.transaction(async (trx) => {
      await trx('agent_status_history').insert({
        agentId: command.agentId,
        oldStatus: command.oldStatus,
        newStatus: command.newStatus,
        changedBy: command.userId,
        timestamp: new Date()
      });
      
      await trx('agents').update({
        currentStatus: command.newStatus,
        lastStatusChange: new Date()
      }).where('id', command.agentId);
    });
    
    // 3. Publish event for read side
    this.eventBus.publish('agent_status_changed', {
      agentId: command.agentId,
      newStatus: command.newStatus,
      timestamp: new Date()
    });
  }
}
```

**Query Side (Read Operations):**
```javascript
class AgentStatusQueryHandler {
  constructor(readDatabase, cache) {
    this.readDb = readDatabase;  // MongoDB for fast reads
    this.cache = cache;          // Redis for ultra-fast queries
  }
  
  async getCurrentTeamStatus(teamId) {
    // 1. Try cache first
    const cached = await this.cache.get(`team_status_${teamId}`);
    if (cached) {
      return JSON.parse(cached);
    }
    
    // 2. Query read database (optimized for queries)
    const agents = await this.readDb.collection('agent_status_views')
      .find({ 
        teamId: teamId,
        active: true 
      })
      .project({
        agentId: 1,
        name: 1,
        currentStatus: 1,
        statusDuration: 1,
        lastActivity: 1
      })
      .sort({ name: 1 })
      .toArray();
    
    // 3. Cache for future requests
    await this.cache.setex(`team_status_${teamId}`, 60, JSON.stringify(agents));
    
    return agents;
  }
  
  async getStatusHistory(agentId, dateRange) {
    // Complex analytical query - optimized read model
    return await this.readDb.collection('agent_status_analytics')
      .aggregate([
        { $match: { agentId, date: { $gte: dateRange.start, $lte: dateRange.end } } },
        { $group: {
            _id: '$status',
            totalDuration: { $sum: '$durationMinutes' },
            count: { $sum: 1 }
          }
        }
      ]).toArray();
  }
}
```

**🔄 CQRS Flow ใน Agent Wallboard System:**
```
Agent เปลี่ยนสถานะ (Command)
    ↓
Command Handler:
  ├── Validate business rules
  ├── Update MSSQL (ACID transaction)
  └── Publish event
    ↓
Event Handler อัพเดท Read Models:
  ├── MongoDB views สำหรับ queries
  ├── Redis cache สำหรับ real-time data
  └── Analytics database สำหรับรายงาน
    ↓
Dashboard queries (Query Side):
  ├── Read from optimized MongoDB collections
  └── Use Redis cache สำหรับข้อมูลที่ใช้บ่อย
```

**✅ ประโยชน์ของ CQRS:**
- **Performance:** แยก optimize read/write operations
- **Scalability:** Scale read และ write แยกกัน
- **Flexibility:** Read models ปรับได้ตาม UI requirements
- **Consistency:** Write side รับประกัน business rules

**⚠️ ข้อพิจารณา:**
- **Complexity:** เพิ่มความซับซ้อน
- **Eventual Consistency:** Read side อาจล่าช้าเล็กน้อย
- **Data Synchronization:** ต้อง sync ระหว่าง write/read sides

---

## Slide 19: 🔧 Component Interface Design

### การออกแบบ Interface ที่มีประสิทธิภาพ

**💡 Component Interface = สัญญาการทำงานระหว่าง Components**

**🎯 หลักการออกแบบ Interface:**

**1. Clear and Descriptive Naming**
```javascript
// ✅ Good naming
interface AgentStatusService {
  getCurrentStatus(agentId: string): Promise<AgentStatus>;
  updateStatus(agentId: string, newStatus: StatusType): Promise<void>;
  getStatusHistory(agentId: string, dateRange: DateRange): Promise<StatusHistory[]>;
}

// ❌ Poor naming  
interface AgentService {
  get(id: string): Promise<any>;
  set(id: string, data: any): Promise<void>;
  list(params: any): Promise<any[]>;
}
```

**2. Single Responsibility per Interface**
```javascript
// ✅ Focused interfaces
interface MessageSender {
  sendMessage(message: Message): Promise<MessageResult>;
  sendBroadcast(message: Message, recipients: string[]): Promise<BroadcastResult>;
}

interface MessageRetriever {
  getMessage(messageId: string): Promise<Message>;
  getMessageHistory(userId: string, limit: number): Promise<Message[]>;
}

interface MessageValidator {
  validateMessage(message: Message): ValidationResult;
  sanitizeContent(content: string): string;
}

// ❌ Mixed responsibilities
interface MessageManager {
  sendMessage(message: Message): Promise<MessageResult>;
  getMessage(messageId: string): Promise<Message>;
  validateMessage(message: Message): ValidationResult;
  generateReport(): Promise<Report>;
  backupMessages(): Promise<void>;
}
```

**3. Consistent Error Handling**
```javascript
// Standardized error response
interface APIResponse<T> {
  success: boolean;
  data?: T;
  error?: {
    code: string;
    message: string;
    details?: any;
  };
  metadata?: {
    timestamp: Date;
    requestId: string;
  };
}

// Usage in interface
interface AgentStatusService {
  updateStatus(agentId: string, status: StatusType): Promise<APIResponse<void>>;
  getCurrentStatus(agentId: string): Promise<APIResponse<AgentStatus>>;
}
```

**4. Versioning Strategy**
```javascript
// Interface versioning
interface AgentStatusServiceV1 {
  updateStatus(agentId: string, status: string): Promise<void>;
}

interface AgentStatusServiceV2 {
  updateStatus(agentId: string, status: StatusType, reason?: string): Promise<void>;
  updateStatusWithValidation(request: StatusUpdateRequest): Promise<StatusUpdateResult>;
}

// Backward compatibility
class AgentStatusServiceAdapter implements AgentStatusServiceV1, AgentStatusServiceV2 {
  // Implement both versions
}
```

**🔄 Interface Examples for Agent Wallboard System:**

**Authentication Interface:**
```javascript
interface AuthenticationService {
  // Core authentication
  authenticate(credentials: LoginCredentials): Promise<AuthenticationResult>;
  validateToken(token: string): Promise<TokenValidationResult>;
  refreshToken(refreshToken: string): Promise<TokenRefreshResult>;
  
  // Session management
  createSession(userId: string): Promise<Session>;
  getSession(sessionId: string): Promise<Session | null>;
  destroySession(sessionId: string): Promise<void>;
}

interface LoginCredentials {
  username: string;
  password: string;
  authMethod: 'local' | 'sso' | 'ldap';
}

interface AuthenticationResult {
  success: boolean;
  user?: User;
  accessToken?: string;
  refreshToken?: string;
  expiresIn?: number;
  error?: string;
}
```

**Dashboard Interface:**
```javascript
interface DashboardService {
  // Data retrieval
  getDashboardData(userId: string, filters?: DashboardFilters): Promise<DashboardData>;
  getAgentSummary(teamId: string): Promise<AgentSummary>;
  getPerformanceMetrics(teamId: string, period: TimePeriod): Promise<PerformanceMetrics>;
  
  // Real-time subscriptions
  subscribeToDashboardUpdates(userId: string, callback: (update: DashboardUpdate) => void): void;
  unsubscribeFromDashboardUpdates(userId: string): void;
}

interface DashboardData {
  agents: AgentStatus[];
  teamMetrics: TeamMetrics;
  alerts: SystemAlert[];
  lastUpdated: Date;
}
```

---

## Slide 20: ✅ Interface Design Best Practices

### หลักปฏิบัติที่ดีในการออกแบบ Interface

**🎯 Best Practices สำหรับ Agent Wallboard System:**

**1. Use TypeScript/Strong Typing**
```typescript
// Define precise types
type AgentStatusType = 'Available' | 'Busy' | 'Away' | 'Break' | 'Offline';
type MessagePriority = 'Low' | 'Normal' | 'High' | 'Critical';

interface StatusUpdateRequest {
  agentId: string;
  newStatus: AgentStatusType;
  reason?: string;
  scheduledTime?: Date;  // For scheduled status changes
}

interface MessageRequest {
  senderId: string;
  recipientIds: string[];
  content: string;
  priority: MessagePriority;
  attachments?: FileAttachment[];
}
```

**2. Provide Default Values and Optional Parameters**
```typescript
interface DashboardQueryOptions {
  teamId?: string;           // Optional - default to user's team
  statusFilter?: AgentStatusType[];  // Optional - default to all statuses
  limit?: number;            // Optional - default to 50
  sortBy?: 'name' | 'status' | 'lastActivity';  // Optional - default to 'name'
  includeInactive?: boolean;  // Optional - default to false
}

// Implementation with defaults
async getDashboardData(userId: string, options: DashboardQueryOptions = {}): Promise<DashboardData> {
  const {
    teamId = await this.getUserTeam(userId),
    statusFilter = ['Available', 'Busy', 'Away', 'Break'],
    limit = 50,
    sortBy = 'name',
    includeInactive = false
  } = options;
  
  // Implementation...
}
```

**3. Design for Extensibility**
```typescript
// Base interface
interface BaseMessage {
  id: string;
  senderId: string;
  recipientId: string;
  content: string;
  timestamp: Date;
  type: string;
}

// Extended interfaces
interface ChatMessage extends BaseMessage {
  type: 'chat';
  attachments?: FileAttachment[];
}

interface SystemAlert extends BaseMessage {
  type: 'alert';
  severity: 'info' | 'warning' | 'error';
  actionRequired: boolean;
}

interface StatusNotification extends BaseMessage {
  type: 'status';
  agentId: string;
  oldStatus: AgentStatusType;
  newStatus: AgentStatusType;
}

// Union type for all message types
type Message = ChatMessage | SystemAlert | StatusNotification;

// Service interface that can handle all types
interface MessageService {
  sendMessage<T extends Message>(message: T): Promise<void>;
  getMessages(userId: string): Promise<Message[]>;
}
```

**4. Include Metadata and Context**
```typescript
interface ServiceResponse<T> {
  data: T;
  metadata: {
    requestId: string;
    timestamp: Date;
    processingTime: number;
    version: string;
  };
  pagination?: {
    total: number;
    page: number;
    pageSize: number;
    hasNext: boolean;
  };
}

interface AgentStatusHistory {
  agentId: string;
  statusChanges: StatusChange[];
  summary: {
    totalDuration: number;
    mostCommonStatus: AgentStatusType;
    statusDistribution: Record<AgentStatusType, number>;
  };
  queryInfo: {
    dateRange: DateRange;
    generatedAt: Date;
    dataSource: 'live' | 'cached' | 'historical';
  };
}
```

**5. Error Handling Patterns**
```typescript
// Custom error types
class ValidationError extends Error {
  constructor(field: string, message: string) {
    super(`Validation error in ${field}: ${message}`);
    this.name = 'ValidationError';
  }
}

class BusinessRuleError extends Error {
  constructor(rule: string, context: any) {
    super(`Business rule violated: ${rule}`);
    this.name = 'BusinessRuleError';
    this.context = context;
  }
}

// Interface with proper error handling
interface AgentStatusService {
  updateStatus(request: StatusUpdateRequest): Promise<Result<void, ValidationError | BusinessRuleError>>;
}

// Result type for better error handling
type Result<T, E> = {
  success: true;
  data: T;
} | {
  success: false;
  error: E;
};

// Usage
const result = await agentStatusService.updateStatus(request);
if (result.success) {
  console.log('Status updated successfully');
} else {
  if (result.error instanceof ValidationError) {
    // Handle validation error
  } else if (result.error instanceof BusinessRuleError) {
    // Handle business rule error
  }
}
```

**💡 Key Takeaways:**
- **Interfaces เป็นสัญญา** ระหว่าง Components
- **Type safety** ลด bugs และเพิ่มความน่าเชื่อถือ
- **Consistency** ใน naming และ patterns
- **Extensibility** สำหรับความต้องการในอนาคต
- **Error handling** ที่ชัดเจนและจัดการได้