# ตัวอย่างเปรียบเทียบ: จาก Component สู่ Class แบบง่ายๆ
## ENGSE206: Software Requirements Specification and Design
### สำหรับนักศึกษาที่เพิ่งเรียน Object-Oriented Programming

---

## 📋 ทำไมต้องแปลง Component เป็น Class?

### เปรียบเทียบกับสิ่งที่คุ้นเคย

**เหมือนการออกแบบบ้าน:**
```
📋 แบบแปลน (Component)         →    🏠 บ้านจริง (Class)
"ห้องครัว"                      →    ห้องครัวที่มีตู้เย็น เตาแก๊ส โต๊ะ
"ห้องนอน"                      →    ห้องนอนที่มีเตียง ตู้เสื้อผ้า โต๊ะทำงาน
"ห้องน้ำ"                       →    ห้องน้ำที่มีสุขภัณฑ์และอุปกรณ์จริง
```

**ในซอฟต์แวร์:**
```
📦 Component (แนวคิด)           →    🏗️ Class (โค้ดจริง)
"Agent Controller Component"    →    class AgentController { methods... }
"Agent Service Component"       →    class AgentService { methods... }  
"Agent Repository Component"    →    class AgentRepository { methods... }
```

### ปัญหาของการมีเฉพาะ Component

**สถานการณ์:** นักศึกษาได้ Component Diagram แล้วต้องเขียนโค้ด

```
👨‍🎓 นักศึกษา: "มี Agent Controller Component ที่จัดการ HTTP requests"
💭 คิด: "แล้วเขียนยังไง? มี method อะไรบ้าง? รับ parameter แบบไหน?"

📋 Component Diagram บอก: "อะไร" และ "ทำไม"
🔧 แต่ไม่บอก: "อย่างไร" ในระดับโค้ด
```

---

## 🏗️ ตัวอย่างที่ 1: Agent Model Class

### จาก Component Description

```
📦 Agent Data Component
├── เก็บข้อมูล Agent (รหัส, ชื่อ, สถานะ)
├── ตรวจสอบความถูกต้องของข้อมูล  
└── จัดการการเปลี่ยนสถานะ
```

### แปลงเป็น Class (เข้าใจง่าย)

```javascript
// Class Agent - เป็นแม่แบบสำหรับสร้าง Agent
class Agent {
  // Constructor - วิธีสร้าง Agent ใหม่ (เหมือนการกรอกใบสมัคร)
  constructor(agentCode, fullName) {
    // Properties - สิ่งที่ Agent "มี"
    this.agentCode = agentCode;        // รหัสพนักงาน
    this.fullName = fullName;          // ชื่อ-สกุล
    this.currentStatus = "Offline";    // สถานะเริ่มต้น
    this.loginTime = null;             // เวลาล็อกอิน
  }
  
  // Methods - สิ่งที่ Agent "ทำได้"
  login() {
    this.currentStatus = "Available";
    this.loginTime = new Date();
    console.log(`${this.fullName} logged in at ${this.loginTime}`);
  }
  
  changeStatus(newStatus) {
    // Business Rule: ตรวจสอบการเปลี่ยนสถานะให้ถูกต้อง
    if (this.isValidStatusChange(newStatus)) {
      console.log(`${this.fullName} changed from ${this.currentStatus} to ${newStatus}`);
      this.currentStatus = newStatus;
      return true;
    } else {
      console.log(`Invalid status change from ${this.currentStatus} to ${newStatus}`);
      return false;
    }
  }
  
  isValidStatusChange(newStatus) {
    // Business Logic: กฎการเปลี่ยนสถานะ
    if (this.currentStatus === "Offline" && newStatus === "Busy") {
      return false; // ไม่ให้เปลี่ยนจาก Offline ไป Busy ตรงๆ
    }
    return true;
  }
  
  getInfo() {
    return `${this.fullName} (${this.agentCode}) - Status: ${this.currentStatus}`;
  }
  
  logout() {
    this.currentStatus = "Offline";
    this.loginTime = null;
    console.log(`${this.fullName} logged out`);
  }
}
```

### การใช้งาน Agent Class

