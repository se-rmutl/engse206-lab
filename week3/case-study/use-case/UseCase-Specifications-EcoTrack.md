# Use Case Specifications - EcoTrack System
**Carbon Footprint Tracking System**

## บทนำ

เอกสารนี้นำเสนอ Use Case Diagram ที่มีความละเอียดครบถ้วนสำหรับระบบ EcoTrack ตามข้อมูลจาก Requirements Analysis Document เพื่อใช้ประกอบการพัฒนาระบบจริง

---

## การวิเคราะห์ Actors จาก Personas

จากการวิเคราะห์ 3 Personas หลัก เราสามารถกำหนด Actors ของระบบได้ดังนี้:

### Primary Actors (ผู้ใช้หลัก)
- **Student (นักศึกษา)** - ตัวแทนโดย "น้องเกม"
- **Staff (บุคลากร)** - ตัวแทนโดย "พี่พลอย"
- **System Administrator** - ตัวแทนโดย "คุณแอน"

### Secondary Actors (ระบบภายนอก)
- **University SSO System** - ระบบ Single Sign-On ของมหาวิทยาลัย
- **Calculation Engine** - ระบบคำนวณ Carbon Footprint

---

## UC-01: Authenticate User

**Primary Actor:** Student, Staff  
**Goal:** เข้าสู่ระบบผ่านบัญชีมหาวิทยาลัย  

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
- 4a. รหัสผ่านผิด → แสดงข้อผิดพลาด
- 5a. SSO ไม่ทำงาน → แสดงข้อความระบบขัดข้อง

**Postconditions:**
- ผู้ใช้เข้าสู่ระบบสำเร็จ
- มี active session

---

## UC-02: Log Transportation Activity

**Primary Actor:** Student, Staff  
**Goal:** บันทึกการเดินทางประจำวัน  

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
- 3a. ระยะทาง ≤ 0 → แสดงข้อผิดพลาด
- 3b. ระยะทาง > 1000 กม. → ขอยืนยัน

**Postconditions:**
- ข้อมูลถูกบันทึก
- CO₂ ถูกคำนวณ
- Dashboard อัพเดท

---

## UC-03: Log Energy Usage

**Primary Actor:** Student, Staff  
**Goal:** บันทึกการใช้พลังงาน (ไฟฟ้า/น้ำ)  

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
- 3a. มีข้อมูลเดือนนั้นแล้ว → ถามว่าจะแทนที่หรือไม่
- 3b. หน่วยผิดปกติสูง → ขอยืนยัน

**Postconditions:**
- ข้อมูลพลังงานถูกบันทึก
- CO₂ ถูกคำนวณ

---

## UC-04: Log Waste Management

**Primary Actor:** Student, Staff  
**Goal:** บันทึกการจัดการขยะและรีไซเคิล  

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
- 3a. ปริมาณ ≤ 0 → แสดงข้อผิดพลาด

**Postconditions:**
- ข้อมูลขยะถูกบันทึก
- Recycling score อัพเดท

---

## UC-05: View Personal Dashboard

**Primary Actor:** Student, Staff  
**Goal:** ดูภาพรวม Carbon Footprint ส่วนตัว  

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
- 2a. ไม่มีข้อมูล → แสดง welcome message และ tutorial

**Postconditions:**
- ผู้ใช้เห็นสถานะปัจจุบัน

---

## UC-06: View Carbon Reports

**Primary Actor:** Student, Staff  
**Goal:** ดูรายงาน Carbon Footprint แบบละเอียด  

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
- 2a. ข้อมูลไม่เพียงพอ → แจ้งให้บันทึกข้อมูลเพิ่ม

**Postconditions:**
- ผู้ใช้ได้รับรายงานที่ต้องการ

---

## UC-07: View Trend Analysis

**Primary Actor:** Student, Staff  
**Goal:** วิเคราะห์แนวโน้มการใช้งานระยะยาว  

**Preconditions:**
- ผู้ใช้ login แล้ว
- มีข้อมูลอย่างน้อย 1 เดือน

