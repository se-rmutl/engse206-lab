# C4 Model Complete Guide: จาก C1 ไป C2 ไป C3
## Agent Wallboard System - การออกแบบสถาปัตยกรรมซอฟต์แวร์แบบเป็นขั้นตอน

---

## 📚 สารบัญ

1. [C4 Model Overview](#c4-model-overview)
2. [C1 - System Context Diagram](#c1-system-context-diagram)
3. [C2 - Container Diagram](#c2-container-diagram)
4. [C3 - Component Diagram](#c3-component-diagram)
5. [การเชื่อมโยงและความต่อเนื่อง](#การเชื่อมโยงและความต่อเนื่อง)
6. [Draw.io Import Codes](#drawio-import-codes)

---

## C4 Model Overview

### 🎯 C4 Model คืออะไร?

**C4 Model** เป็นแนวทางการสร้างแผนภาพสถาปัตยกรรมซอฟต์แวร์ที่มี **4 ระดับ** ที่เชื่อมโยงกันแบบขั้นบันได:

```
C1 (Context) → C2 (Container) → C3 (Component) → C4 (Code)
   ภาพใหญ่      เทคโนโลยี        รายละเอียด       โค้ดจริง
```

### 🏗️ หลักการของ C4 Model

**"เริ่มจากภาพใหญ่ แล้วค่อยซูมเข้าไปในรายละเอียด"**

- **C1 (System Context):** ระบบในบริบทใหญ่ - ใครใช้, เชื่อมต่อกับอะไรบ้าง
- **C2 (Container):** แอปพลิเคชันและเทคโนโลยีหลัก - ใช้เทคโนโลยีอะไร
- **C3 (Component):** ส่วนประกอบภายใน - modules และ services
- **C4 (Code):** รายละเอียดโค้ด - classes และ functions

### 🎨 ประโยชน์ของ C4 Model

**1. Progressive Detail:** เริ่มจากง่ายไปยาก
**2. Stakeholder Communication:** แต่ละระดับเหมาะกับผู้ฟังต่างกัน
**3. Architecture Documentation:** เอกสารที่เป็นมาตรฐาน
**4. Design Validation:** ตรวจสอบการออกแบบได้ทุกระดับ

---

## C1 - System Context Diagram

### 🎯 วัตถุประสงค์ของ C1

**"แสดงภาพรวมระบบ Agent Wallboard ในบริบทของ Call Center"**

**ตอบคำถาม:**
- ใครเป็นผู้ใช้ระบบ?
- ระบบนี้ทำอะไร?
- เชื่อมต่อกับระบบภายนอกอื่นไหม?
- ขอบเขตของระบบคืออะไร?

### 📊 C1 Diagram - Agent Wallboard System Context

```
                    👥 Call Center Agents
                           │
                           │ ใช้งานผ่าน Desktop App
                           ▼
    👨‍💼 Supervisors ◄──────────────────────────► 📊 Agent Wallboard System
    Team Leaders      ใช้งานผ่าน Web Dashboard          │
           │                                          │ ▼ แจ้งเตือนผ่าน Email/SMS (optional)
           │          👨‍💻 Operations Managers ◄────────┘
           └─────────► ใช้งานรายงานและ Analytics
```

### 🔍 C1 Component Analysis

**🧑‍💼 External Actors (ผู้ใช้งานภายนอก):**

**1. Call Center Agents** 👥
- **บทบาท:** ผู้ปฏิบัติงานหลักในศูนย์บริการลูกค้า
- **การใช้งาน:** เปลี่ยนสถานะการทำงาน, รับข้อความจากหัวหน้า
- **อุปกรณ์:** Desktop Application (Electron.js)
- **จำนวน:** 50-500 คน (ขึ้นกับขนาดของ Call Center)

**2. Supervisors & Team Leaders** 👨‍💼  
- **บทบาท:** หัวหน้าทีมควบคุมดูแล agents
- **การใช้งาน:** ติดตามสถานะทีม, ส่งข้อความ, สร้างรายงาน
- **อุปกรณ์:** Web Dashboard ผ่าน Browser
- **จำนวน:** 5-20 คน

**3. Operations Managers** 👨‍💻
- **บทบาท:** ผู้บริหารระดับสูงควบคุมการดำเนินงานทั้งหมด
- **การใช้งาน:** ดูรายงานสถิติ, วิเคราะห์ประสิทธิภาพ, ตั้งค่าระบบ
- **อุปกรณ์:** Web Dashboard + Mobile Dashboard
- **จำนวน:** 1-5 คน

**🏢 The System (ระบบหลัก):**

**Agent Wallboard System** 📊
- **หน้าที่หลัก:** จัดการและติดตามสถานะของ agents แบบ real-time
- **ความสามารถ:** 
  - Real-time status monitoring
  - Supervisor-agent communication
  - Performance analytics & reporting
  - System administration

**🔌 External Systems (ระบบภายนอกที่เชื่อมต่อ - Optional):**
- **Email System** 📧: แจ้งเตือนผ่าน email เมื่อมีเหตุการณ์สำคัญ
- **SMS Gateway** 📱: ส่ง SMS alert ในกรณีฉุกเฉิน
- **HR System** 👤: ซิงค์ข้อมูลพนักงานและ org chart

### 🎨 Draw.io Code สำหรับ C1

```xml
<mxfile host="app.diagrams.net">
  <diagram name="C1-System-Context">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="827" pageHeight="1169">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        
        <!-- Central System -->
        <mxCell id="system" value="Agent Wallboard System&#xa;&#xa;Real-time Agent Status Monitoring&#xa;Supervisor Communication&#xa;Performance Analytics&#xa;System Administration" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontSize=14;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="300" y="300" width="280" height="150" as="geometry" />
        </mxCell>
        
        <!-- Call Center Agents -->
        <mxCell id="agents" value="Call Center Agents&#xa;(50-500 คน)&#xa;&#xa;Desktop Application&#xa;Status Management&#xa;Receive Messages" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="320" y="80" width="160" height="120" as="geometry" />
        </mxCell>
        
        <!-- Supervisors -->
        <mxCell id="supervisors" value="Supervisors &amp;&#xa;Team Leaders&#xa;(5-20 คน)&#xa;&#xa;Web Dashboard&#xa;Team Monitoring&#xa;Send Messages" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="50" y="320" width="160" height="120" as="geometry" />
        </mxCell>
        
        <!-- Managers -->
        <mxCell id="managers" value="Operations&#xa;Managers&#xa;(1-5 คน)&#xa;&#xa;Analytics Dashboard&#xa;System Configuration&#xa;Reports" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="640" y="320" width="160" height="120" as="geometry" />
        </mxCell>
        
        <!-- External Systems -->
        <mxCell id="email" value="Email System&#xa;(Optional)&#xa;&#xa;Alert Notifications" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=11;" vertex="1" parent="1">
          <mxGeometry x="500" y="550" width="120" height="80" as="geometry" />
        </mxCell>
        
        <mxCell id="sms" value="SMS Gateway&#xa;(Optional)&#xa;&#xa;Emergency Alerts" style="rounded=0;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=11;" vertex="1" parent="1">
          <mxGeometry x="660" y="550" width="120" height="80" as="geometry" />
        </mxCell>
        
        <!-- Connections -->
        <mxCell id="conn1" value="Desktop App&#xa;Status Updates" style="endArrow=classic;html=1;rounded=0;fontSize=10;" edge="1" parent="1" source="agents" target="system">
          <mxGeometry relative="1" as="geometry">
            <mxPoint x="400" y="220" as="sourcePoint" />
            <mxPoint x="440" y="280" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn2" value="Web Dashboard&#xa;Team Management" style="endArrow=classic;html=1;rounded=0;fontSize=10;" edge="1" parent="1" source="supervisors" target="system">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <mxCell id="conn3" value="Analytics Dashboard&#xa;System Admin" style="endArrow=classic;html=1;rounded=0;fontSize=10;" edge="1" parent="1" source="managers" target="system">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <mxCell id="conn4" value="Email Notifications" style="endArrow=classic;html=1;rounded=0;fontSize=10;dashed=1;" edge="1" parent="1" source="system" target="email">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <mxCell id="conn5" value="SMS Alerts" style="endArrow=classic;html=1;rounded=0;fontSize=10;dashed=1;" edge="1" parent="1" source="system" target="sms">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## C2 - Container Diagram

### 🎯 วัตถุประสงค์ของ C2

**"แสดงเทคโนโลยีและแอปพลิเคชันหลักที่ประกอบกันเป็น Agent Wallboard System"**

**ตอบคำถาม:**
- ระบบประกอบด้วยแอปพลิเคชันอะไรบ้าง?
- แต่ละแอปพลิเคชันใช้เทคโนโลยีอะไร?
- แอปพลิเคชันเหล่านี้สื่อสารกันอย่างไร?
- ข้อมูลเก็บที่ไหนและอย่างไร?

### 📊 C2 Diagram - Technology Containers

**การแบ่ง Containers ตามหน้าที่:**

**1. Client Applications (Presentation Tier)**
- **Agent Desktop App** (Electron.js)
- **Supervisor Web Dashboard** (React.js)

**2. Server Applications (Application Tier)**  
- **API Application Server** (Node.js + Express)
- **WebSocket Server** (Socket.io)

**3. Data Storage (Data Tier)**
- **Master Database** (Microsoft SQL Server)
- **Real-time Database** (MongoDB)

### 🏗️ Container Details

**💻 Agent Desktop Application**
- **เทคโนโลยี:** Electron.js + React.js
- **หน้าที่:** UI สำหรับ agents, status management, notifications
- **ผู้ใช้:** Call Center Agents (50-500 คน)
- **Deployment:** ติดตั้งในเครื่อง agent แต่ละคน

**🌐 Supervisor Web Dashboard**
- **เทคโนโลยี:** React.js + TypeScript
- **หน้าที่:** Real-time monitoring, team management, reporting
- **ผู้ใช้:** Supervisors, Team Leaders, Managers
- **Deployment:** Web application ผ่าน browser

**⚙️ API Application Server**
- **เทคโนโลยี:** Node.js + Express.js + TypeScript
- **หน้าที่:** Business logic, authentication, data processing
- **APIs:** REST endpoints สำหรับ CRUD operations
- **Deployment:** Docker containers บน cloud/on-premise

**📡 WebSocket Server**
- **เทคโนโลยี:** Socket.io (built-in Node.js server)
- **หน้าที่:** Real-time bidirectional communication
- **Features:** Room management, event broadcasting
- **Deployment:** Same server กับ API หรือแยก cluster

**🗃️ Master Database (MSSQL)**
- **เทคโนโลยี:** Microsoft SQL Server 2019+
- **หน้าที่:** Agent profiles, users, teams, configuration
- **ลักษณะข้อมูล:** Structured, ACID transactions
- **Deployment:** Database server cluster with failover

**🍃 Real-time Database (MongoDB)**
- **เทคโนโลยี:** MongoDB 5.0+
- **หน้าที่:** Status logs, messages, performance metrics
- **ลักษณะข้อมูล:** Document-based, high-write performance
- **Deployment:** Replica set สำหรับ high availability

### 🔄 Communication Protocols

**HTTP/HTTPS APIs:**
```
Desktop App ──REST API──► API Server
Web Dashboard ──REST API──► API Server
```

**WebSocket Connections:**
```
Desktop App ──WebSocket──► WebSocket Server
Web Dashboard ──WebSocket──► WebSocket Server
```

**Database Connections:**
```
API Server ──SQL Queries──► MSSQL Database
API Server ──MongoDB Queries──► MongoDB Database
```

### 🎨 Draw.io Code สำหรับ C2

```xml
<mxfile host="app.diagrams.net">
  <diagram name="C2-Container-Diagram">
    <mxGraphModel dx="1422" dy="950" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        
        <!-- Users -->
        <mxCell id="agents" value="Call Center Agents&#xa;(50-500 คน)" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
          <mxGeometry x="60" y="80" width="30" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="supervisors" value="Supervisors&#xa;&amp; Managers" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;outlineConnect=0;" vertex="1" parent="1">
          <mxGeometry x="60" y="460" width="30" height="60" as="geometry" />
        </mxCell>
        
        <!-- Presentation Tier -->
        <mxCell id="desktop-app" value="Agent Desktop App&#xa;[Electron.js + React]&#xa;&#xa;• Status Management&#xa;• Receive Notifications&#xa;• Profile Management" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="200" y="60" width="200" height="100" as="geometry" />
        </mxCell>
        
        <mxCell id="web-dashboard" value="Supervisor Web Dashboard&#xa;[React.js + TypeScript]&#xa;&#xa;• Team Monitoring&#xa;• Send Messages&#xa;• Generate Reports" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="200" y="440" width="200" height="100" as="geometry" />
        </mxCell>
        
        <!-- Application Tier -->
        <mxCell id="api-server" value="API Application Server&#xa;[Node.js + Express + TypeScript]&#xa;&#xa;• Authentication &amp; Authorization&#xa;• Business Logic Processing&#xa;• Data Validation&#xa;• REST API Endpoints" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="500" y="200" width="250" height="120" as="geometry" />
        </mxCell>
        
        <mxCell id="websocket-server" value="WebSocket Server&#xa;[Socket.io + Node.js]&#xa;&#xa;• Real-time Communication&#xa;• Event Broadcasting&#xa;• Connection Management&#xa;• Room/Namespace Handling" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="500" y="360" width="250" height="120" as="geometry" />
        </mxCell>
        
        <!-- Data Tier -->
        <mxCell id="mssql-db" value="Master Database&#xa;[Microsoft SQL Server]&#xa;&#xa;• Agent Profiles&#xa;• User Accounts&#xa;• Team Structure&#xa;• System Configuration" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="850" y="160" width="200" height="120" as="geometry" />
        </mxCell>
        
        <mxCell id="mongodb" value="Real-time Database&#xa;[MongoDB]&#xa;&#xa;• Agent Status Logs&#xa;• Message History&#xa;• Performance Metrics&#xa;• Analytics Data" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="850" y="320" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Connections -->
        <!-- Users to Apps -->
        <mxCell id="conn1" value="Desktop App" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="agents" target="desktop-app">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <mxCell id="conn2" value="Web Browser" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="supervisors" target="web-dashboard">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <!-- Apps to API Server -->
        <mxCell id="conn3" value="HTTPS REST API&#xa;JSON" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="desktop-app" target="api-server">
          <mxGeometry x="0.1" relative="1" as="geometry">
            <mxPoint as="offset" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn4" value="HTTPS REST API&#xa;JSON" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="web-dashboard" target="api-server">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <!-- Apps to WebSocket -->
        <mxCell id="conn5" value="WebSocket&#xa;Real-time Events" style="endArrow=classic;startArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="desktop-app" target="websocket-server">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="300" y="420" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn6" value="WebSocket&#xa;Real-time Events" style="endArrow=classic;startArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="web-dashboard" target="websocket-server">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <!-- API to Databases -->
        <mxCell id="conn7" value="SQL Queries&#xa;Connection Pool" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="api-server" target="mssql-db">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <mxCell id="conn8" value="MongoDB Queries&#xa;Connection Pool" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="api-server" target="mongodb">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="625" y="380" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- WebSocket to API (internal) -->
        <mxCell id="conn9" value="Internal API Calls" style="endArrow=classic;startArrow=classic;html=1;rounded=0;dashed=1;" edge="1" parent="1" source="websocket-server" target="api-server">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <!-- System Boundary -->
        <mxCell id="boundary" value="Agent Wallboard System" style="rounded=0;whiteSpace=wrap;html=1;fillColor=none;strokeColor=#666666;strokeWidth=2;dashed=1;fontSize=16;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="480" y="140" width="590" height="320" as="geometry" />
        </mxCell>
        
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## C3 - Component Diagram

### 🎯 วัตถุประสงค์ของ C3

**"แสดงส่วนประกอบภายในแต่ละ Container และวิธีการทำงานร่วมกัน"**

**ตอบคำถาม:**
- แต่ละ container ประกอบด้วย components อะไรบ้าง?
- Components เหล่านี้มีหน้าที่อะไร?
- Components สื่อสารกันอย่างไร?
- Interface ระหว่าง components คืออะไร?

### 📊 C3 Diagrams - Component Breakdown

เนื่องจาก C3 มีรายละเอียดมาก เราจะแสดงแยกตาม Container:

#### 🖥️ Desktop Application Components

**หน้าที่หลัก:** UI สำหรับ agents ในการจัดการสถานะและรับการสื่อสาร

**Components:**
- **Authentication Component:** จัดการ login/logout
- **Status Management Component:** เปลี่ยนสถานะ agent
- **Notification Component:** แสดงข้อความและแจ้งเตือน
- **Profile Component:** จัดการข้อมูลส่วนตัว
- **WebSocket Client Component:** การเชื่อมต่อ real-time

#### ⚙️ API Server Components  

**หน้าที่หลัก:** Business logic, data processing, API services

**Components:**
- **Authentication Service:** ตรวจสอบ credentials และ sessions
- **Agent Status Service:** จัดการสถานะ agents และ history
- **Message Routing Service:** จัดส่งข้อความระหว่าง users
- **WebSocket Manager:** จัดการ WebSocket connections
- **Database Access Layer:** เชื่อมต่อและ query databases
- **Event Bus Component:** จัดการ events ระหว่าง services

#### 🌐 Web Dashboard Components

**หน้าที่หลัก:** Interface สำหรับ supervisors ในการควบคุมและติดตาม

**Components:**
- **Dashboard Visualization:** แสดงข้อมูล real-time แบบ charts
- **Agent Monitor:** ติดตาม agent individual
- **Message Management:** ส่งข้อความและจัดการ communication
- **Reports Component:** สร้างและแสดงรายงาน
- **Control Panel:** จัดการการตั้งค่าระบบ

### 🎨 Draw.io Code สำหรับ C3 - API Server Components

```xml
<mxfile host="app.diagrams.net">
  <diagram name="C3-API-Server-Components">
    <mxGraphModel dx="1422" dy="950" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        
        <!-- Container Boundary -->
        <mxCell id="container-boundary" value="API Application Server Container&#xa;[Node.js + Express + TypeScript]" style="rounded=0;whiteSpace=wrap;html=1;fillColor=none;strokeColor=#82b366;strokeWidth=3;fontSize=16;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="40" y="40" width="1080" height="720" as="geometry" />
        </mxCell>
        
        <!-- Authentication Service -->
        <mxCell id="auth-service" value="Authentication Service&#xa;&#xa;• authenticate(credentials)&#xa;• validateToken(token)&#xa;• createSession(userId)&#xa;• destroySession(sessionId)&#xa;• refreshToken()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="80" y="100" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Agent Status Service -->
        <mxCell id="agent-service" value="Agent Status Service&#xa;&#xa;• updateStatus(agentId, status)&#xa;• getStatusHistory(agentId)&#xa;• validateTransition()&#xa;• getCurrentTeamStatus()&#xa;• broadcastStatusChange()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="320" y="100" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Message Routing Service -->
        <mxCell id="message-service" value="Message Routing Service&#xa;&#xa;• sendMessage(from, to, msg)&#xa;• broadcastToTeam(teamId, msg)&#xa;• getMessageHistory()&#xa;• validateMessage()&#xa;• routeMessage()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="560" y="100" width="200" height="120" as="geometry" />
        </mxCell>
        
<!-- WebSocket Manager -->
        <mxCell id="websocket-manager" value="WebSocket Manager&#xa;&#xa;• handleConnection(socket)&#xa;• broadcastToClients(event)&#xa;• manageRooms(userId, teamId)&#xa;• subscribeToEvents()&#xa;• handleDisconnection()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="800" y="100" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Event Bus Component -->
        <mxCell id="event-bus" value="Event Bus Component&#xa;&#xa;• publish(eventType, data)&#xa;• subscribe(event, handler)&#xa;• unsubscribe(event, handler)&#xa;• getEventHistory()&#xa;• handleEventFailure()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="480" y="300" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Database Access Layer -->
        <mxCell id="database-layer" value="Database Access Layer&#xa;&#xa;• executeQuery(sql, params)&#xa;• insertDocument(collection, doc)&#xa;• updateRecord(table, data)&#xa;• transaction(operations)&#xa;• getConnection(dbType)" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="480" y="500" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Configuration Service -->
        <mxCell id="config-service" value="Configuration Service&#xa;&#xa;• getSystemConfig()&#xa;• updateSettings(key, value)&#xa;• validateConfiguration()&#xa;• reloadConfig()&#xa;• getEnvironmentVars()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="80" y="300" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Logging Service -->
        <mxCell id="logging-service" value="Logging Service&#xa;&#xa;• logInfo(message, context)&#xa;• logError(error, context)&#xa;• logAudit(action, userId)&#xa;• getLogHistory()&#xa;• rotateLogFiles()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="800" y="300" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- External Dependencies -->
        <mxCell id="mssql-db" value="MSSQL Database&#xa;[External]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="320" y="660" width="150" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="mongodb" value="MongoDB&#xa;[External]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="540" y="660" width="150" height="60" as="geometry" />
        </mxCell>
        
        <!-- Component Interactions -->
        <!-- Authentication to Database -->
        <mxCell id="conn1" value="User Queries" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="auth-service" target="database-layer">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="180" y="560" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Agent Service to Database -->
        <mxCell id="conn2" value="Status Queries" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="agent-service" target="database-layer">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="420" y="460" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Agent Service to Event Bus -->
        <mxCell id="conn3" value="Status Events" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="agent-service" target="event-bus">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="420" y="280" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Message Service to Database -->
        <mxCell id="conn4" value="Message Storage" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="message-service" target="database-layer">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="660" y="460" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Message Service to Event Bus -->
        <mxCell id="conn5" value="Message Events" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="message-service" target="event-bus">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="660" y="280" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- WebSocket Manager to Event Bus -->
        <mxCell id="conn6" value="Subscribe to Events" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="event-bus" target="websocket-manager">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="680" y="240" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Database Layer to External DBs -->
        <mxCell id="conn7" value="SQL Queries" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="database-layer" target="mssql-db">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="520" y="640" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn8" value="Document Queries" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="database-layer" target="mongodb">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="580" y="640" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- All Services to Logging -->
        <mxCell id="conn9" value="Log Events" style="endArrow=classic;html=1;rounded=0;dashed=1;" edge="1" parent="1" source="auth-service" target="logging-service">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="180" y="360" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn10" value="Log Events" style="endArrow=classic;html=1;rounded=0;dashed=1;" edge="1" parent="1" source="agent-service" target="logging-service">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="420" y="360" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn11" value="Log Events" style="endArrow=classic;html=1;rounded=0;dashed=1;" edge="1" parent="1" source="message-service" target="logging-service">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="660" y="360" />
            </Array>
          </mxGeometry>
        </mxCell>
        
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```


### 🎨 Draw.io Code สำหรับ C3 - Desktop Application Components

```xml
<mxfile host="app.diagrams.net">
  <diagram name="C3-Desktop-App-Components">
    <mxGraphModel dx="1422" dy="950" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        
        <!-- Container Boundary -->
        <mxCell id="container-boundary" value="Agent Desktop Application Container&#xa;[Electron.js + React + TypeScript]" style="rounded=0;whiteSpace=wrap;html=1;fillColor=none;strokeColor=#6c8ebf;strokeWidth=3;fontSize=16;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="40" y="40" width="1080" height="580" as="geometry" />
        </mxCell>
        
        <!-- Authentication Component -->
        <mxCell id="auth-component" value="Authentication Component&#xa;&#xa;• login(credentials)&#xa;• logout()&#xa;• validateSession()&#xa;• getCurrentUser()&#xa;• refreshToken()&#xa;• handleTokenExpiry()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="80" y="100" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Status Management Component -->
        <mxCell id="status-component" value="Status Management Component&#xa;&#xa;• changeStatus(newStatus)&#xa;• getCurrentStatus()&#xa;• getStatusHistory()&#xa;• validateStatusChange()&#xa;• showStatusDropdown()&#xa;• handleStatusError()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="320" y="100" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Notification Component -->
        <mxCell id="notification-component" value="Notification Component&#xa;&#xa;• showNotification(message)&#xa;• playNotificationSound()&#xa;• displaySystemAlert()&#xa;• showMessagePopup()&#xa;• managePriority()&#xa;• dismissNotification()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="560" y="100" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- Profile Component -->
        <mxCell id="profile-component" value="Profile Component&#xa;&#xa;• getProfile()&#xa;• updatePreferences()&#xa;• saveSettings()&#xa;• changePassword()&#xa;• updateAvatar()&#xa;• managePersonalInfo()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="800" y="100" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- WebSocket Client Component -->
        <mxCell id="websocket-client" value="WebSocket Client Component&#xa;&#xa;• connect(serverUrl)&#xa;• disconnect()&#xa;• subscribe(eventType)&#xa;• emit(event, data)&#xa;• handleReconnection()&#xa;• manageConnectionState()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="200" y="300" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- UI State Manager -->
        <mxCell id="state-manager" value="UI State Manager&#xa;&#xa;• updateApplicationState()&#xa;• manageGlobalState()&#xa;• persistLocalData()&#xa;• handleStateChanges()&#xa;• synchronizeWithServer()&#xa;• cacheUserPreferences()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="480" y="300" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- API Client Component -->
        <mxCell id="api-client" value="API Client Component&#xa;&#xa;• makeRequest(endpoint, data)&#xa;• handleAuthentication()&#xa;• manageHttpHeaders()&#xa;• handleErrorResponses()&#xa;• retryFailedRequests()&#xa;• cacheApiResponses()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="720" y="300" width="200" height="120" as="geometry" />
        </mxCell>
        
        <!-- External API Server -->
        <mxCell id="api-server" value="API Server&#xa;[External]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="820" y="500" width="120" height="60" as="geometry" />
        </mxCell>
        
        <!-- WebSocket Server -->
        <mxCell id="websocket-server" value="WebSocket Server&#xa;[External]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="240" y="500" width="120" height="60" as="geometry" />
        </mxCell>
        
        <!-- Component Interactions -->
        <!-- Auth Component to API Client -->
        <mxCell id="conn1" value="Login Requests" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="auth-component" target="api-client">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="180" y="360" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Status Component to API Client -->
        <mxCell id="conn2" value="Status Updates" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="status-component" target="api-client">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="420" y="280" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Status Component to WebSocket -->
        <mxCell id="conn3" value="Real-time Status" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="status-component" target="websocket-client">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="420" y="280" />
              <mxPoint x="300" y="280" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- WebSocket to Notification -->
        <mxCell id="conn4" value="Push Notifications" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="websocket-client" target="notification-component">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="300" y="240" />
              <mxPoint x="660" y="240" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Profile Component to API Client -->
        <mxCell id="conn5" value="Profile Updates" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="profile-component" target="api-client">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="900" y="280" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- All Components to State Manager -->
        <mxCell id="conn6" value="State Updates" style="endArrow=classic;html=1;rounded=0;dashed=1;" edge="1" parent="1" source="auth-component" target="state-manager">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="180" y="270" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn7" value="State Updates" style="endArrow=classic;html=1;rounded=0;dashed=1;" edge="1" parent="1" source="status-component" target="state-manager">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <!-- External Connections -->
        <mxCell id="conn8" value="HTTPS Requests" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="api-client" target="api-server">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <mxCell id="conn9" value="WebSocket Connection" style="endArrow=classic;startArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="websocket-client" target="websocket-server">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## การเชื่อมโยงและความต่อเนื่อง

### 🔄 Evolution from C1 → C2 → C3

**การพัฒนาแบบเป็นขั้นตอน:**

```
C1: "Agent Wallboard System ทำอะไร?"
    ↓ ซูมเข้าไป
C2: "ประกอบด้วยแอปพลิเคชันและเทคโนโลยีอะไรบ้าง?"
    ↓ ซูมเข้าไปอีก
C3: "แต่ละแอปพลิเคชันมี components อะไรภายใน?"
    ↓ (สัปดาห์หน้า)
C4: "Components เหล่านี้ implement ด้วยโค้ดอย่างไร?"
```

### 🎯 ความเชื่อมโยง Detail Level

**C1 → C2 Mapping:**
- C1 "Agent Wallboard System" → C2 แยกเป็น 6 containers
- C1 "Call Center Agents" → C2 "Agent Desktop App"
- C1 "Supervisors" → C2 "Supervisor Web Dashboard"
- C1 System boundary → C2 API Server + Databases

**C2 → C3 Mapping:**
- C2 "API Server" → C3 แยกเป็น 7 major components
- C2 "Desktop App" → C3 แยกเป็น 7 UI components
- C2 "Web Dashboard" → C3 แยกเป็น 5 dashboard components
- C2 Database layer → C3 Database access components

### 📊 Consistency Validation

**เชื่อมโยงการทำงาน:**

**Agent Status Change Flow ผ่าน C1-C2-C3:**

**C1 Level:** Agent → System → Supervisor
**C2 Level:** Desktop App → API Server → Web Dashboard  
**C3 Level:** Status Component → Agent Service → Dashboard Visualization

```
C3 Level Detail:
Agent clicks "Change to Busy"
    ↓
Status Management Component.changeStatus("Busy")
    ↓
API Client Component.makeRequest("/agents/status", {status: "Busy"})
    ↓
API Server: Agent Status Service.updateStatus()
    ↓
Database Access Layer.executeQuery("UPDATE agents...")
    ↓
Event Bus Component.publish("agent_status_changed")
    ↓
WebSocket Manager.broadcastToClients("status_update")
    ↓
Supervisor Web Dashboard: Agent Monitor Component.updateDisplay()
```

### 🏗️ Architecture Decision Traceability

**การตัดสินใจใน C1 → สะท้อนใน C2 → ลงรายละเอียดใน C3:**

**Decision: "Real-time Communication Required"**
- **C1:** แสดงเป็น bidirectional arrows ระหว่าง actors
- **C2:** เพิ่ม WebSocket Server container แยกจาก API Server
- **C3:** WebSocket Manager component + Event Bus component

**Decision: "Support Multiple User Types"**
- **C1:** แสดง 3 กลุ่มผู้ใช้ที่แตกต่างกัน
- **C2:** แยก Desktop App และ Web Dashboard
- **C3:** แต่ละ app มี component sets ที่แตกต่างกัน

**Decision: "Hybrid Database Strategy"**
- **C1:** ไม่แสดงรายละเอียด database
- **C2:** แสดง MSSQL + MongoDB แยกกัน
- **C3:** Database Access Layer มี adapters สำหรับทั้งสอง

---

## Draw.io Import Codes

### 📥 วิธีการ Import ไฟล์ Draw.io

**ขั้นตอนการ Import:**

1. **เปิด Draw.io** (https://app.diagrams.net)
2. **คลิก "File" → "Import from..." → "Text"**
3. **Copy โค้ด XML** จากส่วน C1, C2, หรือ C3 ด้านบน
4. **Paste ลงใน text box** 
5. **คลิก "Import"**
6. **แก้ไขตำแหน่งและสี** ตามต้องการ

### 🎨 Draw.io Code สำหรับ C3 - Web Dashboard Components

```xml
<mxfile host="app.diagrams.net">
  <diagram name="C3-Web-Dashboard-Components">
    <mxGraphModel dx="1422" dy="950" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        
        <!-- Container Boundary -->
        <mxCell id="container-boundary" value="Supervisor Web Dashboard Container&#xa;[React.js + TypeScript + Chart.js]" style="rounded=0;whiteSpace=wrap;html=1;fillColor=none;strokeColor=#6c8ebf;strokeWidth=3;fontSize=16;fontStyle=1;" vertex="1" parent="1">
          <mxGeometry x="40" y="40" width="1080" y="740" as="geometry" />
        </mxCell>
        
        <!-- Dashboard Visualization Component -->
        <mxCell id="dashboard-viz" value="Dashboard Visualization Component&#xa;&#xa;• renderRealTimeCharts()&#xa;• updateKPIMetrics()&#xa;• displayTeamOverview()&#xa;• refreshDashboard()&#xa;• exportDashboardData()&#xa;• customizeDashboardLayout()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="80" y="100" width="220" height="130" as="geometry" />
        </mxCell>
        
        <!-- Agent Monitor Component -->
        <mxCell id="agent-monitor" value="Agent Monitor Component&#xa;&#xa;• displayAgentList()&#xa;• showAgentDetails(agentId)&#xa;• filterAgentsByStatus()&#xa;• sortAgentsByMetric()&#xa;• viewAgentHistory()&#xa;• highlightCriticalAgents()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="340" y="100" width="220" height="130" as="geometry" />
        </mxCell>
        
        <!-- Message Management Component -->
        <mxCell id="message-mgmt" value="Message Management Component&#xa;&#xa;• sendIndividualMessage()&#xa;• broadcastToTeam()&#xa;• scheduleMessage()&#xa;• viewMessageHistory()&#xa;• manageMessageTemplates()&#xa;• trackMessageDelivery()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="600" y="100" width="220" height="130" as="geometry" />
        </mxCell>
        
        <!-- Reports Component -->
        <mxCell id="reports-component" value="Reports Component&#xa;&#xa;• generateDailyReport()&#xa;• createCustomReport()&#xa;• scheduleAutomatedReports()&#xa;• exportToPDF()&#xa;• exportToExcel()&#xa;• visualizeReportData()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="860" y="100" width="220" height="130" as="geometry" />
        </mxCell>
        
        <!-- Control Panel Component -->
        <mxCell id="control-panel" value="Control Panel Component&#xa;&#xa;• manageTeamSettings()&#xa;• configureAlertThresholds()&#xa;• updateUserPermissions()&#xa;• systemHealthCheck()&#xa;• viewAuditLogs()&#xa;• manageAgentAccounts()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="80" y="280" width="220" height="130" as="geometry" />
        </mxCell>
        
        <!-- Real-time Data Service -->
        <mxCell id="realtime-service" value="Real-time Data Service&#xa;&#xa;• subscribeToUpdates()&#xa;• handleWebSocketEvents()&#xa;• updateComponentState()&#xa;• manageDataRefresh()&#xa;• cacheRecentData()&#xa;• handleConnectionLoss()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#e1d5e7;strokeColor=#9673a6;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="340" y="280" width="220" height="130" as="geometry" />
        </mxCell>
        
        <!-- API Client Service -->
        <mxCell id="api-client-service" value="API Client Service&#xa;&#xa;• makeAuthenticatedRequests()&#xa;• handleTokenRefresh()&#xa;• manageRequestQueue()&#xa;• processAPIResponses()&#xa;• handleAPIErrors()&#xa;• cacheAPIData()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#fff2cc;strokeColor=#d6b656;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="600" y="280" width="220" height="130" as="geometry" />
        </mxCell>
        
        <!-- State Management Service -->
        <mxCell id="state-mgmt" value="State Management Service&#xa;&#xa;• manageGlobalState()&#xa;• updateComponentStates()&#xa;• persistUserPreferences()&#xa;• handleStateConflicts()&#xa;• syncStateWithServer()&#xa;• provideStateToComponents()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="860" y="280" width="220" height="130" as="geometry" />
        </mxCell>
        
        <!-- Chart Library Wrapper -->
        <mxCell id="chart-wrapper" value="Chart Library Wrapper&#xa;&#xa;• createLineChart()&#xa;• createBarChart()&#xa;• createPieChart()&#xa;• updateChartData()&#xa;• customizeChartAppearance()&#xa;• exportChartAsImage()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="80" y="460" width="220" height="130" as="geometry" />
        </mxCell>
        
  <!-- Notification Service -->
        <mxCell id="notification-service" value="Notification Service&#xa;&#xa;• showToastNotification()&#xa;• displaySystemAlert()&#xa;• playNotificationSound()&#xa;• managePriorityLevels()&#xa;• dismissNotifications()&#xa;• configureNotificationPrefs()" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#d5e8d4;strokeColor=#82b366;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="340" y="460" width="220" height="130" as="geometry" />
        </mxCell>
        
        <!-- External Services -->
        <mxCell id="api-server-ext" value="API Server&#xa;[External]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="680" y="650" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="websocket-server-ext" value="WebSocket Server&#xa;[External]" style="rounded=1;whiteSpace=wrap;html=1;fillColor=#ffe6cc;strokeColor=#d79b00;fontSize=12;" vertex="1" parent="1">
          <mxGeometry x="400" y="650" width="120" height="60" as="geometry" />
        </mxCell>
        
        <!-- Component Interactions -->
        <!-- Dashboard Viz to Chart Wrapper -->
        <mxCell id="conn1" value="Chart Requests" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="dashboard-viz" target="chart-wrapper">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <!-- Dashboard Viz to Real-time Service -->
        <mxCell id="conn2" value="Data Subscription" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="dashboard-viz" target="realtime-service">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="190" y="345" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Agent Monitor to API Client -->
        <mxCell id="conn3" value="Agent Data Requests" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="agent-monitor" target="api-client-service">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="450" y="345" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Message Management to API Client -->
        <mxCell id="conn4" value="Send Message Requests" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="message-mgmt" target="api-client-service">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <!-- Reports to API Client -->
        <mxCell id="conn5" value="Report Data Requests" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="reports-component" target="api-client-service">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="970" y="345" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Control Panel to API Client -->
        <mxCell id="conn6" value="Configuration Requests" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="control-panel" target="api-client-service">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="190" y="345" />
              <mxPoint x="710" y="345" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Real-time Service to WebSocket Server -->
        <mxCell id="conn7" value="WebSocket Connection" style="endArrow=classic;startArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="realtime-service" target="websocket-server-ext">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <!-- API Client to API Server -->
        <mxCell id="conn8" value="HTTPS Requests" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="api-client-service" target="api-server-ext">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="710" y="450" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <!-- Real-time to Notification Service -->
        <mxCell id="conn9" value="Alert Events" style="endArrow=classic;html=1;rounded=0;" edge="1" parent="1" source="realtime-service" target="notification-service">
          <mxGeometry relative="1" as="geometry" />
        </mxCell>
        
        <!-- All Components to State Management (dashed lines) -->
        <mxCell id="conn10" value="State Updates" style="endArrow=classic;html=1;rounded=0;dashed=1;" edge="1" parent="1" source="dashboard-viz" target="state-mgmt">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="190" y="345" />
              <mxPoint x="970" y="345" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn11" value="State Updates" style="endArrow=classic;html=1;rounded=0;dashed=1;" edge="1" parent="1" source="agent-monitor" target="state-mgmt">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="450" y="345" />
              <mxPoint x="970" y="345" />
            </Array>
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn12" value="State Updates" style="endArrow=classic;html=1;rounded=0;dashed=1;" edge="1" parent="1" source="message-mgmt" target="state-mgmt">
          <mxGeometry relative="1" as="geometry">
            <Array as="points">
              <mxPoint x="710" y="345" />
            </Array>
          </mxGeometry>
        </mxCell>
        
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

### 📋 Complete Component Interface Specifications

### 🔧 Agent Status Service Interface

```typescript
interface IAgentStatusService {
  // Core Status Management
  updateStatus(agentId: string, newStatus: AgentStatus, reason?: string): Promise<StatusUpdateResult>;
  getCurrentStatus(agentId: string): Promise<AgentStatus>;
  getTeamStatus(teamId: string): Promise<TeamStatusSummary>;
  
  // Status History & Analytics
  getStatusHistory(agentId: string, dateRange: DateRange): Promise<StatusHistory[]>;
  getStatusDuration(agentId: string, status: AgentStatus): Promise<number>;
  
  // Status Validation & Business Rules
  validateStatusTransition(currentStatus: AgentStatus, newStatus: AgentStatus): boolean;
  getAvailableStatusOptions(agentId: string): Promise<AgentStatus[]>;
  
  // Event Broadcasting
  subscribeToStatusChanges(callback: (event: StatusChangeEvent) => void): void;
  unsubscribeFromStatusChanges(callback: (event: StatusChangeEvent) => void): void;
}

// Supporting Types
type AgentStatus = 'Available' | 'Busy' | 'Away' | 'Break' | 'Offline' | 'Training';

interface StatusUpdateResult {
  success: boolean;
  previousStatus?: AgentStatus;
  newStatus: AgentStatus;
  timestamp: Date;
  error?: string;
}

interface TeamStatusSummary {
  teamId: string;
  totalAgents: number;
  statusBreakdown: Record<AgentStatus, number>;
  averageStatusDuration: Record<AgentStatus, number>;
  lastUpdated: Date;
}

interface StatusChangeEvent {
  agentId: string;
  oldStatus: AgentStatus;
  newStatus: AgentStatus;
  timestamp: Date;
  reason?: string;
}
```

### 🔧 WebSocket Manager Interface

```typescript
interface IWebSocketManager {
  // Connection Management
  handleConnection(socket: Socket, userId: string): Promise<void>;
  handleDisconnection(socket: Socket): Promise<void>;
  getActiveConnections(): Map<string, Socket>;
  
  // Room & Namespace Management
  joinRoom(socket: Socket, roomId: string): Promise<void>;
  leaveRoom(socket: Socket, roomId: string): Promise<void>;
  createTeamRoom(teamId: string): Promise<string>;
  
  // Broadcasting
  broadcastToAll(event: string, data: any): Promise<void>;
  broadcastToRoom(roomId: string, event: string, data: any): Promise<void>;
  broadcastToUser(userId: string, event: string, data: any): Promise<void>;
  
  // Event Handling
  subscribeToEvents(eventType: string, handler: (data: any) => void): void;
  emitToClient(socketId: string, event: string, data: any): Promise<boolean>;
  
  // Health & Monitoring
  getConnectionStats(): ConnectionStats;
  pingAllConnections(): Promise<PingResults>;
  handleReconnection(socket: Socket): Promise<void>;
}

interface ConnectionStats {
  totalConnections: number;
  activeConnections: number;
  roomsCount: number;
  averageLatency: number;
  lastHeartbeat: Date;
}

interface PingResults {
  totalPinged: number;
  successful: number;
  failed: number;
  averageResponseTime: number;
}
```

### 🔧 Database Access Layer Interface

```typescript
interface IDatabaseAccessLayer {
  // Generic Query Operations
  executeQuery<T>(query: string, parameters?: any[]): Promise<T[]>;
  executeScalar<T>(query: string, parameters?: any[]): Promise<T>;
  executeNonQuery(query: string, parameters?: any[]): Promise<number>;
  
  // Transaction Management
  beginTransaction(): Promise<Transaction>;
  commitTransaction(transaction: Transaction): Promise<void>;
  rollbackTransaction(transaction: Transaction): Promise<void>;
  
  // Connection Management
  getConnection(databaseType: 'MSSQL' | 'MongoDB'): Promise<DatabaseConnection>;
  releaseConnection(connection: DatabaseConnection): Promise<void>;
  testConnection(): Promise<ConnectionTestResult>;
  
  // MSSQL Specific
  executeSQLStoredProcedure(procedureName: string, parameters: any[]): Promise<any>;
  executeSQLBulkInsert(tableName: string, data: any[]): Promise<number>;
  
  // MongoDB Specific
  insertDocument(collection: string, document: any): Promise<InsertResult>;
  findDocuments(collection: string, query: any, options?: FindOptions): Promise<any[]>;
  updateDocument(collection: string, filter: any, update: any): Promise<UpdateResult>;
  deleteDocument(collection: string, filter: any): Promise<DeleteResult>;
  
  // Health Monitoring
  getConnectionPoolStats(): PoolStats;
  healthCheck(): Promise<HealthCheckResult>;
}

interface Transaction {
  id: string;
  startTime: Date;
  isolation: 'READ_COMMITTED' | 'READ_UNCOMMITTED' | 'REPEATABLE_READ' | 'SERIALIZABLE';
}

interface ConnectionTestResult {
  mssqlConnected: boolean;
  mongodbConnected: boolean;
  latency: {
    mssql: number;
    mongodb: number;
  };
  errors?: string[];
}

interface PoolStats {
  mssql: {
    totalConnections: number;
    activeConnections: number;
    idleConnections: number;
    queuedRequests: number;
  };
  mongodb: {
    totalConnections: number;
    activeConnections: number;
    idleConnections: number;
  };
}
```

---

## 🎯 การสรุปและแนวทางต่อไป

### 📊 สรุป C4 Model Journey

**เรื่องราวการออกแบบ Agent Wallboard System:**

```
1. C1 (Context): "ระบบนี้อยู่ในบริบทอะไร?"
   → Agent Wallboard System ใน Call Center environment
   → ผู้ใช้: Agents, Supervisors, Managers
   → External systems: Email, SMS (optional)

2. C2 (Container): "ใช้เทคโนโลยีอะไรบ้าง?"
   → Desktop App (Electron.js), Web Dashboard (React.js)
   → API Server (Node.js), WebSocket Server (Socket.io)
   → Databases (MSSQL + MongoDB)

3. C3 (Component): "แต่ละ container มีส่วนประกอบอะไร?"
   → Desktop App: 7 components (Auth, Status, Notification, etc.)
   → API Server: 7 services (Auth, Agent Status, Message, etc.)
   → Web Dashboard: 8 components (Visualization, Monitor, etc.)
```

### 🚀 Next Steps สำหรับการใช้งาน

**1. วิธีใช้ Diagrams เหล่านี้:**
- **C1 สำหรับ Stakeholders:** แสดงให้ management เห็นภาพรวม
- **C2 สำหรับ Tech Leads:** วางแผน infrastructure และ deployment
- **C3 สำหรับ Developers:** แบ่ง tasks และ implement components

**2. การ Validate Design:**
- ตรวจสอบว่า C1 requirements ครบถ้วนใน C2-C3 หรือไม่
- Trace user journeys ผ่าน component interactions
- Verify non-functional requirements (performance, security, scalability)

**3. Implementation Planning:**
- ใช้ C3 component breakdown เป็น development backlog
- กำหนด priorities และ dependencies ระหว่าง components
- Plan integration testing strategies

### 📚 Learning Outcomes

**จากเอกสารนี้ คุณได้เรียนรู้:**

✅ **C4 Model Methodology** - วิธีการออกแบบ architecture แบบเป็นขั้นตอน
✅ **Progressive Detailing** - การซูมเข้าจากภาพใหญ่สู่รายละเอียด
✅ **Consistency Validation** - การตรวจสอบความเชื่อมโยงระหว่างระดับ
✅ **Documentation Standards** - การสร้างเอกสาร architecture ที่เป็นมาตรฐาน
✅ **Tool Usage** - การใช้ Draw.io สร้าง professional diagrams
✅ **Real-world Application** - การประยุกต์ใช้กับ Agent Wallboard System จริง

### 🔄 Continuous Improvement

**การปรับปรุงและพัฒนา:**
- **รับ feedback** จาก stakeholders และปรับปรุง diagrams
- **Update architecture** เมื่อมีการเปลี่ยนแปลง requirements
- **Version control** สำหรับ architecture documents
- **Regular reviews** เพื่อ validate กับ implementation จริง

**🎊 ขอแสดงความยินดี!** คุณได้เรียนรู้การสร้าง Complete C4 Model Architecture Design แล้ว พร้อมสำหรับการนำไปใช้ในโปรเจกต์จริง!# C4 Model Complete Guide: จาก C1 ไป C2 ไป C3