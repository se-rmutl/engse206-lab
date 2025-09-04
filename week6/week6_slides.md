# สัปดาห์ที่ 6: Design Patterns และ Architectural Patterns
## Agent Wallboard System - ENGSE206 มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา (ดอยสะเก็ด)

---

## Slide 1: 🎯 วัตถุประสงค์และเป้าหมายการเรียนรู้

### 📚 วัตถุประสงค์
- เข้าใจแนวคิด Design Patterns และประโยชน์ในการพัฒนาซอฟต์แวร์
- เลือกใช้ Design Patterns ที่เหมาะสมกับระบบ Real-time Communication
- ออกแบบ Component Architecture ด้วย Patterns สำหรับ Agent Wallboard System

### 🎯 เป้าหมายการเรียนรู้
- วิเคราะห์ปัญหาในระบบและเลือก Pattern ที่เหมาะสม
- ประยุกต์ใช้ Patterns ในการออกแบบระบบ Real-time
- เตรียมความพร้อมสำหรับการออกแบบ Component ในสัปดาห์หน้า

### 📊 ผลที่คาดหวัง
- สามารถระบุและแก้ไขปัญหาการออกแบบด้วย Design Patterns
- ออกแบบระบบที่มีโครงสร้างดีและบำรุงรักษาง่าย
- สร้าง Pattern Implementation Plan สำหรับ Agent Wallboard System

---

## Slide 2: 📚 ทบทวนสัปดาห์ที่แล้ว

### จากหลักการออกแบบสู่การนำไปใช้จริง

**สัปดาห์ที่ 5:**
- หลักการ SOLID, DRY, KISS, YAGNI
- 3-Tier Architecture
- C4 Model (C1-C2)

**สัปดาห์นี้ (ที่ 6):**
- **Design Patterns** = เครื่องมือแก้ปัญหาเฉพาะ
- Patterns สำหรับ Real-time Systems
- การประยุกต์ใช้ใน Agent Wallboard System

**สัปดาห์หน้า (ที่ 7):**
- Component Design ด้วย Patterns
- C3 Level Architecture Design

---

## Slide 3: 🔍 Agent Wallboard System - ปัญหาที่ต้องแก้

### ปัญหาหลักในการพัฒนา

**1. 🔌 Connection Management**
- จัดการ WebSocket connections จำนวนมาก (50-500 agents)
- ป้องกัน memory leak และ connection overflow

**2. 📨 Message Types ที่หลากหลาย**
- Status Update, Chat Message, System Alert
- แต่ละประเภทมี format และการจัดการต่างกัน

**3. ⚡ Real-time Updates**
- Agent เปลี่ยนสถานะ → แจ้ง Supervisor ทันที
- หลายส่วนต้องได้รับข้อมูลพร้อมกัน

**4. 🔐 Multiple Authentication Methods**
- Local Authentication (username/password)
- SSO (Single Sign-On)
- ต้องรองรับและเปลี่ยนได้ง่าย

**💡 Design Patterns จะช่วยแก้ปัญหาเหล่านี้อย่างเป็นระบบ!**

---

## Slide 4: 💭 Design Patterns คืออะไร?

### เปรียบเทียบง่ายๆ

**🍳 การทำอาหาร**
- **สูตรอาหาร** = Design Pattern
- **วัตถุดิบ** = Objects/Classes
- **จานที่ได้** = Software ที่ทำงานได้

**ตัวอย่าง:**
- **สูตรผัดไทย** → ใช้ได้กับวัตถุดิบต่างๆ (หมู/กุ้ง/ไก่)
- **สูตรต้มยำ** → ปรับรสได้ (เปรียว/หวาน)

**🎯 ประโยชน์:**
- ไม่ต้องคิดใหม่ทุกครั้ง
- วิธีการที่ได้รับการพิสูจน์แล้ว
- ทีมเข้าใจกันได้ง่าย

---

## Slide 5: 📊 ประเภทของ Design Patterns

### 3 กลุ่มหลัก

**1. 🏭 Creational Patterns (การสร้าง)**
- จัดการการสร้าง objects
- **ตัวอย่าง:** Singleton, Factory
- **ใช้กับ:** Connection Manager, Message Creation

