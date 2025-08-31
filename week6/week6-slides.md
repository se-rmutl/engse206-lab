# ENGSE206: Software Requirements & Design
## สัปดาห์ที่ 6: การออกแบบข้อมูลและฐานข้อมูล

### Software Engineering Course: Architecture Design Workshop
**Agent Wallboard System Case Study**

---

## Slide 1: Course Overview & Weekly Progress

### 📚 สัปดาห์ที่แล้ว: สัปดาห์ที่ 5
✅ **สิ่งที่เรียนมาแล้ว:**
- หลักการออกแบบพื้นฐาน: SOLID, DRY, KISS, YAGNI
- สถาปัตยกรรม 3-Tier Architecture
- **C4 Model:** C1 (System Context) และ C2 (Containers)
- การออกแบบ Architecture ระดับสูง

### 🎯 **สัปดาห์นี้: สัปดาห์ที่ 6**
**วัตถุประสงค์:** ออกแบบโครงสร้างข้อมูลเพื่อรองรับการทำงานของระบบ สามารถสร้าง ER Diagram และเข้าใจการเลือกใช้ฐานข้อมูล

**เนื้อหาหลัก:**
1. 📊 หลักการออกแบบฐานข้อมูลและ Data Modeling
2. 🗂️ Entity-Relationship (ER) Diagram
3. 🔧 การทำ Normalization พื้นฐาน
4. 🤔 การตัดสินใจเลือกระหว่าง SQL vs NoSQL

### 🎪 **Case Study:** Agent Wallboard System
**ตัวอย่างระบบ Call Center ที่แสดงสถานะและประสิทธิภาพของ Agents แบบ Real-time**

---

## Slide 2: Agent Wallboard System Overview

### 🎯 **Agent Wallboard System คืออะไร?**

**Agent Wallboard System** คือระบบแสดงผลสถานะและประสิทธิภาพของพนักงาน Call Center แบบ Real-time บนจอแสดงผลขนาดใหญ่

### 🏢 **Context และการใช้งานจริง**
```
📞 Call Center Environment
├── 50-200 Agents ทำงานพร้อมกัน
├── 10+ Supervisors ควบคุมและติดตาม
├── Real-time Dashboard บนจอ TV ขนาดใหญ่
└── Performance Metrics และ KPIs แสดงแบบ Live
```

### 🎪 **ฟีเจอร์หลัก**
- **Real-time Agent Status:** Available, Busy, Break, Offline
- **Call Statistics:** Total calls, Answer rate, Average handling time
- **Performance Ranking:** Top performers, Team leaderboards
- **Alert System:** SLA violations, Long queue times
- **Historical Reports:** Daily, weekly, monthly analytics

### 💼 **Stakeholders**
- **Call Center Agents:** ดูสถานะตนเองและทีม
- **Supervisors:** ติดตามประสิทธิภาพและจัดการทีม
- **Managers:** วิเคราะห์ Performance และ KPIs
- **IT Support:** บำรุงรักษาระบบและแก้ไขปัญหา

---

## Slide 3: From Architecture to Data Design

### 🔄 **จากสัปดาห์ที่ 5 สู่สัปดาห์ที่ 6**

**สัปดาห์ที่ 5: C2 Container Diagram Review**

```
┌─────────────────────────────────────────────────────┐
│                Agent Wallboard System               │
│                                                     │
│  ┌─────────────┐    ┌──────────────┐   ┌─────────────┐ │
│  │   Web App   │    │   Mobile     │   │  Display    │ │
│  │  (React.js) │    │    App       │   │  Dashboard  │ │
│  │             │────┤              │───│   (Vue.js)  │ │
│  └─────────────┘    └──────────────┘   └─────────────┘ │
│         │                   │                   │      │
│         └───────────────────┼───────────────────┘      │
│                             │                          │
│  ┌─────────────────────────────────────────────────────┤
│  │              API Gateway                            │
│  │              (Node.js)                              │
│  └─────────────────┬───────────────────────────────────┘
│                    │                                   │
│  ┌─────────────────┼───────────────────────────────────┤
│  │         ┌───────▼────────┐     ┌───────────────────┐ │
│  │         │  Agent Service │     │  Analytics        │ │
│  │         │  (Node.js)     │     │  Service          │ │
│  │         │                │     │  (Python)         │ │
│  │         └───────┬────────┘     └─────────┬─────────┘ │
│  │                 │                        │           │
│  │  ┌──────────────▼─────────────────────────▼────────┐ │
│  │  │           Database Layer                        │ │
│  │  │     (PostgreSQL + Redis Cache)                  │ │
│  │  └─────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────┘
```

**สัปดาห์ที่ 6: ขุดลึกใน Database Layer**

🎯 **วันนี้เราจะเจาะลึก:**
- ข้อมูลอะไรบ้างที่ต้องเก็บใน Database?
- ความสัมพันธ์ระหว่างข้อมูลเป็นอย่างไร?
- จะออกแบบ Database Schema อย่างไรให้เหมาะสม?
- เลือกใช้ SQL หรือ NoSQL?

---

## Slide 4: Data Modeling Fundamentals

### 📊 **Data Modeling คืออะไร?**

> **Data Modeling** คือกระบวนการออกแบบโครงสร้างข้อมูลเพื่อระบุ entities, attributes, และความสัมพันธ์ที่จำเป็นสำหรับระบบ

### 🏗️ **3 ระดับของ Data Modeling**

```
1. 📝 Conceptual Level (ระดับแนวคิด)
   ├── เน้นความเข้าใจทางธุรกิจ
   ├── ไม่เจาะลึกทางเทคนิค
   └── ใช้ High-level Entities

2. 🗂️ Logical Level (ระดับตรรกะ)
   ├── เจาะลึกความสัมพันธ์
   ├── กำหนด Attributes และ Data Types
   └── ER Diagram แบบละเอียด

3. 🔧 Physical Level (ระดับกายภาพ)
   ├── เฉพาะ Database Platform
   ├── Table Schemas, Indexes
   └── Performance Optimization
```

### 🎯 **การออกแบบที่ดี**

**4 หลักการสำคัญ:**
1. **📏 Accuracy:** ข้อมูลถูกต้องและครบถ้วน
2. **🔄 Consistency:** ไม่มีข้อมูลขัดแย้งกัน
3. **⚡ Performance:** เข้าถึงข้อมูลได้อย่างรวดเร็ว
4. **📈 Scalability:** รองรับการขยายตัวในอนาคต

### 💡 **Agent Wallboard System ต้องการข้อมูลอะไรบ้าง?**

**คิดสิ! ระบบ Call Center ต้องเก็บข้อมูลอะไรบ้าง?**
- 👤 ข้อมูล Agents
- 📞 ข้อมูล Calls
- 📊 สถิติ Performance
- 🏢 ข้อมูลองค์กร (Teams, Departments)
- ⏰ ข้อมูล Shifts และ Schedules

---

## Slide 5: Agent Wallboard System - Data Requirements Analysis

### 🔍 **Business Requirements → Data Requirements**

### 📋 **Functional Requirements Review:**
1. **Real-time Agent Status Display**
2. **Call Statistics Tracking**
3. **Performance Metrics Calculation**
4. **Team Management**
5. **Historical Reporting**
6. **Alert and Notification System**

### 📊 **Data Requirements Analysis**

#### 1️⃣ **Agent Status Tracking**
```
💭 Business Need: แสดงสถานะ Agent แบบ Real-time
📊 Data Requirements:
   ├── Agent Identity (ID, Name, Position)
   ├── Current Status (Available, Busy, Break, Offline)
   ├── Status Timestamp (เริ่มต้น, สิ้นสุด)
   └── Team/Department Assignment
```

#### 2️⃣ **Call Management**
```
💭 Business Need: ติดตาม Calls และคำนวณ Metrics
📊 Data Requirements:
   ├── Call Details (ID, Phone Number, Type)
   ├── Agent Assignment (Who handled?)
   ├── Time Tracking (Start, End, Hold, Transfer)
   ├── Call Outcome (Completed, Abandoned, Transferred)
   └── Quality Scores (Customer Satisfaction)
```

#### 3️⃣ **Performance Analytics**
```
💭 Business Need: KPI Calculation และ Reporting
📊 Data Requirements:
   ├── Daily/Weekly/Monthly Aggregates
   ├── Individual Performance Metrics
   ├── Team Performance Comparisons
   └── Historical Trends
```

#### 4️⃣ **Organizational Structure**
```
💭 Business Need: Team Management และ Hierarchy
📊 Data Requirements:
   ├── Department Structure
   ├── Team Assignments
   ├── Supervisor Relationships
   └── Role-based Permissions
```

---

## Slide 6: Identifying Entities & Attributes

### 🏗️ **Entity Identification Process**

### **Step 1: Noun Identification**
จากความต้องการของระบบ ระบุคำนาม (Nouns) ที่เป็น Entity ได้

**📝 Key Nouns ใน Agent Wallboard System:**
- **Agent** (พนักงาน Call Center)
- **Call** (การโทรเข้า-ออก)
- **Team** (ทีมงาน)
- **Department** (แผนก)
- **Shift** (กะการทำงาน)
- **Performance Metric** (ตัวชี้วัดประสิทธิภาพ)
- **Alert** (การแจ้งเตือน)

### **Step 2: Entity Refinement**

#### 🎭 **Core Entities ของ Agent Wallboard System**