```javascript
// สร้าง Agent objects จาก Agent class
const john = new Agent("JOHN001", "John Smith");
const jane = new Agent("JANE002", "Jane Doe");

console.log(john.getInfo()); 
// Output: "John Smith (JOHN001) - Status: Offline"

// John ล็อกอิน
john.login();
// Output: "John Smith logged in at [current time]"

console.log(john.getInfo());
// Output: "John Smith (JOHN001) - Status: Available"

// John เปลี่ยนสถานะ
john.changeStatus("Busy");
// Output: "John Smith changed from Available to Busy"

// ทดสอบ Business Rule
jane.changeStatus("Busy"); 
// Output: "Invalid status change from Offline to Busy"
```

### อธิบายส่วนประกอบ

**Properties (คุณสมบัติ):**
- `agentCode` - รหัสพนักงาน
- `fullName` - ชื่อ-สกุล  
- `currentStatus` - สถานะปัจจุบัน
- `loginTime` - เวลาล็อกอิน

**Methods (ความสามารถ):**
- `constructor()` - สร้าง Agent ใหม่
- `login()` - ล็อกอินเข้าระบบ
- `changeStatus()` - เปลี่ยนสถานะ
- `isValidStatusChange()` - ตรวจสอบการเปลี่ยนสถานะ
- `getInfo()` - แสดงข้อมูล Agent
- `logout()` - ออกจากระบบ

**Business Logic:**
- ตรวจสอบการเปลี่ยนสถานะให้ถูกต้องตาม Business Rules
- ไม่ให้เปลี่ยนจาก "Offline" ไป "Busy" โดยตรง

---

## 🎮 ตัวอย่างที่ 2: Agent Controller Class

### จาก Component Description

```
📦 Agent Controller Component
├── รับ HTTP requests จาก client
├── เรียกใช้ Agent Service เพื่อประมวลผล
├── ส่ง HTTP responses กลับไป
└── จัดการ error handling
```

### แปลงเป็น Class

```javascript
// Class AgentController - จัดการ HTTP requests เกี่ยวกับ Agent
class AgentController {
  // Constructor - รับสิ่งที่ Controller ต้องการเพื่อทำงาน
  constructor(agentService) {
    this.agentService = agentService;  // ต้องการ Service เพื่อประมวลผล
  }
  
  // Method สำหรับ HTTP GET /agents/:id
  async getAgent(request, response) {
    try {
      // 1. ดึงข้อมูลจาก request
      const agentId = request.params.id;
      
      // 2. เรียกใช้ Service ทำงาน
      const agent = await this.agentService.findAgentById(agentId);
      
      // 3. ส่งข้อมูลกลับเป็น JSON
      response.json({
        success: true,
        data: {
          agentId: agent.agentCode,
          name: agent.fullName,
          status: agent.currentStatus
        }
      });
      
      console.log(`Retrieved agent: ${agentId}`);
      
    } catch (error) {
      // 4. จัดการ error
      console.error(`Error getting agent: ${error.message}`);
      response.status(500).json({
        success: false,
        error: error.message
      });
    }
  }
  
  // Method สำหรับ HTTP PUT /agents/:id/status
  async updateAgentStatus(request, response) {
    try {
      // 1. ดึงข้อมูลจาก request
      const agentId = request.params.id;
      const newStatus = request.body.status;
      
      console.log(`Updating agent ${agentId} status to ${newStatus}`);
      
      // 2. Validation
      if (!newStatus) {
        return response.status(400).json({
          success: false,
          error: "Status is required"
        });
      }
      
      // 3. เรียกใช้ Service
      const updatedAgent = await this.agentService.updateAgentStatus(agentId, newStatus);
      
      // 4. ส่งผลลัพธ์กลับ
      response.json({
        success: true,
        data: {
          agentId: updatedAgent.agentCode,
          previousStatus: "Available", // ได้จาก service
          currentStatus: updatedAgent.currentStatus,
          timestamp: new Date().toISOString()
        },
        message: "Status updated successfully"
      });
      
    } catch (error) {
      console.error(`Error updating status: ${error.message}`);
      
      // จัดการ error แบบละเอียด
      if (error.message.includes("not found")) {
        response.status(404).json({
          success: false,
          error: "Agent not found"
        });
      } else if (error.message.includes("Invalid")) {
        response.status(400).json({
          success: false,
          error: error.message
        });
      } else {
        response.status(500).json({
          success: false,
          error: "Internal server error"
        });
      }
    }
  }
  
  // Method สำหรับ HTTP POST /agents/login
  async loginAgent(request, response) {
    try {
      const agentCode = request.body.agentCode;
      
      if (!agentCode) {
        return response.status(400).json({
          success: false,
          error: "Agent code is required"
        });
      }
      
      // เรียกใช้ Service เพื่อ authenticate
      const agent = await this.agentService.authenticateAgent(agentCode);
      
      response.json({
        success: true,
        data: {
          agent: {
            id: agent.agentCode,
            name: agent.fullName,
            status: agent.currentStatus
          },
          loginTime: new Date().toISOString()
        },
        message: "Login successful"
      });
      
    } catch (error) {
      response.status(401).json({
        success: false,
        error: "Invalid agent code"
      });
    }
  }
}
```