**Main Success Scenario:**
1. เลือกเมนู "วิเคราะห์แนวโน้ม"
2. เลือกช่วงเวลา: 1 เดือน, 3 เดือน, 6 เดือน
3. ระบบแสดงกราฟแนวโน้ม
4. แสดงการคาดการณ์อนาคต
5. แสดง insights และ recommendations

**Postconditions:**
- ผู้ใช้เห็นแนวโน้มระยะยาว

---

## UC-08: View Leaderboard

**Primary Actor:** Student, Staff  
**Goal:** ดูการจัดอันดับและเปรียบเทียบกับผู้อื่น  

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
- 4a. ผู้ใช้น้อยกว่า 3 คน → แจ้งว่าผู้ใช้ไม่เพียงพอ

**Postconditions:**
- ผู้ใช้เห็นตำแหน่งของตนเอง

---

## UC-09: Earn Badges & Points

**Primary Actor:** System (Automated)  
**Secondary Actor:** Student, Staff  
**Goal:** คำนวณและมอบ badges/points ตามกิจกรรม  

**Preconditions:**
- ผู้ใช้บันทึกกิจกรรม

**Main Success Scenario:**
1. ระบบตรวจสอบกิจกรรมที่บันทึก
2. คำนวณคะแนนตามกฎที่กำหนด
3. ตรวจสอบเงื่อนไข badges
4. อัพเดทคะแนนและมอบ badges
5. แจ้งเตือนผู้ใช้ (ถ้าได้ badge ใหม่)

**Business Rules:**
- เดิน/จักรยาน = bonus points
- Recycling = bonus points
- Streak (บันทึกต่อเนื่อง) = combo bonus

**Postconditions:**
- คะแนนและ badges อัพเดท

---

## UC-10: Set Personal Goals

**Primary Actor:** Student, Staff  
**Goal:** ตั้งเป้าหมายการลด Carbon Footprint  

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

**Postconditions:**
- เป้าหมายถูกบันทึก
- ระบบเริ่ม track progress

---

## UC-11: Access Admin Dashboard

**Primary Actor:** System Administrator  
**Goal:** เข้าถึงข้อมูลภาพรวมของระบบ  

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
- 1a. ไม่มีสิทธิ์ → ปฏิเสธการเข้าถึง

**Postconditions:**
- Admin เห็นภาพรวมระบบ

---

## UC-12: Generate System Reports

**Primary Actor:** System Administrator  
**Goal:** สร้างรายงานระบบเพื่อนำเสนอผู้บริหาร  

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
- 6a. ข้อมูลไม่เพียงพอ → แจ้งและแนะนำช่วงเวลาอื่น

**Postconditions:**
- Admin ได้รับรายงานที่ต้องการ

---

## UC-13: Manage Emission Factors

**Primary Actor:** System Administrator  
**Goal:** จัดการค่าคงที่สำหรับคำนวณ CO₂  

**Preconditions:**
- ผู้ใช้มีสิทธิ์ admin

**Main Success Scenario:**
1. เข้าหน้า "จัดการ Emission Factors"
2. ระบบแสดงตารางค่าคงที่ปัจจุบัน
3. เลือกแก้ไขค่าที่ต้องการ
4. กรอกค่าใหม่พร้อมแหล่งอ้างอิง
5. คลิก "บันทึก"
6. ระบบอัพเดทค่าและ recalculate ข้อมูลย้อนหลัง

**Business Rules:**
- ต้องมีแหล่งอ้างอิงที่เชื่อถือได้
- การเปลี่ยนแปลงมีผลย้อนหลัง 30 วัน

**Postconditions:**
- ค่าคงที่อัพเดท
- การคำนวณใช้ค่าใหม่

---

## UC-14: Manage User Accounts

**Primary Actor:** System Administrator  
**Goal:** จัดการบัญชีผู้ใช้ในระบบ  

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
- 4a. รีเซ็ตข้อมูล → ขอยืนยันเพิ่มเติม

**Postconditions:**
- บัญชีผู้ใช้อัพเดทตามที่ต้องการ

---

## การเชื่อมโยง Use Cases