```
1️⃣ AGENT 👤
   ├── agent_id (Primary Key)
   ├── employee_code (Unique)
   ├── first_name, last_name
   ├── email, phone
   ├── hire_date, position
   ├── team_id (Foreign Key)
   └── is_active (Boolean)

2️⃣ TEAM 👥
   ├── team_id (Primary Key)
   ├── team_name
   ├── team_leader_id (Foreign Key → AGENT)
   ├── department_id (Foreign Key)
   └── created_date

3️⃣ DEPARTMENT 🏢
   ├── department_id (Primary Key)
   ├── department_name
   ├── manager_id (Foreign Key → AGENT)
   └── budget_allocation

4️⃣ CALL 📞
   ├── call_id (Primary Key)
   ├── call_start_time
   ├── call_end_time
   ├── agent_id (Foreign Key)
   ├── customer_phone
   ├── call_type (Inbound/Outbound)
   ├── call_duration (Calculated)
   ├── hold_time
   └── call_outcome

5️⃣ AGENT_STATUS 📊
   ├── status_id (Primary Key)
   ├── agent_id (Foreign Key)
   ├── status_type (Available/Busy/Break/Offline)
   ├── start_time
   ├── end_time
   └── duration (Calculated)

6️⃣ SHIFT_SCHEDULE ⏰
   ├── schedule_id (Primary Key)
   ├── agent_id (Foreign Key)
   ├── shift_date
   ├── start_time, end_time
   ├── break_start, break_end
   └── is_overtime (Boolean)
```

### **Step 3: Attribute Classification**

#### 🏷️ **Types of Attributes**

```
📊 Simple Attributes: เก็บค่าเดี่ยว
   └── first_name, email, call_duration

🎯 Composite Attributes: ประกอบด้วยหลายส่วน
   └── full_name = first_name + last_name
   └── address = street + city + postal_code

💿 Derived Attributes: คำนวณได้จากข้อมูลอื่น
   └── age ← birth_date
   └── call_duration ← end_time - start_time
   └── total_calls_today ← COUNT(calls WHERE date = today)

🔑 Key Attributes: ระบุ Entity ได้เฉพาะเจาะจง
   └── agent_id, call_id, team_id
```

---

## Slide 7: Entity Relationship Modeling

### 🔗 **Types of Relationships**

### **1️⃣ One-to-One (1:1)**
**หนึ่งต่อหนึ่ง** - แต่ละ entity มีความสัมพันธ์กับ entity อื่นเพียงตัวเดียว

```
👤 AGENT ←→ 🆔 LOGIN_CREDENTIAL
   หนึ่ง Agent มีหนึ่ง Login Account
   หนึ่ง Login Account ใช้โดยหนึ่ง Agent
```

### **2️⃣ One-to-Many (1:M)**
**หนึ่งต่อหลาย** - entity หนึ่งมีความสัมพันธ์กับหลาย entities

```
👥 TEAM ←→ 👤 AGENT
   หนึ่ง Team มีหลาย Agents
   หนึ่ง Agent อยู่ในหนึ่ง Team

🏢 DEPARTMENT ←→ 👥 TEAM  
   หนึ่ง Department มีหลาย Teams
   หนึ่ง Team อยู่ในหนึ่ง Department

👤 AGENT ←→ 📞 CALL
   หนึ่ง Agent handle หลาย Calls
   หนึ่ง Call ถูก handle โดยหนึ่ง Agent
```

### **3️⃣ Many-to-Many (M:N)**
**หลายต่อหลาย** - entities สามารถมีความสัมพันธ์หลายแบบ

```
👤 AGENT ←→ 🛠️ SKILL
   หนึ่ง Agent มีหลาย Skills
   หนึ่ง Skill ถูกมีโดยหลาย Agents
   
   → ต้องสร้าง AGENT_SKILL table (Junction Table)

⏰ SHIFT ←→ 👤 AGENT (ถ้าใช้ Flexible Shift System)
   หนึ่ง Shift สามารถมีหลาย Agents
   หนึ่ง Agent สามารถทำหลาย Shifts
```

### **4️⃣ Cardinality & Participation**

```
📊 Cardinality: จำนวนความสัมพันธ์
   ├── Minimum: อย่างน้อยเท่าไหร่
   └── Maximum: มากสุดเท่าไหร่

🎯 Participation:
   ├── Total (Mandatory): ต้องมีความสัมพันธ์
   └── Partial (Optional): อาจมีหรือไม่มีก็ได้

ตัวอย่าง:
AGENT ←→ CALL
├── Agent อาจไม่มี Call (เพิ่งเข้าทำงาน)  [Partial]
└── Call ต้องมี Agent handle เสมอ        [Total]
```

---

## Slide 8: ER Diagram for Agent Wallboard System

### 📐 **Complete ER Diagram**

```
                    AGENT WALLBOARD SYSTEM
                         ER DIAGRAM

    ┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
    │   DEPARTMENT    │    1    │      TEAM       │    1    │      AGENT      │
    ├─────────────────┤  ←────  ├─────────────────┤  ←────  ├─────────────────┤
    │ department_id*  │    │    │ team_id*        │    │    │ agent_id*       │
    │ department_name │    │    │ team_name       │    │    │ employee_code   │
    │ manager_id      │    │    │ team_leader_id  │    │    │ first_name      │
    │ budget          │    │    │ department_id#  │    │    │ last_name       │
    │ created_date    │    │    │ created_date    │    │    │ email           │
    └─────────────────┘    M    └─────────────────┘    M    │ phone           │
                                                           │ hire_date       │
                                                           │ position        │
                                                           │ team_id#        │
                                                           │ is_active       │
                                                           └─────────────────┘
                                                                    │
                                                                    │ 1
                                                                    │
                                                                    M
                                                           ┌─────────────────┐
                                                           │      CALL       │
                                                           ├─────────────────┤
                                                           │ call_id*        │
                                                           │ agent_id#       │
                                                           │ customer_phone  │
                                                           │ call_start_time │
                                                           │ call_end_time   │
                                                           │ call_type       │
                                                           │ hold_time       │
                                                           │ transfer_count  │
                                                           │ call_outcome    │
                                                           │ satisfaction    │
                                                           └─────────────────┘

        ┌─────────────────┐         ┌─────────────────┐         ┌─────────────────┐
        │  AGENT_STATUS   │    M    │      AGENT      │    M    │ SHIFT_SCHEDULE  │
        ├─────────────────┤  ────→  ├─────────────────┤  ←────  ├─────────────────┤
        │ status_id*      │    1    │                 │    1    │ schedule_id*    │
        │ agent_id#       │         │    (จากข้างบน)    │         │ agent_id#       │
        │ status_type     │         │                 │         │ shift_date      │
        │ start_time      │         │                 │         │ start_time      │
        │ end_time        │         │                 │         │ end_time        │
        │ duration        │         │                 │         │ break_start     │
        └─────────────────┘         └─────────────────┘         │ break_end       │
                                                                │ is_overtime     │
                                                                └─────────────────┘

        ┌─────────────────┐                           ┌─────────────────┐
        │   SKILL         │                           │   AGENT_SKILL   │
        ├─────────────────┤                           ├─────────────────┤
        │ skill_id*       │    1                   M  │ agent_id#*      │
        │ skill_name      │  ←────────────────────────│ skill_id#*      │
        │ skill_category  │                           │ proficiency     │
        │ description     │                           │ certified_date  │
        └─────────────────┘                           └─────────────────┘
                                 M                               M
                                 │                               │
                                 └───────────────────────────────┘
                                           AGENT (M:N)

    ┌─────────────────┐         ┌─────────────────┐
    │   ALERT         │    M    │      AGENT      │
    ├─────────────────┤  ────→  ├─────────────────┤
    │ alert_id*       │    1    │  (จากข้างบน)     │
    │ agent_id#       │         │                 │
    │ alert_type      │         │                 │
    │ message         │         │                 │
    │ severity        │         │                 │
    │ created_time    │         │                 │
    │ is_resolved     │         │                 │
    └─────────────────┘         └─────────────────┘

Legend: * = Primary Key, # = Foreign Key
```

### 🔍 **Key Relationships Explanation**

```
1️⃣ DEPARTMENT → TEAM → AGENT (Hierarchical)
   🏢 Organization structure: Department contains Teams, Teams contain Agents

2️⃣ AGENT → CALL (1:M)
   👤 One Agent handles many Calls over time

3️⃣ AGENT → AGENT_STATUS (1:M)  
   📊 Agent status changes multiple times during workday

4️⃣ AGENT → SHIFT_SCHEDULE (1:M)
   ⏰ Agent can have multiple shifts scheduled

5️⃣ AGENT ↔ SKILL (M:N via AGENT_SKILL)
   🛠️ Many-to-many relationship requiring junction table

6️⃣ AGENT → ALERT (1:M)
   🚨 Agent can have multiple alerts/notifications
```

---

## Slide 9: Normalization Fundamentals

### 🎯 **Normalization คืออะไร?**

> **Normalization** คือกระบวนการปรับโครงสร้างฐานข้อมูลเพื่อลด **Data Redundancy** และป้องกัน **Data Anomalies**

### ⚠️ **ปัญหาที่เกิดจาก Unnormalized Data**

#### **❌ ตัวอย่าง: Unnormalized Agent Table**

```sql
AGENT_DATA (ไม่ได้ Normalize)
┌──────────┬─────────┬──────────────┬───────────────┬──────────────┬───────────┐
│ agent_id │  name   │ team_name    │ team_leader   │ call_count   │ last_call │
├──────────┼─────────┼──────────────┼───────────────┼──────────────┼───────────┤
│    001   │  สมชาย  │ Sales Team   │ นางสาว กมล    │      15      │ 10:30     │
│    002   │  สมหญิง │ Sales Team   │ นางสาว กมล    │       8      │ 10:45     │
│    003   │   สมใส  │ Support Team │ นาย ประยุทธ   │      22      │ 11:00     │
│    004   │  สมศรี  │ Sales Team   │ นางสาว กมล    │      12      │ 10:20     │
└──────────┴─────────┴──────────────┴───────────────┴──────────────┴───────────┘
```

**🚨 ปัญหาที่เกิดขึ้น:**

1. **📊 Data Redundancy:** team_name, team_leader ซ้ำกันหลายครั้ง
2. **🔄 Update Anomaly:** เปลี่ยนชื่อ team_leader ต้องแก้หลายแถว
3. **❌ Delete Anomaly:** ลบ agent สุดท้ายของ team → ข้อมูล team หายไป
4. **➕ Insert Anomaly:** เพิ่ม team ใหม่ที่ยังไม่มี agent ไม่ได้

### 🎯 **3 Normal Forms ที่สำคัญ**