### การใช้งาน AgentController

```javascript
// สร้าง Service (จะอธิบายใน ตัวอย่างที่ 3)
const agentService = new AgentService();

// สร้าง Controller
const agentController = new AgentController(agentService);

// จำลอง HTTP requests
const mockRequest = {
  params: { id: "JOHN001" },
  body: { status: "Busy" }
};

const mockResponse = {
  json: (data) => console.log("Response:", JSON.stringify(data, null, 2)),
  status: (code) => ({
    json: (data) => console.log(`Error ${code}:`, JSON.stringify(data, null, 2))
  })
};

// เรียกใช้ method
await agentController.updateAgentStatus(mockRequest, mockResponse);
```

### อธิบายการทำงาน

**Dependency:**
- Controller ต้องการ `agentService` เพื่อประมวลผล business logic

**HTTP Methods:**
- `getAgent()` - GET /agents/:id
- `updateAgentStatus()` - PUT /agents/:id/status  
- `loginAgent()` - POST /agents/login

**Error Handling:**
- ใช้ try-catch จัดการข้อผิดพลาด
- ส่ง HTTP status codes ที่เหมาะสม (200, 400, 404, 500)
- แยกประเภท error ให้ชัดเจน

**JSON Response Format:**
- มีโครงสร้าง response ที่สม่ำเสมอ
- มี success flag, data, และ message

---

## ⚙️ ตัวอย่างที่ 3: Agent Service Class

### จาก Component Description

```
📦 Agent Service Component
├── จัดการ Business Logic เกี่ยวกับ Agent
├── ตรวจสอบ Business Rules
├── เรียกใช้ Repository เพื่อจัดการข้อมูล
└── จัดการ Events และ Logging
```

### แปลงเป็น Class