### ลำดับการใช้งานทั่วไป:
1. **UC-01** (Login) → **UC-05** (Dashboard)
2. **UC-05** → **UC-02/03/04** (Log Activities)
3. **UC-02/03/04** → **UC-09** (Auto earn points)
4. **UC-05** → **UC-06/07/08** (View Reports/Analysis)

### Dependencies:
- UC-02, 03, 04 ต้องใช้ UC-01 ก่อน
- UC-09 trigger โดย UC-02, 03, 04
- UC-06, 07 ต้องมีข้อมูลจาก UC-02, 03, 04
- UC-11-14 ต้องใช้ UC-01 ด้วยสิทธิ์ admin

### Technical Implementation Notes:
- ใช้ University SSO API สำหรับ UC-01
- Calculation Engine แยกเป็น microservice
- Real-time updates สำหรับ dashboard และ leaderboard
- Caching สำหรับข้อมูลที่ไม่เปลี่ยนแปลงบ่อย
- Background jobs สำหรับการคำนวณ points และ badges

# Traceability Matrix: Requirements to Use Cases

## Epic to Use Case Mapping

| Epic | User Stories | Use Cases | Priority | Notes |
|------|-------------|-----------|----------|-------|
| **E01: User Onboarding** | US-01: เข้าสู่ระบบด้วย SSO | UC-01: Authenticate User | Must Have | Entry point |
| **E02: Activity Logging** | US-02: บันทึกการเดินทาง | UC-02: Log Transportation | Must Have | Core feature |
| | US-03: บันทึกการใช้พลังงาน | UC-03: Log Energy Usage | Must Have | Core feature |
| | (Future) บันทึกการจัดการขยะ | UC-04: Log Waste Management | Should Have | Release 2 |
| **E03: Feedback & Visualization** | US-04: ดู Dashboard ส่วนตัว | UC-05: View Personal Dashboard | Must Have | User engagement |
| | US-06: ดูรายงานสรุปรายเดือน | UC-06: View Carbon Reports | Should Have | Analysis |
| | (Enhanced) ดูแนวโน้ม | UC-07: View Trend Analysis | Could Have | Advanced |
| **E04: Gamification** | US-05: ระบบแต้มและ Badges | UC-08: View Leaderboard | Should Have | Motivation |
| | US-07: ตั้งเป้าหมายส่วนตัว | UC-10: Set Personal Goals | Could Have | Personalization |
| **E05: Administration** | US-08: Admin Dashboard | UC-11: Access Admin Dashboard | Won't Have (MVP) | Future |
| | (Admin) สร้างรายงานระบบ | UC-12: Generate System Reports | Won't Have (MVP) | Future |
| | (Admin) จัดการค่าคงที่ | UC-13: Manage Emission Factors | Won't Have (MVP) | Future |
| | (Admin) จัดการผู้ใช้ | UC-14: Manage User Accounts | Won't Have (MVP) | Future |

## Persona to Use Case Mapping

### น้องเกม (นักศึกษาผู้รักการแข่งขัน) 🏆

| Use Case | Frequency | Importance | User Experience Focus |
|----------|-----------|------------|----------------------|
| UC-01: Authenticate User | Once per session | Critical | Quick & seamless login |
| UC-02: Log Transportation | Daily | High | Fast data entry, 1-minute rule |
| UC-03: Log Energy Usage | Monthly | Medium | Simple form, validation |
| UC-05: View Personal Dashboard | Multiple daily | High | Real-time updates, visual appeal |
| UC-08: View Leaderboard & Badges | Daily | High | Competition, achievements |
| UC-06: View Carbon Reports | Weekly | Medium | Progress tracking |

### พี่พลอย (บุคลากรสายรักษ์โลก) 🌍

| Use Case | Frequency | Importance | User Experience Focus |
|----------|-----------|------------|----------------------|
| UC-01: Authenticate User | Once per session | Critical | Security, trust |
| UC-02: Log Transportation | Daily | High | Accuracy, detailed options |
| UC-03: Log Energy Usage | Monthly | High | Precise calculations |
| UC-05: View Personal Dashboard | Daily | High | Meaningful insights |
| UC-06: View Carbon Reports | Weekly | High | Detailed analysis, trends |
| UC-07: View Trend Analysis | Monthly | High | Long-term patterns |
| UC-10: Set Personal Goals | Monthly | High | Goal setting, progress tracking |