**2. 🏗️ Structural Patterns (การจัดโครงสร้าง)**
- จัดความสัมพันธ์ระหว่าง objects
- **ตัวอย่าง:** Adapter, Facade
- **ใช้กับ:** Database Integration, API Simplification

**3. 🎭 Behavioral Patterns (การจัดการพฤติกรรม)**
- จัดการการสื่อสารระหว่าง objects
- **ตัวอย่าง:** Observer, Strategy
- **ใช้กับ:** Real-time Updates, Authentication

---

## Slide 6: 🏭 Singleton Pattern - หนึ่งเดียวในระบบ

### เปรียบเทียบกับชีวิตจริง

**🏢 CEO ของบริษัท:**
- บริษัทมี CEO เพียงคนเดียว
- ทุกแผนกรายงานไปที่ CEO คนเดียวกัน
- ไม่มี CEO สองคนในเวลาเดียวกัน

**💻 ใน Agent Wallboard System:**

**WebSocket Connection Manager**
- มีตัวจัดการ WebSocket เพียงตัวเดียว
- รับผิดชอบการเชื่อมต่อของ Agent ทุกคน
- ประหยัด resource และป้องกัน conflicts

**Database Connection Pool**
- คลังเชื่อมต่อ database เดียว
- ทุก component ใช้คลังเดียวกัน
- ควบคุมจำนวนการเชื่อมต่อ

**🟢 ข้อดี:** ประหยัด resource, จัดการง่าย
**🔴 ข้อเสีย:** ถ้าพัง กระทบทั้งระบบ

---

## Slide 7: 🏭 Factory Pattern - โรงงานผลิตสินค้า

### เปรียบเทียบกับร้านอาหาร

**🍕 ร้านพิซซ่า:**
- ลูกค้าสั่ง "พิซซ่าแฮม" → ได้พิซซ่าแฮม
- ลูกค้าสั่ง "พิซซ่าไก่" → ได้พิซซ่าไก่
- ลูกค้าไม่ต้องรู้วิธีทำ

**💻 ใน Agent Wallboard System:**

**Message Factory**
- ต้องการ "Status Update" → สร้าง StatusMessage
- ต้องการ "Chat Message" → สร้าง ChatMessage
- ต้องการ "System Alert" → สร้าง AlertMessage

**ประโยชน์:**
- เพิ่ม message type ใหม่ได้ง่าย
- จัดการ format ที่แตกต่างกัน
- ลดความซับซ้อนในการสร้าง objects

**🟢 ข้อดี:** เพิ่ม type ใหม่ง่าย, จัดการรวมศูนย์
**🔴 ข้อเสีย:** อาจซับซ้อนเกินไปกับงานง่ายๆ

---

## Slide 8: 🏗️ Adapter Pattern - ตัวแปลง

### เปรียบเทียบกับปลั๊กแปลง

**🔌 ปลั๊กไฟ:**
- หูฟัง iPhone (Lightning) + Android (USB-C)
- ใช้ตัวแปลง Lightning-to-USB-C
- หูฟัง iPhone ใช้กับ Android ได้

**💻 ใน Agent Wallboard System:**

**Database Adapter**
- ระบบเก่า: MSSQL (SQL commands)
- ระบบใหม่: MongoDB (NoSQL documents)
- Database Adapter แปลงคำสั่งให้เข้ากัน

**API Adapter**
- External System ส่ง XML
- ระบบเราต้องการ JSON
- API Adapter แปลง XML → JSON

**🟢 ข้อดี:** ระบบเก่าใหม่ทำงานร่วมกัน, ไม่ต้องเขียนใหม่
**🔴 ข้อเสีย:** เพิ่มความซับซ้อน, performance อาจช้า

---

## Slide 9: 🏗️ Facade Pattern - หน้าต่างเดียว

### เปรียบเทียบกับแผนกต้อนรับ

**🏦 ธนาคาร:**
- **ปกติ:** ต้องไป แคชเชียร์ → แผนกสินเชื่อ → แผนก IT
- **มี Facade:** ไปแผนกต้อนรับ → เขาจัดการให้หมด

**💻 ใน Agent Wallboard System:**

**Dashboard API Facade**
- Frontend ต้องการข้อมูล Dashboard
- จริงๆ ต้องเรียก: Agent Service + Status Service + Alert Service
- Facade รวมทุกอย่างเป็น getDashboardData()