```javascript
// Class AgentService - จัดการ Business Logic
class AgentService {
  // Constructor - รับสิ่งที่ Service ต้องการ
  constructor(agentRepository) {
    this.agentRepository = agentRepository;  // ต้องการ Repository เพื่อจัดการข้อมูล
    this.eventLog = [];                      // เก็บ log events
  }
  
  // Business Logic: หา Agent จาก ID
  async findAgentById(agentId) {
    console.log(`Service: Finding agent ${agentId}`);
    
    // เรียกใช้ Repository
    const agent = await this.agentRepository.findById(agentId);
    
    if (!agent) {
      throw new Error(`Agent ${agentId} not found`);
    }
    
    return agent;
  }
  
  // Business Logic: Authentication Agent
  async authenticateAgent(agentCode) {
    console.log(`Service: Authenticating agent ${agentCode}`);
    
    // ตรวจสอบรูปแบบ Agent Code
    if (!this.isValidAgentCode(agentCode)) {
      throw new Error("Invalid agent code format");
    }
    
    // หา Agent จาก Repository
    const agent = await this.agentRepository.findByCode(agentCode);
    
    if (!agent) {
      throw new Error("Agent not found");
    }
    
    // Auto-login Agent
    agent.login();
    
    // บันทึก event
    this.logEvent("AGENT_LOGIN", {
      agentCode: agent.agentCode,
      name: agent.fullName,
      time: new Date()
    });
    
    return agent;
  }
  
  // Business Logic: อัปเดตสถานะ Agent
  async updateAgentStatus(agentId, newStatus) {
    console.log(`Service: Updating agent ${agentId} status to ${newStatus}`);
    
    // 1. หา Agent
    const agent = await this.findAgentById(agentId);
    
    // 2. ตรวจสอบ Business Rule
    if (!this.isValidStatusForAgent(agent, newStatus)) {
      throw new Error(`Agent ${agentId} cannot change to status ${newStatus}`);
    }
    
    // 3. เปลี่ยนสถานะ
    const previousStatus = agent.currentStatus;
    const success = agent.changeStatus(newStatus);
    
    if (!success) {
      throw new Error("Invalid status transition");
    }
    
    // 4. บันทึกการเปลี่ยนแปลง (จำลอง database save)
    await this.agentRepository.save(agent);
    
    // 5. บันทึก event
    this.logEvent("STATUS_CHANGED", {
      agentId: agent.agentCode,
      from: previousStatus,
      to: newStatus,
      time: new Date()
    });
    
    console.log(`Service: Status updated successfully`);
    return agent;
  }
  
  // Business Rule: ตรวจสอบรูปแบบ Agent Code
  isValidAgentCode(agentCode) {
    // ตัวอย่าง: Agent Code ต้องมี 3-10 ตัวอักษร และเป็นตัวพิมพ์ใหญ่ + ตัวเลข
    const pattern = /^[A-Z0-9]{3,10}$/;
    return pattern.test(agentCode);
  }
  
  // Business Rule: ตรวจสอบการเปลี่ยนสถานะ
  isValidStatusForAgent(agent, newStatus) {
    // ตัวอย่าง Business Rule: Agent ที่เพิ่งล็อกอินไม่ควรไป Break ทันที
    if (agent.currentStatus === "Available" && newStatus === "Break") {
      const loginDuration = new Date() - agent.loginTime;
      const minimumWorkTime = 30 * 60 * 1000; // 30 นาที
      
      if (loginDuration < minimumWorkTime) {
        console.log(`Agent must work at least 30 minutes before break`);
        return false;
      }
    }
    
    return true;
  }
  
  // Helper Method: บันทึก Events
  logEvent(eventType, eventData) {
    const event = {
      type: eventType,
      data: eventData,
      timestamp: new Date()
    };
    
    this.eventLog.push(event);
    console.log(`Event logged: ${eventType}`, eventData);
  }
  
  // Helper Method: ดู Event History
  getEventHistory() {
    return this.eventLog;
  }
}
```

### อธิบาย Business Logic

**Authentication Logic:**
- ตรวจสอบรูปแบบ Agent Code
- หา Agent จาก Repository
- Auto-login เมื่อ authenticate สำเร็จ

**Status Update Logic:**  
- ตรวจสอบ Agent มีอยู่จริง
- ตรวจสอบ Business Rules
- เปลี่ยนสถานะใน Agent object
- บันทึกลง Repository

**Business Rules:**
- Agent Code ต้องเป็นตัวพิมพ์ใหญ่ + ตัวเลข 3-10 ตัว
- Agent ต้องทำงานอย่างน้อย 30 นาทีก่อนพัก

**Event Logging:**
- บันทึกทุก action ที่สำคัญ
- เก็บ timestamp และรายละเอียด

---

## 💾 ตัวอย่างที่ 4: Agent Repository Class

### จาก Component Description

```
📦 Agent Repository Component
├── จัดการการเก็บและดึงข้อมูล Agent
├── ทำ CRUD operations (Create, Read, Update, Delete)
├── แปลงข้อมูลระหว่าง Database และ Agent Objects
└── จัดการ Database connections
```

### แปลงเป็น Class (ใช้ Memory แทน Database เพื่อความเรียบง่าย)