#### **1️⃣ First Normal Form (1NF)**
**กฎ:** Atomic Values - แต่ละ Cell เก็บค่าเดี่ยวเท่านั้น

```sql
❌ ไม่เป็น 1NF:
┌──────────┬─────────┬──────────────────────┐
│ agent_id │  name   │ skills               │
├──────────┼─────────┼──────────────────────┤
│    001   │  สมชาย  │ English, Sales, CRM  │  ← Multiple values in one cell
└──────────┴─────────┴──────────────────────┘

✅ เป็น 1NF:
┌──────────┬─────────┬──────────┐
│ agent_id │  name   │  skill   │
├──────────┼─────────┼──────────┤
│    001   │  สมชาย  │ English  │
│    001   │  สมชาย  │ Sales    │
│    001   │  สมชาย  │ CRM      │
└──────────┴─────────┴──────────┘
```

#### **2️⃣ Second Normal Form (2NF)**
**กฎ:** 1NF + No Partial Dependency on Primary Key

```sql
❌ ไม่เป็น 2NF (มี Partial Dependency):
CALL_AGENT (call_id, agent_id เป็น Composite Primary Key)
┌─────────┬──────────┬─────────────┬──────────┐
│ call_id │ agent_id │ agent_name  │ duration │
├─────────┼──────────┼─────────────┼──────────┤
│   C001  │   A001   │   สมชาย     │   120    │
└─────────┴──────────┴─────────────┴──────────┘
                       ↑ Depends only on agent_id, not full key

✅ เป็น 2NF (แยก Tables):
CALL                    AGENT
┌─────────┬──────────┬──────────┐  ┌──────────┬─────────────┐
│ call_id │ agent_id │ duration │  │ agent_id │ agent_name  │
├─────────┼──────────┼──────────┤  ├──────────┼─────────────┤
│   C001  │   A001   │   120    │  │   A001   │   สมชาย     │
└─────────┴──────────┴──────────┘  └──────────┴─────────────┘
```

#### **3️⃣ Third Normal Form (3NF)**
**กฎ:** 2NF + No Transitive Dependency

```sql
❌ ไม่เป็น 3NF (มี Transitive Dependency):
AGENT
┌──────────┬─────────────┬───────────────┬──────────────────┐
│ agent_id │ agent_name  │ department_id │ department_name  │
├──────────┼─────────────┼───────────────┼──────────────────┤
│   A001   │   สมชาย     │      D01      │    Sales Dept    │
└──────────┴─────────────┴───────────────┴──────────────────┘
                                          ↑ Depends on department_id, not agent_id

✅ เป็น 3NF (แยก Tables):
AGENT                           DEPARTMENT
┌──────────┬─────────────┬───────────────┐  ┌───────────────┬──────────────────┐
│ agent_id │ agent_name  │ department_id │  │ department_id │ department_name  │
├──────────┼─────────────┼───────────────┤  ├───────────────┼──────────────────┤
│   A001   │   สมชาย     │      D01      │  │      D01      │    Sales Dept    │
└──────────┴─────────────┴───────────────┘  └───────────────┴──────────────────┘
```

---

## Slide 10: Normalized Agent Wallboard Schema

### 🏗️ **Apply Normalization to Agent Wallboard System**

### **Step 1: Identify Tables (3NF)**

```sql
📊 NORMALIZED SCHEMA:

1️⃣ DEPARTMENT (3NF ✅)
┌───────────────┬──────────────────┬─────────────┬──────────────┐
│ department_id │ department_name  │ manager_id  │ created_date │
├───────────────┼──────────────────┼─────────────┼──────────────┤
│     D001      │   Sales Dept     │    A005     │  2024-01-01  │
│     D002      │  Support Dept    │    A010     │  2024-01-01  │
└───────────────┴──────────────────┴─────────────┴──────────────┘

2️⃣ TEAM (3NF ✅)
┌─────────┬─────────────┬───────────────┬────────────────┐
│ team_id │  team_name  │ team_leader   │ department_id  │
├─────────┼─────────────┼───────────────┼────────────────┤
│  T001   │ Sales Team A│     A003      │      D001      │
│  T002   │ Sales Team B│     A007      │      D001      │
│  T003   │Support Team │     A012      │      D002      │
└─────────┴─────────────┴───────────────┴────────────────┘

3️⃣ AGENT (3NF ✅)
┌──────────┬────────────┬─────────────┬─────────────┬─────────┐
│ agent_id │first_name  │  last_name  │    email    │ team_id │
├──────────┼────────────┼─────────────┼─────────────┼─────────┤
│   A001   │   สมชาย    │    ใจดี     │som@email.com│  T001   │
│   A002   │  สมหญิง    │   รักเรียน   │som2@email.com│  T001   │
│   A003   │   สมใส     │   ขยันขัน    │som3@email.com│  T002   │
└──────────┴────────────┴─────────────┴─────────────┴─────────┘

4️⃣ CALL (3NF ✅)
┌─────────┬──────────┬─────────────────┬─────────────────┬────────────┐
│ call_id │ agent_id │ call_start_time │ call_end_time   │ call_type  │
├─────────┼──────────┼─────────────────┼─────────────────┼────────────┤
│  C001   │   A001   │ 2024-01-15 09:00│ 2024-01-15 09:05│  Inbound   │
│  C002   │   A001   │ 2024-01-15 09:10│ 2024-01-15 09:15│  Inbound   │
│  C003   │   A002   │ 2024-01-15 09:05│ 2024-01-15 09:12│  Outbound  │
└─────────┴──────────┴─────────────────┴─────────────────┴────────────┘

5️⃣ AGENT_STATUS (3NF ✅)
┌───────────┬──────────┬─────────────┬─────────────────┬─────────────────┐
│ status_id │ agent_id │status_type  │   start_time    │    end_time     │
├───────────┼──────────┼─────────────┼─────────────────┼─────────────────┤
│   S001    │   A001   │ Available   │ 2024-01-15 08:00│ 2024-01-15 09:00│
│   S002    │   A001   │ Busy        │ 2024-01-15 09:00│ 2024-01-15 09:05│
│   S003    │   A001   │ Available   │ 2024-01-15 09:05│ 2024-01-15 09:10│
└───────────┴──────────┴─────────────┴─────────────────┴─────────────────┘
```

### **Step 2: Benefits ของ Normalization**

```
✅ ประโยชน์ที่ได้รับ:
├── 📉 Data Redundancy ลดลง (ไม่เก็บข้อมูลซ้ำ)
├── 🔧 Update Anomaly หายไป (แก้ไขที่เดียว)
├── ❌ Delete Anomaly หายไป (ข้อมูลไม่หายตาม)
├── ➕ Insert Anomaly หายไป (เพิ่มข้อมูลได้อิสระ)
└── 📊 Data Integrity เพิ่มขึ้น (ข้อมูลถูกต้องคงเดิม)

⚠️ Trade-offs:
├── 🔄 Join Operations เพิ่มขึ้น (Query ซับซ้อนขึ้น)
├── 💾 More Tables (การจัดการเพิ่มขึ้น)
└── 🔍 Complex Queries for Reports
```

---

## Slide 11: SQL vs NoSQL Decision Framework

### 🤔 **การตัดสินใจเลือก Database Type**

### **🔍 Factors ที่ต้องพิจารณา**

#### **1️⃣ Data Structure & Relationships**
```
📊 Agent Wallboard System Analysis:
├── 🔗 Strong Relationships: Agent → Team → Department
├── 📝 Structured Data: Employee info, Call records
├── 🧮 Complex Queries: Join tables for reports
├── 📈 ACID Requirements: Financial data, Call billing
└── 🎯 Consistency เป็นสิ่งสำคัญ
```

#### **2️⃣ Scale & Performance Requirements**
```
⚡ Performance Characteristics:
├── 👥 Concurrent Users: 200 agents + 50 supervisors
├── 📞 Transaction Volume: 1000-5000 calls/hour
├── 🔄 Read vs Write: 70% Read, 30% Write
├── 📊 Real-time Updates: Agent status every second
└── 📈 Growth: 10-20% per year
```

#### **3️⃣ Development & Operations**
```
🛠️ Technical Considerations:
├── 👨‍💻 Team Expertise: SQL มีคนรู้เยอะ
├── 🔧 Tool Ecosystem: Reporting tools support SQL
├── 🏢 Enterprise Integration: ERP systems use SQL
└── 🔒 Compliance: Audit trails ต้อง ACID
```

### **⚖️ SQL vs NoSQL Comparison**

| Criteria | SQL (PostgreSQL) | NoSQL (MongoDB) |
|----------|------------------|-----------------|
| **🔗 Relationships** | ✅ Strong RDBMS features | ❌ Limited JOIN support |
| **📊 ACID** | ✅ Full ACID compliance | ⚠️ Eventual consistency |
| **📈 Scalability** | ⚠️ Vertical scaling mainly | ✅ Horizontal scaling |
| **🔍 Query Complexity** | ✅ Complex SQL queries | ❌ Limited aggregation |
| **🛠️ Development** | ✅ Mature ecosystem | ✅ Flexible schema |
| **📱 Real-time** | ⚠️ Needs additional tools | ✅ Built-in real-time |
| **💾 Data Volume** | ⚠️ Good for structured | ✅ Better for big data |

### **🎯 Recommendation for Agent Wallboard**

```
🏆 RECOMMENDED: PostgreSQL + Redis

📊 Primary Database: PostgreSQL
├── ✅ Perfect for structured agent/call data
├── ✅ Strong consistency for financial data
├── ✅ Complex reporting queries
├── ✅ Enterprise integration
└── ✅ Team expertise available

⚡ Cache Layer: Redis
├── ✅ Real-time agent status
├── ✅ Live dashboard updates
├── ✅ Session management
└── ✅ Performance boost
```

---

## Slide 12: Database Schema Implementation

### 🛠️ **PostgreSQL Implementation**

### **Physical Schema Design**

