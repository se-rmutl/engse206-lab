# 🏛️ ENGSE206: สัปดาห์ที่ 7 การออกแบบสถาปัตยกรรมซอฟต์แวร์ - พื้นฐาน

ยินดีต้อนรับนักศึกษาวิศวกรรมซอฟต์แวร์ทุกคนเข้าสู่สัปดาห์ที่ 7 ของวิชา ENGSE206 ครับ สัปดาห์นี้เราจะลงลึกจากภาพใหญ่ (High-Level Architecture) ที่เรียนในสัปดาห์ที่ 5-6 มาสู่การออกแบบในระดับ **Component** ซึ่งเป็นหัวใจสำคัญที่เชื่อมระหว่างสถาปัตยกรรมกับการลงมือเขียนโค้ดจริง

---

## 📑 เอกสารประกอบการเรียน (Lecture Materials)

นักศึกษาสามารถคลิกเพื่ออ่านเนื้อหาฉบับเต็มของแต่ละส่วนได้ที่นี่:

* **[Part 1: Component คืออะไร และ C4 Model Level 3](./part1.md)**: ทบทวนความรู้จากสัปดาห์ก่อน, รู้จักกับ Component, และการแบ่งส่วนประกอบในระดับ C3 ของ Agent Wallboard System
* **[Part 2: หลักการออกแบบ Component และรูปแบบการสื่อสาร](./part2.md)**: เจาะลึกหลักการ High Cohesion, Loose Coupling, Dependency Injection และ Communication Patterns ที่สำคัญ
* **[Part 3: การสร้าง C3 Component Diagram และ Anti-Patterns](./part3.md)**: ตัวอย่างการสร้าง C3 Diagram อย่างละเอียดสำหรับแต่ละส่วนของระบบ, การวิเคราะห์ Dependencies และข้อควรระวัง
* **[Part 4: Workshop, Assessment และการเตรียมตัว](./part4.md)**: แนวทางการทำ Workshop, เกณฑ์การประเมินผล, รายละเอียดงานที่มอบหมาย และการเตรียมตัวสำหรับสัปดาห์หน้า

#### **C4 Model**
* **[C4 Model Complete Guide: จาก C1 ไป C2 ไป C3](./c4-models)**: แนวทางการทำ Agent Wallboard System - การออกแบบสถาปัตยกรรมซอฟต์แวร์แบบเป็นขั้นตอน

---

## 🎯 สรุปเนื้อหาสำคัญ (Key Concepts)

หลังจากที่เราได้เรียนรู้เกี่ยวกับ **C4 Model** ในระดับ Context (C1) และ Container (C2) ไปแล้ว ในสัปดาห์นี้เราจะโฟกัสที่ **Level 3: Component Diagram** ซึ่งเป็นการ "ซูมอิน" เข้าไปในแต่ละ Container เพื่อดูว่ามีส่วนประกอบย่อยอะไรบ้างที่ทำงานร่วมกัน

### 1. Component คืออะไร? 🧩

**Component** คือหน่วยย่อยของซอฟต์แวร์ที่มีหน้าที่รับผิดชอบเฉพาะเจาะจง สามารถทำงานได้ค่อนข้างอิสระ และสื่อสารกับ Component อื่นๆ ผ่าน **Interface** ที่ชัดเจน

> **เปรียบเทียบง่ายๆ:** ถ้า Container คือ "บ้าน" 🏠, Component ก็คือ "ห้องต่างๆ" 🛋️ เช่น ห้องครัว (จัดการเรื่องอาหาร), ห้องนอน (จัดการเรื่องการพักผ่อน) ซึ่งแต่ละห้องมีหน้าที่ของตัวเอง แต่ทำงานร่วมกันเพื่อให้บ้านสมบูรณ์

### 2. หลักการออกแบบ Component ที่ดี (Component Design Principles)

การออกแบบ Component ที่ดีจะทำให้ระบบของเราดูแลรักษาง่าย (Maintainable), ทดสอบง่าย (Testable) และขยายความสามารถได้ในอนาคต (Scalable) โดยมี 2 หลักการที่สำคัญที่สุดคือ:

#### **✅ High Cohesion (ความสอดคล้องภายในสูง)**
คือการที่ส่วนต่างๆ **ภายใน** Component เดียวกัน ทำงานร่วมกันเพื่อเป้าหมายเดียว ไม่สะเปะสะปะ

* **ตัวอย่างที่ดี (High Cohesion):** `AuthenticationComponent` จะมีแค่ฟังก์ชัน `login()`, `logout()`, `validateSession()` ซึ่งทั้งหมดเกี่ยวข้องกับการยืนยันตัวตน
* **ตัวอย่างที่ไม่ดี (Low Cohesion):** `MixedComponent` ที่มีทั้ง `login()`, `sendMessage()`, `generateReport()` ปะปนกัน ทำให้แก้ไขและทดสอบได้ยาก

#### **✅ Loose Coupling (การพึ่งพากันต่ำ)**
คือการที่ Component **พึ่งพา** Component อื่นให้น้อยที่สุด การเปลี่ยนแปลงใน Component หนึ่ง ไม่ควรส่งผลกระทบเป็นวงกว้างไปยังส่วนอื่นๆ

* **ตัวอย่างที่ดี (Loose Coupling):** `AuthenticationService` ไม่ผูกติดกับ Database ชนิดใดชนิดหนึ่ง แต่เรียกใช้งานผ่าน `DatabaseAdapter` (Interface) ทำให้เราเปลี่ยนจาก MSSQL ไปเป็น MongoDB ได้โดยไม่ต้องแก้ไข `AuthenticationService` เลย
* **ตัวอย่างที่ไม่ดี (Tight Coupling):** `AuthenticationService` เขียนโค้ดเชื่อมต่อกับ MSSQL โดยตรง หากต้องการเปลี่ยน Database ก็ต้องตามไปแก้โค้ดทั้งหมด