```javascript
// Class AgentRepository - จัดการข้อมูล Agent
class AgentRepository {
  // Constructor
  constructor() {
    // ใช้ Map เก็บข้อมูลใน Memory (ในงานจริงจะเป็น Database)
    this.agents = new Map();           // เก็บ Agent objects
    this.agentsByCode = new Map();     // Index สำหรับหาด้วย agentCode
    
    // สร้างข้อมูลทดสอบ
    this.createTestData();
  }
  
  // CRUD: Create - สร้าง Agent ใหม่
  async create(agentData) {
    console.log(`Repository: Creating agent ${agentData.agentCode}`);
    
    // ตรวจสอบว่ามี Agent Code นี้อยู่แล้วหรือไม่
    if (this.agentsByCode.has(agentData.agentCode)) {
      throw new Error(`Agent code ${agentData.agentCode} already exists`);
    }
    
    // สร้าง Agent object
    const agent = new Agent(agentData.agentCode, agentData.fullName);
    agent.agentId = `AGT${Date.now()}`; // สร้าง unique ID
    
    // เก็บใน Map
    this.agents.set(agent.agentId, agent);
    this.agentsByCode.set(agent.agentCode, agent);
    
    console.log(`Repository: Agent ${agentData.agentCode} created successfully`);
    return agent;
  }
  
  // CRUD: Read - หา Agent ด้วย ID
  async findById(agentId) {
    console.log(`Repository: Finding agent by ID: ${agentId}`);
    
    const agent = this.agents.get(agentId);
    
    if (agent) {
      console.log(`Repository: Found agent ${agent.agentCode}`);
    } else {
      console.log(`Repository: Agent ${agentId} not found`);
    }
    
    return agent || null;
  }
  
  // CRUD: Read - หา Agent ด้วย Agent Code
  async findByCode(agentCode) {
    console.log(`Repository: Finding agent by code: ${agentCode}`);
    
    const agent = this.agentsByCode.get(agentCode);
    
    if (agent) {
      console.log(`Repository: Found agent ${agent.fullName}`);
    } else {
      console.log(`Repository: Agent code ${agentCode} not found`);
    }
    
    return agent || null;
  }
  
  // CRUD: Read - ดึง Agent ทั้งหมด
  async findAll() {
    console.log(`Repository: Getting all agents`);
    
    const allAgents = Array.from(this.agents.values());
    console.log(`Repository: Found ${allAgents.length} agents`);
    
    return allAgents;
  }
  
  // CRUD: Update - บันทึกการเปลี่ยนแปลง Agent
  async save(agent) {
    console.log(`Repository: Saving agent ${agent.agentCode}`);
    
    if (!this.agents.has(agent.agentId)) {
      throw new Error(`Cannot save: Agent ${agent.agentId} not found`);
    }
    
    // อัปเดตข้อมูล (ใน Memory)
    this.agents.set(agent.agentId, agent);
    this.agentsByCode.set(agent.agentCode, agent);
    
    console.log(`Repository: Agent ${agent.agentCode} saved successfully`);
    return agent;
  }
  
  // CRUD: Delete - ลบ Agent
  async delete(agentId) {
    console.log(`Repository: Deleting agent ${agentId}`);
    
    const agent = this.agents.get(agentId);
    if (!agent) {
      return false;
    }
    
    // ลบจาก Maps
    this.agents.delete(agentId);
    this.agentsByCode.delete(agent.agentCode);
    
    console.log(`Repository: Agent ${agent.agentCode} deleted successfully`);
    return true;
  }
  
  // Helper Method: สร้างข้อมูลทดสอบ
  createTestData() {
    console.log("Repository: Creating test data");
    
    const testAgents = [
      { agentCode: "JOHN001", fullName: "John Smith" },
      { agentCode: "JANE002", fullName: "Jane Doe" },
      { agentCode: "BOB003", fullName: "Bob Johnson" }
    ];
    
    testAgents.forEach(async (agentData) => {
      await this.create(agentData);
    });
    
    console.log("Repository: Test data created");
  }
  
  // Helper Method: แสดงสถิติ
  getStatistics() {
    const total = this.agents.size;
    const byStatus = {};
    
    this.agents.forEach(agent => {
      byStatus[agent.currentStatus] = (byStatus[agent.currentStatus] || 0) + 1;
    });
    
    return {
      total: total,
      byStatus: byStatus
    };
  }
}
```

