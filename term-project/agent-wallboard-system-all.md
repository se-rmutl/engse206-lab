# Overall Context Analysis - Agent Wallboard System

## 1. Executive Summary

Agent Wallboard System เป็นระบบ real-time monitoring และการจัดการสำหรับ Call Center agents ที่พัฒนาด้วย 3-Tier Architecture โดยมีจุดประสงค์เพื่อให้ผู้บริหารและ supervisors สามารถติดตามสถานะของ agents แบบ real-time และสามารถสื่อสารกับ agents ได้อย่างมีประสิทธิภาพ

---

## 2. Business Context & Current Situation

### 2.1 ธุรกิจและสภาพแวดล้อม
- **อุตสาหกรรม**: Call Center และ Customer Service
- **ขนาดองค์กร**: Medium to Large Call Centers (50-500 agents)
- **การทำงาน**: 24/7 operations with multiple teams และ shifts
- **เทคโนโลยีปัจจุบัน**: Legacy systems ที่ไม่สามารถให้ข้อมูล real-time ได้

### 2.2 Business Drivers
- **ต้องการเพิ่มประสิทธิภาพ**: การทำงานของ call center agents
- **การตอบสนองลูกค้า**: ลดเวลาการรอคอยและปรับปรุง customer satisfaction
- **การจัดการทีม**: ต้องการเครื่องมือในการควบคุมและติดตาม agent performance
- **Operational Excellence**: เพิ่ม efficiency และลด operational costs

---

## 3. Current Problems & Pain Points

### 3.1 ปัญหาหลัก (Core Problems)

#### 🚨 **Problem 1: Lack of Real-time Visibility**
- **ปัญหา**: ผู้บริหารไม่สามารถติดตามสถานะของ agents แบบ real-time ได้
- **ผลกระทบ**: ไม่สามารถจัดการ workload และตอบสนองต่อปัญหาได้อย่างทันท่วงที
- **หลักฐาน**: Queue buildup, missed SLA targets, customer complaints

#### 📞 **Problem 2: Inefficient Communication**
- **ปัญหา**: การสื่อสารระหว่าง supervisors กับ agents ยังไม่มีประสิทธิภาพ
- **ผลกระทบ**: ข้อมูลไม่ถูกส่งผ่านอย่างรวดเร็ว, miscommunication
- **หลักฐาน**: Delayed instructions, manual notification processes

#### 📊 **Problem 3: Manual Monitoring**
- **ปัญหา**: การติดตาม agent status และ performance เป็น manual process
- **ผลกระทบ**: สูญเสียเวลา, human error, delayed response
- **หลักฐาน**: Manual reports, Excel spreadsheets, delayed status updates

#### 🔄 **Problem 4: No Agent Status Standardization**
- **ปัญหา**: ไม่มีมาตรฐานในการแสดงสถานะของ agents
- **ผลกระทบ**: confusion, inconsistent reporting
- **หลักฐาน**: Different teams use different status definitions

### 3.2 ปัญหารอง (Secondary Problems)
- **Data Silos**: ข้อมูลกระจัดกระจายในหลายระบบ
- **Limited Mobility**: ไม่สามารถติดตามสถานะจากอุปกรณ์มือถือได้
- **Reporting Gaps**: ไม่มี real-time dashboard สำหรับผู้บริหาร
- **Agent Productivity**: ขาดเครื่องมือในการจัดการงานของ agents

---

## 4. Target Users & Personas

### 👨‍💼 **Persona 1: Call Center Supervisor - "Manager Mike"**

**Demographics:**
- อายุ: 35-45 ปี
- ตำแหน่ง: Team Lead / Supervisor
- ประสบการณ์: 8-15 ปีในการทำ Call Center
- เทคโนโลยี: Moderate to High tech-savvy

**Goals & Motivations:**
- 🎯 **Primary Goal**: ติดตาม team performance แบบ real-time
- 📈 **KPI Focus**: เพิ่ม team efficiency และ customer satisfaction
- 🚀 **Career Goal**: ก้าวขึ้นเป็น Operations Manager

**Pain Points:**
- ไม่สามารถเห็นสถานะ agents ทั้งหมดในเวลาเดียวกัน
- ต้องเดินไป check agents แต่ละคนเป็นรายบุคคล
- การส่ง notification ต้องใช้หลายช่องทาง (email, phone, in-person)
- รายงานต้องรอ end-of-day ถึงจะได้ข้อมูลสมบูรณ์

**User Scenarios:**
- ตรวจสอบสถานะทีมตอนเช้าก่อนเริ่มงาน
- ติดตาม real-time performance ระหว่างวัน
- ส่งข้อความด่วนให้ agents เมื่อมี priority calls
- ดู dashboard เพื่อ report ให้ management

**Technology Usage:**
- ใช้คอมพิวเตอร์ desktop เป็นหลัก
- มี smartphone สำหรับงานนอกสถานที่
- คุ้นเคยกับ web browsers และ business applications

---

### 🎧 **Persona 2: Call Center Agent - "Agent Anna"**

**Demographics:**
- อายุ: 22-35 ปี
- ตำแหน่ง: Customer Service Representative
- ประสบการณ์: 1-5 ปีในการทำ Call Center
- เทคโนโลยี: Basic to Moderate tech-savvy

**Goals & Motivations:**
- 🎯 **Primary Goal**: ปฏิบัติงานได้อย่างมีประสิทธิภาพและได้รับ feedback ที่ดี
- 💰 **Financial Goal**: ได้รับ bonus จาก performance metrics
- 📚 **Learning Goal**: พัฒนาทักษะเพื่อเลื่อนตำแหน่ง

**Pain Points:**
- ไม่ทราบว่า supervisor ต้องการอะไรจากตนในแต่ละช่วงเวลา
- ไม่สามารถเปลี่ยนสถานะตัวเองได้อย่างรวดเร็ว
- ไม่ได้รับข้อมูลอัปเดตที่สำคัญทันเวลา
- ไม่มีช่องทางสื่อสารที่ตรงไปตรงมากับ supervisor

**User Scenarios:**
- Login เข้าระบบตอนเริ่มงานและ update status เป็น "Available"
- เปลี่ยนสถานะเป็น "Wrap" หลังจบการโทร
- รับ notification จาก supervisor เรื่องงานเร่งด่วน
- ส่งข้อความถาม supervisor เมื่อมีปัญหา

**Technology Usage:**
- ใช้คอมพิวเตอร์ desktop ในการทำงาน
- มี smartphone ส่วนตัว
- คุ้นเคยกับ basic applications และ web interfaces

---

### 🏢 **Persona 3: Operations Manager - "Director David"**

**Demographics:**
- อายุ: 40-55 ปี
- ตำแหน่ง: Operations Manager / Director
- ประสบการณ์: 15+ ปีในการจัดการ Call Center
- เทคโนโลยี: Moderate tech-savvy, focus on business value

**Goals & Motivations:**
- 🎯 **Primary Goal**: เพิ่ม overall call center performance และ ROI
- 📊 **Strategic Goal**: ใช้ data-driven decision making
- 🏆 **Organizational Goal**: สร้างความได้เปรียบทางการแข่งขัน

**Pain Points:**
- ไม่มี executive dashboard สำหรับติดตาม high-level metrics
- ข้อมูลที่ได้รับมามักจะ outdated หรือไม่ complete
- ต้องรอรายงานจาก supervisors หลายคน
- ไม่สามารถ drill-down ลงไปดูรายละเอียดได้ทันที

**User Scenarios:**
- เช็ค overall performance dashboard ตอนเช้า
- ดู real-time metrics ระหว่าง busy periods
- วิเคราะห์ trend data สำหรับ strategic planning
- Present performance report ให้ C-level executives

**Technology Usage:**
- ใช้ laptop/desktop และ tablet สำหรับ mobility
- ต้องการ executive-level dashboard
- มักจะ delegate technical tasks ให้ทีม

---

### 🛠️ **Persona 4: IT Administrator - "TechOps Tom"**

**Demographics:**
- อายุ: 28-40 ปี
- ตำแหน่ง: IT Administrator / System Administrator
- ประสบการณ์: 5-12 ปีในการจัดการระบบ IT
- เทคโนโลยี: High tech-savvy

**Goals & Motivations:**
- 🎯 **Primary Goal**: รักษาระบบให้ทำงานได้ stable และ secure
- 🔧 **Technical Goal**: implement best practices และ automation
- 📈 **Career Goal**: พัฒนาทักษะใน modern technologies

**Pain Points:**
- ต้องจัดการหลายระบบที่แยกกัน
- ไม่มี centralized monitoring สำหรับ application health
- การ troubleshoot ต้องใช้เวลานาน
- user training และ support requests เยอะ

**User Scenarios:**
- ติดตั้งและ configure ระบบใหม่
- Monitor system performance และ uptime
- จัดการ user accounts และ permissions
- Provide technical support ให้ users

**Technology Usage:**
- เชี่ยวชาญใน server administration, databases, networking
- ใช้ command line tools และ monitoring systems
- ต้องการ API access และ technical documentation

---

## 5. Success Criteria & Business Value

### 5.1 Measurable Outcomes
- **📊 Performance Metrics**:
  - ลด average response time ลง 25%
  - เพิ่ม agent utilization rate เป็น 85%+
  - ลด manual monitoring effort ลง 60%

- **💰 Business Impact**:
  - ลด operational cost ลง 15-20%
  - เพิ่ม customer satisfaction score ขึ้น 10%
  - ROI ภายใน 18 เดือน

### 5.2 Qualitative Benefits
- ปรับปรุง employee satisfaction
- เพิ่ม management visibility
- ลด training time สำหรับ new supervisors
- เพิ่ม operational agility

---

## 6. Technical Context

### 6.1 Current Technology Stack
- **Legacy Systems**: MSSQL databases, manual Excel reports
- **Infrastructure**: Windows-based desktop applications
- **Communication**: Email, phone calls, manual notifications

### 6.2 Proposed Solution Architecture
- **3-Tier Architecture**: 
  - **Presentation Tier**: Desktop Application (Electron.js)
  - **Application Tier**: REST API (Node.js + Express)
  - **Data Tier**: MSSQL & MongoDB databases

### 6.3 Key Technical Features
- **Real-time Communication**: WebSocket implementation
- **Cross-platform**: Web and Desktop support
- **Scalable**: Modular architecture design
- **Secure**: Authentication and authorization

---

## 7. Next Steps

การวิเคราะห์ context นี้จะนำไปสู่การสร้าง **User Stories** ที่ครอบคลุม:

1. **Epic 1**: Real-time Agent Status Monitoring
2. **Epic 2**: Supervisor Communication System
3. **Epic 3**: Agent Self-Service Portal
4. **Epic 4**: Management Dashboard & Reporting
5. **Epic 5**: System Administration & Configuration

แต่ละ Epic จะถูกแบ่งเป็น User Stories ที่เฉพาะเจาะจงและสามารถ implement ได้ในแต่ละ Sprint

---

*เอกสารนี้จะเป็นพื้นฐานสำหรับการพัฒนา User Stories และการวางแผน Sprint Planning ในขั้นตอนต่อไป*


# User Stories - Agent Wallboard System

## ภาพรวม
ชุด User Stories นี้ครอบคลุมการพัฒนา Agent Wallboard System ทั้ง 5 Epics ในขอบเขตที่สอดคล้องกับ LAB 5-7 ที่มีอยู่ รวม 14 User Stories

---

## Epic 1: Real-time Agent Status Monitoring

### US-001: การแสดงสถานะ Agent แบบ Real-time
**ในฐานะ** Supervisor ของ Call Center  
**ฉันต้องการ** ดูสถานะปัจจุบันของ agents ทั้งหมดในทีมบน dashboard แบบ real-time  
**เพื่อที่** ฉันจะได้รู้ได้ทันทีว่าใครว่างงาน ใครกำลังยุ่ง หรือใครออฟไลน์  

**Acceptance Criteria:**
- ✅ แสดงรายการ agent พร้อมสถานะปัจจุบัน (Available, Active, Wrap, Not Ready, Offline)
- ✅ แสดง agent code, ชื่อ และสถานะปัจจุบันด้วยสีที่แตกต่างกัน
- ✅ อัปเดตสถานะอัตโนมัติโดยไม่ต้อง refresh หน้าจอ (WebSocket)
- ✅ แสดง timestamp ของการอัปเดตสถานะครั้งล่าสุด

**Priority:** HIGH | **Story Points:** 8 | **Sprint:** 1

---

### US-002: การเปลี่ยนสถานะของ Agent
**ในฐานะ** Agent ของ Call Center  
**ฉันต้องการ** เปลี่ยนสถานะของตัวเองผ่าน desktop application  
**เพื่อที่** supervisor จะได้รู้ว่าฉันพร้อมรับงานหรือไม่  

**Acceptance Criteria:**
- ✅ Agent สามารถเปลี่ยนสถานะผ่าน dropdown (Available, Active, Wrap, Not Ready)
- ✅ การเปลี่ยนสถานะแสดงผลใน wallboard ทันที
- ✅ ระบบบันทึก timestamp ของการเปลี่ยนสถานะ
- ✅ Agent เห็นสถานะปัจจุบันของตัวเองใน application

**Priority:** HIGH | **Story Points:** 5 | **Sprint:** 1

---

### US-003: การติดตาม Login/Logout ของ Agent
**ในฐานะ** Supervisor ของ Call Center  
**ฉันต้องการ** ติดตามเวลา login และ logout ของ agents  
**เพื่อที่** ฉันจะได้ตรวจสอบการเข้างานและความพร้อมใช้งาน  

**Acceptance Criteria:**
- ✅ ระบบบันทึกเวลา login/logout ของแต่ละ agent
- ✅ แสดงสถานะ "Connected" เมื่อ agent login สำเร็จ
- ✅ แสดงสถานะ "Disconnected" เมื่อ agent logout หรือ connection หลุด
- ✅ เก็บ log ประวัติการ login/logout

**Priority:** MEDIUM | **Story Points:** 3 | **Sprint:** 1

---

## Epic 2: Supervisor Communication System

### US-004: การส่งข้อความถึง Agent
**ในฐานะ** Supervisor  
**ฉันต้องการ** ส่งข้อความไปยัง agent ที่เฉพาะเจาะจง  
**เพื่อที่** ฉันจะได้สื่อสารข้อมูลสำคัญหรือคำแนะนำได้ทันที  

**Acceptance Criteria:**
- ✅ Supervisor สามารถเลือก agent ปลายทางและพิมพ์ข้อความ
- ✅ ข้อความส่งผ่าน WebSocket แบบ real-time
- ✅ Agent ได้รับ notification ทันทีเมื่อมีข้อความใหม่
- ✅ แสดง timestamp และผู้ส่งข้อความ

**Priority:** HIGH | **Story Points:** 5 | **Sprint:** 2

---