**Authentication Facade**
- การ login ซับซ้อน: ตรวจ username → password → สร้าง session
- Facade ทำให้เรียกแค่ login(username, password)

**🟢 ข้อดี:** ใช้งานง่าย, ซ่อนความซับซ้อน
**🔴 ข้อเสีย:** อาจลด flexibility

---

## Slide 10: 🎭 Observer Pattern - ระบบแจ้งข่าว

### เปรียบเทียบกับ Social Media

**📱 Facebook:**
- เรา Follow เพจข่าว = เป็น Observer
- เพจโพสต์ข่าวใหม่ = Subject เปลี่ยนแปลง
- เราได้ notification = Observer ได้รับแจ้งเตือน

**💻 ใน Agent Wallboard System:**

**Agent Status Broadcasting**
- **Subject:** Agent (คนที่เปลี่ยนสถานะ)
- **Observers:** Supervisor Dashboard, Manager Report
- **เมื่อ Agent เปลี่ยน Available → Busy:**
  - Dashboard แสดงสีแดงทันที
  - Report บันทึกเวลา

**System Alert Broadcasting**
- **Subject:** Alert System
- **Observers:** Admin Panel, Email Service, SMS Service
- **เมื่อระบบมีปัญหา:** แจ้งทุกช่องทางพร้อมกัน

**🟢 ข้อดี:** Real-time updates, ไม่ต้อง polling
**🔴 ข้อเสีย:** อาจมี observers เยอะเกินไป

---

## Slide 11: 🎭 Strategy Pattern - หลายวิธีหนึ่งเป้าหมาย

### เปรียบเทียบกับ GPS Navigation

**🗺️ เส้นทางไปงาน:**
- **เป้าหมาย:** จากบ้านไปออฟฟิศ
- **หลายวิธี:** ทางด่วน (เร็ว), ถนนธรรมดา (ฟรี), เลียบแม่น้ำ (วิวสวย)
- **เลือกตามสถานการณ์:** เช้าใช้ทางด่วน, เย็นใช้ถนนธรรมดา

**💻 ใน Agent Wallboard System:**

**Authentication Strategies**
- **เป้าหมาย:** ผู้ใช้เข้าระบบได้
- **หลายวิธี:**
  - Local: username/password
  - SSO: Single Sign-On token
  - LDAP: องค์กรใหญ่
- **เลือกตามบริษัท:** SME ใช้ Local, Enterprise ใช้ SSO

**Payment Strategies (ถ้าระบบมี billing)**
- Credit Card, PayPal, Bank Transfer
- เลือกตามความสะดวกของลูกค้า

**🟢 ข้อดี:** เปลี่ยนวิธีได้ง่าย, เพิ่มวิธีใหม่ได้
**🔴 ข้อเสีย:** เพิ่ม classes เยอะ

---

## Slide 12: ⚡ Publisher-Subscriber Pattern

### สำหรับระบบ Real-time

**📺 เปรียบเทียบกับสถานีวิทยุ:**
- **สถานีวิทยุ** = Publisher (ส่งสัญญาณ)
- **วิทยุในรถ** = Subscriber (รับสัญญาณ)
- **คลื่นความถี่** = Channel

**💻 ใน Agent Wallboard System:**

**Event Broadcasting**
- **Publisher:** Agent Status Service
- **Subscribers:** 
  - Supervisor Dashboard
  - Manager Reports
  - Team Leader Screen
- **Channel:** WebSocket Events

**การทำงาน:**
1. Agent เปลี่ยนสถานะ
2. Status Service publish event
3. ทุก subscriber ได้รับ notification พร้อมกัน

**🟢 ข้อดี:** Scalable, Decoupled, Real-time
**🔴 ข้อเสีย:** Network overhead, Message ordering

---

## Slide 13: 🔄 Circuit Breaker Pattern

### ป้องกันระบบล่มแบบลูกโซ่

**🏠 เปรียบเทียบกับเบรกเกอร์ไฟ:**
- **ปกติ:** ไฟไหลผ่านได้
- **ไฟลัดวงจร:** เบรกเกอร์ตัดไฟทันที
- **ป้องกันไฟไหม้:** ไม่ให้กระแสเกินไหลผ่าน
- **แก้ไขแล้ว:** รีเซ็ตเพื่อเปิดใหม่

**💻 ใน Agent Wallboard System:**