```sql
-- ===================================
-- AGENT WALLBOARD SYSTEM DATABASE
-- ===================================

-- 1. Department Table
CREATE TABLE departments (
    department_id SERIAL PRIMARY KEY,
    department_name VARCHAR(100) NOT NULL UNIQUE,
    manager_id INTEGER,
    budget_allocation DECIMAL(12,2),
    created_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    CONSTRAINT fk_dept_manager FOREIGN KEY (manager_id) 
        REFERENCES agents(agent_id)
);

-- 2. Team Table  
CREATE TABLE teams (
    team_id SERIAL PRIMARY KEY,
    team_name VARCHAR(100) NOT NULL,
    team_leader_id INTEGER,
    department_id INTEGER NOT NULL,
    target_calls_per_day INTEGER DEFAULT 50,
    created_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    CONSTRAINT fk_team_leader FOREIGN KEY (team_leader_id) 
        REFERENCES agents(agent_id),
    CONSTRAINT fk_team_department FOREIGN KEY (department_id) 
        REFERENCES departments(department_id)
);

-- 3. Agent Table
CREATE TABLE agents (
    agent_id SERIAL PRIMARY KEY,
    employee_code VARCHAR(20) NOT NULL UNIQUE,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(20),
    hire_date DATE NOT NULL,
    position VARCHAR(50),
    team_id INTEGER,
    salary DECIMAL(10,2),
    is_active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    CONSTRAINT fk_agent_team FOREIGN KEY (team_id) 
        REFERENCES teams(team_id)
);

-- 4. Call Table
CREATE TABLE calls (
    call_id SERIAL PRIMARY KEY,
    agent_id INTEGER NOT NULL,
    customer_phone VARCHAR(20),
    call_start_time TIMESTAMP NOT NULL,
    call_end_time TIMESTAMP,
    call_type VARCHAR(20) CHECK (call_type IN ('inbound', 'outbound')),
    hold_time_seconds INTEGER DEFAULT 0,
    transfer_count INTEGER DEFAULT 0,
    call_outcome VARCHAR(30) CHECK (call_outcome IN 
        ('completed', 'abandoned', 'transferred', 'no_answer')),
    customer_satisfaction INTEGER CHECK (customer_satisfaction BETWEEN 1 AND 5),
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    -- Calculated fields
    call_duration_seconds INTEGER GENERATED ALWAYS AS 
        (EXTRACT(EPOCH FROM (call_end_time - call_start_time))::INTEGER) STORED,
    
    CONSTRAINT fk_call_agent FOREIGN KEY (agent_id) 
        REFERENCES agents(agent_id)
);

-- 5. Agent Status Table
CREATE TABLE agent_statuses (
    status_id SERIAL PRIMARY KEY,
    agent_id INTEGER NOT NULL,
    status_type VARCHAR(20) NOT NULL CHECK (status_type IN 
        ('available', 'busy', 'break', 'lunch', 'meeting', 'offline')),
    start_time TIMESTAMP NOT NULL,
    end_time TIMESTAMP,
    duration_seconds INTEGER,
    notes VARCHAR(200),
    
    CONSTRAINT fk_status_agent FOREIGN KEY (agent_id) 
        REFERENCES agents(agent_id)
);

-- 6. Skills Table
CREATE TABLE skills (
    skill_id SERIAL PRIMARY KEY,
    skill_name VARCHAR(50) NOT NULL UNIQUE,
    skill_category VARCHAR(30),
    description TEXT
);

-- 7. Agent Skills Junction Table
CREATE TABLE agent_skills (
    agent_id INTEGER,
    skill_id INTEGER,
    proficiency_level INTEGER CHECK (proficiency_level BETWEEN 1 AND 5),
    certified_date DATE,
    expiry_date DATE,
    
    PRIMARY KEY (agent_id, skill_id),
    CONSTRAINT fk_agent_skill_agent FOREIGN KEY (agent_id) 
        REFERENCES agents(agent_id) ON DELETE CASCADE,
    CONSTRAINT fk_agent_skill_skill FOREIGN KEY (skill_id) 
        REFERENCES skills(skill_id) ON DELETE CASCADE
);

-- 8. Shift Schedule Table
CREATE TABLE shift_schedules (
    schedule_id SERIAL PRIMARY KEY,
    agent_id INTEGER NOT NULL,
    shift_date DATE NOT NULL,
    start_time TIME NOT NULL,
    end_time TIME NOT NULL,
    break_start_time TIME,
    break_end_time TIME,
    is_overtime BOOLEAN DEFAULT false,
    created_by INTEGER,
    
    CONSTRAINT fk_schedule_agent FOREIGN KEY (agent_id) 
        REFERENCES agents(agent_id),
    UNIQUE(agent_id, shift_date) -- One shift per agent per day
);

-- 9. Alerts Table
CREATE TABLE alerts (
    alert_id SERIAL PRIMARY KEY,
    agent_id INTEGER,
    team_id INTEGER,
    alert_type VARCHAR(30) NOT NULL CHECK (alert_type IN 
        ('sla_breach', 'long_break', 'missed_shift', 'low_satisfaction')),
    severity VARCHAR(20) CHECK (severity IN ('low', 'medium', 'high', 'critical')),
    message TEXT NOT NULL,
    created_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    acknowledged_time TIMESTAMP,
    resolved_time TIMESTAMP,
    is_resolved BOOLEAN DEFAULT false,
    
    CONSTRAINT fk_alert_agent FOREIGN KEY (agent_id) 
        REFERENCES agents(agent_id),
    CONSTRAINT fk_alert_team FOREIGN KEY (team_id) 
        REFERENCES teams(team_id)
);
```

### **Performance Optimization**

```sql
-- ===================================
-- INDEXES FOR PERFORMANCE
-- ===================================

-- Agent Status (Real-time queries)
CREATE INDEX idx_agent_status_current ON agent_statuses(agent_id, start_time DESC) 
    WHERE end_time IS NULL;

-- Call Performance Queries  
CREATE INDEX idx_calls_agent_date ON calls(agent_id, call_start_time);
CREATE INDEX idx_calls_outcome_date ON calls(call_outcome, call_start_time);
CREATE INDEX idx_calls_duration ON calls(call_duration_seconds) 
    WHERE call_duration_seconds IS NOT NULL;

-- Team and Department Hierarchy
CREATE INDEX idx_agents_team ON agents(team_id) WHERE is_active = true;
CREATE INDEX idx_teams_department ON teams(department_id);

-- Alert Management
CREATE INDEX idx_alerts_unresolved ON alerts(created_time DESC) 
    WHERE is_resolved = false;
CREATE INDEX idx_alerts_agent_type ON alerts(agent_id, alert_type, created_time);

-- Shift Scheduling
CREATE INDEX idx_schedule_agent_date ON shift_schedules(agent_id, shift_date);
CREATE INDEX idx_schedule_date_range ON shift_schedules(shift_date, start_time, end_time);
```

---

## Slide 13: Advanced Database Features

### 🚀 **Advanced PostgreSQL Features for Agent Wallboard**

### **1️⃣ Views for Common Queries**

```sql
-- ===================================
-- VIEWS FOR BUSINESS LOGIC
-- ===================================

-- Current Agent Status View
CREATE VIEW current_agent_status AS
SELECT 
    a.agent_id,
    a.first_name || ' ' || a.last_name AS agent_name,
    a.employee_code,
    t.team_name,
    d.department_name,
    ast.status_type AS current_status,
    ast.start_time AS status_since,
    EXTRACT(EPOCH FROM (NOW() - ast.start_time))/60 AS minutes_in_status
FROM agents a
JOIN teams t ON a.team_id = t.team_id
JOIN departments d ON t.department_id = d.department_id
LEFT JOIN agent_statuses ast ON a.agent_id = ast.agent_id 
    AND ast.end_time IS NULL
WHERE a.is_active = true;

-- Daily Performance Summary View
CREATE VIEW daily_agent_performance AS
SELECT 
    DATE(c.call_start_time) AS call_date,
    a.agent_id,
    a.first_name || ' ' || a.last_name AS agent_name,
    t.team_name,
    COUNT(*) AS total_calls,
    COUNT(*) FILTER (WHERE c.call_outcome = 'completed') AS completed_calls,
    ROUND(AVG(c.call_duration_seconds)/60.0, 2) AS avg_call_minutes,
    ROUND(AVG(c.customer_satisfaction), 2) AS avg_satisfaction,
    ROUND(COUNT(*) FILTER (WHERE c.call_outcome = 'completed') * 100.0 / COUNT(*), 2) AS completion_rate
FROM calls c
JOIN agents a ON c.agent_id = a.agent_id
JOIN teams t ON a.team_id = t.team_id
WHERE c.call_start_time >= CURRENT_DATE - INTERVAL '30 days'
GROUP BY DATE(c.call_start_time), a.agent_id, a.first_name, a.last_name, t.team_name
ORDER BY call_date DESC, total_calls DESC;

-- Team Leaderboard View
CREATE VIEW team_leaderboard AS
SELECT 
    t.team_name,
    COUNT(DISTINCT a.agent_id) AS active_agents,
    COUNT(c.call_id) AS total_calls_today,
    ROUND(AVG(c.call_duration_seconds)/60.0, 2) AS avg_call_duration,
    ROUND(AVG(c.customer_satisfaction), 2) AS avg_satisfaction,
    ROUND(COUNT(*) FILTER (WHERE c.call_outcome = 'completed') * 100.0 / COUNT(c.call_id), 2) AS success_rate
FROM teams t
JOIN agents a ON t.team_id = a.team_id AND a.is_active = true
LEFT JOIN calls c ON a.agent_id = c.agent_id 
    AND DATE(c.call_start_time) = CURRENT_DATE
GROUP BY t.team_id, t.team_name
ORDER BY success_rate DESC, total_calls_today DESC;
```

### **2️⃣ Stored Procedures for Business Logic**

