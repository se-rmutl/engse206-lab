# Workshop: สร้าง C1 และ C2 Diagrams สำหรับ Agent Wallboard System

## วัตถุประสงค์การเรียนรู้
นักศึกษาสามารถสร้าง Architecture Diagrams ด้วย Draw.io เพื่ออธิบายสถาปัตยกรรมระดับสูงของ Agent Wallboard System โดยใช้หลักการ C4 Model

---

## กิจกรรมที่ 1: วาด C1 - System Context Diagram (15 นาที)

### โจทย์
สร้างแผนภาพแสดงภาพรวมของระบบ Agent Wallboard System ในบริบทของ Call Center Operation

### ข้อมูลที่กำหนดให้
**ระบบหลัก:** Agent Wallboard System (Call Center Management Platform)

**ผู้ใช้งาน 4 กลุ่ม:**
- Call Center Agents
- Team Leaders/Supervisors  
- Operations Managers
- System Administrators

**ฟีเจอร์หลักของระบบ:**
- Real-time Agent Status Monitoring
- Supervisor-Agent Communication
- Performance Dashboard & Reporting
- System Administration Tools

### สิ่งที่นักศึกษาต้องทำ
1. **เปิด Draw.io** และเลือก Blank Diagram
2. **สร้าง System Box กลาง** สำหรับ "Agent Wallboard System"
3. **สร้าง Actor Shapes** สำหรับผู้ใช้ 4 กลุ่ม พร้อมระบุหน้าที่หลักของแต่ละกลุ่ม
4. **เชื่อมเส้นและใส่ Label** อธิบายการทำงานระหว่าง Users และ System
5. **ใช้สีแยกประเภท** Users กับ System

### คำถามสำหรับนักศึกษา
- [ ] ผู้ใช้แต่ละกลุ่มมีความต้องการหลักอะไรจากระบบ?
- [ ] Agent Wallboard System เป็น Standalone หรือต้องเชื่อมต่อกับระบบภายนอก?
- [ ] การไหลของข้อมูลหลักเป็นแบบไหน?

### ตัวอย่างคำอธิบายที่ควรมี
**Call Center Agents:**
- ใช้งาน Desktop Application
- เปลี่ยนสถานะ Available/Active/Wrap/Not Ready
- รับข้อความจาก Supervisor

**Team Leaders/Supervisors:**
- [นักศึกษาเติมเอง]

**Operations Managers:**
- [นักศึกษาเติมเอง]

**System Administrators:**
- [นักศึกษาเติมเอง]

---

## กิจกรรมที่ 2: วาด C2 - Container Diagram (25 นาที)

### โจทย์
แบ่งระบบ Agent Wallboard System ออกเป็น Containers และแสดงเทคโนโลยีที่ใช้ตาม 3-Tier Architecture

### ข้อมูลที่กำหนดให้

#### 🖼️ Presentation Tier (Frontend)
**Technology Stack:** Electron.js และ React.js

**Containers ที่ต้องสร้าง:**
1. Agent Desktop App (Electron.js) - Port: 3000
2. Supervisor Dashboard (React.js + Browser)
3. Management Portal (React.js + Browser)  
4. Admin Console (React.js + Browser)

#### ⚙️ Application Tier (Backend)
**Technology Stack:** Node.js + Express.js + Socket.io

**Containers ที่ต้องสร้าง:**
1. API Server (Node.js + Express.js) - Port: 8000
2. WebSocket Server (Socket.io + Node.js) - Port: 8080
3. Authentication Service (Node.js + JWT)
4. Background Services (Node.js Workers)

#### 💾 Data Tier (Database)
**Technology Stack:** MSSQL + MongoDB

**Containers ที่ต้องสร้าง:**
1. MSSQL Database - Port: 1433
2. MongoDB Database - Port: 27017

### สิ่งที่นักศึกษาต้องทำ

#### ขั้นตอนที่ 1: สร้าง 3 Subgroups
1. สร้าง Subgroup "Presentation Tier" 
2. สร้าง Subgroup "Application Tier"
3. สร้าง Subgroup "Data Tier"