### อธิบายการทำงาน Repository

**CRUD Operations:**
- `create()` - สร้าง Agent ใหม่
- `findById()` - หา Agent ด้วย ID
- `findByCode()` - หา Agent ด้วย Agent Code  
- `findAll()` - ดึง Agent ทั้งหมด
- `save()` - บันทึกการเปลี่ยนแปลง
- `delete()` - ลบ Agent

**Data Storage:**
- ใช้ Map แทน Database เพื่อความเรียบง่าย
- มี Index สำหรับ agentCode เพื่อค้นหาเร็ว
- สร้างข้อมูลทดสอบอัตโนมัติ

**Error Handling:**
- ตรวจสอบ duplicate Agent Code
- ตรวจสอบ Agent มีอยู่ก่อนอัปเดต

---

## 🔗 ตัวอย่างที่ 5: การเชื่อมต่อทั้งหมด

### แนวคิด Component Dependencies

```
Agent Controller → Agent Service → Agent Repository → Data Storage
```

### Implementation จริง

```javascript
// Application Class - จัดการการเชื่อมต่อทั้งหมด
class Application {
  constructor() {
    console.log("=== Initializing Agent Wallboard System ===");
    
    // สร้าง dependencies ตามลำดับ (จากล่างขึ้นบน)
    this.agentRepository = new AgentRepository();
    this.agentService = new AgentService(this.agentRepository);
    this.agentController = new AgentController(this.agentService);
    
    console.log("=== System initialized successfully ===");
  }
  
  // จำลองการทำงาน HTTP API
  async simulateAPICall() {
    console.log("\n=== Simulating API Calls ===");
    
    // 1. จำลอง Agent Login
    await this.simulateAgentLogin();
    
    // 2. จำลอง Status Update
    await this.simulateStatusUpdate();
    
    // 3. จำลอง Get Agent Info
    await this.simulateGetAgent();
    
    console.log("\n=== API Simulation Complete ===");
  }
  
  async simulateAgentLogin() {
    console.log("\n--- Test 1: Agent Login ---");
    
    const mockRequest = {
      body: { agentCode: "JOHN001" }
    };
    
    const mockResponse = {
      json: (data) => {
        console.log("✅ Login Response:", {
          success: data.success,
          agentName: data.data.agent.name,
          status: data.data.agent.status
        });
      },
      status: (code) => ({
        json: (data) => console.log(`❌ Login Error ${code}:`, data.error)
      })
    };
    
    await this.agentController.loginAgent(mockRequest, mockResponse);
  }
  
  async simulateStatusUpdate() {
    console.log("\n--- Test 2: Status Update ---");
    
    const mockRequest = {
      params: { id: "JOHN001" },
      body: { status: "Busy" }
    };
    
    const mockResponse = {
      json: (data) => {
        console.log("✅ Status Update Response:", {
          success: data.success,
          currentStatus: data.data.currentStatus,
          message: data.message
        });
      },
      status: (code) => ({
        json: (data) => console.log(`❌ Status Update Error ${code}:`, data.error)
      })
    };
    
    await this.agentController.updateAgentStatus(mockRequest, mockResponse);
  }
  
  async simulateGetAgent() {
    console.log("\n--- Test 3: Get Agent Info ---");
    
    const mockRequest = {
      params: { id: "JOHN001" }
    };
    
    const mockResponse = {
      json: (data) => {
        console.log("✅ Get Agent Response:", {
          success: data.success,
          agentId: data.data.agentId,
          name: data.data.name,
          status: data.data.status
        });
      },
      status: (code) => ({
        json: (data) => console.log(`❌ Get Agent Error ${code}:`, data.error)
      })
    };
    
    await this.agentController.getAgent(mockRequest, mockResponse);
  }
  
  // แสดงสถิติระบบ
  showSystemStatistics() {
    console.log("\n=== System Statistics ===");
    
    const stats = this.agentRepository.getStatistics();
    console.log("Repository Stats:", stats);
    
    const eventHistory = this.agentService.getEventHistory();
    console.log("Event History:", eventHistory.length, "events");
    
    eventHistory.forEach((event, index) => {
      console.log(`  ${index + 1}. ${event.type} at ${event.timestamp.toLocaleTimeString()}`);
    });
  }
  
  // ทดสอบ Error Cases
  async testErrorHandling() {
    console.log("\n=== Testing Error Handling ===");
    
    // Test 1: Invalid Agent Code
    console.log("\n--- Test: Invalid Agent Code ---");
    const invalidLoginRequest = {
      body: { agentCode: "invalid123" }  // lowercase, ไม่ตรงกับรูปแบบ
    };
    
    const errorResponse = {
      json: (data) => console.log("✅ Validation working:", data),
      status: (code) => ({
        json: (data) => console.log(`✅ Error handled properly (${code}):`, data.error)
      })
    };
    
    await this.agentController.loginAgent(invalidLoginRequest, errorResponse);
    
    // Test 2: Agent Not Found
    console.log("\n--- Test: Agent Not Found ---");
    const notFoundRequest = {
      params: { id: "NONEXISTENT" }
    };
    
    await this.agentController.getAgent(notFoundRequest, errorResponse);
  }
}

// การใช้งานระบบทั้งหมด
async function runDemo() {
  // สร้างระบบ
  const app = new Application();
  
  // ทดสอบการทำงานปกติ
  await app.simulateAPICall();
  
  // แสดงสถิติ
  app.showSystemStatistics();
  
  // ทดสอบ Error Handling
  await app.testErrorHandling();
}

// เรียกใช้งาน
runDemo().catch(console.error);
```