### 3. รูปแบบการสื่อสารระหว่าง Component (Component Communication Patterns)

เพื่อให้ Component มีความเป็นอิสระและยืดหยุ่น เรานิยมใช้รูปแบบการสื่อสารเหล่านี้:

* **Dependency Injection (DI):** เป็นเทคนิคสำคัญเพื่อให้เกิด Loose Coupling โดยการ "ฉีด" หรือส่ง Dependencies (สิ่งที่ Component ต้องการใช้) เข้าไปจากภายนอก แทนที่จะให้ Component สร้างขึ้นมาเอง
* **Event-Driven Architecture:** Component หนึ่งจะ "ประกาศ" (Publish) เหตุการณ์ (Event) ออกไปเมื่อมีอะไรเกิดขึ้น และ Component อื่นๆ ที่ "ติดตาม" (Subscribe) เหตุการณ์นั้นอยู่ก็จะทำงานต่อ ทำให้ผู้ประกาศไม่จำเป็นต้องรู้จักผู้รับโดยตรง
* **API Gateway Pattern:** เป็นประตูหน้าด่าน (Single Entry Point) สำหรับการสื่อสารจากภายนอก (เช่น Frontend) เข้ามายัง Backend Services ช่วยจัดการเรื่อง Security, Logging, และ Routing ในที่เดียว
* **CQRS (Command Query Responsibility Segregation):** เป็นการแยกส่วนของการ **เขียน/เปลี่ยนแปลงข้อมูล (Command)** ออกจากการ **อ่าน/ดึงข้อมูล (Query)** อย่างชัดเจน เพื่อให้สามารถปรับปรุงประสิทธิภาพ (Optimize) ของแต่ละส่วนได้เต็มที่

---

## 🚀 การประยุกต์ใช้กับ Case Study: Agent Wallboard System

ในสัปดาห์นี้ เราได้นำหลักการข้างต้นมาออกแบบ **C3 Component Diagram** สำหรับระบบ Agent Wallboard ของเรา โดยแบ่งออกเป็น 3 Containers หลักตามสถาปัตยกรรม 3-Tier

### 1. Frontend Components (Desktop App & Supervisor Dashboard)
* **Authentication Component:** จัดการ Login/Logout
* **Status Management Component:** จัดการสถานะ Agent
* **Real-time Notification Component:** แสดงการแจ้งเตือน
* **Dashboard Visualization Component:** แสดงผลกราฟและข้อมูล Real-time

### 2. Backend Components (API Server)
* **Authentication Service:** ตรวจสอบสิทธิ์และจัดการ Session
* **Agent Status Service:** จัดการ Logic การเปลี่ยนสถานะ
* **WebSocket Manager:** หัวใจของการสื่อสารแบบ Real-time
* **Event Bus Component:** ตัวกลางในการส่ง Event ระหว่าง Service เพื่อให้เกิด Loose Coupling
* **Database Access Layer:** ส่วนที่ติดต่อกับฐานข้อมูล

### 3. Data Tier Components (Database)
* **MSSQL Component:** เก็บข้อมูลหลัก (Master Data) เช่น ข้อมูล Agent, Team
* **MongoDB Component:** เก็บข้อมูลที่เกิดขึ้นบ่อยและรวดเร็ว (Real-time Data) เช่น Status Logs, Message History



---

## 🛠️ กิจกรรมและงานที่มอบหมาย (Workshop & Assignment)

* **Workshop:** เราได้ลงมือปฏิบัติ สร้าง C3 Component Diagram และออกแบบ Interface Specifications สำหรับ Container ที่แต่ละกลุ่มได้รับผิดชอบ
* **Assignment:** ให้นักศึกษานำความรู้ทั้งหมดมาประยุกต์ใช้ในการออกแบบ **Complete Component Architecture Design** สำหรับระบบ Agent Wallboard ทั้งระบบ ส่งในสัปดาห์ถัดไป (ดูรายละเอียดใน `class_plan.md` และ `part4.md`)

## 🔑 สรุปประเด็นสำคัญ (Key Takeaways)

1.  **Component Design คือสะพาน:** เป็นขั้นตอนที่เชื่อมระหว่างภาพใหญ่ของสถาปัตยกรรม (C1, C2) ไปสู่การออกแบบโค้ด (C4)
2.  **Interface is King:** การออกแบบ Interface ที่ดี คือหัวใจของการสร้างระบบที่ยืดหยุ่นและดูแลรักษาง่าย
3.  **High Cohesion, Loose Coupling:** ท่องไว้ให้ขึ้นใจ! สองหลักการนี้จะทำให้นักศึกษาเป็น Software Engineer ที่มีคุณภาพ
4.  **Patterns for Scalability:** การใช้ Event-Driven, API Gateway, และ CQRS จะช่วยให้ระบบของเรารองรับการเติบโตในอนาคตได้

## 📚 เตรียมตัวสำหรับสัปดาห์ถัดไป

ในสัปดาห์ที่ 8 เราจะ "ซูมอิน" กันต่อใน **C4 Model Level 4 (Code)** ซึ่งเราจะลงลึกถึงการออกแบบ **Class Diagrams, Sequence Diagrams** และ **API Specifications** เพื่อเตรียมพร้อมสำหรับการลงมือ Implementation ต่อไป ขอให้นักศึกษาทบทวนเรื่อง UML และ REST API มาล่วงหน้าครับ

ขอให้สนุกกับการออกแบบครับ!
**อ.ธนิต เกตุแก้ว**
*สาขาวิชาวิศวกรรมซอฟต์แวร์*
*มทร.ล้านนา (ดอยสะเก็ด)*