### US-005: การรับ Notification สำหรับ Agent
**ในฐานะ** Agent  
**ฉันต้องการ** รับ notification เมื่อมีข้อความจาก supervisor  
**เพื่อที่** ฉันจะได้รับทราบข้อมูลสำคัญทันที  

**Acceptance Criteria:**
- ✅ แสดง desktop notification เมื่อมีข้อความใหม่
- ✅ เล่นเสียงแจ้งเตือนเมื่อได้รับข้อความ
- ✅ แสดงข้อความใน popup window พร้อมปุ่ม "Close"
- ✅ บันทึกประวัติข้อความที่ได้รับ

**Priority:** HIGH | **Story Points:** 3 | **Sprint:** 2

---

## Epic 3: Agent Self-Service Portal

### US-006: การ Authentication ของ Agent
**ในฐานะ** Agent  
**ฉันต้องการ** login เข้าระบบด้วย Agent Code  
**เพื่อที่** ฉันจะได้ใช้งาน desktop application ได้  

**Acceptance Criteria:**
- ✅ Agent สามารถใส่ Agent Code เพื่อ login
- ✅ ระบบตรวจสอบ Agent Code กับฐานข้อมูล
- ✅ แสดงข้อผิดพลาดเมื่อ Agent Code ไม่ถูกต้อง
- ✅ เชื่อมต่อ WebSocket หลังจาก login สำเร็จ

**Priority:** HIGH | **Story Points:** 5 | **Sprint:** 1

---

### US-007: การจัดการข้อมูลส่วนตัวของ Agent
**ในฐานะ** Agent  
**ฉันต้องการ** เห็นข้อมูลส่วนตัวและสถานะปัจจุบันของฉัน  
**เพื่อที่** ฉันจะได้ตรวจสอบความถูกต้องของข้อมูล  

**Acceptance Criteria:**
- ✅ แสดง Agent Code และ Agent Name
- ✅ แสดงสถานะปัจจุบันและเวลาที่เริ่มสถานะนั้น
- ✅ แสดงเวลา login ของวันนี้
- ✅ อัปเดตข้อมูลแบบ real-time

**Priority:** MEDIUM | **Story Points:** 2 | **Sprint:** 2

---

## Epic 4: Management Dashboard & Reporting

### US-008: Dashboard สำหรับ Supervisor
**ในฐานะ** Supervisor  
**ฉันต้องการ** dashboard ที่แสดงสถิติโดยรวมของทีม  
**เพื่อที่** ฉันจะได้ตัดสินใจในการจัดการทีมได้อย่างมีข้อมูล  

**Acceptance Criteria:**
- ✅ แสดงจำนวน agents แต่ละสถานะ (Available, Active, Wrap, Not Ready)
- ✅ แสดงจำนวน agents ที่ online/offline
- ✅ แสดงข้อมูลแบบ real-time ด้วย charts/graphs
- ✅ แสดงเวลาปัจจุบันและข้อมูล team summary

**Priority:** HIGH | **Story Points:** 8 | **Sprint:** 2

---

### US-009: การแสดงสถิติแบบ Real-time
**ในฐานะ** Supervisor  
**ฉันต้องการ** เห็นสถิติการทำงานของ agents แบบ real-time  
**เพื่อที่** ฉันจะได้ติดตาม performance ได้ตลอดเวลา  

**Acceptance Criteria:**
- ✅ แสดงจำนวน Total Queue เป็น 0 (placeholder สำหรับ future development)
- ✅ แสดงจำนวน Offer Call และ Abandon Call (placeholder)
- ✅ อัปเดตตัวเลขแบบ real-time
- ✅ ใช้สีและ icon ที่เหมาะสมสำหรับแต่ละประเภท metric

**Priority:** MEDIUM | **Story Points:** 5 | **Sprint:** 3

---

## Epic 5: System Administration & Configuration

### US-010: การจัดการ Agent Database
**ในฐานะ** System Administrator  
**ฉันต้องการ** จัดการข้อมูล agents ในฐานข้อมูล  
**เพื่อที่** ระบบจะทำงานได้อย่างถูกต้องและมี agents ที่จำเป็น  

**Acceptance Criteria:**
- ✅ ระบบเชื่อมต่อกับ MSSQL database ได้
- ✅ สามารถ query ข้อมูล agent จากตาราง OnlineAgents
- ✅ สามารถ insert/update ข้อมูล agent status
- ✅ จัดการ database connection pool อย่างมีประสิทธิภาพ

**Priority:** HIGH | **Story Points:** 5 | **Sprint:** 1

---

### US-011: API Endpoint Management
**ในฐานะ** System Administrator  
**ฉันต้องการ** API endpoints ที่มั่นคงและปลอดภัย  
**เพื่อที่** ระบบจะสื่อสารระหว่าง tiers ได้อย่างถูกต้อง  

**Acceptance Criteria:**
- ✅ มี API endpoint สำหรับ getOnlineAgentByAgentCode
- ✅ มี API endpoint สำหรับ postOnlineAgentStatus
- ✅ มี API endpoint สำหรับ postSendMessage
- ✅ ใช้ Bearer Token authentication
- ✅ ส่ง response ในรูปแบบ JSON ที่มีมาตรฐาน

**Priority:** HIGH | **Story Points:** 8 | **Sprint:** 1

---

### US-012: WebSocket Connection Management
**ในฐานะ** System Administrator  
**ฉันต้องการ** จัดการ WebSocket connections อย่างมีประสิทธิภาพ  
**เพื่อที่** การสื่อสาร real-time จะทำงานได้เสถียร  

**Acceptance Criteria:**
- ✅ จัดการ WebSocket connection pool
- ✅ ตรวจสอบและจัดการ agent ที่ disconnect
- ✅ ส่งข้อความ broadcast ไปยัง agents ที่เกี่ยวข้อง
- ✅ มี error handling สำหรับ connection failures

**Priority:** HIGH | **Story Points:** 8 | **Sprint:** 1

---

### US-013: Desktop Application Distribution
**ในฐานะ** System Administrator  
**ฉันต้องการ** สร้าง installer สำหรับ desktop application  
**เพื่อที่** agents สามารถติดตั้งและใช้งาน application ได้  

**Acceptance Criteria:**
- ✅ สร้าง executable file จาก Electron.js application
- ✅ สร้าง installer package สำหรับ Windows
- ✅ Application สามารถ auto-update configuration ได้
- ✅ มี error handling และ user-friendly messages

**Priority:** MEDIUM | **Story Points:** 3 | **Sprint:** 3

---

### US-014: System Configuration Management
**ในฐานะ** System Administrator  
**ฉันต้องการ** จัดการ configuration ของระบบแยกตาม environment  
**เพื่อที่** จะสามารถ deploy ระบบใน development และ production ได้  

**Acceptance Criteria:**
- ✅ แยก configuration file สำหรับ development/production
- ✅ จัดการ database connection strings แยกตาม environment
- ✅ จัดการ API URLs และ WebSocket endpoints
- ✅ มี SSL certificate management สำหรับ HTTPS

**Priority:** MEDIUM | **Story Points:** 5 | **Sprint:** 2

---

## สรุป User Stories

| Epic | จำนวน Stories | Total Story Points | Priority Distribution |
|------|---------------|-------------------|---------------------|
| Epic 1: Real-time Monitoring | 3 | 16 | HIGH: 2, MEDIUM: 1 |
| Epic 2: Communication | 2 | 8 | HIGH: 2 |
| Epic 3: Agent Portal | 2 | 7 | HIGH: 1, MEDIUM: 1 |
| Epic 4: Dashboard | 2 | 13 | HIGH: 1, MEDIUM: 1 |
| Epic 5: Administration | 5 | 29 | HIGH: 3, MEDIUM: 2 |

**รวมทั้งสิ้น:** 14 User Stories | **Total Effort:** 73 Story Points

---

## Sprint Planning แนะนำ

### Sprint 1 (Foundation) - 3 สัปดาห์
- US-001, US-002, US-006, US-010, US-011, US-012
- **Focus**: Core functionality และ infrastructure

### Sprint 2 (Communication) - 2 สัปดาห์  
- US-004, US-005, US-007, US-008, US-014
- **Focus**: Communication features และ dashboard

### Sprint 3 (Enhancement) - 2 สัปดาห์
- US-003, US-009, US-013
- **Focus**: Additional features และ deployment

---

# Requirement Analysis - Agent Wallboard System