```sql
-- ===================================
-- STORED PROCEDURES
-- ===================================

-- Update Agent Status with Automatic End Time
CREATE OR REPLACE FUNCTION update_agent_status(
    p_agent_id INTEGER,
    p_new_status VARCHAR(20),
    p_notes VARCHAR(200) DEFAULT NULL
)
RETURNS BOOLEAN AS $
DECLARE
    v_current_status_id INTEGER;
BEGIN
    -- End current status
    UPDATE agent_statuses 
    SET end_time = NOW(),
        duration_seconds = EXTRACT(EPOCH FROM (NOW() - start_time))::INTEGER
    WHERE agent_id = p_agent_id AND end_time IS NULL
    RETURNING status_id INTO v_current_status_id;
    
    -- Insert new status
    INSERT INTO agent_statuses (agent_id, status_type, start_time, notes)
    VALUES (p_agent_id, p_new_status, NOW(), p_notes);
    
    -- Generate alert if needed
    IF p_new_status = 'break' AND 
       (SELECT COUNT(*) FROM agent_statuses 
        WHERE agent_id = p_agent_id 
        AND status_type = 'break' 
        AND start_time::DATE = CURRENT_DATE) > 3 THEN
        
        INSERT INTO alerts (agent_id, alert_type, severity, message)
        VALUES (p_agent_id, 'long_break', 'medium', 
                'Agent has taken more than 3 breaks today');
    END IF;
    
    RETURN TRUE;
EXCEPTION
    WHEN OTHERS THEN
        RETURN FALSE;
END;
$ LANGUAGE plpgsql;

-- Calculate SLA Compliance
CREATE OR REPLACE FUNCTION calculate_team_sla(
    p_team_id INTEGER,
    p_date DATE DEFAULT CURRENT_DATE
)
RETURNS TABLE(
    agent_name TEXT,
    total_calls INTEGER,
    calls_within_sla INTEGER,
    sla_percentage NUMERIC
) AS $
BEGIN
    RETURN QUERY
    SELECT 
        a.first_name || ' ' || a.last_name,
        COUNT(c.call_id)::INTEGER,
        COUNT(c.call_id) FILTER (WHERE c.call_duration_seconds <= 300)::INTEGER, -- 5 min SLA
        ROUND(
            COUNT(*) FILTER (WHERE c.call_duration_seconds <= 300) * 100.0 / 
            NULLIF(COUNT(c.call_id), 0), 
            2
        )
    FROM agents a
    LEFT JOIN calls c ON a.agent_id = c.agent_id 
        AND DATE(c.call_start_time) = p_date
    WHERE a.team_id = p_team_id AND a.is_active = true
    GROUP BY a.agent_id, a.first_name, a.last_name
    ORDER BY COUNT(c.call_id) DESC;
END;
$ LANGUAGE plpgsql;
```

### **3️⃣ Triggers for Data Integrity**

```sql
-- ===================================
-- TRIGGERS FOR AUTOMATIC ACTIONS
-- ===================================

-- Auto-update updated_at timestamp
CREATE OR REPLACE FUNCTION update_timestamp()
RETURNS TRIGGER AS $
BEGIN
    NEW.updated_at = NOW();
    RETURN NEW;
END;
$ LANGUAGE plpgsql;

CREATE TRIGGER agent_update_timestamp
    BEFORE UPDATE ON agents
    FOR EACH ROW
    EXECUTE FUNCTION update_timestamp();

-- Validate call end time
CREATE OR REPLACE FUNCTION validate_call_times()
RETURNS TRIGGER AS $
BEGIN
    IF NEW.call_end_time IS NOT NULL AND NEW.call_end_time <= NEW.call_start_time THEN
        RAISE EXCEPTION 'Call end time must be after start time';
    END IF;
    RETURN NEW;
END;
$ LANGUAGE plpgsql;

CREATE TRIGGER check_call_times
    BEFORE INSERT OR UPDATE ON calls
    FOR EACH ROW
    EXECUTE FUNCTION validate_call_times();

-- Generate alerts for SLA breaches
CREATE OR REPLACE FUNCTION check_sla_breach()
RETURNS TRIGGER AS $
BEGIN
    -- Check if call duration exceeds 10 minutes (SLA breach)
    IF NEW.call_end_time IS NOT NULL AND 
       NEW.call_duration_seconds > 600 THEN
        
        INSERT INTO alerts (agent_id, alert_type, severity, message, created_time)
        VALUES (
            NEW.agent_id,
            'sla_breach',
            'high',
            'Call duration exceeded SLA: ' || (NEW.call_duration_seconds/60) || ' minutes',
            NOW()
        );
    END IF;
    
    RETURN NEW;
END;
$ LANGUAGE plpgsql;

CREATE TRIGGER sla_breach_alert
    AFTER INSERT OR UPDATE ON calls
    FOR EACH ROW
    EXECUTE FUNCTION check_sla_breach();
```

---

## Slide 14: Redis Integration for Real-time Features

### ⚡ **Redis as Cache & Real-time Layer**

### **Why Redis for Agent Wallboard?**

```
🎯 Real-time Requirements:
├── 📊 Agent status updates every 1-2 seconds
├── 📈 Live dashboard metrics refresh
├── 🚨 Instant alerts and notifications
├── 👥 Active user sessions tracking
└── 🔄 WebSocket connection management
```

### **Redis Data Structures**

```redis
# ===================================
# REDIS SCHEMA DESIGN
# ===================================

# 1. Current Agent Status (Hash)
HSET agent:status:A001 
    status "available"
    since "2024-01-15T09:00:00Z"
    team_id "T001" 
    last_activity "2024-01-15T09:15:30Z"

# 2. Live Call Counters (Hash)
HSET team:stats:T001:today
    total_calls "45"
    completed_calls "38"
    active_calls "3"
    avg_duration "285"
    last_updated "2024-01-15T09:15:30Z"

# 3. Real-time Leaderboard (Sorted Set)
ZADD team:T001:leaderboard:today 
    45 "A001"  # Score = call count, Member = agent_id
    38 "A002" 
    41 "A003"

# 4. Active Sessions (Set)
SADD active:agents "A001" "A002" "A003"
SADD active:supervisors "S001" "S002"

# 5. Alert Queue (List)
LPUSH alerts:urgent '{"agent_id":"A001","type":"sla_breach","time":"2024-01-15T09:15:30Z"}'

# 6. Dashboard Cache (String with JSON)
SET dashboard:team:T001 '{
    "team_name": "Sales Team A",
    "active_agents": 8,
    "total_calls_today": 156,
    "avg_satisfaction": 4.2,
    "current_queue": 3,
    "last_updated": "2024-01-15T09:15:30Z"
}' EX 30  # Expire in 30 seconds
```

### **Redis Operations**

```javascript
// ===================================
// REDIS OPERATIONS (Node.js)
// ===================================

const redis = require('redis');
const client = redis.createClient({
    host: 'localhost',
    port: 6379
});

// Update Agent Status
async function updateAgentStatus(agentId, status, teamId) {
    const statusKey = `agent:status:${agentId}`;
    const timestamp = new Date().toISOString();
    
    await client.hset(statusKey, {
        status: status,
        since: timestamp,
        team_id: teamId,
        last_activity: timestamp
    });
    
    // Add to active agents if available
    if (status === 'available') {
        await client.sadd('active:agents', agentId);
    } else if (status === 'offline') {
        await client.srem('active:agents', agentId);
    }
    
    // Update team stats
    await updateTeamStats(teamId);
    
    // Publish real-time update
    await client.publish('agent_status_update', JSON.stringify({
        agent_id: agentId,
        status: status,
        team_id: teamId,
        timestamp: timestamp
    }));
}

// Get Team Dashboard Data
async function getTeamDashboard(teamId) {
    const cacheKey = `dashboard:team:${teamId}`;
    
    // Try cache first
    const cached = await client.get(cacheKey);
    if (cached) {
        return JSON.parse(cached);
    }
    
    // If not cached, calculate and store
    const dashboard = await calculateTeamDashboard(teamId);
    await client.setex(cacheKey, 30, JSON.stringify(dashboard)); // Cache 30 seconds
    
    return dashboard;
}

// Real-time Leaderboard Update
async function updateLeaderboard(teamId, agentId, callCount) {
    const leaderboardKey = `team:${teamId}:leaderboard:today`;
    
    // Update score
    await client.zadd(leaderboardKey, callCount, agentId);
    
    // Set expiration at end of day
    const tomorrow = new Date();
    tomorrow.setDate(tomorrow.getDate() + 1);
    tomorrow.setHours(0, 0, 0, 0);
    const secondsUntilMidnight = Math.floor((tomorrow - new Date()) / 1000);
    
    await client.expire(leaderboardKey, secondsUntilMidnight);
    
    // Get top 5 for broadcasting
    const topAgents = await client.zrevrange(leaderboardKey, 0, 4, 'WITHSCORES');
    
    // Broadcast update
    await client.publish('leaderboard_update', JSON.stringify({
        team_id: teamId,
        top_agents: topAgents,
        timestamp: new Date().toISOString()
    }));
}
```

---

## Slide 15: Workshop Exercise - Hands-on ER Modeling

### 🛠️ **Workshop: Design Your Agent Wallboard Database**

### **Exercise Setup (30 minutes)**

#### **📋 Scenario Extension:**
**Call Center ABC มีความต้องการเพิ่มเติม:**

