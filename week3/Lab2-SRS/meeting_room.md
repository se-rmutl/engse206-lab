# Software Requirements Specification (SRS)
## MeetingRoom Pro - ระบบจองห้องประชุมออนไลน์
**Version:** 1.0  
**Date:** มีนาคม 2024  
**Team:** Software Engineering Students  

---

## Table of Contents

1. [Introduction](#1-introduction)
   - 1.1 Purpose
   - 1.2 Scope
   - 1.3 Definitions, Acronyms, and Abbreviations
   - 1.4 References
   - 1.5 Overview

2. [Overall Description](#2-overall-description)
   - 2.1 Product Perspective
   - 2.2 Product Functions
   - 2.3 User Characteristics
   - 2.4 Constraints
   - 2.5 Assumptions and Dependencies

3. [Specific Requirements](#3-specific-requirements)
   - 3.1 Functional Requirements
   - 3.2 Non-functional Requirements

4. [Use Cases and User Stories](#4-use-cases-and-user-stories)
   - 4.1 Use Case Diagram
   - 4.2 Detailed Use Cases
   - 4.3 User Stories

5. [Validation and Verification](#5-validation-and-verification)
   - 5.1 Acceptance Criteria
   - 5.2 Traceability Matrix

---

## 1. Introduction

### 1.1 Purpose
เอกสารนี้มีจุดประสงค์เพื่อระบุความต้องการทั้งหมดสำหรับระบบ MeetingRoom Pro ซึ่งเป็นระบบจองห้องประชุมออนไลน์สำหรับองค์กรขนาดกลางถึงใหญ่ เอกสารนี้มีไว้สำหรับ:
- ทีมพัฒนาซอฟต์แวร์
- ผู้จัดการโครงการ
- ผู้ใช้งานระบบ (พนักงานและผู้จัดการ)
- ผู้บริหารองค์กร

### 1.2 Scope
**ชื่อผลิตภัณฑ์:** MeetingRoom Pro

**สิ่งที่ระบบจะทำ:**
- จัดการการจองห้องประชุมแบบออนไลน์
- แสดงสถานะห้องประชุมแบบ real-time
- ส่งการแจ้งเตือนและยืนยันการจอง
- จัดการข้อมูลผู้ใช้และสิทธิ์การเข้าถึง
- สร้างรายงานการใช้งานห้องประชุม

**สิ่งที่ระบบจะไม่ทำ:**
- ระบบ video conferencing
- การจัดการงบประมาณและการเงิน
- ระบบ HR หรือ payroll

**ประโยชน์:**
- ลดเวลาในการจองห้องประชุมจาก 15 นาที เหลือ 2 นาที
- ป้องกันการจองซ้ำซ้อน 100%
- เพิ่มประสิทธิภาพการใช้งานห้องประชุม 30%

### 1.3 Definitions, Acronyms, and Abbreviations

| คำศัพท์ | ความหมาย |
|---------|-----------|
| User | ผู้ใช้งานระบบที่มีบัญชีผู้ใช้ |
| Admin | ผู้ดูแลระบบที่มีสิทธิ์ในการจัดการระบบ |
| Booking | การจองห้องประชุมในช่วงเวลาที่กำหนด |
| Room | ห้องประชุมที่สามารถจองได้ |
| Session | ช่วงเวลาที่ผู้ใช้ล็อกอินเข้าระบบ |
| API | Application Programming Interface |
| UI | User Interface |
| DB | Database |

### 1.4 References
- IEEE Std 830-1998: IEEE Recommended Practice for Software Requirements Specifications
- ISO/IEC 25010:2011 - Software Quality Model
- องค์กรตัวอย่าง - Company Meeting Room Policy v2.1

### 1.5 Overview
เอกสารนี้แบ่งออกเป็น 5 ส่วนหลัก โดยส่วนที่ 2 จะอธิบายภาพรวมของระบบ ส่วนที่ 3 จะระบุความต้องการโดยละเอียด ส่วนที่ 4 จะแสดง use cases และ user stories และส่วนที่ 5 จะอธิบายกระบวนการ validation

---

## 2. Overall Description

### 2.1 Product Perspective
MeetingRoom Pro เป็นระบบใหม่ที่พัฒนาขึ้นเป็นอิสระ ซึ่งจะทำงานเป็น web application และมี mobile app สำหรับการใช้งาน

**System Interfaces:**
- การเชื่อมต่อกับระบบ LDAP/Active Directory เพื่อ user authentication
- การเชื่อมต่อกับระบบ email สำหรับการส่งการแจ้งเตือน
- การเชื่อมต่อกับระบบ calendar (Outlook, Google Calendar)

**User Interfaces:**
- Web application สำหรับ desktop/laptop
- Mobile application สำหรับ iOS และ Android
- Admin dashboard สำหรับการจัดการระบบ

**Hardware Interfaces:**
- เซิร์ฟเวอร์สำหรับ hosting application
- Database server สำหรับเก็บข้อมูล

### 2.2 Product Functions
**ฟังก์ชันหลัก:**
1. **การจัดการผู้ใช้** - สมัครสมาชิก, ล็อกอิน, จัดการโปรไฟล์
2. **การจองห้องประชุม** - ค้นหา, จอง, แก้ไข, ยกเลิกการจอง
3. **การแจ้งเตือน** - อีเมล, push notification, SMS
4. **การจัดการห้องประชุม** - เพิ่ม, แก้ไข, ลบห้องประชุม
5. **รายงาน** - สถิติการใช้งาน, รายงานการจอง

### 2.3 User Characteristics

**Primary Users - พนักงานทั่วไป (80% ของผู้ใช้)**
- อายุ: 25-45 ปี
- ความเชี่ยวชาญด้านเทคโนโลยี: ปานกลางถึงสูง
- ใช้งาน: 2-3 ครั้งต่อสัปดาห์
- ความต้องการ: ความรวดเร็ว, ความง่าย

**Secondary Users - ผู้จัดการและหัวหน้าทีม (15% ของผู้ใช้)**
- อายุ: 30-50 ปี
- ความเชี่ยวชาญด้านเทคโนโลยี: ปานกลาง
- ใช้งาน: 5-10 ครั้งต่อสัปดาห์
- ความต้องการ: รายงาน, การจัดการทีม

**Admin Users - ผู้ดูแลระบบ (5% ของผู้ใช้)**
- อายุ: 25-40 ปี
- ความเชี่ยวชาญด้านเทคโนโลยี: สูง
- ใช้งาน: ทุกวัน
- ความต้องการ: การควบคุม, การจัดการ, รายงาน

### 2.4 Constraints
**ข้อจำกัดด้านเทคโนโลยี:**
- ต้องทำงานบน web browsers: Chrome, Firefox, Safari, Edge
- Mobile app ต้องรองรับ iOS 12+ และ Android 8+
- ต้องใช้ HTTPS สำหรับการสื่อสารทั้งหมด

**ข้อจำกัดด้านนโยบาย:**
- ต้องปฏิบัติตามกฎระเบียบการรักษาความปลอดภัยข้อมูลของบริษัท
- ต้องสามารถ backup ข้อมูลได้ทุกวัน
- ต้องเก็บ log การใช้งานไว้อย่างน้อย 1 ปี

**ข้อจำกัดด้านฮาร์ดแวร์:**
- เซิร์ฟเวอร์ต้องมี uptime อย่างน้อย 99.5%
- Database ต้องสามารถรองรับ concurrent users อย่างน้อย 200 คน

### 2.5 Assumptions and Dependencies
**สมมติฐาน:**
- ผู้ใช้มี email address ที่ใช้งานได้
- องค์กรมีระบบ network ที่เสถียร
- ผู้ใช้มีความรู้พื้นฐานในการใช้งาน web application

**Dependencies:**
- การเชื่อมต่อกับระบบ LDAP ของบริษัท
- การใช้งาน third-party email service (SendGrid หรือ AWS SES)
- การใช้งาน cloud hosting service (AWS หรือ Azure)

---

## 3. Specific Requirements

### 3.1 Functional Requirements

#### REQ-F001: User Registration and Authentication
**Description:** ระบบต้องอนุญาตให้ผู้ใช้สามารถสมัครสมาชิกและเข้าสู่ระบบได้อย่างปลอดภัย

**Priority:** High  
**Source:** Business Requirements Document v1.2  
**Rationale:** จำเป็นสำหรับการควบคุมการเข้าถึงและการรักษาความปลอดภัยของระบบ

**Detailed Requirements:**
- ระบบต้องอนุญาตให้ผู้ใช้สมัครสมาชิกด้วย email address ที่ถูกต้อง
- ระบบต้องส่ง verification email ภายใน 2 นาทีหลังจากการสมัครสมาชิก
- ระบบต้องรองรับการ login ด้วย username/password และ Single Sign-On (SSO)
- ระบบต้อง lock account หลังจากพยายาม login ผิด 5 ครั้งติดต่อกัน

**Acceptance Criteria:**
```
Given ผู้ใช้ใหม่เข้ามาในระบบ
When กรอกข้อมูลสมัครสมาชิกด้วย email ที่ถูกต้อง
Then ระบบแสดงข้อความ "Registration successful" 
And ส่ง verification email ภายใน 2 นาที
And ผู้ใช้สามารถ activate account ได้ภายใน 24 ชั่วโมง

Given ผู้ใช้ที่ verified แล้ว
When login ด้วย username และ password ที่ถูกต้อง
Then ระบบนำผู้ใช้เข้าสู่ dashboard หลัก
And สร้าง session ที่มีอายุ 8 ชั่วโมง

Given ผู้ใช้พยายาม login ผิด
When ใส่ password ผิด 5 ครั้งติดต่อกัน
Then ระบบ lock account เป็นเวลา 30 นาที
And ส่ง email แจ้งเตือนถึงเจ้าของ account
```

**Dependencies:** REQ-NF001 (Security Requirements)

---

#### REQ-F002: Room Search and Availability Check
**Description:** ระบบต้องให้ผู้ใช้สามารถค้นหาห้องประชุมที่ว่างตามเงื่อนไขที่กำหนด

**Priority:** High  
**Source:** User Requirements Workshop  
**Rationale:** เป็นฟังก์ชันหลักที่ผู้ใช้ต้องการเพื่อค้นหาห้องที่เหมาะสม

**Detailed Requirements:**
- ระบบต้องแสดงรายการห้องประชุมทั้งหมดพร้อมสถานะ real-time
- ระบบต้องให้ผู้ใช้กรองผลการค้นหาตาม: วันที่, เวลา, ขนาดห้อง, อุปกรณ์
- ระบบต้องแสดงผลการค้นหาภายใน 3 วินาที
- ระบบต้องอัปเดตสถานะห้องแบบ real-time (ทุก 30 วินาที)

**Acceptance Criteria:**
```
Given ผู้ใช้อยู่ในหน้า room search
When เลือกวันที่และช่วงเวลาที่ต้องการ
Then ระบบแสดงรายการห้องที่ว่างในช่วงเวลานั้น
And แสดงรายละเอียดห้อง (ขนาด, อุปกรณ์, รูปภาพ)
And ผลการค้นหาแสดงภายใน 3 วินาที

Given มีการจองห้องใหม่จากผู้ใช้อื่น
When ผู้ใช้อยู่ในหน้า search results
Then สถานะห้องอัปเดตแบบอัตโนมัติ
And ห้องที่ถูกจองจะไม่แสดงในผลการค้นหา
```

**Dependencies:** REQ-F003 (Room Booking)

---

#### REQ-F003: Room Booking and Management  
**Description:** ระบบต้องให้ผู้ใช้สามารถจองห้องประชุม แก้ไข และยกเลิกการจองได้

**Priority:** High  
**Source:** Business Requirements Document v1.2  
**Rationale:** เป็นฟังก์ชันหลักของระบบที่ตอบสนองต่อความต้องการหลักของผู้ใช้

**Detailed Requirements:**
- ระบบต้องให้ผู้ใช้สามารถจองห้องได้ทั้งแบบ instant และ advance (สูงสุด 30 วันล่วงหน้า)
- ระบบต้องตรวจสอบความขัดแย้งของการจองและป้องกันการ double booking
- ระบบต้องให้ผู้ใช้สามารถแก้ไขการจองได้อย่างน้อย 2 ชั่วโมงก่อนเวลาที่จอง
- ระบบต้องให้ผู้ใช้สามารถยกเลิกการจองได้อย่างน้อย 1 ชั่วโมงก่อนเวลาที่จอง

**Acceptance Criteria:**
```
Given ผู้ใช้เลือกห้องและเวลาที่ต้องการ
When กรอกรายละเอียดการจอง (หัวข้อประชุม, จำนวนคน, อุปกรณ์เพิ่มเติม)
Then ระบบบันทึกการจองสำเร็จ
And แสดง booking confirmation พร้อม booking ID
And ส่ง confirmation email ภายใน 1 นาที

Given ผู้ใช้มีการจองที่อยู่ในอนาคต
When ต้องการแก้ไขการจองล่วงหน้าอย่างน้อย 2 ชั่วโมง
Then ระบบอนุญาตให้แก้ไขได้
And อัปเดตข้อมูลการจองใหม่
And ส่ง updated confirmation email

Given การจองมี conflict กับการจองอื่น
When ผู้ใช้พยายามจองห้องในช่วงเวลาเดียวกัน
Then ระบบแสดงข้อความ error "Room is already booked"
And แนะนำช่วงเวลาอื่นที่ว่าง
```

**Dependencies:** REQ-F002 (Room Search), REQ-F004 (Notification System)

---

#### REQ-F004: Notification System
**Description:** ระบบต้องส่งการแจ้งเตือนไปยังผู้ใช้เกี่ยวกับการจอง การเปลี่ยนแปลง และการเตือนก่อนเวลาประชุม

**Priority:** Medium  
**Source:** User Feedback Session  
**Rationale:** ช่วยลดการลืมและเพิ่มประสิทธิภาพการใช้งานห้องประชุม

**Detailed Requirements:**
- ระบบต้องส่ง email confirmation ทันทีหลังจากการจอง แก้ไข หรือยกเลิก
- ระบบต้องส่งการแจ้งเตือนก่อนเวลาประชุม 30 นาทีและ 5 นาที
- ระบบต้องรองรับการส่ง notification ผ่าน email, SMS, และ push notification
- ระบบต้องให้ผู้ใช้สามารถตัดสิ้นเลือกประเภทการแจ้งเตือนที่ต้องการได้

**Acceptance Criteria:**
```
Given ผู้ใช้จองห้องประชุมสำเร็จ
When การจองเสร็จสมบูรณ์
Then ระบบส่ง confirmation email ภายใน 1 นาที
And email มีรายละเอียด: ห้อง, วันที่, เวลา, booking ID

Given เวลาประชุมใกล้จะถึง
When เหลือเวลา 30 นาทีก่อนเวลาประชุม
Then ระบบส่ง reminder notification
And เมื่อเหลือ 5 นาที ส่ง final reminder
And ผู้ใช้สามารถ quick cancel ได้จาก notification

Given ผู้ใช้ไม่ต้องการ notification บางประเภท
When เข้าไปตั้งค่าใน user preferences
Then สามารถเลือก disable ประเภท notification ที่ไม่ต้องการ
And ระบบบันทึกการตั้งค่าและใช้ค่าดังกล่าวในการส่ง notification ต่อไป
```

**Dependencies:** Third-party email service, SMS gateway

---

#### REQ-F005: Reporting and Analytics
**Description:** ระบบต้องสร้างรายงานการใช้งานห้องประชุมและสถิติต่างๆ สำหรับผู้บริหาร

**Priority:** Medium  
**Source:** Management Requirements  
**Rationale:** ช่วยในการตัดสินใจเชิงธุรกิจและการจัดการทรัพยากรให้มีประสิทธิภาพ

**Detailed Requirements:**
- ระบบต้องสร้างรายงานการใช้งานห้องประชุมรายวัน รายสัปดาห์ และรายเดือน
- ระบบต้องแสดงสถิติ: อัตราการใช้งาน, ห้องที่ได้รับความนิยม, การยกเลิกการจอง
- ระบบต้องให้ export รายงานเป็น PDF และ Excel format
- ระบบต้องให้ผู้ใช้ที่มีสิทธิ์สามารถตั้งค่า automated report ได้

**Acceptance Criteria:**
```
Given ผู้ใช้ที่มีสิทธิ์ admin หรือ manager
When เข้าไปในหน้า Reports & Analytics
Then แสดง dashboard พร้อมสถิติการใช้งานของ 30 วันที่ผ่านมา
And มี chart แสดง room utilization rate
And มี top 5 most booked rooms

Given ผู้ใช้ต้องการรายงานในช่วงเวลาเฉพาะ
When เลือก date range และคลิก "Generate Report"
Then ระบบสร้างรายงานตามช่วงเวลาที่เลือก
And สามารถ download เป็น PDF หรือ Excel
And รายงานมีข้อมูล: total bookings, cancellation rate, peak hours
```

**Dependencies:** Database with booking history data

---

### 3.2 Non-functional Requirements

#### REQ-NF001: Performance Requirements
**Description:** ระบบต้องมีประสิทธิภาพที่ตอบสนองความต้องการของผู้ใช้

**Response Time:**
- หน้า login ต้องโหลดเสร็จภายใน 2 วินาที
- การค้นหาห้องประชุมต้องแสดงผลภายใน 3 วินาที  
- การจองห้องต้องเสร็จสิ้นภายใน 5 วินาที
- การส่ง notification ต้องเสร็จภายใน 1 นาที

**Throughput:**
- ระบบต้องรองรับผู้ใช้งานพร้อมกันได้อย่างน้อย 200 คน
- ระบบต้องประมวลผลการจองได้อย่างน้อย 50 transactions ต่อนาที
- Database ต้องรองรับ 1,000 queries ต่อนาที

**Capacity:**
- ระบบต้องเก็บข้อมูลการจองได้อย่างน้อย 100,000 records
- ระบบต้องรองรับการเพิ่มจำนวนห้องประชุมได้สูงสุด 500 ห้อง
- ระบบต้องเก็บข้อมูล user ได้อย่างน้อย 10,000 accounts

**Acceptance Criteria:**
```
Given ระบบมี concurrent users 200 คน
When ทุกคนใช้งานพร้อมกัน
Then response time ต้องไม่เกิน 5 วินาที
And system availability ต้องอย่างน้อย 99%

Given มีการจองห้องประชุม 50 ครั้งในหนึ่งนาที
When ระบบประมวลผลการจอง
Then ทุกการจองต้องประมวลผลสำเร็จ
And ไม่มี data loss หรือ corruption
```

#### REQ-NF002: Security Requirements  
**Description:** ระบบต้องมีการรักษาความปลอดภัยที่เพียงพอ

**Authentication & Authorization:**
- ระบบต้องใช้ HTTPS สำหรับการสื่อสารทั้งหมด
- Password ต้องมีความยาวอย่างน้อย 8 ตัวอักษรและมีตัวอักขระพิเศษ
- Session timeout ต้องไม่เกิน 8 ชั่วโมงสำหรับ inactive users
- ระบบต้องรองรับ two-factor authentication (2FA)

**Data Protection:**
- ข้อมูลส่วนบุคคลต้องเข้ารหัสใน database
- การเข้าถึงข้อมูลต้องมี audit trail
- Sensitive data ต้องไม่แสดงใน logs
- ระบบต้อง backup ข้อมูลทุกวันและเก็บไว้อย่างน้อย 30 วัน

#### REQ-NF003: Usability Requirements
**Description:** ระบบต้องใช้งานง่ายและเป็นมิตรกับผู้ใช้

**Ease of Use:**
- ผู้ใช้ใหม่สามารถเรียนรู้การจองห้องประชุมได้ภายใน 5 นาที
- การจองห้องพื้นฐานต้องใช้คลิกไม่เกิน 5 ครั้ง
- ระบบต้องมี help text และ tooltips ที่เหมาะสม
- Interface ต้องรองรับภาษาไทยและอังกฤษ

**Accessibility:**
- รองรับ screen readers สำหรับผู้พิการทางสายตา
- ใช้งานได้ด้วย keyboard navigation
- สีและ contrast ต้องเป็นไปตามมาตรฐาน WCAG 2.1 AA
- รองรับ font size scaling ตั้งแต่ 100% ถึง 200%

#### REQ-NF004: Reliability Requirements
**Description:** ระบบต้องมีความเชื่อถือได้และสามารถกู้คืนได้

**Availability:**
- System uptime ต้องอย่างน้อย 99.5% (downtime ไม่เกิน 3.65 วันต่อปี)
- Planned maintenance window ไม่เกิน 4 ชั่วโมงต่อเดือน
- ระบบต้องทำงานได้ 24/7 ยกเว้นช่วง maintenance

**Fault Tolerance:**
- ระบบต้องกู้คืนจาก system crash ได้ภายใน 15 นาที
- มี automatic failover สำหรับ database
- การจองที่กำลังดำเนินการต้องไม่สูญหายเมื่อเกิด system failure
- มี error handling ที่เหมาะสมและ user-friendly error messages

---

## 4. Use Cases and User Stories

### 4.1 Use Case Diagram

```
                    MeetingRoom Pro System
    ┌───────────────────────────────────────────────────────────┐
    │                                                           │
    │           📝 Register/Login                               │
    │               ⭕                                          │
    │                │                                         │
    │   🔍 Search     │    📅 Book Room      📧 Send          │
    │    Rooms        │        ⭕             Notifications    │
    │      ⭕         │         │                ⭕            │
    │       │         │         │                 │           │
👤 Employee ──┼─────────┼─────────┼─────────────────┼───────────│
    │       │         │         │                 │           │
    │       │         │    ✏️ Modify Booking      │           │
    │       │         │         ⭕                 │           │
    │       │         │         │                 │           │
    │       │         │    ❌ Cancel Booking      │           │
    │       │         │         ⭕                 │           │
    │       │         │                           