#### ขั้นตอนที่ 2: เพิ่ม Containers ในแต่ละ Tier
**Presentation Tier - เพิ่ม 4 Containers:**
- [ ] Agent Desktop App พร้อมระบุ Technology และ Functions
- [ ] Supervisor Dashboard พร้อมระบุ Technology และ Functions  
- [ ] Management Portal พร้อมระบุ Technology และ Functions
- [ ] Admin Console พร้อมระบุ Technology และ Functions

**Application Tier - เพิ่ม 4 Containers:**
- [ ] API Server พร้อมระบุ Port และ Functions
- [ ] WebSocket Server พร้อมระบุ Port และ Functions
- [ ] Authentication Service พร้อมระบุ Technology และ Functions
- [ ] Background Services พร้อมระบุ Technology และ Functions

**Data Tier - เพิ่ม 2 Containers:**
- [ ] MSSQL Database พร้อมระบุ Port และ Data Types
- [ ] MongoDB Database พร้อมระบุ Port และ Data Types

#### ขั้นตอนที่ 3: เชื่อมต่อ Containers
**Frontend → Backend Connections:**
- [ ] ทุก Frontend Containers เชื่อมต่อ API Server ด้วย REST API/HTTPS
- [ ] เฉพาะ Agent Desktop App และ Supervisor Dashboard เชื่อมต่อ WebSocket Server
- [ ] ระบุ Protocol สำหรับแต่ละเส้นเชื่อม

**Backend Internal Connections:**
- [ ] API Server ↔ WebSocket Server (Internal API)
- [ ] API Server ↔ Background Services (Job Queue)
- [ ] API Server → Authentication Service (Token Validation)
- [ ] WebSocket Server → Authentication Service (User Verification)

**Backend → Database Connections:**
- [ ] API Server → MSSQL Database (SQL Queries)
- [ ] API Server → MongoDB Database (Document Queries)
- [ ] WebSocket Server → MSSQL Database (Status Updates)
- [ ] WebSocket Server → MongoDB Database (Message Storage)
- [ ] Background Services → ทั้ง 2 Databases (Batch Processing)
- [ ] Authentication Service → MSSQL Database (User Validation)

#### ขั้นตอนที่ 4: ใส่ Labels และ Styling
- [ ] ใส่ Protocol Labels: HTTP/HTTPS, WebSocket/WSS, TCP/IP
- [ ] ใช้สีแยกประเภท: Frontend (ส้ม), Backend (น้ำเงิน), Database (เขียว)
- [ ] เพิ่ม Port Numbers และ Technology Stack ในแต่ละ Container

### คำถามสำหรับนักศึกษา

#### คำถามการออกแบบ:
1. **ทำไมต้องแยก Frontend เป็น 4 Containers แยกกัน?**
   - คำตอบที่ต้องการ: Role-based access, Security separation, Performance optimization

2. **ทำไมต้องใช้ทั้ง MSSQL และ MongoDB?**
   - MSSQL สำหรับ: [นักศึกษาเติมเอง]
   - MongoDB สำหรับ: [นักศึกษาเติมเอง]

3. **ทำไมต้องแยก API Server และ WebSocket Server?**
   - คำตอบที่ต้องการ: Separation of concerns, Scalability, Technology optimization

#### คำถามเทคนิค:
4. **Container ไหนต้องการ Real-time Communication?**
   - Agent Desktop App: [เหตุผล]
   - Supervisor Dashboard: [เหตุผล]
   - Management Portal: [ต้องการหรือไม่ เพราะอะไร]
   - Admin Console: [ต้องการหรือไม่ เพราะอะไร]

5. **Authentication Service เชื่อมต่อกับ Container ไหนบ้าง และเพราะอะไร?**
   - [นักศึกษาวิเคราะห์เอง]

### ข้อมูลเพิ่มเติมสำหรับการทำงาน

#### MSSQL Database Tables:
- OnlineAgents (AgentCode, AgentName, LoginTime, Status, LastUpdateTime)
- User Accounts & Permissions
- System Configuration
- Team & Department Information