```
🎯 New Requirements:
1. 📞 Multiple Call Types: Sales, Support, Billing, VIP
2. 🎓 Training Management: Courses, Certifications, Progress  
3. 🏆 Gamification: Points, Badges, Competitions
4.

-------------------


# ENGSE206 สัปดาห์ที่ 6: การออกแบบข้อมูลและฐานข้อมูล
## Slides 15-25

---

## Slide 15: Normalization Fundamentals
**Title:** Database Normalization - พื้นฐาน

**ทำไมต้อง Normalize?**
🎯 **เป้าหมาย:** ลดความซ้ำซ้อนและปรับปรุงคุณภาพข้อมูล

**📊 ปัญหาของฐานข้อมูลที่ไม่ Normalize:**
- **Data Redundancy** - ข้อมูลซ้ำซ้อน เสียพื้นที่
- **Update Anomalies** - แก้ไขข้อมูลต้องแก้หลายที่
- **Insert Anomalies** - ไม่สามารถเพิ่มข้อมูลได้เมื่อขาดข้อมูลบางส่วน
- **Delete Anomalies** - ลบข้อมูลแล้วเสียข้อมูลที่สำคัญ

**🔧 Normal Forms (ขั้นตอนการ Normalize):**

**1NF (First Normal Form):**
✅ ไม่มี repeating groups
✅ แต่ละ cell มีค่าเดียว (atomic value)
✅ แต่ละ column มี data type เดียวกัน

**2NF (Second Normal Form):**
✅ ต้องอยู่ใน 1NF ก่อน
✅ ไม่มี partial functional dependency
✅ Non-key attributes ต้องขึ้นอยู่กับ primary key ทั้งหมด

**3NF (Third Normal Form):**
✅ ต้องอยู่ใน 2NF ก่อน
✅ ไม่มี transitive dependency
✅ Non-key attributes ไม่ขึ้นอยู่กับ non-key attributes อื่น

---

## Slide 16: Normalization Example - Before & After
**Title:** ตัวอย่างการ Normalize แบบ Step-by-Step

**📝 ตัวอย่าง: ระบบลงทะเบียนเรียน**

**Table ก่อน Normalize (Un-normalized):**
```
StudentCourseInfo
------------------------------------------------------
StudentID | StudentName | CourseID | CourseName | Credits | Professor | ProfEmail
S001     | นายดำ       | CS101    | Programming | 3       | อ.สมใจ    | somjai@uni.ac.th
S001     | นายดำ       | CS102    | Database    | 3       | อ.สมหวัง   | somwang@uni.ac.th
S002     | นางแดง      | CS101    | Programming | 3       | อ.สมใจ    | somjai@uni.ac.th
```

**❌ ปัญหาที่เจอ:**
- StudentName ซ้ำ เมื่อนักศึกษาลงทะเบียนหลายวิชา
- CourseName, Credits ซ้ำ เมื่อหลายคนลงวิชาเดียวกัน
- Professor, ProfEmail ซ้ำ เมื่ออาจารย์สอนหลายวิชา

**✅ หลัง Normalize (3NF):**

**Students Table:**
```
StudentID | StudentName
S001     | นายดำ
S002     | นางแดง
```

**Professors Table:**
```
ProfID | ProfName | ProfEmail
P001   | อ.สมใจ   | somjai@uni.ac.th
P002   | อ.สมหวัง  | somwang@uni.ac.th
```

**Courses Table:**
```
CourseID | CourseName  | Credits | ProfID
CS101    | Programming | 3       | P001
CS102    | Database    | 3       | P002
```

**Enrollments Table:**
```
StudentID | CourseID | EnrollDate
S001     | CS101    | 2025-01-15
S001     | CS102    | 2025-01-15
S002     | CS101    | 2025-01-16
```

---

## Slide 17: SQL vs NoSQL Decision Framework
**Title:** เมื่อไหร่ควรเลือก SQL vs NoSQL?

**🎯 Decision Matrix สำหรับเลือก Database Type:**

**เลือก SQL (Relational) เมื่อ:**
✅ **ACID Compliance สำคัญ** - ธุรกรรมทางการเงิน, e-commerce
✅ **ข้อมูลมี Structure ชัดเจน** - ไม่เปลี่ยนแปลงบ่อย
✅ **ต้องการ Complex Queries** - Join หลายตาราง, aggregation
✅ **มี Existing SQL Skills** ในทีม
✅ **ข้อมูลไม่ใหญ่มาก** - < 10M records

**เลือก NoSQL เมื่อ:**
✅ **Scale ต้องใหญ่มาก** - millions/billions of records
✅ **ข้อมูลไม่มี Fixed Schema** - JSON documents ที่เปลี่ยนแปลงได้
✅ **ต้องการ High Performance** - read/write speed สำคัญ
✅ **Distributed System** - multiple servers, geographic distribution
✅ **Rapid Development** - prototype ได้เร็ว

**📊 เปรียบเทียบ Performance:**

| Criteria | SQL | NoSQL |
|----------|-----|-------|
| **Consistency** | Strong | Eventually |
| **Schema** | Fixed | Flexible |
| **Scalability** | Vertical | Horizontal |
| **Query Language** | Standard SQL | Various APIs |
| **Learning Curve** | Moderate | Varies |

**🏗️ กรณีศึกษา: TaskMaster Pro ใช้ MongoDB เพราะ:**
- ข้อมูล Task มี structure ที่แตกต่างกันตาม project type
- ต้องการ store rich metadata (attachments, comments, history)
- Scale to millions of tasks across organizations
- Real-time collaboration features

---

## Slide 18: MongoDB Document Design Best Practices
**Title:** การออกแบบ Document Structure ใน MongoDB

**🎯 MongoDB Design Principles:**

**1. Embed vs Reference - ตัดสินใจยังไง?**

**Embed เมื่อ:**
✅ ข้อมูลมักถูกอ่านพร้อมกัน
✅ ข้อมูล child ไม่เคยถูกใช้แยกจาก parent
✅ ข้อมูลมีขนาดจำกัด (< 16MB per document)
✅ Update frequency ต่ำ

**Reference เมื่อ:**
✅ ข้อมูลมีขนาดใหญ่ หรือเติบโตได้ไม่จำกัด
✅ ข้อมูลถูกแชร์ระหว่างหลาย documents
✅ ต้องการ query ข้อมูล child แยกต่างหาก
✅ Update บ่อย

**📝 ตัวอย่าง TaskMaster Pro Document Design:**

**Task Document (Embedded Design):**
```json
{
  "_id": ObjectId("..."),
  "title": "Fix login bug",
  "description": "Users cannot login with special characters",
  "projectId": ObjectId("..."),
  "assignee": {
    "userId": ObjectId("..."),
    "name": "นายดำ มืดดิ",
    "email": "dam@company.com"
  },
  "status": "IN_PROGRESS",
  "priority": "HIGH",
  "labels": ["bug", "urgent", "frontend"],
  "dueDate": ISODate("2025-09-15"),
  "comments": [
    {
      "commentId": ObjectId("..."),
      "userId": ObjectId("..."),
      "userName": "นางแดง สีใส",
      "message": "กำลังดูปัญหาอยู่",
      "timestamp": ISODate("2025-09-01T10:30:00Z")
    }
  ],
  "attachments": [
    {
      "fileName": "error-screenshot.png",
      "fileUrl": "https://storage.../error.png",
      "uploadDate": ISODate("2025-09-01T09:15:00Z")
    }
  ],
  "timeTracking": {
    "estimatedHours": 8,
    "loggedHours": 3,
    "sessions": [
      {
        "start": ISODate("2025-09-01T09:00:00Z"),
        "end": ISODate("2025-09-01T12:00:00Z"),
        "description": "Initial investigation"
      }
    ]
  },
  "createdAt": ISODate("2025-09-01T08:00:00Z"),
  "updatedAt": ISODate("2025-09-01T12:00:00Z")
}
```

**💡 Design Rationale:**
- **Embed assignee info** - มักใช้พร้อมกับ task info
- **Embed comments** - จำนวนจำกัด, อ่านพร้อมกับ task
- **Reference projectId** - project ใช้ใน context อื่นด้วย
- **Embed labels array** - ง่ายต่อการ search และ filter

---

## Slide 19: Database Indexing Strategy
**Title:** การออกแบบ Index เพื่อ Performance

**🎯 Indexing เป็นหัวใจของ Database Performance**

**📊 Impact of Proper Indexing:**
- Query speed: จาก seconds → milliseconds
- Resource usage: ลด CPU และ Memory consumption
- User experience: Real-time response

**🔍 Types of Indexes:**

**1. Single Field Index:**
```sql
-- SQL
CREATE INDEX idx_task_status ON tasks(status);

-- MongoDB
db.tasks.createIndex({ "status": 1 })
```
**ใช้เมื่อ:** Query แค่ field เดียว, sort by field เดียว

**2. Compound Index:**
```sql
-- SQL
CREATE INDEX idx_task_project_status ON tasks(projectId, status, dueDate);

-- MongoDB
db.tasks.createIndex({ "projectId": 1, "status": 1, "dueDate": 1 })
```
**ใช้เมื่อ:** Query หลาย fields พร้อมกัน

**3. Text Index (สำหรับ Search):**
```mongodb
// MongoDB Full-text search
db.tasks.createIndex({ 
  "title": "text", 
  "description": "text",
  "comments.message": "text" 
})
```

**🎯 Index Design Strategy for TaskMaster:**

**High-Priority Indexes:**
```json
// 1. Task search by project and status (หน้า Kanban board)
{ "projectId": 1, "status": 1, "createdAt": -1 }

// 2. User's tasks across projects (หน้า My Tasks)
{ "assignee.userId": 1, "dueDate": 1, "priority": -1 }

// 3. Text search across tasks
{ "title": "text", "description": "text" }

// 4. Project analytics queries
{ "projectId": 1, "status": 1, "createdAt": 1 }
```

**⚠️ Index Trade-offs:**
- **อย่าสร้าง index เยอะเกินไป** - ช้าตอน write operations
- **Monitor index usage** - ลบ index ที่ไม่ถูกใช้
- **Consider storage cost** - indexes ใช้ disk space

---

## Slide 20: Database Security & Data Protection
**Title:** ความปลอดภัยและการป้องกันข้อมูล

**🔒 Database Security Fundamentals:**

**1. Access Control:**
```sql
-- SQL: Role-based access control
CREATE ROLE app_readonly;
GRANT SELECT ON tasks TO app_readonly;
GRANT app_readonly TO app_user;