## 📋 สารบัญ
1. [Story Mapping](#story-mapping)
2. [Priority Matrix](#priority-matrix)
3. [Release Planning](#release-planning)
4. [Risk Assessment](#risk-assessment)
5. [Dependencies & Constraints](#dependencies--constraints)

---

## 1. Story Mapping

### 1.1 User Journey Flow

```
🎯 Agent Journey:
Login → Set Status → Receive Messages → Change Status → Logout

👥 Supervisor Journey:  
Login → Monitor Dashboard → Send Messages → Review Reports → Manage Team

🔧 Admin Journey:
Setup System → Configure Database → Deploy Application → Monitor System
```

### 1.2 Story Map Visualization

| **User Activities** | **Sprint 1 (Foundation)** | **Sprint 2 (Features)** | **Sprint 3 (Enhancement)** |
|-------------------|-------------------------|-------------------------|--------------------------|
| **🔐 Authentication** | US-006 (Agent Login)<br/>*5 pts - HIGH* | US-007 (Agent Profile)<br/>*2 pts - MEDIUM* | |
| **📊 Status Management** | US-002 (Status Update)<br/>*5 pts - HIGH*<br/><br/>US-001 (Status Display)<br/>*8 pts - HIGH* | | US-003 (Login Tracking)<br/>*3 pts - MEDIUM* |
| **💬 Communication** | | US-004 (Send Message)<br/>*5 pts - HIGH*<br/><br/>US-005 (Receive Notification)<br/>*3 pts - HIGH* | |
| **📈 Monitoring & Reports** | | US-008 (Dashboard)<br/>*8 pts - HIGH* | US-009 (Real-time Stats)<br/>*5 pts - MEDIUM* |
| **⚙️ Administration** | US-010 (Database Mgmt)<br/>*5 pts - HIGH*<br/><br/>US-011 (API Management)<br/>*8 pts - HIGH*<br/><br/>US-012 (WebSocket Mgmt)<br/>*8 pts - HIGH* | US-014 (Configuration)<br/>*5 pts - MEDIUM* | US-013 (App Distribution)<br/>*3 pts - MEDIUM* |

### 1.3 Feature Breakdown by User Type

#### 👨‍💼 **Supervisor Features** (6 Stories - 34 points)
- **Core**: US-001 (Status Display), US-008 (Dashboard)
- **Communication**: US-004 (Send Messages)
- **Reporting**: US-009 (Real-time Stats)
- **Tracking**: US-003 (Login Tracking)
- **Management**: US-014 (Configuration)

#### 🎧 **Agent Features** (4 Stories - 15 points)
- **Core**: US-002 (Status Updates), US-006 (Authentication)
- **Profile**: US-007 (Personal Info)
- **Communication**: US-005 (Receive Notifications)

#### 🔧 **System Admin Features** (4 Stories - 24 points)
- **Infrastructure**: US-010 (Database), US-011 (APIs), US-012 (WebSocket)
- **Deployment**: US-013 (Distribution)

---

## 2. Priority Matrix

### 2.1 MoSCoW Prioritization

| **MUST HAVE** | **SHOULD HAVE** | **COULD HAVE** | **WON'T HAVE** |
|---------------|-----------------|----------------|----------------|
| **Sprint 1 Core** | **Sprint 2 Features** | **Sprint 3 Nice-to-have** | **Future Releases** |
| US-001 (Status Display) | US-004 (Send Message) | US-003 (Login Tracking) | Advanced Reporting |
| US-002 (Status Update) | US-005 (Notifications) | US-009 (Stats) | Mobile Application |
| US-006 (Authentication) | US-007 (Agent Profile) | US-013 (Distribution) | Integration APIs |
| US-010 (Database Mgmt) | US-008 (Dashboard) | | Multi-language |
| US-011 (API Mgmt) | US-014 (Configuration) | | Advanced Analytics |
| US-012 (WebSocket) | | | Role-based Access |

### 2.2 Value vs Effort Matrix

```
HIGH VALUE, LOW EFFORT          |  HIGH VALUE, HIGH EFFORT
📊 US-002 (Status Update)      |  🎯 US-001 (Status Display)
🔐 US-006 (Authentication)     |  📈 US-008 (Dashboard)
💬 US-005 (Notifications)      |  ⚙️  US-011 (API Management)
                                |  🔗 US-012 (WebSocket Mgmt)
--------------------------------+--------------------------------
LOW VALUE, LOW EFFORT           |  LOW VALUE, HIGH EFFORT
📝 US-007 (Agent Profile)      |  📊 US-009 (Real-time Stats)
📦 US-013 (Distribution)       |  ⚙️  US-014 (Configuration)
🕐 US-003 (Login Tracking)     |
```

### 2.3 Risk vs Impact Assessment

| Story ID | Business Impact | Technical Risk | Overall Priority | Sprint |
|----------|----------------|----------------|------------------|---------|
| US-001 | 🔴 Critical | 🟡 Medium | **P1** | Sprint 1 |
| US-002 | 🔴 Critical | 🟢 Low | **P1** | Sprint 1 |
| US-006 | 🔴 Critical | 🟢 Low | **P1** | Sprint 1 |
| US-010 | 🔴 Critical | 🟡 Medium | **P1** | Sprint 1 |
| US-011 | 🔴 Critical | 🔴 High | **P1** | Sprint 1 |
| US-012 | 🔴 Critical | 🔴 High | **P1** | Sprint 1 |
| US-004 | 🟡 High | 🟡 Medium | **P2** | Sprint 2 |
| US-005 | 🟡 High | 🟢 Low | **P2** | Sprint 2 |
| US-008 | 🟡 High | 🟡 Medium | **P2** | Sprint 2 |
| US-014 | 🟡 High | 🟡 Medium | **P2** | Sprint 2 |
| US-007 | 🟢 Medium | 🟢 Low | **P3** | Sprint 2 |
| US-003 | 🟢 Medium | 🟢 Low | **P3** | Sprint 3 |
| US-009 | 🟢 Medium | 🟡 Medium | **P3** | Sprint 3 |
| US-013 | 🟢 Low | 🟡 Medium | **P3** | Sprint 3 |

---

## 3. Release Planning

### 3.1 Release Strategy Overview

#### 🎯 **Release 1.0 - MVP (Minimum Viable Product)**
- **Timeline**: 7 สัปดาห์ (3 Sprints)
- **Scope**: Core functionality สำหรับ real-time agent monitoring
- **Target**: Internal testing และ pilot deployment

#### 🚀 **Release 2.0 - Enhanced (Future)**
- **Timeline**: +4 สัปดาห์ (2 Sprints เพิ่มเติม)
- **Scope**: Advanced features และ integrations
- **Target**: Full production deployment

### 3.2 Detailed Release Plan

#### **📦 Release 1.0 - Sprint Breakdown**

##### **Sprint 1: Foundation & Infrastructure (21 points) - 3 สัปดาห์**
**Theme**: "พื้นฐานระบบและการเชื่อมต่อ"

| Week | Focus Area | Stories | Deliverables |
|------|------------|---------|--------------|
| **Week 1** | Database & API Setup | US-010, US-011 | • Database schema<br/>• Basic API endpoints<br/>• Authentication system |
| **Week 2** | WebSocket & Authentication | US-012, US-006 | • Real-time connection<br/>• Agent login system<br/>• Connection management |
| **Week 3** | Core Status Management | US-001, US-002 | • Status display dashboard<br/>• Agent status updates<br/>• Integration testing |

**Sprint 1 Success Criteria:**
- ✅ Agent สามารถ login และเปลี่ยนสถานะได้
- ✅ Supervisor เห็นสถานะ agent แบบ real-time
- ✅ WebSocket connection ทำงานเสถียร
- ✅ API endpoints พร้อมใช้งาน

##### **Sprint 2: Communication & Dashboard (34 points) - 2 สัปดาห์**
**Theme**: "การสื่อสารและการจัดการ"

| Week | Focus Area | Stories | Deliverables |
|------|------------|---------|--------------|
| **Week 4** | Communication System | US-004, US-005 | • Message sending system<br/>• Desktop notifications<br/>• Message history |
| **Week 5** | Dashboard & Management | US-008, US-007, US-014 | • Supervisor dashboard<br/>• Agent profile view<br/>• Configuration management |

**Sprint 2 Success Criteria:**
- ✅ Supervisor ส่งข้อความไปหา agent ได้
- ✅ Agent รับ notification ทันที
- ✅ Dashboard แสดงข้อมูลสถิติแบบ real-time
- ✅ Configuration แยกระหว่าง dev/production

##### **Sprint 3: Enhancement & Deployment (18 points) - 2 สัปดาห์**
**Theme**: "การปรับปรุงและการติดตั้ง"

| Week | Focus Area | Stories | Deliverables |
|------|------------|---------|--------------|
| **Week 6** | Additional Features | US-003, US-009 | • Login/logout tracking<br/>• Enhanced statistics<br/>• Performance monitoring |
| **Week 7** | Deployment & Testing | US-013 | • Windows installer<br/>• User documentation<br/>• System testing |

**Sprint 3 Success Criteria:**
- ✅ ระบบติดตาม agent attendance ได้
- ✅ แสดงสถิติ real-time ที่สมบูรณ์
- ✅ มี installer สำหรับ production
- ✅ ผ่าน User Acceptance Testing

### 3.3 Release Milestones & Gates

#### **🏁 Milestone 1: Technical Foundation (End of Sprint 1)**
**Success Metrics:**
- [ ] API response time < 200ms
- [ ] WebSocket connection uptime > 99%
- [ ] Agent login success rate > 95%
- [ ] Zero critical bugs

#### **🏁 Milestone 2: Feature Complete (End of Sprint 2)**
**Success Metrics:**
- [ ] All communication features working
- [ ] Dashboard displays real-time data
- [ ] Message delivery rate > 98%
- [ ] User feedback score > 4/5

#### **🏁 Milestone 3: Production Ready (End of Sprint 3)**
**Success Metrics:**
- [ ] Load testing passed (50 concurrent agents)
- [ ] Security testing completed
- [ ] Installation success rate > 95%
- [ ] User training completed

### 3.4 Go-Live Strategy

#### **🎯 Pilot Phase (Week 8)**
- **Scope**: 10-15 agents ในทีมเดียว
- **Duration**: 1 สัปดาห์
- **Focus**: ทดสอบการใช้งานจริงและ feedback

#### **🚀 Rollout Phase (Week 9-10)**
- **Scope**: ทีมละ 20-30 agents
- **Duration**: 2 สัปดาห์
- **Focus**: การ scale up และ performance tuning

#### **✅ Full Production (Week 11+)**
- **Scope**: ทุก agents ในองค์กร
- **Focus**: Monitoring และ continuous improvement

---

## 4. Risk Assessment

### 4.1 Technical Risks

| Risk | Probability | Impact | Mitigation Strategy | Owner |
|------|-------------|---------|-------------------|-------|
| **WebSocket Performance Issues** | 🟡 Medium | 🔴 High | • Load testing early<br/>• Connection pooling<br/>• Fallback mechanisms | Dev Team |
| **Database Connection Problems** | 🟢 Low | 🔴 High | • Connection retry logic<br/>• Database monitoring<br/>• Backup systems | DBA |
| **Electron App Distribution** | 🟡 Medium | 🟡 Medium | • Test installer early<br/>• Multiple distribution channels<br/>• Auto-update mechanism | DevOps |
| **Real-time Data Sync Issues** | 🟡 Medium | 🟡 Medium | • Message queuing<br/>• Conflict resolution<br/>• Data validation | Dev Team |

### 4.2 Business Risks

| Risk | Probability | Impact | Mitigation Strategy |
|------|-------------|---------|-------------------|
| **User Adoption Resistance** | 🟡 Medium | 🔴 High | • Early user involvement<br/>• Training programs<br/>• Change management |
| **Performance Under Load** | 🟡 Medium | 🟡 Medium | • Stress testing<br/>• Gradual rollout<br/>• Performance monitoring |
| **Data Security Concerns** | 🟢 Low | 🔴 High | • Security audit<br/>• Encryption implementation<br/>• Access controls |

### 4.3 Risk Response Matrix

```
HIGH IMPACT, HIGH PROBABILITY    |  HIGH IMPACT, LOW PROBABILITY
• การ train user อย่างเข้มข้น    |  • เตรียม disaster recovery plan
• Performance testing ทุก sprint |  • Security audit ก่อน go-live
                                |
--------------------------------+--------------------------------
LOW IMPACT, HIGH PROBABILITY     |  LOW IMPACT, LOW PROBABILITY
• Regular backup procedures     |  • Documentation updates
• Minor bug fixes               |  • Future enhancement planning
```

---

## 5. Dependencies & Constraints

### 5.1 Technical Dependencies

#### **External Dependencies**
- ✅ **MSSQL Server**: ต้องมี database server พร้อมใช้งาน
- ✅ **Windows Environment**: Desktop application ต้องรันบน Windows
- ✅ **Network Infrastructure**: ต้องมี network ที่เสถียรสำหรับ WebSocket
- ✅ **SSL Certificates**: สำหรับ HTTPS และ secure WebSocket

#### **Internal Dependencies**
- 🔗 **US-010 → US-011**: Database ต้องพร้อมก่อน API
- 🔗 **US-011 → US-001**: API ต้องพร้อมก่อน dashboard
- 🔗 **US-012 → US-004**: WebSocket ต้องพร้อมก่อน messaging
- 🔗 **US-006 → US-002**: Authentication ต้องมีก่อน status management

### 5.2 Resource Constraints

#### **Team Composition**
- **1 Full-stack Developer**: Frontend + Backend development
- **1 System Administrator**: Database + Infrastructure
- **1 Product Owner**: Requirements + Testing
- **1 Scrum Master**: Project management + Coordination

#### **Time Constraints**
- **Fixed Timeline**: 7 สัปดาห์ (ตาม LAB schedule)
- **Academic Calendar**: ต้องเสร็จก่อนสอบปลายภาค
- **Resource Availability**: นักศึกษามีวิชาอื่นด้วย

#### **Technology Constraints**
- **Existing Infrastructure**: ใช้ technology ที่มีใน LAB
- **Learning Curve**: นักศึกษาต้องเรียนรู้ technology ใหม่
- **Testing Environment**: จำกัดที่ VM และ local machines

### 5.3 Success Criteria & Metrics

#### **Technical Metrics**
- **Performance**: Response time < 500ms, 99% uptime
- **Reliability**: Zero data loss, message delivery > 95%
- **Scalability**: Support 50+ concurrent agents
- **Security**: Pass basic security checks

#### **Business Metrics**
- **User Satisfaction**: Score > 4/5 จาก user feedback
- **Adoption Rate**: 80% agents ใช้งานหลัง 2 สัปดาห์
- **Productivity**: ลด manual monitoring time 50%
- **Training Success**: 90% users ผ่าน training assessment

#### **Project Metrics**
- **Schedule Adherence**: Complete within 7 weeks
- **Budget Compliance**: ไม่เกิน resource ที่จัดสรร
- **Quality**: < 5 critical bugs ใน production
- **Documentation**: Complete technical และ user docs

---

## 6. Implementation Roadmap

### 6.1 Weekly Breakdown

```
Week 1: 🏗️  Database Schema + API Foundation
Week 2: 🔐 Authentication + WebSocket Setup  
Week 3: 📊 Status Management + Basic Dashboard
Week 4: 💬 Communication System + Notifications
Week 5: 📈 Enhanced Dashboard + Configuration
Week 6: 📋 Additional Features + Performance Tuning
Week 7: 📦 Deployment + User Testing
Week 8: 🚀 Pilot Launch + Feedback Collection
```

### 6.2 Critical Path Analysis

**Critical Path**: US-010 → US-011 → US-012 → US-001 → US-008
- **Duration**: 5 สัปดาห์
- **Dependencies**: Sequential development required
- **Buffer**: 2 สัปดาห์สำหรับ testing และ refinement

### 6.3 Quality Assurance Plan

#### **Testing Strategy**
- **Unit Testing**: Each API endpoint และ component
- **Integration Testing**: Full workflow testing
- **Performance Testing**: Load testing with simulated agents  
- **User Acceptance Testing**: Real user scenarios

#### **Quality Gates**
- **Code Review**: ทุก pull request ต้องผ่าน review
- **Automated Testing**: CI/CD pipeline with automated tests
- **Manual Testing**: UAT ก่อน deployment
- **Security Review**: Security checklist ก่อน go-live

---

## 📊 Executive Summary

### **Project Scope**: 14 User Stories, 73 Story Points, 7 Weeks
### **Release Strategy**: Single MVP release with 3 sprints
### **Success Factors**: 
- 🎯 Focus on core functionality first
- 🚀 Early and frequent testing
- 👥 Strong user engagement
- ⚡ Agile adaptation to feedback

### **Key Risks**: WebSocket performance, user adoption
### **Mitigation**: Early testing, user training, gradual rollout

---

*เอกสาร Requirement Analysis นี้ให้กรอบการทำงานที่ชัดเจนสำหรับการพัฒนา Agent Wallboard System ตามแนวทาง Software Engineering ที่เหมาะสมกับ academic project*

## 🎯 ไฮไลท์สำคัญของเอกสาร:

### 📋 **1. Story Mapping**
- **User Journey Flow** ที่ชัดเจนสำหรับ Agent, Supervisor, และ Admin
- **Story Map Visualization** แบ่งตาม Sprint และ User Type
- **Feature Breakdown** ตาม priority และความสำคัญ

### 🎯 **2. Priority Matrix** 
- **MoSCoW Analysis** (Must/Should/Could/Won't Have)
- **Value vs Effort Matrix** เพื่อจัด priority อย่างสมเหตุสมผล
- **Risk vs Impact Assessment** สำหรับการจัดการความเสี่ยง

### 📅 **3. Release Planning**
- **7 สัปดาห์** แบ่งเป็น 3 Sprints
- **Weekly Breakdown** ที่ละเอียดพร้อม deliverables
- **Go-Live Strategy** แบบ Pilot → Rollout → Full Production
- **Success Metrics** ที่วัดได้จริง

### ⚠️ **4. Risk Assessment**
- **Technical Risks**: WebSocket performance, Database connections
- **Business Risks**: User adoption, Performance under load  
- **Mitigation Strategies** ที่เฉพาะเจาะจง

### 🔗 **5. Dependencies & Constraints**
- **Technical Dependencies**: ระบุความสัมพันธ์ระหว่าง User Stories
- **Resource Constraints**: ทีมงาน, เวลา, เทคโนโลยี
- **Success Criteria**: Technical, Business, และ Project metrics

## 🚀 **Key Insights:**

### **Critical Path**: 
US-010 → US-011 → US-012 → US-001 → US-008 (5 สัปดาห์)

### **High-Risk Items**:
- WebSocket performance (กำหนด load testing early)
- User adoption (เน้น training และ change management)

### **Success Factors**:
- ✅ **Focus on Core** (Sprint 1 = Foundation)
- ✅ **Early Testing** (ทุก Sprint มี testing)  
- ✅ **User Engagement** (Feedback loops)
- ✅ **Gradual Rollout** (Pilot → Full deployment)

## 📊 **Executive Dashboard:**
```
📦 Release 1.0 MVP: 7 สัปดาห์
🎯 14 User Stories: 73 Story Points  
👥 4 User Types: Agent/Supervisor/Admin/Manager
🎪 3 Sprints: Foundation → Features → Enhancement
```

# Use Case Analysis - Agent Wallboard System

## 📋 สารบัญ
1. [Use Case Overview](#use-case-overview)
2. [Use Case Diagram](#use-case-diagram)
3. [Detailed Use Cases](#detailed-use-cases)
4. [Use Case to User Story Mapping](#use-case-to-user-story-mapping)

---

## 1. Use Case Overview

### 1.1 Actors (ผู้ใช้งาน)

| Actor | Description | Primary Goals |
|-------|-------------|---------------|
| **🎧 Agent** | พนักงาน Call Center ที่ใช้งาน desktop application | จัดการสถานะตัวเอง, รับข้อความจาก supervisor |
| **👨‍💼 Supervisor** | หัวหน้าทีมที่ดูแล agents | ติดตามสถานะทีม, ส่งข้อความ, ดู dashboard |
| **🏢 Operations Manager** | ผู้จัดการระดับสูงที่ดูภาพรวม | ดูรายงานและสถิติโดยรวม |
| **🔧 System Admin** | ผู้ดูแลระบบ IT | จัดการระบบ, configuration, deployment |

### 1.2 System Scope

```
🎯 Primary System: Agent Wallboard System
📦 Components: Desktop App + Web Dashboard + API Server + Database
🔗 External Systems: MSSQL Database, Windows OS, Network Infrastructure
```

---

## 2. Use Case Diagram

### 2.1 Draw.io XML Code

```xml
<mxfile host="app.diagrams.net" modified="2024-01-01T00:00:00.000Z" agent="5.0" version="22.1.16">
  <diagram name="Use Case Diagram - Agent Wallboard System" id="wallboard-usecase">
    <mxGraphModel dx="1422" dy="794" grid="1" gridSize="10" guides="1" tooltips="1" connect="1" arrows="1" fold="1" page="1" pageScale="1" pageWidth="1169" pageHeight="827" math="0" shadow="0">
      <root>
        <mxCell id="0" />
        <mxCell id="1" parent="0" />
        
        <!-- System Boundary -->
        <mxCell id="system-boundary" value="Agent Wallboard System" style="swimlane;whiteSpace=wrap;html=1;fillColor=#f8cecc;strokeColor=#b85450;fontSize=16;fontStyle=1;startSize=30;" vertex="1" parent="1">
          <mxGeometry x="200" y="80" width="700" height="600" as="geometry" />
        </mxCell>
        
        <!-- Use Cases -->
        <mxCell id="uc-login" value="UC-01&#xa;Login to System" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="50" y="80" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-manage-status" value="UC-02&#xa;Manage Agent Status" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="220" y="80" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-monitor-agents" value="UC-03&#xa;Monitor Agents&#xa;Real-time" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="400" y="80" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-send-message" value="UC-04&#xa;Send Message&#xa;to Agent" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="550" y="80" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-receive-notification" value="UC-05&#xa;Receive&#xa;Notification" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="50" y="200" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-view-dashboard" value="UC-06&#xa;View Team&#xa;Dashboard" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="220" y="200" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-track-attendance" value="UC-07&#xa;Track Agent&#xa;Attendance" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="400" y="200" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-view-reports" value="UC-08&#xa;View Statistical&#xa;Reports" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="550" y="200" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-manage-database" value="UC-09&#xa;Manage Database&#xa;Configuration" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="50" y="320" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-manage-api" value="UC-10&#xa;Manage API&#xa;Endpoints" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="220" y="320" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-manage-websocket" value="UC-11&#xa;Manage WebSocket&#xa;Connections" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="400" y="320" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-deploy-application" value="UC-12&#xa;Deploy Desktop&#xa;Application" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="550" y="320" width="120" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="uc-configure-system" value="UC-13&#xa;Configure System&#xa;Environment" style="ellipse;whiteSpace=wrap;html=1;fillColor=#dae8fc;strokeColor=#6c8ebf;" vertex="1" parent="system-boundary">
          <mxGeometry x="300" y="440" width="120" height="60" as="geometry" />
        </mxCell>
        
        <!-- Actors -->
        <mxCell id="actor-agent" value="Agent" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="80" y="200" width="30" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="actor-supervisor" value="Supervisor" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="80" y="350" width="30" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="actor-manager" value="Operations&#xa;Manager" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="80" y="500" width="30" height="60" as="geometry" />
        </mxCell>
        
        <mxCell id="actor-admin" value="System&#xa;Admin" style="shape=umlActor;verticalLabelPosition=bottom;verticalAlign=top;html=1;fillColor=#fff2cc;strokeColor=#d6b656;" vertex="1" parent="1">
          <mxGeometry x="980" y="400" width="30" height="60" as="geometry" />
        </mxCell>
        
        <!-- Agent Connections -->
        <mxCell id="conn-agent-login" value="" style="endArrow=none;html=1;rounded=0;entryX=0;entryY=0.5;" edge="1" parent="1" source="actor-agent" target="uc-login">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="230" as="sourcePoint" />
            <mxPoint x="250" y="190" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-agent-status" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-agent" target="uc-manage-status">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="230" as="sourcePoint" />
            <mxPoint x="420" y="190" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-agent-notification" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-agent" target="uc-receive-notification">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="230" as="sourcePoint" />
            <mxPoint x="250" y="310" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <!-- Supervisor Connections -->
        <mxCell id="conn-supervisor-login" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-supervisor" target="uc-login">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="380" as="sourcePoint" />
            <mxPoint x="250" y="190" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-supervisor-monitor" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-supervisor" target="uc-monitor-agents">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="380" as="sourcePoint" />
            <mxPoint x="600" y="190" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-supervisor-message" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-supervisor" target="uc-send-message">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="380" as="sourcePoint" />
            <mxPoint x="750" y="190" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-supervisor-dashboard" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-supervisor" target="uc-view-dashboard">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="380" as="sourcePoint" />
            <mxPoint x="420" y="310" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-supervisor-attendance" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-supervisor" target="uc-track-attendance">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="380" as="sourcePoint" />
            <mxPoint x="600" y="310" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <!-- Manager Connections -->
        <mxCell id="conn-manager-dashboard" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-manager" target="uc-view-dashboard">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="530" as="sourcePoint" />
            <mxPoint x="420" y="310" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-manager-reports" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-manager" target="uc-view-reports">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="120" y="530" as="sourcePoint" />
            <mxPoint x="750" y="310" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <!-- Admin Connections -->
        <mxCell id="conn-admin-database" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-admin" target="uc-manage-database">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="980" y="430" as="sourcePoint" />
            <mxPoint x="250" y="430" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-admin-api" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-admin" target="uc-manage-api">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="980" y="430" as="sourcePoint" />
            <mxPoint x="420" y="430" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-admin-websocket" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-admin" target="uc-manage-websocket">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="980" y="430" as="sourcePoint" />
            <mxPoint x="600" y="430" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-admin-deploy" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-admin" target="uc-deploy-application">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="980" y="430" as="sourcePoint" />
            <mxPoint x="750" y="430" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="conn-admin-configure" value="" style="endArrow=none;html=1;rounded=0;" edge="1" parent="1" source="actor-admin" target="uc-configure-system">
          <mxGeometry width="50" height="50" relative="1" as="geometry">
            <mxPoint x="980" y="430" as="sourcePoint" />
            <mxPoint x="500" y="550" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <!-- Include Relationships -->
        <mxCell id="include1" value="&amp;lt;&amp;lt;include&amp;gt;&amp;gt;" style="endArrow=open;endSize=12;dashed=1;html=1;rounded=0;" edge="1" parent="1" source="uc-manage-status" target="uc-login">
          <mxGeometry width="160" relative="1" as="geometry">
            <mxPoint x="400" y="300" as="sourcePoint" />
            <mxPoint x="560" y="300" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="include2" value="&amp;lt;&amp;lt;include&amp;gt;&amp;gt;" style="endArrow=open;endSize=12;dashed=1;html=1;rounded=0;" edge="1" parent="1" source="uc-monitor-agents" target="uc-manage-websocket">
          <mxGeometry width="160" relative="1" as="geometry">
            <mxPoint x="600" y="220" as="sourcePoint" />
            <mxPoint x="500" y="320" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
        <mxCell id="include3" value="&amp;lt;&amp;lt;include&amp;gt;&amp;gt;" style="endArrow=open;endSize=12;dashed=1;html=1;rounded=0;" edge="1" parent="1" source="uc-send-message" target="uc-manage-websocket">
          <mxGeometry width="160" relative="1" as="geometry">
            <mxPoint x="650" y="220" as="sourcePoint" />
            <mxPoint x="520" y="320" as="targetPoint" />
          </mxGeometry>
        </mxCell>
        
      </root>
    </mxGraphModel>
  </diagram>
</mxfile>
```

---

## 3. Detailed Use Cases

### 3.1 Epic 1: Real-time Agent Status Monitoring

#### **UC-01: Login to System**
- **Primary Actor**: Agent, Supervisor
- **Goal**: เข้าสู่ระบบเพื่อใช้งาน application
- **Related User Stories**: US-006

**Main Success Scenario:**
1. ผู้ใช้เปิด desktop application
2. ระบบแสดงหน้า login
3. ผู้ใช้กรอก Agent Code
4. ระบบตรวจสอบ Agent Code กับฐานข้อมูล
5. ระบบสร้าง WebSocket connection
6. ระบบแสดงหน้าหลักพร้อมข้อมูล agent
7. ระบบอัปเดตสถานะเป็น "Connected"

**Extensions:**
- 4a. Agent Code ไม่ถูกต้อง:
  - 4a1. ระบบแสดงข้อความ "Agent not found"
  - 4a2. กลับไปขั้นตอนที่ 3
- 5a. WebSocket connection ล้มเหลว:
  - 5a1. ระบบแสดงข้อความเตือน
  - 5a2. พยายามเชื่อมต่อใหม่

**Preconditions**: 
- Agent มี valid Agent Code ในระบบ
- Network connection พร้อมใช้งาน

**Postconditions**:
- Agent อยู่ในสถานะ "Connected"
- WebSocket connection สร้างสำเร็จ

---

#### **UC-02: Manage Agent Status**
- **Primary Actor**: Agent
- **Goal**: เปลี่ยนสถานะการทำงานของตัวเอง
- **Related User Stories**: US-002

**Main Success Scenario:**
1. Agent เลือกสถานะใหม่จาก dropdown (Available, Active, Wrap, Not Ready)
2. ระบบส่งคำขอเปลี่ยนสถานะไปยัง API server
3. API server อัปเดตสถานะในฐานข้อมูล
4. API server ส่งข้อมูลอัปเดตผ่าน WebSocket
5. ระบบอัปเดต UI ของ agent
6. Supervisor dashboard อัปเดตสถานะแบบ real-time

**Extensions:**
- 2a. Network error:
  - 2a1. ระบบแสดงข้อความ "Failed to update status"
  - 2a2. เก็บ status ไว้ใน local cache
  - 2a3. retry เมื่อ connection กลับมา

**Preconditions**: 
- Agent ต้อง login แล้ว
- WebSocket connection active

**Postconditions**:
- Status ในฐานข้อมูลอัปเดต
- All connected supervisors เห็นสถานะใหม่

---

#### **UC-03: Monitor Agents Real-time**
- **Primary Actor**: Supervisor
- **Goal**: ติดตามสถานะของ agents ในทีมแบบ real-time
- **Related User Stories**: US-001, US-008

**Main Success Scenario:**
1. Supervisor เข้าสู่หน้า dashboard
2. ระบบดึงรายการ agents ทั้งหมดจาก API
3. ระบบแสดงรายการ agents พร้อมสถานะปัจจุบัน
4. ระบบแสดงสถิติโดยรวม (Available, Active, Wrap, Not Ready)
5. ระบบรับการอัปเดตผ่าน WebSocket
6. ระบบอัปเดต display แบบ real-time

**Alternative Flows:**
- 2a. API ไม่ตอบสนอง:
  - 2a1. ระบบแสดง cached data
  - 2a2. แสดงสถานะ "Data may not be current"

**Preconditions**: 
- Supervisor login แล้ว
- มี agents ในระบบ

**Postconditions**:
- Dashboard แสดงข้อมูล real-time
- สถิติอัปเดตตามสถานะ agents

---

### 3.2 Epic 2: Supervisor Communication System

#### **UC-04: Send Message to Agent**
- **Primary Actor**: Supervisor
- **Goal**: ส่งข้อความไปยัง agent ที่เฉพาะเจาะจง
- **Related User Stories**: US-004

**Main Success Scenario:**
1. Supervisor เลือก agent จากรายการ
2. Supervisor พิมพ์ข้อความในช่อง message
3. Supervisor กดปุ่ม "Send"
4. ระบบส่งข้อความผ่าน API
5. API server forward ข้อความผ่าน WebSocket ไปยัง agent
6. ระบบแสดงสถานะ "Message sent"
7. Agent ได้รับ notification

**Extensions:**
- 5a. Agent ไม่ online:
  - 5a1. ระบบแสดงข้อความ "Agent not available"
  - 5a2. เก็บข้อความไว้ใน queue (future enhancement)

**Preconditions**: 
- Supervisor login แล้ว
- Target agent ต้อง online

**Postconditions**:
- ข้อความส่งถึง agent สำเร็จ
- มี log การส่งข้อความ

---

#### **UC-05: Receive Notification**
- **Primary Actor**: Agent
- **Goal**: รับและแสดงการแจ้งเตือนจาก supervisor
- **Related User Stories**: US-005

**Main Success Scenario:**
1. Agent ได้รับข้อความผ่าน WebSocket
2. ระบบแสดง desktop notification
3. ระบบเล่นเสียงแจ้งเตือน
4. ระบบแสดง popup พร้อมข้อความ
5. Agent อ่านข้อความ
6. Agent กดปุ่ม "Close"
7. ระบบปิด notification

**Extensions:**
- 2a. Desktop notification ถูก disable:
  - 2a1. แสดงเฉพาะ popup ใน application

**Preconditions**: 
- Agent login และ online
- มี supervisor ส่งข้อความมา

**Postconditions**:
- Agent รับทราบข้อความแล้ว
- Notification history อัปเดต

---

### 3.3 Epic 3: Agent Self-Service Portal

#### **UC-06: View Team Dashboard**
- **Primary Actor**: Supervisor, Operations Manager
- **Goal**: ดูภาพรวมของทีมและสถิติต่างๆ
- **Related User Stories**: US-008, US-009

**Main Success Scenario:**
1. ผู้ใช้เข้าสู่หน้า dashboard
2. ระบบแสดงสถิติทีม (จำนวน agents แต่ละสถานะ)
3. ระบบแสดง charts และ graphs
4. ระบบแสดงเวลาปัจจุบันและ team summary
5. ระบบอัปเดตข้อมูลแบบ real-time
6. ผู้ใช้สามารถ drill-down ดูรายละเอียดได้

**Alternative Flows:**
- 2a. ไม่มีข้อมูล:
  - 2a1. แสดงค่าเริ่มต้น (0 for all metrics)

**Preconditions**: 
- ผู้ใช้ login แล้ว
- มีสิทธิ์เข้าถึง dashboard

**Postconditions**:
- Dashboard แสดงข้อมูลล่าสุด
- ข้อมูลอัปเดตแบบ real-time

---

### 3.4 Epic 4: Management Dashboard & Reporting

#### **UC-07: Track Agent Attendance**
- **Primary Actor**: Supervisor
- **Goal**: ติดตามการเข้า-ออกงานของ agents
- **Related User Stories**: US-003

**Main Success Scenario:**
1. ระบบบันทึก login time เมื่อ agent เข้าระบบ
2. ระบบบันทึก logout time เมื่อ agent ออกจากระบบ
3. Supervisor เข้าดู attendance report
4. ระบบแสดงรายการ agents พร้อม login/logout times
5. ระบบคำนวณชั่วโมงการทำงาน
6. ระบบแสดงสถิติการเข้างาน

**Extensions:**
- 2a. Agent ปิด application กะทันหัน:
  - 2a1. ระบบตรวจจับ connection lost
  - 2a2. บันทึก logout time เป็นเวลาที่ connection หลุด

**Preconditions**: 
- มีข้อมูล login/logout ของ agents
- Supervisor มีสิทธิ์ดู attendance

**Postconditions**:
- มีรายงานการเข้างานที่ถูกต้อง
- สถิติการทำงานอัปเดต

---

#### **UC-08: View Statistical Reports**
- **Primary Actor**: Operations Manager
- **Goal**: ดูรายงานสถิติเพื่อการตัดสินใจ
- **Related User Stories**: US-009

**Main Success Scenario:**
1. Manager เข้าสู่ reports section
2. Manager เลือกประเภทรายงาน (daily, weekly, monthly)
3. ระบบดึงข้อมูลจากฐานข้อมูล
4. ระบบประมวลผลและสร้าง charts
5. ระบบแสดงรายงานในรูปแบบ graphs และ tables
6. Manager สามารถ export รายงานได้

**Alternative Flows:**
- 3a. ไม่มีข้อมูลในช่วงเวลาที่เลือก:
  - 3a1. แสดงข้อความ "No data available for selected period"

**Preconditions**: 
- Manager login แล้ว
- มีข้อมูลประวัติการทำงานในระบบ

**Postconditions**:
- รายงานแสดงข้อมูลที่ถูกต้องและทันสมัย
- Manager ได้ข้อมูลสำหรับตัดสินใจ

---

### 3.5 Epic 5: System Administration & Configuration

#### **UC-09: Manage Database Configuration**
- **Primary Actor**: System Admin
- **Goal**: จัดการและกำหนดค่าฐานข้อมูล
- **Related User Stories**: US-010

**Main Success Scenario:**
1. Admin เข้าสู่ database management interface
2. Admin ตรวจสอบ database connection status
3. Admin กำหนดค่า connection parameters
4. ระบบทดสอบ database connection
5. ระบบบันทึก configuration
6. ระบบ restart database connections
7. ระบบยืนยันการตั้งค่าสำเร็จ

**Extensions:**
- 4a. Database connection ล้มเหลว:
  - 4a1. ระบบแสดง error message พร้อมรายละเอียด
  - 4a2. กลับไปขั้นตอนที่ 3 เพื่อแก้ไข parameters
- 6a. Restart ล้มเหลว:
  - 6a1. ระบบ rollback configuration เดิม
  - 6a2. แจ้งเตือน admin

**Preconditions**: 
- Admin มีสิทธิ์ระดับ administrator
- Database server พร้อมใช้งาน

**Postconditions**:
- Database configuration อัปเดต
- Application สามารถเชื่อมต่อฐานข้อมูลได้

---

#### **UC-10: Manage API Endpoints**
- **Primary Actor**: System Admin
- **Goal**: จัดการ API endpoints และ security
- **Related User Stories**: US-011

**Main Success Scenario:**
1. Admin เข้าสู่ API management console
2. Admin ตรวจสอบสถานะ API endpoints
3. Admin กำหนดค่า authentication tokens
4. Admin ทดสอบ API endpoints
5. ระบบแสดงผล response times และ availability
6. Admin กำหนดค่า rate limiting (ถ้าจำเป็น)
7. ระบบบันทึก configuration changes

**Extensions:**
- 4a. API endpoint ไม่ตอบสนอง:
  - 4a1. ระบบแสดง error details
  - 4a2. Admin ตรวจสอบ server status
  - 4a3. Restart API service หากจำเป็น
- 5a. Performance ต่ำกว่ามาตรฐาน:
  - 5a1. ระบบแจ้งเตือนและแนะนำการแก้ไข

**Preconditions**: 
- API server running
- Admin มี access credentials

**Postconditions**:
- API endpoints ทำงานปกติ
- Security configuration อัปเดต

---

#### **UC-11: Manage WebSocket Connections**
- **Primary Actor**: System Admin
- **Goal**: จัดการ WebSocket connections และ real-time communications
- **Related User Stories**: US-012

**Main Success Scenario:**
1. Admin เข้าสู่ WebSocket management dashboard
2. ระบบแสดงรายการ active connections
3. Admin ตรวจสอบ connection health
4. Admin ดู message throughput statistics
5. Admin จัดการ connection pools
6. ระบบแสดงข้อมูล performance metrics
7. Admin กำหนดค่า timeout และ retry parameters

**Extensions:**
- 3a. มี connections ที่ไม่ตอบสนอง:
  - 3a1. Admin เลือก terminate connection
  - 3a2. ระบบ cleanup resources
  - 3a3. แจ้งเตือน affected users
- 4a. Message throughput สูงผิดปกติ:
  - 4a1. ระบบแสดงการเตือน
  - 4a2. Admin สามารถ throttle connections ได้

**Preconditions**: 
- WebSocket server running
- มี active connections ในระบบ

**Postconditions**:
- WebSocket connections มีประสิทธิภาพดี
- Real-time communication เสถียร

---

#### **UC-12: Deploy Desktop Application**
- **Primary Actor**: System Admin
- **Goal**: สร้างและแจกจ่าย desktop application
- **Related User Stories**: US-013

**Main Success Scenario:**
1. Admin เตรียม source code สำหรับ build
2. Admin รัน build script สำหรับ Electron application
3. ระบบสร้าง executable files
4. Admin ทดสอบ application บน test machine
5. Admin สร้าง installer package
6. Admin ทดสอบ installation process
7. Admin อัปโหลด installer ไป distribution server
8. Admin แจ้งเตือน users เรื่อง update ใหม่

**Extensions:**
- 2a. Build ล้มเหลว:
  - 2a1. ระบบแสดง build errors
  - 2a2. Admin แก้ไข source code
  - 2a3. กลับไปขั้นตอนที่ 2
- 4a. Application ไม่สามารถรันได้:
  - 4a1. Admin ตรวจสอบ dependencies
  - 4a2. แก้ไขปัญหาและ rebuild

**Preconditions**: 
- Source code พร้อมและผ่าน testing
- Build environment ตั้งค่าเรียบร้อย

**Postconditions**:
- Desktop application พร้อม deploy
- Users สามารถ download และติดตั้งได้

---

#### **UC-13: Configure System Environment**
- **Primary Actor**: System Admin
- **Goal**: กำหนดค่าระบบสำหรับ environments ต่างๆ
- **Related User Stories**: US-014

**Main Success Scenario:**
1. Admin เข้าสู่ configuration management interface
2. Admin เลือก environment (development/production)
3. Admin กำหนดค่า database connection strings
4. Admin กำหนดค่า API URLs และ endpoints
5. Admin กำหนดค่า WebSocket server addresses
6. Admin กำหนดค่า SSL certificates
7. ระบบ validate configuration
8. ระบบบันทึกและ apply configuration

**Extensions:**
- 7a. Configuration validation ล้มเหลว:
  - 7a1. ระบบแสดง validation errors
  - 7a2. Admin แก้ไข configuration
  - 7a3. กลับไปขั้นตอนที่ 7
- 8a. Apply configuration ล้มเหลว:
  - 8a1. ระบบ rollback ไปยัง configuration เดิม
  - 8a2. แจ้งเตือน admin

**Preconditions**: 
- Admin มีสิทธิ์เปลี่ยน configuration
- Target environment พร้อมใช้งาน

**Postconditions**:
- System configuration อัปเดตตาม environment
- Application ทำงานด้วย configuration ใหม่

---

## 4. Use Case to User Story Mapping

### 4.1 Complete Mapping Table

| Use Case ID | Use Case Name | Related User Stories | Epic | Priority | Sprint |
|-------------|---------------|---------------------|------|----------|--------|
| **UC-01** | Login to System | US-006 (Agent Authentication) | Epic 3 | HIGH | Sprint 1 |
| **UC-02** | Manage Agent Status | US-002 (Status Updates) | Epic 1 | HIGH | Sprint 1 |
| **UC-03** | Monitor Agents Real-time | US-001 (Status Display)<br/>US-008 (Dashboard) | Epic 1, 4 | HIGH | Sprint 1, 2 |
| **UC-04** | Send Message to Agent | US-004 (Send Message) | Epic 2 | HIGH | Sprint 2 |
| **UC-05** | Receive Notification | US-005 (Receive Notification) | Epic 2 | HIGH | Sprint 2 |
| **UC-06** | View Team Dashboard | US-008 (Dashboard)<br/>US-007 (Agent Profile) | Epic 4, 3 | HIGH | Sprint 2 |
| **UC-07** | Track Agent Attendance | US-003 (Login Tracking) | Epic 1 | MEDIUM | Sprint 3 |
| **UC-08** | View Statistical Reports | US-009 (Real-time Stats) | Epic 4 | MEDIUM | Sprint 3 |
| **UC-09** | Manage Database Configuration | US-010 (Database Management) | Epic 5 | HIGH | Sprint 1 |
| **UC-10** | Manage API Endpoints | US-011 (API Management) | Epic 5 | HIGH | Sprint 1 |
| **UC-11** | Manage WebSocket Connections | US-012 (WebSocket Management) | Epic 5 | HIGH | Sprint 1 |
| **UC-12** | Deploy Desktop Application | US-013 (App Distribution) | Epic 5 | MEDIUM | Sprint 3 |
| **UC-13** | Configure System Environment | US-014 (Configuration) | Epic 5 | MEDIUM | Sprint 2 |

### 4.2 Epic to Use Case Distribution

#### **📊 Epic 1: Real-time Agent Status Monitoring (3 Use Cases)**
- UC-02: Manage Agent Status *(Core functionality)*
- UC-03: Monitor Agents Real-time *(Supervisor view)*  
- UC-07: Track Agent Attendance *(Historical data)*

#### **💬 Epic 2: Supervisor Communication System (2 Use Cases)**
- UC-04: Send Message to Agent *(Outbound communication)*
- UC-05: Receive Notification *(Inbound communication)*

#### **🎧 Epic 3: Agent Self-Service Portal (2 Use Cases)**
- UC-01: Login to System *(Authentication)*
- UC-06: View Team Dashboard *(Shared with Epic 4)*

#### **📈 Epic 4: Management Dashboard & Reporting (2 Use Cases)**
- UC-06: View Team Dashboard *(Shared with Epic 3)*
- UC-08: View Statistical Reports *(Advanced reporting)*

#### **⚙️ Epic 5: System Administration & Configuration (5 Use Cases)**
- UC-09: Manage Database Configuration *(Data tier)*
- UC-10: Manage API Endpoints *(Application tier)*
- UC-11: Manage WebSocket Connections *(Communication layer)*
- UC-12: Deploy Desktop Application *(Presentation tier)*
- UC-13: Configure System Environment *(Environment management)*

### 4.3 Actor to Use Case Matrix

| Actor | Primary Use Cases | Secondary Use Cases | Total |
|-------|------------------|-------------------|-------|
| **🎧 Agent** | UC-01, UC-02, UC-05 | - | 3 |
| **👨‍💼 Supervisor** | UC-03, UC-04, UC-06, UC-07 | UC-01 | 5 |
| **🏢 Operations Manager** | UC-06, UC-08 | - | 2 |
| **🔧 System Admin** | UC-09, UC-10, UC-11, UC-12, UC-13 | - | 5 |

### 4.4 Dependencies Between Use Cases

#### **Critical Path Dependencies**
```
UC-09 (Database) → UC-10 (API) → UC-11 (WebSocket) → UC-01 (Login) → UC-02 (Status)
                                                    ↓
                                                  UC-03 (Monitor)
                                                    ↓
                                                  UC-04 (Message) → UC-05 (Notification)
```

#### **Include Relationships**
- **UC-02** includes **UC-01** (ต้อง login ก่อนเปลี่ยนสถานะ)
- **UC-03** includes **UC-11** (ต้องมี WebSocket เพื่อ monitor real-time)
- **UC-04** includes **UC-11** (ต้องมี WebSocket เพื่อส่งข้อความ)

#### **Extend Relationships**
- **UC-07** extends **UC-01** (เพิ่ม attendance tracking เมื่อ login)
- **UC-08** extends **UC-06** (เพิ่ม advanced reports บน dashboard)

---

## 5. Implementation Guidelines

### 5.1 Use Case Implementation Priority

#### **🔴 Critical (Sprint 1)**
1. **UC-09, UC-10, UC-11**: Infrastructure foundation
2. **UC-01**: User authentication  
3. **UC-02, UC-03**: Core monitoring functionality

#### **🟡 Important (Sprint 2)**
4. **UC-04, UC-05**: Communication features
5. **UC-06**: Dashboard and reporting
6. **UC-13**: Environment configuration

#### **🟢 Enhancement (Sprint 3)**
7. **UC-07**: Attendance tracking
8. **UC-08**: Advanced reporting  
9. **UC-12**: Application distribution

### 5.2 Testing Strategy per Use Case

#### **Unit Testing Focus**
- **UC-01**: Authentication logic, validation
- **UC-02**: Status change logic, data validation
- **UC-04, UC-05**: Message routing, WebSocket handling

#### **Integration Testing Focus**
- **UC-03**: Real-time data flow end-to-end
- **UC-06**: Dashboard data aggregation
- **UC-11**: WebSocket connection management

#### **User Acceptance Testing Focus**
- **UC-02, UC-03**: Agent and Supervisor workflows
- **UC-04, UC-05**: Communication scenarios
- **UC-06, UC-08**: Dashboard and reporting usability

### 5.3 Documentation Requirements

#### **Technical Documentation**
- API specifications for UC-10
- Database schema for UC-09  
- WebSocket protocol for UC-11
- Deployment guide for UC-12

#### **User Documentation** 
- Agent user guide for UC-01, UC-02, UC-05
- Supervisor manual for UC-03, UC-04, UC-06, UC-07
- Administrator handbook for UC-09 through UC-13

---

## 6. Quality Assurance & Validation

### 6.1 Use Case Validation Criteria

| Use Case | Success Metrics | Performance Criteria | Security Requirements |
|----------|-----------------|---------------------|---------------------|
| **UC-01** | Login success rate > 95% | Authentication < 2s | Secure credential handling |
| **UC-02** | Status update success > 99% | Update propagation < 1s | User authorization check |
| **UC-03** | Data freshness < 5s | Dashboard load < 3s | Role-based access |
| **UC-04** | Message delivery > 98% | End-to-end latency < 2s | Message encryption |
| **UC-05** | Notification display 100% | Alert delay < 1s | User privacy protection |

### 6.2 Risk Mitigation per Use Case

#### **High-Risk Use Cases**
- **UC-11 (WebSocket)**: Connection stability, scalability
- **UC-10 (API)**: Security vulnerabilities, performance
- **UC-03 (Real-time)**: Data synchronization, browser compatibility

#### **Medium-Risk Use Cases**  
- **UC-04, UC-05**: Message delivery reliability
- **UC-09**: Database performance and backup
- **UC-12**: Cross-platform compatibility

---

## 📊 Summary

### **Total Use Cases**: 13
### **Total User Stories Covered**: 14 (100% coverage)
### **Primary Actors**: 4 (Agent, Supervisor, Manager, Admin)
### **Implementation Sprints**: 3 (spanning 7 weeks)

### **Key Success Factors**:
- ✅ **Complete traceability** between Use Cases และ User Stories
- ✅ **Clear actor responsibilities** และ system boundaries  
- ✅ **Detailed scenarios** สำหรับ development และ testing
- ✅ **Risk-based prioritization** สำหรับ implementation planning

---

*Use Case Analysis นี้ให้รายละเอียดที่ครบถ้วนสำหรับการ implement Agent Wallboard System ตาม Software Engineering principles และสอดคล้องกับ LAB requirements ที่กำหนดไว้*

# เอกสารกำหนดความต้องการซอฟต์แวร์ (SRS)
## Agent Wallboard System

**เวอร์ชัน**: 1.0  
**วันที่**: มกราคม 2025  
**มาตรฐาน**: IEEE Std 830-1998  
**ผู้จัดทำ**: ทีมพัฒนา ENGSE206  

---

## สารบัญ

1. [บทนำ (Introduction)](#1-บทนำ-introduction)
2. [คำอธิบายโดยรวม (Overall Description)](#2-คำอธิบายโดยรวม-overall-description)
3. [ความต้องการเฉพาะ (Specific Requirements)](#3-ความต้องการเฉพาะ-specific-requirements)
4. [ภาคผนวก (Appendices)](#4-ภาคผนวก-appendices)

---

## 1. บทนำ (Introduction)

### 1.1 วัตถุประสงค์ (Purpose)

เอกสารกำหนดความต้องการซอฟต์แวร์ (SRS) นี้อธิบายความต้องการเชิงหน้าที่ (Functional Requirements) และความต้องการเชิงคุณภาพ (Non-functional Requirements) ของระบบ Agent Wallboard System เอกสารนี้จัดทำสำหรับ:

- **ทีมพัฒนา (Development Team)**: วิศวกรซอฟต์แวร์ที่ทำการ implement ระบบ
- **ทีมทดสอบ (Testing Team)**: วิศวกร Quality Assurance ที่ทำการตรวจสอบระบบ
- **ผู้มีส่วนได้ส่วนเสียในโครงการ (Project Stakeholders)**: Supervisors, Managers และ Administrators ที่จะใช้งานระบบ
- **การประเมินผลทางวิชาการ (Academic Review)**: อาจารย์ผู้สอนและเพื่อนร่วมชั้นในการประเมินโครงการวิชา ENGSE206

ระบบให้ความสามารถในการติดตาม real-time และการสื่อสารสำหรับการดำเนินงาน call center โดยใช้การ implement แบบ 3-tier architecture

### 1.2 ขอบเขต (Scope)

**ชื่อผลิตภัณฑ์**: Agent Wallboard System  
**ขอบเขตผลิตภัณฑ์**: ระบบติดตามและสื่อสาร call center agents แบบ real-time

**หน้าที่หลัก (Primary Functions)**:
- ✅ **การติดตาม Agent Status แบบ Real-time**: ติดตามสถานะความพร้อมและการทำงานของ agent
- ✅ **การสื่อสารสองทิศทาง (Bidirectional Communication)**: ให้ supervisor สามารถส่งข้อความถึง agent ได้
- ✅ **Dashboard และ Reporting**: แสดงข้อมูลเชิงลึกและสถิติการดำเนินงาน
- ✅ **การบริหารระบบ (System Administration)**: จัดการ configuration และ deployment ของระบบ

**ประโยชน์หลัก (Major Benefits)**:
- เพิ่มประสิทธิภาพการดำเนินงาน 25% ผ่านการติดตาม real-time
- ลดความพยายามในการควบคุมดูแลแบบ manual 60%
- เพิ่มความเร็วในการสื่อสารระหว่าง supervisors และ agents
- ให้ข้อมูลสำหรับการตัดสินใจที่อิงข้อมูล (data-driven decision making)

**สิ่งที่ไม่อยู่ในขอบเขต (Out of Scope)**:
- การรวม (Integration) กับระบบ telephony หรือ PBX
- การจัดการ customer data หรือ call recording
- Mobile application สำหรับ smartphone
- Advanced analytics หรือ machine learning features

### 1.3 คำจำกัดความ, คำย่อ และข้อตกลง (Definitions, Acronyms, and Abbreviations)

**คำจำกัดความ (Definitions)**:

| คำศัพท์ | ความหมาย |
|---------|-----------|
| **Agent** | พนักงาน call center ที่ใช้งาน desktop application |
| **Supervisor** | หัวหน้าทีมที่ดูแลและติดตาม agents |
| **Operations Manager** | ผู้จัดการระดับสูงที่ดูภาพรวมการดำเนินงาน |
| **System Admin** | ผู้ดูแลระบบ IT และการ configuration |
| **Wallboard** | หน้าจอแสดงสถานะของ agents แบบ real-time |
| **Real-time** | การอัปเดตข้อมูลที่มีความหน่วงเวลาไม่เกิน 5 วินาที |

**คำย่อ (Acronyms)**:

| คำย่อ | ความหมาย |
|--------|-----------|
| **SRS** | Software Requirements Specification |
| **API** | Application Programming Interface |
| **UI/UX** | User Interface/User Experience |
| **MSSQL** | Microsoft SQL Server |
| **HTTP/HTTPS** | Hypertext Transfer Protocol (Secure) |
| **WebSocket** | Protocol สำหรับการสื่อสาร real-time |
| **JSON** | JavaScript Object Notation |
| **SSL/TLS** | Secure Sockets Layer/Transport Layer Security |
| **JWT** | JSON Web Token |
| **REST** | Representational State Transfer |

### 1.4 การอ้างอิง (References)

**มาตรฐานและเอกสารอ้างอิง**:
- IEEE Std 830-1998 - IEEE Recommended Practice for Software Requirements Specifications
- RFC 6455 - The WebSocket Protocol  
- RFC 7519 - JSON Web Token (JWT)
- ENGSE206 Course Materials - Software Requirements and Design

**เอกสารที่เกี่ยวข้อง**:
- Overall Context Analysis - Agent Wallboard System
- User Stories และ Requirements Analysis
- Use Case Analysis พร้อม Use Case Diagram

### 1.5 ภาพรวม (Overview)

เอกสาร SRS นี้จัดองค์ประกอบตามมาตรฐาน IEEE 830 ดังนี้:

**Section 2 (คำอธิบายโดยรวม)**: อธิบายบริบท, หน้าที่หลัก, ลักษณะผู้ใช้งาน, ข้อจำกัด และสมมติฐานของระบบ

**Section 3 (ความต้องการเฉพาะ)**: รายละเอียดความต้องการเชิงหน้าที่ (Functional Requirements) และความต้องการเชิงคุณภาพ (Non-functional Requirements) พร้อม traceability mapping

**Section 4 (ภาคผนวก)**: ข้อมูลเสริมรวมถึง glossary และรายละเอียดเทคนิค

---

## 2. คำอธิบายโดยรวม (Overall Description)

### 2.1 มุมมองผลิตภัณฑ์ (Product Perspective)

#### 2.1.1 System Context

Agent Wallboard System เป็น standalone system ที่ออกแบบด้วย **3-Tier Architecture**:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  Presentation   │    │   Application   │    │      Data       │
│      Tier       │◄──►│      Tier       │◄──►│      Tier       │
│                 │    │                 │    │                 │
│ Desktop App     │    │ Node.js API     │    │ MSSQL Database  │
│ (Electron.js)   │    │ WebSocket       │    │ MongoDB         │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

#### 2.1.2 System Interfaces

**External System Interfaces**:
- **Database Systems**: MSSQL Server สำหรับ transactional data, MongoDB สำหรับ real-time data
- **Operating System**: Windows 10/11 สำหรับ desktop application
- **Network Infrastructure**: TCP/IP network สำหรับ HTTP/HTTPS และ WebSocket communications

**User Interfaces**:
- **Desktop Application**: Electron.js-based application สำหรับ agents
- **Web Dashboard**: Browser-based interface สำหรับ supervisors และ managers

**Hardware Interfaces**:
- **Client Workstations**: Windows PCs ที่มี minimum 4GB RAM, dual-core processor
- **Server Hardware**: Application server และ database server ตามความต้องการใน production

**Software Interfaces**:
- **Node.js Runtime**: Version 18 หรือสูงกว่า
- **Database Drivers**: MSSQL driver, MongoDB driver
- **Web Browser**: Chrome 90+, Firefox 88+, Edge 90+

**Communication Interfaces**:
- **REST API**: HTTP/HTTPS protocols สำหรับ client-server communication
- **WebSocket**: Real-time bidirectional communication
- **SSL/TLS**: Secure communication channels

### 2.2 หน้าที่ของผลิตภัณฑ์ (Product Functions)

ระบบ Agent Wallboard System มีหน้าที่หลัก 5 กลุ่ม ตาม Epic structure:

#### **2.2.1 Epic 1: Real-time Agent Status Monitoring**
- 📊 **แสดงสถานะ Agent**: แสดงสถานะ Available, Active, Wrap, Not Ready, Offline แบบ real-time
- 🔄 **อัปเดตสถานะ**: Agent สามารถเปลี่ยนสถานะผ่าน desktop application
- 📝 **ติดตาม Login/Logout**: บันทึกเวลาเข้า-ออกงานของ agents

#### **2.2.2 Epic 2: Supervisor Communication System**  
- 💬 **ส่งข้อความ**: Supervisor ส่งข้อความไปยัง agent ที่เฉพาะเจาะจง
- 🔔 **การแจ้งเตือน**: Agent รับ desktop notification และ popup messages

#### **2.2.3 Epic 3: Agent Self-Service Portal**
- 🔐 **การยืนยันตัวตน**: Agent login ด้วย Agent Code
- 👤 **ข้อมูลส่วนตัว**: แสดงข้อมูลและสถานะปัจจุบันของ agent

#### **2.2.4 Epic 4: Management Dashboard & Reporting**
- 📈 **Dashboard**: แสดงสถิติทีมและ real-time metrics
- 📊 **รายงาน**: สถิติการทำงานและ attendance reports

#### **2.2.5 Epic 5: System Administration & Configuration**
- 🛠️ **จัดการฐานข้อมูล**: Database configuration และ connection management
- ⚙️ **API Management**: จัดการ endpoints และ security
- 🔗 **WebSocket Management**: จัดการ real-time connections
- 📦 **Deployment**: สร้างและแจกจ่าย desktop application

### 2.3 ลักษณะผู้ใช้งาน (User Characteristics)

#### **2.3.1 Agent (Primary User)**
- **จำนวน**: 50-500 คนต่อองค์กร
- **ความเชี่ยวชาญด้านเทคโนโลยี**: พื้นฐานถึงปานกลาง
- **ความถี่การใช้งาน**: ใช้งานต่อเนื่อง 8 ชั่วโมงต่อวัน
- **วัตถุประสงค์หลัก**: จัดการสถานะงาน, รับข้อมูลจาก supervisor
- **การฝึกอบรม**: ต้องการการฝึกอบรม 1-2 ชั่วโมง

#### **2.3.2 Supervisor (Power User)**
- **จำนวน**: 5-50 คนต่อองค์กร
- **ความเชี่ยวชาญด้านเทคโนโลยี**: ปานกลางถึงสูง
- **ความถี่การใช้งาน**: ใช้งานสม่ำเสมอตลอดวัน
- **วัตถุประสงค์หลัก**: ติดตามทีม, ส่งข้อความ, ดูรายงาน
- **การฝึกอบรม**: ต้องการการฝึกอบรม 2-4 ชั่วโมง

#### **2.3.3 Operations Manager (Executive User)**
- **จำนวน**: 1-10 คนต่อองค์กร  
- **ความเชี่ยวชาญด้านเทคโนโลยี**: ปานกลาง
- **ความถี่การใช้งาน**: ใช้งานเป็นระยะเพื่อดูรายงาน
- **วัตถุประสงค์หลัก**: ดูสถิติโดยรวม, วิเคราะห์ performance
- **การฝึกอบรม**: ต้องการการฝึกอบรม 1 ชั่วโมง

#### **2.3.4 System Administrator (Technical User)**
- **จำนวน**: 1-5 คนต่อองค์กร
- **ความเชี่ยวชาญด้านเทคโนโลยี**: สูง
- **ความถี่การใช้งาน**: ใช้งานเมื่อต้องการบำรุงรักษาและ configuration
- **วัตถุประสงค์หลัก**: จัดการระบบ, deployment, troubleshooting  
- **การฝึกอบรม**: ต้องการเอกสารเทคนิคและการฝึกอบรม 4-8 ชั่วโมง

### 2.4 ข้อจำกัด (Constraints)

#### **2.4.1 Regulatory Constraints**
- ไม่มีข้อจำกัดด้าน regulatory เนื่องจากเป็น internal system
- ต้องปฏิบัติตามนโยบาย IT security ของบริษัท

#### **2.4.2 Hardware Limitations**  
- **Client Requirements**: Windows 10/11, minimum 4GB RAM, 1GB disk space
- **Server Requirements**: ต้องมี dedicated server สำหรับ production deployment
- **Network Requirements**: Stable internet connection สำหรับ real-time features

#### **2.4.3 Technology Constraints**
- **Programming Language**: JavaScript (Node.js) สำหรับ backend
- **Database**: MSSQL และ MongoDB เท่านั้น
- **Desktop Platform**: Windows only (Electron.js limitation ตาม LAB requirements)
- **Browser Support**: Modern browsers ที่รองรับ WebSocket

#### **2.4.4 Academic/Project Constraints**
- **Timeline**: ต้องพัฒนาให้เสร็จใน 7 สัปดาห์ ตาม academic schedule
- **Team Size**: Limited team members (3-4 คน)
- **Budget**: ไม่มี budget สำหรับ commercial software licenses
- **Learning Curve**: ทีมต้องเรียนรู้ technology ขณะพัฒนา

### 2.5 สมมติฐานและการพึ่งพิง (Assumptions and Dependencies)

#### **2.5.1 Assumptions**
- **Network Stability**: สมมติว่า network connection มีความเสถียรสำหรับ real-time features
- **User Training**: สมมติว่าผู้ใช้งานจะได้รับการฝึกอบรมก่อนใช้งานจริง  
- **Data Volume**: สมมติว่าจะมี agents ไม่เกิน 100 คนใน initial deployment
- **Operating Hours**: ระบบจะใช้งานในเวลาทำการปกติ (8AM-6PM)

#### **2.5.2 Dependencies**
- **External Dependencies**:
  - Windows Operating System availability
  - MSSQL Server instance พร้อมใช้งาน  
  - Network infrastructure พร้อมรองรับ WebSocket
  - SSL certificates สำหรับ secure communication

- **Internal Dependencies**:
  - Database schema ต้องสร้างก่อน API development
  - API endpoints ต้องพร้อมก่อน frontend development
  - WebSocket server ต้องเสถียรก่อน real-time features
  - Authentication system ต้องทำงานก่อน user-specific features

#### **2.5.3 Risk Mitigation**
- **Performance Risk**: จะมี performance testing ก่อน production deployment
- **Security Risk**: จะมี security review และ testing
- **Scalability Risk**: จะออกแบบให้รองรับการขยายใน future versions
- **User Adoption Risk**: จะมี user training และ change management plan

---

## 3. ความต้องการเฉพาะ (Specific Requirements)

### 3.1 ความต้องการเชิงหน้าที่ (Functional Requirements)

#### **3.1.1 Epic 1: Real-time Agent Status Monitoring**

##### **FR-001: Agent Status Display**
- **Requirement ID**: FR-001
- **Title**: แสดงสถานะ Agent แบบ Real-time
- **Description**: ระบบต้องสามารถแสดงสถานะปัจจุบันของ agents ทั้งหมดบน dashboard แบบ real-time
- **Related Use Cases**: UC-03
- **Related User Stories**: US-001
- **Priority**: HIGH
- **Input**: Agent status changes จาก database
- **Process**: Query agent data, format display, update via WebSocket
- **Output**: Real-time dashboard แสดง agent list พร้อมสถานะ
- **Success Criteria**: 
  - แสดงข้อมูล agents ภายใน 3 วินาที
  - อัปเดต real-time เมื่อมี status changes
  - แสดง color coding ตาม status
  - แสดง timestamp ของการอัปเดตล่าสุด

##### **FR-002: Agent Status Update**  
- **Requirement ID**: FR-002
- **Title**: การเปลี่ยนสถานะของ Agent
- **Description**: Agent ต้องสามารถเปลี่ยนสถานะของตัวเองผ่าน desktop application
- **Related Use Cases**: UC-02
- **Related User Stories**: US-002
- **Priority**: HIGH
- **Input**: Status selection จาก dropdown (Available, Active, Wrap, Not Ready)
- **Process**: Validate status, update database, broadcast via WebSocket
- **Output**: Status อัปเดตใน dashboard และ agent application
- **Success Criteria**:
  - Status อัปเดตใน dashboard ภายใน 1 วินาที
  - ไม่มี status conflicts หรือ race conditions
  - บันทึก timestamp ของการเปลี่ยนสถานะ
  - Agent เห็น confirmation ของการเปลี่ยนสถานะ

##### **FR-003: Agent Login/Logout Tracking**
- **Requirement ID**: FR-003  
- **Title**: ติดตามการ Login/Logout ของ Agent
- **Description**: ระบบต้องบันทึกและติดตามเวลา login/logout ของ agents
- **Related Use Cases**: UC-01, UC-07
- **Related User Stories**: US-003, US-006
- **Priority**: HIGH
- **Input**: Agent login/logout events
- **Process**: Record timestamps, update connection status, log to database
- **Output**: Attendance logs และ connection status indicators
- **Success Criteria**:
  - บันทึก login time เมื่อ agent เข้าระบบสำเร็จ
  - บันทึก logout time เมื่อ agent ออกจากระบบ
  - ตรวจจับ unexpected disconnection
  - เก็บ attendance history สำหรับ reporting

#### **3.1.2 Epic 2: Supervisor Communication System**

##### **FR-004: Send Message to Agent**
- **Requirement ID**: FR-004
- **Title**: การส่งข้อความไปยัง Agent
- **Description**: Supervisor ต้องสามารถส่งข้อความไปยัง agent ที่เฉพาะเจาะจงผ่าน dashboard
- **Related Use Cases**: UC-04
- **Related User Stories**: US-004
- **Priority**: HIGH  
- **Input**: Target agent selection, message text
- **Process**: Validate message, route via WebSocket, log message
- **Output**: Message delivered to target agent, delivery confirmation
- **Success Criteria**:
  - ส่งข้อความถึง online agent ภายใน 2 วินาที
  - แสดง delivery status confirmation
  - บันทึก message history
  - Handle case เมื่อ agent offline

##### **FR-005: Receive Notification**
- **Requirement ID**: FR-005
- **Title**: การรับ Notification สำหรับ Agent  
- **Description**: Agent ต้องรับ notification เมื่อมีข้อความจาก supervisor
- **Related Use Cases**: UC-05
- **Related User Stories**: US-005
- **Priority**: HIGH
- **Input**: Message จาก supervisor via WebSocket
- **Process**: Display notification, play alert sound, show popup
- **Output**: Desktop notification และ popup message
- **Success Criteria**:
  - แสดง desktop notification ทันที
  - เล่นเสียงแจ้งเตือน
  - แสดง popup พร้อม message content
  - Agent สามารถปิด notification ได้

#### **3.1.3 Epic 3: Agent Self-Service Portal**

##### **FR-006: Agent Authentication**
- **Requirement ID**: FR-006
- **Title**: การยืนยันตัวตนของ Agent
- **Description**: Agent ต้องสามารถ login เข้าระบบด้วย Agent Code
- **Related Use Cases**: UC-01
- **Related User Stories**: US-006
- **Priority**: HIGH
- **Input**: Agent Code
- **Process**: Validate against database, create session, establish WebSocket
- **Output**: Authenticated session, dashboard access
- **Success Criteria**:
  - Authentication ภายใน 2 วินาที
  - แสดง error message สำหรับ invalid Agent Code
  - สร้าง secure session
  - เชื่อมต่อ WebSocket หลัง authentication สำเร็จ

##### **FR-007: Agent Profile Information**
- **Requirement ID**: FR-007
- **Title**: การจัดการข้อมูลส่วนตัวของ Agent
- **Description**: Agent ต้องสามารถดูข้อมูลส่วนตัวและสถานะปัจจุบัน
- **Related Use Cases**: UC-06 (ส่วนหนึ่ง)
- **Related User Stories**: US-007
- **Priority**: MEDIUM
- **Input**: Agent session information
- **Process**: Query agent data, format display
- **Output**: Agent profile information display
- **Success Criteria**:
  - แสดง Agent Code, Name, และ current status
  - แสดงเวลา login วันปัจจุบัน
  - อัปเดตข้อมูลแบบ real-time

#### **3.1.4 Epic 4: Management Dashboard & Reporting**

##### **FR-008: Team Dashboard**
- **Requirement ID**: FR-008
- **Title**: Dashboard สำหรับ Supervisor
- **Description**: แสดงสถิติโดยรวมของทีมและ real-time metrics
- **Related Use Cases**: UC-06
- **Related User Stories**: US-008
- **Priority**: HIGH
- **Input**: Aggregated agent data
- **Process**: Calculate statistics, create visualizations, update real-time
- **Output**: Interactive dashboard พร้อม charts และ metrics
- **Success Criteria**:
  - แสดงจำนวน agents ตาม status categories
  - แสดงสถิติ online/offline agents
  - อัปเดตข้อมูลแบบ real-time
  - แสดงเวลาปัจจุบันและ team summary

##### **FR-009: Statistical Reports**
- **Requirement ID**: FR-009
- **Title**: รายงานสถิติแบบ Real-time
- **Description**: แสดงสถิติการทำงานและ performance metrics
- **Related Use Cases**: UC-08
- **Related User Stories**: US-009
- **Priority**: MEDIUM
- **Input**: Historical และ real-time data
- **Process**: Generate reports, create visualizations
- **Output**: Statistical reports และ performance metrics
- **Success Criteria**:
  - แสดง placeholder metrics (Queue, Calls statistics)
  - อัปเดตตัวเลขแบบ real-time  
  - ใช้สีและ icons ที่เหมาะสม
  - เตรียมไว้สำหรับ future enhancements

#### **3.1.5 Epic 5: System Administration & Configuration**

##### **FR-010: Database Management**
- **Requirement ID**: FR-010
- **Title**: การจัดการฐานข้อมูล
- **Description**: จัดการ database connections และ data operations
- **Related Use Cases**: UC-09
- **Related User Stories**: US-010
- **Priority**: HIGH
- **Input**: Database configuration parameters
- **Process**: Establish connections, handle queries, manage connection pool
- **Output**: Stable database operations
- **Success Criteria**:
  - เชื่อมต่อ MSSQL database สำเร็จ
  - จัดการ connection pool อย่างมีประสิทธิภาพ
  - Handle connection failures gracefully
  - Support concurrent operations

##### **FR-011: API Endpoint Management**
- **Requirement ID**: FR-011
- **Title**: การจัดการ API Endpoints
- **Description**: จัดการ REST API endpoints และ authentication
- **Related Use Cases**: UC-10
- **Related User Stories**: US-011
- **Priority**: HIGH
- **Input**: API requests พร้อม authentication tokens
- **Process**: Route requests, validate authentication, process business logic
- **Output**: JSON responses ตาม REST principles
- **Success Criteria**:
  - API endpoints ทำงานตาม specification
  - Bearer Token authentication ทำงานถูกต้อง
  - Response times ภายใน 500ms
  - Error handling และ appropriate HTTP status codes

##### **FR-012: WebSocket Connection Management**
- **Requirement ID**: FR-012
- **Title**: การจัดการ WebSocket Connections
- **Description**: จัดการ real-time connections และ message routing
- **Related Use Cases**: UC-11
- **Related User Stories**: US-012
- **Priority**: HIGH
- **Input**: WebSocket connection requests และ messages
- **Process**: Manage connection pool, route messages, handle disconnections
- **Output**: Stable real-time communication
- **Success Criteria**:
  - Support concurrent WebSocket connections
  - Message routing ระหว่าง clients
  - Handle connection drops และ reconnection
  - Performance monitoring และ logging

##### **FR-013: Application Deployment**
- **Requirement ID**: FR-013
- **Title**: การ Deploy Desktop Application
- **Description**: สร้างและแจกจ่าย desktop application installer
- **Related Use Cases**: UC-12
- **Related User Stories**: US-013
- **Priority**: MEDIUM
- **Input**: Electron.js application source code
- **Process**: Build executable, create installer, distribute
- **Output**: Windows installer package
- **Success Criteria**:
  - สร้าง .exe installer สำเร็จ
  - Installer ทำงานบน target Windows systems
  - Application รันได้หลัง installation
  - Configuration management สำหรับ different environments

##### **FR-014: System Configuration**
- **Requirement ID**: FR-014
- **Title**: การจัดการ Configuration ระบบ
- **Description**: จัดการ configuration แยกตาม environment (development/production)
- **Related Use Cases**: UC-13
- **Related User Stories**: US-014
- **Priority**: MEDIUM
- **Input**: Environment-specific configuration parameters
- **Process**: Load configuration, validate settings, apply to system components
- **Output**: System configured สำหรับ target environment
- **Success Criteria**:
  - แยก configuration files ตาม environment
  - จัดการ database connection strings
  - กำหนด API URLs และ WebSocket endpoints
  - SSL certificate management

### 3.2 ความต้องการเชิงคุณภาพ (Non-functional Requirements)

#### **3.2.1 Performance Requirements**

##### **NFR-001: Response Time**
- **Requirement ID**: NFR-001
- **Description**: ระบบต้องมี response time ที่เหมาะสมสำหรับ real-time operations
- **Specifications**:
  - API response time: < 500ms สำหรับ 95% ของ requests
  - WebSocket message delivery: < 1 วินาที
  - Dashboard loading time: < 3 วินาที
  - Status update propagation: < 1 วินาที
- **Measurement**: Response time monitoring และ performance testing
- **Priority**: HIGH

##### **NFR-002: Throughput**
- **Requirement ID**: NFR-002
- **Description**: ระบบต้องรองรับจำนวน concurrent users และ operations ตามที่กำหนด
- **Specifications**:
  - Concurrent agents: ≥ 100 agents
  - Concurrent supervisors: ≥ 20 supervisors  
  - API requests: ≥ 1000 requests/minute
  - WebSocket connections: ≥ 120 concurrent connections
- **Measurement**: Load testing และ performance monitoring
- **Priority**: HIGH

##### **NFR-003: Scalability**
- **Requirement ID**: NFR-003
- **Description**: ระบบต้องสามารถขยายตัวได้เมื่อมีผู้ใช้เพิ่มขึ้น
- **Specifications**:
  - Horizontal scaling: รองรับ multiple API server instances
  - Database scaling: Connection pooling และ query optimization
  - Memory usage: < 500MB RAM ต่อ 100 concurrent users
- **Measurement**: Scalability testing และ resource monitoring
- **Priority**: MEDIUM

#### **3.2.2 Reliability Requirements**

##### **NFR-004: Availability**
- **Requirement ID**: NFR-004
- **Description**: ระบบต้องมี uptime ที่สูงสำหรับการใช้งานต่อเนื่อง
- **Specifications**:
  - System uptime: ≥ 99% ในเวลาทำการ
  - WebSocket connection stability: ≥ 95% connection success rate
  - Data consistency: 100% ของ status updates ต้องถูกบันทึก
- **Measurement**: Uptime monitoring และ reliability testing
- **Priority**: HIGH

##### **NFR-005: Error Handling**
- **Requirement ID**: NFR-005
- **Description**: ระบบต้องจัดการ errors และ exceptions ได้อย่างเหมาะสม
- **Specifications**:
  - Graceful degradation เมื่อ network issues
  - Automatic reconnection สำหรับ WebSocket
  - User-friendly error messages
  - Error logging และ monitoring
- **Measurement**: Error rate monitoring และ exception handling testing
- **Priority**: HIGH

#### **3.2.3 Usability Requirements**

##### **NFR-006: User Interface**
- **Requirement ID**: NFR-006
- **Description**: User interface ต้องใช้งานง่ายและเป็นมิตรกับผู้ใช้
- **Specifications**:
  - Intuitive navigation: Users สามารถเข้าใจการใช้งานภายใน 5 นาที
  - Consistent UI: ใช้ design patterns เดียวกันทั้งระบบ
  - Responsive design: แสดงผลได้ดีบน screen sizes ต่างๆ
  - Accessibility: รองรับ basic accessibility features
- **Measurement**: Usability testing และ user feedback
- **Priority**: MEDIUM

##### **NFR-007: Learning Curve**
- **Requirement ID**: NFR-007
- **Description**: ผู้ใช้ใหม่ต้องสามารถเรียนรู้การใช้งานได้อย่างรวดเร็ว
- **Specifications**:
  - Agent training time: ≤ 1 ชั่วโมง
  - Supervisor training time: ≤ 2 ชั่วโมง
  - Online help และ documentation
  - Clear labeling และ visual cues
- **Measurement**: Training time metrics และ user feedback
- **Priority**: MEDIUM

#### **3.2.4 Security Requirements**

##### **NFR-008: Authentication & Authorization**
- **Requirement ID**: NFR-008
- **Description**: ระบบต้องมีความปลอดภัยในการ authentication และ authorization
- **Specifications**:
  - Secure authentication: Bearer Token authentication
  - Session management: Secure session handling
  - Role-based access: แยกสิทธิ์ตาม user roles
  - Password security: Secure credential storage (ถ้ามี)
- **Measurement**: Security testing และ penetration testing
- **Priority**: HIGH

##### **NFR-009: Data Protection**
- **Requirement ID**: NFR-009
- **Description**: ข้อมูลต้องได้รับการปกป้องจากการเข้าถึงที่ไม่ได้รับอนุญาต
- **Specifications**:
  - HTTPS/SSL encryption สำหรับ web communications
  - WSS (Secure WebSocket) สำหรับ real-time communications
  - Database connection security
  - Input validation และ sanitization
- **Measurement**: Security audit และ vulnerability testing
- **Priority**: HIGH

#### **3.2.5 Compatibility Requirements**

##### **NFR-010: Platform Compatibility**
- **Requirement ID**: NFR-010
- **Description**: ระบบต้องทำงานได้บน platforms ที่กำหนด
- **Specifications**:
  - Desktop OS: Windows 10/11 (64-bit)
  - Web browsers: Chrome 90+, Firefox 88+, Edge 90+
  - Node.js: Version 18 หรือสูงกว่า
  - Database: MSSQL 2019+, MongoDB 4.4+
- **Measurement**: Compatibility testing บน target platforms
- **Priority**: HIGH

##### **NFR-011: Integration Compatibility**
- **Requirement ID**: NFR-011
- **Description**: ระบบต้องสามารถ integrate กับ systems และ tools ปัจจุบัน
- **Specifications**:
  - Database connectivity: Standard drivers และ protocols
  - API compatibility: REST API standards
  - Network protocols: Standard TCP/IP, HTTP/HTTPS, WebSocket
- **Measurement**: Integration testing
- **Priority**: MEDIUM

#### **3.2.6 Maintainability Requirements**

##### **NFR-012: Code Quality**
- **Requirement ID**: NFR-012
- **Description**: Code ต้องมีคุณภาพและบำรุงรักษาได้ง่าย
- **Specifications**:
  - Code documentation: Comments และ technical documentation
  - Coding standards: Consistent coding style
  - Modular design: Separation of concerns
  - Error logging: Comprehensive logging system
- **Measurement**: Code review และ static analysis
- **Priority**: MEDIUM

##### **NFR-013: Deployment & Updates**
- **Requirement ID**: NFR-013
- **Description**: ระบบต้อง deploy และ update ได้ง่าย
- **Specifications**:
  - Automated deployment: Build และ deployment scripts
  - Configuration management: Environment-specific configurations
  - Rollback capability: สามารถ rollback เมื่อมีปัญหา
  - Update mechanism: สำหรับ desktop application updates
- **Measurement**: Deployment success rate และ update testing
- **Priority**: MEDIUM

### 3.3 Traceability Matrix

#### **3.3.1 Requirements to Use Case Mapping**

| Functional Requirement | Use Case | User Story | Epic | Priority | Verification Method |
|------------------------|----------|------------|------|----------|-------------------|
| **FR-001** | UC-03 | US-001 | Epic 1 | HIGH | Integration Testing, UI Testing |
| **FR-002** | UC-02 | US-002 | Epic 1 | HIGH | Unit Testing, Integration Testing |
| **FR-003** | UC-01, UC-07 | US-003, US-006 | Epic 1, Epic 3 | HIGH | Database Testing, Session Testing |
| **FR-004** | UC-04 | US-004 | Epic 2 | HIGH | WebSocket Testing, Message Testing |
| **FR-005** | UC-05 | US-005 | Epic 2 | HIGH | Notification Testing, UI Testing |
| **FR-006** | UC-01 | US-006 | Epic 3 | HIGH | Authentication Testing, Security Testing |
| **FR-007** | UC-06 | US-007 | Epic 3 | MEDIUM | UI Testing, Data Validation Testing |
| **FR-008** | UC-06 | US-008 | Epic 4 | HIGH | Dashboard Testing, Real-time Testing |
| **FR-009** | UC-08 | US-009 | Epic 4 | MEDIUM | Reporting Testing, Data Analysis Testing |
| **FR-010** | UC-09 | US-010 | Epic 5 | HIGH | Database Testing, Connection Testing |
| **FR-011** | UC-10 | US-011 | Epic 5 | HIGH | API Testing, Security Testing |
| **FR-012** | UC-11 | US-012 | Epic 5 | HIGH | WebSocket Testing, Performance Testing |
| **FR-013** | UC-12 | US-013 | Epic 5 | MEDIUM | Deployment Testing, Installation Testing |
| **FR-014** | UC-13 | US-014 | Epic 5 | MEDIUM | Configuration Testing, Environment Testing |

#### **3.3.2 Epic Coverage Analysis**

| Epic | Requirements Count | Use Cases Count | User Stories Count | Completion % |
|------|-------------------|-----------------|-------------------|--------------|
| **Epic 1: Real-time Monitoring** | 3 (FR-001 to FR-003) | 3 (UC-01, UC-02, UC-03, UC-07) | 3 (US-001, US-002, US-003, US-006) | 100% |
| **Epic 2: Communication** | 2 (FR-004, FR-005) | 2 (UC-04, UC-05) | 2 (US-004, US-005) | 100% |
| **Epic 3: Agent Portal** | 2 (FR-006, FR-007) | 2 (UC-01, UC-06) | 2 (US-006, US-007) | 100% |
| **Epic 4: Dashboard & Reporting** | 2 (FR-008, FR-009) | 2 (UC-06, UC-08) | 2 (US-008, US-009) | 100% |
| **Epic 5: Administration** | 5 (FR-010 to FR-014) | 5 (UC-09 to UC-13) | 5 (US-010 to US-014) | 100% |

#### **3.3.3 Verification and Validation Matrix**

| Requirement Type | Verification Method | Validation Method | Acceptance Criteria |
|------------------|-------------------|------------------|-------------------|
| **Functional Requirements** | Unit Testing, Integration Testing | User Acceptance Testing | Business rules compliance |
| **Performance Requirements** | Load Testing, Performance Testing | Stress Testing | Performance benchmarks met |
| **Security Requirements** | Security Testing, Code Review | Penetration Testing | Security standards compliance |
| **Usability Requirements** | Usability Testing, UI Review | User Experience Testing | User satisfaction metrics |
| **Compatibility Requirements** | Platform Testing, Browser Testing | Cross-platform Validation | Platform support verification |

### 3.4 System Features

#### **3.4.1 Feature: Real-time Status Monitoring**
- **Feature ID**: F-001
- **Description**: ระบบแสดงและอัปเดตสถานะ agents แบบ real-time
- **Associated Requirements**: FR-001, FR-002, FR-003, NFR-001, NFR-004
- **Priority**: HIGH
- **Risk**: MEDIUM (WebSocket stability dependencies)

#### **3.4.2 Feature: Bidirectional Communication**
- **Feature ID**: F-002  
- **Description**: ระบบสื่อสารระหว่าง supervisors และ agents แบบ real-time
- **Associated Requirements**: FR-004, FR-005, NFR-002, NFR-008
- **Priority**: HIGH
- **Risk**: MEDIUM (Message delivery reliability)

#### **3.4.3 Feature: Management Dashboard**
- **Feature ID**: F-003
- **Description**: Dashboard สำหรับการจัดการและติดตาม team performance
- **Associated Requirements**: FR-008, FR-009, NFR-006, NFR-010
- **Priority**: HIGH  
- **Risk**: LOW (Standard dashboard functionality)

#### **3.4.4 Feature: System Administration**
- **Feature ID**: F-004
- **Description**: เครื่องมือสำหรับ system administrators ในการจัดการระบบ
- **Associated Requirements**: FR-010 to FR-014, NFR-012, NFR-013
- **Priority**: MEDIUM
- **Risk**: LOW (Administrative tools)

---

## 4. ภาคผนวก (Appendices)

### 4.1 Glossary

#### **4.1.1 Technical Terms**

| Term | Definition |
|------|------------|
| **3-Tier Architecture** | แบบแผนการออกแบบซอฟต์แวร์ที่แบ่งเป็น 3 ชั้น: Presentation, Application, และ Data |
| **API (Application Programming Interface)** | ชุดของ protocols และ tools สำหรับการสร้าง software applications |
| **Bearer Token** | วิธีการ authentication โดยใช้ token ในการยืนยันตัวตน |
| **Desktop Application** | โปรแกรมที่รันบน desktop operating system |
| **Electron.js** | Framework สำหรับการสร้าง desktop applications ด้วย web technologies |
| **JSON (JavaScript Object Notation)** | รูปแบบการแลกเปลี่ยนข้อมูลที่อ่านได้ง่าย |
| **JWT (JSON Web Token)** | มาตรฐานสำหรับการสร้าง access tokens |
| **MongoDB** | NoSQL database ที่เก็บข้อมูลในรูปแบบ documents |
| **MSSQL (Microsoft SQL Server)** | Relational database management system ของ Microsoft |
| **Node.js** | JavaScript runtime สำหรับการพัฒนา server-side applications |
| **Real-time** | การประมวลผลที่ให้ผลลัพธ์ทันทีหรือใกล้เคียงกับเวลาจริง |
| **REST (Representational State Transfer)** | Architectural style สำหรับการออกแบบ web services |
| **SSL/TLS** | Protocols สำหรับการเข้ารหัสการสื่อสารผ่าน network |
| **WebSocket** | Protocol สำหรับการสื่อสารแบบ bidirectional ระหว่าง client และ server |

#### **4.1.2 Business Terms**

| Term | Definition |
|------|------------|
| **Agent** | พนักงาน call center ที่รับโทรศัพท์จากลูกค้า |
| **Available** | สถานะที่แสดงว่า agent พร้อมรับงานใหม่ |
| **Active** | สถานะที่แสดงว่า agent กำลังดำเนินงานอยู่ |
| **Call Center** | ศูนย์บริการลูกค้าทางโทรศัพท์ |
| **Dashboard** | หน้าจอแสดงข้อมูลสรุปและสถิติ |
| **Not Ready** | สถานะที่แสดงว่า agent ไม่พร้อมรับงาน |
| **Operations Manager** | ผู้จัดการระดับสูงที่ดูแลการดำเนินงานโดยรวม |
| **Supervisor** | หัวหน้าทีมที่ดูแลและควบคุม agents |
| **System Administrator** | ผู้ดูแลระบบ IT และการกำหนดค่าระบบ |
| **Wallboard** | หน้าจอแสดงสถานะและสถิติของ agents |
| **Wrap** | สถานะที่แสดงว่า agent กำลังจัดการงานหลังการให้บริการ |

### 4.2 Requirements Verification Plan

#### **4.2.1 Testing Strategy**

##### **Unit Testing (ระดับ Component)**
- **Scope**: ทดสอบ individual functions และ methods
- **Coverage Target**: ≥ 80% code coverage
- **Tools**: Jest, Mocha
- **Responsibility**: Development Team

##### **Integration Testing (ระดับ System)**  
- **Scope**: ทดสอบการทำงานร่วมกันระหว่าง components
- **Focus Areas**: API integration, Database connectivity, WebSocket communication
- **Tools**: Postman, Custom test scripts
- **Responsibility**: Development Team + Testing Team

##### **System Testing (ระดับ End-to-End)**
- **Scope**: ทดสอบระบบทั้งหมดตาม user scenarios  
- **Focus Areas**: User workflows, Performance, Security
- **Tools**: Selenium, Manual testing
- **Responsibility**: Testing Team

##### **User Acceptance Testing (ระดับ Business)**
- **Scope**: ทดสอบตาม business requirements และ user expectations
- **Participants**: End users, Project stakeholders
- **Duration**: 1 สัปดาห์
- **Responsibility**: Product Owner + End Users

#### **4.2.2 Acceptance Criteria Summary**

| Requirement Category | Success Metrics | Testing Method |
|---------------------|-----------------|----------------|
| **Functional** | All user stories pass acceptance criteria | UAT, Integration Testing |
| **Performance** | Response time < 500ms, Support 100+ users | Load Testing, Performance Testing |
| **Security** | Authentication working, HTTPS encryption | Security Testing, Penetration Testing |
| **Usability** | User satisfaction > 4/5, Training time < targets | Usability Testing, User Feedback |
| **Compatibility** | Works on target platforms | Platform Testing, Browser Testing |

### 4.3 Risk Assessment

#### **4.3.1 Technical Risks**

| Risk | Probability | Impact | Mitigation Strategy |
|------|-------------|---------|-------------------|
| **WebSocket Performance Issues** | Medium | High | Early performance testing, Connection pooling |
| **Database Scalability** | Medium | Medium | Query optimization, Connection management |
| **Browser Compatibility** | Low | Medium | Cross-browser testing, Fallback mechanisms |
| **Security Vulnerabilities** | Low | High | Security review, Penetration testing |

#### **4.3.2 Project Risks**

| Risk | Probability | Impact | Mitigation Strategy |
|------|-------------|---------|-------------------|
| **Timeline Delays** | Medium | High | Agile development, Regular progress monitoring |
| **Skill Gap** | Medium | Medium | Training, Knowledge sharing, Mentoring |
| **Scope Creep** | Medium | Medium | Clear requirements, Change control process |
| **Resource Availability** | Low | Medium | Resource planning, Backup plans |

### 4.4 Change Management Process

#### **4.4.1 Change Request Process**
1. **Change Identification**: Stakeholder identifies need for change
2. **Impact Analysis**: Assess impact on timeline, resources, other requirements
3. **Change Approval**: Project stakeholders review and approve/reject
4. **Implementation**: Update requirements, design, and implementation
5. **Verification**: Test and validate changes
6. **Documentation Update**: Update all relevant documents

#### **4.4.2 Version Control**
- **Document Version**: SRS version tracked และ maintained
- **Requirements Traceability**: Changes tracked back to source
- **Baseline Management**: Approved baselines maintained
- **Change History**: Complete change history documented

### 4.5 Compliance and Standards

#### **4.5.1 IEEE 830 Compliance Checklist**

| IEEE 830 Criterion | Compliance Status | Notes |
|--------------------|------------------|-------|
| **Correct** | ✅ Compliant | Requirements reviewed by stakeholders |
| **Unambiguous** | ✅ Compliant | Clear descriptions และ acceptance criteria |
| **Complete** | ✅ Compliant | All system functions covered |
| **Consistent** | ✅ Compliant | No conflicting requirements |
| **Ranked for importance** | ✅ Compliant | Priority levels assigned |
| **Verifiable** | ✅ Compliant | Testable acceptance criteria |
| **Modifiable** | ✅ Compliant | Clear structure และ traceability |
| **Traceable** | ✅ Compliant | Traceability matrix provided |

#### **4.5.2 Quality Standards**
- **Software Quality**: ISO 9126 quality characteristics considered
- **Security Standards**: Basic security principles applied
- **Development Standards**: Coding standards และ best practices
- **Documentation Standards**: Consistent documentation format

---

## สรุปผู้บริหาร (Executive Summary)

### Project Overview
Agent Wallboard System เป็นระบบ real-time monitoring และ communication สำหรับ call center operations ที่พัฒนาด้วย 3-tier architecture โดยมีเป้าหมายเพื่อเพิ่มประสิทธิภาพการดำเนินงานและปรับปรุงการสื่อสารระหว่าง supervisors และ agents

### Key Requirements Summary
- **14 Functional Requirements** ครอบคลุม 5 Epic areas
- **13 Non-functional Requirements** เน้น performance, security และ usability  
- **13 Use Cases** พร้อม complete traceability
- **4 Primary User Types** ที่มีความต้องการแตกต่างกัน

### Success Criteria
- ✅ **100% Requirements Coverage**: ทุก user stories มี functional requirements รองรับ
- ✅ **Complete Traceability**: Requirements ↔ Use Cases ↔ User Stories mapping
- ✅ **IEEE 830 Compliance**: เป็นไปตามมาตรฐาน IEEE 830-1998
- ✅ **Academic Quality**: เหมาะสมสำหรับการประเมินในระดับ undergraduate