### ผลลัพธ์ที่คาดว่าจะได้

```
=== Initializing Agent Wallboard System ===
Repository: Creating test data
Repository: Creating agent JOHN001
Repository: Agent JOHN001 created successfully
Repository: Creating agent JANE002
Repository: Agent JANE002 created successfully
Repository: Creating agent BOB003
Repository: Agent BOB003 created successfully
Repository: Test data created
=== System initialized successfully ===

=== Simulating API Calls ===

--- Test 1: Agent Login ---
Service: Authenticating agent JOHN001
Repository: Finding agent by code: JOHN001
Repository: Found agent John Smith
John Smith logged in at [timestamp]
Event logged: AGENT_LOGIN { agentCode: 'JOHN001', name: 'John Smith', time: [timestamp] }
✅ Login Response: {
  success: true,
  agentName: 'John Smith',
  status: 'Available'
}

--- Test 2: Status Update ---
Service: Updating agent JOHN001 status to Busy
Service: Finding agent JOHN001
Repository: Finding agent by code: JOHN001
Repository: Found agent John Smith
John Smith changed from Available to Busy
Repository: Saving agent JOHN001
Repository: Agent JOHN001 saved successfully
Event logged: STATUS_CHANGED { agentId: 'JOHN001', from: 'Available', to: 'Busy', time: [timestamp] }
Service: Status updated successfully
✅ Status Update Response: {
  success: true,
  currentStatus: 'Busy',
  message: 'Status updated successfully'
}

--- Test 3: Get Agent Info ---
Service: Finding agent JOHN001
Repository: Finding agent by code: JOHN001
Repository: Found agent John Smith
✅ Get Agent Response: {
  success: true,
  agentId: 'JOHN001',
  name: 'John Smith',
  status: 'Busy'
}
```

### อธิบายการไหลของข้อมูล

**1. HTTP Request มาถึง Controller:**
```
Client → AgentController.updateAgentStatus()
```

**2. Controller เรียก Service:**
```
AgentController → AgentService.updateAgentStatus()
```

**3. Service เรียก Repository:**
```
AgentService → AgentRepository.findByCode()
AgentService → AgentRepository.save()
```

**4. Service ประมวลผล Business Logic:**
```
- ตรวจสอบ Business Rules
- เปลี่ยนสถานะใน Agent Object
- บันทึก Event Log
```

**5. ผลลัพธ์ไหลกลับไป:**
```
Repository → Service → Controller → Client
```

---

## 📚 สรุป: ประโยชน์ของการแปลง Component เป็ Class

### สำหรับนักศึกษา OOP

#### 1. เข้าใจความแตกต่างระหว่าง Design และ Implementation