**Database Connection Resilience**
- **ปกติ:** เชื่อมต่อ database ได้
- **Database ล่ม:** Circuit Breaker เปิด (ตัดการเชื่อมต่อ)
- **ใช้ Cache:** แสดงข้อมูลล่าสุดจาก memory
- **Database กลับมา:** รีเซ็ตให้เชื่อมต่อใหม่

**States:**
- **CLOSED:** ปกติ, ส่งคำขอผ่าน
- **OPEN:** มีปัญหา, ไม่ส่งคำขอ
- **HALF-OPEN:** ทดสอบว่าหายดีแล้วหรือยัง

**🟢 ข้อดี:** ป้องกันระบบล่ม, Auto recovery
**🔴 ข้อเสีย:** ซับซ้อน, ต้อง monitor

---

## Slide 14: 🎯 Pattern Selection สำหรับ Agent Wallboard

### เลือก Pattern อย่างไรให้เหมาะสม

**🔍 การวิเคราะห์ปัญหา:**

| ปัญหา | Pattern ที่เหมาะสม | เหตุผล |
|-------|-------------------|--------|
| จัดการ WebSocket connections | **Singleton** | ต้องการตัวจัดการเดียว |
| สร้าง message หลายประเภท | **Factory** | แต่ละ type ต่างกัน |
| เชื่อมต่อ MSSQL + MongoDB | **Adapter** | API ต่างกัน |
| Dashboard API ซับซ้อน | **Facade** | ซ่อนความซับซ้อน |
| Real-time status updates | **Observer** | หลายจุดต้องรับข้อมูล |
| หลายวิธี authentication | **Strategy** | เปลี่ยนวิธีได้ |
| Event broadcasting | **Pub-Sub** | ส่งหลาย subscribers |
| Database ล่มบ่อย | **Circuit Breaker** | ป้องกันล่มลูกโซ่ |

**🎯 Agent Wallboard System Architecture:**
```
┌─── Singleton (WebSocket Manager)
├─── Factory (Message Creation)
├─── Adapter (Database Integration)  
├─── Facade (API Simplification)
├─── Observer (Status Broadcasting)
├─── Strategy (Authentication)
└─── Circuit Breaker (Resilience)
```

---

## Slide 15: 📋 Implementation Strategy

### วางแผนการพัฒนาทีละขั้น

**Phase 1: Core Infrastructure**
- **Singleton:** WebSocket Manager, Database Pool
- **Factory:** Message Factory
- **เป้าหมาย:** ระบบพื้นฐานทำงานได้

**Phase 2: Integration Layer**
- **Adapter:** Database Adapter (MSSQL ↔ MongoDB)
- **Facade:** Dashboard API, Authentication API
- **เป้าหมาย:** เชื่อมต่อระบบต่างๆ ได้

**Phase 3: Real-time Features**
- **Observer:** Status Broadcasting
- **Publisher-Subscriber:** Event System
- **เป้าหมาย:** Real-time updates ทำงานได้

**Phase 4: Resilience & Flexibility**
- **Strategy:** Multiple Authentication Methods
- **Circuit Breaker:** Database Resilience
- **เป้าหมาย:** ระบบมั่นคงและยืดหยุ่น

---

## Slide 16: 🛠️ Workshop: Pattern Design Exercise

### กิจกรรมออกแบบ Patterns

**🎯 แบ่งกลุ่ม 4-5 คน:**

**สถานการณ์:** ระบบห้องสมุดอัจฉริยะ
- นักเรียนค้นหาหนังสือผ่านแอป
- มีหนังสือหลายประเภท: นิยาย, วิชาการ, การ์ตูน
- เมื่อมีหนังสือใหม่ → แจ้งผู้ที่สนใจ
- รองรับการค้นหาหลายวิธี: ชื่อ, ผู้แต่ง, หมวด
- เชื่อมต่อกับห้องสมุดอื่นๆ

**คำถาม:**
1. ควรใช้ Pattern อะไรบ้าง?
2. เพราะอะไร?
3. วาดแผนภาพแสดงความสัมพันธ์

**⏰ เวลา:** 15 นาที อภิปราย + 10 นาที นำเสนอ

---

## Slide 17: 💡 Workshop Solution

### เฉลยกิจกรรม

**Patterns ที่ควรใช้:**