-- MongoDB: Role-based access
db.createRole({
  role: "taskReadOnly",
  privileges: [
    { resource: { db: "taskmaster", collection: "tasks" }, 
      actions: ["find", "listIndexes"] }
  ],
  roles: []
})
```

**2. Data Encryption:**
- **At Rest:** Encrypt database files
- **In Transit:** TLS/SSL connections
- **Application Level:** Sensitive fields (passwords, personal data)

**3. Audit Logging:**
```json
// ตัวอย่าง Audit Log Entry
{
  "timestamp": "2025-09-01T14:30:00Z",
  "user": "api_user",
  "action": "UPDATE",
  "collection": "tasks",
  "documentId": "64f123...",
  "changes": {
    "status": { "from": "TODO", "to": "IN_PROGRESS" }
  },
  "ipAddress": "192.168.1.100"
}
```

**🛡️ Data Protection Strategies:**

**Personal Data Handling (PDPA Compliance):**
```json
// ตัวอย่าง User document with privacy considerations
{
  "_id": ObjectId("..."),
  "email": "user@company.com", // ต้อง encrypt
  "name": "นายสมชาย ใจดี", // pseudonymization option
  "role": "developer",
  "preferences": {
    "notifications": true,
    "timezone": "Asia/Bangkok"
  },
  "dataConsent": {
    "marketing": false,
    "analytics": true,
    "consentDate": ISODate("2025-01-15"),
    "ipAddress": "xxx.xxx.xxx.xxx" // masked
  }
}
```

**Backup & Recovery:**
- **Daily automated backups** - ข้อมูลล่าสุด
- **Point-in-time recovery** - กู้คืนเมื่อเวลาที่เฉพาะเจาะจง
- **Cross-region replication** - disaster recovery
- **Backup testing** - ทดสอบการกู้คืนเป็นประจำ

---

## Slide 21: Workshop Activity - ER Diagram Creation
**Title:** 🛠️ Workshop: สร้าง ER Diagram สำหรับโครงงาน

**📋 Workshop Instructions:**

**วัตถุประสงค์:** สร้าง ER Diagram สำหรับโครงงานของแต่ละทีม

**⏰ เวลา: 25 นาที**
- 5 นาที: ทีมวางแผนและกำหนด entities หลัก
- 15 นาที: สร้าง ER Diagram
- 5 นาที: Review และปรับปรุง

**🎯 ขั้นตอนการทำ:**

**Step 1: ระบุ Entities (5 นาที)**
ให้ทีมระบุ entities หลักจากโครงงาน เช่น:
- User, Product, Order (e-commerce)
- Student, Course, Enrollment (ระบบลงทะเบียน)
- Task, Project, Team Member (project management)

**Step 2: กำหนด Attributes (5 นาที)**
สำหรับแต่ละ entity ให้กำหนด:
- Primary Key (PK)
- Attributes ที่จำเป็น
- Data types โดยคร่าว

**Step 3: สร้าง Relationships (10 นาที)**
- ระบุความสัมพันธ์ระหว่าง entities
- กำหนด cardinality (1:1, 1:N, M:N)
- ระบุ foreign keys

**🛠️ เครื่องมือที่แนะนำ:**
- **ERD Plus** - ฟรี, ใช้งานง่าย
- **Lucidchart** - มีฟีเจอร์เยอะ
- **MySQL Workbench** - สำหรับ SQL database
- **กระดาษ + ปากกา** - สำหรับ brainstorm เร็วๆ

**✅ เกณฑ์การประเมิน:**

**พื้นฐาน (60%):**
- มี entities หลักครบถ้วนตามโครงงาน
- Attributes มี primary key ที่ชัดเจน
- Relationships และ cardinality ถูกต้อง

**กลาง (80%):**
- Data types เหมาะสมกับการใช้งาน
- Foreign keys ระบุได้ถูกต้อง
- ไม่มีความซ้ำซ้อนที่ไม่จำเป็น

**ดี (100%):**
- คำนึงถึง normalization (อย่างน้อย 2NF)
- มี derived attributes หรือ calculated fields
- ใส่ constraints ที่สำคัญ (unique, not null)
- เพิ่มเติม indexes ที่ควรมี

**💡 Tips for Success:**
- เริ่มจาก core functionality ก่อน
- ใช้ naming convention ที่สม่ำเสมอ
- คิดถึง query patterns ที่จะใช้บ่อย
- อย่าลืม audit fields (created_at, updated_at)

---

## Slide 22: Common Database Design Mistakes
**Title:** ❌ ข้อผิดพลาดที่พบบ่อยในการออกแบบ Database

**🚫 Top 10 Database Design Anti-Patterns:**

**1. ไม่ใช้ Primary Key**
```sql
❌ Wrong:
CREATE TABLE tasks (
  title VARCHAR(100),
  description TEXT,
  status VARCHAR(20)
);

✅ Correct:
CREATE TABLE tasks (
  id INT PRIMARY KEY AUTO_INCREMENT,
  title VARCHAR(100) NOT NULL,
  description TEXT,
  status VARCHAR(20) DEFAULT 'TODO'
);
```

**2. ใช้ VARCHAR แทน Appropriate Data Types**
```sql
❌ Wrong:
price VARCHAR(20),  -- "123.45"
created_date VARCHAR(50), -- "2025-09-01 10:30:00"

✅ Correct:
price DECIMAL(10,2),
created_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
```

**3. ไม่ทำ Normalization (หรือ Over-normalization)**
```sql
❌ Denormalized (เก็บ customer info ซ้ำใน orders):
orders: id, customer_name, customer_email, product, price

❌ Over-normalized (แยก address เป็น 5 tables):
addresses, provinces, districts, sub_districts, postal_codes

✅ Balanced:
customers: id, name, email
addresses: id, customer_id, street, city, province, postal_code
orders: id, customer_id, product, price
```

**4. EAV (Entity-Attribute-Value) Pattern Abuse**
```sql
❌ Wrong: ใช้ EAV เมื่อไม่จำเป็น
attributes_table:
entity_id | attribute_name | attribute_value
1        | name          | "John"
1        | email         | "john@email.com"
1        | age           | "25"

✅ Better: ใช้ proper columns
users:
id | name | email           | age
1  | John | john@email.com  | 25
```

**5. ไม่วางแผน Indexing**
```sql
❌ No indexes on frequently queried columns:
SELECT * FROM orders WHERE customer_id = 123 AND status = 'pending';

✅ Proper indexing:
CREATE INDEX idx_orders_customer_status ON orders(customer_id, status);
```

**📊 Performance Impact Examples:**

**Before Optimization:**
```sql
-- Query without index: 2.3 seconds
SELECT * FROM tasks WHERE project_id = 456 AND status = 'TODO'
ORDER BY created_at DESC LIMIT 20;
```

**After Optimization:**
```sql
-- Same query with proper index: 0.003 seconds
CREATE INDEX idx_tasks_project_status_created 
ON tasks(project_id, status, created_at DESC);
```

**🔧 How to Avoid These Mistakes:**

**Development Process:**
1. **Database Review Sessions** - ให้ senior developer review
2. **Performance Testing** - ทดสอบด้วยข้อมูลจริง
3. **Query Analysis** - ใช้ EXPLAIN PLAN ตรวจสอบ query performance
4. **Code Review** - ตรวจสอบ database schema ใน PR

**Tools ที่ช่วยได้:**
- **Database Documentation** - ER diagrams, data dictionary
- **Monitoring Tools** - slow query logs, performance metrics
- **Schema Migration Tools** - version control สำหรับ database changes

---

## Slide 23: Database Performance Optimization
**Title:** 🚀 เทคนิคการปรับปรุง Database Performance

**⚡ Performance Optimization Strategy:**

**1. Query Optimization**

**Before:**
```sql
-- Slow query (no index, inefficient WHERE clause)
SELECT t.*, u.name as assignee_name, p.name as project_name
FROM tasks t 
LEFT JOIN users u ON t.assignee_id = u.id 
LEFT JOIN projects p ON t.project_id = p.id 
WHERE YEAR(t.created_at) = 2025 AND t.status != 'DONE'
ORDER BY t.due_date;
```

**After:**
```sql
-- Optimized query
SELECT t.*, u.name as assignee_name, p.name as project_name
FROM tasks t 
LEFT JOIN users u ON t.assignee_id = u.id 
LEFT JOIN projects p ON t.project_id = p.id 
WHERE t.created_at >= '2025-01-01' 
  AND t.created_at < '2026-01-01'
  AND t.status IN ('TODO', 'IN_PROGRESS', 'REVIEW')
ORDER BY t.due_date;

-- Index สำหรับ query นี้
CREATE INDEX idx_tasks_performance 
ON tasks(created_at, status, due_date);
```

**2. Database-Level Optimizations**

**Connection Pooling:**
```javascript
// Node.js with MongoDB
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost/taskmaster', {
  maxPoolSize: 10, // ไม่เกิน 10 connections
  minPoolSize: 2,  // อย่างน้อย 2 connections
  maxIdleTimeMS: 30000, // close connection หลัง idle 30 วินาที
  bufferMaxEntries: 0
});
```

**Query Result Caching:**
```javascript
// Redis caching example
const redis = require('redis');
const client = redis.createClient();

async function getTasksByProject(projectId) {
  const cacheKey = `tasks:project:${projectId}`;
  
  // ลองเอาจาก cache ก่อน
  const cached = await client.get(cacheKey);
  if (cached) {
    return JSON.parse(cached);
  }
  
  // ถ้าไม่มีใน cache ค่อย query database
  const tasks = await Task.find({ projectId }).populate('assignee');
  
  // เก็บใน cache 5 นาที
  await client.setEx(cacheKey, 300, JSON.stringify(tasks));
  
  return tasks;
}
```

**📊 Monitoring & Metrics:**

**Key Performance Indicators:**
- **Query Response Time** - < 100ms สำหรับ simple queries
- **Connection Pool Usage** - ไม่เกิน 80%
- **Cache Hit Ratio** - > 90%
- **Database CPU/Memory** - < 70% usage

**Database Profiling:**
```sql
-- MySQL: Enable slow query log
SET GLOBAL slow_query_log = 'ON';
SET GLOBAL long_query_time = 0.5; -- queries > 0.5 seconds

