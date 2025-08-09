# Requirements Discovery Document
## ระบบติดตาม Carbon Footprint - EcoTrack (Student Edition)
### Personas, User Stories, Epics & Story Mapping

**Document ID:** RDD-ECO-STUDENT-001  
**Version:** 1.0  
**วันที่:** มีนาคม 2567  
**สถานะ:** Final  
**จัดทำโดย:** นักศึกษาวิศวกรรมซอฟต์แวร์ ปี 2  
**วัตถุประสงค์:** เพื่อการเรียนรู้และฝึกปฏิบัติ Software Requirements Engineering

---

## สารบัญ

1. [บทนำและวัตถุประสงค์](#1-บทนำและวัตถุประสงค์)
2. [Personas (ตัวละครผู้ใช้งาน)](#2-personas-ตัวละครผู้ใช้งาน)
3. [Epics (กลุ่มฟีเจอร์หลัก)](#3-epics-กลุ่มฟีเจอร์หลัก)
4. [User Story Mapping](#4-user-story-mapping)
5. [User Stories รายละเอียด](#5-user-stories-รายละเอียด)
6. [การจัดลำดับความสำคัญ](#6-การจัดลำดับความสำคัญ)
7. [MVP Scope สำหรับนักศึกษา](#7-mvp-scope-สำหรับนักศึกษา)

---

## 1. บทนำและวัตถุประสงค์

### 1.1 ภาพรวมโครงการ
**EcoTrack** เป็นระบบติดตาม Carbon Footprint ขนาดเล็กที่ออกแบบมาสำหรับนักศึกษาวิศวกรรมซอฟต์แวร์ปี 2 ใช้เป็นโครงการเรียนรู้การพัฒนาซอฟต์แวร์แบบครบวงจร

### 1.2 ขอบเขตโครงการสำหรับนักศึกษา
- **ระยะเวลาพัฒนา:** 1 ภาคการศึกษา (4 เดือน)
- **ทีมพัฒนา:** 4-5 คน/กลุ่ม
- **เทคโนโลยี:** Web Application พื้นฐาน
- **ฟีเจอร์หลัก:** 3-4 ฟีเจอร์สำคัญ

### 1.3 Learning Objectives
- เข้าใจกระบวนการ Requirements Discovery
- ฝึกการสร้าง Personas และ User Stories
- เรียนรู้การทำ Story Mapping
- ประยุกต์ใช้ Agile Methodology

---

## 2. Personas (ตัวละครผู้ใช้งาน)

### 2.1 Primary Persona: น้องมิ้นท์ - นักศึกษาทั่วไป

**ข้อมูลพื้นฐาน:**
- **อายุ:** 19 ปี
- **ชั้นปี:** นักศึกษาปี 2 คณะวิศวกรรมศาสตร์
- **ที่พัก:** หอพักมหาวิทยาลัย
- **งบประมาณ/เดือน:** 5,000 บาท
- **อุปกรณ์:** Smartphone (Android), Laptop

**ไลฟ์สไตล์:**
- เดินไปเรียน 1 กม./วัน
- ใช้รถมอเตอร์ไซค์รับจ้างบางครั้ง
- กินข้าวในโรงอาหาร 2 มื้อ/วัน
- ใช้ไฟในหอพักประมาณ 50 หน่วย/เดือน

**พฤติกรรมการใช้เทคโนโลยี:**
- ใช้ LINE, Instagram, TikTok ทุกวัน
- คุ้นเคยกับ Mobile Apps
- ไม่ชอบแอปที่ซับซ้อน
- ชอบ Gamification และการแข่งขัน

**Pain Points:**
> "ไม่รู้ว่าตัวเองทำให้เกิด Carbon เท่าไหร่"
> "อยากช่วยโลกแต่ไม่รู้จะเริ่มยังไง"
> "ลืมบันทึกข้อมูลบ่อย"
> "ไม่เห็นผลที่ชัดเจน"

**Goals:**
- อยากรู้ว่าตัวเองปล่อย Carbon เท่าไหร่
- อยากลด Carbon Footprint
- อยากได้รับการยอมรับจากเพื่อน
- อยากเห็นการเปลี่ยนแปลงที่ดีขึ้น

**User Journey ปัจจุบัน:**
```
ตื่นนอน → อาบน้ำ (ใช้น้ำ) → เดินไปเรียน → ใช้ไฟฟ้าห้องเรียน 
→ กินข้าวกลางวัน → เรียนต่อ → กลับหอพัก → ใช้ไฟฟ้า 
→ ทิ้งขยะ → นอน
```

---

### 2.2 Secondary Persona: พี่เบนซ์ - นักศึกษาที่ใช้รถยนต์

**ข้อมูลพื้นฐาน:**
- **อายุ:** 21 ปี
- **ชั้นปี:** นักศึกษาปี 4
- **ที่พัก:** บ้านนอกมหาวิทยาลัย (10 กม.)
- **การเดินทาง:** ขับรถยนต์มาเรียนทุกวัน

**พฤติกรรม:**
- ขับรถ 20 กม./วัน
- รู้ว่าการขับรถทำให้เกิด Carbon แต่จำเป็น
- สนใจการ Offset Carbon
- มีเพื่อนนั่งรถมาด้วย 2-3 คน

**Pain Points:**
> "รู้ว่าขับรถไม่ดีต่อสิ่งแวดล้อม แต่ไม่มีทางเลือก"
> "อยากรู้ว่าถ้า carpool จะลด carbon ได้เท่าไหร่"

**Goals:**
- หาวิธีลด impact จากการขับรถ
- Track การใช้น้ำมัน
- เปรียบเทียบกับการเดินทางวิธีอื่น

---

### 2.3 Admin Persona: อาจารย์ปุ๊ก - ผู้ดูแลระบบ

**ข้อมูลพื้นฐาน:**
- **อายุ:** 32 ปี
- **ตำแหน่ง:** อาจารย์ที่ปรึกษาโครงการ
- **ความเชี่ยวชาญ:** Environmental Science + IT

**หน้าที่:**
- ดูภาพรวม Carbon Footprint ของนักศึกษา
- สร้างรายงานสรุป
- ให้คำแนะนำการลด Carbon
- จัดกิจกรรม/แคมเปญ

**Pain Points:**
> "ยากที่จะติดตามข้อมูลของนักศึกษาทั้งหมด"
> "ต้องการข้อมูลเพื่อทำรายงานให้มหาวิทยาลัย"

---

## 3. Epics (กลุ่มฟีเจอร์หลัก)

### Epic Structure
```
EPIC-01: User Management (การจัดการผู้ใช้)
EPIC-02: Activity Tracking (การบันทึกกิจกรรม)  
EPIC-03: Carbon Calculation (การคำนวณ Carbon)
EPIC-04: Data Visualization (การแสดงผลข้อมูล)
EPIC-05: Gamification (ระบบเกมมิฟิเคชั่น)
EPIC-06: Reporting (รายงาน)
```

### Epic Details

#### EPIC-01: User Management
**Goal:** ผู้ใช้สามารถสร้างบัญชีและจัดการข้อมูลส่วนตัว
**Value:** ระบุตัวตนและติดตามข้อมูลรายบุคคล
**Scope:**
- Registration
- Login/Logout  
- Profile Management
- Password Reset

#### EPIC-02: Activity Tracking
**Goal:** ผู้ใช้สามารถบันทึกกิจกรรมประจำวัน
**Value:** เก็บข้อมูลเพื่อคำนวณ Carbon Footprint
**Scope:**
- บันทึกการเดินทาง
- บันทึกการใช้ไฟฟ้า
- บันทึกการใช้น้ำ
- บันทึกการจัดการขยะ

#### EPIC-03: Carbon Calculation  
**Goal:** ระบบคำนวณ Carbon Footprint อัตโนมัติ
**Value:** แปลงกิจกรรมเป็นค่า CO2 equivalent
**Scope:**
- คำนวณจากสูตรมาตรฐาน
- แสดงผลแบบ real-time
- เปรียบเทียบกับค่าเฉลี่ย

#### EPIC-04: Data Visualization
**Goal:** แสดงข้อมูลในรูปแบบที่เข้าใจง่าย
**Value:** ช่วยให้ผู้ใช้เห็นภาพรวมและแนวโน้ม
**Scope:**
- Dashboard สรุปรายวัน/สัปดาห์/เดือน
- กราฟแสดงแนวโน้ม
- เปรียบเทียบกับเพื่อน

#### EPIC-05: Gamification (Optional for Students)
**Goal:** สร้างแรงจูงใจในการใช้งาน
**Value:** เพิ่ม engagement และ retention
**Scope:**
- Points system
- Badges/Achievements
- Leaderboard
- Challenges

#### EPIC-06: Reporting
**Goal:** สร้างรายงานสรุป
**Value:** ใช้ข้อมูลในการตัดสินใจ
**Scope:**
- รายงานรายเดือน
- Export data (CSV)
- Summary statistics

---

## 4. User Story Mapping

### Story Map Structure

```
USER JOURNEY PHASES:
┌────────────┬────────────┬────────────┬────────────┬────────────┐
│  DISCOVER  │   SIGNUP   │   TRACK    │   VIEW     │   SHARE    │
│            │            │            │            │            │
├────────────┼────────────┼────────────┼────────────┼────────────┤
│ Find App   │ Register   │ Log Daily  │ Dashboard  │ Compare    │
│            │            │ Activities │            │ w/ Friends │
│ Learn      │ Login      │            │ Reports    │            │
│ About App  │            │ Quick Add  │            │ Share      │
│            │ Setup      │            │ Analytics  │ Progress   │
│            │ Profile    │ Edit/Delete│            │            │
└────────────┴────────────┴────────────┴────────────┴────────────┘

RELEASE PLANNING:
┌─────────────────────────────────────────────────────────────────┐
│ RELEASE 1 (MVP) - 1 Month                                      │
├─────────────────────────────────────────────────────────────────┤
│ • Basic Registration/Login                                     │
│ • Add Travel Activity                                          │
│ • Simple Dashboard                                             │
│ • Basic CO2 Calculation                                        │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│ RELEASE 2 - 2 Months                                           │
├─────────────────────────────────────────────────────────────────┤
│ • Add Energy & Water Tracking                                  │
│ • Improved Dashboard with Graphs                               │
│ • Weekly/Monthly Reports                                       │
│ • Profile Management                                           │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│ RELEASE 3 - 3 Months                                           │
├─────────────────────────────────────────────────────────────────┤
│ • Gamification (Points, Badges)                                │
│ • Social Features (Compare, Share)                             │
│ • Advanced Analytics                                           │
│ • Data Export                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### Walking Skeleton (เริ่มต้นที่ง่ายที่สุด)
```
1. User สามารถ Register ได้
2. User สามารถ Login ได้
3. User สามารถบันทึกการเดินทางได้
4. User สามารถดู Carbon ที่เกิดขึ้นได้
5. User สามารถ Logout ได้
```

---

## 5. User Stories รายละเอียด

### Format ที่ใช้:
```
As a [type of user]
I want to [action/goal]
So that [benefit/value]

Acceptance Criteria:
Given [context]
When [action]
Then [expected result]
```

### EPIC-01: User Management

#### US-01: ลงทะเบียนผู้ใช้ใหม่
```
As a นักศึกษา
I want to สร้างบัญชีใหม่ด้วย email มหาวิทยาลัย
So that ฉันสามารถเริ่มติดตาม Carbon Footprint ของตัวเอง

Acceptance Criteria:
Given ฉันอยู่ที่หน้า Register
When ฉันกรอก email, password, ชื่อ, คณะ
Then ระบบสร้างบัญชีและนำฉันไปหน้า Dashboard

Story Points: 3
Priority: Must Have
```

#### US-02: เข้าสู่ระบบ
```
As a ผู้ใช้ที่ลงทะเบียนแล้ว
I want to login ด้วย email และ password
So that ฉันสามารถเข้าถึงข้อมูลของฉัน

Acceptance Criteria:
Given ฉันมีบัญชีแล้ว
When ฉันกรอก email และ password ที่ถูกต้อง
Then ระบบนำฉันไป Dashboard พร้อมแสดงชื่อ

Story Points: 2
Priority: Must Have
```

#### US-03: ออกจากระบบ
```
As a ผู้ใช้ที่ login อยู่
I want to logout จากระบบ
So that ข้อมูลของฉันปลอดภัย

Acceptance Criteria:
Given ฉัน login อยู่
When ฉันคลิก Logout
Then ระบบนำฉันกลับไปหน้า Login และลบ session

Story Points: 1
Priority: Must Have
```

#### US-04: แก้ไขโปรไฟล์
```
As a ผู้ใช้
I want to แก้ไขข้อมูลส่วนตัว (ชื่อ, รูป, เป้าหมาย)
So that ข้อมูลของฉันเป็นปัจจุบัน

Acceptance Criteria:
Given ฉันอยู่ที่หน้า Profile
When ฉันแก้ไขข้อมูลและกด Save
Then ระบบบันทึกและแสดงข้อความสำเร็จ

Story Points: 2
Priority: Should Have
```

### EPIC-02: Activity Tracking

#### US-05: บันทึกการเดินทางด้วยการเดิน
```
As a น้องมิ้นท์
I want to บันทึกว่าวันนี้เดินไปเรียน 2 กม.
So that ฉันรู้ว่าการเดินไม่ปล่อย Carbon

Acceptance Criteria:
Given ฉันอยู่ที่หน้า Add Activity
When ฉันเลือก "เดิน" และใส่ระยะทาง 2 กม.
Then ระบบแสดง CO2 = 0 kg และบันทึกข้อมูล

Story Points: 3
Priority: Must Have
```

#### US-06: บันทึกการเดินทางด้วยรถยนต์
```
As a พี่เบนซ์
I want to บันทึกว่าวันนี้ขับรถมาเรียน 10 กม.
So that ฉันรู้ว่าปล่อย Carbon เท่าไหร่

Acceptance Criteria:
Given ฉันอยู่ที่หน้า Add Activity
When ฉันเลือก "รถยนต์" และใส่ระยะทาง 10 กม.
Then ระบบแสดง CO2 = 2.1 kg (10 × 0.21)

Story Points: 3
Priority: Must Have
```

#### US-07: บันทึกการใช้ไฟฟ้า
```
As a น้องมิ้นท์
I want to บันทึกค่าไฟเดือนนี้ 50 หน่วย
So that ฉันรู้ว่าการใช้ไฟปล่อย Carbon เท่าไหร่

Acceptance Criteria:
Given ฉันอยู่ที่หน้า Add Activity
When ฉันเลือก "ไฟฟ้า" และใส่ 50 kWh
Then ระบบแสดง CO2 = 28.05 kg (50 × 0.561)

Story Points: 3
Priority: Must Have
```

#### US-08: แก้ไขกิจกรรมที่บันทึกไปแล้ว
```
As a ผู้ใช้
I want to แก้ไขข้อมูลที่บันทึกผิด
So that ข้อมูลของฉันถูกต้อง

Acceptance Criteria:
Given ฉันมีกิจกรรมที่บันทึกไว้
When ฉันคลิก Edit และแก้ไขข้อมูล
Then ระบบ update และคำนวณ CO2 ใหม่

Story Points: 2
Priority: Should Have
```

#### US-09: ลบกิจกรรม
```
As a ผู้ใช้
I want to ลบกิจกรรมที่บันทึกซ้ำ
So that ไม่มีข้อมูลซ้ำซ้อน

Acceptance Criteria:
Given ฉันมีกิจกรรมที่บันทึกไว้
When ฉันคลิก Delete และยืนยัน
Then ระบบลบข้อมูลและอัพเดท Dashboard

Story Points: 2
Priority: Should Have
```

### EPIC-03: Carbon Calculation

#### US-10: คำนวณ Carbon Footprint อัตโนมัติ
```
As a ผู้ใช้
I want to เห็น CO2 ทันทีหลังบันทึกกิจกรรม
So that ฉันเข้าใจ impact ของการกระทำ

Acceptance Criteria:
Given ฉันบันทึกกิจกรรมใดๆ
When ระบบได้รับข้อมูล
Then แสดง CO2 คำนวณตามสูตร:
- เดิน/จักรยาน: 0 kg CO2/km
- รถเมล์: 0.04 kg CO2/km
- รถยนต์: 0.21 kg CO2/km
- ไฟฟ้า: 0.561 kg CO2/kWh

Story Points: 5
Priority: Must Have
```

#### US-11: เปรียบเทียบกับค่าเฉลี่ย
```
As a น้องมิ้นท์
I want to รู้ว่า Carbon ของฉันมากหรือน้อยกว่าเฉลี่ย
So that ฉันรู้ว่าต้องปรับพฤติกรรมไหม

Acceptance Criteria:
Given ฉันดู Dashboard
When ระบบแสดง Carbon ของฉัน
Then แสดงเปรียบเทียบกับค่าเฉลี่ยของนักศึกษา
(เฉลี่ย 5 kg CO2/วัน)

Story Points: 3
Priority: Should Have
```

### EPIC-04: Data Visualization

#### US-12: Dashboard แสดงสรุปรายวัน
```
As a ผู้ใช้
I want to เห็นสรุป Carbon วันนี้
So that ฉันรู้สถานะปัจจุบัน

Acceptance Criteria:
Given ฉัน login แล้ว
When ฉันเข้า Dashboard
Then เห็น:
- Total CO2 วันนี้
- จำนวนกิจกรรม
- กราฟแบ่งตามประเภท

Story Points: 5
Priority: Must Have
```

#### US-13: กราฟแสดงแนวโน้มรายสัปดาห์
```
As a ผู้ใช้
I want to เห็นกราฟ Carbon 7 วันย้อนหลัง
So that ฉันเห็นแนวโน้มการเปลี่ยนแปลง

Acceptance Criteria:
Given ฉันมีข้อมูลอย่างน้อย 7 วัน
When ฉันดู Dashboard
Then เห็น Line Chart แสดง CO2 รายวัน

Story Points: 3
Priority: Should Have
```

#### US-14: รายงานสรุปรายเดือน
```
As a อาจารย์ปุ๊ก
I want to ดูรายงาน Carbon รายเดือนของนักศึกษา
So that ฉันสามารถติดตามความก้าวหน้า

Acceptance Criteria:
Given ฉันเป็น Admin
When ฉันเลือก Monthly Report
Then เห็น:
- Total CO2 ของเดือน
- จำนวนผู้ใช้ที่ active
- Top 10 ผู้ที่ Carbon น้อยสุด

Story Points: 5
Priority: Could Have
```

### EPIC-05: Gamification (Optional)

#### US-15: ระบบคะแนน
```
As a น้องมิ้นท์
I want to ได้คะแนนจากการบันทึกกิจกรรม
So that ฉันมีแรงจูงใจในการใช้งาน

Acceptance Criteria:
Given ฉันบันทึกกิจกรรม
When กิจกรรมเป็น eco-friendly (เดิน, จักรยาน)
Then ได้คะแนนพิเศษ:
- เดิน: 10 points/km
- จักรยาน: 8 points/km
- รถเมล์: 4 points/km
- รถยนต์: 1 point/km

Story Points: 3
Priority: Could Have
```

#### US-16: Badges สำหรับความสำเร็จ
```
As a ผู้ใช้
I want to ได้ Badge เมื่อทำภารกิจสำเร็จ
So that ฉันรู้สึกภูมิใจ

Acceptance Criteria:
Given ฉันทำตามเงื่อนไข
When ครบเกณฑ์ (เช่น บันทึก 7 วันติด)
Then ได้รับ Badge และแสดงในโปรไฟล์

Badges:
- Eco Starter: บันทึก 7 วันติด
- Green Walker: เดิน 50 km
- Carbon Saver: ลด CO2 20%/เดือน

Story Points: 5
Priority: Won't Have (Phase 1)
```

#### US-17: Leaderboard
```
As a น้องมิ้นท์
I want to เห็นอันดับของฉันเทียบกับเพื่อน
So that ฉันมีแรงจูงใจแข่งขัน

Acceptance Criteria:
Given ฉันดู Leaderboard
When ระบบแสดงรายการ
Then เห็น Top 10 คนที่ CO2 น้อยสุด
และเห็นอันดับของตัวเอง

Story Points: 3
Priority: Won't Have (Phase 1)
```

---

## 6. การจัดลำดับความสำคัญ

### MoSCoW Prioritization

#### Must Have (60% effort) - สำหรับ MVP
1. **US-01:** Registration (3 points)
2. **US-02:** Login (2 points)
3. **US-03:** Logout (1 point)
4. **US-05:** บันทึกการเดิน (3 points)
5. **US-06:** บันทึกรถยนต์ (3 points)
6. **US-07:** บันทึกไฟฟ้า (3 points)
7. **US-10:** คำนวณ CO2 (5 points)
8. **US-12:** Dashboard พื้นฐาน (5 points)
**Total: 25 Story Points**

#### Should Have (20% effort)
1. **US-04:** Edit Profile (2 points)
2. **US-08:** Edit Activity (2 points)
3. **US-09:** Delete Activity (2 points)
4. **US-11:** เปรียบเทียบค่าเฉลี่ย (3 points)
5. **US-13:** กราฟ 7 วัน (3 points)
**Total: 12 Story Points**

#### Could Have (10% effort)
1. **US-14:** Monthly Report (5 points)
2. **US-15:** Points System (3 points)
**Total: 8 Story Points**

#### Won't Have (Phase 1)
1. **US-16:** Badges (5 points)
2. **US-17:** Leaderboard (3 points)
**Total: 8 Story Points**

### Value vs Effort Matrix
```
        High Value
             │
    [US-12]  │  [US-01,02,05,06,07]
    [US-10]  │        
    ─────────┼─────────
    [US-13]  │  [US-03,04,08,09]
    [US-14]  │  [US-11,15]
             │
        Low Value
        
    Low Effort    High Effort
```

---

## 7. MVP Scope สำหรับนักศึกษา

### Sprint Planning (2-week sprints)

#### Sprint 1: Foundation (สัปดาห์ 1-2)
**Goal:** สร้างระบบ Authentication พื้นฐาน
- Setup project structure
- Database design (users, activities tables)
- US-01: Registration
- US-02: Login
- US-03: Logout

#### Sprint 2: Core Features (สัปดาห์ 3-4)
**Goal:** สร้างระบบบันทึกกิจกรรมพื้นฐาน
- US-05: บันทึกการเดิน
- US-06: บันทึกรถยนต์
- US-07: บันทึกไฟฟ้า
- Database: activities table

#### Sprint 3: Calculation Engine (สัปดาห์ 5-6)
**Goal:** สร้างระบบคำนวณ CO2
- US-10: คำนวณ CO2 อัตโนมัติ
- Emission factors configuration
- Basic validation

#### Sprint 4: Dashboard (สัปดาห์ 7-8)
**Goal:** สร้างหน้า Dashboard แสดงผล
- US-12: Dashboard พื้นฐาน
- Summary statistics
- Basic charts (Pie chart)

#### Sprint 5: Enhancement (สัปดาห์ 9-10)
**Goal:** ปรับปรุง UX และเพิ่มฟีเจอร์
- US-04: Edit Profile
- US-08: Edit Activity
- US-09: Delete Activity
- UI improvements

#### Sprint 6: Analytics (สัปดาห์ 11-12)
**Goal:** เพิ่มการวิเคราะห์ข้อมูล
- US-11: เปรียบเทียบค่าเฉลี่ย
- US-13: กราฟ 7 วัน
- Data aggregation

#### Sprint 7: Testing & Polish (สัปดาห์ 13-14)
**Goal:** ทดสอบและปรับปรุง
- User testing
- Bug fixes
- Documentation
- Performance optimization

#### Sprint 8: Deployment (สัปดาห์ 15-16)
**Goal:** Deploy และ present
- Production deployment
- User manual
- Final presentation
- Project handover

### Definition of Done (DoD)
สำหรับแต่ละ User Story ให้ถือว่า "Done" เมื่อ:
- [ ] Code เขียนเสร็จและ reviewed
- [ ] Unit tests ผ่าน (ถ้ามี)
- [ ] Feature ทำงานได้ตาม Acceptance Criteria
- [ ] UI responsive บน mobile/desktop
- [ ] ไม่มี console errors
- [ ] Merged to main branch
- [ ] Tested by teammate

### Technical Stack แนะนำสำหรับนักศึกษา

#### Option 1: Simple Stack (แนะนำสำหรับ Beginner)
**Frontend:**
- HTML, CSS, JavaScript (Vanilla)
- Bootstrap 5 for styling
- Chart.js for graphs

**Backend:**
- Node.js + Express.js
- SQLite database (ง่ายต่อการ setup)
- Simple JWT authentication

**Deployment:**
- GitHub Pages (Frontend)
- Render.com or Railway (Backend)

#### Option 2: Modern Stack (สำหรับที่มีพื้นฐาน)
**Frontend:**
- React.js
- Material-UI or Tailwind CSS
- Recharts for visualization

**Backend:**
- Node.js + Express.js
- PostgreSQL
- JWT + bcrypt

**Deployment:**
- Vercel (Frontend)
- Heroku or Railway (Backend)

### Emission Factors Reference
```javascript
const EMISSION_FACTORS = {
  // Transportation (kg CO2 per km)
  walking: 0,
  bicycle: 0,
  motorcycle: 0.11,
  car: 0.21,
  bus: 0.04,
  train: 0.02,
  
  // Energy (kg CO2 per unit)
  electricity: 0.561, // per kWh
  water: 0.272, // per cubic meter
  
  // Waste (kg CO2 per kg)
  general_waste: 2.86,
  recycling: -1.02, // negative = carbon saved
  organic_waste: 0.47
};
```

---

## 8. Risk Management สำหรับโครงการนักศึกษา

### Technical Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| ไม่เคยทำ Web App | High | เริ่มจาก tutorial, ใช้ template |
| Database design ผิด | Medium | ปรึกษาอาจารย์, ดูตัวอย่าง |
| การคำนวณ CO2 ผิด | High | ใช้สูตรจาก TGO, double-check |
| Deploy ไม่เป็น | Medium | ใช้ free service, ดู tutorial |

### Project Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| สมาชิกลาออก | High | แบ่งงานให้ independent |
| Scope creep | Medium | ยึด MVP, ไม่เพิ่ม feature |
| เวลาไม่พอ | High | ทำ Must Have ก่อน |
| Bug เยอะ | Medium | Test ตั้งแต่ sprint แรก |

---

## 9. Success Criteria

### Functional Success
- [ ] ผู้ใช้สามารถลงทะเบียนและ login ได้
- [ ] บันทึกกิจกรรมอย่างน้อย 3 ประเภท
- [ ] คำนวณ CO2 ได้ถูกต้อง
- [ ] แสดง Dashboard พื้นฐาน
- [ ] ข้อมูลบันทึกในฐานข้อมูล

### Learning Success
- [ ] เข้าใจ Requirements Engineering Process
- [ ] สามารถเขียน User Stories ได้
- [ ] ใช้ Agile methodology
- [ ] ทำงานเป็นทีม
- [ ] Deploy application ได้

### Quality Metrics
- [ ] ไม่มี critical bugs
- [ ] Response time < 3 seconds
- [ ] Mobile responsive
- [ ] Code documented
- [ ] User manual ready

---

## 10. Resources สำหรับนักศึกษา

### Learning Resources
1. **Requirements Engineering:**
   - [User Story Mapping by Jeff Patton](https://www.jpattonassociates.com/user-story-mapping/)
   - [Writing Good User Stories](https://www.atlassian.com/agile/project-management/user-stories)

2. **Web Development:**
   - [MDN Web Docs](https://developer.mozilla.org/)
   - [W3Schools](https://www.w3schools.com/)
   - [freeCodeCamp](https://www.freecodecamp.org/)

3. **Carbon Footprint Calculation:**
   - [Thailand Greenhouse Gas Management Organization (TGO)](http://www.tgo.or.th/)
   - [EPA Carbon Calculator](https://www.epa.gov/energy/greenhouse-gas-equivalencies-calculator)

### Tools แนะนำ
1. **Project Management:**
   - Trello (free for students)
   - GitHub Projects
   - Notion

2. **Design:**
   - Figma (free for students)
   - Draw.io (diagrams)
   - Canva (presentations)

3. **Development:**
   - VS Code
   - GitHub (version control)
   - Postman (API testing)

4. **Communication:**
   - Discord/Slack
   - Google Meet
   - LINE Group

---

## 11. Templates และ Examples

### User Story Template
```
Story ID: US-XX
Title: [Short descriptive title]
As a [persona]
I want to [action]
So that [benefit]

Acceptance Criteria:
- [ ] Given [context]
      When [action]
      Then [result]
- [ ] Given [context]
      When [action]
      Then [result]

Story Points: [1, 2, 3, 5, 8]
Priority: [Must/Should/Could/Won't]
Sprint: [1-8]
Assigned to: [Team member]
Status: [To Do/In Progress/Testing/Done]
```

### Daily Standup Template
```
Yesterday:
- Completed [task]
- Worked on [feature]

Today:
- Will complete [task]
- Will start [feature]

Blockers:
- [Issue that needs help]
```

### Sprint Review Template
```
Sprint X Review (Date)

Completed:
- US-XX: [Title] ✅
- US-XX: [Title] ✅

Not Completed:
- US-XX: [Title] - Reason: [why]

Demo:
- Feature 1: [Who will demo]
- Feature 2: [Who will demo]

Metrics:
- Story Points Completed: X/Y
- Bugs Found: X
- Bugs Fixed: X

Next Sprint:
- Priority items
- Carry over items
```

---

## 12. Grading Rubric (เกณฑ์การให้คะแนน)

### Requirements Document (20%)
- Personas ครบถ้วนและสมจริง (5%)
- User Stories มี acceptance criteria (5%)
- Story Mapping สมเหตุสมผล (5%)
- Prioritization ถูกต้อง (5%)

### Implementation (40%)
- MVP Features ทำงานได้ (20%)
- Code Quality (10%)
- Database Design (5%)
- UI/UX (5%)

### Process (20%)
- ใช้ Agile/Scrum (5%)
- Version Control (Git) (5%)
- Team Collaboration (5%)
- Documentation (5%)

### Testing (10%)
- Test Cases (5%)
- Bug-free MVP (5%)

### Presentation (10%)
- Demo (5%)
- Q&A (5%)

---

## สรุป

เอกสาร Requirements Discovery นี้เป็นแนวทางสำหรับนักศึกษาวิศวกรรมซอฟต์แวร์ปี 2 ในการพัฒนาระบบ EcoTrack ซึ่งเป็นระบบติดตาม Carbon Footprint ขนาดเล็ก โดยมีจุดมุ่งหมายเพื่อ:

1. **ฝึกปฏิบัติ Requirements Engineering** - การสร้าง Personas, User Stories, Story Mapping
2. **เรียนรู้ Agile Development** - การทำงานแบบ Sprint, Daily Standup, Retrospective
3. **พัฒนา Technical Skills** - Web Development, Database, API
4. **ทำงานเป็นทีม** - แบ่งงาน, สื่อสาร, แก้ปัญหาร่วมกัน

ระบบ EcoTrack ที่นักศึกษาจะพัฒนาเป็น MVP (Minimum Viable Product) ที่มีฟีเจอร์หลัก:
- ระบบสมาชิก (Register/Login)
- บันทึกกิจกรรม (การเดินทาง, ไฟฟ้า)
- คำนวณ Carbon Footprint
- แสดงผล Dashboard

โครงการนี้ใช้เวลาพัฒนา 1 ภาคการศึกษา (16 สัปดาห์) แบ่งเป็น 8 Sprints และสามารถต่อยอดเพิ่มฟีเจอร์ เช่น Gamification, Social Features ในอนาคต

**Remember:** เริ่มจากสิ่งที่ง่ายที่สุด (Walking Skeleton) แล้วค่อยๆ เพิ่ม features ทีละอย่าง การมี MVP ที่ทำงานได้ดีกว่ามีฟีเจอร์เยอะแต่ไม่สมบูรณ์!

---

*"The best way to learn is by doing. Start small, fail fast, learn quickly, and iterate!"*

**Good luck with your EcoTrack project! 🌱💚**