**Component (Design Level):**
```
"Agent Controller Component ที่จัดการ HTTP requests"
```

**Class (Implementation Level):**
```javascript
class AgentController {
  constructor(agentService) { }
  async updateAgentStatus(req, res) { }
  async getAgent(req, res) { }
  async loginAgent(req, res) { }
}
```

#### 2. เห็นการใช้งาน OOP Concepts จริง

**Encapsulation:**
- Agent Class ซ่อนรายละเอียดการจัดการสถานะ
- Repository Class ซ่อนวิธีการเก็บข้อมูล

**Abstraction:**
- Service Class แยก business logic จาก data access
- Controller Class แยก HTTP handling จาก business logic

**Composition:**
- Controller ใช้ Service
- Service ใช้ Repository
- การเชื่อมต่อผ่าน Constructor

#### 3. เรียนรู้ Software Design Principles

**Single Responsibility:**
- Agent Class: จัดการข้อมูล Agent
- AgentService Class: จัดการ business logic
- AgentRepository Class: จัดการข้อมูล
- AgentController Class: จัดการ HTTP

**Dependency Injection:**
- Classes รับ dependencies ผ่าน Constructor
- ไม่สร้าง dependencies เอง
- ทำให้ยืดหยุ่นและทดสอบง่าย

### การเรียนรู้ต่อ

#### ขั้นต่อไป: เพิ่ม Interfaces

```javascript
// กำหนด Contract สำหรับ Repository
interface IAgentRepository {
  findById(id: string): Promise<Agent>;
  findByCode(code: string): Promise<Agent>;  
  save(agent: Agent): Promise<Agent>;
}

// Implementation ที่ 1: Memory Repository
class MemoryAgentRepository implements IAgentRepository {
  // ... methods
}

// Implementation ที่ 2: Database Repository  
class DatabaseAgentRepository implements IAgentRepository {
  // ... methods
}

// Service ไม่สนใจ Implementation ไหน
class AgentService {
  constructor(agentRepository: IAgentRepository) {
    // ทำงานได้กับทุก Implementation
  }
}
```

#### ขั้นต่อไป: เพิ่ม Error Handling

```javascript
class AgentService {
  async updateAgentStatus(agentId: string, status: string) {
    try {
      // Business Logic
    } catch (error) {
      if (error instanceof ValidationError) {
        throw new BusinessLogicError("Invalid status change", error);
      } else if (error instanceof RepositoryError) {
        throw new ServiceError("Data access failed", error);
      } else {
        throw new ServiceError("Unexpected error", error);
      }
    }
  }
}
```

#### ขั้นต่อไป: เพิ่ม Testing

```javascript
describe('AgentService', () => {
  test('should update agent status successfully', async () => {
    // Arrange
    const mockRepository = new MockAgentRepository();
    const service = new AgentService(mockRepository);
    
    // Act
    const result = await service.updateAgentStatus('JOHN001', 'Busy');
    
    // Assert
    expect(result.currentStatus).toBe('Busy');
  });
});
```

### Tips สำหรับนักศึกษา

**1. เริ่มจากง่าย:**
- เริ่มจาก Model Classes (Agent, StatusLog)
- ใช้ console.log() ดูการทำงาน
- ทดสอบทีละ method

**2. ทำความเข้าใจก่อนท่อง:**
- รู้ว่าแต่ละ Class ทำหน้าที่อะไร
- เข้าใจการไหลของข้อมูล
- เข้าใจ dependencies ระหว่าง Classes

**3. ใช้เครื่องมือช่วย:**
- VS Code สำหรับ syntax highlighting
- Node.js สำหรับรัน JavaScript
- Git สำหรับ version control

**4. ฝึกเขียนเอง:**
- ลองเขียน Classes เพิ่มเติม (Message, Team)
- ลองเพิ่ม methods ใหม่
- ลองแก้ไข business rules

การแปลง Component เป็น Class ไม่ใช่แค่การเขียนโค้ด แต่เป็นการเรียนรู้การคิดแบบ Object-Oriented และเตรียมพร้อมสำหรับการพัฒนาระบบซอฟต์แวร์ขนาดใหญ่ในอนาคต