**1. Observer Pattern**
- แจ้งผู้สนใจเมื่อมีหนังสือใหม่
- Subscribers: นักเรียนที่สนใจหมวดนั้น

**2. Factory Pattern**
- สร้าง objects สำหรับหนังสือแต่ละประเภท
- BookFactory.create("novel", data)

**3. Strategy Pattern**
- วิธีค้นหาหลากหลาย (ชื่อ, ผู้แต่ง, หมวด)
- SearchStrategy: ByTitle, ByAuthor, ByCategory

**4. Adapter Pattern**
- เชื่อมต่อกับห้องสมุดอื่น
- แต่ละห้องสมุดมี API ต่างกัน

**5. Facade Pattern**
- API ค้นหาที่ซับซ้อน → SearchFacade.search()

---

## Slide 18: 📊 Benefits Analysis

### ประโยชน์ของการใช้ Patterns

**📈 ในระยะสั้น:**
- **โค้ดเป็นระเบียบ** มากขึ้น
- **ทีมเข้าใจ** กันได้ง่าย
- **แก้ไขปัญหา** เฉพาะจุดได้

**📈 ในระยะยาว:**
- **บำรุงรักษา** ง่ายขึ้น
- **เพิ่ม feature** ใหม่ได้เร็ว
- **ขยายระบบ** ได้ดีกว่า

**📊 ROI (Return on Investment):**
- **ลงทุน:** เวลาเรียนรู้ Patterns
- **ผลตอบแทน:** ประหยัดเวลาพัฒนาและ maintain
- **Break-even:** ประมาณ 3-6 เดือน

**⚠️ ข้อควรระวัง:**
- อย่าใช้ Pattern เพื่อใช้
- เลือกให้เหมาะกับปัญหา
- อย่า over-engineering

---

## Slide 19: 🎬 สรุปการเรียนรู้

### สิ่งสำคัญที่ได้เรียนรู้

**🔑 Key Takeaways:**

**1. Design Patterns = เครื่องมือแก้ปัญหา**
- ไม่ใช่ศาสนา แต่เป็นเครื่องมือ
- ใช้เมื่อมีปัญหาจริง

**2. 3 ประเภทหลัก:**
- **Creational:** จัดการการสร้าง objects
- **Structural:** จัดระเบียบความสัมพันธ์
- **Behavioral:** จัดการการสื่อสาร

**3. Patterns สำหรับ Real-time Systems:**
- **Observer:** สำหรับ real-time updates
- **Publisher-Subscriber:** สำหรับ broadcasting
- **Circuit Breaker:** สำหรับ resilience

**4. Pattern Selection Process:**
- วิเคราะห์ปัญหาก่อน
- เลือก Pattern ที่เหมาะสม
- พิจารณาความซับซ้อนที่เพิ่มขึ้น

**🚀 เตรียมพร้อมสำหรับสัปดาห์หน้า:**
Component Architecture Design!

---

## Slide 20: 📋 การประเมินผล และ Assignment

### 📊 การประเมินผล (10% ของคะแนนรวม)

**Assignment: Design Patterns Implementation Strategy**

**📝 รายละเอียดงาน:**
1. **วิเคราะห์ Agent Wallboard System** (40 คะแนน)
   - ระบุปัญหาที่ต้องแก้ด้วย Patterns
   - เลือก Patterns ที่เหมาะสม พร้อมเหตุผล

2. **ออกแบบ Implementation Plan** (40 คะแนน)
   - วางแผนการพัฒนาเป็น phases
   - กำหนด timeline และ priorities

3. **สร้าง Pattern Relationship Diagram** (20 คะแนน)
   - แสดงความสัมพันธ์ระหว่าง Patterns
   - อธิบายการทำงานร่วมกัน

**📅 กำหนดส่ง:** สัปดาห์หน้าก่อนเรียน
**📄 รูปแบบ:** PDF 3-5 หน้า พร้อม diagrams

**💡 เกณฑ์การให้คะแนน:**
- ความถูกต้องของ Pattern selection
- ความสมเหตุสมผลของ implementation plan
- ความชัดเจนของ diagrams และคำอธิบาย

**🚀 Next Week Preview:**
สัปดาห์หน้าจะเรียนเรื่อง Component Architecture Design โดยใช้ Patterns ที่เรียนวันนี้!