-- Monitor slow queries
SELECT * FROM mysql.slow_log 
WHERE start_time > NOW() - INTERVAL 1 DAY
ORDER BY query_time DESC LIMIT 10;
```

**3. Scaling Strategies**

**Read Replicas:**
- Master-Slave setup สำหรับ read-heavy workloads
- ใช้ slave สำหรับ reports และ analytics
- Keep master สำหรับ writes เท่านั้น

**Horizontal Partitioning (Sharding):**
```javascript
// ตัวอย่าง sharding strategy
function getShardKey(userId) {
  // แบ่ง users ออกเป็น 4 shards
  return userId % 4;
}

function getTaskDatabase(userId) {
  const shard = getShardKey(userId);
  return `taskmaster_shard_${shard}`;
}
```

---

## Slide 24: Integration with Application Layer
**Title:** 🔗 การเชื่อมต่อ Database กับ Application

**🏗️ Database Integration Patterns:**

**1. Repository Pattern**
```javascript
// TaskRepository.js - Abstract database operations
class TaskRepository {
  async findByProjectId(projectId, filters = {}) {
    const query = { projectId };
    
    // Apply filters
    if (filters.status) query.status = filters.status;
    if (filters.assigneeId) query['assignee.userId'] = filters.assigneeId;
    if (filters.dueDate) query.dueDate = { $lte: filters.dueDate };
    
    return await Task.find(query)
      .populate('assignee', 'name email')
      .sort({ createdAt: -1 })
      .limit(50);
  }
  
  async updateStatus(taskId, newStatus, userId) {
    const updateData = {
      status: newStatus,
      updatedAt: new Date(),
      'statusHistory': {
        $push: {
          status: newStatus,
          changedBy: userId,
          changedAt: new Date()
        }
      }
    };
    
    return await Task.findByIdAndUpdate(taskId, updateData, { new: true });
  }
}
```

**2. Data Access Layer (DAL)**
```javascript
// TaskService.js - Business logic layer
class TaskService {
  constructor(taskRepository, userService, notificationService) {
    this.taskRepo = taskRepository;
    this.userService = userService;
    this.notificationService = notificationService;
  }
  
  async assignTask(taskId, assigneeId, assignedBy) {
    // Validate permissions
    const canAssign = await this.userService.canAssignTasks(assignedBy);
    if (!canAssign) {
      throw new Error('Insufficient permissions');
    }
    
    // Update task
    const updatedTask = await this.taskRepo.assignUser(taskId, assigneeId);
    
    // Send notification
    await this.notificationService.notifyTaskAssignment(updatedTask);
    
    return updatedTask;
  }
}
```

**📊 Database Connection Best Practices:**

**Environment Configuration:**
```javascript
// config/database.js
const databaseConfig = {
  development: {
    uri: process.env.DB_URI_DEV || 'mongodb://localhost/taskmaster_dev',
    options: {
      maxPoolSize: 5,
      retryWrites: true
    }
  },
  production: {
    uri: process.env.DB_URI_PROD,
    options: {
      maxPoolSize: 20,
      readPreference: 'secondaryPreferred', // ใช้ read replica
      retryWrites: true,
      ssl: true
    }
  }
};
```

**Error Handling & Retry Logic:**
```javascript
async function executeWithRetry(operation, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await operation();
    } catch (error) {
      console.log(`Database operation failed (attempt ${i + 1}):`, error.message);
      
      if (i === maxRetries - 1) throw error; // Last attempt
      
      // Exponential backoff
      await new Promise(resolve => setTimeout(resolve, Math.pow(2, i) * 1000));
    }
  }
}
```

**🔄 Data Synchronization:**

**Event-Driven Updates:**
```javascript
// When task status changes, update related data
taskSchema.post('findOneAndUpdate', async function(doc) {
  if (doc && this.getUpdate().status) {
    // Update project statistics
    await ProjectStats.updateTaskCounts(doc.projectId);
    
    // Send real-time update to clients
    socketService.broadcastTaskUpdate(doc.projectId, doc);
  }
});
```

**Batch Operations:**
```javascript
// Batch update for performance
async function updateMultipleTasks(updates) {
  const bulkOps = updates.map(update => ({
    updateOne: {
      filter: { _id: update.taskId },
      update: { $set: update.changes },
      upsert: false
    }
  }));
  
  return await Task.bulkWrite(bulkOps, { ordered: false });
}
```

---

## Slide 25: Summary & Next Steps
**Title:** สรุป การออกแบบข้อมูลและฐานข้อมูล

**🎯 สิ่งที่เราได้เรียนรู้วันนี้:**

**1. Database Design Fundamentals**
✅ **ER Modeling** - สร้างแบบจำลองข้อมูลที่ถูกต้อง
✅ **Normalization** - ลดความซ้ำซ้อน ปรับปรุงคุณภาพข้อมูล
✅ **Data Relationships** - เข้าใจการเชื่อมโยงระหว่าง entities

**2. SQL vs NoSQL Decision Making**
✅ **เลือกฐานข้อมูลที่เหมาะสม** ตามลักษณะข้อมูลและการใช้งาน
✅ **MongoDB Document Design** - best practices สำหรับ NoSQL
✅ **Trade-offs Analysis** - ข้อดี/ข้อเสียของแต่ละแบบ

**3. Performance & Security**
✅ **Indexing Strategy** - วางแผน indexes เพื่อประสิทธิภาพ
✅ **Security Best Practices** - ป้องกันข้อมูลและควบคุมการเข้าถึง
✅ **Query Optimization** - เทคนิคการเขียน query ที่มีประสิทธิภาพ

**4. Integration Patterns**
✅ **Repository Pattern** - แยก business logic จาก data access
✅ **Connection Management** - จัดการ connection pool อย่างมีประสิทธิภาพ
✅ **Error Handling** - การจัดการข้อผิดพลาดและ retry logic

**📝 Workshop Results Review:**
- ER Diagrams ที่สร้างขึ้นครอบคลุม entities หลักของโครงงาน
- ความสัมพันธ์และ cardinality ถูกต้อง
- คำนึงถึง normalization และ performance considerations

**🏆 Key Takeaways สำหรับการออกแบบจริง:**

**💡 Design Principles:**
1. **Start Simple** - เริ่มจาก core entities ก่อน
2. **Think in Queries** - ออกแบบตาม usage patterns
3. **Plan for Scale** - คิดถึงการเติบโตของข้อมูล
4. **Document Everything** - เก็บ ER diagrams และ data dictionary

**⚠️ Common Pitfalls to Avoid:**
- Over-normalization หรือ under-normalization
- ไม่วางแผน indexing strategy
- ขาด backup และ recovery plan
- ไม่ monitor database performance

**📚 Required Reading สำหรับสัปดาห์หน้า:**
1. **"UML Modeling Fundamentals"** - Chapter 7-8
2. **"RESTful API Design Principles"** - Online resource
3. **"Software Architecture Patterns"** - Chapter 3: Layered Architecture

**📋 Assignment Due Next Week:**

**Individual Assignment: Database Design Document**
- ER Diagram สำหรับโครงงานของท่าน (ใช้เครื่องมือ ERD Plus หรือ Lucidchart)
- Database Schema (tables/collections พร้อม data types)
- Normalization ถึงอย่างน้อย 3NF (สำหรับ SQL) หรือ Document Design Rationale (สำหรับ NoSQL)
- Index Strategy พร้อมเหตุผล
- 8-12 หน้า PDF format

**Submission Details:**
- Upload ไฟล์ PDF ไป LMS ภายในวันอาทิตย์ 23:59 น.
- ชื่อไฟล์: `DatabaseDesign_StudentID_ProjectName.pdf`
- Include source files (.erdplus หรือ .lucid) ในไฟล์ zip แยกต่างหาก

**🔮 Next Week Preview: "Low-Level Design & UML Modeling"**

**สิ่งที่จะได้เรียน:**
- **Class Diagram** - ออกแบบโครงสร้างของ components
- **Sequence Diagram** - modeling การทำงานของระบบ
- **API Design** - RESTful API specification
- **Design Principles** - Coupling, Cohesion, Abstraction

**🛠️ Tools to Prepare:**
- **StarUML** หรือ **Lucidchart** สำหรับ UML diagrams
- **Postman** สำหรับ API testing
- **Swagger Editor** สำหรับ API documentation

**❓ Q&A - คำถามที่พบบ่อย:**

**Q: MongoDB กับ MySQL เลือกยังไงสำหรับโครงงาน startup?**
A: **MySQL** ถ้าทีมคุ้นเคยกับ SQL, ข้อมูลมี structure ชัดเจน. **MongoDB** ถ้าต้องการ rapid prototyping, ข้อมูลมี flexibility สูง, หรือต้อง scale horizontally

**Q: Normalization ทำถึงไหนพอ?**
A: **3NF เพียงพอสำหรับส่วนใหญ่** - ลดความซ้ำซ้อนโดยไม่ซับซ้อนเกินไป. BCNF หรือสูงกว่านั้นใช้เฉพาะกรณีพิเศษ

**Q: Index ควรสร้างกี่อัน?**
A: **เริ่มจาก high-impact queries** - queries ที่รันบ่อยและใช้เวลานาน. Monitor usage แล้วค่อยเพิ่ม. หลีกเลี่ยงการสร้าง index เยอะเกินไปเพราะจะช้าตอน write

**Q: การ backup database ทำยังไง?**
A: **Automated daily backups** + **weekly full backups** + **test recovery process** เป็นประจำ. สำหรับ production ควรมี **cross-region backup** ด้วย

**Q: NoSQL จะ replace SQL หมดมั้ย?**
A: **ไม่** - แต่ละแบบมีจุดแข็งต่างกัน. **SQL** ยังคงดีสำหรับ transactional systems, complex reporting. **NoSQL** เหมาะกับ big data, real-time applications, rapid development

**🎉 ขอบคุณสำหรับการมีส่วนร่วมในวันนี้!**

**Remember:** Database design เป็นพื้นฐานสำคัญ - ออกแบบดีตั้งแต่ต้นจะช่วยประหยัดเวลาและปัญหาในอนาคต!

**See you next week สำหรับ UML และ Low-Level Design! 🚀**