### คุณแอน (ผู้ดูแลระบบ) 📊

| Use Case | Frequency | Importance | User Experience Focus |
|----------|-----------|------------|----------------------|
| UC-01: Authenticate User | Daily | Critical | Admin privileges |
| UC-11: Access Admin Dashboard | Daily | Critical | Comprehensive overview |
| UC-12: Generate System Reports | Weekly | High | Flexible reporting |
| UC-13: Manage Emission Factors | Monthly | Medium | Data management |
| UC-14: Manage User Accounts | As needed | Medium | User administration |

## MoSCoW Analysis with Use Cases

### Must Have (Release 1 - MVP)
- **UC-01: Authenticate User** - No system access without this
- **UC-02: Log Transportation** - Core data collection
- **UC-03: Log Energy Usage** - Core data collection
- **UC-05: View Personal Dashboard** - User feedback loop

### Should Have (Release 1 Enhancement)
- **UC-08: View Leaderboard & Badges** - User engagement driver
- **UC-06: View Carbon Reports** - Analysis capability

### Could Have (Release 2)
- **UC-04: Log Waste Management** - Additional data source
- **UC-07: View Trend Analysis** - Advanced analytics
- **UC-10: Set Personal Goals** - Personalization

### Won't Have This Time (Future Releases)
- **UC-11: Access Admin Dashboard** - Complex feature
- **UC-12: Generate System Reports** - Administrative tool
- **UC-13: Manage Emission Factors** - Configuration management
- **UC-14: Manage User Accounts** - User administration

## Business Value vs Technical Complexity Matrix

```
High Business Value │ UC-05 Dashboard    │ UC-08 Leaderboard │
                    │ UC-02 Transport    │ UC-06 Reports     │
                    │ UC-03 Energy       │                   │
────────────────────┼──────────────────  ┼─────────────────── │
                    │ UC-04 Waste        │ UC-11 Admin       │
Low Business Value  │ UC-10 Goals        │ UC-12 System Rpt  │
                    │                    │ UC-13 Config      │
                    │                    │ UC-14 User Mgmt   │
                    └────────────────────┴─────────────────── ┘
                   Low Technical        High Technical
                   Complexity           Complexity

Legend:
- Top-left: Quick wins (implement first)
- Top-right: Major projects (implement second)
- Bottom-left: Fill-ins (implement when time allows)
- Bottom-right: Questionable (evaluate carefully)
```

## Implementation Roadmap

### Sprint 1 (Weeks 1-2): Foundation
- UC-01: Authenticate User
- UC-02: Log Transportation (basic)
- UC-03: Log Energy Usage (basic)

### Sprint 2 (Weeks 3-4): Core Loop
- UC-05: View Personal Dashboard
- Enhance UC-02 & UC-03 with validation

### Sprint 3 (Weeks 5-6): Engagement
- UC-08: View Leaderboard & Badges
- Basic gamification system

### Sprint 4 (Weeks 7-8): Analysis
- UC-06: View Carbon Reports
- Data export functionality

### Future Sprints:
- UC-04, UC-07, UC-10 (User enhancements)
- UC-11, UC-12, UC-13, UC-14 (Admin features)

## Success Metrics per Use Case

| Use Case | Success Metric | Target Value |
|----------|---------------|--------------|
| UC-01 | Login success rate | >95% |
| UC-02 | Daily logging rate | >70% of active users |
| UC-03 | Monthly logging rate | >80% of active users |
| UC-05 | Dashboard load time | <3 seconds |
| UC-08 | Leaderboard engagement | >50% weekly views |
| UC-06 | Report generation | >30% monthly usage |

This traceability matrix ensures that every requirement from the Requirements Analysis Document is properly addressed by corresponding use cases, and provides clear guidance for implementation priorities.
