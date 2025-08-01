# Software Requirements Specification (SRS)
## ระบบจองห้องประชุม MeetingRoom Lite

**Document ID:** SRS-MRL-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2567  
**สถานะ:** Final  
**จัดทำโดย:** ทีมวิศวกรรมซอฟต์แวร์  

---

## Revision History

| Version | วันที่ | ผู้แก้ไข | รายละเอียด |
|---------|--------|----------|-------------|
| 0.1 | 01/03/2567 | ทีมพัฒนา | ร่างเอกสารเบื้องต้น |
| 0.5 | 05/03/2567 | ทีมพัฒนา | เพิ่ม functional requirements |
| 0.8 | 08/03/2567 | ทีมพัฒนา | เพิ่ม use cases |
| 1.0 | 10/03/2567 | ทีมพัฒนา | เอกสารฉบับสมบูรณ์ |

---

## สารบัญ

1. [บทนำ (Introduction)](#1-บทนำ-introduction)
   - 1.1 [วัตถุประสงค์ (Purpose)](#11-วัตถุประสงค์-purpose)
   - 1.2 [ขอบเขต (Scope)](#12-ขอบเขต-scope)
   - 1.3 [คำนิยาม คำย่อ และตัวย่อ (Definitions, Acronyms, and Abbreviations)](#13-คำนิยาม-คำย่อ-และตัวย่อ)
   - 1.4 [เอกสารอ้างอิง (References)](#14-เอกสารอ้างอิง-references)
   - 1.5 [ภาพรวม (Overview)](#15-ภาพรวม-overview)

2. [คำอธิบายโดยรวม (Overall Description)](#2-คำอธิบายโดยรวม-overall-description)
   - 2.1 [มุมมองผลิตภัณฑ์ (Product Perspective)](#21-มุมมองผลิตภัณฑ์-product-perspective)
   - 2.2 [ฟังก์ชันของผลิตภัณฑ์ (Product Functions)](#22-ฟังก์ชันของผลิตภัณฑ์-product-functions)
   - 2.3 [ลักษณะผู้ใช้ (User Characteristics)](#23-ลักษณะผู้ใช้-user-characteristics)
   - 2.4 [ข้อจำกัด (Constraints)](#24-ข้อจำกัด-constraints)
   - 2.5 [สมมติฐานและการพึ่งพา (Assumptions and Dependencies)](#25-สมมติฐานและการพึ่งพา-assumptions-and-dependencies)

3. [ความต้องการเฉพาะ (Specific Requirements)](#3-ความต้องการเฉพาะ-specific-requirements)
   - 3.1 [ความต้องการด้านหน้าที่ (Functional Requirements)](#31-ความต้องการด้านหน้าที่-functional-requirements)
   - 3.2 [ความต้องการที่ไม่ใช่ด้านหน้าที่ (Non-functional Requirements)](#32-ความต้องการที่ไม่ใช่ด้านหน้าที่-non-functional-requirements)
   - 3.3 [ความต้องการด้าน Interface ภายนอก (External Interface Requirements)](#33-ความต้องการด้าน-interface-ภายนอก-external-interface-requirements)

4. [Use Cases](#4-use-cases)
   - 4.1 [Use Case Diagram](#41-use-case-diagram)
   - 4.2 [Use Case Descriptions](#42-use-case-descriptions)

5. [ภาคผนวก (Appendices)](#5-ภาคผนวก-appendices)

---

## 1. บทนำ (Introduction)

### 1.1 วัตถุประสงค์ (Purpose)

เอกสาร Software Requirements Specification (SRS) ฉบับนี้มีวัตถุประสงค์เพื่อกำหนดความต้องการทั้งหมดของระบบจองห้องประชุม MeetingRoom Lite สำหรับองค์กรขนาดเล็กถึงขนาดกลาง เอกสารนี้จะเป็นข้อตกลงระหว่างผู้พัฒนาและผู้มีส่วนได้ส่วนเสีย (stakeholders) เกี่ยวกับสิ่งที่ระบบจะทำ

### 1.2 ขอบเขต (Scope)

**ชื่อซอฟต์แวร์:** MeetingRoom Lite  
**ประเภท:** Web Application

**สิ่งที่ระบบจะทำ:**
- อนุญาตให้ผู้ใช้ลงทะเบียนและเข้าสู่ระบบ
- แสดงรายการห้องประชุมและสถานะ
- อนุญาตให้ผู้ใช้จองห้องประชุม
- ป้องกันการจองซ้ำซ้อน
- อนุญาตให้ผู้ใช้ดูและยกเลิกการจองของตนเอง
- อนุญาตให้ผู้ดูแลระบบจัดการข้อมูลห้อง

**สิ่งที่ระบบจะไม่ทำ:**
- ไม่มีระบบการแจ้งเตือนทาง email
- ไม่มีการเชื่อมต่อกับระบบปฏิทิน
- ไม่มีการจองแบบประจำ (recurring bookings)
- ไม่มีระบบการชำระเงิน

### 1.3 คำนิยาม คำย่อ และตัวย่อ

| คำศัพท์ | คำอธิบาย |
|---------|----------|
| **User** | ผู้ใช้ทั่วไปที่สามารถจองห้องได้ |
| **Admin** | ผู้ดูแลระบบที่มีสิทธิ์จัดการข้อมูลห้อง |
| **Booking** | การจองห้องประชุมในช่วงเวลาที่กำหนด |
| **Room** | ห้องประชุมที่สามารถจองได้ |
| **Session** | ช่วงเวลาที่ผู้ใช้เข้าสู่ระบบ |
| **SRS** | Software Requirements Specification |

### 1.4 เอกสารอ้างอิง (References)

1. IEEE Std 830-1998 - IEEE Recommended Practice for Software Requirements Specifications
2. นโยบายการใช้ห้องประชุมขององค์กร

### 1.5 ภาพรวม (Overview)

เอกสารนี้ประกอบด้วย 5 ส่วนหลัก:
- ส่วนที่ 1: บทนำ
- ส่วนที่ 2: คำอธิบายโดยรวมของระบบ
- ส่วนที่ 3: ความต้องการเฉพาะ
- ส่วนที่ 4: Use Cases
- ส่วนที่ 5: ภาคผนวก

---

## 2. คำอธิบายโดยรวม (Overall Description)

### 2.1 มุมมองผลิตภัณฑ์ (Product Perspective)

MeetingRoom Lite เป็นระบบ web application แบบ standalone ที่ไม่ต้องเชื่อมต่อกับระบบอื่น ระบบจะทำงานผ่าน web browser และเก็บข้อมูลในฐานข้อมูลของตัวเอง

### 2.2 ฟังก์ชันของผลิตภัณฑ์ (Product Functions)

ฟังก์ชันหลักของระบบ:
1. **การจัดการผู้ใช้** - ลงทะเบียน, เข้าสู่ระบบ, ออกจากระบบ
2. **การดูข้อมูลห้อง** - แสดงรายการห้อง, ดูสถานะห้อง
3. **การจองห้อง** - สร้างการจอง, ตรวจสอบความพร้อม
4. **การจัดการการจอง** - ดูการจองของตนเอง, ยกเลิกการจอง
5. **การดูแลระบบ** - จัดการข้อมูลห้อง (เฉพาะ admin)

### 2.3 ลักษณะผู้ใช้ (User Characteristics)

**ผู้ใช้ทั่วไป (Regular Users)**
- จำนวน: ประมาณ 100-200 คน
- ทักษะ: ใช้คอมพิวเตอร์พื้นฐานได้
- ความถี่: ใช้งาน 2-3 ครั้งต่อสัปดาห์

**ผู้ดูแลระบบ (Administrators)**
- จำนวน: 2-3 คน
- ทักษะ: มีความรู้ด้าน IT
- ความถี่: ใช้งานทุกวัน

### 2.4 ข้อจำกัด (Constraints)

1. **ข้อจำกัดด้านเวลา** - ต้องพัฒนาให้เสร็จภายใน 1 เดือน
2. **ข้อจำกัดด้านเทคโนโลยี** - ต้องใช้ open source software เท่านั้น
3. **ข้อจำกัดด้านบุคลากร** - ทีมพัฒนามีนักศึกษา 1-2 คน
4. **ข้อจำกัดด้านงบประมาณ** - ไม่มีงบประมาณสำหรับซื้อ software

### 2.5 สมมติฐานและการพึ่งพา (Assumptions and Dependencies)

**สมมติฐาน:**
- ผู้ใช้ทุกคนมี email address
- องค์กรมีอินเทอร์เน็ตที่เสถียร
- มีห้องประชุมอย่างน้อย 5 ห้อง

**การพึ่งพา:**
- ต้องมี web server สำหรับ deploy
- ต้องมี database server
- ผู้ใช้ต้องมี web browser ที่รองรับ

---

## 3. ความต้องการเฉพาะ (Specific Requirements)

### 3.1 ความต้องการด้านหน้าที่ (Functional Requirements)

#### FR-001: การลงทะเบียนผู้ใช้
**คำอธิบาย:** ระบบต้องอนุญาตให้ผู้ใช้ใหม่ลงทะเบียนด้วย email และ password  
**ระดับความสำคัญ:** สูง  
**Acceptance Criteria:**
- ระบบต้องตรวจสอบรูปแบบ email ที่ถูกต้อง
- Password ต้องมีความยาวอย่างน้อย 6 ตัวอักษร
- ไม่อนุญาตให้ใช้ email ที่ซ้ำกับที่มีอยู่แล้ว

#### FR-002: การเข้าสู่ระบบ
**คำอธิบาย:** ระบบต้องอนุญาตให้ผู้ใช้เข้าสู่ระบบด้วย email และ password  
**ระดับความสำคัญ:** สูง  
**Acceptance Criteria:**
- ระบบต้องตรวจสอบ email และ password
- หากถูกต้อง ระบบต้องสร้าง session
- หากไม่ถูกต้อง ระบบต้องแสดงข้อความแสดงข้อผิดพลาด

#### FR-003: การดูรายการห้องประชุม
**คำอธิบาย:** ระบบต้องแสดงรายการห้องประชุมทั้งหมด  
**ระดับความสำคัญ:** สูง  
**Acceptance Criteria:**
- แสดงชื่อห้อง ความจุ และสถานที่
- แสดงสถานะว่าง/ไม่ว่าง
- สามารถกรองตามวันที่และเวลาได้

#### FR-004: การจองห้องประชุม
**คำอธิบาย:** ระบบต้องอนุญาตให้ผู้ใช้จองห้องประชุม  
**ระดับความสำคัญ:** สูง  
**Acceptance Criteria:**
- ผู้ใช้ต้องระบุวันที่ เวลาเริ่ม เวลาสิ้นสุด และหัวข้อการประชุม
- ระบบต้องตรวจสอบว่าห้องว่างในช่วงเวลานั้น
- ระบบต้องป้องกันการจองซ้ำซ้อน
- จองได้ล่วงหน้าไม่เกิน 30 วัน

#### FR-005: การดูการจองของตนเอง
**คำอธิบาย:** ระบบต้องแสดงรายการการจองของผู้ใช้  
**ระดับความสำคัญ:** กลาง  
**Acceptance Criteria:**
- แสดงการจองที่กำลังจะมาถึง
- แสดงการจองในอดีต
- แสดงรายละเอียดการจอง

#### FR-006: การยกเลิกการจอง
**คำอธิบาย:** ระบบต้องอนุญาตให้ผู้ใช้ยกเลิกการจองของตนเอง  
**ระดับความสำคัญ:** กลาง  
**Acceptance Criteria:**
- ยกเลิกได้เฉพาะการจองในอนาคต
- ต้องยกเลิกล่วงหน้าอย่างน้อย 1 ชั่วโมง
- ระบบต้องขอการยืนยันก่อนยกเลิก

#### FR-007: การจัดการข้อมูลห้อง (Admin)
**คำอธิบาย:** ระบบต้องอนุญาตให้ admin จัดการข้อมูลห้อง  
**ระดับความสำคัญ:** กลาง  
**Acceptance Criteria:**
- สามารถเพิ่ม แก้ไข ลบห้องได้
- ไม่สามารถลบห้องที่มีการจองอยู่
- สามารถเปลี่ยนสถานะห้องได้

### 3.2 ความต้องการที่ไม่ใช่ด้านหน้าที่ (Non-functional Requirements)

#### NFR-001: ประสิทธิภาพ (Performance)
- ระบบต้องแสดงหน้าเว็บภายใน 3 วินาที
- ระบบต้องรองรับผู้ใช้พร้อมกัน 50 คน
- การค้นหาต้องแสดงผลภายใน 2 วินาที

#### NFR-002: ความปลอดภัย (Security)
- Password ต้องเข้ารหัสก่อนเก็บในฐานข้อมูล
- ระบบต้องใช้ HTTPS
- Session ต้องหมดอายุหลังไม่มีกิจกรรม 30 นาที

#### NFR-003: ความสามารถในการใช้งาน (Usability)
- ผู้ใช้ใหม่ต้องสามารถจองห้องได้ภายใน 5 นาที
- ระบบต้องมี interface ที่เข้าใจง่าย
- ระบบต้องแสดงข้อความแสดงข้อผิดพลาดที่ชัดเจน

#### NFR-004: ความเข้ากันได้ (Compatibility)
- ต้องรองรับ Chrome, Firefox, Safari เวอร์ชันล่าสุด
- ต้องแสดงผลได้ดีบนหน้าจอขนาด 1024x768 ขึ้นไป
- ต้องเป็น responsive design

#### NFR-005: ความน่าเชื่อถือ (Reliability)
- ระบบต้องมี uptime อย่างน้อย 95%
- ต้องมีการ backup ข้อมูลทุกวัน
- ต้องกู้คืนระบบได้ภายใน 24 ชั่วโมง

### 3.3 ความต้องการด้าน Interface ภายนอก (External Interface Requirements)

#### User Interfaces
- ระบบต้องมี web-based user interface
- ต้องใช้งานผ่าน standard web browser
- ต้องรองรับทั้ง desktop และ mobile

#### Hardware Interfaces
- ไม่ต้องการ hardware พิเศษ
- ใช้งานผ่าน standard computer หรือ mobile device

#### Software Interfaces
- ต้องทำงานร่วมกับ PostgreSQL database
- ต้องทำงานบน Node.js runtime

#### Communications Interfaces
- ใช้ HTTP/HTTPS protocol
- ใช้ RESTful API สำหรับ communication
- Data format เป็น JSON

---

## 4. Use Cases

### 4.1 Use Case Diagram

```
                    MeetingRoom Lite System
       ┌──────────────────────────────────────────┐
       │                                          │
       │    ○ UC-01: Register                    │
       │    │                                     │
       │    ○ UC-02: Login                       │
       │    │                                     │
       │    ○ UC-03: View Rooms                  │
       │    │                                     │
User ──┼────○ UC-04: Book Room                   │
       │    │                                     │
       │    ○ UC-05: View My Bookings            │
       │    │                                     │
       │    ○ UC-06: Cancel Booking              │
       │    │                                     │
       │    │                                     │
Admin ─┼────○ UC-07: Manage Rooms                │
       │                                          │
       └──────────────────────────────────────────┘
```

### 4.2 Use Case Descriptions

#### UC-01: Register
**Primary Actor:** User  
**Preconditions:** ผู้ใช้ยังไม่มีบัญชี  
**Main Flow:**
1. ผู้ใช้เข้าหน้าลงทะเบียน
2. ผู้ใช้กรอก email, password, และชื่อ
3. ระบบตรวจสอบข้อมูล
4. ระบบสร้างบัญชีใหม่
5. ระบบแสดงข้อความสำเร็จ

**Alternative Flow:**
- 3a. ข้อมูลไม่ถูกต้อง: ระบบแสดงข้อผิดพลาด
- 3b. Email ซ้ำ: ระบบแสดงว่า email นี้ถูกใช้แล้ว

**Postconditions:** ผู้ใช้มีบัญชีใหม่ในระบบ

#### UC-02: Login
**Primary Actor:** User  
**Preconditions:** ผู้ใช้มีบัญชีแล้ว  
**Main Flow:**
1. ผู้ใช้เข้าหน้า login
2. ผู้ใช้กรอก email และ password
3. ระบบตรวจสอบข้อมูล
4. ระบบสร้าง session
5. ระบบนำผู้ใช้ไปหน้าหลัก

**Alternative Flow:**
- 3a. ข้อมูลไม่ถูกต้อง: ระบบแสดงข้อผิดพลาด

**Postconditions:** ผู้ใช้เข้าสู่ระบบและมี active session

#### UC-03: View Rooms
**Primary Actor:** User  
**Preconditions:** ผู้ใช้ login แล้ว  
**Main Flow:**
1. ผู้ใช้เลือกดูรายการห้อง
2. ระบบแสดงรายการห้องทั้งหมด
3. ผู้ใช้สามารถกรองตามวันที่และเวลา
4. ระบบแสดงสถานะห้อง

**Postconditions:** ผู้ใช้เห็นรายการห้องและสถานะ

#### UC-04: Book Room
**Primary Actor:** User  
**Preconditions:** ผู้ใช้ login แล้ว  
**Main Flow:**
1. ผู้ใช้เลือกห้องที่ต้องการ
2. ผู้ใช้เลือกวันที่และเวลา
3. ผู้ใช้กรอกหัวข้อการประชุม
4. ระบบตรวจสอบความว่าง
5. ระบบบันทึกการจอง
6. ระบบแสดงข้อความยืนยัน

**Alternative Flow:**
- 4a. ห้องไม่ว่าง: ระบบแสดงข้อผิดพลาด

**Postconditions:** การจองถูกบันทึกในระบบ

#### UC-05: View My Bookings
**Primary Actor:** User  
**Preconditions:** ผู้ใช้ login แล้ว  
**Main Flow:**
1. ผู้ใช้เลือกดูการจองของตนเอง
2. ระบบแสดงรายการการจองทั้งหมด
3. ผู้ใช้สามารถดูรายละเอียด

**Postconditions:** ผู้ใช้เห็นการจองของตนเอง

#### UC-06: Cancel Booking
**Primary Actor:** User  
**Preconditions:** ผู้ใช้มีการจองในอนาคต  
**Main Flow:**
1. ผู้ใช้เลือกการจองที่ต้องการยกเลิก
2. ผู้ใช้กดปุ่มยกเลิก
3. ระบบขอการยืนยัน
4. ผู้ใช้ยืนยันการยกเลิก
5. ระบบยกเลิกการจอง
6. ระบบแสดงข้อความสำเร็จ

**Alternative Flow:**
- 3a. เวลาใกล้เกินไป: ระบบแสดงว่าไม่สามารถยกเลิกได้

**Postconditions:** การจองถูกยกเลิก

#### UC-07: Manage Rooms
**Primary Actor:** Admin  
**Preconditions:** ผู้ใช้เป็น admin  
**Main Flow:**
1. Admin เข้าหน้าจัดการห้อง
2. Admin สามารถเพิ่ม/แก้ไข/ลบห้อง
3. ระบบบันทึกการเปลี่ยนแปลง

**Alternative Flow:**
- 2a. ลบห้องที่มีการจอง: ระบบแสดงข้อผิดพลาด

**Postconditions:** ข้อมูลห้องถูกอัพเดท

---

## 5. ภาคผนวก (Appendices)

### ภาคผนวก A: การวิเคราะห์ความเสี่ยง

| ความเสี่ยง | ความน่าจะเป็น | ผลกระทบ | การป้องกัน |
|-----------|--------------|---------|-----------|
| เวลาไม่พอ | สูง | สูง | จัดลำดับความสำคัญ features |
| ทีมขาดประสบการณ์ | ปานกลาง | ปานกลาง | ศึกษาเพิ่มเติม, ขอคำแนะนำ |
| ระบบล่ม | ต่ำ | สูง | ทำ backup, มีแผนกู้คืน |

### ภาคผนวก B: อภิธานศัพท์

| คำศัพท์ | คำอธิบาย |
|---------|----------|
| Booking Conflict | การจองที่ซ้อนทับกันในห้องและเวลาเดียวกัน |
| Session Timeout | การหมดอายุของการเข้าสู่ระบบ |
| Responsive Design | การออกแบบที่ปรับตัวตามขนาดหน้าจอ |

---

**หมายเหตุ:** เอกสารนี้เป็น living document ที่อาจมีการแก้ไขตามความเหมาะสม