#### MongoDB Collections:
- StatusLogs (real-time agent status changes)
- Message History (supervisor-agent communications)
- Session & Connection Logs
- Analytics Data (performance metrics)

#### API Endpoints ตัวอย่าง:
- `/api/agents` - Agent management
- `/api/status` - Status operations
- `/api/messages` - Message handling  
- `/api/reports` - Report generation

#### WebSocket Events ตัวอย่าง:
- `statusUpdate` - Agent status changes
- `newMessage` - Message notifications
- `agentLogin` - Agent login events
- `systemAlert` - System notifications

---

## เกณฑ์การประเมิน (25 คะแนน)

### C1 - System Context Diagram (10 คะแนน)
- [ ] แสดงระบบกลางและผู้ใช้ 4 กลุ่มครบถ้วน (3 คะแนน)
- [ ] Label อธิบายการทำงานชัดเจน (3 คะแนน)
- [ ] ใช้สีและ layout เหมาะสม (2 คะแนน)
- [ ] ความเป็น Standalone System (2 คะแนน)

### C2 - Container Diagram (15 คะแนน)
- [ ] แสดง 3-Tier Architecture ครบถ้วน (4 คะแนน)
- [ ] Container details ถูกต้อง (Technology, Ports, Functions) (4 คะแนน)
- [ ] Connection protocols ชัดเจน (4 คะแนน)
- [ ] Color coding และ styling เหมาะสม (3 คะแนน)

### Bonus Points (5 คะแนน)
- [ ] คำอธิบาย Architecture Decisions ชัดเจน (2 คะแนน)
- [ ] การใช้ Draw.io features อย่างสร้างสรรค์ (2 คะแนน)
- [ ] การพิจารณา Non-functional Requirements (1 คะแนน)

---

## ส่งงาน

### รูปแบบการส่ง:
1. **ไฟล์ Draw.io** (.drawio หรือ .xml)
2. **ไฟล์ภาพ** (PNG หรือ PDF) สำหรับ C1 และ C2
3. **เอกสารคำอธิบาย** (1-2 หน้า) อธิบาย Architecture Decisions

### เนื้อหาในเอกสารคำอธิบาย:
1. **Technology Stack Justification** - เหตุผลการเลือกเทคโนโลยี
2. **Architecture Trade-offs** - ข้อดี/ข้อเสียของการออกแบบ
3. **Scalability Considerations** - การรองรับการขยายตัว
4. **Security Aspects** - ประเด็นความปลอดภัย

### กำหนดส่ง:
ก่อนเรียนสัปดาห์หน้า ผ่าน LMS

---

## Tips สำหรับนักศึกษา

### การใช้ Draw.io อย่างมีประสิทธิภาพ:
1. **ใช้ Shape Libraries**: Software Architecture, Network, Database icons
2. **Keyboard Shortcuts**: Ctrl+D (duplicate), Ctrl+G (group), F2 (edit text)
3. **Color Consistency**: กำหนดสีมาตรฐานและใช้ตลอด diagram
4. **Layout Planning**: วางแผน layout ก่อนเริ่มวาด

### หลีกเลี่ยงข้อผิดพลาดทั่วไป:
- ❌ Container ที่มีหน้าที่มากเกินไป (God Object)
- ❌ Protocol labels ไม่ชัดเจนหรือขาดหายไป
- ❌ Connection lines ที่ยุ่งเหยิงไม่เป็นระเบียบ
- ❌ สีที่ไม่สอดคล้องกันหรือใช้มากเกินไป

### แนวทางคิดเพิ่มเติม:
- 🤔 ทำไมต้องแยก containers แบบนี้?
- 🤔 ถ้า user เพิ่มขึ้น 10 เท่า จะต้องปรับอะไรบ้าง?
- 🤔 Security risks มีอะไรบ้าง และป้องกันอย่างไร?
- 🤔 ถ้าต้องเพิ่ม mobile app จะส่งผลกระทบอย่างไร?