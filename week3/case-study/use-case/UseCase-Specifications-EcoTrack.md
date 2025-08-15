# Use Cases Document
## ระบบติดตาม Carbon Footprint - EcoTrack

**Document ID:** UC-ECO-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2568  
**สถานะ:** Final  
**อ้างอิงจาก:** SRS-ECO-001 v1.0  

---

## Revision History

| Version | วันที่ | ผู้แก้ไข | รายละเอียด |
|---------|--------|----------|-------------|
| 0.1 | 12/03/2568 | ทีมพัฒนา | ร่าง Use Cases เบื้องต้น |
| 0.5 | 16/03/2568 | ทีมพัฒนา | เพิ่ม Use Case descriptions |
| 0.8 | 18/03/2568 | ทีมพัฒนา | เพิ่ม traceability matrix |
| 1.0 | 20/03/2568 | ทีมพัฒนา | เอกสารฉบับสมบูรณ์ |

---

## สารบัญ

1. [บทนำ (Introduction)](#1-บทนำ-introduction)
2. [Use Case Overview](#2-use-case-overview)
3. [Actors Definition](#3-actors-definition)
4. [Use Case Descriptions](#4-use-case-descriptions)
5. [Traceability Matrix](#5-traceability-matrix)
6. [ภาคผนวก (Appendices)](#6-ภาคผนวก-appendices)

---

## 1. บทนำ (Introduction)

### 1.1 วัตถุประสงค์

เอกสารนี้อธิบาย Use Cases ทั้งหมดของระบบ EcoTrack รวมถึงการเชื่อมโยงระหว่าง Use Cases กับ Functional Requirements เพื่อให้สามารถติดตามและตรวจสอบความครอบคลุมของความต้องการได้

### 1.2 ขอบเขต

เอกสารครอบคลุม:
- การกำหนด Actors ทั้งหมดในระบบ
- Use Cases แบบละเอียดพร้อม preconditions และ postconditions
- การเชื่อมโยง Use Cases กับ Functional Requirements
- ลำดับการดำเนินงานและ dependencies

### 1.3 เอกสารอ้างอิง

- SRS-ECO-001: Software Requirements Specification
- UML 2.5 Specification
- IEEE Std 1016-2009: System and Software Design Descriptions

---

## 2. Use Case Overview

### 2.1 Use Case Diagram

```
                    EcoTrack System
    ┌────────────────────────────────────────────────────────┐
    │                                                        │
    │    ○ UC-01: Authenticate User                          │
    │    │                                                   │
    │    ○ UC-02: Log Transportation Activity                │
    │    │                                                   │
    │    ○ UC-03: Log Energy Usage                           │
    │    │                                                   │
    │    ○ UC-04: Log Waste Management                       │
User ────○ UC-05: View Personal Dashboard                    │
    │    │                                                   │
    │    ○ UC-06: View Carbon Reports                        │
    │    │                                                   │
    │    ○ UC-07: View Trend Analysis                        │
    │    │                                                   │
    │    ○ UC-08: View Leaderboard                           │
    │    │                                                   │
    │    ○ UC-09: Set Personal Goals                         │
    │    │                                                   │
    │    ○ UC-10: Receive Recommendations                    │
    │                                                        │
    │    ○ UC-11: Access Admin Dashboard                     │
    │    │                                                   │
Admin────○ UC-12: Generate System Reports                    │
    │    │                                                   │
    │    ○ UC-13: Manage Emission Factors                   │
    │    │                                                   │
    │    ○ UC-14: Manage User Accounts                       │
    │    │                                                   │
    │    ○ UC-15: Configure Notifications                    │
    │                                                        │
    │                    ○ UC-16: Calculate Carbon Footprint│
System ──┤                                                  │
    │                    ○ UC-17: Earn Badges & Points      │
    │                                                        │
    └────────────────────────────────────────────────────────┘
```

### 2.2 Use Case Summary

| Use Case ID | Use Case Name | Primary Actor | Priority | Complexity | Linked FR |
|-------------|---------------|---------------|----------|------------|-----------|
| UC-01 | Authenticate User | User | High | Low | FR-001 |
| UC-02 | Log Transportation Activity | User | High | Medium | FR-002 |
| UC-03 | Log Energy Usage | User | High | Medium | FR-003 |
| UC-04 | Log Waste Management | User | Medium | Medium | FR-004 |
| UC-05 | View Personal Dashboard | User | High | High | FR-006 |
| UC-06 | View Carbon Reports | User | Medium | High | FR-008 |
| UC-07 | View Trend Analysis | User | Low | High | FR-008 |
| UC-08 | View Leaderboard | User | Medium | Medium | FR-011 |
| UC-09 | Set Personal Goals | User | Medium | Medium | FR-009 |
| UC-10 | Receive Recommendations | User | Medium | High | FR-010 |
| UC-11 | Access Admin Dashboard | Admin | High | High | FR-012 |
| UC-12 | Generate System Reports | Admin | Medium | High | FR-012 |
| UC-13 | Manage Emission Factors | Admin | Medium | Medium | FR-012 |
| UC-14 | Manage User Accounts | Admin | Low | Medium | FR-012 |
| UC-15 | Configure Notifications | Admin | Low | Low | FR-013 |
| UC-16 | Calculate Carbon Footprint | System | High | High | FR-005 |
| UC-17 | Earn Badges & Points | System | Medium | Medium | FR-007 |

---

## 3. Actors Definition

### 3.1 Primary Actors

#### 3.1.1 User (ผู้ใช้งานทั่วไป)
**Description:** นักศึกษาและบุคลากรมหาวิทยาลัยที่ใช้ระบบเพื่อติดตาม Carbon Footprint

**Characteristics:**
- มีบัญชีมหาวิทยาลัย (@university.ac.th)
- สามารถบันทึกกิจกรรมประจำวัน
- ดูรายงานและสถิติส่วนตัว
- เข้าร่วมกิจกรรม Gamification

**Sub-types:**
- **Student:** นักศึกษาในมหาวิทยาลัย
- **Staff:** บุคลากรและอาจารย์

#### 3.1.2 Admin (ผู้ดูแลระบบ)
**Description:** ผู้ดูแลระบบที่มีสิทธิ์จัดการข้อมูลและการตั้งค่าระบบ

**Characteristics:**
- มีสิทธิ์เข้าถึงข้อมูลระดับมหาวิทยาลัย
- จัดการการตั้งค่าระบบ
- สร้างรายงานสำหรับผู้บริหาร
- ดูแลความปลอดภัยของข้อมูล

### 3.2 Secondary Actors

#### 3.2.1 University SSO System
**Description:** ระบบ Single Sign-On ของมหาวิทยาลัย

**Responsibilities:**
- ตรวจสอบ authentication
- ให้ข้อมูลผู้ใช้พื้นฐาน (ชื่อ, คณะ, สถานะ)

#### 3.2.2 Email System
**Description:** ระบบอีเมลสำหรับส่ง notifications

**Responsibilities:**
- ส่งรายงานรายเดือน
- แจ้งเตือนและ reminders

#### 3.2.3 Calculation Engine
**Description:** ระบบคำนวณ Carbon Footprint

**Responsibilities:**
- คำนวณ CO2e จากข้อมูลกิจกรรม
- อัพเดท emission factors

---

## 4. Use Case Descriptions

### UC-01: Authenticate User

**Use Case ID:** UC-01  
**Use Case Name:** Authenticate User  
**Primary Actor:** Student, Staff  
**Supporting Actors:** University SSO System  
**Goal:** เข้าสู่ระบบผ่านบัญชีมหาวิทยาลัย  
**Priority:** High  
**Frequency:** ทุกครั้งที่เริ่มใช้งาน  

**Preconditions:**
- มีบัญชีมหาวิทยาลัย
- ระบบ SSO ทำงานปกติ

**Main Success Scenario:**
1. ผู้ใช้เปิดแอป EcoTrack
2. คลิก "Login with University Account"
3. ระบบ redirect ไป University SSO
4. ผู้ใช้กรอก username/password
5. SSO ส่ง authentication token กลับ
6. ระบบสร้าง session และ redirect ไป Dashboard

**Alternative Flows:**
- **A1: รหัสผ่านผิด**
  - 4a. SSO ส่งข้อผิดพลาด "Invalid credentials"
  - 4b. ระบบแสดงข้อความ "รหัสผ่านไม่ถูกต้อง"
  - 4c. กลับไปที่ขั้นตอน 2

- **A2: SSO ไม่ทำงาน**
  - 3a. ไม่สามารถเชื่อมต่อ SSO ได้
  - 3b. ระบบแสดงข้อความ "ระบบขัดข้อง กรุณาลองใหม่อีกครั้ง"

**Postconditions:**
- ผู้ใช้เข้าสู่ระบบสำเร็จ
- มี active session

**Business Rules:**
- เฉพาะ email domain @university.ac.th เท่านั้น
- Session timeout หลัง 30 นาทีไม่ใช้งาน

**Linked Functional Requirements:** FR-001

---

### UC-02: Log Transportation Activity

**Use Case ID:** UC-02  
**Use Case Name:** Log Transportation Activity  
**Primary Actor:** Student, Staff  
**Supporting Actors:** Calculation Engine  
**Goal:** บันทึกการเดินทางประจำวัน  
**Priority:** High  
**Frequency:** รายวัน  

**Preconditions:**
- ผู้ใช้ login แล้ว

**Main Success Scenario:**
1. เลือกเมนู "บันทึกการเดินทาง"
2. เลือกประเภท: เดิน, จักรยาน, รถยนต์, รถเมล์, BTS/MRT
3. กรอกระยะทาง (กม.)
4. เลือกวันที่
5. คลิก "บันทึก"
6. ระบบคำนวณ CO₂ และแสดงผล

**Alternative Flows:**
- **A1: ข้อมูลไม่ถูกต้อง**
  - 3a. ระยะทาง ≤ 0 → แสดงข้อผิดพลาด "กรุณาใส่ระยะทางที่ถูกต้อง"
  - 3b. ระยะทาง > 1000 กม. → แสดงข้อความยืนยัน "ระยะทางมากกว่า 1000 กม. ต้องการบันทึกหรือไม่?"

**Postconditions:**
- ข้อมูลถูกบันทึก
- CO₂ ถูกคำนวณ
- Dashboard อัพเดท

**Business Rules:**
- เดิน/จักรยาน ให้ bonus points
- บันทึกย้อนหลังได้ไม่เกิน 7 วัน

**Linked Functional Requirements:** FR-002, FR-005, FR-007

---

### UC-03: Log Energy Usage

**Use Case ID:** UC-03  
**Use Case Name:** Log Energy Usage  
**Primary Actor:** Student, Staff  
**Supporting Actors:** Calculation Engine  
**Goal:** บันทึกการใช้พลังงาน (ไฟฟ้า/น้ำ)  
**Priority:** High  
**Frequency:** รายเดือน  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูลจากบิลหรือมิเตอร์

**Main Success Scenario:**
1. เลือกเมนู "บันทึกการใช้พลังงาน"
2. เลือกประเภท: ไฟฟ้า หรือ น้ำ
3. กรอกจำนวนหน่วย
4. เลือกเดือน/ปี
5. คลิก "บันทึก"
6. ระบบคำนวณ CO₂ และแสดงผลเปรียบเทียบ

**Alternative Flows:**
- **A1: มีข้อมูลเดือนนั้นแล้ว**
  - 5a. ระบบตรวจพบข้อมูลซ้ำ
  - 5b. แสดงข้อความ "มีข้อมูลเดือนนี้แล้ว ต้องการแทนที่หรือไม่?"

- **A2: หน่วยผิดปกติสูง**
  - 5a. ค่าที่กรอกสูงเกินปกติ
  - 5b. แสดงข้อความยืนยัน "การใช้พลังงานสูงกว่าปกติ ข้อมูลถูกต้องหรือไม่?"

**Postconditions:**
- ข้อมูลพลังงานถูกบันทึก
- CO₂ ถูกคำนวณ

**Business Rules:**
- การลดการใช้พลังงาน > 10% ได้ bonus points
- บันทึกได้ย้อนหลัง 12 เดือน

**Linked Functional Requirements:** FR-003, FR-005, FR-007

---

### UC-04: Log Waste Management

**Use Case ID:** UC-04  
**Use Case Name:** Log Waste Management  
**Primary Actor:** Student, Staff  
**Goal:** บันทึกการจัดการขยะและรีไซเคิล  
**Priority:** Medium  
**Frequency:** เมื่อมีกิจกรรมรีไซเคิล  

**Preconditions:**
- ผู้ใช้ login แล้ว

**Main Success Scenario:**
1. เลือกเมนู "บันทึกการจัดการขยะ"
2. เลือกประเภทขยะ: กระดาษ, พลาสติก, แก้ว, อลูมิเนียม, อื่นๆ
3. ระบุปริมาณ (กก. หรือ ชิ้น)
4. เลือกวิธีจัดการ: รีไซเคิล, บริจาค, ทิ้งทั่วไป
5. คลิก "บันทึก"
6. ระบบคำนวณ environmental impact

**Alternative Flows:**
- **A1: ปริมาณไม่ถูกต้อง**
  - 3a. ปริมาณ ≤ 0 → แสดงข้อผิดพลาด "กรุณาใส่ปริมาณที่ถูกต้อง"

**Postconditions:**
- ข้อมูลขยะถูกบันทึก
- Recycling score อัพเดท

**Business Rules:**
- รีไซเคิลได้คะแนนมากกว่าทิ้งขยะทั่วไป
- กิจกรรมรีไซเคิลมีผลต่อการคำนวณ net carbon footprint

**Linked Functional Requirements:** FR-004, FR-007

---

### UC-05: View Personal Dashboard

**Use Case ID:** UC-05  
**Use Case Name:** View Personal Dashboard  
**Primary Actor:** Student, Staff  
**Goal:** ดูภาพรวม Carbon Footprint ส่วนตัว  
**Priority:** High  
**Frequency:** ทุกครั้งที่เข้าระบบ  

**Preconditions:**
- ผู้ใช้ login แล้ว

**Main Success Scenario:**
1. เข้าหน้า Dashboard
2. ระบบแสดงข้อมูลวันนี้: CO₂ รวม, เปรียบเทียบเมื่อวาน
3. แสดงกราฟสัดส่วนตาม activity (Pie chart)
4. แสดงแนวโน้ม 7 วันล่าสุด (Line chart)
5. แสดงคะแนนและ badges
6. แสดงปุ่ม quick actions

**Alternative Flows:**
- **A1: ไม่มีข้อมูล**
  - 2a. ผู้ใช้ใหม่หรือไม่เคยบันทึกข้อมูล
  - 2b. แสดง welcome message และ tutorial

**Postconditions:**
- ผู้ใช้เห็นสถานะปัจจุบัน

**Business Rules:**
- Dashboard อัพเดท real-time เมื่อมีการบันทึกข้อมูลใหม่

**Linked Functional Requirements:** FR-006, FR-007

---

### UC-06: View Carbon Reports

**Use Case ID:** UC-06  
**Use Case Name:** View Carbon Reports  
**Primary Actor:** Student, Staff  
**Goal:** ดูรายงาน Carbon Footprint แบบละเอียด  
**Priority:** Medium  
**Frequency:** รายสัปดาห์หรือรายเดือน  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูลอย่างน้อย 3 วัน

**Main Success Scenario:**
1. เลือกเมนู "รายงานของฉัน"
2. เลือกประเภท: รายสัปดาห์, รายเดือน, เปรียบเทียบ
3. เลือกช่วงเวลา
4. คลิก "ดูรายงาน"
5. ระบบแสดงรายงานพร้อมกราฟและตาราง
6. แสดงการเปรียบเทียบและคำแนะนำ

**Alternative Flows:**
- **A1: ข้อมูลไม่เพียงพอ**
  - 4a. ข้อมูลในช่วงที่เลือกน้อยกว่า 3 วัน
  - 4b. แจ้งให้บันทึกข้อมูลเพิ่ม "ข้อมูลไม่เพียงพอสำหรับรายงาน"

**Postconditions:**
- ผู้ใช้ได้รับรายงานที่ต้องการ

**Business Rules:**
- รายงานสามารถส่งออกเป็น PDF
- รายงานสามารถย้อนหลังได้สูงสุด 2 ปี

**Linked Functional Requirements:** FR-008

---

### UC-07: View Trend Analysis

**Use Case ID:** UC-07  
**Use Case Name:** View Trend Analysis  
**Primary Actor:** Student, Staff  
**Goal:** วิเคราะห์แนวโน้มการใช้งานระยะยาว  
**Priority:** Low  
**Frequency:** รายเดือนหรือรายไตรมาส  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูลอย่างน้อย 1 เดือน

**Main Success Scenario:**
1. เลือกเมนู "วิเคราะห์แนวโน้ม"
2. เลือกช่วงเวลา: 1 เดือน, 3 เดือน, 6 เดือน
3. ระบบแสดงกราฟแนวโน้ม
4. แสดงการคาดการณ์อนาคต
5. แสดง insights และ recommendations

**Alternative Flows:**
- **A1: ข้อมูลไม่เพียงพอ**
  - 3a. ข้อมูลน้อยกว่า 2 สัปดาห์
  - 3b. แสดงข้อความ "ข้อมูลไม่เพียงพอสำหรับการวิเคราะห์แนวโน้ม"

**Postconditions:**
- ผู้ใช้เห็นแนวโน้มระยะยาว

**Business Rules:**
- การคาดการณ์ต้องมีข้อมูลอย่างน้อย 1 เดือน

**Linked Functional Requirements:** FR-008, FR-010

---

### UC-08: View Leaderboard

**Use Case ID:** UC-08  
**Use Case Name:** View Leaderboard  
**Primary Actor:** Student, Staff  
**Goal:** ดูการจัดอันดับและเปรียบเทียบกับผู้อื่น  
**Priority:** Medium  
**Frequency:** รายวันหรือรายสัปดาห์  

**Preconditions:**
- ผู้ใช้ login แล้ว

**Main Success Scenario:**
1. เลือกเมนู "Leaderboard"
2. เลือกขอบเขต: มหาวิทยาลัย, คณะ, แผนก
3. เลือกช่วงเวลา: สัปดาห์, เดือน, ตลอดกาล
4. ระบบแสดงอันดับ 1-10
5. ไฮไลท์ตำแหน่งของผู้ใช้
6. แสดงคะแนนและ badges ของแต่ละคน

**Alternative Flows:**
- **A1: ผู้ใช้ไม่เพียงพอ**
  - 4a. ผู้ใช้น้อยกว่า 3 คน → แจ้งว่าผู้ใช้ไม่เพียงพอ

**Postconditions:**
- ผู้ใช้เห็นตำแหน่งของตนเอง

**Business Rules:**
- อันดับอัพเดท real-time
- ปกป้องความเป็นส่วนตัวด้วยการแสดงเฉพาะอันดับและคะแนน

**Linked Functional Requirements:** FR-011

---

### UC-09: Set Personal Goals

**Use Case ID:** UC-09  
**Use Case Name:** Set Personal Goals  
**Primary Actor:** Student, Staff  
**Goal:** ตั้งเป้าหมายการลด Carbon Footprint  
**Priority:** Medium  
**Frequency:** รายเดือนหรือรายไตรมาส  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูล baseline อย่างน้อย 1 สัปดาห์

**Main Success Scenario:**
1. เลือกเมนู "ตั้งเป้าหมาย"
2. ระบบแสดง baseline ปัจจุบัน
3. เลือกประเภทเป้าหมาย: ลด CO₂ %, เพิ่ม green transport %, ฯลฯ
4. ระบุ target value และ timeframe
5. คลิก "บันทึกเป้าหมาย"
6. ระบบสร้าง tracking plan

**Alternative Flows:**
- **A1: ข้อมูลไม่เพียงพอ**
  - 2a. ไม่มีข้อมูล baseline
  - 2b. แสดงข้อความ "กรุณาบันทึกข้อมูลอย่างน้อย 1 สัปดาห์ก่อนตั้งเป้าหมาย"

**Postconditions:**
- เป้าหมายถูกบันทึก
- ระบบเริ่ม track progress

**Business Rules:**
- สามารถมีเป้าหมายพร้อมกันได้สูงสุด 3 เป้าหมาย
- เป้าหมายมีระยะเวลาขั้นต่ำ 1 สัปดาห์

**Linked Functional Requirements:** FR-009

---

### UC-10: Receive Recommendations

**Use Case ID:** UC-10  
**Use Case Name:** Receive Recommendations  
**Primary Actor:** User  
**Goal:** รับคำแนะนำการลด Carbon Footprint  
**Priority:** Medium  
**Frequency:** รายสัปดาห์  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูลกิจกรรมอย่างน้อย 1 สัปดาห์

**Main Success Scenario:**
1. ระบบวิเคราะห์ behavior pattern ของผู้ใช้
2. ระบบสร้างคำแนะนำที่เป็นส่วนตัว
3. แสดงคำแนะนำใน Dashboard
4. ผู้ใช้สามารถดูรายละเอียดเพิ่มเติม
5. ระบบติดตามการนำคำแนะนำไปใช้

**Alternative Flows:**
- **A1: ข้อมูลไม่เพียงพอ**
  - 1a. ไม่มีข้อมูลเพียงพอสำหรับการวิเคราะห์
  - 1b. แสดงคำแนะนำทั่วไป

**Postconditions:**
- ผู้ใช้ได้รับคำแนะนำที่เหมาะสม
- ระบบติดตามผลการนำไปใช้

**Business Rules:**
- คำแนะนำอัพเดททุกสัปดาห์
- คำแนะนำต้องสามารถปฏิบัติได้จริง

**Linked Functional Requirements:** FR-010

---

### UC-11: Access Admin Dashboard

**Use Case ID:** UC-11  
**Use Case Name:** Access Admin Dashboard  
**Primary Actor:** System Administrator  
**Goal:** เข้าถึงข้อมูลภาพรวมของระบบ  
**Priority:** High  
**Frequency:** ทุกวันทำการ  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin
- Login แล้ว

**Main Success Scenario:**
1. เข้าหน้า Admin Dashboard
2. ระบบแสดงสถิติภาพรวม:
   - จำนวนผู้ใช้ active
   - กิจกรรมที่บันทึกวันนี้
   - CO₂ รวมของมหาวิทยาลัย
3. แสดงกราฟแนวโน้ม 30 วัน
4. แสดงการจัดอันดับคณะ
5. แสดงเมนูการจัดการ

**Alternative Flows:**
- **A1: ไม่มีสิทธิ์**
  - 1a. ผู้ใช้ไม่มีสิทธิ์ admin
  - 1b. ปฏิเสธการเข้าถึง "คุณไม่มีสิทธิ์เข้าถึงหน้านี้"

**Postconditions:**
- Admin เห็นภาพรวมระบบ

**Business Rules:**
- เฉพาะ admin เท่านั้นที่เข้าถึงได้
- การเข้าถึงถูกบันทึกใน audit log

**Linked Functional Requirements:** FR-012

---

### UC-12: Generate System Reports

**Use Case ID:** UC-12  
**Use Case Name:** Generate System Reports  
**Primary Actor:** System Administrator  
**Goal:** สร้างรายงานระบบเพื่อนำเสนอผู้บริหาร  
**Priority:** Medium  
**Frequency:** รายสัปดาห์หรือรายเดือน  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin
- มีข้อมูลในระบบ

**Main Success Scenario:**
1. เข้าหน้า "สร้างรายงาน"
2. เลือกประเภท: ภาพรวมมหาวิทยาลัย, เปรียบเทียบคณะ, แนวโน้ม
3. เลือกช่วงเวลา
4. เลือกรูปแบบ: PDF, Excel, PowerPoint
5. คลิก "สร้างรายงาน"
6. ระบบประมวลผลและสร้างไฟล์
7. ดาวน์โหลดรายงาน

**Alternative Flows:**
- **A1: ข้อมูลไม่เพียงพอ**
  - 6a. ข้อมูลในช่วงที่เลือกไม่เพียงพอ
  - 6b. แจ้งและแนะนำช่วงเวลาอื่น

**Postconditions:**
- Admin ได้รับรายงานที่ต้องการ
- การสร้างรายงานถูกบันทึกใน log

**Business Rules:**
- รายงานมี watermark และข้อมูลผู้สร้าง
- รายงานสามารถสร้างได้สูงสุด 10 ครั้งต่อวัน

**Linked Functional Requirements:** FR-012

---

### UC-13: Manage Emission Factors

**Use Case ID:** UC-13  
**Use Case Name:** Manage Emission Factors  
**Primary Actor:** System Administrator  
**Goal:** จัดการค่าคงที่สำหรับคำนวณ CO₂  
**Priority:** Medium  
**Frequency:** รายไตรมาสหรือเมื่อมีการอัพเดทมาตรฐาน  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin

**Main Success Scenario:**
1. เข้าหน้า "จัดการ Emission Factors"
2. ระบบแสดงตารางค่าคงที่ปัจจุบัน
3. เลือกแก้ไขค่าที่ต้องการ
4. กรอกค่าใหม่พร้อมแหล่งอ้างอิง
5. คลิก "บันทึก"
6. ระบบอัพเดทค่าและ recalculate ข้อมูลย้อนหลัง

**Alternative Flows:**
- **A1: ค่าไม่ถูกต้อง**
  - 4a. ค่าที่กรอกเป็นลบหรือเกินขอบเขต
  - 4b. แสดงข้อผิดพลาด "กรุณาใส่ค่าที่ถูกต้อง"

**Postconditions:**
- ค่าคงที่อัพเดท
- การคำนวณใช้ค่าใหม่

**Business Rules:**
- ต้องมีแหล่งอ้างอิงที่เชื่อถือได้
- การเปลี่ยนแปลงมีผลย้อนหลัง 30 วัน

**Linked Functional Requirements:** FR-012

---

### UC-14: Manage User Accounts

**Use Case ID:** UC-14  
**Use Case Name:** Manage User Accounts  
**Primary Actor:** System Administrator  
**Goal:** จัดการบัญชีผู้ใช้ในระบบ  
**Priority:** Low  
**Frequency:** เมื่อจำเป็น  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin

**Main Success Scenario:**
1. เข้าหน้า "จัดการผู้ใช้"
2. ระบบแสดงรายการผู้ใช้ทั้งหมด
3. เลือกผู้ใช้ที่ต้องการจัดการ
4. เลือกการดำเนินการ:
   - ดูข้อมูลโดยละเอียด
   - ปิดใช้งานบัญชี
   - รีเซ็ตข้อมูล
   - เปลี่ยนสิทธิ์
5. ยืนยันการดำเนินการ

**Alternative Flows:**
- **A1: รีเซ็ตข้อมูล**
  - 4a. เลือกรีเซ็ตข้อมูล
  - 4b. ขอยืนยันเพิ่มเติม "การดำเนินการนี้ไม่สามารถยกเลิกได้"

**Postconditions:**
- บัญชีผู้ใช้อัพเดทตามที่ต้องการ
- การดำเนินการถูกบันทึกใน audit log

**Business Rules:**
- ไม่สามารถลบบัญชี admin สุดท้าย
- การรีเซ็ตข้อมูลไม่สามารถกู้คืนได้

**Linked Functional Requirements:** FR-012

---

### UC-15: Configure Notifications

**Use Case ID:** UC-15  
**Use Case Name:** Configure Notifications  
**Primary Actor:** System Administrator  
**Goal:** ตั้งค่าการแจ้งเตือนระดับระบบ  
**Priority:** Low  
**Frequency:** เมื่อต้องการเปลี่ยนแปลง  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin

**Main Success Scenario:**
1. เข้าหน้า "ตั้งค่าการแจ้งเตือน"
2. ระบบแสดงการตั้งค่าปัจจุบัน
3. แก้ไขการตั้งค่าที่ต้องการ:
   - ความถี่การแจ้งเตือน
   - ประเภทการแจ้งเตือน
   - เทมเพลตข้อความ
4. ทดสอบการแจ้งเตือน
5. บันทึกการตั้งค่า

**Alternative Flows:**
- **A1: การทดสอบล้มเหลว**
  - 4a. การทดสอบส่งการแจ้งเตือนล้มเหลว
  - 4b. แสดงข้อผิดพลาดและไม่บันทึกการตั้งค่า

**Postconditions:**
- การตั้งค่าการแจ้งเตือนอัพเดท
- ระบบใช้การตั้งค่าใหม่

**Business Rules:**
- การแจ้งเตือนต้องไม่บ่อยเกินไป (สูงสุดวันละ 3 ครั้ง)

**Linked Functional Requirements:** FR-013

---

### UC-16: Calculate Carbon Footprint

**Use Case ID:** UC-16  
**Use Case Name:** Calculate Carbon Footprint  
**Primary Actor:** System (Automated)  
**Supporting Actors:** Calculation Engine  
**Goal:** คำนวณ Carbon Footprint อัตโนมัติ  
**Priority:** High  
**Frequency:** ทุกครั้งที่มีการบันทึกข้อมูล  

**Preconditions:**
- มีข้อมูลกิจกรรมที่บันทึก
- มี emission factors ในระบบ

**Main Success Scenario:**
1. ระบบรับข้อมูลกิจกรรมใหม่
2. ดึง emission factor ที่เหมาะสม
3. คำนวณ CO₂e ตามสูตร
4. อัพเดทสถิติส่วนตัวของผู้ใช้
5. อัพเดทสถิติระดับมหาวิทยาลัย
6. ส่งผลการคำนวณกลับ

**Alternative Flows:**
- **A1: ไม่มี emission factor**
  - 2a. ไม่พบ emission factor สำหรับกิจกรรมนี้
  - 2b. ใช้ค่าเริ่มต้นและ log ข้อผิดพลาด

**Postconditions:**
- CO₂e ถูกคำนวณและบันทึก
- สถิติทุกระดับอัพเดท

**Business Rules:**
- การคำนวณต้องมีความถูกต้อง 99.9%
- ใช้ emission factors ตามมาตรฐาน TGO

**Linked Functional Requirements:** FR-005

---

### UC-17: Earn Badges & Points

**Use Case ID:** UC-17  
**Use Case Name:** Earn Badges & Points  
**Primary Actor:** System (Automated)  
**Secondary Actor:** Student, Staff  
**Goal:** คำนวณและมอบ badges/points ตามกิจกรรม  
**Priority:** Medium  
**Frequency:** ทุกครั้งที่มีการบันทึกกิจกรรม  

**Preconditions:**
- ผู้ใช้บันทึกกิจกรรม

**Main Success Scenario:**
1. ระบบตรวจสอบกิจกรรมที่บันทึก
2. คำนวณคะแนนตามกฎที่กำหนด
3. ตรวจสอบเงื่อนไข badges
4. อัพเดทคะแนนและมอบ badges
5. แจ้งเตือนผู้ใช้ (ถ้าได้ badge ใหม่)

**Alternative Flows:**
- **A1: เงื่อนไข badge ไม่ครบ**
  - 3a. ยังไม่ครบเงื่อนไขสำหรับ badge ใดๆ
  - 3b. ให้เฉพาะคะแนน

**Postconditions:**
- คะแนนและ badges อัพเดท
- ผู้ใช้ได้รับการแจ้งเตือน (ถ้ามี)

**Business Rules:**
- เดิน/จักรยาน = bonus points
- Recycling = bonus points
- Streak (บันทึกต่อเนื่อง) = combo bonus

**Linked Functional Requirements:** FR-007

---

## 5. Traceability Matrix

### 5.1 Use Case to Functional Requirements Mapping

| Use Case ID | Use Case Name | Linked Functional Requirements | Requirements Coverage |
|-------------|---------------|------------------------------|----------------------|
| UC-01 | Authenticate User | FR-001 | 100% |
| UC-02 | Log Transportation Activity | FR-002, FR-005, FR-007 | 100% |
| UC-03 | Log Energy Usage | FR-003, FR-005, FR-007 | 100% |
| UC-04 | Log Waste Management | FR-004, FR-007 | 100% |
| UC-05 | View Personal Dashboard | FR-006, FR-007 | 100% |
| UC-06 | View Carbon Reports | FR-008 | 80% |
| UC-07 | View Trend Analysis | FR-008, FR-010 | 60% |
| UC-08 | View Leaderboard | FR-011 | 100% |
| UC-09 | Set Personal Goals | FR-009 | 100% |
| UC-10 | Receive Recommendations | FR-010 | 100% |
| UC-11 | Access Admin Dashboard | FR-012 | 70% |
| UC-12 | Generate System Reports | FR-012 | 50% |
| UC-13 | Manage Emission Factors | FR-012 | 30% |
| UC-14 | Manage User Accounts | FR-012 | 25% |
| UC-15 | Configure Notifications | FR-013 | 100% |
| UC-16 | Calculate Carbon Footprint | FR-005 | 100% |
| UC-17 | Earn Badges & Points | FR-007 | 100% |

### 5.2 Functional Requirements to Use Case Mapping

| FR ID | Functional Requirement | Linked Use Cases | Coverage |
|-------|----------------------|------------------|----------|
| FR-001 | การลงทะเบียนและเข้าสู่ระบบ | UC-01 | Complete |
| FR-002 | การบันทึกกิจกรรมการเดินทาง | UC-02 | Complete |
| FR-003 | การบันทึกการใช้พลังงาน | UC-03 | Complete |
| FR-004 | การจัดการขยะและรีไซเคิล | UC-04 | Complete |
| FR-005 | การคำนวณ Carbon Footprint | UC-02, UC-03, UC-16 | Complete |
| FR-006 | การแสดงผล Dashboard | UC-05 | Complete |
| FR-007 | ระบบแต้มและรางวัล | UC-02, UC-03, UC-04, UC-05, UC-17 | Complete |
| FR-008 | การสร้างรายงานสรุป | UC-06, UC-07 | Complete |
| FR-009 | การตั้งเป้าหมายส่วนตัว | UC-09 | Complete |
| FR-010 | ระบบการแนะนำ | UC-07, UC-10 | Complete |
| FR-011 | การเปรียบเทียบและ Leaderboard | UC-08 | Complete |
| FR-012 | Admin Dashboard และรายงานมหาวิทยาลัย | UC-11, UC-12, UC-13, UC-14 | Partial |
| FR-013 | การแจ้งเตือนและ Reminders | UC-15 | Partial |

### 5.3 Requirements Coverage Analysis

#### Complete Coverage (100%)
- FR-001: การลงทะเบียนและเข้าสู่ระบบ
- FR-002: การบันทึกกิจกรรมการเดินทาง
- FR-003: การบันทึกการใช้พลังงาน
- FR-004: การจัดการขยะและรีไซเคิล
- FR-005: การคำนวณ Carbon Footprint
- FR-006: การแสดงผล Dashboard
- FR-007: ระบบแต้มและรางวัล
- FR-008: การสร้างรายงานสรุป
- FR-009: การตั้งเป้าหมายส่วนตัว
- FR-010: ระบบการแนะนำ
- FR-011: การเปรียบเทียบและ Leaderboard

#### Partial Coverage (50-90%)
- FR-012: Admin Dashboard และรายงานมหาวิทยาลัย (75%)
  - **Missing:** Advanced analytics, Custom reports, Data export
- FR-013: การแจ้งเตือนและ Reminders (70%)
  - **Missing:** User preference settings, Smart notifications

#### Gaps Identified

**FR-012 Gaps:**
1. **Custom Dashboard Creation** - Admin สร้าง dashboard แบบกำหนดเอง
2. **Advanced Analytics** - การวิเคราะห์ขั้นสูงด้วย machine learning
3. **Bulk Data Operations** - การจัดการข้อมูลจำนวนมาก
4. **Integration Management** - การจัดการการเชื่อมต่อระบบภายนอก

**FR-013 Gaps:**
1. **Smart Notifications** - การแจ้งเตือนตาม AI prediction
2. **Multi-channel Notifications** - การแจ้งเตือนหลายช่องทาง
3. **User Preference Management** - การจัดการความชอบของผู้ใช้
4. **Notification Analytics** - การวิเคราะห์ประสิทธิภาพการแจ้งเตือน

### 5.4 Additional Use Cases Needed

#### UC-18: Manage User Notification Preferences
**Goal:** ให้ผู้ใช้จัดการการตั้งค่าการแจ้งเตือนส่วนตัว  
**Linked FR:** FR-013  
**Priority:** Medium  

#### UC-19: Create Custom Admin Reports
**Goal:** ให้ admin สร้างรายงานแบบกำหนดเอง  
**Linked FR:** FR-012  
**Priority:** Low  

#### UC-20: Manage System Integrations
**Goal:** จัดการการเชื่อมต่อกับระบบภายนอก  
**Linked FR:** FR-012  
**Priority:** Low  

---

## 6. ภาคผนวก (Appendices)

### 6.1 การเชื่อมโยง Use Cases

#### ลำดับการใช้งานทั่วไป:
1. **UC-01** (Authenticate User) → **UC-05** (View Personal Dashboard)
2. **UC-05** → **UC-02/03/04** (Log Activities)
3. **UC-02/03/04** → **UC-16** (Calculate Carbon Footprint) → **UC-17** (Earn Points)
4. **UC-05** → **UC-06/07/08** (View Reports/Analysis)
5. **UC-10** (Receive Recommendations) → **UC-09** (Set Goals)

#### Dependencies:
- **Prerequisites:** UC-01 ต้องสำเร็จก่อน UC อื่นๆ ทั้งหมด
- **Data Dependencies:** UC-06, UC-07 ต้องมีข้อมูลจาก UC-02, UC-03, UC-04
- **System Triggers:** UC-16, UC-17 ถูก trigger โดย UC-02, UC-03, UC-04
- **Admin Functions:** UC-11-15 ต้องใช้ UC-01 ด้วยสิทธิ์ admin

### 6.2 Technical Implementation Notes

#### Authentication & Authorization
- ใช้ University SSO API สำหรับ UC-01
- JWT tokens สำหรับ session management
- Role-based access control สำหรับ admin functions

#### Data Processing
- Calculation Engine แยกเป็น microservice สำหรับ UC-16
- Real-time updates สำหรับ UC-05, UC-08
- Background jobs สำหรับ UC-17, UC-10

#### Performance Considerations
- Caching สำหรับข้อมูลที่ไม่เปลี่ยนแปลงบ่อย (UC-08, UC-11)
- Pagination สำหรับ reports (UC-06, UC-12)
- Asynchronous processing สำหรับ heavy calculations

#### Error Handling
- Graceful degradation เมื่อ external services ไม่ทำงาน
- Rollback mechanisms สำหรับ data modifications
- Comprehensive logging สำหรับ debugging

### 6.3 Testing Strategy per Use Case

#### High Priority Use Cases (Must Test Thoroughly)
- **UC-01:** Authentication flow, edge cases, security
- **UC-02, UC-03:** Data validation, calculation accuracy
- **UC-05:** Performance, real-time updates
- **UC-16:** Calculation accuracy, formula validation

#### Medium Priority Use Cases (Standard Testing)
- **UC-04, UC-06, UC-08, UC-09:** Functional testing, user experience
- **UC-11, UC-12:** Admin workflows, permission validation

#### Low Priority Use Cases (Basic Testing)
- **UC-07, UC-10, UC-13, UC-14, UC-15:** Basic functionality, happy path

### 6.4 Success Metrics

#### User Engagement Metrics
- **UC-02, UC-03, UC-04:** Daily active logging rate > 70%
- **UC-05:** Dashboard visit frequency > 3 times/week
- **UC-08:** Leaderboard engagement > 50% weekly

#### System Performance Metrics
- **UC-01:** Login success rate > 99%
- **UC-16:** Calculation accuracy > 99.9%
- **UC-05:** Dashboard load time < 3 seconds

#### Business Value Metrics
- **UC-09:** Goal completion rate > 60%
- **UC-10:** Recommendation adoption rate > 40%
- Overall: 15% reduction in average Carbon Footprint after 6 months

---

**หมายเหตุ:** เอกสารนี้เป็น Use Cases ฉบับสมบูรณ์ที่เชื่อมโยงกับ Functional Requirements ใน SRS-ECO-001 โดยสามารถใช้เป็นพื้นฐานสำหรับการออกแบบระบบ การเขียน test cases และการติดตามความคืบหน้าในการพัฒนา

**การใช้งานเอกสาร:**
1. ใช้เป็นข้อมูลอ้างอิงในการออกแบบ user interface
2. สร้าง test cases จาก use case scenarios
3. ติดตามความครอบคลุมของ requirements
4. ใช้ในการ validate การทำงานของระบบ
5. อ้างอิงในการสื่อสารกับ stakeholders